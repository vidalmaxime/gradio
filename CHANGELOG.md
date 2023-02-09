# Upcoming Release

## New Features:

### New `gr.BarPlot` component! 📊

Create interactive bar plots from a high-level interface with `gr.BarPlot`. 
No need to remember matplotlib syntax anymore!

Example usage:

```python
import gradio as gr
import pandas as pd

simple = pd.DataFrame({
    'a': ['A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I'],
    'b': [28, 55, 43, 91, 81, 53, 19, 87, 52]
})

with gr.Blocks() as demo:
    gr.BarPlot(
        simple,
        x="a",
        y="b",
        title="Simple Bar Plot with made up data",
        tooltip=['a', 'b'],
    )

demo.launch()
```


By [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3157](https://github.com/gradio-app/gradio/pull/3157)

## Bug Fixes:
- Adds ability to add a single message from the bot or user side.

```python
gr.Chatbot([("Hi, I'm DialoGPT. Try asking me a question.", None)], starts_with="bot")
```
By [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 3165](https://github.com/gradio-app/gradio/pull/3165)

## Documentation Changes:
* Sort components in docs by alphabetic order by [@aliabd](https://github.com/aliabd) in [PR 3152](https://github.com/gradio-app/gradio/pull/3152)
* Changes to W&B guide by [@scottire](https://github.com/scottire) in  [PR 3153](https://github.com/gradio-app/gradio/pull/3153)
* Keep pnginfo metadata for gallery by [@wfng92](https://github.com/wfng92) in [PR 3150](https://github.com/gradio-app/gradio/pull/3150)

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Fix demos page css and add close demos button by [@aliabd](https://github.com/aliabd) in [PR 3151](https://github.com/gradio-app/gradio/pull/3151)

## Contributors Shoutout:
No changes to highlight.

# Version 3.18.0

## New Features:

### Revamped Stop Button for Interfaces 🛑

If your Interface function is a generator, there used to be a separate `Stop` button displayed next
to the `Submit` button.

We've revamed the `Submit` button so that it turns into a `Stop` button during the generation process.
Clicking on the `Stop` button will cancel the generation and turn it back to a `Submit` button. 
The `Stop` button will automatically turn back to a `Submit` button at the end of the generation if you don't use it!

By [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3124](https://github.com/gradio-app/gradio/pull/3124) 


### Queue now works with reload mode!

You can now call `queue` on your `demo` outside of the `if __name__ == "__main__"` block and
run the script in reload mode with the `gradio` command. 

Any changes to the `app.py` file will be reflected in the webpage automatically and the queue will work
properly!


By [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3089](https://github.com/gradio-app/gradio/pull/3089) 


### Allow serving files from additional directories

```python
demo = gr.Interface(...)
demo.launch(
  file_directories=["/var/lib/demo/path/to/resources"]
)
```

By [@maxaudron](https://github.com/maxaudron) in [PR 3075](https://github.com/gradio-app/gradio/pull/3075) 

## Bug Fixes:
- Fixes URL resolution on Windows by [@abidlabs](https://github.com/abidlabs) in [PR 3108](https://github.com/gradio-app/gradio/pull/3108) 
- Example caching now works with components without a label attribute (e.g. `Column`) by [@abidlabs](https://github.com/abidlabs) in [PR 3123](https://github.com/gradio-app/gradio/pull/3123) 
- Ensure the Video component correctly resets the UI state whe a new video source is loaded and reduce choppiness of UI by [@pngwn](https://github.com/abidlabs) in [PR 3117](https://github.com/gradio-app/gradio/pull/3117)
- Fixes loading private Spaces by [@abidlabs](https://github.com/abidlabs) in [PR 3068](https://github.com/gradio-app/gradio/pull/3068) 
- Added a warning when attempting to launch an `Interface` via the `%%blocks` jupyter notebook magic command by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3126](https://github.com/gradio-app/gradio/pull/3126)
- Fixes bug where interactive output image cannot be set when in edit mode by [@dawoodkhan82](https://github.com/@dawoodkhan82) in [PR 3135](https://github.com/gradio-app/gradio/pull/3135)
- A share link will automatically be created when running on Sagemaker notebooks so that the front-end is properly displayed by [@abidlabs](https://github.com/abidlabs) in [PR 3137](https://github.com/gradio-app/gradio/pull/3137) 
- Fixes a few dropdown component issues; hide checkmark next to options as expected, and keyboard hover is visible by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 3145]https://github.com/gradio-app/gradio/pull/3145)
- Fixed bug where example pagination buttons were not visible in dark mode or displayed under the examples table. By [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3144](https://github.com/gradio-app/gradio/pull/3144) 
- Fixed bug where the font color of axis labels and titles for native plots did not respond to dark mode preferences. By [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3146](https://github.com/gradio-app/gradio/pull/3146) 

## Documentation Changes:
- Added a guide on the 4 kinds of Gradio Interfaces by [@yvrjsharma](https://github.com/yvrjsharma) and [@abidlabs](https://github.com/abidlabs) in [PR 3003](https://github.com/gradio-app/gradio/pull/3003) 
- Explained that the parameters in `launch` will not be respected when using reload mode, e.g. `gradio` command  by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3089](https://github.com/gradio-app/gradio/pull/3089) 
- Added a demo to show how to set up variable numbers of outputs in Gradio by  [@abidlabs](https://github.com/abidlabs) in [PR 3127](https://github.com/gradio-app/gradio/pull/3127) 
- Updated docs to reflect that the `equal_height` parameter should be passed to the `.style()` method of `gr.Row()` by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3125](https://github.com/gradio-app/gradio/pull/3125) 

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
- Changed URL of final image for `fake_diffusion` demos by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3120](https://github.com/gradio-app/gradio/pull/3120)


## Contributors Shoutout:
No changes to highlight.


# Version 3.17.1

## New Features:

### iOS image rotation fixed 🔄

Previously photos uploaded via iOS would be rotated after processing. This has been fixed by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3089](https://github.com/gradio-app/gradio/pull/3091)

#### Before
![image](https://user-images.githubusercontent.com/41651716/215846507-a36e9d05-1ac2-4867-8ab3-ce045a9415d9.png)

#### After
![image](https://user-images.githubusercontent.com/41651716/215846554-e41773ed-70f0-491a-9952-6a18babf91ef.png)

### Run on Kaggle kernels 🧪

A share link will automatically be created when running on Kaggle kernels (notebooks) so that the front-end is properly displayed.

![image](https://user-images.githubusercontent.com/41651716/216104254-2cf55599-449c-436c-b57e-40f6a83f9eee.png)

By [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3101](https://github.com/gradio-app/gradio/pull/3101)

## Bug Fixes:
- Fix bug where examples were not rendered correctly for demos created with Blocks api that had multiple input compinents by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3090](https://github.com/gradio-app/gradio/pull/3090)
- Fix change event listener for JSON, HighlightedText, Chatbot by [@aliabid94](https://github.com/aliabid94) in [PR 3095](https://github.com/gradio-app/gradio/pull/3095)
- Fixes bug where video and file change event not working [@tomchang25](https://github.com/tomchang25) in [PR 3098](https://github.com/gradio-app/gradio/pull/3098)
- Fixes bug where static_video play and pause event not working [@tomchang25](https://github.com/tomchang25) in [PR 3098](https://github.com/gradio-app/gradio/pull/3098)
- Fixed `Gallery.style(grid=...)` by by [@aliabd](https://github.com/aliabd) in [PR 3107](https://github.com/gradio-app/gradio/pull/3107)

## Documentation Changes:
* Update chatbot guide to include blocks demo and markdown support section by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 3023](https://github.com/gradio-app/gradio/pull/3023)
- Fix a broken link in the Quick Start guide, by [@cakiki](https://github.com/cakiki) in [PR 3109](https://github.com/gradio-app/gradio/pull/3109)
- Better docs navigation on mobile by [@aliabd](https://github.com/aliabd) in [PR 3112](https://github.com/gradio-app/gradio/pull/3112)
- Add a guide on using Gradio with [Comet](https://comet.com/), by [@DN6](https://github.com/DN6/) in [PR 3058](https://github.com/gradio-app/gradio/pull/3058)

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Set minimum `markdown-it-py` version to `2.0.0` so that the dollar math plugin is compatible by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3102](https://github.com/gradio-app/gradio/pull/3102)

## Contributors Shoutout:
No changes to highlight.

# Version 3.17.0

## New Features:

### Extended support for Interface.load! 🏗️

You can now load `image-to-text` and `conversational` pipelines from the hub!

### Image-to-text Demo
```python
io = gr.Interface.load("models/nlpconnect/vit-gpt2-image-captioning",
                       api_key="<optional-api-key>")
io.launch()
```
<img width="1087" alt="image" src="https://user-images.githubusercontent.com/41651716/213260197-dc5d80b4-6e50-4b3a-a764-94980930ac38.png">

### conversational Demo
```python
chatbot = gr.Interface.load("models/microsoft/DialoGPT-medium",
                           api_key="<optional-api-key>")
chatbot.launch()
```
![chatbot_load](https://user-images.githubusercontent.com/41651716/213260220-3eaa25b7-a38b-48c6-adeb-2718bdf297a2.gif)


By [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3011](https://github.com/gradio-app/gradio/pull/3011)

### Download Button added to Model3D Output Component 📥

No need for an additional file output component to enable model3d file downloads anymore. We now added a download button to the model3d component itself.

<img width="739" alt="Screenshot 2023-01-18 at 3 52 45 PM" src="https://user-images.githubusercontent.com/12725292/213294198-5f4fda35-bde7-450c-864f-d5683e7fa29a.png">

By [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 3014](https://github.com/gradio-app/gradio/pull/3014)

### Fixing Auth on Spaces 🔑

Authentication on spaces works now! Third party cookies must be enabled on your browser to be able
to log in. Some browsers disable third party cookies by default (Safari, Chrome Incognito).

![auth_spaces](https://user-images.githubusercontent.com/41651716/215528417-09538933-0576-4d1d-b3b9-1e877ab01905.gif)


## Bug Fixes:
* Fixes bug where interpretation event was not configured correctly by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2993](https://github.com/gradio-app/gradio/pull/2993)
* Fix relative import bug in reload mode by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2992](https://github.com/gradio-app/gradio/pull/2992)
* Fixes bug where png files were not being recognized when uploading images by [@abidlabs](https://github.com/abidlabs) in [PR 3002](https://github.com/gradio-app/gradio/pull/3002)
* Fixes bug where external Spaces could not be loaded and used as functions if they returned files by [@abidlabs](https://github.com/abidlabs) in [PR 3004](https://github.com/gradio-app/gradio/pull/3004)
* Fix bug where file serialization output was not JSON serializable by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2999](https://github.com/gradio-app/gradio/pull/2999)
* Fixes bug where png files were not being recognized when uploading images by [@abidlabs](https://github.com/abidlabs) in [PR 3002](https://github.com/gradio-app/gradio/pull/3002)
* Fixes bug where temporary uploaded files were not being added to temp sets by [@abidlabs](https://github.com/abidlabs) in [PR 3005](https://github.com/gradio-app/gradio/pull/3005)
* Fixes issue where markdown support in chatbot breaks older demos [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 3006](https://github.com/gradio-app/gradio/pull/3006)
* Fixes the `/file/` route that was broken in a recent change in [PR 3010](https://github.com/gradio-app/gradio/pull/3010)
* Fix bug where the Image component could not serialize image urls by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2957](https://github.com/gradio-app/gradio/pull/2957)
* Fix forwarding for guides after SEO renaming by [@aliabd](https://github.com/aliabd) in [PR 3017](https://github.com/gradio-app/gradio/pull/3017)
* Switch all pages on the website to use latest stable gradio by [@aliabd](https://github.com/aliabd) in [PR 3016](https://github.com/gradio-app/gradio/pull/3016)
* Fix bug related to deprecated parameters in `huggingface_hub` for the HuggingFaceDatasetSaver in [PR 3025](https://github.com/gradio-app/gradio/pull/3025)
* Added better support for symlinks in the way absolute paths are resolved by [@abidlabs](https://github.com/abidlabs) in [PR 3037](https://github.com/gradio-app/gradio/pull/3037)
* Fix several minor frontend bugs (loading animation, examples as gallery) frontend [@aliabid94](https://github.com/3026) in [PR 2961](https://github.com/gradio-app/gradio/pull/3026).
* Fixes bug that the chatbot sample code does not work with certain input value by [@petrov826](https://github.com/petrov826) in [PR 3039](https://github.com/gradio-app/gradio/pull/3039).
* Fix shadows for form element and ensure focus styles more visible in dark mode   [@pngwn](https://github.com/pngwn) in [PR 3042](https://github.com/gradio-app/gradio/pull/3042).
* Fixed bug where the Checkbox and Dropdown change events were not triggered in response to other component changes by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3045](https://github.com/gradio-app/gradio/pull/3045)
* Fix bug where the queue was not properly restarted after launching a `closed` app by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3022](https://github.com/gradio-app/gradio/pull/3022)
* Adding missing embedded components on docs by [@aliabd](https://github.com/aliabd) in [PR 3027](https://github.com/gradio-app/gradio/pull/3027)
* Fixes bug where app would crash if the `file_types` parameter of `gr.File` or `gr.UploadButton` was not a list by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3048](https://github.com/gradio-app/gradio/pull/3048)
* Ensure CSS mounts correctly regardless of how many Gradio instances are on the page [@pngwn](https://github.com/pngwn) in [PR 3059](https://github.com/gradio-app/gradio/pull/3059).
* Fix bug where input component was not hidden in the frontend for `UploadButton` by  [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3053](https://github.com/gradio-app/gradio/pull/3053)
* Fixes issue where after clicking submit or undo, the sketch output wouldn't clear. [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 3047](https://github.com/gradio-app/gradio/pull/3047)
* Ensure spaces embedded via the web component always use the correct URLs for server requests and change ports for testing to avoid strange collisions when users are working with embedded apps locally by [@pngwn](https://github.com/pngwn) in [PR 3065](https://github.com/gradio-app/gradio/pull/3065)
* Preserve selected image of Gallery through updated by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3061](https://github.com/gradio-app/gradio/pull/3061)
* Fix bug where auth was not respected on HF spaces by [@freddyaboulton](https://github.com/freddyaboulton) and [@aliabid94](https://github.com/aliabid94) in [PR 3049](https://github.com/gradio-app/gradio/pull/3049)
* Fixes bug where tabs selected attribute not working if manually change tab by [@tomchang25](https://github.com/tomchang25) in [3055](https://github.com/gradio-app/gradio/pull/3055)
* Change chatbot to show dots on progress, and fix bug where chatbot would not stick to bottom in the case of images by [@aliabid94](https://github.com/aliabid94) in [PR 3067](https://github.com/gradio-app/gradio/pull/3079)

## Documentation Changes:
* SEO improvements to guides by[@aliabd](https://github.com/aliabd) in [PR 2915](https://github.com/gradio-app/gradio/pull/2915)
* Use `gr.LinePlot` for the `blocks_kinematics` demo by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2998](https://github.com/gradio-app/gradio/pull/2998)
* Updated the `interface_series_load` to include some inline markdown code by [@abidlabs](https://github.com/abidlabs) in [PR 3051](https://github.com/gradio-app/gradio/pull/3051)

## Testing and Infrastructure Changes:
* Adds a GitHub action to test if any large files (> 5MB) are present by [@abidlabs](https://github.com/abidlabs) in [PR 3013](https://github.com/gradio-app/gradio/pull/3013)

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Rewrote frontend using CSS variables for themes by [@pngwn](https://github.com/pngwn) in [PR 2840](https://github.com/gradio-app/gradio/pull/2840)
* Moved telemetry requests to run on background threads by [@abidlabs](https://github.com/abidlabs) in [PR 3054](https://github.com/gradio-app/gradio/pull/3054)


## Contributors Shoutout:
No changes to highlight.


# Version 3.16.2

## New Features:
No changes to highlight.

## Bug Fixes:
* Fixed file upload fails for files with zero size by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2923](https://github.com/gradio-app/gradio/pull/2923)
* Fixed bug where `mount_gradio_app` would not launch if the queue was enabled in a gradio app by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2939](https://github.com/gradio-app/gradio/pull/2939)
* Fix custom long CSS handling in Blocks by [@anton-l](https://github.com/anton-l) in [PR 2953](https://github.com/gradio-app/gradio/pull/2953)
* Recovers the dropdown change event by [@abidlabs](https://github.com/abidlabs) in [PR 2954](https://github.com/gradio-app/gradio/pull/2954).
* Fix audio file output by [@aliabid94](https://github.com/aliabid94) in [PR 2961](https://github.com/gradio-app/gradio/pull/2961).
* Fixed bug where file extensions of really long files were not kept after download by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2929](https://github.com/gradio-app/gradio/pull/2929)
* Fix bug where outputs for examples where not being returned by the backend by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2955](https://github.com/gradio-app/gradio/pull/2955)
* Fix bug in `blocks_plug` demo that prevented switching tabs programmatically with python [@TashaSkyUp](https://github.com/https://github.com/TashaSkyUp) in [PR 2971](https://github.com/gradio-app/gradio/pull/2971).

## Documentation Changes:
No changes to highlight.

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
No changes to highlight.

## Contributors Shoutout:
No changes to highlight.


# Version 3.16.1

## New Features:

No changes to highlight.

## Bug Fixes:
* Fix audio file output by [@aliabid94](https://github.com/aliabid94) in [PR 2950](https://github.com/gradio-app/gradio/pull/2950).

## Documentation Changes:
No changes to highlight.

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
No changes to highlight.

## Contributors Shoutout:
No changes to highlight.

# Version 3.16.0

## New Features:

### Send custom progress updates by adding a `gr.Progress` argument after the input arguments to any function. Example:

```python
def reverse(word, progress=gr.Progress()):
    progress(0, desc="Starting")
    time.sleep(1)
    new_string = ""
    for letter in progress.tqdm(word, desc="Reversing"):
        time.sleep(0.25)
        new_string = letter + new_string
    return new_string

demo = gr.Interface(reverse, gr.Text(), gr.Text())
```

Progress indicator bar by [@aliabid94](https://github.com/aliabid94) in [PR 2750](https://github.com/gradio-app/gradio/pull/2750).

* Added `title` argument to `TabbedInterface` by @MohamedAliRashad in [#2888](https://github.com/gradio-app/gradio/pull/2888)
* Add support for specifying file extensions for `gr.File` and `gr.UploadButton`, using `file_types` parameter (e.g  `gr.File(file_count="multiple", file_types=["text", ".json", ".csv"])`) by @dawoodkhan82 in [#2901](https://github.com/gradio-app/gradio/pull/2901)
* Added `multiselect` option to `Dropdown` by @dawoodkhan82 in [#2871](https://github.com/gradio-app/gradio/pull/2871)

### With `multiselect` set to `true` a user can now select multiple options from the `gr.Dropdown` component.

```python
gr.Dropdown(["angola", "pakistan", "canada"], multiselect=True, value=["angola"])
```
<img width="610" alt="Screenshot 2023-01-03 at 4 14 36 PM" src="https://user-images.githubusercontent.com/12725292/210442547-c86975c9-4b4f-4b8e-8803-9d96e6a8583a.png">


## Bug Fixes:
* Fixed bug where an error opening an audio file led to a crash by [@FelixDombek](https://github.com/FelixDombek) in [PR 2898](https://github.com/gradio-app/gradio/pull/2898)
* Fixed bug where setting `default_enabled=False` made it so that the entire queue did not start by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2876](https://github.com/gradio-app/gradio/pull/2876)
* Fixed bug where csv preview for DataFrame examples would show filename instead of file contents by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2877](https://github.com/gradio-app/gradio/pull/2877)
* Fixed bug where an error raised after yielding iterative output would not be displayed in the browser by
[@JaySmithWpg](https://github.com/JaySmithWpg) in [PR 2889](https://github.com/gradio-app/gradio/pull/2889)
* Fixed bug in `blocks_style` demo that was preventing it from launching by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2890](https://github.com/gradio-app/gradio/pull/2890)
* Fixed bug where files could not be downloaded by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2926](https://github.com/gradio-app/gradio/pull/2926)
* Fixed bug where cached examples were not displaying properly by [@a-rogalska](https://github.com/a-rogalska) in [PR 2974](https://github.com/gradio-app/gradio/pull/2974)

## Documentation Changes:
* Added a Guide on using Google Sheets to create a real-time dashboard with Gradio's `DataFrame` and `LinePlot` component, by [@abidlabs](https://github.com/abidlabs) in [PR 2816](https://github.com/gradio-app/gradio/pull/2816)
* Add a components - events matrix on the docs by [@aliabd](https://github.com/aliabd) in [PR 2921](https://github.com/gradio-app/gradio/pull/2921)

## Testing and Infrastructure Changes:
* Deployed PRs from forks to spaces by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2895](https://github.com/gradio-app/gradio/pull/2895)

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* The `default_enabled` parameter of the `Blocks.queue` method has no effect by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2876](https://github.com/gradio-app/gradio/pull/2876)
* Added typing to several Python files in codebase by [@abidlabs](https://github.com/abidlabs) in [PR 2887](https://github.com/gradio-app/gradio/pull/2887)
* Excluding untracked files from demo notebook check action by [@aliabd](https://github.com/aliabd) in [PR 2897](https://github.com/gradio-app/gradio/pull/2897)
* Optimize images and gifs by [@aliabd](https://github.com/aliabd) in [PR 2922](https://github.com/gradio-app/gradio/pull/2922)
* Updated typing by [@1nF0rmed](https://github.com/1nF0rmed) in [PR 2904](https://github.com/gradio-app/gradio/pull/2904)

## Contributors Shoutout:
* @JaySmithWpg for making their first contribution to gradio!
* @MohamedAliRashad for making their first contribution to gradio!

# Version 3.15.0

## New Features:

Gradio's newest plotting component `gr.LinePlot`! 📈

With this component you can easily create time series visualizations with customizable
appearance for your demos and dashboards ... all without having to know an external plotting library.

For an example of the api see below:

```python
gr.LinePlot(stocks,
            x="date",
            y="price",
            color="symbol",
            color_legend_position="bottom",
            width=600, height=400, title="Stock Prices")
```
![image](https://user-images.githubusercontent.com/41651716/208711646-81ae3745-149b-46a3-babd-0569aecdd409.png)


By [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2807](https://github.com/gradio-app/gradio/pull/2807)

## Bug Fixes:
* Fixed bug where the `examples_per_page` parameter of the `Examples` component was not passed to the internal `Dataset` component by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2861](https://github.com/gradio-app/gradio/pull/2861)
* Fixes loading Spaces that have components with default values by [@abidlabs](https://github.com/abidlabs) in [PR 2855](https://github.com/gradio-app/gradio/pull/2855)
* Fixes flagging when `allow_flagging="auto"` in `gr.Interface()` by [@abidlabs](https://github.com/abidlabs) in [PR 2695](https://github.com/gradio-app/gradio/pull/2695)
* Fixed bug where passing a non-list value to `gr.CheckboxGroup` would crash the entire app by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2866](https://github.com/gradio-app/gradio/pull/2866)

## Documentation Changes:
* Added a Guide on using BigQuery with Gradio's `DataFrame` and `ScatterPlot` component,
by [@abidlabs](https://github.com/abidlabs) in [PR 2794](https://github.com/gradio-app/gradio/pull/2794)

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Fixed importing gradio can cause PIL.Image.registered_extensions() to break by `[@aliencaocao](https://github.com/aliencaocao)` in `[PR 2846](https://github.com/gradio-app/gradio/pull/2846)`
* Fix css glitch and navigation in docs by [@aliabd](https://github.com/aliabd) in [PR 2856](https://github.com/gradio-app/gradio/pull/2856)
* Added the ability to set `x_lim`, `y_lim` and legend positions for `gr.ScatterPlot` by  [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2807](https://github.com/gradio-app/gradio/pull/2807)
* Remove footers and min-height the correct way by [@aliabd](https://github.com/aliabd) in [PR 2860](https://github.com/gradio-app/gradio/pull/2860)

## Contributors Shoutout:
No changes to highlight.

# Version 3.14.0

## New Features:

### Add Waveform Visual Support to Audio
Adds a `gr.make_waveform()` function that creates a waveform video by combining an audio and an optional background image by [@dawoodkhan82](http://github.com/dawoodkhan82) and [@aliabid94](http://github.com/aliabid94) in [PR 2706](https://github.com/gradio-app/gradio/pull/2706. Helpful for making audio outputs much more shareable.

![waveform screenrecording](https://user-images.githubusercontent.com/7870876/206062396-164a5e71-451a-4fe0-94a7-cbe9269d57e6.gif)

### Allows Every Component to Accept an `every` Parameter

When a component's initial value is a function, the `every` parameter re-runs the function every `every` seconds. By [@abidlabs](https://github.com/abidlabs) in [PR 2806](https://github.com/gradio-app/gradio/pull/2806). Here's a code example:

```py
import gradio as gr

with gr.Blocks() as demo:
    df = gr.DataFrame(run_query, every=60*60)

demo.queue().launch()
```

## Bug Fixes:
* Fixed issue where too many temporary files were created, all with randomly generated
filepaths. Now fewer temporary files are created and are assigned a path that is a
hash based on the file contents by [@abidlabs](https://github.com/abidlabs) in [PR 2758](https://github.com/gradio-app/gradio/pull/2758)

## Documentation Changes:
No changes to highlight.

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
No changes to highlight.

## Contributors Shoutout:
No changes to highlight.


# Version 3.13.2

## New Features:
No changes to highlight.

## Bug Fixes:
*No changes to highlight.
*
## Documentation Changes:
* Improves documentation of several queuing-related parameters by [@abidlabs](https://github.com/abidlabs) in [PR 2825](https://github.com/gradio-app/gradio/pull/2825)

## Testing and Infrastructure Changes:
* Remove h11 pinning by [@ecederstrand]([https://github.com/abidlabs](https://github.com/ecederstrand)) in [PR 2820]([https://github.com/gradio-app/gradio/pull/2808](https://github.com/gradio-app/gradio/pull/2820))

## Breaking Changes:
No changes to highlight.

## Full Changelog:
No changes to highlight.

## Contributors Shoutout:
No changes to highlight.

# Version 3.13.1

## New Features:

### New Shareable Links

Replaces tunneling logic based on ssh port-forwarding to that based on `frp` by [XciD](https://github.com/XciD) and [Wauplin](https://github.com/Wauplin) in [PR 2509](https://github.com/gradio-app/gradio/pull/2509)

You don't need to do anything differently, but when you set `share=True` in `launch()`,
you'll get this message and a public link that look a little bit different:

```bash
Setting up a public link... we have recently upgraded the way public links are generated. If you encounter any problems, please downgrade to gradio version 3.13.0
.
Running on public URL: https://bec81a83-5b5c-471e.gradio.live
```

These links are a more secure and scalable way to create shareable demos!

## Bug Fixes:
* Allows `gr.Dataframe()` to take a `pandas.DataFrame` that includes numpy array and other types as its initial value, by [@abidlabs](https://github.com/abidlabs) in [PR 2804](https://github.com/gradio-app/gradio/pull/2804)
* Add `altair` to requirements.txt by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2811](https://github.com/gradio-app/gradio/pull/2811)
* Added aria-labels to icon buttons that are built into UI components by [@emilyuhde](http://github.com/emilyuhde) in [PR 2791](https://github.com/gradio-app/gradio/pull/2791)

## Documentation Changes:
* Fixed some typos in the "Plot Component for Maps" guide by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2811](https://github.com/gradio-app/gradio/pull/2811)

## Testing and Infrastructure Changes:
* Fixed test for IP address by [@abidlabs](https://github.com/abidlabs) in [PR 2808](https://github.com/gradio-app/gradio/pull/2808)

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Fixed typo in parameter `visible` in classes in `templates.py` by [@abidlabs](https://github.com/abidlabs) in [PR 2805](https://github.com/gradio-app/gradio/pull/2805)
* Switched external service for getting IP address from `https://api.ipify.org` to `https://checkip.amazonaws.com/` by [@abidlabs](https://github.com/abidlabs) in [PR 2810](https://github.com/gradio-app/gradio/pull/2810)

## Contributors Shoutout:
No changes to highlight.

* Fixed typo in parameter `visible` in classes in `templates.py` by [@abidlabs](https://github.com/abidlabs) in [PR 2805](https://github.com/gradio-app/gradio/pull/2805)
* Switched external service for getting IP address from `https://api.ipify.org` to `https://checkip.amazonaws.com/` by [@abidlabs](https://github.com/abidlabs) in [PR 2810](https://github.com/gradio-app/gradio/pull/2810)


# Version 3.13.0

## New Features:

### Scatter plot component

It is now possible to create a scatter plot natively in Gradio!

The `gr.ScatterPlot` component accepts a pandas dataframe and some optional configuration parameters
and will automatically create a plot for you!

This is the first of many native plotting components in Gradio!

For an example of how to use `gr.ScatterPlot` see below:

```python
import gradio as gr
from vega_datasets import data

cars = data.cars()

with gr.Blocks() as demo:
    gr.ScatterPlot(show_label=False,
                   value=cars,
                   x="Horsepower",
                   y="Miles_per_Gallon",
                   color="Origin",
                   tooltip="Name",
                   title="Car Data",
                   y_title="Miles per Gallon",
                   color_legend_title="Origin of Car").style(container=False)

demo.launch()
```

<img width="404" alt="image" src="https://user-images.githubusercontent.com/41651716/206737726-4c4da5f0-dee8-4f0a-b1e1-e2b75c4638e9.png">


By [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2764](https://github.com/gradio-app/gradio/pull/2764)


### Support for altair plots

The `Plot` component can now accept altair plots as values!
Simply return an altair plot from your event listener and gradio will display it in the front-end.
See the example below:

```python
import gradio as gr
import altair as alt
from vega_datasets import data

cars = data.cars()
chart = (
    alt.Chart(cars)
    .mark_point()
    .encode(
        x="Horsepower",
        y="Miles_per_Gallon",
        color="Origin",
    )
)

with gr.Blocks() as demo:
    gr.Plot(value=chart)
demo.launch()
```

<img width="1366" alt="image" src="https://user-images.githubusercontent.com/41651716/204660697-f994316f-5ca7-4e8a-93bc-eb5e0d556c91.png">

By [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2741](https://github.com/gradio-app/gradio/pull/2741)

### Set the background color of a Label component

The `Label` component now accepts a `color` argument by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2736](https://github.com/gradio-app/gradio/pull/2736).
The `color` argument should either be a valid css color name or hexadecimal string.
You can update the color with `gr.Label.update`!

This lets you create Alert and Warning boxes with the `Label` component. See below:

```python
import gradio as gr
import random

def update_color(value):
    if value < 0:
        # This is bad so use red
        return "#FF0000"
    elif 0 <= value <= 20:
        # Ok but pay attention (use orange)
        return "#ff9966"
    else:
        # Nothing to worry about
        return None

def update_value():
    choice = random.choice(['good', 'bad', 'so-so'])
    color = update_color(choice)
    return gr.Label.update(value=choice, color=color)


with gr.Blocks() as demo:
    label = gr.Label(value=-10)
    demo.load(lambda: update_value(), inputs=None, outputs=[label], every=1)
demo.queue().launch()
```

![label_bg_color_update](https://user-images.githubusercontent.com/41651716/204400372-80e53857-f26f-4a38-a1ae-1acadff75e89.gif)

### Add Brazilian Portuguese translation

Add Brazilian Portuguese translation (pt-BR.json) by [@pstwh](http://github.com/pstwh) in [PR 2753](https://github.com/gradio-app/gradio/pull/2753):

<img width="951" alt="image" src="https://user-images.githubusercontent.com/1778297/206615305-4c52031e-3f7d-4df2-8805-a79894206911.png">

## Bug Fixes:
* Fixed issue where image thumbnails were not showing when an example directory was provided
by [@abidlabs](https://github.com/abidlabs) in [PR 2745](https://github.com/gradio-app/gradio/pull/2745)
* Fixed bug loading audio input models from the hub by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2779](https://github.com/gradio-app/gradio/pull/2779).
* Fixed issue where entities were not merged when highlighted text was generated from the
dictionary inputs [@payoto](https://github.com/payoto) in [PR 2767](https://github.com/gradio-app/gradio/pull/2767)
* Fixed bug where generating events did not finish running even if the websocket connection was closed by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2783](https://github.com/gradio-app/gradio/pull/2783).

## Documentation Changes:
No changes to highlight.

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Images in the chatbot component are now resized if they exceed a max width by [@abidlabs](https://github.com/abidlabs) in [PR 2748](https://github.com/gradio-app/gradio/pull/2748)
* Missing parameters have been added to `gr.Blocks().load()` by [@abidlabs](https://github.com/abidlabs) in [PR 2755](https://github.com/gradio-app/gradio/pull/2755)
* Deindex share URLs from search by [@aliabd](https://github.com/aliabd) in [PR 2772](https://github.com/gradio-app/gradio/pull/2772)
* Redirect old links and fix broken ones by [@aliabd](https://github.com/aliabd) in [PR 2774](https://github.com/gradio-app/gradio/pull/2774)

## Contributors Shoutout:
No changes to highlight.

# Version 3.12.0

## New Features:

### The `Chatbot` component now supports a subset of Markdown (including bold, italics, code, images)

You can now pass in some Markdown to the Chatbot component and it will show up,
meaning that you can pass in images as well! by [@abidlabs](https://github.com/abidlabs) in [PR 2731](https://github.com/gradio-app/gradio/pull/2731)

Here's a simple example that references a local image `lion.jpg` that is in the same
folder as the Python script:

```py
import gradio as gr

with gr.Blocks() as demo:
    gr.Chatbot([("hi", "hello **abubakar**"), ("![](/file=lion.jpg)", "cool pic")])

demo.launch()
```

![Alt text](https://user-images.githubusercontent.com/1778297/204357455-5c1a4002-eee7-479d-9a1e-ba2c12522723.png)

To see a more realistic example, see the new demo `/demo/chatbot_multimodal/run.py`.


### Latex support
Added mathtext (a subset of latex) support to gr.Markdown. Added by [@kashif](https://github.com/kashif) and [@aliabid94](https://github.com/aliabid94) in [PR 2696](https://github.com/gradio-app/gradio/pull/2696).

Example of how it can be used:

```python
gr.Markdown(
    r"""
    # Hello World! $\frac{\sqrt{x + y}}{4}$ is today's lesson.
    """)
```

### Update Accordion properties from the backend

You can now update the Accordion `label` and `open` status with `gr.Accordion.update` by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2690](https://github.com/gradio-app/gradio/pull/2690)

```python
import gradio as gr

with gr.Blocks() as demo:
    with gr.Accordion(label="Open for greeting", open=False) as accordion:
        gr.Textbox("Hello!")
    open_btn = gr.Button(value="Open Accordion")
    close_btn = gr.Button(value="Close Accordion")
    open_btn.click(
        lambda: gr.Accordion.update(open=True, label="Open Accordion"),
        inputs=None,
        outputs=[accordion],
    )
    close_btn.click(
        lambda: gr.Accordion.update(open=False, label="Closed Accordion"),
        inputs=None,
        outputs=[accordion],
    )
demo.launch()
```

![update_accordion](https://user-images.githubusercontent.com/41651716/203164176-b102eae3-babe-4986-ae30-3ab4f400cedc.gif)

## Bug Fixes:
* Fixed bug where requests timeout is missing from utils.version_check() by [@yujiehecs](https://github.com/yujiehecs) in [PR 2729](https://github.com/gradio-app/gradio/pull/2729)
* Fixed bug where so that the `File` component can properly preprocess files to "binary" byte-string format by [CoffeeVampir3](https://github.com/CoffeeVampir3) in [PR 2727](https://github.com/gradio-app/gradio/pull/2727)
* Fixed bug to ensure that filenames are less than 200 characters even for non-English languages by [@SkyTNT](https://github.com/SkyTNT) in [PR 2685](https://github.com/gradio-app/gradio/pull/2685)

## Documentation Changes:
* Performance improvements to docs on mobile by  [@aliabd](https://github.com/aliabd) in [PR 2730](https://github.com/gradio-app/gradio/pull/2730)

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Make try examples button more prominent by [@aliabd](https://github.com/aliabd) in [PR 2705](https://github.com/gradio-app/gradio/pull/2705)
* Fix id clashes in docs by [@aliabd](https://github.com/aliabd) in [PR 2713](https://github.com/gradio-app/gradio/pull/2713)
* Fix typos in guide docs by [@andridns](https://github.com/andridns) in [PR 2722](https://github.com/gradio-app/gradio/pull/2722)
* Add option to `include_audio` in Video component. When `True`, for `source="webcam"` this will record audio and video, for `source="upload"` this will retain  the audio in an uploaded video by [@mandargogate](https://github.com/MandarGogate) in [PR 2721](https://github.com/gradio-app/gradio/pull/2721)

## Contributors Shoutout:
* [@andridns](https://github.com/andridns) made their first contribution in [PR 2722](https://github.com/gradio-app/gradio/pull/2722)!


# Version 3.11.0

## New Features:

### Upload Button
There is now a new component called the `UploadButton` which is a file upload component but in button form! You can also specify what file types it should accept in the form of a list (ex: `image`, `video`, `audio`, `text`, or generic `file`). Added by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2591](https://github.com/gradio-app/gradio/pull/2591).

Example of how it can be used:

```python
import gradio as gr

def upload_file(files):
    file_paths = [file.name for file in files]
    return file_paths

with gr.Blocks() as demo:
    file_output = gr.File()
    upload_button = gr.UploadButton("Click to Upload a File", file_types=["image", "video"], file_count="multiple")
    upload_button.upload(upload_file, upload_button, file_output)

demo.launch()
```
### Revamped API documentation page

New API Docs page with in-browser playground and updated aesthetics. [@gary149](https://github.com/gary149) in [PR 2652](https://github.com/gradio-app/gradio/pull/2652)

### Revamped Login page

Previously our login page had its own CSS, had no dark mode, and had an ugly json message on the wrong credentials. Made the page more aesthetically consistent, added dark mode support, and a nicer error message. [@aliabid94](https://github.com/aliabid94) in [PR 2684](https://github.com/gradio-app/gradio/pull/2684)

### Accessing the Requests Object Directly

You can now access the Request object directly in your Python function by [@abidlabs](https://github.com/abidlabs) in [PR 2641](https://github.com/gradio-app/gradio/pull/2641). This means that you can access request headers, the client IP address, and so on. In order to use it, add a parameter to your function and set its type hint to be `gr.Request`. Here's a simple example:

```py
import gradio as gr

def echo(name, request: gr.Request):
    if request:
        print("Request headers dictionary:", request.headers)
        print("IP address:", request.client.host)
    return name

io = gr.Interface(echo, "textbox", "textbox").launch()
```

## Bug Fixes:
* Fixed bug that limited files from being sent over websockets to 16MB. The new limit
is now 1GB  by [@abidlabs](https://github.com/abidlabs) in [PR 2709](https://github.com/gradio-app/gradio/pull/2709)

## Documentation Changes:
* Updated documentation for embedding Gradio demos on Spaces as web components by
[@julien-c](https://github.com/julien-c) in [PR 2698](https://github.com/gradio-app/gradio/pull/2698)
* Updated IFrames in Guides to use the host URL instead of the Space name to be consistent with the new method for embedding Spaces, by
[@julien-c](https://github.com/julien-c) in [PR 2692](https://github.com/gradio-app/gradio/pull/2692)
 * Colab buttons on every demo in the website! Just click open in colab, and run the demo there.



https://user-images.githubusercontent.com/9021060/202878400-cb16ed47-f4dd-4cb0-b2f0-102a9ff64135.mov

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Better warnings and error messages for `gr.Interface.load()` by [@abidlabs](https://github.com/abidlabs) in [PR 2694](https://github.com/gradio-app/gradio/pull/2694)
* Add open in colab buttons to demos in docs and /demos by [@aliabd](https://github.com/aliabd) in [PR 2608](https://github.com/gradio-app/gradio/pull/2608)
* Apply different formatting for the types in component docstrings by [@aliabd](https://github.com/aliabd) in [PR 2707](https://github.com/gradio-app/gradio/pull/2707)

## Contributors Shoutout:
No changes to highlight.

# Version 3.10.1

## New Features:
No changes to highlight.

## Bug Fixes:
* Passes kwargs into `gr.Interface.load()` by [@abidlabs](https://github.com/abidlabs) in [PR 2669](https://github.com/gradio-app/gradio/pull/2669)

## Documentation Changes:
No changes to highlight.

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Clean up printed statements in Embedded Colab Mode by [@aliabid94](https://github.com/aliabid94) in [PR 2612](https://github.com/gradio-app/gradio/pull/2612)

## Contributors Shoutout:
No changes to highlight.


# Version 3.10.0

* Add support for `'password'` and `'email'` types to `Textbox`. [@pngwn](https://github.com/pngwn) in [PR 2653](https://github.com/gradio-app/gradio/pull/2653)
* `gr.Textbox` component will now raise an exception if `type` is not "text", "email", or "password" [@pngwn](https://github.com/pngwn) in [PR 2653](https://github.com/gradio-app/gradio/pull/2653). This will cause demos using the deprecated `gr.Textbox(type="number")` to raise an exception.

## Bug Fixes:
* Updated the minimum FastApi used in tests to version 0.87 by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2647](https://github.com/gradio-app/gradio/pull/2647)
* Fixed bug where interfaces with examples could not be loaded with `gr.Interface.load` by [@freddyaboulton](https://github.com/freddyaboulton) [PR 2640](https://github.com/gradio-app/gradio/pull/2640)
* Fixed bug where the `interactive` property of a component could not be updated by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2639](https://github.com/gradio-app/gradio/pull/2639)
* Fixed bug where some URLs were not being recognized as valid URLs and thus were not
loading correctly in various components by [@abidlabs](https://github.com/abidlabs) in [PR 2659](https://github.com/gradio-app/gradio/pull/2659)


## Documentation Changes:
* Fix some typos in the embedded demo names in "05_using_blocks_like_functions.md" by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2656](https://github.com/gradio-app/gradio/pull/2656)

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Add support for `'password'` and `'email'` types to `Textbox`. [@pngwn](https://github.com/pngwn) in [PR 2653](https://github.com/gradio-app/gradio/pull/2653)

## Contributors Shoutout:
No changes to highlight.


# Version 3.9.1

## New Features:
No changes to highlight.

## Bug Fixes:
* Only set a min height on md and html when loading by [@pngwn](https://github.com/pngwn) in [PR 2623](https://github.com/gradio-app/gradio/pull/2623)

## Documentation Changes:
* See docs for the latest gradio commit to main as well the latest pip release:

![main-vs-pip](https://user-images.githubusercontent.com/9021060/199607887-aab1ae4e-a070-4527-966d-024397abe15b.gif)

* Modified the "Connecting To a Database Guide" to use `pd.read_sql` as opposed to low-level postgres connector by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2604](https://github.com/gradio-app/gradio/pull/2604)

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Dropdown for seeing docs as latest or main by [@aliabd](https://github.com/aliabd) in [PR 2544](https://github.com/gradio-app/gradio/pull/2544)
* Allow `gr.Templates` to accept parameters to override the defaults by [@abidlabs](https://github.com/abidlabs) in [PR 2600](https://github.com/gradio-app/gradio/pull/2600)
* Components now throw a `ValueError()` if constructed with invalid parameters for `type` or `source` (for components that take those parameters) in [PR 2610](https://github.com/gradio-app/gradio/pull/2610)
* Allow auth with using queue by [@GLGDLY](https://github.com/GLGDLY) in [PR 2611](https://github.com/gradio-app/gradio/pull/2611)

## Contributors Shoutout:
No changes to highlight.


# Version 3.9

## New Features:
* Gradio is now embedded directly in colab without requiring the share link by [@aliabid94](https://github.com/aliabid94) in [PR 2455](https://github.com/gradio-app/gradio/pull/2455)

### Calling functions by api_name in loaded apps

When you load an upstream app with `gr.Blocks.load`, you can now specify which fn
to call with the `api_name` parameter.

```python
import gradio as gr
english_translator = gr.Blocks.load(name="spaces/gradio/english-translator")
german = english_translator("My name is Freddy", api_name='translate-to-german')
```

The `api_name` parameter will take precendence over the `fn_index` parameter.

## Bug Fixes:
* Fixed bug where None could not be used for File,Model3D, and Audio examples by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2588](https://github.com/gradio-app/gradio/pull/2588)
* Fixed links in Plotly map guide + demo by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2578](https://github.com/gradio-app/gradio/pull/2578)
* `gr.Blocks.load()` now correctly loads example files from Spaces [@abidlabs](https://github.com/abidlabs) in [PR 2594](https://github.com/gradio-app/gradio/pull/2594)
* Fixed bug when image clear started upload dialog [@mezotaken](https://github.com/mezotaken) in [PR 2577](https://github.com/gradio-app/gradio/pull/2577)

## Documentation Changes:
* Added a Guide on how to configure the queue for maximum performance by [@abidlabs](https://github.com/abidlabs) in [PR 2558](https://github.com/gradio-app/gradio/pull/2558)


## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Add `api_name` to `Blocks.__call__` by  [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2593](https://github.com/gradio-app/gradio/pull/2593)
* Update queue with using deque & update requirements by [@GLGDLY](https://github.com/GLGDLY) in [PR 2428](https://github.com/gradio-app/gradio/pull/2428)


## Contributors Shoutout:
No changes to highlight.


# Version 3.8.2

## Bug Fixes:

* Ensure gradio apps embedded via spaces use the correct endpoint for predictions. [@pngwn](https://github.com/pngwn) in [PR 2567](https://github.com/gradio-app/gradio/pull/2567)
* Ensure gradio apps embedded via spaces use the correct websocket protocol. [@pngwn](https://github.com/pngwn) in [PR 2571](https://github.com/gradio-app/gradio/pull/2571)

## New Features:

### Running Events Continuously
Gradio now supports the ability to run an event continuously on a fixed schedule. To use this feature,
pass `every=# of seconds` to the event definition. This will run the event every given number of seconds!

This can be used to:
* Create live visualizations that show the most up to date data
* Refresh the state of the frontend automatically in response to changes in the backend

Here is an example of a live plot that refreshes every half second:
```python
import math
import gradio as gr
import plotly.express as px
import numpy as np


plot_end = 2 * math.pi


def get_plot(period=1):
    global plot_end
    x = np.arange(plot_end - 2 * math.pi, plot_end, 0.02)
    y = np.sin(2*math.pi*period * x)
    fig = px.line(x=x, y=y)
    plot_end += 2 * math.pi
    return fig


with gr.Blocks() as demo:
    with gr.Row():
        with gr.Column():
            gr.Markdown("Change the value of the slider to automatically update the plot")
            period = gr.Slider(label="Period of plot", value=1, minimum=0, maximum=10, step=1)
            plot = gr.Plot(label="Plot (updates every half second)")

    dep = demo.load(get_plot, None, plot, every=0.5)
    period.change(get_plot, period, plot, every=0.5, cancels=[dep])

demo.queue().launch()
```

![live_demo](https://user-images.githubusercontent.com/41651716/198357377-633ce460-4e31-47bd-8202-1440cdd6fe19.gif)


## Bug Fixes:
No changes to highlight.

## Documentation Changes:
* Explained how to set up `queue` and `auth` when working with reload mode by by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 3089](https://github.com/gradio-app/gradio/pull/3089) 

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Allows loading private Spaces by passing an an `api_key` to `gr.Interface.load()`
by [@abidlabs](https://github.com/abidlabs) in [PR 2568](https://github.com/gradio-app/gradio/pull/2568)

## Contributors Shoutout:
No changes to highlight.


# Version 3.8

## New Features:
* Allows event listeners to accept a single dictionary as its argument, where the keys are the components and the values are the component values. This is set by passing the input components in the event listener as a set instead of a list. [@aliabid94](https://github.com/aliabid94) in [PR 2550](https://github.com/gradio-app/gradio/pull/2550)

## Bug Fixes:
* Fix whitespace issue when using plotly. [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2548](https://github.com/gradio-app/gradio/pull/2548)
* Apply appropriate alt text to all gallery images. [@camenduru](https://github.com/camenduru) in [PR 2358](https://github.com/gradio-app/gradio/pull/2538)
* Removed erroneous tkinter import in gradio.blocks by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2555](https://github.com/gradio-app/gradio/pull/2555)

## Documentation Changes:
No changes to highlight.

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Added the `every` keyword to event listeners that runs events on a fixed schedule by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2512](https://github.com/gradio-app/gradio/pull/2512)
* Fix whitespace issue when using plotly. [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2548](https://github.com/gradio-app/gradio/pull/2548)
* Apply appropriate alt text to all gallery images. [@camenduru](https://github.com/camenduru) in [PR 2358](https://github.com/gradio-app/gradio/pull/2538)

## Contributors Shoutout:
No changes to highlight.


# Version 3.7

## New Features:

### Batched Functions

Gradio now supports the ability to pass *batched* functions. Batched functions are just
functions which take in a list of inputs and return a list of predictions.

For example, here is a batched function that takes in two lists of inputs (a list of
words and a list of ints), and returns a list of trimmed words as output:

```py
import time

def trim_words(words, lens):
    trimmed_words = []
    time.sleep(5)
    for w, l in zip(words, lens):
        trimmed_words.append(w[:l])
    return [trimmed_words]
```

The advantage of using batched functions is that if you enable queuing, the Gradio
server can automatically *batch* incoming requests and process them in parallel,
potentially speeding up your demo. Here's what the Gradio code looks like (notice
the `batch=True` and `max_batch_size=16` -- both of these parameters can be passed
into event triggers or into the `Interface` class)

```py
import gradio as gr

with gr.Blocks() as demo:
    with gr.Row():
        word = gr.Textbox(label="word", value="abc")
        leng = gr.Number(label="leng", precision=0, value=1)
        output = gr.Textbox(label="Output")
    with gr.Row():
        run = gr.Button()

    event = run.click(trim_words, [word, leng], output, batch=True, max_batch_size=16)

demo.queue()
demo.launch()
```

In the example above, 16 requests could be processed in parallel (for a total inference
time of 5 seconds), instead of each request being processed separately (for a total
inference time of 80 seconds).

### Upload Event

`Video`, `Audio`, `Image`, and `File` components now support a `upload()` event that is triggered when a user uploads a file into any of these components.

Example usage:

```py
import gradio as gr

with gr.Blocks() as demo:
    with gr.Row():
        input_video = gr.Video()
        output_video = gr.Video()

     # Clears the output video when an input video is uploaded
    input_video.upload(lambda : None, None, output_video)
```


## Bug Fixes:
* Fixes issue where plotly animations, interactivity, titles, legends, were not working properly. [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2486](https://github.com/gradio-app/gradio/pull/2486)
* Prevent requests to the `/api` endpoint from skipping the queue if the queue is enabled for that event by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2493](https://github.com/gradio-app/gradio/pull/2493)
* Fixes a bug with `cancels` in event triggers so that it works properly if multiple
Blocks are rendered by [@abidlabs](https://github.com/abidlabs) in [PR 2530](https://github.com/gradio-app/gradio/pull/2530)
* Prevent invalid targets of events from crashing the whole application. [@pngwn](https://github.com/pngwn) in [PR 2534](https://github.com/gradio-app/gradio/pull/2534)
* Properly dequeue cancelled events when multiple apps are rendered by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2540](https://github.com/gradio-app/gradio/pull/2540)

## Documentation Changes:
* Added an example interactive dashboard to the "Tabular & Plots" section of the Demos page by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2508](https://github.com/gradio-app/gradio/pull/2508)

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Fixes the error message if a user builds Gradio locally and tries to use `share=True` by [@abidlabs](https://github.com/abidlabs) in [PR 2502](https://github.com/gradio-app/gradio/pull/2502)
* Allows the render() function to return self by [@Raul9595](https://github.com/Raul9595) in [PR 2514](https://github.com/gradio-app/gradio/pull/2514)
* Fixes issue where plotly animations, interactivity, titles, legends, were not working properly. [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2486](https://github.com/gradio-app/gradio/pull/2486)
* Gradio now supports batched functions by [@abidlabs](https://github.com/abidlabs) in [PR 2218](https://github.com/gradio-app/gradio/pull/2218)
* Add `upload` event for `Video`, `Audio`, `Image`, and `File` components [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2448](https://github.com/gradio-app/gradio/pull/2456)
* Changes websocket path for Spaces as it is no longer necessary to have a different URL for websocket connections on Spaces by [@abidlabs](https://github.com/abidlabs) in [PR 2528](https://github.com/gradio-app/gradio/pull/2528)
* Clearer error message when events are defined outside of a Blocks scope, and a warning if you
try to use `Series` or `Parallel` with `Blocks` by [@abidlabs](https://github.com/abidlabs) in [PR 2543](https://github.com/gradio-app/gradio/pull/2543)
* Adds support for audio samples that are in `float64`, `float16`, or `uint16` formats by [@abidlabs](https://github.com/abidlabs) in [PR 2545](https://github.com/gradio-app/gradio/pull/2545)

## Contributors Shoutout:
No changes to highlight.


# Version 3.6

## New Features:

### Cancelling Running Events
Running events can be cancelled when other events are triggered! To test this feature, pass the `cancels` parameter to the event listener.
For this feature to work, the queue must be enabled.

![cancel_on_change_rl](https://user-images.githubusercontent.com/41651716/195952623-61a606bd-e82b-4e1a-802e-223154cb8727.gif)

Code:
```python
import time
import gradio as gr

def fake_diffusion(steps):
    for i in range(steps):
        time.sleep(1)
        yield str(i)

def long_prediction(*args, **kwargs):
    time.sleep(10)
    return 42


with gr.Blocks() as demo:
    with gr.Row():
        with gr.Column():
            n = gr.Slider(1, 10, value=9, step=1, label="Number Steps")
            run = gr.Button()
            output = gr.Textbox(label="Iterative Output")
            stop = gr.Button(value="Stop Iterating")
        with gr.Column():
            prediction = gr.Number(label="Expensive Calculation")
            run_pred = gr.Button(value="Run Expensive Calculation")
        with gr.Column():
            cancel_on_change = gr.Textbox(label="Cancel Iteration and Expensive Calculation on Change")

    click_event = run.click(fake_diffusion, n, output)
    stop.click(fn=None, inputs=None, outputs=None, cancels=[click_event])
    pred_event = run_pred.click(fn=long_prediction, inputs=None, outputs=prediction)

    cancel_on_change.change(None, None, None, cancels=[click_event, pred_event])


demo.queue(concurrency_count=1, max_size=20).launch()
```

For interfaces, a stop button will be added automatically if the function uses a `yield` statement.

```python
import gradio as gr
import time

def iteration(steps):
    for i in range(steps):
       time.sleep(0.5)
       yield i

gr.Interface(iteration,
             inputs=gr.Slider(minimum=1, maximum=10, step=1, value=5),
             outputs=gr.Number()).queue().launch()
```

![stop_interface_rl](https://user-images.githubusercontent.com/41651716/195952883-e7ca4235-aae3-4852-8f28-96d01d0c5822.gif)


## Bug Fixes:
* Add loading status tracker UI to HTML and Markdown components. [@pngwn](https://github.com/pngwn) in [PR 2474](https://github.com/gradio-app/gradio/pull/2474)
* Fixed videos being mirrored in the front-end if source is not webcam by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2475](https://github.com/gradio-app/gradio/pull/2475)
* Add clear button for timeseries component [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2487](https://github.com/gradio-app/gradio/pull/2487)
* Removes special characters from temporary filenames so that the files can be served by components [@abidlabs](https://github.com/abidlabs) in [PR 2480](https://github.com/gradio-app/gradio/pull/2480)
* Fixed infinite reload loop when mounting gradio as a sub application by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2477](https://github.com/gradio-app/gradio/pull/2477)

## Documentation Changes:
* Adds a demo to show how a sound alert can be played upon completion of a prediction by [@abidlabs](https://github.com/abidlabs) in [PR 2478](https://github.com/gradio-app/gradio/pull/2478)

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:
* Enable running events to be cancelled from other events by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2433](https://github.com/gradio-app/gradio/pull/2433)
* Small fix for version check before reuploading demos by [@aliabd](https://github.com/aliabd) in [PR 2469](https://github.com/gradio-app/gradio/pull/2469)
* Add loading status tracker UI to HTML and Markdown components. [@pngwn](https://github.com/pngwn) in [PR 2400](https://github.com/gradio-app/gradio/pull/2474)
* Add clear button for timeseries component [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2487](https://github.com/gradio-app/gradio/pull/2487)

## Contributors Shoutout:
No changes to highlight.


# Version 3.5

## Bug Fixes:

* Ensure that Gradio does not take control of the HTML page title when embedding a gradio app as a web component, this behaviour flipped by adding `control_page_title="true"` to the webcomponent. [@pngwn](https://github.com/pngwn) in [PR 2400](https://github.com/gradio-app/gradio/pull/2400)
* Decreased latency in iterative-output demos by making the iteration asynchronous [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2409](https://github.com/gradio-app/gradio/pull/2409)
* Fixed queue getting stuck under very high load by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2374](https://github.com/gradio-app/gradio/pull/2374)
* Ensure that components always behave as if `interactive=True` were set when the following conditions are true:
  - no default value is provided,
  - they are not set as the input or output of an event,
  - `interactive` kwarg is not set.

  [@pngwn](https://github.com/pngwn) in [PR 2459](https://github.com/gradio-app/gradio/pull/2459)

## New Features:

* When an `Image` component is set to `source="upload"`, it is now possible to drag and drop and image to replace a previously uploaded image by [@pngwn](https://github.com/pngwn) in [PR 1711](https://github.com/gradio-app/gradio/issues/1711)
* The `gr.Dataset` component now accepts `HTML` and `Markdown` components by [@abidlabs](https://github.com/abidlabs) in [PR 2437](https://github.com/gradio-app/gradio/pull/2437)


## Documentation Changes:
* Improved documentation for the `gr.Dataset` component by [@abidlabs](https://github.com/abidlabs) in [PR 2437](https://github.com/gradio-app/gradio/pull/2437)

## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
* The `Carousel` component is officially deprecated. Since gradio 3.0, code containing the `Carousel` component would throw warnings. As of the next release, the `Carousel` component will raise an exception.

## Full Changelog:
* Speeds up Gallery component by using temporary files instead of base64 representation in the front-end by [@proxyphi](https://github.com/proxyphi), [@pngwn](https://github.com/pngwn), and [@abidlabs](https://github.com/abidlabs) in [PR 2265](https://github.com/gradio-app/gradio/pull/2265)
* Fixed some embedded demos in the guides by not loading the gradio web component in some guides by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2403](https://github.com/gradio-app/gradio/pull/2403)
* When an `Image` component is set to `source="upload"`, it is now possible to drag and drop and image to replace a previously uploaded image by [@pngwn](https://github.com/pngwn) in [PR 2400](https://github.com/gradio-app/gradio/pull/2410)
* Improve documentation of the `Blocks.load()` event by [@abidlabs](https://github.com/abidlabs) in [PR 2413](https://github.com/gradio-app/gradio/pull/2413)
* Decreased latency in iterative-output demos by making the iteration asynchronous [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2409](https://github.com/gradio-app/gradio/pull/2409)
* Updated share link message to reference new Spaces Hardware [@abidlabs](https://github.com/abidlabs) in [PR 2423](https://github.com/gradio-app/gradio/pull/2423)
* Automatically restart spaces if they're down by [@aliabd](https://github.com/aliabd) in [PR 2405](https://github.com/gradio-app/gradio/pull/2405)
* Carousel component is now deprecated by [@abidlabs](https://github.com/abidlabs) in [PR 2434](https://github.com/gradio-app/gradio/pull/2434)
* Build Gradio from source in ui tests by by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2440](https://github.com/gradio-app/gradio/pull/2440)
* Change "return ValueError" to "raise ValueError" by [@vzakharov](https://github.com/vzakharov) in [PR 2445](https://github.com/gradio-app/gradio/pull/2445)
* Add guide on creating a map demo using the `gr.Plot()` component [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2402](https://github.com/gradio-app/gradio/pull/2402)
* Add blur event for `Textbox` and `Number` components [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2448](https://github.com/gradio-app/gradio/pull/2448)
* Stops a gradio launch from hogging a port even after it's been killed [@aliabid94](https://github.com/aliabid94) in [PR 2453](https://github.com/gradio-app/gradio/pull/2453)
* Fix embedded interfaces on touch screen devices by [@aliabd](https://github.com/aliabd) in [PR 2457](https://github.com/gradio-app/gradio/pull/2457)
* Upload all demos to spaces by [@aliabd](https://github.com/aliabd) in [PR 2281](https://github.com/gradio-app/gradio/pull/2281)

## Contributors Shoutout:
No changes to highlight.


# Version 3.4.1

## New Features:

### 1. See Past and Upcoming Changes in the Release History 👀

You can now see gradio's release history directly on the website, and also keep track of upcoming changes. Just go [here](https://gradio.app/changelog/).

![release-history](https://user-images.githubusercontent.com/9021060/193145458-3de699f7-7620-45de-aa73-a1c1b9b96257.gif)

## Bug Fixes:

1. Fix typo in guide image path by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2357](https://github.com/gradio-app/gradio/pull/2357)
2. Raise error if Blocks has duplicate component with same IDs by [@abidlabs](https://github.com/abidlabs) in [PR 2359](https://github.com/gradio-app/gradio/pull/2359)
3. Catch the permission exception on the audio component by [@Ian-GL](https://github.com/Ian-GL) in [PR 2330](https://github.com/gradio-app/gradio/pull/2330)
4. Fix image_classifier_interface_load demo by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2365](https://github.com/gradio-app/gradio/pull/2365)
5. Fix combining adjacent components without gaps by introducing `gr.Row(variant="compact")` by [@aliabid94](https://github.com/aliabid94) in [PR 2291](https://github.com/gradio-app/gradio/pull/2291) This comes with deprecation of the following arguments for `Component.style`: `round`, `margin`, `border`.
6. Fix audio streaming, which was previously choppy in [PR 2351](https://github.com/gradio-app/gradio/pull/2351). Big thanks to [@yannickfunk](https://github.com/yannickfunk) for the proposed solution.
7. Fix bug where new typeable slider doesn't respect the minimum and maximum values [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2380](https://github.com/gradio-app/gradio/pull/2380)


## Documentation Changes:

1. New Guide: Connecting to a Database 🗄️

    A new guide by [@freddyaboulton](https://github.com/freddyaboulton) that explains how you can use Gradio to connect your app to a database. Read more [here](https://gradio.app/connecting_to_a_database/).

2. New Guide: Running Background Tasks 🥷

    A new guide by [@freddyaboulton](https://github.com/freddyaboulton) that explains how you can run background tasks from your gradio app. Read more [here](https://gradio.app/running_background_tasks/).

3. Small fixes to docs for `Image` component by [@abidlabs](https://github.com/abidlabs) in [PR 2372](https://github.com/gradio-app/gradio/pull/2372)


## Testing and Infrastructure Changes:
No changes to highlight.

## Breaking Changes:
No changes to highlight.

## Full Changelog:

* Create a guide on how to connect an app to a database hosted on the cloud by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2341](https://github.com/gradio-app/gradio/pull/2341)
* Removes `analytics` dependency by [@abidlabs](https://github.com/abidlabs) in [PR 2347](https://github.com/gradio-app/gradio/pull/2347)
* Add guide on launching background tasks from your app by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2350](https://github.com/gradio-app/gradio/pull/2350)
* Fix typo in guide image path by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2357](https://github.com/gradio-app/gradio/pull/2357)
* Raise error if Blocks has duplicate component with same IDs by [@abidlabs](https://github.com/abidlabs) in [PR 2359](https://github.com/gradio-app/gradio/pull/2359)
* Hotfix: fix version back to 3.4 by [@abidlabs](https://github.com/abidlabs) in [PR 2361](https://github.com/gradio-app/gradio/pull/2361)
* Change version.txt to 3.4 instead of 3.4.0 by [@aliabd](https://github.com/aliabd) in [PR 2363](https://github.com/gradio-app/gradio/pull/2363)
* Catch the permission exception on the audio component by [@Ian-GL](https://github.com/Ian-GL) in [PR 2330](https://github.com/gradio-app/gradio/pull/2330)
* Fix image_classifier_interface_load demo by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2365](https://github.com/gradio-app/gradio/pull/2365)
* Small fixes to docs for `Image` component by [@abidlabs](https://github.com/abidlabs) in [PR 2372](https://github.com/gradio-app/gradio/pull/2372)
* Automated Release Notes by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2306](https://github.com/gradio-app/gradio/pull/2306)
* Fixed small typos in the docs [@julien-c](https://github.com/julien-c) in [PR 2373](https://github.com/gradio-app/gradio/pull/2373)
* Adds ability to disable pre/post-processing for examples [@abidlabs](https://github.com/abidlabs) in [PR 2383](https://github.com/gradio-app/gradio/pull/2383)
* Copy changelog file in website docker by [@aliabd](https://github.com/aliabd) in [PR 2384](https://github.com/gradio-app/gradio/pull/2384)
* Lets users provide a `gr.update()` dictionary even if post-processing is diabled [@abidlabs](https://github.com/abidlabs) in [PR 2385](https://github.com/gradio-app/gradio/pull/2385)
* Fix bug where errors would cause apps run in reload mode to hang forever by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2394](https://github.com/gradio-app/gradio/pull/2394)
* Fix bug where new typeable slider doesn't respect the minimum and maximum values [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2380](https://github.com/gradio-app/gradio/pull/2380)


## Contributors Shoutout:
No changes to highlight.

# Version 3.4

## New Features:

### 1. Gallery Captions 🖼️

You can now pass captions to images in the Gallery component. To do so you need to pass a {List} of (image, {str} caption) tuples. This is optional and the component also accepts just a list of the images.

Here's an example:

```python
import gradio as gr

images_with_captions = [
    ("https://images.unsplash.com/photo-1551969014-7d2c4cddf0b6", "Cheetah by David Groves"),
    ("https://images.unsplash.com/photo-1546182990-dffeafbe841d", "Lion by Francesco"),
    ("https://images.unsplash.com/photo-1561731216-c3a4d99437d5", "Tiger by Mike Marrah")
    ]

with gr.Blocks() as demo:
    gr.Gallery(value=images_with_captions)

demo.launch()
```

<img src="https://user-images.githubusercontent.com/9021060/192399521-7360b1a9-7ce0-443e-8e94-863a230a7dbe.gif" alt="gallery_captions" width="1000"/>

### 2. Type Values into the Slider 🔢

You can now type values directly on the Slider component! Here's what it looks like:

![type-slider](https://user-images.githubusercontent.com/9021060/192399877-76b662a1-fede-4417-a932-fc15f0da7360.gif)

### 3. Better Sketching and Inpainting 🎨

We've made a lot of changes to our Image component so that it can support better sketching and inpainting.

Now supports:
* A standalone black-and-white sketch
```python
import gradio as gr
demo = gr.Interface(lambda x: x, gr.Sketchpad(), gr.Image())
demo.launch()
```
![bw](https://user-images.githubusercontent.com/9021060/192410264-b08632b5-7b2a-4f86-afb0-5760e7b474cf.gif)


* A standalone color sketch
```python
import gradio as gr
demo = gr.Interface(lambda x: x, gr.Paint(), gr.Image())
demo.launch()
```
![color-sketch](https://user-images.githubusercontent.com/9021060/192410500-3c8c3e64-a5fd-4df2-a991-f0a5cef93728.gif)


* An uploadable image with black-and-white or color sketching

```python
import gradio as gr
demo = gr.Interface(lambda x: x, gr.Image(source='upload', tool='color-sketch'), gr.Image()) # for black and white, tool = 'sketch'
demo.launch()
```
![sketch-new](https://user-images.githubusercontent.com/9021060/192402422-e53cb7b6-024e-448c-87eb-d6a35a63c476.gif)


* Webcam with black-and-white or color sketching

```python
import gradio as gr
demo = gr.Interface(lambda x: x, gr.Image(source='webcam', tool='color-sketch'), gr.Image()) # for black and white, tool = 'sketch'
demo.launch()
```
![webcam-sketch](https://user-images.githubusercontent.com/9021060/192410820-0ffaf324-776e-4e1f-9de6-0fdbbf4940fa.gif)


As well as other fixes


## Bug Fixes:
1. Fix bug where max concurrency count is not respected in queue by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2286](https://github.com/gradio-app/gradio/pull/2286)
2. fix : queue could be blocked by [@SkyTNT](https://github.com/SkyTNT) in [PR 2288](https://github.com/gradio-app/gradio/pull/2288)
3. Supports `gr.update()` in example caching by [@abidlabs](https://github.com/abidlabs) in [PR 2309](https://github.com/gradio-app/gradio/pull/2309)
4. Clipboard fix for iframes by [@abidlabs](https://github.com/abidlabs) in [PR 2321](https://github.com/gradio-app/gradio/pull/2321)
5. Fix: Dataframe column headers are reset when you add a new column by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2318](https://github.com/gradio-app/gradio/pull/2318)
6. Added support for URLs for Video, Audio, and Image by [@abidlabs](https://github.com/abidlabs) in [PR 2256](https://github.com/gradio-app/gradio/pull/2256)
7. Add documentation about how to create and use the Gradio FastAPI app by [@abidlabs](https://github.com/abidlabs) in [PR 2263](https://github.com/gradio-app/gradio/pull/2263)

## Documentation Changes:
1. Adding a Playground Tab to the Website by [@aliabd](https://github.com/aliabd) in [PR 1860](https://github.com/gradio-app/gradio/pull/1860)
3. Gradio for Tabular Data Science Workflows Guide by [@merveenoyan](https://github.com/merveenoyan) in [PR 2199](https://github.com/gradio-app/gradio/pull/2199)
4. Promotes `postprocess` and `preprocess` to documented parameters by [@abidlabs](https://github.com/abidlabs) in [PR 2293](https://github.com/gradio-app/gradio/pull/2293)
5. Update 2)key_features.md by [@voidxd](https://github.com/voidxd) in [PR 2326](https://github.com/gradio-app/gradio/pull/2326)
6. Add docs to blocks context postprocessing function by [@Ian-GL](https://github.com/Ian-GL) in [PR 2332](https://github.com/gradio-app/gradio/pull/2332)

## Testing and Infrastructure Changes
1. Website fixes and refactoring by [@aliabd](https://github.com/aliabd) in [PR 2280](https://github.com/gradio-app/gradio/pull/2280)
2. Don't deploy to spaces on release by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2313](https://github.com/gradio-app/gradio/pull/2313)

## Full Changelog:
* Website fixes and refactoring by [@aliabd](https://github.com/aliabd) in [PR 2280](https://github.com/gradio-app/gradio/pull/2280)
* Fix bug where max concurrency count is not respected in queue by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2286](https://github.com/gradio-app/gradio/pull/2286)
* Promotes `postprocess` and `preprocess` to documented parameters by [@abidlabs](https://github.com/abidlabs) in [PR 2293](https://github.com/gradio-app/gradio/pull/2293)
* Raise warning when trying to cache examples but not all inputs have examples by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2279](https://github.com/gradio-app/gradio/pull/2279)
* fix : queue could be blocked by [@SkyTNT](https://github.com/SkyTNT) in [PR 2288](https://github.com/gradio-app/gradio/pull/2288)
* Don't deploy to spaces on release by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2313](https://github.com/gradio-app/gradio/pull/2313)
* Supports `gr.update()` in example caching by [@abidlabs](https://github.com/abidlabs) in [PR 2309](https://github.com/gradio-app/gradio/pull/2309)
* Respect Upstream Queue when loading interfaces/blocks from Spaces by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2294](https://github.com/gradio-app/gradio/pull/2294)
* Clipboard fix for iframes by [@abidlabs](https://github.com/abidlabs) in [PR 2321](https://github.com/gradio-app/gradio/pull/2321)
* Sketching + Inpainting Capabilities to Gradio by [@abidlabs](https://github.com/abidlabs) in [PR 2144](https://github.com/gradio-app/gradio/pull/2144)
* Update 2)key_features.md by [@voidxd](https://github.com/voidxd) in [PR 2326](https://github.com/gradio-app/gradio/pull/2326)
* release 3.4b3 by [@abidlabs](https://github.com/abidlabs) in [PR 2328](https://github.com/gradio-app/gradio/pull/2328)
* Fix: Dataframe column headers are reset when you add a new column by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2318](https://github.com/gradio-app/gradio/pull/2318)
* Start queue when gradio is a sub application by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2319](https://github.com/gradio-app/gradio/pull/2319)
* Fix Web Tracker Script by [@aliabd](https://github.com/aliabd) in [PR 2308](https://github.com/gradio-app/gradio/pull/2308)
* Add docs to blocks context postprocessing function by [@Ian-GL](https://github.com/Ian-GL) in [PR 2332](https://github.com/gradio-app/gradio/pull/2332)
* Fix typo in iterator variable name in run_predict function by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2340](https://github.com/gradio-app/gradio/pull/2340)
* Add captions to galleries by [@aliabid94](https://github.com/aliabid94) in [PR 2284](https://github.com/gradio-app/gradio/pull/2284)
* Typeable value on gradio.Slider by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2329](https://github.com/gradio-app/gradio/pull/2329)

## Contributors Shoutout:
* [@SkyTNT](https://github.com/SkyTNT) made their first contribution in [PR 2288](https://github.com/gradio-app/gradio/pull/2288)
* [@voidxd](https://github.com/voidxd) made their first contribution in [PR 2326](https://github.com/gradio-app/gradio/pull/2326)


# Version 3.3

## New Features:

### 1. Iterative Outputs ⏳

You can now create an iterative output simply by having your function return a generator!

Here's (part of) an example that was used to generate the interface below it. [See full code](https://colab.research.google.com/drive/1m9bWS6B82CT7bw-m4L6AJR8za7fEK7Ov?usp=sharing).

```python
def predict(steps, seed):
    generator = torch.manual_seed(seed)
    for i in range(1,steps):
        yield pipeline(generator=generator, num_inference_steps=i)["sample"][0]
```


![example](https://user-images.githubusercontent.com/9021060/189086273-f5e7087d-71fa-4158-90a9-08e84da0421c.mp4)

### 2. Accordion Layout 🆕

This version of Gradio introduces a new layout component to Blocks: the Accordion. Wrap your elements in a neat, expandable layout that allows users to toggle them as needed.

Usage: ([Read the docs](https://gradio.app/docs/#accordion))

```python
with gr.Accordion("open up"):
# components here
```

![accordion](https://user-images.githubusercontent.com/9021060/189088465-f0ffd7f0-fc6a-42dc-9249-11c5e1e0529b.gif)

### 3. Skops Integration 📈

Our new integration with [skops](https://huggingface.co/blog/skops) allows you to load tabular classification and regression models directly from the [hub](https://huggingface.co/models).

Here's a classification example showing how quick it is to set up an interface for a [model](https://huggingface.co/scikit-learn/tabular-playground).

```python
import gradio as gr
gr.Interface.load("models/scikit-learn/tabular-playground").launch()
```

![187936493-5c90c01d-a6dd-400f-aa42-833a096156a1](https://user-images.githubusercontent.com/9021060/189090519-328fbcb4-120b-43c8-aa54-d6fccfa6b7e8.png)


## Bug Fixes:
No changes to highlight.
## Documentation Changes:
No changes to highlight.
## Testing and Infrastructure Changes:
No changes to highlight.
## Breaking Changes:
No changes to highlight.
## Full Changelog:

* safari fixes by [@pngwn](https://github.com/pngwn) in [PR 2138](https://github.com/gradio-app/gradio/pull/2138)
* Fix roundedness and form borders by [@aliabid94](https://github.com/aliabid94) in [PR 2147](https://github.com/gradio-app/gradio/pull/2147)
* Better processing of example data prior to creating dataset component by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2147](https://github.com/gradio-app/gradio/pull/2147)
* Show error on Connection drops by [@aliabid94](https://github.com/aliabid94) in [PR 2147](https://github.com/gradio-app/gradio/pull/2147)
* 3.2 release! by [@abidlabs](https://github.com/abidlabs) in [PR 2139](https://github.com/gradio-app/gradio/pull/2139)
* Fixed Named API Requests by [@abidlabs](https://github.com/abidlabs) in [PR 2151](https://github.com/gradio-app/gradio/pull/2151)
* Quick Fix: Cannot upload Model3D image after clearing it by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2168](https://github.com/gradio-app/gradio/pull/2168)
* Fixed misleading log when server_name is '0.0.0.0' by [@lamhoangtung](https://github.com/lamhoangtung) in [PR 2176](https://github.com/gradio-app/gradio/pull/2176)
* Keep embedded PngInfo metadata by [@cobryan05](https://github.com/cobryan05) in [PR 2170](https://github.com/gradio-app/gradio/pull/2170)
* Skops integration: Load tabular classification and regression models from the hub by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2126](https://github.com/gradio-app/gradio/pull/2126)
* Respect original filename when cached example files are downloaded by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2145](https://github.com/gradio-app/gradio/pull/2145)
* Add manual trigger to deploy to pypi by [@abidlabs](https://github.com/abidlabs) in [PR 2192](https://github.com/gradio-app/gradio/pull/2192)
* Fix bugs with gr.update by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2157](https://github.com/gradio-app/gradio/pull/2157)
* Make queue per app by [@aliabid94](https://github.com/aliabid94) in [PR 2193](https://github.com/gradio-app/gradio/pull/2193)
* Preserve Labels In Interpretation Components by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2166](https://github.com/gradio-app/gradio/pull/2166)
* Quick Fix: Multiple file download not working by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2169](https://github.com/gradio-app/gradio/pull/2169)
* use correct MIME type for js-script file by [@daspartho](https://github.com/daspartho) in [PR 2200](https://github.com/gradio-app/gradio/pull/2200)
* Add accordion component by [@aliabid94](https://github.com/aliabid94) in [PR 2208](https://github.com/gradio-app/gradio/pull/2208)


## Contributors Shoutout:

* [@lamhoangtung](https://github.com/lamhoangtung) made their first contribution in [PR 2176](https://github.com/gradio-app/gradio/pull/2176)
* [@cobryan05](https://github.com/cobryan05) made their first contribution in [PR 2170](https://github.com/gradio-app/gradio/pull/2170)
* [@daspartho](https://github.com/daspartho) made their first contribution in [PR 2200](https://github.com/gradio-app/gradio/pull/2200)

# Version 3.2

## New Features:

### 1. Improvements to Queuing 🥇

We've implemented a brand new queuing system based on **web sockets** instead of HTTP long polling. Among other things, this allows us to manage queue sizes better on Hugging Face Spaces. There are also additional queue-related parameters you can add:

* Now supports concurrent workers (parallelization)
```python
demo = gr.Interface(...)
demo.queue(concurrency_count=3)
demo.launch()
```
* Configure a maximum queue size
```python
demo = gr.Interface(...)
demo.queue(max_size=100)
demo.launch()
```

* If a user closes their tab / browser, they leave the queue, which means the demo will run faster for everyone else

### 2. Fixes to Examples

* Dataframe examples will render properly, and look much clearer in the UI: (thanks to PR #2125)

![Screen Shot 2022-08-30 at 8 29 58 PM](https://user-images.githubusercontent.com/9021060/187586561-d915bafb-f968-4966-b9a2-ef41119692b2.png)

* Image and Video thumbnails are cropped to look neater and more uniform: (thanks to PR #2109)


![Screen Shot 2022-08-30 at 8 32 15 PM](https://user-images.githubusercontent.com/9021060/187586890-56e1e4f0-1b84-42d9-a82f-911772c41030.png)

* Other fixes in PR #2131 and #2064  make it easier to design and use Examples

### 3. Component Fixes 🧱
* Specify the width and height of an image in its style tag (thanks to PR #2133)
```python
components.Image().style(height=260, width=300)
```
* Automatic conversion of videos so they are playable in the browser (thanks to PR #2003). Gradio will check if a video's format is playable  in the browser and, if it isn't, will automatically convert it to a format that is (mp4).
* Pass in a json filepath to the Label component (thanks to PR #2083)
* Randomize the default value of a Slider (thanks to PR #1935)

![slider-random](https://user-images.githubusercontent.com/9021060/187596230-3db9697f-9f4d-42f5-9387-d77573513448.gif)


* Improvements to State in PR #2100

### 4. Ability to Randomize Input Sliders and Reload Data whenever the Page Loads
* In some cases, you want to be able to show a different set of input data to every user as they load the page app. For example, you might want to randomize the value of a "seed" `Slider` input. Or you might want to show a `Textbox` with the current date. We now supporting passing _functions_ as the default value in input components. When you pass in a function, it gets **re-evaluated** every time someone loads the demo, allowing you to reload / change data for different users.

Here's an example loading the current date time into an input Textbox:

```python
import gradio as gr
import datetime

with gr.Blocks() as demo:
    gr.Textbox(datetime.datetime.now)

demo.launch()
```

Note that we don't evaluate the function -- `datetime.datetime.now()` -- we pass in the function itself to get this behavior -- `datetime.datetime.now`

Because randomizing the initial value of `Slider` is a common use case, we've added a `randomize` keyword argument you can use to randomize its initial value:

```python
import gradio as gr
demo = gr.Interface(lambda x:x, gr.Slider(0, 10, randomize=True), "number")
demo.launch()
```

### 5. New Guide 🖊️
* [Gradio and W&B Integration](https://gradio.app/Gradio_and_Wandb_Integration/)


## Full Changelog:

* Reset components to original state by setting value to None by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2044](https://github.com/gradio-app/gradio/pull/2044)
* Cleaning up the way data is processed for components by [@abidlabs](https://github.com/abidlabs) in [PR 1967](https://github.com/gradio-app/gradio/pull/1967)
* version 3.1.8b by [@abidlabs](https://github.com/abidlabs) in [PR 2063](https://github.com/gradio-app/gradio/pull/2063)
* Wandb guide  by [@AK391](https://github.com/AK391) in [PR 1898](https://github.com/gradio-app/gradio/pull/1898)
* Add a flagging callback to save json files to a hugging face dataset by [@chrisemezue](https://github.com/chrisemezue) in [PR 1821](https://github.com/gradio-app/gradio/pull/1821)
* Add data science demos to landing page by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2067](https://github.com/gradio-app/gradio/pull/2067)
* Hide time series + xgboost demos by default by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2079](https://github.com/gradio-app/gradio/pull/2079)
* Encourage people to keep trying when queue full by [@apolinario](https://github.com/apolinario) in [PR 2076](https://github.com/gradio-app/gradio/pull/2076)
* Updated our analytics on creation of Blocks/Interface by [@abidlabs](https://github.com/abidlabs) in [PR 2082](https://github.com/gradio-app/gradio/pull/2082)
* `Label` component now accepts file paths to `.json` files  by [@abidlabs](https://github.com/abidlabs) in [PR 2083](https://github.com/gradio-app/gradio/pull/2083)
* Fix issues related to demos in Spaces by [@abidlabs](https://github.com/abidlabs) in [PR 2086](https://github.com/gradio-app/gradio/pull/2086)
* Fix TimeSeries examples not properly displayed in UI by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2064](https://github.com/gradio-app/gradio/pull/2064)
* Fix infinite requests when doing tab item select by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2070](https://github.com/gradio-app/gradio/pull/2070)
* Accept deprecated `file` route as well by [@abidlabs](https://github.com/abidlabs) in [PR 2099](https://github.com/gradio-app/gradio/pull/2099)
* Allow frontend method execution on Block.load event by [@codedealer](https://github.com/codedealer) in [PR 2108](https://github.com/gradio-app/gradio/pull/2108)
* Improvements to `State` by [@abidlabs](https://github.com/abidlabs) in [PR 2100](https://github.com/gradio-app/gradio/pull/2100)
* Catch IndexError, KeyError in video_is_playable by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 2113](https://github.com/gradio-app/gradio/pull/2113)
* Fix: Download button does not respect the filepath returned by the function by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 2073](https://github.com/gradio-app/gradio/pull/2073)
* Refactoring Layout: Adding column widths, forms, and more. by [@aliabid94](https://github.com/aliabid94) in [PR 2097](https://github.com/gradio-app/gradio/pull/2097)
* Update CONTRIBUTING.md by [@abidlabs](https://github.com/abidlabs) in [PR 2118](https://github.com/gradio-app/gradio/pull/2118)
* 2092 df ex by [@pngwn](https://github.com/pngwn) in [PR 2125](https://github.com/gradio-app/gradio/pull/2125)
* feat(samples table/gallery): Crop thumbs to square by [@ronvoluted](https://github.com/ronvoluted) in [PR 2109](https://github.com/gradio-app/gradio/pull/2109)
* Some enhancements to `gr.Examples` by [@abidlabs](https://github.com/abidlabs) in [PR 2131](https://github.com/gradio-app/gradio/pull/2131)
* Image size fix by [@aliabid94](https://github.com/aliabid94) in [PR 2133](https://github.com/gradio-app/gradio/pull/2133)

## Contributors Shoutout:
* [@chrisemezue](https://github.com/chrisemezue) made their first contribution in [PR 1821](https://github.com/gradio-app/gradio/pull/1821)
* [@apolinario](https://github.com/apolinario) made their first contribution in [PR 2076](https://github.com/gradio-app/gradio/pull/2076)
* [@codedealer](https://github.com/codedealer) made their first contribution in [PR 2108](https://github.com/gradio-app/gradio/pull/2108)

# Version 3.1

## New Features:

### 1.  Embedding Demos on Any Website 💻

With PR #1444, Gradio is now distributed as a web component. This means demos can be natively embedded on websites. You'll just need to add two lines: one to load the gradio javascript, and one to link to the demos backend.

Here's a simple example that embeds the demo from a Hugging Face space:

```html
<script type="module" src="https://gradio.s3-us-west-2.amazonaws.com/3.0.18/gradio.js"></script>
<gradio-app space="abidlabs/pytorch-image-classifier"></gradio-app>
```

But you can also embed demos that are running anywhere, you just need to link the demo to `src` instead of `space`. In fact, all the demos on the gradio website are embedded this way:

<img width="1268" alt="Screen Shot 2022-07-14 at 2 41 44 PM" src="https://user-images.githubusercontent.com/9021060/178997124-b2f05af2-c18f-4716-bf1b-cb971d012636.png">


Read more in the [Embedding Gradio Demos](https://gradio.app/embedding_gradio_demos) guide.

### 2. Reload Mode 👨‍💻

Reload mode helps developers create gradio demos faster by automatically reloading the demo whenever the code changes. It can support development on Python IDEs (VS Code, PyCharm, etc), the terminal, as well as Jupyter notebooks.

If your demo code is in a script named `app.py`, instead of running `python app.py` you can now run `gradio app.py` and that will launch the demo in reload mode:

```bash
Launching in reload mode on: http://127.0.0.1:7860 (Press CTRL+C to quit)
Watching...
WARNING: The --reload flag should not be used in production on Windows.
```

If you're working from a Jupyter or Colab Notebook, use these magic commands instead: `%load_ext gradio` when you import gradio, and `%%blocks` in the top of the cell with the demo code. Here's an example that shows how much faster the development becomes:

![Blocks](https://user-images.githubusercontent.com/9021060/178986488-ed378cc8-5141-4330-ba41-672b676863d0.gif)

### 3. Inpainting Support on `gr.Image()` 🎨

We updated the Image component to add support for inpainting demos. It works by adding `tool="sketch"` as a parameter, that passes both an image and a sketchable mask to your prediction function.

Here's an example from the [LAMA space](https://huggingface.co/spaces/akhaliq/lama):

![FXApVlFVsAALSD-](https://user-images.githubusercontent.com/9021060/178989479-549867c8-7fb0-436a-a97d-1e91c9f5e611.jpeg)

### 4. Markdown and HTML support in Dataframes 🔢

We upgraded the Dataframe component in PR #1684 to support rendering Markdown and HTML inside the cells.

This means you can build Dataframes that look like the following:

![image (8)](https://user-images.githubusercontent.com/9021060/178991233-41cb07a5-e7a3-433e-89b8-319bc78eb9c2.png)


### 5. `gr.Examples()` for Blocks 🧱

We've added the `gr.Examples` component helper to allow you to add examples to any Blocks demo. This class is a wrapper over the `gr.Dataset` component.

<img width="1271" alt="Screen Shot 2022-07-14 at 2 23 50 PM" src="https://user-images.githubusercontent.com/9021060/178992715-c8bc7550-bc3d-4ddc-9fcb-548c159cd153.png">


gr.Examples takes two required parameters:

- `examples` which takes in a nested list
-  `inputs` which takes in a component or list of components

You can read more in the [Examples docs](https://gradio.app/docs/#examples) or the [Adding Examples to your Demos guide](https://gradio.app/adding_examples_to_your_app/).

### 6. Fixes to Audio Streaming

With [PR 1828](https://github.com/gradio-app/gradio/pull/1828) we now hide the status loading animation, as well as remove the echo in streaming. Check out the [stream_audio](https://github.com/gradio-app/gradio/blob/main/demo/stream_audio/run.py) demo for more or read through our [Real Time Speech Recognition](https://gradio.app/real_time_speech_recognition/) guide.

<img width="785" alt="Screen Shot 2022-07-19 at 6 02 35 PM" src="https://user-images.githubusercontent.com/9021060/179808136-9e84502c-f9ee-4f30-b5e9-1086f678fe91.png">


## Full Changelog:

* File component: list multiple files and allow for download #1446 by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 1681](https://github.com/gradio-app/gradio/pull/1681)
* Add ColorPicker to docs by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 1768](https://github.com/gradio-app/gradio/pull/1768)
* Mock out requests in TestRequest unit tests by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 1794](https://github.com/gradio-app/gradio/pull/1794)
* Add requirements.txt and test_files to source dist by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 1817](https://github.com/gradio-app/gradio/pull/1817)
* refactor: f-string for tunneling.py by [@nhankiet](https://github.com/nhankiet) in [PR 1819](https://github.com/gradio-app/gradio/pull/1819)
* Miscellaneous formatting improvements to website by [@aliabd](https://github.com/aliabd) in [PR 1754](https://github.com/gradio-app/gradio/pull/1754)
* `integrate()` method moved to `Blocks` by [@abidlabs](https://github.com/abidlabs) in [PR 1776](https://github.com/gradio-app/gradio/pull/1776)
* Add python-3.7 tests by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 1818](https://github.com/gradio-app/gradio/pull/1818)
* Copy test dir in website dockers by [@aliabd](https://github.com/aliabd) in [PR 1827](https://github.com/gradio-app/gradio/pull/1827)
* Add info to docs on how to set default values for components by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 1788](https://github.com/gradio-app/gradio/pull/1788)
* Embedding Components on Docs by [@aliabd](https://github.com/aliabd) in [PR 1726](https://github.com/gradio-app/gradio/pull/1726)
* Remove usage of deprecated gr.inputs and gr.outputs from website by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 1796](https://github.com/gradio-app/gradio/pull/1796)
* Some cleanups to the docs page by [@abidlabs](https://github.com/abidlabs) in [PR 1822](https://github.com/gradio-app/gradio/pull/1822)

## Contributors Shoutout:
* [@nhankiet](https://github.com/nhankiet) made their first contribution in [PR 1819](https://github.com/gradio-app/gradio/pull/1819)

# Version 3.0

### 🔥 Gradio 3.0 is the biggest update to the library, ever.

## New Features:

### 1.  Blocks 🧱

Blocks is a new, low-level API that allows you to have full control over the data flows and layout of your application. It allows you to build very complex, multi-step applications. For example, you might want to:

* Group together related demos as multiple tabs in one web app
* Change the layout of your demo instead of just having all of the inputs on the left and outputs on the right
* Have multi-step interfaces, in which the output of one model becomes the input to the next model, or have more flexible data flows in general
* Change a component's properties (for example, the choices in a Dropdown) or its visibility based on user input

Here's a simple example that creates the demo below it:

```python
import gradio as gr

def update(name):
    return f"Welcome to Gradio, {name}!"

demo = gr.Blocks()

with demo:
    gr.Markdown(
    """
    # Hello World!
    Start typing below to see the output.
    """)
    inp = gr.Textbox(placeholder="What is your name?")
    out = gr.Textbox()

    inp.change(fn=update,
               inputs=inp,
               outputs=out)

demo.launch()
```

![hello-blocks](https://user-images.githubusercontent.com/9021060/168684108-78cbd24b-e6bd-4a04-a8d9-20d535203434.gif)


Read our [Introduction to Blocks](http://gradio.app/introduction_to_blocks/) guide for more, and join the 🎈 [Gradio Blocks Party](https://huggingface.co/spaces/Gradio-Blocks/README)!


### 2. Our Revamped Design 🎨

We've upgraded our design across the entire library: from components, and layouts all the way to dark mode.

![kitchen_sink](https://user-images.githubusercontent.com/9021060/168686333-7a6e3096-3e23-4309-abf2-5cd7736e0463.gif)


### 3. A New Website 💻

We've upgraded [gradio.app](https://gradio.app) to make it cleaner, faster and easier to use. Our docs now come with components and demos embedded directly on the page. So you can quickly get up to speed with what you're looking for.

![website](https://user-images.githubusercontent.com/9021060/168687191-10d6a3bd-101f-423a-8193-48f47a5e077d.gif)


### 4. New Components: Model3D, Dataset, and More..

We've introduced a lot of new components in `3.0`, including `Model3D`, `Dataset`, `Markdown`, `Button` and `Gallery`. You can find all the components and play around with them [here](https://gradio.app/docs/#components).


![Model3d](https://user-images.githubusercontent.com/9021060/168689062-6ad77151-8cc5-467d-916c-f7c78e52ec0c.gif)

## Full Changelog:

* Gradio dash fe by [@pngwn](https://github.com/pngwn) in [PR 807](https://github.com/gradio-app/gradio/pull/807)
* Blocks components by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 765](https://github.com/gradio-app/gradio/pull/765)
* Blocks components V2 by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 843](https://github.com/gradio-app/gradio/pull/843)
* Blocks-Backend-Events by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 844](https://github.com/gradio-app/gradio/pull/844)
* Interfaces from Blocks by [@aliabid94](https://github.com/aliabid94) in [PR 849](https://github.com/gradio-app/gradio/pull/849)
* Blocks dev by [@aliabid94](https://github.com/aliabid94) in [PR 853](https://github.com/gradio-app/gradio/pull/853)
* Started updating demos to use the new `gradio.components` syntax by [@abidlabs](https://github.com/abidlabs) in [PR 848](https://github.com/gradio-app/gradio/pull/848)
* add test infra + add browser tests to CI by [@pngwn](https://github.com/pngwn) in [PR 852](https://github.com/gradio-app/gradio/pull/852)
* 854 textbox by [@pngwn](https://github.com/pngwn) in [PR 859](https://github.com/gradio-app/gradio/pull/859)
* Getting old Python unit tests to pass on `blocks-dev` by [@abidlabs](https://github.com/abidlabs) in [PR 861](https://github.com/gradio-app/gradio/pull/861)
* initialise chatbot with empty array of messages by [@pngwn](https://github.com/pngwn) in [PR 867](https://github.com/gradio-app/gradio/pull/867)
* add test for output to input by [@pngwn](https://github.com/pngwn) in [PR 866](https://github.com/gradio-app/gradio/pull/866)
* More Interface -> Blocks features by [@aliabid94](https://github.com/aliabid94) in [PR 864](https://github.com/gradio-app/gradio/pull/864)
* Fixing external.py in blocks-dev to reflect the new HF Spaces paths by [@abidlabs](https://github.com/abidlabs) in [PR 879](https://github.com/gradio-app/gradio/pull/879)
* backend_default_value_refactoring by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 871](https://github.com/gradio-app/gradio/pull/871)
* fix default_value  by [@pngwn](https://github.com/pngwn) in [PR 869](https://github.com/gradio-app/gradio/pull/869)
* fix buttons by [@aliabid94](https://github.com/aliabid94) in [PR 883](https://github.com/gradio-app/gradio/pull/883)
* Checking and updating more demos to use 3.0 syntax by [@abidlabs](https://github.com/abidlabs) in [PR 892](https://github.com/gradio-app/gradio/pull/892)
* Blocks Tests by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 902](https://github.com/gradio-app/gradio/pull/902)
* Interface fix by [@pngwn](https://github.com/pngwn) in [PR 901](https://github.com/gradio-app/gradio/pull/901)
* Quick fix: Issue 893 by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 907](https://github.com/gradio-app/gradio/pull/907)
* 3d Image Component by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 775](https://github.com/gradio-app/gradio/pull/775)
* fix endpoint url in prod by [@pngwn](https://github.com/pngwn) in [PR 911](https://github.com/gradio-app/gradio/pull/911)
* rename Model3d to Image3D by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 912](https://github.com/gradio-app/gradio/pull/912)
* update pypi to 2.9.1 by [@abidlabs](https://github.com/abidlabs) in [PR 916](https://github.com/gradio-app/gradio/pull/916)
* blocks-with-fix by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 917](https://github.com/gradio-app/gradio/pull/917)
* Restore Interpretation, Live, Auth, Queueing by [@aliabid94](https://github.com/aliabid94) in [PR 915](https://github.com/gradio-app/gradio/pull/915)
* Allow `Blocks` instances to be used like a `Block` in other `Blocks` by [@abidlabs](https://github.com/abidlabs) in [PR 919](https://github.com/gradio-app/gradio/pull/919)
* Redesign 1 by [@pngwn](https://github.com/pngwn) in [PR 918](https://github.com/gradio-app/gradio/pull/918)
* blocks-components-tests by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 904](https://github.com/gradio-app/gradio/pull/904)
* fix unit + browser tests by [@pngwn](https://github.com/pngwn) in [PR 926](https://github.com/gradio-app/gradio/pull/926)
* blocks-move-test-data by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 927](https://github.com/gradio-app/gradio/pull/927)
* remove debounce from form inputs by [@pngwn](https://github.com/pngwn) in [PR 932](https://github.com/gradio-app/gradio/pull/932)
* reimplement webcam video by [@pngwn](https://github.com/pngwn) in [PR 928](https://github.com/gradio-app/gradio/pull/928)
* blocks-move-test-data by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 941](https://github.com/gradio-app/gradio/pull/941)
* allow audio components to take a string value by [@pngwn](https://github.com/pngwn) in [PR 930](https://github.com/gradio-app/gradio/pull/930)
* static mode for textbox by [@pngwn](https://github.com/pngwn) in [PR 929](https://github.com/gradio-app/gradio/pull/929)
* fix file upload text by [@pngwn](https://github.com/pngwn) in [PR 931](https://github.com/gradio-app/gradio/pull/931)
* tabbed-interface-rewritten by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 958](https://github.com/gradio-app/gradio/pull/958)
* Gan demo fix by [@abidlabs](https://github.com/abidlabs) in [PR 965](https://github.com/gradio-app/gradio/pull/965)
* Blocks analytics by [@abidlabs](https://github.com/abidlabs) in [PR 947](https://github.com/gradio-app/gradio/pull/947)
* Blocks page load by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 963](https://github.com/gradio-app/gradio/pull/963)
* add frontend for page load events by [@pngwn](https://github.com/pngwn) in [PR 967](https://github.com/gradio-app/gradio/pull/967)
* fix i18n and some tweaks by [@pngwn](https://github.com/pngwn) in [PR 966](https://github.com/gradio-app/gradio/pull/966)
* add jinja2 to reqs by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 969](https://github.com/gradio-app/gradio/pull/969)
* Cleaning up `Launchable()` by [@abidlabs](https://github.com/abidlabs) in [PR 968](https://github.com/gradio-app/gradio/pull/968)
* Fix #944 by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 971](https://github.com/gradio-app/gradio/pull/971)
* New Blocks Demo: neural instrument cloning by [@abidlabs](https://github.com/abidlabs) in [PR 975](https://github.com/gradio-app/gradio/pull/975)
* Add huggingface_hub client library by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 973](https://github.com/gradio-app/gradio/pull/973)
* State and variables by [@aliabid94](https://github.com/aliabid94) in [PR 977](https://github.com/gradio-app/gradio/pull/977)
* update-components by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 986](https://github.com/gradio-app/gradio/pull/986)
* ensure dataframe updates as expected by [@pngwn](https://github.com/pngwn) in [PR 981](https://github.com/gradio-app/gradio/pull/981)
* test-guideline by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 990](https://github.com/gradio-app/gradio/pull/990)
* Issue #785: add footer by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 972](https://github.com/gradio-app/gradio/pull/972)
* indentation fix by [@abidlabs](https://github.com/abidlabs) in [PR 993](https://github.com/gradio-app/gradio/pull/993)
* missing quote by [@aliabd](https://github.com/aliabd) in [PR 996](https://github.com/gradio-app/gradio/pull/996)
* added interactive parameter to components by [@abidlabs](https://github.com/abidlabs) in [PR 992](https://github.com/gradio-app/gradio/pull/992)
* custom-components by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 985](https://github.com/gradio-app/gradio/pull/985)
* Refactor component shortcuts by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 995](https://github.com/gradio-app/gradio/pull/995)
* Plot Component by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 805](https://github.com/gradio-app/gradio/pull/805)
* updated PyPi version to 2.9.2 by [@abidlabs](https://github.com/abidlabs) in [PR 1002](https://github.com/gradio-app/gradio/pull/1002)
* Release 2.9.3 by [@abidlabs](https://github.com/abidlabs) in [PR 1003](https://github.com/gradio-app/gradio/pull/1003)
* Image3D Examples Fix by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 1001](https://github.com/gradio-app/gradio/pull/1001)
* release 2.9.4 by [@abidlabs](https://github.com/abidlabs) in [PR 1006](https://github.com/gradio-app/gradio/pull/1006)
* templates import hotfix by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1008](https://github.com/gradio-app/gradio/pull/1008)
* Progress indicator bar by [@aliabid94](https://github.com/aliabid94) in [PR 997](https://github.com/gradio-app/gradio/pull/997)
* Fixed image input for absolute path by [@JefferyChiang](https://github.com/JefferyChiang) in [PR 1004](https://github.com/gradio-app/gradio/pull/1004)
* Model3D + Plot Components by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 1010](https://github.com/gradio-app/gradio/pull/1010)
* Gradio Guides: Creating CryptoPunks with GANs by [@NimaBoscarino](https://github.com/NimaBoscarino) in [PR 1000](https://github.com/gradio-app/gradio/pull/1000)
* [BIG PR] Gradio blocks & redesigned components by [@abidlabs](https://github.com/abidlabs) in [PR 880](https://github.com/gradio-app/gradio/pull/880)
* fixed failing test on main by [@abidlabs](https://github.com/abidlabs) in [PR 1023](https://github.com/gradio-app/gradio/pull/1023)
* Use smaller ASR model in external test by [@abidlabs](https://github.com/abidlabs) in [PR 1024](https://github.com/gradio-app/gradio/pull/1024)
* updated PyPi version to 2.9.0b by [@abidlabs](https://github.com/abidlabs) in [PR 1026](https://github.com/gradio-app/gradio/pull/1026)
* Fixing import issues so that the package successfully installs on colab notebooks by [@abidlabs](https://github.com/abidlabs) in [PR 1027](https://github.com/gradio-app/gradio/pull/1027)
* Update website tracker slackbot  by [@aliabd](https://github.com/aliabd) in [PR 1037](https://github.com/gradio-app/gradio/pull/1037)
* textbox-autoheight by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1009](https://github.com/gradio-app/gradio/pull/1009)
* Model3D Examples fixes by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 1035](https://github.com/gradio-app/gradio/pull/1035)
* GAN Gradio Guide: Adjustments to iframe heights by [@NimaBoscarino](https://github.com/NimaBoscarino) in [PR 1042](https://github.com/gradio-app/gradio/pull/1042)
* added better default labels to form components by [@abidlabs](https://github.com/abidlabs) in [PR 1040](https://github.com/gradio-app/gradio/pull/1040)
* Slackbot web tracker fix by [@aliabd](https://github.com/aliabd) in [PR 1043](https://github.com/gradio-app/gradio/pull/1043)
* Plot fixes by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 1044](https://github.com/gradio-app/gradio/pull/1044)
* Small fixes to the demos by [@abidlabs](https://github.com/abidlabs) in [PR 1030](https://github.com/gradio-app/gradio/pull/1030)
* fixing demo issue with website by [@aliabd](https://github.com/aliabd) in [PR 1047](https://github.com/gradio-app/gradio/pull/1047)
* [hotfix] HighlightedText by [@aliabid94](https://github.com/aliabid94) in [PR 1046](https://github.com/gradio-app/gradio/pull/1046)
* Update text by [@ronvoluted](https://github.com/ronvoluted) in [PR 1050](https://github.com/gradio-app/gradio/pull/1050)
* Update CONTRIBUTING.md by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1052](https://github.com/gradio-app/gradio/pull/1052)
* fix(ui): Increase contrast for footer by [@ronvoluted](https://github.com/ronvoluted) in [PR 1048](https://github.com/gradio-app/gradio/pull/1048)
* UI design update by [@gary149](https://github.com/gary149) in [PR 1041](https://github.com/gradio-app/gradio/pull/1041)
* updated PyPi version to 2.9.0b8 by [@abidlabs](https://github.com/abidlabs) in [PR 1059](https://github.com/gradio-app/gradio/pull/1059)
* Running, testing, and fixing demos by [@abidlabs](https://github.com/abidlabs) in [PR 1060](https://github.com/gradio-app/gradio/pull/1060)
* Form layout by [@pngwn](https://github.com/pngwn) in [PR 1054](https://github.com/gradio-app/gradio/pull/1054)
* inputless-interfaces by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1038](https://github.com/gradio-app/gradio/pull/1038)
* Update PULL_REQUEST_TEMPLATE.md by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1068](https://github.com/gradio-app/gradio/pull/1068)
* Upgrading node memory to 4gb in website Docker by [@aliabd](https://github.com/aliabd) in [PR 1069](https://github.com/gradio-app/gradio/pull/1069)
* Website reload error by [@aliabd](https://github.com/aliabd) in [PR 1079](https://github.com/gradio-app/gradio/pull/1079)
* fixed favicon issue by [@abidlabs](https://github.com/abidlabs) in [PR 1064](https://github.com/gradio-app/gradio/pull/1064)
* remove-queue-from-events by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1056](https://github.com/gradio-app/gradio/pull/1056)
* Enable vertex colors for OBJs files by [@radames](https://github.com/radames) in [PR 1074](https://github.com/gradio-app/gradio/pull/1074)
* Dark text by [@ronvoluted](https://github.com/ronvoluted) in [PR 1049](https://github.com/gradio-app/gradio/pull/1049)
* Scroll to output by [@pngwn](https://github.com/pngwn) in [PR 1077](https://github.com/gradio-app/gradio/pull/1077)
* Explicitly list pnpm version 6 in contributing guide by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 1085](https://github.com/gradio-app/gradio/pull/1085)
* hotfix for encrypt issue by [@abidlabs](https://github.com/abidlabs) in [PR 1096](https://github.com/gradio-app/gradio/pull/1096)
* Release 2.9b9 by [@abidlabs](https://github.com/abidlabs) in [PR 1098](https://github.com/gradio-app/gradio/pull/1098)
* tweak node circleci settings by [@pngwn](https://github.com/pngwn) in [PR 1091](https://github.com/gradio-app/gradio/pull/1091)
* Website Reload Error by [@aliabd](https://github.com/aliabd) in [PR 1099](https://github.com/gradio-app/gradio/pull/1099)
* Website Reload: README in demos docker by [@aliabd](https://github.com/aliabd) in [PR 1100](https://github.com/gradio-app/gradio/pull/1100)
* Flagging fixes by [@abidlabs](https://github.com/abidlabs) in [PR 1081](https://github.com/gradio-app/gradio/pull/1081)
* Backend for optional labels by [@abidlabs](https://github.com/abidlabs) in [PR 1080](https://github.com/gradio-app/gradio/pull/1080)
* Optional labels fe by [@pngwn](https://github.com/pngwn) in [PR 1105](https://github.com/gradio-app/gradio/pull/1105)
* clean-deprecated-parameters by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1090](https://github.com/gradio-app/gradio/pull/1090)
* Blocks rendering fix by [@abidlabs](https://github.com/abidlabs) in [PR 1102](https://github.com/gradio-app/gradio/pull/1102)
* Redos #1106 by [@abidlabs](https://github.com/abidlabs) in [PR 1112](https://github.com/gradio-app/gradio/pull/1112)
* Interface types: handle input-only, output-only, and unified interfaces by [@abidlabs](https://github.com/abidlabs) in [PR 1108](https://github.com/gradio-app/gradio/pull/1108)
* Hotfix + New pypi release 2.9b11 by [@abidlabs](https://github.com/abidlabs) in [PR 1118](https://github.com/gradio-app/gradio/pull/1118)
* issue-checkbox by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1122](https://github.com/gradio-app/gradio/pull/1122)
* issue-checkbox-hotfix by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1127](https://github.com/gradio-app/gradio/pull/1127)
* Fix demos in website by [@aliabd](https://github.com/aliabd) in [PR 1130](https://github.com/gradio-app/gradio/pull/1130)
* Guide for Gradio ONNX model zoo on Huggingface by [@AK391](https://github.com/AK391) in [PR 1073](https://github.com/gradio-app/gradio/pull/1073)
* ONNX guide fixes by [@aliabd](https://github.com/aliabd) in [PR 1131](https://github.com/gradio-app/gradio/pull/1131)
* Stacked form inputs css by [@gary149](https://github.com/gary149) in [PR 1134](https://github.com/gradio-app/gradio/pull/1134)
* made default value in textbox empty string by [@abidlabs](https://github.com/abidlabs) in [PR 1135](https://github.com/gradio-app/gradio/pull/1135)
* Examples UI by [@gary149](https://github.com/gary149) in [PR 1121](https://github.com/gradio-app/gradio/pull/1121)
* Chatbot custom color support by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 1092](https://github.com/gradio-app/gradio/pull/1092)
* highlighted text colors by [@pngwn](https://github.com/pngwn) in [PR 1119](https://github.com/gradio-app/gradio/pull/1119)
* pin to pnpm 6 for now by [@pngwn](https://github.com/pngwn) in [PR 1147](https://github.com/gradio-app/gradio/pull/1147)
* Restore queue in Blocks by [@aliabid94](https://github.com/aliabid94) in [PR 1137](https://github.com/gradio-app/gradio/pull/1137)
* add select event for tabitems by [@pngwn](https://github.com/pngwn) in [PR 1154](https://github.com/gradio-app/gradio/pull/1154)
* max_lines + autoheight for textbox by [@pngwn](https://github.com/pngwn) in [PR 1153](https://github.com/gradio-app/gradio/pull/1153)
* use color palette for chatbot by [@pngwn](https://github.com/pngwn) in [PR 1152](https://github.com/gradio-app/gradio/pull/1152)
* Timeseries improvements by [@pngwn](https://github.com/pngwn) in [PR 1149](https://github.com/gradio-app/gradio/pull/1149)
* move styling for interface panels to frontend by [@pngwn](https://github.com/pngwn) in [PR 1146](https://github.com/gradio-app/gradio/pull/1146)
* html tweaks by [@pngwn](https://github.com/pngwn) in [PR 1145](https://github.com/gradio-app/gradio/pull/1145)
* Issue #768: Support passing none to resize and crop image by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 1144](https://github.com/gradio-app/gradio/pull/1144)
* image gallery component + img css by [@aliabid94](https://github.com/aliabid94) in [PR 1140](https://github.com/gradio-app/gradio/pull/1140)
* networking tweak by [@abidlabs](https://github.com/abidlabs) in [PR 1143](https://github.com/gradio-app/gradio/pull/1143)
* Allow enabling queue per event listener by [@aliabid94](https://github.com/aliabid94) in [PR 1155](https://github.com/gradio-app/gradio/pull/1155)
* config hotfix and v. 2.9b23 by [@abidlabs](https://github.com/abidlabs) in [PR 1158](https://github.com/gradio-app/gradio/pull/1158)
* Custom JS calls by [@aliabid94](https://github.com/aliabid94) in [PR 1082](https://github.com/gradio-app/gradio/pull/1082)
* Small fixes: queue default fix, ffmpeg installation message by [@abidlabs](https://github.com/abidlabs) in [PR 1159](https://github.com/gradio-app/gradio/pull/1159)
* formatting by [@abidlabs](https://github.com/abidlabs) in [PR 1161](https://github.com/gradio-app/gradio/pull/1161)
* enable flex grow for gr-box by [@radames](https://github.com/radames) in [PR 1165](https://github.com/gradio-app/gradio/pull/1165)
* 1148 loading by [@pngwn](https://github.com/pngwn) in [PR 1164](https://github.com/gradio-app/gradio/pull/1164)
* Put enable_queue kwarg back in launch() by [@aliabid94](https://github.com/aliabid94) in [PR 1167](https://github.com/gradio-app/gradio/pull/1167)
* A few small fixes by [@abidlabs](https://github.com/abidlabs) in [PR 1171](https://github.com/gradio-app/gradio/pull/1171)
* Hotfix for dropdown component by [@abidlabs](https://github.com/abidlabs) in [PR 1172](https://github.com/gradio-app/gradio/pull/1172)
* use secondary buttons in interface by [@pngwn](https://github.com/pngwn) in [PR 1173](https://github.com/gradio-app/gradio/pull/1173)
* 1183 component height by [@pngwn](https://github.com/pngwn) in [PR 1185](https://github.com/gradio-app/gradio/pull/1185)
* 962 dataframe by [@pngwn](https://github.com/pngwn) in [PR 1186](https://github.com/gradio-app/gradio/pull/1186)
* update-contributing by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1188](https://github.com/gradio-app/gradio/pull/1188)
* Table tweaks by [@pngwn](https://github.com/pngwn) in [PR 1195](https://github.com/gradio-app/gradio/pull/1195)
* wrap tab content in column by [@pngwn](https://github.com/pngwn) in [PR 1200](https://github.com/gradio-app/gradio/pull/1200)
* WIP: Add dark mode support by [@gary149](https://github.com/gary149) in [PR 1187](https://github.com/gradio-app/gradio/pull/1187)
* Restored /api/predict/ endpoint for Interfaces by [@abidlabs](https://github.com/abidlabs) in [PR 1199](https://github.com/gradio-app/gradio/pull/1199)
* hltext-label by [@pngwn](https://github.com/pngwn) in [PR 1204](https://github.com/gradio-app/gradio/pull/1204)
* add copy functionality to json by [@pngwn](https://github.com/pngwn) in [PR 1205](https://github.com/gradio-app/gradio/pull/1205)
* Update component config by [@aliabid94](https://github.com/aliabid94) in [PR 1089](https://github.com/gradio-app/gradio/pull/1089)
* fix placeholder prompt by [@pngwn](https://github.com/pngwn) in [PR 1215](https://github.com/gradio-app/gradio/pull/1215)
* ensure webcam video value is propogated correctly by [@pngwn](https://github.com/pngwn) in [PR 1218](https://github.com/gradio-app/gradio/pull/1218)
* Automatic word-break in highlighted text, combine_adjacent support by [@aliabid94](https://github.com/aliabid94) in [PR 1209](https://github.com/gradio-app/gradio/pull/1209)
* async-function-support by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1190](https://github.com/gradio-app/gradio/pull/1190)
* Sharing fix for assets by [@aliabid94](https://github.com/aliabid94) in [PR 1208](https://github.com/gradio-app/gradio/pull/1208)
* Hotfixes for course demos by [@abidlabs](https://github.com/abidlabs) in [PR 1222](https://github.com/gradio-app/gradio/pull/1222)
* Allow Custom CSS by [@aliabid94](https://github.com/aliabid94) in [PR 1170](https://github.com/gradio-app/gradio/pull/1170)
* share-hotfix by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1226](https://github.com/gradio-app/gradio/pull/1226)
* tweaks by [@pngwn](https://github.com/pngwn) in [PR 1229](https://github.com/gradio-app/gradio/pull/1229)
* white space for class concatenation by [@radames](https://github.com/radames) in [PR 1228](https://github.com/gradio-app/gradio/pull/1228)
* Tweaks by [@pngwn](https://github.com/pngwn) in [PR 1230](https://github.com/gradio-app/gradio/pull/1230)
* css tweaks by [@pngwn](https://github.com/pngwn) in [PR 1235](https://github.com/gradio-app/gradio/pull/1235)
* ensure defaults height match for media inputs by [@pngwn](https://github.com/pngwn) in [PR 1236](https://github.com/gradio-app/gradio/pull/1236)
* Default Label label value by [@radames](https://github.com/radames) in [PR 1239](https://github.com/gradio-app/gradio/pull/1239)
* update-shortcut-syntax by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1234](https://github.com/gradio-app/gradio/pull/1234)
* Update version.txt by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1244](https://github.com/gradio-app/gradio/pull/1244)
* Layout bugs by [@pngwn](https://github.com/pngwn) in [PR 1246](https://github.com/gradio-app/gradio/pull/1246)
* Update demo by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1253](https://github.com/gradio-app/gradio/pull/1253)
* Button default name by [@FarukOzderim](https://github.com/FarukOzderim) in [PR 1243](https://github.com/gradio-app/gradio/pull/1243)
* Labels spacing by [@gary149](https://github.com/gary149) in [PR 1254](https://github.com/gradio-app/gradio/pull/1254)
* add global loader for gradio app by [@pngwn](https://github.com/pngwn) in [PR 1251](https://github.com/gradio-app/gradio/pull/1251)
* ui apis for dalle-mini by [@pngwn](https://github.com/pngwn) in [PR 1258](https://github.com/gradio-app/gradio/pull/1258)
* Add precision to Number, backend only by [@freddyaboulton](https://github.com/freddyaboulton) in [PR 1125](https://github.com/gradio-app/gradio/pull/1125)
* Website Design Changes by [@abidlabs](https://github.com/abidlabs) in [PR 1015](https://github.com/gradio-app/gradio/pull/1015)
* Small fixes for multiple demos compatible with 3.0 by [@radames](https://github.com/radames) in [PR 1257](https://github.com/gradio-app/gradio/pull/1257)
* Issue #1160: Model 3D component not destroyed correctly by [@dawoodkhan82](https://github.com/dawoodkhan82) in [PR 1219](https://github.com/gradio-app/gradio/pull/1219)
* Fixes to components by [@abidlabs](https://github.com/abidlabs) in [PR 1260](https://github.com/gradio-app/gradio/pull/1260)
* layout docs by [@abidlabs](https://github.com/abidlabs) in [PR 1263](https://github.com/gradio-app/gradio/pull/1263)
* Static forms by [@pngwn](https://github.com/pngwn) in [PR 1264](https://github.com/gradio-app/gradio/pull/1264)
* Cdn assets by [@pngwn](https://github.com/pngwn) in [PR 1265](https://github.com/gradio-app/gradio/pull/1265)
* update logo by [@gary149](https://github.com/gary149) in [PR 1266](https://github.com/gradio-app/gradio/pull/1266)
* fix slider by [@aliabid94](https://github.com/aliabid94) in [PR 1268](https://github.com/gradio-app/gradio/pull/1268)
* maybe fix auth in iframes by [@pngwn](https://github.com/pngwn) in [PR 1261](https://github.com/gradio-app/gradio/pull/1261)
* Improves "Getting Started" guide by [@abidlabs](https://github.com/abidlabs) in [PR 1269](https://github.com/gradio-app/gradio/pull/1269)
* Add embedded demos to website by [@aliabid94](https://github.com/aliabid94) in [PR 1270](https://github.com/gradio-app/gradio/pull/1270)
* Label hotfixes by [@abidlabs](https://github.com/abidlabs) in [PR 1281](https://github.com/gradio-app/gradio/pull/1281)
* General tweaks by [@pngwn](https://github.com/pngwn) in [PR 1276](https://github.com/gradio-app/gradio/pull/1276)
* only affect links within the document by [@pngwn](https://github.com/pngwn) in [PR 1282](https://github.com/gradio-app/gradio/pull/1282)
* release 3.0b9 by [@abidlabs](https://github.com/abidlabs) in [PR 1283](https://github.com/gradio-app/gradio/pull/1283)
* Dm by [@pngwn](https://github.com/pngwn) in [PR 1284](https://github.com/gradio-app/gradio/pull/1284)
* Website fixes by [@aliabd](https://github.com/aliabd) in [PR 1286](https://github.com/gradio-app/gradio/pull/1286)
* Create Streamables by [@aliabid94](https://github.com/aliabid94) in [PR 1279](https://github.com/gradio-app/gradio/pull/1279)
* ensure table works on mobile by [@pngwn](https://github.com/pngwn) in [PR 1277](https://github.com/gradio-app/gradio/pull/1277)
* changes by [@aliabid94](https://github.com/aliabid94) in [PR 1287](https://github.com/gradio-app/gradio/pull/1287)
* demo alignment on landing page by [@aliabd](https://github.com/aliabd) in [PR 1288](https://github.com/gradio-app/gradio/pull/1288)
* New meta img by [@aliabd](https://github.com/aliabd) in [PR 1289](https://github.com/gradio-app/gradio/pull/1289)
* updated PyPi version to 3.0 by [@abidlabs](https://github.com/abidlabs) in [PR 1290](https://github.com/gradio-app/gradio/pull/1290)
* Fix site by [@aliabid94](https://github.com/aliabid94) in [PR 1291](https://github.com/gradio-app/gradio/pull/1291)
* Mobile responsive guides by [@aliabd](https://github.com/aliabd) in [PR 1293](https://github.com/gradio-app/gradio/pull/1293)
* Update readme by [@abidlabs](https://github.com/abidlabs) in [PR 1292](https://github.com/gradio-app/gradio/pull/1292)
* gif by [@abidlabs](https://github.com/abidlabs) in [PR 1296](https://github.com/gradio-app/gradio/pull/1296)

## Contributors Shoutout:

* [@JefferyChiang](https://github.com/JefferyChiang) made their first contribution in [PR 1004](https://github.com/gradio-app/gradio/pull/1004)
* [@NimaBoscarino](https://github.com/NimaBoscarino) made their first contribution in [PR 1000](https://github.com/gradio-app/gradio/pull/1000)
* [@ronvoluted](https://github.com/ronvoluted) made their first contribution in [PR 1050](https://github.com/gradio-app/gradio/pull/1050)
* [@radames](https://github.com/radames) made their first contribution in [PR 1074](https://github.com/gradio-app/gradio/pull/1074)
* [@freddyaboulton](https://github.com/freddyaboulton) made their first contribution in [PR 1085](https://github.com/gradio-app/gradio/pull/1085)

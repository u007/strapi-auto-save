
# Instructions

Current setting autosave within 20seconds,
You may modify the interval by modifying call to useInterval function with second parameter

# installation

Copy extensions/content-manager/ to your [projectroot]/extensions/content-manager/ 

```
npm i --save "@use-it/interval"
npm run build

```

# compatibility

```
strapi: "3.2.3"
strapi-plugin-content-manager: "3.2.3" # part of strapi
```

# changes

```
import useInterval from '@use-it/interval';

useInterval(function() {
    console.debug('autosave');
    const { draftAndPublish } = allLayoutData.contentType.schema.options;
    // const modifiedData = state.modifiedData;
    const data = modifiedData;
    let published = data.published_at !== undefined && data.published_at !== null
    if ('published_at' in modifiedData) {
      published = modifiedData.published_at !== undefined && modifiedData.published_at !== null
    }
    const modified = !isEqual(initialData, modifiedData);
    // const hasPublish = false;
    // console.debug("fetched data", id, "hasPublish", draftAndPublish, data, 'published', published);
    // console.debug("modified data", modifiedData, modified);

    if (! isCreatingEntry && modified && draftAndPublish && ! published) {
      console.debug('saving...');
      handleSubmit(document.createEvent('HTMLEvents'));
    }
  }, 20 * 1000);
```
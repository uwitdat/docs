# Issue SER-172 (Oct-6-2021)

[View Issue](https://servushealth.atlassian.net/browse/SER-172)

## Changes in files

- src/api/provider/index.js
- src/components/dialogs/add-provider/addProviderDialog.jsx

## Summary

- Used Select component from 'react-select'. Could not get Material UI Select to work with Formik.
- Added: new field 'type' to initalValues, addProviderSchema, and body of addProvider function (in index.js file).
- New field is not hooked up to API. (Maybe we could go through that at some point?)

line 17:

```js
import Select from "react-select"; // npm install react-select
```

line 54:

```js
const options = [
  {
    value: "Funeral / End of Life Services",
    label: "Funeral / End of Life Services",
  },
  { value: "Medical Equipment Provider", label: "Medical Equipment Provider" },
  { value: "Home Support Services", label: "Home Support Services" },
  { value: "Mental Health", label: "Mental Health" },
];
```

line 235:

```js
<Field
  type="select"
  id="type"
  name="type"
  placeholder="Select Your Service Type"
  component={Select}
  options={options}
  value={setSelectValue(options, values.type)} //refactored to get Select value to update
  onChange={(e) => (values.type = e.value)}
  menuPortalTarget={document.body} //fixes dropdown menu z-index bug
  styles={{ menuPortal: (base) => ({ ...base, zIndex: 9999 }) }}
/>
```

line 134:

```js
const setSelectValue = (options, value) => {
  return options ? options.find((option) => option.value === value) : "";
};
```

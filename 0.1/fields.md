---
prev: ./fields-reference
next: ./relations
---

# Fields

[[toc]]

## Boolean

The boolean field renders a `checkbox` `input` and supports the following options.

```ruby
boolean :is_published,
  name: 'Published',
  required: true,
  readonly: true,
  true_value: 'yes',
  false_value: 'no',
```

### Customize true/false values

You might store the value differently than `1` and `0`. You may customize those values using `true_value` and `false_value`.

## Boolean Group

The boolean group can be used to update a Hash with string keys and boolean values in the database.

```ruby
# Example boolean group hash
{
  admin: true,
  manager: true,
  creator: true,
}
```

```ruby
boolean_group :roles,
  name: 'User roles',
  required: true,
  readonly: true,
```

## Date

The Date field may be used to display date values. The `edit` view of the picker is using flatpickr. You may use the [formatting tokens](https://flatpickr.js.org/formatting/) to format the `edit` element and the moment.js [tokens](https://momentjs.com/docs/#/displaying/format/) to display the `index` and `show` element.

```ruby
boolean_group :roles,
  name: 'User roles',
  placeholder: 'The date',
  required: true,
  readonly: true,
  first_day_of_week: 1, # 1 is Monday (default), 7 is Sunday
  picker_format: 'Y-m-d', # flatpickr date forma
  format: 'YYYY-MM-DD' # momentjs date format
```

## DateTime

The DateTime field is similar to the Date field.

```ruby
datetime :created_at,
  name: 'User joined',
  required: true,
  readonly: true,
  first_day_of_week: 1, # 1 is Monday (default), 7 is Sunday
  picker_format: 'Y-m-d', # flatpickr date format
  format: 'YYYY-MM-DD', # momentjs date format
  time_24hr: true, # Whether to display the field in a 24 hour format
  timezone: 'PST' # The timezone in which to display the time
```

## File

The File field may be used to attach files using the [Active Storage](https://edgeguides.rubyonrails.org/active_storage_overview.html) module.

```ruby
file :avatar,
  name: 'User avatar',
  required: true,
  readonly: true,
  is_avatar: true, # Whether to show the image next to the model in searches. Also sets is_image: true
  is_image: true # Whether the file is an image
```

## Files

The File field may be used to attach files using the [Active Storage](https://edgeguides.rubyonrails.org/active_storage_overview.html) module.

```ruby
files :documents,
  name: 'User docs',
  required: true,
  readonly: true,
  is_image: true # Whether the files are images
```

## ID

The ID field is used to show the record's id.

```ruby
id :ID
```

## Number

The number field renders a `number` `input` and supports the following options:

```ruby
number :age,
  name: "User's age",
  required: true,
  readonly: true,
  placeholder: 'Happy Birthday!',
  format_using: -> (value) { "🥂 #{value}" }
  min: 0,
  max: 120,
  step: 5
```

## Password

The password field renders a `password` `input` and supports the following options:

```ruby
password :password,
  name: 'The password',
  required: true,
  readonly: true,
  placeholder: 'secret',
```

## Select

The select field renders a `select` element and supports the following options:

```ruby
select :type,
  options: { large: 'Large container', medium: 'Medium container', small: 'Tiny container' }, # The options that should be listed in the dropdown
  display_with_value: true, # Wether to display the values of the labels
  placeholder: 'Choose the size of the container.'
```

On `index` and `show` views you may want to display the values and not the labels off the options. You may change that using `display_with_value`.

## Text

The text field renders a `text` `input` and supports the following options:

```ruby
text :title, # The database field ID
  name: 'Post title', # The name you want displayed
  required: true, # Display it as required
  readonly: true, # Display it disabled
  placeholder: 'My shiny new post', # Update the placeholder text
  format_using: -> (value) { value.truncate 3 } # Format the output
```

## Textarea

The textarea field renders a `textarea` element and supports the following options:

```ruby
textarea :body,
  name: 'Post contents',
  required: true,
  readonly: true,
  placeholder: 'My shiny new post',
  format_using: -> (value) { value.truncate 3 },
  rows: 5 # The size of the element
```
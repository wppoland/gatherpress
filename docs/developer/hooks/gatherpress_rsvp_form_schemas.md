# gatherpress_rsvp_form_schemas


Filters the RSVP form schemas stored for a post.

The blocks in the post are the default source, and they remain the
only source when nothing filters. A consumer that composes its form
somewhere other than the editor can supply its own schemas here, or
merge them with the block-derived ones, and they survive the save
rather than being cleared as soon as the post has no RSVP Form block.

The stored shape is a map of form ID to `array( 'fields' => array,
'hash' => string )`, where each field carries `name`, `type`,
`required`, `label` and `placeholder`, plus `validation`, `options`
or `max_length` depending on the type. `Rsvp_Form::get_field_options()`
and the REST and POST submission handlers all read that shape, so a
schema supplied here is validated and persisted like any other.

Returning an empty array clears the meta, which is what an editor
composed post with no RSVP Form block does today.

## Auto-generated Example

```php
add_filter(
   'gatherpress_rsvp_form_schemas',
    function(
        array,
        int $post_id
    ) {
        // Your code here.
        return array;
    },
    10,
    2
);
```

## Parameters

- `array` $schemas Schemas extracted from the post's blocks, keyed by form ID. Other variable names: `$schemas`
- *`int`* `$post_id` The post ID being saved.

## Returns

`array` Schemas to store for the post, keyed by form ID.

## Files

- [includes/core/classes/blocks/class-rsvp-form.php:458](https://github.com/GatherPress/gatherpress/blob/develop/includes/core/classes/blocks/class-rsvp-form.php#L458)
```php
apply_filters( 'gatherpress_rsvp_form_schemas', $schemas, $post_id )
```



[← All Hooks](Hooks.md)

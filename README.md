# Converts a string to different naming conventions.


### The code


```php
/**
 * Converts a string to different naming conventions.
 *
 * @since  1.0.0
 *
 * @author Lee Anthony https://seothemes.com
 *
 * @param string $string String to convert.
 * @param string $case   Naming convention.
 *
 * @return string
 */
function convert_case( $string, $case = 'snake' ) {
	$delimiters = 'sentence' === $case ? [ ' ', '-', '_' ] : [ ' ', '-', '_', '.' ];
	$lower      = trim( str_replace( $delimiters, $delimiters[0], strtolower( $string ) ), $delimiters[0] );
	$upper      = trim( ucwords( $lower ), $delimiters[0] );
	$pieces     = explode( $delimiters[0], $lower );

	$cases = [
		'camel'    => lcfirst( str_replace( ' ', '', $upper ) ),
		'pascal'   => str_replace( ' ', '', $upper ),
		'snake'    => strtolower( implode( '_', $pieces ) ),
		'ada'      => str_replace( ' ', '_', $upper ),
		'macro'    => strtoupper( implode( '_', $pieces ) ),
		'kebab'    => strtolower( implode( '-', $pieces ) ),
		'train'    => lcfirst( str_replace( ' ', '-', $upper ) ),
		'cobol'    => strtoupper( implode( '-', $pieces ) ),
		'lower'    => strtolower( $string ),
		'upper'    => strtoupper( $string ),
		'title'    => $upper,
		'sentence' => ucfirst( $lower ),
		'dot'      => strtolower( implode( '.', $pieces ) ),
	];

	return $cases[ $case ];
}
```


### How to use


Copy and paste the helper function into your project, then use it:

```php
// Outputs: thisIsAnExampleString
echo convert_case( 'This is_an example-string.', 'camel' );
```


### Available cases


| Case      | Example |
| --------- | ------- |
| camel:    | myNameIsBond |
| pascal:   | MyNameIsBond |
| snake:    | my_name_is_bond |
| ada:      | My_Name_Is_Bond |
| macro:    | MY_NAME_IS_BOND |
| kebab:    | my-name-is-bond |
| train:    | My-Name-Is-Bond |
| cobol:    | MY-NAME-IS-BOND |
| lower:    | my name is bond |
| upper:    | MY NAME IS BOND |
| title:    | My Name Is Bond |
| sentence: | My name is bond |
| dot:      | my.name.is.bond |

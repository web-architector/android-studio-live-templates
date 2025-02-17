# Шаблоны для Freezed
  
  
| Name                       | Expression                   | Default value                                       | Skip if defined |
|----------------------------|------------------------------|-----------------------------------------------------|-----------------|
| `NAME`                     |                              | `capitalize(camelCase(fileNameWithoutExtension()))` |                 |
| `fileNameWithoutExtension` | `fileNameWithoutExtension()` | `""`                                                | `x`             |

  
---
  
`freezed`
```dart
import 'package:freezed_annotation/freezed_annotation.dart';
import 'package:flutter/foundation.dart';

part '$fileNameWithoutExtension$.freezed.dart';

@freezed
abstract class $NAME$<$T$> with _$$$NAME$<$T$> {
  const factory $NAME$.enterNameHere({
      @required $T$ id,
      $END$
  }) = _$NAME$;
}
```
---
  
`freezedWithJSON`
```dart
import 'package:freezed_annotation/freezed_annotation.dart';

part '$fileNameWithoutExtension$.freezed.dart';
part '$fileNameWithoutExtension$.g.dart';

@freezed
abstract class $NAME$ with _$$$NAME$ {
  const factory $NAME$({
    @required @JsonKey(name: 'id', required: true, disallowNullValue: true) int id,
    $END$
  }) = _$NAME$;

  /// Generate Class from Map<String, dynamic>
  factory $NAME$.fromJson(Map<String, dynamic> json) => _$$$NAME$FromJson(json);
}
```
---
  
`freezedUnion`
| Name                       | Expression                   | Default value                                       | Skip if defined |
|----------------------------|------------------------------|-----------------------------------------------------|-----------------|
| `NAME`                     |                              | `capitalize(camelCase(fileNameWithoutExtension()))` |                 |
| `fileNameWithoutExtension` | `fileNameWithoutExtension()` | `""`                                                | `x`             |
| `A1                      ` |                              | `capitalize(camelCase(A))`                          | `x`             |
| `B1                      ` |                              | `capitalize(camelCase(B))`                          | `x`             |

```dart
import 'package:freezed_annotation/freezed_annotation.dart';

part '$fileNameWithoutExtension$.freezed.dart';
part '$fileNameWithoutExtension$.g.dart';

@freezed
abstract class $NAME$ with _$$$NAME$ {
  const $NAME$._();

  const factory $NAME$.$A$({
    @required @JsonKey(name: 'id', required: true, disallowNullValue: true) int id,
    $END$
  }) = _$A1$;

  const factory $NAME$.$B$({
    @required @JsonKey(name: 'id', required: true, disallowNullValue: true) int id,
    $END$
  }) = _$B1$;

  /// Generate Class from Map<String, dynamic>
  factory $NAME$.fromJson(Map<String, dynamic> json) => _$$$NAME$FromJson(json);
}
``` 

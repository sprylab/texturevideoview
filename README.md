TextureVideoView for Android
============================

A `VideoView` based on the official Android 7.1.1_r13 sources using a `TextureView` instead of a `SurfaceView` by [sprylab technologies GmbH][1]. It will work on Android 4.0+ (API level 15 and above).

The main advantages of this drop-in replacement compared to the original `VideoView` are the following:

* extends `android.view.TextureView` instead of a `android.view.SurfaceView` thus allowing proper view animations as described in the [Property Animation API guide][2]
* API addition: Call `setShouldRequestAudioFocus(true)` to programmatically disable audio focus request before opening a video file -
  default behaviour is unchanged and complies with the current `VideoView` implementation (thanks to @ezaquarii)
* fixed a sizing bug when auto-starting the video with view size != video size (thanks to @lhunath)
* fixed various memory leaks
  * potential leak by releasing surface when destroyed
  * potential activity leak when streaming videos over HTTP(S) (thanks to @koral)
  * potential activity leak caused by AudioMananger on Android pre-6.0 devices (thanks to @hzsweers)

Unfortunately, code that uses hidden APIs and thus is not publicly available had to be removed (e.g. subtitle support).

Download
--------

Download [the latest JAR][3] or grab via Maven:
```xml
<dependency>
  <groupId>com.sprylab.android.texturevideoview</groupId>
  <artifactId>texturevideoview</artifactId>
  <version>1.2.0</version>
</dependency>
```
or Gradle:
```groovy
compile 'com.sprylab.android.texturevideoview:texturevideoview:1.2.0'
```

License
=======

    Copyright 2014-2016 sprylab technologies GmbH

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

Note: The sample application includes a trailer for [Big Buck Bunny][4], which is released under the [Creative Commons Attribution 3.0][5] license.

 [1]: https://sprylab.com
 [2]: https://developer.android.com/guide/topics/graphics/prop-animation.html
 [3]: http://repository.sonatype.org/service/local/artifact/maven/redirect?r=central-proxy&g=com.sprylab.android.texturevideoview&a=texturevideoview&v=LATEST
 [4]: http://www.bigbuckbunny.org
 [5]: http://creativecommons.org/licenses/by/3.0/

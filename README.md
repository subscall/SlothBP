# More Breakpoints!

# SlothBP

Collaborative Breakpoint Manager for x64dbg.

![screenshot](https://i.imgur.com/v07n6LT.png)

## Example INI

```
[Memory]
VirtualAlloc="kernel32.VirtualAlloc"

[Code Injection]
SetWindowsHookEx="user32.SetWindowsHookEx"

[Networking]
UrlDownloadToFile="urlmon.UrlDownloadToFile"
```

See [SlothBP.ini](https://github.com/x64dbg/SlothBP/blob/master/SlothBP.ini) for a more complete example.

## How to use

* Download relases from [Release] (https://ci.appveyor.com/project/mrexodia/slothbp/build/artifacts)
* Place Plugin in x32/64 plugin directory
* Debug your favorite target and set the breakpoints from the menu items.

Alternatively you can fork and compile the source code.

### Sharing ini's.

The 'Collaborative' part comes with the ability to share your own INI files with predefined breakpoints.
The format is simple:

Add a category

```
[SomeCategory]
```
The fields are in a APIName = BreakpointName format, meaning that APIName will be the menu item name, and BreakpointName is a module.apiname format. This allows the plugin to automatically set the correct breakpoint. (The module isnt necessarily required but definitely recommended).

```
SomeApi = module.SomeApi
```

Thanks to:
* @mrexodia
* [anuj](https://twitter.com/asoni)
* All others who provided input

Feel free to share your INI configurations!
---------------------------------------------------------------------------------
```
Build started
git clone -q --branch=master https://github.com/x64dbg/SlothBP.git C:\projects\slothbp
git checkout -qf 176d161e753883fc1ce9fafb5604c1b408c673ed
msbuild.exe SlothBP.sln /verbosity:minimal /t:Build /p:Configuration=Release;Platform=Win32
Microsoft (R) Build Engine version 14.0.25420.1
Copyright (C) Microsoft Corporation. All rights reserved.
  plugin.cpp
  pluginmain.cpp
     Creating library C:\projects\slothbp\bin\x32\SlothBP.lib and object C:\projects\slothbp\bin\x32\SlothBP.exp
  Generating code
  Finished generating code
  SlothBP.vcxproj -> C:\projects\slothbp\bin\x32\SlothBP.dp32
msbuild.exe SlothBP.sln /verbosity:minimal /t:Build /p:Configuration=Release;Platform=x64
Microsoft (R) Build Engine version 14.0.25420.1
Copyright (C) Microsoft Corporation. All rights reserved.
  plugin.cpp
  pluginmain.cpp
     Creating library C:\projects\slothbp\bin\x64\SlothBP.lib and object C:\projects\slothbp\bin\x64\SlothBP.exp
  Generating code
  Finished generating code
  SlothBP.vcxproj -> C:\projects\slothbp\bin\x64\SlothBP.dp64
call release.bat
        1 file(s) copied.
        1 file(s) copied.
        1 file(s) copied.
        1 file(s) copied.
Discovering tests...OK
Collecting artifacts...
Found artifact 'release' matching 'release' path
Uploading artifacts...
[1/1] release.zip (195,302 bytes)...100%
````
---------------------------------------------
Build success

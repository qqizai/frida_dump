# frida_dump

## 1. 使用dump_so

```Text
> frida -U packagename -l dump_so.js
     ____
    / _  |   Frida 12.4.8 - A world-class dynamic instrumentation toolkit
   | (_| |
    > _  |   Commands:
   /_/ |_|       help      -> Displays the help system
   . . . .       object?   -> Display information about 'object'
   . . . .       exit/quit -> Exit
   . . . .
   . . . .   More info at http://www.frida.re/docs/home/

[LGE AOSP on HammerHead::packagename]-> dump_so("name.so")
[name]: name.so
[base]: 0x99adf000
[size]: 0x2d4000
[path]: /data/app/packagename-2/lib/arm/name.so
[dump]: /data/user/0/packagename/files/name.so_0x99adf000_0x2d4000.so
undefined
[LGE AOSP on HammerHead::packagename]->
```

## 2. 使用dump_dex

目前仅支持Android8,Android9 arm64系统，如果需要适配其他系统，请修改DefineClass的函数签名和base, size

```Text
frida -U --no-pause -f packagename  -l dump_dex.js
     ____
    / _  |   Frida 12.4.8 - A world-class dynamic instrumentation toolkit
   | (_| |
    > _  |   Commands:
   /_/ |_|       help      -> Displays the help system
   . . . .       object?   -> Display information about 'object'
   . . . .       exit/quit -> Exit
   . . . .
   . . . .   More info at http://www.frida.re/docs/home/
Spawned `packagename`. Resuming main thread!
[Google Pixel XL::packagename]-> [dlopen:] libart.so
_ZN3art11ClassLinker11DefineClassEPNS_6ThreadEPKcmNS_6HandleINS_6mirror11ClassLoaderEEERKNS_7DexFileERKNS9_8ClassDefE 0x7ac6dc4f74
[DefineClass:] 0x7ac6dc4f74
[dump dex]: /data/data/packagename/files/7aab800000_8341c4.dex
```

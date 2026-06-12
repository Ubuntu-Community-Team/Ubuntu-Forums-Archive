---
title: "Dyson"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by PolloE on 2009-07-10
Hi, i tried to play dyson, [http://www.dyson-game.com/read.php?page=8](http://www.dyson-game.com/read.php?page=8) 
i downloaded and extracted the archive and i know that im meant to download and install some packages, but i dont know how:

    * mono
    * libmono-i18n (and perhaps other basic mono stuff)
    * libgdiplus
    * libsdl
    * libsdl-gfx
    * libsdl-mixer
    * libsdl-image
    * libvorbis
    * libpng

please tell me what to type or were to get it. thanks!

~PolloE

---

### Post by directhex on 2009-07-11
> **PolloE said:**
> Hi, i tried to play dyson, [http://www.dyson-game.com/read.php?page=8](http://www.dyson-game.com/read.php?page=8) 
i downloaded and extracted the archive and i know that im meant to download and install some packages, but i dont know how:

    * mono
    * libmono-i18n (and perhaps other basic mono stuff)
    * libgdiplus
    * libsdl
    * libsdl-gfx
    * libsdl-mixer
    * libsdl-image
    * libvorbis
    * libpng

please tell me what to type or were to get it. thanks!

~PolloE

You probably already have it. Try "mono Dyson.exe"

---

### Post by directhex on 2009-07-11
> **PolloE said:**
> Hi, i tried to play dyson, [http://www.dyson-game.com/read.php?page=8](http://www.dyson-game.com/read.php?page=8) 
i downloaded and extracted the archive and i know that im meant to download and install some packages, but i dont know how:

    * mono
    * libmono-i18n (and perhaps other basic mono stuff)
    * libgdiplus
    * libsdl
    * libsdl-gfx
    * libsdl-mixer
    * libsdl-image
    * libvorbis
    * libpng

please tell me what to type or were to get it. thanks!

~PolloE

You probably already have it. Try "mono Dyson.exe"

Doesn't run on 64-bit though.

---

### Post by PolloE on 2009-07-11
> **directhex said:**
> You probably already have it. Try "mono Dyson.exe"

Doesn't run on 64-bit though.

K, i'll try, so do I just go to the command bar and type.... 

mono dyson.exe


?????

---

### Post by PolloE on 2009-07-11
K, so I put the folder in my home folder, then i went to the folder in the terminal (with CD) and typed "mono dyson.exe"

and it replied:

> [FONT="Courier New"]The assembly mscorlib.dll was not found or could not be loaded.
It should have been installed in the "/usr/lib/mono/1.0/mscorlib.dll" directory.[/FONT]


i think im missing something...

---

### Post by directhex on 2009-07-11
> **PolloE said:**
> K, so I put the folder in my home folder, then i went to the folder in the terminal (with CD) and typed "mono dyson.exe"

and it replied:



i think im missing something...

mono-1.0-devel should pull in the .net 1.1 crap (Jaunty is 2.0-only)

---

### Post by PolloE on 2009-07-11
so the code is

```

mono-1.0-devel
```

---

### Post by Partyboi2 on 2009-07-11
Hi, from the terminal you can install mono-1.0-devel with
```
sudo apt-get install mono-1.0-devel
``` If you want mono-2.0-devel instead replace mono-1.0-devel with mono-2.0-devel 
```
sudo apt-get install mono-2.0-devel
```

---

### Post by PolloE on 2009-07-11
k....

so typing  
```

mono-1.0-devel
```

by itslef didnt work... it said that mono wasnt a command.... what do I type EXACLY?


Thabks tho!!!!!!!

~PolloE


EDIT,

 the post above me wasnt there when I wrote this... tahnks!!!!

---

### Post by PolloE on 2009-07-11
k.... so now i should just have to type

```
mono Dyson.exe
```

right? well i did, but it replied with:

```
** (Dyson.exe:5368): WARNING **: The following assembly referenced from /home/raul/dyson/Dyson.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=7)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/raul/dyson/).


** (Dyson.exe:5368): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (Dyson.exe:5368): WARNING **: Missing method get_PrimaryScreen in assembly /home/raul/dyson/Dyson.exe, type System.Windows.Forms.Screen

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
File name: 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'
  at Dyson.Game.Main () [0x00000] 
```

what am I missing now???

Thanks for all the help so far though!!!!!

~PolloE

---

### Post by Partyboi2 on 2009-07-11
Try installing the libmono-winforms2.0-cil package.
```
sudo apt-get install libmono-winforms2.0-cil
```
then
```
mono Dyson.exe
```


[B]
[/B]

---

### Post by PolloE on 2009-07-11
i did... now there is something else (sorry for buthering so much) it replied to

```
mono Dyson.exe
```

with

```
Stacktrace:

  at (wrapper managed-to-native) System.Windows.Forms.X11Keyboard.XOpenIM (intptr,intptr,intptr,intptr) <0x00004>
  at (wrapper managed-to-native) System.Windows.Forms.X11Keyboard.XOpenIM (intptr,intptr,intptr,intptr) <0xffffffff>
  at System.Windows.Forms.X11Keyboard.SetupXIM () <0x000c3>
  at System.Windows.Forms.X11Keyboard.EnsureLayoutInitialized () <0x0005a>
  at System.Windows.Forms.X11Keyboard..ctor (intptr,intptr) <0x00096>
  at System.Windows.Forms.XplatUIX11.SetDisplay (intptr) <0x004b2>
  at System.Windows.Forms.XplatUIX11..ctor () <0x000b1>
  at System.Windows.Forms.XplatUIX11.GetInstance () <0x0003b>
  at System.Windows.Forms.XplatUI..cctor () <0x000e6>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at System.Windows.Forms.SystemInformation.get_VirtualScreen () <0xffffffff>
  at System.Windows.Forms.SystemInformation.get_VirtualScreen () <0x0000f>
  at System.Windows.Forms.Screen..cctor () <0x00024>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Dyson.Game..ctor () <0xffffffff>
  at Dyson.Game..ctor () <0x003f8>
  at Dyson.Game.Main () <0x00016>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	mono [0x806d944]
	mono [0x808616b]
	[0xb7f96410]
	/usr/lib/libX11.so.6 [0xb702c21f]
	/usr/lib/libX11.so.6(XrmQGetResource+0x3e) [0xb7042dce]
	/usr/lib/libX11.so.6(XStringToKeysym+0x149) [0xb703a1b9]
	/usr/lib/libX11.so.6(_XimParseStringFile+0xd9a) [0xb706cf9a]
	/usr/lib/libX11.so.6(_XimLocalOpenIM+0x434) [0xb706aa84]
	/usr/lib/libX11.so.6(_XimOpenIM+0x13d) [0xb706912d]
	/usr/lib/libX11.so.6(XOpenIM+0x4a) [0xb704d08a]
	[0xb6652cfc]
	[0xb6652b64]
	[0xb66667b3]
	[0xb66664e7]
	[0xb6fa9aeb]
	[0xb6fa24da]
	[0xb6fa20c4]
	[0xb6fa1487]
	[0xb789d1ae]
	mono [0x80be75d]
	mono(mono_runtime_class_init+0x19) [0x80bee19]
	mono [0x81b1d6e]
	mono [0x807029f]
	[0xb7ba7066]
	[0xb6fa11ad]
	[0xb789d1ae]
	mono [0x80be75d]
	mono [0x8198c48]
	mono [0x81afc95]
	mono [0x81b1ba1]
	mono [0x807029f]
	[0xb7ba7066]
	[0xb78a4497]
	[0xb789d1ae]
	mono(mono_runtime_exec_main+0xe5) [0x80bad75]
	mono(mono_runtime_run_main+0x16b) [0x80bb4eb]
	mono(mono_main+0x1727) [0x805c917]
	mono [0x805ac62]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7d2e775]
	mono [0x805aba1]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7ce46e0 (LWP 3647)]
[New Thread 0xb74dfb90 (LWP 3649)]
[New Thread 0xb7503b90 (LWP 3648)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7f96430 in __kernel_vsyscall ()
  3 Thread 0xb7503b90 (LWP 3648)  0xb7f96430 in __kernel_vsyscall ()
  2 Thread 0xb74dfb90 (LWP 3649)  0xb7f96430 in __kernel_vsyscall ()
  1 Thread 0xb7ce46e0 (LWP 3647)  0xb7f96430 in __kernel_vsyscall ()

Thread 3 (Thread 0xb7503b90 (LWP 3648)):
#0  0xb7f96430 in __kernel_vsyscall ()
#1  0xb7eae8f6 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081492e8 in ?? ()
#3  0xb7ea74ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7dfc49e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb74dfb90 (LWP 3649)):
#0  0xb7f96430 in __kernel_vsyscall ()
#1  0xb7eab0e5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c607 in ?? ()
#3  0x0814f1f4 in ?? ()
#4  0x0814f25c in ?? ()
#5  0x08169b02 in ?? ()
#6  0x080d565a in ?? ()
#7  0x080f7639 in ?? ()
#8  0x081653b6 in ?? ()
#9  0x081833b5 in ?? ()
#10 0xb7ea74ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7dfc49e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7ce46e0 (LWP 3647)):
#0  0xb7f96430 in __kernel_vsyscall ()
#1  0xb7df8a87 in syscall () from /lib/tls/i686/cmov/libc.so.6
#2  0x0806d9e7 in ?? ()
#3  0x0808616b in ?? ()
#4  <signal handler called>
#5  0xb7ea89e0 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6  0xb702c21f in ?? () from /usr/lib/libX11.so.6
#7  0xb7042dce in XrmQGetResource () from /usr/lib/libX11.so.6
#8  0xb703a1b9 in XStringToKeysym () from /usr/lib/libX11.so.6
#9  0xb706cf9a in _XimParseStringFile () from /usr/lib/libX11.so.6
#10 0xb706aa84 in _XimLocalOpenIM () from /usr/lib/libX11.so.6
#11 0xb706912d in _XimOpenIM () from /usr/lib/libX11.so.6
#12 0xb704d08a in XOpenIM () from /usr/lib/libX11.so.6
#13 0xb6652cfc in ?? ()
#14 0xb6652b64 in ?? ()
#15 0xb66667b3 in ?? ()
#16 0xb66664e7 in ?? ()
#17 0xb6fa9aeb in ?? ()
#18 0xb6fa24da in ?? ()
#19 0xb6fa20c4 in ?? ()
#20 0xb6fa1487 in ?? ()
#21 0xb789d1ae in ?? ()
#22 0x080be75d in ?? ()
#23 0x080bee19 in mono_runtime_class_init ()
#24 0x081b1d6e in ?? ()
#25 0x0807029f in ?? ()
#26 0xb7ba7066 in ?? ()
#27 0xb6fa11ad in ?? ()
#28 0xb789d1ae in ?? ()
#29 0x080be75d in ?? ()
#30 0x08198c48 in ?? ()
#31 0x081afc95 in ?? ()
#32 0x081b1ba1 in ?? ()
#33 0x0807029f in ?? ()
#34 0xb7ba7066 in ?? ()
#35 0xb78a4497 in ?? ()
#36 0xb789d1ae in ?? ()
#37 0x080bad75 in mono_runtime_exec_main ()
#38 0x080bb4eb in mono_runtime_run_main ()
#39 0x0805c917 in mono_main ()
#40 0x0805ac62 in ?? ()
#41 0xb7d2e775 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#42 0x0805aba1 in ?? ()
#0  0xb7f96430 in __kernel_vsyscall ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
```

THANKS AGAIN!!!!

~PolloE

---

### Post by Partyboi2 on 2009-07-12
Looks like there could be a bug with mono as mentioned [[COLOR=Blue]here[/COLOR]]("http://www.dyson-game.com/smf/index.php?topic=129.0;wap2"). The workaround mentioned is to set 'MONO_WINFORMS_XIM_STYLE=disabled' as a environment variable.
Open a terminal and type
```
gksu gedit ~/.bashrc
```at the bottom of the file that opens add
```
export MONO_WINFORMS_XIM_STYLE=disabled
``` then save the changes and close gedit. You can either Ctrl+Alt+Backspace (if you have this functioned enabled) or you will need to reboot for the changes to take effect.

---

### Post by directhex on 2009-07-12
> **PolloE said:**
> k.... so now i should just have to type

```
mono Dyson.exe
```

right? well i did, but it replied with:

```
** (Dyson.exe:5368): WARNING **: The following assembly referenced from /home/raul/dyson/Dyson.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=7)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/raul/dyson/).


** (Dyson.exe:5368): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (Dyson.exe:5368): WARNING **: Missing method get_PrimaryScreen in assembly /home/raul/dyson/Dyson.exe, type System.Windows.Forms.Screen

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
File name: 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'
  at Dyson.Game.Main () [0x00000] 
```

what am I missing now???

[libmono-winforms2.0-cil](apt:libmono-winforms2.0-cil)

---


---
title: "OpenOffice crashing X"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by ArsGeek on 2006-10-31
Hey Folks,

I've been having a weird problem with my Edgy laptop recently.  Whenever I open OpenOffice either through a menu, or by double clicking on a document, X crashes completely.  

I'm currently using a dual monitor setup with Xinerama on an IBM X60 with an i915 graphics controller.

I've included the Backtrace from my xorg.0 log as well as my xorg.conf file below.  Note that I've been commenting out stuff in the xorg.conf file in an attempt to stop this behavior.  

When I start X with a standard xorg.conf file (which is remarkably like my dual monitor file) Openoffice acts normally and X does not crash.  

Before I did a fresh install of Edy, this same xorg.conf file was working fine in 6.06.  

Any help, pointers or links would be wonderful.

Here's the Backtrace:
[INDENT]Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/lib/xorg/modules/extensions/libglx.so [0xb7cb0946]
3: /usr/lib/xorg/modules/extensions/libglx.so(__glXleaveServer+0x22) [0xb7c8cc62
]
4: /usr/lib/xorg/modules/extensions/libglx.so [0xb7c8d2fe]
5: /usr/X11R6/bin/X(Dispatch+0x18f) [0x808693f]
6: /usr/X11R6/bin/X(main+0x485) [0x806e715]
7: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7dcb8cc]
8: /usr/X11R6/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting[/INDENT]

Here's my xorg.conf file:

[INDENT]
Section "Files"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
#FontPath "/usr/share/fonts/X11/CID"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
#FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#Load "GLcore"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

# Section "Extensions"
# Option "Composite" "Enable"
# EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection


Section "Device"
Identifier "intel0"
Driver "i810"
BusID "PCI:0:2:0"
Option "MonitorLayout" "CRT,LFP"
VideoRam 131072
Screen 0
#Option "DevicePresence" "true"
#Option "DRI" "true"
# Option "ForceBIOS" "800x600=1400x1050"
# Option "FlipPrimary" "true"
EndSection

Section "Device"
Identifier "intel1"
# Option "Rotate" "CCW"
Driver "i810"
BusID "PCI:0:2:0"
Screen 1
#Option "DRI" "true"
#Option "GLX" "true"
#Option "DevicePresence" "true"
# Option "ForceBIOS" "1920x1440=1920x1200"
# Option "FlipPrimary" "true"
EndSection

Section "Monitor"
Identifier "Internal"
Option "DPMS"
EndSection

Section "Monitor"
Identifier "dell1905"
Option "DPMS"
Modeline "1280x1024" 114.98 1280 1312 1744 1776 1024 1045 1055 1076

DisplaySize 519 324
HorizSync 30-81
VertRefresh 60-60
# Modeline "1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235
EndSection

Section "Screen"
Identifier "builtinlcd"
Device "intel0"
Monitor "Internal"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection

Section "Screen"
Identifier "externallcd"
Device "intel1"
Monitor "dell1905"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1280x1024"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Xinerama"
Screen 0 "builtinlcd" 0 0
Screen 1 "externallcd" RightOf "builtinlcd"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
Option "Xinerama" "False"
EndSection

Section "DRI"
Mode 0666
EndSection[/INDENT]

---

### Post by handband2 on 2006-10-31
> **ArsGeek said:**
> Hey Folks,

I've been having a weird problem with my Edgy laptop recently.  Whenever I open OpenOffice either through a menu, or by double clicking on a document, X crashes completely.  

I'm currently using a dual monitor setup with Xinerama on an IBM X60 with an i915 graphics controller.

I've included the Backtrace from my xorg.0 log as well as my xorg.conf file below.  Note that I've been commenting out stuff in the xorg.conf file in an attempt to stop this behavior.  

When I start X with a standard xorg.conf file (which is remarkably like my dual monitor file) Openoffice acts normally and X does not crash.  

Before I did a fresh install of Edy, this same xorg.conf file was working fine in 6.06.  

Any help, pointers or links would be wonderful.


ArsGeek,

Many are having problems with Xinerama.  I was one of them.  When running Xinerama gnome-terminal wouldn't launch and some of my 3D games didn't run at full speed.  
I noticed you are running an intel chipset.  I was lucky to be running on an NVIDIA.  This allowed me to switch to Twinview.

Though you're not running on a NVIDIA graphics chipset your problem might be associated to this:
[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232]("https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232")

---

### Post by okl on 2006-10-31
Start OpenOffice with a normal (non-dualhead) xorg.conf and then in OO go to options VIEW and uncheck all in the box called 3D...
Then close OO again stop xorg and restart it with your quoted xorg.conf.
Now OO should work fine.
It is a problem with dri on dualhead configurations.
Would be intersting to see what happens if you open a console and type glxinfo. Should be the same x-crash.
okl

---

### Post by ArsGeek on 2006-10-31
Hey okl,

No dice with this one.  I made sure all the options were unchecked under 3D in open office but I'm still getting a crash when I try to restart it, with the same error as in my first post.

Thanks for the suggestion though!

Interstingly, I did get the same crash/error with the glxinfo bit.

> **okl said:**
> Start OpenOffice with a normal (non-dualhead) xorg.conf and then in OO go to options VIEW and uncheck all in the box called 3D...
Then close OO again stop xorg and restart it with your quoted xorg.conf.
Now OO should work fine.
It is a problem with dri on dualhead configurations.
Would be intersting to see what happens if you open a console and type glxinfo. Should be the same x-crash.
okl

---

### Post by okl on 2006-10-31
> **ArsGeek said:**
> 
Interstingly, I did get the same crash/error with the glxinfo bit.

Could you just try to comment out the lines which load glx and dri and the dri section at the end of your xorg.conf.
#load glx
#load dri
#Section "DRI"
#        Mode    0666
#EndSection


I had the same problem with matrox-dualhead configuration but without glx and dri (which you can't use anyhow because glxinfo is crashing) OO starts without crashing.

In the meantime I downgraded to OO 2.0.2 because of the "ugly fonts" situation in OO 2.0.4.

okl

---

### Post by ArsGeek on 2006-10-31
That worked.

In my multitude of edits to the xorg.conf file I had thought I did that and restarted with the same results (which further baffled me). Turns out I just thought I had done it without actually doing it.

Thanks for the jog to my memory and the fix.



> **okl said:**
> Could you just try to comment out the lines which load glx and dri and the dri section at the end of your xorg.conf.
#load glx
#load dri
#Section "DRI"
#        Mode    0666
#EndSection


I had the same problem with matrox-dualhead configuration but without glx and dri (which you can't use anyhow because glxinfo is crashing) OO starts without crashing.

In the meantime I downgraded to OO 2.0.2 because of the "ugly fonts" situation in OO 2.0.4.

okl

---

### Post by makhand on 2006-11-13
> **okl said:**
> Could you just try to comment out the lines which load glx and dri and the dri section at the end of your xorg.conf.
#load glx
#load dri
#Section "DRI"
#        Mode    0666
#EndSection


I had the same problem with matrox-dualhead configuration but without glx and dri (which you can't use anyhow because glxinfo is crashing) OO starts without crashing.

In the meantime I downgraded to OO 2.0.2 because of the "ugly fonts" situation in OO 2.0.4.

okl

Thank you for this, it fixed my OpenOffice and Screensaver as well. I'm also running a dual setup, though i dont think i'm using either twinview or xinerama. I have a i810 card. 

However, I still cant log into gnome as is. it freezes. I have to login to a failsafe terminal, then start metacity, gnome-panel, and nautilus. The gnome-settings-daemon that does nice things like themes doesnt work. 
I get the following crash report: 
```
Memory status: size: 28176384 vsize: 0 resident: 28176384 share: 0 rss: 7094272 rss_rlim: 0
CPU usage: start_time: 1163442290 rtime: 0 utime: 13 stime: 0 cutime:9 cstime: 0 timeout: 4 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-settings-daemon'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
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
[Thread debugging using libthread_db enabled]
[New Thread -1226365264 (LWP 4763)]
[New Thread -1227617376 (LWP 4765)]
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
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb77fa34b in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ef81b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0x0806915d in keyboard_config_registry_get_type ()
#5  0xb782a89a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#6  0xb7811952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
#7  0xb780fbdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#8  0xb781073f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#9  0xb78108f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#10 0x08058169 in gnome_settings_keyboard_xkb_init ()
#11 0x080551ea in gnome_settings_daemon_new ()
#12 0x08053efc in main ()

Thread 2 (Thread -1227617376 (LWP 4765)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb77f93fb in __read_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb776245d in g_main_context_wakeup () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb777f38f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb77f3504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#5  0xb76b151e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1226365264 (LWP 4763)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb77fa34b in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ef81b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0x0806915d in keyboard_config_registry_get_type ()
No symbol table info available.
#5  0xb782a89a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#6  0xb7811952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#7  0xb780fbdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#8  0xb781073f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#9  0xb78108f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#10 0x08058169 in gnome_settings_keyboard_xkb_init ()
No symbol table info available.
#11 0x080551ea in gnome_settings_daemon_new ()
No symbol table info available.
#12 0x08053efc in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
```

What is the issue with edgy? All of this stuff worked perfectly with Dapper. It would take so long to go back to it and i have a lot of work to do.

---

### Post by makhand on 2006-11-14
Hey all, I've had success following the step by step intro and then Xinerama setup found at [http://www.ubuntuforums.org/showthread.php?t=221174](http://www.ubuntuforums.org/showthread.php?t=221174)

Everything seems to work now. its like a dream

---


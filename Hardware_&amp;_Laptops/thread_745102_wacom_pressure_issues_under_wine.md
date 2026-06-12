---
title: "wacom pressure issues under wine"
date: 2008-04-04
forum: Hardware &amp; Laptops
---

### Post by thesleepless on 2008-04-04
okay, i am running ubuntu 8.04 beta, it's running pretty well

i've got my usb wacom graphire2 plugged in, it's come up as /dev/input/event2 with symlinks to wacom and tablet-graphire2-4x5 as it should

xorg.conf is set up and it's lets me use the tablet as it should in absolute mode, pressure sensitivity works in The Gimp

however running xxd /dev/input/wacom remains blank when i move the stylus over the tablet (this didn't occur under earlier attempts on other distros) and ArtRage running under wine is unable to access the pressure sensitivity information like it does on other distros

anyone else have this or similar issues and perhaps know a solution?

---

### Post by oedipuss on 2008-04-19
I have the exact same issue. 
In fact it has been so since gutsy, with the wine deb, but then I would compile wine from source, and pressure would work. 
I've tried compiling it now in hardy rc, but still no pressure. I'd try again, but compiling takes so much time... 

xxd behaves the same way here too. It shows data for the regular mouse and keyboard, but nothing for the wacom stylus / mouse.

I've tried with artrage full (updated to latest) and starter edition, with the same results.
I don't think it's related to artrage specifically, but do you know of any other small free programs besides Artrage we can test pressure with ?

---

### Post by vries on 2008-04-21
I'm currently using Arch Linux but I've encountered the same problem. If the same thing is causing it, I will be able to help you.
First of all I need to know output of:
xidump -l
xsetpointer -l
WINEDEBUG=wintab32 wine xxx.exe 
(where xxx is name of .exe file you want to run)

sorry for my bad english

---

### Post by oedipuss on 2008-04-21
```
~$ xidump -l
Virtual core keyboard          keyboard
Virtual core pointer           disabled
Generic Keyboard               unknown
Configured Mouse               unknown
eraser                         unknown
cursor                         unknown
stylus                         unknown

```

```
~$ xsetpointer -l
0: "Virtual core keyboard"	[XKeyboard]
1: "Virtual core pointer"	[XPointer]
2: "Generic Keyboard"	[XExtensionKeyboard]
3: "Configured Mouse"	[XExtensionPointer]
4: "eraser"	[XExtensionPointer]
5: "cursor"	[XExtensionPointer]
6: "stylus"	[XExtensionPointer]

```

```
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:win:EnumDisplayDevicesW ((null),0,0x32f53c,0x00000000), stub!
preloader: Warning: failed to reserve range 00000000-00010000
fixme:process:RegisterApplicationRestart (L"-rm",0)
preloader: Warning: failed to reserve range 00000000-00010000
trace:wintab32:DllMain 0x7dc40000, 1, (nil)
trace:wintab32:DllMain Initialization
trace:wintab32:TABLET_WindowProc Incoming Message 0x81  (0x00000000, 0x0032f69c)
trace:wintab32:TABLET_WindowProc Incoming Message 0x83  (0x00000000, 0x0032f64c)
trace:wintab32:TABLET_WindowProc Incoming Message 0x1  (0x00000000, 0x0032f69c)
trace:wintab32:TABLET_WindowProc Incoming Message 0x5  (0x00000000, 0x00000000)
trace:wintab32:TABLET_WindowProc Incoming Message 0x3  (0x00000000, 0x00000000)
trace:wintab32:WTInfoT (0, 0, (nil), 0)
trace:wintab32:LoadTablet Initializing the tablet to hwnd 0x3002a
trace:wintab32:X11DRV_LoadTabletInfo XListInputDevices reports 7 devices
trace:wintab32:X11DRV_LoadTabletInfo Device 0:  [id 0|name Virtual core keyboard|type |num_classes 1|use IsXKeyboard]
trace:wintab32:X11DRV_LoadTabletInfo Device 1:  [id 1|name Virtual core pointer|type |num_classes 2|use IsXPointer]
trace:wintab32:X11DRV_LoadTabletInfo Device 2:  [id 2|name Generic Keyboard|type KEYBOARD|num_classes 1|use Unknown]
trace:wintab32:X11DRV_LoadTabletInfo Device 3:  [id 3|name Configured Mouse|type MOUSE|num_classes 2|use Unknown]
trace:wintab32:X11DRV_LoadTabletInfo Device 4:  [id 4|name eraser|type Wacom Eraser|num_classes 3|use Unknown]
trace:wintab32:X11DRV_LoadTabletInfo Device 5:  [id 5|name cursor|type Wacom Cursor|num_classes 3|use Unknown]
trace:wintab32:X11DRV_LoadTabletInfo Device 6:  [id 6|name stylus|type Wacom Stylus|num_classes 3|use Unknown]
warn:wintab32:X11DRV_LoadTabletInfo Did not find a valid stylus cursor with >= 5 axes, returning 0 valid devices.
trace:wintab32:X11DRV_WTInfoW (0, 0, (nil))
trace:wintab32:X11DRV_WTInfoW 0 cursors
trace:wintab32:WTInfoT returns 0
trace:wintab32:TABLET_WindowProc Incoming Message 0x1c  (0x00000000, 0x00000000)
trace:wintab32:DllMain 0x7dc40000, 0, (nil)
trace:wintab32:DllMain Detaching
trace:wintab32:TABLET_WindowProc Incoming Message 0x2  (0x00000000, 0x00000000)
trace:wintab32:TABLET_WindowProc Incoming Message 0x82  (0x00000000, 0x00000000)

```

Here you go, I hope it helps. Those preloader warnings at the beginning happen with every wine app, I think they've something to do with a new security feature in hardy.
It seems it finds all the tablet devices, but refuses to use them ? Also, the stylus has indeed 5 axes in my case, but other tablets have 3. I can't imagine why it explicitly expects 5..

---

### Post by oedipuss on 2008-04-21
OK i have a solution !!
First, open dlls/winex11.drv/wintab.c (from wine source) .
Around line #623 , there's a check for 5 or more axes which according to a bug report was left there without any particular reason :
```
 if (!axis_read_complete && Val->num_axes >= 5 && cursor->TYPE == CSR_TYPE_PEN)
```

change this to : 
```
if (!axis_read_complete && cursor->TYPE == CSR_TYPE_PEN)
```

It seems it checks for each axis anyway after that, so it's redundant. 

Most importantly, however, change every instance of** IsXExtensionDevice** in that file with **IsXExtension*Pointer***

It works in artrage now, fully supports pressure and tilt. The only perhaps unrelated bug is that there is some weird behaviour when "Precise tablet mode" is enabled from Edit/Preferences menu. That might be related only to artrage, however.

---

### Post by vries on 2008-04-21
> **oedipuss said:**
> OK i have a solution !!
First, open dlls/winex11.drv/wintab.c (from wine source) .
Around line #623 , there's a check for 5 or more axes which according to a bug report was left there without any particular reason :
```
 if (!axis_read_complete && Val->num_axes >= 5 && cursor->TYPE == CSR_TYPE_PEN)
```

change this to : 
```
if (!axis_read_complete && cursor->TYPE == CSR_TYPE_PEN)
```

It seems it checks for each axis anyway after that, so it's redundant. 

Most importantly, however, change every instance of** IsXExtensionDevice** in that file with **IsXExtension*Pointer***

It works in artrage now, fully supports pressure and tilt. The only perhaps unrelated bug is that there is some weird behaviour when "Precise tablet mode" is enabled from Edit/Preferences menu. That might be related only to artrage, however.
There is a reason why number of axis must be 5 or more. After check program determine behavior of each axis. If there is not enough axis suported by the device wine may fail to run (as there is no variable representing tilt).  

My case was even more bizarre. My stylus was represented as IsExtentionKeyboard. So in addition to editing line 623 I had to delete
```
if (device[loop].use == IsExtensionDevice)
```
in line 505 and respective brackets. But probably deleting line 505 was enough to make wintab find number of axis (but I'm to lazy to recompile wine to check if that is true).

---

### Post by oedipuss on 2008-04-21
Keyboard?? very weird indeed .. 

But concerning the axis check, as far as I can tell, it checks right after that for extra axes. In particular , when setting tilt it does a  :
 if (Val->num_axes >= 5)
so any device with less axes should set the first 3 and fail this check skipping setting tilt parameters where there's no tilt support. It even checks for x and y position axes separately, so it should be safe even for single axis devices, if there are any.

---

### Post by vries on 2008-04-21
yes, it should be like that but...
[http://bugs.winehq.org/show_bug.cgi?id=12005](http://bugs.winehq.org/show_bug.cgi?id=12005)

Anyway, I checked and deletion of line 623 alone  is good enough (if you have 5 or more axis, that is :P).

---

### Post by oedipuss on 2008-04-21
Yes that's where I saw to remove the extra val->num_axes check, look at the first patch there.

It's the change from XExtensionDevice to XExtensionPointer that matters in my case, though. I suppose in other systems XExtensionDevice must be valid, though. It might be a change in X, or something like that.

---

### Post by jklehm on 2008-04-21
This issue is tracked in wine bug 12005:
[http://bugs.winehq.org/show_bug.cgi?id=12005](http://bugs.winehq.org/show_bug.cgi?id=12005)

---

### Post by FrostBlue on 2008-04-27
Hi everyone,my first time here.
So, I had wine 0.9.60 working great with Gutsy.And then I upgraded to Hardy just yesterday.Now a lot of things in Hardy are amazing,but the upgrade has broken my wine.I cant get pressure sensitivity with photoshop.I tried the wintab.c changes mentioned here but nothing works.
Help please , am in dire need:confused:

---

### Post by oedipuss on 2008-04-29
Do you have pressure sensitivity in a native app , such as gimp ? If not, you may need to add some sections to your /etc/X11/xorg.conf file, related to wacom tablets. They used to be there in gutsy, but got removed in hardy, I think because it tries to autoconfigure the X server, or something like that.

You'll need to enable extended devices in gimp, as described [here]("https://help.ubuntu.com/community/Wacom"), section *Configuring the "Extended input devices"*

Here are the sections from my xorg.conf, adding them should work, assuming your tablet is a usb wacom : 

```

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "USB"           "on"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "pad"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "pad"
        Option          "ButtonsOnly"   "on"
        Option          "USB"           "on"
EndSection

```

and the following lines in bold, to the ServerLayout section (the non bold text should already be there): 

```

Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
[B]        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
	InputDevice     "stylus"        "SendCoreEvents"[/B]


EndSection

```

---

### Post by FrostBlue on 2008-05-01
I am getting pressure in Gimp and other Linux apps,but not in wine software.
I used to get it under gutsy...but not since Hardy upgrade.

---

### Post by kougaru on 2008-05-03
I'm also having trouble getting pressure to work in wine after my Hardy upgrade :\

So far I tried compiling 9.60 from source after making the changes that have been mentioned, but I still do not have working pressure sensitivity in wine. I have confirmed I have pressure in gimp.

I'm using a Graphire 4 tablet.

After running WINEDEBUG=wintab32 wine on OpenCanvas 1.1 I found that it is still reporting that my tablet has less then five axes and returning zero valid devices even though I made the changes in the source code.

```
warn:wintab32:X11DRV_LoadTabletInfo Did not find a valid stylus cursor with >= 5 axes, returning 0 valid devices.
```

Then it just goes on repeating this:

```
trace:wintab32:WTPacketsGet ((nil), 1, (nil))
```

I hope someone can help me get it working.

---

### Post by vries on 2008-05-05
1.Detecting tablets have changed in 0.9.61 try it (maybe compiled from source).
2.try applying patch for wine 0.9.61 I've created for arch pgbuild system. 
[http://azure.freehost.pl/patch.file](http://azure.freehost.pl/patch.file)
to apply it, enter directory where you unpack wine source, copy there patch file  and type 
patch -p0 -i patch.file 
(you may edit it by changing  &#8220;if (!axis_read_complete && Val->num_axes >= 5 && cursor->TYPE == CSR_TYPE_PEN&#8221; into   &#8220;if (!axis_read_complete && cursor->TYPE == CSR_TYPE_PEN)&#8221; first)
3.If that fails provide me with output of:
xidump -l
xsetpointer -l
and full output of WINEDEBUG=wintab32 wine xxx.exe (similar to that which was provided by oedipuss). Maybe I will be able to find a solution

PS. patch also enables drag&drop (one sided) form linux native applications to wine applications. But that is not working with newest foobar.

---

### Post by kougaru on 2008-05-05
Just as a precaution I backed up all my important files and did a clean install of Ubuntu.

0.9.61 seems to have fixed the problem. I now have pressure in wine, but I only have one oddity left. The Y axis seems to be inverted in OpenCanvas 1.1, but in ArtRage it works perfectly fine. Oh well, I've been using sketcher boards more anyway :P

---

### Post by oedipuss on 2008-05-06
Some similar weirdness happens with artrage too, when you select 'Precise tablet mode'. Perhaps there's an equivalent option in OpenCanvas.

---

### Post by the dsc on 2008-06-21
> **kougaru said:**
> Just as a precaution I backed up all my important files and did a clean install of Ubuntu.

0.9.61 seems to have fixed the problem. I now have pressure in wine, but I only have one oddity left. The Y axis seems to be inverted in OpenCanvas 1.1, but in ArtRage it works perfectly fine. Oh well, I've been using sketcher boards more anyway :P

The same with me.

Just one question, in which programs did you test pressure sensivity in wine?

With me, it works only in Art Rage (with "precise tablet" option disabled, so there no axis weirdness) and Open Canvas, but fails under Art Weaver and Deep Paint 2.


Would be so great to have the tablet fully working with these programs under wine! 



I'm using debian lenny, with wine 1.0. I've installed it from the source, and this version already have one of the changes mentioned earlier, by default. (That is, the line isn't "* if (!axis_read_complete && Val->num_axes >= 5 && cursor->TYPE == CSR_TYPE_PEN)*", but is already in the way it was suggested to be)





Another thing... my results for xidump -l and xsetpointer -l...

 xidump -l
Virtual core keyboard          keyboard
Virtual core pointer           disabled
Generic Keyboard               extension
Configured Mouse               extension
stylus                         extension
cursor                         extension
pad                            extension
eraser                         extension
Generic Keyboard               extension


 xsetpointer -l
0: "Virtual core keyboard"      [XKeyboard]
1: "Virtual core pointer"       [XPointer]
2: "Generic Keyboard"   [XExtensionKeyboard]
3: "Configured Mouse"   [XExtensionPointer]
4: "stylus"     [XExtensionKeyboard]
5: "cursor"     [XExtensionKeyboard]
6: "pad"        [XExtensionKeyboard]
7: "eraser"     [XExtensionKeyboard]
8: "Generic Keyboard"   [XExtensionKeyboard]


I think that the tablet things beint labeled or detected as keyboard things may not be a good thing... anyone knows what is wrong?

---


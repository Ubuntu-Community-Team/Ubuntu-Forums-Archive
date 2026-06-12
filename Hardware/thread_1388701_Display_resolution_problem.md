---
title: "Display resolution problem"
date: 2010-01-23
forum: Hardware
---

### Post by CinemaScope on 2010-01-23
I just installed 32-bit Ubuntu 9.10 on an old desktop machine (3.0 Ghz Pentium 4, dating from about 2006 -- previous Ubuntu 8.10 ran well on it with no problems). Installation went ok, but the desktop image was completely black. Thinking this might be the default image (unlikely, I know!), I tried changing the desktop, but non of my changes were applied. I created some desktop shortcut icons, but they did not show up -- so the desktop is not only black but not there! Checking the desktop contents in a window shows the shortcuts are there, just not displayed. I did a video test, and was able to see the desktop image briefly during the tests at different resolutions, except for the correct resolution in which the desktop image remained black. So I deliberately set the display to the wrong settings (using System/Preferences/Display) to 1152 x 864 (4:3), instead of the correct settings of 1280 x 1024 (5:4) and this allows me to see the desktop image and the shortcut icons. But of course, the image is not correct and now the monitor itself frequently issues resolution warning messages: "For best picture quality change resolution to 1280 x 1024". When I do that I see a black desktop again (top and bottom taskbars are visible, only desktop image itself and shortcuts remain blacked out). Ubuntu has correctly identified the screen resolution, so what's the problem? My graphics card is not an obscure type: it's an AGP ATI Radeon with 128 onboard RAM.

Co-coincidently, my laptop which also runs Ubuntu 8.10 has just had a display issue. The image seems slightly lower resolution than normal and definitely has a slight stretched appearance. Unfortunately I don't know what the original resolution is but it is showing as "laptop 15", 1024 x 768 (4:3)". I feel this may have happened after a routine update -- seem to be having two display issues at the same time! Can someone help me please? I am not a Linux expert by the way...

---

### Post by zwaardmeester on 2010-01-23
Hi there, try in a terminal:

```
sudo killall nautilus
sudo nautilus &
```

---

### Post by blackened on 2010-01-23
> **zwaardmeester said:**
> Hi there, try in a terminal:

```
sudo killall nautilus
sudo nautilus &
```

You don't need to restart nautilus with superuser privileges, just a regular restart will do:

```
sudo killall nautilus
nautilus &
```

If that works and nautilus doesn't throw a bunch of errors, then you can restart it without tying the process to a terminal window by again using killall nautilus, then alt+F2, nautilus, and press enter.

Some background on why this is happening: Nautilus is the system's filemanager and is also used to draw the desktop. I would say that it's the Gnome equivalent to Windows' explorer.exe, but I would probably be chastised for doing so. Oh wait, I did.

---

### Post by CinemaScope on 2010-01-23
Thanks for quick replies. I put the display resolution back to the correct figures which again gives the black desktop, and then brought up a terminal. Here's what comes up in the terminal after typing those commands:

(nautilus:1659): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:1659): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1659): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1659): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension

Then a graphical dialogue box is invoked ("root -- file browser") which shows a folder called "Desktop" with no items in it. What does all this mean? Thanks.

---

### Post by blackened on 2010-01-23
Which is why I said not to invoke sudo. Just type
```
nautilus &
```
and post the output errors. 

The empty desktop folder you saw belongs to the root user.

---

### Post by CinemaScope on 2010-01-24
"Which is why I said.." -- sorry, working at the limit of my understanding in this forum! I typed just "nautilus &" and got this in the terminal:


(nautilus:1712): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed


Invokes a window "John - file browser" which shows the folders making up my home directory and the desktop folder containing my test shortcuts. Strange why the wrong resolutions show the desktop image but not the correct one. Any ideas?

---

### Post by blackened on 2010-01-24
Ok, this may be bug related, and if so, there is a fix:

First open a terminal window and kill nautilus
```
killall nautilus
```
make a backup of the gvfs-metadata directory
```
cp -r ~/.local/share/gvfs-metadata ~/
```
then delete the original
```
rm -r ~/.local/share/gvfs-metadata
```
now restart nautilus
```
nautilus &
```

If all goes as planned and nautilus draws the desktop with icons and everything is normal, then you can close the terminal and start nautilus with alt+F2.

---

### Post by CinemaScope on 2010-01-25
Thanks blackened. Here's a paste from the terminal:


john@computer7:~$ killall nautilus
john@computer7:~$ cp -r ~/.local/share/gvfs-metadata ~/
john@computer7:~$ rm -r ~/.local/share/gvfs-metadata
john@computer7:~$ nautilus &
[1] 1758
john@computer7:~$ 
(nautilus:1758): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:1758): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1758): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1758): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.



Still no desktop image. Using Alt + F2 invokes a "Run Application" dialogue, typing "Nautilus" and clicking ""Run" invokes the main window of my system: "john - File Browser" but desktop remains black. Rebooted and tried Alt + F2 again but still the same: black desktop image. Interestingly, when the computer is powering down, the desktop image is briefly seen!

PS. Sorry about the those smiley faces, should of course be "8 ):" (without the space).

Thanks.

---

### Post by blackened on 2010-01-25
Well, I'm at a loss then. This is one of those grey area problems that could be caused by anything, and judging by the variety of bug reports that I've read, is hard to pin down to a singular source.

You should copy back the gvfs-metadata folder just to avoid any problems that missing it might cause, like the samba problem that cropped up.

```
cp -r ~/gvfs-metadata ~/.local/share/
rm -r ~/gvfs-metadata
```

> **CinemaScope said:**
> ...Sorry about the those smiley faces, should of course be "8 ):" (without the space).

Wrap terminal output with code tags (the # sign available in the advanced editor {"Go Advanced", below the post input box}) and that won't be an issue. Plus it makes it much easier to read.

---

### Post by neeraj2608 on 2010-01-25
> **CinemaScope said:**
> I just installed 32-bit Ubuntu 9.10 on an old desktop machine (3.0 Ghz Pentium 4, dating from about 2006 -- previous Ubuntu 8.10 ran well on it with no problems). Installation went ok, but the desktop image was completely black. Thinking this might be the default image (unlikely, I know!), I tried changing the desktop, but non of my changes were applied. I created some desktop shortcut icons, but they did not show up -- so the desktop is not only black but not there! Checking the desktop contents in a window shows the shortcuts are there, just not displayed. I did a video test, and was able to see the desktop image briefly during the tests at different resolutions, except for the correct resolution in which the desktop image remained black. So I deliberately set the display to the wrong settings (using System/Preferences/Display) to 1152 x 864 (4:3), instead of the correct settings of 1280 x 1024 (5:4) and this allows me to see the desktop image and the shortcut icons. But of course, the image is not correct and now the monitor itself frequently issues resolution warning messages: "For best picture quality change resolution to 1280 x 1024". When I do that I see a black desktop again (top and bottom taskbars are visible, only desktop image itself and shortcuts remain blacked out). Ubuntu has correctly identified the screen resolution, so what's the problem? My graphics card is not an obscure type: it's an AGP ATI Radeon with 128 onboard RAM.

Co-coincidently, my laptop which also runs Ubuntu 8.10 has just had a display issue. The image seems slightly lower resolution than normal and definitely has a slight stretched appearance. Unfortunately I don't know what the original resolution is but it is showing as "laptop 15", 1024 x 768 (4:3)". I feel this may have happened after a routine update -- seem to be having two display issues at the same time! Can someone help me please? I am not a Linux expert by the way...
Have you checked that the key [FONT="Courier New"]/apps/nautilus/preferences/show_desktop[/FONT] is enabled in [FONT="Courier New"]gconf-editor[/FONT]?

---

### Post by efflandt on 2010-01-25
From the dropdown list at bottom of login screen, can you log into FailsafeGNOME?  If that works, you might need some other video driver.

What shows for your video in **sudo lspci -v** ?

I had an older PC with ATI video that would not work properly in gnome (seemingly partially drawn with no background).  It worked in FailsafeGNOME, but what you can do from that is limited.  That one needed xorg-driver-fglrx package specifically for ATI, but if you have nVidia you may need something else.  All other computers I tried Ubuntu on with ATI or nVidia worked fine with default modules.

---

### Post by CinemaScope on 2010-01-25
neeraj2608: "Have you checked that the key /apps/nautilus/preferences/show_desktop is enabled in gconf-editor" -- how would I do that?

blackened: "You should copy back the gvfs-metadata folder just to avoid any problems" -- how do I do that? Thanks for all your help, blackened.

efflandt: "xorg-driver-fglrx package specifically for ATI" -- I am using an ATI graphics card. Can I download the driver you mentioned through the Synaptic repo as normal? I keyed your command in a terminal (sudo lspci -v) and got a long result, I just paste here the entry concerning the graphics card (I assume that's what I need to see?):

VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
	Subsystem: Connect Components Ltd Device 2801
	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 16
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at f9000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at f8000000 [disabled] [size=128K]
	Capabilities: [58] AGP version 3.0
	Capabilities: [50] Power Management version 2
	Kernel modules: radeon, radeonfb



What I find strange about this desktop problem is that the computer ran Ubuntu 8.10 with no problems, but making a clean install of 9.10 has thrown up this problem. What is different about 9.10?

---

### Post by blackened on 2010-01-26
> **CinemaScope said:**
> blackened: "You should copy back the gvfs-metadata folder just to avoid any problems" -- how do I do that? Thanks for all your help, blackened.

The terminal code in my last post will restore the gvfs-metadata folder to its rightful place.

> What I find strange about this desktop problem is that the computer ran Ubuntu 8.10 with no problems, but making a clean install of 9.10 has thrown up this problem. What is different about 9.10?

It's not really strange, while the OS looks the same on the surface it is constantly undergoing, sometimes drastic and occassionally dysfunctional, evolutionary changes. That's why there is a difference between the regular 6 month cycle and the sesquiannual LTS releases: the former being relatively unstable when compared to the most recent tried-and-true (in theory) LTS.

---

### Post by neeraj2608 on 2010-01-26
> **CinemaScope said:**
> neeraj2608: "Have you checked that the key /apps/nautilus/preferences/show_desktop is enabled in gconf-editor" -- how would I do that?


Press Alt + F2, type in 'gconf-editor' (without the quotes). Navigate to [FONT="Courier New"]/apps/nautilus/preferences[/FONT] in the left-side pane. The [FONT="Courier New"]show_desktop[/FONT] key will show up in the right-side pane. Make sure it's selected.

> 
What I find strange about this desktop problem is that the computer ran Ubuntu 8.10 with no problems, but making a clean install of 9.10 has thrown up this problem.

Hmmm, looking at this, I don't think the [FONT="Courier New"]show_desktop[/FONT] key is the problem. But it can't hurt to check.

---

### Post by CinemaScope on 2010-01-27
Thanks everyone for your help. In a few months I'll get Ubuntu 10.4 and see if that works ok. Cheers.

---


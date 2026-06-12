---
title: "System crashes"
date: 2008-07-13
forum: General Help
---

### Post by vlc on 2008-07-13
Hi *,

I am suffering from frequent system crashes, most likely related to active content in Firefox (like flash / VLC plugin). The system crashes completely, as

- I cannot terminate the X-server with Ctrl-Alt-Backspace
- the PC does not react on pings any more
- the screen is completely frozen
- the PC does not react on the OFF button any more

Only a power-on reset helps.

glxgears runs without problems (> 3 hours), memory check is also okay, the problem also does not depend on the release (same problem in 7.10 and 8.04).

I have the following graphics card in my PC:

```
$ lscpi | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 828456/GLI[Brookdale]/GE Chipset Integrated Graphics Device (rev 3)
```

I attach my Xorg.conf and Xorg.0.log to the post. In the Xorg.conf, I have already tried the following settings:

```
Section "Device"
        Identifier "Configured Video Device"
EndSection
```

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection
```

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "i810"
EndSection
```

```
Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "i810"
        Driver          "Intel"
EndSection 
```

In the Xorg.0.log, the only warnings I can find are:

```
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) intel(0): EXA greedy migration mode enabled.
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(WW) Configured Mouse: No Device specified, looking for one...
```

I do not know if this could be a problem (?).

It also cannot be an obvious hardware issue as Windows XP runs without problems on the same PC.

Furthermore, I tried Kubuntu, but the problem is much worse there. The PC crashes completely after a few operations (most likely related to opening and closing windows). The funny thing is that the PC crashes with Kubuntu installed on the hard drive after a few minutes, but works without problems using the live CD. Does anyone know the differences between the Live CD and the installation concerning window managers? I already found that the NVIDIA driver is not loaded on the live CD (file /etc/default/linux-restricted-modules), but in the installed OS. Correcting this does unfortunately not make a difference.

Does anyone have an idea what I could do to find a solution for this problem?

Thanks a lot in advance!

P.S.: I added the attachments as gzipped tar as extensions ".conf" and ".log" are not accepted ...

---

### Post by vlc on 2008-07-13
It also does not depend on the browser. I have the same problem with Epiphany when displaying flash.

---

### Post by dracayr on 2008-07-13
do you use compiz(desktop effects)? try disabling it.

also, do you use gnash or adobe flash? try the other one.

dracayr

---

### Post by vlc on 2008-07-13
Compiz has always been disabled (compiz and alltray don't like each other very much).

I already tried gnash instead of adobe flash but removed it after a few minutes as it could not play the flash animations on some of my favorite web sites.

I will try it again to make sure that it's a adobe flash problem.

Thanks!

---

### Post by dracayr on 2008-07-13
Just a little pointer: You probably won't need to shut down your computer by shutting off the power. just press this (the letters only ~1s apart):

Alt+SysRq+R+E+I+S+U+O

that should perform a safe shutdown. Replace the O with a B for a reboot.

dracayr

---

### Post by vlc on 2008-07-13
Now I removed adobe flash and installed gnash: same problem under Firefox.

Thanks for the hint with Alt+SysRq+R+E+I+S+U+O. Now I have to figure out what SysReq is on a spanish keyboard :confused:

But I am afraid that it won't work as Ctrl+Alt+Backspace doesn't work and the PC does not react any more on pings, therefore neither ssh nor telnet is possible. Looks to me like a complete system crash.

---

### Post by vlc on 2008-07-13
Next crash :mad: Alt+SysRq+R+E+I+S+U+O does not help. Complete system crash.

There is one suspicious thing: I run my PC now for several hours, but the temperature is only 22°C (?).

```
$ cat /proc/acpi/thermal_zone/THRM/temperature 
temperature:             22 C
```

Is this realistic?

---

### Post by vlc on 2008-07-14
I just tried browsing some Flash-intensive Websites with the Live-CD and had no problem at all - the installed image just survives a few seconds on these web sites.

What is the difference between the Live-CD and the installed Image?
Does anyone have an idea where to look why the Live CD works and the installed OS does not?

Thanks a lot in advance!

---

### Post by vlc on 2008-07-15
It does not seem to be restricted only to flash. I just had a crash on a web page without flash animations.

I also tried to disable all flash animations using Firefox NoScript, but unfortunately this also does not help.

---

### Post by vlc on 2008-07-16
There is a "workaround": I installed Firefox for Windows (and Adobe Flash plus VLC) under Wine and it works quite well. No crashes, just a bit slow. And it looks like sh**, the MS Windows theme between all the Gnome windows ...

Nevertheless if anyone has an idea how to solve the root problem, please do not hesitate to post.

Thanks!

---

### Post by vlc on 2008-08-04
Another workaround is to use Opera instead of Firefox. As Firefox and Epiphany are affected by the bug, I assume that the problem lies somewhere in the common code of both applications. If I remember right, Epiphany uses Mozilla's Gecko HTML rendering engine (which is also used by Firefox).

---


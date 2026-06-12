---
title: "Successful ATI driver install ???"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by doobydave on 2007-02-21
Ok, breathe, try to stay calm......:oops:

I appear to have installed the drivers correctly (using the various methods described at the end of the how-tos) yet the graphics are an utter joke. Much worse in fact than the open-source ones supplied.

My glxinfo show DRI:yes and fglrxinfo shows the fglrx module being used.

Currently using dapper after trying on edgy (same result) I have a ghost image of freshly installed dapper and edgy so i can start anew.

I've read about nforce2 issues but not sure if they are still applicable.
have also tried the k7 kernel optimisations yet same results (although better monitor detction).

Sorry to post on such a prolific topic, but my patience is dwindling. It may very well be time to send my ati card on a one way holiday!
I have an abit nf-7s rev2 board and a gigabyte ati 9600 Pro 256MB

Thanx in advance (he says presumptuously)

---

### Post by doobydave on 2007-02-21
Me again.

fgl_glxgears give ok (i think) score of >400 but
glxgears -printfps only scores 125

Any thoughts?

---

### Post by IcemanV9 on 2007-02-21
[[COLOR="Orange"]Howto[/COLOR]]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") wiki on ATI is very straightforward information. I got mine working from it.

Please tell me what's the output of two commands:

```
glxinfo |grep rendering
fglrxinfo
```

---

### Post by doobydave on 2007-02-21
dave@davesbuntu:~$ glxinfo |grep rendering
direct rendering: Yes

dave@davesbuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6286 (8.33.6)

cheers.

---

### Post by xbytes on 2007-02-21
well I tried the new ATI drivers posted today but couldn't get them to work, are these the ones you tried also?

-xbytes

---

### Post by doobydave on 2007-02-22
No, it was the previous release.

I also have downloaded the ones posted yesterday, and tried on edgy but to no avail.

When using the method i used before i get same results - good fgl_glxgears, bad glxgears and appalling 3d.

When using method posted above by IceMan (thankx btw, had not seen that) i get a dri missing error in fglrxinfo and lousy mesa.

bizarrely, last night, (on dapper)i just ran the driver with " sudo sh ati-intaller*.run" and did a direct install.
There was error about missing "atiogl_a_dri.so" but install finished.

Miraculously, 3d worked a treat, but glgears still v.low.

will carry on trying ....](*,)

---

### Post by xbytes on 2007-02-22
Yeah it is kind of annoying that it is so complex to setup a gfx card I had no problems with me previous Radeon 7500... but thats an old card, hard to find info for the x1300 install.

---

### Post by ctt1wbw on 2007-02-22
I am using a laptop with the 200m XPress card in it, and I noticed that when logged into a normal Gnome session, the glxgears frame rate was at around 700 fps, but when I logged into my XGL/Beryl session, it jumped up to about 2600 fps.  Go figure.

---

### Post by hippieh8er15 on 2007-02-22
> **IcemanV9 said:**
> [[COLOR="Orange"]Howto[/COLOR]]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") wiki on ATI is very straightforward information. I got mine working from it.

Please tell me what's the output of two commands:

```
glxinfo |grep rendering
fglrxinfo
```

Hey i am tryinig this and i get the message:

Media change: please insert the disc labled
'Ubuntu 6.10 _Edgy EFT_ - Release i386 (20061025.1)'
in the drive '/cdrom/' and press enter

I tried using my install disk and it gave me the same message how do i get this disk?

---

### Post by IcemanV9 on 2007-02-22
@doobydave - looks like you're all set with ATI driver based on the output you provided. However, please don't rely on the output of glxgears as THE benchmark. :) Better yet, try 3D games, such as Tuxracer or Frozen Bubble, to test 3D stuff.

@hippieh8er15 - comment out the CDRom line in your /etc/apt/sources.list

---

### Post by doobydave on 2007-02-22
Not quite.

The only time i have seen good 3d screensavers was on dapper when i did a direct install from the .run file. This was also after a broken install. Unfortunately, no 2d.

Using my edgy image (with the 2.6.10.17 kernel), i tried ENVY which was recommended to me. Nice program but gave me the same results as the first manual install. like initial post symptoms.

sigh...

might try dapper again but its getting a bit boring now. I might take pity on my neurons and go but nvidia.

---

### Post by doobydave on 2007-02-24
noticed some errors in xorg.0.log

dave@davesbuntu:~$ grep WW /var/log/Xorg.0.log
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used

Anybody ??

---

### Post by IcemanV9 on 2007-02-27
It's just a few warnings that you are missing some X11 fonts. Need to re-install X11 fonts (xfonts-base, xfonts-scalable, xfonts-100dpi, xfonts-75dpi).

I only have one missing fonts (which is not important) from X11 log.

```
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
```

---

### Post by doobydave on 2007-02-27
Its more the ones at the end which i thought could be important-

(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used

---

### Post by doobydave on 2007-02-27
If you are interested in helping hunt down the problem check my posts in this thread-
[http://ubuntuforums.org/showthread.php?t=255929&page=82](http://ubuntuforums.org/showthread.php?t=255929&page=82)

---


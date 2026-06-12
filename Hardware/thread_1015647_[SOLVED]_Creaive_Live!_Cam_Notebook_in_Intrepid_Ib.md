---
title: "[SOLVED] Creaive Live! Cam Notebook in Intrepid Ibex"
date: 2008-12-19
forum: Hardware
---

### Post by duffrecords on 2008-12-19
Has anyone managed to get the Creative Live! Cam Notebook working in Intrepid Ibex?  Mine used to work in Hardy Heron but after the upgrade, none of my applications will recognize it.  In fact, I can't even pipe the raw output from /dev/video0 into mplayer anymore:```
cat /dev/video0 | mplayer -
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Mobile Intel(R) Pentium(R) 4 - M CPU 1.80GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing -.
Reading from stdin...
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
Cannot seek backward in linear streams!
Seek failed
cat: /dev/video0: Bad address
Cannot seek backward in linear streams!
Seek failed


Exiting... (End of file)
```Rastageeks has a [new version]("http://www.rastageeks.org/ov51x-jpeg/index.php/Ov51xJpegHackedInstall") of ov51x-jpeg hacked with installation instructions for Intrepid Ibex, but they didn't work for me.

---

### Post by duffrecords on 2008-12-19
Sorry, I should have tried the trunk version before I posted.  There is a small change from version 1.5.9 in which line 8377 is changed from```
	ov->vdev->dev = dev->dev;
```to```
	ov->vdev->parent = &dev->dev;
```My webcam is working again.

---

### Post by Maratonda on 2008-12-25
Please can you provide details as to how to use the latest svn version?

EDIT: Sorry I mean, do you need to reload modules etc? Or just run "svn update" at the end of the procedure?

---

### Post by duffrecords on 2009-01-30
Yes, you'll need to reload the modules.  When you use the "svn update" command, all it does is download the latest source code.  You still need to compile the new version of the module and reload it.

---

### Post by alessandro57 on 2009-01-30
> **duffrecords said:**
> Yes, you'll need to reload the modules.  When you use the "svn update" command, all it does is download the latest source code.  You still need to compile the new version of the module and reload it.

Help me!!!

Pls, my QuickCam Express doesnt work (no dev/video0 recognized), do u think that ur solution could be good for me too? If u think so, pls, could u explain it in detail? I'm totally new to Lunux. I have Intrepid.

Thank u so much.

---

### Post by duffrecords on 2009-06-14
Sorry for the late response but... yes, try the latest code via subversion.  If you're new to Linux, you should read about how to [compile source code]("http://www.tuxfiles.org/linuxhelp/softinstall.html") and also how to [check out code using subversion]("http://subversion.tigris.org/faq.html#co-svn").

---


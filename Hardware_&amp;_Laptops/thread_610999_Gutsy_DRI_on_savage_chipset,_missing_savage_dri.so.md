---
title: "Gutsy: DRI on savage chipset, missing savage_dri.so?"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by Lastaii on 2007-11-12
Hi all, here's my problem, I'm using a old Toshiba portege 3440ct which had DRI running fine on Feisty. I've done a fresh install of Gutsy and can't for the life of me get DRI to work. A  quick peek in /var/log/Xorg.0.log points the finger:

([COLOR="Red"]EE) AIGLX error: dlopen of /usr/lib/dri/savage_dri.so failed (/usr/lib/dri/savage_dri.so: cannot open shared object file: No such file or directory)[/COLOR]

I've run a "find / -name savage_dri.so" and come up empty. Additionally I reinstalled xserver-xorg-video-savage with no joy. Am I doing something stunningly wrong, or is savage_dri.so really missing?

---

### Post by claytronic on 2007-12-18
It appears to be missing on my install of Gutsy as well.  This wasn't a problem before with Feisty.  Then it was just getting a working DRI driver.

```
LIBGL_DEBUG=verbose glxinfo
name of display: :0.0
libGL: XF86DRIGetClientDriverName: 2.1.2 savage (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/savage_dri.so
libGL error: dlopen /usr/lib/dri/savage_dri.so failed (/usr/lib/dri/savage_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: savage_dri.so
display: :0  screen: 0

```

--
Claytronic

---

### Post by claytronic on 2007-12-18
[Solved]

Just realized while I was staring at my previous post that I better check that I have the mesa-dri package loaded.  I didn't. 

```
root@foo:~# apt-get install libgl1-mesa-dri
```

Now my SuperSavage IX/C SDR has little extra 3d power. :lolflag:

---

### Post by Lastaii on 2008-01-01
Well spotted, that fixed it :)

---


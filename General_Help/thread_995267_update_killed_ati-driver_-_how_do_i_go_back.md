---
title: "update killed ati-driver - how do i go back?"
date: 2008-11-27
forum: General Help
---

### Post by Mzwo on 2008-11-27
hi,

i installed version 8-6 of fglrx - with the result that the screen goes white. the cube will still work but it's a little pointless since i can't see anything at all. how do i go back to a previous version? envyng doesn't give me much choice regarding driver version ...

thanks,

Mzwo

running 8.04

---

### Post by Mzwo on 2008-11-28
bump

---

### Post by zeigfried on 2008-11-28
Run _Synaptic Package Manager_:

Search for "fglrx":

Mark for complete removal:
```

fglrx-kernel-source
xorg-driver-fglrx

```

Run ```
gksudo gedit /etc/X11/xorg.conf
```

Under Section "Device"

change  Driver      "fglrx" to ```
 Driver      "ati"
```

If you want to reinstall fglrx use the official supported Ubuntu drivers (please don't use envyng).
You can find a how to install fglrx [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

Cheers,

---

### Post by immrlizard on 2008-11-28
I also am having some trouble with stability after today's patches that contained a new fgrlx driver and a new kernel.   

It has been freezing a bit since.   I am not sure which one did the damage and would love to know how to troubleshoot it.   I am on 8.04 with an ATI 850GT that has been flawless until the update.   

Any advice or help troubleshooting this is welcome.

---

### Post by Mzwo on 2008-11-29
> **zeigfried said:**
> Run _Synaptic Package Manager_:

Search for "fglrx":

Mark for complete removal:
```

fglrx-kernel-source
xorg-driver-fglrx

```

Run ```
gksudo gedit /etc/X11/xorg.conf
```

Under Section "Device"

change  Driver      "fglrx" to ```
 Driver      "ati"
```

If you want to reinstall fglrx use the official supported Ubuntu drivers (please don't use envyng).
You can find a how to install fglrx [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

Cheers,


hi, 
thanks for your help. one more question, though - the device section in xorg.conf reads as follows:
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

no "Driver". should i add it?


Cheers,
Mzwo

---

### Post by zeigfried on 2008-11-30
Mwzo.

I'm not sure if you need to add it, but it will not do any damage to you.

Cheers

---


---
title: "Questions! Ubuntu 64bit gutsy and MotoQ"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by leroy_30 on 2008-02-26
I just switched back from windows to Ubuntu Gutsy AMD64 about a week ago. I'm loving it so far (everything worked including the multimedia buttons on the front of my laptop) :)

Anyway, I've run into a little problem. I recently purchased a motoQ (Alltel) and am having trouble getting it to sync. I've followed numerous How To's about installing synce and multisync and none are getting me there.

One of the problems seems to be that on one of the posts it advises to add
```

deb http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main
deb-src http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main
```

and 

```
deb http://ppa.launchpad.net/synce/ubuntu gutsy main
deb-src http://ppa.launchpad.net/synce/ubuntu gutsy main
```

to the sources.list 

However, when I attempt to install it appears to be looking for AMD64 which dosen't seem to exist. I've tried installing synce via svn following their how to: to no effect.

I'm beginning to believe it's a AMD64 issue. Can anyone confirm this? If so It may just be better for me to re-install with Ubuntu 32bit.

dmesg shows

```
[ 1034.957575] usb 1-2: new full speed USB device using uhci_hcd and address 8
[ 1035.139551] usb 1-2: configuration #1 chosen from 1 choice
[ 1036.891176] rndis0: register 'rndis_host' at usb-0000:00:1d.0-2, RNDIS device, 80:30:00:00:a4:c5
[ 1049.135323] rndis0: no IPv6 routers present

```

```

sudo odccm -f

gives 

** (odccm:6913): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_30_00_00_a4_c5'
```

and stops

```
pls

** (process:6972): WARNING **: No devices connected to odccm
pls: Could not find configuration at path '(Default)'
```

If someone has any suggestions I would be glad to hear them.

---

### Post by leroy_30 on 2008-02-26
Just an FYI. I have been able to fix the OBEX browse device funtion (wasn't working either). I'm hoping someone may be able to tell me how to config multisync to sync. I would think if I can browse the device I should be able to sync the files. (I could be wrong though)

---

### Post by sammys on 2008-03-16
For those of you wanting OpenSync 0.22 packages for Ubuntu Gutsy amd64 architecture i've created them and put them into a repository. Add this as a third party repository in Software Sources:
```
deb http://synerger.com/opensync-amd64 gutsy main
```

Please note that i'm **not** providing support or warranty for these packages. They are simply a rebuild for amd64 using the source packages provided at [http://opensync.gforge.punktart.de/repo/opensync-0.21](http://opensync.gforge.punktart.de/repo/opensync-0.21)

**Use these packages at your own risk!** I've tested it using my N82 and the sync gives no errors.

Enjoy!

---


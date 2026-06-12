---
title: "USB Mouse Problem - USB HC takeover failed! ( and partial fix )"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by Slade Winstone on 2007-02-12
Hi, 

I have a Asus A8M laptop, running Edgy, 2.6.17-11-generic, and am having problems with a USB mouse working erratically.
Checking dmesg, I see the following problem:

"ohci_hcd 0000:00:0b.0: USB HC takeover failed! (BIOS/SMM bug)"

This is a bug reported in launchpad (bug #63651).

I have something to add that might help...

It sounds weird but I can actually  get my USB mouse to work 100% of the time, by wiggling/moving it at the right time during the boot process (it sounds weird, I know).

If, I start moving my Logitech USB mouse after the graphical boot progress bar is about 10% done, but before it is 50% done and keep moving it until the graphical logon screen appears, then the mouse works fine and is recognised (it also shows up correctly in dmesg).

Give it a try and see if you can get your mouse working.  If you start moving the mouse too soon, or leave it too late, it doesn't work.  Other wise, it works fine for me.

I would still appreciate it if there is a fix available of course :)

Let me know if there is something I can do to collect more information, to help fix this problem...

Regards,
Slade.

---

### Post by Slade Winstone on 2007-02-12
Googling, I've found that the following will re-activate the mouse after startup:

$ sudo rmmod ohci-hcd
$ sudo modprobe ohci-hcd no_handshake=1

This will re-activate the mouse.

I've tried adding the option line to /etc/modprobe.d/options:
options ohci-hcd no_handshake=1

But, this doesn't seem to work at boot.  

Anybody got any ideas?

Slade.

---

### Post by Slade Winstone on 2007-02-12
More googling and full fix:

Thanks to reech and especially [http://doc.ubuntu-fr.org/materiel/liste_portables/packard_bell/easynote_w51101](http://doc.ubuntu-fr.org/materiel/liste_portables/packard_bell/easynote_w51101)

To add the options ohci-hcd no_handshake=1 to bootup:

1) Create /etc/init.d/usbfix.sh
```
     #! /bin/sh
     sudo rmmod ohci_hcd 
     sudo modprobe ohci-hcd no_handshake=1 
```

2) $ sudo chmod 755 /etc/init.d/usbfix.sh

3) $ cd /etc/rc5.d

4) $ sudo ln -s /etc/init.d/usbfix.sh S99usbfix

Seems to fix the problem... :guitar: 

Slade.

---

### Post by martisek on 2007-02-17
That doesnt work for my ASUS A6M.

---

### Post by marshcast on 2007-04-17
if it's just a matter of getting up and running, I've found feisty to work.

you may have to put lilo instead of grub (for the time being, anyways), but there's a good walkthrough for it here:

[http://ubuntuforums.org/showthread.php?t=409345](http://ubuntuforums.org/showthread.php?t=409345)

I just got runnning (optiplex-320 intel Dual), can't say much about how well it working, but that's fr another thread - or maybe not (could be perfect!)


good luck ;)

---


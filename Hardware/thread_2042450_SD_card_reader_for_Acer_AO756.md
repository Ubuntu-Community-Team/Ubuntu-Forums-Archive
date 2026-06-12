---
title: "SD card reader for Acer AO756"
date: 2012-08-14
forum: Hardware
---

### Post by saou on 2012-08-14
I'm running xubuntu 12.04 on my Acer 756 netbook; everything works except for the sdcard:  It does not show up under lspci  (I tried to boot with or without the sdcard inserted).  It does work in window 7. After some digging I found this thread

[http://ubuntuforums.org/showthread.php?t=1506925&page=2](http://ubuntuforums.org/showthread.php?t=1506925&page=2)

(note that this thread is for the atom netbook whereas the 756 is bascially sandy bridge, which is why I start a new thread).  I tried the various suggestions in that thread but none works.   The suggestions in post #70 there does help a bit:  

(1) edit /etc/default/grub with

GRUB_CMDLINE_LINUX_DEFAULT="pciehp.pciehp_force=1 pciehp.pciehp_poll=1 elevator=noop quiet splash"

(2) add to /etc/moduels

pciehp
And if you reboot the machine WITH THE SDCARD then it works!  And lspci gives

04:00:1  SD Host controller: Broadcom Corporation Nextreme BCM57765 Memory Card Reader (Rev 10)

Unfortunately, if you umount the card and reinsert it the card is not longer recognized.

This is driving me crazy...  any help and suggestion is most appreciative!

---

### Post by bee4oo on 2012-08-15
I'm having the same problem. After inserting a card all I see is this message repeating in the kernel log

```

mmc0: Timeout waiting for hardware interrupt.
```

A strange workaround I've found is to reload the tg3 network driver while the card is inserted, perhaps the two devices share some parts in the broadcom chip and need special care?

```

rmmod tg3; modprobe tg3
```

---

### Post by saou on 2012-08-15
I just discovered something interesting:  If I boot the xubuntu 12.04 live CD *without* an sdcard plugged in,  the sdcard reader works fine -- I can hotplug/unplug sdcards at will and the card reader works.  But 

* you need to install the Broadcomm restricted drivers

* it takes 3-4 seconds for the sdcard to be recognized, whereas usb thumb drivers work right away

* I've booted this several times to be sure, and the system crahsed once when I plug/unplug 3-4 times in a roll (and since I'm running this off live CD I don't know how to make a log)

* when I revert back to normal boot from hdd then the sdcard reader fails again...

This is so weird...  Suggestions and comments are most welcome!

---

### Post by saou on 2012-08-15
> **bee4oo said:**
> A strange workaround I've found is to reload the tg3 network driver while the card is inserted, perhaps the two devices share some parts in the broadcom chip and need special care?

```

rmmod tg3; modprobe tg3
```

 Thanks for the update.  I tried this on my 756 and I got this error message:  > sudo rmmod t3g; sudo modprobe t3g > ERROR: Module t3g does not exist in /proc/modules > FATAL: Module t3g not found  The weird thing is that when I type   "more /etc/modules"  I got  > tg3 152032 0 - Live 0x(log string of zeros)  Puzzles...

---

### Post by bee4oo on 2012-08-17
> **saou said:**
> sudo rmmod t3g; sudo modprobe t3g > ERROR: Module t3g does not exist in /proc/modules > FATAL: Module t3g not found 

The module's name is tg3, not t3g. Or does it fail even with tg3?

---

### Post by bee4oo on 2012-08-19
Perhaps this patch will fix the problem?

[http://patchwork.ozlabs.org/patch/174095/](http://patchwork.ozlabs.org/patch/174095/)

---

### Post by vigi84 on 2012-08-20
I have just ordered an Acer like this.
I hope I won't have such troubles, though I am planning to stick with Ubuntu 10.10.

---

### Post by saou on 2012-08-21
> **bee4oo said:**
> Perhaps this patch will fix the problem?

[http://patchwork.ozlabs.org/patch/174095/](http://patchwork.ozlabs.org/patch/174095/)

Interesting!  Questions:

(1) This patch seems (?) to address the issue of reactivating the card reader after the user ejects a sdcard.  But what about recognizing the sdcard after a freshboot (without the card already plugged in)?

(2) How do we apply/test this patch?

Thanks!
p.s.  Thanks for noting the typo in post #4; I'm travelling now; I will test that again as soon as I get home...

---

### Post by sunlee1988 on 2013-02-09
> **saou said:**
> Interesting!  Questions:

(1) This patch seems (?) to address the issue of reactivating the card reader after the user ejects a sdcard.  But what about recognizing the sdcard after a freshboot (without the card already plugged in)?

(2) How do we apply/test this patch?

Thanks!
p.s.  Thanks for noting the typo in post #4; I'm travelling now; I will test that again as soon as I get home...

Has anyone tried installing the patch? I'm not sure where to place it before running it.

---

### Post by mtambo on 2013-03-08
hi everybody,
i'm having the same problem with my memory card reader. i don't know if i'm wrong but 
dmesg in /var/log tells me:
tg3.c:v3.121
seems to be the version number.

broadcom offers a driver download at [https://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php](https://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php)
unzipping the linux driver says the version is v3.124c

so probably installing this could help?
am i right if i follow the steps in the README.TXT with the non-rpm installation?

regards
mtambo

---

### Post by mulluysavage on 2013-05-24
> **mtambo said:**
> hi everybody,
i'm having the same problem with my memory card reader. i don't know if i'm wrong but 
dmesg in /var/log tells me:
tg3.c:v3.121
seems to be the version number.

broadcom offers a driver download at [https://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php](https://www.broadcom.com/support/ethernet_nic/netxtreme_desktop.php)
unzipping the linux driver says the version is v3.124c

so probably installing this could help?
am i right if i follow the steps in the README.TXT with the non-rpm installation?

regards
mtambo

Tried installing the driver as to the linux instructions in the readme.txt, got nothin but errors.

---


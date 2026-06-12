---
title: "Chain loading grub2"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by silmarilwest on 2009-10-31
In the past I've used Vista's boot manager to boot Ubuntu 9.04 and earlier.  The basic steps I used are outlined in the first section of [this article]("http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx").
With 9.10 however I have hit a snag.  The bootsector file I grabbed with dd if=/dev/sda5 (yes that's the partition I told grub to install to) is all zeroes, and obviously does not successfully boot.  I know that there are two major changes with 9.10 (ext4 and grub2) so I'm trying to figure out where the problem lies.

---

### Post by Sensiva on 2009-10-31
I don't know that much about Vista boot loader, may be this info would help you

to chainload grub2 from legacy grub I used this line 
```
kernel /boot/grub/core.img
```Maybe it would help you in figuring out how to chainload grub2 from Vista boot loader

---

### Post by grandtoubab on 2009-10-31
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by silmarilwest on 2009-10-31
Thanks for the suggestions.  I tried using the core.img file but no luck, just got some garbage character feedback after attempting to boot from it.
Would it be possible to install grub legacy from the live cd onto /dev/sda5?  Basically my idea is to chain load grub legacy from the vista boot loader and chain load grub 2 from that.
I tried "sudo grub-install /dev/sda5" but got an error back (obviously I'm not exactly an expert).

---

### Post by Sensiva on 2009-11-01
> **silmarilwest said:**
> Basically my idea is to chain load grub legacy from the vista boot loader and chain load grub 2 from that.


Then install grub4dos , its alot easer :D
- Download it from here [http://ubuntuforums.org/newreply.php?do=newreply&p=8210516](http://ubuntuforums.org/newreply.php?do=newreply&p=8210516) 
- Extract "gldr" and the example menu.lst from the zip file into ur vista partition. in Boot.ini add  c:\gldr = "Grub" (I don't know about Vista)

Edit the example menu.lst whatever you like , reboot, select Grub from Vista bootloader menu, now you have a legacy grub ready to go.

---

### Post by coffeecat on 2009-11-01
> **silmarilwest said:**
> Thanks for the suggestions.  I tried using the core.img file but no luck, just got some garbage character feedback after attempting to boot from it.

I've only just come across this "kernel /boot/grub/core.img" trick and I can confirm it works. However, you need a root line in your **Legacy Grub** menu.lst. So, say your Karmic/grub2 root partition is sda5, you need this stanza in your grub1 menu.lst:

```
title Whatever you want
root (hd0,4)
kernel /boot/grub/core.img
```

---

### Post by silmarilwest on 2009-11-01
Thanks again for the great suggestions.  It only took a little modification to point my vista bcd entry at grub4dos (grldr.mbr).
However I don't think the grub4dos syntax is exactly the same as the grub I am used to.
My entry:
> title Load Ubuntu 9.10
root (hd0,4)
kernel /boot/grub/core.img
It shows up in the grub4dos menu but is not selectable.  Any suggestions on how to modify the entry so it works in my grub4dos menu.lst?

---

### Post by silmarilwest on 2009-11-02
> **silmarilwest said:**
> It shows up in the grub4dos menu but is not selectable.  Any suggestions on how to modify the entry so it works in my grub4dos menu.lst?

Scratch that, I'm just retarded (I spelled kernel kernal).  Working beautifully now with the correct spelling, thanks very much to everyone for the very helpful replies.

---

### Post by Bjalf on 2009-11-02
> **silmarilwest said:**
> In the past I've used Vista's boot manager to boot Ubuntu 9.04 and earlier.  The basic steps I used are outlined in the first section of [this article]("http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx").
With 9.10 however I have hit a snag.  The bootsector file I grabbed with dd if=/dev/sda5 (yes that's the partition I told grub to install to) is all zeroes, and obviously does not successfully boot.  I know that there are two major changes with 9.10 (ext4 and grub2) so I'm trying to figure out where the problem lies.

I installed grub 2 to /dev/sda6, grabbed the bootsector with dd, and it is **not** filled with zeroes. Everything works just as it did with 8.04. I use XP's boot manager. I compared the old and new bootsectors (legacy grub and grub 2), and the differences were like expected.

Perhaps just a reinstall of grub 2?

---

### Post by silmarilwest on 2009-11-02
Odd, I installed grub2 about 5 times so I don't think that would be a fix for me.  Regardless, grub4dos works great so I have no reason to use dd anymore at the moment.  Out of curiosity what was the exact syntax you used?[FONT=Verdana][/FONT]
For me it was: "dd if=/dev/sda5 of=/tmp/linux.bin bs=512 count=1"
Or perhaps it's a bug specific to my hardware.

---

### Post by Bjalf on 2009-11-02
> **silmarilwest said:**
> Out of curiosity what was the exact syntax you used?
For me it was: "dd if=/dev/sda5 of=/tmp/linux.bin bs=512 count=1"

I never remember, so I always google it. :oops:

But a good guess would be: "[FONT=Verdana]sudo dd if=/dev/sda6 of=grub.bin bs=512 count=1[/FONT]" Then I copied [FONT=Verdana]grub.bin[/FONT] to the windows partition, rebooted into XP, checked boot.ini, and the contents of [FONT=Verdana]grub.bin[/FONT] just to make sure that it looked like a boot sector.

---

### Post by silmarilwest on 2009-11-02
Not sure why my dd grab was different, but I guess it doesn't matter.  Marked as solved.  Thanks again everyone.

---


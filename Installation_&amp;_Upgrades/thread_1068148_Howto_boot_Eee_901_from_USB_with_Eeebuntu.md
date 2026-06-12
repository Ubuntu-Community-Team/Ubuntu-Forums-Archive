---
title: "Howto boot Eee 901 from USB with Eeebuntu?"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by Halsnalle on 2009-02-12
This is probably a stupid question, but...:

I've successfully installed the Eeebuntu ISO onto a USB drive via the Create bootable USB drive thing in Ubuntu 8.10, intending to install Eeebuntu on my Asus Eee 901. But what do I do then? How do I get my Eee to start from the USB stick?

---

### Post by snowpine on 2009-02-13
Insert the USB stick, turn the eee on, and press Esc. You should see a list of devices to boot from.

If pressing esc does nothing, you probably have "boot booster" enabled. Turn on the eee, press F2 to enter the bios, go to Boot, and turn off the boot booster. Then, you should be able to reboot and press Esc to boot from the USB stick.

ps If you have any trouble with the USB Creator (I've found it to be a little buggy) a good alternative is Unetbootin.

---

### Post by Halsnalle on 2009-02-22
> **snowpine said:**
> Insert the USB stick, turn the eee on, and press Esc. You should see a list of devices to boot from.

If pressing esc does nothing, you probably have "boot booster" enabled. Turn on the eee, press F2 to enter the bios, go to Boot, and turn off the boot booster. Then, you should be able to reboot and press Esc to boot from the USB stick.

ps If you have any trouble with the USB Creator (I've found it to be a little buggy) a good alternative is Unetbootin.

Thanks! That took me closer, but not all the way:

After having turned off boot booster, I still have not had any success with the Eeebuntu USB stick i created with USB Creator, so I tried Uneetbootin. Install seems to have gone well, but my Eee simply refuses to boot from my USB stick. Is there some easy way to tell whether the problem is the USB stick rather than the software? Maybe I should just try with another USB stick...

---

### Post by kyphi on 2009-02-22
Perhaps this will help:  [http://ubuntuforums.org/showthread.php?p=6771503#post6771503](http://ubuntuforums.org/showthread.php?p=6771503#post6771503)

---

### Post by Halsnalle on 2009-02-26
After having tried with a different USB stick, I actually get the Eee to load UNetbootin's boot menu. But after that, it simply says:

> Loading /ubnkern.
Invalid or corrupt kernel image.
boot:

Any ideas what might be wrong here?

---

### Post by Halsnalle on 2009-02-26
Okay, I reformatted the USB from FAT16 to FAT32 and then downloaded a different Eeebuntu ISO (NBR). Now it boots.

---

### Post by kyphi on 2009-02-26
As the error message says:
"Loading /ubnkern. Invalid or corrupt kernel image."

Whenever you download a program always do the md5sum check to ensure that there have been no errors:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Lost In Linux on 2009-03-03
Thanks for the post.  Solved my problem and now I am up & running Eeebuntu 2.0 Base in my 901.

:D

---


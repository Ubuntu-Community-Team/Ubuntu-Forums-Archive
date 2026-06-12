---
title: "Not Detecting Hard Drive on Install"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by MPD51 on 2009-05-28
Hey everyone,

I posted a problem on the "Absolutely Beginner" board pertaining to this, but now that it's been isolated, I feel it would be best to start from here (although I contemplated whether this belongs here or in the Hardware board).

I am trying to install Ubuntu 9.04 on my desktop (Hard drive: Hitachi 7K1000.B - 1TB).

I believe it's a driver issue, here is a photograph of what happens when I reach step 4 of the graphical install (Desktop CD):

[IMG]http://i559.photobucket.com/albums/ss32/ronnyvince/IMG_0155.jpg[/IMG]

As you can see, the table is pure blank.

Furthermore, when I just load Ubuntu from the CD and open up the partition editor, there are no drives detected.

Has anyone encountered this/know how I may proceed?

Thanks in advance.

---

### Post by Mike'sHardLinux on 2009-05-28
Have you already gone into the CMOS Setup screen and verified that your computer recognizes the drive?

---

### Post by MPD51 on 2009-05-28
Yep, the drive should be fine.

I've been running Windows Vista on it (and tried 7, as well).

I also tried formatting as ext3, but still nothing. =/

---

### Post by Mike'sHardLinux on 2009-05-28
What is your motherboard manufacturer and model #?

Oh, also, do you have any other drives on that system, and can Ubuntu see them?

---

### Post by MPD51 on 2009-05-28
It's an XFX Geforce Motherboard Socket AM2+ (model:  **MIA78S8209).**

And no, it's just the one drive.

---

### Post by Mike'sHardLinux on 2009-05-28
I google around and found this in a Newegg review of that motherboard:

*Cons: Pain in the rear to get Ubuntu 8.04 to recognize the SATA drive. After hours of googling and failed attempts I found that you should add ""pci=nomsi"" to your kernel boot options to get linux to recognize the SATA drives. Worked like a charm!*

I know that's a different version of Ubuntu, but couldn't hurt to try.

---

### Post by MPD51 on 2009-05-28
Sweet, thanks a lot.

I'll give that a shot (as well as Google how to do that).

I'll let you know.

Thanks again!

---

### Post by Mike'sHardLinux on 2009-05-28
I found this:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Hope it works for ya!

---

### Post by MPD51 on 2009-05-28
Man, you are intense!

That did the trick. It's installing as we speak.

Thanks so much for your help! Microsoft Technet, be damned.

---

### Post by Mike'sHardLinux on 2009-05-28
Fantastic! 

I assume you will need to add that option in grub so it will always boot with that option.

---

### Post by MPD51 on 2009-05-28
Actually, no.
It's booting up just fine without any further alterations.

---


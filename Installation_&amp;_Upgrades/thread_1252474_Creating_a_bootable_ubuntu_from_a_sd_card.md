---
title: "Creating a bootable ubuntu from a sd card"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by kgonepostl on 2009-08-28
This is what I've done
I used a sd card adapter it pops up in the gui as it should "sd card". Now from what I understand you can't use the usb startup disk creator because sd cards act differently than flash drives

From what I understand you have to use the install feature.
I created a 350 meg swap partition and the main is a ext3 filestructure that it's installed on.

Once installed using the installer I noticed it was placed on sdc1 so that's where I pointed my boot loader.

I clicked "make as bootable"

Why isn't this working? I get the error about can't find the kernal. And says something along the lines of softreset failed on hd0 and says that it can't find /boot/blahblahblah
I checked in the grub bootloader and vista is set as hd0 but why does that matter since I'm hitting f12 and completely bypassing that and going straight to my sd card to boot?

It installs just fine. I can't figure out what I'm doing wrong. Do I have to set grub to my main mbr? Why can't I just do what I'm doing and point the mbr to sdc1 which is where ubuntu is installed on my sd card?  I just don't get it. What am I doing wrong?

---

### Post by kgonepostl on 2009-08-28
Kgonepostl again with a followup

If you know how to get a sd card hooked into a usb adapter running as ubuntu with write privalages, let me know how. It's so easy to do with a flash drive but I can't figure out how to do it with a sd card.

Just to let you know. I don't own any flash drives so that's out of the question. I gotta get this sd card goin!

---

### Post by stlsaint on 2009-08-28
whats the size of the card?

---

### Post by kgonepostl on 2009-08-28
I have one microsd card that's 8 gigs and another that's 2 gigs.

---

### Post by darthnerd on 2009-08-29
Have you read [this ]("http://ubuntuforums.org/showthread.php?t=1229299&highlight=grub+problem+94%25")yet?? 8-)

---


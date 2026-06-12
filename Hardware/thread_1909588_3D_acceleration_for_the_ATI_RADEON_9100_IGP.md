---
title: "3D acceleration for the ATI RADEON 9100 IGP"
date: 2012-01-15
forum: Hardware
---

### Post by eckeroo on 2012-01-15
When will the open source drivers allow 3D acceleration for the ATI RADEON 9100 IGP?

Here it says '3d support using open source is close!':

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)

But how soon is now?

Grrrrr...:-x

---

### Post by Mark Phelps on 2012-01-16
Probably NOT going to happen.  

Notice the entries that say that they "hope" the drivers will work in 5.04!  Most of these entries are YEARS old.

And, the ones that say the binary driver is required are useless now because support for THAT driver ended with Ubuntu 8.10.

---

### Post by eckeroo on 2012-01-19
Ha HA!

The open source radeon drivers work fine. The problem appears to be with the KMS.

Follow the instructions [here]("https://wiki.ubuntu.com/X/KernelModeSetting") (under sub heading 'KMS with a Radeon card') and amend the grub file so that radeon.modeset=0

After a restart, my fps on glxgears jumped from 60 to 1306 fps!!

This is on a NEC Versa E6000 with ATI Radeon 9100 IGP graphics card.

:biggrin:

---

### Post by MoreOrLess on 2012-01-19
> **eckeroo said:**
> After a restart, my fps on glxgears jumped from 60 to 1306 fps!!

You disabled vsync (where 60Hz means 60fps), so the numbers returned by glxgears (which isn't a benchmark) are misleading. Turning off KMS usually does make 3D faster on old radeons (and helps with some bugs), but you lose kms' features (dri2, vsync, etc.). It's a trade-off, but your excitement over the massive fps gain is unfounded.

---

### Post by eckeroo on 2012-01-19
> your excitement over the massive fps gain is unfounded.

Yeah-but 60 fps is pants and the 3d acceleration wasn't working so that opengl applications such as GLBlur on screensaver ran very sluggishly.

With the KMS off, the GLBlur now runs smoothly. I got the KMS tip from this thread at the Arch [forums]("https://bbs.archlinux.org/viewtopic.php?id=86898").

---

### Post by eckeroo on 2012-01-20
Just to clarify, 3D Acceleration was not working with KMS enabled for this card using the open source Radeon drivers. Ideally you would want KMS on; but for this card having KMS enabled meant no 3D acceleration.

*actually, one 3D opengl application did run, assault cube, but not as smooth as when KMS was switched off. Other opengl applications just failed or were very sluggish - you could not get opengl with wine games. With KMS switched off you do get more crashes, but all you've got to do then is ctrl+alt+F2, enter username & password, ps -e, and kill the crashed application, then ctrl+alt+F7 and start your app again.

---

### Post by coreychbt8295 on 2012-01-20
I have an Ati graphics card also and have had many issues with it, most of which are unresolved.  Running less programs seems to help it.

---


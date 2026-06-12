---
title: "Can't run Ubuntu from a CD on Dell 9150"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by w i l l on 2008-12-15
I'm trying to boot Ubuntu from a CD (not install on Windows).

I've burnt the contents if the ISO file (not the actual ISO file to the CD which should be correct) and I can see the Ubuntu icon by the CD drive when the CD is in the drive (as I should do).

When I put the CD in the drive and switch on the PC Ubuntu doesn't boot from the CD - the PC just starts as Windows. 

I thought I might have to change the boot sequence by pressing f2 on start up. What order should it read?

1. Onboard or USB CD-ROM Drive
2. Onboard or USB Floppy Drive (not present)
3. Onboard SATA Hard Drive (not present)
4. Onboard IDE Hard Drive (not present)
5. Intel Array
6. USB Device

Does anyone have any other advice? Any help appreciated.

Thanks.

---

### Post by snowpine on 2008-12-15
You should burn the ISO as a disk image (most burning software has this option), not the contents of the ISO file. I think that is the problem. :)

---

### Post by taurus on 2008-12-15
You're supposed to burn the ISO image to a CD instead of unpacking it first and then burning the content of it.

[https://help.ubuntu.com/community/BurningIsoHowto?highlight](https://help.ubuntu.com/community/BurningIsoHowto?highlight)

---

### Post by w i l l on 2008-12-15
I got the CD to work in the end - Ubunto loads up with the orange looking timer but then I just get weird display problems - all I can see is a series of 80's looking green lines running vertically along the screen. Any ideas on how to solve this problem?

Thanks.

---

### Post by taurus on 2008-12-15
What's the spec of your machine?

---

### Post by w i l l on 2008-12-15
Something like 2.33 GHz Dual Core with 3.0 Gig of Ram.

---

### Post by taurus on 2008-12-15
Another option is to use the alternate CD to install Ubuntu on your Dell.  It's a text based installer but should be real easy to follow (and fast too).

---

### Post by w i l l on 2008-12-15
Ok i'll try that. Now after trying to install Ubuntu i've noticed a few odd things in Windows - the icons on the desktop are all spaced too far apart and 'locked' to that spacing, the icons for the windows/toolbars look different and text is different, plus in Outlook I can't seem to attach files any more.

---

### Post by w i l l on 2008-12-15
> **taurus said:**
> Another option is to use the alternate CD to install Ubuntu on your Dell.  It's a text based installer but should be real easy to follow (and fast too).

So with this method do I have to install Ubuntu on my PC? Can I not just boot from the CD without installing? I couldn't see the option for this.

---

### Post by taurus on 2008-12-15
You cannot try Ubuntu from the CD with the alternate CD.  It only lets you install it.  If you just want to check it first before installing it, then you have to use the LiveCD (desktop CD).

---

### Post by w i l l on 2008-12-15
This is obviously the reason for the graphics problem.

[http://ubuntuforums.org/showthread.php?t=189752]("http://ubuntuforums.org/showthread.php?t=189752")

Is there a fix out there yet?

---


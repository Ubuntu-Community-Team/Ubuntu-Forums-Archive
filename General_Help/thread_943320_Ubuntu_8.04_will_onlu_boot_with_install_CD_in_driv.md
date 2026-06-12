---
title: "Ubuntu 8.04 will onlu boot with install CD in drive"
date: 2008-10-10
forum: General Help
---

### Post by supadid on 2008-10-10
Hello,

I recently installed Ubuntu but I have noticed that it will only boot when the ubuntu CD-ROM is in the drive. If I try to boot without, then the computer will go to a black screen after the Ubuntu progress load bar has finished and stay there.

I am using the Ubuntu 8.04 alternative install iso, which i burnt to a DVD, not the LIVE iso.

:confused: Very bizarre, any help would be appreciated! :)

---

### Post by suhaib1thariq on 2008-10-10
i think you need to burn iso into live cd.....and then try to install

---

### Post by geirha on 2008-10-10
When you get to the "black screen", are you able to get to a console by hitting Ctrl+Alt+F1?

---

### Post by happyhamster on 2008-10-10
Try checking System --> Administration --> Software Sources --> Third Party Software, to see if the cd-option is ticked. If so, unselect that option.

Good luck.

---

### Post by supadid on 2008-10-10
> **geirha said:**
> When you get to the "black screen", are you able to get to a console by hitting Ctrl+Alt+F1?

No, I do not get a console :(

---

### Post by supadid on 2008-10-10
> **happyhamster said:**
> Try checking System --> Administration --> Software Sources --> Third Party Software, to see if the cd-option is ticked. If so, unselect that option.

Good luck.

This was already unchecked :(

---

### Post by thegner on 2008-10-10
> **supadid said:**
> No, I do not get a console :(
Can you try booting into the recovery console? When it says "Loading GRUB boot menu..." press escape, and choose the option that says (recovery console) to see if you get a command prompt in single user mode. From there you can at least sift through some logs and get an idea of what the problem is.

It sounds like it could be a video driver problem, although you should still be able to get the ctrl-alt-f1 console with that, but I've seen stranger things.

Once in recovery mode, try editing the /etc/X11/xorg.conf file and change the video driver to "vesa". It's the "Driver" line under the "Device" section.

HTH,

Travis

---

### Post by thegner on 2008-10-10
> **thegner said:**
> Can you try booting into the recovery console? When it says "Loading GRUB boot menu..." press escape, and choose the option that says (recovery console) to see if you get a command prompt in single user mode. From there you can at least sift through some logs and get an idea of what the problem is.

It sounds like it could be a video driver problem, although you should still be able to get the ctrl-alt-f1 console with that, but I've seen stranger things.

Once in recovery mode, try editing the /etc/X11/xorg.conf file and change the video driver to "vesa". It's the "Driver" line under the "Device" section.

HTH,

Travis
I guess this may not make sense if you can boot with the CD in the drive... That is pretty strange, especially considering it's an alternate CD...

---

### Post by thegner on 2008-10-10
> **thegner said:**
> I guess this may not make sense if you can boot with the CD in the drive... That is pretty strange, especially considering it's an alternate CD...
Try booting with the power and data cables disconnected from the CD completely...

---

### Post by happyhamster on 2008-10-10
> **supadid said:**
> Hello,

I recently installed Ubuntu but I have noticed that it will only boot when the ubuntu CD-ROM is in the drive. If I try to boot without, then the computer will go to a black screen after the Ubuntu progress load bar has finished and stay there.
Do you get the same result if *any* cd is in the drive (i.e. some data cd/dvd or such)?

---


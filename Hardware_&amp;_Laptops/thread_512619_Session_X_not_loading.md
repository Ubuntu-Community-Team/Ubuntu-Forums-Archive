---
title: "Session X not loading"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by brad1150 on 2007-07-29
I moved my hard drive with Feisty Fawn to my better pc. When I tried starting Ubuntu with my secondary 80gb NTFS drive plugged in it would only load the first bar and then froze. When I removed the drive it booted Ubuntu very slowly and said the session X or whatever was not configured properly and then put me back to a black screen with the terminal. I moved from a 1ghz P3 768mb ram, 64mb Nvidia GFX card to a 2.40ghz P3, 1gb ram, and a 256 Ati Radeon 9800XT. I am running from the Live CD right now and I would liek to not have to reinstall Ubuntu as I already have everything I want installed and its too much to replace.


EDIT: Sorry, title may be misleading. Its the X Server thats screwing up. It says it has no screens.

---

### Post by brad1150 on 2007-07-29
*Bump* Now that its edited and mroe understandable of my problem. I would really liek to get thsi working without having to reinstall Ubuntu.

I found [this]("http://http://ubuntuforums.org/showthread.php?t=285637") thread and it says to use ```
sudo aptitude reinstall linux-restricted-modules-2.6.17-10-generic
``` to fix it. This was on an Edgy post, is it the same for Feisty?

---

### Post by ronny_d on 2007-07-30
> **brad1150 said:**
> I moved my hard drive with Feisty Fawn to my better pc. When I tried starting Ubuntu with my secondary 80gb NTFS drive plugged in it would only load the first bar and then froze. When I removed the drive it booted Ubuntu very slowly and said the session X or whatever was not configured properly and then put me back to a black screen with the terminal. I moved from a 1ghz P3 768mb ram, 64mb Nvidia GFX card to a 2.40ghz P3, 1gb ram, and a 256 Ati Radeon 9800XT. I am running from the Live CD right now and I would liek to not have to reinstall Ubuntu as I already have everything I want installed and its too much to replace.


EDIT: Sorry, title may be misleading. Its the X Server thats screwing up. It says it has no screens.

I wonder the processors on both computers: Intel of AMD?

---

### Post by brad1150 on 2007-07-30
I said in my post they were pentiums, but the 2.40ghz is a P4. I may just end up installing Mandriva.

---

### Post by w4ett on 2007-07-30
Try this...from recovery mode/CLI type:
```

sudo dpkg-reconfigure xserver-xorg
```

and set your video driver to ati. this SHOULD get you back to a GUI.

---


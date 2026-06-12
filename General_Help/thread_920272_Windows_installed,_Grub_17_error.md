---
title: "Windows installed, Grub 17 error"
date: 2008-09-15
forum: General Help
---

### Post by rmlewisuk on 2008-09-15
Ok, so I installed Ubuntu onto my Acer Travlemate 2490. I meant to do it so I could dual boot with xp. But I installed onto the whole hard drive so obviously xp was overwritten. So I thought I would give it another go by restoring my xp from my back up disk. All seemed fine during installation until I tried to boot my machine up, and all I got was the Grub error 17. I have searched the forums which havnt really helped as most of the posts refer to having linux installed, which as of this moment, I dont. If anyone walk me through what I need to do that would be great.

NB: I have every intention of install Linux again, unfortunatly I need it for a windows specific software that I have to use for work.

---

### Post by DFlame on 2008-09-15
If you installed Windows from a backup disc, it's likely that it wiped the drive before installing. Here's some infor on how to recover GRUM and more about the error message you encountered:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

DFlame

---

### Post by caljohnsmith on 2008-09-15
Do you have a Windows Install CD or just a back up CD? If you have a Windows Install CD, just boot it up, go to the recovery console (press "r" at the first menu), and run:
```
fixmbr
```
That's all you need to do to restore the Windows master boot record (MBR) to overwrite Grub. If you don't have a Windows Install CD, you can still restore the Windows MBR from your Ubuntu Live CD, but it's a little more involved. Let me know how it goes or if you need to do it from the Live CD.

---


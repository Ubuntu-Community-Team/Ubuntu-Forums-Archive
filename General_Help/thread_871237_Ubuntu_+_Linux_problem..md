---
title: "Ubuntu + Linux problem."
date: 2008-07-26
forum: General Help
---

### Post by somescrub on 2008-07-26
I first installed Windows XP then Ubuntu on the same hard drive it was working fine. Then i reinstalled XP on the same partition as it was on and it just boots into XP and my Ubuntu partition is still there. I tried using the ubuntu installation CD. Is there another way that i can get the GRUB boot screen back? : (

---

### Post by Sealbhach on 2008-07-26
Did you follow these steps here when using the Live CD?

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If so, what went wrong? It usually works no problems.



.

---

### Post by somescrub on 2008-07-26
> **Sealbhach said:**
> Did you follow these steps here when using the Live CD?

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If so, what went wrong? It usually works no problems.



.

Well after they both were installed i reinstalled windows! that caused the problem

---

### Post by somescrub on 2008-07-30
halp?

---

### Post by Mgiacchetti on 2008-07-30
[your requested help]("http://ubuntuforums.org/showpost.php?p=5488518&postcount=6")

start reading around #4 below the red text.

---

### Post by caljohnsmith on 2008-07-30
Mgiacchetti, #4 from that link you gave says "If you run into problems with not being able to boot back into windows... (you installed GRUB on the MBR by accident)". I think you may have misread what somescrub said, he said he wants to get Grub back and not replace it with the Windows MBR.

Somescrub, I think this will easily solve your problem: boot from the Live CD, pull up a terminal, and then do:
```
sudo grub
grub> find /boot/grub/stage1
```
For whatever partition it returns, say (hd0,1), then type:
```
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
That will reinstall Grub to the MBR, and Grub will look for its configuration files (e.g. menu.lst) in the (hd0,1) partition.

---

### Post by stchman on 2008-07-30
> **somescrub said:**
> I first installed Windows XP then Ubuntu on the same hard drive it was working fine. Then i reinstalled XP on the same partition as it was on and it just boots into XP and my Ubuntu partition is still there. I tried using the ubuntu installation CD. Is there another way that i can get the GRUB boot screen back? : (

Reinstalling XP wipes the MBR.  Windows apparently is not aware that another OS can be present.

Follow these instructions.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Potatoj316 on 2008-07-30
actually when i installed windows after I already had linux it specifically mentioned "dual boot" in the installer.  It understands that there can be more than one, but it still installed its own bootloader.

---

### Post by koenn on 2008-07-30
> **Potatoj316 said:**
> actually when i installed windows after I already had linux it specifically mentioned "dual boot" in the installer.  It understands that there can be more than one, but it still installed its own bootloader.
It understands that you might want to dual-boot 2 Windows systems, but it completely neglects any other operating system

---

### Post by Mgiacchetti on 2008-07-30
> **caljohnsmith said:**
> Mgiacchetti, #4 from that link you gave says "If you run into problems with not being able to boot back into windows... (you installed GRUB on the MBR by accident)". I think you may have misread what somescrub said, he said he wants to get Grub back and not replace it with the Windows MBR.

Somescrub, I think this will easily solve your problem: boot from the Live CD, pull up a terminal, and then do:
```
sudo grub
grub> find /boot/grub/stage1
```For whatever partition it returns, say (hd0,1), then type:
```
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```That will reinstall Grub to the MBR, and Grub will look for its configuration files (e.g. menu.lst) in the (hd0,1) partition.

and if you would have kept reading (start reading means read until you find the relevant information) you would have found this ```

4.5> [FONT=Verdana]Now, to get your grub installed on the correct drive,
you need to read [this]("http://ubuntuforums.org/showthread.php?t=224351")[/FONT], return when you are done.

```

---


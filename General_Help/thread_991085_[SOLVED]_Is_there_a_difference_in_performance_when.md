---
title: "[SOLVED] Is there a difference in performance when installed from windows?"
date: 2008-11-23
forum: General Help
---

### Post by maduranga on 2008-11-23
I have been using ubuntu since its early releases. But I installed the new version in a different way. using the "install from windows" feature. I want to make sure that after the installation, ubuntu runs as normal as a installation done in the usual way. 

My second question is, I see the ubuntu files in my NTFS partition, Does that means this version of ubuntu uses NTFS file system? or Is there been a file system conversion or something like that? 

after all the things, will it (if there is anything) affect my system performance? 

Any information on "installing ubuntu from windows" is welcome. cons I'm confused!!!!

---

### Post by CatKiller on 2008-11-23
I've never done it, so I can't tell you much about Wubi. However, 
> **maduranga said:**
> I see the ubuntu files in my NTFS partition, Does that means this version of ubuntu uses NTFS file system? or Is there been a file system conversion or something like that?

Ubuntu has always been able to read NTFS filesystems. The ability to safely write to them comes with the ntfs-3g driver. That was determined to be stable enough to be included by default quite some time ago now.

Ubuntu doesn't use NTFS for its own files. NTFS really isn't up to the task. Ext3 remains the default, although there are other options that will also be fine.

---

### Post by Charlie708 on 2008-11-23
I used Wubi one time, and was completely confused as to how it works.  It somehow nests an ext3 FS inside of the existing NTFS volume Windows is currently installed on.  I think it uses a similar method of storage as a VM.

---

### Post by hoze on 2008-11-26
EDIT: moved: [http://ubuntuforums.org/showthread.php?p=6254538#post6254538](http://ubuntuforums.org/showthread.php?p=6254538#post6254538)

i have a similar problem. (win xp and ubuntu installed)
i wanned to free some disk space when i noticed that i have the wubi in my d:\ ntfs partition, it takes 13GB.
i booted the ubuntu and i started Gparted, i wanned to resize the D:\ partition, 
but i cant resize any partition, does that mean that the ubuntu is installed on a virtual partition inside the windows?
my ext3 partition is 15GB, 3.85GB used,
but... 13GB in D:\ubuntu and the 15GB ext3 is too much for 80GB hard drive. 

question: how can i check if my ubuntu is not installed on a virtual partition?
if is or not, is it safe to delete the d:\ubuntu?

thank you.

---

### Post by CatKiller on 2008-11-26
As I said, I don't know exactly how Wubi works. Wubi doesn't just create that folder with the filesystem file in, it also changes your bootloader (otherwise you wouldn't be able to boot it). Wubi comes with an uninstall utility if you don't want to use it any more.

There is apparently a way to migrate your settings from a Wubi install to a separate install, but I don't know what it is, since I haven't used Wubi.

You can't change a partition that's mounted. That partition can't be unmounted, since you're using the partition to run Ubuntu from. If you want to resize that NTFS partition, you can do so by using GParted on your Ubuntu cd.

Wubi might well have some settings for the amount of space your pretend hard drive takes up, but I don't know for sure because I've not used Wubi.

You say that you've got Wubi installed, and an ext3 partition. Did you install Ubuntu twice?

---

### Post by bodhi.zazen on 2008-11-26
> **maduranga said:**
> I have been using ubuntu since its early releases. But I installed the new version in a different way. using the "install from windows" feature. I want to make sure that after the installation, ubuntu runs as normal as a installation done in the usual way. 

You are talking about wubi, and yes it runs just like Ubuntu with a few exceptions.

First, it uses LVM to essentially creeate a virtual Hard drive, which is seen as a file by windows.

Second it uses teh windows boot loader.

See : [http://wubi-installer.org/](http://wubi-installer.org/)

and the FAQ : [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

> **hoze said:**
> EDIT: moved: [http://ubuntuforums.org/showthread.php?p=6254538#post6254538](http://ubuntuforums.org/showthread.php?p=6254538#post6254538)

i have a similar problem. (win xp and ubuntu installed)
i wanned to free some disk space when i noticed that i have the wubi in my d:\ ntfs partition, it takes 13GB.
i booted the ubuntu and i started Gparted, i wanned to resize the D:\ partition, 
but i cant resize any partition, does that mean that the ubuntu is installed on a virtual partition inside the windows?
my ext3 partition is 15GB, 3.85GB used,
but... 13GB in D:\wubi and the 15GB ext3 is too much for 80GB hard drive. 

question: how can i check if my ubuntu is not installed on a virtual partition?
if is or not, is it safe to delete the d:\wubi?

thank you.

What are you wanting to do exactly ? Remove Ubuntu ? Resize Ubuntu ?

These questions too are answered in the Ubuntu wiki page :

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by hoze on 2008-11-27
> **bodhi.zazen said:**
> 
What are you wanting to do exactly ? Remove Ubuntu ? Resize Ubuntu ?


1. how can i check if my ubuntu is not installed on a virtual partition?
2. if is or not, is it safe to delete the d:\ubuntu?
3. will i lose my ubuntu if i delete d:\ubuntu?

---

### Post by philinux on 2008-11-27
If you dont want wubi anymore then uninstall it via add/remove software like any other windows app. 

This then puts your windows bootloader back the way it was.

---

### Post by bodhi.zazen on 2008-11-27
> **hoze said:**
> 1. how can i check if my ubuntu is not installed on a virtual partition?
2. if is or not, is it safe to delete the d:\ubuntu?
3. will i lose my ubuntu if i delete d:\ubuntu?

How did you install Ubuntu ? Did you use wubi or did you install it after booting the live CD ?

I assume by d:\ubuntu you mean a file on your D drive , in which case you are asking about wubi.

The removal procedure for wubi is in the links I gave you earlier.

If you installed from the live CD you remove it in a different way and you can not simply remove the partition.

If you could clarify what you did exactly and which step you are having a problem with I could be more specific.

---

### Post by maduranga on 2008-11-27
> **bodhi.zazen said:**
> You are talking about wubi, and yes it runs just like Ubuntu with a few exceptions.

First, it uses LVM to essentially creeate a virtual Hard drive, which is seen as a file by windows.

Second it uses teh windows boot loader.

See : [http://wubi-installer.org/](http://wubi-installer.org/)

and the FAQ : [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)



What are you wanting to do exactly ? Remove Ubuntu ? Resize Ubuntu ?

These questions too are answered in the Ubuntu wiki page :

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Thanks for the information

---

### Post by hoze on 2008-11-28
> **bodhi.zazen said:**
> How did you install Ubuntu ? Did you use wubi or did you install it after booting the live CD ?

I assume by d:\ubuntu you mean a file on your D drive , in which case you are asking about wubi.

The removal procedure for wubi is in the links I gave you earlier.

If you installed from the live CD you remove it in a different way and you can not simply remove the partition.

If you could clarify what you did exactly and which step you are having a problem with I could be more specific.

i made a bootable usb drive from my winblows.
i remember running the autorun within windows.
also i booted the ubuntu from the usb without installing.
after that i think i booted the usb and istalling it.. 
never mind, cant remember clearly anyway.
i had 13GB in d:\ubuntu, but also i had a ext3 partition
and i Uninstalled the ubuntu from Winblow's add / remove programs.
and the d:\ubuntu was removed.
but my ubuntu is still here, i am writing from ubuntu now.
i probably installed the ubuntu twice, but i am 90% sure that i didn't did that. 

thank you for your answers, problem solved.

---


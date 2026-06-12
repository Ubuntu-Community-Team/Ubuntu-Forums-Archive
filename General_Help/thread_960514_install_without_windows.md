---
title: "install without windows"
date: 2008-10-27
forum: General Help
---

### Post by tjustleft on 2008-10-27
Sorry if I already posted this. My connection broke and I can't find the post now. Anyway.

I read somewhere that you must have windows installed before installing ubuntu. My daughter's computer fried and I put together another for her. We can't afford now to buy windows. Can ubuntu be installed on a fresh machine that has no os on it? If so how?

Thanks.

---

### Post by logos34 on 2008-10-27
> **tjustleft said:**
> 
I read somewhere that you must have windows installed before installing ubuntu. 

Incorrect.  The reason they say that is because windows will overwrite the linux bootloader (i.e. grub) with its own.  But you can easily fix that by restoring grub from the live cd.  So its *better* to install windows first, but not necessary.

To install ubuntu on a blank HDD, follow this:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by bodhi.zazen on 2008-10-27
Not true, just install Ubuntu and use the entire disk (or go with the defaults).

---

### Post by Nuverde on 2008-10-27
> **logos34 said:**
> Incorrect.  The reason they say that is because windows will overwrite the linux bootloader (i.e. grub) with its own.  But you can easily fix that by restoring grub from the live cd.  So its *better* to install windows first, but not necessary.

To install ubuntu on a blank HDD, follow this:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

It is important to note that it is only "better" to install Windows first IF you plan to have BOTH Windows and Ubuntu installed on the same system.  But as the OP doesn't seem to want Windows at all, there is no benefit to installing Windows on the system first.  They can go ahead and install Ubuntu by itself.  In fact, it can be easily argued that an Ubuntu system with no Windows at all is much better than a system running both OSes.

---

### Post by tjustleft on 2008-10-27
Thanks.

> **Nuverde said:**
> In fact, it can be easily argued that an Ubuntu system with no Windows at all is much better than a system running both OSes.

I am starting to agree with that. I tried it as dual boot with windows 98. Ubuntu seemed to pick up bad habits from 98. One of them is reporting less memory than I have. First I had 256 mb and both OS's said 96 mb. I replaced the 256 with a 512 stick and they show 480. That's better but still wrong.

---

### Post by ad_267 on 2008-10-27
I think the context of that was that if you want both Ubuntu and Windows, then you need to install Windows first, rather than installing Ubuntu and then Windows.

It's perfectly normal/easy to install Ubuntu without Windows installed.

---

### Post by SunnyRabbiera on 2008-10-27
Ubuntu can probably run on any computer without windows already on the drive, the only issue you might encounter if you install Ubuntu on a blank system is if you want to install windows afterwards as windows both wants to use the whole drive itself and it will overwrite grub the linux bootloader.
Its just easier on systems to install windows first, but its not impossible to install Ubuntu on a computer without windows on it.

---

### Post by alienprdkt on 2008-10-27
> **tjustleft said:**
> Thanks.



I am starting to agree with that. I tried it as dual boot with windows 98. Ubuntu seemed to pick up bad habits from 98. One of them is reporting less memory than I have. First I had 256 mb and both OS's said 96 mb. I replaced the 256 with a 512 stick and they show 480. That's better but still wrong.


I think you may have 32mb dedicated to video??

---


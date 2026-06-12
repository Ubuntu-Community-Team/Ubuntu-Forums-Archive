---
title: "grub loading error"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by mrfab on 2009-05-01
Hi All
I have Ubuntu dual booting on my notebook (latest 9.04) with XP. All was working fine but all of a sudden I can't boot it into anything, I get a grub error 15.

I have 2 possible reasons that I can think of.
1. I hibernated XP, can that effect the grub loader so that I can't get back in?
2. I deleted a minor partition and recreated it to show a student how. It had no data on it and was just a working partition I use when doing video editing.

Looking for Ubuntu help I found some instruction for fixing, namely Boot from the CD Open a terminal Type the following commands Sudo grub Root (hd,0) Setup (hd,0)

I get into grub ok but all other commands say "Unrecognised command"

Any ideas?

Michael

---

### Post by zeex on 2009-05-01
> **mrfab said:**
> 
Looking for Ubuntu help I found some instruction for fixing, namely Boot from the CD Open a terminal Type the following commands Sudo grub Root (hd,0) Setup (hd,0)

Michael

Hi, 

I think your problem is that you are using capital letters (Root , Setup ..) here try this.

```
**$** sudo grub
```
This 'll take you to grub prompt. 

```
**grub>** find /boot/grub/stage1
``` 
It ‘ll give you something like …. (hdX,Y) example (hd0,1) 

```

**grub>** root (hd0,1)
**grub> **setup (hd0)
**grub> **quit

```

This should help. Don't use capital letters in Linux. All the commands are in small letters. IF you want to try Linux again use 8.04 it's much better and relatively bug free.

Good luck :)

---

### Post by mrfab on 2009-05-01
Thanks

that all worked. I won't give up that easy :-), oh and it was on (hd0,4)

Michael

---


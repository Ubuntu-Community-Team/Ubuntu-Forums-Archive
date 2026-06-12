---
title: "R9 390 Default kernel is Radeon not AMD GPU"
date: 2020-06-20
forum: Hardware
---

### Post by csesztes on 2020-06-20
Hi Guys,

I tried several distros (not just Ubuntu derives), but all of them were having Radeon as its default GPU kernel instead of AMDGPU.
Could somebody please explain why and why AMD GPU can not be the default one? Is there an option to choose this during installation?

 I always need to blacklist if I want my DXVK up and running.

Thanks in advance.
Csesztes

---

### Post by QIII on 2020-06-20
Since that GPU is GCN 1.2, I would expect that the amdgpu module would load.

How have you determined that the radeon module is loaded?

Can you provide your machine specs?  Desktop?  Laptop?  Hybrid graphics (Intel/AMD)?  Dual graphics (AMD/AMD)?

---

### Post by Yellow Pasque on 2020-06-20
> **QIII said:**
> Since that GPU is GCN 1.2

Really? Wikipedia has it listed as GCN 1.1  (I know it's not easy to keep straight with all the rebadging and marketing tricks).
[https://en.wikipedia.org/wiki/List_of_AMD_graphics_processing_units#Radeon_R5/R7/R9_300_series](https://en.wikipedia.org/wiki/List_of_AMD_graphics_processing_units#Radeon_R5/R7/R9_300_series)

Try this (if you don't like vim, use whatever text editor you want):
```
sudo vim /etc/default/grub
```
Find the GRUB_CMDLINE_LINUX_DEFAULT line and add these two parameters:
```
radeon.cik_support=0 amdgpu.cik_support=1
```
So the complete line should look something like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.cik_support=0 amdgpu.cik_support=1"
```
When you're done, save the file, quit the editor, and run:
```
sudo update-grub2
```

---

### Post by QIII on 2020-06-20
Right you are.  I thought is was 1.2.  Still, 1.1 should be using amdgpu.

---

### Post by Yellow Pasque on 2020-06-20
> **QIII said:**
> 1.1 should be using amdgpu.

It's still considered "experimental", but maybe that will change: [https://phoronix.com/scan.php?page=news_item&px=AMDGPU-GCN1.0-UVD-2020](https://phoronix.com/scan.php?page=news_item&px=AMDGPU-GCN1.0-UVD-2020)

---

### Post by csesztes on 2020-06-20
Desktop
CPU: I7 4770K
GPU: XFX R9 390
Memo: 8GB DDR3
Mob:MSI Z87-GD65 GAMING

---

### Post by csesztes on 2020-06-20
Thanks for the commands, but I am currently on Win 10. The point of my thread was if it is possible to avoid these steps in the first place.
I tested Solus roughly 1 year ago and that was the only distro so far which had amdgpu as its default gpu kernel.

---

### Post by Yellow Pasque on 2020-06-20
> **csesztes said:**
> The point of my thread was if it is possible to avoid these steps in the first place.
It's only a one-time procedure.

> I tested Solus roughly 1 year ago and that was the only distro so far which had amdgpu as its default gpu kernel.
I've never used Solus, so I have no idea. Maybe they build their kernel that way. You can always build your own kernel, but it would be a heck a lot quicker/easier to add the parameters to GRUB..

---


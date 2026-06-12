---
title: "Toshiba A100 w/ phoenix bios"
date: 2007-07-15
forum: Hardware &amp; Laptops
---

### Post by nwadams on 2007-07-15
hi

so my sound just spontaneously started working correctly so that makes me happy...

but i still cannot adjust brightness at all on my A100 with the phoenix bios...is there anything I can do to fix this
i've updated bios and everything, 

if i cannot get the gnome power manager to recognize my lcd brightness control is there some command line way to dim my screen if i need to, so i can save batteries

thanks

---

### Post by lisati on 2007-07-15
I'd like to know too....

---

### Post by nwadams on 2007-07-15
bump

---

### Post by lisati on 2007-07-22
> **nwadams said:**
> bump

Bumpity bump

---

### Post by Axed on 2007-10-23
I know bumping threads that are months old is bad form, but I'm also having trouble with suspend on my Toshiba A100 (PSAA9A-00S00F). This is Core Duo model (not Core 2), with an Intel core chipset and ATI graphics adaptor. I'm using the ATI binary driver installed via the restricted drivers manager, and the bios is the latest version, 5.90.

The problem is that it doesn't go into suspend mode at all, the screen goes black and it just hangs, requiring me to hold down the power button for 5 seconds to power it off. Hibernate does exactly the same thing.

So far I've tried numerous suggestions from various sources, including compiling the "omnibook" kernel module from svn - an acpi module which is designed for Toshiba Satellites and HP Omniboks that use the Phoenix bios. This didn't really do anything except allow access to a few extra functions such as bluetooth, and it also seemed to break the lcd brightness adjustment, although that was sporadic anyway.

It would appear that suspend is handled by the core ACPI module, which makes sense as it's supposedly a standard ACPI function, which *should* function the same way on any computer. Except ones with a Phoenix bios.

Has anyone had success with suspend on these models? It's a critical function on a laptop and I really don't want to use windows! :confused:

---

### Post by devel3 on 2007-10-24
Hi Axed, I have a Toshiba A100 ( PSAARE-04K019SP) with Intel Core 2 Duo and Nvidia Geforce Go 7300. I have exactly the same problem: when I resume the laptop, after a suspension, the screen doesn't work. The bios, that I downloaded from toshiba, is the 5.90. I haven't tried the omnibook module because I think that it won't work. The suspend-to-disk (Hibernate) works perfectly on my laptop with Gustsy Gibbon Ibut I prefer suspend-to-ram.

A question, when I resume, apart from the screen, the keyboard doesn't work, I mean, when I press the caps lock button, it doesn`t light. Have you got the same problem?

Some days ago I posted the same problem here... :)
[http://ubuntuforums.org/showthread.php?t`t=575598]("http://ubuntuforums.org/showthread.php?t=575598")

Excuse me, my English isn't very good, I am from other country.

---


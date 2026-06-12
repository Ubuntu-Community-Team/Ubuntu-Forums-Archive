---
title: "Can't install on my laptop"
date: 2008-09-02
forum: Hardware
---

### Post by kvalis on 2008-09-02
Can anyone help help me. I've got a laptop I used to run XP on. My girlfriend got a new laptop, so I thought it was time I tried to install Ubuntu on the old one.  It is set to boot from CD, it loads the splash screen - but then everything stops.  Tried out a couple of other distros as well, but to no avail - the same thing happened there.

Any ideas??

Or, is it possible to somehow install Ubuntu without waiting for X Windows to load??


Tore

---

### Post by jolx on 2008-09-02
sure you can install ubuntu, all you need to do is install it

---

### Post by jolx on 2008-09-02
ok serious

how much ram do u have?

---

### Post by in-dust-rial on 2008-09-02
if you are desperate enough:
disable boot from floppy disc, and disable all floppy disc soupports in bios!
older versions of ubuntu-installer look for floppy disc, and hang when they dont see one!


good luck

if the liveCD hangs itself ... bad thing, ... but if you can browse the options, try to look at some boot options:

```
https://help.ubuntu.com/community/BootOptions
```
acpi issues may be the problem (thats what my BSD experience says ;D, so maybe very wrong)

AND TRY TO HAVE A LOOK AT YOUR LAPTOP MODEL here:
```
http://www.linux-laptop.net/
```

if this doesnt help, post version of your liveCD(or date when downloaded) give the model of your LAptop and maybe version of the bios ... 
without this helping you is guessing around!











===> and do checksum test on the livecd, maybe^^

---

### Post by kvalis on 2008-09-02
Thanks for your suggestions. Got 756MB of RAM, the laptop is about 5 yrs old. Will return later with BIoS info. Tried latest versions (live CD's) of Ubuntu, Mint, Mandrake and SUSE

Tore

---

### Post by kvalis on 2008-09-02
BIOS is American Megatrends Inc. ver. 0206 Firmware 101.114

---

### Post by in-dust-rial on 2008-09-02
and now a better description of what goes wrong... when does the system crah... can you take any actions? can you browse the livecd menu?

good luck

---

### Post by ugm6hr on 2008-09-02
Did you check md5 and do check disc on boot?

Have you tried Safe graphics mode?

If yes to all - try AlternateCD.

---

### Post by dodle on 2008-09-02
This sounds just like the problem I was having with my old laptop.  The only distros I could get to install were Debian Etch and Ulteo, but I wanted Ubuntu, so bad that I even tried converting my Debian install into Ubuntu through the Ubuntu repositories (which ALMOST worked :p).  What worked for me, in the end, was installing an older version of Ubuntu (6.06) then upgrading it to 8.04.  You can give that a shot.  Or, you can reinstall Windows then download and install Wubi, which is just like having a regular Ubuntu installation.

---

### Post by in-dust-rial on 2008-09-02
i dont think upgrading from ubuntu 6.06 is a good idea!
i got often problems with system upgrades.:mad:

```
http://ubuntuforums.org/showthread.php?t=282094
```
use google!
try stuff ugm6hr says!
try this install wubi, like dodle says!
explain your problem in detail!
change the kernel-boot parameters!

but hell yeah, try to avoid the upgradeing from 6.06

good luck

---

### Post by IntuitiveNipple on 2008-09-02
When the initial Ubuntu LiveCD menu appears, choose F6 (Other Options) and the kernel command-line will be shown for editing. Use the backspace key to remove ffrom the end of the line the part that reads:
```

quiet splash --

```
Press the Enter key and the kernel will boot. It will now display all the kernel messages as it boots and you will get a good indication of when and what causes the problem.

If possible, photograph or copy the relevant messages so we can come up with some suggestions.

---

### Post by kvalis on 2008-09-04
Tried the boot option.  See enclose .jpg file for details

---

### Post by kvalis on 2008-09-19
Hello again! 

Have had no replies to my post for over a week, so I thought I would update you a little bit.

Have tried Ubuntu, LinuxMint, Suse, Slax, Mandriva.  None of them worked past the startup screen.

I have been able to install PC-BSD, sooooo eeeeeeasyyyyy -  and GParted worked as well.

Any fresh ideas whether I can install Linux on the laptop or not? - and how do I go about it

It's a ASUS M2400N with 756MB of RAM

Tore

---

### Post by kvalis on 2008-10-11
Re-installed windows,downloaded ASUS Flash Bios update, and voila. That update of Bios let me install Ubuntu.

Thank you myself!

Tore

---

### Post by linux_tech on 2008-10-11
Be better to install new copy instead of trying to upgrade from 
earlier version.  You could probably run live cd install,
but the alternate cd install would be best due to the limited hardware (memory). I'm guessing the i386 version is the one you want.
[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

---

### Post by stylis on 2008-10-29
Tried to install Xubuntu 8.4 on an older laptop with 512mb memory, 80gb HDD BUT Amibios Hiflex version 1.30 Build date 15/7/1995.
After the opening menu I selected Install and it returned the message: Bios 1997 failed the 2000 cutoff date. APCI 1.0 requires forced ...etc. 
I assume that older versions of Xubuntu will work with that Bios/APCI. Can anyone tell me if this is so?

---

### Post by ugm6hr on 2008-10-29
> **stylis said:**
> Tried to install Xubuntu 8.4 on an older laptop with 512mb memory, 80gb HDD BUT Amibios Hiflex version 1.30 Build date 15/7/1995.
After the opening menu I selected Install and it returned the message: Bios 1997 failed the 2000 cutoff date. APCI 1.0 requires forced ...etc. 
I assume that older versions of Xubuntu will work with that Bios/APCI. Can anyone tell me if this is so?

Since Feisty (7.04), Ubuntu requires BIOS 2000+

Any chance you could fing a newer BIOS for your motherboard? Google's a good place to start.

If not - try another distro.  Edgy is no longer supported at all.

---


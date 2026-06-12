---
title: "Each version progressively worse"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by xJohnnyx on 2009-05-12
I am still stuck on ubuntu 7.10, if anyone could help me get 9.04 up and running this would be great.

Each version since 7.10 has had some problem at boot (I don't even get to the install screen) and it is getting worse and worse each time. At 8.04 it would just hang when the desktop would load via live CD. Ok, fine, i'll wait till the next version whatever. 8.10, I dont even get that far, after the loading screen with the orange bar going back and forth i get io errors like so:

[IMG]http://img21.imageshack.us/img21/3871/fgbfdgwow.jpg[/IMG]

Now on 9.04, I don't even get near that! The menu comes up, I select English, and every option makes the computer stall for about a minute then a red messagebox pops up and says IO Error and the only option it gives me is to reboot. 

Now before everyone uses the typical excuse and blames it on burning problems, it isn't a problem with CD burning. I've checked MD5 sums, burnt about 3 copies myself. Then I ordered an official CD from canonical just in case. The CD they prepared is even giving me these errors. I doubt it's my CD burner as I am able to boot from any other linux CD just fine. Gentoo, SuSE, Fedora, Arch, Slax.... all perfect. Ubuntu: ****.

I thought the main approach was to make it compatible with most hardware... Not like my system is old or anything, P5K SE/EPU, E8400, 8GB DDR2 dual channel, 2x1TB Caviars, LG DVD burner.

Windows install works fine, every other linux install works fine, every other bootable CD works fine and my hardware isn't old, and not very new. I mean, it was supported in ubuntu 7.xx, it's obviously not a case of the hardware being too new. I thought Ubuntu strived for compatibility... Is there something I'm missing?

It would be a good idea in future versions to test compatibility on a wide range of computers before shipping.

---

### Post by lisati on 2009-05-12
I'm sorry to hear of your bad experience. 
The error message seems to suggest that your computer is having trouble reading the disk for some reason, which could be anything from a "bad" burn to a CD/DVD drive that needs maintenance.
Please forgive me if you've tried these already: have you used the "Check disk for errors" option on the CD? Do you have another CD/DVD drive that you can use? Do have some lens cleaning paraphenalia that could check your CD/DVD drive?

---

### Post by xJohnnyx on 2009-05-12
> **lisati said:**
> I'm sorry to hear of your bad experience. 
The error message seems to suggest that your computer is having trouble reading the disk for some reason, which could be anything from a "bad" burn to a CD/DVD drive that needs maintenance.
Please forgive me if you've tried these already: have you used the "Check disk for errors" option on the CD? Do you have another CD/DVD drive that you can use? Do have some lens cleaning paraphenalia that could check your CD/DVD drive?
If you read over 10% of my post you wouldn't have asked any of that

---

### Post by whoop on 2009-05-12
Maybe boot from usb stick if you have that lying around. So you can eliminate CD-drive problems. I know the chance that your cd is bad or your cd drive is bad is negligible (but thats what the CLI is saying or at least thinking).

---

### Post by lisati on 2009-05-12
> **xJohnnyx said:**
> If you read over 10% of my post you wouldn't have asked any of that

:) Try whoop's suggestion of a USB stick if you can so that you can be sure that it's definitely not a CD drive problem. Some problems are subtle, and are tricky to troubleshoot.

Friendly teasing about "not born yesterday" skipped in the interests of avoiding a flame war. Keep on smiling!

---

### Post by whoop on 2009-05-12
Looks like the bug or a similar one was reported here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266951](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266951)

There are some solutions in the comments. Some don't even require you to burn (any more) or put it on usb. As an example:
> 
At the boot prompt, just after the language choice, press F6 and simply add this parameter : all_generic_ide
It solved everything for me ! No more error messages !


If I read the report, I think you do not have a burning problem, it's possibly a device problem (not necessarily blaming it on the device here, more as in Ubuntu has problems with the device).

---

### Post by lovinglinux on 2009-05-12
Do you have a HP or Compaq notebook? 

Check the bottom of your notebook and verify the name of the motherboard manufacturer.

I'm asking this because I have a Compaq and the problem is related to a hack made by the manufacturer on the motherboard to get the Vista compatibility logo. This hack mess with Linux installations, specially those with most recent kernel like Ubuntu 8.04 and newer. So not Ubuntu fault. 

I had the same IO errors. I tried special parameters for installation like noapic and nolapic but nothing worked. I was able to install Ubuntu 9.10 after creating the ext3 partitions from inside the Windows installation, using Partition Magic.

---

### Post by xJohnnyx on 2009-05-12
> **lovinglinux said:**
> Do you have a HP or Compaq notebook? 

Check the bottom of your notebook and verify the name of the motherboard manufacturer.

I'm asking this because I have a Compaq and the problem is related to a hack made by the manufacturer on the motherboard to get the Vista compatibility logo. This hack mess with Linux installations, specially those with most recent kernel like Ubuntu 8.04 and newer. So not Ubuntu fault. 

I had the same IO errors. I tried special parameters for installation like noapic and nolapic but nothing worked. I was able to install Ubuntu 9.10 after creating the ext3 partitions from inside the Windows installation, using Partition Magic.

My mobo manufacturer is ASUS, I built this system myself, as I do with all of my systems. Whoop your suggestion has gotten me the furthest so far using the all_generic_ide boot option. It gets me to the startup where it starts the various daemons and says [OK] after each one, then stops half way and throws me a tty3 error, and says it is restarting the init process, then hangs there.

---

### Post by whoop on 2009-05-12
> **xJohnnyx said:**
> My mobo manufacturer is ASUS, I built this system myself, as I do with all of my systems. Whoop your suggestion has gotten me the furthest so far using the all_generic_ide boot option. It gets me to the startup where it starts the various daemons and says [OK] after each one, then stops half way and throws me a tty3 error, and says it is restarting the init process, then hangs there.

I added your problem to the existing bug report, cause I agree with you that this bug needs fixing (and you are not the only one having the problem).
I understand you are fed up with burning but did you by any chance try the alternate cd install?

---


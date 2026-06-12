---
title: "Unable to install versions newer than 10.04"
date: 2012-03-18
forum: Hardware
---

### Post by mathiaho on 2012-03-18
Hi

I have a Toshiba Satellite L650D-15G (AMD Phenom II N850, ATI Mobility Radeon™ HD 5650)

It can run Ubuntu 10.04 fine, but I would really like to install a newer version

I have tried installing 10.10, 11.04, 11.10 and 12.04, (both 64 and 32 bit) all with the same result:

I can reach this screen: [http://ubuntuforums.org/showpost.php?p=10740097&postcount=3](http://ubuntuforums.org/showpost.php?p=10740097&postcount=3)

Whenever I select "Try Ubuntu without installing" or "Install Ubuntu", I get a black screen with a white blinking cursor.

I have tried all the different modesettings. None of them helps.
I've also tried upgrading the system from 10.04, but all I get when rebooting is the damn black screen and white blinking cursor.

Any ideas?

Thanks

---

### Post by recluce on 2012-03-19
Did you try the "alternate install" CD?

---

### Post by mathiaho on 2012-03-19
Oh, sorry about not mentioning that. I've tried the alternate install. Same symptoms occur.

---

### Post by recluce on 2012-03-21
Hmm. Not too many things come to my mind. You could try to isolate a possible kernel issue. To do this (from Lucid), install a newer kernel (eg 2.6.38-13) from the lucid-proposed/main repository. Try to boot that kernel. If you get the black screen, you know it is strictly a kernel issue on your hardware. The good thing is that you will not break your machine, as you can simply boot to the older kernel again.

---

### Post by mathiaho on 2012-03-21
Kernel issue is my bet as well. I'll do what you wrote tomorrow and post back then. Thanks

---

### Post by mathiaho on 2012-03-22
It's confirmed: 2.6.38-13 does not boot.

When booting 2.6.38-13 in recovery mode it stops after:

```
[        1.132277] pci_root PNP0A08 :00 : host bridge window [mem 0xfed45000-0xffffffff] 
```

The numbers in the first bracket are different every time I boot, but the rest are the same.

What should I do now?

---

### Post by recluce on 2012-03-23
> **mathiaho said:**
> It's confirmed: 2.6.38-13 does not boot.

When booting 2.6.38-13 in recovery mode it stops after:

```
[        1.132277] pci_root PNP0A08 :00 : host bridge window [mem 0xfed45000-0xffffffff] 
```

The numbers in the first bracket are different every time I boot, but the rest are the same.

What should I do now?

Good question. Does the 3.0.0-17 kernel boot(also in the proposed repository)? Did you test with both 32bit and 64bit versions of Ubuntu?

You could file a bug on launchpad (not that I have high hopes for that). You could try another flavour of Linux (Feodora or OpenSUSE Live CDs come to mind) to nail it down to either a general problem with your machine or an Ubuntu-related problem (they do modify the kernels).

Last not least: try to find out if other owners of the same machine run Ubuntu successfully (google, forum search). If so, you might have a flaky motherboard.

---

### Post by mathiaho on 2012-03-23
3.0.0-17 does not boot. But it gives us some more info:

```

[    0.745026] pci_root PNP0A08 :00 : host bridge window [mem 0xfed45000-0xffffffff]
[    0.745075] pci_root PNP0A08 :00 : address space collision: host bridge window [mem 0x000cc000-0x000cffff] conflicts with Video ROM [mem 0x000c0000-0x000cf1ff]
[    0.745124] pci_root PNP0A08 :00 : address space collision: host bridge window [mem 0x000d0000-0x000d3fff] conflicts with Adapter ROM [mem 0x000cf800-0x000d07ff]

```Then it stops.

I've only tried 64bit versions of these kernels, but as mentioned in my opening post, I've tried both 32bit and 64bit clean installs, all with the same problems. Should I try the 32bit versions of these kernels as well?

I' ve found at least one forum-user with the exact same laptop model, who seems the same problem as me. I'll invite him over.

---

### Post by mathiaho on 2012-03-23
After searching for address space collisions like these, I've started to suspect this have something to do with UEFI:

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

My Toshiba runs InsydeH2O

---

### Post by mathiaho on 2012-03-23
I've found a lot of bugs describing address space collisions in newer kernels, and pci=nocrs is a common workaround. However it just gives me another last message before freezing:

```
ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
```

---

### Post by recluce on 2012-03-24
If it is related to UEFI-boot, do you need to use UEFI? If not, does your BIOS Setup allow you to disable UEFI and use a plain BIOS boot? I write this from a Dell Precision M4500 (which has UEFI), but the boot mode is set to BIOS - no problems with that.

---

### Post by mathiaho on 2012-03-24
No such option in setup, I'm afraid.

I'm not completely sure that UEFI is the problem though, only that many who has had similar problems had them because of UEFI. In those fora the solution was usually PCI=nocrs, which doesn't help me at all.

---

### Post by recluce on 2012-03-25
I am starting to run out of ideas here. As this is a video / chipset address collision, do you have "Optimus" style graphics, that is graphics that are switchable between an on-CPU graphics processor and a dedicated GPU (NVidia, ATI)? If yes, can you disable this in your BIOS Setup? That might be worth a try.

Also, did you try some other distro live CD, like Fedora or SUSE? While I have my doubts that this might help, it could be worth a try.

---

### Post by mathiaho on 2012-03-25
No luck.

There's no graphics option in setup.

I tried Fedora now, and I got the exact same result as I did in post #8

---

### Post by recluce on 2012-03-25
I guess I am officially out of ideas now. You might try Debian with the FreeBSD kernel, but that is far away from what you wanted. I also assume that there is no BIOS update available for your machine?

---

### Post by mathiaho on 2012-03-26
Actually there is a BIOS update. I'm fetching my win 7 dvd now (the bios update is a windows installer)

I want Ubuntu. Not only because it's such a nice OS to use, I'm also interested in the realtime-priorities possible in the newer linux kernels (I've used the rt kernels before).

I guess I can use Lucid a bit more, but what should I do when Lucid's no longer supported?

---

### Post by mathiaho on 2012-03-26
I just found a thread on the Toshiba support forum:

[http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=60636](http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=60636)

> 
I have been able to install Ubuntu on my Toasiba satellite L650D 

Ubuntu 10.04 
On the purple screen press any key
Press F6
Press escape
now press Tab and add
 pcie_aspm=off
Hit enter and be patient, it worked for me.

Same procedure with Ubuntu10.10  and  11.04
But before you reboot:
open gedit in terminal
Edit the file /etc/default/grub   insert  pcie_aspm=off as boot option

GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash pcie_aspm=off&#8221;

save and recompile grub.cfg with the command:

sudo update-grub

Good luck.

 Bozox

I'll try that if BIOS update isn't enough

---

### Post by mathiaho on 2012-03-26
Guess what? The BIOS update solved everything! I feel stupid now, since it wasn't the first thing I tried (I have updated BIOS on this machine before for hardware reasons, and it didn't solve anything, so I didn't have high hopes for it).

So I guess the old saying is right: Always check if your BIOS is up to date

To summarize:

Toshiba Satellite L650D w****ith BIOS version 1.80 + Ubuntu 12.04 works like a charm!

Thanks so much for your help, recluce!

---


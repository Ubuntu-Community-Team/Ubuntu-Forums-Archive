---
title: "Installation on Dell Inspiron 2650 - Fails to go on after Install is selected"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by Poison Rain on 2009-04-27
Hi,

I had an old Dell Inspiron  2650, decided to install Ubuntu JJ on it, got the ISO burnt a live CD, got Gparted formatted the drive to ext2, created s swaps-space and booted the laptop with the live cd.

I get to see 

1. language selection page

2. then i get to select Install Ubuntu

3. I get a blank screen and nothing more...when i am to get the welcome window!!!

any pointers as to why this could be>

thank you,
-Uday

---

### Post by Dearhell on 2009-04-27
What's your graphic card?

You should see [this](http://ubuntuforums.org/showthread.php?t=1133931) and [this](http://ubuntuforums.org/showthread.php?t=1138302)

---

### Post by Poison Rain on 2009-04-27
Hi,

It looks like i may have shot myself in the foot here, i have no OS on the laptop at the moment. So i cant see much info...

I thun the problem is that it needed 384MB ram i have only a 256MB, so i am now trying Xubuntu.

hope that works.

Thank you for your pointers.
-Uday

---

### Post by JB7 on 2009-04-27
I have the same laptop (Dell Inspiron 2650).  80GB HD on board, 0.5GB RAM, NVIDIA GeForce2 Go graphics card.  Can't wait to upgrade...get the same results, EXACTLY as above...nothing to see but a blank screen after the LiveCD boot menu.  The LiveCD I created works and boots correctly on numerous other machines, and the LiveCD built-in check shows no errors.  

I tried to download the upgrade thru Update Manager, and the first GRUB entry (Ubuntu 9.04, kernel 2.6.28-11-generic) does the same as the LiveCD.  Can't get out of the blank screen with CTL-ALT-DEL either.  

The second entry (recovery mode) freezes after the following line of output:
[    0.875357] pci 0000:00:1e.0:   PREFETCH window: 0x00000030000000-0x00000035ffffff.  

(I'm not proficient enough yet to figure out how to get a good memory dump to anyone, but I can be coached!)

The third GRUB entry (Ubuntu 9.04, kernel 2.6.27-11-generic) DOES boot, but the Tracker is not indexing properly.  I turned off the e-mail indexing, and rebooted...taking the same numerous errors.  Most of the new GNOME tweaks I saw in the previews do appear on the Desktop.  Everything appears to work except the Tracker and it's indexing.  But I've only been banging on this new install about four hours.  

Apparently, the Jackalope doesn't like my Dell.  That's really a shame because I really don't like WinXP.

Anyone else see the same thing?  Any ideas??  I'm just a bit past a n00b, but not by much...I'm tryin'....#-o


LATER >> removed the Tracker, all seems to be working, but still can't boot to kernel 2.6.28-11-generic...could still use help...

---

### Post by border on 2009-04-28
Well, I have a Dell Inspiron 2500, which I figure should be more or less the same (maybe slightly older?) and I have the same problem.

If you remove quiet and splash from the kernel line (grub menu, press e, select kernel line, press e again, remove quiet and splash, press enter and b), then I see the same line with the pci prefetch window stuff.

Somewhere I read about putting acpi=off in the kernel line, an it does work for me (same procedure as removing quiet and splash, just adding acpi=off instead). It boots fine. Only thing I notice is that if you press the power button, it powers off immediatly.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/343268)

Hope this helps a bit already.

I read that kernel 2.6.29 should be better for people with problems such as ours (I hope so), but that would be for the next release I guess.
Problem is not ubuntu but the kernel

---

### Post by akabigbro on 2009-04-28
I had the same problem with my Dell Inspiron 2650. I am installing it now using the acpi=off kernel parameter. Seems to be working...

Thanks for the info.

---

### Post by JB7 on 2009-04-29
Thanks, all.  With the links and info you included, I found an ubuntuforums page that was for "Troubleshooting ACPI".  I booted several times using the options provided, then altered my GRUB menu entry for the latest kernel with "pci=noacpi" and it boots great.  For my install, this is the option that gives me the ability to boot.  It's specifically the PCI part of the acpi setup that's causing my laptop to stall, so I don't have to disable all the other aspects of acpi to get things booted.

UPDATE: The site I used was _[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI),_ which indicates there's a PCI scanning problem with the combination of the new kernel and my laptop.  So using this option, I don't lose all the other benefits from ACPI support.  You might want to check out the link, "akabigbro".

---

### Post by Poison Rain on 2009-05-21
Thank you all for this treasure trove of information. I was finally able to get my OLD Dell Inspiron 2650 to boot with XUBUNTU 9.04. scored some major brownie points from the M.I.L 

**My system:**
Dell Inspiron 2650
512MB RAM
No OS [cleaned it using GParted]
1.7GHz P4

**Installed XUBUNTU 9.04**

**Encountered issue:**
A black screen after choosing the language and install ubuntu options on the CD
[B]
Went past them by:[/B]
A combination of the previous 2 posts** #6 and #7**

-Uday

---

### Post by jhansonxi on 2010-01-09
Still an issue with Ubuntu 9.10 (Karmic Koala).  Alternate CD install hangs unless pci=noacpi is added to kernel line in Grub.

---

### Post by NorCalDubber on 2010-04-22
Border and akabigbro solution worked for me on my 2650.  Thanks guys!

---

### Post by afrodeity on 2010-05-02
Ive just installed Lucid on a 2650. Install went off bang and everything working fine except the following:

fan not working

keyboard unstable, periodically gets into sticky shift mode, especially if I do anything in network manager.


Tried various acpi options

pci=noacpi makes fan work a bit, but still quite hot

I now have it set to nolapic

there is a also a noacpic option which I have yet to try out.

Set the keyboard option in preferences > keyboard to Inspiron 6xxx/8xxx

Seems to disable the shift key which can be regained by toggling the capslock.

have filed a support request with dell and posted a note on the community laptop support bbs

---

### Post by gabak on 2010-05-15
i found the problem when i used the memtest and it was saying i had errors.
so disabling USB in bios solve my problem.

---


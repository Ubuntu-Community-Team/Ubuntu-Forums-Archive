---
title: "Ubuntu 11.04 64 bit on Lenovo B570"
date: 2011-07-27
forum: Hardware
---

### Post by bph on 2011-07-27
I have a problem installing Ubuntu 11.04 64 bit from CD on my (new) Lenovo B570 laptop

I've set up the BIOS to boot from CD but on startup the CD sounds like it spins up but then nothing happens, screen remains blank or in some instances it has a partially corrupted blank screen

The laptop came pre-installed with Win 7 and lenovo have a 'feature' one stop recovery which I think has a backup of the Win system on a separate partition, possibly this is causing a problem

I have also tried installing Ubuntu form a USB stick with the same 64 bit .iso but same thing happens

Not sure how to progress with fixing the problem as I can't even get to a cmd prompt

regards,
- ben

---

### Post by bph on 2011-07-28
tried installing the 32 bit 11.04 and it worked fine

seems a bit odd as i'm sure the lenovo B570 has 64 bit Win 7 installed running fine

Anyone else successfully got the 64 bit version working on a B570?

A google search seems to indicate they have, but I couldn't find anyone having the same problem as me, e.g. no go on 64 bit but 32 bit works ok

I think ubuntu can still access 4GB of RAM even on 32 bits though so I'm not unduly worried

---

### Post by alan.gustavo on 2011-12-07
Hi,

I have same problem. I try install Ubuntu 11.04 64Bits.
I do the installation ok. 
But, when it restart it not found boot.
Can you help me?
Alan

---

### Post by nailora on 2011-12-17
The bad news: I can reproduce this as described above.

My description of the problem: With an Lenovo B570 notebook it is possible to boot the Ubuntu 11.10 AMD64 64bit CD and (supposedly) install it successfully. I did a clean install giving all hard disk space to Ubuntu, deleting Windows. However upon reboot the operating system does not come up, but booting from network is tried and "PXE-E61 Media test failure, check cable PXE-M0F Exiting PXE ROM" (if no ethernet cable is attached) is displayed. After 5 seconds you can choose to boot from HDD/CD/LAN, but choosing HDD will bring you back to where you started.

Installing the 32bit version with exactly the same steps results in a fully boot-able system, no tweak required.

The good news: Some background information, albeit no real solution.

I am convinced that this is not really related to the selected architecture (64bit vs. 32bit), but an issue with the bootloader installed by Ubuntu. With the 64bit version Ubuntu tries to use a uEFI setup, but what it creates does not work, and from a first inspection should not even work.
The 32bit version does not even try to use uEFI but goes with a master boot record (MBR), and things work the way it is used.

I tried to install the 64bit version with manual formatting of the disk MBR + MSDOS partition table, and replacing grub-efi* with grub-pc after the installation. In theory this should have worked and resulted in a boot-able system, but in my test it did not.

---

### Post by dcrooke on 2011-12-22
I got one for my father for Xmas, after seeing that it was well supported ... I too am having the 64 bit grub problem.

Is there any way with 11.10 and 64-bit to force it to use traditional grub and an MBR, or to retrospectively fix the bootloader that Ubuntu lays down (or fails to ;) ?

Why does this happen only on certain Lenovo systems, and not everything?

To whomever mentioned the "corrupt blank screen" this is simply the Ubuntu CD start screen at the wrong framebuffer layout ... fist option is Live CD, second is installer, 3rd is media check I think

---

### Post by nailora on 2011-12-22
[http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2011-December/050444.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2011-December/050444.html)

All other note apply to the B570 as well, so maybe installing grub legacy might just work (I did not try it yet).

---

### Post by oldfred on 2011-12-22
It looks like it should be UEFI, how is Windows installed and is the partition table gpt not msdos/MBR?

Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.

---

### Post by dcrooke on 2011-12-23
[https://bugs.launchpad.net/ubuntu/+bug/908109](https://bugs.launchpad.net/ubuntu/+bug/908109)

---

### Post by JCoop on 2011-12-26
I believe I was able to solve the problem you are describing. I will post a link below to my solution. I have a lenovo v570 by the way, so it should work the same. Also, there wasnt any conflict with the one key recovery or Windows. I do go into detail about the issues with the 64 bit installation as well. I hope this helps and let me know if you have any more questions. Good luck. 

[http://ubuntuforums.org/showthread.php?t=1863125](http://ubuntuforums.org/showthread.php?t=1863125)

---


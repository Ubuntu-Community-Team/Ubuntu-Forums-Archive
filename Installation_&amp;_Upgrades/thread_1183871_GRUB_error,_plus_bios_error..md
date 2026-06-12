---
title: "GRUB error, plus bios error."
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by drew212 on 2009-06-10
I recently installed jaunty x86 and i couldnt access all of my ram so I tried installing a bios update but the ASUS update utility failed but my memory(ram) magically bumped up to 3.8 gigs from 3.4 gigs. So I just left it be not wanting to fiddle with things.

Now after a few restarts, i got a Grub error 18. Now i consistently get a grub error 17 and i once recieved a grub error 16. All of my Sata settings are set to auto, so I decided to try to reflash to a different bios, but the update utility doesnt work, and EZ flash wont work, giving me a "No bootable signatures found in file" error. So i tried to create a bootable flash drive but with no avail.

Anyone able and willing to help me along here? I keep running into dead ends and I'm thinking about blowing my computer up.


My mobo specs are:
M2N-SLi Deluxe
4Gib of ram
AMD Athlon 64 X2 4200+

---

### Post by dstew on 2009-06-10
One thing, the BIOS does not determine RAM access in Linux, that is the responsibility of the operating system. What I mean is, as opposed to Windows, Linux completely bypasses the BIOS, and has its own primitive hardware access software. I think with x86 Linux, the most RAM that you can access is about 4 Gb, but some of the RAM may be unavailable for general use due to the hardware configuration. I think the AMD 64-bit version of Ubuntu will access much more RAM.

On the other hand, grub accesses RAM by way of the BIOS. If you installed grub with one BIOS, then re-flash it, grub may now be mis-configured (relative to the new BIOS). You might need to re-install grub. It is also possible that the BIOS is corrupted, especially if it seems unable to boot. I would concentrate on getting the BIOS working, so it can at least boot something, like a CD-ROM.

---

### Post by drew212 on 2009-06-10
I can boot my computer up, its just takes a few reboots before I can pass the grub error.

---

### Post by drew212 on 2009-06-10
Actually, after trying to upgrade my bios again my computer stopped booting so i cleared CMOS and this so far has cleared up the issue.

---

### Post by presence1960 on 2009-06-10
32 bit will not see  or utilize 4 GB of RAM. If that is bothering you try 64 bit.

---

### Post by drew212 on 2009-06-10
I am on x86, so it is 64 bit. But it wasnt showing all of my ram on the system monitor.

---

### Post by dstew on 2009-06-11
We mean you have to install the AMD 64-bit version of Ubuntu, not the x86 version. The image file is named ubuntu-9.04-desktop-amd64.iso. That is what you get if you go to the [Download Ubuntu]("http://www.ubuntu.com/getubuntu/download") page and check the 64-bit box under computer architecture. I am not aware that there is an image file with the name x86-64, but please correct me if I am wrong. Even if your processor is an x86-64, download the amd64 version.

---

### Post by drew212 on 2009-06-11
I do have the AMD64 version, but when i type the command that tells me what version i'm running, i cant remember which, it gives me something with an X86_64, but i know its the AMD version.

---

### Post by presence1960 on 2009-06-11
> **drew212 said:**
> I do have the AMD64 version, but when i type the command that tells me what version i'm running, i cant remember which, it gives me something with an X86_64, but i know its the AMD version.

if it reports x86-64 on the command then you are running AMD64 which is the 64 bit version. Sometimes all your RAM is not seen due to it being allocated for other uses. I have 4 GB and show 3.8 GB. I wouldn't worry about it. Unless you are really doing some intensive stuff a lot of that 4 GB is free which means it is "wasted" RAM.

---


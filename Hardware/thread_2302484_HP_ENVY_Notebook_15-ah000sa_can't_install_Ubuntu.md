---
title: "HP ENVY Notebook 15-ah000sa can't install Ubuntu"
date: 2015-11-10
forum: Hardware
---

### Post by sreeslinux on 2015-11-10
I have the following HP laptop
Product Name
15-ah000sa
Product Number
N0M01EA
Microprocessor
AMD Quad-Core A10-8700P APU with Radeon R6 Graphics (1.8 GHz, 2 MB cache)
Video Graphics
AMD Radeon R6 Graphics
and am having major headaches trying to get Ubuntu (or any distro) to run on it. I have tried every 64 bit version of Ubuntu as far back as 12.04. Install mediums are USBs created by Unetbootin and Ubuntus Startup disk creator.
I have had the most success with 16.04 and adding radeon.runpm=0 during boot. I have even managed to install this version (with Grub working) but am experiencing major instability when trying to use it.  It only boots about 1 in every 20 times.  I've tried the fglrx driver and fglrx-updates driver and still have the same issues.  The rest of the time it freezes at various stages of the boot process.  I have tried noapic and acpi=off to no avail. 
I have searched the internet but have not been able to find any further recommendations.  I am willing to try anything - without Nix I will have to sell the laptop on and get a different one.

---

### Post by bennietriest on 2016-02-12
Same with hp envy ah151sa...
kernel lock

Installed Debian instead ... hopefully resolved soon
will go back to Ubuntu when resolved.

---

### Post by bossbob88 on 2016-04-26
Same problem with HP Pavilion 15 ab100 with amd a10-8700p+R7 m360
I've also tried 14.04 without any success. I could only install 15.10 and 16.04 but both of them have the above described problem. The 16.04 sometimes manage to boot up but after like 5 minutes, the screen just turns off.

---


---
title: "UNR img gives boot error"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by Kinst on 2009-04-25
Here's my process:

[LIST=1]
[*]Format usb to fat32
[*]winMD5sum says the image file is good
[*]Used win32diskimager to write the image file to usb
[*]Safely remove hardware
[*]Turn on my laptop
[*]Boot ERRROR!
[/LIST]

---

### Post by Rotaj on 2009-04-25
Just for the fun of it, reformat the thumb drive and install the ISO using [Unetbootin]("http://unetbootin.sourceforge.net/")

---

### Post by ddrichardson on 2009-04-25
I have a Bytestor USB disk that does the same thing, when I use another drive it works.

---

### Post by stoneguy on 2009-04-26
I had the same problem with a eeePC900 installing UNR's img file to a 16GB SDHC. Tried the win32diskimager, and even the dd method. Nada.

Thought I'd look around the card with parted to figure out what was going on. Turns out whatever the formatting of the card starts out as, it ends up as a loop device with a single FAT32 partition when the transfer completes. Loopdevs don't allow bootflags.

Booting from an Unetbootin'd EasyPeasy1.1 iso, I installed to that card as a single ext2 partition, with the boot loader in its boot sector. Then everything was fine for booting from the resulting card.

If someone manages to get a bootable UNR on a 16GB card, please reveal the method.

---

### Post by Kinst on 2009-05-02
I tried 3 different usb sticks, nothing works. I have a thinkpad x61 tablet :(

---

### Post by ddrichardson on 2009-05-03
What is the *exact* boot error?

---

### Post by Kinst on 2009-05-03
I figured it out! If a thinkpad doesn't boot, change the bios setting from AHCI to Compatibility mode. :P

---

### Post by ddrichardson on 2009-05-03
Bizarre, AHCI has been supported since 2.6.19.

---

### Post by joejgarcia on 2009-06-06
I am having this issue with my IBM r51 laptop.  I don't have a compatibility mode in my bios for my USB ports.  The same usb img works fine on my HP dv6663cl.  Any ideas on how to make this work on the r51?  Is there any way to quickly and easily make the img into an iso?  I am sure I can figure it out, but what a headache the research is going to be.

---

### Post by joejgarcia on 2009-06-06
Ok I figured this out.  Basically follow the instructions for creating a usb boot cd.  On my ibm r51 I also had to make sure the floppy and power management was disabled in the bios as well as adding the noacpi nolacpi noapm to the kernel params passed by grub.  Once it boots into the live usb system, I just clicked Favorites -> Install.  After install, you can go back and turn all the bios stuff you turned off back on.

[https://help.ubuntu.com/community/BootFromUSB#Booting%20the%20kernel%20from%20a%20bootable%20CD]("https://help.ubuntu.com/community/BootFromUSB#Booting%20the%20kernel%20from%20a%20bootable%20CD")

---


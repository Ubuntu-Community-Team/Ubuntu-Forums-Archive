---
title: "Please check my dual-boot setup on two hard drives"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by macleodjd on 2009-01-17
I've used a few versions of Fedora and thought I would give Ubuntu a try. I've tried setting up Ubuntu and Fedora on my present hardware setup and have screwed up WinXP twice in the process. I have a 60 GB IDE drive that I want to install the OSes on (40 Gb Windows, approx 20 Gb Ubuntu), and install the /home mount on my 250 Gb SATA drive. I think my problem is where I'm installing the boot loader.

I have attached five images. Can I get some feedback on my setup. My big question is, in the BootLoaderOptions image, where should I be installing the boot loader? I haven't installed anything a third time, I took the screenshots for feedback hoping I won't screw it up again.

As well, do I have my logical and physical options correct for each of my partitions?

Thanks for the help.

---

### Post by logos34 on 2009-01-17
on the 'Boot Loader' screen, replace (hd0) with **/dev/sdb**.  That will write grub stage1 to the MBR of the IDE disk.  make sure the Bios is set to boot that disk.

good luck

---

### Post by Irony on 2009-01-17
Accept the default of hd0 for installing the bootloader.

This installs grub to the mbr (master boot record) of the first disk (overwriting the windows boot loader). Windows will show up as an option when everything is installed.

---

### Post by logos34 on 2009-01-17
> **Irony said:**
> Accept the default of hd0 for installing the bootloader.


Using the '/dev/sdb' format will assure grub goes on the ide disk--the default (hd0) doesn't always put the bootloader on the desired disk

---

### Post by macleodjd on 2009-01-18
I installed as above using '/dev/sdb' for the bootloader. Ubuntu loads fine. When I first tried to load Windows I received the following message:

Error 13: Invalid or Unsupported Executable Format

I checked menu.lst which was setup as follows:

title Windows XP
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

I checked another forum and changed it to:

title Windows XP
root (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Now when I try to load Windows, it just sits at "Starting..." on a black screen. How do I fix this?

---

### Post by logos34 on 2009-01-18
you only need the map lines if windows is on another disk.

try

> title Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by macleodjd on 2009-01-18
Thanks for all the help. I'm up and running and able to log into both operating systems. If they only made World of Warcraft for Linux.

---

### Post by logos34 on 2009-01-18
> **macleodjd said:**
> If they only made World of Warcraft for Linux.

Some day, maybe.

good luck and enjoy

---


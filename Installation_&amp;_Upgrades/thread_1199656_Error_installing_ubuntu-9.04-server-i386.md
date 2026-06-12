---
title: "Error installing ubuntu-9.04-server-i386"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by plankt on 2009-06-29
Hi.

I'm new to ubuntu and just installed and burned a dvd with the server image
ubuntu-9.04-server-i386

I checked the md5 hash of the iso, it was correct
I checked the dvd and memory in the installer, they both were good

Computer speccs:
Processor: Intel(R) Celeron(R) CPU 430 @ 1.80GHz
RAM: 2048MB
Harddrive: Hitachi 160GB

Installation progress:
For the partition, I chose automatic partition with VPL or what it was called, the middle option.

The installer works untill the step "Choose and install software" where it stops at 85% on file 1 of 140 and gives no specific error messages.
I chose "No automatic updates" and then "LAMP server".
The recent messages from pressing alt+f4:
in-target: E:
in-target: Some archives couldn't be downloaded
in-target: tasksel: aptitude failed (100)
main-menu[803]: WARNING **: Configuring 'pkgsel' failed with error code 1
main-menu[803]: WARNING **: Menu item 'pkgsel' failed.

I then tried to skip to Installing GRUB (not version 2, even tho GRUB 2 didn't work aswell).
It's the same there, it couldn't download the packages from the DVD.

LILO failed aswell.

I could finish the installer w/o installing any bootloader and it gave some info on what to pass instead for the kernel, partition and argument.

I have been using the language Swedish so all translations of the errors might not be 100% word by word.

I would like to know what I could do and would be more then glad to know why aswell so that I can learn.

Thanks in advance, Plankt.

---

### Post by The-Don on 2009-06-29
Alrighty then, I had the same problem - it seems the image I downloaded was borked (regardless of MD5's). I tried from a different source. Plus my CD/DVD was a crappy cheap make so I tried a different one.

If you're new to Ubuntu, then why download the server version? Try out the desktop version first ):P

---

### Post by cariboo on 2009-06-29
Is your network getting setup properly, because if I remember correctly, that is about where it checks the mirrors. The solution I've seen in several posts is to disconnect the network cable, and reinstall

---

### Post by plankt on 2009-06-29
I tried to reinstall without the cable plugged in but still got the same message.
I read some more in the alt+f4 screen and it says a bit up:
"Failed to fetch cdrom:........... Hash Sum mismatch" (The dots replace a long name)

I'll try to redownload the ISO from another source and get back to you.
The mismatch of the hash sum seems to me as an ISO error.

Redownloaded the ISO and burned at the speed x2 on a rewriteable disk. Same error.

The reason I'm going for server is because I'm going to use it as a LAMP server.

Thanks in advance.

---


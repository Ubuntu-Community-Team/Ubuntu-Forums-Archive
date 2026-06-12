---
title: "Problem installing Ubuntu 8.04 alternate"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by AlFrugal on 2009-02-13
I would like to install ubuntu-8.04.2-alternate-i386 on an old PC (Celeron 566 MHz; 192 MB RAM). I used the "Transmission" Bittorrent client running under Fedora 9 to download the ISO. I got the torrent from a reliable site: [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate). I tried to burn the ISO image to CD. With K3b (under Fedora 9) I got the message: "seems not to be a usable image".  With the Nautilus CD burner (under Fedora 9) I got the message "not a valid disc image". With Nero Express (under Windows XP), I burned an image, but it did not boot? I didn't check md5sum or sha1sum. AFAIK, bittorrent does this.

Any ideas whats going wrong?

---

### Post by cariboo on 2009-02-13
It sounds like the torrent didn't finish downloading, start up transmission and let it go for a couple hours.

Jim

---

### Post by AlFrugal on 2009-02-13
Transmission displayed a message that the download had completed. I am letting Transmission continue until I upload 100% of what I had downloaded.However, Transmission status reports only seeds (i.e. it is only uploading) and no peers (no downloading).

---

### Post by avtolle on 2009-02-13
With 192mb RAM, installing the alternate will be problematic, at best; I believe the system requirements for install from the alternate include 256mb RAM minimum.

---

### Post by AlFrugal on 2009-02-13
This is from the "LowMemorySystems" page of Ubuntu Community Documentation:

Memory Requirements
Installing Ubuntu on any system requires at least 32 MB of memory: The text-based installer included with the alternate (install) CDs needs that much space to run reliably. Smaller memory configurations run into problems, and while not impossible, it can be very difficult to complete an installation with less than the minimum RAM requirement. 
Depending on the hardware requirements, you can expect a sparse Ubuntu system to boot to a graphical desktop on anywhere from 19 MB to 54 MB. That requirement will fluctuate with the system demands, and increase while the system is active. Swap space is crucial to low-memory machines, so don't be stingy when setting up your system.

---

### Post by AlFrugal on 2009-02-15
I checked the md5sum of the iso  of Ubuntu 8.04.2-alternate.i386 that I downloaded with bittorrent. It did not match the reference md5sum, so it looks like the bittorrent iso was corrupted. The full 696 MB was downloaded.  I thought bittorrent was supposed to be reliable!

I then downloaded the iso via ftp from a mirror site. This time the md5sum was correct.

When I installed the alternate CD, there was no option to "install command line system". The only install option was "install Ubuntu". This installed a regular version of Ubuntu with X and GNOME. On various web pages and in the community documentation for "low memory systems", the alternate iso is supposed to give an option for a "command line system". Fortunately, this version of Ubuntu seems to run OK on my 192 MB RAM PC.

The documentation says that the iso for the "server version" also installs a command line system, but this shouldn't be used.

The only other option for a "low memory" Ubuntu system that I'm aware of is xubuntu, which uses xfce.

Is there an official document somewhere that would explain when and why the command line system option is no longer available on the alternate CD?

---


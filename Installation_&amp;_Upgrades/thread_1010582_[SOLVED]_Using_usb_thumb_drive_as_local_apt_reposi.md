---
title: "[SOLVED] Using usb thumb drive as local apt repository?"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by thecake on 2008-12-13
I recently installed 8.10 from a flash drive, and would like to use the thumb drive as a repository in a way similar to using a cd with apt-cdrom.  I've looked around and still can't figure it out. :(

---

### Post by cdtech on 2008-12-13
Theres a lot of information about the "Advanced Packaging Tool":
[http://en.wikipedia.org/wiki/Advanced_Packaging_Tool](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)

**UPDATE::.**
I believe you have to use file method within the /etc/apt/sources.list: Deb file:/mnt/usbdevice

---

### Post by thecake on 2008-12-14
Thanks cd tech.  That works fine for the main and restricted packages, however the packages in /pool on the cd/flash drive (mainly backports, which are what I needed :X) aren't in the "standard" repository format (eg dists/intrepid/backports) which seems to confuse file:/ (If anyone knows how to add the /pool format to sources.list I'd love to know).

I found a solution however: pretend to be a cd :P.

1. Unmount whatever is mounted to /cdrom

2. run apt-cdrom.  Wait until it asks for a cd.

3. mount the flash drive to /cdrom.  It should complete successfully

4. apt-get update.

It then successfully recognizes the packages in pool.  Hopefully this will be useful to someone trying the same thing.

---


---
title: "Black screen with artefacts on boot"
date: 2009-06-23
forum: Hardware
---

### Post by mksplg on 2009-06-23
Hi,

a few weeks ago i tried installing Ubuntu 9.04 amd64, but when booting from the CD, after the boot splash screen, I only see a black screen with some artefacts at the top and a garbled mouse pointer (see attached screen photo).

Booting in save graphics mode works so it must be a driver problem. I since installed in save graphics mode but as soon as i delete /etc/X11/xorg.conf the same problem occurs.
Updating via apt-get hasn't fixed the problem so far. The problem also persisted in the current Alpha 1 of Ubuntu 9.10.
<edit>I just tried with Ubuntu 9.10 Alpha 2 with the same problem</edit>

My graphics card is a Sapphire Ati Radeon X1900 GT graphics card.

I have attached my Xorg.log and it says "(EE) open /dev/fb0: No such file or directory" but I couldn't find anything useful for this error message.

Do you have any ideas what I could try?

---


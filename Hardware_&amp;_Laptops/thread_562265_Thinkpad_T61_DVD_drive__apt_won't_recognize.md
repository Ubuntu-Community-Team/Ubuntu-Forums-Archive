---
title: "Thinkpad T61 DVD drive / apt won't recognize"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by infernon on 2007-09-28
I am trying to install the video drivers as I can not get X to load, but my post is about something I'm having a problem with before getting to that point.

When attempting to install the video drivers from nVidia's site, I'm prompted to install the libc headers.  When I run:

sudo apt-get install build-essential

I am prompted for the disc.  Ubuntu doesn't recognize my drive however although I've made the change to Compatibility to AHCI in the BIOS.

Is there a way to either get Ubuntu 7.04 to recognize the drive or install build-essentials without prompting for the disc?

---

### Post by infernon on 2007-09-28
bumpenstein?

---

### Post by infernon on 2007-09-28
OK, I figured this out.

I need to comment out the cdrom line in /etc/apt/sources.list.

Just in case someone else finds themselves in my predicament.

---


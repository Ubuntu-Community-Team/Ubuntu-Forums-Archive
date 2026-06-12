---
title: "manual download of b43 driver for jockey"
date: 2008-07-13
forum: Hardware
---

### Post by PaladinOfKaos on 2008-07-13
I have a friend using an Ubuntu livecd on her Inspiron 1501. Ethernet works great, but WiFi requires the b43 driver. It's a pain in the but for her to get to an ethernet port to install the WiFi every time she reboots, so I figured I'd put the needed b43 files on her USB thumb drive, and write a little script to copy them into the proper locations (/var/cache/apt/archives, /tmp, &c). Then she can just run the restricted drivers manager, and it can install the driver without downloading anything.

I know I'll need to grab the b43-fw-cutter package. Are there any other files that need to downloaded, and where will jockey expect to find them?

---


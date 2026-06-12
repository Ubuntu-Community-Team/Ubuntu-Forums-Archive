---
title: "Rio500?"
date: 2005-09-16
forum: Hardware &amp; Laptops
---

### Post by ry_ry on 2005-09-16
Hi.

I have a Rio500 mp3 player and it still works great and everything. How can I use it in Ubuntu? I've heard about a program called "gnome-rio", does this work and is it in the repositories?

I've also heard about a program called "rioutil" too. Would this work with the Rio500 and is it in the repositories too?

Any help or advice would be great. Thanks. :)

---

### Post by ry_ry on 2005-09-16
So far I've heard that "rioutil" does not support the Rio500. But I did learn about installing the Rio500 tools from the repositories. It's a command line tool that is suppose to let you transfer files to your Rio500 player.

So far, it does not work. the Rio500 player is listed when I issue the "lsusb" command, and I even "modprobe rio500" to make sure that the module was loaded. Ubuntu still can't connect with it. What's wrong? Do I have to compile another kernel just to use my mp3 player?

I would really like to be able to use my Rio500 player in Ubuntu. Is it even possible?

---

### Post by ry_ry on 2005-09-18
Update:

As a follow-up to this post I just wanted to let others know that the Rio500 is NOT compatible with Linux or at least not with Ubuntu 5.04.

I've tried everything I could think of. I tested the following software from the Ubuntu repositories.
1. rio
2. rio500
3. rioutil

All are command-line tools, but none would work with the Rio500 even though 1 and 2 claim to be written for the Rio500. They simply don't work. Dmesg shows that the Rio500 is connected and that the proper Rio500 driver has been installed. "lsusb" shows the Rio500 connected. But all of the utilities cannot connect with the Rio500. Who knows why? I guess the Rio500 is too old and the utilities are too old also, and simply don't work anymore.

Anyway, this is just a FYI in case someone else decides to get a Rio500, I would suggest not to get one.

I'm now in the market for a good flash MP3 player that will auto-mount as a USB mass storage device so I can just drag and drop files with nautilus.

---


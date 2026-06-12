---
title: "What can an external hdd install do?"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by finnj6 on 2009-05-06
Hi

I'm thinking about installing ubuntu to an external 30gb hdd that I have, and I'm wondering if I have to install it using the computer that I'm planning on using it on or will it work on any computer.

Basicaly this is coming from that I'm going travelling for the summer and I like the idea of having what is basicaly my own computer in my pocket. I would like to have an install that I can boot into from any computer without having to worry about set up and driver etc.

Is this possible?

ps I'm a noob to the linux world

Jeff

---

### Post by cariboo on 2009-05-06
> I'm thinking about installing ubuntu to an external 30gb hdd that I have, and I'm wondering if I have to install it using the computer that I'm planning on using it on or will it work on any computer.

Your setup will work on any computer, the only thing you may have problems with is graphics drivers, which you can install on an as needed basis. Most of the drivers needed are included with the kernel, and are loaded as needed, so it doesn't matter which computer you do the install from.

When installing on an external drive that will be moved from computer to computer, make sure you install grub on the external, and set the BIOS to boot from a USB drive. That way you won't have to make any changes to the computer you are using.

---


---
title: "Intel Wireless Issues Getting Out of Control!!!"
date: 2019-04-13
forum: Hardware
---

### Post by andrewfer000 on 2019-04-13
Okay Ubuntu and Linux kernel maintainers, Intel Laptop WiFi modules like the 7265 (the one I have) are extremely dumb. They seem to be supported well but after Ubuntu 18.04 they stopped working properly! I tried everything but whenever I put my laptop to sleep or try to use a faster 5Ghz network it just stops working!  If I change networks at all then all hell breaks loose. It works fine when I boot and i'm on a 2.4Ghz network but unfortunately my office doesn't support it which is very bad. I'm very sad because if a solution doesn't exist (external cards are not an option) I will be forced to use Microsoft Windows again :( Downloading Intel's official driver didn't do anything either! WiFi is one of the biggest mainstream hardware issues in the GNU/Linux world and we need to do something about it. I know there MUST be a solution for this and if someone can give me a guide or a tutorial that will be good. I have the drivers in the firmware folder and I just don't know how to activate them myself.

Yes, I'm running 19.04 With Kernel 5.0 in hopes this would of been fixed, sadly, its just worse!    

This is also my first post in a few years so please don't be mad if i messed up!

---

### Post by andrewfer000 on 2019-04-13
SO here was the issue. It was not the driver, or Ubuntu (kind of) It was a setting in Gnome that basically let my non-existent (anymore) power manager control my network adapter. The fix was to go into Ubuntu Gnome and use the Gnome Settings program to disable power management for wifi! The issue was that on first boot it works fine, If I disconnect and reconnect there would be error, if I suspend or hibernate It wont work or if I logged in and out it will fail. (When it fails I can access LAN fine but no WAN) But now everything works better than ever. So if you get the same issue just be sure to disable power management for your WiFI card.

---


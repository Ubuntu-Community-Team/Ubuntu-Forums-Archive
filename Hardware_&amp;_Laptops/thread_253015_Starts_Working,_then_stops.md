---
title: "Starts Working, then stops"
date: 2006-09-07
forum: Hardware &amp; Laptops
---

### Post by AlReece45 on 2006-09-07
I have recently bought a Compaq Presario v6030 laptop. It comes with a AMD Turion(TM) 64 X2 Mobile TL-50 (1.60GHz/256KB), 1GB DDR2,  and 80 GB 5400 RPM Hard Drive. I also have a Microsoft Wireless Notebook Optical Mouse 4000. All of the following are working well under Windows.

I have installed the AMD64 Ubuntu from DVD media successfully by using "acpi=off" as not using it prevents proper startup. So here's the situation (problem):

I start up the computer, and as expected it boots up into Ubuntu asking for login. I can login, and everything that I expect to work (I don't expect wireless/sound to work) works for a little while.

Then randomly, devices stop working. As I havn't experimented with every piece of my hardware, the problem was most apparent when trying to update Ubuntu; my network connection and wireless mouse failed at precisely the same time.

I have already updated ubuntu (after about 6 restarts) and the updates do not appear to fix the problem. I am really looking forward to using Ubuntu over Windows XP, but when the internet and wireless mouse fail to work correctly for more than a few minutes I can't do this. Any help would be appreciated.

---

### Post by AlReece45 on 2006-09-10
Some update, even though there are only 20 views:

Network Card works fine when no USB mouse is plugged in at startup, that is until I try plugging one in, then it stops working, and the mouse still doesn't work.

I have now tested this with my old (at least 1 year) Targus Wireless Mouse and my new Microsft Wireless Mouse.

If either mouse is plugged in during startup, the mouse and NIC both work for a short time and then stop at the same moment.

After the NIC stops working, a restart is required to get it working again.

Again, any help would be appreciated.

Edit:

Also, the mouse still appears when for the utility "lsusb" when it stops working. "dmesg" doesn't have anything odd or resembling any errors, even though It somehow detects when I remove the mouse from the port.

There are no BIOS settings for resources in the laptop bios.

Come on Ubuntu Community, I have friends arguing over your community support, I would like to be on the side that says they're very helpful.

---

### Post by Vlad Janicek on 2006-09-10
I have the same laptop --great machine by the way-- and I'm in the same point as you are... it seems that there's some bug in the chipset kernel driver that locks the machine. I'll keep you informed. 

The same error happens with ubuntu dev and all the linux distros I have tried](*,)

---

### Post by AlReece45 on 2006-09-12
Thanks for the info, I guess I'm stuck with Windows for now then. I would use Ubuntu with the touchpad, but I can't seem to move the mouse around without it trying to drag and drop things (I have already set the sensitivity to the lowest).

---


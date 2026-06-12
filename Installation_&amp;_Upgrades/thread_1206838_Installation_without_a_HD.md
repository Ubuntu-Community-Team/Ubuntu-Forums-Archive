---
title: "Installation without a HD"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by Milneuve on 2009-07-07
Hi, I have an old PC that I use as a Linux Firewall. I would like to install Ubuntu on this PC but without the Hard Disk.
Is is possible to boot from the floppy and use a USB stick instead of the HD? My PC cannot boot from a USB device. 
How would I do that?
Thanks.

---

### Post by dandnsmith on 2009-07-07
An interesting project,
but I'm not sure i understand all the parameters:

1. don't touch the HDD content (so firewall usage can still be employed)
2. install ubuntu to a usb device
3. boot, using the FDD

Is there no mention of CD/DVD because you have no such device?
How long would you expect the ubuntu system to remain viable - usb sticks will fail after a while, because of the number of writes.

It would be very much easier if you allowed modifying the boot process for the firewall installation to include the provision for booting the usb stuff.

Have you checked to see if ubuntu will run on that hardware, especially in regard to the amount of RAM?

---

### Post by Milneuve on 2009-07-07
Hi,
 
1) My plan was to remove the HD from equation and do a fresh install. I was looking for a less energy hungry solution since the PC is up and running 24/7 all year long.
2) The machine has a CD ROM which could be used.
3) But the **most important point** is : <<usb sticks will fail after a while, because of the number of writes>>. I never thought about that. That is probably why my research never went very far. You just answered my question. 
 
I will keep my current setup ( Debian 4), which is reliable and stable, until the HD die of old age.
 
Thanks again for taking the time to respond.

---

### Post by dandnsmith on 2009-07-08
> **Milneuve said:**
> 
1) My plan was to remove the HD from equation and do a fresh install. I was looking for a less energy hungry solution since the PC is up and running 24/7 all year long.
I'm not sure that you'd save very much by taking out the HDD.
You could consider using an SDD device, which is like an SD card, but manages its writes on a positionally varying basis to make the lifetime longer (look at Asus and other netbook technology.

> 2) The machine has a CD ROM which could be used.
That would give you a way of booting other devices, such as USB stick, USB HDD, SDD, employing a specially configured CD. Then you could remove the existing HDD (just remove the power and data cables).

---

### Post by Mighty_Joe on 2009-07-08
> **dandnsmith said:**
> You could consider using an SDD device, which is like an SD card, but manages its writes on a positionally varying basis to make the lifetime longer


I'm pretty sure most flash devices implement some form of wear leveling.  [This guy]("http://www.bress.net/blog/archives/114-How-Long-Does-a-Flash-Drive-Last.html") was able to get 90,593,104 writes out of a flash drive.
There's a lot of things one can tweak to prolong drive life when running from flash, for example, moving logging and caching to tmpfs and not using a swap partition (assuming, of course, that you have enough RAM to handle your applications.

---

### Post by Milneuve on 2009-07-08
These are good ideas, but for the moment I will keep my current installation. The machine has been running for a couple of years on a UPS with very few shut downs. With a little chance, it could go on for another couple of years. By that time, technology will have changed.  
 
Thanks again.

---


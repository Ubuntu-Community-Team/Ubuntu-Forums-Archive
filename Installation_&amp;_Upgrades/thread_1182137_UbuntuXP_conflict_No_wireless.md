---
title: "Ubuntu/XP conflict: No wireless"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by larrybaden on 2009-06-08
I installed 9.04 on a Dell Inspiron 1520, dual-booting with XP Pro SP3. Eventually, U saw my wireless network, but wouldn't connect. New drivers, updates, all that, still no connect.

Now, however, XP will no longer connect, either. Both see the network, neither will connect.

Also, since installing U, my XP boot process is somewhat squirrelly, requiring a couple tries to get a good boot.

I'm wondering what options there are, besided wiping the disk clean and starting over, which I don't want to do.

---

### Post by dstew on 2009-06-09
How did you install Ubuntu? Did you create new disk partitions, and install that way, or install within Windows using Wubi?

Possibly Ubuntu re-configured your wireless card, possibly even installed new firmware in it, depending on what you tried to get it going. If so, you will need to re-install the card in Windows in order for it to work. In Windows XP, I think you can "remove" the wireless card using the device manager, then try to re-install it. If the firmware has been changed, maybe Windows will recognize this and try to update the driver to work with the new firmware. Maybe you can visit the manufacturer's site and get the latest firmware.

---

### Post by larrybaden on 2009-06-10
Well, I got it to see the network and log in in XP. However, it sees the network but won't log in in Ubuntu. I'm thinking that since it sees the network, the card is working. So I'll keep experimenting and hoping I find a solution before I go get a hammer. :)

Incidentally, the installation was form an ISO file on a CD.

---


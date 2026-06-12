---
title: "PCMCI Devices not getting activated in Ubuntu 7.04 Feisty"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by eabhi on 2007-05-21
Hi

I have a Compaq Presario 900 Series Laptop. (Mobile AMD Athlon XP 1500, 512 MB RAM, 60 GB HDD) I had Windows XP and Ubuntu 6.06 Installed. I have 2 PCMCI Devices which both were fine with this configuration
1. Netgrear 802.11b/g Wireless LAN Card
2. VIA USB 2.0 Card

I have just upgraded from 6.0 to 6.10 to 7.04 via CDUpgrade. Both the above cards were working fine with 6.06 and even on 6.10 after upgrading, they were working fine. But since I have upgraded to 7.04, both of them have stopped working.:(

When I checked in the Hardware Manager, they get detected properly as 802.11b/g Wireless Card and USB 2.0 Card, but don't work. In the Network Connection, there is no Wireless Connection available :( and any USB Mass storage device connected on to the USB 2.0 card doesn't get mounted :-(

This was the same case with the 7.04 Live DVD, but I thought it will work once I install it on HDD as it was working in 6.06 and 6.10. But sadly no wireless connection now.

I think this is the problem with the PCMCI Slot driver and not the Wireless Connection. Anybody else facing the same problem???

Thanks in Advance for any solutions :)

---

### Post by Arubafjc on 2007-05-21
I had the same problem and when I looked around I noticed alot of other people are having that same problem.. so far the only thing thats worked for me is to just reinstall 6.10..

---

### Post by eabhi on 2007-05-22
> **Arubafjc said:**
> I had the same problem and when I looked around I noticed alot of other people are having that same problem.. so far the only thing thats worked for me is to just reinstall 6.10..

I don't wanted to do a clean install, I have other applications installed and have lot of setting in my current installation. I have to check that if I have some place to do a separate installation.

Meanwhile I have a USB 802.11g adapter which is working in Ubuntu 7.04, so I am using that. It would be great if there is someway of fixing the PCMCI Problem in my current installation. I still don't have a way to get the USB 2.0 card working :(

---

### Post by vampyrebytes on 2007-05-22
I am also in this boat, but I do not have an alternate wireless connection and no available wired connection.

7.04 has forced me back to Windows until this problem is resolved.

((I could clean install 6.10, but I really don't want to lose all my settings and everything else I've tweaked.))

---


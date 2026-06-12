---
title: "IBM/Lenovo IdeaPad Z575 - General Info?"
date: 2012-03-12
forum: Hardware
---

### Post by gdea73 on 2012-03-12
Today I bought the IdeaPad Z575 from Newegg. I'll be getting it in the mail soon. I'm going to run Ubuntu 10.10 (x86_64) on it, and may experiment a bit with Arch in the future, but surely Linux will be my sole OS.

I've already decided on buying it, so I hope it's not terrible with Linux, but I was looking for some opinions or experience regarding this shiny laptop and how well it works on Ubuntu. For example, my desktop built around the Gigabyte GA-880GA-UD3H motherboard will never suspend more than once before a reboot, due to the SATA chip, which is a problem that I had no idea about until I bought it (and I still don't think many other people have complained, at least with the same board).

The specs of the laptop are as follows:
- AMD A-Series (A6-3420M) (1.5/2.4GHz Quad Core)
- 6GB DDR3 1333 RAM
- 500GB, 5400RPM SATA HD
- AMD Radeon HD 6650M (1GB/GDDR5?)

I think the way the graphics work is that the APU's integrated chip works as a hybrid along with the discrete card. I'm hoping that will work alright in Catalyst on 10.10, as the CPU isn't very powerful on its own and I'd like to be able to utilize its GPU capabilities.

(side note: Will this run Minecraft at playable speeds? I was hoping it might... :D)

Update: Well I finally got all the stuff working. If you get this laptop, for the graphics, check my thread on hybrid / switchable graphics in this section to get them configured right.

And using the APU's graphics *alone*, Minecraft ran at 30+ FPS on the highest settings :D

---

### Post by gdea73 on 2012-03-13
So I see no one has any suggestions / ideas so far.

I greatly prefer 10.10 to 11.04 or 11.10 so I am going to use that if at all possible. Now I know this laptop was released somewhat recently, as was the APU/hybrid graphics chipset in use, so I'm *hoping* it will work alright with the 10.10 kernel.

In case it would work better with a newer kernel, are those still provided for 10.10 (the 11.10 kernel?), or would I manually have to use a backport for Maverick?

---

### Post by lsutiger on 2012-03-13
I just received my Acer 5560-7402. It has the AMD A6-3420M APU. What I had before was a Dell Inspiron 1501. All I did was pull the drive from the old Dell and put it into the Acer (the drive was the same size - 500GB - but the drive in the Dell is faster :) ). I then downloaded the ATI driver from ATI. Everything works except the microphone, which I will try to fix later.
Also, I am running 10.4, due to the LTS. I also dislike the 11.XX version of Ubuntu.
Wish you luck on your new acquisition and have fun!
[Link for driver]("http://www2.ati.com/drivers/linux/amd-driver-installer-12-2-x86.x86_64.run")

---

### Post by gdea73 on 2012-03-14
Cool, I'm in the process of installing Ubuntu now. I originally (accidentally) used disk encryption, but then I reformatted because turning it off by a specific method caused errors. I've also downloaded Ralink's RT3090 PCIe WLAN chipset drivers for Linux, which I will somehow or other figure out how to install. I think I can handle the Catalyst installation using wiki.cchtml.com. Thanks for the driver link, BTW.

Let me know how it goes trying to get the mic to work, that would be nice to be able to figure out. I know we have different models but in the event that mine doesn't work either, I'd like to know the troubleshooting procedure if you find a solution. Thanks! :)

---


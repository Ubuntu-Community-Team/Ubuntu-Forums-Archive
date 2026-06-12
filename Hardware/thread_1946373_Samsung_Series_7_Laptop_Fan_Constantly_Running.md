---
title: "Samsung Series 7 Laptop Fan Constantly Running"
date: 2012-03-24
forum: Hardware
---

### Post by Abundnce10 on 2012-03-24
I recently purchased a Samsung Series 7 Chronos laptop from Bestbuy [http://www.bestbuy.com/site/Samsung+-+15.6%22+Series+7+Laptop+-+8GB+Memory+-+1TB+Hard+Drive+-+Silver/4708803.p?id=1218512740623&skuId=4708803&st=samsung%20laptop&cp=1&lp=5](http://www.bestbuy.com/site/Samsung+-+15.6%22+Series+7+Laptop+-+8GB+Memory+-+1TB+Hard+Drive+-+Silver/4708803.p?id=1218512740623&skuId=4708803&st=samsung%20laptop&cp=1&lp=5)

It's a great piece of machinery, however, the fan constantly runs when I boot into Ubuntu.  On Windows there's a function, "fn + F11", that turns 'Silent Mode' on and off.  It doesn't work on Ubuntu, and so the fan runs constantly which is a little unpleasant.  

Is there any way to address this issue?  I bought this laptop with the intention of running Linux the majority of the time but it's a little uncomfortable to have the fan running constantly.

I hope I can solve this issue because I really want to keep this machine.  Thanks..

---

### Post by Mark Phelps on 2012-03-24
Understand the fan noise can be irritating, but that is not the REAL problem; instead, the problem is that bugs in recent Linux kernels used in Ubuntu prevent the CPU from scaling down automatically (which it CAN do in Win7).

This keeps the CPU running fast, which keeps the fan running fast -- to cool down the CPU.

The real solution is to slow down the CPU, which will cool it down, and also slow down the fan.

Google on jupiter -- if you can install that, you may be able to throttle the CPU back.

---

### Post by Abundnce10 on 2012-03-26
Do you think either of these two resources would help me solve my problem?

[https://bugs.launchpad.net/samsung-tools/+bug/884686](https://bugs.launchpad.net/samsung-tools/+bug/884686)

[http://linuxtweaking.blogspot.com/2011/02/linux-kernel-will-soon-provide-better.html](http://linuxtweaking.blogspot.com/2011/02/linux-kernel-will-soon-provide-better.html)

---

### Post by Abundnce10 on 2012-03-26
I tried this solution but to no avail..

[http://ubuntuforums.org/showpost.php?p=9197545&postcount=24](http://ubuntuforums.org/showpost.php?p=9197545&postcount=24)

---

### Post by Mark Phelps on 2012-03-26
My suggestion was to look around for Jupiter ...

See the link below:

[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html]("http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html")

---

### Post by Abundnce10 on 2012-03-27
I successfully installed Jupiter, however, the power-level settings had no affect on my fan (verified by checking the estimated battery length when varying the level).  Note, it was able to successfully disable my wifi but not my touchpad.

If you have any other ideas send 'em my way.  I'm looking for any solution so I don't have to take this guy back to Best buy.

Thanks!

---

### Post by Mark Phelps on 2012-03-29
I'm guessing that the "Silent Mode" Windows feature simply downscales the processor -- which will make it run cooler, which will have the effect of the fan running slower (and quieter) as well.

Since Jupiter doesn't do it for you, you have little choice but to return it.

And GOOD LUCK with getting a refund from Best Buy. Not saying you won't get it, but telling them the laptop won't do what it was not designed to do (i.e., run quietly in Linux) may not be sufficient for them to refund your money.

---

### Post by n8fr8 on 2012-04-15
I have had some success with Ubuntu 12 on mine, and blogged about it here: [http://openideals.org/2012/04/15/tuning-ubuntu-on-samsung-series-7-laptop/](http://openideals.org/2012/04/15/tuning-ubuntu-on-samsung-series-7-laptop/)

important excerpt below:
:guitar:
The big two breakthroughs to really making this hardware hum were though were finding a way to enable the custom Samsung function keys and to stop the endless fan noise from whining away. The fan noise was an indicator the processor was too hot, which also meant the battery life was not going to be so great. The estimate was only two hours, which was not good enough for my needs.

What I had to do was install the proprietary ATI/AMD graphics driver, instead of using the open-source video driver that is default in Ubuntu now. While I am used to this with MBP’s and the NVidia driver, and I had hoped not to have to use the proprietary driver with my new laptop. However, once I realized that by using the proprietary driver that the fan noise would stop, and my battery life would double, it was an easy choice to make. This driver can be easily installed through the System Settings -> Additional Drivers menu.

The second breakthrough was finding the Linux on my Samsung project, aka Voria. By installing the tools offered in this repo, all the various function keys necessary for brightness, volume and other options control mostly seem to work. I think there is also some other under the hood improvements, as well, but I haven’t fully parsed that. To install the tools, just follow the installation info from the link above, which basically involes Aptitude or ‘apt-get’.

I can happily say that I used my new laptop all weekend for an epic, intensive open-source hackfest, and it performed like a champ, had fantastic battery life, and generally impressed everyone who saw it. In a sea of Macbooks and Thinkpads, it definitely stands out, and at the current price, can’t really be beat.

From here, I am going to look into better utilizing the 8GB SSD cache as a swap or perhaps installing the core OS directly onto that. I don’t have much time these days to tinker in that way, but I would love to be able to get Ubuntu back up to a 7 to 8 hour battery life, especially with the travel I do. Otherwise, I will be experimenting with the HDMI video out, the Wifi Direct support and more in the coming days, as well as keeping up to date with the final Ubuntu 12 releases.

---

### Post by probin51 on 2012-04-17
> **n8fr8 said:**
> I have had some success with Ubuntu 12 on mine, and blogged about it here: [url]http://openideals.org/2012/04/15/tuning-ubuntu-
on-samsung-series-7-laptop/[/url]

Thanks for the info. After debating a lot, I bought the Chronos 7 15"6 because I wanted the extra GUI space to develop on. 

I immediately removed the 1TB HHD and replaced with a Samsung 256GB SSDD. My installation of Ubuntu 11.10 from scratch went very well indeed. Even Bluetooth and HDMI worked. I Can transfer between my Samsung Galxy S2 and the laptop and watch it on my 46" TV. :D

If I can get the temperature down, the battery life up. I'll give this machine 5 stars under Ubuntu. There are a few problems, detailed below, but they don't bother me personally.


Problems I "suffered" out of the box:

1. Trackpad works as a normal mouse, no special multi-touch featurs. I'm a bit old fashioned and hate trackpads anyway and disabled it in the BIOS.

2. Realtek R8169/R8111B. Wi-Fi worked great. But LAN had problems , kept dropping the connection. Resolved in minutes by installing the R8168 driver ([http://murzal-arsya.blogspot.com/2012/01/ubuntu-1110-and-realtek-rtl8111rtl8168.html](http://murzal-arsya.blogspot.com/2012/01/ubuntu-1110-and-realtek-rtl8111rtl8168.html)). 

3. A further problem (tricky to diagnose) was even the R8168 had problems on the RJ45-Connection (not Wi Fi) which I discovered (trial and error searching the log files) was when it was receiving IPV6 packets. Quickly disable it in Network Connections applet (select "Ignorw" on the last tab "ipv6 settings)). No more problems. Haven't checked throughput though.

4. HDMI output . No sound. haven't really looked at this (not bothered). But HDMI 1080p works straight out of the box 1920x1080. Just remember to ttach the cable AFTER booting.

5. The CPU is running at 60°C-65°C, fan on and off a bit. 

I'll adopt the 12.04 release early and the ATI drivers as you suggest and hope that will solve this remaining problem. I've heared the kernel update has brought wonders.

Thanks again for your post and your tips.

---

### Post by probin51 on 2012-04-18
> **n8fr8 said:**
> The fan noise was an indicator the processor was too hot, which also meant the battery life was not going to be so great. The estimate was only two hours, which was not good enough for my needs.

What I had to do was install the proprietary ATI/AMD graphics driver, instead of using the open-source video driver that is default in Ubuntu now.

I replaced the ATI driver as you indicated and the machine is idling at around 18W - 21W, temperature between 52°C (126°F)and 56°C (133°F), down around 10°C (50°F) from around 63°C (145°F) with >5 hours battery life, up from 2.5.

But Compiz kinda stopped working. :confused: 

Jeez, down you just love linux. Figure that one out tomorrow.:lolflag:

Once Again Thank You Very Much.

---

### Post by caliber556 on 2012-12-01
Struggling with t myself. Samsung Series 7 17" (NP700Z7C) though the ACPI/kworker kernel bug affects many other newer notebooks. No fixes mentioned in the bug thread work (pci= noacpi, etc.). After several clean installs I can confirm it is NOT a dual graphics or Bumblebee issue. It does not happen booting from Live CD. And though intermittent, it is very annoying. You have to wonder "Do I need to fight the kworker this time?" upon every reboot. Do not Suspend - kworker goes nuts upon resume and it is hard to calm it down with reboots. 

Unfortunately the bug was classified as an XFS (filesystem) issue by the Linux kernel team, and that is probably preventing it from being fixed over several months now. I posted my findings here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/887793](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/887793)

---


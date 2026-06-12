---
title: "Slow and unreliable network performance on Acer aspire 5050"
date: 2011-05-01
forum: Hardware
---

### Post by Tom743 on 2011-05-01
After installing Ubuntu using the internet is extremely slow. A test at Speedtest.net is averaging at 15kb/s (on windows it used to be around 450kb/s). I'm using Ubuntu 11.04 and connected to the Internet via wireless. Ping times to local IP's vary between 17ms and 3000ms.

The laptop parts are:

   * Processor:   AMD Turion(tm) 64 X2 Mobile Technology TL-50
   * RAM: 1 Gbyte
   * Video: ATI Radeon Xpress 200M
   * HDD:  WDC WD1200UE-22K  120Gb
   * Network1: Realtek 8139 Ethernet
   * Network2: Atheros AR2414 802.11a/b/g

Is there a way to speed it up?

---

### Post by roberto.ur on 2011-05-03
Similar problem here.

Acer Aspire 5050. It has a headache dealing with wifi in this laptop since I use Ubuntu.

It seems everything is ok at the beggining but then it just do not detect the networks. However, sometimes, after a while, it does...

Any ideas?

---

### Post by Scott Deagan on 2011-05-09
I have the same problem. I have a Sony Vaio VPCF11S1/E. I'm not 100% certain what the wireless hardware is, but running "lspci | grep -i network" shows:

02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)

The symptoms: network throughput (consistently) 33% slower than throughput in Windows 7 running on same machine or Ubuntu 10.10 running on different laptop, throughput eventually degrades and eventually grinds to a halt.

It's impossible to watch a 10 minutes YouTube video without the video freezing about 2 minutes (or so) in. Downloading large (500MB) files is "touch-and-go", as in most of the time the download will simply freeze anywhere between 80MB and 200MB.

---

### Post by Gr!MM^ on 2011-05-14
Hello there gentlemen.

I've had many versions of Ubuntu installed in my own Aspire 5050.

Since Ubuntu 9.04 or so, I started having problems, the wireless connection was just awful, but soon I found out a solution that worked out great for me, replacing the ath5k module with the ath_pci (madwifi) one.

[http://ubuntuforums.org/showthread.php?t=1163380](http://ubuntuforums.org/showthread.php?t=1163380)

Also, yesterday I installed 11.04 and had some trouble compiling the source code for the ath_pci. Since I'm too lazy, I just shoved an old kernel (2.6.35, the one I was using in 10.10) into it, compiled and installed the driver and now everything is working just fine :D

Hope this helps!

---


---
title: "BCM4312 not working in ubuntu 8.10 intrepid ibex"
date: 2008-11-03
forum: Hardware
---

### Post by vance morris on 2008-11-03
This is a Dell Latitude 910 (Mini 9)
release : Ubuntu 8.10 Intrepid Ibex
uname -r : 2.6.27-7-generic
relevant lspci output :
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
 Subsystem: Broadcom Corporation Device [14e4:04b5]
 Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
 Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
 Latency: 0, Cache Line Size: 64 bytes
 Interrupt: pin A routed to IRQ 17
 Region 0: Memory at f0200000 (64-bit, non-prefetchable) [size=16K]
 Capabilities: <access denied>
 Kernel driver in use: wl
 Kernel modules: wl

I have installed the b43-fwcutter package and extracted the firmware for this BCM4312 wifi adapter but when I load up jockey there is only the proprietary broadcom STA driver showing as an option. According to linuxwireless.org, this card is supported by the b43 drivers.

I have manually removed the wl module and installed the b43 module, but this doesn't result in any functional interfaces appearing under ifconfig or under the NetworkManager applet.

Thanks in advance for any help.

---

### Post by der_vegi on 2008-11-03
I have almost the same card (BCM4312 802.11a/b/g [14e4:4312] (rev 01)) and it works fine with 8.10.

Could you please post the output of 'dmesg'? There one can usually see, if the firmware is properly loaded or not... My card works with firmware version 410.2160.

---

### Post by whichpaul on 2008-11-05
It seems I have a very similar problem. I have a BCM4312 in my recently purchased HP Pavilion dv5. I installed a fresh copy of Ubuntu 8.10 (Intrepid Ibex) and it all seems to work but yet doesn't. Allow me to explain.

I installed Ubuntu 8.10 and once signed-in the Restricted Hardware Driver program immediately recognised my wireless card and allowed me to activate the "Broadcom STA" wireless driver. Under the hood I noticed that the "wl" kernel module was loaded and an "eth1" network device was successfully created BUT no wireless networks are detected in the Network Manager applet and all my attempts to manually connect to an existing wireless lan are just plain unsuccessful. So, it seems that Ubuntu is quite happy with the wireless card yet it is not actually doing anything useful at all.

I too have a "revision 01" card but there is no firmware version advertised in either dmesg, lspci and so on. I don't know if this is a problem. Additionally, I noticed that in dmesg the card is recognised as a 4315, but in all other outputs it's referred to as a 4312 (seems odd to me).

Rant: I foolishly thought that if there was a driver for my specific card (especially from the manufacturer) and if the distribution was even able to detect in install it for me that there should be no reason for it not to work. I'm now thoroughly confused and moderately disheartened! Grrrr....

Any help or suggestion would be appreciated!

---

### Post by ravl on 2008-11-05
I recently installed Intrepid on a friend's Acer laptop with a Broadcom 4318. I didn't install or replaced any modules, just the stock b43 module.

At first, I had an interface, but couldn't scan or connect. After thinking about it for some minutes, I pressed the wifi button on the laptop and checked dmesg. It turns out that the card was off, but the light was on.
Once turned on, NetworkManager could scan and connect without problems.

Hope this helps.

---

### Post by whichpaul on 2008-11-05
You know it seems my problem may have been a little mundane for me. I decided to try another wireless router and, wouldn't you know it, it's now working. I'm not sure what the problem was yet, but I'm currently writing this on my laptop via wireless. Looks like the nasty old D-Link was in someway to blame, and my nasty old Netgear has saved the day.

So for the moment I withdraw my protest and would like to thank ravl for the response! No doubt I'll be back on the forums soon with a suspend / hibernate problem or some non-responsive hotkeys!

Good luck vance, try starting from a clean distro install and give your wireless router a good reset!

Ubuntu 8.10 (Intrepid Ibex)
HP Pavilion dv5: Intel Core 2 Duo 2.4Ghz / Broadcom 4312 WiFi / nVidia GeForce 9600M GT 512MB / 3GB RAM / 320GB HDD / and a whole lot of other stuff... including a Russian keyboard!

---

### Post by vance morris on 2008-11-06
I posted my fix in a similar thread I had running here.
Check it out if you so please:
[http://ubuntuforums.org/showthread.php?p=6119250#post6119250]("http://ubuntuforums.org/showthread.php?p=6119250#post6119250")

---


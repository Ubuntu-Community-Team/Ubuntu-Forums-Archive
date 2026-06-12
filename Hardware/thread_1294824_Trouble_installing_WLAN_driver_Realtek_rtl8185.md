---
title: "Trouble installing WLAN driver Realtek rtl8185"
date: 2009-10-18
forum: Hardware
---

### Post by ladaghini on 2009-10-18
Hi.  I'm new to Linux and installed it on my laptop.  The laptop has a Realtek RTL8185 chipset, and Realtek updated the linux driver for the WLAN card recently.  I downloaded it from here: [http://www.realtek.com.tw/downloads/ExpressFTPSite.aspx?DownTypeID=3&DownID=435&PFid=1&Conn=5](http://www.realtek.com.tw/downloads/ExpressFTPSite.aspx?DownTypeID=3&DownID=435&PFid=1&Conn=5)

First of all, in which folder do I unzip the download to? 

The first step to install is 'make', but I get this output:

[email]ubuntu@ubuntu:~/Desktop/rtl8185_linux_26.1030.0625.2009.releas[/email]e$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_softmac.o
  CC [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_rx.o
  CC [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_tx.o
  CC [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_wx.o
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_wx.c: In function ‘ieee80211_wx_set_encode_ext’:
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_wx.c:702: warning: format not a string literal and no format arguments
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_wx.c: In function ‘ieee80211_wx_set_gen_ie’:
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_wx.c:890: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘size_t’
  CC [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_module.o
  CC [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt.o
  CC [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt_ccmp.o
  CC [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211-rtl.o
  LD [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211-rtl.ko
  CC      /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.o
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c: In function ‘proc_get_stats_hw’:
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:350: warning: cast from pointer to integer of different size
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:351: warning: cast from pointer to integer of different size
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:354: warning: cast from pointer to integer of different size
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:355: warning: cast from pointer to integer of different size
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:358: warning: cast from pointer to integer of different size
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:359: warning: cast from pointer to integer of different size
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c: In function ‘check_tx_ring’:
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:826: warning: cast from pointer to integer of different size
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:826: warning: cast from pointer to integer of different size
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:827: warning: cast from pointer to integer of different size
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:827: warning: cast from pointer to integer of different size
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c: In function ‘alloc_tx_desc_ring’:
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:1447: warning: cast from pointer to integer of different size
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:1447: warning: cast to pointer from integer of different size
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c: In function ‘alloc_rx_desc_ring’:
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:1621: warning: cast from pointer to integer of different size
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:1621: warning: cast to pointer from integer of different size
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c: In function ‘rtl8180_rx’:
/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.c:2065: error: implicit declaration of function ‘rdtsc_rtl’
make[2]: *** [/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185/r8180_core.o] Error 1
make[1]: *** [_module_/home/ubuntu/Desktop/rtl8185_linux_26.1030.0625.2009.release/rtl8185] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2

If anyone can provide a step by step solution 'for dummies', I would really appreciate it.

Thanks.

---

### Post by TheGeebs on 2009-11-08
You should search the forums before you post a question. Thats where I found my answers.  You need to use ```
sudo #before a command to run it as root
```

I've installed the realtek drivers from their website but I had to run ```
wlan0up
``` every time I turned on the computer.  I found a better solution which works well here:
[http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)

---

### Post by S1lverado on 2009-11-22
You need to search the site before making a post:lolflag:

---

### Post by davidfdr on 2010-01-27
Hello guys. I had the same problem and i'm running those commands AS ROOT!

My system is:
uname -a:
```

Linux mynx 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

```
lspci
```

00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

```
Linux Distribution: Ubuntu 9.10 64bit.


sudo -s, sudo... All did the same error:

/home/david/Downloads/rtl8185_linux_26.1031.1207.2009.release/rtl8185/r8180_core.c:2065: error: implicit declaration of function &#8216;rdtsc_rtl

So I did these steps:
1  - Downloaded driver from Realtek .
2  - Unziped the file .
3:

..

So i opened the file r8180_core.c and went to line 2065 and commented the line (just by putting a "//" before it):
...
```

prism_hdr[2]=htonl(stats.mac_time[1]);
prism_hdr[3]=htonl(stats.mac_time[0]);
//rdtsc_rtl(prism_hdr[5], prism_hdr[4]);
prism_hdr[4]=htonl(prism_hdr[4]);
prism_hdr[5]=htonl(prism_hdr[5]);

```
...
4 - make and make install;
5 - sudo apt-get install libssl-dev ;
6 - unziped wpa_supplicant-0.5.5.zip;
7 - cp defconfig .config inside realtek drivers wpa_supplicant directory;
8 - make and cp wpa_cli wpa_supplicant /usr/local/bin
9 - reboot and let the job for the networkmanager
---

Special thanks to blog do calouro: URL:
[http://blogdocalouro.blogspot.com/2009/08/pci-wireless-card-realtek-8185-weak.html]("http://blogdocalouro.blogspot.com/2009/08/pci-wireless-card-realtek-8185-weak.html")








...

---

### Post by Pithikos on 2010-06-29
Hi! I tryied all that. I first blacklisted *ndiswrapper* and *rtl8180* to make sure they don't interfere. Then I made sure nothing of them is running and followed your guide point by point. Everything seemed to install correctly(at least I didn't get those errors I got before). Unfortunetaly it doesn't work for me :/

ifconfig gives me only this: ```
eth0      Link encap:Ethernet  HWaddr 40:61:86:c0:e3:ee  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4261:86ff:fec0:e3ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2017260 (2.0 MB)  TX bytes:428146 (428.1 KB)
          Interrupt:27 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```

---

### Post by okplayer02 on 2010-06-29
well can you run the command 

```
lspci
```

to list your wireless network card.

---

### Post by Pithikos on 2010-06-29
Yeah I see my card now: 
```
01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

What does that mean? :S

---

### Post by okplayer02 on 2010-06-29
well you posting in 2 threads so i dont want to give you advice to confuse you even more. but search for your chipset using google that is one suggestion

---

### Post by Pithikos on 2010-06-29
I fixed the problem. Someone suggested I run ```
cp /etc/modprobe.d/ndiswrapper ~ && sudo rm /etc/modprobe.d/ndiswrapper
``` and it worked! It just backups and removes ndiswrapper. Then I just rebooted and voila! Seems like it was conflicting with the card's other drivers. Everything works perfect with r8185b(which I guess is the linux driver given by realtek). Hope that that helps others :)

---

### Post by crd6640 on 2010-07-12
> **S1lverado said:**
> You need to search the site before making a post:lolflag:I think I've tried everything. Some required a link to the Internet so I could get the Internet working -- Hum!
I've tried to use at least two different pci cards and a belkin USB dongle all without success on versions from 8.0 thru 10.04.  I've had no luck so I gave up and looked for compatible Cards/USB dongles and decided to buy a new dongle that is claimed to work out of the box just by adding the user password. A list of the USB wireless dongles that are compatible are at this site:
[http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html]("http://www.cyberciti.biz/tips/linux-usb-wireless-compatibility-adapter-list.html")
I believe (and hope)this solution will solve my frustration as well as my wireless connection problem under UBUNTU.  Perhaps it is also your best bet!

---

### Post by Pithikos on 2010-07-12
Well which cards did you try out? Because if you have the same card with mine then that means that there is a solution for you ;)

---

### Post by danimall on 2011-03-02
I'm using the 64-bit Ubuntu 10.10 and this is what I found for a solution

wget [http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin](http://svn.debian.org/wsvn/kernel/dists/trunk/firmware-nonfree/realtek/RTL8192SU/rtl8192sfw.bin)
sudo mkdir /lib/firmware/RTL8192SU
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU

It's way easier than any of the other posts and it actually works.  Essentially, you are just downloading the firmware and moving it into your firmware directory.  After unplugging and plugging it back in, it worked.

I found the solution here

[http://ossnotebook.blogspot.com/2010/08/dlink-dwa-131-usb-wireless-on-ubuntu.html](http://ossnotebook.blogspot.com/2010/08/dlink-dwa-131-usb-wireless-on-ubuntu.html)

---


---
title: "problem installing driver for realtek rtl8185 wireless card."
date: 2008-06-09
forum: Hardware
---

### Post by spartanghost on 2008-06-09
I have a Toshiba Satellite A210-MS9.  I upgraded to hearty heron the other day (i was running gutsy before, but i had no sound so i upgraded) and now i can't reinstall my wireless drivers.  can anyone give me some help, or if not, tell me what information you need to help and/or how to get it? thanks

---

### Post by stchman on 2008-06-09
> **spartanghost said:**
> I have a Toshiba Satellite A210-MS9.  I upgraded to hearty heron the other day (i was running gutsy before, but i had no sound so i upgraded) and now i can't reinstall my wireless drivers.  can anyone give me some help, or if not, tell me what information you need to help and/or how to get it? thanks

Go to [www.realtek.com.tw](www.realtek.com.tw) and download the drivers for that card.

You are going to have ot make them, but there should be instructions in the .tar.gz archive.

---

### Post by spartanghost on 2008-06-09
I tried that, but i get errors. i'll try and get the errors so i can posrt what they are.

update: ok, i tried it again, but when it ( i assume ) tries to complile trhe drivers, it gets a bunch of warnings along the lines of "incompatible pointer type from assignment" or something. i remember from my programming classes that was when i used . instead of -> with pointers ( i think )

that was when i made the drivers. after that i had to do a command along the lines of ./wlan0up , but then it complains that the files it needs dont exist.

any ideas?

---

### Post by stchman on 2008-06-09
> **spartanghost said:**
> I tried that, but i get errors. i'll try and get the errors so i can posrt what they are.

update: ok, i tried it again, but when it ( i assume ) tries to complile trhe drivers, it gets a bunch of warnings along the lines of "incompatible pointer type from assignment" or something. i remember from my programming classes that was when i used . instead of -> with pointers ( i think )

that was when i made the drivers. after that i had to do a command along the lines of ./wlan0up , but then it complains that the files it needs dont exist.

any ideas?

Is there a readme in the driver install?

Looks like you just run the makedrv script.

Did you try rebooting after the makedrv was done.  Hardy installs the WPA Supplicant by default.

Also to compile drivers in Hardy you need to have build-essential installed.

---

### Post by spartanghost on 2008-06-09
that could explain the problem. where can i get them? im posting from windows ( wireless in windoze works fine ) so i can save BE on my external drive to install in linux

---

### Post by stchman on 2008-06-09
> **spartanghost said:**
> that could explain the problem. where can i get them? im posting from windows ( wireless in windoze works fine ) so i can save BE on my external drive to install in linux

I am assuming your laptop has a working wired ethernet connection.  If yes hook your laptop up to a wire and then do the following in a terminal:

```
sudo apt-get install build-essential
```

You need an internet connection to get that package installed.

---

### Post by spartanghost on 2008-06-09
alright. ill try that and post if it works or not.

ok, this is stupid. i typed that in exactly into the terminal and it says it cannot find the package. im starting to get really frustrated.

update: so i got build essentials installed, BUT it STILL wont install right.

it does this when i do the ./makedrv:

./ieee80211/
./ieee80211/ieee80211_module.c
./ieee80211/ieee80211_rx.c
./ieee80211/tags
./ieee80211/Makefile
./ieee80211/ieee80211_crypt_tkip.c
./ieee80211/ieee80211_softmac.c
./ieee80211/readme
./ieee80211/ieee80211_crypt_ccmp.c
./ieee80211/ieee80211.h
./ieee80211/ieee80211_tx.c
./ieee80211/ieee80211_softmac_wx.c
./ieee80211/ieee80211_crypt.h
./ieee80211/ieee80211_wx.c
./ieee80211/license
./ieee80211/ieee80211_crypt_wep.c
./ieee80211/ieee80211_crypt.c
rtl8185/
rtl8185/README.adhoc
rtl8185/r8180_sa2400.h
rtl8185/Makefile
rtl8185/copying
rtl8185/README.master
rtl8185/r8180.h
rtl8185/install
rtl8185/r8180_max2820.h
rtl8185/r8180_max2820.c
rtl8185/r8180_rtl8225.h
rtl8185/r8180_wx.h
rtl8185/authors
rtl8185/tags
rtl8185/r8180_pm.c
rtl8185/r8180_hw.h
rtl8185/r8180_gct.c
rtl8185/r8180_gct.h
rtl8185/r8180_rtl8225.c
rtl8185/readme
rtl8185/r8180_93cx6.h
rtl8185/ieee80211.h
rtl8185/license
rtl8185/r8180_pm.h
rtl8185/changes
rtl8185/r8180_rtl8225z2.c
rtl8185/r8180_wx.c
rtl8185/r8180_rtl8255.c
rtl8185/r8180_93cx6.c
rtl8185/r8180_sa2400.c
rtl8185/r8180_core.c
rtl8185/r8180_rtl8255.h
rtl8185/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/tmp
make -C /lib/modules/2.6.24-16-generic/build M=/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.o
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c: In function &#8216;ieee80211_softmac_init&#8217;:
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2236: warning: assignment from incompatible pointer type
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2237: warning: assignment from incompatible pointer type
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2238: warning: assignment from incompatible pointer type
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2239: warning: assignment from incompatible pointer type
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2240: warning: assignment from incompatible pointer type
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2241: warning: assignment from incompatible pointer type
  CC [M]  /home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_rx.o
  CC [M]  /home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_tx.o
  CC [M]  /home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_wx.o
  CC [M]  /home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_module.o
  CC [M]  /home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt.o
  CC [M]  /home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.o
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_aes_encrypt&#8217;:
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:88: warning: passing argument 1 of &#8216;crypto_cipher_encrypt_one&#8217; from incompatible pointer type
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_init&#8217;:
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:110: warning: assignment from incompatible pointer type
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:127: warning: passing argument 1 of &#8216;crypto_free_cipher&#8217; from incompatible pointer type
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_deinit&#8217;:
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:144: warning: passing argument 1 of &#8216;crypto_free_cipher&#8217; from incompatible pointer type
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: In function &#8216;ieee80211_ccmp_set_key&#8217;:
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:422: warning: passing argument 1 of &#8216;crypto_cipher_setkey&#8217; from incompatible pointer type
  CC [M]  /home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.o
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c: In function &#8216;ieee80211_tkip_encrypt&#8217;:
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:417: error: &#8216;struct scatterlist&#8217; has no member named &#8216;page&#8217;
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c: In function &#8216;ieee80211_tkip_decrypt&#8217;:
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:511: error: &#8216;struct scatterlist&#8217; has no member named &#8216;page&#8217;
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c: In function &#8216;michael_mic&#8217;:
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:613: error: &#8216;struct scatterlist&#8217; has no member named &#8216;page&#8217;
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:617: error: &#8216;struct scatterlist&#8217; has no member named &#8216;page&#8217;
make[2]: *** [/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.o] Error 1
make[1]: *** [_module_/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/tmp
make -C /lib/modules/2.6.24-16-generic/build M=/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.o
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: In function &#8216;rtl8180_proc_module_init&#8217;:
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:588: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:588: error: (Each undeclared identifier is reported only once
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:588: error: for each function it appears in.)
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: In function &#8216;rtl8180_proc_module_remove&#8217;:
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:594: error: &#8216;proc_net&#8217; undeclared (first use in this function)
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: In function &#8216;rtl8180_init&#8217;:
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3159: warning: assignment from incompatible pointer type
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3522: error: &#8216;SA_SHIRQ&#8217; undeclared (first use in this function)
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3522: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: In function &#8216;rtl8180_pci_probe&#8217;:
/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:4213: error: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
make[2]: *** [/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.o] Error 1
make[1]: *** [_module_/home/renault/Desktop/rtl8185_linux_26.1027.0823.2007/rtl8185] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2

and then when i do ./wlan0up (like it says to do in the readme i get this:

insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8180.ko': No such file or directory
wlan0: ERROR while getting interface flags: No such device


can anyone translate that?

---

### Post by stchman on 2008-06-10
Did you reboot to see if your wireless connection is in Network?

System--->Administration--->Network

---

### Post by spartanghost on 2008-06-10
i've rebooted a number of times, but i never thought to look there. i'll try it and see what i get

---

### Post by spartanghost on 2008-06-11
ok, i checked there and it doesnt show any wireless.  either that or i dont know where to look. I really need to get this wireless card working.  for some reason it's on the USB bus. might that be causing recognition issues?

---

### Post by sanford42 on 2009-12-30
I just bought a PCI card with this chipset on it. 

I can connect to wireless networks, but every network I see has "1 bar", and my other two machines (my eeePC running Ubuntu 9.04 Netbook Remix and my home-built Windows7 gaming rig... ironically with the exact same card) show my network signal at full bars. 

I downloaded the drivers from RealTek and tried to compile them but here's what I get:

> 
$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  CC [M]  /home/sanford/Downloads/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_module.o
/home/sanford/Downloads/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_module.c: In function ‘alloc_ieee80211_rtl’:
/home/sanford/Downloads/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_module.c:123: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
make[2]: *** [/home/sanford/Downloads/rtl8185_linux_26.1030.0625.2009.release/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/sanford/Downloads/rtl8185_linux_26.1030.0625.2009.release/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [all] Error 2


It's been **FOREVER** since I've had to compile drivers from source.  I have build-essential but with or without it, that's the same console output. 

Any clues/suggestions/tips?

---

### Post by cggaret on 2010-01-04
Make sure that you have the headers for the kernel that you are working in installed.  I had a similar problem and this fixed it.  To find the header package search in synaptic for your kernel number.  In gnome, the easiest way to figure out which kernel you are working in is the System Monitor, which is in the menu under System>Administration>System Monitor.  Hope this helps.

---

### Post by sanford42 on 2010-01-04
<facepalm>

I didn't even think about the headers... Ugh. 

I'll try that in just a second when I get to that machine and let you know if it worked :)

---

### Post by sanford42 on 2010-01-04
Actually, the headers *were* already installed... so I guess that's not it either. 

Grr... I mean I'm not doing anything particularly needing a super-fast connection on this box (it's my "every day use" system for web browsing, IM's and Facebook), but it would be nice to have at least a moderately decent connection speed, ya know?

---

### Post by jonny.allred on 2010-01-24
I'm having the exact same problem.  Any help is appreciated, thanks in advance, you guys rock.

---

### Post by Yellow Pasque on 2010-01-25
Have you tried using ndiswrapper and the appropriate windows XP driver? (I'm sure you can find it somewhere on realtek's site)

---


---
title: "Toshiba L655-S5096 Wireless not functioning"
date: 2011-04-06
forum: Hardware
---

### Post by THGIC on 2011-04-06
Hello everyone, 

     The wireless function on my Toshiba Satellite L655-S5096 laptop is not functioning. I am trying to turn on the wireless with this command; FN + F8. That is how you enable it in Windows (the Wireless symbol is located on the F8 key), but it will not turn on or anything. I can try and connect to a wireless network, if I do it manually -- it still wont connect, even if I do that. 

     I have tried to install the wireless driver from 'Wine': I extracted the files and set the .exe files as trusted. Nothing at this point has yet to work and I am kind of frustrated with this. 

Any thoughts and/or ideas?

---

### Post by mikewhatever on 2011-04-06
Can you post the output of the following from Applications->Accessories->Terminal:
```
lspci | grep -i net
```

Some wireless cards require their drivers manually installed, and there is a way to use Windows drivers, but Wine is not that way.

---

### Post by THGIC on 2011-04-06
> **mikewhatever said:**
> Can you post the output of the following from Applications->Accessories->Terminal:
```
lspci | grep -i net
```Some wireless cards require their drivers manually installed, and there is a way to use Windows drivers, but Wine is not that way.

lauren@lauren-Satellite-L655:~$ lspci | grep -i net
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
03:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
lauren@lauren-Satellite-L655:~$ 

That is what I got from it.

---

### Post by TeoBigusGeekus on 2011-04-06
Can you post us the output of 
```
lshw -C network
```
?

---

### Post by THGIC on 2011-04-06
lauren@lauren-Satellite-L655:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:d4400000-d4403fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c1
       serial: 60:eb:69:80:49:50
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A ip=192.168.1.102 latency=0 multicast=yes
       resources: irq:46 memory:d3400000-d343ffff ioport:2000(size=128)
lauren@lauren-Satellite-L655:~$

---

### Post by TeoBigusGeekus on 2011-04-06
See [this]("http://ubuntuforums.org/showthread.php?t=1420752") thread.

---

### Post by THGIC on 2011-04-06
> **TeoBigusGeekus said:**
> See [this]("http://ubuntuforums.org/showthread.php?t=1420752") thread.

I am very lost in this link. 

I need to get rid of this 'NDISWrapper' I think, then try and install the package that I downloaded (Realtek Driver). I don't know how to do that and I wouldn't know where to start. I am not ignorant to learning this stuff from other threads, it is that I am very new to Ubuntu and so used to Windows. 

I would greatly appreciate any help, if anyone can help me or guide me through that thread that was posted.

---

### Post by TeoBigusGeekus on 2011-04-06
To uninstall ndiswrapper
```
sudo apt-get purge ndiswrapper
```
Do it and post back if it succeeded.

---

### Post by THGIC on 2011-04-06
lauren@lauren-Satellite-L655:~$ sudo apt-get purge ndiswrapper
[sudo] password for lauren: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ndiswrapper
lauren@lauren-Satellite-L655:~$

---

### Post by TeoBigusGeekus on 2011-04-06
How did you install ndiswrapper in the first place?

---

### Post by THGIC on 2011-04-06
I didn't even know what that thing was or that it even existed; let alone me install it. I am just saying, I didn't install it, but I guess I need drivers still.

---

### Post by TeoBigusGeekus on 2011-04-06
Ok then.
Download [this]("http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz") archive, say on your Desktop and double click it.
Extract its contents on your Desktop.
Now open a terminal and give
```
cd ~/Desktop/rtl8192se_linux_2.6.0010.1211.2009
sudo make
sudo sed -i 's/install: modules/install:/g' ./ieee80211/Makefile
sudo sed -i 's/install: modules/install:/g' ./HAL/rtl8192/Makefile
sudo make install
sudo echo "r8192se_pci" > /etc/modules
sudo modprobe r8192se_pci
```

---

### Post by THGIC on 2011-04-06
> **TeoBigusGeekus said:**
> Ok then.
Download [this]("http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz") archive, say on your Desktop and double click it.
Extract its contents on your Desktop.
Now open a terminal and give
```
cd ~/Desktop/rtl8192se_linux_2.6.0010.1211.2009
sudo make
sudo sed -i 's/install: modules/install:/g' ./ieee80211/Makefile
sudo sed -i 's/install: modules/install:/g' ./HAL/rtl8192/Makefile
sudo make install
sudo echo "r8192se_pci" > /etc/modules
sudo modprobe r8192se_pci
```

I already saved it to my desktop and I ran that command line. I exited out of the original window and I ran that command line again, just so I could post the results. Tell me if anything is missing or I need to do anything else. 

lauren@lauren-Satellite-L655:~$ lauren@lauren-Satellite-L655:~$ cd ~/Desktop/rtl8192se_linux_2.6.0010.1211.2009
u
lauren@lauren-Satellite-L655:~$: command not found
lauren@lauren-Satellite-L655:~$ lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$ sudo make
bash: lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$: No such file or directory
lauren@lauren-Satellite-L655:~$ make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/rtl_core.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/rtl8192se.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/rtl_eeprom.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/rtl_wx.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/rtl_cam.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/rtl_pm.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/rtl_ps.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/rtl_debug.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/rtl_ethtool.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8190_rtl8256.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8192S_Efuse.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8192S_phy.o
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8192S_phy.c: In function ‘rtl8192_phy_setTxPower’:
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8192S_phy.c:1785: warning: enumeration value ‘RF_TYPE_MIN’ not handled in switch
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8192S_phy.c:1785: warning: enumeration value ‘RF_PSEUDO_11N’ not handled in switch
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8192S_firmware.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8192E_dm.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8192S_rtl6052.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8192S_hwimg.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8192S_led.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8192S_mp.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_rx.o
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_rx.c: In function ‘RxReorderIndicatePacket’:
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_rx.c:855: warning: the frame size of 1072 bytes is larger than 1024 bytes
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_softmac.o
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_softmac.c: In function ‘ieee80211_sta_send_associnfo’:
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_softmac.c:2350: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘size_t’
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_softmac.c:2350: warning: format ‘%d’ expects type ‘int’, but argument 4 has type ‘size_t’
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_tx.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_wx.o
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_wx.c: In function ‘ieee80211_wx_set_gen_ie_rsl’:
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_wx.c:1292: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘size_t’
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_wx.c:1308: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘size_t’
>   CC [M]  /home/lauren/Desktop/rtl8192se_linu
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_module.c: In function ‘store_debug_level’:
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_module.c:429: warning: comparison of distinct pointer types lacks a cast
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_softmac_wx.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/rtl819x_HTProc.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/rtl819x_TSProc.o
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/rtl819x_TSProc.c: In function ‘RxPktPendingTimeout’:
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/rtl819x_TSProc.c:118: warning: the frame size of 1056 bytes is larger than 1024 bytes
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/rtl819x_BAProc.o
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/rtl819x_BAProc.c: In function ‘ieee80211_rx_ADDBAReq’:
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/rtl819x_BAProc.c:284: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/rtl819x_BAProc.c: In function ‘ieee80211_rx_ADDBARsp’:
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/rtl819x_BAProc.c:372: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/rtl819x_BAProc.c: In function ‘ieee80211_rx_DELBA’:
> /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/rtl819x_BAProc.c:481: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘long unsigned int’
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/dot11d.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_crypt.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_crypt_tkip.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_crypt_ccmp.o
>   CC [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/../../ieee80211/ieee80211_crypt_wep.o
>   LD [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8192se_pci.o
>   Building modules, stage 2.
>   MODPOST 1 modules
>   CC      /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8192se_pci.mod.o
>   LD [M]  /home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192/r8192se_pci.ko
> make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
> lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$ sudo sed -i 's/install: modules/install:/g' ./ieee80211/Makefile
> lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$ sudo sed -i 's/install: modules/install:/g' ./HAL/rtl8192/Makefile
> lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$ sudo make install
> make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 61: syntax error: unexpected end of file
make[1]:: command not found
lauren@lauren-Satellite-L655:~$   Building modules, stage 2.
Building: command not found
lauren@lauren-Satellite-L655:~$   MODPOST 1 modules
MODPOST: command not found
lauren@lauren-Satellite-L655:~$ make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
> make[1]: Entering directory `/home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192'
> install -p -m 644 r8192se_pci.ko /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/
> depmod -a
> make[1]: Leaving directory `/home/lauren/Desktop/rtl8192se_linux_2.6.0010.1211.2009/HAL/rtl8192'
bash: command substitution: line 1: unexpected EOF while looking for matching `''
bash: command substitution: line 3: syntax error: unexpected end of file
make[1]:: command not found
lauren@lauren-Satellite-L655:~$ lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$ sudo echo "r8192se_pci" > /etc/modules
bash: /etc/modules: Permission denied
lauren@lauren-Satellite-L655:~$ bash: /etc/modules: Permission denied
No command 'bash:' found, did you mean:
 Command 'bash' from package 'bash' (main)
bash:: command not found
lauren@lauren-Satellite-L655:~$ lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$ sudo modprobe r8192se_pci
bash: lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$: No such file or directory
lauren@lauren-Satellite-L655:~$ WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save, it will be ignored in a future release.
WARNING:: command not found
lauren@lauren-Satellite-L655:~$ lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$ 
bash: lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$: No such file or directory
lauren@lauren-Satellite-L655:~$ lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$ 
bash: lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$: No such file or directory
lauren@lauren-Satellite-L655:~$ lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$ 
bash: lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$: No such file or directory
lauren@lauren-Satellite-L655:~$ lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$ 
bash: lauren@lauren-Satellite-L655:~/Desktop/rtl8192se_linux_2.6.0010.1211.2009$: No such file or directory
lauren@lauren-Satellite-L655:~$

---

### Post by THGIC on 2011-04-06
In all honesty, I don't believe it installed the driver. It came up with an error stating, 'WARNING: All config files need .conf: /etc/modprobe.d/blacklist.save, it will be ignored in a future release.
WARNING:: command not found'. 

Any thoughts about it?

---

### Post by THGIC on 2011-04-06
***ATTENTION***

To TeoBigusGeekus,

I just realised that the laptop I am trying to get the wireless card to work with is running Ubuntu 10.10 and my laptop that IS WORKING, is running the new Ubuntu 11.04. 

My sincerest apologies for any headaches and inconveniences when trying to solve this thread. I did not realise this until my friend mentioned something about Ubuntu 11.04 being glitchy and I said, "That's ok, this laptop is running Ubuntu 10.10 ..." FAIL. 

I would ask that you forgive my blond moment and maybe it might be easier from here to fix this issue. 

The Toshiba Satellite L655-S5096 is running Ubuntu 10.10, NOT UBUNTU 11.04. 

Thank you.

---

### Post by xXkanfirXx on 2011-04-06
I'm having a problem with my wireless too.. What's happening is my wireless card will turn on, find networks, and connect to them. But the Internet will not work. Firefox won't work update manager won't work, software center won't work, nothing. I've checked under "additional drivers" and it shows the driver is installed and activated and currently in use. What could be wrong!? I'm so frustrated! I'm seriously about to pull my hair out. I've been fighting this and trying to get help with this for two days. So Please any help would be MUCH appreciated.

---

### Post by THGIC on 2011-04-06
> **xXkanfirXx said:**
> I'm having a problem with my wireless too.. What's happening is my wireless card will turn on, find networks, and connect to them. But the Internet will not work. Firefox won't work update manager won't work, software center won't work, nothing. I've checked under "additional drivers" and it shows the driver is installed and activated and currently in use. What could be wrong!? I'm so frustrated! I'm seriously about to pull my hair out. I've been fighting this and trying to get help with this for two days. So Please any help would be MUCH appreciated.

Which version of Ubuntu are you running and how did you install it? Automatically or manually editing partitions?

---

### Post by xXkanfirXx on 2011-04-06
> **THGIC said:**
> Which version of Ubuntu are you running and how did you install it? Automatically or manually editing partitions?

10.10 I installed as the primary OS. So no partitions.

---

### Post by THGIC on 2011-04-07
> **xXkanfirXx said:**
> 10.10 I installed as the primary OS. So no partitions.

For as much as it is worth to you, I upgraded to Ubuntu 11.04 (32-Bit) and it solved my wireless issue. While running Ubuntu 10.10, I could connect wired, but not wireless. There was no indication that I had wireless connections available, let alone the fact that I had a wireless card. 

Ubuntu 11.04 recognized my wireless card and allowed to connect wired and wireless. The page layout if just a tad different, but it is a good one. People may argue that it is still not stable and is still "testing" software, but I have found no issues with it thus far (and hopefully I wont!). 

I would consider upgrading to Ubuntu 11.04. But, I wiped my drive and did a clean install -- not the upgrade. I had already backed up my info, so I did a clean install. 

Reasons why I did a clean install:

If you upgrade from Ubuntu 10.10 to 11.04, while experiencing software/hardware difficulties, you may incur those same issues in 11.04, just by simply upgrading. By upgrading to 11.04, you are still keeping your personal info. on there and a few, important system files, so the upgrade process is quicker and smooth. The problem I see with that is; if you upgrade from a stable OS (Ubuntu 10.10), while you are having issues (whether it be hardware or software), to an unstable OS (Ubuntu 11.04), as it is still "testing software"; you may experience glitching and a few other issues. 

The choice is of course yours; I am merely making the suggestion to install 11.04. It worked for me -- even on the most glitched system or brand of laptop I can think of (Toshiba), it works just fine.

---

### Post by xXkanfirXx on 2011-04-07
> **THGIC said:**
> For as much as it is worth to you, I upgraded to Ubuntu 11.04 (32-Bit) and it solved my wireless issue. While running Ubuntu 10.10, I could connect wired, but not wireless. There was no indication that I had wireless connections available, let alone the fact that I had a wireless card. 

Ubuntu 11.04 recognized my wireless card and allowed to connect wired and wireless. The page layout if just a tad different, but it is a good one. People may argue that it is still not stable and is still "testing" software, but I have found no issues with it thus far (and hopefully I wont!). 

I would consider upgrading to Ubuntu 11.04. But, I wiped my drive and did a clean install -- not the upgrade. I had already backed up my info, so I did a clean install. 

Reasons why I did a clean install:

If you upgrade from Ubuntu 10.10 to 11.04, while experiencing software/hardware difficulties, you may incur those same issues in 11.04, just by simply upgrading. By upgrading to 11.04, you are still keeping your personal info. on there and a few, important system files, so the upgrade process is quicker and smooth. The problem I see with that is; if you upgrade from a stable OS (Ubuntu 10.10), while you are having issues (whether it be hardware or software), to an unstable OS (Ubuntu 11.04), as it is still "testing software"; you may experience glitching and a few other issues. 

The choice is of course yours; I am merely making the suggestion to install 11.04. It worked for me -- even on the most glitched system or brand of laptop I can think of (Toshiba), it works just fine.
Thank you, I'll try it out. I have nothing to loose. I just installed 10.10 a couple days ago. So is 10.10 64bit? and 10.4 32bit? Cause my laptop was originally running 32bit windows 7.

---

### Post by TeoBigusGeekus on 2011-04-07
> **THGIC said:**
> For as much as it is worth to you, I upgraded to Ubuntu 11.04 (32-Bit) and it solved my wireless issue. While running Ubuntu 10.10, I could connect wired, but not wireless. There was no indication that I had wireless connections available, let alone the fact that I had a wireless card. 

Ubuntu 11.04 recognized my wireless card and allowed to connect wired and wireless. The page layout if just a tad different, but it is a good one. People may argue that it is still not stable and is still "testing" software, but I have found no issues with it thus far (and hopefully I wont!). 

I would consider upgrading to Ubuntu 11.04. But, I wiped my drive and did a clean install -- not the upgrade. I had already backed up my info, so I did a clean install. 

Reasons why I did a clean install:

If you upgrade from Ubuntu 10.10 to 11.04, while experiencing software/hardware difficulties, you may incur those same issues in 11.04, just by simply upgrading. By upgrading to 11.04, you are still keeping your personal info. on there and a few, important system files, so the upgrade process is quicker and smooth. The problem I see with that is; if you upgrade from a stable OS (Ubuntu 10.10), while you are having issues (whether it be hardware or software), to an unstable OS (Ubuntu 11.04), as it is still "testing software"; you may experience glitching and a few other issues. 

The choice is of course yours; I am merely making the suggestion to install 11.04. It worked for me -- even on the most glitched system or brand of laptop I can think of (Toshiba), it works just fine.

Glad to hear you've fixed your issue, cause the compiling of the driver was a mess.
Natty uses a much later kernel than maverick so it was somehow expected that it would recognise your wireless card.
Welcome to linux.

---

### Post by THGIC on 2011-04-07
> **TeoBigusGeekus said:**
> Glad to hear you've fixed your issue, cause the compiling of the driver was a mess.
Natty uses a much later kernel than maverick so it was somehow expected that it would recognise your wireless card.
Welcome to linux.

Thank you Teo. The kernel from 10.10 just didn't have the proper driver support like 11.04 Natty does. I could run 10.10 on my Sony Vaio with ease, but I couldn't resist the change! 

Pros: 
Better Pics if I wanna change my LoginWindow and more themes for Window schemes.

'sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow' 

'sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop' (to remove the prompt when you're all done)

Looks pretty clean; side-bar is easy to use (still getting used to though); much better driver support.

Cons: 
It is still "beta" software, so you will have minor glitches here and there. Google Chrome is translated as 32-Bit, if you want to use it -- unless you downloaded a different ISO for 11.04, the standard ISO was 32-Bit (at least that's how mine happened). Everything seems slow at first, but after about five minutes, everything is how it should be. 

I am running:

Sony Vaio - Gunmetal Black
Intel Core i3 350M @ 2.27GHz
4GB DDR3 @1066MHz
320GB Toshiba @ 5400RPM (bottleneck in my system  >.>)
Intel integrated HD graphics (chip set) 
Ubuntu 11.04 Natty.

It isn't like I am running anything incompetent of producing decent performance; although, it is "beta" software, so anything is possible. 

Anyways, sorry about all of the confusion with my original issue. I got totally lost in trying to figure out why my wireless card was not supported and forgot to mention the correct version of Ubuntu I was running. My apologies to all for the headaches I may have caused and I thank you for your patience through all of this trouble. 

Looks like this thread is solved.  :)

---

### Post by xXkanfirXx on 2011-04-07
> **THGIC said:**
> For as much as it is worth to you, I upgraded to Ubuntu 11.04 (32-Bit) and it solved my wireless issue. While running Ubuntu 10.10, I could connect wired, but not wireless. There was no indication that I had wireless connections available, let alone the fact that I had a wireless card. 

Ubuntu 11.04 recognized my wireless card and allowed to connect wired and wireless. The page layout if just a tad different, but it is a good one. People may argue that it is still not stable and is still "testing" software, but I have found no issues with it thus far (and hopefully I wont!). 

I would consider upgrading to Ubuntu 11.04. But, I wiped my drive and did a clean install -- not the upgrade. I had already backed up my info, so I did a clean install. 

Reasons why I did a clean install:

If you upgrade from Ubuntu 10.10 to 11.04, while experiencing software/hardware difficulties, you may incur those same issues in 11.04, just by simply upgrading. By upgrading to 11.04, you are still keeping your personal info. on there and a few, important system files, so the upgrade process is quicker and smooth. The problem I see with that is; if you upgrade from a stable OS (Ubuntu 10.10), while you are having issues (whether it be hardware or software), to an unstable OS (Ubuntu 11.04), as it is still "testing software"; you may experience glitching and a few other issues. 

The choice is of course yours; I am merely making the suggestion to install 11.04. It worked for me -- even on the most glitched system or brand of laptop I can think of (Toshiba), it works just fine.
Well what do you know?! It's working! I'm so happy. Thanks for the suggestion! :)

---


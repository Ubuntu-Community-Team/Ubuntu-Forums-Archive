---
title: "Broadcom b43 Legacy Driver not active in Ubuntu 10.04 2.6.32-22"
date: 2010-06-10
forum: Hardware
---

### Post by joebobthe13th on 2010-06-10
When using Ubuntu 10.04 2.6.32-22, my Broadcom b43 Legacy driver is not activated, meaning that I can't access the internet. Whats weird is that in 2.6.32-21, the drive works just fine. If I run the command "sudo apt-get install b43-fwcutter" I am told that the packaged is already installed. Does this mean I have to activate it? Thanks in advance.

---

### Post by dvlchd3 on 2010-06-10
For b43 to work properly, the firmware must be installed.  Try reconfiguring the b43-fwcutter package:

```

sudo dpkg --configure b43-fwcutter

```
Hopefully you will be prompted to download the firmware, if so select yes.

If this does not resolve the issue, try the manual route:

Download firmware files:
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

Install the firmware:
```

cd ~/Downloads
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar jxvf broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o

```

Hope this helps.

---

### Post by joebobthe13th on 2010-06-11
I tried both solutions, but unfortunately neither worked. The first solution resulted in this message:  "dpkg: error processing b43-fwcutter (--configure):  package b43-fwcutter is already installed and configured Errors were encountered while processing:  b43-fwcutter:"  The second one gave no error message but also didn't fix anything.

---

### Post by dvlchd3 on 2010-06-11
I just found a bug report that may apply.  **Before reading anything below, please run this command:**
```

lspci | grep Network

```
If you have a Broadcom BCM4312, go here: [https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/581250](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/581250)

There appears to be a bug with the new kernel, but appears to only apply to that card.  My BCM4311 works fine.

If you do not have the BCM4312, read on...

I'm sorry, maybe I was being dumb with the first response, but I think I missed a step here.

Your question implied you are unable to see the Broadcom driver activated in "Hardware Drivers"? (System -> Administration -> Hardware Drivers).  That is simply a graphically interface to installing restricted drivers, and may not properly represent what is actually installed.

I'm assuming you are unable to scan or see any wifi hotspots, and your wifi light is off.  If this is the case, simply try bringing up the interface:
```

sudo ifconfig wlan0 up

```

If you receive an error along the lines of wlan0 does not exist, or failed to bring up the interface, lets try to completely reinstall the driver:

```

sudo apt-get update && sudo apt-get --purge autoremove b43-fwcutter && sudo apt-get -y install b43-fwcutter

```

If you are still not seeing any results, please post the results of these commands:
```

iwconfig
lsmod | grep b43
lspci | grep Network
dmesg | grep wlan0

```

---

### Post by joebobthe13th on 2010-06-13
I had high hopes, but no joy.
 After running "lspci | grep Network" I got "03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)" which I'm assuming means that I have a BBCM4306.
 "sudo ifconfig wlan0 up" resulted in   "wlan0: ERROR while getting interface flags: No such device" 
 The next line of code you gave me ran without error, but after a restart my wireless was still not available and "wlan0: ERROR while getting interface flags: No such device" was still shown. 

iwconfig: "lo        no wireless extensions.  eth0      no wireless extensions." 
 lsmod | grep b43: No output. 
 lspci | grep Network: 03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)    
dmesg | grep wlan0: No output.

---

### Post by joebobthe13th on 2010-06-17
Bump?

---

### Post by Youresorock on 2010-06-18
I upgraded to 10.04 and have the same problem.  This is on my work machine which is a 24" iMac.
```

iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

dmesg | grep wlan0
[no output]

lspci | grep Network
04:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

lsmod | grep b43
b43                   174953  0 
mac80211              238128  1 b43
cfg80211              148386  2 b43,mac80211
led_class               3732  2 b43,applesmc
ssb                    43517  1 b43

uname -a
Linux iUbuntu 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

```


This didn't work in 9.10 either, but I was hopeful for 10.04.  ;)

Both the gui Hardware Drivers and the above posted commandline install method complete without reported error.

---

### Post by sk@ssL on 2010-09-07
Hey there... i had the same problem and i could fix it this way :D
First do this on a terminal apt-get update && apt-get upgrade, 2.- go to Synaptic Package Manager, write this git-core and apply the changes, b43-fwcutter and also apply the changes then go to System>Administration>Hardware drivers and select B43 wireless driver and activate  it and thats it!!! your wireless connection should be working ;) with the wlan0 interface.

;)
[CENTER]Wireshark Cookie Dump:

OKCancel[/CENTER]

---


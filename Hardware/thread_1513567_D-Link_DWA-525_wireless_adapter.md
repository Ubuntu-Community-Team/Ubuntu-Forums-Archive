---
title: "D-Link DWA-525 wireless adapter"
date: 2010-06-19
forum: Hardware
---

### Post by nacho.lpe on 2010-06-19
I have bought a D-Link DWA-525 wireless adapter and I can't make it work. I Have downloaded the drivers from its website and when I try to install them keep getting the same error.

I have also found the drivers here. 
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

and there it says " extracted and followed their README_STA."

I tried that but I'm quite new in linux and couldn't understand almost anything.
I have a fresh install of xubuntu 10.4 (as I couldn't make the wifi to work I couldn't update it)

I attached here both files, readme and readme_sta


thanks in advance.

---

### Post by indiebuntu on 2010-07-22
I'm going to give this a shot - have the same adapter with Xubuntu. Did you get yours working?

---

### Post by dadsy on 2010-07-30
I've just bought this card thinking either the RaLink or D-link drivers will work. I can't find out if they work or not, when I try to follow their instructions I get the equivalent of a file not found.

If anyone's got any hints or tips they'd be greatly appreciated.

---

### Post by dadsy on 2010-07-31
I've had some success tonight. I adapted this how to [http://ubuntuforums.org/showthread.php?t=1045703]("http://ubuntuforums.org/showthread.php?t=1045703") to the rt3060 and it seems to be working well. 

I downloaded the RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592) drivers and placed them in my home directory.

I used the same commands as in the how-to but changed the 2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2 to 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2 or variations thereof. 
Lastly, I used modprobe rt3562sta in leiu of rtrt2860sta.

I've since rebooted and am now posting this on my new wireless connection.

Hopefully this helps.

---

### Post by kris_gopal on 2010-11-05
I did the same exact thing that dadsy has mentioned in the last post and I was able to configure the DWA-525 in my Ubuntu 10.10 without any problem. 

Thanks for the post

---

### Post by totterdell91 on 2010-12-26
I am running a Dell optiplex 760 with a DWA-525, with 10.10 installed.

I followed the instructions, and did the modprobe and it connects and works fine.... until I reboot. It then loses the configuration.

To get it working I simply change to the driver directory,
do a "sudo make install", then a "sudo modprobe rt3562sta".

I dont know why it is that the fix is not sticking in the kernel image, but I am looking to find out. If someone has some simple advice to save me some time I would appreciate it. 

I am planning on swapping to a maxxed out 960, and I would like to take this card with me (because it has such good reception, and a low profile backing plate)

**afternote
for some reason shutting down and then restarting (not a reboot) has fixed the problem

---

### Post by ronsonk on 2011-03-21
Thanks to all that have posted here. I now have wireless access!  But...

Every time Ubuntu does a kernel upgrade (say through Update Manager), I lose wireless and have to go through most of the steps again.  How do I make this driver 'stick' and stay in place when updating the kernel?

Thanks!

---

### Post by ASolano on 2011-05-11
Hi All,

I just got this card and just installed Ubuntu 10.10 (still testing 11.04)

I failed with the above instructions because I couldn't find where to download the packages they were refering to.

On the D-Link ftp there is only a ZIP file available in the Drivers/Linux folder.

If you find yourself in the same situation, use the following link.  The instructions are easy to follow and it works.

[http://xenstreet.com/2011/02/installing-dlink-dwa-525-linux-drivers.html](http://xenstreet.com/2011/02/installing-dlink-dwa-525-linux-drivers.html)

NOTE:
* When creating a folder to extract the driver files into, do NOT have any spaces in the folder name.
* They make a spelling mistake
  - Mistake = vi  /etc/modeprob.d/blacklist.conf
  - Correct = vi  /etc/modprob.d/blacklist.conf

  In this instruction I used "sudo gedit /etc/modpro......".

---

### Post by khajoor on 2012-10-15
> **dadsy said:**
> I've had some success tonight. I adapted this how to [http://ubuntuforums.org/showthread.php?t=1045703]("http://ubuntuforums.org/showthread.php?t=1045703") to the rt3060 and it seems to be working well. 

I downloaded the RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592) drivers and placed them in my home directory.

I used the same commands as in the how-to but changed the 2008_0918_RT2860_Linux_STA_v1.8.0.0.tar.bz2 to 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2 or variations thereof. 
Lastly, I used modprobe rt3562sta in leiu of rtrt2860sta.

I've since rebooted and am now posting this on my new wireless connection.

Hopefully this helps.

i tried what you did and i got the following ...

```
modprobe rt3562sta
```
gave
```
FATAL: Module rt3562sta not found
```

I tried even this
```
modprobe rt2860sta
```
got the following
```
FATAL: Error inserting rt2860sta (/lib/modules/3.2.0-31-generic/kernel/drivers/net/wireless/rt2860sta.ko): Device or resource busy
```

[COLOR="Red"]EDIT : I TRIED THIS COMMAND AFTER REBOOT 
```
modprobe rt2860sta
```
AND IT  EXECUTED SUCCESSFULLY ... 

HOWEVER WHEN I RAN THIS ```
lsmod | grep rt2860sta
```
I GOT ```
rt2860sta             864748  0 
```

AND ```
iwconfig
``` THREW THE FOLLOWING
```

lo        no wireless extensions.

eth0      no wireless extensions.

```[/COLOR]



;
;
;




Could it be bcos of the following ?



```
lshw -C network
```

this command throws the following info

 ```
description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=4 mingnt=2
       resources: memory:febf0000-febfffff
```

```
lspci
```

throws this info

```
04:00.0 Network controller: Ralink corp. Device 5360
```


I have tried to  ```
make, make install
``` for the following list of driver packages 

1. 2010_01_28_RT2860_Linux_STA_v2.3.0.0_Alpha_v2
2. DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
3. 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO

4. 2010_07_16_RT2860_Linux_STA_v2.4.0.0


i have also tried ```
make uninstall
``` after each attempt of the above ... however i can see that a few remnants of my above attempts are seen at '/sys/bus/drivers/rt2860' probably the uninstallation hasn't happened in a clean manner ... can i delete this folder ? will it not crash my system ...

can i delete this folder and try once again this package

2010_07_16_RT2860_Linux_STA_v2.4.0.0

;
;
;

this thread probably describes my device correctly ... but no solution so far ...

[http://askubuntu.com/questions/124001/there-is-no-driver-for-ralink-chip-5360](http://askubuntu.com/questions/124001/there-is-no-driver-for-ralink-chip-5360)

any help to get this card working on my ubuntu 12.04 is most appreciated !!!

Note : this card works great on Win7 ... FYI

thnx

---


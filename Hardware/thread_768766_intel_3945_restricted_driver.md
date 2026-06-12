---
title: "intel 3945 restricted driver"
date: 2008-04-26
forum: Hardware
---

### Post by litmos95 on 2008-04-26
I upgraded my system from feisty to gutsy yesterday on my laptop Zepto 6214W with Intel Pro 3945AGB wlan card. Now the wlan doesn't work anymore, my question is, how do i use the restricted driver? the ipw3945 is enabled but **not in use**. I have tried to use iwlwifi but always got error during compilation. 
I'm frustrated now, please somebody help.

---

### Post by steveneddy on 2008-04-26
Try installing the backports for Hardy.

```

sudo apt-get install linux-backports-modules-hardy-generic 

```

and then restart

---

### Post by Palu on 2008-04-27
I want to try this. My 3945 is not working either. However, I can only feel safe trying if someone explains the "undo" steps for the instructions above. Thanks!

---

### Post by encompass on 2008-04-27
To my knowledge this card works rather well in ubuntu.  have you tried a live cd?
(Why do people upgrade... it's like so full of problems when they could just install and keep their home partition. so much cleaner.)

---

### Post by Palu on 2008-04-27
> **encompass said:**
> To my knowledge this card works rather well in ubuntu.  have you tried a live cd?
(Why do people upgrade... it's like so full of problems when they could just install and keep their home partition. so much cleaner.)

I wiped everything and did a fresh install. Hardy no longer supports 3945. That makes me think it's a bug--not a missing driver. The first thing I tried to do after installing was get wireless. I'm not the only one with this issue either.

---

### Post by Syke on 2008-04-27
> **Palu said:**
> Hardy no longer supports 3945.I'm not sure why people are having troubles, but Hardy definitely still supports the 3945, and backports are not necessary.

---

### Post by encompass on 2008-04-27
I agree these are one of those cards you buy because you know they will work.
I would check the live cd and see if that one is working.
If this is a fresh install, I would try to avoid the term upgrade as that means you still have peices of the old system installed.
But non-the less if you seem to have a bug, report it.  They will fix something like this for sure!  It would be a huge problem.

---

### Post by Mr_Congeniality on 2008-04-27
If you try transfering a file of about 175MB in size over your network in hardy using this adapter, it will transfer approximately 20MB of the file and proceed to crash your wireless.  I rely on my local network like my backbone, so if I can't walk, then what's the reason of having hardy?

---

### Post by Blackdrive on 2008-04-27
> **encompass said:**
> I agree these are one of those cards you buy because you know they will work.
I would check the live cd and see if that one is working.
If this is a fresh install, I would try to avoid the term upgrade as that means you still have peices of the old system installed.
But non-the less if you seem to have a bug, report it.  They will fix something like this for sure!  It would be a huge problem.

It's been reported already:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190346](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190346)
And on several other places too.

It seems there are major issues with this card. It either doesn't work or it works half of the times or very slow.

I had the problem too, after installing the backports it's fine now. Some people had to install wicd to get it working.

---

### Post by litmos95 on 2008-04-27
How could my card work on Feisty while not in Gutsy? This is ridiculous. It's against the philosophy of Linux as the OS "that just **work**". I've spent more than 6 hours trying to make it work without success. Frustrating...

---

### Post by steveneddy on 2008-04-27
> **Palu said:**
> I want to try this. My 3945 is not working either. However, I can only feel safe trying if someone explains the "undo" steps for the instructions above. Thanks!

It's just another software source. It come from Ubuntu, so you don't "undo", although you could disable it on Software Sources.

The backports just add more functionality to sometime buggy hardware.

---

### Post by pesacadman on 2008-04-27
Thanks for all the help - my 3945 works now!  It did not work on an upgrade from 7.10 but it did work with a clean install. Once the backports were enabled and a restart, the wireless card worked, and the wifi light works also!

---

### Post by funnypanks on 2008-04-27
well 3945 worked from the start in hardy, just now noticed thought that my wifi doesn't light up... strange.. but as they say in the business, who cares

---

### Post by litmos95 on 2008-04-27
Well, i can confirm now that my wlan card works with Hardy. Thanks for the helps.

---

### Post by andydread on 2008-05-03
I agree.  The ipw3945 card has NEVER worked reliably and it seems NOBODY CARES to fix it.  This card was always flaky.  It worked sometimes in dapper
on and off in edgy, really good in feisty, never worked in gutsy reliably for me. could not connect to any secured network. Now in Hardy it does not work at all..  Do they even test stuff before they release it?  This is absolutely ridiculous.  The driver is loaded, No led is on, network manager does not detect anything.   totally frustrating

---

### Post by encompass on 2008-05-03
Work for me... but then again... I seem to do testing of products before the release.  Next time an ubuntu release comes, besure to try it out and report errors!  The don't have the power to test every kind of software out there.  They depend on us.  I always test my hardware so they fix my problems.

---

### Post by damis648 on 2008-05-03
i have this card and it works fine for me on hardy...

---

### Post by Zorael on 2008-05-03
It didn't work at all for me until I created a file located at and named **/etc/modprobe.d/iwl3945**, with the following contents:
```
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 hwcrypto=1
```
Then I restarted the module and it worked flawlessly.
```
$ sudo modprobe -r iwl3945
$ sudo modprobe iwl3945
```

---

### Post by starcannon on 2008-05-03
I have that wireless card on an HP Pavilion dv2600, it "just works" I didn't have to do anything. might be time to give the old home folder a cleaning. Every once in awhile (generally when I'm doing a fresh clean upgrade install) I'll go in and clean out all the personal config files, downside is you have to set everything back up the way you like it, upside is that if you have something goofy causing problems in a personal config its been removed from the equation. 

Not to be a smartarse but do make sure your wifi switch (if you have one) is on, that got me once, kinda made me smack myself in the forehead ;)

---

### Post by Zorael on 2008-05-03
I've had two different 3945 chipsets on my laptop. The first one worked out-of-the-box, no issues. Then I sent in my laptop for repairs (busted motherboard). This was in Feisty, and while it briefly functioned in a Hardy beta, it hasn't properly worked yet, at all, without modification.

It works without flaws in Windows. In Gutsy, I managed to compile drivers that worked, and I stayed the hell away from tinkering with them after that. In Hardy, it just didn't work again, not even after installing backports drivers. Nor could I manage to compile the drivers.

It doesn't work in the new 2.6.24-17 kernel from the backports repo. In fact, it's even worse there. The kill switch is at the front of the unit itself so I can hardly miss it. And after adding that file mentioned in my last post it miraculously started working. Naturally, on the current 2.6.24-16 kernel.


I think I can safely draw the conclusion that it's due to hardware differences.

---

### Post by Marcus82 on 2008-05-04
Hi, new to Ubuntu, have installed it on a Dell Inspiron E1505 with a 3945AGB wireless and I can't get the wireless to work. It worked yesterday after installing linux backports .18 but I messed something else up and had to format. But now after installing the .19 backport (the .18 is gone, only .19, .15 and .14 shows) the operating system stops during start. After I login the background turns grey and I get the mouse pointer but after that nothing happens.

Have tried earlier with the ndiswrapper but I think I messed it up ... as said, I'm new to this...

Hope this isn't to confusing, thanks!

---

### Post by gryzzly on 2008-05-05
Hi there. Using my current laptop (lenovo 3000 n200) since Gutsy, 
also got intel 3945 wifi module, in Gutsy everything worked properly, on Hardy it doesn't :( Made a clean installation, fully formated hard disk and installed from "desktop installation disk for 8.04". Totally frustrated because I use this laptop for work. Please help somebody. (tried to make [this]("http://ubuntuforums.org/showpost.php?p=4871564&postcount=18") and also some other stuff)

---

### Post by gryzzly on 2008-05-11
bump

---

### Post by Zorael on 2008-05-11
You could try compiling your own driver. I had some success with this one on the 2.6.24-16 kernel: [http://www.orbit-lab.org/kernel/compat-wireless-2.6/2008/05/compat-wireless-2008-05-07.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2008/05/compat-wireless-2008-05-07.tar.bz2).

Instructions over here: [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download).
> [SIZE="4"]**Building and installing**[/SIZE]

[SIZE="4"]Extract:[/SIZE]
Extract the content of the package:
```
tar jxvf compat-wireless-$(date -I).tar.bz2
```

[SIZE="4"]Build:[/SIZE]
Build the latest Linux wireless subsystem:

```
cd compat-wireless-$(date -I)
make
```

[SIZE="4"]Install:[/SIZE]
We use the updates/ directory so your distribution's drivers are left intact.
```
sudo make install
```

[SIZE="4"]Uninstall:[/SIZE]
This nukes our changes to updates/ so you can go back to using your distribution's supported drivers.
```
sudo make uninstall
```

[SIZE="4"]Unload:[/SIZE]
Since you might be replacing your old mac80211 drivers you should first try to unload all existing mac80211 and related drivers. Note also that broadcom, zydas, and atheros devices have old legacy drivers which you need to be sure are removed first. We provide a mechanism to unload all old and legacy drivers first so you should run to be sure:
```
sudo make unload
```

[SIZE="4"]Load:[/SIZE]
If you know what module you need you can simply load the module using modprobe. If you simply are not sure you can use:
```
sudo make load
```

Note that this will run make unload first, just in case you forgot. This unloads your old wireless subsystem drivers and loads the new shiny ones. For example if ipw3945 and its proprietary daemon are found it'll be stopped and the module unloaded and then iwl3945 will be loaded. If you are simply upgrading a mac80211 driver this will unload the old one and the old mac80211 drivers and load the new ones.

---

### Post by gryzzly on 2008-05-12
> **Zorael said:**
> You could try compiling your own driver. I had some success with this one on the 2.6.24-16 kernel: [http://www.orbit-lab.org/kernel/compat-wireless-2.6/2008/05/compat-wireless-2008-05-07.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/2008/05/compat-wireless-2008-05-07.tar.bz2).

Instructions over here: [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download).

Thank you for response. Tried that solution - really straightforward explanation is in there. Thanks for link. Unfortunately it didn't help me :( Even thou all commands and buildings passed smoothly. 

Here are output for "dmesg | grep -i iwl" and for "dmesg | grep 3945" (it's the same):
```

misha@ubuntu-laptop:~$ dmesg | grep -i iwl

[   35.696895] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   35.696900] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   35.697064] iwl3945: Detected Intel Wireless WiFi Link 3945BG
[   35.802032] iwl3945: Tunable channels: 13 802.11bg, 0 802.11a channels
[   35.821081] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   45.235508] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[   45.235521] iwl3945: Error Reply type 0x00000005 cmd REPLY_SCAN_CMD (0x80) seq 0x4418 ser 0x0000004B
[   46.307122] iwl3945: Can't stop Rx DMA.
```

And here is is output for "iwconfig":
```
misha@ubuntu-laptop:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated  
          Tx-Power=15 dBm  
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.
```

This is all after installation of this thing you linked to. But actually I think it's very similar to what I have seen before that :(

---

### Post by lnogueir on 2008-05-14
I found a how-to ipw and the new kernel at the end of this site [http://www.klamstwo.org/evad/archives/59](http://www.klamstwo.org/evad/archives/59)

Can someone do a how-to for Hardy???

Thanks!

---


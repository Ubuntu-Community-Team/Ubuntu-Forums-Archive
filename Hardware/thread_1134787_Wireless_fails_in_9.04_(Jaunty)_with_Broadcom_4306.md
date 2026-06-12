---
title: "Wireless fails in 9.04 (Jaunty) with Broadcom 4306"
date: 2009-04-23
forum: Hardware
---

### Post by bpat1434 on 2009-04-23
I've just did a clean install of Jaunty on my HP notebook.  The notebook has a Broadcom BCM4306 wireless card which worked prior to my reinstall.

So I installed Jaunty, hard-wired the notebook and updated then upgraded.  Then I rebooted, went into the Hardware manager and enabled the B43-fwcutter driver (and the nVidia 96 driver) and then rebooted again.  The driver loads fine (no error messages in dmesg) and I can see the MAC address in ifconfig.  

Problem is that it doesn't "see" any wireless networks, and if I tell it to connect to my hidden network and give it the correct WPA key, it just churns trying to connect but ultimately failing.

Anyone know of any issues with 9.04 and Broadcom's restricted driver?  Like I said, previous versions didn't have this issue (or if it did, when I rebooted the issues resolved themselves).

Thanks for any help you can offer.

```
**~$ uname -a**
Linux bpat-laptop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

**~$ ifconfig**
wlan0     Link encap:Ethernet  HWaddr 00:90:4b:a3:2d:80  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**~$ dmesg**
[   18.321069] b43-phy0: Broadcom 4306 WLAN found
[   18.369034] phy0: Selected rate control algorithm 'pid'
[color=blue][   18.558815] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ][/color]
[   18.574331] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 21
[   18.574337] Intel ICH 0000:00:06.0: PCI INT A -> Link[LACI] -> GSI 21 (level, low) -> IRQ 21
[   18.574529] Intel ICH 0000:00:06.0: setting latency timer to 64
[   18.684029] AC'97 0 analog subsections not ready
[   19.036038] floppy0: no floppy controllers found
[   19.252039] intel8x0_measure_ac97_clock: measured 55431 usecs
[   19.252043] intel8x0: clocking to 48000
[   19.395061] lp0: using parport0 (interrupt-driven).
[   19.476113] Adding 2963952k swap on /dev/sda5.  Priority:-1 extents:1 across:2963952k
[   20.016325] EXT3 FS on sda1, internal journal
[   21.173809] type=1505 audit(1240542822.227:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2001
[   21.220505] type=1505 audit(1240542822.275:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2005
[   21.220671] type=1505 audit(1240542822.275:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2005
[   21.220720] type=1505 audit(1240542822.275:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2005
[   21.220767] type=1505 audit(1240542822.275:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2005
[   21.355406] type=1505 audit(1240542822.407:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2010
[   21.355639] type=1505 audit(1240542822.407:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2010
[   21.385769] type=1505 audit(1240542822.439:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2014
[   25.042615] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.042618] Bluetooth: BNEP filters: protocol multicast
[   25.099027] Bridge firewalling registered
[   27.239111] agpgart-amd64 0000:00:00.0: AGP 2.0 bridge
[   27.239131] agpgart-amd64 0000:00:00.0: putting AGP V2 device into 4x mode
[   27.239180] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   30.945079] eth0: link down
[   30.945381] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.092265] input: b43-phy0 as /devices/virtual/input/input9
[color=blue][   31.156046] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   31.296580] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   31.332545] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   31.458625] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   31.604048] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   31.685906] Registered led device: b43-phy0::tx
[   31.685924] Registered led device: b43-phy0::rx
[   31.685940] Registered led device: b43-phy0::radio
[   31.720043] b43-phy0: Radio turned on by software
[   31.720370] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/color]
[   74.704115] ppdev0: registered pardevice
[   74.752049] ppdev0: unregistered pardevice
[   76.147180] ppdev0: registered pardevice
[   76.201096] ppdev0: unregistered pardevice
[   76.969283] ppdev0: registered pardevice
[   77.021693] ppdev0: unregistered pardevice
[  174.370888] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
[  174.371454] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  185.288032] eth0: no IPv6 routers present

**~$ lscpi | grep "Wireless"**
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

[color=green]**UPDATE:**[/color] *This has been solved (at least for me).  You can read my solution in [post #7](http://ubuntuforums.org/showpost.php?p=7138599&postcount=7)*

---

### Post by Ayuthia on 2009-04-23
Have you tried taking it out of hidden mode to see if you can connect?

---

### Post by bpat1434 on 2009-04-24
There are other wireless networks around me (like 4 or 5) some hidden, some not, some encrypted, other not.  No wireless networks are being listed and the "strength" of my hidden one is 0.

---

### Post by switch10 on 2009-04-24
glad to know this.

---

### Post by TheStudent on 2009-04-24
I have a HP Compaq Presario R3000
I'm having the same problem.

8.10 worked great but a clean install of 9.04 shows no wireless networks.

In some digging it should I'm not claimed or unclaimed but disabled. How do I enable it? (and I don't mean the little check box that is enabled it just finds no networks)

I have 3-4 wireless networks around me broadcasting. In windows on the same computer it works fine. 

I'm sure my wireless card is turned on as in windows its workign fine.

---

### Post by WhoDoTech on 2009-04-24
I have the same problem.

I have a HP Pavilion 6005us that was running 8.10 with no problems what so ever including wireless.  I know everything was working just fine until I did the upgrade to 9.04 last night.  After the update was finished I did get en error about fwcutter but I didn't know what that was.  It was too late anyhow as the the upgrade was finished.

I did find this site [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) and I believe the problem has to do with the firmware.  

Here is my machine is showing:

llspci -vnn | grep 14e4
Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

According to the docs on the site above 14e4:4320 is not supported.

I can't afford to be without my laptop as I removed Windows sometime ago.  Hopefully they will be a fix for it soon as this is a VERY popular wireless card.  I as going to have to go back to 8.10 until then.

---

### Post by bpat1434 on 2009-04-24
Glad to see I'm not the only one having issues with it.  I'll keep digging some this weekend, but hopefully there's something.

I did notice that in looking through all my logs, I found only one possible explanation:

```
Apr 23 23:08:46 bpat-laptop firmware.sh[3548]: Cannot find  firmware file 'b43/ucode5.fw'
Apr 23 23:08:46 bpat-laptop firmware.sh[3574]: Cannot find  firmware file 'b43/ucode5.fw'
Apr 23 23:14:37 bpat-laptop hp: io/hpmud/pp.c 627: unable to read device-id ret=-1 
Apr 23 23:14:38 bpat-laptop python: io/hpmud/pp.c 627: unable to read device-id ret=-1 
```

So I googled the above, and read through [this thread at Linux forums](http://www.linuxforums.org/forum/wireless-internet/131370-debian-lenny-problems-getting-wireless-work.html).  So I said well why not... and just ran
```
~$ sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```
and it ran, then I checked for wireless networks and voila! I can now see wireless networks.  I'm not sure what it did, but it works!

As a side note, I did notice that when the restricted driver was activated, it never did the "Do you want to extract the firmware" confirmation like 8.10 did.  So possibly this is the issue.

---

### Post by affan00 on 2009-04-24
Hi,

I had the same problem. I tried your solution and it worked. But after some time it disconnects. And then connects again. And again disconnects. Sometimes forever until you reboot or repeat the whole process. 

I would appreciate if you can post any further insight in this thread

Thanks!

---

### Post by ZaHACKieL on 2009-04-25
I have the same problem. My machine is a Dell Studio 1735 laptop. I made the update from Ubuntu 8.10 to 9.04 yesterday. 

I also have a Broadcom. Mine is BCM4322. Wireless networks are not showing either.

The weird part is that in "Hardware drivers" the driver is active but says: "it's not currently in use".

If I boot the Jaunty using the 2.6.27-11 kernel, the wifi works fine, just as it did in Intrepid.

Anyone? 

Thanx!

---

### Post by chopeen on 2009-04-25
Same problem here (ASUS A6RP-AP069).

Installing the b43-fwcutter package (use Synaptic or apt-get to do it) and rebooting the computer solved the problem.

---

### Post by StuartN on 2009-04-25
My wireless is Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
and Hardware Drivers gave me a choice of either b43 or wl, and I picked the wl driver - Broadcom's own Linux driver. I had no problems at all connecting to WPA on a visible access point, but I have not tried hidden. (I gave up trying to connect to hidden in 8.04)

---

### Post by TheStudent on 2009-04-25
I was runnning 9.04 RC I updated to 9.04 with the latest updates and my wireless now works. :-)

I have a compaq R3000

---

### Post by eatberrys on 2009-04-25
Hi all,

Im now runing 9.04 on a Gateway mx6445 when I first upgraded the wireless didnt work. I ran the suggested command rebooted and it's all good.

---

### Post by ZaHACKieL on 2009-04-25
Something weird happened. As I said before, even when Jaunty had the wireless drivers active, they where not in use so you couldn't see the wireless networks but the wifi worked fine booting tje Jaunty from the 2.6.27-11 Kernel. Well, I was using the wifi there in the 27-11 kernel and when I returned to 2.6.28-11 kernel, just out of nowhere, the wifi started to work fine and it has been working fine since then.

Anyone had the same experience?

---

### Post by kruzztee on 2009-04-27
I managed to make my PCI Linksys WMP54G with Broadcom 4306 Rev 3.0 running in my Jaunty installation, just by installing B43 fw-cutter on a wired connection. 
I rebooted the system and my card detected access points around my house with good power reception.

Surely this installation is flawless compared to make my WMP54G workin in 8.10.

---

### Post by groovomata on 2009-04-27
I, unfortunately, can't seem to get my wireless to work. It did work correctly immediately after I installed Jaunty, however, it stopped working yesterday. I tried doing the: > sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh command, however my wireless card still sees no wireless networks (of which there are many). My card is the Broadcom BCM4311 and I have two proprietary drivers available. One is the Broadcom B43 Wireless driver (which reads as active and currently in use) the other is the Broadcom STA wireless Driver. I'll try the other driver and report back.
Regards,
Erik.

---

### Post by groovomata on 2009-04-27
I removed the Broadcom B43 Wireless driver and sure enough, the usr/share/b43-fwcutter folder and firmware disappeared. I then enabled the other driver available, the Broadcom STA wireless driver, and unfortunately no joy. I still am unable to detect any wireless networks.

---

### Post by groovomata on 2009-04-28
Looking at some other threads I noticed a useful looking page on troubleshooting wireless connections. It may help:
[https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html](https://help.ubuntu.com/9.04/internet/C/troubleshooting-wireless.html)
I'll give it a go when I get home from work and report back.
All the best,
Erik.

---

### Post by aloyr on 2009-05-03
I upgraded my Kubuntu from Intrepid to Jaunty on my HP dv9010us laptop and the wireless stopped working.

I tried removing the b43-fwcutter package and activating the Broadcom STA proprietary driver, but that did not work.

Since jockey-kde didn't disable the STA driver I then had to install the jockey-gtk to get that driver disabled. After that, I installed the b43-fwcutter again, ran the command suggested on post #7, rebooted and my wireless is finally working under Jaunty!!!

In hindsight, finding this post sooner and just running the command would have saved me a bunch of time if I had switched to geico...

---

### Post by jkjk222 on 2009-05-05
I have downloaded b43-fwcutter-008.tar.bz2.....NOW, how do I install it, to get my BCM4306 controller to work?  Thanks

---

### Post by groovomata on 2009-05-05
Wouldn't you simply run the command > sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh from post seven?

---

### Post by chopeen on 2009-05-06
> **jkjk222 said:**
> I have downloaded b43-fwcutter-008.tar.bz2.....NOW, how do I install it, to get my BCM4306 controller to work?  Thanks

You don't have to download it. Just use Synaptic to install it.

---

### Post by depaulmatthew on 2009-05-06
> **ZaHACKieL said:**
> Something weird happened. As I said before, even when Jaunty had the wireless drivers active, they where not in use so you couldn't see the wireless networks but the wifi worked fine booting tje Jaunty from the 2.6.27-11 Kernel. Well, I was using the wifi there in the 27-11 kernel and when I returned to 2.6.28-11 kernel, just out of nowhere, the wifi started to work fine and it has been working fine since then.

Anyone had the same experience?


The same happened with me too. Weird indeed. Any insights on this?:confused:

---

### Post by banduan on 2009-05-07
I have a similar issue.

When I first upgraded to Jaunty it was working fine.
Then after the last update the wireless did not work.

I've installed b43-fwcutter, and carried out the suggestion in post 7, and it did not work.
Hardware drivers does not list b43 as a driver, the only one there is the Broadcom STA driver.

Help much appreciated! This is just one of a series of really bad experiences in Jaunty.

---

### Post by groovomata on 2009-05-09
My issue is that my Dell Inspiron 6400, can only connect to my wireless network immediately after a boot, suspend or hibernation and then it will invariably lose that connection after a few minutes. Every time. I can see wireless networks with the Broadcom BCM4311 fwcutter driver installed, and the wireless network indicator light is on. If I use the Broadcom STA driver then I don't see any networks and my wireless indicator light doesn't go on. So I'm pretty much stuck with the Broadcom BCM4311 driver. Anyhow, I posted a launchpad bug report: [HTML]https://bugs.launchpad.net/ubuntu/+bug/373791[/HTML]
Regards,
Erik.

---

### Post by cmo1976 on 2009-05-12
The guidance in the link in the quoted text worked for me.  So far my wireless card is working without a hitch.

Thanks!

I have the Broadcom 4306 wireless card, installed on an HP Pavillion zv5000


> **WhoDoTech said:**
> I have the same problem.

I have a HP Pavilion 6005us that was running 8.10 with no problems what so ever including wireless.  I know everything was working just fine until I did the upgrade to 9.04 last night.  After the update was finished I did get en error about fwcutter but I didn't know what that was.  It was too late anyhow as the the upgrade was finished.

I did find this site [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) and I believe the problem has to do with the firmware.  

Here is my machine is showing:

llspci -vnn | grep 14e4
Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

According to the docs on the site above 14e4:4320 is not supported.

I can't afford to be without my laptop as I removed Windows sometime ago.  Hopefully they will be a fix for it soon as this is a VERY popular wireless card.  I as going to have to go back to 8.10 until then.

---

### Post by groovomata on 2009-06-01
I am currently typing this note using a wireless connection. After I was unable to get wireless to work with ubuntu 9.04, I got paranoid that my wireless adapter was no longer working and decided to see if it would work if I install Windows Vista on my computer. Lo and behold, it did not, but while digging around in vista, one dialogue box informed me that my card was not enabled, and indeed the little wireless light was not lit in vista. Once I enabled it, wireless worked fine in vista. So then I wiped out vista and re-installed Jaunty and voila! My wireless worked. I very much prefer ubuntu over Windows, but I do wish in all of the different outputs of various commands that I pored over, one of them had simply said that my wireless card was not enabled, afterall, the little wireless light was on the whole time in ubuntu. How was I to know?
Anyways, I'm happy to report that my wireless now works fine!

---

### Post by Cuppa-Chino on 2009-06-18
> **cmo1976 said:**
> The guidance in the link in the quoted text worked for me.  So far my wireless card is working without a hitch.

Thanks!

I have the Broadcom 4306 wireless card, installed on an HP Pavillion zv5000

how can I force the non-legacy driver as I have this card:

```
$ lspci -vnn | grep 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
$ dmesg | grep Broadcom
[    3.676982] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0f:1f:0b:d4:00
[   11.629587] b43legacy-phy0: Broadcom 4306 WLAN found
[   11.842967] Broadcom 43xx-legacy driver loaded [ Features: PLRID, Firmware-ID: FW10 ]

```

it does rev02 but has the rev03,04 id of 14e4:4320 

any ideas how I can force the "non-legacy"

---

### Post by Ayuthia on 2009-06-18
> **Cuppa-Chino said:**
> how can I force the non-legacy driver as I have this card:

```
$ lspci -vnn | grep 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
$ dmesg | grep Broadcom
[    3.676982] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0f:1f:0b:d4:00
[   11.629587] b43legacy-phy0: Broadcom 4306 WLAN found
[   11.842967] Broadcom 43xx-legacy driver loaded [ Features: PLRID, Firmware-ID: FW10 ]

```

it does rev02 but has the rev03,04 id of 14e4:4320 

any ideas how I can force the "non-legacy"

The rev02 version of the 4306 card uses the b43legacy module.  I think that if you want to use the b43 module, it would be a matter of doing the following:
```
sudo modprobe -r b43legacy b44 b43 ssb
sudo modprobe b44
sudo modprobe b43
```
However, I don't think that your card will work with the b43 module.

---

### Post by xileBurela on 2009-08-31
> **TheStudent said:**
> I was runnning 9.04 RC I updated to 9.04 with the latest updates and my wireless now works. :-)

I have a compaq R3000

I have the same laptop and I can't use my wireless card. It doesn't recognize any wireless network around me.  I've already installed the fwcutter and i checked the driver and is shown as active. I really don't know which is the problem

---

### Post by MugOTea on 2009-09-15
Using Jaunty on a HP (compaq 6720s) w/ Broadcomm Wireless - I had the same problem, wireless was installed (using Windows Wireless Drivers) but no netwrks were visible.

Did the following:

> **chopeen said:**
> Same problem here (ASUS A6RP-AP069).

Installing the b43-fwcutter package (use Synaptic or apt-get to do it) and rebooting the computer solved the problem.

Then, ran the following command as suggested:

> sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

Restarted the laptop and now its found all my access points and I no longer require the USB wireless dongle. YAY :P

---

### Post by kcox5342 on 2009-10-11
I found this thread after installing a new HD and a fresh install of Jaunty, which I had just reinstalled on the OLD hd on Friday.  Last time, wireless worked - I had to let it do the first round of Update Manager updates before a driver would show up in the Hardware Drivers, but then it worked.  This time it didn't and it frustrated me to no end for a few minutes before I realized...

On my Acer Aspire 3004WLMI, in Jaunty, the WiFi light is on whether or not the switch is on.  In previous versions, when you hit the physical button on the front, the light would go off when it was disabled.  This is confusing, and possibly a bug.

---

### Post by Sun3160 on 2009-10-30
I have an old Presario 2100 with a Broadcom 4306 running 9.10. 

At first I installed b43-fwcutter through the Synaptic Package Manager over standard ethernet, and it got my wireless up and running.  But no matter how close I got to my router or access point, it was only reporting (and I was barely getting) 1Mb/s.  

I tried running the command in post #7 and now I'm getting much higher speeds when close to the wireless points, and slower speeds when further away.  

It's a little cryptic at times, but I'm *very* pleased with the online assistance available for Ubuntu, thanks, all.  :)

---


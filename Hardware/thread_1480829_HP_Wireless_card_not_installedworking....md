---
title: "HP Wireless card not installed/working..."
date: 2010-05-12
forum: Hardware
---

### Post by myromance123 on 2010-05-12
Hey guys,

 Alright, to the main issue. I have a:
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

```

 I'm not sure if that means that the wireless part of my laptop is separate from my ethernet section. Nonetheless my issue is that I have no wireless capability on this laptop.

 Since it's a HP dv3500, the wireless enabler button is not really a button but a sort of touch screen item (lighted). Its currently red, which means that it is disabled. Pressing it does not activate it.

Unlike the standard Ubuntu 10.04 which has a network configuration icon in the top right of the menu, I've discovered Ubuntu Studio doesn't have this. So I went to System -> Administration -> Network. All there is there is General, DNS and Hosts. I believe its missing a Connections tab (as shown in the Help).

Normally in 10.04 I would just right click that top right network icon and choose from the available wireless connections (on this exact same laptop). I believe the problem here in Ubuntu Studio 10.04 is that my wireless card is not installed... 

ifconfig gives me this:
```
yusuf@yusuf:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:81:66:75:3e  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fe66:753e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:141959 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99553 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:203383621 (203.3 MB)  TX bytes:8272986 (8.2 MB)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:145 errors:0 dropped:0 overruns:0 frame:0
          TX packets:145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11968 (11.9 KB)  TX bytes:11968 (11.9 KB)

```

Its missing a wlan0 isn't it?

---

### Post by pytheas22 on 2010-05-12
Yes, the problem is that no driver is claiming the wireless card.  That's strange, because you have an Intel wireless chipset, which should work well out-of-the-box using the iwlagn driver, which ships with Ubuntu.  If you could please post the following commands, it should help figure out what might be going wrong:
```

dmesg | grep -i iwl -i wlan
modinfo iwlagn
cat /etc/issue
uname -rm
lshw -C Network
ifconfig
```

---

### Post by myromance123 on 2010-05-12
Thanks for replying so fast, pytheas22!

 Heres the information.
```
yusuf@yusuf:~$ dmesg | grep -i iwl -i wlan
grep: wlan: No such file or directory

```
```
yusuf@yusuf:~$ modinfo iwlagn
filename:       /lib/modules/2.6.32-22-preempt/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        1.3.27k
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-2.ucode
firmware:       iwlwifi-6050-4.ucode
firmware:       iwlwifi-6000-4.ucode
srcversion:     9B8B8B62434B92B6793FD7A
alias:          pci:v00008086d00000084sv*sd*bc*sc*i*
alias:          pci:v00008086d00000083sv*sd*bc*sc*i*
alias:          pci:v00008086d00000089sv*sd*bc*sc*i*
alias:          pci:v00008086d00000088sv*sd*bc*sc*i*
alias:          pci:v00008086d00000087sv*sd*bc*sc*i*
alias:          pci:v00008086d00000086sv*sd*bc*sc*i*
alias:          pci:v00008086d00004239sv*sd*bc*sc*i*
alias:          pci:v00008086d00004238sv*sd*bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000008Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000008Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004237sv*sd*bc*sc*i*
alias:          pci:v00008086d00004236sv*sd*bc*sc*i*
alias:          pci:v00008086d00004235sv*sd*bc*sc*i*
alias:          pci:v00008086d00004232sv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,mac80211,cfg80211
vermagic:       2.6.32-22-preempt SMP preempt mod_unload modversions 
parm:           swcrypto50:using software crypto engine (default 0 [hardware])
 (bool)
parm:           queues_num50:number of hw queues in 50xx series (int)
parm:           11n_disable50:disable 50XX 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm:           fw_restart50:restart firmware in case of error (int)
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart4965:restart firmware in case of error (int)

```
```
yusuf@yusuf:~$ cat /etc/issue
Ubuntu 10.04 LTS \n \l


```

```
yusuf@yusuf:~$ uname -rm
2.6.32-22-preempt x86_64

```

```
yusuf@yusuf:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:81:66:75:3e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=10.0.0.4 latency=0 multicast=yes
       resources: irq:28 ioport:3000(size=256) memory:d8200000-d8200fff memory:d3000000-d300ffff(prefetchable) memory:d3020000-d303ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fa:ad:fd:20
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:d7100000-d7101fff

```

I already did ifconfig above but here it is again:
```
yusuf@yusuf:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:81:66:75:3e  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fe66:753e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:177014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:122620 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:256577177 (256.5 MB)  TX bytes:10298456 (10.2 MB)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)


```

This doesn't look pleasing to the eyes.
> *-network DISABLED


---

### Post by pytheas22 on 2010-05-12
Thanks for the output.  It does look like the device is being claimed properly by the iwlagn driver, so that's good.  The "DISABLED" bit is probably the result either of the radio being turned off, or of an issue with the device's firmware.

One of the commands that I asked you to run was incorrect (sorry about that--it was late and I made a typo).  Could you please post the output of:
```

dmesg | grep -e iwl -e wlan -ie firmware -ie radio
```

That should let us know where exactly the issue lies.

---

### Post by myromance123 on 2010-05-14
Thanks pytheas22 for assisting me :)

Here's what that gives me.

```
yusuf@yusuf:~$ dmesg | grep -e iwl -e wlan -ie firmware -ie radio
[    9.853049] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    9.853053] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    9.853191] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.853221] iwlagn 0000:03:00.0: setting latency timer to 64
[    9.853318] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[    9.894157] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.894245] iwlagn 0000:03:00.0: irq 30 for MSI/MSI-X
[   10.229965] phy0: Selected rate control algorithm 'iwl-agn-rs'
```

---

### Post by pytheas22 on 2010-05-14
Hmmm, dmesg doesn't mention anything about the radio on the wireless card being turned off.  Perhaps the problem is as simple as the device being down.  What output do you get from these commands (in this order):
```

sudo ifconfig wlan0 up
sudo iwlist scan
dmesg | grep -ie wlan -ie iwlagn
```

And are you then able to see networks and connect?

---

### Post by myromance123 on 2010-05-14
Well it fails at the beginning. 

```
yusuf@yusuf:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132
```
```

yusuf@yusuf:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


```
```
yusuf@yusuf:~$ dmesg | grep -ie wlan -ie iwlagn
[    9.853049] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    9.853053] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    9.853191] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.853221] iwlagn 0000:03:00.0: setting latency timer to 64
[    9.853318] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[    9.894157] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    9.894245] iwlagn 0000:03:00.0: irq 30 for MSI/MSI-X

```

---

### Post by pytheas22 on 2010-05-14
The bit about "SIOCSIFFLAGS: Unknown error 132" is useful.  According to this [bug report]("http://bugs.gentoo.org/298290"), it has to do with the wireless radio being shut off.  What is the output of:

```
rfkill list
```

And if you type:
```

sudo rfkill unblock all
```

are you then able to bring the interface up with "sudo ifconfig wlan0 up" without getting an error?

Also, on some computers BIOS will have different options regarding the wireless card radio.  You may want to check on this and play with those settings to see if they will either force your radio to be on all the time, or all the wireless button on your laptop to start working again.

---

### Post by myromance123 on 2010-05-14
Due to this being a dv3500 hp laptop and its poorly designed state, I remembered something.

 Pressing the wireless "button" twice will enable it (Once disables it. NOT turn it off). BUT it still stayed red. So I retried doing this:
```
yusuf@yusuf:~$ sudo ifconfig wlan0 up
```
Its now blue indicating that its on.
 I am unsure if this will still work after a restart, as I have read else where that it normally needs to be redone at each start up...

 I am going to give it a go first.

PS: Poorly designed as in the keyboard letter color is almost identical to the keys color itself, making it invisible in darkly lit places. Also, the new touchscreen like buttons have issues with knowing when to stop receiving input. Most annoying with the Volume control.

EDIT: Just to note. I can't find a way to connect to any of my wireless networks. Since this is Ubuntu Studio 10.04, it doesn't have Network icon on the top right. Opening the Network manager does not help, since it has no Wireless settings/tab.

---

### Post by myromance123 on 2010-05-14
Alright after restarting, my wireless is still on which is great news!

Thanks pytheas22 for assisting me :)

Now the only issue is that I can't connect to my wireless networks. Ubuntu Studio doesn't come with a WiFi network manager for some odd reason. Seems it didn't come with it in the past either.

So I read [here]("http://ubuntuforums.org/showthread.php?t=1442144") that I should do this to install the normal Ubuntu manager:
```
sudo apt-get install network-manager
```

I'm still unable to find the Network Manager icon in the top right. Adding the Network Manager through Add to Panel is not helpful. It gives me the same information, only regarding eth0.

So I tried a wireless search through Ubuntu Software Center.
I then downloaded Wifi Radar.

Wifi Radar detects the networks around me which is a step forward.
Only thing is, it WONT connect. It stays stuck at "Acquiring IP Address (DHCP)" forever.

 This same laptop, with this same wireless network never had an issue using standard Ubuntu 9.10 and 10.04. I really want to make this work out with Ubuntu Studio 10.04, **without** having to resort to installing Ubuntu 10.04 from scratch and then installing Studio in that installation.

---

### Post by pytheas22 on 2010-05-14
Good to hear you can see networks now; that's progress!

I've never used Ubuntu Studio, but if it uses Gnome as its desktop environment, you probably need to install the package network-manager-gnome, and not just network-manager, to get NetworkManager working.  You may also need to start the applet manually by typing:
```

nm-applet
```

Another thing to try is installing wicd, another connection manager that may work better than wifi radar.  You can install wicd with:
```

sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu.

---

### Post by myromance123 on 2010-05-15
I forgot to add the information last night.
Sadly, I did and still am trying to get Wicd to work. It coughs up where WiFi Radar does. At obtaining the IP address.

 Trying to connect wireless messes up the laptops network connecting capabilities. After one attempt, eth0 becomes unstable. Connects and may disconnect at random. If I turn off Firefox for example, it may reconnect. Other times not.

Very odd.

```
yusuf@yusuf:~$ nm-applet
An instance of nm-applet is already running.

** (nm-applet:2215): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.
```

I already have the gnome-network-manager installed. Not sure where to go from here.

 Thanks pytheas22 :)

---

### Post by pytheas22 on 2010-05-15
Are you positive the notification area is visible?  Do you see any other icons there?  On my system, there's an applet for setting the keyboard layout (its icon is the letters "USA"), as well as an icon for Dropbox, in the notification area.

It could also be worth trying to reinstall NetworkManager from scratch, just in case that helps.  You can purge it by typing:
```

sudo apt-get remove --purge network-manager
```

Then reinstall with:
```

sudo apt-get install network-manager-gnome
```

Also, another solution would be to figure out how to make the connection work without relying on NetworkManager.  If you could please post the output of:

```
sudo iwlist scan
```

and tell me the name of your network, we could try connecting from the command line.  If that works, we can probably figure out how to get it to work in wicd and wifi radar as well.

Sorry things are not going as well as we'd like, but thanks for your patience!

---

### Post by myromance123 on 2010-05-16
Hey pytheas22,

 some good news. I'm finally connected to my wireless network!
Through Wicd nonetheless.
> Are you positive the notification area is visible?
Yep positive. Guess what? After purging the network manager, the icon appears. Restarting/Reinstalling makes it disappear. Its not functioning at all so I reinstalled it like you said. It then disappears. Bringing up the Network Manager through Add to Panel, is something different...

 The step that did fix my problem with obtaining the IP I believe was most likely purging the network manager, then reinstalling it.
EDIT: Do not reinstall it. I confirm that without the network manager, only then does my wireless card work.

 A great big thanks to you pytheas22 :)
I'll monitor if anything changes, but I think I'm good to go now!

 You rock mate :D

---

### Post by pytheas22 on 2010-05-16
Good to hear you're online :)

---

### Post by kaig20 on 2010-05-16
Hey do you think you could check out my thread about pretty much the same thing but I went through everything you said but came up with very similar results but they don't work
[http://ubuntuforums.org/showthread.php?p=9310541#post9310541:confused:](http://ubuntuforums.org/showthread.php?p=9310541#post9310541:confused:)

---

### Post by big wody on 2010-06-01
Had the same problem getting my hp dv2500 laptop to connect to wireless networks after installing ubuntu studio 10.04. Removing the network manager and then restarting my computer worked as well for me.

---


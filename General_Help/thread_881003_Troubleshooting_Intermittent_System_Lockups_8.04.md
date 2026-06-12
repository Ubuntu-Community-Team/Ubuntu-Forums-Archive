---
title: "Troubleshooting Intermittent System Lockups 8.04?"
date: 2008-08-05
forum: General Help
---

### Post by jza103 on 2008-08-05
I've been running Ubuntu 8.04 on my Dell 8600 Inspiron  shortly after it was released and never encountered these intermittent crashes that I started experiencing over the last couple of months.  The crashes start off by an unresponsive cursor, and then I notice the wireless connection disassociates.  The cursor then becomes intermittently responsive and then eventually just halts completely.  I have to physically power off the laptop to get it to come back.

I ran a memory test for about 10 hours and it didn't return any errors.  I also ran a smartctl test on the hard drive and it came back without errors.  I started to mix things up a bit, so I switched to KDE and then XFCE but I had still had the identical problem.

I did a fresh install of 8.04 thinking that something I did may have broken the system.  I installed ths OS while plugged in via ethernet and after I browsed around a bit here and there without an issue.  It wasn't until I tried to install the drivers for the wireless card that the system crashed(I used the restricted driver manager to install b43-fwcutter).  The system locked the instant the driver was installed.  I hadn't even tried to associate to an AP yet.  

I did a hard reset on the laptop(while still connected via ethernet) and was able to login and browse without issue.  I then tried to switch to Wireless and within a few minutes the system locked up again at approximately 11:21.  I rebooted the system again at 11:24 to obtain the syslogs

Here's the /var/log/messages:

```
Aug  5 11:08:59 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Aug  5 11:09:01 laptop dhcdbd:  dhclient 5469 down (9) but si_code == 0 and releasing==0 !
Aug  5 11:11:45 laptop kernel: [14928.238121] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug  5 11:11:47 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Aug  5 11:11:47 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Aug  5 11:11:47 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Aug  5 11:11:47 laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Aug  5 11:19:48 laptop kernel: [ 7811.536025] printk: 401442 messages suppressed.
Aug  5 11:19:55 laptop kernel: [15654.468176] printk: 621771 messages suppressed.
Aug  5 11:19:58 laptop kernel: [15697.951477] printk: 942196 messages suppressed.
Aug  5 11:20:03 laptop kernel: [ 6294.082845] printk: 439867 messages suppressed.
Aug  5 11:20:08 laptop kernel: [15785.457909] printk: 426544 messages suppressed.
Aug  5 11:20:13 laptop kernel: [15833.969939] printk: 1008268 messages suppressed.
Aug  5 11:20:20 laptop kernel: [15887.988975] printk: 1147219 messages suppressed.
Aug  5 11:20:23 laptop kernel: [15911.129821] printk: 382363 messages suppressed.
Aug  5 11:24:42 laptop syslogd 1.5.0#1ubuntu1: restart.

```

(Notice the huge number of suppressed messages.  I'm not sure what messages they are suppressing)


Here is from /var/log/kern.log

```
Aug  5 11:09:40 laptop kernel: [ 5923.908986] b43-phy0 ERROR: PHY transmission error
Aug  5 11:09:40 laptop kernel: [ 5923.909105] b43-phy0 ERROR: PHY transmission error
Aug  5 11:10:40 laptop kernel: [ 5944.837369] b43-phy0 ERROR: PHY transmission error
Aug  5 11:10:40 laptop kernel: [ 5944.837508] b43-phy0 ERROR: PHY transmission error
Aug  5 11:10:40 laptop kernel: [ 5944.837575] b43-phy0 ERROR: PHY transmission error
Aug  5 11:11:41 laptop kernel: [ 5968.667193] b43-phy0 ERROR: PHY transmission error
Aug  5 11:11:41 laptop kernel: [ 5968.667313] b43-phy0 ERROR: PHY transmission error
Aug  5 11:11:45 laptop kernel: [14928.229712] wlan0: Initial auth_alg=0
Aug  5 11:11:45 laptop kernel: [14928.229749] wlan0: authenticate with AP 00:1e:8c:3d:fe:ed
Aug  5 11:11:45 laptop kernel: [14928.232244] wlan0: RX authentication from 00:1e:8c:3d:fe:ed (alg=0 transaction=2 status=0)
Aug  5 11:11:45 laptop kernel: [14928.232269] wlan0: authenticated
Aug  5 11:11:45 laptop kernel: [14928.232288] wlan0: associate with AP 00:1e:8c:3d:fe:ed
Aug  5 11:11:45 laptop kernel: [14928.236481] wlan0: RX AssocResp from 00:1e:8c:3d:fe:ed (capab=0x411 status=0 aid=3)
Aug  5 11:11:45 laptop kernel: [14928.236507] wlan0: associated
Aug  5 11:11:45 laptop kernel: [14928.236531] wlan0: switched to short barker preamble (BSSID=00:1e:8c:3d:fe:ed)
Aug  5 11:11:45 laptop kernel: [14928.238121] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug  5 11:11:56 laptop kernel: [ 8967.180530] wlan0: no IPv6 routers present
Aug  5 11:12:39 laptop kernel: [14993.835902] b43-phy0 ERROR: PHY transmission error
Aug  5 11:12:39 laptop kernel: [14993.836013] b43-phy0 ERROR: PHY transmission error
Aug  5 11:12:39 laptop kernel: [14993.836076] b43-phy0 ERROR: PHY transmission error
Aug  5 11:13:40 laptop kernel: [ 6031.363517] b43-phy0 ERROR: PHY transmission error
Aug  5 11:13:40 laptop kernel: [ 6031.363640] b43-phy0 ERROR: PHY transmission error
Aug  5 11:14:40 laptop kernel: [ 6061.729110] b43-phy0 ERROR: PHY transmission error
Aug  5 11:14:40 laptop kernel: [ 6061.729235] b43-phy0 ERROR: PHY transmission error
Aug  5 11:15:41 laptop kernel: [ 6088.288464] b43-phy0 ERROR: PHY transmission error
Aug  5 11:15:41 laptop kernel: [ 6088.288586] b43-phy0 ERROR: PHY transmission error
Aug  5 11:16:41 laptop kernel: [15288.713707] b43-phy0 ERROR: PHY transmission error
Aug  5 11:16:41 laptop kernel: [15288.713817] b43-phy0 ERROR: PHY transmission error
Aug  5 11:16:41 laptop kernel: [15288.713881] b43-phy0 ERROR: PHY transmission error
Aug  5 11:17:42 laptop kernel: [ 6145.501146] b43-phy0 ERROR: PHY transmission error
Aug  5 11:17:42 laptop kernel: [ 6145.501270] b43-phy0 ERROR: PHY transmission error
Aug  5 11:18:42 laptop kernel: [ 6171.609568] b43-phy0 ERROR: PHY transmission error
Aug  5 11:18:42 laptop kernel: [ 6171.609693] b43-phy0 ERROR: PHY transmission error
Aug  5 11:18:42 laptop kernel: [ 6171.609760] b43-phy0 ERROR: PHY transmission error
Aug  5 11:18:42 laptop kernel: [ 6171.609807] b43-phy0 ERROR: PHY transmission error
Aug  5 11:19:43 laptop kernel: [ 6225.062029] b43-phy0 ERROR: PHY transmission error
Aug  5 11:19:43 laptop kernel: [ 6225.062420] b43-phy0 ERROR: PHY transmission error
Aug  5 11:19:43 laptop kernel: [ 6225.062490] b43-phy0 ERROR: PHY transmission error
Aug  5 11:19:43 laptop kernel: [ 6225.062555] b43-phy0 ERROR: PHY transmission error
Aug  5 11:19:43 laptop kernel: [ 6225.062621] b43-phy0 ERROR: PHY transmission error
Aug  5 11:19:43 laptop kernel: [ 6225.062686] b43-phy0 ERROR: PHY transmission error
Aug  5 11:19:43 laptop kernel: [ 6225.062753] b43-phy0 ERROR: PHY transmission error
Aug  5 11:19:43 laptop kernel: [ 6225.062819] b43-phy0 ERROR: PHY transmission error
Aug  5 11:19:43 laptop kernel: [ 6225.062889] b43-phy0 ERROR: PHY transmission error
Aug  5 11:19:43 laptop kernel: [ 6225.062956] b43-phy0 ERROR: PHY transmission error
Aug  5 11:19:47 laptop kernel: [ 6236.579901] wlan0: No ProbeResp from current AP 00:1e:8c:3d:fe:ed - assume out of range
Aug  5 11:19:48 laptop kernel: [ 7811.536025] printk: 401442 messages suppressed.
Aug  5 11:19:48 laptop kernel: [ 7811.536044] b43-phy0 ERROR: PHY transmission error
Aug  5 11:19:48 laptop kernel: [ 6250.192872] wlan0: Initial auth_alg=0
Aug  5 11:19:48 laptop kernel: [ 6250.193119] wlan0: authenticate with AP 00:1e:8c:3d:fe:ed
Aug  5 11:19:48 laptop kernel: [ 6250.235818] wlan0: Initial auth_alg=0
Aug  5 11:19:48 laptop kernel: [ 6250.236004] wlan0: authenticate with AP 00:1e:8c:3d:fe:ed
Aug  5 11:19:48 laptop kernel: [ 6250.301323] wlan0: Initial auth_alg=0
Aug  5 11:19:48 laptop kernel: [ 6250.301509] wlan0: authenticate with AP 00:1e:8c:3d:fe:ed
Aug  5 11:19:49 laptop kernel: [ 6250.799939] wlan0: authenticate with AP 00:1e:8c:3d:fe:ed
Aug  5 11:19:49 laptop kernel: [15627.758435] wlan0: authenticate with AP 00:1e:8c:3d:fe:ed
Aug  5 11:19:49 laptop kernel: [15628.376979] wlan0: authentication with AP 00:1e:8c:3d:fe:ed timed out

Aug  5 11:19:55 laptop kernel: [15654.468176] printk: 621771 messages suppressed.
Aug  5 11:19:55 laptop kernel: [15654.468208] b43-phy0 ERROR: PHY transmission error
Aug  5 11:19:58 laptop kernel: [15697.951477] printk: 942196 messages suppressed.
Aug  5 11:19:58 laptop kernel: [15697.951505] b43-phy0 ERROR: PHY transmission error
Aug  5 11:20:03 laptop kernel: [ 6294.082845] printk: 439867 messages suppressed.
Aug  5 11:20:03 laptop kernel: [ 6294.082861] b43-phy0 ERROR: PHY transmission error
Aug  5 11:20:08 laptop kernel: [15785.457909] printk: 426544 messages suppressed.
Aug  5 11:20:08 laptop kernel: [15785.457938] b43-phy0 ERROR: PHY transmission error
Aug  5 11:20:13 laptop kernel: [15833.969939] printk: 1008268 messages suppressed.
Aug  5 11:20:13 laptop kernel: [15833.969967] b43-phy0 ERROR: PHY transmission error
Aug  5 11:20:20 laptop kernel: [15887.988975] printk: 1147219 messages suppressed.
Aug  5 11:20:20 laptop kernel: [15887.989003] b43-phy0 ERROR: PHY transmission error
Aug  5 11:20:23 laptop kernel: [15911.129821] printk: 382363 messages suppressed.
Aug  5 11:20:23 laptop kernel: [15911.129850] b43-phy0 ERROR: PHY transmission error
Aug  5 11:24:42 laptop kernel: Inspecting /boot/System.map-2.6.24-19-generic
Aug  5 11:24:42 laptop kernel: Loaded 27883 symbols from /boot/System.map-2.6.24-19-generic.
Aug  5 11:24:42 laptop kernel: Symbols match kernel version 2.6.24.
Aug  5 11:24:42 laptop kernel: Loaded 18069 symbols from 95 modules.

```

(The large amounts of b43-phy0 ERROR: PHY transmission error seem significant, but I remember seeing a lot of these even before I starting seeing system crashes)

and from lshw:

```
 *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:7d:28:34:27
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```


Kernel Version:

```

uname -a
Linux laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

```

So I'm at a loss on where to go from here.  Anyone have any ideas of what's going on or any other troubleshooting suggestions?

Keep in mind that these problem just started happening a couple of months ago, which lead me to believe it was either some update that's causing this or it's a hardware issue. I did a search on my hardware but it didn't come up with anything that seemed to related to my problem.  


Thanks.

---

### Post by priyank1 on 2008-08-19
Hi,
I am getting the same error with Ubuntu 8.04. Did you able to resolve this?
Thanks
Priyank

---

### Post by James_the_dude on 2008-08-20
I just started experiencing this problem too. I am seeing the same message about "message handler not found /com/redhat...etc...etc...". This bug appears to affect mostly Broadcom 802.11 mini pci express cards, according to some googling. I tried my friends Atheros mini pci express wireless card, which worked great, leading me to believe the the issue has something to do with the b43 driver. The strange thing is that ubuntu 8.04 worked perfectly fine with my Broadcom card right up until... now. I have tried reinstalling 64 and 32 bit ubuntu and xubuntu with the same results (card still not working). Perhaps our cards have just burnt out; I see no other reason why they would spontaneously quit working, and continue to fail after OS re-installations.

---

### Post by jza103 on 2008-08-25
I still haven't figured out problem, but I'm glad I'm not the only one having this issue.  

It's definitely a possibility that the hardware is in the process of dying.  I've been using my work laptop which has Ubnuntu 8.04 and a Broadcom 4311 card using the b43 driver and haven't been able to duplicate the issue.  

At this point, I'm going to try and install Windows XP and see how that works.  This will at least allow me to narrow down the possibilities.

---

### Post by benne on 2008-10-06
I can report that Windows XP has no problems with the wlan card, however my driver has some problems with WPA2 networks. 

I am having the same problems and I am running the same kernel. My card is in my Dell Latitude D505 laptop. Has somebody found a resolution yet?

I would like to add that according to [http://ubuntuforums.org/showthread.php?t=768710](http://ubuntuforums.org/showthread.php?t=768710), ndiswrapper is the solution. I wrote a few lines on how to get it working with this card on my page for Ubuntu 7.10 on d505. You can see it (and access the windows driver) on [http://www.fjall.org/d505/](http://www.fjall.org/d505/)

Hope it helps.

---


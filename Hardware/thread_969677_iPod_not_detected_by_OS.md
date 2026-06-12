---
title: "iPod not detected by OS"
date: 2008-11-03
forum: Hardware
---

### Post by mozuku on 2008-11-03
iPod classic (5th generation)

Ubuntu 7.10 Gutsy

When I plug my iPod into a USB port, the iPod activates and begins charging its battery, but Ubuntu does not seem to detect the presence of the iPod (no icon on desktop, not listed in "Places", nothing under /media, not listed with lsusb).  Also, no notice appears on the iPod warning not to disconnect.  The same problem is apparent in Windows XP and in Ubuntu 8.04 Hardy.

I've reproduced this on two laptops (dual booting Ubuntu and XP), and one desktop (XP only), and also using a different USB cable.  Other USB devices automount as expected (i.e. USB flash stick, external HDD).  An iPod nano (4th generation) also automounts correctly.

I originally loaded the iPod with music in XP on a borrowed laptop.  I subsequently reinstalled Windows on that machine.  I don't think I've ever attempted to mount the iPod in Ubuntu before.

How should I make a start on troubleshooting this?

---
Posts mentioning similar symptoms:
[http://ubuntuforums.org/showthread.php?t=966351]("http://ubuntuforums.org/showthread.php?t=966351")
[http://ubuntuforums.org/showthread.php?t=964952]("http://ubuntuforums.org/showthread.php?t=964952")

---

### Post by linux_tech on 2008-11-03
If usb is the issue, try restarting dbus: ```
sudo /etc/init.d/dbus restart
```
You can also try a different USB port.
Otherwise this may provide more info on ipod software to use such as rythymbox-
[http://ubuntuforums.org/showthread.php?t=658523](http://ubuntuforums.org/showthread.php?t=658523)

---

### Post by mozuku on 2008-11-03
I tried restarting dbus as suggested, but the iPod remains undetected.

```

campbell@obelisk:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

```

Restarting dbus produces the following output in /var/log/messages:

```

Nov  3 22:23:03 obelisk kernel: [ 8630.964000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov  3 22:23:03 obelisk kernel: [ 8631.164000] Failure registering capabilities with primary security module.
Nov  3 22:23:04 obelisk dhcdbd: Started up.
Nov  3 22:23:04 obelisk kernel: [ 8631.952000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Nov  3 22:23:04 obelisk kernel: [ 8631.952000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
Nov  3 22:23:04 obelisk kernel: [ 8631.952000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Nov  3 22:23:06 obelisk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Nov  3 22:23:12 obelisk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Nov  3 22:23:12 obelisk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Nov  3 22:23:12 obelisk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Nov  3 22:23:12 obelisk dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers

```

I tried each of the three USB ports on the laptop but without any success.

Am I correct in thinking that a fifth generation iPod *should* work out of the box in Gutsy?

---

### Post by mozuku on 2008-11-04
I've experimented with connecting the iPod nano which is working and the iPod classic which isn't.

I list the contents of /dev before and after connecting an iPod, then compare the two lists.  When I connect the nano (which is working) I get the following:

```

campbell@obelisk:~$ ls /dev/ > a.tmp 
campbell@obelisk:~$ ls /dev/ > b.tmp 

campbell@obelisk:~$ diff a.tmp b.tmp 
1a2
> 5-1
314a316,317
> sdb
> sdb1
317a321
> sg1
669a674,676
> usbdev5.4_ep00
> usbdev5.4_ep02
> usbdev5.4_ep83
campbell@obelisk:~$ 

```

But when I connect the iPod classic there is no change in /dev.

```

campbell@obelisk:~$ ls /dev/ > a.tmp 
campbell@obelisk:~$ ls /dev/ > b.tmp 

campbell@obelisk:~$ diff a.tmp b.tmp 
campbell@obelisk:~$ 

```

Is it reasonable to assume that there is a hardware fault in the iPod itself, or could this behaviour be due to something in software or firmware?

---

### Post by littleperks on 2008-12-06
I am having this exact same problem.  Any ideas?

---

### Post by mozuku on 2008-12-08
Thank you littleperks, I've been meaning to post an update.

I made an appointment and took my iPod to the Genius Bar at an Apple retail store.  The guy there tried connecting the iPod to a laptop, and also charging it with a power adapter.  According to him the iPod wasn't recognised and it didn't charge, but when I said that I had been able to charge it at home he tried again and said that now it was charging.

His diagnosis was that although there is no visible damage, the iPod's connector socket is probably faulty.  I asked if it would be possible to transfer the iPod's hard disk into a new machine, the answer to which was no.  He gave me the choice of buying another iPod video at 116 GBP, or turning in the defective iPod for a 10% discount on any new iPod.

At some point I might attempt to repair the iPod myself using spare parts, but I've wanted a more free and open source friendly device for a long time - now I have a chance to look for one.

---

### Post by littleperks on 2008-12-09
Thanks for the reply!  You are indeed correct...It is  hardware problem.  I started messing with the plug-in at the bottom of the ipod and pressing it in real hard - and then it would work.  As soon as i let off pressure it quit working.  Sucks but least I know now what the problem is.  

Thanks for your help.

---


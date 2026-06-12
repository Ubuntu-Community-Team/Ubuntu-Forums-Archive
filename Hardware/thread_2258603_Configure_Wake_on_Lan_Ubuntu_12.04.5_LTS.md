---
title: "Configure Wake on Lan Ubuntu 12.04.5 LTS"
date: 2014-12-29
forum: Hardware
---

### Post by Irrationalis on 2014-12-29
Hello, I have installed Ubuntu 12.04.5 LTS on my iMac Intel Core Duo 2006. I am trying to configure Wake on Lan for this machine. Macs do not have BIOS, they use EFI, (when OS X is installed WOL is actually configured solely through the OS) so I can't configure WOL there.   

I have tried many guides including these: [1]("http://guide.ubuntuforums.org/showthread.php?t=1380776") [2]("http://www.linuxquestions.org/questions/linux-networking-3/howto-make-wake-on-lan-wol-work-712283/") [3]("http://ubuntuforums.org/showthread.php?t=234588") [4]("https://help.ubuntu.com/community/WakeOnLan").   
I just can't seem to get it to work. I can see that the network switch light is on, even when the machine is not, but to no avail.  

Ethtool:
```
Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: No
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pg
    Wake-on: d
    Current message level: 0x000000ff (255)
                   drv probe link timer ifdown ifup rx_err tx_err
    Link detected: yes


```

---

### Post by tgalati4 on 2014-12-29
Turn "d" into "g":

> 	Supports Wake-on: g
	Wake-on: g


---

### Post by Irrationalis on 2014-12-29
If I run,
```
sudo ethtool -s eth0 wol g
```

it does set it to g, but wol is reset to d after a reboot. What is the preferred method of keeping it at g?

---

### Post by tgalati4 on 2014-12-30
Put that line in /etc/rc.local above "exit 0".  Some network cards store the WoL value.  Yours does not, so you need to run that command at each boot.  It's a common issue with WoL.

---

### Post by Irrationalis on 2014-12-30
Ethtool now shows "g" for WOL permanently, but when I shutdown, the ethernet card doesn't appear to be on (no lights on network switch). 
I have tried these methods of shutdown:

> shutdown -h now: no ethernet link
shutdown now: fail, does not completely shutdown
poweroff: no ethernet link


Is there a correct way to shutdown that I'm missing?

---

### Post by tgalati4 on 2014-12-31
What you want is "p" mode, which is Power-on-LAN.  You want your machine to cold boot when it receives a magic packet from another machine.  Typically WoL is to wake a computer that is sleeping.  To put your computer to sleep:

```
sudo pm-suspend
```

To see which parts of the computer remain powered during sleep (S3 mode) use *acpitool*:

```
sudo apt-get install acpitool
acpitool -w
```

---

### Post by Irrationalis on 2014-12-31
So I should have been suspending instead of shutting down?
It's now working perfectly, even though acpitool shows PXS disabled.

Wow, I was looking for something else the entire time. :oops: 
I have got WOL working and I think I like not having to reboot frequently for POL anyway. Thanks tgalati! ):P

---

### Post by tgalati4 on 2014-12-31
Most computers only use about 5 watts of power when in suspend mode, and it is only about 8 seconds until your display and networking come up.  MacBoooks come up quicker, but then you spend a lot more money.  If you dual boot into Windows frequently, then WoL is not convenient.  Power-on-LAN is helpful for booting a server that is not needed frequently--like for periodic backups or for a home-entertainment system.

---


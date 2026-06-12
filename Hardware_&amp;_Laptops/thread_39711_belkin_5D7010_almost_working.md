---
title: "belkin 5D7010 almost working"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by legatodnl on 2005-06-06
I think I'm very close to getting this troublesome wifi card working.
```

root@laptop:/home/dan # ndiswrapper -l
Installed ndis drivers:
bcmwl5 driver present, hardware present
```

When I modprobe ndiswrapper the power light on the card lights up and the following has come up on dmesg

```

ndiswrapper version 1.2rc1 loaded (preempt=yes, smp=no)
ndiswrapper: driver bcml5 (Broadcom,06/13/2003, 3.20.23.0) loaded
ACPI: PCI interrupt 0000:07:00.0[A] -> GSI 9 (level, low) -> IRQ 9
ndisweapper: using irq 9
wlan0: ndiswrapper ethernet device 00:30:bd:fc:22:03 using driver bcmwl5, configuration file 14E4:4320.5.conf
wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
```

But as of yet I have yet to managed to get the network light to flash. The Network configuraion GUI  lists wireless but activating does nothing and iwlist wlan0 scan gives no scan results. The router is set to broadcast the ESSID details.


I would be very grateful for any ideas.

Dan

---

### Post by spd106 on 2005-06-06
Hi, did you run iwlist as sudo?

check that you have the right driver for your card version
**$lspci** will tell you which one you have.

Disable any wep or wpa on the AP till it works. Also check any firewalls aren't stopping you.

I have an f5d7010 running fine with ndis1.1, and i've heard it works on ndis1.2rc.

Check over /etc/network/interfaces
make sure you have **map wlan0**, this caught me out #-o 
and 
[B]iface wlan0 inet dhcp
auto wlan0[/B].

Hope this helps

---

### Post by legatodnl on 2005-06-07
Thanks for the reply.

I've added map wlan0 to /etc/network/interfaces 

I've been trying both version 1.1 and 1.2rc1 and both give me the same results. The bcmwl5 and bcmwl5a drivers both activate the power to the card. I'm not at the laptop atm but i remember lspci telling me that it was a Broadcom chipset.

I have a horrible suspision that my AP doesn't support IPV6 and that could be the cause of the problem. It is a Netgear DG834G.

If you are not near a AP and you wlist scan or dhclient wlan0 do both lights on the belkin fd7010 blink? At the moment only the power light functions. If your net traffic light flickers even when theres no AP to communicate with, then it means my card is still not properly been configured. If not, then it might be my AP.

Dan

---

### Post by spd106 on 2005-06-07
On my card the activity light does not flash when scanning. I think it only flashes when you have a connection.

Could you try it out on another AP, any neighbours/friends with a wifi network?

 I have this for my driver
```
ndiswrapper version 1.1 loaded (preempt=yes,smp=no)
ndiswrapper: driver bcmwl5 (Broadcom,07/17/2003, 3.30.15.0) loaded
```

I'm not sure, but i think this one came with the card. I tried so many to get it working on warty in the end i used bcmwl5a. But after upgrading to hoary i had to switch back to bcmwl5. 

I think there is a way to disable ipv6, i remember someone on this forum wantig to do that. I can't see why that would interfer though.

---

### Post by aamir on 2005-06-20
if you have not found a solution to this issue after following th ndis instructions, try using the real tek driver (if you have the wireless g notebook adapter)

quoted from [http://ndiswrapper.sourceforge.net/phpwiki/index.php/List?PHPSESSID=e8421215c30a939b596058759696dbbc](http://ndiswrapper.sourceforge.net/phpwiki/index.php/List?PHPSESSID=e8421215c30a939b596058759696dbbc)

> Card: Belkin F5D7010 Wireless-G Notebook Adapter
Chipset: RaLink RT2500
pciid: 1814:0201 (rev 01)
Driver: ndiswrapper 0.11 and A-Link [ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip](ftp://ftp.a-link.com/wl54h/WL54driver2.2.6.0.zip)
Other: Debian sid/i386, kernel 2.6.7/9, Inspiron 2650. Tried the linux driver (v1.4.3.0) from [http://www.ralinktech.com/](http://www.ralinktech.com/) -- module loaded, interface created, but settings for iwconfig don't get committed. Tried to get NDIS driver off CD but couldn't locate/extract INF file. Finally tried NDIS driver for another card using RT2500 (the A-Link above), and (so far) it has worked wonderfully.

this got me working after much fustration...make sure you remove all you attempts to get it working previously  \\:D/

---


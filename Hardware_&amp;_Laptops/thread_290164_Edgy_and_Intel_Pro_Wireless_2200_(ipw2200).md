---
title: "Edgy and Intel Pro Wireless 2200 (ipw2200)"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by KAding on 2006-10-31
Hello,

Even been using Fedora for a few years and decided to give Ubuntu another try on my Dell Inspiron 6000 laptop. Everything is looking great, except for the wireless internet. I've spend many hours on this forum looking for a solution, but I simply can't find it ](*,).

The problem: the wireless card is seemingly working, except that it won't detect any access points at all.

I installed networkmanager and disabled all the interfaces in System -> Admin -> Networking. 

It looks to me like the driver loads fine:
```

kading@flaptop:~$ dmesg | grep ipw2200
[17179591.060000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179591.060000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179591.060000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179591.116000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179591.676000] ipw2200: Radio Frequency Kill Switch is On:
[17179591.676000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)

```

Can't detect any networks. I can't connect using iwconfig manually either btw. No luck with wifi-rader either. So the problem is not really network-manager. I know it should detect at least 6-7 networks, most of them secured.
```

kading@flaptop:~$ iwlist eth1 scanning
eth1      No scan results

```

Ifconfig:
```

eth1      Link encap:Ethernet  HWaddr 00:13:CE:83:A8:95  
          inet6 addr: fe80::213:ceff:fe83:a895/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1155 (1.1 KiB)  TX bytes:432 (432.0 b)
          Interrupt:201 Memory:dfcfd000-dfcfdfff 

```

```

kading@flaptop:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

I don't know what more information would be relevant :(. Please help, I'm getting desperate.

Should I try to install the latest driver and firmware from the ipw2200.sourceforge.net website?

Thanks :)

KAding

---

### Post by wieman01 on 2006-10-31
Yes, most likely you need to update a number of components such as the firmware, ieee80211, etc. There is a good howto for Dapper, but I believe it equally applies to Edgy. Worked for me under Dapper.

[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200]("http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200")

If this does not work, may I suggest to go for Dapper instead. That's the current stable version of Ubuntu with long-term suport (3 years). Edgy is meant to experimental.

---

### Post by KingArthur10 on 2006-11-01
nevermind, wrong solution from the look of things.

---

### Post by wieman01 on 2006-11-01
> **KingArthur10 said:**
> Found the answer in another thread.

you'll need to edit /etc/network/interfaces

Comment out everything except "auto lo" and "iface lo inet loopback".

Restart and everything should work like a charm again. Did for me!
Not quite... only the wireless adapters... he has done so already. You only see "eth0" which is his Ethernet device.

---

### Post by KAding on 2006-11-03
Thanks for the help. I got it to work, somehow. Not sure exactly how, but it detects the networks now!

---

### Post by secundar on 2006-11-10
I have the same problem. Any tips? Asus z71v running Edgy. The wireless button turns t on and off which is cool but it failes to connect to any networks.

---

### Post by coffeecat on 2006-11-10
I installed Ubuntu Edgy on this Sony Vaio laptop with ipw2200 this evening. With an ethernet cable connection to my router I selected network-manager-gnome in Synaptic for download. Synaptic automatically added network-manager as a dependency. After download and installation I removed the ethernet cable and rebooted. NM started by itself so I clicked on the applet icon, selected my network, put in my WPA passkey where prompted, then gave it a keyring password and I was connected in seconds. This was much easier than Fedora Core 6 (also on this multibooting machine) where I had to download, unpack and manually copy the firmware to /lib/firmware and enable NM in startup services - although that wasn't particularly difficult.

I keep coming across threads where people seem to have difficulty with the ipw2200 wireless chipset, so I wanted to put the record straight. **With recent versions of the kernel it couldn't be easier.**

By the way, the howto linked to by wieman01 was excellent when it was written, but it's now very out of date.

---

### Post by wieman01 on 2006-11-10
> **coffeecat said:**
> By the way, the howto linked to by wieman01 was excellent when it was written, but it's now very out of date.
Yes, I think you're right. Does not apply to Edgy anymore... Apparently they have done their homework. I still used it for Dapper & it worked.

---

### Post by coffeecat on 2006-11-11
> **wieman01 said:**
> Yes, I think you're right. Does not apply to Edgy anymore... Apparently they have done their homework. I still used it for Dapper & it worked.

Glutton for punishment, aren't you? :wink: I can't remember exactly what I did for Dapper, but it wasn't much more than what I have just done in Edgy. Perhaps I had to download and install the ipw2200 firmware as well, but whatever, network-manager 'just worked'.

**Edit:** although I see from another thread that you have good reasons for not using network-manager. Fair enough. Perhaps I've been lucky in that NM has been stable for me, I don't need a static IP address on my laptop and I don't need a hidden ESSID.

---

### Post by wieman01 on 2006-11-11
> **coffeecat said:**
> Glutton for punishment, aren't you? :wink: I can't remember exactly what I did for Dapper, but it wasn't much more than what I have just done in Edgy. Perhaps I had to download and install the ipw2200 firmware as well, but whatever, network-manager 'just worked'.
Alright, alright... Got it. I had to upgrade because WPA2 would not work. I hope you accept that as an excuse. ;-) I'll stick to my last in future...

---

### Post by BlaY0 on 2006-11-14
> **KAding said:**
> Thanks for the help. I got it to work, somehow. Not sure exactly how, but it detects the networks now!

Your problem was in:

[17179591.676000] ipw2200: Radio Frequency Kill Switch is On:

Your radio switch was set to off! There should be some HW switch on your laptop or some combo of keypress to activate the radio. You should search for  the solution in this direction...

---

### Post by Buffalo Soldier on 2006-11-21
> **BlaY0 said:**
> Your problem was in:

[17179591.676000] ipw2200: Radio Frequency Kill Switch is On:

Your radio switch was set to off! There should be some HW switch on your laptop or some combo of keypress to activate the radio. You should search for  the solution in this direction...
On my DELL Inspiron 510m the key combo for turning on/off the wireless is FN + F2.

---

### Post by greatnate on 2006-11-21
I am really confused about whats going on with my wireless as well.  I am actually using it right now, I can see it with ifconfig, I can see it with iwconfig, iwconfig will show the switch on and off when I hit Fn+F2.   However WiFi Radar and the built in Network Manager are unable to show me a list of wireless networks.

iwconfig:
eth1      IEEE 802.11b  ESSID:"Champion_28thEast"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:95:51:51:70   
          Bit Rate=11 Mb/s   Tx-Power:16 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:15   Missed beacon:0

ifconfig:
eth1      Link encap:Ethernet  HWaddr 00:0C:F1:3D:52:34  
          inet addr:192.168.0.19  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe3d:5234/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11253 errors:15 dropped:0 overruns:0 frame:0
          TX packets:1736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2330534 (2.2 MiB)  TX bytes:269712 (263.3 KiB)
          Interrupt:5 Base address:0x8000 Memory:fafef000-fafeffff

---

### Post by yeehawjared on 2006-11-22
I can't turn off the kill switch to save my life.

please take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=303135&highlight=ipw2200](http://ubuntuforums.org/showthread.php?t=303135&highlight=ipw2200)

---

### Post by _Q_ on 2006-11-23
i have ipw2100 integrated wireless card on my laptop...

after i recompile the kernel (with ipw2100 included as a module), it can't seem to find the firmware...

does anyone know in which location does the driver look for the firmware? (i tryed /usr/lib/firmware and /usr/lib/hotplug/firmware so far...)

---

### Post by qiemem on 2006-11-23
Similar problem to greatnate (though I had the kill switch problem too... easiest solution to a problem ever). I can connect fine to a network, but none of the guis ever list networks to connect to (except, strangely, the one I was on when I upgrade to edgy).

Oh, greatnate, if you know the name of the network you wish to connect to, you can:
```

$ sudo -s
$ ifdown eth1
$ iwconfig eth1 [network name]
$ ifconfig eth1 up
$ dhclient eth1

```
Its kinda annoying to have to manually connect... plus you have to know the network name... Haven't tried listing networks via "iwlist eth1 scanning". It found the network I'm on alright (which is the one I installed edgy); haven't tried it on any others.

Anyway, if anyone knows what might causing this, help would be much appreciated.
Workin with an ipw2200... Oh, so just ran "dmesg|grep ipw" and found, well:
"Driver 'ipw2200' needs updating - please use bus_type methods"
Um, don't know much about this stuff. Where can I get the new driver? Could this be the problem?
Greatnate, you might want to check your dmesg as well.
Oh ya, using an Inspiron 9300

---

### Post by greatnate on 2006-11-23
> **qiemem said:**
> Similar problem to greatnate (though I had the kill switch problem too... easiest solution to a problem ever). I can connect fine to a network, but none of the guis ever list networks to connect to (except, strangely, the one I was on when I upgrade to edgy).

Oh, greatnate, if you know the name of the network you wish to connect to, you can:
```

$ sudo -s
$ ifdown eth1
$ iwconfig eth1 [network name]
$ ifconfig eth1 up
$ dhclient eth1

```
Its kinda annoying to have to manually connect... plus you have to know the network name... Haven't tried listing networks via "iwlist eth1 scanning". It found the network I'm on alright (which is the one I installed edgy); haven't tried it on any others.

Anyway, if anyone knows what might causing this, help would be much appreciated.
Workin with an ipw2200... Oh, so just ran "dmesg|grep ipw" and found, well:
"Driver 'ipw2200' needs updating - please use bus_type methods"
Um, don't know much about this stuff. Where can I get the new driver? Could this be the problem?
Greatnate, you might want to check your dmesg as well.
Oh ya, using an Inspiron 9300

I have checked my dmesg.  It seems to detect the card ok; i'll post it later.  Another weird thing is that the default GUIs will not work with the orinoco gold card either.  WiFiRadar will work with the orinoco but that is all.

---


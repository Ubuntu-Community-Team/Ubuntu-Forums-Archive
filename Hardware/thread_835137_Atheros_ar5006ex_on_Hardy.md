---
title: "Atheros ar5006ex on Hardy"
date: 2008-06-20
forum: Hardware
---

### Post by sunami88 on 2008-06-20
I installed Ubuntu 7.04 last night (it was the only Ubuntu CD I had lying around), and after playing around a bit making sure it liked my laptops hardware I decided to upgrade to the latest version.

Before the update my wireless worked fine, but now I dont have an option for wireless networks when I click on the little connection manager in the bottom right bar.

Any suggestions? My ethernet still works, but I'd like to use my wireless for when I'm not around the house. Thanks.

P.S.
  Nothing shows up in the restricted drivers manager, whereas before it showed my Atheros wifi as enabled.

---

### Post by ukripper on 2008-06-20
> **sunami88 said:**
> I installed Ubuntu 7.04 last night (it was the only Ubuntu CD I had lying around), and after playing around a bit making sure it liked my laptops hardware I decided to upgrade to the latest version.

Before the update my wireless worked fine, but now I dont have an option for wireless networks when I click on the little connection manager in the bottom right bar.

Any suggestions? My ethernet still works, but I'd like to use my wireless for when I'm not around the house. Thanks.

P.S.
  Nothing shows up in the restricted drivers manager, whereas before it showed my Atheros wifi as enabled.

Can you post output of the followign commands:

```
lspci
```
```
iwconfig
```
```
iwlist scan
```

---

### Post by sunami88 on 2008-06-20
> **ukripper said:**
> Can you post output of the followign commands:

```
lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
**0c:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)**


```
iwconfig
```
lo        no wireless extensions.
eth0      no wireless extensions.


```
iwlist scan
```
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

.

---

### Post by ukripper on 2008-06-20
Your card is detected but drivers are not.

Try this link this will fix this for you.
[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

if you are runnign 32 bit this is better howto-
[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

---

### Post by sunami88 on 2008-06-20
> **ukripper said:**
> Your card is detected but drivers are not.
Try this link this will fix this for you.
[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)
if you are runnign 32 bit this is better howto-
[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

I have a 32 bit proc, so I used madwifi. I also chose to install Wicd. The only problem I'm having now is I can't connect to my network. I can see my network now (so scanning is working). I ran iwconfig and came up with this;
```

sunami88@Omar:~$ iwconfig ath0 essid <my network>
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; Operation not permitted.

```

I tried going back to the Ubuntu default Network Manager, but I had the same problem...

---

### Post by ukripper on 2008-06-20
> **sunami88 said:**
> I have a 32 bit proc, so I used madwifi. I also chose to install Wicd. The only problem I'm having now is I can't connect to my network. I can see my network now (so scanning is working). I ran iwconfig and came up with this;
```

sunami88@Omar:~$ iwconfig ath0 essid <my network>
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device ath0 ; Operation not permitted.

```

I tried going back to the Ubuntu default Network Manager, but I had the same problem...

What you get in ```
iwlist scan
``` Can you post here if you essid is visible?

---

### Post by sunami88 on 2008-06-20
> **ukripper said:**
> What you get in ```
iwlist scan
``` Can you post here if you essid is visible?

Yep. It's visible, I just can't seem to connect...

---

### Post by ukripper on 2008-06-20
> **sunami88 said:**
> Yep. It's visible, I just can't seem to connect...

Make sure you are selecting correct key format
hex or ASCII
and WEP or WPA

---

### Post by sunami88 on 2008-06-20
> **ukripper said:**
> Make sure you are selecting correct key format
hex or ASCII
and WEP or WPA

I went back just to make sure, but ya it was set to the proper encryption. It fails pretty quickly, which makes me think its not trying to connect...

Scanning works, but when I try to connect it fails in less than a second.

---

### Post by ukripper on 2008-06-20
> **sunami88 said:**
> I went back just to make sure, but ya it was set to the proper encryption. It fails pretty quickly, which makes me think its not trying to connect...

Scanning works, but when I try to connect it fails in less than a second.

If scanning works that means drivers are installed fine. It is just matter of configuration.

Can you post output of the following:
```
iwconfig
```

---

### Post by sunami88 on 2008-06-20
> **ukripper said:**
> If scanning works that means drivers are installed fine. It is just matter of configuration.

Can you post output of the following:
```
iwconfig
```

```

sunami88@Omar:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sunami88@Omar:~$ 

```
.

---

### Post by ukripper on 2008-06-20
Are you using WPA or WEP to connect with Network manager or WICD?

if you add nm-applet to panel and then try to connect through that what you get?

---

### Post by sunami88 on 2008-06-20
> **ukripper said:**
> Are you using WPA or WEP to connect with Network manager or WICD?

if you add nm-applet to panel and then try to connect through that what you get?

Here is what System-> Admin-> Network shows me;
[img]http://home.cogeco.ca/~kev_cumming/ubuntutemp/wifimissing1.png[/img]

When I use the Ubuntu applet, this is what I see;
[img]http://home.cogeco.ca/~kev_cumming/ubuntutemp/wifimissing2.jpg[/img]

When I switch to Wicd, I can see my networks (the last one is my neighbors);
[img]http://home.cogeco.ca/~kev_cumming/ubuntutemp/wifimissing3.png[/img]

As you can see, I've put in my 128-bit Hex WEP key;
[img]http://home.cogeco.ca/~kev_cumming/ubuntutemp/wifimissing4.jpg[/img]

But when I try to connect;
[img]http://home.cogeco.ca/~kev_cumming/ubuntutemp/wifimissing5.png[/img]

But it sits connecting for a minute, then after a time fails.

---


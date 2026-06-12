---
title: "problem getting wireless connection with linksys WUSB54GCv3"
date: 2009-12-04
forum: Hardware
---

### Post by Kojans on 2009-12-04
Hi!

I cannot get a working wireless connection from my laptop (HP compaq nc6000) with the wireless USB adaptor from Linksys: WUSB54GC v.3. I think the adaptor is recognised: I got this output from /var/log/messages after plugging in the adaptor:

> Dec  4 20:39:36 ko-laptop kernel: [ 6375.868085] usb 1-1: new high speed USB device using ehci_hcd and address 4
Dec  4 20:39:36 ko-laptop kernel: [ 6376.018110] usb 1-1: configuration #1 chosen from 1 choice
Dec  4 20:39:36 ko-laptop kernel: [ 6376.057957] Registered led device: rt2800usb-phy1::radio
Dec  4 20:39:36 ko-laptop kernel: [ 6376.057985] Registered led device: rt2800usb-phy1::assoc
Dec  4 20:39:36 ko-laptop kernel: [ 6376.058013] Registered led device: rt2800usb-phy1::quality
Dec  4 20:39:36 ko-laptop kernel: [ 6376.119286] udev: renamed network interface wlan0 to wlan1
Dec  4 20:39:36 ko-laptop kernel: [ 6376.123172] rt2800usb 1-1:1.0: firmware: requesting rt2870.bin
Dec  4 20:39:36 ko-laptop kernel: [ 6376.370193] ADDRCONF(NETDEV_UP): wlan1: link is not ready
from iwconfig:
> 
ko@ko-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   MissedNetworkManager Applet beacon:0

I have Ubuntu 9-10 installed, and (tried to) use the NetworkManager Applet to configure network access. My router is a SpeedTouch THOMSON ST780; I can get a wireless connection from Windows XP.
My questions:
Do I need to download a driver?
From Where/which driver?
Do I have to install ndiswrapper?

Any help would be appreciated; I found a lot of posts about wireless connections, but none of them could make me any wiser...

Thanks!

---

### Post by IcarusR on 2009-12-05
Try this thread....
[http://newyork.ubuntuforums.org/showthread.php?t=1155941&highlight=WUSB54GCv3]("http://newyork.ubuntuforums.org/showthread.php?t=1155941&highlight=WUSB54GCv3")

---

### Post by RedSingularity on 2009-12-05
You may need ndiswrapper if there are no proprietary drivers made for linux.  While the device is plugged in look at System>Admin>Hardware Drivers.  It may be in there to activate.

---

### Post by Kojans on 2009-12-06
Thanks, IcarusR!

I read the post you mentioned. It's quite a long story... I printed out the very detailed instructions in post  			#[**182**]("http://newyork.ubuntuforums.org/showpost.php?p=8418039&postcount=182"); I going to try it next week.

---


---
title: "Another b43-fwcutter thread."
date: 2008-09-20
forum: Hardware
---

### Post by Khev on 2008-09-20
Okay, before you jump down my throat, hear me out.  I've tried everything I could find on the forums, so I thought I'd come for some more help.  I'm not an entire noob (pretty close though), and I'd like to think I can follow directions.  So... here we go.

I have an old eMachines laptop, model M6805.  Total piece of crap, but it's what I've got to work with.  'lspci' yields this for the network controller:

```
00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

Using 8.04, found b43-fwcutter on the distro CD under /pool/main/b/b43-fwcutter.  It worked like a charm during the install.  Restarted, and the wireless light lit up.  ifconfig yielded this:

```
$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:90:96:8a:ce:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

Uh, yeah.  You can see that something is amiss there.  I used the nm-applet in Gnome to check for wireless... and... Nothing.  Been a while since I've had a chance to play with *nix, so I had to look up some commands.  Here's the most interesting one.

```
$ sudo iwlist wlan0 scan
wlan0     No scan results
```

No matter what I do, it won't see the access point.  Here's the printout of all relevant 'dmesg' data too.. but this is slightly over my head.

```
[  954.129211] b43-phy0 debug: Removing Interface type 2
[  954.177391] b43-phy0 debug: Wireless interface stopped
[  954.177560] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 0/64
[  954.177632] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[  954.185200] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[  954.193183] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[  954.201181] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[  954.209186] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 2/128
[  954.217185] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[ 1045.376857] input: b43-phy0 as /devices/virtual/input/input10
[ 1045.496085] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 1046.489118] b43-phy0 debug: Chip initialized
[ 1046.489862] b43-phy0 debug: 30-bit DMA initialized
[ 1046.492673] Registered led device: b43-phy0:tx
[ 1046.493018] Registered led device: b43-phy0:rx
[ 1046.493300] Registered led device: b43-phy0:radio
[ 1046.493344] b43-phy0 debug: Wireless interface started
[  464.695808] b43-phy0 debug: Adding Interface type 2
[  464.696222] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Anyone have any ideas?  My thanks in advance.

---

### Post by bpl07 on 2008-09-20
This is just a quick response, and I'm sure you've already checked this, but is it turned on?  That kind of output is what I get when my wireless card is turned off.

---

### Post by Khev on 2008-09-20
Yup.  As on as I can get it.  :\

---

### Post by bpl07 on 2008-09-20
Could you post the results of 

> dmesg | grep b43

and 

> uname -a

---

### Post by tariquepark on 2008-09-20
hi its funny because i just booted this very compaq laptop from the hardy live disk
it has the same broadcom chipset as yours and, well im using it now so it works
any how this what i did:
booted from the live disk and connected the lan cable
after it booted the restricted device manager popped up asking if i wanted to use them
naturally i went for yes
t downloaded the firmware and dependencies and all was good
then i unplugged the lan cable and waited a connected couple secs and the network icon had the little red cross on it  so i ticked it and it connected
ithought it was fantastic and just oh so easy

if you have a live disk handy it might show you where you have gone wrong :)

regards

---

### Post by Khev on 2008-09-20
Surely.

```
$ dmesg | grep b43
[   27.402553] b43-phy0: Broadcom 4306 WLAN found
[   27.440868] b43-phy0 debug: Found PHY: Analog 2, Type 2, Revision 2
[   27.440889] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   79.093746] input: b43-phy0 as /devices/virtual/input/input9
[   35.342312] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   36.314528] b43-phy0 debug: Chip initialized
[   36.315013] b43-phy0 debug: 30-bit DMA initialized
[   36.316697] Registered led device: b43-phy0:tx
[   36.316899] Registered led device: b43-phy0:rx
[   36.317071] Registered led device: b43-phy0:radio
[   36.317105] b43-phy0 debug: Wireless interface started
[   36.370196] b43-phy0 debug: Adding Interface type 2
[  954.129211] b43-phy0 debug: Removing Interface type 2
[  954.177391] b43-phy0 debug: Wireless interface stopped
[  954.177560] b43-phy0 debug: DMA-32 0x0200 (RX) max used slots: 0/64
[  954.177632] b43-phy0 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[  954.185200] b43-phy0 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[  954.193183] b43-phy0 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[  954.201181] b43-phy0 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[  954.209186] b43-phy0 debug: DMA-32 0x0220 (TX) max used slots: 2/128
[  954.217185] b43-phy0 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[ 1045.376857] input: b43-phy0 as /devices/virtual/input/input10
[ 1045.496085] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[ 1046.489118] b43-phy0 debug: Chip initialized
[ 1046.489862] b43-phy0 debug: 30-bit DMA initialized
[ 1046.492673] Registered led device: b43-phy0:tx
[ 1046.493018] Registered led device: b43-phy0:rx
[ 1046.493300] Registered led device: b43-phy0:radio
[ 1046.493344] b43-phy0 debug: Wireless interface started
[  464.695808] b43-phy0 debug: Adding Interface type 2

```

```
$ uname -a
Linux margaritaville 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
```

In response to tariquepark:  That's pretty much what I did the first time (install before this.)  It had the same effect when it found it automatically as it did when I launched it from the package on the disc.  Thanks though.  :)

---

### Post by bpl07 on 2008-09-20
I don't really see anything there to suggest why it isn't working.  You could try reporting your bug to the developers as described here:

[http://linuxwireless.org/en/users/Drivers/b43#bugreporting](http://linuxwireless.org/en/users/Drivers/b43#bugreporting)

Sorry I couldn't help anymore.

---

### Post by Khev on 2008-09-20
After doing some more research (coincidentally, on the same page that you linked me to), I found that my card needs to use b43legacy.  Is it?  If so, how do you know?  If not, do you have a suggestion on a way to fix it?

No apology necessary.  I'm just shooting in the dark here.  :)

---

### Post by bpl07 on 2008-09-20
Yours is revision 03, so it should be using b43, not b43legacy.

---

### Post by Khev on 2008-09-20
From that page:
> 4306 and 4309 cards with a MAC core revision of 4 or less should also use b43legacy.

---

### Post by Khev on 2008-09-20
I resolved this.  Sorta.  Main goal accomplished, but using fwcutter.  Tried ndiswrapper, and it worked the first time.  I'd still like to get fwcutter to work, but I guess I'll just content myself with the fact that it works now.  

Thank you for your help and suggestions, bpl07.  :KS

---

### Post by jabeez on 2008-09-21
hey, I just dealt with this same chipset while installing 'Buntu on my mom's laptop, and after following one of the "fool-proof" how-to's that took about 20 min. and still wouldn't connect, I found this thread...

[http://ubuntuforums.org/showthread.php?t=900763&highlight=broadcom+4306]("http://ubuntuforums.org/showthread.php?t=900763&highlight=broadcom+4306")


and went to that omattos link, downloaded the file and extracted it into /lib/firmware like it says, and voila!! working, fast wireless that took about 2 minutes and didn't require any cutters or ndiswrapper. this was on a fresh install mind you, I thought it easier to reinstall than try to back out of everything that how-to I tried had me do. so check it out, it was ridiculously easy after reading through the pages of broadcom/hardy threads......

---

### Post by Khev on 2008-10-01
Wow.  This is.. wow.  

My setup with ndiswrapper was working dandy, until I flashed my Linksys router today.  Don't ask me what happened or how, but it totally would not connect to the router with the new firmware.  I hadn't really done much more than toss some servers on it for testing.  Found this, and figured, why not try a clean install.  It took no time at all, and I went from 40-50% reception to a steady 80%.  

Thank you sir.  This is quite helpful.  :)

---


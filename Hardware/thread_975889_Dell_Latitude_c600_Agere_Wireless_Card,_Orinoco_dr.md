---
title: "Dell Latitude c600 Agere Wireless Card, Orinoco driver, Modprobe help"
date: 2008-11-08
forum: Hardware
---

### Post by dfgilbert on 2008-11-08
Here's some preface.  I got two 700MHz Dell Latitude Notebooks for free, with 128Mb of ram in each.  They turned on, ran, etc so I figured I'd install Linux and give one to my girlfriend because she desperately needs a home computer for email, term papers, research, and other basic college stuff.  But, there was no wifi card, so I purchased an Agere MPCI3A-20/R wireless ethernet card for $20 and installed it.

I butchered one to improve the other, ie I stole the 128Mb of ram out of the 2nd and put it in the first.  To give it 256Mb.

So the Notebook's specs are
700MHz with 256Mb RAM

Then I downloaded Ubuntu 6.04 Dapper LTS, because I figured I should start small and see what the performance is like, and installed it.  Runs amazingly fast on the computer, but it doesn't allow access to the internet. I tried 8.04 live CD, same results.

I go in Network Settings and it shows that it's there and Enabled.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=91767&stc=1&d=1226193404[/IMG]

I also ran lshw
```

 *-network
       description: Wireless interface
       physical id: 1
       logical name: eth0
       serial: 00:02:2d:XX:XX:XX
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

```
Which shows the card being there and active, but no driver information (which is my issue, I believe).

_**[SIZE="6"]My Question/Issue:[/SIZE]**_
What I need help with, I believe my trouble is that I don't have the driver active.  But I don't really know what to do to activate it.  Below is some information on the system dmesg, lspci, iwconfig data.

[SIZE="5"]**Could you help me solve my wireless problem?**[/SIZE]

I did some reading and ran some commands

dmesg
```

[17179610.772000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179610.780000] orinoco_cs 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179610.864000] eth0: Hardware identity 0005:0004:0005:0000
[17179610.864000] eth0: Station identity  001f:0001:0008:000a
[17179610.864000] eth0: Firmware determined as Lucent/Agere 8.10
[17179610.864000] eth0: Ad-hoc demo mode supported
[17179610.864000] eth0: IEEE standard IBSS ad-hoc mode supported
[17179610.864000] eth0: WEP supported, 104-bit key
[17179610.864000] eth0: MAC address 00:02:2D:7C:CE:97
[17179610.864000] eth0: Station name "HERMES I"
[17179610.864000] eth0: ready
[17179610.864000] eth0: index 0x01: Vcc 3.3, irq 11, io 0x0100-0x013f

```

It shows up in here.

Then I did

lspci
```

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:03.0 CardBus bridge: Texas Instruments PCI1420
0000:00:03.1 CardBus bridge: Texas Instruments PCI1420
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
0000:00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
0000:00:10.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)

```
Doesn't show up here.

I go to /sbin and do iwconfig

```

eth0      IEEE 802.11b  ESSID:""  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None
          Bit Rate:2 Mb/s   Sensitivity:1/3
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
The thing about doing iwconfig is, everytime I've done something to the computer, I check it.  And... sometimes it connects to my router.  Which is weird.  It comes up saying ESSID:"dogbot" <-- which is my router name.  So I get that but no access point, I tried adding the MAC address to that, but it gives me an error.

I read that I should enable the Orinoco module in the kernel, but I'm not sure how to do that 100%

I used locate to find all the module names containing orinoco, then I tried to
```

modprove orinoco

```
and all the variants.

But I'm not really sure what the heck I'm doing now, kind of over my head.  Any advice would help a lot.

---

### Post by dfgilbert on 2008-11-09
please help

---

### Post by priegog on 2008-11-27
Hi. I'm interested in knowing if this agere card works too. So I'll just bounce a couple of ideas off of you. 
First would be to install the latest version 8.10. There's no reason to think it uses any more resources than the older distros do, and the newer kernels have bunchs of newer drivers, specifically wifi ones. Altho with 256 RAM I think you might have to use the alternate install CD, since the live CD might not be able to boot. 
And also, in this newer versions the proprietary hardware wizard comes up if it detects something that needs a special driver outside the kernel. 
So give it a try and let us know. 
Oh, and also, 512MB or even 1GB ram SODIMMs are dirt cheap nowadays, so you could also find a use for that other laptop you cannibalized. I run an older tablet with 1GB ram, and it works wonderfull.
I hope that helps.

---

### Post by ocarlson on 2009-04-02
My Orinoco Gold card works with Ubuntu 8.10 with no mods.  Just install what 8.10 wants to install.

WPA security sometimes takes several passes to connect, but after that it is rock-solid.

C600, 850mHz, 256mRam, 40gB disk, added DVD-ROM/CDRW drive DRN8080B, Cardbus USB2.0 card, Cardbus Orinico Gold.

after sudo lshw, it shows up as:
           *-network
                description: AR5001-0000-0000
                product: Wireless LAN Reference Card
                vendor: Atheros Communications, Inc.
                physical id: 0
                version: 00
                slot: Socket 0
                resources: irq:11



in dmesg, it loads as ath0:
[   36.513476] ath_rate_sample: 1.2 (0.9.4)
[   36.515082] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   36.515101] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   36.515131] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   36.515151] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   36.515163] wifi0: mac 5.9 phy 4.3 radio 4.6
[   36.515179] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   36.515185] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   36.515191] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   36.515198] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   36.515204] wifi0: Use hw queue 8 for CAB traffic
[   36.515210] wifi0: Use hw queue 9 for beacons
[   36.537348] wifi0: Atheros 5212: mem=0x24000000, irq=11


in lspci, the card shows up as:
02:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

/sbin iwconfig shows:
ath0      IEEE 802.11g  ESSID:"Summerwood"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0F:66:9E:35:C6   
          Bit Rate:48 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/70  Signal level=-60 dBm  Noise level=-92 dBm
          Rx invalid nwid:287  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Regards, O

---

### Post by CitizenJames on 2010-01-24
I'm trying to get my Orinoco Gold working on Ubuntu Studio 9.04. It doesnt...

---


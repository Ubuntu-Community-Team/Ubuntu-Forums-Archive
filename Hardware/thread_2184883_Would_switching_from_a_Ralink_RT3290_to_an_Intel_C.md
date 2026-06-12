---
title: "Would switching from a Ralink RT3290 to an Intel Centrino 2230 NIC do me any good?"
date: 2013-10-31
forum: Hardware
---

### Post by dericke on 2013-10-31
**UPDATE: **Though I was able to get WiFi working reliably, I was disappointed in the reception, as well as the Bluetooth drivers for the card. I picked up a used 2230 on eBay for $7 US and have seen much better performance for both WiFi and Bluetooth.

My HP Envy 4-1117nr came with a Ralink RT3290 WiFi + Bluetooth combo module installed. To my dismay, I've found that the WiFi functionality only recently got supported in the kernel, and the bluetooth requires a user to compile a driver. The WiFi performance has been disappointing from the start, and I've been using a D-Link USB dongle with much better results. The Bluetooth, since I got the driver working, seems a bit unstable as well. Also, [this]("http://h30434.www3.hp.com/t5/Wireless-Internet-Home-Networking/Ralink-RT3290-adapter-issues/td-p/2271893") thread suggests that the hardware itself is somewhat crappy, since several Windows users are having problems.

I was looking at buying an Intel Centrino-N 2230 card on eBay. HP has a BIOS whitelist for wireless cards, and the Intel card is one of only a few options. The others are an Atheros and a Broadcom card. My questions are:

[LIST]
[*]Is there anything else I should look into before buying a new card? 
[*]Does anyone have experience with the Centrino-N 2230 in Ubuntu 13.10 and can tell me if it's a decent card and has good drivers? 
[*]Have any Hp Envy 4/6 owners resolved wireless issues to their satisfaction with a different card or other option? 
[/LIST]

Thanks.

EDIT: Kernel 3.12 seems to have solved my WiFi connection problem. I haven't yet tried re-installing the bluetooth driver over it, but that part is low-priority.

---

### Post by Bucky Ball on 2013-10-31
You might want to try this:

[http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/](http://rricketts.com/installing-ralink-rt3290-wireless-drivers-in-ubuntu-12-04/)

... or the range of options here:

[http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working)

... before forking out for a new card. Many people have this working without issue. Sounds to me like you might have a conflict with another driver and need to blacklist it. Have you connected your machine with a cable and done an update? Or done an update? While on a cable, open a terminal and issue these two commands (with the dongle out and the internal card in):

```

sudo apt-get update
sudo apt-get upgrade
```

Reboot (with dongle and cable out). Any improvement?

---

### Post by dericke on 2013-10-31
EDIT 2: Relevant bugs:

[ Bug #1189721]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721") - bluetooth driver not in kernel
[ Bug #1245819]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1245819") - wireless driver disconnection -- potentially fixed in kernel 3.12. I'm trying it now, so far, so good

First, a little more detail of my symptoms: I get OK wifi signal for 20~30 min after booting or resuming from sleep, then the signal drops. It is low at all times, however--I'm getting half-strength at one meter from the router. As of right now, I am only using the driver that is in  kernel 3.11. I've also been religiously running apt-get update and apt-get upgrade at least daily since I installed a few days ago.

I spent a good deal of time online today trying to get the WiFi drivers to compile. I haven't tried absolutely everything--there's still a few things from that AskUbuntu post that I haven't tried yet--but the drivers, as downloaded from Zotac and from MediaTek, will not compile without some magic configuration, which I have not yet found. One lead I got: [this PPA]("https://launchpad.net/~barracuda72/+archive/ralink") has modified drivers. I downloaded both as tarballs. The Bluetooth driver  compiled and installed without issue, but the WiFi driver gave this:

```

$ make
Makefile:26: /var/lib/dkms/rt3290/2.6.0.0rev1/build/os/linux/config.mk: No such file or directory
make: *** No rule to make target `/var/lib/dkms/rt3290/2.6.0.0rev1/build/os/linux/config.mk'.  Stop.

```

There's a .debian file in there that isn't part of the vendor's tarball, but I don't know how to utilize it. I'm guessing that the PPA's maintainer's changes are contained in that?

Your mention of conflicting drivers gave me another idea. I ran this:

```

$ lsmod | grep 'rt2'
rt2800pci              18690  0 
rt2800lib              79963  1 rt2800pci
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  1 rt2800pci
rt2x00lib              55238  4 rt2x00pci,rt2800lib,rt2800pci,rt2x00mmio
mac80211              596969  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              479757  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib

```

Do you think the rt2x00pci and rt2800pci modules could conflict?

EDIT: Here's some more info:

On this last session, I had wireless for a good 90 minutes, while on AC power and sitting at my desk, but without an ethernet plugged in, from a resume from sleep until I lost signal. Here's iwconfig while I had signal:

```

$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"WTC#4"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:18:24:BC:BE   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=34/70  Signal level=-76 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:60   Missed beacon:0


```

and here it is after signal was lost:

```

$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

Hope that helps!

---


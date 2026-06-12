---
title: "orinoco w200 maverick"
date: 2011-02-13
forum: Hardware
---

### Post by vanquishedangel on 2011-02-13
Ok so here is the issue, My old laptop, a Compaq Presario 1500us, has a w200 wireless card and a funny usb port behind the monitor, it isn't a normal usb as in its not a usb port, but electronically it is seen as one.
 I have tried to install a newer version of Ubuntu on it but the driver wont compile and run on new versions, so I installed hardy on it and my friend uses this laptop for her work and wants to attend an online class with it which it should be capable of doing just fine. The wireless card works with hardy and the Orinoco driver, however as support for the os is about to quit and she will need it for other applications it maybe important to get it working with a newer version of Ubuntu. I tried nswrapper and that didn't work with this card so if anyone knows how to go about this please help.Is it possible to update it from Hardy to maverick and recompile the driver that way and will it work? here are some links.....

[http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=95169](http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=95169)

specs

[http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00009242&lang=en&cc=us&taskId=101&prodSeriesId=96344&prodTypeId=321957](http://bizsupport1.austin.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c00009242&lang=en&cc=us&taskId=101&prodSeriesId=96344&prodTypeId=321957)

---

### Post by vanquishedangel on 2011-02-23
Well ok, not that there was much help this past week but i kept on it, I got the driver loaded and got the firmware on it. The little light is on now and it shows available networks, however it doesn't connect. I click on a network, mine at home has no security set, and it tries, but then a window pops up saying network disconnected. This isnt the only issue this laptop is having but this actually fixed others issues so far. here is the output of lsmod

Module                  Size  Used by
binfmt_misc             6599  1 
microcode               9749  0 
michael_mic             1744  4 
radeon                829447  2 
snd_intel8x0           25664  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
ttm                    56633  1 radeon
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30200  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 35973  0 
orinoco_usb            16857  0 
snd_timer              19067  2 snd_pcm,snd_seq
ndiswrapper           184207  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168092  4 radeon,ttm,drm_kms_helper
orinoco                64558  1 orinoco_usb
ppdev                   5556  0 
yenta_socket           21518  0 
irda                  178970  0 
joydev                  8767  0 
intel_agp              26566  1 
pcmcia_rsrc            10566  1 yenta_socket
parport_pc             26058  1 
psmouse                59033  0 
snd                    49038  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit            5168  1 radeon
cfg80211              144694  1 orinoco
crc_ccitt               1351  1 irda
serio_raw               4022  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
shpchp                 29886  0 
agpgart                32011  3 ttm,drm,intel_agp
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
firewire_ohci          21234  0 
e100                   30356  0 
firewire_core          46643  1 firewire_ohci
mii                     4425  1 e100
floppy                 54311  0 
crc_itu_t               1383  1 firewire_core


here is the out put of lspci

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:04.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)
02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0e.0 USB Controller: NEC Corporation USB (rev 41)
02:0e.1 USB Controller: NEC Corporation USB (rev 41)
02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)

This is the output from iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"default"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

this is from sudo lshw -c network

 *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:08:02:9d:86:02
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.2.4 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:10 memory:40180000-40180fff ioport:2000(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@2
       logical name: eth1
       serial: 00:0b:cd:8e:1b:ab
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb driverversion=2.6.35-25-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b

sudo ifdown eth1 && sudo ifup eth1   command gave

ifdown: interface eth1 not configured
Ignoring unknown interface eth1=eth1

sudo ifconfig gave me this

eth0      Link encap:Ethernet  HWaddr 00:08:02:9d:86:02  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe9d:8602/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3359 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3707599 (3.7 MB)  TX bytes:517081 (517.0 KB)

eth1      Link encap:Ethernet  HWaddr 00:0b:cd:8e:1b:ab  
          inet6 addr: fe80::20b:cdff:fe8e:1bab/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3367 (3.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:508 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29488 (29.4 KB)  TX bytes:29488 (29.4 KB)

sudo cat /var/log/messages | grep switch  gave me this 

Feb 22 14:28:33 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 22 14:28:33 amber-Presario-1500 kernel: [    0.013202] SMP alternatives: switching to UP code
Feb 22 14:28:34 amber-Presario-1500 kernel: [   13.994881] Console: switching to colour frame buffer device 128x48
Feb 22 21:10:42 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 22 21:10:42 amber-Presario-1500 kernel: [    0.013204] SMP alternatives: switching to UP code
Feb 22 21:10:45 amber-Presario-1500 kernel: [   22.696288] Console: switching to colour frame buffer device 128x48
Feb 22 22:20:36 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 22 22:20:36 amber-Presario-1500 kernel: [    0.009192] SMP alternatives: switching to UP code
Feb 22 22:20:38 amber-Presario-1500 kernel: [   18.497901] Console: switching to colour frame buffer device 128x48
Feb 22 22:42:28 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 22 22:42:28 amber-Presario-1500 kernel: [    0.009836] SMP alternatives: switching to UP code
Feb 22 22:42:30 amber-Presario-1500 kernel: [   16.315187] Console: switching to colour frame buffer device 128x48
Feb 22 22:47:23 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 22 22:47:23 amber-Presario-1500 kernel: [    0.013205] SMP alternatives: switching to UP code
Feb 22 22:47:25 amber-Presario-1500 kernel: [   20.046214] Console: switching to colour frame buffer device 128x48
Feb 22 23:02:27 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 22 23:02:27 amber-Presario-1500 kernel: [    0.013687] SMP alternatives: switching to UP code
Feb 22 23:02:28 amber-Presario-1500 kernel: [   19.446341] Console: switching to colour frame buffer device 128x48
Feb 23 00:06:45 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 00:06:45 amber-Presario-1500 kernel: [    0.013202] SMP alternatives: switching to UP code
Feb 23 00:06:46 amber-Presario-1500 kernel: [   17.684774] Console: switching to colour frame buffer device 128x48
Feb 23 00:32:42 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 00:32:42 amber-Presario-1500 kernel: [    0.013202] SMP alternatives: switching to UP code
Feb 23 00:32:43 amber-Presario-1500 kernel: [   30.640307] Console: switching to colour frame buffer device 128x48
Feb 23 02:33:13 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 02:33:13 amber-Presario-1500 kernel: [    0.009192] SMP alternatives: switching to UP code
Feb 23 02:33:19 amber-Presario-1500 kernel: [   30.723539] Console: switching to colour frame buffer device 128x48
Feb 23 03:04:37 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 03:04:37 amber-Presario-1500 kernel: [    0.013207] SMP alternatives: switching to UP code
Feb 23 03:04:38 amber-Presario-1500 kernel: [   17.283069] Console: switching to colour frame buffer device 128x48
Feb 23 03:35:48 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 03:35:48 amber-Presario-1500 kernel: [    0.013202] SMP alternatives: switching to UP code
Feb 23 03:35:49 amber-Presario-1500 kernel: [   19.748220] Console: switching to colour frame buffer device 128x48
Feb 23 03:40:03 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 03:40:03 amber-Presario-1500 kernel: [    0.009192] SMP alternatives: switching to UP code
Feb 23 03:40:05 amber-Presario-1500 kernel: [   20.264234] Console: switching to colour frame buffer device 128x48
Feb 23 04:18:55 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 04:18:55 amber-Presario-1500 kernel: [    0.009192] SMP alternatives: switching to UP code
Feb 23 04:18:55 amber-Presario-1500 kernel: [   16.711400] Console: switching to colour frame buffer device 128x48
Feb 23 11:32:28 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 11:32:28 amber-Presario-1500 kernel: [    0.009193] SMP alternatives: switching to UP code
Feb 23 11:32:29 amber-Presario-1500 kernel: [   27.287265] Console: switching to colour frame buffer device 128x48
Feb 23 11:40:38 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 11:40:38 amber-Presario-1500 kernel: [    0.009192] SMP alternatives: switching to UP code
Feb 23 11:40:39 amber-Presario-1500 kernel: [   27.305596] Console: switching to colour frame buffer device 128x48
Feb 23 11:59:44 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 11:59:44 amber-Presario-1500 kernel: [    0.013206] SMP alternatives: switching to UP code
Feb 23 11:59:45 amber-Presario-1500 kernel: [   27.425154] Console: switching to colour frame buffer device 128x48
Feb 23 12:00:43 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 12:00:43 amber-Presario-1500 kernel: [    0.013205] SMP alternatives: switching to UP code
Feb 23 12:00:44 amber-Presario-1500 kernel: [   27.834669] Console: switching to colour frame buffer device 128x48
Feb 23 12:01:50 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 12:01:50 amber-Presario-1500 kernel: [    0.013201] SMP alternatives: switching to UP code
Feb 23 12:01:52 amber-Presario-1500 kernel: [   27.961313] Console: switching to colour frame buffer device 128x48
Feb 23 21:19:27 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 21:19:28 amber-Presario-1500 kernel: [    0.009192] SMP alternatives: switching to UP code
Feb 23 21:19:29 amber-Presario-1500 kernel: [   27.203285] Console: switching to colour frame buffer device 128x48
Feb 23 21:25:25 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 21:25:25 amber-Presario-1500 kernel: [    0.009191] SMP alternatives: switching to UP code
Feb 23 21:25:27 amber-Presario-1500 kernel: [   27.131056] Console: switching to colour frame buffer device 128x48
Feb 23 22:03:02 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 22:03:02 amber-Presario-1500 kernel: [    0.013207] SMP alternatives: switching to UP code
Feb 23 22:03:03 amber-Presario-1500 kernel: [   27.455465] Console: switching to colour frame buffer device 128x48
Feb 23 22:43:45 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 22:43:45 amber-Presario-1500 kernel: [    0.014617] SMP alternatives: switching to UP code
Feb 23 22:43:46 amber-Presario-1500 kernel: [   27.749115] Console: switching to colour frame buffer device 128x48
Feb 23 23:22:09 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 23 23:22:09 amber-Presario-1500 kernel: [    0.013203] SMP alternatives: switching to UP code
Feb 23 23:22:11 amber-Presario-1500 kernel: [   18.359921] Console: switching to colour frame buffer device 128x48
Feb 24 00:52:03 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 24 00:52:03 amber-Presario-1500 kernel: [    0.009194] SMP alternatives: switching to UP code
Feb 24 00:52:04 amber-Presario-1500 kernel: [   31.718093] Console: switching to colour frame buffer device 128x48
Feb 24 01:18:50 amber-Presario-1500 kernel: [    0.000000] APIC: switched to apic NOOP
Feb 24 01:18:50 amber-Presario-1500 kernel: [    0.013204] SMP alternatives: switching to UP code
Feb 24 01:18:54 amber-Presario-1500 kernel: [   19.097282] Console: switching to colour frame buffer device 128x48


I have looked at all the wifi how tos and this is the farthest i have ever gotten please help, here is a link to some

[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

And there have been many others, i have also downloaded the lastest from the git repository for orinoco, i will try to reload the firmware. also the make install kept putting up errors when i would try it before it was working.

---

### Post by frotzed on 2011-02-24
Disclaimer: I'm not a wireless expert.

I have experienced an old laptop that was picky about the type of encryption it would connect to.  It wouldn't connect to a WPA2, only WEP.  It was odd to say the least.  Perhaps try broadcasting a little differently?

---

### Post by vanquishedangel on 2011-02-24
> **frotzed said:**
> Disclaimer: I'm not a wireless expert.

I have experienced an old laptop that was picky about the type of encryption it would connect to.  It wouldn't connect to a WPA2, only WEP.  It was odd to say the least.  Perhaps try broadcasting a little differently?

Actually this card only does wep, and the router to, the router is a smc barricade turbo. I know this card works and works with the router because of the fact that it was working not long ago with it, with the security enabled, but now all security on both is disabled. I have tried many things and read many wifi docs and nada, i am sure this is just a setting.


For those that see this this page and need to try to enable your wireless w200, the old guide is way out dated, orinoco drivers are written into the kernel now. so the process is different.

( better instructions on the second page)Follow these instructions

first get these programs, i used synaptic
# subversion
# build-essential
# curl
# gcc
# cpp
# linux-headers-XXX 
# wireless-tools
# Linux-backports-modules-wireless-XXX


just in case you need them, and to find your kernel type, type uname -r in a command line (terminal) and replace XXX with the out put.

download the drivers and the utilities package from here

[http://www.nongnu.org/orinoco/downloads/](http://www.nongnu.org/orinoco/downloads/)

in your downloads menu find and extract the utilities package folder that appears you will find get_ezusb_fw, right click it, go to properties, go to permissions tab and tick the box "allow executing file as a program" then click close. then double click on get_ezusb_fw and click run in terminal. Then cd to the directory of the file or type in the terminal cd and drag the orinoco-fwutils-0.25 to the command line and hit enter. then type 

sudo cp orinoco_ezusb_fw /lib/firmware/`XXX`/

again XXX replaced by what you got from uname -r earlier, that should place the firmware, and for me took care of the "wireless extentions are not enabled" error so many people get.

Now extract the Orinoco driver pacakage and go into that folder when it appears, and find the makefile and right click it, go to properties, and tick the box "allow executing file as a program". Double click it and click run in terminal. then in a command line (terminal) type

sudo modprobe -v orinoco_usb

enter your password, and the light may come on, or restart and it should come on mine sees networks and tries to connect but then after a minute it says wireless network disconnected both with a vanilla maverick and a fully updated one.

---

### Post by vanquishedangel on 2011-02-25
update

it seems no wireless cards are working, I just tried a netgear and that failed as well, exactly the same, can see all the networks but not connect. this seems to be a software issue more, and more. I am going to try lucid next.

---

### Post by frotzed on 2011-02-25
> **vanquishedangel said:**
> update

it seems no wireless cards are working, I just tried a netgear and that failed as well, exactly the same, can see all the networks but not connect. this seems to be a software issue more, and more. I am going to try lucid next.

I think that's a good idea.  Please post an update here when you can.

---

### Post by vanquishedangel on 2011-02-26
update

Ok so i tried Lucid, karmic, and jaunty and all versions of each failed except jaunty. Lucid, and karmic wouldn't compile it no matter what i tried, maverick compiled it and saw networks but would not connect. Jaunty is fully updated.

---

### Post by vanquishedangel on 2011-02-27
Ok, i found a happy medium for now at jaunty fully updated, it really doesn't seem that far behind maverick in most of its softwares. Open office on jaunty is at 3.0 and in maverick it is at 3.2, firefox in maverick is at 3.6.13 and in jaunty it is at 3.6.11. maybe some is different or not, i ruled out libnss3-1d as the issue because jaunty works with that library to. The is probably some base softwares that are improved but all in all it is really close, also i followed the directions here.

[http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)

and it worked like a charm.

---

### Post by frotzed on 2011-02-28
> **vanquishedangel said:**
> ... and it worked like a charm.

That's just odd.  Well, cheers on getting it working!  I wish I knew where the incompatibility lay.

---

### Post by vanquishedangel on 2011-03-01
It may lay inside the firewall, as i was looking to see how natty was doing i came across a thread that said to enter this in a command line

sudo rfkill unblock wlan

However for this card i think it would be 

sudo rfkill unblock eth1

if i am not mistaken, that may explain why the first command never worked. and I may need to install rfkill, i don't know if it is an extra program or not.

---

### Post by vanquishedangel on 2011-03-02
I was wrong on alot of accounts, it is fixed not and it turns out it was a firmware issue

the fix was originally posted here

[http://ubuntuforums.org/showthread.php?t=1617549](http://ubuntuforums.org/showthread.php?t=1617549)

---

### Post by vanquishedangel on 2011-03-03
Ok I got this fixed, first off ignore the previous parts of this post as I was trying to figure out the issue at those times and here is a better way to do it that works, that I have found.

First install maverick and then update fully to the latest, or if you can't because of internet access then in stall maverick.

once installed you need to also download just the orinoco-fwutils-0.2 package from here

[http://www.nongnu.org/orinoco/downloads/](http://www.nongnu.org/orinoco/downloads/)

and right click and choose extract here, this file should be located in your downloads file just go to places---> downloads. Go into the extracted file and double click get_ezusb_fw, and choose run in terminal. Then open a terminal and type cd, and drag the extracted folder to the terminal. then hit enter, that will bring the terminal to the directory you need it to be at. In another terminal type uname -r and hit enter, that will give you the name of your kernel. then in the original terminal type

sudo cp orinoco_ezusb_fw /lib/firmware/`XXX`/

and replace the 'XXX' with your kernel name and hit enter, thats it you are almost done. next in another termonal type 

sudo modprobe -v orinoco_usb

This should start the little light on, if not it will after a restart. Now for the technical part. in a terminal type

sudo nautilus

and hit enter and put in your password, wait a bit and a window will open. In the left panel click "File system", Double click the "lib" file and then double click the "firmware" file. Then right click the file "agere_ap_fw.bin" and choose move to home. do the same with "agere_sta_fw.bin". restart the computer and it should be working like a charm when restarted, close all your windows first. Moving them to the home directory will also avoid a firmware error.

I hope this was easy to follow, The problem is the firmware written by the company that made the card, the firmware is faulty under linux and windows i have been told. this can do wep and gives options for wpa and wpa2 as well for security though I haven't tried them.

---

### Post by learnp on 2011-09-08
Great !! These instructions worked perfectly for a Compaq Wireless LAN  W200 card on a Compaq Evo N610c laptop with a fresh install of **Ubuntu 11.04**.  Thanks much ! The community wiki/instructions are definitely outdated.  The below instructions will probably have to be repeated for every  account on a computer but worked the first time for me - I just had to switch the router to 128-bit WEP encryption.

> **vanquishedangel said:**
> Ok I got this fixed, first off ignore the previous parts of this post as I was trying to figure out the issue at those times and here is a better way to do it that works, that I have found.

First install maverick and then update fully to the latest, or if you can't because of internet access then in stall maverick.

once installed you need to also download just the orinoco-fwutils-0.2 package from here

[http://www.nongnu.org/orinoco/downloads/](http://www.nongnu.org/orinoco/downloads/)

and right click and choose extract here, this file should be located in your downloads file just go to places---> downloads. Go into the extracted file and double click get_ezusb_fw, and choose run in terminal. Then open a terminal and type cd, and drag the extracted folder to the terminal. then hit enter, that will bring the terminal to the directory you need it to be at. In another terminal type uname -r and hit enter, that will give you the name of your kernel. then in the original terminal type

sudo cp orinoco_ezusb_fw /lib/firmware/`XXX`/

and replace the 'XXX' with your kernel name and hit enter, thats it you are almost done. next in another termonal type 

sudo modprobe -v orinoco_usb

This should start the little light on, if not it will after a restart. Now for the technical part. in a terminal type

sudo nautilus

and hit enter and put in your password, wait a bit and a window will open. In the left panel click "File system", Double click the "lib" file and then double click the "firmware" file. Then right click the file "agere_ap_fw.bin" and choose move to home. do the same with "agere_sta_fw.bin". restart the computer and it should be working like a charm when restarted, close all your windows first. Moving them to the home directory will also avoid a firmware error.

I hope this was easy to follow, The problem is the firmware written by the company that made the card, the firmware is faulty under linux and windows i have been told. this can do wep and gives options for wpa and wpa2 as well for security though I haven't tried them.

---

### Post by dakodasara on 2012-02-02
I get to this step:

sudo cp orinoco_ezusb_fw /lib/firmware/`XXX`/

and it gives me this:

cp: cannot stat 'orinoco_ezusb_fw' :  No such file or directory

I believe running get_ezusb_fw pulls orinoco_ezusb_fw to the directory stated above, but it is not actually doing that, any suggestions?

---

### Post by vanquishedangel on 2012-02-08
> **dakodasara said:**
> I get to this step:

sudo cp orinoco_ezusb_fw /lib/firmware/`XXX`/

and it gives me this:

cp: cannot stat 'orinoco_ezusb_fw' :  No such file or directory

I believe running get_ezusb_fw pulls orinoco_ezusb_fw to the directory stated above, but it is not actually doing that, any suggestions?

It seems that you are not in the directory in the terminal would be my guess, your terminal needs to be in the directory the file is in, it has been awhile since I have worked on this computer.

---


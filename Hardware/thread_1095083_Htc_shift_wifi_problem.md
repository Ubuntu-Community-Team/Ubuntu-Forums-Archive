---
title: "Htc shift wifi problem"
date: 2009-03-13
forum: Hardware
---

### Post by Arabiest on 2009-03-13
Recently i bought an HTC SHIFT mini-laptop and since i have been using ubuntu on my earlier Fujitsu T4210 with no problems, i guessed i wont have it here since my HTC SHIFT uses almost the same chipset Intel.

what i have observed that wifi operates manually from within its default operating system Vista which i have completely superceeded by Ubuntu 8.10 and now I am unable to use wifi except wired connection which is working perfectly.

---------------------------------------
root@subaieb-laptop:/home/subaiesb# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:06.0 SD Host controller: Device 1947:4743 (rev 09)

-----------------------------------
root@subaieb-laptop:/home/subaiesb# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:b6:02:ca:99  
          inet addr:192.168.15.4  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::250:b6ff:fe02:ca99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20655 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20656996 (20.6 MB)  TX bytes:3577715 (3.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

----------------------------------------
root@subaieb-laptop:/home/subaiesb# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

-------------------------------------------
root@subaieb-laptop:/home/subaiesb# lsmod
Module                  Size  Used by
ath5k                 116612  0 
lbm_cw_mac80211       215856  1 ath5k
lbm_cw_cfg80211        46744  2 ath5k,lbm_cw_mac80211
led_class              12164  1 ath5k
ipv6                  263972  8 
i915                   38528  2 
drm                    86056  3 i915
af_packet              25728  2 
binfmt_misc            16904  1 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 sco,bnep,rfcomm,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
wmi                    14504  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12680  0 
container              11520  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
wl                   1080212  0 
ieee80211_crypt        13572  1 wl
ndiswrapper           196380  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
asix                   22656  0 
usbnet                 24072  1 asix
uvcvideo               63624  0 
mii                    13440  2 asix,usbnet
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev
snd_hda_intel         384176  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
evdev                  17696  10 
snd_seq_dummy          10884  0 
video                  25232  0 
output                 11008  1 video
battery                18436  0 
ac                     12292  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
serio_raw              13444  0 
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
pcspkr                 10624  0 
snd_rawmidi            29824  1 snd_seq_midi
psmouse                45200  0 
mmc_core               58268  1 sdhci
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 14224  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
ata_piix               24580  2 
pata_acpi              12160  0 
libata                178208  3 ata_generic,ata_piix,pata_acpi
scsi_mod              155212  3 sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
uhci_hcd               30736  0 
usbcore               149360  7 ndiswrapper,asix,usbnet,uvcvideo,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  3 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

------------------------------------
i believe the installation is perfect and complete and all the required drivers do exist....the only thing is how to switch the wifi and bluetooth from within the system since the devise does not have keybopard nor external button to switch it on.....

Please help if u can...

---

### Post by Arabiest on 2009-03-13
hi again, you may advise me to go to the below link which i did but most of its files that are in tar.gz format cant be extracted nor its .deb files are healthy....so please help me.

[http://pof.eslack.org/blog/2008/04/1...-on-htc-shift/](http://pof.eslack.org/blog/2008/04/1...-on-htc-shift/)

---

### Post by Arabiest on 2009-03-14
from another angle, i have contacted HTC technical support to give help or advise as seen below:

----------------------------

Dears,

I am one of your valued customers since many years and before that a customer of I-Mate.

Recently, i have your HTC Touch HD which is a fine piece and wished if it can be Ubuntu-Linux based....but its ok and this is not a concern as of now.

My concern is that I recently bought HTC Shift and becuase I am an ubuntu loyal user, I managed to install it as my only main OS. But discovered that Wifi and bluetooth regardless of touch and any other features which i can live without cant be activated by function keys nor any other hardware buttuns like in some of laptops...

If there is a tweak way of activating it that you rather keep it to your self, but wont hesitate to share it wioth your loyal customer as well, please do...or advise me to a website that has active solution to this.

Also, i would like to suggest if you can add wifi and bluetooth in the command manager of HTC Shift like in any other HTC mobile...this would help...but i believe windows VISTA has advised you not to do so, if they will give you the licence for free.

Please do communicate with me ASAP and doing so, i will ensure that your support will be appreciated in many of the technical forums i am a member in especially ce4arab.com and ubuntu forum as well.

Best Regards,
Arabiest

---

### Post by Arabiest on 2009-03-14
root@subaieb-laptop:/home/subaiesb/Desktop/Documents# dmesg | grep -e ndis -e wlan
[   29.464227] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   29.571177] usbcore: registered new interface driver ndiswrapper
[   29.805851] wlan: 0.9.4
--------------------------------

6. make sure the wireless is turned on

Some computers, particularly laptops, have switches for enabling and disabling wireless cards. Usually this is either a physical button on the outside of the computer, or a software switch that you toggle using key combinations, like function+F2. More often than you might think, wireless issues come down to the card being physically disabled, so if nothing above has helped you yet, make sure that your wireless is turned on.

In rare cases, your wireless card (or the PCI bus holding it) may be disabled in your computer's BIOS for some reason, so if you can't seem to get the system to detect a wireless device at all (even an unclaimed one in the output of lshw -C Network), check BIOS.

---------------------------

the question is how to nswitch it ON if there are no Funtion key indicating it nor an external physical button

---

### Post by pytheas22 on 2009-03-14
It actually doesn't look like Ubuntu is recognizing your wireless device at all--so the problem is not necessarily simply that the radio is turned off.  Please post the output of these commands so that we can get a better idea of what might be wrong:
```

lshw -C Network
dmesg | grep -i -e radio -e ath -e wlan -e ndis
sudo iwlist scan
```

Also, what kind of wireless card do you have?  Is it a USB card or PCMCIA, or an internal one?  I don't see anything that looks like a wireless device mentioned in your 'lspci' output, which is strange.

---

### Post by Arabiest on 2009-03-15
At last....thank u....

to answer your question....IT IS A BUILT IN RADIO...Its an HTC Shift and u can verify from the below Specs (by the way...HTC does not belong to me and i am not promoting here as it may be seen)

Processor and Chipset 	Intel® Processor A110, 800 MHz
Operating System 	Windows Vista® Business
Memory 	RAM: 1GB DDR2 microDIMM RAM for Vista + 64 MB for SnapVUE™
ROM: 128 MB for SnapVUE™
Hard Disk 	1.8-inch 40 GB or 60 GB hard disk (manufacturer's option)
Dimensions 	207 mm (L) X 129 mm (W) X 25 mm (T)
Weight 	800g with battery
Display 	7-inch, 800 X 480 TFT-LCD display with adjustable screen angle and touch-sensitive screen
Network 	HSDPA/UMTS: Tri-band 850, 1900, 2100 MHz
HSDPA: Up to 3.6Mbps for download and 384kbps for upload UMTS: Up to 384kbps for download and upload
GSM/GPRS/EDGE: Quad-band 850, 900, 1800, 1900 MHz (The device will operate on frequencies available from the cellular network)
Keyboard 	Slide-out QWERTY keyboard
Mouse Control 	Left/right mouse buttons and microPad
Wireless Connections 	Bluetooth® 2.0 Wi-Fi®. IEEE 802.11 b/g
I/O Ports 	1 USB 2.0, VGA out, and 3.5mm stereo audio out with microphone
Card Slots 	1.8/3V USIM/SIM card slot
SDIO slot with hotswap functionality
Security 	Fingerprint sensor
Web Camera 	Color CMOS VGA camera for videoconferencing
Audio 	Built-in microphone and dual speakers
Battery 	2700 mAh rechargeable Lithium-ion polymer battery
Vista® operating time: Up to 2 hours
SnapVUE™ standby time (push e-mail enabled): Up to 53 hours
SnapVUE™ standby time (push e-mail disabled): Up to 10 days
AC Adapter 	Voltage range/frequency: 90 ~ 265V AC, 47/63Hz
DC output: 12Vdc, 3A max.

---------------------------
root@subaieb-laptop:/home/subaiesb# lshw -C Network
  *-network:0 DISABLED    
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 0a:75:78:b9:96:a2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: eth0
       serial: 00:50:b6:02:ca:99
       size: 100MB/s
       capacity: 100MB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=14-Jun-2006 duplex=full firmware=ASIX AX88772 USB 2.0 Ethernet ip=10.2.6.101 link=yes multicast=yes port=MII speed=100MB/s
-----------------------------

root@subaieb-laptop:/home/subaiesb# dmesg | grep -i -e radio -e ath -e wlan -e ndis
[   35.448276] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   35.553611] usbcore: registered new interface driver ndiswrapper
[   35.794334] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   35.869119] wlan: 0.9.4
[   35.895546] ath_pci: 0.9.4
-----------------------------

root@subaieb-laptop:/home/subaiesb# sudo iwlist scan
lo        Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
------------------------------------

Once again thank u and hope i could get the cure on your hands!

Saad (Arabiest)

---

### Post by Kevbert on 2009-03-15
Do you have the Windows XP driver files (.inf and .sys) for wireless ? You may be able to use them via ndiswrapper.

---

### Post by Arabiest on 2009-03-15
thank u for trying to help...but if u had not seen this unit before, then it would be diff. to imagine the way it designed....both wifi and BT works from within its OEM Vista OS and since i am a LOYAL Ubuntu i decided to entirely replace it with Ubuntu...what i am trying to say that both wifi and BT are disabled by Bios and for commercial reasons between HTC and Windows to have the BT and WIFI be activated from within Vista...The above snap shots of 

lshw -C Network
dmesg | grep -i -e radio -e ath -e wlan -e ndis
sudo iwlist scan

clearly state a DISABLED unit! and all the required drivers are there and ready once it is switched on from the bios by some means other than Vista if possible....by the way...the unit keyboard does not indicate any Function Key for Radio nor the body has an external swiitch....

**[COLOR="Red"][SIZE="7"]IT SEEMS MICROSOFT DID A HARD DEAL WITH HTC IF THEY WANT TO HAVE THE THEIR OS INSIDE THEIR UNIT[/SIZE][/COLOR]**

---

### Post by pytheas22 on 2009-03-15
In the output you posted, no wireless device appears--Ubuntu can't see any at all.  So it sounds likely that the wireless is just disabled in BIOS, and there's no way Ubuntu can do anything about it until you re-enable the wireless card.  Hopefully you can do that yourself in BIOS, without using Windows; otherwise, you're probably going to have to install Windows again just to turn the wireless on, then reinstall Ubuntu.

There's also a chance that the wireless would come back on if you reset the BIOS by clearing CMOS memory, if you can get access to the motherboard.

---

### Post by Arabiest on 2009-03-15
thank u for the willingness to help and u r right my friend that nothing can be done and just to answer u...i wont install windows and therefore, i bought external wifi and BT and it is working properly and hope HTC would respond to my problem soon and i will share with y their feedback when relieved.

also, with regards to BOIS, there is no chance since ot contains only date and time and booting preference.

Once again thank u

Saad:(

---

### Post by Arabiest on 2009-03-15
My HTC Shift PC after external WIFI and BT working fine as expected from my beloved ubuntu

[IMG]http://i267.photobucket.com/albums/ii304/Arabiest/HTCSHIFTMINISCREEN-1.jpg[/IMG]

---

### Post by Arabiest on 2009-03-15
THIS IS HTC.COM REPLY BACK SHARED FOR YOUR INFO...
----------------------
Thank you for choosing HTC the PDA maker to the world In regards to your inquiry, as the Bluetooth and Wi-Fi are software enabled features on your device's operating system "SnapVUE", and as you changed the operating system on your device –which is not recommended- therefore, you would not be able to enable such features on your device as long as the current operating system you have on your device does not support enabling those features. Please do not hesitate to contact us back for any inquires. HTC Corporation Middle East Support Team Sincerely, 	2009/03/15 23:18:49 
-----------------------

MY FINAL REPLY TO THEM IS:

i understand your message and i've realized that your answer is since i have changed the OS system to ubuntu, i wont be able to activate WIFI & BT since it can only be activated from VISTA.

But my FINAL claim is whether the devise has HIDDEN Function Key to activate the WIFI & BT since the keyboard does not illustrate the same that you might guide me to it please.

I wish to hear your final reply back ASAP.

---

### Post by avdzm on 2009-11-21
Hey guys,
The wireless and bluetooth work fine with me,
Although I have ubuntu 8.04 installed, but it still works.

And I take it, that you guys haven't googled.

Here is a link, to guide you how to enable them.
[http://pof.eslack.org/blog/2008/04/14/linux-on-htc-shift/](http://pof.eslack.org/blog/2008/04/14/linux-on-htc-shift/)

---

### Post by lotech on 2011-03-28
Any update ? I googled for days but can't find any solution, all info I can get is outdated doesn't work with 10.10, and I read somewhere the Shift has build in GPS but can only activate via windows with special tool, but without wifi the Shift is just another paper weight to me, so I desperately need wifi working, I appreciate any help thanks !!

---

### Post by pytheas22 on 2011-03-29
> Any update ? I googled for days but can't find any solution, all info I can get is outdated doesn't work with 10.10, and I read somewhere the Shift has build in GPS but can only activate via windows with special tool, but without wifi the Shift is just another paper weight to me, so I desperately need wifi working, I appreciate any help thanks !!

What happens when you try following the instructions on [this site]("http://pof.eslack.org/2008/04/14/linux-on-htc-shift/") to get the wifi working?  I see from comments there that those instructions seem not to work on Ubuntu 10.10, but no one is specific about what goes wrong.  If you could try following the directions and post all the output you get, maybe we can work through the issues and make the wifi work.

It would also be good to know the output of:
```

lspci -nn
lsusb
uname -a
lshw -C Network
```

just so I know more about your software environment.

Let's try to take care of the wifi first, before thinking about the GPS.

---

### Post by daehenoc on 2011-04-20
OK, I've just put Ubuntu on my HTC Shift and I'm going to go to the pof web site and see if I can get wireless working - I've read that page before I started putting Ubuntu on this Shift, and it seems that the firmware for the wireless card is no longer available, but anyway...

Here is the output of the commands listed by pytheas22:
> $ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
01:06.0 SD Host controller [0805]: C-guys, Inc. CG200 Dual SD/SDIO Host controller device [1947:4743] (rev 09)
> $ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 002: ID 2001:3c05 D-Link Corp. [hex] DUB-E100 Fast Ethernet [asix]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
> $ uname -a
Linux monitor 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux
> $ sudo lshw -C Network
  *-network               
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:80:c8:38:76:a6
       size: 100MB/s
       capacity: 100MB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=14-Jun-2006 duplex=full firmware=ASIX AX88772 USB 2.0 Ethernet ip=10.1.23.16 link=yes multicast=yes port=MII speed=100MB/sI'm going to go digging in the BIOS to double check that the wireless is enabled...  OK, the BIOS doesn't have any option to turn the wireless on or off.  It almost has zero options at all!

There is a USB-Ethernet adapter plugged into the Shift now, which is what you can see reported above.

---

### Post by daehenoc on 2011-04-21
> **pytheas22 said:**
> What happens when you try following the instructions on [this site]("http://pof.eslack.org/2008/04/14/linux-on-htc-shift/") to get the wifi working?  I see from comments there that those instructions seem not to work on Ubuntu 10.10, but no one is specific about what goes wrong.  If you could try following the directions and post all the output you get, maybe we can work through the issues and make the wifi work.The problem with these instructions is that it appears that there are no source files for the sd8686.ko module in Ubuntu.

I've found the source for the sd8686.ko off the Marvell web site here: [http://extranet.marvell.com/drivers/driverDisplay.do?driverId=203](http://extranet.marvell.com/drivers/driverDisplay.do?driverId=203) but I am not very good at compiling modules and haven't been able to get the module to compile successfully.

Apparently the libertas driver is an open source version of the Marvell driver, but I haven't been able to get the libertas module (libertas-sdio) to load and subsequently use the sd8686.bin firmware.

I have 10.04 installed on the Shift, and had no luck with libertas, found that sd8686.bin is included in 10.10, so I put 10.10 on a USB key and booted the Shift off that but still no joy.

---

### Post by pytheas22 on 2011-04-21
**daehenoc**: for starters, are you positive the wireless hardware in your laptop is actually enabled and working?  I don't see anything that looks like a wireless card in your "lspci" output (there is a wireless card mentioned by "lsusb" but I presume that's the one you're only using temporarily).  If the system doesn't think the hardware is present, that will need to be solved before you can move on to finding a driver for the hardware.

Did you complete the step in the POF instructions where you run "sudo ./install.sh kernel"?  I am not completely sure, but it seems that that should perform the magic necessary for the built-in ethernet device to become visible, and make it show up in your lsusb or lspci output.  I think you'll need to make that happen before you'll be able to do anything with the driver.

If you're lucky, the libertas module will be able to drive the device once the hardware becomes visible; if not, we can try making the source code compile.  (I couldn't get it to compile on the first try either because it complained about CFLAGS issues, but I think those should be easy to fix by editing the Makefile...of course, there's no guarantee that that's not the only problem to be overcome.)

---

### Post by daehenoc on 2011-04-21
> **pytheas22 said:**
> **daehenoc**: for starters, are you positive the wireless hardware in your laptop is actually enabled and working?You know, I was wondering the same thing myself, I thought that maybe the wifi card was somehow hidden behind the SDIO controller?  I'm going to put Windows back onto the device and check if the wireless is working in Windows or not.
> **pytheas22 said:**
> Did you complete the step in the POF instructions where you run "sudo ./install.sh kernel"?  I am not completely sure, but it seems that that should perform the magic necessary for the built-in ethernet device to become visible, and make it show up in your lsusb or lspci output.  I think you'll need to make that happen before you'll be able to do anything with the driver.I've had a look through the script and the only magic the script does is copy the correct kernel version modules to the correct locations.

I will report back once I've tested the h/w in Windows.

---

### Post by daehenoc on 2011-04-22
Alright, I have been playing around with this device and I was pretty sure that the wireless was not turned on at all - I have a copy of Win7 here and I installed that and tried to get the HTC Control Centre s/w working, which is tricky (run in compatibility mode, install as administrator) since the drivers available from the HTC site are for Vista - your mileage will vary.

I have not been able to get the required software and drivers for the control center installed and working and been able to successfully reboot the Shift - I have gotten the Control Center software working once, and could see that the Wireless and Bluetooth devices were turned off!  I turned them on, and rebooted, but Win7 just bluescreens on me.

I've subsequently booted the Shift off a USB with Ubuntu 10.10 on it, but the wireless device was not discovered.  So not really sure where to go from here, unless the wireless device **requires** a working installation of Windows, with the Control Center software installed before it will stay on past a reboot!!!

---

### Post by pytheas22 on 2011-04-23
hmmm, it seems dumb to make the wireless only controllable via a software switch within Windows, but that may be how it was designed.  Unfortunately I'm not sure what to do, other than contact the company and ask about it.

It might also theoretically be possible to install Windows inside VirtualBox or KVM in Ubuntu and then "pass through" the hardware device that Windows needs to interact with to control the wireless so that you could enable the latter.  Really I doubt this would work in practice, but it's the only other thought I have.

---

### Post by daehenoc on 2011-04-23
> **pytheas22 said:**
> hmmm, it seems dumb to make the wireless only controllable via a software switch within Windows, but that may be how it was designed.  Unfortunately I'm not sure what to do, other than contact the company and ask about it.

It might also theoretically be possible to install Windows inside VirtualBox or KVM in Ubuntu and then "pass through" the hardware device that Windows needs to interact with to control the wireless so that you could enable the latter.  Really I doubt this would work in practice, but it's the only other thought I have.You would think so, huh!!!  I have now successfully gotten Win7 installed and wrestled the drivers into submission and can now reboot the device without Win7 bluescreening on boot, and subsequently run the Control Center software and turn the 3G modem, bluetooth and wireless radios on and off.  When Win7 starts up, the wireless network icon has the little blue circle like the radio can see a network and is about to connect to it, but then the blue circle goes away and Windows cannot find any networks at all.

Even when turning on all the above radios and rebooting the Shift off a Ubuntu 10.10 USB key, I still can not see the wireless radio in Ubuntu.

Well, I give up.  I've put quite a few hours into this device, so I conclude that the radio is broken, or ... something.  I'm going to use this Shift to monitor my UPS, and have a 4-port USB hub attached so that I can attach the USB->Ethernet adapter as well as the UPS.

---

### Post by pytheas22 on 2011-04-24
Well, that does sound like a hardware issue.  At least we know it's not just Ubuntu, because I was pretty puzzled as to what could be going on there other than hardware problems.  It's still strange that Windows can at least detect the hardware being present while Ubuntu can't, but the fact that Windows can't actually connect probably means, as you say, that the radio on the device is broken, or that there's some other sort of strange problem.

At least you can put it to work on your UPS...

---


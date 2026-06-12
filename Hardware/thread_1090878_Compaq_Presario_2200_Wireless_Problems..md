---
title: "Compaq Presario 2200 Wireless Problems."
date: 2009-03-08
forum: Hardware
---

### Post by Seuche on 2009-03-08
Hiya wonderful people of the Ubuntu Forums, I have turned to you for help!

I've recently got my hands on a Compaq Presario 2200, used to be my Dad's but after sitting under his bed for almost a year he gave it to my bro, two weeks after he got it he ran an update on it and XP died on him. He gave it to me at first with the intention of me fixing it, dunno why all I do is scour tech support forums...half the time I fix the comps I'm on another comp scouring the internet for fixes and explanations. Anywho found out to fix it we'd basically need to run XP off the disc or reinstall it. Since we don't know where the original disc has gone off to and of course the fact that computer stores in the area don't carry XP anymore, they've all filled their shelves with Vista. My bro just gave the dead comp to me to keep, since I"m the only one in my family that seems to want to even think of using a Linux or Unix Distribution, even though many times I find using Ubuntu, which I have on my old laptop, alot easier to use than any windows I've used to date.

Anywho enough rambling, on to the Problem!!

Since I've basically fallen in love with Ubuntu while using it on my old Inspiron 600m, I decided to install it on the Compaq Presario 2200 and upgrade to the newer laptop. So I just intsalled the most recent Ubuntu, 8.10 I think, and thought 'awesome! I got a new comp, and its free of junk files!' then I ran into the problem. I can't get the Wireless to work! As I'm on the Internet most of the time when I'm on my Laptop the wireless not working is kinda making my new hand-me-down comp kinda useless, I can still type things, edit pictures, and what not, but to move those things onto the net, I'll need to find a portable drive with enough space to do so. Anyways, the Compaq has a little button that apparently was supposed to turn on and off the wireless. Well I press it, nothing happens, I hold the button for a few seconds, nothing happens, I hold the button for a minute or two, and nothing happens. 

So my question is, Is there anyway I can my wireless to work on the Compaq some how, or is it going to have to spend the rest of its electronic life as a glorified data storage place?

if there is anything info you guys need to help me just ask and I will do my best to supply it. though if it requires me to do anything fancy with the terminal you'll probably need to tell me what to input into the terminal.

Thank you for any and all help you wonderful people can give me!

---

### Post by Seuche on 2009-03-11
Not a single person has any idea what might be wrong or how to find out whats wrong? Someone? Anyone? Please?

---

### Post by mountzionryan on 2009-03-13
> **Seuche said:**
> Not a single person has any idea what might be wrong or how to find out whats wrong? Someone? Anyone? Please?

I hope we get an aswer I am in exactly the same boat.  Friend gave me the Presario 2200, finally getting to try dedicate a machine solely to Ubuntu and no wireless.

---

### Post by mountzionryan on 2009-03-13
ON a Presario 2200 here's all the info from terminal:


ryan@ryan:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13fe:1e00 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ryan@ryan:~$ lspci -nn | grep 'Broadcom'
02:06.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

ryan@ryan:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


ryan@ryan:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ryan@ryan:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
usb_storage            81728  1 
libusual               27156  1 usb_storage
ipv6                  263972  8 
af_packet              25728  2 
rfkill_input           12672  0 
i915                   38144  2 
drm                    86056  3 i915
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
pcmcia                 43052  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
b43                   131356  0 
rfkill                 17176  2 rfkill_input,b43
mac80211              216820  1 b43
cfg80211               32392  1 mac80211
evdev                  17696  9 
led_class              12164  1 b43
snd_intel8x0           37532  3 
input_polldev          11912  1 b43
snd_ac97_codec        111652  1 snd_intel8x0
psmouse                45200  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
serio_raw              13444  0 
yenta_socket           31756  1 
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_dummy          10884  0 
container              11520  0 
video                  25104  0 
output                 11008  1 video
pcspkr                 10624  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
wmi                    14504  0 
battery                18436  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
ac                     12292  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                 14224  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  5 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  2 
pata_acpi              12160  0 
8139cp                 27520  0 
ata_generic            12932  0 
libata                177312  3 ata_piix,pata_acpi,ata_generic
ssb                    40580  1 b43
8139too                31616  0 
mii                    13440  2 8139cp,8139too
uhci_hcd               30736  0 
ehci_hcd               43276  0 
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
usbcore               148848  5 usb_storage,libusual,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

ryan@ryan:~$ sudo lshw -C network
[sudo] password for ryan: 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:6d:2b:ea
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:b5:f8:0b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7e:73:0c:ad:6b:14
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


ryan@ryan:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.


ryan@ryan:~$ uname -mr
2.6.27-7-generic i686

ryan@ryan:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 



PLease Help!

---

### Post by go2dell on 2009-04-28
Have you installed the proprietary drivers?  The Broadcom 4306 requires a proprietary driver using the "b43-fwcutter" package.  In Ubuntu it's completely painless to install, but it will require a working Internet connection to download the correct driver -- which is completely automatic, btw.

You should be heavily warned that the bcm4306 is painfully slow, and nobody seems to know the reason why.  It's not a Linux problem, since it's possibly very slightly faster on Linux platforms than on Windows.  It will easily outstrip whatever your Internet connection can do, but if you expect to transfer lots of files on your own wireless LAN, then expect to become intimately familiar with the port for a Cat5 cable.

Unfortunately, since Broadcom is more concerned with making money than with producing quality products, they flat refuse to provide any assistance to anyone concerning creating good open source firmware for their products, and thus the performance will likely always suck.

Just as a side note, the latest Ubuntu, 9.04, was just released, so you may want to go ahead and install that to get started.

If you can plug in a wired Internet connection now, go to System > Administration > Hardware Drivers and it should find your bcm4306 and offer to install it for you.

---

### Post by DavidP01 on 2009-05-17
I do not have the solution but I do hold out hope. I had this very problem and spent all night reading forums etc. Eventually it all came good. For what it is worth I just updated to Jaunty and it seems to be OK now.

---

### Post by go2dell on 2009-05-17
The solution is in my post above.

---

### Post by tdjr86 on 2009-11-08
Go2Dell, 

What you suggested with the Administration > Hardware Drivers does not work...

However, I solved this problem from what I found in another thread....[http://ubuntuforums.org/showpost.php?p=5469730&postcount=13](http://ubuntuforums.org/showpost.php?p=5469730&postcount=13)

Worked perfect for me.

Hope this helps.

---

### Post by blackduck on 2009-11-19
> **go2dell said:**
> Have you installed the proprietary drivers?  The Broadcom 4306 requires a proprietary driver using the "b43-fwcutter" package.  In Ubuntu it's completely painless to install, but it will require a working Internet connection to download the correct driver -- which is completely automatic, btw.

You should be heavily warned that the bcm4306 is painfully slow, and nobody seems to know the reason why.  It's not a Linux problem, since it's possibly very slightly faster on Linux platforms than on Windows.  It will easily outstrip whatever your Internet connection can do, but if you expect to transfer lots of files on your own wireless LAN, then expect to become intimately familiar with the port for a Cat5 cable.

Unfortunately, since Broadcom is more concerned with making money than with producing quality products, they flat refuse to provide any assistance to anyone concerning creating good open source firmware for their products, and thus the performance will likely always suck.

Just as a side note, the latest Ubuntu, 9.04, was just released, so you may want to go ahead and install that to get started.

If you can plug in a wired Internet connection now, go to System > Administration > Hardware Drivers and it should find your bcm4306 and offer to install it for you.

I followed your advice and installed b43 ok as Sys > Admin > Hardware reports that it is in use. Like mountzionryan I was given a Compaq Presario R3000 with winxp on board. The wireless, complete with blue indicator light was working just before partitioning & installation of ubuntu 9.04, and then upgraded to 9.10. Any suggestion to solve will be hoisted aboard gratefully.

---


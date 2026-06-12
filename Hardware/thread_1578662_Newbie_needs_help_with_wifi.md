---
title: "Newbie needs help with wifi"
date: 2010-09-20
forum: Hardware
---

### Post by czarjosh on 2010-09-20
I just picked up a Dell Vostro 1000.  I installed Ubuntu 10.04 on it the other day.  It has an AMD 64 Athlon X2 processor.   Everything went fine on the install and when I first started using the machine it found my wireless network.   After a restart I get a "Wireless is disabled" message under my network settings area.

I found this thread:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

and started to work through it.

WHen I enter:

lspci -vvnn | grep 14e4


I get:

05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

When I enter:

sudo modprobe -r b43 ssb wl

I get:

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module ssb is in use.


I am not sure what I did wrong.   I tried some other commands I found on older threads and I do not recall what they were, so I am lost and still do not have any wifi.

---

### Post by Iowan on 2010-09-20
Right-click on the Network Manager icon and verify that Networking and Wireless are still enabled. Here are a few threads that might be useful:
[http://ubuntuforums.org/showthread.php?t=1564615]("http://ubuntuforums.org/showthread.php?t=1564615")
[http://ubuntuforums.org/showthread.php?t=1484913]("http://ubuntuforums.org/showthread.php?t=1484913")
[http://ubuntuforums.org/showthread.php?t=1505217]("http://ubuntuforums.org/showthread.php?t=1505217")
[http://ubuntuforums.org/showthread.php?t=1537792]("http://ubuntuforums.org/showthread.php?t=1537792")

---

### Post by czarjosh on 2010-09-20
> **Iowan said:**
> Right-click on the Network Manager icon and verify that Networking and Wireless are still enabled. Here are a few threads that might be useful:
[http://ubuntuforums.org/showthread.php?t=1564615]("http://ubuntuforums.org/showthread.php?t=1564615")
[http://ubuntuforums.org/showthread.php?t=1484913]("http://ubuntuforums.org/showthread.php?t=1484913")
[http://ubuntuforums.org/showthread.php?t=1505217]("http://ubuntuforums.org/showthread.php?t=1505217")
[http://ubuntuforums.org/showthread.php?t=1537792]("http://ubuntuforums.org/showthread.php?t=1537792")
Enable NEtworking is checked. Enable Wireless is greyed out an d I am unable to check it.

---

### Post by Yellow Pasque on 2010-09-20
Tried restarting after installing the new driver? (the modprobe is a workaround to avoid this, but it doesn't work...)

---

### Post by czarjosh on 2010-09-24
I did.  I am still stuck.

---

### Post by czarjosh on 2010-10-11
I am still stuck on this.  I just did a fresh install and I am getting the same problem.   I wanted to paste some outputs to see if anyone of is useful to all of you.

"Enable Wireless" is greyed out.

$ lspci -vnn | grep 14e4
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)


$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:b7:c6:21  
          inet addr:192.168.1.39  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:feb7:c621/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3258970 (3.2 MB)  TX bytes:455334 (455.3 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

$ iwlist scan
lo        Interface doesn't support scanning.

eth2      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

$ lsmod
Module                  Size  Used by
nls_iso8859_1           4657  1 
nls_cp437               6375  1 
vfat                   10954  1 
fat                    56244  1 vfat
usb_storage            50372  1 
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
joydev                 11363  0 
snd_hda_codec_idt      64667  1 
radeon                906714  3 
snd_hda_intel          26019  2 
snd_hda_codec         100919  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
ttm                    68212  1 radeon
snd_seq_midi            5932  0 
drm_kms_helper         32836  1 radeon
snd_rawmidi            22207  1 snd_seq_midi
b44                    31274  0 
ssb                    46169  1 b44
mii                     5261  1 b44
drm                   206161  5 radeon,ttm,drm_kms_helper
snd_seq_midi_event      7291  1 snd_seq_midi
lib80211_crypt_tkip     8732  0 
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
i2c_algo_bit            6208  1 radeon
wl                   1965231  0 
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                3372  0 
lib80211                6175  2 lib80211_crypt_tkip,wl
dell_laptop             6722  0 
snd                    64117  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  6910  1 dell_laptop
edac_core              46822  0 
psmouse                62080  0 
serio_raw               4910  0 
i2c_piix4              10047  0 
shpchp                 34910  0 
k8temp                  4064  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
edac_mce_amd            9387  0 
video                  22176  0 
output                  2527  1 video
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   21857  0 
sdhci_pci               7765  0 
libahci                26167  3 ahci
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci
pata_atiixp             4405  0

---

### Post by sgosnell on 2010-10-11
Your wireless card isn't necessarily wlan0.  On my system, it's wlan1.

---

### Post by czarjosh on 2010-10-11
Yes.  I think mine is "lo"

---

### Post by czarjosh on 2010-10-11
I mean eth2

---

### Post by sgosnell on 2010-10-11
Have you tried enabling eth2?

---

### Post by czarjosh on 2010-10-11
How do I do that through the command line?

---

### Post by sgosnell on 2010-10-12
sudo ifconfig eth2 up

But first try running "sudo iwconfig" and see what interfaces you get.  Then try replacing eth2 with what you see, if anything.

---


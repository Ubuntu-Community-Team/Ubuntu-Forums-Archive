---
title: "Trouble Connecting to Wireless Router"
date: 2007-07-04
forum: Hardware &amp; Laptops
---

### Post by khaledaboualfa on 2007-07-04
Ok the issue I'm having issues connecting to my wireless network. In the top right hand corner my Network Manager shows the available network and the little shield (which I guess implies that the network is password protected). 

When I click on it and use either the WEP 128Bit passphase or 64/128-bit hex option, both as either open system or shared key (not that I actually understand what the difference is but I've tried both in any case). What happens is that the searching icon in the panel at the top does nothing but keeps looking for a while and then fails.

So I've looked on the forums and found this command which might help in finding out what's wrong with the connection:
1. **lshw -short | grep network**
gives me:
**/0/c0000000/le/a eth0 network PRO/Wireless LAN 2100 3B Mini PCI Adapter**

2. **iwconfig**
gives me:
lo no wireless extensions

eth0 unassociated ESSID: off/any Nickname:"ipw2100"
Mode: Managed Channel=0 Access Point: Not Associated
Bit Rate= 0kb/s Tx-Power:16 dBm
Retry limit: 7 RTS thr: off Fragment thr: off
Encryption key: off
Power Management: off
link quality: 0 signal level: 0 noise level: 0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I've also installed the windows drivers (just in case) but that doesn't seem to do anything to be honest.

Any thoughts on what I should do would be really appreciated. Thank you.

---

### Post by d3n0 on 2007-07-04
Output of lspci and lsmod.

---

### Post by khaledaboualfa on 2007-07-04
lspci give me:

```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XP4m32 (rev 91)
02:0a.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)

```

While lsmod give me:
```

Module                  Size  Used by
nls_iso8859_1           5120  0 
nls_cp437               6784  0 
vfat                   14208  0 
fat                    53916  1 vfat
usb_storage            72256  0 
libusual               17936  1 usb_storage
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ipv6                  268704  10 
ppdev                  10116  0 
speedstep_centrino      9920  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  1 
freq_table              5792  3 speedstep_centrino,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
toshiba_acpi           11972  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
dock                   10268  0 
button                  8720  0 
battery                10756  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  2 toshiba_acpi,asus_acpi
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
snd_intel8x0           34204  1 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
joydev                 10816  0 
pcmcia                 39212  0 
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ipw2100                72244  0 
ieee80211              34760  1 ipw2100
ieee80211_crypt         7040  1 ieee80211
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
pcspkr                  4224  0 
psmouse                38920  0 
serio_raw               7940  0 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
intel_agp              25116  1 
agpgart                35400  1 intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
tsdev                   8768  0 
evdev                  11008  4 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  3 
ata_piix               15492  4 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 usb_storage,sg,sd_mod,libata
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  5 usb_storage,libusual,ehci_hcd,uhci_hcd
raid10                 26240  0 
raid456               126480  0 
xor                    16648  1 raid456
raid1                  25600  0 
raid0                   9600  0 
multipath               9856  0 
linear                  7296  0 
md_mod                 79764  7 raid10,raid456,raid1,raid0,multipath,linear
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
dm_mod                 59084  4 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability


```

---

### Post by d3n0 on 2007-07-04
check if this helps, and try firts without encryption:

[http://ubuntuforums.org/archive/index.php/t-215925.html](http://ubuntuforums.org/archive/index.php/t-215925.html)

and i also forgot, what is that for a notebook? and output of "ifconfig -a".

---

### Post by khaledaboualfa on 2007-07-04
First off, thanks ever so much for all of your help it's much appreciated. This is for my Toshiba R100 laptop. Based on my experiences with this laptop so far, (I honestly wouldn't recommend it for Ubuntu use for many reasons but I'll be writing about that on my site, far too many bugs associated).

Now I went through that thread and tried most things, seems the guy was going through the same thing as me, but there doesn't seem to have been a full resolution. 

Typing: **sudo iwconfig eth0 essid "your essid"** (putting in the proper essid, which is my username for the wireless network right?)

Doesn't give me any output. Does it matter that the router has WEP encryption on it? Should I have another line to put the password in there as well?

Typing: **sudo ifconfig eth1 down** gives me an error message:

eth1: ERROR while getting interface flags: No such device

Finally typing in: **sudo dhclient eth0 ** gives me the following output:
```
There is already a pid file /var/run/dhclient.pid with pid 5869
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:04:23:93:3a:74
Sending on   LPF/eth0/00:04:23:93:3a:74
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```


Typing in **ifconfig -a** gives me:
```
eth0      Link encap:Ethernet  HWaddr 00:04:23:93:3A:74  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x6000 Memory:dfdff000-dfdfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by d3n0 on 2007-07-04
you don't have to type 'sudo ifconfig eth1' you don't have that device, and your wireless card is eth0. yes it does matter that wep encryption is on, that is why i have said that you may first try without it. but, this is from man iwconfig:[HTML] key/enc[ryption]
              Used to manipulate encryption or scrambling keys and security mode.
              To  set the current encryption key, just enter the key in hex digits as XXXX-XXXX-XXXX-XXXX or XXXXXXXX.  To set a key other than the current
              key, prepend or append [index] to the key itself (this won’t change which is the active key). You can also enter the key as an  ASCII  string
              by using the s: prefix. Passphrase is currently not supported.
              To change which key is the currently active key, just enter [index] (without entering any key value).
              off and on disable and reenable encryption.
              The  security  mode  may  be open or restricted, and its meaning depends on the card used. With most cards, in open mode no authentication is
              used and the card may also accept non-encrypted sessions, whereas in restricted mode only encrypted sessions are accepted and the  card  will
              use authentication if available.
              If  you  need  to set multiple keys, or set a key and change the active key, you need to use multiple key directives. Arguments can be put in
              any order, the last one will take precedence.
              Examples :
                   iwconfig eth0 key 0123-4567-89
                   iwconfig eth0 key [3] 0123-4567-89
                   iwconfig eth0 key s:password [2]
                   iwconfig eth0 key [2]
                   iwconfig eth0 key open
                   iwconfig eth0 key off
                   iwconfig eth0 key restricted [3] 0123456789
                   iwconfig eth0 key 01-23 key 45-67 [4] key [4]
[/HTML]

so i presume you could try something like 'iwlist essid "your network" key "your key". since i use wpa and wpa_supplicant on my gentoo notebook am not sure but i think/hope you should be fine with this. in case it didn't work  i would continue reading man pages and debian docs. the card is supported so there should be a way of make it work. so donÄT give up ;).

---

### Post by d3n0 on 2007-07-05
Any news?

---

### Post by khaledaboualfa on 2007-07-05
I thought I'd typed it in, hehe oops, thanks for getting back to me. Basically yeah I typed in:

**iwlist essid "my network" key "my key"**

And got a list which said:
iwlist [interface] scanning
         [interface] frequency
         [interface] channel

and a bunch of other things.

Here's the thing, I don't know how to remove the wep encryption. I'm visiting and trying to connect to their network. The thing is though I've got the password, and obviously the network is being 'caught' how can I connect to the wireless network say from the terminal rather than the network manager? 

The thing that I have noticed however that's making me wonder that it's not the actual encryption is the fact that there is another network that doesn't seem to be password protected (it doesn't have the shield unlike all the other networks I'm picking up, including my own) that I'm picking up and I'm just testing to see if I can actually get connected and it does the same thing, so obviously there's something wrong somewhere else?

Once again thanks for all your help. I'll definitely write this up in the wiki if I get it to work :).

---

### Post by khaledaboualfa on 2007-07-05
Here's the latest development. Basically I tried and manually configured the connection (as opposed to enabling roaming) and nothing happened, however when I went back to roaming for some reason the two little screens had converted into the 5 bars that tell you the level of the actual signal. The level is shown as 0% in the bars but clicking on it and having a look at the strength of the network (and the other networks as well) shows a completely different story. Something is really screwy here.

Finally I had a look at the documentation found here again:
[https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#internet-basic-procedure](https://help.ubuntu.com/7.04/internet/C/connect-to-internet.html#internet-basic-procedure)

I have no idea why the option networking cannot be found here, but network manager is showing up in the top right hand corner (and displaying available networks) so I don't know what the problem is there.

---

### Post by d3n0 on 2007-07-05
Btw. command is iwconfig not iwlist. Ever heard for man pages? man iwlist, man iwconfig. Further when you try to connect on not yours access points even if they are not using encryption they may filter MAC addresses and prevent essid to be broadcast.

---

### Post by khaledaboualfa on 2007-07-06
Ahh well I typed in 

**iwconfig essid "my network" key "my key"**

and this time I got the following error:

Error : unrecognised wireless network request "my network"

That seems strange, network manager obviously can see it. Is there somewhere which could be blocking this?

---

### Post by d3n0 on 2007-07-06
:D no, no, you should not type "my netrowk". you should type essid, the name of your network. same for the key. you are not going to type "my key".

---

### Post by khaledaboualfa on 2007-07-06
:) No, no, I know I know, I didn't type 'my network', I actually put in the name of my network, (which in this case it was aboualfa), and I put the numbered key in there as well. Here's the thing, for the key we've got 10 numbers. Do I have to convert them into something different (like hex or ascii or whatever) before I type them in or does it matter?

---


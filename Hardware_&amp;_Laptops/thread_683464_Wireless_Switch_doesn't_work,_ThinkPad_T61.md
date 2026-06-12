---
title: "Wireless Switch doesn't work, ThinkPad T61"
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by MattK358 on 2008-01-31
Hey everyone,

I'm using Ubuntu Gutsy 7.10 on a ThinkPad T61, following this guide ([http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61)) and I'm having some trouble. The biggest problem so far, is while that article lists the Wireless switch works "out of the box" I am finding it to be completely ineffective, I have the "ThinkPad 11a/b/g" Atheros chipset, and no matter which way I toggle the hardware switch, or if I try using Fn+F5, the WiFi radio is powered up. This is not only inconvenient but it prevents me from realistically using the computer as I frequently operate on battery without wireless and need the extra power.

I've run every update I can, I followed the guide and everything else is working more or less completely fine, but I need that switch to work.
Also, the bluetooth script provided in that guide does not work at all as well, it seems like my /proc filesystem is resilient to change, because running the commands in the script manually as root yields no change.

```

root@Gigan:~# cd /proc/acpi/ibm/
root@Gigan:/proc/acpi/ibm# echo enable > bluetooth 
root@Gigan:/proc/acpi/ibm# cat bluetooth 
status:         enabled
commands:       enable, disable
root@Gigan:/proc/acpi/ibm# 

```

As you can see, there is no change to the files contents, nor does the Bluetooth LED light, so it appears that it just isn't working.
I am not sure where to proceed from here, suggestions please?

Also, here is my lspci output

```

root@Gigan:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
root@Gigan:~# 

```

And my lsmod output

```

root@Gigan:~# lsmod
Module                  Size  Used by
hci_usb                18332  0 
ipv6                  273892  10 
wlan_tkip              13696  1 
wlan_ccmp               9600  1 
af_packet              24840  4 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  5 hci_usb,rfcomm,l2cap
thinkpad_acpi          44588  0 
ppdev                  10244  0 
acpi_cpufreq           10568  1 
cpufreq_ondemand        9612  1 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
video                  18060  0 
container               5504  0 
bay                     6912  0 
dock                   10656  1 bay
battery                11012  0 
ac                      6148  0 
sbs                    19592  0 
button                  8976  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
joydev                 11328  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4740  0 
pcmcia                 41388  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
uvcvideo               48644  0 
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wlan_scan_sta          15104  1 
compat_ioctl32          2304  1 uvcvideo
ath_rate_sample        14208  1 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
psmouse                39952  0 
yenta_socket           27532  1 
videodev               29312  1 uvcvideo
v4l1_compat            15364  2 uvcvideo,videodev
snd                    54660  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                  4224  0 
nvidia               7822336  36 
serio_raw               8068  0 
rsrc_nonstatic         14080  1 yenta_socket
v4l2_common            18432  2 uvcvideo,videodev
ath_pci                98336  0 
wlan                  206660  6 wlan_tkip,wlan_ccmp,wlan_scan_sta,ath_rate_sample,ath_pci
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
usbhid                 29536  0 
i2c_core               26112  1 nvidia
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
ath_hal               192720  3 ath_rate_sample,ath_pci
hid                    28928  1 usbhid
intel_agp              25620  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
agpgart                35016  2 nvidia,intel_agp
evdev                  11136  5 
usb_storage            73024  0 
ide_core              116804  1 usb_storage
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
libusual               18448  1 usb_storage
sd_mod                 30336  3 
ata_piix               17540  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ahci                   23300  2 
ata_generic             8452  0 
ehci_hcd               36492  0 
libata                125168  3 ata_piix,ahci,ata_generic
scsi_mod              147084  6 sbp2,sr_mod,usb_storage,sg,sd_mod,libata
e1000                 126272  0 
uhci_hcd               26640  0 
usbcore               138632  8 hci_usb,uvcvideo,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
root@Gigan:~# 

```

Matt

---

### Post by MattK358 on 2008-02-06
Nobody has any idea?

---

### Post by ihavenoideax2 on 2008-02-06
Mine works perfect out of the box. I wonder if it might be because you have the Thinkpad wifi and i have the Intel 3945abg card. It shouldn't matter i would think but i have seen stranger. Currently I'm trying to get aps to work but have had no success in that. But other than that everything worked almost right right out of box including the Bluetooth script.

---

### Post by el_perseguidor on 2008-03-18
I also have the Intel wireless card, and wireless works from the beginning. What happens to me is that using either the switch or the Fn+F5 I can switch off the wireless (or at least I loose the Internet connection, I have no idea if the radio is consuming power since the wireless LED doesn't work) but then I can never get the connection back again. The only way seems to be rebooting. 
How can I check that the wireless radio is effectively switched off? And what can I do to get the connection back afterwards?

---

### Post by Am6er on 2008-03-21
Hi everyone, i had the same problem on my T41 with Intel 2100 3B wireless adapter (ipw2100).
(Sorry for my English). :(

I solved that problem by separating Bluetooth and Wireless switcher to different keys:
Fn+F5 switches my Bluetooth adapter and Fn+F6 swithches my ipw2100.
Maybe this method can be helpfull for you. So, first of all, i caught microcodes of Fn+F5 and Fn+F6 by acpi_listen utility:
```
Fn+F5 -- ibm/hotkey HKEY 00000080 00001005
Fn+F6 -- ibm/hotkey HKEY 00000080 00001006
```

Then i found in /etc/acpi/events some events, that activate scripts in /et/acpi with this two strings above. I bakup and remove this events from /etc/acpi/events and create my own:
For Fn+F5:
amber@amba:/etc/acpi/events$ cat ibm-bth 
```

### File: /etc/acpi/events/ibm-bth
event=ibm/hotkey HKEY 00000080 00001005
action=/etc/acpi/ibm-bth.sh

```

For Fn+F6:
amber@amba:/etc/acpi/events$ cat ibm-wifi 
```

### File: /etc/acpi/events/ibm-wifi
event=ibm/hotkey HKEY 00000080 00001006
action=/etc/acpi/ibm-wifi.sh
amber@amba:/etc/acpi/events$ 
```

then i found (sorry for author, i forgot from where :confused:) script for switching wi-fi and adapted it for my case. So we have two scripts for wifi and bth:

Fn+F5 (bth):
amber@amba:/etc/acpi$ cat ibm-bth.sh 
```

#!/bin/bash

BLUETOOTH=/proc/acpi/ibm/bluetooth
grep -q disabled $BLUETOOTH
bluetooth_state=$?

if [ "$bluetooth_state" = 0 ]; then
            echo enable > $BLUETOOTH;
   else
            echo disable > $BLUETOOTH
   fi
```

Fn+F6 (wifi):
amber@amba:/etc/acpi$ cat ibm-wifi.sh 
```

#!/bin/bash

STATUS=`grep -c 'eth1' /proc/net/wireless`

wlan_up()
{
        if [ $STATUS -eq 0 ]
        then
                modprobe ipw2100
        fi
}

wlan_down()
{
        if [ $STATUS -eq 1 ]
        then
                modprobe -r ipw2100
        fi
}

case "$1" in
        off)
                wlan_down
                ;;
        on)
                wlan_up
                ;;
        *)
                if [ $STATUS -eq 1 ]
                then
                        wlan_down
                else
                        wlan_up
                fi
                ;;
esac

```

Where eth1 - my Intel 2100 3B wireless adapter controlled by ipw2100 kernel module

Then i make sudo /etc/init.d/acpid restart
to make scipts work and in then i decided to modify /etc/default/acpi-support by adding ipw2100 module:
```
MODULES="ipw2100"
```
because i noticed, that if eth1 before hibernate was disabled, after hibernate it is enabled.

You may combine this two scripts to make bth+wifi toggle on\off together by pressing Fn+F5, i don't do that, cause i don't like that way.

---


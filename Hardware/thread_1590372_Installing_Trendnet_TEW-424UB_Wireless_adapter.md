---
title: "Installing Trendnet TEW-424UB Wireless adapter"
date: 2010-10-07
forum: Hardware
---

### Post by pulseplanet on 2010-10-07
Hello All,

  I am running Ubuntu 10.04 LTS and am trying to set up my USB wireless adapter (Trendnet TEW-424UB) as an access point (internet sharing). When I started, simply plugging in the wireless adapter was sufficient and the system recogonised it. However, something else was not working (unrelated to the driver itself) and I mistakenly assumed it was the driver. So I downloaded some drivers and started compiling and installing them and forgot what I did. Now when I plug in the device, even the LED light on the adapter does not come on. I have no idea what I messed up.

   . The USB hub is ok. Other devices work.
   . The adapter itself is ok. When plugged into my Widows laptop it works.

Any idea about how I restore the original drivers that came with 10.04. Many thanks. 

Here is my dmesg:
```
> [12164.933641] usb 2-3.4: new high speed USB device using ehci_hcd and address 12
> [12165.051628] usb 2-3.4: configuration #1 chosen from 1 choice
> [12165.442312] usb 4-2: new full speed USB device using uhci_hcd and address 78
> [12165.572495] usb 4-2: device descriptor read/64, error -71
> [12165.812076] usb 4-2: device descriptor read/64, error -71
> [12166.041893] usb 4-2: new full speed USB device using uhci_hcd and address 79
> [12166.181779] usb 4-2: device descriptor read/64, error -71
> [12166.411620] usb 4-2: device descriptor read/64, error -71
> [12166.641444] usb 4-2: new full speed USB device using uhci_hcd and address 80
> [12167.061119] usb 4-2: device not accepting address 80, error -71
> [12167.190974] usb 4-2: new full speed USB device using uhci_hcd and address 81
> [12167.610942] usb 4-2: device not accepting address 81, error -71
> [12167.610964] hub 4-0:1.0: unable to enumerate USB device on port 2
```


```
~> lsusb
...
Bus 002 Device 012: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
...
```

```
~> lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
ndiswrapper           244800  0 
binfmt_misc             7960  1 
vboxnetadp              5171  0 
vboxnetflt             14998  0 
vboxdrv              1792440  2 vboxnetadp,vboxnetflt
snd_hda_codec_analog    78702  1 
nfs                   310643  1 
lockd                  75079  1 nfs
nfs_acl                 2709  1 nfs
auth_rpcgss            44452  1 nfs
sunrpc                228067  11 nfs,lockd,nfs_acl,auth_rpcgss
snd_hda_intel          25773  3 
usbhid                 41084  0 
snd_hda_codec          85759  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
iptable_nat             5219  0 
snd_seq_dummy           1782  0 
nf_nat                 19501  1 iptable_nat
snd_seq_oss            31219  0 
hid                    83472  1 usbhid
nf_conntrack_ipv4      12980  3 iptable_nat,nf_nat
snd_seq_midi            5829  0 
nf_conntrack           73966  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
iptable_mangle          3315  0 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                2177  0 
ppdev                   6375  0 
snd                    71187  17 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          2791  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
ip_tables              18390  3 iptable_nat,iptable_mangle,iptable_filter
soundcore               8052  1 snd
font                    8053  1 fbcon
x_tables               22461  2 iptable_nat,ip_tables
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
parport_pc             29958  1 
dcdbas                  6886  0 
psmouse                64576  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
nvidia              10832442  38 
shpchp                 33711  0 
serio_raw               4918  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
usb_storage            49961  3 
ahci                   37870  2 
tg3                   122382  0 
```

---


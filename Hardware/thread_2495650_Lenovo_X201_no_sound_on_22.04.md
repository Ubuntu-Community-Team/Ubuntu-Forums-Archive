---
title: "Lenovo X201: no sound on 22.04"
date: 2024-02-26
forum: Hardware
---

### Post by ninoivanov on 2024-02-26
EDIT: REALLY?! NOBODY?!

So, I got only "dummy device" with regard to audio.

---- DMESG GIVES ME -----

sudo dmesg | grep -iE 'snd|sof'
[    0.452316] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.513442] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.513445] software IO TLB: mapped [mem 0x00000000b727c000-0x00000000bb27c000] (64MB)
[    4.379385] xor: measuring software checksum speed
[   86.298821] audit: type=1326 audit(1708934630.029:158): auid=1000 uid=1000 gid=15 ses=4 subj=snap.snap-store.ubuntu-software pid=6656 comm="snap-store" exe="/snap/snap-store/959/usr/bin/snap-store" sig=0 arch=c000003e syscall=93 compat=0 ip=0x7fd63fc18c8b code=0x50000
[   86.368362] audit: type=1107 audit(1708934630.097:159): pid=1750 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.4" pid=6656 label="snap.snap-store.ubuntu-software" peer_pid=1784 peer_label="unconfined"
[   86.369325] audit: type=1107 audit(1708934630.101:160): pid=1750 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.4" pid=6656 label="snap.snap-store.ubuntu-software" peer_pid=1784 peer_label="unconfined"
[   86.376154] audit: type=1107 audit(1708934630.105:161): pid=1750 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.4" pid=6656 label="snap.snap-store.ubuntu-software" peer_pid=1784 peer_label="unconfined"
[   86.377873] audit: type=1107 audit(1708934630.109:162): pid=1750 uid=103 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/PolicyKit1/Authority" interface="org.freedesktop.PolicyKit1.Authority" member="CheckAuthorization" mask="send" name=":1.4" pid=6656 label="snap.snap-store.ubuntu-software" peer_pid=1784 peer_label="unconfined"
[   87.310455] audit: type=1400 audit(1708934631.041:163): apparmor="DENIED" operation="open" profile="snap.snap-store.ubuntu-software" name="/etc/appstream.conf" pid=6656 comm="snap-store" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0

----- END OF DMESG ----

---- ALSAMIXER GIVES ME ----

alsamixer
ALSA lib confmisc.c:855:(parse_card) cannot find card '0'
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_card_inum returned error: No such file or directory
ALSA lib confmisc.c:422:(snd_func_concat) error evaluating strings
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1334:(snd_func_refer) error evaluating name
ALSA lib conf.c:5178:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:5701:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib control.c:1528:(snd_ctl_open_noupdate) Invalid CTL default
cannot open mixer: No such file or directory

---- END OF ALSAMIXER ----

---- JOURNALCTL GIVES ME ----

journalctl -k | grep -Ei "ALSA|HDA|sof[-]|HDMI|snd[_-]|sound|hda.codec|hda.intel"
Feb 26 09:02:37 RedOctober kernel: ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
Feb 26 09:25:45 RedOctober kernel: usb 3-3: Product: USB PnP Sound Device
Feb 26 09:25:45 RedOctober kernel: input: C-Media Electronics Inc.       USB PnP Sound Device as /devices/pci0000:00/0000:00:1c.3/0000:05:00.0/usb3/3-3/3-3:1.3/0003:8086:0808.0003/input/input14
Feb 26 09:25:45 RedOctober kernel: hid-generic 0003:8086:0808.0003: input,hidraw0: USB HID v1.00 Device [C-Media Electronics Inc.       USB PnP Sound Device] on usb-0000:05:00.0-3/input3

---- END OF JOURNALCTL ----

---- SOUND CARDS ARE NOT SEEN ----

cat /proc/asound/cards
--- no soundcards ---

----- END OF SOUND CARDS ARE NOT SEEN ----

I already tried:

apt-get --purge remove linux-sound-base alsa-base alsa-utils pulseaudio pipewire


and then:

apt-get install linux-sound-base alsa-base alsa-utils  pulseaudio osspd pipewire gdm3 ubuntu-desktop

(Still no sound, all it did was mess up my desktop icons.)

What else can I do?

---

### Post by ninoivanov on 2024-02-26
OK, as root, "**modprobe snd-usb-audio**" gave me USB-stick-audio (always handy to have, highly recommended), and "**modprobe snd-hda-intel**" gave me the default audio. This be a bottle in the ocean of time, to aid unfortunate souls as I once hath been: *tu fui, ego eris*.

---


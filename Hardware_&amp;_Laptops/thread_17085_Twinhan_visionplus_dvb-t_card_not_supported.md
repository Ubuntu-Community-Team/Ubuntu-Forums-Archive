---
title: "Twinhan visionplus dvb-t card not supported?"
date: 2005-02-25
forum: Hardware &amp; Laptops
---

### Post by brainstuff on 2005-02-25
Hi folks!

A new day, a new problem...!

Have decided to install Hoary on one of my desktop PCs - Athlon 2400, 512Mb RAM, Radeon 9600 xt, Twinhan visionplus dvb-t.

Reason for Hoary install, is that Warty kernel didn't seem to support DVB natively, and I think 2.6.10 does?

Anyway, I'm at a total loss as to how to get apps to see my DVB card - I've installed XawTV which says: 

This is xawtv-3.93, running on Linux/i686 (2.6.10-3-386)
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available


I've even installed MythTV (I got the SQL working I think - woo me!). No joy detecting the card though.

Anyway, from what I can tell, I am running some of the necessary BTXX drivers (it's the BT878 chipset) - here's my lsmod:

Module                  Size  Used by
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
video                  16260  0
sony_acpi               6280  0
pcc_acpi               11264  0
button                  6800  0
battery                10244  0
container               4608  0
ac                      4996  0
ipv6                  229376  9
af_packet              20744  2
via_rhine              19972  0
mii                     4736  1 via_rhine
usbhid                 29376  0
snd_via82xx            25248  1
snd_ac97_codec         64608  1 snd_via82xx
gameport                4608  1 snd_via82xx
snd_mpu401_uart         7168  1 snd_via82xx
snd_rawmidi            22944  1 snd_mpu401_uart
snd_seq_device          8332  1 snd_rawmidi
i2c_viapro              7436  0
via_ircc               24340  0
irda                  168000  1 via_ircc
crc_ccitt               2176  1 irda
ehci_hcd               29444  0
uhci_hcd               30224  0
usbcore               107384  4 usbhid,ehci_hcd,uhci_hcd
ohci1394               31876  0
snd_bt87x              12612  0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  4 snd_via82xx,snd_ac97_codec,snd_bt87x,snd_pcm_osssnd_timer              23300  1 snd_pcm
snd                    50276  10 snd_via82xx,snd_ac97_codec,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_bt87x,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  3 snd_via82xx,snd_bt87x,snd_pcm
tuner                  20388  0
bttv                  142928  0
video_buf              20484  1 bttv
firmware_class          9728  1 bttv
i2c_algo_bit            9224  1 bttv
v4l2_common             5888  1 bttv
btcx_risc               4744  1 bttv
i2c_core               21264  4 i2c_viapro,tuner,bttv,i2c_algo_bit
videodev                9728  1 bttv
shpchp                 86116  0
pci_hotplug            30512  1 shpchp
via_agp                 9216  1
agpgart                31784  1 via_agp
pcspkr                  3816  0
rtc                    12216  0
floppy                 54864  0
md                     43728  0
dm_mod                 53116  1
capability              5000  0
evdev                   9088  0
commoncap               7808  1 capability
tsdev                   7488  0
sr_mod                 16036  0
sbp2                   22408  0
scsi_mod              120064  2 sr_mod,sbp2
ieee1394              100408  2 ohci1394,sbp2
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  2 sr_mod,ide_cd
ext3                  120200  1
jbd                    53912  1 ext3
ide_generic             1664  0
via82cxxx              12956  1
ide_disk               18176  4
ide_core              118988  4 ide_cd,ide_generic,via82cxxx,ide_disk
unix                   26164  811
thermal                13576  0
processor              22708  1 thermal
fan                     4612  0
fbcon                  34048  0
crc32                   4352  2 via_rhine,fbcon
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb


...and here's my lspci:
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
**0000:00:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)**
0000:00:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:0b.0 FireWire (IEEE 1394): Lucent Microelectronics FW323 (rev 04)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)

Does anyone have a solution that preferably uses a nice simple apt-get, rather than what I fear will otherwise be my first ever kernel compile? (I'm not ready for it yet!!!!).

Google has pretty much drawn a blank for me :(

Thanks
brain

---

### Post by Schugy on 2005-03-13
I have Warty and this PCI-card too and I have no usable devices. But I have created them with mknod. Don't know what is wrong. tzap doesn't work. I had to compile the linuxtv-dvb-apps on my own. I wasn't able to find a package for apt-get. My kernel is 2.6.8.1-4-k7. What can I do?

---

### Post by brainstuff on 2005-03-14
I still haven't fixed this, although I do have a go every now and again.

If I modprobe a load of stuff, the card turns up in lsmod, and mythtv can now see the card, but I can't get it to tune...

Here's a post I made on mythtvtalk which sees me getting a bit further...and then stop!

[http://www.mythtvtalk.com/forum/viewtopic.php?t=737&highlight=](http://www.mythtvtalk.com/forum/viewtopic.php?t=737&highlight=)

edit: oh yeah, you might need to remove the bttv audio driver too (see the link above).

---

### Post by brainstuff on 2005-03-14
here's another good place to look for tips:

Twinhan DVB-T specific forum...

[http://forums.dvbowners.com/index.php?showforum=17](http://forums.dvbowners.com/index.php?showforum=17)

---

### Post by Starchild on 2005-03-15
You don't have enough modules loaded. After loading bttv, try loading these as well:

dvb-bt8xx
dst

The last one should add the DST frontend which Twinhan uses.

I have the exact same card only it's a DVB-S. I've been able to make it work in SUSE 9.1 (Kernel 2.6.4) so It should have no problem working in Warty. But strangely enough I haven't been able to make it work under Warty! 

Try these modules and if yours work then it means I should consider a 2.6.10 kernel as well.

This is how I do it in SUSE:

modprobe bttv i2c_hw=1 card=0x71
modprobe dvb-bt8xx
modprobe dst

---

### Post by brainstuff on 2005-03-16
Thanks for the prod! I'll give it a go tonight...

Thanks
brain

---

### Post by Markp.com on 2005-06-27
[QUOTE=brainstuff]Thanks for the prod! I'll give it a go tonight...

Thanks
brain[/QUOTE]
 Did you get your card working? I've just installed Ubuntu and would like to get my TwinHan DVB-T PCI card working! :)

---

### Post by brainstuff on 2005-06-28
Hi there

Nope - never did - although I got pretty close on a few occasions. Ended up trying Fedora Core 3, the MythTV knoppix CD, Hoary, recompiling kernels (bear in mind I'm a n00b). None of it worked.

Sadly an install of WinXP Media Center completely borked my dual-boot mbr and my 40Gb hard drive started telling me it had 9 spare partitions of 200Gb each, so I ended up getting rid of Linux altogether on my media PC :(  At the end of the day I was just spending too much time trying to get what is essentially a TV and VCR to work, when I had an actual TV and VCR sat right next to the PC.

If you ever get yours working though, do drop me a line and let me know how you did it :)

---

### Post by gyaresu on 2005-07-09
For me I needed to remove all the DVB relevant modules and then reinstall them.
Just a matter of putting them in the blacklist and the /etc/modules file to get them to load in the right order.

Still don't know how to go about getting the PIDS for the channels...
Just thought I'd post this as It's not mentioned as a solution many places...

Where I found it:
[http://www.ussg.iu.edu/hypermail/linux/kernel/0408.2/2352.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0408.2/2352.html)

---

### Post by dhanjel on 2005-07-15
I have the same card and added:

dvb-bt8xx
dst

to /etc/modules, but at startup, the following is displayed:

```

Linux video capture interface: v1.00
bttv: driver version 0.9.15 loaded
bttv: using 8 buffers with 2080k (520 pages) each for capture
bttv: Bt8xx card found (0).
ACPI: PCI interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
bttv0: Bt878 (rev 17) at 0000:00:0b.0, irq: 19, latency: 32, mmio: 0xcfdfe000
bttv0: detected: Twinhan VisionPlus DVB-T [card=113], PCI subsystem ID is 1822:0001
bttv0: using: Twinhan DST + clones [card=113,autodetected]
bttv0: gpio: en=00000000, out=00000000 in=00f500fd [init]
bttv0: using tuner=4
bttv0: add subdevice "dvb0"
bt878: AUDIO driver version 0.0.0 loaded
bt878: Bt878 AUDIO function found (0).
ACPI: PCI interrupt 0000:00:0b.1[A] -> GSI 19 (level, low) -> IRQ 19
bt878(0): Bt878 (rev 17) at 00:0b.1, irq: 19, latency: 32, memory: 0xcfdff000
DVB: registering new adapter (bttv0).
dst_check_ci: unable to recognize  or DTT-CI
dst_check_ci please email linux-dvb@linuxtv.org with this type in
DST type : satellite
DST type flags : 0x4 symdiv
DVB: registering frontend 0 (DST DVB-S)...

```

DST identifies the card as a dvb-s (satellite), what could be wrong?

Edit: What are the dst module for? (I don't have a CI-module installed at the moment, could that be it?)

---


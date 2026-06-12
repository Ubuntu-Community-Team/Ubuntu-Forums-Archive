---
title: "Lenovo Y550P Boot Failure and Freezing"
date: 2010-08-12
forum: Hardware
---

### Post by cmartin0 on 2010-08-12
I am having two problems with Ubuntu

Some times when Ubuntu boots all I will get is a blinking underscore. I cannot get a terminal by going ctrl + alt + F1 - F11. Pressing ctrl + alt + F12  gives me the message in the image below.

[http://h.imagehost.org/0043/boot_error.jpg]("http://h.imagehost.org/0043/boot_error.jpg")

ctrl + alt + delete will not reboot the laptop. I have to press and hold the power button to shut it down. I may have to do this two times or once before Ubuntu will boot. Once Ubuntu boots I can reboot several times back into a fully working Ubuntu. It seems to be random when I can boot or not into Ubuntu.

so the behavior is like what this guy was having.
[http://ubuntuforums.org/showthread.php?t=1490932](http://ubuntuforums.org/showthread.php?t=1490932)

The other problem is Ubuntu will freeze randomly while in graphics mode. I can move my mouse but the cursor will not change, the applets do not update. Keyboard input is  ignored. I have to hold the power button to shutdown. I was having this same problem running Ubuntu from a flash drive moths ago back in May. This maybe a graphics problem. I haven't tried a different driver yet.

I am dual booting windows 7 and it is not having any problems.

I can post more log info if need be.

```
Linux leno 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux

```

lsmod
```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_codec_realtek   203310  1 
snd_hda_intel          21941  2 
arc4                    1153  2 
joydev                  8708  0 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
nouveau               467048  2 
iwlagn                105694  0 
snd_seq_midi            4557  0 
ttm                    49943  1 nouveau
iwlcore               105922  1 iwlagn
snd_rawmidi            19056  1 snd_seq_midi
led_class               2864  1 iwlcore
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
drm_kms_helper         29297  1 nouveau
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205146  2 iwlagn,iwlcore
drm                   162377  4 nouveau,ttm,drm_kms_helper
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               56990  0 
soundcore               6620  1 snd
agpgart                31724  2 ttm,drm
psmouse                63245  0 
video                  17375  0 
videodev               34361  1 uvcvideo
lp                      7028  0 
serio_raw               3978  0 
i2c_algo_bit            5028  1 nouveau
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
cfg80211              126517  3 iwlagn,iwlcore,mac80211
v4l1_compat            13251  2 uvcvideo,videodev
parport                32635  2 ppdev,lp
output                  1871  1 video
tg3                   109324  0 
ahci                   32200  2 
```

lspci
```
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 240M] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
06:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300
07:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```

---

### Post by itsjustarumour on 2010-08-13
> **cmartin0 said:**
> Some times when Ubuntu boots all I will get is a blinking underscore

I get that sometimes, but only when I've booted the PC whilst a USB memory stick is in one of the sockets.  The machine isn't set in the BIOS to boot first from a USB stick of course, it just seems to be unable to mount the drive during the boot process and so it just hangs.  This happens on about 1 boot in 5 on Ubuntu 10.04 (and also Fedora 13) so I think its a kernel bug.

---

### Post by itsjustarumour on 2010-08-13
> **cmartin0 said:**
> The other problem is Ubuntu will freeze randomly while in graphics mode.

Are you using the NVidia driver?  I've been getting this problem since the recent updates installed the latest current NVidia 256.44 driver.  I haven't got to the bottom of it yet, but it seems like a bug. Other people seem to be having problems also.  If you're also using the NVidia driver, post up your exact specs and have a search around the forum to see if you can find anyone else whose problem matches yours.

---

### Post by cmartin0 on 2010-08-14
> **itsjustarumour said:**
> I get that sometimes, but only when I've booted the PC whilst a USB memory stick is in one of the sockets.  The machine isn't set in the BIOS to boot first from a USB stick of course, it just seems to be unable to mount the drive during the boot process and so it just hangs.  This happens on about 1 boot in 5 on Ubuntu 10.04 (and also Fedora 13) so I think its a kernel bug.
Looking in /var/log/kern.log the problem seems to be usb related. I have a Dell USB mouse plugged in most the time when I use my laptop. I used my laptop today without the mouse I did not encounter any boot problems. I'll post the kern.log info later.


> **itsjustarumour said:**
> Are you using the NVidia driver?  I've been getting this problem since the recent updates installed the latest current NVidia 256.44 driver.  I haven't got to the bottom of it yet, but it seems like a bug. Other people seem to be having problems also.  If you're also using the NVidia driver, post up your exact specs and have a search around the forum to see if you can find anyone else whose problem matches yours.
At the time I was running nouveau, the FOSS NVidia driver. I have switch to the closed source driver by selecting it System > Administration Hardware Drivers. Since then I am running compiz without any freezing up.

---

### Post by cmartin0 on 2010-08-21
I think the problem with the kernel hang is the blue tooth.

I sometimes get some errors in /var/log/kern.log like this 

```
Aug 12 20:25:58 leno kernel: [ 5873.008328] usb 1-1.4: USB disconnect, address 3
Aug 12 20:25:58 leno kernel: [ 5873.008369] btusb_intr_complete: hci0 urb f34c0680 failed to resubmit (19)
Aug 12 20:25:58 leno kernel: [ 5873.008440] btusb_bulk_complete: hci0 urb f34c0180 failed to resubmit (19)
Aug 12 20:25:58 leno kernel: [ 5873.008449] btusb_bulk_complete: hci0 urb f34c0880 failed to resubmit (19)
Aug 12 20:25:58 leno kernel: [ 5873.008585] btusb_send_frame: hci0 urb f3705a80 submission failed
```

I have a blue tooth module tied to the wifi switch. I can toggle the switch to disable blue tooth but it fully does not disengage the blue tooth. When the wifi switch is off the blue tooth light will be on when the laptop turns on. The light does not turn off unless a kernel loads. Starting windows or linux will turn the blue tooth light off but memtest will leave the light on. I cannot disable  the blue tooth in the laptop BIOS. 

The kernel hang happens no matter when I have plugged in or not or the state of the wifi switch. 


I took apart my laptop and removed the blue tooth module. I will run the same kernel to see if this fixes the problem. I don't use blue tooth anyways so thats not much of a problem.

---

### Post by grednel on 2010-10-31
Hello,
Let me get in the lenovo freezing victims club.
I have just installed an ubuntu distribution on a Lenovo with no dual boot, using the complete disk. Whenever i use a 10.04 or a 10.10 distribution a get the same problem. Sometimes i can't even log in, sometimes it get freezed after several minutes using.
I got some progress when the graphics effects were disabled but that's all. using ctrl alt F1 allowed me to get on console mode : everything i tested were OK like sudo dpkg --configure -a, update or upgrade. The problem seems to concern the graphic mode.
I use Ubuntu for several years on different PC like Dell laptop, Dell office station, Fujitsu siemens or other but i never had this kind of problem.
I have red something about specific drivers on different posts but nothing really convincing.
The machine is a MT-M but i can't see whether it runs as a 32 or a 64 bits machine. I have installed the 32 bits distribution and received no error message. Some posts say that the machine could run under both 32 or 64 configuration but that the 64 one could be more sensitive to these problems. It seems that 32 bugs in the same way.
If anyone has a suggestion, it would be welcomed.
PS : excuse my english but it's rather old

---


---
title: "Buffer I/O error on device dm-24"
date: 2005-04-06
forum: Hardware &amp; Laptops
---

### Post by grimborg on 2005-04-06
At boot time I get the following error messages: 

Apr  6 00:28:54 alhares kernel: Inspecting /boot/System.map-2.6.10-4-k7
Apr  6 00:28:54 alhares kernel: Loaded 26828 symbols from /boot/System.map-2.6.10-4-k7.
Apr  6 00:28:54 alhares kernel: Symbols match kernel version 2.6.10.
Apr  6 00:28:54 alhares kernel: No module symbols loaded - kernel modules not enabled. 
Apr  6 00:28:54 alhares kernel: block 0
Apr  6 00:28:54 alhares kernel: Buffer I/O error on device dm-24, logical block 0
Apr  6 00:28:54 alhares kernel: Buffer I/O error on device dm-24, logical block 1
Apr  6 00:28:54 alhares kernel: Buffer I/O error on device dm-24, logical block 2
Apr  6 00:28:54 alhares kernel: Buffer I/O error on device dm-24, logical block 3
Apr  6 00:28:54 alhares kernel: Buffer I/O error on device dm-24, logical block 4
Apr  6 00:28:54 alhares kernel: Buffer I/O error on device dm-24, logical block 5
Apr  6 00:28:54 alhares kernel: Buffer I/O error on device dm-24, logical block 6
Apr  6 00:28:54 alhares kernel: Buffer I/O error on device dm-24, logical block 7
Apr  6 00:28:54 alhares kernel: Buffer I/O error on device dm-24, logical block 0
Apr  6 00:28:54 alhares kernel: Buffer I/O error on device dm-24, logical block 445952
Apr  6 00:28:54 alhares kernel: Buffer I/O error on device dm-24, logical block 445952

(these last messages are repeated several times)

What do these messages refer to? What's the device dm-24? 

Also, unbelievable as it may sound, my Ubuntu locks up from time to time. Maybe these lookups are related to these messages? If not, where could I look for information? There are no other errors in the logs...

I'm running Hoary (up to date) and Linux 2.6.10-4-k7.

Thanks.

---

### Post by p!=f on 2005-04-06
Post lspci here please...
```

[~] > dpkg -l linux-image-2.6.10*
ii  linux-image-2.6.10-5-k7        2.6.10-34                      Linux kernel image for version 2.6.10 on AMD K7.

```
... and check whether you run lastest available 2.6.10 kernel.

I'm not sure but isn't dm-24 sound device?

---

### Post by grimborg on 2005-04-06
Thanks for your answer.

I upgraded the kernel to the latest version and booted into it.. after a couple of hours it locked again.

Here's the output of lspci:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:06.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:06.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:06.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
0000:00:06.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
0000:00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 10)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

Any ideas? 

Btw, is there any list to find out what dm-24 stands for?

Thanks.

---

### Post by p!=f on 2005-04-07
Hmmm. And lsmod?

---

### Post by grimborg on 2005-04-07
Here it is (the output of lsmod)

> Module                  Size  Used by
binfmt_misc            11592  1
proc_intf               3972  0
freq_table              4100  0
cpufreq_userspace       4444  0
cpufreq_ondemand        6236  0
cpufreq_powersave       1728  0
autofs4                19332  1
video                  16068  0
sony_acpi               6024  0
pcc_acpi               11072  0
button                  6544  0
battery                10052  0
container               4416  0
ac                      4740  0
nvidia               3921788  8
ipv6                  258944  11
nfs                   208164  10
lockd                  64872  2 nfs
sunrpc                149668  13 nfs,lockd
sd_mod                 17872  0
snd_via82xx            27616  1
snd_ac97_codec         74208  1 snd_via82xx
snd_pcm_oss            52516  0
snd_mixer_oss          19776  2 snd_pcm_oss
snd_pcm                94920  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25156  1 snd_pcm
snd_page_alloc          9796  2 snd_via82xx,snd_pcm
gameport                4544  1 snd_via82xx
snd_mpu401_uart         7744  1 snd_via82xx
snd_rawmidi            24928  1 snd_mpu401_uart
snd_seq_device          8524  1 snd_rawmidi
snd                    55268  9 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10080  2 snd
uhci_hcd               33040  0
i2c_viapro              7500  0
i2c_core               22416  1 i2c_viapro
via_ircc               30356  0
irda                  192704  1 via_ircc
crc_ccitt               1984  1 irda
usb_storage            72384  0
scsi_mod              127936  2 sd_mod,usb_storage
8139cp                 20480  0
8139too                26048  0
mii                     4992  2 8139cp,8139too
ehci_hcd               32772  0
ohci_hcd               21576  0
usbcore               119224  5 uhci_hcd,usb_storage,ehci_hcd,ohci_hcd
shpchp                 99300  0
pci_hotplug            33584  1 shpchp
via_agp                 9408  1
agpgart                33704  2 nvidia,via_agp
pcspkr                  3560  0
rtc                    12536  0
floppy                 59152  0
reiserfs              264464  5
md                     47376  0
evdev                   9408  0
dm_mod                 59708  8
tsdev                   7616  0
capability              4744  0
commoncap               7808  1 capability
psmouse                21384  0
mousedev               11352  1
parport_pc             37444  1
lp                     11240  0
parport                36872  2 parport_pc,lp
ide_cd                 41924  0
cdrom                  40476  1 ide_cd
ext3                  137352  1
jbd                    60568  1 ext3
mbcache                 8452  1 ext3
ide_generic             1408  0
via82cxxx              13852  1
ide_disk               20480  5
ide_core              129548  5 usb_storage,ide_cd,ide_generic,via82cxxx,ide_disk
unix                   28532  902
thermal                13384  0
processor              22516  1 thermal
fan                     4484  0
fbcon                  38016  0
font                    8256  1 fbcon
bitblit                 5568  1 fbcon
vesafb                  6820  0
cfbcopyarea             3904  1 vesafb
cfbimgblt               3008  1 vesafb
cfbfillrect             3584  1 vesafb


thanks for your time :)

---

### Post by nadamsieee on 2006-10-23
> **p!=f said:**
> I'm not sure but isn't dm-24 sound device?

No, this error is related to the filesystem:

[http://ubuntuforums.org/showthread.php?t=276930](http://ubuntuforums.org/showthread.php?t=276930)

---


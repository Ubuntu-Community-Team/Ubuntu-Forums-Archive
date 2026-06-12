---
title: "USB mouse recognized as 1.1 on 2.0 ports"
date: 2006-01-13
forum: Hardware &amp; Laptops
---

### Post by impact201 on 2006-01-13
Hello,

I've gone through a few reinstalls trying to get my USB set up properly, and just can't seem to get it right.  Ubuntu recognizes my onboard USB 2.0 Host driver...but my Logitech MX1000 mouse always shows up as USB 1.1.  I'm still new to Linux, so I'll post a few things that may help in diagnosing.  Please let me know if there's more you would need.  (yes, I have searched the forums for info on this but none have worked for me so far)

AMD64 3000+
1GB RAM
GeForce 6200
Logitech MX1000 mouse (USB)
MSI mobo (VIA K8M800-CE + VT8237R Chipset)

Also, I am using the 64-bit version of Ubuntu.

```
jason@ubuntu:~$ sudo dmesg | grep "usb"
Password:
[   23.235330] usbcore: registered new driver usbfs
[   23.235347] usbcore: registered new driver hub
[   30.874872] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   31.925028] usbcore: registered new driver hiddev
[   31.947644] input: USB HID v1.11 Mouse [Logitech USB RECEIVER] on usb-0000:00:10.1-2
[   31.947652] usbcore: registered new driver usbhid
[   31.947654] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
jason@ubuntu:~$ lsmod
Module                  Size  Used by
ppdev                  10248  0
powernow_k8            10512  0
cpufreq_userspace       5584  1
cpufreq_stats           5896  0
freq_table              5384  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2432  0
cpufreq_ondemand        7212  0
cpufreq_conservative     8236  0
rfcomm                 37168  0
l2cap                  24328  5 rfcomm
bluetooth              48964  4 rfcomm,l2cap
video                  17416  0
tc1100_wmi              8200  0
sony_acpi               6296  0
pcc_acpi               13696  0
hotkey                 10696  0
dev_acpi               14980  0
i2c_acpi_ec             6528  0
button                  7968  0
battery                10760  0
container               5248  0
ac                      5768  0
ipv6                  246400  6
af_packet              22668  2
tsdev                   8960  0
floppy                 62840  0
pcspkr                  4176  0
snd_seq_dummy           4484  0
snd_seq_oss            32128  0
snd_seq_midi            9920  0
snd_seq_midi_event      8064  2 snd_seq_oss,snd_seq_midi
snd_seq                52032  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            29472  1
gameport               16392  1 snd_via82xx
snd_ac97_codec         87000  1 snd_via82xx
snd_pcm_oss            51232  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                91020  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              24200  2 snd_seq,snd_pcm
snd_page_alloc         11408  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7936  1 snd_via82xx
snd_rawmidi            27040  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9488  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    55784  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10912  1 snd
i2c_viapro              9236  0
i2c_core               22936  2 i2c_acpi_ec,i2c_viapro
shpchp                 87976  0
pci_hotplug            28008  1 shpchp
dm_mod                 54904  0
evdev                  10496  0
rtc                    13448  0
psmouse                27908  0
mousedev               12260  1
parport_pc             36328  1
lp                     13576  0
parport                38540  3 ppdev,parport_pc,lp
md                     43904  0
ext3                  127632  1
jbd                    54960  1 ext3
thermal                15120  0
processor              25684  2 powernow_k8,thermal
fan                     5384  0
usbhid                 32416  0
via_rhine              23812  0
mii                     6144  1 via_rhine
ehci_hcd               31752  0
uhci_hcd               30368  0
sata_via               10244  0
libata                 52744  1 sata_via
scsi_mod              143984  1 libata
ide_cd                 40608  0
cdrom                  36520  1 ide_cd
ide_disk               17152  3
ide_generic             1920  0
via82cxxx              13488  1
ide_core              148932  4 ide_cd,ide_disk,ide_generic,via82cxxx
unix                   28728  601
vesafb                  9252  0
capability              6152  0
commoncap               8448  1 capability
vga16fb                12288  1
vgastate                9216  1 vga16fb
softcursor              2944  2 vesafb,vga16fb
cfbimgblt               3200  2 vesafb,vga16fb
cfbfillrect             4736  2 vesafb,vga16fb
cfbcopyarea             4352  2 vesafb,vga16fb
fbcon                  36480  72
tileblit                2944  1 fbcon
font                    9216  1 fbcon
bitblit                 5760  1 fbcon

```

```
jason@ubuntu:/proc/bus/usb$ cat devices

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-amd64-generic ehci_hcd
S:  Product=VIA Technologies, Inc. USB 2.0
S:  SerialNumber=0000:00:10.4
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-amd64-generic uhci_hcd
S:  Product=VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
S:  SerialNumber=0000:00:10.3
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-amd64-generic uhci_hcd
S:  Product=VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
S:  SerialNumber=0000:00:10.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=118/900 us (13%), #Int=  1, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-amd64-generic uhci_hcd
S:  Product=VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
S:  SerialNumber=0000:00:10.1
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c50e Rev=25.10
S:  Manufacturer=Logitech
S:  Product=USB RECEIVER
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr= 70mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.12-9-amd64-generic uhci_hcd
S:  Product=VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
S:  SerialNumber=0000:00:10.0
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

```

Any suggestions would be VERY much appreciated.  Thank you.  :)

---

### Post by hanover.fiste on 2006-02-27
That's because it's a USB 1.1 device.

---

### Post by mjwood0 on 2006-02-27
Esentially, your motherboard has a built in USB 2.0 hub.  The USB controller on your Motherboard is also a v2.0 controller.  However, both of these devices are backward compatible with USB 1.1

So, if you plug in a USB 1.1 mouse, that's what it will show up as.  Don't worry.  This doesn't mean that your USB 2.0 isn't working.  Can you plug in a known USB 2.0 device like a thumb drive or something?  It should show up as USB 2.0.

---

### Post by impact201 on 2006-02-27
I'm sorry, I tried to edit the title to this thread long ago to reflect my "fixing" of the non-existant problem, but for some reason I can't get access to the thread title.  ;)  

I had done exactly as suggested and plugged in my flash drive, and it showed up as USB 2.0.  Thank you for the replies though.

---


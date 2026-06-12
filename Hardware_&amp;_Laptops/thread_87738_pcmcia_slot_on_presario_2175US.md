---
title: "pcmcia slot on presario 2175US"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by binz on 2005-11-08
Hello, there:

I am new in this forum, but I have been using ubuntu for several months on my desktop. Ubuntu is really good, and I really like it.

Recently, I installed Breezy Badger 5.10 on my laptop, which is a Compaq Presario 2175US. Everything works well except the internal wireless card and some one-tuch buttons. For the latter, the one-tuch buttons, I do not care. I hardly used them. For the internal wireless card, I do not expect it would work. I have been work with linux for a while and I knew that it is not an easy task to build the driver for each wireless card. However, one thing I do care is the pcmcia port. It seems that ubuntu does not support the pcmcia port on my laptop. I have some Orinoco cards, which have been used for some embeded linux systems. My plan was to use one Orinoco card for my laptop. However, when I plugged the wireless card in the pcmcia slot, ubuntu freezed. I tried this several times and it always freezed no matter whether the X server started or not.

Does anyone have some idea why did this happen? Is this some bug?

I have read some threads here and get my internal wireless card working with the ndiswrapper (Thank you guys). But it would really nice if I can get the pcmcia slot work.

Thank you,

binz

---

### Post by az on 2005-11-08
If it is an older laptop and the pcmcia system is on the isa bus, then you need to load the module by hand.  

What is the output of
lsmod
from a terminal?


Also, can you check the log (/var/log/messages) and see what happened when you plugged the thing in and your system froze?

---

### Post by binz on 2005-11-10
Here is the output of lsmod:
=============================================
~$ lsmod
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
powernow_k7             8616  0
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 powernow_k7,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
radeon                 68352  1
drm                    58004  2 radeon
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  8
af_packet              20232  2
ndiswrapper           114376  0
pcspkr                  3652  0
rtc                    11832  0
i2c_ali1535             6788  0
i2c_ali15x3             7172  0
i2c_core               19728  3 i2c_acpi_ec,i2c_ali1535,i2c_ali15x3
ohci1394               30644  0
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_ali5451            22596  1
snd_ac97_codec         72188  1 snd_ali5451
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  1 snd_pcm
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
ati_agp                 8716  1
agpgart                32328  2 drm,ati_agp
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
sr_mod                 15652  0
sbp2                   21128  0
scsi_mod              124872  2 sr_mod,sbp2
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 powernow_k7,thermal
fan                     4740  0
natsemi                23904  0
ohci_hcd               18564  0
usbcore               104188  3 ndiswrapper,ohci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  3
ide_generic             1664  0
alim15x3               11020  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,alim15x3
unix                   24624  778
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
===============================================
I guess you might want to check if the pcmcia module loaded or not, so I also do the following commands:
==============================================
binz@wraith:~$ lsmod | grep pcmcia
pcmcia                 24584  2
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
=============================================

I also checked the log, but there is no information on what was going on after I insert the card. I guess that is because the whole system froze and when I restart the computer, ubuntu just creates another log file. However, I found following in the log file:

=============================================
-> IRQ 11
Nov 10 10:48:32 localhost kernel: [4294714.245000] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:0024]
Nov 10 10:48:32 localhost kernel: [4294714.245000] Yenta O2: res at 0x94/0xD4: 00/ea
Nov 10 10:48:32 localhost kernel: [4294714.245000] Yenta O2: enabling read prefetch/write burst
Nov 10 10:48:32 localhost kernel: [4294714.365000] Yenta: ISA IRQ mask 0x0018, PCI irq 11
Nov 10 10:48:32 localhost kernel: [4294714.365000] Socket status: 30000007
Nov 10 10:48:32 localhost kernel: [4294714.498000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
Nov 10 10:48:32 localhost kernel: [4294714.498000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
Nov 10 10:48:32 localhost kernel: [4294714.498000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNKC] -> GSI 10 (level, low) -
==============================================

Does this mean that my laptop has the pcmcia system on the ISA bus?

Thank you

bin

---

### Post by binz on 2006-06-16
I just have this problem fixed. This problem is caused by the IRQ confliction. After I disable all the IRQ from 1 to 15 for pcmcia to use, it works fine. Here is what I added to the file /etc/pcmcia/config.opts in case some one is interested in:
-----------------------------
exclude irq 1

exclude irq 2

exclude irq 3

exclude irq 5

exclude irq 6

exclude irq 8

exclude irq 9

exclude irq 10

exclude irq 11

exclude irq 12

exclude irq 13

exclude irq 14

exclude irq 15


-----------------------------------------

The IRQ 1, 4, and 7 have already been excluded. So, this file just not allow the pcmica use any IRQ from 1 to 15.

---


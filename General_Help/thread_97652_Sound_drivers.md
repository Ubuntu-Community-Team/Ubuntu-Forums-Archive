---
title: "Sound drivers"
date: 2005-12-01
forum: General Help
---

### Post by Mitja_ on 2005-12-01
Hi!

I've been looking all over for this solution and none has helped so far.
I installed kubuntu "Breezy Badger" 5.10 i386 on an AMD 64 3000+ machine, with Realtek ALC655 on board audio chip. Sound worked properly, but then (why oh why) I uninstalled some packages (don't know exactly which ones) and sound stopped working. At the moment I get only PC speaker beep sometimes, nothing else.
This is lsmod output:
```
Module                  Size  Used by
loop                   15752  0 
binfmt_misc            10888  1 
rfcomm                 34972  0 
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0 
cpufreq_stats           5124  0 
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0 
cpufreq_ondemand        5916  0 
cpufreq_conservative     6820  0 
autofs4                16772  0 
capifs                  5768  1 
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
ipv6                  217408  6 
tsdev                   7616  0 
floppy                 52692  0 
pcspkr                  3652  0 
rtc                    11832  0 
tuner                  24488  0 
saa7134                98772  0 
video_buf              19844  1 saa7134
v4l2_common             5888  1 saa7134
v4l1_compat            12420  1 saa7134
soundcore               9184  1 saa7134
ir_common               7428  1 saa7134
videodev                9344  1 saa7134
ohci1394               30644  0 
shpchp                 80612  0 
pci_hotplug            24628  1 shpchp
i2c_nforce2             6528  0 
i2c_core               19728  4 i2c_acpi_ec,tuner,saa7134,i2c_nforce2
nls_iso8859_2           4736  3 
nls_iso8859_1           4224  2 
vfat                   12288  5 
fat                    46492  1 vfat
nls_cp437               5888  7 
ntfs                   92016  2 
dm_mod                 50364  1 
evdev                   9088  0 
sr_mod                 15652  0 
sbp2                   21128  0 
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0 
mousedev               10912  1 
parport_pc             31812  1 
lp                     11460  0 
parport                32072  2 parport_pc,lp
md                     40656  0 
ext3                  115976  3 
jbd                    48536  1 ext3
thermal                13192  0 
processor              23100  1 thermal
fan                     4740  0 
usbhid                 30688  0 
forcedeth              19072  0 
ehci_hcd               29448  0 
ohci_hcd               18564  0 
usbcore               104188  4 usbhid,ehci_hcd,ohci_hcd
sd_mod                 17424  12 
ide_cd                 36996  0 
cdrom                  33952  2 sr_mod,ide_cd
ide_generic             1664  0 
sata_nv                 9092  22 
libata                 47876  1 sata_nv
scsi_mod              124872  4 sr_mod,sbp2,sd_mod,libata
amd74xx                12828  1 
ide_core              125268  3 ide_cd,ide_generic,amd74xx
unix                   24624  313 
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

```

You may notice that there isn't any snd* like modules installed. Also /dev/dsp doesn't exist in / whatever that is. /etc/modprobe.conf also doesn't exist. I reinstalled the packages I thought were crucial for sound by looking at the working system: live cd of breezy, but that didn't really help. Someone suggested hotplug, but I don't know how to use it.

I would really appreciate if anyone  could point me into the right direction.
I could reinstall the whole OS, but this is not the way of how I want to solve problems (Windows anyone?).

I installed Realtek drivers which gave me sound while playing movies (avi, bin), but that doesn't help me now (recently reinstalled them). I have no clue what to install or what to do to get snd_ like "things" back.

Any ideas how to tackle this?


Cheers,
Mitja

---

### Post by mlomker on 2005-12-02
I'm not convinced that your problem is only packages.  Attached is a list of the default packages installed on Kubuntu i386 out of the box.  You can make certain that they are installed by changing to the directory that you download the file to and issuing these commands:

```

sudo apt-get update
gunzip packages.txt.gz
sudo cat packages.txt | dpkg --set-selections
sudo apt-get upgrade

```

---

### Post by metoo on 2005-12-04
Install/re-install the alsa packages.
It's odd, that ubuntu does not come with the detection/configuration program from alsa.
You have probably already tried if you can re-detect your sound card via the system settings...

---


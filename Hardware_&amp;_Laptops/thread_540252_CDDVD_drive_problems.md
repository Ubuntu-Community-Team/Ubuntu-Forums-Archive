---
title: "CD/DVD drive problems"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by dean20007 on 2007-09-01
I Posted this a couple of days ago. I have a bit of an  update but still can't any cd/dvd to play in ubuntu. In nautilus there are two entries, one for CDROM1 and CD/DVDRW. The second I believe is mine. but this never appears to detect a CD has been entered. if I ask the CDROM1 to mount I get  a "mount: special device /dev/hdc does not exist"

This was working up until a few days ago and I don't think i have done anything to the system to break it. 

It is still the case that if I run gmplayer through terminal I can play DVDs


Please can anyone help, If there is anymore info/files I can provide which might help please just let me know. This is so frustrating!! 



```
Hi

Tonight I tried to burn a data cd using brasero. It appeared to complete after taking quite a long time, but now whenever I put a cd in the drive the drive seems to struggle and doesn't get recognized bu Ubuntu.

1) I can get DVDs and CDs to play running gmplayer via terminal however even in Places menu where I would expect see DVD or CD menu entry I get CD/DVD creator instead
2) putting a blank CD in the drive (or any data cd) it won't get recognized and I can't browse the disk either I get told there is no disk in the drive.

here is my fstab. Can anyone help
Code:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=1a77410d-bb22-40f9-bc81-884fde112d44 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=E6488002487FCFB3 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=843CBAE23CBACE84 /media/sda4     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=c5838b8c-d01d-43af-8868-088eae20f15c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by dean20007 on 2007-09-04
Bumping in the hope someone can help. I have searched the forums but can't see anyone else with a simialr problem. If i haven't provided enough info please let me know.

---

### Post by dean20007 on 2007-09-11
Further information in the hope someone can help

if i type eject in the terminal the drive will eject.

looking at the output of /etc/mtab seems to indicate that the drive is not there but IS in the fstab

```
/dev/sda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
/dev/sda2 /media/sda2 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/sda4 /media/sda4 ntfs rw,nls=utf8,umask=007,gid=46 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
```


my lspci output is thus 
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 755 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0c.0 Modem: Motorola Unknown device 3052 (rev 04)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
```

and my lsmod output is:

```
Module                  Size  Used by
ipv6                  268960  21 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nfs                   240876  0 
nfsd                  218992  17 
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
ppdev                  10116  0 
radeon                124576  3 
drm                    81044  4 radeon
powernow_k8            16064  0 
cpufreq_userspace       5408  0 
cpufreq_ondemand        9228  1 
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
freq_table              5792  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
pcc_acpi               13184  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
ac                      6020  0 
sbs                    15652  0 
asus_acpi              17308  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
backlight               7040  1 asus_acpi
video                  16388  0 
container               5248  0 
button                  8720  0 
battery                10756  0 
dock                   10268  0 
isofs                  36284  0 
udf                    85252  0 
nls_utf8                3072  2 
ntfs                  107764  2 
lp                     12452  0 
fuse                   46612  0 
joydev                 10816  0 
sn9c102                90892  0 
wacom                  17024  0 
xpad                    9988  0 
gspca                 607824  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
videodev               28160  2 sn9c102,gspca
snd_usb_audio          79744  0 
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
ac97_bus                3200  1 snd_ac97_codec
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
rt73                  214528  0 
snd_pcm                79876  4 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_usb_lib            17280  1 snd_usb_audio
snd_seq_midi            9600  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
pcspkr                  4224  0 
usbhid                 26592  0 
snd_rawmidi            25472  2 snd_usb_lib,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                38920  0 
v4l2_common            25216  2 sn9c102,videodev
v4l1_compat            15236  1 videodev
hid                    27392  1 usbhid
snd_hwdep               9988  1 snd_usb_audio
snd                    54020  14 snd_intel8x0,snd_ac97_codec,snd_usb_audio,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,snd_hwdep
soundcore               8672  1 snd
serio_raw               7940  0 
k8temp                  6656  0 
amd64_agp              13700  1 
sis_agp                 9604  0 
agpgart                35400  3 drm,amd64_agp,sis_agp
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  6 
tsdev                   8768  0 
evdev                  11008  6 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sd_mod                 23428  5 
sg                     36252  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
generic                 5124  0 [permanent]
sata_sis               10500  4 
sis5513                14856  0 [permanent]
floppy                 59524  0 
ehci_hcd               34188  0 
sis900                 24704  0 
mii                     6528  1 sis900
ohci_hcd               22532  0 
usbcore               134280  11 sn9c102,wacom,xpad,gspca,snd_usb_audio,rt73,snd_usb_lib,usbhid,ehci_hcd,ohci_hcd
pata_sis               14732  1 sata_sis
ata_generic             9092  0 
libata                125720  3 sata_sis,pata_sis,ata_generic
scsi_mod              142348  4 sd_mod,sg,sr_mod,libata
thermal                14856  0 
processor              31048  2 powernow_k8,thermal
fan                     5636  0 
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

### Post by dabl on 2007-09-11
Does this drive work right in Windows, both read and write?  Your fstab entry for it looks fine, but Nautilus should not be detecting 2 different drives -- this suggests something is screwed up elsewhere, unless you attempted manually to rename it or something.  :confused:

---

### Post by dean20007 on 2007-09-11
Thanks for the reply. 

I am solely using Ubuntu on this machine now, but the drive worked on XP read and write for just under 2 years absolutely and worked in ubuntu read and write fine up until a few weeks ago. Any other information I can give you to help troubleshoot just let me know 

Cheers

---

### Post by dabl on 2007-09-11
Hmmmmmm ... I tend to suspect hardware too often, but in this case, we are dealing with a device that is partly mechanical, and has 2 years of wear on it.  If it were mine, I'd be figuring out a way to prove beyond doubt that the old drive is still working correctly in SOME machine or OS, before continuing down the path of suspecting a Ubuntu setup problem.

Wouldn't hurt to remove and re-seat both ends of the cable to that drive, while you've got the lid off the computer, BTW.   :)

---

### Post by dean20007 on 2007-09-11
Cheers for the advice I'll definitely try that. Can you perhaps help me understand one point though, The drive will still play DVDs in Gm player, I can watch them no problem. If it was a hardware problem I would expect nothing to work but I may be misunderstanding.

Thanks for all your help so far i can;t begin to tell how much it is appreciated as this thread has been sitting unanswered for ages

---

### Post by dabl on 2007-09-11
Well, a DVD is not a CD, and reading is not writing.  So, I dunno -- it works on one medium in one mode, but that doesn't mean it's fully functional.

---

### Post by TaintedTux on 2007-09-12
IM having the same problem. It just started within the past week...after an update naturally. I dont know the culprit, and am not sure what to do. The drive works...I know this for a fact. Also I can hear it running when I put ANY media in but it dosn't detect the media....be it a cd, dvd, cdr dvdr etc...Ive tried them all. My solution? Ill probably just install Arch Linux ;-)

---


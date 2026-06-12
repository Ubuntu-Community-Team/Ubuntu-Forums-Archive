---
title: "Intel 845GV Graphic Issue"
date: 2008-12-31
forum: Hardware
---

### Post by monomalvado on 2008-12-31
Hello,
First time poster, long time linux tinkerer.

(I wrote up a huge explanation but then realized a lot of it was just be babbling so I condensed it.)

I am having a problem with changing my video driver from Vesa to an Intel driver for the 845GV chipset.
I am currently running Xubuntu 8.10 (After a crap load of work) and I'm having issues with the display.  It appears to be stuck in 1280x1024, which is awesome because thats my fav Resolution, however, windows a very choppy when being moved around and several small bugs that lead me to believe I got a bad graphics driver.

Here is some more information about the system.
It's a Compaq Presario sr1503WM (Yes Wal-mart edition... It was a Christmas gift.) It's got 1 Gig of ram (maxed :'( ) No additional PCI cards except a Agere Modem which I don't want to use anyway. It's an Intel Celeron D 2.93 GHz processor.  (I got four drives in it, three HDs and 1 CD-RW/DVD)

This is my lsmod

```
Module                  Size  Used by
ipv6                  263972  10 
af_packet              25728  2 
bridge                 56980  0 
rfcomm                 44432  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
speedstep_lib          12676  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       9856  0 
video                  25104  0 
output                 11008  1 video
wmi                    14504  0 
sbs                    19464  0 
pci_slot               12552  0 
sbshc                  13440  1 sbs
container              11520  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
lp                     17156  0 
snd_intel8x0           37532  2 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
serio_raw              13444  0 
psmouse                45200  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                 10624  0 
snd                    63268  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
joydev                 18368  0 
evdev                  17696  8 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
button                 14224  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
intel_agp              33724  1 
agpgart                42184  1 intel_agp
ext3                  133384  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usb_storage            81728  0 
libusual               27156  1 usb_storage
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
usbhid                 35840  0 
hid                    50560  1 usbhid
sg                     39732  0 
ata_piix               24580  2 
ata_generic            12932  0 
8139cp                 27520  0 
pata_acpi              12160  0 
libata                177312  3 ata_piix,ata_generic,pata_acpi
ohci1394               37936  0 
scsi_mod              155212  6 sbp2,usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ieee1394               96324  2 sbp2,ohci1394
8139too                31616  0 
mii                    13440  2 8139cp,8139too
uhci_hcd               30736  0 
ehci_hcd               43276  0 
usbcore               148848  6 usb_storage,libusual,usbhid,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  1 
```

In addition, this is my xorg.conf
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

I do have the intel drivers on the system, I installed them through the Syn Package Manager, however, this configuration file reflects a Vesa driver, which I assume is the root of my problems. (While I am familiar with the Linux platform, I'm not very well traversed in these specific driver issues, All my previous instillations had NO issues at all. (<3 my developer community.)

Any help with fixing this most likely simple problem would be greatly appreciated.

(As a sub note.  I have done the search through the forums for additional info.  My BIOS is correctly configured to allot 8MB of memory to it.)

Thanks!!!

---

### Post by abn91c on 2008-12-31
disable desktop effects, you may need to remove compiz completely if you have it installed

---

### Post by monomalvado on 2009-01-01
Okay so I decided to do some experimenting on my own and was able to do the following.

I manually edited the file with a small amount of knowledge and simply changed the "vesa" to "intel" and rebooted.
Good lord was it DARK when it started X up, but I was happier to see a login screen instead of a shell telling me I destroyed it. ;)

I adjusted the brightness and Gamma correction to make it legible and decided to go back at it.  I then replaced the "intel" with "i810" which did the black screening, shell saying "OMGZ X IS TEH BROKE!"

So I had to apt-get emacs, which was a blast from the past, so I could fix it again.  I went ahead and removed all of Compiz, /cry (I wanted to do those tight effects) but it seems to be up and going fine.

Thanks.

---

### Post by Astinsan on 2009-04-07
try this. Found it on launch pad.

```

Section "Device"
 Identifier "Configured Video Device"
 Driver "intel"
 Option "AccelMethod" "XAA"
EndSection

Section "Monitor"
 Identifier "Configured Monitor"
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
EndSection

```

I think there are several issues that cause it. 1 being the i810 driver pushed off the distro for the more up to date intel driver. Obviously the bugs are there. There is light on the horizon though. Since more are using the intel driver now. There is more likely going to be fixes. 

Second thing has to do with X11 changes that will cause headaches. Some programmers don't look to the future and provide drivers that don't rely on other software. Now that the software has changed the driver is broken. This is true for almost every OS. Not a linux only bug (vista eh em)

Hope this sheds some light on the issues.

---


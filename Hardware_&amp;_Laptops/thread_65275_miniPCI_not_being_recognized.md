---
title: "miniPCI not being recognized"
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by Drilus on 2005-09-13
I have a Dell latitude C400 with a True Mobile 1150 miniPCI that doesn't recognize after install.

Is there any way to get this working?

Edit: I have 5.10 Breezy

---

### Post by netsyd on 2005-09-13
[QUOTE=Drilus]I have a Dell latitude C400 with a True Mobile 1150 miniPCI that doesn't recognize after install.

Is there any way to get this working?

Edit: I have 5.10 Breezy[/QUOTE]

That should be based upon orinoco/prism/hermes... 

Do you have wireless-tools installed? 

What happens when you type into the console -  iwconfig? If the card is active you should see either eth1 or ath0.

What is the output of lsmod?


PS. A quick google search for this card turned up this page:
[http://www.flarg.com/dell_i4100/](http://www.flarg.com/dell_i4100/)

Highlights -- ```
The 802.11b wi-fi internal mini-PCI card was setup to use the wvlan_cs driver. This driver will probably work for most people. However, I have a LinkSys wireless access point. There is a bug in wvlan_cs which causes problems with the linksys access point. The orinoco_cs driver fixes the problem. It is probably good to upgrade to the orinoco_cs driver anyway, since it has better support and is generally more stable.

To switch to the orinoco_cs driver, you can grab the configuration files for the wireless options at the end of this document.

The /etc/pcmcia/config file must force loading of the proper modules: 
device "orinoco_cs"
  class "network" module hermes", "orinoco", "orinoco_cs"

The /etc/pcmcia/config file must bind the orinoco driver to the card: 
card "Lucent Technologies WaveLAN Adapter"
  version "Lucent Technologies", "WaveLAN/PCMCIA"
  bind "orinoco_cs"

The /etc/pcmcia/wireless.opts file must be modified by hand to support your wireless setup. I had to switch to the "Ad-Hoc" mode and set my ESSID to "linksys". It is sometimes useful to check the WindowsXP network properties to find out this information. 


``` 



Hope some of that helps. I had a truemobile 1300series that was pain in the you know what. Sometimes these cards just don't want to play nice! ](*,)

---

### Post by Drilus on 2005-09-13
I'm sorry but I'm a complete newb with linux. So that stuff about the orinoco drivers i'm only vaguely familiar with.

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

lsmod:
```

Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
sony_acpi               5516  0
pcc_acpi               11392  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
tsdev                   7616  0
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
snd_ens1371            22240  1
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         71804  1 snd_ens1371
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  1 snd_pcm
mptscsih               31188  0
mptbase                39008  1 mptscsih
scsi_mod              124872  1 mptscsih
i2c_piix4               8336  0
i2c_core               19728  2 i2c_acpi_ec,i2c_piix4
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  1 intel_agp
evdev                   9088  0
psmouse                25988  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  2
jbd                    48536  1 ext3
dm_mod                 50364  4
vga16fb                12232  1
vgastate                8320  1 vga16fb
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  3
ide_generic             1664  0
pcnet32                24836  0
mii                     5248  1 pcnet32
uhci_hcd               28048  0
usbcore               104188  2 uhci_hcd
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
unix                   24624  625
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
vesafb                  8088  0
cfbcopyarea             4480  2 vga16fb,vesafb
cfbimgblt               2944  2 vga16fb,vesafb
cfbfillrect             3840  2 vga16fb,vesafb
softcursor              2432  2 vga16fb,vesafb
capability              5000  0
commoncap               6784  1 capability

```

---


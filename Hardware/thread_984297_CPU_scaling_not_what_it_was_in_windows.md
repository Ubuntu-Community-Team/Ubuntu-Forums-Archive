---
title: "CPU scaling not what it was in windows"
date: 2008-11-16
forum: Hardware
---

### Post by malfist on 2008-11-16
I'm trying to scale my CPU power. I have a dual core, and when I"m on battery power I'd like to turn a core off, but that's not my main question.

Often while I was on windows, my cpu frequency would scale all the way down to 200MHz, with ubuntu I have two option 1GH or 1.5GHz. Is there a way to improve this?

---

### Post by wirespot on 2008-11-16
In theory you can mess around with files under /sys. You can echo values to some of them to make things happen. Two examples.

```
echo 0 > /sys/devices/system/cpu/cpu1/online
```

The above will take the second core offline. You echo 1 to re-enable it. Same goes for other cores. First core doesn't have that file so you can never take it offline.

```
echo 800000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq
```

The above will set the bottom cpu scaling frequency to 800 MHz. The cpufreq dir is symlinked between all cores so it doesn't matter via which cpuN dir you access it. Of course, you need to have cpufreq activated and even so the current scaling driver may refuse to go below a certain value. For me 1 GHz is as low as it will go.

Perhaps [this article](http://xlife.zuavra.net/index.php/70/) may help you more.

---

### Post by malfist on 2008-11-16
Thanks for the tip for turnning it off, but it doesn't work with just sudo prefixed to it, says permision denided. I have to do sudo su before I can get it to accept the command.

---

### Post by Keyper7 on 2008-11-16
Sudo does not work with output redirection, you might want to try using the "tee" command:

echo 0 | sudo tee /sys/devices/system/cpu/cpu1/online

PS: It might take an entire day to check your reply to this, but I will.

---

### Post by malfist on 2008-11-16
That fixed it. Although I can't get a my cpu to scale below 1GH :(

---

### Post by Keyper7 on 2008-11-16
Try gconf-editor. Perhaps the options in apps > gnome-power-manager > cpufreq might be useful somehow? Although if I remember correctly I think they are also restricted to the same levels...

---

### Post by malfist on 2008-11-16
There is no cpufreq under gnome-power-manager. I had already checked...

---

### Post by wirespot on 2008-11-17
If it can't go below 1 GHz it's probably a limitation of the current cpufreq driver.

Try to see if there's another driver you can use (the article I linked to has a command under "Finding the necessary modules" that will list all installed kernel modules). Also use cpufreq-info and cpufreq-set.

Most cpufreq drivers are CPU-related, such as powernow-k8. But there are a few motherboard/hybrid drivers too, like acpi-cpufreq or cpufreq-nforce2. acpi-cpufreq is probably used by default. Depending on your mobo chipset/CPU you could try switching to another driver.

If that doesn't work either than sorry, it probably means that in Windows you were using an advanced feature of the motherboard through the drivers that came with the install disk. Which is probably not replicated by the Linux kernel drivers. Usually it's a form of on-the-fly underclocking which changes the FSB and/or multiplier.

You can try something like [lfsb](http://sourceforge.net/projects/lfsb/), at your own risk.

Also check out the [LessWatts Tips](http://www.lesswatts.org/tips/) for powersaving on Linux. Here's something interesting from them: :)

> Linux has the ability to, at runtime, take cores offline. Some people use this feature in an attempt to save power. However, measurements show that an offline core actually uses more power than a core that's in an idle sleep state.

---

### Post by Keyper7 on 2008-11-17
The fact that there is not even a cpufreq option in gconf-editor might be a hint that the proper driver is not even installed, but I'm not sure.

Which processor do you have, exactly?

---

### Post by malfist on 2008-11-17
Some intel dual core, 1.5GHz. How can I check?

---

### Post by wirespot on 2008-11-18
[http://xlife.zuavra.net/index.php/70/#checking-the-cpufreq-sysfs-directory](http://xlife.zuavra.net/index.php/70/#checking-the-cpufreq-sysfs-directory)

---

### Post by Keyper7 on 2008-11-18
mafilst, could you post the output of "cat /proc/cpuinfo" and "lsmod"?

---

### Post by malfist on 2008-11-19
```

jerome@ubuntu-lappy:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz
stepping	: 13
cpu MHz		: 1000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc up arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 2992.43
clflush size	: 64
power management:

```

```

jerome@ubuntu-lappy:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
usb_storage            81728  1 
libusual               27156  1 usb_storage
i915                   38144  2 
drm                    86056  3 i915
af_packet              25728  4 
binfmt_misc            16904  1 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
sco                    18308  2 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 bnep,rfcomm,sco,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
pci_slot               12552  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
loop                   23180  0 
ipv6                  263972  17 
joydev                 18368  0 
pcmcia                 43052  0 
snd_hda_intel         381616  3 
arc4                    9984  2 
ecb                    10880  2 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
evdev                  17696  13 
serio_raw              13444  0 
snd_seq_dummy          10884  0 
iwl3945                98804  0 
psmouse                45200  0 
pcspkr                 10624  0 
snd_seq_oss            38528  0 
rfkill                 17176  2 iwl3945
snd_seq_midi           14336  0 
mac80211              216820  1 iwl3945
snd_rawmidi            29824  1 snd_seq_midi
led_class              12164  1 iwl3945
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211               32392  2 iwl3945,mac80211
tifm_7xx1              13824  0 
sdhci_pci              15360  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tifm_core              16028  1 tifm_7xx1
video                  25104  0 
sdhci                  23940  1 sdhci_pci
output                 11008  1 video
container              11520  0 
yenta_socket           31756  1 
rsrc_nonstatic         19072  1 yenta_socket
mmc_core               58268  1 sdhci
wmi                    14504  0 
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
battery                18436  0 
ac                     12292  0 
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 14224  0 
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 37908  0 
soundcore              15328  1 snd
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp
pci_hotplug            35236  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133384  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sha256_generic         20352  0 
aes_i586               15744  2 
aes_generic            35880  1 aes_i586
cbc                    11776  1 
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  0 
ata_generic            12932  0 
ohci1394               37936  0 
pata_acpi              12160  0 
ahci                   37132  2 
ieee1394               96324  2 sbp2,ohci1394
libata                177312  4 ata_piix,ata_generic,pata_acpi,ahci
scsi_mod              155212  6 usb_storage,sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43404  0 
dm_crypt               21124  1 
crypto_blkcipher       25476  4 ecb,cbc,dm_crypt
uhci_hcd               30736  0 
e1000e                112680  0 
usbcore               149104  5 usb_storage,libusual,ehci_hcd,uhci_hcd
dm_mirror              26880  0 
dm_log                 17924  1 dm_mirror
dm_snapshot            26276  0 
dm_mod                 63432  11 dm_crypt,dm_mirror,dm_log,dm_snapshot
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

---

### Post by Keyper7 on 2008-11-19
Okay, that's weird... You do have the cpufreq drivers.

Could you tell me if the CPU frequency applet works? Right click on the gnome-panel, add it and check what the tooltip says.

---

### Post by malfist on 2008-11-19
It does work.

---

### Post by Keyper7 on 2008-11-20
Okay, lemme try brute force: what do you get when you search for "cpufreq" in the gconf-editor? (Edit > Find)

---

### Post by sdennie on 2008-11-20
I have a feeling the 200Mhz number you were seeing in Windows was simply incorrect.  I don't think any Core 2 Duos get even near that low for frequency scaling and a quick google search makes me believe that 1Ghz is the lowest frequency for that chip.

---

### Post by malfist on 2008-11-20
The 200MHz was coming from RealTemp which monitored my CPU temp and frequency. I'm pretty sure it was managing both clock speed and FBS. I also read somewhere that intel was complaining because they gave microsoft expected parameters for power savings and microsoft ignored it. Particularly on the minimum speed, i.e. Intel would recommend a minimum speed for optimal power usage and windows would throttle it even lower.

---

### Post by sdennie on 2008-11-20
You can check to see what speeds your cpu supports with:

```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

```

As far as I know, there is no way to change those numbers on linux.  As far as Microsoft going out of spec for power savings reasons, are you certain you aren't referring to chip voltage?  Each P-state can have a different (non-standard) voltage.  Maybe what you were seeing in Windows was an undervolted 1Ghz state that was mistaken for the voltage that would be used for a 200Mhz state.  You can, at your own risk, undervolt a chip in linux as well: [http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)

---

### Post by malfist on 2008-11-21
No it was the frequency. Realtemp monitors tempurature, volage, and frequency. I don't think the voltage was changing at all.

---

### Post by paulistoan on 2009-04-30
Hi,

You might like to try p4-clockmod instead of acpi_cpufreq.

---


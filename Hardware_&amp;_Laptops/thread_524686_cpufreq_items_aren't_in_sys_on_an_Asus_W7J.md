---
title: "cpufreq items aren't in sys on an Asus W7J"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by edisk on 2007-08-13
Hi all -

I'm writing because I'm having a problem with CPU frequency scaling on my Asus W7J laptop. Essentially I'm on a fresh install of Feisty, and I am unable to get cpufreq to work. This computer has an Intel Core Duo T2400 which previously worked with frequency scaling without too much fuss, so I've never really had to learn what was going on under the hood. I've gotten to a point where I'm not sure what to try next, and I'd appreciate it if someone could lightly bump me in the right direction.

This starts with the Gnome panel icons; I found a howto saying I had to dpkg-reconfigure them, which I did. They still weren't working. I ultimately did a little more detective work and found out that even though the appropriate cpufreq kernel modules seem to be loaded, the cpufreq items inside the sysfs don't exist at all. There is nothing obviously relevant in dmesg.

I don't know where exactly it ties in, but ACPI is loaded, and it furthermore seems to acknowledge that I have two cores, each of which should be able to be stepped down: inside the two /proc/acpi/processor/CPUx, I see "throttling control:      yes".

I've tried to look this up on the Ubuntu forums, as well as doing wider Google searches, and the fact that I've not found anything specific to my problem makes me think that I'm missing something small and stupid. Could anyone here shed a little bit of light on this?


----
uname -a:
```
Linux nixon 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

```

To give you an idea of what's wrong:
```
sami@nixon:~$ cpufreq-selector -g conservative
No cpufreq support
sami@nixon:~$ cd /sys/devices/system/cpu/
sami@nixon:/sys/devices/system/cpu$ ls
cpu0  cpu1  sched_mc_power_savings
sami@nixon:/sys/devices/system/cpu$ cd cpu0
sami@nixon:/sys/devices/system/cpu/cpu0$ ls
cache  crash_notes  topology

```

lsmod:
```
sami@nixon:/sys/devices/system/cpu/cpu0$ lsmod
Module                  Size  Used by
usbhid                 26592  0 
hid                    27392  1 usbhid
michael_mic             3584  6 
arc4                    2944  6 
ecb                     4480  6 
blkcipher               6784  1 ecb
ieee80211_crypt_tkip    12032  3 
isofs                  36284  1 
udf                    85252  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
ipv6                  268960  12 
ppdev                  10116  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  0 
cpufreq_userspace       5408  0 
cpufreq_powersave       2688  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
battery                10756  0 
ac                      6020  0 
dock                   10268  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
button                  8720  0 
container               5248  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
nls_iso8859_1           5120  2 
nls_cp437               6784  3 
vfat                   14208  2 
fat                    53916  1 vfat
visor                  20364  0 
usbserial              32488  1 visor
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
snd_hda_intel          21912  1 
snd_hda_codec         205056  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_mixer_oss          17408  1 snd_pcm_oss
joydev                 10816  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
tpm_infineon            9112  0 
tpm                    16672  1 tpm_infineon
tpm_bios                8448  1 tpm
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               4713780  22 
ipw3945               118816  1 
ieee80211              34760  1 ipw3945
ieee80211_crypt         7040  2 ieee80211_crypt_tkip,ieee80211
serio_raw               7940  0 
soundcore               8672  1 snd
hci_usb                18204  2 
bluetooth              55908  7 rfcomm,l2cap,hci_usb
psmouse                38920  0 
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
pcspkr                  4224  0 
i2c_core               22656  2 i2c_ec,nvidia
sdhci                  18700  0 
mmc_core               26756  1 sdhci
intel_agp              25244  1 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
agpgart                35400  2 nvidia,intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
af_packet              23816  8 
tsdev                   8768  0 
evdev                  11008  8 
ext3                  133128  2 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  1 
sd_mod                 23428  6 
cdrom                  37664  1 sr_mod
ata_generic             9092  0 
ata_piix               15492  6 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ehci_hcd               34188  0 
generic                 5124  0 [permanent]
r8169                  32392  0 
uhci_hcd               25360  0 
usbcore               134280  7 usbhid,visor,usbserial,hci_usb,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
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

cat /proc/cpuinfo:
```
sami@nixon:/sys/devices/system/cpu/cpu0$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1828.855
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3661.63
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1828.855
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3657.70
clflush size    : 64

```

---

### Post by yorkie on 2007-08-13
here is an excellent howto cpu scaling its easy to do and it works

[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

use it myself
good luck

---

### Post by heor on 2007-08-15
I'm having the exact same problem on the same computer. Nothing in that guide works because there are no cpufreq directories in /sys/devices/system/cpu/cpuX. And running cpufreq-selector only gives: "No cpufreq support"

I'm clueless...

---

### Post by SubZero_AK on 2007-10-23
I have the same laptop and have noted similar behavior.  First off, problems began when I updated to the revision 304 BIOS.  Even the latest upgrade to 305 did not help.  I had no problems when I ran the 302 BIOS that shipped with my machine.  There was no difference between Fiesty and Gutsy, they all exhibited the same symptoms on this box.

I can get the frequency scaling to work manually if I do a few things.  Note, I am typing from work in a Windows environment.  So, if I skip a step or goof the syntax, please forgive me.  What I do to make the scaling work is this:

1. I unload the running module:
sudo modprobe -rv acpi-cpufreq

2. I reload the module
sudo modprobe acpi-cpufreq

3. I set the scaling governor
sudo cpufreq-set -g ondemand

Bingo!  Suddenly the scaling works.  I have not spent any time investigating what causes this behavior, I suspect something gets loaded in the wrong order.  Maybe someone else can chime in on a way to fix this at boot time.

Now, if I could keep the fix the ata timeouts and clean up the sound, this would be the perfect OS!

Cheers,
Mark

---

### Post by Gifty85 on 2007-11-12
I have this problem too... :(

Any solution?!

---


---
title: "IBM ThinkPad T42 on Ubuntu *GRAPHICS ISSUE!* HELP!!!"
date: 2009-01-29
forum: Hardware
---

### Post by tombom62 on 2009-01-29
Ok, I've just installed ubuntu 8.10 on a friend's laptop, everything went great, even network, and audio drivers.... PERFECT!  Even WinE running flawlessly even though I've never installed it before :p ;) , so, the problem:
I followed this tutorial, from 2005:
[http://aaltonen.us/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/](http://aaltonen.us/2005/03/02/ubuntu-linux-on-the-ibm-thinkpad-t42/)
and I followed what it said about video drivers, and, it can't play any games, or graphical programs that I've seen work on WinE, and it boots in "Low graphics Mode" - Whatever that is, it's at like 640x480 and basically sucks.  Any HELP?

thanks in advance,
Tommy

---

### Post by IQRules on 2009-01-29
Under Low graphic Mode, can you open xterm and run this?


$ lsmod | grep fglrx

fglrx                 237088  9

You might try go to safemode, and remove /etc/X11/xorg.conf file and reboot.

---

### Post by tombom62 on 2009-01-30
Im sorry, im a bit of a n00b, what's xterm, is it terminal?  I renamed xorg.conf, and it didn't help.

---

### Post by tombom62 on 2009-01-30
or do i need to totally delete it?

---

### Post by ajmctaggart on 2009-01-30
Renaming it should have been good enough...xterm is just the terminal, you may need to run the above command with "sudo"

From System, you could also check to see if you need any restricted drivers?  Sorry but until you post output we don't know what card you've got, so Restricted Drivers is a quick way to see if there's a driver available to correct the lo-res...

The laptop is probably running an ATI card, correct?

Check this thread, last post...may be worth a shot...[http://ubuntuforums.org/archive/index.php/t-979379.html]("http://ubuntuforums.org/archive/index.php/t-979379.html")

---

### Post by tombom62 on 2009-01-30
here's the terminal, the whole thing:
> edward@edward-laptop:~$ sudo lsmod  grep fglrx
Usage: lsmod
edward@edward-laptop:~$ sudo lsmod
Module                  Size  Used by
ipv6                  263972  8 
wlan_wep               14080  1 
isofs                  40100  1 
udf                    88356  0 
crc_itu_t              10112  1 udf
af_packet              25728  4 
binfmt_misc            16904  1 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 sco,bnep,rfcomm,l2cap
ppdev                  15620  0 
acpi_cpufreq           15500  0 
cpufreq_stats          13188  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
container              11520  0 
wmi                    14504  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
lp                     17156  0 
joydev                 18368  0 
pcmcia                 43052  0 
wlan_scan_sta          20608  1 
ath_rate_sample        19968  1 
thinkpad_acpi          66176  0 
rfkill                 17176  1 thinkpad_acpi
led_class              12164  1 thinkpad_acpi
nvram                  16524  1 thinkpad_acpi
evdev                  17696  11 
battery                18436  0 
serio_raw              13444  0 
ath_pci                99096  0 
ac                     12292  0 
psmouse                45200  0 
wlan                  211952  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               198864  3 ath_rate_sample,ath_pci
yenta_socket           31756  2 
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
video                  25104  0 
output                 11008  1 video
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
nsc_ircc               28816  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
irda                  199612  1 nsc_ircc
crc_ccitt              10112  1 irda
snd_seq_dummy          10884  0 
pcspkr                 10624  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
button                 14224  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              33724  1 
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
agpgart                42184  1 intel_agp
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  1 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  4 
pata_acpi              12160  0 
ata_generic            12932  0 
libata                177312  3 ata_piix,pata_acpi,ata_generic
e1000                 132164  0 
scsi_mod              155212  4 sr_mod,sd_mod,sg,libata
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  3 ehci_hcd,uhci_hcd
dock                   16656  1 libata
thermal                23708  0 
processor              42156  3 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 


---

### Post by tombom62 on 2009-01-30
THANK YOU!  That thread had the solution!  now it can open anything I've tried in wine, and boots normally. thanks!:)

---

### Post by ajmctaggart on 2009-02-02
Oh good, I didn't have a connection over the weekend, but I'm glad your issue was resolved!

---


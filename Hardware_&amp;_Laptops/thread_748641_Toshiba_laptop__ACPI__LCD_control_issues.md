---
title: "Toshiba laptop : ACPI / LCD control issues"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by hell_rider on 2008-04-07
Hello all,

Am having some major problem getting to control my LCD brightness on my laptop.

System is as follows:

Satellite A100 (Asia specific model, I believe)
Model no : PSAA9L 0ML00C
Intel Core Duo T2300 1.66 GHz
BIOS : Phoenix v 1.80  (YES - The dreaded Phoenix BIOS)

Its a dual boot setup with XP Pro.
I originally installed Ubuntu 7.04 from the ISO CD and then upgraded to 7.10 using Synaptic.

Installation and upgradation was smooth and all hardware works (display , wireless etc.)

One of the main issues being abysmal battery life, I tried to look at ways to reduce power consumption which is when I discovered that I am unable to control the LCD brightness.  There are some Toshiba files and utilities but apparently they won't work on a Toshiba laptop with Phoenix BIOS.

I trawled the web and these forums but have been unable to come up with anything.

I came across the below thread right here on Ubuntu forums:
[http://ubuntuforums.org/showthread.php?t=321089]("http://ubuntuforums.org/showthread.php?t=321089")

Unfortunately, his solution does not work in my case.  Specifically, when I issue the mentioned "cat" command, my result is a no-go.  It says "not supported".
```
$ cat /proc/acpi/video/VGA/LCD/brightness
<not supported>

```
It is actually supposed to show a set of brightness levels, which you can also set with the echo command.  but as seen above, it does not work for me.

However, I have another folder in the same directory structure and a similar file in the location :
/proc/acpi/video/GFX0/LCD/brightness

The same command on this file gives me the following output:
```
$ cat /proc/acpi/video/GFX0/LCD/brightness
levels:  80 60 0 20 40 60 80 100
current: 0
```

When I try to set it to something else I get the following output.  It does change the value, but the screen brightness is unchanged.
```
$ echo 20 | sudo dd of=/proc/acpi/video/GFX0/LCD/brightness
0+1 records in
0+1 records out
3 bytes (3 B) copied, 0.00015373 seconds, 19.5 kB/s
```

So, I am now basically stuck.  Can someone please tell me if there is anything else I can try ?  Is there any other module that needs to be loaded ?  I am pasting below the output of lsmod.```

$ lsmod
Module                  Size  Used by
binfmt_misc            12936  1 
fglrx                 656352  15 
video                  18060  820 
dock                   10656  0 
button                  8976  0 
ac                      6148  0 
container               5504  0 
sbs                    19592  0 
battery                11012  0 
acpi_cpufreq           10568  0 
cpufreq_powersave       2688  2 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  0 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_userspace       5280  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
ieee80211_crypt_wep     6272  1 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  2 parport_pc,lp
joydev                 11328  0 
snd_hda_intel         263712  1 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  2 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
pcmcia                 41388  0 
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ipw3945               119840  1 
snd                    54660  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci                  18828  0 
mmc_core               28420  1 sdhci
serio_raw               8068  0 
ieee80211              35656  1 ipw3945
ieee80211_crypt         7040  2 ieee80211_crypt_wep,ieee80211
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
soundcore               8800  2 snd
pcmcia_core            40980  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
tifm_7xx1               8576  0 
tifm_core              11268  1 tifm_7xx1
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
psmouse                39952  0 
ipv6                  273892  10 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
intel_agp              25620  0 
agpgart                35016  2 fglrx,intel_agp
evdev                  11136  4 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  4 
usbhid                 29536  0 
hid                    28928  1 usbhid
ohci1394               36528  0 
ata_piix               17540  3 
ieee1394               96312  2 sbp2,ohci1394
e100                   37644  0 
mii                     6528  1 e100
uhci_hcd               26640  0 
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  5 sbp2,sg,sr_mod,sd_mod,libata
ehci_hcd               36492  0 
usbcore               138632  4 usbhid,uhci_hcd,ehci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  14 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

I, however, see the following files , but am totally lost if and how they are used :
```
/etc/acpi/events/tosh-battery
/etc/acpi/events/tosh-brightness-down
/etc/acpi/events/tosh-brightness-up
/etc/acpi/events/tosh-hibernate
/etc/acpi/events/tosh-ibutton
/etc/acpi/events/tosh-lock
/etc/acpi/events/tosh-mail
/etc/acpi/events/tosh-media
/etc/acpi/events/tosh-mute
/etc/acpi/events/tosh-next
/etc/acpi/events/tosh-play
/etc/acpi/events/tosh-prev
/etc/acpi/events/tosh-sleep
/etc/acpi/events/tosh-stop
/etc/acpi/events/tosh-wireless
/etc/acpi/events/tosh-www
/etc/acpi/events/video_brightnessdown
/etc/acpi/events/video_brightnessup
```

I also see the following message in the log files in System Log Viewer: (syslog,  messages, kern.log)
 kernel: [ 3399.544000] ACPI: Please implement acpi_video_bus_ROM_seq_show

Would really appreciate your help in resolving this issue.  

Thanks in advance,

ciao,
hell_rider

---

### Post by hell_rider on 2008-04-09
After some further googling and investigation, I found that the lshal command  does not show device "laptop-panel" in its output. Neither is there anything like "monitor" or "display".

Is this the reason it gives me a "<not supported>" message when I try to read the contents of the /proc/acpi/video/VGA/LCD/brightness file ?

If I can read/write to the above "brightness" file I believe I will be able to set the brightness levels of my laptop LCD. But I am not finding any way of being able to do that or even understand why I am unable to do that.

Some help please guys.

thanks.

---

### Post by TmP on 2008-04-09
I think I've got a solution for you:
[http://ubuntuforums.org/showthread.php?t=316358&highlight=omnibook](http://ubuntuforums.org/showthread.php?t=316358&highlight=omnibook)

don't bother with the instructions on how to set up buetooth if you don't have it.

Just 
1.
$ sudo apt-get install subversion build-essential linux-source linux-headers-generic

2.
$ cd ~
$ mkdir omnibook
$ cd omnibook
$ svn co [https://omnibook.svn.sourceforge.net/svnroot/omnibook/omnibook/trunk](https://omnibook.svn.sourceforge.net/svnroot/omnibook/omnibook/trunk)

3.
$ cd trunk
$ make
$ sudo make install
$ sudo make load

then add omnibook to modules
sudo gedit /etc/modules

and at the end add 
omnibook

restart your computer

This _should_ work.

KTHNXBYE

---


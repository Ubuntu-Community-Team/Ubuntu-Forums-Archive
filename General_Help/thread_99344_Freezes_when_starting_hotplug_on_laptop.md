---
title: "Freezes when starting hotplug on laptop"
date: 2005-12-05
forum: General Help
---

### Post by Paloseco on 2005-12-05
I have tried the ubuntu/kubuntu 5.10 live and install and none of the 4 is able to boot on my [Clevo M540G]("http://www.clevo.com.tw/products/M540G.asp"). The slax boots perfectly and even I have installed suse 10. The pcbsd also works perfect. Just freezes when starting the hotplug subsystem. Any ideas?

---

### Post by ok67 on 2005-12-05
Are U using ndiswrapper and a wireles lan card?
Mine also freeze if I do this, the solution is to remove the wlan card when booting, and insert it after the computer has finished booting.

The next I like to know is how to automaticaly activate my networksettings when the card is inserted. Now I have to run network-admin manualy afterwards to start the wlan.

---

### Post by Paloseco on 2005-12-05
I have it plugged since is is installed inside the laptop but is disconnected. I do it with FN+F11 and the green light goes off. I wonder if you mean that or to disconnect physically the card.

---

### Post by ok67 on 2005-12-05
Yes I have a PCMCIA Linksys card, that I physically disconnect during boot.

---

### Post by Paloseco on 2005-12-05
I won´t disconnect physically the card, this is a bit overkill. I hope next version to have it solved. I will use suse 10 meanwhile.

---

### Post by newuser111 on 2005-12-05
you can just edit /etc/default/hotplug to disable hotplugging for a module, it even tells you in the file how to do so

# You can use HOTPLUG_RC_<subsystem>=no to disable hotplugging for it, e.g:
#HOTPLUG_RC_pci=no
#HOTPLUG_RC_net=no

---

### Post by Paloseco on 2005-12-07
Finally I have found a way to not to load the module, although is not permanent.
First I went to /etc/init.d/hotplug and changed the line 20 to QUIET=no
After booting and pressing Alt+F1 the output was:
> sysenter_past_esp ...(stuff)
snd-hda-intel: can´t be loaded
missing kernel or user mode driver snd_hda_intel
<6> pci_hotplug: PCI Hor plug PCI core version 0.5
After that i added snd-hda-intel to /etc/hotplug/blacklist and now boots correctly.

After that I could not get the sound card working. Here is some info.
> root@ubuntu:~# modprobe snd-hda-intel
sh: line 1:  8723 Segmentation fault      modprobe --ignore-install snd-hda-intel
FATAL: Error running install command for snd_hda_intel


root@ubuntu:~# lsmod
Module                  Size  Used by
snd_hda_intel          15884  1
snd_hda_codec          72064  1 snd_hda_intel
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  6 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_hda_intel,snd_pcm
ipv6                  217408  6
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_centrino      7380  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
i915                   17920  1
drm                    58004  2 i915
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
rtc                    11832  0
ohci1394               30644  0
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
intel_agp              21276  1
agpgart                32328  3 drm,intel_agp
reiserfs              217200  1
nls_iso8859_1           4224  2
nls_cp437               5888  2
vfat                   12288  2
fat                    46492  1 vfat
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
sr_mod                 15652  0
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
usbhid                 30688  0
r8169                  23180  0
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 36996  0
cdrom                  33952  2 sr_mod,ide_cd
ide_disk               16128  6
ide_generic             1664  0
ata_piix                9476  0
ahci                   11268  0
libata                 47876  2 ata_piix,ahci
scsi_mod              124872  4 sr_mod,sbp2,ahci,libata
piix                    9476  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,piix
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


root@ubuntu:~# rmmod snd_hda_intel
ERROR: Module snd_hda_intel is in use





---


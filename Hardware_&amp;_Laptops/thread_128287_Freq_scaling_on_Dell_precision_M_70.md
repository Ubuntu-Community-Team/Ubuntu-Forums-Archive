---
title: "Freq scaling on Dell precision M 70"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by bretonfou on 2006-02-11
The application pu-freqselector apparently  works 
it is set with SUI, anyway i tried first to run it as root. 

I don't even know what is the applet that provide a GUI to that utility, i truly hate all that  graphical mouse and click thing. 



I also tried to change the governor to performance, but it fails too. 

 


It seems that i have the modules loaded ... otherwise anyway i would not get the possible freq list :


 lsmod
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  2 rfcomm,l2cap
ipv6                  217408  8
speedstep_centrino      7380  1
cpufreq_powersave       1920  0
cpufreq_stats           5124  0
cpufreq_userspace       4444  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
pcmcia                 24584  2
tc1100_wmi              6916  0
video                  16004  0
battery                 9604  0
container               4608  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
pcc_acpi               11392  0
sony_acpi               5516  0
ac                      4996  0
dev_acpi               11396  0
hotkey                  9508  0
af_packet              20232  2
pcspkr                  3652  0
rtc                    11832  0
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  1 intel_agp
nls_cp437               5888  2
ntfs                   92016  1
ext3                  115976  1
jbd                    48536  1 ext3
tsdev                   7616  0
joydev                  9280  0
evdev                   9088  1
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
reiserfs              217200  3
dm_mod                 50364  1
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
usbhid                 30688  0
tg3                    83716  0
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  4 usbhid,ehci_hcd,uhci_hcd
sd_mod                 17424  7
ide_generic             1664  0
ide_core              125268  1 ide_generic
ata_piix                9476  13
ahci                   11268  0
libata                 47876  2 ata_piix,ahci
scsi_mod              124872  3 sd_mod,ahci,libata
unix                   24624  431
fbcon                  34176  71
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
vesafb                  8088  1
cfbcopyarea             4480  1 vesafb
cfbimgblt               2944  1 vesafb
cfbfillrect             3840  1 vesafb
softcursor              2432  1 vesafb
capability              5000  0
commoncap               6784  1 capability
speren@fromage:~/MIX/MIX$



The gnome-power applet returns errors .. but tha'ts another topic. 




speren@fromage:~/MIX/MIX$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_avail able_frequencies
2133000 1867000 1600000 1333000 1067000 800000


speren@fromage:~/MIX/MIX$ cpufreq-selector -f 1867000 


speren@fromage:~/MIX/MIX$ cat  /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 2.13GHz
stepping        : 8
cpu MHz         : 798.198
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx est tm2
bogomips        : 1572.86

---


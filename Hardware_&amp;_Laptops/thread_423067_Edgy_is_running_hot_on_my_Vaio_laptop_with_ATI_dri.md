---
title: "Edgy is running hot on my Vaio laptop with ATI drivers"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by s0n|k on 2007-04-25
So Ubuntu is running my cpu ragged. The fan never seems to die down when running it. I've ran other Unix distros (Solaris 10, RH9, etc..) as well as XP and have never seen this problem. I have a Vaio 1.8mhz Pentium M with 512mb and an ATI card. Here is the output of my lsmod:

```
Module                  Size  Used by
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
sonypi                 24252  0 
radeon                118816  3 
drm                    74644  4 radeon
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sbs                    16804  0 
sony_acpi               6412  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dev_acpi               12292  0 
button                  7952  0 
battery                11652  0 
container               5632  0 
ac                      6788  0 
asus_acpi              17688  0 
ipv6                  272288  10 
af_packet              24584  4 
sbp2                   24584  0 
scsi_mod              144648  1 sbp2
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
pcmcia                 40380  0 
e100                   38020  0 
ipw2200               115652  0 
yenta_socket           28812  1 
rsrc_nonstatic         15360  1 yenta_socket
ieee80211              35272  1 ipw2200
ieee80211_crypt         7552  1 ieee80211
mii                     6912  1 e100
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
joydev                 11200  0 
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
tsdev                   9152  0 
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
psmouse                41352  0 
hw_random               7320  0 
intel_agp              26012  1 
agpgart                34888  2 drm,intel_agp
serio_raw               8452  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
evdev                  11392  2 
ext3                  142856  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  3 ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
piix                   11780  1 
generic                 6276  0 
thermal                15624  0 
processor              31560  2 speedstep_centrino,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability
```

Oh yea, and when I shut my lid it doesn't go into standby mode either.

---

### Post by moon2js on 2007-04-27
Edgy? Did you just install it or has it always been like this?

My P3 with ATI Radeon 7500 has been SO NOISY ever since I installed Feisty. I don't remember it being this noisy with Edgy.

I've been trying to figure out what the extra noise is, and I traced it to the fan on the video card, which turns on a few minutes after startup and stays on regardless of whether I'm doing anything graphics intensive or not.

I used to prefer this older machine because it's not as loud as my other computer. (All my computers are handmedowns.) But now it's so loud I can't bear it.

I'm using the default drivers that were autodetected with installation. Would meddling with the ATI drivers make a difference? I'm also thinking about rolling back to Edgy or Dapper. Or maybe making it a headless server. It's SO LOUD.

Also, is there any way I can monitor temperature of the video card?

---

### Post by vvlist on 2007-06-22
I have the same problem. You can monitor your system temps by installing lm-sensors and sensors-applet. But before you run sensors-applet, run sensors-detect.

---

### Post by whayong on 2007-06-22
I can't comment to much on the temp issue you're having.  Exactly how hot is it running?  The reason I asked is I thought my Vaio was running hot as well because it felt warmer to the touch then when it was running XP.  I installed a temp monitor, I cannot remember which one to be honest, only to find out that The processor is within it's "normal" operating range.  Temps vary between 40-60 degrees depending on the weather and the placement of the laptop.  

As for your lid, you have to set it under "power management" in your settings menu.  Becarefull though.  My suspend and hibernate didn't work in Edgy but works great in Fiesty.  Many other people have varried results.

---


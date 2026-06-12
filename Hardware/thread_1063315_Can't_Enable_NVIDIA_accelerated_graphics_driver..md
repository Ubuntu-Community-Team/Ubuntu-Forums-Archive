---
title: "Can't Enable NVIDIA accelerated graphics driver."
date: 2009-02-07
forum: Hardware
---

### Post by kylepotts on 2009-02-07
Hi there guys. Small problem here. I can't enable the NVIDIA accelerated graphics driver. I go to System > Admin > Hardware Drivers.

It gives me two options the version 173 or 177. 177 being recommended. I click on activate on 177. And it asks for my password. I enter it and then it downloads for a quick second then disappears. I tried restarting and no avail.

Any help?

---

### Post by taurus on 2009-02-07
What kind of nvidia graphic card do you have?

Applications -> Accessories -> Terminal
```
lspci | grep VGA
```

---

### Post by kylepotts on 2009-02-07
> **taurus said:**
> What kind of nvidia graphic card do you have?

Applications -> Accessories -> Terminal
```
lspci | grep VGA
```

I have a

```
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7100 / nForce 620i (rev a2)
```

---

### Post by taurus on 2009-02-07
Click System -> Administration -> Synaptic Package Manager -> Search and type in **nvidia** and see if nvidia-glx-177 is installed.

---

### Post by kylepotts on 2009-02-07
Yes it s installed.

---

### Post by kylepotts on 2009-02-07
Anyone any help?

---

### Post by taurus on 2009-02-07
What's the output of this command from a terminal?

```
lsmod
```

---

### Post by zero244 on 2009-02-07
I installed Fusion-Icon from synaptic.
Start it and right click on the icon and select compiz and emerald if you have it installed.
You dont need to enable the driver if its installed.
You just need to crank up compiz and fusion-icon is a good way to do that.
You can run Fusion-icon from sessions startup every time you boot.

---

### Post by kylepotts on 2009-02-08
```
 Module                  Size  Used by
ipv6                  263972  14 
aes_i586               15744  1 
aes_generic            35880  1 aes_i586
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
acpi_cpufreq           15500  1 
cpufreq_conservative    14600  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  1 
freq_table             12672  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
sbs                    19464  0 
wmi                    14504  0 
sbshc                  13440  1 sbs
video                  25232  0 
output                 11008  1 video
pci_slot               12680  0 
container              11520  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
snd_usb_audio          89728  1 
snd_usb_lib            24192  1 snd_usb_audio
arc4                    9984  2 
snd_hwdep              15236  1 snd_usb_audio
snd_seq_dummy          10884  0 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_hda_intel         384176  3 
snd_rawmidi            29824  2 snd_usb_lib,snd_seq_midi
rt73usb                30464  0 
uvcvideo               63624  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
serio_raw              13444  0 
crc_itu_t              10112  1 rt73usb
rt2x00usb              18816  1 rt73usb
rt2x00lib              36224  2 rt73usb,rt2x00usb
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
compat_ioctl32          9344  1 uvcvideo
psmouse                45200  0 
snd_pcm                83204  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
rfkill                 17176  1 rt2x00lib
videodev               41344  1 uvcvideo
snd_timer              29960  2 snd_seq,snd_pcm
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
v4l1_compat            22404  2 uvcvideo,videodev
pcspkr                 10624  0 
snd                    63268  19 snd_usb_audio,snd_hwdep,snd_seq_oss,snd_hda_intel,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_seq,snd_pcm,snd_timer,snd_seq_device
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
evdev                  17696  9 
soundcore              15328  1 snd
led_class              12164  1 rt2x00lib
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
mac80211              216820  2 rt2x00usb,rt2x00lib
cfg80211               32392  2 rt2x00lib,mac80211
button                 14224  0 
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
loop                   23180  2 
usb_storage            82752  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
sr_mod                 22212  0 
sd_mod                 42392  2 
cdrom                  43168  1 sr_mod
libusual               30356  1 usb_storage
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_amd               18692  0 
ata_generic            12932  0 
ahci                   37132  1 
pata_acpi              12160  0 
ohci1394               37936  0 
ehci_hcd               43788  0 
ohci_hcd               32016  0 
forcedeth              61328  0 
ieee1394               96324  2 sbp2,ohci1394
libata                178208  4 pata_amd,ata_generic,ahci,pata_acpi
scsi_mod              155212  6 sbp2,usb_storage,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
usbcore               149360  11 snd_usb_audio,snd_usb_lib,rt73usb,uvcvideo,rt2x00usb,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd
thermal                23708  0 
processor              42156  2 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  5 

```

---

### Post by taurus on 2009-02-08
Is that an onboard graphic card or an add-on one?

---

### Post by kylepotts on 2009-02-08
It is a on-board chipset. I am also having trouble setting my resolution. It is 1440X900. I tried editing the xorg.cong and it didnt work. I tried setting compiz up. It just freezes up. See picture for details

[IMG]http://i160.photobucket.com/albums/t182/punkkid219/Screenshot-UntitledWindow.png[/IMG]

---

### Post by kunde on 2009-02-24
same problem

---

### Post by Kaiser928 on 2009-02-24
> **kylepotts said:**
> It is a on-board chipset. I am also having trouble setting my resolution. It is 1440X900. I tried editing the xorg.cong and it didnt work. I tried setting compiz up. It just freezes up. See picture for details

[IMG]http://i160.photobucket.com/albums/t182/punkkid219/Screenshot-UntitledWindow.png[/IMG]


I read here 

[http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html](http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html)

that that is a minor bug and that if you simply wait for 5 or so minutes it will complete the download. I'm not sure though.

It says afterward that:

"After that, just check under System -> Administration for a new menu entry “NVIDIA Settings”, if so, the driver is installed. If you select the menu item, it will say “Looks like NVIDIA driver is not being used, Update your Xorg.conf file, just run “nvidia-xconfig” from terminal as root”.

Do that, and it will update your xorg.conf file, just restart X, using CTRL + ALT + BACKSPACE, it will logout you out and ask for login again. Just login and you have NVIDIA 3D fully working."


I am having the same problem however, being unable to get the drivers for my nvidia graphics card to work.

My processor is an

AMD Atholon(tm) 64 X2 Dual Core Processor 5600+ 2.80 GHz
3.00 GB of RAM

My Card is an nvidia 8600

I've followed all the other instructions but whenever I restart I still get the following error:

(EE)NVIDIA(0): Failed to initialize the NVIDIA Graphics device PCI:2:0:0.



I'm at a complete loss at what to do.

---

### Post by the-penguin on 2010-01-26
i have the same problem, only when i configure the xorg file and restart the computer i get all the way to the log in window and after input-ing my information and loggin in the screen will go black and read "input not supported"
I did solve this by un-installing the driver and reconfiguring the  Xorg file but i still dont have a 3d graphic accelerator. 
:S 
any comments?
the-penguin

---


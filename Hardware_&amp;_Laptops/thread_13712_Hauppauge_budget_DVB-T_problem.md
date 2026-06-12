---
title: "Hauppauge budget DVB-T problem"
date: 2005-02-02
forum: Hardware &amp; Laptops
---

### Post by Cred on 2005-02-02
I have Hauppauge budget card, known as WinTV NOVA-T
([product homepage](http://www.hauppauge.com/Pages/products/data_novatpci.html)).

I have been trying to get this thing to work with tricks that made it work under Slackware but so far I have been out of luck. I have tried MythTV and tvtime, nothing works.

First of all, there is no video, video0 or dvb devices under /dev so the device isn't created for some reason. I though that maybe wrong modules are loaded or something but as you can see from the list below, everything seems to be loaded. So, if you have any idea what would be wrong or missing please tell me.

lsmod output:
Module                  Size  Used by
proc_intf               3972  0
cpufreq_powersave       1728  0
cpufreq_userspace       4444  0
cpufreq_ondemand        6236  0
freq_table              4100  0
video                  16068  0
battery                10052  0
container               4416  0
button                  6544  0
pcc_acpi               11072  0
sony_acpi               6024  0
ac                      4740  0
ipv6                  258944  18
af_packet              22280  2
budget_ci              13632  0
tda1004x               14532  1 budget_ci
firmware_class         10240  1 budget_ci
budget_core             9540  1 budget_ci
dvb_core               82920  2 budget_ci,budget_core
saa7146                18724  2 budget_ci,budget_core
ttpci_eeprom            2688  1 budget_core
stv0299                10244  1 budget_ci
8139too                26048  0
8139cp                 20480  0
mii                     4992  2 8139too,8139cp
emu10k1_gp              3712  0
gameport                4544  1 emu10k1_gp
snd_emu10k1            98116  2
snd_rawmidi            24928  1 snd_emu10k1
snd_seq_device          8524  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         74208  1 snd_emu10k1
snd_pcm_oss            52516  1
snd_mixer_oss          19776  1 snd_pcm_oss
snd_pcm                94920  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              25156  1 snd_pcm
snd_page_alloc          9796  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  1 snd_emu10k1
snd_hwdep               9476  1 snd_emu10k1
snd                    55268  11 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97 _codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore              10080  2 snd
tsdev                   7616  0
usbhid                 32192  0
shpchp                 99300  0
pci_hotplug            33584  1 shpchp
forcedeth              17408  0
ehci_hcd               32772  0
ohci_hcd               21576  0
usbcore               119224  4 usbhid,ehci_hcd,ohci_hcd
i2c_nforce2             6464  0
i2c_core               22416  6 budget_ci,tda1004x,budget_core,ttpci_eeprom,stv0 299,i2c_nforce2
nvidia_agp              7708  1
agpgart                33704  2 nvidia_agp
floppy                 59152  0
pcspkr                  3560  0
rtc                    12536  0
nls_iso8859_1           4032  4
ntfs                  111536  4
evdev                   9408  0
md                     47376  0
dm_mod                 59708  1
capability              4744  0
commoncap               7808  1 capability
fglrx                 237312  7
parport_pc             37444  1
lp                     11240  0
parport                36872  2 parport_pc,lp
ide_cd                 41924  0
cdrom                  40476  1 ide_cd
mousedev               11352  1
psmouse                21384  0
reiserfs              264464  1
ext2                   67144  0
ext3                  137352  0
jbd                    60568  1 ext3
mbcache                 8452  2 ext2,ext3
ide_generic             1408  0
ide_disk               20480  8
amd74xx                14044  1
ide_core              129548  4 ide_cd,ide_generic,ide_disk,amd74xx
unix                   28532  768
thermal                13384  0
processor              22196  1 thermal
fan                     4484  0
fbcon                  38016  0
crc32                   4224  4 dvb_core,8139too,8139cp,fbcon
font                    8256  1 fbcon
bitblit                 5568  1 fbcon
vesafb                  6820  0
cfbcopyarea             3904  1 vesafb
cfbimgblt               3008  1 vesafb
cfbfillrect             3584  1 vesafb

lspci output (removed useless lines):
0000:01:0a.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)

---

### Post by WillCooke on 2005-02-16
Did you make any progress on this?

Cheers,
Will

---

### Post by kobeyu on 2005-02-17
This sounds similar to my problem. Have you looked through the logs and dmesg for something like "Firmware (xxxxxx.fw) unavailable"?

---

### Post by WillCooke on 2005-02-17
My card arrived this morning, and I know for a fact that it is supported (I've spoken to the chap that wrote the drivers!).

I've got a feeling a kernel re-compile is going to be needed as some patches need to be applied to the source.

The firmware issue I know a little about.  The logic on these Conexant chips is all done in firmware rather than being hard-wired.  (They're more like little computers than just a chip).  So, they need instuctions loading on to them, which is the firmware.  (I'm sure most of you know this already!).

The firmware needs to be uploaded to the card via hotplug.  The firmware is found on the windows driver CD that comes with the card, or possibily a newer version can be downloaded from the web.  I can't remember off the top of my head what the file name is.


Anyway, I will write a "HowTo" once I've got it working. I will also ask if some of the patches can be be applied to the kernel Ubuntu is going to be using for Hoary.  If they give it the OK (I don't know what the impact to other TV cards would be) then the card should become plug-and-play (minus the firmware issue!).

-W

---

### Post by WillCooke on 2005-02-20
Success!

It's taken me two solid days, but it's working!

I've written down everything, so a how-to should be ready by the end of the day.

---

### Post by Leebobs on 2005-02-20
Thats good news... hopefully I can use this to work out how to get my Nebula Electronics card working in Linux

---

### Post by WillCooke on 2005-02-24
[QUOTE=WillCooke]Success!

It's taken me two solid days, but it's working!

I've written down everything, so a how-to should be ready by the end of the day.[/QUOTE]
 OK, a little later than planned, but here it is.........


[https://www.ubuntulinux.org/wiki/NovaTHowTo](https://www.ubuntulinux.org/wiki/NovaTHowTo)

Please make use of the Wiki and correct any bits I've got wrong.

---


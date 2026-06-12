---
title: "What wireless drivers am I using?"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by sickfreq on 2006-11-25
Hello, I am trying to configure kismet running on my Thinkpad t42p laptop.  I have installed Ubuntu 6.10 and everything JUST WORKS, which is sweet, however, I have no idea what wireless driver I am using for the kismet.conf file setup.  

source=sourcetype,interface,name[,initialchannel]

I need to have the sourcetype properly identified.  When I had wireless working on FC4, I used ipw2200, but I am not sure that is what I am using.  Here is the output from my lspci:

02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
Subsystem: Unknown device 17ab:8331
Flags: bus master, medium devsel, latency 168, IRQ 11
Memory at c0210000 (32-bit, non-prefetchable) [size=64K]
Capabilities: [44] Power Management version 2

I have tried using "atheros", "ipw2200", "madwifi", etc.
I have also tried to examine the output of dmesg to determine what driver I am using:

dmesg |grep ath |less

[17179586.728000] ath_hal: module license 'Proprietary' taints kernel.
[17179586.728000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179586.760000] ath_rate_sample: 1.2 (0.9.2)
[17179586.764000] ath_pci: 0.9.4.5 (0.9.2)
[17179622.884000] ath0: no IPv6 routers present
[17179822.636000] ath_pci: driver unloaded

using ar5210 also does not work.  Can someone who knows more about linux than me point me to the driver I am using to use wireless.  Yes, wireless does work on my computer, I just have no idea what driver is being utilized!

Thanks,
Sick

---

### Post by taurus on 2006-11-25
Maybe you can see it from this list!

```
lsmod
```

---

### Post by sickfreq on 2006-11-25
Right!  Here is the output from the lsmod command.  The only ones that look promising is the ath_pci ath_* stuff, and wlan but are those drivers?  Specifically, can any of those be used to configure kismet?

Thanks,
Sick

Module                  Size  Used by
battery                11652  0 
ac                      6788  0 
ibm_acpi               28672  0 
thermal                15624  0 
fan                     6020  0 
button                  7952  0 
e1000                 128452  0 
ath_pci               100000  0 
ath_rate_sample        16512  1 ath_pci
ath_hal               192976  3 ath_pci,ath_rate_sample
isofs                  38076  0 
udf                    89348  0 
iptable_filter          4224  0 
ip_tables              15204  1 iptable_filter
x_tables               16132  1 ip_tables
nls_utf8                3200  0 
nls_cp437               6912  0 
vfat                   14720  0 
fat                    56348  1 vfat
sg                     37404  0 
sd_mod                 22656  0 
usb_storage            75072  0 
scsi_mod              144648  3 sg,sd_mod,usb_storage
libusual               17040  1 usb_storage
ipv6                  272288  8 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
nvram                  10376  1 
uinput                 10368  1 
radeon                118816  2 
drm                    74644  3 radeon
speedstep_centrino      9760  1 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  1 i2c_ec
hotkey                 11556  0 
dock                    8716  0 
dev_acpi               12292  0 
container               5632  0 
asus_acpi              17688  0 
af_packet              24584  4 
wlan_wep                8064  1 
lp                     12964  0 
wlan_scan_sta          15744  1 
pcmcia                 40380  0 
tsdev                   9152  0 
wlan                  207580  5 ath_pci,ath_rate_sample,wlan_wep,wlan_scan_sta
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
yenta_socket           28812  2 
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
psmouse                41352  0 
irtty_sir              10112  0 
sir_dev                18308  1 irtty_sir
pcspkr                  4352  0 
intel_agp              26012  1 
agpgart                34888  2 drm,intel_agp
serio_raw               8452  0 
parport_pc             37796  1 
evdev                  11392  2 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
parport                39496  2 lp,parport_pc
floppy                 63044  0 
irda                  214332  2 irtty_sir,sir_dev
crc_ccitt               3200  1 irda
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  5 usb_storage,libusual,ehci_hcd,uhci_hcd
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
ide_disk               18560  3 
piix                   11780  1 
generic                 5764  0 
processor              31560  2 thermal,speedstep_centrino
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

---

### Post by hagan on 2006-12-02
You are running a card with an Atheros chipset. The madwifi drivers are the one for you to go. Your sources line should look something like:

Sources=madwifi_ag,wifi0,madwifi

Hagan

---

### Post by sickfreq on 2006-12-03
Hagan, you are a true scholar.  Thanks for the help!

How did you know those were the drivers I was using?

Sick

---


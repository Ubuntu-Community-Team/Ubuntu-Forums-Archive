---
title: "I'm completely confused... T23, WLAN, ACPI"
date: 2006-06-11
forum: Hardware &amp; Laptops
---

### Post by jarrad on 2006-06-11
Hello,

I've several problems with Ubuntu on my Thinkpad T23.

First problem, WLAN does not work with my internal card (minipci?). It has an Intersil Prism 2.5 chipset. Sometimes I can discover networks but I was never able to connect successfully (WPA or WEP). I installed wpa_supplicant and the linux-wlan-ng drivers but I don't know how to use them.

There are lots of modules loaded, for example hostap *and* orinoco. Is that correct? I think they could maybe jamm each other. Additional info: my wlan-router/access point is a Netgear MR814v3.

There are also 3 different ACPI modules loaded... thats my second problem. Suspend and Hibernate does not work too. The computer shuts down but when I try to use it again the display keeps dark.

Can you please help me? I don't know how the system starting process works so I don't know where to tell ubuntu which modules to load when booting... If possible explain it for idiots because I'm new with this (and I'm German so english is not always easy to understand for me).

Here is some additinal info from lspci and lsmod:

0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04) 
0000:00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42) 
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02) 
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02) 
0000:00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02) 
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02) 
0000:00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02) 
0000:01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05) 
0000:02:00.0 CardBus bridge: Texas Instruments PCI1420 
0000:02:00.1 CardBus bridge: Texas Instruments PCI1420 
0000:02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01) 
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42) 

Module Size Used by 
binfmt_misc 12296 1 
rfcomm 40216 0 
l2cap 26244 5 rfcomm 
bluetooth 49892 4 rfcomm,l2cap 
nvram 9224 1 
uinput 9088 1 
ppdev 9220 0 
savage 35584 1 
drm 73236 2 savage 
speedstep_ich 5260 0 
speedstep_lib 4484 1 speedstep_ich 
cpufreq_userspace 4696 1 
cpufreq_stats 5636 0 
freq_table 4740 2 speedstep_ich,cpufreq_stats 
cpufreq_powersave 1920 0 
cpufreq_ondemand 6428 0 
cpufreq_conservative 7332 0 
video 16260 0 
tc1100_wmi 6916 0 
sony_acpi 5644 0 
pcc_acpi 12416 0 
ibm_acpi 26112 0 
hotkey 11556 0 
dev_acpi 11140 0 
container 4608 0 
button 6672 0 
acpi_sbs 19980 0 
battery 9988 1 acpi_sbs 
ac 5252 1 acpi_sbs 
i2c_acpi_ec 5120 1 acpi_sbs 
i2c_core 21904 1 i2c_acpi_ec 
ipv6 265600 8 
dm_mod 58936 1 
md_mod 72532 0 
af_packet 22920 8 
lp 11844 0 
hostap_pci 56848 0 
hostap 119428 1 hostap_pci 
pcmcia 40508 0 
ieee80211_crypt 6272 1 hostap 
irtty_sir 8576 0 
sir_dev 19500 1 irtty_sir 
nsc_ircc 23488 0 
irda 186940 3 irtty_sir,sir_dev,nsc_ircc 
orinoco_pci 7168 0 
orinoco 43156 1 orinoco_pci 
hermes 7808 2 orinoco_pci,orinoco 
e100 40580 0 
mii 5888 1 e100 
floppy 62148 0 
yenta_socket 28428 2 
rsrc_nonstatic 13440 1 yenta_socket 
pcmcia_core 42640 3 pcmcia,yenta_socket,rsrc_nonstatic 
parport_pc 35780 1 
parport 36296 3 ppdev,lp,parport_pc 
crc_ccitt 2304 1 irda 
tsdev 8000 0 
pcspkr 2180 0 
rtc 13492 0 
psmouse 36228 0 
serio_raw 7300 0 
snd_intel8x0 33692 1 
snd_ac97_codec 92704 1 snd_intel8x0 
snd_ac97_bus 2304 1 snd_ac97_codec 
snd_pcm_oss 53664 0 
snd_mixer_oss 18688 1 snd_pcm_oss 
snd_pcm 89864 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss 
snd_timer 25220 1 snd_pcm 
snd 55268 8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer 
soundcore 10208 1 snd 
snd_page_alloc 10632 2 snd_intel8x0,snd_pcm 
hw_random 5652 0 
intel_agp 22940 1 
agpgart 34888 2 drm,intel_agp 
shpchp 45632 0 
pci_hotplug 29236 1 shpchp 
evdev 9856 2 
ext3 135688 2 
jbd 58772 1 ext3 
ide_generic 1536 0 
uhci_hcd 33680 0 
usbcore 129668 2 uhci_hcd 
ide_cd 33028 0 
cdrom 38560 1 ide_cd 
ide_disk 17664 4 
piix 11012 1 
generic 5124 0 
thermal 13576 0 
processor 23360 1 thermal 
fan 4868 0 
capability 5000 0 
commoncap 7296 1 capability 
vesafb 8476 1 
fbcon 42784 72 
tileblit 2816 1 fbcon 
font 8320 1 fbcon 
bitblit 6272 1 fbcon 
softcursor 2304 1 bitblit 

Looks like a lot of modules for this little hardware for me.

Thank you.

With kind regards

jarrad

---


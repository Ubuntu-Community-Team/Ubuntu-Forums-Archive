---
title: "Freezes during wireless usage"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by Donnieb on 2007-03-29
I'm having a problem with the wireless and my laptop, a Lenovo 3000 N100 when the wireless is being used, as in sending and receiving packets. The computer locks up briefly. 

Relevent  information 



1.7 GHZ core 2 duo
Intel Laptop pci express pro wireless

If any additional information is needed I will be happy to provide.

---

### Post by azemute on 2007-03-29
Could you perhaps post...

your kernel version ( uname -a )
what wireless chipset you're using ( sudo lshw -C network )
and maybe the output of your loaded-modules listing (lsmod)

Sounds like it may be a driver issue... but it could be a variety of things... something else that might be useful would be the output of running "tail -20 /var/log/syslog" immediatly after it locks up on you.

---

### Post by Donnieb on 2007-03-29
I was browsing the support a little and I've found out its not a display/graphics card issue,,, because output messes up and I had the terminal display a list of text and it does freeze that also. 

The output requested below.

uname -a
Linux lappyt2535 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

sudo lshw -C network
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:44:8d:59
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.1.0mp firmware=13.0 1:0 () ip=192.168.1.119 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:d0000000-d0000fff irq:145
  *-usb
       description: Bluetooth wireless interface
       product: Foxconn Bluetooth 2.0 plus EDR
       vendor: Broadcom Corp
       physical id: 2
       bus info: usb@2:2
       version: 1.00
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@05:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:d2:2c:b0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=half link=no multicast=yes port=MII speed=10MB/s
       resources: ioport:2000-20ff iomemory:d0100000-d01000ff irq:169

lsmod

Module                  Size  Used by
ipv6                  272288  10
nls_utf8                3200  1
nls_cp437               6912  1
vfat                   14720  1
fat                    56348  1 vfat
rfcomm                 42260  6
l2cap                  27136  5 rfcomm
i915                   21632  2
drm                    74644  3 i915
cpufreq_userspace       5408  0
cpufreq_stats           7744  0
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0
cpufreq_ondemand        8876  0
cpufreq_conservative     8712  0
af_packet              24584  6
sbp2                   24584  0
parport_pc             37796  0
lp                     12964  0
parport                39496  2 parport_pc,lp
8139cp                 24832  0
pcmcia                 40380  0
joydev                 11200  0
tsdev                   9152  0
hci_usb                18068  6
bluetooth              53476  15 rfcomm,l2cap,hci_usb
sg                     37404  0
ipw3945               124576  1
8139too                29056  0
ieee80211              35272  1 ipw3945
ieee80211_crypt         7552  1 ieee80211
mii                     6912  2 8139cp,8139too
sdhci                  20108  0
mmc_core               32392  1 sdhci
yenta_socket           28812  1
rsrc_nonstatic         15360  1 yenta_socket
pcmcia_core            43924  3 pcmcia,yenta_socket,rsrc_nonstatic
evdev                  11392  2
serio_raw               8452  0
psmouse                41352  0
snd_hda_intel          20116  1
snd_hda_codec         164608  1 snd_hda_intel
snd_pcm_oss            47360  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
pcspkr                  4352  0
snd_timer              25348  1 snd_pcm
intel_agp              26012  1
agpgart                34888  3 drm,intel_agp
snd                    58372  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
hw_random               7320  0
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
shpchp                 42144  0
pci_hotplug            32828  1 shpchp
ext3                  142728  1
jbd                    62228  1 ext3
usbhid                 45152  0
usb_storage            75072  1
libusual               17040  1 usb_storage
ohci1394               37040  0
ieee1394              306104  2 sbp2,ohci1394
uhci_hcd               24968  0
ehci_hcd               34696  0
usbcore               134912  7 hci_usb,usbhid,usb_storage,libusual,uhci_hcd,ehci_hcd
ide_generic             2432  0
sr_mod                 18212  0
cdrom                  38944  1 sr_mod
sd_mod                 22656  5
generic                 5764  0
ata_piix               11780  2
libata                 74892  1 ata_piix
scsi_mod              144648  6 sbp2,sg,usb_storage,sr_mod,sd_mod,libata
processor              31560  0
fbcon                  41504  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability


tail -20 /var/log/syslog

Mar 29 13:38:39 lappyt2535 kernel: [17182447.256000] ipw3945: Microcode SW error
 detected.  Restarting.
Mar 29 13:38:39 lappyt2535 kernel: [17182447.256000] ipw3945: Error Reply type 0
x000000FF cmd LEDS_CMD (0x48) seq 0x0409 ser 0x00030000
Mar 29 13:38:39 lappyt2535 kernel: [17182447.256000] ipw3945: Can't stop Rx DMA.
Mar 29 13:38:39 lappyt2535 kernel: [17182448.624000] ipw3945: Detected geography
 ABG (11 802.11bg channels, 13 802.11a channels)
Mar 29 13:38:40 lappyt2535 kernel: [17182449.012000] ipw3945: Microcode SW error
 detected.  Restarting.
Mar 29 13:38:40 lappyt2535 kernel: [17182449.012000] ipw3945: Error Reply type 0
x000000FF cmd TX (0x1C) seq 0x0000 ser 0x00030000
Mar 29 13:38:41 lappyt2535 kernel: [17182449.012000] ipw3945: Can't stop Rx DMA.
Mar 29 13:38:41 lappyt2535 kernel: [17182450.380000] ipw3945: Detected geography                                                                                                    ABG (11 802.11bg channels, 13 802.11a channels)
Mar 29 13:38:42 lappyt2535 kernel: [17182450.704000] ipw3945: Microcode SW error                                                                                                    detected.  Restarting.
Mar 29 13:38:42 lappyt2535 kernel: [17182450.704000] ipw3945: Error Reply type 0                                                                                                   x000000FF cmd TX (0x1C) seq 0x0000 ser 0x00030000
Mar 29 13:38:42 lappyt2535 kernel: [17182450.704000] ipw3945: Can't stop Rx DMA.
Mar 29 13:38:43 lappyt2535 kernel: [17182452.072000] ipw3945: Detected geography                                                                                                    ABG (11 802.11bg channels, 13 802.11a channels)
Mar 29 13:38:43 lappyt2535 kernel: [17182452.404000] ipw3945: Microcode SW error                                                                                                    detected.  Restarting.
Mar 29 13:38:43 lappyt2535 kernel: [17182452.404000] ipw3945: Error Reply type 0                                                                                                   x000000FF cmd TX (0x1C) seq 0x0000 ser 0x00030000
Mar 29 13:38:44 lappyt2535 kernel: [17182452.404000] ipw3945: Can't stop Rx DMA.
Mar 29 13:38:44 lappyt2535 kernel: [17182453.772000] ipw3945: Detected geography                                                                                                    ABG (11 802.11bg channels, 13 802.11a channels)
Mar 29 13:38:46 lappyt2535 kernel: [17182454.224000] ipw3945: Microcode SW error                                                                                                    detected.  Restarting.
Mar 29 13:38:46 lappyt2535 kernel: [17182454.224000] ipw3945: Error Reply type 0                                                                                                   x000000FF cmd TX (0x1C) seq 0x0000 ser 0x00030000
Mar 29 13:38:46 lappyt2535 kernel: [17182454.224000] ipw3945: Can't stop Rx DMA.
Mar 29 13:38:46 lappyt2535 kernel: [17182455.592000] ipw3945: Detected geography                                                                                                    ABG (11 802.11bg channels, 13 802.11a channels)

---

### Post by azemute on 2007-03-29
> I was browsing the support a little and I've found out its not a display/graphics card issue,,, because output messes up and I had the terminal display a list of text and it does freeze that also. 

Well, this is infact a known set of bugs for the ipw3945 chipset from intel [for this specific driver, at least]

> 
Mar 29 13:38:46 lappyt2535 kernel: [17182454.224000] ipw3945: Can't stop Rx DMA.
Mar 29 13:38:46 lappyt2535 kernel: [17182455.592000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)


With a quick bit of google searching, I found some bug reports, and a couple "fixes"... I won't specifically suggest anything of yet, as I can't personally test it to verify if it'll work [and what issues you might encounter] though, if you want to attempt a fix, that is a good place to start. 

Google tells you of a bunch of bug-reports... mostly unsolved.
[http://www.google.ca/search?hl=en&q=ipw3945%3A+Microcode+SW+error+detected.+Restarting.&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=ipw3945%3A+Microcode+SW+error+detected.+Restarting.&btnG=Google+Search&meta=)

A ucode solution was proposed here:
[http://bughost.org/bugzilla/show_bug.cgi?id=1085#c39](http://bughost.org/bugzilla/show_bug.cgi?id=1085#c39)

but for the love of god, be careful :) It's fun to play with hardware, but you can break your kernel/modules fairly easily. It would likely require you to build your own kernel, to boot. 

It seems the problem stems from the following:

> 
> Common threads seem to be Core Duo and SMP kernels.

Thanks for the information. I have only used the ipw3945 driver with an SMP
kernel, so don't know if the problem exists in a non-smp kernel. However, the
ndiswrapper+windows driver seems to work fine with the smp kernel. 


but again, this is just a quick formative overview of the problem.

So, your options are: unload the ipw3945 driver and use NDIS wrapper [there are tutorials about here, somewhere....]
or if you can bear it, I'd wait for the bug to get fixed, and the new code to get merged back into the default kernel. With the upgrade to feisty, you may see the problem go away [though it could return again, if it was indeed SMP related and hasn't been formally fixed yet.]

NDIS provides a temporary solution [possibly permanent], I however don't like binary drivers but they tend to be a fact of life these days.

Good luck... if I find anything else, or a better solution... I'll post it. Or... perhaps someone else here knows a better solution.

---

### Post by Donnieb on 2007-03-30
I got the microcode and it appears to be working perfectly, thank you for your time and effort.

---


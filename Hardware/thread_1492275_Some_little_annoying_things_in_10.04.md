---
title: "Some little annoying things in 10.04"
date: 2010-05-24
forum: Hardware
---

### Post by obalix on 2010-05-24
Hey everyone!

I have 10.04 ubuntu on a Toshiba L40-14F notebook. I have 2 small problems, I hope someone can help me :)

1. After boot my screen brightness is low. It doesn't matter if the power is plugged in or not, I have to press FN+F7 (that is "brightness up" on my laptop) to get my maximum brightness. My notebook is always on the charger, and I want to start the system with full brightness, I do not want to press the hotkey every time I boot.

2. My second problem is very random. Not every time, but sometimes my wireless adapter is disabled after startup. Sometimes it is working good, and after login the wifi is enabled (as it should be) and it connects to the wifi network. But there are cases when its just disabled. I have to press the hotkey on the laptop to enable the wifi adapter. It's very annoying. BTW, the wlan adapter is REALTEK RTL8187B. Its an usb based internal wifi chip.

Do you have any idea what's going on? :)
Thank you for your help in advance!

p.s.: sorry for my english :) i hope its not that bad, and you understand it :)

---

### Post by obalix on 2010-05-25
up? :)

---

### Post by obalix on 2010-05-26
anyone? :confused:

---

### Post by obalix on 2010-05-30
bump :(

---

### Post by aphirst on 2010-05-30
1. In System > Preferences > Power Management, have a look in the "On Mains Power" tab. There should be an option called "Set display brightness to:". Move the slider to the far right. That should force Ubuntu to set the brightness to maximum on boot-up.

2. That's a bit bonkers. I'm not particularly familiar with the chip-set, so I don't know anything specific. Just a thought; what's your Wi-Fi enable hot-key? Is it possible that you could be accidentally disabling the Wi-Fi when you are manually increasing the screen brightness?

Hope I could help. :)

~ Adam

---

### Post by obalix on 2010-05-30
Hey Adam!

Thank you for your reply!

1. Yep, I already did this, but it did not help. I adjusted the settings, I saved it, entered the password, and done. No error message, so I think the config file saved successfully. Maybe a manual edit on the config file should do the thing, but I don't know what file is this and where it is.

2. The brightness and wifi hotkeys are indeed next to each other, but I am 100% sure, that I didn't disable the wifi accidentally :) I am using my laptop, browsing the web...etc. And I power off when I'm done. On the other day, I power on, booting, and the wifi is disabled :) But its very odd, 'cause its not disabled all the time. I don't understand :)

---

### Post by Julita on 2010-05-30
Your
```
lspci
```
please. Your video card, specifically. Also 
```
lsmod
``` to see which drivers are used by your system. As to your second problem, I am sure there must be a script to switch on Wifi card after every boot.

In 10.04, my card is also disabled, and I have to as a root
```
ifconfig wlan0 up
``` every time I boot, thank God, the most often interval is once a week, so it doesn't bother me, really :)

---

### Post by obalix on 2010-05-30
lspci (vga part):

```
oba@toshiba:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
```

it's an intel gma965 also known as intel gma x3100

lsmod

```
oba@toshiba:~$ lsmod
Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
joydev                  8708  0 
ipt_REJECT              1928  1 
ipt_LOG                 4542  5 
xt_multiport            2378  2 
xt_limit                1382  7 
xt_tcpudp               2011  14 
ipt_addrtype            1631  4 
xt_state                1098  7 
ip6table_filter         2343  1 
ip6_tables             11227  1 ip6table_filter
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
snd_hda_intel          21877  2 
nf_nat                 15735  2 nf_nat_irc,nf_nat_ftp
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
nf_conntrack_ipv4      10672  9 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
nf_conntrack_ftp        5381  1 nf_nat_ftp
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nf_conntrack           61583  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_timer              19098  2 snd_pcm,snd_seq
iptable_filter          2271  1 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  3 
rtl8187                50680  0 
drm_kms_helper         29297  1 i915
ip_tables               9991  1 iptable_filter
x_tables               14299  9 ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
mac80211              204922  1 rtl8187
drm                   162471  4 i915,drm_kms_helper
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
asus_laptop            17008  0 
i2c_algo_bit            5028  1 i915
led_class               2864  2 rtl8187,asus_laptop
cfg80211              126485  2 rtl8187,mac80211
eeprom_93cx6            1333  1 rtl8187
soundcore               6620  1 snd
intel_agp              24177  2 i915
lp                      7028  0 
psmouse                63245  0 
serio_raw               3978  0 
agpgart                31724  2 drm,intel_agp
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
parport                32635  2 ppdev,lp
8139too                18545  0 
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
ahci                   32008  3 
oba@toshiba:~$
```

sry I paste all the lsmod output, I don't know what do you need :)

my wlan is not disabled at every boot :) I didn't noticed any rules or sg like that, but its disabled about 3-4 times of 10 ubuntu boot :)

---

### Post by Julita on 2010-05-30
The problem with your display seems to be in DPMS... You have to disable it by
```
xset -dpms
```

Does it help?

---

### Post by obalix on 2010-05-31
Unfortunately, no :(

---

### Post by Saghaulor on 2010-05-31
> **Julita said:**
> The problem with your display seems to be in DPMS... You have to disable it by
```
xset -dpms
```

Does it help?

I'm having issue with my brightness controls not affecting the actual brightness of the monitor.

Gave your suggestion a shot. Didn't seem to do anything.

---

### Post by martintang on 2010-06-01
try adding a line to /etc/rc.local
echo "5">/sys/class/backlight/acpi_video0/brightness

and restart

---

### Post by martintang on 2010-06-01
> **aphirst said:**
> 1. In System > Preferences > Power Management, have a look in the "On Mains Power" tab. There should be an option called "Set display brightness to:". Move the slider to the far right. That should force Ubuntu to set the brightness to maximum on boot-up.


The problem of unable to tune the brightness using the bar seems to be specific to 10.04. I picked out my old 9.10 CD and used it on the same computer. The bar can tune the brightness.

---

### Post by obalix on 2010-06-01
> **martintang said:**
> try adding a line to /etc/rc.local
echo "5">/sys/class/backlight/acpi_video0/brightness

and restart

It didn't work :( Its still the same brightness at startup. BTW thank you for your reply.

---

### Post by obalix on 2010-06-01
> **martintang said:**
> The problem of unable to tune the brightness using the bar seems to be specific to 10.04. I picked out my old 9.10 CD and used it on the same computer. The bar can tune the brightness.

Indeed. I use hungarian version of ubuntu 10.04, but I also don't see the option here. I have a brightness bar at the energy saving preferences, but that one controls the brightness when computer goes to "energy saving mode". So yeah, that doesn't affect the "main" or the "startup" brightness at all.

---

### Post by Saghaulor on 2010-06-03
> **martintang said:**
> try adding a line to /etc/rc.local
echo "5">/sys/class/backlight/acpi_video0/brightness

and restart

Thanks for that suggestion.

That definitely did something. My lcd is much dimmer, however, the keyboard toggle for brightness up and down isn't changing anything. The notifier reacts, but the overall brightness doesn't budge.

Please advise.

---

### Post by obalix on 2010-06-08
bump? :(

---

### Post by Saghaulor on 2010-06-14
bump

---

### Post by Rodney9 on 2010-06-14
I use Xubuntu 10.4 on my Toshiba Satellite L500/08P Laptop and I installed xfce4-goodies and gnome-applets, I now have a laptop brightness applet in xubuntu. 

Of course if you are using Ubuntu and Gnome the brightness applet is already there.

---

### Post by Saghaulor on 2010-06-14
> **Rodney9 said:**
> I use Xubuntu 10.4 on my Toshiba Satellite L500/08P Laptop and I installed xfce4-goodies and gnome-applets, I now have a laptop brightness applet in xubuntu. 

Of course if you are using Ubuntu and Gnome the brightness applet is already there.

Thanks for your best effort. I'm using gnome, so yeah, the applet is native. Unfortunately my problems are much more advanced than that.

Brightness applet changes, however, the actual screen brightness does nothing.

I'm running upstream kernel 2.6.34, and upstream xorg. That doesn't seem to help much either.

---

### Post by Saghaulor on 2010-06-14
This bug report is worth noting as it's my present issue.[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984")

---

### Post by obalix on 2010-06-14
my hotkeys are working, I can adjust the brightness with them, the only problem is the brightness level at startup
I want full brightness, and I didn't find a way to set it.

---

### Post by Saghaulor on 2010-06-14
> **obalix said:**
> my hotkeys are working, I can adjust the brightness with them, the only problem is the brightness level at startup
I want full brightness, and I didn't find a way to set it.

Do you mind posting the output of the following commands?:

```
uname -a
```
```
aptitude show xserver-xorg-core
```
```
aptitude show xserver-xorg-video-intel
```
```
lspci
```

---

### Post by obalix on 2010-06-15
sure... :)

```
oba@toshiba:~$ uname -a
Linux toshiba 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
oba@toshiba:~$ 

```

aptitude show xserver-xorg-core

sorry for the hungarian texts, but I use hungarian language, 'cause I am hungarian :)
some translations:

állapot: telepítve ---> state: installed
automatikusan telepítve: nem ---> automaticaly installed: no
prioritás: opcionális ---> priority: optional
függ&#337;ségek ---> dependencies

```
oba@toshiba:~$ aptitude show xserver-xorg-core
Csomag: xserver-xorg-core
Állapot: telepítve
Automatikusan telepített: nem
Verzió: 2:1.7.6-2ubuntu7
Prioritás: opcionális
Szakasz: x11
Karbantartó: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Tömörítetlen méret: 4.575k
Függ&#337;ségek: xserver-common (>= 2:1.7.6-2ubuntu7), xserver-xorg, udev (>= 149),
               libc6 (>= 2.7), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.4.2),
               libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.15.16), libudev0
               (>= 147), libxau6, libxdmcp6, libxfont1 (>= 1:1.2.9)
Ajánlott csomagok: libgl1-mesa-dri (>= 7.1~rc1)
Javasolt csomagok: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Ütközések: xserver-common (< 7), xserver-xfree86 (< 1:7.0.0), xserver-xorg (<
              6.8.2-38), xserver-xorg-input, xserver-xorg-input-2,
              xserver-xorg-input-2.1, xserver-xorg-input-4,
              xserver-xorg-input-wacom (< 0.7.8), xserver-xorg-video,
              xserver-xorg-video-1.0, xserver-xorg-video-1.9,
              xserver-xorg-video-2, xserver-xorg-video-4, xserver-xorg-video-5
Helyettesíti: xserver-common (< 7), xserver-xfree86 (< 1:7.0.0), xserver-xorg (<
               6.8.2-38)
Biztosítja: xserver
Leírás: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers. 
 
 The Xorg server supports most modern graphics hardware from most vendors, and
 supersedes all XFree86 X servers. 
 
 More information about X.Org can be found at: <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 
 
 This package is built from the X.org xserver module.

oba@toshiba:~$

```

aptitude show xserver-xorg-video-intel

```
oba@toshiba:~$ aptitude show xserver-xorg-video-intel
Csomag: xserver-xorg-video-intel
Állapot: telepítve
Automatikusan telepített: nem
Verzió: 2:2.11.0-1ubuntu1~xup
Prioritás: opcionális
Szakasz: x11
Karbantartó: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Tömörítetlen méret: 1.221k
Függ&#337;ségek: libc6 (>= 2.4), libdrm-intel1 (>= 2.4.13), libdrm2 (>= 2.4.17),
               libpciaccess0 (>= 0.8.0+git20071002), libx11-6 (>= 0),
               libx11-xcb1, libxcb-aux0 (>= 0.3.6), libxcb-dri2-0 (>= 0),
               libxcb1 (>= 0), libxext6, libxfixes3 (>= 1:4.0.1), libxv1,
               libxvmc1, xserver-xorg-core (>= 2:1.6.99.900)
Ütközések: 915resolution, xserver-xorg-driver-i810, xserver-xorg-video-i810 (<
              2:1.9.91-1), xserver-xorg-video-i810-modesetting,
              xserver-xorg-video-intel-modesetting
Helyettesíti: xserver-xorg (< 6.8.2-35), xserver-xorg-driver-i810,
               xserver-xorg-video-i810 (< 2:1.9.91-1),
               xserver-xorg-video-i810-modesetting,
               xserver-xorg-video-intel-modesetting
Biztosítja: xserver-xorg-video-6
Leírás: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides the driver for the Intel i8xx and i9xx family of
 chipsets, including i810, i815, i830, i845, i855, i865, i915, i945 and i965
 series chips. 
 
 This package also provides XvMC (XVideo Motion Compensation) drivers for
 i810/i815 and i9xx and newer chipsets. 
 
 More information about X.Org can be found at: <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 
 
 This package is built from the X.org xf86-video-intel driver module.

oba@toshiba:~$ 

```

lspci 

```
oba@toshiba:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
oba@toshiba:~$ 

```

---

### Post by Saghaulor on 2010-06-16
> **obalix said:**
> sure... :)

```
oba@toshiba:~$ uname -a
Linux toshiba 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
oba@toshiba:~$ 

```

aptitude show xserver-xorg-core

sorry for the hungarian texts, but I use hungarian language, 'cause I am hungarian :)
some translations:

állapot: telepítve ---> state: installed
automatikusan telepítve: nem ---> automaticaly installed: no
prioritás: opcionális ---> priority: optional
függ&#337;ségek ---> dependencies

```
oba@toshiba:~$ aptitude show xserver-xorg-core
Csomag: xserver-xorg-core
Állapot: telepítve
Automatikusan telepített: nem
Verzió: 2:1.7.6-2ubuntu7
Prioritás: opcionális
Szakasz: x11
Karbantartó: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Tömörítetlen méret: 4.575k
Függ&#337;ségek: xserver-common (>= 2:1.7.6-2ubuntu7), xserver-xorg, udev (>= 149),
               libc6 (>= 2.7), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.4.2),
               libpciaccess0 (>= 0.10.7), libpixman-1-0 (>= 0.15.16), libudev0
               (>= 147), libxau6, libxdmcp6, libxfont1 (>= 1:1.2.9)
Ajánlott csomagok: libgl1-mesa-dri (>= 7.1~rc1)
Javasolt csomagok: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Ütközések: xserver-common (< 7), xserver-xfree86 (< 1:7.0.0), xserver-xorg (<
              6.8.2-38), xserver-xorg-input, xserver-xorg-input-2,
              xserver-xorg-input-2.1, xserver-xorg-input-4,
              xserver-xorg-input-wacom (< 0.7.8), xserver-xorg-video,
              xserver-xorg-video-1.0, xserver-xorg-video-1.9,
              xserver-xorg-video-2, xserver-xorg-video-4, xserver-xorg-video-5
Helyettesíti: xserver-common (< 7), xserver-xfree86 (< 1:7.0.0), xserver-xorg (<
               6.8.2-38)
Biztosítja: xserver
Leírás: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers. 
 
 The Xorg server supports most modern graphics hardware from most vendors, and
 supersedes all XFree86 X servers. 
 
 More information about X.Org can be found at: <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 
 
 This package is built from the X.org xserver module.

oba@toshiba:~$

```

aptitude show xserver-xorg-video-intel

```
oba@toshiba:~$ aptitude show xserver-xorg-video-intel
Csomag: xserver-xorg-video-intel
Állapot: telepítve
Automatikusan telepített: nem
Verzió: 2:2.11.0-1ubuntu1~xup
Prioritás: opcionális
Szakasz: x11
Karbantartó: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Tömörítetlen méret: 1.221k
Függ&#337;ségek: libc6 (>= 2.4), libdrm-intel1 (>= 2.4.13), libdrm2 (>= 2.4.17),
               libpciaccess0 (>= 0.8.0+git20071002), libx11-6 (>= 0),
               libx11-xcb1, libxcb-aux0 (>= 0.3.6), libxcb-dri2-0 (>= 0),
               libxcb1 (>= 0), libxext6, libxfixes3 (>= 1:4.0.1), libxv1,
               libxvmc1, xserver-xorg-core (>= 2:1.6.99.900)
Ütközések: 915resolution, xserver-xorg-driver-i810, xserver-xorg-video-i810 (<
              2:1.9.91-1), xserver-xorg-video-i810-modesetting,
              xserver-xorg-video-intel-modesetting
Helyettesíti: xserver-xorg (< 6.8.2-35), xserver-xorg-driver-i810,
               xserver-xorg-video-i810 (< 2:1.9.91-1),
               xserver-xorg-video-i810-modesetting,
               xserver-xorg-video-intel-modesetting
Biztosítja: xserver-xorg-video-6
Leírás: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides the driver for the Intel i8xx and i9xx family of
 chipsets, including i810, i815, i830, i845, i855, i865, i915, i945 and i965
 series chips. 
 
 This package also provides XvMC (XVideo Motion Compensation) drivers for
 i810/i815 and i9xx and newer chipsets. 
 
 More information about X.Org can be found at: <URL:http://www.X.org>
 <URL:http://xorg.freedesktop.org>
 <URL:http://lists.freedesktop.org/mailman/listinfo/xorg> 
 
 This package is built from the X.org xf86-video-intel driver module.

oba@toshiba:~$ 

```

lspci 

```
oba@toshiba:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
oba@toshiba:~$ 

```

Ah, I think you're running a different graphics chipset. That's probably why your's is working.

> $ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


---

### Post by Saghaulor on 2010-06-23
Now I'm getting somewhere.

There seems to be an issue with permissions on /proc/acpi/video/GFX0/DD02/brightness

After ```
sudo su
``` and then ```
echo 50 > /proc/acpi/video/GFX0/DD02/brightness
``` my brightness level changed.

See my post here.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984/comments/27](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573984/comments/27)

---

### Post by obalix on 2010-06-24
> **Saghaulor said:**
> ```
echo 50 > /proc/acpi/video/GFX0/DD02/brightness
```

I don't have that folder :( 

In the /proc/acpi/video/ folder I have only one folder named VGA
In that VGA folder I have these files and folders

```
root@toshiba:/proc/acpi/video/VGA# ls -l
összesen 0
dr-xr-xr-x 2 root root 0 2010-06-24 13:49 CRTD
-rw-r--r-- 1 root root 0 2010-06-24 13:49 DOS
dr-xr-xr-x 2 root root 0 2010-06-24 13:49 DVID
-r--r--r-- 1 root root 0 2010-06-24 13:49 info
dr-xr-xr-x 2 root root 0 2010-06-24 13:49 LCDD
-rw-r--r-- 1 root root 0 2010-06-24 13:49 POST
-r--r--r-- 1 root root 0 2010-06-24 13:49 POST_info
-r--r--r-- 1 root root 0 2010-06-24 13:49 ROM
root@toshiba:/proc/acpi/video/VGA# 

```

In that 3 folders (CRTD, DVID, LCDD) there are 1-1 brightness file, but I'm not sure which one is the right one for the command you suggested.

---

### Post by Saghaulor on 2010-06-24
> **obalix said:**
> I don't have that folder :( 

In the /proc/acpi/video/ folder I have only one folder named VGA
In that VGA folder I have these files and folders

```
root@toshiba:/proc/acpi/video/VGA# ls -l
összesen 0
dr-xr-xr-x 2 root root 0 2010-06-24 13:49 CRTD
-rw-r--r-- 1 root root 0 2010-06-24 13:49 DOS
dr-xr-xr-x 2 root root 0 2010-06-24 13:49 DVID
-r--r--r-- 1 root root 0 2010-06-24 13:49 info
dr-xr-xr-x 2 root root 0 2010-06-24 13:49 LCDD
-rw-r--r-- 1 root root 0 2010-06-24 13:49 POST
-r--r--r-- 1 root root 0 2010-06-24 13:49 POST_info
-r--r--r-- 1 root root 0 2010-06-24 13:49 ROM
root@toshiba:/proc/acpi/video/VGA# 

```

In that 3 folders (CRTD, DVID, LCDD) there are 1-1 brightness file, but I'm not sure which one is the right one for the command you suggested.

Well, let me start by saying, if you're having a problem where the brightness applet changes, but the actual brightness doesn't change, the above solution may not even solve your problem, as I've recently discovered. 

Tony, who started the above referenced bug report on launchpad, has very similar hardware to me. Unfortunately, his hardware is sufficiently dissimilar so that the aforementioned solution is not a solution for him. Nevertheless, we can try to see if it works for you.

The from what I gather about your system, you want to do something like the following:
The below code assumes the root role, require to modify the file.
```
sudo su
```
The next code should tell you what the acceptable brightness settings are.
```
cat /proc/acpi/video/VGA/LCDD/brightness
```
Then, if it reads something like below,
> levels: 0 5 10 15 20 25 30 35 40 45 50 55 60 65 70 75 80 85 90 95 100
current: 100
you should be able to adjust the brightness using one of those listed numbers, using something like
```
echo 50 > /proc/acpi/video/VGA/LCDD/brightness
```

That's all assuming that I'm guessing the correct folder. You can try all three. If nothing happens on any of them, then unfortunately, this is not your solution friend.

If nothing happens, I'd recommend resetting the brightness level back to 100, just in case a fix is released and for whatever reason your brightness level doesn't reset on it's own. It's no fun trying to run on a black screen.

---

### Post by obalix on 2010-06-25
that's odd :)

I adjust my brightness with the hotkeys, and after I enter the command:

```
oba@toshiba:~$ sudo su
[sudo] password for oba: 
root@toshiba:/home/oba# cat /proc/acpi/video/VGA/LCDD/brightness 
levels:  30 40 50 60 70 80 90 100
current: 60
root@toshiba:/home/oba# 

```

It seems that it is the right folder and file, cause it recognizes my current brightness level.
After that, I enter the other command:

```
root@toshiba:/home/oba# echo 100 > /proc/acpi/video/VGA/LCDD/brightness
root@toshiba:/home/oba# 

```

...but nothing happens. My display is still "dark", however, my current brightness level is 100 (according to this):

```
root@toshiba:/home/oba# cat /proc/acpi/video/VGA/LCDD/brightness 
levels:  30 40 50 60 70 80 90 100
current: 100
root@toshiba:/home/oba# 

```

If I enter the command for the other 2 folders, it comes back with a "not supported" error message.

So yeah, unfortunately, this is not the solution I am looking for :(

BTW, thank you for your help and reply :)

---

### Post by Saghaulor on 2010-06-25
> **obalix said:**
> that's odd :)

I adjust my brightness with the hotkeys, and after I enter the command:

```
oba@toshiba:~$ sudo su
[sudo] password for oba: 
root@toshiba:/home/oba# cat /proc/acpi/video/VGA/LCDD/brightness 
levels:  30 40 50 60 70 80 90 100
current: 60
root@toshiba:/home/oba# 

```

It seems that it is the right folder and file, cause it recognizes my current brightness level.
After that, I enter the other command:

```
root@toshiba:/home/oba# echo 100 > /proc/acpi/video/VGA/LCDD/brightness
root@toshiba:/home/oba# 

```

...but nothing happens. My display is still "dark", however, my current brightness level is 100 (according to this):

```
root@toshiba:/home/oba# cat /proc/acpi/video/VGA/LCDD/brightness 
levels:  30 40 50 60 70 80 90 100
current: 100
root@toshiba:/home/oba# 

```

If I enter the command for the other 2 folders, it comes back with a "not supported" error message.

So yeah, unfortunately, this is not the solution I am looking for :(

BTW, thank you for your help and reply :)

Obalix, not enough caffeine. Ignore my previous reply. I'm sorry this isn't your solution. Like I said, its not working for everyone. Good luck.

---


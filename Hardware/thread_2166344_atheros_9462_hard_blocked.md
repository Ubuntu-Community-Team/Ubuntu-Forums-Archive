---
title: "atheros 9462 hard blocked"
date: 2013-08-08
forum: Hardware
---

### Post by Murdoc_of_puts on 2013-08-08
Allright, so I'm having problems. I've followed [this thread]("http://ubuntuforums.org/showthread.php?t=2035902&page=8") to the end, I've got a slightly different card- 9462 :0034 . I've been adjusting things as I go for that model, which is supported mostly in all of the drivers that I've been looking at. Given that I've a different card and a different problem I'm following advice and starting a new thread.  My problem is that I can't turn on the card. I was hoping that if I just installed the right driver magic would happen. So far though, no magic. Weird thing is that the bluetooth works just fine. Here's some tech specs.

```


_uname -r_
3.2.50

_lsmod_
Module                  Size  Used by
arc4                   12529  2 
ath9k                 149721  0 
bnep                   18176  2 
parport_pc             32688  0 
rfcomm                 46747  12 
mac80211              582504  1 ath9k
ppdev                  17030  0 
snd_hda_codec_hdmi     32114  1 
snd_hda_codec_realtek   222872  1 
snd_hda_intel          33239  3 
snd_hda_codec         117087  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17659  1 snd_hda_codec
snd_pcm                96420  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k_common           14053  1 ath9k
ath9k_hw              409068  2 ath9k,ath9k_common
snd_seq_midi           13324  0 
snd_rawmidi            30569  1 snd_seq_midi
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
cfg80211              534055  3 ath9k,mac80211,ath
btusb                  18291  0 
ath3k                  12917  0 
bluetooth             228797  25 bnep,rfcomm,btusb,ath3k
fglrx                3264017  64 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61553  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               71447  0 
joydev                 17457  0 
usbhid                 46777  0 
videodev               97843  1 uvcvideo
snd_timer              29532  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
compat                 21151  10 ath9k,bnep,rfcomm,mac80211,ath9k_common,ath9k_hw,cfg80211,btusb,ath3k,bluetooth
v4l2_compat_ioctl32    16780  1 videodev
edac_core              53353  0 
snd                    77973  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid                    99200  1 usbhid
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
sp5100_tco             13697  0 
k10temp                13119  0 
i2c_piix4              13167  0 
shpchp                 37032  0 
edac_mce_amd           23414  0 
psmouse                72903  0 
jmb38x_ms              17369  0 
mac_hid                13205  0 
serio_raw              13211  0 
memstick               16476  1 jmb38x_ms
toshiba_acpi           18195  0 
sparse_keymap          13890  1 toshiba_acpi
video                  19151  0 
lp                     17759  0 
binfmt_misc            17431  1 
parport                46354  3 parport_pc,ppdev,lp
r8169                  60930  0 
sdhci_pci              18741  0 
sdhci                  32705  1 sdhci_pci

_lshw -C network_

*-network DISABLED      
       description: Wireless interface
       product: AR9462 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: wlan2
       version: 01
       serial: b8:76:3f:78:e2:cd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.50 firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:fe800000-fe87ffff memory:fe880000-fe88ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 05
       serial: 88:ae:1d:57:b8:a4
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.132 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 ioport:b000(size=256) memory:d0204000-d0204fff memory:d0200000-d0203fff

_rfkill list_
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
      **  Hard blocked: yes**

_lspci (edited)_
0a:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)
0b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

_lspci -nn |grep 0280_
0a:00.0 Network controller [0280]: Atheros Communications Inc. AR9462 Wireless Network Adapter [168c:0034] (rev 01)

_iwconfig_
wlan2     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on


_modinfo ath9k_

filename:       /lib/modules/3.2.50/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     CDBF9312B7D43C49C80D3C2
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,compat,cfg80211
vermagic:       3.2.50 SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)

```

I'm on a toshiba a665d-so91. There's a little button to turn on the wifi, that isn't working, but will work on another wifi card no problem, so it's not that section of hardware. I would really appreciate any help that you could give me. I hate to just dump info onto here, but hopefully this will help with a solution.

---

### Post by chili555 on 2013-08-08
Please show me the result of these commands in exact order. First press the wireless button on your laptop. Disregard whether the LED glows or changes color. Run and post:```
rfkill list all
```Press the button again and run again and post:```
rfkill list all
```Any changes?

Now do:```
sudo rfkill unblock all
rfkill list all
sudo modprobe -r toshiba_acpi
sudo rfkill unblock all
rfkill list all
```Any changes now?

---

### Post by Murdoc_of_puts on 2013-08-08
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

---no change

```

root@poopzilla:/home/murdoc# sudo modprobe -r toshiba_acpi
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
root@poopzilla:/home/murdoc# sudo rfkill unblock all
root@poopzilla:/home/murdoc# rfkill list all
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: yes

```

---

### Post by chili555 on 2013-08-08
> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.Ooops! We'd better have a look and fix it:```
cat /etc/modprobe.d/blacklist
```

---

### Post by Murdoc_of_puts on 2013-08-08
OK that's weird,black list is empty.  There is a blacklist.conf, and a blacklist-ath-pci.conf file.

looking into the blacklist-ath-pci file, ath_pci is blacklisted.  But that's talking about ath5k.

```

blacklist.conf

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by chili555 on 2013-08-08
> OK that's weird,black list is empty. Let's remove it:```
sudo rm /etc/modprobe.d/blacklist
```Proofread very carefully before you press Enter. 'rm' can be a system wrecker if not used with care.

Let's try one other thing:```
sudo modprobe toshiba_acpi
sudo modprobe -r ath9k
sudo modprobe ath9k btcoex_enable=1
sudo rfkill unblock all
rfkill list all 
```I will be off for the evening and will check back tomorrow.

---

### Post by Murdoc_of_puts on 2013-08-08
Still no dice.

---

### Post by bglassmaker on 2013-08-09
I was having the same issues with my Acer being hard blocked with the same chipset. The wireless toggle on mine has multiple states with combinations of BT and Wireless on and off. I had to toggle through with my function key (Fn F3) till they were all unblocked.

---

### Post by chili555 on 2013-08-09
> **Murdoc_of_puts said:**
> Still no dice.I am just about out of options. Please carefully check in the computer's BIOS to be sure there is no option to enable and disable wireless.

I believe this is a bug in toshiba_acpi, the little module that is supposed to translate key presses to action; in your case, pressing the wireless button to enable wireless. You might look for and report a bug: [https://bugs.launchpad.net/ubuntu?field.searchtext=toshiba_acpi&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu?field.searchtext=toshiba_acpi&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

Finally, you might borrow a USB wireless from a friend or neighbor.

---

### Post by Murdoc_of_puts on 2013-08-09
I really do appreciate all that you've tried to do for me.  

I found a module...wistron_btns  that is supposed to enable all of the weird led switches.   Perhaps that will work, however, 
```

FATAL: Module wiston_btns not found.

```

is what I get when I try to modprobe it.  Would you know of a way to just download it, and force it into the kernel?

---

### Post by chili555 on 2013-08-09
> I found a module...wistron_btns that is supposed to enable all of the weird led switches. Where, pray tell? This isn't and hasn't been included in Ubuntu for some time now. Of course, you might as an experiment, burn a live CD for, say 10.04, and see if it works.

FYI: [http://ubuntuforums.org/showthread.php?t=1768816&page=2](http://ubuntuforums.org/showthread.php?t=1768816&page=2)> $ modinfo wistron_btns
filename: /lib/modules/[COLOR="#FF0000"]2.6.38-8-generic[/COLOR]/kernel/drivers/input/misc/wistron_btns.ko
version: 0.3
license: GPL v2
description: Wistron laptop button driver
author: Miloslav Trmac <mitr@volny.cz>
srcversion: AF8D9C3A27B38B6CA2BA1B1
depends: input-polldev,sparse-keymap
vermagic: 2.6.38-8-generic SMP mod_unload modversions 686
parm: force:Load even if computer is not in database (bool)
parm: keymap:Keymap name, if it can't be autodetected [generic, 1557/MS2141] (charp) In Linux years, kernel version 2.6.38 is synonymous with the stone ax.

---


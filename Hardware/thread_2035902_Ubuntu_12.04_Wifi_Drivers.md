---
title: "Ubuntu 12.04 Wifi Drivers"
date: 2012-07-31
forum: Hardware
---

### Post by FrogInABoxx on 2012-07-31
I recently bought a new laptop from [Novatech]("http://novatech.co.uk/"). (the nSpire 2760 to be precise. **not the black edition**.) and I cannot find any wifi drivers for it.

I cannot determine the model number of the wifi card, all I have discovered is that it has the chipset ID '168c:0037'. From general google searching, I have discovered this being referenced as the AR9485, AR9285, AR1111 and various other model numbers. Therefore, I have no idea which model I actually have.

If anyone has any ideas on how I can get drivers for this card, or any suggestions that I could try, I am open to anything, as it would be such a shame to have to resort to Windows only due to lack of wifi drivers on linux.

If you need any more information just let me know and I will do my best to provide it.

---

### Post by ahallubuntu on 2012-07-31
Are there any "Additional Drivers" available for this laptop, including perhaps one for the Atheros AR9485 card you seem to have?  Search for "Additional Drivers" in Ubuntu and see if any are suggested.  You may have to be online to access/download them however.

Sometimes plugging the laptop in temporarily with a cable to update and get access to additional drivers can help fix these kinds of problems.

It's a shame Atheros hasn't provided good Linux support for this wireless card.  You aren't the only one with this problem:

[http://ubuntuforums.org/showthread.php?t=1983003](http://ubuntuforums.org/showthread.php?t=1983003)

---

### Post by FrogInABoxx on 2012-08-01
No, I have updated everything that I have installed and there are no additional drivers or compatibility for this card in any updates.

If it helps, 'ifconfig' does not show up wlan0 at all, and 'lshw' shows *-network UNCLAIMED which has no driver set in configuration.

I have also tried building and installing the latest version of compat-wireless, still to no avail.

---

### Post by levlaz on 2012-08-01
Open a terminal and type;
```
lspci
```


Post the output here please.

---

### Post by FrogInABoxx on 2012-08-01
> **levlaz said:**
> Open a terminal and type;
```
lspci
```


Post the output here please.

```
:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
02:00.0 Network controller: Atheros Communications Inc. Device 0037 (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)

```

---

### Post by levlaz on 2012-08-01
Try [this thread]("http:// http://ubuntuforums.org/showthread.php?t=1935049") should work for you.

---

### Post by FrogInABoxx on 2012-08-01
> **levlaz said:**
> Try [this thread]("http:// http://ubuntuforums.org/showthread.php?t=1935049") should work for you.

I tried installing the ```
linux-backports-modules-cw-3.3-precise-generic
``` package as suggested by the last post in the thread you specified, however this has had no effect.

Upon running the command 'modinfo ath9k' in a terminal, it outputs:
```
:~$ modinfo ath9k
filename:       /lib/modules/3.2.0-27-generic/updates/cw-3.3/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     21EAA32311830AA82C5169B
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
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
depends:        ath9k_hw,ath9k_common,mac80211,cfg80211,ath
vermagic:       3.2.0-27-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)

```

Which as you can see, has several aliases for the '168c' cards, but not '0037'.

---

### Post by FrogInABoxx on 2012-08-01
Quick update:

Just tried ndiswrapper. Unfortunately I could not find any supported drivers on the list, or any drivers for my device for windows xp, therefore I had to try the .sys and .inf that I got on the windows 7 driver CD with the laptop, which are the same ones being used by my windows 7 partition.

Unfortunately, this did not work. The drivers installed succesfully, and after running 'sudo ndiswrapper -l' the driver was installed correctly and had correctly associated itself with the device.

However, after this whole ndiswrapper process (followed exactly from the tutorial on [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")) upon running 'iwconfig', there was still no reference to wlan0.

Any suggestions are appreciated at this point.

---

### Post by ahallubuntu on 2012-08-01
I am very sorry to hear of your difficulties.  Wireless cards are probably the worst issue people have with Linux.  It's partly due to the way hardware makers themselves choose to support Linux.  Many wireless card makers do not directly support their wireless cards and instead work with the laptop maker to release drivers.  And usually, laptop manufacturers do not release any Linux drivers.  So you have to wait for Linux developers to develop a working driver that is released in the kernels that go into the distros like Ubuntu - or juggle some fixes like trying to install various packages.

Some hardware manufacturers have much better Linux support than others.  Intel has very good Linux support for its wireless cards - one reason I always get an Intel wireless card whenever it's possible.  Realtek also has decent support - they release Linux driver source code on their website, but you have to compile it; Realtek chipsets are found in a lot of USB wireless cards.  

I've upgraded many laptops to Intel wireless cards for that reason.  Some laptop internal wireless cards are very easy to upgrade (a few screws on a bottom panel, two or three antenna wires).  Sometimes the wireless card is buried deep inside the laptop and is a pain to get to.  Of course, it could void your warranty upgrading a wireless card if the laptop is new.  Even so, some manufacturers' hardware doesn't even allow you to install unapproved wireless cards.  HP and Lenovo "whitelist" their wireless cards to block unapproved cards.  Dell and Acer (and others) do not.  I don't know  Novatech's policy or if that is even possible for you.  I'm a hardware guy by background so swapping a wireless card is usually routine for me, not for everyone.

In your case, I'd probably keep googling for AR9485 solutions involving Linux.  I'm sure it's possible to get your card working, just a bit of a pain.

---

### Post by wildmanne39 on 2012-08-01
Hi, the driver for your card is included with ubuntu  12.04 please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by FrogInABoxx on 2012-08-02
> **wildmanne39 said:**
> Hi, the driver for your card is included with ubuntu  12.04 please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

The result of this is:

```
kai@Kai-Lapbuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux Kai-Lapbuntu 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
kai@Kai-Lapbuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0037] (rev 01)
	Subsystem: AzureWave Device [1a3b:2100]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0123]
	Kernel driver in use: r8169
kai@Kai-Lapbuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 05c8:032a Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 004: ID 0cf3:3008 Atheros Communications, Inc. 
kai@Kai-Lapbuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

kai@Kai-Lapbuntu:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
kai@Kai-Lapbuntu:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223962  1 
rfcomm                 46621  0 
bnep                   18139  2 
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
mxm_wmi                12979  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
btusb                  18295  1 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
bluetooth             185573  13 rfcomm,bnep,btusb
snd_seq_midi           13324  0 
ndiswrapper           283340  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
snd_rawmidi            30748  1 snd_seq_midi
v4l2_compat_ioctl32    17128  1 videodev
ums_realtek            18248  0 
uas                    18180  0 
psmouse                87692  0 
serio_raw              13211  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
i915                  472897  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
wmi                    19256  1 mxm_wmi
mei                    41616  0 
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49198  1 ums_realtek
r8169                  62099  0 

```

---

### Post by wildmanne39 on 2012-08-02
Hi, please try:
```
sudo su
modprobe -v ath9k
echo "168c 0037" > /sys/bus/pci/drivers/ath9k/new_id
exit

```
Then check modinfo.
Thanks

---

### Post by FrogInABoxx on 2012-08-02
> **wildmanne39 said:**
> Hi, please try:
```
sudo su
modprobe -v ath9k
echo "168c 0037" > /sys/bus/pci/drivers/ath9k/new_id
exit

```
Then check modinfo.
Thanks

The result of this was:

```
kai@Kai-Lapbuntu:~$ sudo su
[sudo] password for kai: 
root@Kai-Lapbuntu:/home/kai# modprobe -v ath9k
insmod /lib/modules/3.2.0-27-generic/updates/cw-3.3/cfg80211.ko 
insmod /lib/modules/3.2.0-27-generic/updates/cw-3.3/ath.ko 
insmod /lib/modules/3.2.0-27-generic/updates/cw-3.3/ath9k_hw.ko 
insmod /lib/modules/3.2.0-27-generic/updates/cw-3.3/ath9k_common.ko 
insmod /lib/modules/3.2.0-27-generic/updates/cw-3.3/mac80211.ko 
insmod /lib/modules/3.2.0-27-generic/updates/cw-3.3/ath9k.ko 
root@Kai-Lapbuntu:/home/kai# echo "168c 0037" > /sys/bus/pci/drivers/ath9k/new_id
root@Kai-Lapbuntu:/home/kai# exit
exit
kai@Kai-Lapbuntu:~$ modinfo ath9k
ath9k         ath9k_common  ath9k_htc     ath9k_hw      
kai@Kai-Lapbuntu:~$ modinfo ath9k
ath9k         ath9k_common  ath9k_htc     ath9k_hw      
kai@Kai-Lapbuntu:~$ modinfo ath9k
filename:       /lib/modules/3.2.0-27-generic/updates/cw-3.3/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     21EAA32311830AA82C5169B
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
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
depends:        ath9k_hw,ath9k_common,mac80211,cfg80211,ath
vermagic:       3.2.0-27-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)

```

Unfortunately, it is still not in the list.

---

### Post by wildmanne39 on 2012-08-02
Hi, I asked the wireless expert to take a look hopefully he has time to help out because it can be hard to get an unsupported card to work.
Thanks

---

### Post by FrogInABoxx on 2012-08-02
Alright, thank you so much for putting the effort in to help me.

---

### Post by chili555 on 2012-08-02
@Wild Man--  I have never seen the new_id trick work for PCI devices. Maybe it does, I just haven't seen it.

@Frog--

The Wild Man and I are looking at a thread here: [http://www.digipedia.pl/usenet/thread/18835/36627/](http://www.digipedia.pl/usenet/thread/18835/36627/)

It suggests using the driver ath9k but it says:> it wasn't there in the device ID table in pci.c of ath9kThat's what we're going to do; add the device ID to the driver files and compile a new version. Please be sure you have a wired ethernet connection and do:```
sudo apt-get install linux-headers-generic build-essential
```Now go here and download compat-wireless-2.6.tar.bz2 to your desktop. [http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball](http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball)

When you have the file on your desktop, right-click it and select *Extract Here*. Open the folder it extracts and drill down to drivers/net/wireless/ath/ath9k. Open the file pci.c with any text editor such as gedit. Add your device ID as follows:> static DEFINE_PCI_DEVICE_TABLE(ath_pci_id_table) = {
	{ PCI_VDEVICE(ATHEROS, 0x0023) }, /* PCI   */
	{ PCI_VDEVICE(ATHEROS, 0x0024) }, /* PCI-E */
	{ PCI_VDEVICE(ATHEROS, 0x0027) }, /* PCI   */
	{ PCI_VDEVICE(ATHEROS, 0x0029) }, /* PCI   */
	{ PCI_VDEVICE(ATHEROS, 0x002A) }, /* PCI-E */
	{ PCI_VDEVICE(ATHEROS, 0x002B) }, /* PCI-E */
	{ PCI_VDEVICE(ATHEROS, 0x002C) }, /* PCI-E 802.11n bonded out */
	{ PCI_VDEVICE(ATHEROS, 0x002D) }, /* PCI   */
	{ PCI_VDEVICE(ATHEROS, 0x002E) }, /* PCI-E */
	{ PCI_VDEVICE(ATHEROS, 0x0030) }, /* PCI-E  AR9300 */
	{ PCI_VDEVICE(ATHEROS, 0x0032) }, /* PCI-E  AR9485 */
	{ PCI_VDEVICE(ATHEROS, 0x0033) }, /* PCI-E  AR9580 */
	{ PCI_VDEVICE(ATHEROS, 0x0034) }, /* PCI-E  AR9462 */
	[COLOR="Red"]{ PCI_VDEVICE(ATHEROS, 0x0037) }, /* PCI-E */[/COLOR]
	{ 0 }
};Caution! Spacing, punctuation, etc. are crucial. Proofread twice before saving and closing gedit. All the text before and after the line I've highlighted remains unchanged.

Now in the terminal:```
cd Desktop/compat-wireless-2012-05-10 [COLOR="Red"]<--or whatever version was extracted, if not 2012-05-10[/COLOR]
sudo su
./scripts/driver-select ath9k
make
make install
exit
```Reboot and tell us if your wireless works.

FYI:> modinfo drivers/net/wireless/ath/ath9k/ath9k.ko
filename:       drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     90915124DAEF86FBB8E4295
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000[COLOR="Red"]168C[/COLOR]d0000[COLOR="Red"]0037[/COLOR]sv*sd*bc*sc*i*
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
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211,compat
vermagic:       3.2.0-27-generic-pae SMP mod_unload modversions 686 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)

---

### Post by wildmanne39 on 2012-08-02
Hi, also remove ndiswrapper like this:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```

Thanks chili555.

---

### Post by FrogInABoxx on 2012-08-03
Although it sounded very promising, unfortunately this also has not worked.

After rebooting, modinfo shows that the chipset ID is in the list, however ifconfig and iwconfig still show no sign of wlan0.

```
kai@Kai-Lapbuntu:~$ modinfo ath9k
filename:       /lib/modules/3.2.0-27-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     90915124DAEF86FBB8E4295
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
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
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211,compat
vermagic:       3.2.0-27-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
kai@Kai-Lapbuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

---

### Post by chili555 on 2012-08-03
Let's see:```
sudo modprobe ath9k
dmesg | grep ath9k
```Thanks.

---

### Post by FrogInABoxx on 2012-08-03
> **chili555 said:**
> Let's see:```
sudo modprobe ath9k
dmesg | grep ath9k
```Thanks.

The result is:

```
kai@Kai-Lapbuntu:~$ sudo modprobe ath9k
WARNING: Error inserting ath9k_hw (/lib/modules/3.2.0-27-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko): Invalid argument
WARNING: Error inserting ath9k_common (/lib/modules/3.2.0-27-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko): Invalid argument
WARNING: Error inserting mac80211 (/lib/modules/3.2.0-27-generic/updates/cw-3.3/mac80211.ko): Invalid argument
FATAL: Error inserting ath9k (/lib/modules/3.2.0-27-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko): Invalid argument
kai@Kai-Lapbuntu:~$ dmesg | grep ath9k
kai@Kai-Lapbuntu:~$

```

Although I dont have a lot of knowledge of modprobe, I would be willing to assume that the issue may have something to do with the 3 warnings and fatal error. :)

---

### Post by chili555 on 2012-08-03
> Although I dont have a lot of knowledge of modprobe, I would be willing to assume that the issue may have something to do with the 3 warnings and fatal error..ko-rrect! A little inside joke there. For the benefit of all the driver dawgs out there, we have a conflict in the mac80211 driver. This one is being loaded:> Error inserting mac80211 (/lib/modules/[COLOR="Red"]3.2.0-27-generic/updates/cw-3.3/mac80211.ko[/COLOR]): Invalid argumentHowever, a mac80211 driver was built but is not being loaded in compat-wireless. The two versions conflict. Let's try to fix that.> I tried installing the
```
linux-backports-modules-[COLOR="Red"]cw-3.3[/COLOR]-precise-generic
```
package as suggested by the last post in the thread you specified, however this has had no effect.
We are going to remove it.```
sudo apt-get remove --purge linux-backports-modules-cw-3.3-precise-generic
sudo apt-get remove --purge linux-backports-modules-cw-3.3-3.2.0-27-generic
```Now reboot and give us a report. If it's not working as expected, let us see:```
sudo modprobe ath9k
dmesg | grep ath9k
```

---

### Post by FrogInABoxx on 2012-08-03
As usual, its still not working, though I'm hopeful that if we keep trying it will eventually.

Terminal output from your commands is:

```
kai@Kai-Lapbuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

kai@Kai-Lapbuntu:~$ sudo modprobe ath9k
kai@Kai-Lapbuntu:~$ dmesg | grep ath9k
[    6.644495] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.644507] ath9k 0000:02:00.0: setting latency timer to 64
[    6.644654] ath9k 0000:02:00.0: Failed to initialize device
[    6.644717] ath9k 0000:02:00.0: PCI INT A disabled
[    6.644720] ath9k: probe of 0000:02:00.0 failed with error -95
kai@Kai-Lapbuntu:~$ 

```

---

### Post by chili555 on 2012-08-03
Let's broaden the search:```
dmesg | grep -e ath -e 80211
```> though I'm hopeful that if we keep trying it will eventually.We do too!

---

### Post by chili555 on 2012-08-03
More and newer information! We are going to modify two other files in the compat-wireless package you compiled and then re-compile it.

In the file drivers/net/wireless/ath/ath9k/hw.**c**, change around line 680 as I've highlighted:```
case AR9300_DEVID_AR9485_PCIE:
	case AR9300_DEVID_AR9330:
	case AR9300_DEVID_AR9340:
	case AR9300_DEVID_AR9580:
	case AR9300_DEVID_AR9462:
        [COLOR="Red"]case AR9485_DEVID_AR1111:[/COLOR]
		break;
	default:
		if (common->bus_ops->ath_bus_type == ATH_USB)
			break;
```Also modify drivers/net/wireless/ath/ath9k/hw.**h** around line 51 as highlighted:```
#define AR9300_DEVID_AR9340	0x0031
#define AR9300_DEVID_AR9485_PCIE 0x0032
#define AR9300_DEVID_AR9580	0x0033
#define AR9300_DEVID_AR9462	0x0034
#define AR9300_DEVID_AR9330	0x0035
[COLOR="Red"]#define AR9485_DEVID_AR1111	0x0037
[/COLOR]
#define AR5416_AR9100_DEVID	0x000b

#define	AR_SUBVENDOR_ID_NOG	0x0e11
#define AR_SUBVENDOR_ID_NEW_A	0x7065
#define AR5416_MAGIC		0x19641014
```Now we recompile:```
cd Desktop/compat-wireless-2012-05-10
sudo su
./scripts/driver-select restore
./scripts/driver-select ath9k
make clean
make
make install
exit
```Reboot and give the Wild Man a reason to cheer.

EDIT: Reference for driver dawgs: [http://www.spinics.net/lists/linux-wireless/msg95047.html](http://www.spinics.net/lists/linux-wireless/msg95047.html)

---

### Post by FrogInABoxx on 2012-08-04
> **chili555 said:**
> Let's broaden the search:```
dmesg | grep -e ath -e 80211
```

Returns:

```
kai@Kai-Lapbuntu:~$ dmesg | grep -e ath -e 80211
[    1.876009] ACPI Error: Method parse/execution failed [\GTFB] (Node ffff880211875e60), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[    1.876014] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff880211894190), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[    1.877867] ACPI Error: Method parse/execution failed [\GTFB] (Node ffff880211875e60), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[    1.877872] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT2._GTF] (Node ffff8802118940a0), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[    1.881796] ACPI Error: Method parse/execution failed [\GTFB] (Node ffff880211875e60), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[    1.881801] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff880211894190), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[    1.889625] ACPI Error: Method parse/execution failed [\GTFB] (Node ffff880211875e60), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[    1.889630] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT2._GTF] (Node ffff8802118940a0), AE_AML_BUFFER_LIMIT (20110623/psparse-536)
[    6.649404] cfg80211: Calling CRDA to update world regulatory domain
[    6.698511] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    6.698522] ath9k 0000:02:00.0: setting latency timer to 64
[    6.698670] ath: phy0: Hardware device ID 0x0037 not supported
[    6.698672] ath9k 0000:02:00.0: Failed to initialize device
[    6.698735] ath9k 0000:02:00.0: PCI INT A disabled
[    6.698739] ath9k: probe of 0000:02:00.0 failed with error -95
[    6.731616] cfg80211: World regulatory domain updated:
[    6.731618] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    6.731620] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.731622] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.731623] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    6.731625] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    6.731626] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```

I am going to try your newer solution now, and will be post again soon with the results.

---

### Post by chili555 on 2012-08-04
> ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff880211894190), AE_AML_BUFFER_LIMIT (20110623/psparse-536)Mmmmmm...I don't like that one bit but I doubt it's at all related to wireless.> will be post again soon with the results. Looking forward to it.

---

### Post by FrogInABoxx on 2012-08-04
> **chili555 said:**
> More and newer information! We are going to modify two other files in the compat-wireless package you compiled and then re-compile it.

In the file drivers/net/wireless/ath/ath9k/hw.**c**, change around line 680 as I've highlighted:```
case AR9300_DEVID_AR9485_PCIE:
	case AR9300_DEVID_AR9330:
	case AR9300_DEVID_AR9340:
	case AR9300_DEVID_AR9580:
	case AR9300_DEVID_AR9462:
        [COLOR="Red"]case AR9485_DEVID_AR1111:[/COLOR]
		break;
	default:
		if (common->bus_ops->ath_bus_type == ATH_USB)
			break;
```Also modify drivers/net/wireless/ath/ath9k/hw.**h** around line 51 as highlighted:```
#define AR9300_DEVID_AR9340	0x0031
#define AR9300_DEVID_AR9485_PCIE 0x0032
#define AR9300_DEVID_AR9580	0x0033
#define AR9300_DEVID_AR9462	0x0034
#define AR9300_DEVID_AR9330	0x0035
[COLOR="Red"]#define AR9485_DEVID_AR1111	0x0037
[/COLOR]
#define AR5416_AR9100_DEVID	0x000b

#define	AR_SUBVENDOR_ID_NOG	0x0e11
#define AR_SUBVENDOR_ID_NEW_A	0x7065
#define AR5416_MAGIC		0x19641014
```Now we recompile:```
cd Desktop/compat-wireless-2012-05-10
sudo su
./scripts/driver-select restore
./scripts/driver-select ath9k
make clean
make
make install
exit
```Reboot and give the Wild Man a reason to cheer.

EDIT: Reference for driver dawgs: [http://www.spinics.net/lists/linux-wireless/msg95047.html](http://www.spinics.net/lists/linux-wireless/msg95047.html)


IT WORKED!
Thank you so much!
You sir are an amazing human being, and should be proud of the fact that you have just helped someone that you don't even know, purely out of kindness.


If there is any more information I can provide, or anything I can do to help prevent others from encountering this issue in the future, please let me know, I will be happy to.

Thank you again.

---

### Post by wildmanne39 on 2012-08-04
Hi, please use thread tools at the top of the page and mark the thread solved.
Enjoy

Chili555 you are a genius.
Thanks

---

### Post by FrogInABoxx on 2012-08-04
It is done.

Thank you both again.

---

### Post by chili555 on 2012-08-04
Thank you very much for your kind words. We are glad it's working!> If there is any more information I can provide, or anything I can do to help prevent others from encountering this issue in the future, please let me know, I will be happy to.You already have. The method to get this device working has been implemented and tested by you. I am quite confident that many others will search and find the solution. I'm glad the Wild Man and I could help.

Please remember that when a newer kernel version, known in Ubuntu-land as linux-image is installed by Update Manager, you'll need to recompile this driver:```
cd Desktop/compat-wireless-2012-05-10
sudo su
./scripts/driver-select restore
./scripts/driver-select ath9k
make clean
make
make install
exit
```You might print off these instructions so you'll recall when the time comes. The smart and fast guys like Wild Man, print a pdf and put it in the folder with compat-wireless. Please see attached.

---

### Post by jrave on 2012-08-05
Thank you all!
The modified driver works like a charm for me running Ubuntu 12 on a Novatech Nspire laptop (available without bundled OS)
Today is a happy day.

---

### Post by Gibbs on 2012-08-08
> **jrave said:**
> Thank you all!
The modified driver works like a charm for me running Ubuntu 12 on a Novatech Nspire laptop (available without bundled OS)
Today is a happy day.

Likewise.

Cheers everyone.

---

### Post by ClearCarbon on 2012-08-09
Thanks for these instructions I can confirm it works with the Novatech nSpire N1507 as well ([http://www.novatech.co.uk/laptop/range/novatechnspiren1507.html](http://www.novatech.co.uk/laptop/range/novatechnspiren1507.html))

It was in fact a little easier, only had to make the modifications to the wireless drives didnt have the fatal warnings when doing a sudo modprobe ath9k after the first compile.

---

### Post by Jedwinjim on 2012-08-28
I hate to do this, but I just got back from the shop with a Novatech Ultrabook N1403 & am having the same problem with my wireless. Unfortunately I think I have a little more difficulty following all these instructions & methods than the rest of you do! Should I go from stage 1 of this thread & follow it through as best I can or do I not need to? How exactly did you fix the problem last time with the minimum of steps?

Sorry to be struggling, any help appreciated.

joe.

---

### Post by jrave on 2012-08-28
> **Jedwinjim said:**
> I hate to do this, but I just got back from the shop with a Novatech Ultrabook N1403 & am having the same problem with my wireless. Unfortunately I think I have a little more difficulty following all these instructions & methods than the rest of you do! Should I go from stage 1 of this thread & follow it through as best I can or do I not need to? How exactly did you fix the problem last time with the minimum of steps?

Sorry to be struggling, any help appreciated.

joe.

Patched together from Wild Man and Chili's efforts:

> **chili555 said:**
> 
The Wild Man and I are looking at a thread here: [http://www.digipedia.pl/usenet/thread/18835/36627/](http://www.digipedia.pl/usenet/thread/18835/36627/)

It suggests using the driver ath9k but it says:That's what we're going to do; add the device ID to the driver files and compile a new version.
Please be sure you have a wired ethernet connection and do:
```
sudo apt-get install linux-headers-generic build-essential
```Now go here and download compat-wireless-2.6.tar.bz2 to your desktop.
[http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball](http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball)

When you have the file on your desktop, right-click it and select *Extract Here*. Open the folder it extracts and drill down to drivers/net/wireless/ath/ath9k.
Open the file pci.c with any text editor such as gedit. Add your device ID as follows:

> 
static DEFINE_PCI_DEVICE_TABLE(ath_pci_id_table) = {
{ PCI_VDEVICE(ATHEROS, 0x0023) }, /* PCI */
{ PCI_VDEVICE(ATHEROS, 0x0024) }, /* PCI-E */
{ PCI_VDEVICE(ATHEROS, 0x0027) }, /* PCI */
{ PCI_VDEVICE(ATHEROS, 0x0029) }, /* PCI */
{ PCI_VDEVICE(ATHEROS, 0x002A) }, /* PCI-E */
{ PCI_VDEVICE(ATHEROS, 0x002B) }, /* PCI-E */
{ PCI_VDEVICE(ATHEROS, 0x002C) }, /* PCI-E 802.11n bonded out */
{ PCI_VDEVICE(ATHEROS, 0x002D) }, /* PCI */
{ PCI_VDEVICE(ATHEROS, 0x002E) }, /* PCI-E */
{ PCI_VDEVICE(ATHEROS, 0x0030) }, /* PCI-E AR9300 */
{ PCI_VDEVICE(ATHEROS, 0x0032) }, /* PCI-E AR9485 */
{ PCI_VDEVICE(ATHEROS, 0x0033) }, /* PCI-E AR9580 */
{ PCI_VDEVICE(ATHEROS, 0x0034) }, /* PCI-E AR9462 */
[COLOR="Red"]{ PCI_VDEVICE(ATHEROS, 0x0037) }, /* PCI-E */[/COLOR]
{ 0 }
};

Caution! Spacing, punctuation, etc. are crucial.
Proofread twice before saving and closing gedit. All the text before and after the line I've highlighted remains unchanged.

In the file drivers/net/wireless/ath/ath9k/hw.**c**, change around line 680 as I've highlighted:
```
case AR9300_DEVID_AR9485_PCIE:
	case AR9300_DEVID_AR9330:
	case AR9300_DEVID_AR9340:
	case AR9300_DEVID_AR9580:
	case AR9300_DEVID_AR9462:
        [COLOR="Red"]case AR9485_DEVID_AR1111:[/COLOR]
		break;
	default:
		if (common->bus_ops->ath_bus_type == ATH_USB)
			break;
```

Also modify drivers/net/wireless/ath/ath9k/hw.**h** around line 51 as highlighted:
```
#define AR9300_DEVID_AR9340	0x0031
#define AR9300_DEVID_AR9485_PCIE 0x0032
#define AR9300_DEVID_AR9580	0x0033
#define AR9300_DEVID_AR9462	0x0034
#define AR9300_DEVID_AR9330	0x0035
[COLOR="Red"]#define AR9485_DEVID_AR1111	0x0037
[/COLOR]
#define AR5416_AR9100_DEVID	0x000b

#define	AR_SUBVENDOR_ID_NOG	0x0e11
#define AR_SUBVENDOR_ID_NEW_A	0x7065
#define AR5416_MAGIC		0x19641014
```

Now in the terminal:
```
cd Desktop/compat-wireless-2012-05-10 [COLOR="Red"]<--or whatever version was extracted, if not 2012-05-10[/COLOR]
sudo su
./scripts/driver-select ath9k
make
make install
exit
```

Reboot and give the Wild Man a reason to cheer.

EDIT: Reference for driver dawgs: [http://www.spinics.net/lists/linux-wireless/msg95047.html](http://www.spinics.net/lists/linux-wireless/msg95047.html)


If you have installed ndiswrapper:

> **Wild Man said:**
> Hi, also remove ndiswrapper like this:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```

Thanks chili555.

You can avoid a reboot if you are comfortable to do so after the **`make install`** by following the instructions it gives you.
Something like: ```
sudo make wlunload
sudo modprobe ath9k
```

---

### Post by rabideau on 2012-09-04
I hate being dumb, although I am good at it.  But when I follow the link to get the base code to change:

Now go here and download compat-wireless-2.6.tar.bz2 to your desktop.
[http://linuxwireless.org/en/users/Do...ng_the_tarball]("http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball")

I end up on the following page
[http://wireless.kernel.org/en/users/Download/stable/#Older_stable_releases](http://wireless.kernel.org/en/users/Download/stable/#Older_stable_releases) 

and I have no idea which file I am supposed to use to edit for my ar9462 wireless.

Any help for the hopeless?

---

### Post by chili555 on 2012-09-04
> **rabideau said:**
> I hate being dumb, although I am good at it.  But when I follow the link to get the base code to change:

Now go here and download compat-wireless-2.6.tar.bz2 to your desktop.
[http://linuxwireless.org/en/users/Do...ng_the_tarball]("http://linuxwireless.org/en/users/Download#Directly_downloading_the_tarball")

I end up on the following page
[http://wireless.kernel.org/en/users/Download/stable/#Older_stable_releases](http://wireless.kernel.org/en/users/Download/stable/#Older_stable_releases) 

and I have no idea which file I am supposed to use to edit for my ar9462 wireless.

Any help for the hopeless?The latest version 3.5.1.1snpc already contains the change but may or may not compile correctly depending on your kernel version. I suggest you start with that one and if you get through 'make' with no errors, you're all set. You may safely sudo make install and sudo modprobe ath9k.

FYI:> static DEFINE_PCI_DEVICE_TABLE(ath_pci_id_table) = {
        { PCI_VDEVICE(ATHEROS, 0x0023) }, /* PCI   */
        { PCI_VDEVICE(ATHEROS, 0x0024) }, /* PCI-E */
        { PCI_VDEVICE(ATHEROS, 0x0027) }, /* PCI   */
        { PCI_VDEVICE(ATHEROS, 0x0029) }, /* PCI   */
        { PCI_VDEVICE(ATHEROS, 0x002A) }, /* PCI-E */
        { PCI_VDEVICE(ATHEROS, 0x002B) }, /* PCI-E */
        { PCI_VDEVICE(ATHEROS, 0x002C) }, /* PCI-E 802.11n bonded out */
        { PCI_VDEVICE(ATHEROS, 0x002D) }, /* PCI   */
        { PCI_VDEVICE(ATHEROS, 0x002E) }, /* PCI-E */
        { PCI_VDEVICE(ATHEROS, 0x0030) }, /* PCI-E  AR9300 */
        { PCI_VDEVICE(ATHEROS, 0x0032) }, /* PCI-E  AR9485 */
        { PCI_VDEVICE(ATHEROS, 0x0033) }, /* PCI-E  AR9580 */
        { PCI_VDEVICE(ATHEROS, 0x0034) }, /* PCI-E  AR9462 */
        { PCI_VDEVICE(ATHEROS, 0x[COLOR="Red"]0037[/COLOR]) }, /* PCI-E  AR1111/AR9485 */
        { 0 }
};
Yippee.

---

### Post by rabideau on 2012-09-07
Thank you VERY MUCH!  This fix is as 'slick as goose grease'.

---

### Post by chili555 on 2012-09-07
> This fix is as 'slick as goose grease'.That's our goal!

Glad it's working. You have compiled the driver only for your currently running kernel version. When Update Manager installs a later linux-image, aka kernel, you'll need to compile a driver for the new one after you reboot:```
cd Desktop/compat-wireless-3.5.1-1-snpc  [COLOR="Red"]<--or wherever you extracted it[/COLOR]
[COLOR="Red"]make clean[/COLOR]
make
sudo make install
sudo modprobe ath9k
```Please retain these notes for that inevitable day.

---

### Post by daaxwizeman on 2012-09-14
Hi,

I have an Atheros AR9462 card and I cannot connect to the net. I ead all he thread and I don't know if I can apply theses procedures to my case. I don' seem to have a problem with my device ID not appearing in modinfo ath9k.

Anyway, I tried all sorts of solution proposed here and there and nothing works. I didn't try the madwifi nor the ndiswrapper solution though.

Here's some of the output of commands suggested by Wild Man :

```

karine@karlinux:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux karlinux 3.2.0-30-generic #48-Ubuntu SMP Fri Aug 24 16:52:48 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

``````

karine@karlinux:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:0696]
    Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6621]
    Kernel driver in use: ath9k

``````

karine@karlinux:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 1bcf:2c18 Sunplus Innovation Technology Inc. 
Bus 004 Device 002: ID 04ca:3006 Lite-On Technology Corp. 
Bus 003 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
karine@karlinux:~$ iwconfig

``````

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

karine@karlinux:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
karine@karlinux:~$ lsmod

``````

Module                  Size  Used by
usbhid                 47199  0 
hid                    99559  1 usbhid
ath9k                 130564  0 
rfcomm                 46621  12 
bnep                   18139  2 
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
vesafb                 13844  1 
snd_hda_codec_realtek   224173  1 
snd_hda_codec_hdmi     32474  0 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
mac80211              514621  1 ath9k
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           14053  1 ath9k
snd                    78855  16 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
btusb                  18295  2 
ath9k_hw              400326  2 ath9k,ath9k_common
uvcvideo               72627  0 
bluetooth             185573  23 rfcomm,bnep,btusb
ath                    23827  3 ath9k,ath9k_common,ath9k_hw
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
psmouse                87692  0 
fglrx                3263886  120 
serio_raw              13211  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_piix4              13301  0 
cfg80211              209821  3 ath9k,mac80211,ath
k10temp                13166  0 
wmi                    19256  1 acer_wmi
rts_pstor             445196  0 
video                  19596  0 
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
atl1c                  40748  0 


```

Any help would be appreciated and thanks in advance. :D

---

### Post by chili555 on 2012-09-14
> **daaxwizeman said:**
> Hi,

I have an Atheros AR9462 card and I cannot connect to the net. I ead all he thread and I don't know if I can apply theses procedures to my case. I don' seem to have a problem with my device ID not appearing in modinfo ath9k.

Anyway, I tried all sorts of solution proposed here and there and nothing works. I didn't try the madwifi nor the ndiswrapper solution though.Does it scan?```
sudo iwlist wlan0 scan
```Are there any interesting clues in the message logs?```
dmesg | grep ath
```When you click the Network Manager icon, do you see networks?

---

### Post by daaxwizeman on 2012-09-14
Hi chili555

It does scan. Here's what I have :

```

karine@karlinux:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: C4:3D:C7:A3:08:05
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"daax"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000004cefe2adc41
                    Extra: Last beacon: 228ms ago
                    IE: Unknown: 000464616178
                    IE: Unknown: 01088C129824B048606C
                    IE: Unknown: 03012C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CE011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACE011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C342C0D0800000000000000000000000000000000000000
                    IE: Unknown: 3D162C0D0800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD860050F204104A0001101044000102103B0001031047001000000000000010000000C43DC7A308031021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F204000110110017574E445233373030763228576972656C65737320415029100800020086103C000103
          Cell 02 - Address: C4:3D:C7:A3:08:03
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"daax"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b93cdb6d
                    Extra: Last beacon: 4948ms ago
                    IE: Unknown: 000464616178
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33CC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401080800000000000000000000000000000000000000
                    IE: Unknown: 3D1601080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD860050F204104A0001101044000102103B0001031047001000000000000010000000C43DC7A308031021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F204000110110017574E445233373030763228576972656C65737320415029100800020086103C000103

```It is weird because I get a lot of this IE: Unknown.

The second command gave me this :

```

karine@karlinux:~$ dmesg | grep ath
[   16.874381] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.874411] ath9k 0000:02:00.0: setting latency timer to 64
[   16.883842] ath: EEPROM regdomain: 0x6a
[   16.883846] ath: EEPROM indicates we should expect a direct regpair map
[   16.883850] ath: Country alpha2 being used: 00
[   16.883852] ath: Regpair used: 0x6a
[   16.894631] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   17.193527] Registered led device: ath9k-phy0
[ 1045.910098] ath9k 0000:02:00.0: PCI INT A disabled
[ 1045.910149] ath9k: Driver unloaded
[ 1063.956868] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 1063.956900] ath9k 0000:02:00.0: setting latency timer to 64
[ 1063.966468] ath: EEPROM regdomain: 0x6a
[ 1063.966471] ath: EEPROM indicates we should expect a direct regpair map
[ 1063.966476] ath: Country alpha2 being used: 00
[ 1063.966478] ath: Regpair used: 0x6a
[ 1063.977139] ieee80211 phy1: Selected rate control algorithm 'ath9k_rate_control'
[ 1063.979252] Registered led device: ath9k-phy1

```When I ran the liveCD, everything worked. When I installed it, I was able to connect without any problem. After the install complete and the updates applied, I couldn't connect anymore.

---

### Post by chili555 on 2012-09-14
> Cell 01 - Address: C4:3D:C7:A3:08:05
                    [COLOR="Red"]Channel:44[/COLOR]
                    Frequency:5.22 GHz (Channel 44)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"daax"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:MasterDoes your card do channel 44?```
sudo iwlist wlan0 channel
```> When I ran the liveCD, everything worked. When I installed it, I was able to connect without any problem. After the install complete and the updates applied, I couldn't connect anymore. Can you run the live CD again and run:```
dmesg | grep ath
```I am very interested in this:> ieee80211 phy1: Selected rate control algorithm 'ath9k_rate_control'[http://comments.gmane.org/gmane.linux.drivers.ath9k.devel/6751](http://comments.gmane.org/gmane.linux.drivers.ath9k.devel/6751)

We might try minstrel_ht.

---

### Post by daaxwizeman on 2012-09-14
Hi,

I do not know if my card is doing channel 44 since I don't know what you are talking about.... ;)

Here's the output :

```

karine@karlinux:~$ sudo iwlist wlan0 channel
wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.412 GHz (Channel 1)

```

Ok, I'll try again with the liveCD and get back to you.

---

### Post by chili555 on 2012-09-14
> karine@karlinux:~$ sudo iwlist wlan0 channel
wlan0     32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          <snip>
          [COLOR="Red"]Channel 44 : 5.22 GHz[/COLOR]
          Channel 48 : 5.24 GHz
          <snip>Your wireless card receives and sends on channel 44 just fine. I await your live CD report.>  do not know if my card is doing channel 44 since I don't know what you are talking about...Imagine if you paid for cable TV and, like cheap old Dr. Chili, you only got channels 1-12. If your pal asked you if you saw a program on channel 607, you'd have to admit you didn't. We just want to confirm that the channel your router is transmitting on is receivable by your driver/card combination. We have; no worries there.

---

### Post by daaxwizeman on 2012-09-14
> **chili555 said:**
> Your wireless card receives and sends on channel 44 just fine. I await your live CD report.Imagine if you paid for cable TV and, like cheap old Dr. Chili, you only got channels 1-12. If your pal asked you if you saw a program on channel 607, you'd have to admit you didn't. We just want to confirm that the channel your router is transmitting on is receivable by your driver/card combination. We have; no worries there.

Thanks for the explanation and I am glad some things are right. ;)

Now I am posting here form a liveCD session and I am connecting to the net without an itch. Here's the output of the command you required :

```

ubuntu@ubuntu:~$ dmesg | grep ath
[   80.524449] device-mapper: multipath: version 1.3.0 loaded
[  101.998701] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  101.998732] ath9k 0000:02:00.0: setting latency timer to 64
[  102.007448] ath: EEPROM regdomain: 0x6a
[  102.007451] ath: EEPROM indicates we should expect a direct regpair map
[  102.007455] ath: Country alpha2 being used: 00
[  102.007456] ath: Regpair used: 0x6a
[  102.816412] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[  102.817581] Registered led device: ath9k-phy0
[  529.660775] ath: Could not kill baseband RX


```

The thing you are interested in is there again.

---

### Post by chili555 on 2012-09-14
> The thing you are interested in is there again.Yes, indeed. Also, most everything else is virtually unchanged. That leaves us no clues as to what to fix.

I suggest you install the Ubuntu version of compat-wireless:```
sudo apt-get install linux-backports-modules-cw-3.3-precise-generic
```Unload the old and reload the new driver:```
sudo modprobe -r ath9k
sudo modprobe ath9k
```Any improvement?

---

### Post by daaxwizeman on 2012-09-14
Hi chili555,

I don't know what is happening right now but guess what ? The wireless card connect to the net wihout an itch this time since I came back from the live session. I am fighting with it til yesterday and now it is working....:-s

Though, I don't know if it'll work for good.

When I did first post in this thread, I already had the linux-backports-modules-cw.... installed on my system.

I'll reboot again to see if it still works.

---

### Post by daaxwizeman on 2012-09-14
Here's what I have with the command : 

```

dmesg | grep ath
[   15.872836] ath9k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.872866] ath9k 0000:02:00.0: setting latency timer to 64
[   15.884906] ath: EEPROM regdomain: 0x6a
[   15.884911] ath: EEPROM indicates we should expect a direct regpair map
[   15.884915] ath: Country alpha2 being used: 00
[   15.884917] ath: Regpair used: 0x6a
[   16.047611] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   16.048379] Registered led device: ath9k-phy0
[   19.027050] type=1400 audit(1347640583.956:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=965 comm="apparmor_parser"

```

The last line wasn't there... There is something about apparmor ???

---

### Post by chili555 on 2012-09-14
> **daaxwizeman said:**
> 
The last line wasn't there... There is something about apparmor ???It's unrelated to ath9k. Is your wireless working correctly now?

---

### Post by daaxwizeman on 2012-09-14
Hi chili555,

I rebooted again and the connection worked like a charm.... 

So, I'll keep on testing and seee if it holds. I cross my finger. ;)

Thanks a lot for the help, it is really appreciated. :)

---

### Post by chili555 on 2012-09-14
Awesome! Post back if we can help again.

---

### Post by daaxwizeman on 2012-09-14
Hi again chili555.

So, it wasn't awesome in fact. I rebooted again the system and wasn't able to connect again.

I did a fresh reinstall of ubuntu, I think something broke my driver or whatever it is.

In liveCD everything went fine. After instalation and 400 updates, everything works fine. I booted the system 5 times since then and it connected with no hassle.

I thought it could be the update of the kernel that broke something, but it doesn't seem so. Let's hope it'll brake no more.

I'll report to you if I have problems again. Fingers crossed. ;)

---

### Post by norm.h on 2012-11-09
I'm not sure if I should have started a new thread, but my problem relates to the instructions here, and my machine is also similar to that of the OP.

I have installed Mint 13 (Mate) on a brand new Novatech nSpire laptop, and there doesn't seem to be a driver for the wifi.

lspci shows the Network Controller as an Atheros 0037 (rev 1), so I followed the instructions in Post 35 of this thread, but it failed.

Could it be that the instructions don't apply to Mint 13, as I'm sure I followed the instructions correctly?

I have also posted in the Linux Mint forums.

For information:

normh@normh-nspire ~ $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

normh@normh-nspire ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 4c:72:b9:86:d8:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
lo        no wireless extensions.

eth0      no wireless extensions.

normh@normh-nspire ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 4c:72:b9:86:d8:23  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0http://ubuntuforums.org/showthread.php?t=2035902&page=4
          collisions:0 txqueuelen:0 
          RX bytes:1920 (1.9 KB)  TX bytes:1920 (1.9 KB)

normh@normh-nspire ~ $ sudo lshw -c network
[sudo] password for normh: 
  *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHzhttp:
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7c00000-f7c7ffff memory:f7c80000-f7c8ffff

---

### Post by norm.h on 2012-11-09
Some more info, in case it helps:

lspci -v
02:00.0 Network controller: Atheros Communications Inc. Device 0037 (rev 01)
	Subsystem: AzureWave Device 2100
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at f7c00000 (64-bit, non-prefetchable) [size=512K]
	Expansion ROM at f7c80000 [disabled] [size=64K]
	Capabilities: <access denied>

lspci -k
02:00.0 Network controller: Atheros Communications Inc. Device 0037 (rev 01)
	Subsystem: AzureWave Device 2100

---

### Post by chili555 on 2012-11-09
> **norm.h said:**
> Some more info, in case it helps:

lspci -v
02:00.0 Network controller: Atheros Communications Inc. Device 0037 (rev 01)
	Subsystem: AzureWave Device 2100
	Flags: bus master, fast devsel, latency 0, IRQ 3
	Memory at f7c00000 (64-bit, non-prefetchable) [size=512K]
	Expansion ROM at f7c80000 [disabled] [size=64K]
	Capabilities: <access denied>

lspci -k
02:00.0 Network controller: Atheros Communications Inc. Device 0037 (rev 01)
	Subsystem: AzureWave Device 2100We'd love to see:```
lspci -nn
```

---

### Post by norm.h on 2012-11-09
normh@normh-nspire ~ $ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1c.2 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 3 [8086:1e14] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e59] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0037] (rev 01)
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
normh@normh-nspire ~ $

---

### Post by chili555 on 2012-11-09
> Atheros Communications Inc. Device [[COLOR="Red"]168c:0037[/COLOR]] (rev 01)Let's see if the module you built correctly covers your device:```
modinfo ath9k | grep 0037
```Let's see if there are any interesting warnings or errors:```
sudo modprobe ath9k
dmesg | grep ath
```

---

### Post by norm.h on 2012-11-09
normh@normh-nspire ~ $ modinfo ath9k | grep 0037
normh@normh-nspire ~ $ sudo modprobe ath9k
[sudo] password for normh: 
normh@normh-nspire ~ $ dmesg | grep ath
normh@normh-nspire ~ $ 

Oh dear!

EDIT:
As a point of interest, the compat-wireless gives the option of number of files to download.
I downloaded version 2.6.39-1, as it's the latest in the 2.6 series. 
Was this the right one?

---

### Post by chili555 on 2012-11-09
> Oh dear!Oh, dear, indeed. It looks like you didn't make or make all or make correctly the highlighted changes as per post #35. Please double-check. If you need to make further changes, you'll need to recompile:```
sudo su
make clean
./scripts/driver-select restore
./scripts/driver-select ath
make
make install
make wlunload
modprobe ath9k
exit
```> I downloaded version 2.6.39-1, as it's the latest in the 2.6 series.
Was this the right one?Ideally, the version you selected to build would 'make' with no error and no warnings. Did it? If so, you're good.

---

### Post by norm.h on 2012-11-09
Will do, but may not be until tomorrow.

EDIT: 
During make / make install I got messages saying warnings were being treated as errors.
Should I try a different compat-wireless version and if so, which one?
Or is it a matter of trial and error?
Thanks.

---

### Post by chili555 on 2012-11-09
I'd try this: [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.1/compat-wireless-3.1.1-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.1/compat-wireless-3.1.1-1.tar.bz2)

Please post any errors and we'll try to help.

---

### Post by norm.h on 2012-11-09
OK, will try that one, but do all the other steps in Post 35 still apply, and is there anything from my first attempts that needs to be removed?

---

### Post by chili555 on 2012-11-09
All the steps still apply; 0037 is not included until you add it. The newer install will overwrite the old.

---

### Post by norm.h on 2012-11-10
I copied and pasted the commands from the instructions in Post 35, but unfortunately it's still not working.
FWIW, sudo lshw -c network still shows UNCLAIMED


Here are extracts from make and make install.

Extract from MAKE. This was preceded by LOTS of WARNINGS

/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:25:15: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:26:20: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:27:25: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:28:16: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:31:40: error: expected &#8216;)&#8217; before &#8216;uint&#8217;
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:32:25: error: expected &#8216;)&#8217; before string constant
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:35:57: error: expected &#8216;)&#8217; before &#8216;int&#8217;
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:36:29: error: expected &#8216;)&#8217; before string constant
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:39:38: error: expected &#8216;)&#8217; before &#8216;int&#8217;
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:40:25: error: expected &#8216;)&#8217; before string constant
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:43:56: error: expected &#8216;)&#8217; before &#8216;int&#8217;
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:44:33: error: expected &#8216;)&#8217; before string constant
make[5]: *** [/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.o] Error 1
make[4]: *** [/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k] Error 2
make[3]: *** [/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath] Error 2
make[2]: *** [/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/normh/Desktop/compat-wireless-3.1.1-1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make: *** [modules] Error 2

Extract from MAKE INSTALL

make -C /lib/modules/3.2.0-23-generic/build M=/home/normh/Desktop/compat-wireless-3.1.1-1 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  CC [M]  /home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.o
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:25:15: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:26:20: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:27:25: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:28:16: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:31:40: error: expected &#8216;)&#8217; before &#8216;uint&#8217;
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:32:25: error: expected &#8216;)&#8217; before string constant
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:35:57: error: expected &#8216;)&#8217; before &#8216;int&#8217;
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:36:29: error: expected &#8216;)&#8217; before string constant
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:39:38: error: expected &#8216;)&#8217; before &#8216;int&#8217;
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:40:25: error: expected &#8216;)&#8217; before string constant
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:43:56: error: expected &#8216;)&#8217; before &#8216;int&#8217;
/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.c:44:33: error: expected &#8216;)&#8217; before string constant
make[5]: *** [/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.o] Error 1
make[4]: *** [/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k] Error 2
make[3]: *** [/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath] Error 2
make[2]: *** [/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/normh/Desktop/compat-wireless-3.1.1-1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make: *** [modules] Error 2
normh-nspire compat-wireless-3.1.1-1 # e

---

### Post by chili555 on 2012-11-10
Those are more than warnings; they are errors.> [COLOR="Red"]make[/COLOR][5]: *** [/home/normh/Desktop/compat-wireless-3.1.1-1/drivers/net/wireless/ath/ath9k/init.o] [COLOR="Red"]Error[/COLOR] 1When you see errors at 'make' stop, because nothing following is going to work at all. That's Linux-speak that means, roughly, "Stop! You have a version mis-match!!!"

I believe Mint 13 uses a 3.2.0.xx kernel. Verify:```
uname -r
```Let's try a compat-wireless version closer to 3.2.0.xx: [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.2/compat-wireless-3.2-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.2/compat-wireless-3.2-1.tar.bz2)

Your device 0037 is still not covered in this version, you'll need to make the changes from post #35.

You may as well delete the other versions of compat-wireless on your desktop since they don't work.

---

### Post by norm.h on 2012-11-10
normh@normh-nspire ~ $ uname -r
3.2.0-23-generic
normh@normh-nspire ~ $ 

Stopped as instructed because:

Extract from "make":

/home/normh/Desktop/compat-wireless-3.2-1/net/wireless/core.c:7:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
/home/normh/Desktop/compat-wireless-3.2-1/net/wireless/core.c:7:0: warning: "pr_fmt" redefined [enabled by default]
include/linux/printk.h:152:0: note: this is the location of the previous definition
  CC [M]  /home/normh/Desktop/compat-wireless-3.2-1/net/wireless/sysfs.o
  CC [M]  /home/normh/Desktop/compat-wireless-3.2-1/net/wireless/radiotap.o
  CC [M]  /home/normh/Desktop/compat-wireless-3.2-1/net/wireless/util.o
/home/normh/Desktop/compat-wireless-3.2-1/net/wireless/util.c: In function &#8216;cfg80211_change_iface&#8217;:
/home/normh/Desktop/compat-wireless-3.2-1/net/wireless/util.c:810:2: error: implicit declaration of function &#8216;br_port_exists&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[3]: *** [/home/normh/Desktop/compat-wireless-3.2-1/net/wireless/util.o] Error 1
make[2]: *** [/home/normh/Desktop/compat-wireless-3.2-1/net/wireless] Error 2
make[1]: *** [_module_/home/normh/Desktop/compat-wireless-3.2-1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make: *** [modules] Error 2


EDIT: Can't respond until tomorrow, I'm afraid

---

### Post by chili555 on 2012-11-10
I am on the way out the door, but when I return, I will fire up a 12.04 live CD and figure this tough problem out. I'm sorry, I usually compile before I recommend, but installing Mint is not an option. I will, however, try a 12.04 live CD.

Later.

---

### Post by chili555 on 2012-11-10
This version compiles on 3.2.0-xx with a few warnings and no errors!

[http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-11-10-pc.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2012-11-10-pc.tar.bz2)

Best of all, it has the needed modifications to cover your 0037 device *ALREADY PRESENT!*  Woo hoo!> static DEFINE_PCI_DEVICE_TABLE(ath_pci_id_table) = {
        { PCI_VDEVICE(ATHEROS, 0x0023) }, /* PCI   */
        { PCI_VDEVICE(ATHEROS, 0x0024) }, /* PCI-E */
        { PCI_VDEVICE(ATHEROS, 0x0027) }, /* PCI   */
        { PCI_VDEVICE(ATHEROS, 0x0029) }, /* PCI   */
        { PCI_VDEVICE(ATHEROS, 0x002A) }, /* PCI-E */
        { PCI_VDEVICE(ATHEROS, 0x002B) }, /* PCI-E */
        { PCI_VDEVICE(ATHEROS, 0x002C) }, /* PCI-E 802.11n bonded out */
        { PCI_VDEVICE(ATHEROS, 0x002D) }, /* PCI   */
        { PCI_VDEVICE(ATHEROS, 0x002E) }, /* PCI-E */
        { PCI_VDEVICE(ATHEROS, 0x0030) }, /* PCI-E  AR9300 */
        { PCI_VDEVICE(ATHEROS, 0x0032) }, /* PCI-E  AR9485 */
        { PCI_VDEVICE(ATHEROS, 0x0033) }, /* PCI-E  AR9580 */
        { PCI_VDEVICE(ATHEROS, 0x0034) }, /* PCI-E  AR9462 */
        { PCI_VDEVICE(ATHEROS, 0x[COLOR="Red"]0037[/COLOR]) }, /* PCI-E  AR1111/AR9485 */
        { PCI_VDEVICE(ATHEROS, 0x0036) }, /* PCI-E  AR9565 */
        { 0 }
Please compile and give us a good report.

---

### Post by norm.h on 2012-11-11
"*Woo hoo!*" indeed.
Well the good news is that this works.
It finds the networks OK.

The bad news is that it won't let me connect.
I'm sure it's a router configuration issue, which I'll have to overcome.

Many thanks for your interest, perseverance and patience.
Like British Rail used to say: "*We're getting there*!"

Will your comment about recompiling the driver for a newer kernel still apply?
I've copied the commands just in case.

EDIT:
Router reconfigured - all working OK
Again, many thanks

---

### Post by chili555 on 2012-11-11
> Will your comment about recompiling the driver for a newer kernel still apply?Yessir!

Let us know how you get on.

---

### Post by norm.h on 2012-11-11
You must have missed my edit:
"[I]Router reconfigured - all working OK
Again, many thanks"[/I]

---

### Post by chili555 on 2012-11-11
> **norm.h said:**
> You must have missed my edit:
"[I]Router reconfigured - all working OK
Again, many thanks"[/I]Awesome, sir! I'm glad to hear it and you will have helped many searchers.

Have fun!

---

### Post by nezero on 2013-01-09
```
Network controller: Atheros Communications Inc. Device 0037 (rev 01)
```

Thanks guys, you help me a great deal with my new laptop.

I posted details about my laptop [here]("http://ubuntuforums.org/showpost.php?p=12446399&postcount=1307"), though i'll repeat my WiFi experience.

I downloaded [this]("http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1.tar.bz2") driver and ran these commands after extracting.

```
sudo su
./scripts/driver-select restore
./scripts/driver-select ath9k
make clean
make
make install
reboot
```

There was no need to edit code (may have been mentioned already in this thread), that driver and those commands all worked fine.

Thanks again to all those who contributed to fixing this.

---

### Post by Murdoc_of_puts on 2013-08-08
Allright, so I'm having problems.  I've followed this thread to the end, I've got a slightly different card- 9462 :0034  .  I've been adjusting things as I go for that model, which is supported mostly in all of the drivers that I've been looking at.  My problem is that I can't turn on the card.  I was hoping that if I just installed the right driver magic would happen.  So far though, no magic.  Weird thing is that the bluetooth works just fine.  Here's some tech specs.

```

uname -a
Linux poopzilla 3.2.50 #1 SMP Sat Aug 3 12:23:28 PDT 2013 x86_64 x86_64 x86_64 GNU/Linux

lsmod
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

lshw -C network

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

rfkill list
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
       ** Hard blocked: yes**

lspci (edited)
0a:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)
0b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

iwconfig
wlan2     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on


modinfo ath9k

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

I'm on a toshiba a665d-so91. There's a little button to turn on the wifi, that isn't working, but will work on another wifi card no problem, so it's not that section of hardware.  I would really appreciate any help that you could give me. I hate to just dump info onto here, but hopefully this will help with a solution.

---

### Post by chili555 on 2013-08-08
> **Murdoc_of_puts said:**
> Allright, so I'm having problems.  I've followed this thread to the end, I've got a slightly different card- 9462 :0034  .  I've been adjusting things as I go for that model, which is supported mostly in all of the drivers that I've been looking at.  My problem is that I can't turn on the card.  I was hoping that if I just installed the right driver magic would happen.  So far though, no magic.  Weird thing is that the bluetooth works just fine. 

I'm on a toshiba a665d-so91. There's a little button to turn on the wifi, that isn't working, but will work on another wifi card no problem, so it's not that section of hardware.  I would really appreciate any help that you could give me. I hate to just dump info onto here, but hopefully this will help with a solution.Since you have a slightly different problem and a slightly different card, please start your own new thread. Include everything here plus:```
lspci -nn | grep 0280
uname -r

```Fascinating.

---

### Post by Murdoc_of_puts on 2013-08-08
Ok, thanks, I moved it to [here]("http://ubuntuforums.org/showthread.php?t=2166344&p=12750496#post12750496")

---


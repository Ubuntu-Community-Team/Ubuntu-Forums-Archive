---
title: "MSI wind U135 wireless card"
date: 2010-02-03
forum: Hardware
---

### Post by banditxkr on 2010-02-03
Hi everyone and thanks in advance,

I just bought an MSI wind and am going to install Ubuntu on it. I've tried booting using a flash drive with many different flavors and variations. None of them seem to recognize my wireless card. I've run ifconfig in the terminal every time and it never returns anything on the wireless card.

Any ideas?

Thanks again!


Versions tried(Ubuntu 9.10,9.04, netbook remix 9.10, fedora 12)

---

### Post by josmeijer on 2010-02-04
> **banditxkr said:**
> Hi everyone and thanks in advance,

I just bought an MSI wind and am going to install Ubuntu on it. I've tried booting using a flash drive with many different flavors and variations. None of them seem to recognize my wireless card. I've run ifconfig in the terminal every time and it never returns anything on the wireless card.

Any ideas?

Thanks again!


Versions tried(Ubuntu 9.10,9.04, netbook remix 9.10, fedora 12)

risking asking a stupid question:
did you turn the card on by the the Fn+F3 keycombination?

---

### Post by banditxkr on 2010-02-04
It's actually f11 on this model but yes i did (f3 turns off touch-pad). It's best to remove any possibility though.

---

### Post by banditxkr on 2010-02-06
I've decided to do a full install and see how it goes, maybe it's just a USB mode thing....

---

### Post by Alienswede on 2010-02-27
FWIW, I have my MSI Wind running Xubuntu 9.10. Surprisingly it mostly worked out of the box. I was expecting and was ready for a bit more fuss but I'm glad it did work. The only problem was spotty wireless reception with the installed drivers. An upgrade to the most current drivers solved my problems.

For posterity...

```

$ lspci
00:00.0 Host bridge: Intel Corporation Pineview DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation Pineview Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation Pineview Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation Tigerpoint LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

```

---

### Post by banditxkr on 2010-02-27
the only problem is that, even when i run lspci the wireless card doesn't show up, it also doesn't show up under ifconfig.

my friend has the msi u100 and his worked great out of the box, this is the u135 and im having much less luck

---

### Post by Alienswede on 2010-02-28
Does it work under *shudder* Windows? Can you post the output of [FONT=Courier New]dmesg[/FONT] after a fresh reboot as well as [FONT=Courier New]sudo lshw -C network[/FONT]? (There's a small chance you may need to install [FONT=Courier New]lshw[/FONT] first)

---

### Post by taffy-nay on 2010-03-13
I'm am having the same problem. I really want to get this working as my U135 came with Windows 7 Starter Edition. I am unable to even change my wallpaper without hacking the registry.

---

### Post by isuc on 2010-04-10
> **Alienswede said:**
> FWIW, I have my MSI Wind running Xubuntu 9.10. Surprisingly it mostly worked out of the box. I was expecting and was ready for a bit more fuss but I'm glad it did work. The only problem was spotty wireless reception with the installed drivers. An upgrade to the most current drivers solved my problems.
[/code]

I have the same model and same symptoms, connection gets a bit spotty at times, how were you able to update the drivers?

2nd question: has anyone been able to get the webcam to work?

---

### Post by M.a.d on 2010-04-13
> **isuc said:**
> I have the same model and same symptoms, connection gets a bit spotty at times, how were you able to update the drivers?

2nd question: has anyone been able to get the webcam to work?

Same issues here: No wireless and no camera :-(

This model worked fine with Ubuntu in 9.04 but 9.10 as well as 10.04 beta2 has no wireless and camera support.

---

### Post by isuc on 2010-04-13
Hey M.a.d i fixed my wireless problem by installing Wicd, search for it in the software center, now i stay connected with a stronger signal. no luck on the webcam though

---

### Post by isuc on 2010-04-13
(Possible Solution)
I now have my webcam working in ubuntu. what i did was boot back into windows, my webcam was turned off (with the function-F7 key) i re-enabled it. quit windows and booted back into ubuntu, now it shows up, in cheese, skype, all seems to be well. guess windows is still good for something.

it seems to me that both problems with the wireless and the webcam were related to the function keys misbehaving or not behaving at all, hopefully this will be mended in an update.

---

### Post by clipt on 2010-09-18
my u135 worked correctly when i installed from usb. only thing that is sketchy is the webcam.. but wifi works!

---

### Post by yron87 on 2010-09-30
Worked for me on Wifi

[http://ubuntuforums.org/showthread.php?p=9909732#post9909732](http://ubuntuforums.org/showthread.php?p=9909732#post9909732)

---


---
title: "Lubuntu LXQt won't connect to my BCM4311 802.11b/g WLAN"
date: 2021-03-11
forum: Hardware
---

### Post by Toledoubf on 2021-03-11
I have an hp 500c with Lubuntu LXQt  (Ubuntu 18.1) Kernel  Linux 4.18.0-10-generic.

Here is some info:

[FONT=Arial]00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)[/FONT]
[FONT=Arial]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)[/FONT]
[FONT=Arial]00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)[/FONT]
[FONT=Arial]00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01) [/FONT][FONT=Arial]00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)[/FONT]
[FONT=Arial]00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 01)[/FONT]
[FONT=Arial]00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)[/FONT]
[FONT=Arial]00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)[/FONT]
[FONT=Arial]00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)[/FONT]
[FONT=Arial]00:1d.7 USB controller: Intel Corporation NM10/ICH7
[/FONT][FONT=Arial]Family USB2 EHCI Controller (rev 01)[/FONT]
[FONT=Arial]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)[/FONT]
[FONT=Arial]00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)[/FONT]
[FONT=Arial]00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)[/FONT]
[FONT=Arial]00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 01)[/FONT]
[FONT=Arial]00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
[/FONT][FONT=Arial]06:00.0 Network controller: Broadcom Inc. and subsidiaries BCM4311 802.11b/g WLAN (rev 01)[/FONT]
[FONT=Arial]08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)

[/FONT]I am able to connect with my ethernet but not my wireless.

Any suggestions?
Thanks
[COLOR=#202124][FONT=Roboto][/FONT][/COLOR]

---

### Post by ajgreeny on 2021-03-11
You say Lubuntu 18.1 which together with the kernel version suggests to me that are on 18.10 which lost all support in Aug 2019.

You really must install a supported version of the OS of your choice if we are to try and help you as there is little of use to you that we can offer for an 18.10 installation.

I suggest you do a clean install of 20.04 after backing up all your personal files, which of course you do already, don't you?

---

### Post by tea for one on 2021-03-11
After you have installed a supported version and restored your data as suggested by [COLOR="#0000FF"]ajgreeny[/COLOR], you should then have a look at this information:-
[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by Toledoubf on 2021-03-14
It is an old 32 bit machine (Hp 500c). Is there any Linux OS that still supports 32 bit? If there is, where can I find it? I have 3 of them and would like to try Linux on them.

---

### Post by ajgreeny on 2021-03-14
Have a look at Debian 10 using either Lxde or Lxqt, if the latter is available.

The basic "structure" of it is very similar to the Ubuntu family, Ubuntu being based on Debian, of course, so the transfer should be relatively easy for you.

---

### Post by guiverc on 2021-03-14
Lubuntu 18.04 LTS is still supported ([https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)) and offers two ISOs for installation.

The alternate ISO is for boxes with <768MB of RAM, as the default ISO contains a *live* system (ie. *it loads & runs the OS as if installed all from RAM, and during operation there isn't enough free ram to also run the installer if you've less 768MB of RAM*).

The major drawback to it is it came with only 3 years of *full*-support, which ends 2021-April.

The base system will still get upgrades until 2023-April (5 years from release in 2018-April), however that includes only the packages from the 'main' repository of Ubuntu.  You can use `ubuntu-support-status` to view what gets five years of support, and what has only ~a month remaining.

The main alternative I'd suggest is Debian 10/Buster.

Boxes I used to test [Lubuntu 18.04.5 LTS]("https://lubuntu.me/bionic-5-released/") (which was released in 2020-August) are

- dell latitude d610 (pentium m, 1.5gb, intel i915)
- ibm thinkpad t43 (pentium m, 1.5gb ram, radeon x300)
- ibm thinkpad t42p (pentium m, 2gb ram, amd/ati mobility firegl t2; rv350/m10 gl)
- ibm thinkpad r50p (pentium m, 1gb ram, amd/ati mobility firegl t2; rv350/m10 gl)
- asus eepc 1000HE (intel atom n270, 1gb, intel mobile 945gse integrated), wireless RT2790
- hp d220mt (dr159p), (celeron 2ghz, 1gb (732mb useable), 82845G/GL Brookdale-G/GE (i915))
- hp dx6120mt (pentium 4, 3gb, winfast clone of nvidia 7600gt)

all of which are x86/i386 only (ie. 32-bit) being pentium M, pentium 4, early atom or the *celeron*.

FYI: The *celeron* box was horrid; but actually ran Lubuntu 18.04 LTS better than it did Debian Buster/10.   I test Debian too, so they'll have been used to test Debian Buster too (*non-free (all boxes) & free (some only) with XFCE, LXDE & LXQt; if I tested others I don't recall anymore as Debian 10 was released some time ago*)

---

### Post by ajgreeny on 2021-03-14
I see that's two suggesting Debian 10.

I have it on an old, 2011 I think, eePC equivalent, 32 bit Atom 270N with only 1G ram and it runs quite well as long as I don't try anything such as HD video.
I installed Lxde not Lxqt which is a bit heavier and I don't use Firefox or chromium which are also too big and heavy for that hardware; I use epiphany-browser instead which is fine for my use.
I installed "buster" but then later moved to "bullseye" by simply editing the /etc/apt/sources.list file and that went without problem and what I now have seems so like the Ubuntu family of OSs that it's almost indistinguishable from Lubuntu-20.04 but with Lxde not Lxqt.

---

### Post by guiverc on 2021-03-14
I find that interesting @ajgreeny, thank you.

> eePC equivalent, 32 bit Atom 270N with only 1G ram and it runs quite well as
> long as I don't try anything such as HD video.

In testing I'm doing the same thing over & over, and watching news/music.vids on youtube is a common test I use in a browser (small window, maximized, f11 & fullscreen)..   For Debian Buster I added I'd test non-free XFCE, LXQt, LXDE... then repeat using the free...  (*the streaming news or music.vids was usually left on so I had something to listen to as I continued testing*)

I have monthly bandwidth quotas, thus run tests in a low-medium-resolution anyway so I'd not noticed that the low-powered n270 doesn't like HD  (I'd not use HD for fear I'd reach my quota & drop to *dial-up* speeds (*no thank you! its horrific*)).  Could possibly be true of pentium M also.

Anyway thank you.   (*the eeepc I just recall it being a pain to get it to boot thumb-drives*)

---

### Post by tea for one on 2021-03-14
> **Toledoubf said:**
> It is an old 32 bit machine (Hp 500c). Is there any Linux OS that still supports 32 bit? If there is, where can I find it? I have 3 of them and would like to try Linux on them.

Possibly consider Antix

I'm pretty sure that Antix allows some Broadcom wifi devices to connect without too much effort.

[https://antixlinux.com/](https://antixlinux.com/)
[http://download.tuxfamily.org/antix/docs-antiX-19/FAQ/index.html](http://download.tuxfamily.org/antix/docs-antiX-19/FAQ/index.html)

---

### Post by Toledoubf on 2021-03-15
Thanks all! I'll look into your suggestions. I'm also going to try a usb wifi dongle to bypass the broadcom problem.

---

### Post by him610 on 2021-03-16
> **Toledoubf said:**
> It is an old 32 bit machine (Hp 500c). Is there any Linux OS that still supports 32 bit? If there is, where can I find it? I have 3 of them and would like to try Linux on them.

I have an Acer ZG5 netbook (circa 2008) which I recently installed 32bit Raspberry Pi Desktop for PC which is Debian with the PI desktop for PCs. It can be downloaded from this link, [https://www.raspberrypi.org/software/]("https://www.raspberrypi.org/software/")  Look for the heading, "Raspberry Pi Desktop for PC and Mac"

---


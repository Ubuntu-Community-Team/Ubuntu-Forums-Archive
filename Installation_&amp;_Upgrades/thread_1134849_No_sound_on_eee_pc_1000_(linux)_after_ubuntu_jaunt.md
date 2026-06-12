---
title: "No sound on eee pc 1000 (linux) after ubuntu jaunty install"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by YakaFett on 2009-04-24
Please help. I just installed jaunty nbr and I love it except one major problem - I got no sound!  I have had a similar problem on another PC and I was able to figure it by poking  around in the sound options. I have tried this on my eee pc 1000 to no avail. Anyone have any ideas?  I am a linux novice so please dumb it down for me.

Thanks to the great ubuntu community,

YakaFett:(

---

### Post by halovivek on 2009-04-24
Could you please post your system configuration? 
type this is in terminal and post result
lspci

---

### Post by john stiles on 2009-04-24
Hi,

Don't upgrade, reinstall.

I tried to upgrade to jaunty on my eeepc 1000 and hit several issues around the downgraded kernel I had installed. It installed and ran but not well...

I then downloaded the unr image and installed imagewriter and carried out a clean usb key install. Works flawlessly and the icing on the cake is it gives the option to import your old settings. Wireless, sound, touchpad, and old custom tweaks work straight out of the box. Congrats and thanks to team.

---

### Post by YakaFett on 2009-04-24
> **halovivek said:**
> Could you please post your system configuration? 
type this is in terminal and post result
lspci

Ok here it is:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: RaLink RT2860
04:00.0 Ethernet controller: Attansic Technology Corp. L1e Gigabit Ethernet Adapter (rev b0)

---

### Post by YakaFett on 2009-04-24
I did a fresh install.  Only thing is that it is a dual boot machine (for now) with xp.

---

### Post by MN Noob on 2009-04-27
Did you get any resolution on this?
I have similar issue. I have sound, but it is very quiet. I need to poke around a bit more, but I don't think there will be any option to make it any louder.
I am running the same machine, but will post later today the configuration if it is different.

---

### Post by isaaca on 2009-05-06
I recently upgraded my eee 1000H to jaunty from intrepid. I had been running the custom kernel for the eee, "2.6.27-8-eeepc". After the upgrade I had no sound. This problem seems to have been resolved by installing the generic ubuntu kernel "2.6.28-11-generic". I had previously installed the custom kernel for the eee to get wireless and wired internet driver support, but these things seem to be supported by the generic ubuntu kernel now. :)

---

### Post by sandwormblues on 2009-05-07
same problem on my laptop...intel 80821G ich7 rev 02 audio controller, no sound.  the "options snd-hda-intel model=3stack" trick doesn't work like it did with past kernel versions.

I'm upgrading from 2.6.28-11 to 2.6.30rc2 to fix my graphics acceleration.  we'll see if that changes anything in the sonic department.

---

### Post by chefin on 2009-05-07
I also have same problem with my 1000h, sound is very quiet.

---

### Post by paxmark1 on 2009-06-25
eee 900A on unr 9.10 alpha rc2   intel 82801g dropped rhythmbox and added mplayer and sound is nice, but could be louder.  mp3's and avi's

---

### Post by Divider on 2009-06-25
array.org has a custom eee kernel for full installations, check it out.

```
 http://array.org/ubuntu/
```

---

### Post by rsun on 2009-07-02
I have a somewhat similar problem too.
My original install of UNR that comes with Linux 2.6.28-11 kernel works fine until I upgraded to Linux 2.6.28-13 last week. This seem to be the problem with Ubuntu these days. For the last couple of years, I've experienced several kernel upgrade problems. The first install works fine until the next kernel upgrade. I now fear of upgrading to newer Linux kernels.
I used Ubuntu Linux to avoid the upgrade problem that comes as default with Microsoft OS. Now it's in Ubuntu. 
I have another machine running Mandriva, they don't seem to have this issue.

---

### Post by hurricanesfan66 on 2009-07-12
Ok...my case is slightly different.  I am running an eeePC 701 with UNR.  I did have sound initially after the fresh install.  Now, after prepping this to serve as an image for our school system's 150+ eeePCs (moving to UNR from stock Xandros), I have lost sound.  Here is my lspci:

fcstech@fcstech:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet Adapter (rev a0)

Appears to have a different sound card than the 900 series, obviously.

---


---
title: "Compaq CQ61 problems"
date: 2009-11-06
forum: Hardware
---

### Post by Gantlett on 2009-11-06
Hi everyone

Got a Compaq CQ61-117TU and it just doesn't like Linux.

With 9.04, I had two problems:
1. No sound
2. Computer wouldn't wake from sleep properly (had to kill it every time) 

With 9.10, oddly enough, things just got worse:
No video AT ALL - total black screen.

Tried OpenSuse 11.1 and Fedora 11, video works with both but locked to 640x480 / 800x600 with no acceleration and still no sound.

How do I get this lovely OS to work on my poor laptop? ](*,)

---

### Post by Gantlett on 2009-11-06
Well I tried a few more workarounds to get the display to work, but I'm stuck...

I installed Ubuntu Desktop 9.10 32-bit on my Vista using wubi. When I boot into Ubuntu I get a black screen, I don't even see the splash screen. I tried pressing ctrl-alt-f1 to get into terminal, but I still see s black screen - nothing happens. I tried this after choosing Recovery Mode in Grub as well - same results exactly.

If I change the runlevel manually before I actually boot into Ubuntu, by editing the /etc/inittab file from Windows, will that boot me into terminal? I tried browsing the C:\Ubuntu directory in Windows but I can't see the Ubuntu system files there...

What do I do??? :-(

---

### Post by Gantlett on 2009-11-06
Oh, if I could somehow enable SSH on Ubuntu I could control it. Problem is it's closed by default. Any way I can enable it from Windows..?

---

### Post by Gantlett on 2009-11-07
OK, it's starting to feel a bit weird to talk to myself here, but what the heck:

Installed 9.04, configured openssh-server, configured a wireless connection and upgraded to 9.10, hoping 9.10 has an update that fixes the video for my CQ61. 
Restarted after the upgrade process has completed, got a black screen as expected, no worries, connected through SSH to the machine and checked for updates. Alas, no updates are available!

So now I really am out of options...

---

### Post by Gantlett on 2009-11-08
Alright, thanks to the enormous help I got in this post (I still can't believe NO ONE bothered to post even one suggestion here) I found a solution. That solution is called Linux Mint 7, which is kinda like having 9.04 without the wake from sleep bug.

Video works OOTB, fixed sound by upgrading ALSA and the computer wakes from sleep without any problems (unlike 9.04 which simply doesn't wake at all).

Now I need to fix the built-in mic!

P.S.
Thanks again

---

### Post by jaie on 2010-01-14
I have exactly the same problem with two CQ61's that I recently bought. Neither of them have any video what so ever in karmic.

---

### Post by Sergio7676 on 2010-01-14
I have a CQ61 too and have problems but managed to solve everything. It would be helpful if you post a detailed hardware configuration list as there are different configurations for the CQ61. Having that I may be of some help.


Cheers!

Sergio

---

### Post by jaie on 2010-01-14
I dont know if this will help, I am currently running Jaunty (because not having video on Karmic isn't very productive). If i use the command "lspci" i get the following.

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by Sergio7676 on 2010-01-14
Unfortunately we do not have the same graphic card ( mine is an NVIDIA 103 M). The issues with my card were quite different and I am afraid that I am not familiar with the intel integrated card. On the other hand I found the solution for the sound here [http://ubuntuforums.org/showthread.php?p=7717667&highlight=compaq+cq61#post7717667](http://ubuntuforums.org/showthread.php?p=7717667&highlight=compaq+cq61#post7717667)

I hope it works for you!

Cheers

---


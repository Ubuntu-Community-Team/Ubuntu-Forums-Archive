---
title: "Problem With Onboard Sound"
date: 2005-02-21
forum: Hardware &amp; Laptops
---

### Post by zelda on 2005-02-21
Hey all!  I just installed Ubuntu a day ago and upgraded it to Hoary.  However, I am experiencing sound problems in so that I have not heard any sound come out from my speakers when I'm in my Linux partition.  I've tried opening common media files (*.ogg or whatnot) but got error messages instead.

After trying sudo alsamixer, it returned: alsamixer: function snd_ctl_open failed for default: No such file or directory.  

Another error I got was a popup during startup saying mixer element/device not found (or something to that extent).

I am using the onboard sound that comes with my GigaByte GA-8I915P Duo Pro 915P motherboard.  Please let me know how I can solve this problem I am having with sound.

Thank you guys so much :)

---

### Post by timefantom on 2005-02-22
[QUOTE=zelda]Hey all!  I just installed Ubuntu a day ago and upgraded it to Hoary.  However, I am experiencing sound problems in so that I have not heard any sound come out from my speakers when I'm in my Linux partition.  I've tried opening common media files (*.ogg or whatnot) but got error messages instead.

After trying sudo alsamixer, it returned: alsamixer: function snd_ctl_open failed for default: No such file or directory.  

Another error I got was a popup during startup saying mixer element/device not found (or something to that extent).

I am using the onboard sound that comes with my GigaByte GA-8I915P Duo Pro 915P motherboard.  Please let me know how I can solve this problem I am having with sound.

Thank you guys so much :)[/QUOTE]
 Hi all.
I am having a similar problem with a new SB-95P Shuttle I bought. I have the Intel 925X Chipset.
I am suspecting this is an issue to do with no support for the i9xx chipsets yet.
Does anyone know much about this?
Here is my lspci listing....

0000:00:00.0 Host bridge: Intel Corp. 925X Memory Controller Hub (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 925X PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5e4b
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5e6b
0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
0000:03:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by timefantom on 2005-02-24
Hi all again.

I have done a little reading, and I have found that the 9xx series sound is supported with the module azx which is in asla 1.0.8, but it seems the ubuntu packages don't ship this driver?
Does anyone know why it isn't shipped, or if they know how I can build it against a standard ubuntu kernel from the source.

Any help would be much appreciated.

---

### Post by zelda on 2005-03-01
Yes, I have researched and found that my onboard sound card C-Media 9880 is supported by Alsa drivers 1.08, but after I updated alsa-base, alsa-utils and so forth, I am still getting errors saying that certain elements and sound are not found.

It seems to me that Ubuntu has a large amount of problems in regards to users getting sound on their system.  Perhaps it's time to look into making sound an easily configurable element for n00b users like myself, with absolutely no knowledge of using Debian-based Linux OSs at all.

Anyway, does anyone know how to check if the system is actually detecting the presence of a sound card on the machine?  As I've installed the alsa-drivers 1.08 "manually" and I'm still getting no sound.

Thanks in advance!

---

### Post by jakeofnote on 2005-09-28
sorry about bringing this dead thread back to life, but was a sollution ever found?
i tried contacting zelda as i have the same motherb, but someone help me QUICK!!!

---

### Post by treebeardjrm on 2005-10-06
Intel High Definition Audio wasn't supported with a kernel module until 2.6.12 (perhaps a bit sooner, but not much).  So if you're using a kernel older than 2.6.12 (do uname -r to find out), you either need to upgrade the kernel, or download the kernel module from someplace else.  From what I hear, ALSA 1.0.9 or newer contains the proper module, called snd-hda-intel.  If you upgrade the kernel, you should just be able to reboot and use alsamixer to unmute the sound (it comes muted by default so you don't damage your ears).

If you go the 'updated ALSA' route, you'll have to do a 'modprobe snd-hda-intel' to load the proper driver.

As far as the 'Linux for n00b' users goes, if you're trying to learn about Linux, and actually care about it, then you're not a 'n00b.'  This name-calling stuff is one tradition that I wish would just die.

---


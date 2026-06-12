---
title: "ASUS p7p55 lx + core i5 instability"
date: 2010-03-05
forum: Hardware
---

### Post by PleegWat on 2010-03-05
Hi,

Two weeks ago I've done big system upgrade, and since then I've been having instability issues.

Old hardware:

ASUS P5LD2 mainboard
Intel Pentium D
2GB ram

New hardware:

Asus p7p55 LX mainboard
Intel Core i7
4GB ram

Hardware staying the same:
Nvidia 8800 GTX gpu
1x200 GB hard drive containing 2 partitions, one windows, one linux
3x1000 GB hard drives, software raid 5, ext4
600 watt PSU
Logitech G11 keyboard
Logitech MX518 mouse

It occasionally crashes while booting, without leaving any trace about the entire boot attempt in the logs. It also (more often) crashes while gaming (world of warcraft on wine). When it crashes from wow, I find long lists of kernel oopses in the /var/log/syslog, and I do not have a clue what those mean.

I'm booting with acpi=off noapic, this seems to reduce the crashing frequency. I've tried pnpbios=off (as one line in the bootup log suggests), but this makes things worse.

I've tested the disks with smart self-test, and the memory with memtest86, and found no errors.

Attached:
- Today's syslog (after the 2.6.31-20 kernel update)
- Yesterday's syslog (with the 2.6.31-19 kernel)
- Output of lspci
- Output of lsusb

---

### Post by hal8000 on 2010-06-27
Not sure if you have this fixed or not.

Have you tried just booting with a single HD thereby eliminating RAID setup?


If it still crashes, try booting from the live CD and no hard drives, this may prove software issues.
Hope that helps

---

### Post by PleegWat on 2010-06-28
I've been trying tons of things since I originally made that post. I've located at least 3 causes:

- My IDE chipset (Don't have the serial number available offhand, but made by VIA) isn't being detected properly or doesn't work properly. Booting without it works reasonable, with it it doesn't boot at all, even without any hard drives.
- My primary hard drive was suffering from bad sectors. I've since replaced it, which signficantly reduces the number of issues.
- The remaining problems disappeared when I cleaned my keyboard last week. I don't get that bit either. Didn't do any software updates over the change.

Since the issues seem to have disappeared, I haven't retried with the IDE chipset enabled yet. Might take a while till I get round to trying that, given the weather we're having here.

---

### Post by hal8000 on 2010-06-28
> **PleegWat said:**
> I've been trying tons of things since I originally made that post. I've located at least 3 causes:

- My IDE chipset (Don't have the serial number available offhand, but made by VIA) isn't being detected properly or doesn't work properly. Booting without it works reasonable, with it it doesn't boot at all, even without any hard drives.
- My primary hard drive was suffering from bad sectors. I've since replaced it, which signficantly reduces the number of issues.
- The remaining problems disappeared when I cleaned my keyboard last week. I don't get that bit either. Didn't do any software updates over the change.

Since the issues seem to have disappeared, I haven't retried with the IDE chipset enabled yet. Might take a while till I get round to trying that, given the weather we're having here.


AFAIK that board has an Intel chipset the P55 so should be detected ok by the linux kernel.
If this does have a VIA chipset how have you disabled it?

That motherboard most likely supports SATA II hard drives so one of these should be significantly faster than ordinary SATA.

Cleaned keyboard? Was this the connector or physical keys? Its possible a stuck key may have sent false signals.
Asus is great gear, so your hardware should run very well on linux.

---

### Post by PleegWat on 2010-06-29
Yeah, may have been a short on a key. I completely opened the keyboard up, and cleaned everything. I encountered some sticky substance which may have been spilled fruit juice, and which had managed to get past the spill protection in the keyboard.

The board does indeed have an intel P55 chipset. However, the P55 does not contain any IDE (PATA) ports. The board contains a separate chip that provides a PATA port. I've got my cd-rom drive attached to that.

Since the IDE chip is just a completely optional component attached to a PCIe channel, it can be disabled from the bios.

---

### Post by RJARRRPCGP on 2010-06-29
Reset the CMOS and make sure the Vcore is set right. Your symptoms don't sound keyboard-related.

---

### Post by hal8000 on 2010-06-30
OK, did some more digging the Asus P7P55D-E (very similar to your board ) is listed on the Debian HCL list:


[http://kmuto.jp/debian/hcl/ASUS/P7P55D-E](http://kmuto.jp/debian/hcl/ASUS/P7P55D-E)

It looks as though all these boards use Via 1828S for onboard sound
and Via VT6830P for firewire.

Post an output of lspci
if you still have problems. I am building a new computer in a few weeks
and Asus P7P55 D-E and i5 750   will be my prime choice for motherboard and CPU

---

### Post by dino99 on 2010-06-30
check your bios and select ahci mode

note that old settings often brings issues, so backup or rename everything about gnome (.gnome2, .gconf, ...) then delete them and reboot

---

### Post by piko7 on 2010-07-02
> **PleegWat said:**
> Hi,
Asus p7p55 LX mainboard
...
It occasionally crashes while booting

I had the same problem on the same hardware untill replacing my IDE DVD-RW with SATA DVD-RW.

---

### Post by PleegWat on 2010-07-04
> **piko7 said:**
> I had the same problem on the same hardware untill replacing my IDE DVD-RW with SATA DVD-RW.

I've seen the same, disabling the IDE controller. Probably that controller is not correctly supported, but I don't really feel tempted to look into it deeper. I'll just do what you did one of these days and buy a SATA dvd-rw.

I'm also 99% certain I've found the real cause of the keyboard-related crashes: A bug in the way g15daemon uses libusb. It's quite possible I'll be submitting patches for that to g15daemon.

---

### Post by RJARRRPCGP on 2010-07-08
> **piko7 said:**
> I had the same problem on the same hardware untill replacing my IDE DVD-RW with SATA DVD-RW.

Even when I don't have that problem with the PATA IDE controller on my Asus P5QL Pro, the PATA IDE controller appears to have compatibility issues! 

Most distros will give up if you're trying to install a distro from an optical drive connected to the PATA IDE controller! 

They will falsely claim a file wasn't found or refuse to acknowledge a CD or DVD exists.

Thus, I agree with disabling the PATA controller and using SATA only!

Most Linux distros seem to be fine with the SATA controller.

---

### Post by ojuano on 2010-09-03
Try my solution. It worked for me as far as the unstable booting goes.

[http://ubuntuforums.org/showthread.php?t=1567023&highlight=ASUS+P7P55D](http://ubuntuforums.org/showthread.php?t=1567023&highlight=ASUS+P7P55D)

---

### Post by TheBuzzSaw on 2010-10-26
I am having this exact problem.

ASUS P7P55 LX + Core i5 processor

I have no IDE devices. I've switched the BIOS to AHCI and reinstalled everything. Windows 7 is happy, but Ubuntu hates booting. It is fairly consistent in alternating (successful boot, failed boot, etc.).

Help? :(

---

### Post by smx-smx on 2010-12-18
I'm having the same problem, even with the lastest BIOS (revision 1101) and the lastest kernel. If i disable the graphic boot i can see the boot process hanging at ATA devices scanning, and the lastest line contains the name of my 2 dvd drives.

If i insist in rebooting (5 or more times) sometimes it boots and dvd drives works, but if i disable the IDE Controller (VIA PCIE2IDE OPROM) it just boots fine.

Someone should report this as a kernel bug, i think

---


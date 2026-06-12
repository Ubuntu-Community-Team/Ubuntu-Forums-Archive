---
title: "Ubuntu won't boot from flash drive (stuck on boot device select)"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by max.goedjen on 2009-03-17
Hey guys,
Having a bit of an issue. I have Ubuntu 8.10 on one of my computers, and am using the boot drive creation tool that comes with it. I picked up a 16GB Sandisk Cruzer micro, and removed U3 (their packaged apps) from it. I then downloaded an ISO of Ubuntu 8.10, and apparently successfully ran the utility. However, when I try to go to a PC and boot from it, (tried this on 2 PCs, both Dells), I select USB from the boot device list, and nothing happens. Anyone know what could be causing this?

---

### Post by PenguinsFan on 2009-03-17
This may be a little tricky to figure out without any actual messages.... I guess I'd try two things:

1) Turn off any other USB Devices! I've have problems in the past there having other USB devices like external hard drives, etc, powered on during boot would cause issues like this. For me, my system would get confused and try to boot from the wrong device.

2) Instead of having your system present you with a boot menu, enter your system bios (usually F1, or Delete on system startup) and tell it to boot from USB first

---

### Post by max.goedjen on 2009-03-17
PenguinsFan
That's what I'm doing right now, is rebooting and holding the key (F12 in my case) to get to the boot select list (BIOS doesn't seem to want to let me boot just from USB). All other USB devices are unplugged.

---

### Post by max.goedjen on 2009-03-17
I have successfully booted it from a Toshiba Satellite laptop, but still no luck with the Dell systems. Any ideas?

---

### Post by max.goedjen on 2009-03-17
Also note that these systems have successfully booted from an older Fedora Live USB stick, so I believe the problem, at least in part, lies with the Ubuntu installation.

---

### Post by max.goedjen on 2009-03-18
Update:
So, I had been thinking that it might have been something with the flash drive (it came preinstalled with some software (U3) that I thought may have been preventing it from booting. I just installed Fedora on the drive to see if it would work, and it did. So, as far as I can tell, the problem lies somewhere with Dell and Ubuntu. Any ideas?

---

### Post by Sir_Tom on 2009-03-19
Your can create a USB Boot with UNetbootin.

It worked on a 4GB and a 8GB that failed when I used the built-in Ubuntu USB boot tool.

If you in a Windows environment download this 
[http://sourceforge.net/project/downloading.php?group_id=222386&use_mirror=superb-west&filename=unetbootin-windows-319.exe&a=12477670](http://sourceforge.net/project/downloading.php?group_id=222386&use_mirror=superb-west&filename=unetbootin-windows-319.exe&a=12477670)

It will allow you to make the USB boot stick from the Ubuntu iso.

If you going to run it from Linux 
Try this or search Sourceforge for the last version.
[http://sourceforge.net/project/downloading.php?groupname=unetbootin&filename=unetbootin-linux-319&use_mirror=superb-east](http://sourceforge.net/project/downloading.php?groupname=unetbootin&filename=unetbootin-linux-319&use_mirror=superb-east)
 
UNetbootin - Homepage and Downloads
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
(Don't download the Window installer from here.  It errors out when you run it, use the link above)

The current version has built-in support for automatically downloading and loading the following distributions, though installing other distributions is also supported:

Ubuntu (and official derivatives)
6.06 LTS 
6.10 
7.04 
7.10 
8.04 LTS 
8.10 
Daily CD Images 
Debian
Stable/Etch 
Testing/Lenny 
Unstable/Sid 
Linux Mint
3.1 
4.0 
5-r1 
6 
openSUSE
10.2 
10.3 
11.0 
11.1 
Factory 
Arch Linux
2007.08 
Damn Small Linux
4.4 
SliTaz
Stable 
Cooking 
Puppy Linux
4.00 
gNewSense
deltah-2.1 
FreeBSD
6.3 
7.0 
NetBSD
4.0 
Fedora
7 
8 
9 
10 
Rawhide 
PCLinuxOS
2007 
2008 
Sabayon Linux
4-LiteMCE 
Gentoo
2007.0 
2008.0 
MEPIS
SimplyMEPIS 8 
AntiX 8 
Zenwalk
5.2 
Slax
6 
Dreamlinux
3.2 
Elive
Development 
CentOS
4 
5 
Mandriva
2007.1 
2008.0 
2008.1 
FaunOS
0.5.4 
Frugalware Linux
Stable 
Testing 
Current

---


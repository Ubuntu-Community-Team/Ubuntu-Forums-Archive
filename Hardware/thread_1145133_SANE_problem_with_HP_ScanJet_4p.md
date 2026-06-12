---
title: "SANE problem with HP ScanJet 4p"
date: 2009-05-01
forum: Hardware
---

### Post by David Brant on 2009-05-01
Hello

I would dearly like to get my Hewlet Packard ScanJet 4p (SCSI) working under ubuntu, but Xsane Image Scanner returns "No devices available'.

I have tried several approaches from the web:

[http://it.toolbox.com/blogs/locutus/make-the-linux-kernel-recognise-a-scsi-device-22410](http://it.toolbox.com/blogs/locutus/make-the-linux-kernel-recognise-a-scsi-device-22410)
[http://ubuntuforums.org/showthread.php?t=11718](http://ubuntuforums.org/showthread.php?t=11718)

The SCSI card i use is an Adaptec AVA-2904 PCI-to-Fast SCSI Host Adapter (7800 Family) which i assume presents no problem to the Linux Kernel as it was recognised during the original ubuntu 8.10 installation.

According to the SANE Supported Devices List ([http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)), this combination is 'completely' supported with the sane-hp manual backend.

I have tried to manually install it, by installing libsane-extras and editing /etc/sane.d/dll.conf, but the "hp" reference to the SANE dynamic backend loader is already active.

```
# /etc/sane.d/dll.conf - Configuration file for the SANE dynamic backend loader
#
# On Debian systems, the dll backend will also look for pieces of configuration
# in the /etc/sane.d/dll.d directory -- packages providing backends should drop
# a config file similar to dll.conf in this directory.
#

# enable the next line if you want to allow access through the network:
net
abaton
agfafocus
apple
avision
artec
artec_eplus48u
as6e
bh
canon
canon630u
#canon_pp
cardscan
coolscan
coolscan2
#dc25
#dc210
#dc240
dell1600n_net
dmc
epjitsu
epson
epson2
fujitsu
#gphoto2
genesys
gt68xx
**[COLOR="Red"]hp[/COLOR]**
hp3900
hpsj5s
hp3500
hp4200
hp5400
hp5590
hpljm1005
hs2p
ibm
leo
lexmark
ma1509
matsushita
microtek
microtek2
mustek
#mustek_pp
mustek_usb
mustek_usb2
nec
niash
pie
pixma
plustek
#plustek_pp
#pnm
qcam
ricoh
s9036
sceptre
sharp
sm3600
sm3840
snapscan
sp15c
#st400
#stv680
tamarack
teco1
teco2
teco3
#test
u12
umax
#umax_pp
umax1220u
v4l

```

Could anybody please advise me as to what to try next.

Dave

---

### Post by David Brant on 2009-05-08
Trying a little more using SANE i get the following

```
david@david-desktop:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

found SCSI processor "HP C1130A 3614" at /dev/sg2
  # Your SCSI scanner was detected. It may or may not be supported by SANE. Try
  # scanimage -L and read the backend's manpage.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
```

and as the SANE output suggests

```
david@david-desktop:~$ sudo scanimage -L

device `hp:/dev/sg2' is a Hewlett-Packard C1130A flatbed scanner
```

Surely this means SANE detects my scanner.

A little more testing from the web gives

```
david@david-desktop:~$ udevinfo -a -p /sys/class/scsi_generic/sg2

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:0d.0/host2/target2:0:2/2:0:2:0/scsi_generic/sg2':
    KERNEL=="sg2"
    SUBSYSTEM=="scsi_generic"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:0d.0/host2/target2:0:2/2:0:2:0/scsi_generic':
    KERNELS=="scsi_generic"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0d.0/host2/target2:0:2/2:0:2:0':
    KERNELS=="2:0:2:0"
    SUBSYSTEMS=="scsi"
    DRIVERS==""
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="3"
    ATTRS{scsi_level}=="3"
    ATTRS{vendor}=="HP      "
    ATTRS{model}=="C1130A          "
    ATTRS{rev}=="3614"
    ATTRS{state}=="running"
    ATTRS{timeout}=="0"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x185"
    ATTRS{iodone_cnt}=="0x185"
    ATTRS{ioerr_cnt}=="0x1"
    ATTRS{modalias}=="scsi:t-0x03"
    ATTRS{evt_media_change}=="0"
    ATTRS{queue_depth}=="2"
    ATTRS{queue_type}=="none"

  looking at parent device '/devices/pci0000:00/0000:00:0d.0/host2/target2:0:2':
    KERNELS=="target2:0:2"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0d.0/host2':
    KERNELS=="host2"
    SUBSYSTEMS=="scsi"
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0d.0':
    KERNELS=="0000:00:0d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="aic7xxx"
    ATTRS{vendor}=="0x9004"
    ATTRS{device}=="0x5078"
    ATTRS{subsystem_vendor}=="0x9004"
    ATTRS{subsystem_device}=="0x7850"
    ATTRS{class}=="0x010000"
    ATTRS{irq}=="11"
    ATTRS{local_cpus}=="ffffffff,ffffffff"
    ATTRS{local_cpulist}=="0-63"
    ATTRS{modalias}=="pci:v00009004d00005078sv00009004sd00007850bc01sc00i00"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```
and finally

```
david@david-desktop:~$ cat /proc/scsi/scsi
Attached devices:
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: IBM-DTTA-371010  Rev: T77O
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: SONY     Model: CD-ROM CDU701    Rev: 1.0f
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 02 Lun: 00
  Vendor: HP       Model: C1130A           Rev: 3614
  Type:   Processor                        ANSI  SCSI revision: 02

```
My scanner happens to be set to address 2 which is correctly detected.

As far as i can tell, the Linux Kernel detects and talks to the scanner via the SCSI interface.

So why does it not appear to be supported and detected by XSane?

It should be supported according to ([http://www.sane-project.org/sane-mfg...EWLETT-PACKARD](http://www.sane-project.org/sane-mfg...EWLETT-PACKARD)). 

This is beginning to drive me insane!

---

### Post by Philk on 2009-05-11
David,

If you're still using Intrepid, you need to go into "System", "Users and Groups" and modify your permissions.  Scanning is not allowed by default.

I'm having the same problem you are, now that I've upgraded to Jaunty.  My Intrepid scanning still works, with the fix I noted above.  Other than my path to my HP ScanJet 4p being "sg8", our various responses are similar.  Jaunty doesn't have the same permissions set - no scanning group. [I found one may add a "scanner" group in Jaunty, but it makes no difference.  One may also change authorizations - again, no difference.]

If you've found a fix in the meantime, please note it.

Phil

---

### Post by Philk on 2009-05-11
David,

I now have my scanner working!

I had done the changes mentioned in my previous reply above.  I finally tried the two lines below (modified to my sg8 - you would modify to your sg2) from the "sane-scsi.5" MAN:
             $ chgrp scanner /dev/sg0
             $ chmod 660 /dev/sg0

I had also placed a line: "/dev/sg8" [without the quotes] in my hp.conf file in /etc/sane.d.  After I did that, I saw no difference.  I left it there, though - suggested somewhere on the sane homepage.  May or may not make any difference in my eventual solution.

Hope these changes, modified for your "sg2", will get you going.

I'm a happy camper (and in line with your earlier comment much more sane)!

Phil :guitar:

---

### Post by David Brant on 2009-05-13
Phil

Great to hear you got your scanner working. It's nice to know there is still actually someone out there with the same piece of quality built kit, albeit dated.

Reading your first post, strange thing is i had already enabled the default no-scanning user privileges beforehand in Intrepid prior to the whole saga.

In the meantime, I too got things working, but again for puzzling reasons :confused:

Inquires via (sane-devel) forum

[http://lists.alioth.debian.org/pipermail/sane-devel/2009-May/024692.html](http://lists.alioth.debian.org/pipermail/sane-devel/2009-May/024692.html)

Following their instructions using (scanimage --help) I was non the wiser to a possible solution. Finally typing (scanimage > image.pnm) i was slightly surprised to find using GIMP a lineart scanned image in my (/home/'username') folder. Thinking i was stuck with a command line scanner of limited flexibility, I fortuitously clicked on Xsane and ... it kicked in! :)

Inquiring further why this occured

[http://lists.alioth.debian.org/pipermail/sane-devel/2009-May/024701.html](http://lists.alioth.debian.org/pipermail/sane-devel/2009-May/024701.html)

was informed it was probably a driver issue, which may be impossible to debug unless i could reliably reproduce the problem!

Dunno if this possible "driver issue" is particular to the SCSI card i use (probably different to you?). I did notice something in (/var/log/kernel.log), but this is way above my head and needs a more informed person to deduce if the answer lies somewhere within it. For me the scanner now works ... or at least until i update to Jaunty! 

This brings me to two aspects in your second post.

1: my "edited" (/usr/share/man/man5/sane-scsi.5) lies within a compressed gz file. Was this the same in your case before you replaced the 2 key lines with sg"X" ?

```
(etc)
$ chgrp scanner /dev/sg0
(etc)
$ chmod 660 /dev/sg0
(etc)
```

2: my (/etc/sane.d/hp.conf) has

```
scsi HP
# Uncomment the following if you have "Error during device I/O" on SCSI
#   option dumb-read
#
# The usual place for a SCSI-scanner on Linux
/dev/scanner
#
# USB-scanners supported by the hp-backend
# HP ScanJet 4100C
usb 0x03f0 0x0101
# HP ScanJet 5200C
usb 0x03f0 0x0401
# HP ScanJet 62X0C
usb 0x03f0 0x0201
# HP ScanJet 63X0C
usb 0x03f0 0x0601
#
# Uncomment the following if your scanner is connected by USB,
# but you are not using libusb
# /dev/usb/scanner0
#   option connect-device

```
You also replaced the line /dev/scanner with /dev/sg"X" with no effect, but for consistency if nothing else?

Both your suggestions are similar to what has been recommended

[http://lists.alioth.debian.org/pipermail/sane-devel/2009-May/024697.html](http://lists.alioth.debian.org/pipermail/sane-devel/2009-May/024697.html)

I'd just like to be clear on these points in case i come up against this problem in the future :popcorn:

The world moves in mysterious ways

Dave

---

### Post by Philk on 2009-05-15
Dave,

I'm glad you have at least limited use of your scanner.  As you said, it is quality.

On the first point you raised, the man[ual] pages, in the same place on my Jaunty x64 version as you reported in your Intrepid version, are compressed.  However, I didn't edit those pages, I simply entered those two commands in a terminal window.  Those let the system reset the scanner group and its permissions.

On the second point, I did NOT get rid of the "/dev/scanner" line in file hp.conf.  Following that line, I appended a comment line and one reading "/dev/sg8".  So I ended up with:

scsi HP
# Uncomment the following if you have "Error during device I/O" on SCSI
#   option dumb-read
#
# The usual place for a SCSI-scanner on Linux
/dev/scanner
#
/dev/sg8
#
...etc.

I hope those suggestions can help you.

My SCSI card is one I've brought forward through several intervening computers, but I don't think it's the one I originally got with my 4p. I believe that one flaked out after a few years.  The one I have is one for a PCI slot and my current motherboard has two such - I made sure before buying it.  I'm not sure how much longer the older PCI slots will still be around.  Maybe I'll have to upgrade my SCSI card before too many more iterations.  I'm holding on to the p4, though, as long as I can run it.

Especially now that the trusty HP is working, all my initial reservations about Jaunty have disappeared.  It seems to take much better and more efficient advantage of the hardware I have.

Good luck with the continuing saga,
Phil

---

### Post by jhansonxi on 2009-08-15
> **Philk said:**
> David,
             $ chgrp scanner /dev/sg0
             $ chmod 660 /dev/sg0

Phil

The correct solution is to make a local udev rule to automatically set the permissions.  I just did this with a HP ScanJet 6100C.  **[Read my blog]("http://jhansonxi.blogspot.com/2009/08/writing-udev-rules-to-get-scsi-scanner.html")** for a quick HOWTO.

---

### Post by Philk on 2009-10-27
Thank you for that more lasting and more elegant solution to the scsi scanner problem in Ubuntu!

A very well-written HOW-TO, also.

Phil

---


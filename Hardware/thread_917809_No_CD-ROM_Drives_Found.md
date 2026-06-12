---
title: "No CD-ROM Drives Found"
date: 2008-09-12
forum: Hardware
---

### Post by Nopposan on 2008-09-12
Hello all.  'Working on this same old Dell that I had trouble getting the display resolution for the old graphics card.

New problem:

There was an old CD-ROM in this machine that did not work at all, although I checked and it was connected.  There is also a CD-Reader-Writer drive that did work fine, and that's the one I used to install Ubuntu 8.04 i386.
After the install, I actually used this same CD-Writer to burn another CD, so I know it works.  Then I unplugged the computer and swapped out the old non-functional CD-ROM with a new DVD-ROM.  After I did that, the following symptoms began.

I could not use either optical drive.
When I put an audio CD in the CD-Writer drive the "Audio CD-Extractor" fails to find the CD and displays a message "No CD-ROM Drives Found".
When I put a disk-mounter onto my Gnome panel, two CD drives show up, but neither will mount; when I select one and choose "Mount CD-ROM 1" I get the message "Unable to mount selected volume.  mount: special device /dev/scd1 does not exist".

So, I removed the DVD-ROM that I'd stuck in there mostly to fill the empty space anyhow, but the problems remain.
'Tried reinstalling udev as a shot in the dark, but to no avail.

Curiously, my lspci output seems not to list the CD-ROM.  Also, if I try to boot the Ubuntu Live CD that I used to install the OS, the CD-ROM is completely ignored even though it's the first boot device in the BIOS' boot menu.

Here's lspci anyway, just in case:
```
linuxuser@linuxuser-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0d.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 Multimedia audio controller: Aureal Semiconductor Vortex 2 (rev fe)
01:00.0 VGA compatible controller: NVidia / SGS Thomson (Joint Venture) Riva128 (rev 10)
```

And, here's the contents of fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5a3548ae-6e8f-43d9-8704-6d081a6eac4b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=af38cf55-f53a-4e19-83c0-592e00b18795 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,auto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,auto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Here's the contents of /etc/udev/rules.d/30-cdrom_id.rules:
```
# import optical drive properties

KERNEL=="sr[0-9]*|hd[a-z]|pcd[0-9]*", IMPORT{program}="cdrom_id --export $tempnode"
```
Please help me to solve this problem if you can.  All of your help is greatly appreciated.

Cheers!

---

### Post by prshah on 2008-09-12
> **Nopposan said:**
> 
After the install, I actually used this same CD-Writer to burn another CD, so I know it works.  Then I unplugged the computer and swapped out the old non-functional CD-ROM with a new DVD-ROM.  After I did that, 

I could not use either optical drive.

 the message "Unable to mount selected volume.  mount: special device /dev/scd1 does not exist".


When you put two or more drives on the same "channel", one has to be master, and the other slave; and the cable has to be connected in a particular order.

Put back your DVD drive; But first, make sure it's set as Master. (Look at the back of the drive for jumpers, small plastic tabs, and set it in the "MA" position).

Change your CD writer to slave (Set jumper on back to "SL").

You should not let any jumper remain on "CS".

If you have an 80 wire cable (Stiff, 3 colored connectors) then connect blue to the motherboard, Grey to the slave and Black to the master.

If you have a 40 wire cable (Limp, same colored connectors), connect the most distant one to the motherboard, the middle to master and end to slave.

Post back if you need more help,

---

### Post by Nopposan on 2008-09-12
Excellent!

Problem solved.  Thank you, PRshah.

I decided to use the DVD-ROM in another machine, but changing the jumper to "MA" on the CD-ROM did the trick.  I'll try to remember that for next time.

Goodbye for now.

---


---
title: "Hardware installation questions"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by denzilla on 2005-04-13
I added a DVD-Rom and a floppy drive to my Ubuntu box today and I can see the new hardware in the Device manager, but they aren't shown in places-computer. It only shows the CD-RW and HDD I already had. How can I make Ubuntu add my new hardware to places-computer? 

Next question is how can I install my network printer on ubuntu? Its an HP deskjet 656c. 

Thanks all

---

### Post by hagman on 2005-04-14
Hi,

- Add your new drives to your /etc/fstab like:
> /dev/hdx        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fdx        /media/floppy0  auto    rw,user,noauto  0       0
- Change the devices to match your configuration, e.g. /dev/hdd, /dev/fd0.
- Create the directories in /media, e.g. /media/cdrom1, /media/floppy0.
- Reboot.

Printer:
How is the printer connected (Network, SMB/Windows-Share, CUPS)?
If your printer has a network interface, use the HP JetDirect connection type and set the printer's IP address, e. g. 192.168.1.100.

Cheers,

Helge

---

### Post by denzilla on 2005-04-14
Its connected to my main rig (XP) and shared with other computers in the house. This is the only linux box (for now :) )

---

### Post by hagman on 2005-04-14
Ok. Now we have the network printer type.
You can add this printer by choosing System -> Administration -> Printers -> Add new printer -> Choose network printer -> Windows printer:


Fill the input fields:

Computer: The IP address or hostname your printer is connected (use the IP address until you have the appropriate entry in your /etc/hosts)
Printer: The Windows printer name
User: Your Windows user name
Password: Your Windows user password

Then choose the printer driver and finish the installation... that's it.

Cheers,

Helge

---

### Post by denzilla on 2005-04-14
[QUOTE=hagman]Hi,

- Add your new drives to your /etc/fstab like:

- Change the devices to match your configuration, e.g. /dev/hdd, /dev/fd0.
- Create the directories in /media, e.g. /media/cdrom1, /media/floppy0.
- Reboot.

Printer:
How is the printer connected (Network, SMB/Windows-Share, CUPS)?
If your printer has a network interface, use the HP JetDirect connection type and set the printer's IP address, e. g. 192.168.1.100.

Cheers,

Helge[/QUOTE]


Okay, I got the printer going. Much easier than I expected :)

About adding the DVD ROM shouldn't it be dvdrom1 instead of cdrom1 in the fstab config, or does it matter? 

Someone in another forum said that "Hal" or something should've added them automatically. Is that true?

---

### Post by hagman on 2005-04-15
Well, the name doesn't really matter. It may help you to identify the driver if you have more than one. You can rename it if you like.

The automatic hardware detection should add the drives automatically, but that doesn't always work perfectly.

Cheers,

Helge

---

### Post by denzilla on 2005-04-15
If I copy the CD rom fstab info, like you have, it adds another CD-RW to the listing. this is just a DVD-ROM. Here is the current fstab without the DVD-rom added.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


*UPDATE*  I added this and it worked:

/dev/hdd        /media/dvdrom0  udf,iso9660 ro,user,noauto  0   0

I assume since the drive now works, Its correct? Does both a cd-rom and dvd-rom use udf,iso9660?

---

### Post by hagman on 2005-04-15
Your settings are correct. Normally, only DVDs use the UDF (Universal Disc Format). CD-ROMs commonly use the iso9660 file system. By saying "udf, iso9660" you allow both drives to handle udf and iso9660 formats, that's okay.

Cheers,

Helge

---

### Post by denzilla on 2005-04-15
Thanks for your help :)

---


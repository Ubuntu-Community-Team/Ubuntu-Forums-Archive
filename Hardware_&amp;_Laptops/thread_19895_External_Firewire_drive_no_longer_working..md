---
title: "External Firewire drive no longer working."
date: 2005-03-14
forum: Hardware &amp; Laptops
---

### Post by dougr on 2005-03-14
I was running Warty, and my firewire drive was running fine.  Only problem is when I was trying to delete some files from it, they seemed stuck in the recycling bin.  I could not empty the recycling bin because some of the files were locked.  The only thing I did was did a chmod on /media/sda1 and some of the sub folders in order to try and get permission to delete the files.  It did work, but ever since then the drive has no longer mounted when I plug it in. It no longer even shows up in the devices section.  I tried to change the permissions back on sda1, but since that module no longer shows up in /dev since the drive is not recognized, I cannot seem to change permissions.  I don't know if that is for sure what changed things, but it's the last thing I did before it no longer worked.  

I then upgraded to Hoary hoping that may change things, but it is still the same.

Odd thing is my firewire ipod mounts just fine and works, and my usb palm works as well.  It's just this firewire HDD that does not work. Also it does work on other computers, so I know it's not the drive.

Any idea what I can do?

Thank You.
Doug

---

### Post by dougr on 2005-03-15
just a bump...anyone?

---

### Post by alastair on 2005-03-15
Boot the computer WITH the HDD connected.

Look at the logs :

sudo gedit /var/log/syslog

Look for firewire or disk messages - warnings, errors etc.

Then, also try booting WITHOUT the HDD connected. Log in.

Open a terminal and :

sudo tail -f /var/log/syslog

(this shows messages in the syslog log file as they are written).

Plug in the HDD - watch for messages. Anything?

---

### Post by dougr on 2005-03-15
I will check those when I get home, and post back.

I did check Dmesg, and I do get some sort of error, but I cannot remember what it is.  It was something about not being able to be root holder or something.  I will check it as well again, and post the exact message.

Thanks!

---

### Post by dougr on 2005-03-15
Ok first, the error in Dmesg says.  

ieee1394: The root node is not cycle master compable, selecting a new root node and resetting....

I checked the log you mentioned, and when I plug the drive in, nothing happens :(

---

### Post by dougr on 2005-03-15
out of curiosity I booted the hoary cd, and tried to install hoary to the firewire drive.  Sure enough the installer saw the disk and formatted it and all that.  I was hoping if I reformatted it, it would pick up in my install.  I let it format then booted into hoary, the story is still the same.

What I think initially happened is this.  I brought the disk home, that is factory formatted fat32 160GB.  I plugged it into a windows machine.  Since windows will only recognize FAT32 up to 32GB, I think it screwed something up when I plugged it into the windows drive.  Because it is ever since then that it has not worked.

---

### Post by dougr on 2005-03-15
Just formatted the drive NTFS on a windows XP machine.  Sure enough I plugged it into my ubuntu laptop and it picked up.  Of course I cannot write to it at this point, but it works.  I guess I can go from here.

---

### Post by dougr on 2005-03-15
Another update.  I just formatted the drive in ubuntu back to FAT32, and now I can copy files to it, and all is well in the world...weird crap.  I sure had to take the long way around.  I wonder now if I plug it back into the XP machine if the same thing will happen.

---

### Post by dougr on 2005-03-15
Now I just rebooted my hoary laptop, and it is doing the same freakin thing!!! Gah!

---

### Post by alastair on 2005-03-16
Look at the logs again - and "tail" of the syslog when you plug it in. I don't think it has anything to do with the filesystem etc. but a problem seeing the device.

Firewire is (as far as I know) still problematic on Linux, especially 2.6 kernels. IT can be hit or miss.

---

### Post by mathiasv on 2005-04-17
Hi.

I don't no how to get to read my firewire harddrive either. As a newbie the output from dmesg did not help me any further, but maybe it makes sense to some of you guys:

```
eth0: no IPv6 routers present
ieee1394: Node added: ID:BUS[0-01:1023]  GUID[00d04b0003084008]
ieee1394: The root node is not cycle master capable; selecting a new root node and resetting...
ieee1394: Node changed: 0-01:1023 -> 0-00:1023
ieee1394: Node changed: 0-00:1023 -> 0-01:1023
scsi0 : SCSI emulation for IEEE-1394 SBP-2 Devices
ieee1394: sbp2: Logged into SBP-2 device
ieee1394: Node 0-00:1023: Max speed [S400] - Max payload [2048]
  Vendor: IBM-DPTA  Model: -353750           Rev:
  Type:   Direct-Access                      ANSI SCSI revision: 02
SCSI device sda: 73261440 512-byte hdwr sectors (37510 MB)
sda: cache data unavailable
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: p1
Attached scsi disk sda at scsi0, channel 0, id 0, lun 0

```

Does anyone know of a good introduction to this storage device (fstab, mtab, mount, umount etc.) thing?

Thanks. 
Mathias

---

### Post by mathiasv on 2005-05-03
Got it working by re-reading the modules ieee1394, ohci1394 and sbp2 plus ntfs. It works fine with ext3

---

### Post by jon21 on 2005-05-11
What do you mean by "re-reading" the modules?

---

### Post by steamedpenguin on 2005-06-18
[QUOTE=jon21]What do you mean by "re-reading" the modules?[/QUOTE]
 *code:*

$ sudo su -

# rmmod ohci1394
# rmmod sbp2
# rmmod ieee1394
# modprobe ohci1394
# modprobe sbp2
# modprobe ieee1394

Now plug in your firewire drive and it should work. For further testing I removed the firewire drive again and the desktop icons dissappeared, then returned when I plugged the firewire drive back in.

While I am at it I'll recommend the Bytecc harddrive, CD/DVD enclosures. You can plop any IDE hard drive in there (up to 300 GB for the latest ones), and you can put a CD/DVD drive in there.

You can get the USB2 enclosure for around 25 USD, or the USB2 and firewire option for 38 USD. The clincher for me is that the power cable is a regular computer power cable not one of those funky special power interfaces. So no accidentally twisting off your power interface or ruining your power cable. Last plus: they are stackable.

My plan for the future is to get two more enclosures, one for my CDRW and one for my DVD player and run all my disks off my PCI firewire card.

peace, linux, love, and kicking ass!

---


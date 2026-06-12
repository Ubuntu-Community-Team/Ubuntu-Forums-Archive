---
title: "Problem mounting external hdd"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by SteveHoffmanUK on 2006-07-07
Newbie here.

Plugged in a newly-bought Freecom FHD-2 Pro 80GB external hard disk. It wasn't picked up automatically, so am wrestling with mounting it.

Following instructions from an earlier thread for Warty, I typed this into terminal:

```
fdisk -l
```
and got this:
```
Disk /dev/sda: 519 MB, 519045120 bytes
32 heads, 32 sectors/track, 990 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         990      506863+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(988, 31, 32) logical=(989, 31, 31)
```

So far, so good, I think. So it's /dev/sda1 

Then I create a directory for it and give it the name 'externalhdd':

```
$sudo mkdir /mnt/externalhdd 
```

Seems to accept that OK. So then I try to mount it, with ```
mnt -tvfat /dev/sda1 mnt/externalhdd
``` 
and this is what I get:
```
steve@steve-desktop:~$ mnt -tvfat/dev/sda1 mnt/externalhdd
bash: mnt: command not found

```

What am I doing wrong?

On edit, reread the message and guessed that "mnt" wasn't a valid command (duhh), so I changed it to "mount" and got this seriously verbose response:
```
steve@steve-desktop:~$ sudo mount -tvfat/dev/sda1 mnt/externalhdd
Password:
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
steve@steve-desktop:~$
```

Now my question is this: did it work?:) How do I know that it worked? It still doesn't show up in the Nautilus view of my computer.

And, oh, BTW, this was sold to me as an 80GB disk; does that square with the information produced above from the fdisk command? Seems inconsistent to me, but what do I know?:)

---

### Post by wislon on 2006-07-07
That looks like the kind of response you'd get if the 'mount' command didn't understand the parameters you were giving it. I think your problem might be with the command:

mnt -tvfat/dev/sda1 mnt/externalhdd

I suspect it should actually be  

mount -t vfat /dev/sda1 mnt/externalhdd

(note the additional spaces between the -t and 'vfat' and /dev). I suspect mount was picking that up as a whole lot of command line parameters it didn't understand.

If the thing mounted properly, you can go into the folder

mnt/externalhdd

in nautilus and you should be able to see your files. It may even drop a shortcut to the thing on your desktop too (my system is a little flaky and sometimes it does this and sometimes not).

Hope that helps :)

---

### Post by SteveHoffmanUK on 2006-07-07
Wislon: thanks very much for that. I tried your suggested change, and clearly you are right about my mount command, as it produced a different result, but unfortunately not the result I was looking for:
```
steve@steve-desktop:~$ sudo mount -t vfat /dev/sda1 mnt/externalhdd
mount: mount point mnt/externalhdd does not exist
steve@steve-desktop:~$
```

What is causing this?

ON EDIT:

I retried your suggested coding, but added a "/" in front of "mnt/externalhdd", so that the new command line entry was:
```
sudo mount -t vfat /dev/sda1 [COLOR="Red"]/[/COLOR]mnt/externalhdd
```

...and it "took", that is, it came back with no further error messages. However, the device is still not visible in Nautilus. What else should I try?

---

### Post by SteveHoffmanUK on 2006-07-07
Further investigation reveals that what I thought was my external hdd in the 'fdisk -l' listing was, in fact, a USB stick memory device. Once I removed that, nothing is listed. (I should have recognised that from the listing, where it says it's 519Mb, not 80Gb). Sorry to have confused everyone.

Try again: I plug in my Freecom external USB hard disk, it lights up during boot, but it not recognised at all by Ubuntu. What can I do, besides take it back and exchange it for something more Linux-friendly? :twisted:

---

### Post by SteveHoffmanUK on 2006-07-07
Following advice in another thread, I unplugged the device, activated the log display, then plugged the device in again and got this:
```

Jul  8 00:31:47 localhost kernel: [17182243.588000] usb 5-4: new high speed USB device using ehci_hcd and address 13
Jul  8 00:31:47 localhost kernel: [17182243.852000] scsi137 : SCSI emulation for USB Mass Storage devices
Jul  8 00:31:58 localhost kernel: [17182255.464000] usb 5-4: reset high speed USB device using ehci_hcd and address 13
```

and so on it goes ...

Does this help me to construct a mount command for this that will work?

---

### Post by Ptero-4 on 2006-07-07
It's resetting itself. That means it's probably or incompatible with linux or it's wiring is DOA. If you can, remove the enclosure and see if there's any anomally in the drive or wirings. If you see a chip anong the drive internals with the names "infineon" or "TPM" in it, the drive is incompatible and needs to be replaced with one from another brand. If OTOH you see something like broken, loose or unusually worn conectors in the base of the cable that goes from the drive to the computer it means the drive you got is faulty and nneds to be fixed or taken back for replacement (is your drive still under warranty?).

---

### Post by wislon on 2006-07-08
> **SteveHoffmanUK said:**
> Wislon: thanks very much for that. I tried your suggested change, and clearly you are right about my mount command, as it produced a different result, but unfortunately not the result I was looking for:
```
steve@steve-desktop:~$ sudo mount -t vfat /dev/sda1 mnt/externalhdd
mount: mount point mnt/externalhdd does not exist
steve@steve-desktop:~$
```

What is causing this?

ON EDIT:

I retried your suggested coding, but added a "/" in front of "mnt/externalhdd", so that the new command line entry was:
```
sudo mount -t vfat /dev/sda1 [COLOR="Red"]/[/COLOR]mnt/externalhdd
```

...and it "took", that is, it came back with no further error messages. However, the device is still not visible in Nautilus. What else should I try?


Doh! My profuse apologies, I missed that '/' myself. Sorry about that.

Wen you say it's not visible, are you looking for a new drive in 'Computer', or actually browsing to that folder?


Also (just to add to the confusion), I have a Vantech Nexstar external HDD mount that works via USB. If I plug it into the FRONT USB slots on my PC (it takes 2, one for power), it doesn't work. The light comes on, you can here it spinning up and down but the damn thing never actually mounts.

However, if I plug it into the BACK USB slots on the PC, it mounts, every time. I just checked and I can see it giving much the same reset message if I plug it into the front slots, so maybe this is also your problem?

If not, then I agree with Ptero-4, it sounds like that drive itself is dodgy. Have you tried plugging it into another PC to see if it mounts ok there? Windows *usually* works with these devices, immediately, so that might be a good indicator.

---

### Post by SteveHoffmanUK on 2006-07-08
Thanks to you both. 

I don't want to take the cover off because, as the sticker on it says, that would invalidate the warranty. I have another XP machine, so I will try to install it on that and see what happens. If it installs on XP, I have to assume that it's OK but it's incompatible with Linux, don't I?

---

### Post by SteveHoffmanUK on 2006-07-09
Wislon: thanks for the bit about front slots/back slots. The problem is solved, though I'm not sure how I did it. Here's what happened:

1. As per your suggestion, I plugged the 80Gb Freecom external hard disk drive into my wife's XP system and, as you would expect, BLING! new hardware detected, and it's installed straight away. Grr.

2. Before packing it away for return to the retailer, I thought, "Let's give it one more try". 

3. Unplugged my 512Kb stick memory from my Ubuntu system, plugged the hdd into one of the front USB slots; nothing happens. I then restart Ubuntu and BLING! it is immediately recognised; I write a file to it, fine, everything is OK. 

4. Next, I replug in my stick memory into the other front USB slot and BLING! it's immediately recognised BUT the hdd disappears. Hmmm. You mean I can't have two external storage USB devices on my Ubuntu system?

5. So then I plug the hdd into the front slot and move the stick memory to one of the rear USB slots, reboot and now both are recognised. Problem solved. 

Obviously there is some contention if I have both external storage devices on the two front slots. OTOH, if I plug both into two rear USB slots, that's OK -- they are both recognised.

Thanks for your help; I can now set up my backup/restore system with the hdd. 

Unfortunately, neither is recognised by my XP system running in my virtual machine on Ubuntu. There's always another problem (challenge) isn't there?:(

---


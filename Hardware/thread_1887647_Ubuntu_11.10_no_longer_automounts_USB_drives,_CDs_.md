---
title: "Ubuntu 11.10 no longer automounts USB drives, CDs and DVDs"
date: 2011-11-27
forum: Hardware
---

### Post by SavvasKatseas on 2011-11-27
My Ubuntu 11.10/64 installation no longer automounts external USB drives and CDs/DVDs inserted in the drive, be they empty or not. I've noticed the problem today, when I wanted to transfer some files to a friends' computer. 

I can see external USB drives in Disk Utility so I ended up manually mounting a flash drive and unmounting it from there too (nautilus returned a message that it did not know how to unmount).

I'm not sure of the procedure to mount a DVD disk, empty or full so I didn't try that route. As far as I can tell, Ubuntu knows that there's a DVD drive in place and that there's something inserted there, but marks the volume as "unclaimed":

**sudo lshw**
> *-cdrom
                description: DVD-RAM writer
                product: DVDRAM GH24LS70
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: GL00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   capabilities: partitioned partitioned:dos
                   configuration: signature=5653ab03
                 *-volume UNCLAIMED
                      description: Hidden HPFS/NTFS partition
                      physical id: 1
                      capacity: 1525MiB
                      capabilities: primary bootable hidden

Things that might help troubleshooting:

- I've edited /etc/fstab to add the following line so I could have a network drive automatically mounted:
> //192.168.1.11/music /media/smusic cifs credentials=/home/sino/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

There's nothing under that line in fstab and there's no line concerning CD/DVD drives there, but I'm not sure if there *should* be one in the first place.

- Right before I noticed the problem, I've connected my iPhone in one of the USB ports in order to charge it. Strangely enough, whenever I connect my iPhone in one of the ports it is recognized and mounted. No other USB storage devices are automatically mounted though.

Let me know if there's more info I can provide.

---

### Post by SavvasKatseas on 2011-11-27
Any ideas?

---

### Post by cbowman57 on 2011-11-27
Try tinkering with System Settings > Removable Media & see if that helps.

---

### Post by SavvasKatseas on 2011-11-28
Strange, really strange. Yesterday I've restarted my system 3-4 times and it refused to automount anything. When I saw your message today and booted it up to check Removable Media, it had already automounted the DVD in the drive. Checked with a USB hard drive and it automounts it too.

Anyways, problem solved, for time being.

---

### Post by SavvasKatseas on 2011-11-28
Nope, the problem's still there. When I booted today and tried to use another DVD Uubuntu won't automount it. I've checked with Removable Media, but there's nothing of help there.

Any ideas?

---

### Post by cbowman57 on 2011-11-28
I'd try reinstalling udev & dbus, but I'm grasping at straws.

---

### Post by SavvasKatseas on 2011-11-28
I'm not sure what that means. 

BTW, this installation is my second one, and I'm pretty sure I've faced this problem with my first one (which was 11.10/64 too), and I suspect it has something to do with the iPhone. In both cases, after plugging the iPhone in one of the ports the iPhone automounted but no other devices did.

---

### Post by cbowman57 on 2011-11-28
It means I'm taking a wild guess out of desperation. :)

---

### Post by SavvasKatseas on 2011-11-28
I'm not surprised by your straw-clutching (hey, where would we be without brave experimentation, even if it's our last resort? :D) but I'm afraid I'm not that familiar with Linux and Ubuntu in particular to know what a reinstallation of udev and dbus means. :)

---

### Post by cbowman57 on 2011-11-28
The way I understand it (& I could be wrong), the udev & dbus let hardware & software communicate.

Another thing that might help is adding those devices to the fstab set for automounting if they don't already exist.  I don't know how you'd do it exactly.

---

### Post by SavvasKatseas on 2011-11-28
Thanks for all the help so far, then :)

Does anybody know how I should go adding them to fstab? I've tinkered with it before but only following instructions and I've read in some threads that messing with it without knowing what you're doing may end up catastrophic. Now, I know I'm asking for chewed food (does that expression even exist in English?), so I'll be doing as much research as I can, but if anybody has an idea that might help, please let me know.

---

### Post by cbowman57 on 2011-11-28
This might be helpful [http://ubuntuforums.org/showthread.php?t=1658827](http://ubuntuforums.org/showthread.php?t=1658827)

---

### Post by SavvasKatseas on 2011-11-28
It was useful indeed. Now the discs automount -- no fancy icons support etc., but it works and that's what's most important. I'll check with empty DVDs later -- and I still have to figure out USB drives.

Thanks again!

---

### Post by cbowman57 on 2011-11-28
Cool!  Some success beats no success.

Hopefully it gives you a starting point & new things things to figure out. :)

---

### Post by slizovskiy on 2012-01-16
I have the same problems since yesterday... It appeared unexpectedly...  it worked previously.

---

### Post by swajime on 2012-01-17
likewise ... my phone's sdcards are no longer mounted when i plug it in

---

### Post by swajime on 2012-01-17
could it be related to this line in the logs?

Upgrade: nautilus:amd64 (3.2.1-0ubuntu3.1, 3.2.1-0ubuntu3.2), mousetweaks:amd64 (3.2.0-0ubuntu1, 3.2.1-0ubuntu1), nautilus-data:amd64 (3.2.1-0ubuntu3.1, 3.2.1-0ubuntu3.2), python-cups:amd64 (1.9.59-0ubuntu0.1, 1.9.59-0ubuntu0.2), libnautilus-extension1:amd64 (3.2.1-0ubuntu3.1, 3.2.1-0ubuntu3.2), gir1.2-nautilus-3.0:amd64 (3.2.1-0ubuntu3.1, 3.2.1-0ubuntu3.2)
End-Date: 2012-01-16  10:18:18

---

### Post by BurtaN on 2012-01-28
I also have the problem since months that automount does not work. Sometimes it worked for a day or so but then the bug disappeared.

---

### Post by Ross Gayler on 2012-03-14
I have the same problem - 11.10/64 used to automount DVDs fine.  It stopped automounting after I tried using some crazy-formatted DVDs written by a malfunctioning PVR.  Now when I load a good DVD it spins for a while then stops without mounting or prompting for an action (System settings | Removable media | DVD Video is set to Open Folder). However, I can open and play the DVD with VLC without the DVD being mounted.

Does anyone have any more recent suggestions before I try re-installing udev and dbus, as suggested above?

---


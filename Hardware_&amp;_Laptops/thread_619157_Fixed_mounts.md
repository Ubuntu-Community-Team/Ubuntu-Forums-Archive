---
title: "Fixed mounts"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by chrishoeppner on 2007-11-21
Hi guys!

I know I can make a certain device mount at startup (or not) on a fixed place editing fstab. But how do I make sure a certain firewire disk is always assigned to the same device (eg, /dev/sdb), so I can make sure *that* drive is always mounted in the same place, no matter how often you reboot and replug things.

I need this for a backup script that assumes the backup drive to be mounted in a certain location.

Of course, kind slaps and rtfm, are also appretiated :)

---

### Post by AlanRogers on 2007-11-21
This is covered very well in Ubuntu Hacks written by Kyle Rankin and others published by O'Reilly. You can [see the content here]("http://www.oreilly.com/catalog/ubuntuhks/toc.html") and the section you're after is called **Mount Removable Devices with Persistent Names **in chapter 8. 
 
You can even by a PDF of that section, rather than buy the whole book. I've got the book and think it's fantastic; I don't normally deface books, in case I want to lend them, but I've highlighted this one all to within an inch of it's life![-X

---

### Post by chrishoeppner on 2007-11-21
I will be getting that book as soon as I can afford it. I guess you couldn't just tell me the steps I need to take? Or is it too complicated to just type it down?

---

### Post by dabl on 2007-11-21
@chris, check out "mount by UUID" for that drive.  Here's what my NTFS-formatted USB memory stick looks like in /etc/fstab:

# Entry for /dev/sde1 :
UUID=A8FC3435FC33FC5E /media/NTFSTICK ntfs nouser,defaults,atime,exec,force 0 2


You find the UUID of your firewire drive (when it is running and attached to your Linux system) by running ```
blkid
``` in a console window.  You make a mount point in /media -- I did ```
sudo mkdir /media/NTFSTICK
```  and then you use gedit in Super User mode -- ```
gksu gedit /etc/fstab
``` to add the line to your /etc/fstab file accordingly.

Hope this helps. :)

---

### Post by AlanRogers on 2007-11-21
> **chrishoeppner said:**
> I will be getting that book as soon as I can afford it. I guess you couldn't just tell me the steps I need to take? Or is it too complicated to just type it down?If I could remember it all, and be certain to type it correctly, it'd be a very long post!

---

### Post by chrishoeppner on 2007-11-21
For some reason, blkid returns nothing for my external drive. Perhaps the firewire box is "not compatible" or whatever other kind of "I don't want to show the info". Great *lol*

---

### Post by paxmark1 on 2007-12-29
Bought book last summer.  Finally up to pg. 322 and in Gutsy Kubuntu 7.10

Setting up 10-local.rules for the USB dvd-rw that doesn't play right with the internal dvd-rw at times and a pen drive (crazy - want to someday put /var on pendrive),  

Results are after udev restart are

sudo udevtest /sysblock/scd1 block      is

parse_file: reading '/etc/udev/rules.d/00-init.rules' as rules file
parse_file: reading '/etc/udev/rules.d/025_logitechmouse.rules' as rules file
parse_file: reading '/etc/udev/rules.d/05-options.rules' as rules file
parse_file: reading '/etc/udev/rules.d/10-local.rules' as rules file
parse_file: reading '/etc/udev/rules.d/20-names.rules' as rules file
parse_file: reading '/etc/udev/rules.d/30-cdrom_id.rules' as rules file
parse_file: reading '/etc/udev/rules.d/40-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-hplip.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libgphoto2.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libnjb.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libsane.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-symlinks.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-dmsetup.rules' as rules file
add_to_rules: link priority=-100
add_to_rules: link priority=-90
parse_file: reading '/etc/udev/rules.d/65-libmtp.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-persistent-input.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-persistent-storage.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/80-programs.rules' as rules file
parse_file: reading '/etc/udev/rules.d/84-linux-wlan-ng.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-alsa.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-brltty.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hplj10xx.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hwclock.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-ifupdown.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-linux-wlan-ng.rules' as rules file
add_to_rules: PHYSDEV* values are deprecated and will be removed from a future kernel, please fix it in /etc/udev/rules.d/85-linux-wlan-ng.rules:1
add_to_rules: PHYSDEV* values are deprecated and will be removed from a future kernel, please fix it in /etc/udev/rules.d/85-linux-wlan-ng.rules:2
add_to_rules: PHYSDEV* values are deprecated and will be removed from a future kernel, please fix it in /etc/udev/rules.d/85-linux-wlan-ng.rules:3
add_to_rules: PHYSDEV* values are deprecated and will be removed from a future kernel, please fix it in /etc/udev/rules.d/85-linux-wlan-ng.rules:4
parse_file: reading '/etc/udev/rules.d/85-pcmcia.rules' as rules file
parse_file: reading '/etc/udev/rules.d/90-modprobe.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-hal.rules' as rules file
parse_file: reading '/etc/udev/rules.d/99-udevmonitor.rules' as rules file
unable to open device '/block/scd1'


10-local.rules is

BUS=="usb", SYSFS{serial}=="P01070504025352", NAME(all_partitions}="extburner"

BUS=="usb", SYSFS{serial}=="23DEABBB50448214", NAME(all_partitions}="phillips"

BUS=="usb", SYSFS{serial}=="2004351491029d20a9b4", NAME(all_partitions}="cruzer"


Any clues

---

### Post by paxmark1 on 2007-12-29
fixed (all_partitions}    to {all_partitions}      still no go 
when restarted, it said that it noticed the new hardware.  I then did mkdir /media/cruzer and media/phillips

Now when I try to mount it says that the pen drive and the mp3 player are not block devices.  

any clues?

---


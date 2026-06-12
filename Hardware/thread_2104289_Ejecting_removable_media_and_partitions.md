---
title: "Ejecting removable media and partitions"
date: 2013-01-12
forum: Hardware
---

### Post by freddo63 on 2013-01-12
Ok, so I just wiped Ubuntu 12.04 LTS off of my computer and installed Xubuntu 12.04. A couple of things I've noticed that are a little strange all of a sudden. I also installed BackTrack5 afterwards and all that seems fine, the boot manager is there though I haven't yet booted to BT. The funky things are these, I plugged in my portable 1TB seagate and can't seem to eject it. It's not mounted, but I don't feel safe removing it yet. Is it just me, and I can already safely remove it or is there another step towards removing it? Also, I have a pair of partitions (one FAT32 ~95GB and one ext4 ~48GB) that are also showing on the desktop, though they don't seem to be mounted, and I can't seem to get rid of them. The FAT32 one won't open either! What's going on here? I never had this problem in Ubuntu 12.04 LTS. I don't need the 48GB to ever show up, and the FAT32 is my data drive. Also, when I shutdown, can I remove the portable USB drive and start the system up again without causing any harm to either?

and on a sidenote, i can't get the sound settings panel to show up so that I can increase sound beyond 100% like I could in Ubuntu 12.04 LTS. Are there things or programs/drivers I haven't yet done/installed that affect these kinds of things? Any one command fixes that check for missing drivers and or programs that are necessary for proper operation? I've installed all the updates and restarted a couple of times.

---

### Post by The Cog on 2013-01-12
In the file manager (thunar) press F9 to get the sidepane (or menu View Sidepane Shortcuts) and there should be an eject symbol next to the drive. For USB devices, it powers them off as well as unmounting them.

---

### Post by freddo63 on 2013-01-12
> **The Cog said:**
> In the file manager (thunar) press F9 to get the sidepane (or menu View Sidepane Shortcuts) and there should be an eject symbol next to the drive. For USB devices, it powers them off as well as unmounting them.

As far as I can tell, it only unmounted the TB external USB drive, but it didn't disappear from there. Also nothing happens to the two partitions when I click the eject button on them... =/

---

### Post by The Cog on 2013-01-12
In which case I would use the command
sudo umount <wherever>
where <wherever> is either the device (like /dev/sdc1) or the mount point (like /media/123ABC).
You will not be able to unmount when there is a command prompt or a file manager using that mount point though - cd all your command prompts to home and change all your thunar windows to look at home as well.

---

### Post by Merrattic on 2013-01-12
You can hide desktop icons for drives: Settings > Desktop > icons tab 
and adjust settings to you taste

May be better to setup a line in your fstab for your data partition?

---


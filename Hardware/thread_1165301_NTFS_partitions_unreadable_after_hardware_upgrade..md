---
title: "NTFS partitions unreadable after hardware upgrade."
date: 2009-05-20
forum: Hardware
---

### Post by TimGS on 2009-05-20
I have upgraded my computer but am using my old hard drive (the previous machines' motherboard is dead).

Ubuntu is fine (8.04) but my dual-booting Windows XP install is not. This I care less about than the fact thay my other NTFS partition with my photographs on is also not fine since attempting to boot into Windows.

(It should be emphasised here that on starting my new machine and booting into Ubuntu, I could access my photos. Booting later on into Windows not only resulted in that not working (I expected some complaints from Windows) but it was also at that point that my Photos partition became inaccessible).

Obviously moving the hard drive back to the old machine to keep Windows happy and attempting to run chkdsk is not an option, as the old machine is broken.

The partitions show up in the Gnome 'Places' menu, but on selecting them I get 'You are not priviged to mount the volume...'

I have some quite recent backups, but cannot remember if I have changed anything since then. I would like to fix the partition just so I'm sure I haven't lost anything.

Help! I need some way of fixing these partitions from linux!

-- Tim.

---

### Post by albinootje on 2009-05-20
> **TimGS said:**
>  The partitions show up in the Gnome 'Places' menu, but on selecting them I get 'You are not priviged to mount the volume...'


Can you fire up gparted and see whether that gives some more details ?
```

sudo gparted

```
Click on the exclamation mark icon, or the keys icon of the MS-Windows partitions in gparted.

And can you also do the following, and post the output :
```

sudo apt-get install ntfsprogs
sudo fdisk -l

```

---

### Post by TimGS on 2009-05-20
Thanks for the reply - I have however since found a Windows installation disk which has a recovery mode where I could run chkdsk.

This takes a long long long time to run.

Although apparently successful, it didn't recover Windows enough to make it boot (I expected I'd get as far as being asked for a new validation code, but no luck) but never mind...

After that I had to run chkdsk again to fix the problems caused by that boot failure.

I think I'll install 64 bit 9.04 instead. The broken Windows partition is just about the right size.

thanks again anyway,

-- Tim.

---


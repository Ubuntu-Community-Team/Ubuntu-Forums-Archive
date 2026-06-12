---
title: "External media device not disconnected but not unmounted"
date: 2013-05-07
forum: Hardware
---

### Post by sameerjaffer on 2013-05-07
I have an external USB drive that when I disconnect still shows up in the /media folder. the device name is MediaDrive and when i connect it now it shows up as MediaDrive_ and the old name still show up too. I am not able to umount it.

The drive is an NTFS partition not sure how to remove the ghost media drive.

Cheers,


Sameer Jaffer

---

### Post by Mark Phelps on 2013-05-10
When you "disconnect" it, are you simply unplugging the drive? IF so, this is asking for filesystem corruption on an NTFS-formatted drive.

Instead, you should be using the option to "safely remove" it.

---

### Post by sameerjaffer on 2013-05-10
I will keep that in mind, but for now I can't get that ghost drive removed since I need to use the same name for the device. when I re-connect I it shows two devices. one as the /media/MediaDrive (which is the one I am trying to remove) and the other /media/MediaDrive_ (new device when plugging in). Also, there are no references in fstab for this external drive and rebooting does not help. are there any other configuration files like NTFS-3G or system other than fstab that might still have these settings for the drive? I am not sure.

---

### Post by sameerjaffer on 2013-05-10
Also, there are no references in fstab for this external drive and rebooting does not help (Disregard, could not delete post)

---

### Post by sameerjaffer on 2013-05-15
Anyone!!! :)

---

### Post by pumkis on 2013-05-18
Do you have daemons running whith access to your device? In my case, they were not shown with lsof or fuser, but the device was unable to unmount until all daemons (like transmission daemon, smbd and mpd) were stopped.

---


---
title: "Exernal Hard Drive: strange mounting behavior"
date: 2010-05-09
forum: Hardware
---

### Post by asdir on 2010-05-09
Hi all,

my external 1 TB hard drive is listed when I type

> sudo fdisk -l

but is not mounted automatically or shown in nautilus at all.

When I try
> 
sudo mount /dev/sdb1 /mnt/sdbfolder

it answers that it needs the type of filesystem.

Naturally I try 

> sudo mount -t vfat /dev/sdb1 /mnt/sdbfolder

and it works. However, since I have to use sudo, I need root-rights to copy things onto the drive or delete stuff. Why isn't the drive simply picked up by Nautilus like any other USB-drive?

(Additional information: Some time ago (read: some updates ago) the drive was recognized in nautilus but I had to click to mount it a couple of times before it actually worked with error messages in between. Unfortunately I don't remember the messages. :S )

Thanks for any help you can give me to figure this out.

---

### Post by khelben1979 on 2010-05-09
I think one solution would be that you install KDE and let that take care of mounting that harddrive. Have you tried it?

---

### Post by asdir on 2010-05-10
I haven't and I probably won't mess with installing KDE on my Gnome-system. However, I might try a Live-CD. Should have the same effect, right?

By the way: Isn't the underlying system for mounting harddrives the same for KDE and Gnome?

At any rate: It SHOULD work under Gnome, too. So, any other comment on the problem is welcome.

---

### Post by asdir on 2010-05-12
Additionally I found the following problems:

When I type "sudo fsck /dev/sdb", the system answers that the resource is busy although I just mounted it as described above and did nothing else.

When I try to unmount the drive, it says the same (not matter if I use the device or the mountpoint for umount).

Also I am not allowed to use chmod or chown on anything on the drive, even with sudo (is that maybe, because it's fat32-formatted).

I would reformat it, but I would not know where to store 0.5 TB in the meantime. *shrug*

---

### Post by khelben1979 on 2010-05-12
> **asdir said:**
> By the way: Isn't the underlying system for mounting harddrives the same for KDE and Gnome?

From my own experience using KDE, things have worked better with KDE than when trying to do the same thing with Gnome, so I think it would be worth a try. You can try with a Live CD first to see what it says.

---

### Post by asdir on 2010-05-17
I tried a KDE live CD, to no avail. I also updated to Lucid Lynx now, which did not help either.
Could it be it is a hardware problem even though it works on *the other* OS?

---


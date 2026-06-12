---
title: "Screwed up mounts for drives with NTFS partitions"
date: 2008-05-01
forum: Hardware
---

### Post by Jordanwb on 2008-05-01
I got two hard drives that have NTFS partitions. I clicked on Places -> 250.1 GB Media, and it mounted the drive then showed it on the desktop. I right clicked the icon on the desktop and selected Properties then to the Volume tab. Under "Mount Point" I put "/sda" ("/sdb" for the other), where it said "File System" I put NTFS and for "Mount Options" I put default. Now I can't mount either drive. I get an error saying "mount_point cannot contain the following characters: newline, G_DIR_SEPERATOR (usually /)" I understand what that means but I don't know how to fix it.

---

### Post by argosreality on 2008-05-01
Did you ever create the folders for /sda /sdb in the location that you're mounting them? can you paste in the contents of /etc/fstab?

---

### Post by Jordanwb on 2008-05-01
Yes I did create the folders. Here's /etc/fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=aa723c70-ecd5-4a5d-a5c0-008e82dca7f8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=0b69abd6-10a3-4555-8d97-65fe017fd437 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by LoungeAct on 2008-05-01
Funny... I just ran into this same problem.  I mounted my drive called "500.1 GB Media" in the gui and changed the Mount Point to /media/windows_c/.  Then I couldn't mount that drive again, getting the same error in the OP. Here's how I fixed it.

In your /etc/fstab you need to have a line that points to your drives so even though you chose /sda and /sdb for your drives, you need to know what those drives are called so you can set your fstab up correctly.  In my case, the drive "500.1 GB Media" pointed to /dev/sda1.  So in my fstab, I added this line:

```
/dev/sda1	/media/Disk1    ntfs    defaults   0   0
```

Then I made a folder in /media called Disk1.  Then I ran:

```
sudo mount /dev/sda1
```

The icon "500.1GB Media" appeared on my desktop and I right clicked it and removed "/media/windows_c" from "Mount Point" in the Volume tab.  Then unmount the drive using umount:

```
sudo umount /media/Disk1 
```

And now the drive should be mountable from the gui.

Hope this helps.

---

### Post by Jordanwb on 2008-05-02
How do I find out what Ubuntu calls the two hard drives?

[Edit] I discovered something. I only tried to mount one drive (I think). I can access the 250 Gig drive but not the 160. I'll do what you suggested for the 250 Gig.

However I'm confused on what this is going to do. Currently I have the Hard Drive icon on the desktop, when I click on that I get the contents of the 250 Gig drive. Is the stuff in fstab going to do that?

[Edit #2] I can't get into my 250 Gig drive now.

[Edit #3] I found a how-to (if you want to call it that) that solved the problem: [http://infobits.org/taxonomy/term/20](http://infobits.org/taxonomy/term/20)
I'll do what you suggested and I'll mount the drives to a folder on the desktop for easy access but I want the folder to be called "250 GB Hard Drive", and I suspect the spaces will be a problem.

---


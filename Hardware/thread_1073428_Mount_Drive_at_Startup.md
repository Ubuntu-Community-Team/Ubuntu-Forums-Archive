---
title: "Mount Drive at Startup"
date: 2009-02-18
forum: Hardware
---

### Post by Rex Regis on 2009-02-18
Hi, I'm a new Linux user and am trying to make a complete switch from Vista.  At the moment I am still dual booting with vista, although I am mostly living in Ubuntu (Intrepid).  My problem is that I have all my files on an NTFS drive (partition), and there are a lot of them, and so rather than copying everything and having   lots of everything, I am just linking the Ubuntu *Pictures*, *Music* etc files tot the appropriate place on the NTFS drive.  That's fine.  the problem is that my Desktop wallpaper is also on this drive, and when I start up Ubuntu, the wallpaper will not load until I have actually gone and accessed the NTFS drive that it's on.  Is there some way that I can have this done automatically at startup?

---

### Post by ajmctaggart on 2009-02-18
You can by looking at something like this

[http://www.goitexpert.com/entry.cfm?entry=Automount-NTFS-Drive-in-UBUNTU]("http://www.goitexpert.com/entry.cfm?entry=Automount-NTFS-Drive-in-UBUNTU")

OR

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

I googled "ubuntu automatic mount drive" to find this stuff...

I like your idea of linking the files from your NTFS partition, but 2 things...

1) It is ALWAYS safer to have your files in an OS's native filesystem, and far more efficient as a "power user" (especially if you really get into Ubuntu, you'll eventually want to move everything over to a different partitioning scheme.)

2) Why not just copy that particular wallpaper over to your Ubuntu Partition?  Auto-Mounting a Drive and having your wallpaper on your NTFS partition is adding quite a bit of time to boot up, especially for one .jpg, just copy it over to ~/Pictures or ~/ if you don't have a Pictures folder on your Home partition...

Hope this helps...

---

### Post by Rex Regis on 2009-02-18
thanks a lot for this helpful advice.  :D

---

### Post by tombott on 2009-02-18
Take a look at my guide, it shows you exactly how to do this:

[http://tombott.com/Automatically_Mount_Additional_HD_in_Ubuntu_8.10](http://tombott.com/Automatically_Mount_Additional_HD_in_Ubuntu_8.10)

Tom

---

### Post by robhamm on 2009-05-07
I know this thread is a few months old, but just in case you (or anyone else) is still having trouble--Check out pysdm in Synaptic Package Manager, and read [this quick-start guide]("http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14"). It took me all of about thirty seconds to set my NTFS partition to automount on startup.

Yes, I know it's not the cool way to do it, but we newbies sometimes need things like this while we're learning. 

For that matter, there should be no shame even for an old hand doing things the easy GUI way. Not everyone is a command-line geek (although I aspire to be one someday). It's good to get used to the command line, but some of us just want our tools to work out of the box. After all, we want more desktop *nix users, right?

---

### Post by Sumerian on 2009-09-02
Hi,

my ubuntu 8.10 can't read cds and dvds suddenly, when i insert a cd or dvd the dive works for seconds then stops and nothing shows, 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=10fb490f-549f-4dfd-9a67-bfbf12342352 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5998fd08-d3c7-4a3e-9123-68e5776bc11e none            swap    sw              0       0
# /dev/scd0       /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0 0

---

### Post by tombott on 2009-09-02
> **Sumerian said:**
> Hi,

my ubuntu 8.10 can't read cds and dvds suddenly, when i insert a cd or dvd the dive works for seconds then stops and nothing shows, 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=10fb490f-549f-4dfd-9a67-bfbf12342352 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5998fd08-d3c7-4a3e-9123-68e5776bc11e none            swap    sw              0       0
# /dev/scd0       /media/cdrom0   iso9660,udf user,noauto,exec,utf8 0 0

Silly question I know, but can your PC boot from CD ?
Just trying to establish if its a hardware problem or a software problem.

---


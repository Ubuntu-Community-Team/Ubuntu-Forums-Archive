---
title: "Hard Drive Access Restrictions"
date: 2005-11-30
forum: General Help
---

### Post by BadServo on 2005-11-30
First post here, so bear with me.  ^_^  I've been a DOS/Win user for ages, and don't really have any animosity towards the MS products, but I can easily recognize the benefits of Linux.  About twice a year I download about 6 current distros and give them a test drive to see how things are comming along, and each time I end up back with Windows.

Recently, my wife expressed interest in migrating to Linux after some prompting from the resident guru in her office.  After considering a few options I decided on Ubuntu.  Unfortunately I've had numerous problems.  Most of them I've been able to rectify (at least partially) with the help of old forum posts, but two outstanding issues remain.

Firstly, this is the "Family" machine.  It currently has 4 NTFS partitions loaded with media, archives, photos, etc....   I can easily get them mounted and accessible using the Ubuntu Disk Manager, but cannot access them via teh file manager or by clickign the links on teh Desktop since root is the owner.  Nor can I change the owner from root, since the partitions are read-only.  As it stands, the only way they are accessible is by clicking the "Browse" button within teh Disk Manager or by launching Nautilus from a Terminal using teh sudo command.

Both of those options are a little more than I would feel comfortable making the missus do jsut to access a couple pictures.  I know that I could/should convert teh partitions to something more linux friendly than NTFS, but I have no way of backing up such a large portion of data at the moment, and don't feel like risking it.

Now before anyone starts preaching I can assure you that I'm WELL AWARE of the dangers of running as root.  I swear I know it's a catastrophically bad idea.  That said, every time I try to do anything, I can't because I'm not root.  Even somethign as simple as trying to modify my xorg.conf file to enable dual monitors becomes a severe pain, since everythign has to be launched form a terminal to enable any editing.  Even creating the mount points for the afore mentioned drives required such actions, and it's terribly tedious.  It would be easier to login as root, but you can't even do this from the login screen of Ubuntu.

So my request is this:  Is there any way to grant FULL root priveledges to the default user so that I can edit what needs to be edited when I need to, AND access those partitions without all the hoopla.  Or, is there a simpel way to enable a standard user to browse those partitions without root access, and I'll jsut let Ubuntu's resrictions torment me until I get everythign else setup?

Again, let me emphasize that I'm very impressed with this distro, it's jsut been far harder getting it setup like I need it to be without tons of extra aggrevation.

Thanx for any input.

---

### Post by Bachstelze on 2005-11-30
> So my request is this: Is there any way to grant FULL root priveledges to the default user so that I can edit what needs to be edited when I need to, AND access those partitions without all the hoopla. Or, is there a simpel way to enable a standard user to browse those partitions without root access, and I'll jsut let Ubuntu's resrictions torment me until I get everythign else setup?

could you please post the contents of your /etc/fstab file ? Just a little thing to modify in there will do the trick :)

---

### Post by BadServo on 2005-11-30
Here is the current contents of teh fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               reiserfs notail          0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by BadServo on 2005-11-30
For reference I want to mount things with the following access paths:

/dev/hda1 = /media/c
/dev/hda2 = /media/d
/dev/sda1 = /media/g
/dev/hdb1 = /media/t

---

### Post by Bachstelze on 2005-11-30
OK, so you have to add the four following lines at the end of the file : 

```
/dev/hda1	/media/c	ntfs	ro,user,auto,gid=100,nls=utf8,umask=002	0	0
/dev/hda2	/media/d	ntfs	ro,user,auto,gid=100,nls=utf8,umask=002	0	0
/dev/sda1	/media/g	ntfs	ro,user,auto,gid=100,nls=utf8,umask=002	0	0
/dev/hdb1	/media/t	ntfs	ro,user,auto,gid=100,nls=utf8,umask=002	0	0
```

Save the file, unmount the partitions if you mounted them manualy and run "sudo mount -a", voil&#224; :)

---

### Post by BadServo on 2005-11-30
Awesome, that's got it knocked out.  Thanks alot for the prompt assistance.  Now to dig into some help files and learn what those commands all mean for future reference.  ^_^

If I could ever figure out how to get all my monitors working on my private machine, I'd probably switch it too.  I have 4 monitors on that one, and I've had dreadful luck getting even 2 to work correctly.  But I'll figure it out before it's over.

---

### Post by Edit on 2005-11-30
> So my request is this: Is there any way to grant FULL root priveledges to the default user so that I can edit what needs to be edited when I need to,

When you're using the terminal, add 'sudo' before any commands that you wish to run as root.  It'll prompt you for your root password, run the command as root, then chuck you back to your normal user.

-Edit

---


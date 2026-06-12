---
title: "Drives won't remount on boot."
date: 2006-02-07
forum: Installation &amp; Upgrades
---

### Post by littleman54321 on 2006-02-07
Hey anyone who happens to stumble in here...I've been using ubuntu for about a week or so now, and it's been treating me fairly decently :-D  I've been reading the forums here and I've gotten a lot of stuff to work on my own, but it seems I have finally hit a wall.  I have 3 hdd's, all formatted to ext3, but the 2 storage drives simply will not remount when I boot...which is insanley annoying!  If I go into the terminal, I can remount them fine, but that is really getting old.  Here is my fstab, so please help! :)

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1 	/Storage300	ext3 	defaults,rw,users,umask=0000 0 0
/dev/hdf5 	/Storage120	ext3 	defaults,rw,users,umask=0000 0 0

```

---

### Post by goatflyer on 2006-02-07
just comparing with my own /etc/fstab...

I have only 3 x 0s on umask, i.e. umask=000

try 'user' singular, not plural 'users'

when you say you are able to mount manually, do you mean using mount -a ?  or are you typing the full command.

last thing to check, if it isn;t coming up on boot, examine permissions on directory /Storage300 etc.  It should be plain vanilla directory owned by root.

---

### Post by littleman54321 on 2006-02-07
I changed the 0's to 3, and users to user...made no difference.

When I say manually, I am typing in
```

sudo mount /dev/hdb1 /Storage300

```
I'm not sure what you mean by mount -a, can you please explain this?

Also, the permissions are all checked (as in, Owner Group Others can all read write execute)...file owner: matt, file group: root.

---

### Post by Sutekh on 2006-02-08
[QUOTE=littleman54321]I changed the 0's to 3, and users to user...made no difference.

When I say manually, I am typing in
```

sudo mount /dev/hdb1 /Storage300

```
I'm not sure what you mean by mount -a, can you please explain this?

Also, the permissions are all checked (as in, Owner Group Others can all read write execute)...file owner: matt, file group: root.[/QUOTE]
```
sudo mount -a
``` is a command that will cause all entries in your /etc/fstab to be mounted, except those that have a **noauto** in their entry.

If it were my fstab I would just use the following entries for hdb1 and hdf5 (Storage 300 and Storage 120)
```

/dev/hdb1 	/Storage300	ext3 	defaults 0 0
/dev/hdf5 	/Storage120	ext3 	defaults 0 0

```
All that other jazz, **rw** and **users**, I don't think is needed for ext3 filesystems.  Could be wrong, but thats what I would have.

This is a good link or understanding the entries in fstab
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by littleman54321 on 2006-02-08
[QUOTE=Sutekh]```
sudo mount -a
``` is a command that will cause all entries in your /etc/fstab to be mounted, except those that have a **noauto** in their entry.

If it were my fstab I would just use the following entries for hdb1 and hdf5 (Storage 300 and Storage 120)
```

/dev/hdb1 	/Storage300	ext3 	defaults 0 0
/dev/hdf5 	/Storage120	ext3 	defaults 0 0

```
All that other jazz, **rw** and **users**, I don't think is needed for ext3 filesystems.  Could be wrong, but thats what I would have.

This is a good link or understanding the entries in fstab
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")[/QUOTE]

Thanks, this worked :)
The only thing that is different now is that I don't see the little icon on the desktop, but that isn't that big of a deal really.

---

### Post by Sutekh on 2006-02-08
There is an option to turn this on if you want it

Go to the **Configuration Editor** in the **Applications -> System Tools** Menu.

Then open up **apps -> nautilus -> desktop** and look for the **volumes_visible** key and check it.

---

### Post by littleman54321 on 2006-02-08
[QUOTE=Sutekh]There is an option to turn this on if you want it

Go to the **Configuration Editor** in the **Applications -> System Tools** Menu.

Then open up **apps -> nautilus -> desktop** and look for the **volumes_visible** key and check it.[/QUOTE]

It was already checked, so I unchecked and rechecked, but they still aren't showing up. :scratch:

---

### Post by Sutekh on 2006-02-12
[QUOTE=littleman54321]It was already checked, so I unchecked and rechecked, but they still aren't showing up. :scratch:[/QUOTE]

This will only work if the mounted partitions are in the **/media** folder.  I just tried this today, when re-arranging my windows partition.

The entry in /etc/fstab for windows was
```

/dev/sda1 /winxp ....

```
While this mounted fine, I never had an icon on my desktop.

This new line
```

/dev/sda1 /media/winxp ....

```
Will put an icon on the desktop.

---


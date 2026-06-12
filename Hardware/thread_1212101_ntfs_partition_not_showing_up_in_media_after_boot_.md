---
title: "ntfs partition not showing up in /media after boot up"
date: 2009-07-13
forum: Hardware
---

### Post by snu on 2009-07-13
hello.

I am having a small problem on an Acer Aspire 4935G;
Whenever i try to access my NTFS parition "DATA" from the gnome file browser for the first time after booting it doesn't show up in /media.

Whenever i want to use the shortcut in the panel using
> 
nautilus /media/DATA
the first time after booting i get an error that looks a little bit like this
> /media/DATA could not be found.

Please check spelling and try again
(Why "a little bit" - it's translated from german. don't know what it says in english).

Now, whenever i have ONCE accessed DATA from the left part of the file browser  (where cursor is set in screenshot attached) and not via /media (which would not be possible since it doesn't appear there)  it also appears in /media fron then on.
The panel shortcut also works from then on.

There's no problem after hybernating or going stand-by

I find this rather annoying.
An idea how to get rid of that "warm-up phase"?


PS.: Same problem if I, for instance, wanto set /media/DATA as the library folder for a music player. It seems to be a system-wide thing.

---

### Post by snu on 2009-07-15
hmm... does nobody else have a similar problem and/or a solution?

---

### Post by drs305 on 2009-07-15
> **snu said:**
> hmm... does nobody else have a similar problem and/or a solution?

Could it be that it is not mounting until you select it for the first time? You can put the partition into fstab so that it automounts.

The easiest way is to install "ntfs-config" and then run it via System Tools, NTFS Configuration (or in terminal "gksudo ntfs-config"). It will ask whether it is an internal or external drive and then for the mount point. It will then automatically make an fstab entry. From then on, the partition will automount during boot.

---

### Post by Hobgoblin on 2009-07-15
> **drs305 said:**
> Could it be that it is not mounting until you select it for the first time?

That's what I thought.

NTFS partitions are not auto mounted by default.  Probably for very good reasons.  Clicking on them either in places or in Nautilus causes them to be mounted.

---

### Post by snu on 2009-07-15
thanks for the replies - i'll try applying your advice the next time i boot ubuntu

> **drs305 said:**
> Could it be that it is not mounting until you select it for the first time? 


i guess that's it. i am only familiar with this term (mount) from mounting .iso-s, but it sounds reasonable.

> You can put the partition into fstab so that it automounts.
how would this work manually? i'd like to understand what ntfs-config does.

> **Hobgoblin said:**
> 
NTFS partitions are not auto mounted by default.  Probably for very good reasons.
i'd like to know - can you think of possible reasons?

---

### Post by drs305 on 2009-07-15
> **snu said:**
> how would this work manually? i'd like to understand what ntfs-config does.


I'll go through the procedure. Fstab is the file that assigns mount points to specific partitions when the system boots. It is a file owned by root, so only someone with administrative power can edit the file (/etc/fstab).

To mount a partition in fstab, it needs to know what to mount, where to mount it, and what type of filesystem it uses. You can also specify additional options. 

1. Specify a mount point. We will make one called "DATA" and put it in the /media folder. "/media" is normally where *removable* drives are mounted, but since that is where ntfs-config would put it, that's where we will put it as well.
To make the mount point, and to make yourself the owner (which isn't really necessary for NTFS and fat partitions):
```
sudo mkdir /media/DATA
sudo chown -R *yourusername*: /media/DATA
```
Example: sudo chown -R john: /media/DATA

Next, we have to edit the fstab file. We will make a back up first, then open it with a standard text editor.
```

sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab

```
"sudo" is necessary since this is a system file. We use "gksudo" for graphical applications like gedit.

Next, we add the entry to fstab. We need to know the filesystem type and the device identifier. Although "sdXX" (sda1, sdb3, etc) is a standard designation, it can change. So we normally now use UUIDs, which do not change unless the partition is physically changed.
To get the UUID and filesystem type, we use the following command:
```

sudo blkid -c /dev/null

```
The switch after "sudo blkid" ensures an accurate return if something changed recently but is normally not required. From that command, you look for the NTFS partition and the UUID number. Now you are ready to add the entry to fstab. It would look something like the following. Use the *actual* UUID number from the command.
> 
UUID=[COLOR="DarkRed"]508289e8-d84c-460c-906e-1f6b6c133ef5[/COLOR] /media/DATA  ntfs  auto,users,uid=1000,umask=022,utf8 0 0


This assumes you are user 1000 (first user). You can check with the "id" command. You can refer to the following link to see what the options do:
[_https://help.ubuntu.com/community/Fstab_]("https://help.ubuntu.com/community/Fstab")

Finally, save fstab and run this command - it will attempt to mount all the entries in fstab. If the DATA partition is not already mounted, it should mount. The command worked properly if you do not get any error messages.
```
sudo mount -a
```

ntfs-config does the same thing, except it doesn't make you the owner of the mount point (not necessary), uses "sdXX" instead of the UUID to identify the partition (UUID is better), and doesn't give you the same options at the end of the fstab line (but the ones it provides work).

---

### Post by snu on 2009-07-17
thanks a bunch, drs 305, for taking the time to lay this out for me, I really appreciate that.

worked like a charm, by the way.

---


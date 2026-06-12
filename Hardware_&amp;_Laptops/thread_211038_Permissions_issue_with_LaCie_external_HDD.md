---
title: "Permissions issue with LaCie external HDD"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by Thruxomatic on 2006-07-07
Hello all,


I have a firewire 120GB LaCie "D" drive and a firewire iPod mini, both formatted in HFS.  When I connect either one to my Powerbook, they automount to /media and show up on my desktop (yay).  I can read the files on my iPod, so I have HFS support and Firewire support in the kernel.

When I attempt to read the files on the LaCie, I get a permissions error, saying I don't have permission to access the files.  The device permissions are listed as 99.  Is there any way to permanently change the permissions on the drive so I don't have to worry about this anymore?

---

### Post by mlind on 2006-07-07
You can write a /etc/fstab entry for your harddrive that has umask attribute
to specify the permissions.

Can you see what group 'owns' your Lacie drive when it's mounted?
If it's called **plugdev** then adding yourself to plugdev group could solve
this the easy way without any fstab entries.

Problem using a fstab entry with removable drives is that drive assigments
may change depending on which order you plug other devices. This can be
solved by writing a udev rule for the Lacie which will always use defined
node for the drive.

---

### Post by aysiu on 2006-07-07
Who is the owner of your iPod and what are its permissions?

Are they the same for the LaCie?

To find out permissions and ownership, do something like this: ```
cd /media/ipod
ls -al
```

---

### Post by Thruxomatic on 2006-07-07
Hmmm.  I'm already a member of plugdev, so that's not the issue.
  
When I right click on the drive, it shows the group as 99 and the owner as 99 in the properties.  Listing it using ls -l while in the /media directory shows drwxr-x-wx permissions and 99 as the owner of the file.

When I open the iPod, all the *directories* list me as the owner.  All the *files* however, are listed exactly like the LaCie: drwxr-x-wx and 99.

There has to be a way to change the permissions on the item using root so that it never needs to be changed again.  Using fstab and a rule seems like a kludgy fix to me.

---

### Post by Thruxomatic on 2006-07-07
If it helps, the mtab entries for the two items are:

/dev/sda3 /media/ipod hfsplus rw,nosuid,nodev,uid=1000,gid=1000 0 0

/dev/sdc6 /media/LaCie\040120\040GB hfsplus rw,nosuid,nodev,uid=1000,gid=1000 0 0

---

### Post by mlind on 2006-07-07
Can you find the group with id 99 from /etc/groups?

Group using id 99 is often group called 'nobody'. If you see that group listed, add yourself to that group.

```

sudo adduser *user* *group*

```

---

### Post by Thruxomatic on 2006-07-07
Tried that.  There wasn't a group listed with GID 99 at all.

---

### Post by bhuot on 2006-10-27
I had the same problem - LaCie hard drive, HFS formatted and it worked fine all the time under Dapper Drake and Edgy Eft until I did an update which included a kernel update (which I think is the problem). I had the ownership of 99. I couldn't get write support and when I brought it back to my Mac it didn't show up on the desktop when I plugged it in and I had to reformat it with disk utility to get it to work. If Ubuntu is working ok in any respect, *never* update. Everything was working fine on Dapper Drake until they released an X-Windows update which screwed up the display and so instead of waiting for the developers to realize that it was not our fault and a problem with one of their updates I reinstalled. There should never be updates to X-Windows, major libraries, or the kernel as updates to a stable version - this is just asking for problems. Luckily I had other backups and was able to restore all my files. The only thing I am using Ubuntu now for is Xara Xtreme. It is pretty uselss for any web browsing with Flash crashing  Firefox whenever it loads because the developers thought it more important to add little effects on the desktop at the cost of making this incompatible. What is more important - being able to view flash on the Internet or some fancy effect of your windows?

---


---
title: "Read/Write Access on Mounted HDD"
date: 2007-06-25
forum: Hardware &amp; Laptops
---

### Post by ucsblaw on 2007-06-25
I just installed feisty on my comp using gparted to make a partition from my C drive that had XP installed already. In feisty I have access to my XP files as my C drive is mounted. 

What I really want to do is have both read and Write access to my XP drive...what can I do here? My XP is mounted as NTFS.

Does anyone recommend automatix mounter???? I am afraid of messing something up. 

thanks

---

### Post by merlinus on 2007-06-25
```

sudo apt-get install ntfs-3g

```

-merlin

---

### Post by logos34 on 2007-06-25
**sudo apt-get install ntfs-3g ntfs-config**

then,

sudo ntfs-config

enable write to external/internal devices

Reboot.  Hopefully the first time around theyll mount with r+w.  Check  with 

**mount**

ntfs parititons will show up with 'fuse' module

check /etc/fstab for new ntfs-3g entries

---

### Post by merlinus on 2007-06-25
Hi logos34.  Seems like a fair amount of folks are having problems lately with ntfs-3g.

I am trying to help someone with this problem right now, and the person yesterday disappeared when it got complicated.  And there have been others....

Most of the feedback is either that the checkboxes for "enable write support" are greyed out, or even if checked, root is the owner and no one else has any permissions except read.

And

chown -R username:username /media/mountpoint 

is not changing anything.

Any ideas???

Thanks!

-merlin

---

### Post by logos34 on 2007-06-25
> **merlinus said:**
> Hi logos34.  Seems like a fair amount of folks are having problems lately with ntfs-3g.

I am trying to help someone with this problem right now, and the person yesterday disappeared when it got complicated.  And there have been others....

Most of the feedback is either that the checkboxes for "enable write support" are greyed out, or even if checked, root is the owner and no one else has any permissions except read.

And

chown -R username:username /media/mountpoint 

is not changing anything.

Any ideas???

Thanks!

-merlin

I've been noticing that too.  Same experience with the guy I was working with last night, but we eventually got the ntfs-3g to mount the partitions correctly so he could get into windows.  I've never had any probs with that driver--maybe two reboots at most and the changes 'take'.  Grayed out config, dunno, looking into why that is happening.

Permissions are really not my area--god knows I'd probably get someone locked outof their desktop!

---


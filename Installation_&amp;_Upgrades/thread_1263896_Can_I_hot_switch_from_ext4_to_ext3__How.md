---
title: "Can I hot switch from ext4 to ext3?  How?"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by grikdog on 2009-09-11
I formatted my hard drive to ext4 (no reason, it seemed like the thing to do) when I installed Jaunty.  Now I hear that ext4 is unstable.  Is that true?  This is just a home computer, a Dell Inspiron 1525 laptop.  Do the ext4 issues affect me?  Is it possible to switch back to ext3 with live data on the drive?  Am I worried about nothing?

Thanks,
d

---

### Post by imhotep59 on 2009-09-11
I run with Jaunty and ext4 for 6 months without problem. I suggest you keep ext4 which is now stable.

---

### Post by grikdog on 2009-09-11
> **imhotep59 said:**
> I run with Jaunty and ext4 for 6 months without problem. I suggest you keep ext4 which is now stable.

I haven't had any data loss problems, and all seems well.  Yesterday, I turned my wireless back on (Jaunty includes a proprietary Dell driver that Hardy did not, and I finally noticed that).  When I shut down and rebooted (later), my screen came up in the wrong resolution, with additional functional annoyances.  This was ameliorated by simply restarting and it hasn't happened again.

But it made me wonder...

Aside from that, I can't tell any difference between ext3 and ext4.  Jaunty mangled a lot of things (especially video), so I have too many variables to follow.  I'll proceed on the assumption that ext4 is not my problem, for now.

Thanks.
d

---

### Post by imhotep59 on 2009-09-11
I think the problem you experienced is not related to ext4. The bug reported with ext4 was about loss of very big files (several Gio).
Your problem with the resolution could be somewhere in the configuration of Xorg which was corrected after reboot ?

---

### Post by Udayakiran on 2009-09-12
> **imhotep59 said:**
> I think the problem you experienced is not related to ext4. The bug reported with ext4 was about loss of very big files (several Gio).
Your problem with the resolution could be somewhere in the configuration of Xorg which was corrected after reboot ?
Is the bug still there? I'm planning to use ext4 for my file server.

---

### Post by Udayakiran on 2009-09-12
Sorry, triple post. :(

---

### Post by Udayakiran on 2009-09-12
Sorry, again. :(

---

### Post by imhotep59 on 2009-09-12
> **Udayakiran said:**
> Is the bug still there? I'm planning to use ext4 for my file server.

No the bug with ext4 is fixed.

---

### Post by Udayakiran on 2009-09-12
> **imhotep59 said:**
> No the bug with ext4 is fixed.


Whew!!! Thx...

---

### Post by shae on 2009-09-12
Ext4 is rather safe now, but if you want to be sure, the newest kernels are probably a bit better at handling it (2.6.30+).

---

### Post by imhotep59 on 2009-09-12
> **shae said:**
> Ext4 is rather safe now, but if you want to be sure, the newest kernels are probably a bit better at handling it (2.6.30+).

+1

That's probably why ext4 is the default file system in Karmic which runs with the kernel 2.6.31.

Some people say that the next FS will be btrfs and that ext4 is just a transition. Does anyone get more informations about btrfs and ubuntu ?

---

### Post by shae on 2009-09-12
> **imhotep59 said:**
> +1

That's probably why ext4 is the default file system in Karmic which runs with the kernel 2.6.31.

Some people say that the next FS will be btrfs and that ext4 is just a transition. Does anyone get more informations about btrfs and ubuntu ?

I think this has changed somewhat.  Oracle who started btrfs just bought SUN, pending EU approval, who has their own filesystem called ZFS.  Now that Oracle will probably own that code, they may relicense it as GPL.

If they do not, then btrfs will continue to be developed, at least by people not related to Oracle.  But this may decrease the odds of it becoming successful.

Btrfs will have to come a very long way before Ubuntu begins to consider using it.

---

### Post by jacksaff on 2009-09-12
Back to the original question, you can't change an ext4 formated partition to ext3. Ext4 is backwards compatible - ext4 understands ext3, but not the other way around. Ext4 can organise files into 'extents' that ext3 can't understand. You can mount an ext3 partition as ext4 no problems but it won't have the featrues that extents allow. You can also tweak an ext3 partition to become an ext4 one (basically defrag it and reorganise the data into extents), though if you do this you can't go back.

---


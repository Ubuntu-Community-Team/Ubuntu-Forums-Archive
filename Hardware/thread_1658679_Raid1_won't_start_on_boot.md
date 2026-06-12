---
title: "Raid1 won't start on boot"
date: 2011-01-02
forum: Hardware
---

### Post by brew1brew on 2011-01-02
I created a raid1 disk with Disk Utilities on with Karmic, then upgraded my system to Lucid then Maverick. This Raid disk is just a data store, I'm not booting off of it.

when I reboot the raid1 disk does not start. I have to go into Disk Utilities, stop the array and then start it. Then it comes up and I can mount it. I ran dpkg-reconfigure mdadm and it created a valid entry in mdadm.conf. but the array still does not start on boot. I want to have it auto mount with fstab but need to make sure the array starts first.

I searched but didn't find the answer on here or on linuxquestion.org. thanks in advance for your help.

Les

---

### Post by brew1brew on 2011-01-04
:bump: 

Take 2.

No one has any ideas?

---


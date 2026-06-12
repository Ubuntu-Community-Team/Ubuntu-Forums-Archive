---
title: "Attempting to Unmount a Read-Only Root Partition"
date: 2005-11-17
forum: General Help
---

### Post by organgtool on 2005-11-17
I am attempting to do something very complex and I am looking for help.  I would like to run Ubuntu Breezy Server with a read-only root partition accompanied by separate /home, /var, and /tmp.  However, I would like to occassionally upgrade packages without performing a reboot.  This is complicated since the root partition has been mounted as read-only.

I extracted the initrd image to /tmp and attempted to pivot_root to that directory, but as I expected, the pivot_root command cannot unmount the root partition because there are processes running on it.  I know what I am looking to do is possible, although it will come with severe limitations.  What I would like to know is what can I do to make this possible and what limitations will come with it?

If I establish a fairly elegant way to do this, I would be glad to contribute my work back to the Ubuntu community along with other tweaks that provide a paranoid level of security.  Thanks for any help you may provide.

---

### Post by timfrost on 2005-11-17
You can remount the root partition with (as root)
   mount -o remount,rw /
   [do the task that needs the root partition to be writable]
   mount -o remount,ro /

Note that you must NOT have any spaces around the comma in the sequence 'remount,rw' or 'remount,ro', (unless the entire parameter is in quotes) because the -o switch expects all the options to be in the next parameter

The "remount" option tells the kernmel that the partition is already mounted, and that you are wanting to change attrributes (in this case, whether the partition is writable or not).


Tim

---

### Post by organgtool on 2005-11-17
Thanks, Timfrost!  You rock!

---


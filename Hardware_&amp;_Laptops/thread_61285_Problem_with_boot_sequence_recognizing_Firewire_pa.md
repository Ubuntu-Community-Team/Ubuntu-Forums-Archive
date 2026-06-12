---
title: "Problem with boot sequence recognizing Firewire partition"
date: 2005-08-31
forum: Hardware &amp; Laptops
---

### Post by gordonbp on 2005-08-31
I dual-boot Windows XP and Hoary 5.04. I have an external Firewire HDD on which there is a dedicated 10GB Linux partition. My problem is this: It doesn't matter how or where I format this partition (as ext3) , the boot sequence is always halted with the error message that there is a bad superblock on this partition (sda2) and "if it is a genuine ext2 partition".......?????? What gives with that? I've formatted COUNTLESS times both with the Ubuntu Installer partition tool and also after installation with Qparted, but I STILL get this message about a bad superblock in a ext2 partition. IT'S NOT EXT2!!!!! So how do I fix this?

(I press Ctl-D and the boot then goes on as normal....)

---

### Post by tonym on 2005-08-31
Firstly,  I think I would ignore the ext2/ext3 issue.  ext3 is basically ext2 plus journalling.  There is a lot of common code so the message is just telling you you have a problem with this partition.

Once you have booted,  can you mount the partition OK without reformatting?  If you can this may be an example of a problem I've seen before whereby fsck kicks in before udev has created the appropriate device nodes.  Try adding "sleep 5" to the top of the fsck file in /etc/init.d.  This should allow udev to finish before fsck kicks in.

Regards

Tony.

---

### Post by gordonbp on 2005-08-31
[QUOTE=tonym]
Once you have booted,  can you mount the partition OK without reformatting?  .[/QUOTE]

yes - that's ok. I'll try your suggestion about "sleep 5" when I get home.

Thanks!

---


---
title: "Mount 2nd hard drive on boot"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by Indefual on 2007-07-02
Hello everyone,

1. Quick question: if I want to mount a hard drive on boot, is there any utility I can use to set that, or do I need to add the lines to my /etc/fstab file manually?

2. Also, my computer uses regular IDE hard drives, but I notice my device names are sda and sdb... I'm worried that it thinks they are something else other than thay are (like SCSI or something).  Should I be worried about this?

3. My second hard drive is displayed when I click Palces -> Computer, and mounts fine so I can read it.  But when it mounts (ext3 with journaling) I can't write.  Is the only way I can write to it if I add it to my /etc/fstab?

3a. Can I change the name it mounts it as? "disk" it pretty unimaginative.  So is "disk1" "disk2" that I saw on another computer.

4. off topic: And is there a graphical UI to edit the grub configuration, or do I need to edit the menu.lst file myself?  Is there any order they need to be in (I think not) do I need to worry about any of the commands in the list orders? Like chain-boot/loader or anything that need to be at the very bottom (listed in the WindowsXP menu item)?

Just switched over from Mandriva, and I want to make sure I do things that Ubuntu way properly.  Thanks for reading this, hope to hear from you.

---

### Post by logos34 on 2007-07-02
1.  It's easy to just add a line to fstab, but there is a storage device manager
**apt-cache show pysdm**

2. Feisty use the libata scsi subsystem driver to identify all drives, IDE, ATAPI, sata, scsi.  I have yet to be convinced that this is an improvement.  More [here]("https://launchpad.net/ubuntu/+spec/libata-for-all-ata-disks").

3. fstab entry will fix that.  But yu can right-click on it and try to change permissions in properties.

4.  GrubEd.  Persoanally, I'd recommend editing it by hand.  Check out the [Grub Page]("http://users.bigpond.net.au/hermanzone/p15.htm").

---

### Post by Indefual on 2007-07-03
That's great, thanks a lot.

> **logos34 said:**
> 3. fstab entry will fix that.  But yu can right-click on it and try to change permissions in properties.

Nah, it says it can't change it.

Have a great day.

---

### Post by logos34 on 2007-07-03
> **Indefual said:**
> That's great, thanks a lot.

Nah, it says it can't change it.

for example, let's say it mounts at /media/disk1.  To add write permission for owner:

[B]
sudo chmod u+w /media/disk1[/B]

---

### Post by Indefual on 2007-07-04
Thanks,

In terms of the fstab, I'm thinking of adding the following:

/dev/scb1	/media/fileserver	ext3	rw,user	0	2

Does this seem right to all?

The last two numbers I'm not sure about.  The first zero has something to do with dumping, but I don't know what that means.  Since the default is 0, I put in zero.  2 indicated that this drive is a second priority drive, rather than the root, which is first priority.  I think this has to do with checking the file system for errors.

Thanks for your help so far, every.

[edit for clarity]

---

### Post by logos34 on 2007-07-04
> /dev/scb1 /media/fileserver ext3 rw,user 0 2

Does this seem right to all?

has to be 's[COLOR="Red"]d[/COLOR]xy'

how about
> 
**/dev/sdb1 /media/fileserver ext3 [COLOR="Blue"]auto[/COLOR],rw,user 0 2**

Then it will mount at boot, read+write, accessible by any user, fsck after root partition.  '0' = dump option for whether the backup utility backs up the partition--in this case 'pass/no'

---

### Post by Indefual on 2007-07-05
Ah, is that what auto means.  Okay, that's wonderful, thanks!

Thank you very much.

---


---
title: "problem mounting drives on startup"
date: 2009-10-07
forum: Hardware
---

### Post by darthenstein on 2009-10-07
Hey everyone, newb question here;

I recently purchased a Seagate FreeAgent external hard drive, I partitioned it with ext4, changed the owner to myself (with the chmod command), and when I restart the system it mounts normally.

I decided to reformat 2 of my other internal hard drives (not my system hard drives [i have 3 internal total]) and went through the same procedure.  The problem now is that I cannot get the internal drives to mount normally, and I have to manually change the owner every time I start up.

Is there a way through Gnome to get these drives to mount on startup, or is there something else I have to do?

Thank you very much!  I apologize for I am rather new to linux, but I really like it so far!

---

### Post by darthenstein on 2009-10-07
update:  I can mount the drives quickly and normally when I go under places > Removable Media, and select the drive...may I ask how to get Ubuntu to do this automatically?

I am running Ubuntu 9.04 Jaunty Jackelope kernel 2.6.28-15

---

### Post by AppleBonker on 2009-10-07
If you're trying to mount your internal drives automatically, try installing the pysdm package from synaptic or from the command line.  This is probably the simplest way.  Otherwise, you can manually edit the fstab file.

My vote would be to use pysdm.  Once it's installed, click system>administration>storage device manager

Then, click on the device and the partition (IE sdb2 or hdb2 or whatever it happens to be).  Then click assistant and check the "mount drive at boot" option.  You might also want to make sure the "mount as read-only" isn't selected.  Then apply.  This will edit the fstab file for you.

Or, check the /etc/fstab file and edit that manually.  There should be tutorials all over the web for that.  Additionally, you can run pysdm as above and see how the fstab file changes to see what was added to it.

---


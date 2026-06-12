---
title: "Error message about harddisk defekt"
date: 2019-04-18
forum: Hardware
---

### Post by kklive on 2019-04-18
Hi,
in my Samsung-Laptop there is a little built-in SSD (SanDisk SSD i100 24 GB) which was used by Windows in former times but now is unrepairable broken and in addition not removable. Now I installed Ubuntu 18.04 and every time immediately after booting on desktop appears a black box: Hard Disk Problems detected / A hard disk is likely to fail soon.

Deleting the partitions of this sdb with gnome-disk-utility or gparted is not possible!

How can I get rid of this message? I do not need this sdb, the main harddisk sda works fine.

There is no entry of sdb in /etc/fstab!
In /etc/default/grub I inserted GRUB_CMDLINE_LINUX_DEFAULT="quiet splash sdb=noprobe" but this didn't work.

In Bios I can't deactivate it.

So what can I do?

---

### Post by Rubi1200 on 2019-04-18
Hi and welcome to the forums :-)

Preferably from a liveCD/USB post the summary report for boot info (link in my signature). Please do not repair anything, just post the report so we can try and figure out what is going on.

Thanks.

---

### Post by kklive on 2019-04-19
Thank you very much. Here is the requested link:  [http://paste.ubuntu.com/p/s8vZPc4bbT/](http://paste.ubuntu.com/p/s8vZPc4bbT/)

---

### Post by Rubi1200 on 2019-04-19
Instead of the line you added (which I would remove) to GRUB, I would do it like this:

Add this to /etc/default/grub:

```
GRUB_DISABLE_OS_PROBER=true
```

Save the file, then:

```
sudo update-grub
```

Let us know if it helps.

---

### Post by kklive on 2019-04-19
No, unfortunately, there is no change :sad::sad::sad:

---

### Post by Rubi1200 on 2019-04-20
Can you post a screenshot of the message you get?

Another thing to try, if you have not done so already, is to open the Gnome Disk Utility and unmount/hide sdb there.

Failing that, what about booting from a LiveCD?USB and reformat sdb to something like FAT32 and then hide it?

---

### Post by kklive on 2019-04-21
Here are the screenshot:
[ATTACH=CONFIG]283067[/ATTACH][ATTACH=CONFIG]283068[/ATTACH]

As you see, unmount is not possible. If I try to delete the partitions, I get the message:
Error deleting partition /dev/sdb1: Failed to commit changes to device '/dev/sdb' (input/output error during write on /dev/sdb) (udisks-error-quark, 0).
Same with sdb2.
GParted reports several I/O-Errors while starting. After ignoring them several times, I have the partition list, but it is not possible to delete them or format: several I/O-errors.

When I boot Ubuntu from USB I have exactly the same problems.

Somebody told me, the message above may come from 
/usr/lib/gnome-disk-utility/gsd-disk-utility-notify

Is that possible? What can I do?

---

### Post by Rubi1200 on 2019-04-21
Just out of curiosity, if you click on Examine what happens?

In the disk utility, when you click on the partition is there an option for S.M.A.R.T? If yes, at the bottom there should be an option to check the box don't warn me if the disk is failing.

That should fix it I think.

---

### Post by kklive on 2019-04-22
That's a bit funny: When I click on "Examine" the DiskManager opens. Here, in the upper right corner is an icon which opens a menu where you can find SMART-settings (I don't know the right expression in english because my system is german). Here I can of course switch off the SMART monitoring. If I reboot immediately, the black box with the error message does not appear. But unfortunately after a while the SMART monitoring is switching on by itself! I never found out what to do against this behavior. So if I wait a little time and then reboot, the error message appears as usual.

---

### Post by Rubi1200 on 2019-04-23
I've searched around and was unable to find an easy way to at least turn off SMART monitoring for that drive.

I suggest opening a question or bug report with the developers:
[https://gitlab.gnome.org/GNOME/gnome-disk-utility](https://gitlab.gnome.org/GNOME/gnome-disk-utility)

Sorry could not be of more help.

---


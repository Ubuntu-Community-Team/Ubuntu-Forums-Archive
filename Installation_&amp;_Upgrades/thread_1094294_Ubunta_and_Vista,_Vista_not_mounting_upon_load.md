---
title: "Ubunta and Vista, Vista not mounting upon load"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by landaut on 2009-03-12
I have recently installed Ubuntu as a 2nd OS.  I am using a IBM Lenovo R61 Laptop. I have 3 partitions, 1 partition contains Vista, the 2nd is just open space for data, and the 3rd for Ubuntu. When I initially installed Ubuntu I immediately tested to see if Vista would boot up properly and whatnot and it appeared stable. However, I didn't use vista for about 3 or 4 days and last night when I booted in to Vista it ran incredibly slow.  Any action would take 50 times longer (no exaggeration). I rebooted to see if that would fix the issue, but then Vista would no longer boot up.  It gets to the Vista loading bar and tries to load for an extended period of time then I get a BSoD with a message containing unbootable volume. I booted back in to Ubuntu with no problem and I tested to see if I could mount the partition.  I did it successfully, but only after receiving an error message that it could not mount do to a failed boot up and I had to force the mount with 'sudo blah blah -o force'.  This let me mount the partition in Ubuntu and I could see all the data with no problem. I tried booting in to Vista while leaving the partition mounted in Ubuntu and having it successfully unmounted(To test).  Both of these actions had no effect on Vista booting properly.
I know a reformat would probably cure this, but obviously I would like to do that as a last course of action.

Not sure if this is usefull to know, but here is the listing of fdisk -l:
```
trevor@trevor-laptop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaa9a29f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5341    42893312    7  HPFS/NTFS
/dev/sda2            5341        8096    22131672    7  HPFS/NTFS
/dev/sda3            8097       19457    91257232+   5  Extended
/dev/sda5            8097       18989    87497991   83  Linux
/dev/sda6           18990       19457     3759178+  82  Linux swap / Solaris

```

Any help is greatly appreciated.  Thank you.

---

### Post by landaut on 2009-03-12
Bump.  Really need some assistance.

---

### Post by landaut on 2009-03-12
I forgot to mention, I am out of town at the time, and I don't have my Vista install disk with me. A rebuild of the MBR will probably fix it, but I'm looking for a way to fix it without the disk at the time.

---

### Post by landaut on 2009-03-12
bump

---

### Post by landaut on 2009-03-13
bump

---

### Post by Mark Phelps on 2009-03-13
First of all, bumping every few hours is considered rude.  The general rule is to bump no more frequently than once every 24 hours.

Second, as the name indicates, this is a Linux forum, not a Vista forum.  So, while quite a few folks providing support here (including me) use Vista as well as Ubuntu, we're not the experts on Vista boot problems.  So, it's likely to take a while for one of the few resident Vista gurus to see your post and respond.

Third, didn't understand some of your details but it looks like you are mounting your Vista OS partition in Ubuntu in read/write mode, or something happened to your Vista OS partition to turn on the "dirty bit".  If the former, and you're mounting in FSTAB, my personal advice is to either remove the mount from FSTAB or change it to read only.  I used to have my Vista OS mounting in FSTAB and the occasional Vista partition problem would prevent my Ubuntu startup. So now, I only mount the OS on demand -- and NEVER, in read/write mode.  If the latter (dirty bit), you will have to boot into Vista  and do a chkdsk to clean up the OS.

If you can't boot into Vista via the menu, you will have no choice other than to boot with your Vista DVD and run Startup Repair.  Realize this will most probably overwrite GRUB (if you installed it to the MBR) and in that case, if you're using GRUB for the OS menu, you'll have to reinstall it.

Best of luck continuing to use Vista. I've pretty much given up on it -- due to frequent corruption of my machine through Windows Udpates, and the slightest hickup rendering it unbootable.  I've had to repair the boot three times in the last few weeks.

---

### Post by landaut on 2009-03-13
Sorry, I was just watching my post fly down the the list and assumed it was as good as dead. This is a Ubuntu and Vista issue. I assumed someone might have the same problem. 

Anyway, I originally put the mount in fstab, but I removed it when this problem began to happen. How do I set the option to read only?

---

### Post by landaut on 2009-03-13
Well, I found a repair disk for Vista:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Just putting it up for anyone who might have the same issue or may run in to it.  Running standard windows repairs (chkdsk, fixboot, etc) worked and I can now boot in properly.  It seems that me mounting those drives or somewhere in the install of Ubuntu disrupted some files in my windows partition.

---


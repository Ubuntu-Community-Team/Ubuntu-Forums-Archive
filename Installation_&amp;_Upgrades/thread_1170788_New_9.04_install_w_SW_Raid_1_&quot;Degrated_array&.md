---
title: "New 9.04 install w/ SW Raid 1 &quot;Degrated array&quot;?"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by antifaithstl on 2009-05-26
Just installed 9.04 using software raid on two brand new 1 TB disks. On the first boot-up & got a "degraded array" warning.  These are new HDD & I did test them before using a HW raid card & installed Win2k3 server just fine.  

I choose to boot anyway.  I then restarted & DID NOT see this error again.  I've rebooted several times (after installing updates) & still haven't seen the "degraded array" warning.
Was this just a 1 time event?  Is there a way I can test the SW raid 1 to make sure both disks are in use?

Thanks for the help.

---

### Post by ronparent on 2009-05-27
The odds are that you are using only one drive of the array. You would have had to configure the array with mddam or activate with dmraid (one or the other) to be using a raid setup. Did you do either?

If not, since you want a raid1, whichever approach you choose to use can still be setup at this point, probably without loss of data. If you plan on dual booting with any version of windows you will have to use dmraid. Otherwise you can use either dmraid or mddam. Be aware that your raid bios has probably already written to the metadata section of your drives and that metadata will probably have to be erased and the raid disabled in bios to permit you to assemble a mddam array. Good luck.

---

### Post by mhilarius on 2009-06-22
What is the result of this command:
  sudo cat /proc/mdstat

---

### Post by discodan on 2009-07-15
Hi,

I just ran into this myself.  I'm not sure if it is identical to what previous posters were experiencing, but I thought I would comment with my experience in case it is helpful for someone else.

I am working on a project to implement 2 ubuntu 9.04 file servers.  They are being "frankensteined" together out of spare parts.  So both servers are very-very different hardware.  Fileserver1 is an Intel Dualcore CPU on an ASUS Motherbaord.  Fileserver2 is an AMD Phenom CPU on a Gigabyte motherboard.  However, both systems, regardless of the dissimilar hardware behaved identically when trying to install ubuntu 9.04 server on a raid1 volume.

The install would go fine;  then on reboot... all kinds of chaos.  /dev/md0 would be degraded, and I would get dumped to a minimal shell.

The solution that worked for me, on both systems was... don't reboot immediately when prompted.  Essentially the mirrored drives are way out of sync, and they need to sync up 100% before rebooting.  Instead of rebooting, choose the option to "go back".  Then go to a shell.

type the command:

mdadm --detail /dev/md0

notice the sync status.  On both my machines, the sync status was at less than 10% when the installer prompted me to reboot.  Keep issuing the mdadm --detail command for each software raid volume you created until they are all sync'd 100%.  then do a "shutdown -r now".

this is what worked for both of these servers.

hope this helps someone else out there...

-disc-

---

### Post by discodan on 2009-07-16
I repeated this one more time using drives that were previously members of a linux software raid5 array.  I was trying to get ubuntu 9.04 server to install with / on 2 mirrored drives.  Even though I repeated the previously posted procedure exactly the same way, it would not work.  It was really weird.  

As posted above, the install went smooth.  I did the partitioning manually, setup the raid1 successfully.  I didn't reboot when prompted;  instead I went to a shell and watched mdadm --detail /dev/md0 and my hdd light to b sure that the drives were sync'd.  Then rebooted.  This time, on boot, when it listed the raid array as degraded, it reported that it was a RAID5, not a RAID1.  It said it was missing 2 of 4 drives.  This was the from the old RAID5 array that the drives used to be members of.  Hrmmm... very very peculiar.

The only way I could get it to work was to use a live cd and dd each the drives to all zeros.  In my setup this was accomplished with the following:

dd if=/dev/zero of=/dev/sda
dd if=/dev/zero of=/dev/sdb

It took a long time to finish, but when it did, the install behaved as the other 2 servers I had built just the other night.

To summarize my experiences:

1)  If you are using drives that previously were included in any other linux SW raid, you may need to wipe the drives with dd before they will behave.

2)  If you are booting to your SW raid, don't reboot as promtped by the installer.  Wait till your HDD light goes off and mdadm --detail reports the array is in sync.

Hope this helps,

-disc-

---

### Post by discodan on 2009-07-16
a much faster way to do the dd trick is:

dd if=/dev/zero of=/dev/sda count=5

---


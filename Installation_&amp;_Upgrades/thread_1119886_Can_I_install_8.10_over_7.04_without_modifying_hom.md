---
title: "Can I install 8.10 over 7.04 without modifying /home?"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by bliffle on 2009-04-08
I'd like to upgrade my old 7.04 to 8.10 (Ihave both the liveCD and the alternate CD) without damaging the old /home. Is it possible, or do I have to offload the /home and restore it later (it's 30gb)?

I assume I can do this without affecting the XP partition, or maybe just requiring a GRUB run.

---

### Post by Dougie187 on 2009-04-08
Well, you could do iterative updates. But doing that you have to update using the update-manager to 7.10, then 8.04, then 8.10.

If you want to do a fresh instal of 8.10, and you want to preserve /home it totally depends on how you setup your installation of 7.04. If when you were setting up your partitions you created a seperate /home partition, then yes it is possible without offloading, please note, this is not the default and you would have had to have done special steps to do this. If you just set it up as the default, then you have to offload all of your /home and do a clean install.

---

### Post by upchucky on 2009-04-08
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by bliffle on 2009-04-20
I got a new, bigger, HDD, installed WinXP then installed Ubuntu 8.10 from the LiveCD. The liveCD gave an opportunity to allocate partitions so I set aside 5gb in linux-swap format and also created a large partition for '/home' and a 20gb partition for the system.

It works fine.

Now I want to copy my old '/home' data from the old HDD (which is now in a USB box) into that '/home' partition on the new HDD. How should I do that? Can I just do a 'cp' in terminal? Or should I do a partition copy of the old system into the '/home' partition then delete all the non-/home directories?

I seem to recall running into problems before when I just tried to copy a bunch of directoies/files, like incomplete copies, messed up permissions, etc.

---

### Post by stchman on 2009-04-20
> **bliffle said:**
> I'd like to upgrade my old 7.04 to 8.10 (Ihave both the liveCD and the alternate CD) without damaging the old /home. Is it possible, or do I have to offload the /home and restore it later (it's 30gb)?

I assume I can do this without affecting the XP partition, or maybe just requiring a GRUB run.

I recommend you backup your /home partition and do a clean install.  Also install Jaunty instead of Intrepid.  Jaunty will be out in 4 days.

Use this command to backup your home partition.  Navigate to your home partition and use the following command.  Select a place on your hdd or USB drive for <dest>

```

cd ~
find . -depth -print0 | cpio --null --sparse -pvd <dest> 	
```

Install the new OS and use the process in reverse and make <dest> ~/.

---

### Post by bliffle on 2009-04-21
I followed the psychocats process, and it worked.  But I recommend using 'sudo' for the 'find' and 'cpio' commands since I didn't get the other users '/home' directories (they were empty anyhow).

I'm not sure why the addition is required to 'fstab', since '/home' seemed to get mounted OK before, but I did it anyhow.

Now, in a couple days, I'll try to see how easy it is to upgrade from Intrepid to Jaunty (which comes out on the 23rd).

---


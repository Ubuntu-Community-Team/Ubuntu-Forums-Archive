---
title: "swap partition stpps wubi install"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2009-09-06
Have experienced problems in installing ubuntu 9.04 with wubi, booting 9.04 installation etc.

Found , that this problems are only occurring when there is other linux installation on the same system using swap partition as swap space.

When swap partition exists on a system and one tries to install wubi 8.10 on some data partition, all goes fine, the wubi creates a swapfile.disk and makes all proper entries in fstab etc, pointing all swap to this location. Such installation will boot and will use the swap file as swap space.

After upgrading to 9.04, the system will not boot any more, it gets stuck at 'activating swap file…' message.

When trying to make an installation of 9.04 with wubi on a system where swap partition exists, also the installation process will get stuck at a point saying 'activating swap file…'
This is because the wubi installer created also here a swapfile.disk and the 9.04 gets now confused.

In cases when it was an upgrade to 9.04, one can try to simply boot to windows or a live system and delete the swapfile.disk. Booting will then be ok and after that from command line set the swap to the swap partition on the system. Check then in fstab that this is done so too.

When trying gto install wubi 9.04, this is more difficult, since in presence of swap partition on the system the installation will not be possible.

Bootting a live system and formatting the swap partition to some ext2 or so will kind of disable it. Wubi 9.04 installation is then possible. 
Later format the swap partition again to swap format , delete the swapfile.disk (/host/ubuntu/disks/swapfile.disk) and set the swap to point to the swap partition. From there on all will work.

I am just surprised that this does only happens with 9.04 , but not with any previous versions which have no problem to live with swapfile and swap partition on same system.

To me this is a bug, thought such arrangement of installations is probably seldem.
I have multiboot with XP, w98se, DOS622, Suse10.3, Debian L, knoppix  and ubuntu on same machine, swap partition present since suse installation on it.

People who have no other linux using swap partition will not be affected apparently and wont notice this problem.

---

### Post by presence1960 on 2009-09-06
> **ottosykora said:**
> Have experienced problems in installing ubuntu 9.04 with wubi, booting 9.04 installation etc.

Found , that this problems are only occurring when there is other linux installation on the same system using swap partition as swap space.

When swap partition exists on a system and one tries to install wubi 8.10 on some data partition, all goes fine, the wubi creates a swapfile.disk and makes all proper entries in fstab etc, pointing all swap to this location. Such installation will boot and will use the swap file as swap space.

After upgrading to 9.04, the system will not boot any more, it gets stuck at 'activating swap file&#8230;' message.

When trying to make an installation of 9.04 with wubi on a system where swap partition exists, also the installation process will get stuck at a point saying 'activating swap file&#8230;'
This is because the wubi installer created also here a swapfile.disk and the 9.04 gets now confused.

In cases when it was an upgrade to 9.04, one can try to simply boot to windows or a live system and delete the swapfile.disk. Booting will then be ok and after that from command line set the swap to the swap partition on the system. Check then in fstab that this is done so too.

When trying gto install wubi 9.04, this is more difficult, since in presence of swap partition on the system the installation will not be possible.

Bootting a live system and formatting the swap partition to some ext2 or so will kind of disable it. Wubi 9.04 installation is then possible. 
Later format the swap partition again to swap format , delete the swapfile.disk (/host/ubuntu/disks/swapfile.disk) and set the swap to point to the swap partition. From there on all will work.

I am just surprised that this does only happens with 9.04 , but not with any previous versions which have no problem to live with swapfile and swap partition on same system.

To me this is a bug, thought such arrangement of installations is probably seldem.
I have multiboot with XP, w98se, DOS622, Suse10.3, Debian L, knoppix  and ubuntu on same machine, swap partition present since suse installation on it.

People who have no other linux using swap partition will not be affected apparently and wont notice this problem.

Hmmm, I had a Ubuntu 9.04 on a partition & then decided to install 9.04 via wubi on my windows partition just to see how it works so I can increase my knowledge. I had no such problem. That is interesting. BTW I am not saying that your problem is not real. I am just commenting and making note that I did the same thing and it worked fine for me. 

maybe we can get a better look at what is happening by doing this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

P.S. at the time I installed 9.04 via wubi I had Ubuntu 9.04, Sabayon 4.1 & Mint 5 installed.

---

### Post by presence1960 on 2009-09-06
> **ottosykora said:**
> 

After upgrading to 9.04, the system will not boot any more, it gets stuck at 'activating swap file…' message.


That is the key - after upgrading to 9.04

If you peruse back in time thru these forums from now until the time 9.04 was released you will see a lot of threads in which those who upgraded to 9.04 instead of doing a clean install had major problems. 

That does not mean to say that every upgrade to 9.04 will be problematic, but we have certainly heard from a great many users who have had problems.

---

### Post by ottosykora on 2009-09-07
>This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

P.S. at the time I installed 9.04 via wubi I had Ubuntu 9.04, Sabayon 4.1 & Mint 5 installed.<

ok will try that all, as soon as I get to my PC back, I am kind of underway now.

But the wubi install was not disturbed by the only presence of other linux, only by the presence of the swap partition on it.
Even running wubi installation upgrade to 9.04 from 8.10 did not work, either the swap partition had to go or the swap file.
8.10 can handle both, 9.04 apparently only one of them.

Have seen some threads here in forum reporting similar and all did work after they pointed to the swap partition.

---

### Post by ottosykora on 2009-09-07
> **presence1960 said:**
> That is the key - after upgrading to 9.04

If you peruse back in time thru these forums from now until the time 9.04 was released you will see a lot of threads in which those who upgraded to 9.04 instead of doing a clean install had major problems. 

That does not mean to say that every upgrade to 9.04 will be problematic, but we have certainly heard from a great many users who have had problems.

yes I have seen those threads too, but similar as I was not able to see what might be the problem , all around this was also kind of fuzzy.
Actually first with the upgraded installation from 8.10 to 9.04 I was able to slightly localize the problem and found the cure was to delete the swapfile.disk and to have swap again, point to the swap partition.

Those who try to install wubi 9.04 and have swap partition present will spent lot of time and probably get fedup after few starts of wubi.
All attempts to install with wubi 9.04 on my side failed in a progress bar with note 'activating swapfile...' when swap partition was present.

---


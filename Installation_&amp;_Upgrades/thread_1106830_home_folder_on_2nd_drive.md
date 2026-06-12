---
title: "home folder on 2nd drive"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by DarinB on 2009-03-26
I finally ordered a new pc....
i have read that if i put the home folder on a secondary drive i will be able wipe out old releases and easily do clean installs of new releases and not have to redo all my settings. is this really true?? and how do i do it?? and when at install?? or after install? what if the 2ndary drive wont auto mount at install??? any good tutorials on this,,,i plan on dual boot with vista.....

---

### Post by megamania on 2009-03-26
> **DarinB said:**
> I finally ordered a new pc....
i have read that if i put the home folder on a secondary drive i will be able wipe out old releases and easily do clean installs of new releases and not have to redo all my settings. is this really true?? and how do i do it?? and when at install?? or after install? what if the 2ndary drive wont auto mount at install??? any good tutorials on this,,,i plan on dual boot with vista.....
You don't need a secondary drive, you just need a separate partition.
If you want to dual boot, you'll need to partition your drive as follows:
- swap partition
- / (root) partition for linux
- /home partition for linux
- windows partition

to preserve your home partition, when installing linux set it so that it will NOT be formatted.

---

### Post by DarinB on 2009-03-26
at my stage of skills i need more details, and ubuntu will automatically partition my primary drive for dual boot. it 
is the home folder i want to put on a secondary drive? i read that it will make moving to a new version much easier and clean, any help?

---

### Post by megamania on 2009-03-26
My suggestion is to investigate a bit about drive partitioning etc.

You can start here:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

After that, let us know if you need further help.  :-)

---

### Post by DarinB on 2009-03-27
when i decide to do a fresh reinstall on the os partition with the next version, what will be the procedure to have the separate hd with the home partition be the one utilized and not the default.

---

### Post by pbpersson on 2009-03-27
I don't have the screen shots here because.....well.....I would need to be doing an install ;)

BACKUP YOUR DATA!!!

When you get to the partitioning section.....choose manual partitioning.....you probably want to keep your current swap partition......then you choose your current partition you are using as your root ( / ).....the new hard drive will be /home.

That is all there is to it!

Now you can also do all this without re-installing Ubuntu but it will take some effort and you will have to learn some things and it would take time.  I had to add this paragraph so you know a re-install is not a requirement to get this all working.  :)

---

### Post by pbpersson on 2009-03-27
To answer your dual boot question, if you already have Vista up and running on one partition, when you install Ubuntu just make sure it DOES NOT TOUCH that partition and Ubuntu should automatically set you up with dual boot - it will recognize that Windows is there and will configure GRUB so you can get to it :)

---

### Post by megamania on 2009-03-27
> **pbpersson said:**
> 
BACKUP YOUR DATA!!!

When you get to the partitioning section.....choose manual partitioning.....you probably want to keep your current swap partition......then you choose your current partition you are using as your root ( / ).....the new hard drive will be /home.

If you have an existing /home that you want to preserve, mount it as /home in the manual partitioning and uncheck the "format?" checkbutton.
This way your existing data on the home partition will be safe.

Anyway, as pbpersson said, BACKUP your data before attempting a reinstall!

---

### Post by DarinB on 2009-03-27
i ordered a new system and when i get it. i will start the process. i have set many dual boots that is the easy part. 
One thing i noticed with my old system is that when the upgrades have failed i had to do a clean install but i seem to have difficulty getting my secondary drives to mount automatically, so i come to the forums and get help. Therefore i imagine this new system that will have 3 750 GB hds with vista business...will be the same, i think i will install ubuntu on half the hard drive but if the other drives are not mounted automatically then  how will i set up the /home on the 2nd hard drive???? I am not trying to be difficult i am trying to understand the possible pit falls. it seems that i will have to move the home folder after the install to avoid the issues or at least create the mount point and *(i think, haven't totally understood that part)* add it to fstab,,,unless the installer will actually see all the hard drives. ?????????? Am i making life harder or will all this not only teach tons of stuff but also create a system that doesn't have to be redone twice a year with the next release. it takes me a long time to tweak my desktop the way I like it and it is a real bother to have to do that twice a year. I suppose i could use 8.04 and wait till the next LTS but that is not as much fun as getting a new release. Besides i will never remember all the tweaks by then. SO please give me some expert advise?????????

---

### Post by megamania on 2009-03-27
> **DarinB said:**
> SO please give me some expert advise?????????
There's quite a lot involved in what you're asking.

The basic stuff is:
- when you're reinstalling, you have to start with a clean root (/)
- for this reason, it is wise to have a separate partition for your home stuff: this way, you will only format the root partition and all other partitions (and so your data) will not be touched.
- since you are familiar with dual boot, I'll skip this step.
- when installing Ubuntu on the new computer, create a small partition for / (root). I have 10 GB for root, and currently half of it is unused. With 15GB you'll be absolutely safe.
- create another partition for /home. You decide the size for this.
- you will hopefully see the other drives/partitions. If I remember correctly, you'll be able to mount them at install (I installed over 12 months ago, so don't take this for granted).
- when you're done with the install and everything is working, make a backup of the main system files (for example fstab)
- next time you reinstall on the same computer and hardware, you'll just format the root partition and mount /home to the old /home partition. When you boot up, linux will see the old settings. 
- in case some other partitions are not mounted, you can just copy the old fstab and reboot (or re-mount), as long as the hardware (the hard disks in particular) is the same.

hope that clears things up a bit. I was in your position five years ago, so I understand. Just remember to backup your data!

---

### Post by DarinB on 2009-03-27
Megamania! Grazie mille
that was great at least when i try this i will have old pc running so i can play with it until i get what i want.
It will be a new adventure. i should receive the pc in a week or so.
Do you think i should run 8.04 LTS and wait for the next LTD or 8.10 and keep on with the upgrades, I am not sure of the benefit of the kernel change from 8.04 to 8.10 and juanty seems weak so far.
Any thoughts

---

### Post by megamania on 2009-03-28
> **DarinB said:**
> Grazie mille
Prego!

I just clean-installed Jaunty Beta and so far everything is ok. I'll probably avoid updating until the final release comes out, so that I'm sure I won't get in trouble with broken updates.
I personally don't see a reason to stick to a LTS, unless you're managing the IT for a company and you need to keep all the systems stable and "aligned".

Jaunty seems more responsive at the moment, but I can't say much more since I've been using it for an hour altogether.

Let me know if you need further help with your adventure... :-)

---

### Post by aquascrotum on 2009-03-29
I'm in a similar position to the OP - I've just bought a 2nd HDD and would like to create a partition on it solely for /home. I currently have 1 HDD that is dual booting Intrepid/XP.

Is this possible without reinstalling Ubuntu? Presumably just creatinng the partition and moving the /home directory wont work...?

---

### Post by megamania on 2009-03-30
> **aquascrotum said:**
> I'm in a similar position to the OP - I've just bought a 2nd HDD and would like to create a partition on it solely for /home. I currently have 1 HDD that is dual booting Intrepid/XP.

Is this possible without reinstalling Ubuntu? Presumably just creatinng the partition and moving the /home directory wont work...?

I've never done it myself, but I'd suggest the following:
- backup your data
- partition/format the new hd
- boot from a live cd
- copy all the contents of your /home to the new partition
- change your fstab file so that your /home is mounted to the new file system
- reboot
- if it doesn't work, don't blame me.  :-)

---


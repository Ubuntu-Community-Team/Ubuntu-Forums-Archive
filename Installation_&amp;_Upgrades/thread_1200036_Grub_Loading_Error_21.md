---
title: "Grub Loading Error 21"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by rolyreefer on 2009-06-29
I have just installed Ubunto and can't boot up my system because of the above error.  I have had a look at this forum and found something that seems to reinstall the grubs, but that didn't work.

Thanks for any help,

Roly

---

### Post by merlinus on 2009-06-29
Boot from live cd, open a terminal and post results of:

```
sudo fdisk -l
```

Also, you can try supergrub:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by rolyreefer on 2009-06-29
Here is the results:

Unable to seek on /dev/sda

---

### Post by merlinus on 2009-06-29
It would seem that your installation did not go successfully.  The sudo fdisk -l command run in a terminal window would have showed the partitions on sda, which is your hdd.  If it did not, then clearly something is wrong.

If you do have important data, then you might try reinstalling.  But first do a checksum on your downloaded .iso, and check the cd for errors at the opening menu.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, just to be sure, the l is a lowercase L in sudo fdisk -l.  ALso, do have more than one hdd?

---

### Post by rolyreefer on 2009-06-29
I have tried to open the md5sum file, but nothing happens.  I have tried reinstalling, but the same problem happens.

I have 2 raid 0 disks and setup some partitions when installing, but I couldn't setup us NFTS system, whihc were shown in the screenshots.  Do you think this is related or some other problem?

---

### Post by merlinus on 2009-06-29
The problems may be related to your raid setup.  Search for the topic in this forum and at google.

---

### Post by ronparent on 2009-06-29
If you used the  standard live cd to install, the odds are that you trashed the raid0 set. Raid recognition is not built into the live cd version of the installation disks. In that case the partition editor only shows the individual disks as unallocated space. You would need to use an alternate cd to install.

---

### Post by rolyreefer on 2009-06-30
I have been looking at this site trying to work out which is the correct version for me and ain't got a clue!!!  Please could you tell me which version to get with raid drives, intel inside and a desktop...

I do see what you mean about not recognising my disks, but I haven't managed to get it booted up since I installed it, so probably lucky for me!!  Hoping this new version will sort out my boot up problems too...

Thanks,

Roly

---

### Post by ronparent on 2009-06-30
Get the alternate cd from the same site you downloaded the live cd from. If nothing else it will tell you the status of your raid set. If what I suspect is true you will have to reinstal everything formally in the set from scratch. At least if you still want to use the disks as a raid0 you will be able to restore the integrity of the raid set, repartion it, and reinstall everything (both for windows and ubuntu). You should read the following site to install ubuntu to a raid: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---


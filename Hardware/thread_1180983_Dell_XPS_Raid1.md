---
title: "Dell XPS Raid1"
date: 2009-06-07
forum: Hardware
---

### Post by darkhammer8108 on 2009-06-07
I just bought two WD 1TB drives and want to mirror them in my Dell XPS 600. I went into my bios and told both drives to be in 'raid-on' mode rather than just 'on' mode. then i pressed ctrl+n after exiting the bios to get into the nvidia mediashield raid controler. from here i set up a raid1 mirroring array and it says its healthy. problem is when i boot back into ubuntu im told i have two separate drives still (sdb and sdc). what am i supposed to do from here to make the drives in raid1? is this a fake raid card that dell installed and am i going to have to use a software raid? if so how do i make a software raid?

---

### Post by ronparent on 2009-06-08
You actually have what is called a fakeraid. So called because software is actually needed to acces the drive set as one raid array. In windows that software is a driver provided by the mb manufacturer. In ubuntu it is called dmraid, which, you have to install and activate to see the raid set.
 
Since you will be booting to the array you will have to follow the fakeraidHowTo to set it up - [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

The dmraid install process is itself easy if your computer has an internet connection active. Open a terminal - Applications>Accedsories>Terminal. Then write to the terminal **sudo apt-get install dmraid -y**. When the installation is complete, write **sudo dmraid -ay**. This last command will activate your raid1 array. If you now write **ls /dev/mapper** the output will show you the symbolic links that will permit you to access the drives as a set. This is the simple part. If you are using 9.04 the next part may not be so simple. But try to follow the fakeraidHowTo step-by-step and post if you have a problem.

---


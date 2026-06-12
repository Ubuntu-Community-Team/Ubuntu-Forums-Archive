---
title: "stuck on Step 4 of 7 Installation of ubuntu 8.10"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by greenart on 2009-03-03
Cant seem to get past Step 4 when installing 8.10 from USB session. Trying to install to hard drive on a Dell Mini 9 (came with Ubuntu 8.04 and am now installing version 8.10). I can use it from the usb live session but now want it on hard drive. Step 4 - doesnt see any partitions. My only option is to quit and I cant move forward. Any suggestions?

---

### Post by avtolle on 2009-03-03
Wondering if [http://www.ubuntu.com/getubuntu/releasenotes/810#Hard%20disks%20potentially%20not%20shown%20when%20installing%20in%20Live%20CD%20mode](http://www.ubuntu.com/getubuntu/releasenotes/810#Hard%20disks%20potentially%20not%20shown%20when%20installing%20in%20Live%20CD%20mode) applies to your situation?

---

### Post by greenart on 2009-03-04
i instead loaded 8.10 and am able to use this with no problems from a CD. However, my hard drive appears to have crapped out since I keep getting error codes messages like smart disk failure/no root found/ - I cant even use the partition feature. I also ran gparted and that found errors w/my video/. I called Dell to report the problems and want a new hard drive. They are blaming ubuntu even tho they admit its the hard drive. I want to use the flash usb and was wondering if I should continue using that as a substitute just to keep using Ubuntu. I also dont know what I should replace as my new hard drive. I tried wiping it clean and cant even do that unless you have a solution? I also want to upgrade to 32g ssd.... thanks much - I like ubuntu and am a past Unix users many moons ago.....

---

### Post by kdlp313 on 2009-05-14
[SIZE=3]_**Try Moving the Jumper**_[/SIZE]
[SIZE=2]Ubuntu 8.04 Unable to Detect Partition?[/SIZE]

**Greenart**, I had the same issue trying to install **Ubuntu 8.04**.  Here's what fixed it for me: I had moved the jumper on the hard drive to the '**Slave**' position when I was formatting the drive before installation, and I had neglected to set it back to '**Master**'.  Switching the jumper was all that it took, and I was finally able to get past Step 4!  Hope this helps...

-Kp

---

### Post by b@sh_n3rd on 2009-05-14
How many HDD's *DO* you have? If you've got only one, you should try setting it to single. Some drives have this option and some say to remove the jumper to set it to single. Otherwise, set it to master as kdlp313 suggested. You can also try CS or "Cable Select". Hope this helps.

---


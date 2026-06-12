---
title: "Ubuntu 7.10 w/ standard SATA OS HDD and RAID1 configuration"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by chrisgibbs on 2008-01-08
Hi All,

I have a somewhat interesting situation.

My desktop computer was my last computer running windows. Up until now this was ok but now i want to get more involved with the community and figured what the hell im gonna convert it.

First install was smooth with Ubuntu 7.10 going on a 80Gb SATA drive. I then commenced setup of the rest of the system that didnt migrate over. My number one concern was the RAID1 setup I have for storage, when researching for a RAID controller I wanted one that had native linux support so settled on a Silicon Image SiI 3112 SATA. Attached to this controller is 2 x 320Gb HD's operating in RAID1 (There is 1 NTFS partition on the RAID1).

With the first install, I did a upgrade of the entire system when I installed and pulled down all updates. Then I pulled down dmraid and started configuring up the RAID. Brilliant! It worked! Then I went and grabbed the NVIDIA drivers for my gfx and rebooted at the end..... This is where the problem started. It could not find my root partition. I booted into the liveCD and started checking things out. fdisk -l was reporting a different location for the OS. I mouted the / partition manually and reran the grub installer. No good.

I again booted into the liveCD and this time fdisk -l was reporting the old location for the / partition, I again remouted and setup grub (At this stage i thought i was going crazy). Still did not work.


I then thought maybe the graphic drivers were being funny, reinstalled the OS onto the same 80Gb HD. Installation was fine. This time i applied no updates and decided to get my RAID1 to work. 
sudo apt-get install dmraid. 
sudo dmraid -ay 

I was able to mount the drive as before and read the data. 

Then i tried a reboot.... Fails..... same error as before about the partition not being able to be mounted....

No idea where to go from here. Kinda driving me crazy as well :)

Any help please?

Cheers all,

---

### Post by chrisgibbs on 2008-01-08
Looks like I may have figured it out.

In my previous post I did not state that my M/B also supports RAID via an onboard NVIDIA controller.

I think i may have to follow the guide in FakeRaidHowTo to get grub to figure out that I want to use a /dev/mapper device. I will have a go and post how I went.

Im still open to ideas though :)

cheers

---

### Post by chrisgibbs on 2008-01-08
Nope that is not it.

The NVIDIA controller is on my mainboard but im not plugged into any of them.

I am only using 1 x SATA port that is on the Southbridge.

BTW Motherboard is a Asus P5K

Kinda stuck for ideas now ......

Cheers,

---

### Post by chrisgibbs on 2008-01-08
Fixed....

[http://ubuntuforums.org/showpost.php?p=2134349&postcount=3](http://ubuntuforums.org/showpost.php?p=2134349&postcount=3)

---

### Post by chrisgibbs on 2008-01-09
Looks like I closed the thread off to early...


Same problem and I really need a fix. 

Any ideas?

Cheers,

---

### Post by chrisgibbs on 2008-01-11
bump.

---

### Post by CLANWIRE on 2008-01-12
i was looking at this guide today as i want to setup raid 1
on my 2x 160GB hd's to

[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

hopefully this is a useful link

---

### Post by chrisgibbs on 2008-01-13
Unfortunately I do not wish to install the OS on a RAID.

I do wish however to be able to mount a NTFS partition that exists on a RAID0.

I already have an OS installed on a 1 x 80Gb drive (No RAID)

Cheers anyway though :)

---


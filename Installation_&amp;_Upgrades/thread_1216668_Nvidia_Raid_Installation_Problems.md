---
title: "Nvidia Raid Installation Problems"
date: 2009-07-18
forum: Installation &amp; Upgrades
---

### Post by l33t5241494E on 2009-07-18
I decided to dual boot Ubuntu 9.04 and Windows XP on the same raid array. I'm using nvraid striped on Raid0 with 2 WD Velociraptors (150GB). I booted the Alternate Install CD, and it found my raid array. Windows XP takes up the entire disc, so I'll need to resize the partition in order to install Ubuntu.

When I choose resize, it doesn't allow me to resize the partition. It tells me there is an unknown error, and I'm unable to resize the partition. The point of the installation is to NOT have to rebuild my raid array and lose everything in it. 

I was wondering if there's anything else I can do in order to resize my NTFS partition.

---

### Post by RJARRRPCGP on 2009-07-18
> **l33t5241494E said:**
> I decided to dual boot Ubuntu 9.04 and Windows XP on the same raid array. I'm using nvraid striped on Raid0 with 2 WD Velociraptors (150GB). I booted the Alternate Install CD, and it found my raid array. Windows XP takes up the entire disc, so I'll need to resize the partition in order to install Ubuntu.

When I choose resize, it doesn't allow me to resize the partition. It tells me there is an unknown error, and I'm unable to resize the partition. The point of the installation is to NOT have to rebuild my raid array and lose everything in it. 

I was wondering if there's anything else I can do in order to resize my NTFS partition.

Try resizing the partition with disk management in Vista. (The partitioning software in Ubuntu may be the problem)

Then, if you get an error again, then the HDD probably is corrupted.

---

### Post by l33t5241494E on 2009-07-18
Does the Vista install DVD have something that my windows xp one doesn't? Or did you just mean to repartition it using the managers in XP? If I change the size in XP's startup will it break the raid array?

---

### Post by ronparent on 2009-07-19
If you had xp partitioning software in an installed system, it could shrink the windows partition (probably c:) without destroying your raid array. The raid drivers that permit windows to access the raid partitions would protect the integrity of the raid when running on the installed system. The ubuntu partition manager should do likewise as long as the raid partion is active and you are working on the raid partition and not on the individual drives (sda, sdb, sdc, etc which will also appear when gparted is run). Try it by partitoning the raid manually while running on the live cd. You internet connectivity and you need to install dmraid (temporary while the live cd session lasts) by entering **sudo apt-get install dmraid -y** in a terminal. Verify that the raid is active by then entering **sudo dmraid -ay**. At this point you should be able to run the ubuntu partitioner from the menu. 

For complete instruction on the process for installing ubuntu to a raid see this site: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto). Post again here if you still need help. And yes, you do need to be very careful so that you don't break the raid array! There is absolutely no room for error with a raid0.

note - : ) without a space appears as :) in the post.

---

### Post by l33t5241494E on 2009-07-22
I know how to install dm raid. I tried it with both methods. The problem is, no partition manager would allow me to resize my partitions. I did find though that the newest Symantec Partition Manager will. It supports Raid arrays and allows you to easily resize and fix corruption on your harddrives. I then used the alternate install disc to install 9.04 with dmraid. I'd suggest anyone that has trouble resizing a windows raid partition and fear breaking it should use Symantec's program. Thanks for the responses, though!

---

### Post by ronparent on 2009-07-23
I presume you mean Partition magic. I acquired version 8 more than six years ago, before Symantec bought it out. It is competent within limits. I initiated a firestorm on this forum the last time I made that statement.

The program is at least 6 years old and has had no updating that I know about since its original release for use on XP and pruchased by Symantec. Two warning. It cannot be used relyably on Windows releases since XP. Disk partitioning by Ubuntu could render the partition table unreadable by partition magic. I currently have a drive in that condition, soon to be retired, which contains both ubuntu and win 7. Partition Magic operated in XP is useless with that drive. Good luck.

---

### Post by l33t5241494E on 2009-07-23
Yea, I'm not sure why I typed "Partition Manager." I meant partition magic as you stated below. I'm using partition magic 9.0, and yes, it is quite buggy. The problem I was having though, wasn't Ubuntu. It was the fact that I couldn't get a windows partition resized using other partition managers (I probably had some corruption in them if you want to know the truth). Depending on how you setup your partitions in Ubuntu could cause problems later on, but that wasn't my concern. I have no desire to continue to use partition magic; I just used it to correct the issue at hand so I could install Ubuntu on my PC.

---

### Post by ronparent on 2009-07-23
I didn't say it, but good move. Any port in a storm.

---


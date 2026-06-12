---
title: "Raid Recommendations"
date: 2010-12-29
forum: Hardware
---

### Post by TangRedSocks on 2010-12-29
I am planning on setting up a Raid 5 config under Mdadm. I am looking to optimize the volume for streaming to my HTPC running XMBC. The volume will consist of 6 2TB Samsung HD204UI (5400 RPM 32mb cache). It will hold mostly files with a size around 1GB each.

I am looking for advice on these two issues:
 
1) File system choice. The default seems to go with ext4 but I have seen some articles online that suggest XFS is more well suited for large volumes. 

2) Raid chuck size when I set up the disks. I was leaning towards a 64K chunk but have seem some people report that a 128k works best for raid 5 configurations. If I go with ext4 I was going to use the following command: "mkfs.ext4 -b 4096 -E stride=16,stripe-width=80"

-Background 
I am moving away from a Fakeraid windows setup using Intel Rapid Storage Technology. SMB shares on the windows box seem to not sustain consistent read/writes. This is also a headless unit so I like how you can set up email notifications using the monitor in mdadm. I would go days without knowing my volume had been degraded when using windows because I hardly remote into it. 

Thanks again for any suggestion you might have to offer.

---

### Post by Fafler on 2010-12-29
I don´t see any reason not to go with ext4. It works great

As for chuck size, i don´t think it will matter very much, but you can always reshape the array, if you want to try different layouts. It just takes a while.

No matter what, you should be able to fill a gigabit ethernet interface with 6 of those drives.

As for email, just setup exim locally on the server, put your username in mdadm.conf and make your email program check mail from your user account on the server. I don´t know how it works if you want to forward it to the "real" internet, but i guess that can be done too.

Do you need 10 tb? Personally i would go with 8 tb and use RAID 6 instead. One thing i´ve learned from building arrays like this from consumer drives is that they aren´t that reliable.

---

### Post by TangRedSocks on 2011-01-11
> Do you need 10 tb? Personally i would go with 8 tb and use RAID 6 instead. One thing i´ve learned from building arrays like this from consumer drives is that they aren´t that reliable.

That is actually a great suggestion. I am going with 128k stripe and raid 6. I am doing a write up of the project here: [http://ubuntuforums.org/showthread.php?t=1663597](http://ubuntuforums.org/showthread.php?t=1663597)

Where I am at now is getting the share to work correctly across OSX.

---


---
title: "sudo badblocks and sudo fsck to get a hdd to work again?"
date: 2014-07-04
forum: Hardware
---

### Post by ubto66 on 2014-07-04
Ubuntu 14.04 64 bit.
 

 I have a 2tb hdd, that I used for data backup and it was truecrypt full hdd encryted.

 

 Some error occurred. Maybe because of a not correctly working hdd power supply connector. That meant I could see the truecrypt hdd as a device listed in truecrypt, but I could not mount it.
 

 I shred the hdd. I used miray 4 which is a free boot shred software. The program shreds and tells if there are sektor writing errors. The hdd got shred, and there were 55 writing errors. I could reformat the hdd.
 

 If I try the 'disks' 'smart data and self test', it says 'self-test failed'.
 

 I want to know, if the hdd is for the garbage bin?
 

 I have watched this video [http://www.youtube.com/watch?v=Ay9AKBO8rsI](http://www.youtube.com/watch?v=Ay9AKBO8rsI)
 It says first you write this command sudo badblocks -v /dev/x > bad-blocks-result
 and then sudo fsck -t ext4 -l bad-blocks-result /dev/x
 

 Is that how I get to use the hdd again?
 

 After more than 12 hours, sudo badblocks -v /dev/x > bad-blocks-result had not finished.
 

 Can I alternate the commands so progress, if any, gets displayed?
 

 Thank you.

---


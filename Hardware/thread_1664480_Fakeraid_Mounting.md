---
title: "Fakeraid Mounting"
date: 2011-01-11
forum: Hardware
---

### Post by PoppinJ on 2011-01-11
p { margin-bottom: 0.08in; }  Hello all. I tried really hard to figure this out without having to ask because I'm sure the answer is out there, but I'm to new to Linux and am stuck.

I have a 250 GB Hard drive that dual boots Win 7 and Ubuntu desktop 10.10, both x64. I then added 2 separate hardware (fakeraid?) RAID 1 (2 x 2TB each) arrays using an integrated AMD 740G chip set. I then went into windows 7 and mounted the two arrays using GUID partition tables and NTFS formating using 4096 blocks. Everything is working normally in win 7 but in Linux it seems to not be recognizing the arrays. The drives are showing up as 4 separate drives instead of 2 arrays. I can mount them to the desktop but i haven't tried to put any data on them yet as I'm afraid I will desynchronize and ruin the arrays. I guess i need fakeraid or dmraid but i dint know what that means and am under the impression that dmraid doesn't recognize GUID. From what I'm reading it should already be recognised after 9.10.

I think this guy had a similar issue but i couldn't find any closure
[http://ubuntuforums.org/showthread.php?t=1635801](http://ubuntuforums.org/showthread.php?t=1635801)
[http://ubuntuforums.org/showthread.php?p=10223109](http://ubuntuforums.org/showthread.php?p=10223109)

fakeraid how to
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by PoppinJ on 2011-01-11
[http://ubuntuforums.org/showthread.php?t=1601596](http://ubuntuforums.org/showthread.php?t=1601596)

Ummm getting closer?
I have installed dmraid and now the 4 seperate hard drives are no longer seen individual in "places" The disk utility still sees them separately but there is now a section called peripheral devices that looks like my two raid arrays.  Sooooo... now i have to mount them or reformat them first? Im not to terrible sure how to do that though. 

This thread was helpful to me.
[http://ubuntuforums.org/showthread.php?t=1601596](http://ubuntuforums.org/showthread.php?t=1601596)

Since I think Im getting close the most important thing is for someone to let me know how to ensure the array is working or how to monitor it. Also, ive never had to rebuild an array but utalizing this message will I be able to easily rebuild the arrary in case of hard drive failure?

---

### Post by PoppinJ on 2011-01-11
Ok, I finaly have everything set up. I was using the disk utility to format the arrays but that was a terrible idea. It would format them into 4 or 5 different partitions and then recognize them each as their own  disk. Then it would not allow me to partition them any more. Windows would recognise them as several different allocated and unallocated partitions but the could not be initialised. .I had to use gparted along with kpartx to fix the partitions and reformat the drives. Now the drives can be manipulated with both win 7 and ubuntu.

The final issue I have is that they will not mount after a restart. I have to re open g parted to let it map or scan the drives, then they will show up in computer or places so that I can get them to mount. Is there a way to get this to happen automatically?

---


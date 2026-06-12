---
title: "Cannot move files onto external hdd"
date: 2009-01-06
forum: Hardware
---

### Post by bedake on 2009-01-06
I am trying to transfer files onto an external HDD.  Every time I attempt to cut/paste the files into the drive I experience an error:

Error while coopying "file name"
there was an error copying the file into /media/disk-1/Media.

Error opening file /media/disk-1/Media: Input/output error

I am trying to transfer Family guy episodes to my external HDD to watch on my nintendo wii,  

I put on a few seasons a month or so ago succesfully, though now ubuntu fails to open the files.


When attached to the The Wii, I  can open and view the files with no problem at all from the HDD through my wii, but ubuntu fails completely at opening them. 

 It is even stranger, I can open and watch futurama episodes stored in another directory on the hdd under ubuntu but trying to watch the family guy episodes will cause the drive to unmount ittself.





Any suggestions?  This external HDD is around 7 years old i think, is it likely its finally starting to fail on me?

I am not sure this is the case because I believe I am experiencing a similar problem with my USB thumb crive

---

### Post by MusicMastaMike on 2009-01-06
double post, see next post.

---

### Post by MusicMastaMike on 2009-01-06
Please post the output of the following 3 commands:

```

sudo fdisk -l
mount
ls -l /media/disk-1

```

---


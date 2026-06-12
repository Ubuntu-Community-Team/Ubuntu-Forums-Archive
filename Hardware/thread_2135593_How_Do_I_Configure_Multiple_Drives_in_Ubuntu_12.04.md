---
title: "How Do I Configure Multiple Drives in Ubuntu 12.04"
date: 2013-04-14
forum: Hardware
---

### Post by Ron Brooks on 2013-04-14
Hello--

I have just built a new computer, which has an SSD and a regular HD. It was my first build, so it's been a learning process. I just got it all together yesterday, and was excited to see all the drives present on the BIOS screen. 

I have decided to use Ubuntu 12.04 rather than Windows because philosophically I have always wanted to move in that direction. Right now, everything I have been downloading goes to my SSD and that's fine for now, but I would like to be able to set up my music, documents, pictures, videos, etc to be saved on the standard HD. 

The BIOS and the disc utility in Ubuntu show the HD as present, and I just had the disk utlility format the HD, but I am a bit lost as to how to configure the music, document, video, and picture folders (do I move them, reroute them, configure from another place altogether?). I think I'm having difficulty because I can't see something like the "My Computer" option in Windows here. (For what it's worth, I'm not doing a dual boot with Windows. I'm just focusing on Ubuntu.) When I try to download a document to my HD, I simply can't find it. 

I'm sure that my question marks me as a newcomer, but that's what I am. Any help you could offer would be appreciated.   

Ron

---

### Post by oldfred on 2013-04-14
How large is SSD? 
My SSD is 64GB but I installed 2 / (root) partitions so I have the current install and the future install. I keep all data in data partitions on my rotating drive. I have two data partitions and link them back into my /home which I keep on the SSD with just the hidden files & folders that are user configuration of the system. That way system can fully boot from SDD without hard drive in case of issues, but would give errors on not mounting data partition. It is more advanced than the usual suggestion of just having / (root) on the SSD and /home on rotating drive, which is a reasonable alternative.

I orginally was moving my /home to another partition and realized that was not exactly what I wanted. So my data partition ended up with all my default folders at the top level like Music, Documents etc. I think like each folder back into my /home.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by ahallubuntu on 2013-04-14
~

---

### Post by Ron Brooks on 2013-04-14
The SSD is 120GB, and I appreciate knowing how to partition it, but I also have a 1TB Hard Drive that I want to put my video files on, etc. The deeper I look now I realize that for some reason the "Computer" section of Ubuntu is not seeing my HD. It's only seeing the SSD and the CD drive. Any thoughts on how to handle this?

---

### Post by Ron Brooks on 2013-04-14
Sorry, ahallubuntu, my reply was to the post above yours. I've got to study what you are saying a bit.

---

### Post by ahallubuntu on 2013-04-14
~

---

### Post by ahallubuntu on 2013-04-14
~

---

### Post by Ron Brooks on 2013-04-14
It is brand new. I'm going to install Gparted and follow your directions. I was just reading about fstab when I checked back here, so thanks! We'll see what happens.

---

### Post by Ron Brooks on 2013-04-14
That worked! The secondary drive is showing up now. I just split the drive in half and made two partitions, which may not have been the wisest thing, but right now it's an empty disk, so I think I can still play around with it. Now, I'll follow your other directions and see if I can get the folders moved over there. Thanks so much.

---


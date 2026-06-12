---
title: "Ubuntu 9.04 Installation Problem"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by zachary715 on 2009-06-16
I'm trying to become a new Ubuntu user however I'm having trouble installing.  I get through all the steps and when I actually select to install it hangs at about 27% with an error saying there's a problem with the ext3 or something.  I've read other forums and realized I burned the disc too quick (48x) so I'll try that but has anyone else had this problem or have any other ideas or suggestions? Thanks

---

### Post by merlinus on 2009-06-16
You might also do a checksum on your .iso:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by rogst on 2009-06-17
You could also run the "Check CD for defects" utility at the first menu when booting on the CD.
:D

---

### Post by zachary715 on 2009-06-17
I ran the "Check CD for defects" and it came up clean so I figured the disk was fine.  I'm installing on an old...

Dell Dimension 8100 1.5 GHz proc.
256MB Ram
20 GB HD

Someone gave me this old computer and I figured I'd try it out.  I'm actually planning on installing on this system tho and putting the hard into another old system with 512MB Ram for more efficiency.

I haven't had time to run md5 checksum should I try that first or make new cd at slower speed first?  Which is more likely?

---

### Post by dstew on 2009-06-17
I assume you are using the Alternate Install CD. My guess is that the disk is bad. Me personally, I would [check the md5 checksum]("https://help.ubuntu.com/community/HowToMD5SUM") first, and if it is OK make another disk at a slow burn rate

---

### Post by zachary715 on 2009-06-17
checked the md5 checksum and it's fine it "compared" or whatever but as far as CD I just downloaded the .iso from ubuntu download page and burn it using nero essentials but the speed was at 48x.  I'm going to download infra recorder or a similar program and try to make another cd to see if that helps..

---

### Post by dstew on 2009-06-18
One other thought. Have you done a memory check? Your memory is right at the border for what is sufficient, so if you have some bad memory the installation will fail.

---

### Post by zachary715 on 2009-06-18
Update:  The error message I kept getting I googled and found another forum that had many others with the same problem. I removed the hard drive and put it into the system with 512MB memory and tried to install there too but same error.  I was then told that if all else fails install 8.04 so I did.  At this point I had to install in safe graphics mode and all was looking good until I had to partition the drive... none showed up.  I googled this error and it could be an array of things.  I'm ready to give up on linux unless someone can tell me a good distro that isn't a bit$& to install..

---

### Post by zachary715 on 2009-06-18
If I tried Mandriva do you think I'd still get all these same problems?

---


---
title: "Access to resource has been denied+"
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by kliljedahl on 2007-02-08
I originally posted a thread about how to install a scanner driver here:[http://www.ubuntuforums.org/showthread.php?t=353303]("http://www.ubuntuforums.org/showthread.php?t=353303")

It's an HP Scanjet 4370. That was never resolved, but then I found a deb file here: [http://sourceforge.net/project/showfiles.php?group_id=150599&package_id=166435&re lease_id=453913]("http://sourceforge.net/project/showfiles.php?group_id=150599&package_id=166435&re lease_id=453913") and installed it.
But now when I try to access XSane I get: 
Failed to open device 'HP3900:libusb:004:002':
Access to resource has been denied

Please bear with me, I'm a total newbie. I'm never going back to Windows, so I will learn this,

---

### Post by Haegin on 2007-02-09
Sounds like a permissions problem which I have found to be common with sane - you probably need to add the udev entry. Almost all of my limited knowledge is located in this thread which covers setting up a scanner: [http://ubuntuforums.org/showthread.php?t=316961](http://ubuntuforums.org/showthread.php?t=316961)

---

### Post by kliljedahl on 2007-02-09
> **Human Prototype said:**
> Sounds like a permissions problem which I have found to be common with sane - you probably need to add the udev entry. Almost all of my limited knowledge is located in this thread which covers setting up a scanner: [http://ubuntuforums.org/showthread.php?t=316961](http://ubuntuforums.org/showthread.php?t=316961)

Thanks for the response. I was starting to wonder if I was going to get any. I'll check it out in a little bit, I just got home from work. I don't really want to reinstall Windows just for some hardware, so I appreciate this. I got this scanner primarily because I have a lot of old negatives I need to scan. The HP replaced an Acer flatbed that was supported but doesn't do negatives, and a Pacific Imaging negative/slide scanner that I'm sure will never be. I hope I can follow your instructions. I am a total newbie to Linux, and have much to learn. I know virtually nothing of the commands or how they work.

---


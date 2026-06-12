---
title: "Ubuntu 64 bit open files"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by it99 on 2009-08-24
I have a Pentium 4 , 64 bit processor and Ubuntu installed.
 
[LIST=1]
[*]How can I tell if the Ubuntu version I have installed is 32 or 64 bit?
[*]Is it hard to convert from 32 to 64?
[*]I'm trying to switch to 64 becuase I've been using Hadoop/Katta indexing and have been running into the 'Too many open Files' problem. I heard that the 64 bit version can have unlimited open files. Is this true? What is the best way to change the maximum value? I've seen a few different thing around the web.
[/LIST] 
Thanks you very much!

---

### Post by starcraft.man on 2009-08-24
1. Open a terminal and type in:

```
uname -m
```
If it returns 86_64 then your running 64, otherwise 32.

2. You can't, if you want to move to 64 bit you reinstall the OS. It's an architectural shift not like installing an application.

3. I am not aware of this problem with 32. I know there are limits on files, this does not have to do with the architecture of OS 32 or 64 but the filesystem used on the disk. See [here]("http://en.wikipedia.org/wiki/Comparison_of_file_systems#Limits"). As ya can see, there are limits, but not the number of open files systems to my knowledge. I don't think I can fully answer question, not a user of the software, perhaps its a bug.

You can try moving to 64, I don't think it's the problem. Backup data (or if you've separate /home just reinstall and don't format it) and then use a 64 bit version.

---


---
title: "Change ownership/mount location of External hard drive"
date: 2009-11-30
forum: Hardware
---

### Post by Bridgestone24 on 2009-11-30
Hello,
   I have a Seagate Freeagent Go 250GB USB external hard drive. I usually use it on my MAC but would like to be able to use it on my desktop machine which runs 9.10. I can only read the drive i cannot write to it which is the issue.

Here is some other info to maybe help guide my problem.

Permissions: drwxrwxrwx
Where all other volumes say 'root' the external says '99'
when using 'mount' command it returns that it's type hftplus
under the 'fdisk' command it shows /dev/sdc1 and that it is HFS/HFS+

Not exactly sure what's going on here, It seems that i need to change to user from 99 to root or to my user name. Any idea on how to do that or of what's going on? Thanks.

---

### Post by Bridgestone24 on 2009-11-30
Figured it out. When i originally purchased the drive it wouldn't work on my Mac so i reformatted it wish OS X disk utility. I didn't realized i selected that it be journaled which apparently complicates things. I'll have to dumb it's contents onto my laptop and reformat it someday.

---


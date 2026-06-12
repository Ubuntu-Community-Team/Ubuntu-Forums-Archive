---
title: "windows 7 + ubuntu"
date: 2009-09-21
forum: Installation &amp; Upgrades
---

### Post by jithendra89 on 2009-09-21
hello can someone please tell me whether i can install ubuntu in my windows 7 OS... before i installed ubuntu with XP... thank you

---

### Post by raymondh on 2009-09-21
> **jithendra89 said:**
> hello can someone please tell me whether i can install ubuntu in my windows 7 OS... before i installed ubuntu with XP... thank you

are you referring to a WUBI-install (ubuntu inside windows) or Ubuntu in its' own partition.  Either way should work.  Defrag windows and back-up your files.

---

### Post by jithendra89 on 2009-09-23
> **raymondhenson said:**
> are you referring to a WUBI-install (ubuntu inside windows) or Ubuntu in its' own partition.  Either way should work.  Defrag windows and back-up your files.

ubuntu in its own partition.... d i hv 2 configure da boot manager manually?:confused::confused::confused:

---

### Post by bumanie on 2009-09-23
If you install windows 7 first, the ubuntu, grub should configure the dual boot system automatically. There are a number of guides around - read a few before you continue if you are not sure.

---

### Post by raymondh on 2009-09-23
1.  Back-up your files
2.  Defrag windows. 
3.  Boot into the liveCD
-  You may want to double-check the [MD5]("https://help.ubuntu.com/community/HowToMD5SUM")
-  You may want to "check CD for defects"
-  You may want to try a live session (try ubuntu without changes...) to see how the version plays well with your system
4.  If OK, proceed with the install
5.  In step 4, select side-by-side.  REMEMBER ... there is a slider below that **you HAVE to grab and use (use your mouse) to allocate partition sizes** because if not, you will be given the 2.5GB install which is not even enough for the first update.  See link below.

Grub will be set-up automatically in the process.

Good luck and happy ubuntu-ing.

[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874)

---


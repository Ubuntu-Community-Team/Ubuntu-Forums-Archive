---
title: "can not boot"
date: 2008-10-13
forum: General Help
---

### Post by williy0385 on 2008-10-13
I have installed ubuntu 8.04 on my laptop. which is a dell inspiron 1100. I have benn using it for about a month know but when I started it up it wouldnt boot so i turned it off and restarted in recovery mode. when i do this /dev/sda1 contains  a file system errors check forced. then I get a  unattached inode 1761664 it says run fsck manually without -a -p options. i dont not know how to do this i try fsck then all it say is pass 1 checking inodes,blocks,and sizes but does nothing else.
 I am a newbie so please help as i would like to get it working again.

---

### Post by bcom on 2008-10-13
fsck -a is used to automatically  repair the file system without any questions.

I did not see a -p option.  There is a -P option.  The man page says this about the -P option:

 When  the  -A flag is set, check the root filesystem in parallel
              with the other filesystems.  This is not the safest thing in the
              world  to  do,  since  if the root filesystem is in doubt things
              like the e2fsck(8) executable might be corrupted!   This  option
              is  mainly provided for those sysadmins who don’t want to repar&#8208;
              tition the root filesystem to be small  and  compact  (which  is
              really the right solution).

Maybe you should run fsck with just the -a option first.

Type: sudo fsck -a

---


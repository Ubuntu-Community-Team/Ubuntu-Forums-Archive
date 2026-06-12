---
title: "HDD partition"
date: 2010-11-27
forum: Hardware
---

### Post by ConspX on 2010-11-27
Hi

I just installed ubuntu on a hard drive using the wubi installer from windows, but now I cannot manage to see the other partition. I installed it on patition 2, so now I can't see the partition ubuntu is installed in.
Do you have any ideas how to fix that, because I'm pretty new to ubuntu and have no idea.

---

### Post by Fafler on 2010-11-27
I don't quite sure i follow you. Is it that you cannot access the Ubuntu partition from Windows?`That's quite normal, as Ubuntu uses a filesystem Windows cannot access. You can, however, access your Windows partition from within Ubuntu.

---

### Post by ConspX on 2010-11-27
yeah that's what im trying to say, I can access the windows partition from linux but since my hard drive is divided into 2 partitions (C:/ and D:/) and I installed ubuntu on D:/, I can only access C:/, I can't see the files in D:/

---

### Post by mitchd123 on 2010-11-27
Ubuntu is an operating system, not a program.  Ubuntu may have taken over the D partition. 

From a Linux terminal window type in 

sudo  fdisk -l /dev/sd[a-d]
sudo  fdisk -l /dev/hd[a-d]

(note that's an lower case -L, not the number 1)


Highlight the text and copy.  Post the output.  If it shows the partitions as Linux, then the windows based files are gone.

---


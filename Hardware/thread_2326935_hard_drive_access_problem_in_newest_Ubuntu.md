---
title: "hard drive access problem in newest Ubuntu"
date: 2016-06-06
forum: Hardware
---

### Post by kristoffer4 on 2016-06-06
Hello Ubuntu community. Ill get straight to the point. I was running wiindows 10 on my Workstation and decided to upgrade it by installing Ubuntu. Love it so far, its really great, BUT

The additiional disk drives where I have my art and files cannot be accessed from Ubuntu. I tried Virtual Box, which is supercool, but I cant get into the driives. I need to access them so I can copy my files and very important documents to Ubuntu and then II can format them. Is there a way to access them? I attached a screen grab so you see what happens when I try to access the drives. I cannot mount them as well.

Can anyone help as Im very new to this operating system.

Hope I can solve it.

---

### Post by yancek on 2016-06-06
The error message you posted explains it all.  You have left your windows system hibernated and no Linux will mount a hibernated filesystem as it could easily be damaged.  You need to turn off fast boot and anything related to hibernation if you want to access your windows partition from Linux.

---

### Post by kristoffer4 on 2016-06-06
thank you very much for your answer. Well, I read that there is a file that everything is saved to that relates to hibernation on windows. I dont have windows anymore on my machine except you know, the viirtual box one. I have to somehowe delete this file, and that means I need to get in the command prompt and call on a function that will delete it.

---

### Post by yancek on 2016-06-06
You could try the second option in post two at the link below, mounting that partition read only from Ubuntu.  That should allow you to access the folders/files on the partition and copy what you want from that partition to another partition.

[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by houstonbofh on 2016-06-06
Download hirens boot cd and run checkdisk to clean and repair the Windows filesystem.  Do not use it to edit the Linux partitions aor touch the MBR.  Then you should be able to mount the partitions easily.

---


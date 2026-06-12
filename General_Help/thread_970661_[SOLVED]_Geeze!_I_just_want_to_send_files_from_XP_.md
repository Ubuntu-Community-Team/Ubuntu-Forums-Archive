---
title: "[SOLVED] Geeze! I just want to send files from XP to my linux on same network!"
date: 2008-11-04
forum: General Help
---

### Post by n2stc on 2008-11-04
It should be easy.  I would like to back up files from the main winXP box to my KUBUNTU 7.10 older box.  I've tried to setup samba; can't get past the password prompt(from XP).  VSFTPD worked for a while, but now always says the connection was reset by the server.  Any suggestions would be appreciated!

Stan

---

### Post by Peter09 on 2008-11-04
Can you see the windows box on the network?

---

### Post by n2stc on 2008-11-04
I'm not in front of it but, come to think of it, not from the Linux box.  I can see it from other windows boxes though.

Thanks,
S

---

### Post by Peter09 on 2008-11-04
You should be able to see your windows shares from your Linux Box. What version of Linux are you running?

---

### Post by n2stc on 2008-11-04
Kubuntu 7.01.  gutsy

---

### Post by Peter09 on 2008-11-04
Do not know KDE very well, but you should be able to see your windows shares on the network

---

### Post by cariboo on 2008-11-04
Make sure you have **smb4k** installed on your Kubuntu computer to make browsing share a lot easier.

Smb4k is available in the repositories.

Jim

---

### Post by n2stc on 2008-11-05
Jim: Thanks for the tip.  (nice dog!)

PC: I can see the windows boxes from KUBUNTU.  Still can't FTP though.

---

### Post by KeyserSoze93 on 2008-11-05
Install openssh-server on your ubuntu box, and then use WinSCP on the windows box.

---

### Post by Peter09 on 2008-11-05
If you can get to your windows shares then you can drag a drop files to you Ubuntu filesystem. You will not be able to ftp unless you have an ftp server set up.

---

### Post by n2stc on 2008-11-06
> **KeyserSoze93 said:**
> Install openssh-server on your ubuntu box, and then use WinSCP on the windows box.

thanks.   When I try to log in as local_host, it asks for a pass word?  Where is that set?

---

### Post by n2stc on 2008-11-13
I got this solved reading
[http://ubuntuforums.org/showthread.php?t=867133](http://ubuntuforums.org/showthread.php?t=867133)

and others.  THANKS!

---

### Post by n2stc on 2008-11-13
Now I just need to figure out how to control which drives/directories are made available to the world.

---


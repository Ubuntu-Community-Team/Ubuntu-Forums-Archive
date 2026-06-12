---
title: "gdmsetup Segmentation Fault"
date: 2008-08-11
forum: General Help
---

### Post by oVIXx on 2008-08-11
Anyone now how to fix this? 

When I start gdmsetup either through System/Administration/Login Window or sudo (& gksu) gdmsetup I get a segmentation fault and the window for the login manager closes. I searched through the archive threads and any solution posted has to do with Xgl, which I didn't install, and the file gdm.conf-custom. However if I delete the gdm.conf-custom or restore it both scenarios make the gdmsetup crash. 

It started about a week ago when the gdm was in the list of Security updates, and I allowed it to overwrite the current configuration file. No use in keeping the old one if the old configuration allows for the closed exploits in the new gdm.

Any thoughts on this?
Thanks

---

### Post by oVIXx on 2008-08-12
Hmm, only a few hours and almost to page 3...

---

### Post by sr20ve on 2008-08-23
I'm having the same problem.

Aug 23 14:16:42 error kernel: [  100.121378] gdmsetup[6325]: segfault at 00000000 eip 00000000 esp bf9ce53c error 4

Aug 23 14:20:37 error kernel: [  219.019380] gdmsetup[6610]: segfault at 
00000000 eip 00000000 esp bff2a1bc error 4

any ideas?

---

### Post by BoredOutOfMyMind on 2008-08-24
Same issue here after kernel upgrade...

---

### Post by lintoon on 2008-08-25
I had the problem where System - Administration - Login Window 
would open for a second then quit.  When I ran gdmsetup from the command line I was getting segmentation faults.

I read somewhere that gdm.conf-custom could be damaged or has been replaced.

So replacing gdm.conf-custom got it working for me.

Here's how I done it.

$ cd /etc/gdm

Backup your current gdm.conf-custom (my backup is gdm.conf-custom.org)

$ sudo cp gdm.conf-custom gdm.conf-custom.org

I have a file called gdm.conf-custom.dpkg-old so i thought I'd try it.

$ sudo cp gdm.conf-custom.dpkg-old gdm.conf-custom

Hope this helps someone.

---

### Post by Dbyte on 2008-08-26
Not a fix, but a workaround:
In terminal type "sudo dbus-launch gdmsetup"

I was battling this for days before I found the info posted [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5610731").

BIG thanks to [[COLOR="Blue"]oVIXx[/COLOR]]("http://ubuntuforums.org/member.php?u=163444") for the helpful post!

---


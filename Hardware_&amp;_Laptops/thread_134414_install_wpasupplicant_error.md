---
title: "install wpasupplicant error"
date: 2006-02-21
forum: Hardware &amp; Laptops
---

### Post by m_walker on 2006-02-21
Hello, I just installed ubuntu 5.10 breezy and I've been having problems getting my wireless setup.  I read through the forums and found some good HOW-TOs.  The driver seems to work fine, except I can't connect because of wpa from my access point.  From following the HOW-TO for setting up wpasupplicant, I tried doing:

sudo apt-get install wpasupplicant

and I get this error:

Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  wpasupplicant
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 153kB of archives.
After unpacking 414kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe wpasupplicant 0.4.5-0ubuntu1 [153kB]
Fetched 394B in 0s (776B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wpasupplicant/wpasupplicant_0.4.5-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/w/wpasupplicant/wpasupplicant_0.4.5-0ubuntu1_i386.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

any suggestions?
Thanks, I appreciate the help.

Mike

---

### Post by ape on 2006-02-21
Looks like there's a problem on the server you're trying to hit.  Try modifying your /etc/sources.list file and use a different server such as [http://ubuntu.cs.utah.edu](http://ubuntu.cs.utah.edu)

---

### Post by m_walker on 2006-02-21
thanks for the reply.
That couldve been the problem.  I didnt do anything different and I tried the same command about an hour after i got the error and it worked.  It was really frustrating.  But now I got my wireless working so its great!

---


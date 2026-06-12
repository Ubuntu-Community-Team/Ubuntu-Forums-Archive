---
title: "I can't update the repositories"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by aarelovich on 2009-03-17
Hi I've just instaled the latest kubuntu (8.10 I think).

I've desperately need to download certain programs but uptitudes raises this error:

Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (113 No route to host)
0% [Connecting to ar.archive.ubuntu.com (91.189.88.46)] [Connecting to security.ubuntu.com (91.189.88.37)]rr [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (113 No route to host)
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (113 No route to host)
0% [Connecting to ar.archive.ubuntu.com (91.189.88.45)] [Connecting to security.ubuntu.com (91.189.88.37)]
Err [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) intrepid Release.gpg
  Could not connect to ar.archive.ubuntu.com:80 (91.189.88.40). - connect (113 No route to host) [IP: 91.189.88.40 80]


With all my addresses
Here is what my sources.list say. I'm behind a proxy but it is all ready configured in the system as I'm using the internet just fine.

Thanks for any help.

---

### Post by dunkar70 on 2009-03-17
aarelovich,

Check out this thread...

[http://ubuntuforums.org/showthread.php?t=136065](http://ubuntuforums.org/showthread.php?t=136065)

---

### Post by aarelovich on 2009-03-17
Hey. Thanks a lot. 


I'll try the apt.conf thing to see if that is the problem

Thank you so very much.

---

### Post by aarelovich on 2009-03-18
That didn't work exactly.

I had to generate the apt.conf file and write this line:

Acquire::proxy "http:://myproxy:myport"

But thanks. That solved it.

---


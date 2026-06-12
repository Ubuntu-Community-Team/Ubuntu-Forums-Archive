---
title: "password doesn't work, can't do ubuntu reinstall"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by dlteach2 on 2009-10-07
Ubuntu 9.04 was successfully installed on my laptop.  I edited the password and now cannot get in at all, using the old one or the new one - error message says I have the wrong password or username no matter what I try. So, tried to   reinstall ubuntu from a cd- keeps going back and asking for the password. I'll try the password suggestions on the forums - if that doesn't work, any advice about what to do next to get a clean reinstall that works?  Many thanks.

---

### Post by mdmarmer on 2009-10-07
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Mike

---

### Post by dlteach2 on 2009-10-08
I did use that and was able to retrieve my password - thank you. However, as soon as I opened ubuntu, there was a popup about several security files to be updated. I used the update manager and got the following response:

"w. failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/newt/python-newt_0.52.2-11.3ubuntu](http://security.ubuntu.com/ubuntu/pool/main/n/newt/python-newt_0.52.2-11.3ubuntu) 3.1-1386.deb
could not resolve 'security.ubuntu.com'



"w. failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/newt/librewto.52_O.52.2-11,3ubuntu3.1-i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/newt/librewto.52_O.52.2-11,3ubuntu3.1-i386.deb) 
could not resolve 'security.ubuntu.com'


What do I do now? Is there a security problem because of being identified as the "root" (I read the comment about that in the psychocats article) but am still concerned. 

Thanks in advance!

---

### Post by dlteach2 on 2009-10-09
After retrieving my passwords (they didn't work) with the help of the forum, there were messages saying to update some security files. The update manager can't do that. Also, can't use the solitaire game anymore as the cards won't move. What happened? What to do?

---

### Post by dlteach2 on 2009-10-12
Sorry, the password issue was resolved but not the updating issue.

---

### Post by dlteach2 on 2009-10-12
Thank you! Problem solved.

---

### Post by dlteach2 on 2009-10-12
Thank you. Problem solved.

---

### Post by rippin on 2009-10-12
> **dlteach2 said:**
> I did use that and was able to retrieve my password - thank you. However, as soon as I opened ubuntu, there was a popup about several security files to be updated. I used the update manager and got the following response:

"w. failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/newt/python-newt_0.52.2-11.3ubuntu](http://security.ubuntu.com/ubuntu/pool/main/n/newt/python-newt_0.52.2-11.3ubuntu) 3.1-1386.deb
could not resolve 'security.ubuntu.com'

"w. failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/newt/librewto.52_O.52.2-11,3ubuntu3.1-i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/newt/librewto.52_O.52.2-11,3ubuntu3.1-i386.deb) 
could not resolve 'security.ubuntu.com'!

That simply means, as the message said, that the URL could not be resolved - no contact made to destination Internet site. Just 'apt-get update' again.

> What do I do now? Is there a security problem because of being identified as the "root" (I read the comment about that in the psychocats article) but am still concerned. Has nothing to do with your prior problem or security in any way. Read the message, "could not resolve 'security.ubuntu.com".

---

### Post by dlteach2 on 2009-10-12
okay. Thanks.

---

### Post by dlteach2 on 2009-10-17
Thank you. I'll work on this and report back.

---


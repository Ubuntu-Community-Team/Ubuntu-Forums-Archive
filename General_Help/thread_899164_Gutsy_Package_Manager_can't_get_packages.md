---
title: "Gutsy Package Manager can't get packages"
date: 2008-08-24
forum: General Help
---

### Post by msknight on 2008-08-24
Gutsy Gibbon, 32 bit on a laptop.  Trying to install SSh via package manager.  It wants openssh-server as well, but on application...

W: Failed to fetch [http://security/ubuntu/com/ubuntu/pool/main/o/openssh/openssh-server_4.6p1-5ubuntu0.1_i386.deb](http://security/ubuntu/com/ubuntu/pool/main/o/openssh/openssh-server_4.6p1-5ubuntu0.1_i386.deb)
404 Not Found

W: Failed to fetch [http://security/ubuntu/com/ubuntu/pool/main/o/openssh/ssh_4.6p1-5ubuntu0.1_all.deb](http://security/ubuntu/com/ubuntu/pool/main/o/openssh/ssh_4.6p1-5ubuntu0.1_all.deb)
404 Not Found

So ... I presume my installation points to a location of packages that don't exist any more. (which will explain why my laptop hasn't told me of any upgardes for a while)  Any ideas how I get around this please?

---

### Post by Stemp on 2008-08-24
indeed [http://security/ubuntu/com](http://security/ubuntu/com) does not exist ! (but security.ubuntu.com does)
Check your sources.list (file /etc/apt/sources.list)
Your have a problem there.

---

### Post by msknight on 2008-08-24
Hi Stemp,

I was actually typing the error on to another machine and the error does contain a . not a / - I typoed reporting the error. Sorry!

So the error does exist and it is security.ubuntu.com

---

### Post by Ryadt on 2008-08-24
Have a look at this link: [https://answers.edge.launchpad.net/ubuntu/+source/dpkg/+question/40321](https://answers.edge.launchpad.net/ubuntu/+source/dpkg/+question/40321)

---

### Post by Stemp on 2008-08-24
@msknight :You did an update before trying to install ssh ?

---

### Post by msknight on 2008-08-24
I'm going to try an update to 8.04 now.  We'll see what blows up :popcorn:

---

### Post by msknight on 2008-08-25
Thanks - updating the entire installation took some time, but it did the trick.  SSH then went in with no problem at all.  It certainly beats the Windows upgrades!

---

### Post by Stemp on 2008-08-25
In fact, I wasn't asking you to upgrade to Hardy.
I was just asking you to update your current installation ;)

But well, you're now an Hardy user and SSH is installed.

---


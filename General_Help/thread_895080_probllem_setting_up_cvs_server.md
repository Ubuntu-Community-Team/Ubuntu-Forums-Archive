---
title: "probllem setting up cvs server"
date: 2008-08-19
forum: General Help
---

### Post by badperson on 2008-08-19
Hi,

I was going through the docs [here]("http://doc.ubuntu.com/ubuntu/serverguide/C/cvs-server.html")

and I'm not getting any output when I type:

sudo netstat -tap | grep cvs
when i enter
sudo netstat -tap

I get a bunch of stuff; samba, nfs, mysql, but no cvs. 

When configuring xinetd, when the instructions told you to enter the xinetd.d/cvspserver file, that file did not exist when I went to edit it. 

Also, I changed the cvs repository default location before configuring...those are the only two things where I didn't follow the documentation to the letter...

anyone run into this before? 
bp

---

### Post by RealPSL on 2008-08-19
I am not a CVS expert but I think the instructions wanted you to create the /etc/xinetd.d/cvspserver file with the contents in the document. This file will tell the super daemon xinetd how to respond to requests for cvs service.  Create the file making sure to put in the right repository location and then restart the xinetd daemon with ```
sudo /etc/init.d/xinetd start
```

---

### Post by badperson on 2008-08-20
Hi,

I followed those instructions, but am not getting anything when entering

```
gksudo netstat -tap | grep cvs
```

is there any way to uninstall xinetd and start over? 
bp

---

### Post by RealPSL on 2008-08-20
I apologize I gave you the wrong command

```
sudo /etc/init.d/xinetd restart
```

If that does not resolve the problem. Can you attach your 
/etc/xinetd.d/cvspserver file? Also send the output of ```
ls -l /usr/bin/cvs
```

---

### Post by badperson on 2008-08-21
that did the trick, thanks!
bp

---

### Post by kruser on 2009-01-27
I am new to linux and having problems with this as well... I've created the file cvspserver. 

when I do sudo /etc/init.d/xinetd restart I get:

* Stopping internet superserver xinetd                                  [ OK ] 
* Starting internet superserver xinetd                                  [ OK ]

which I assume means it is running, however when I do 

gksudo netstat -tap | grep cvs

nothing comes up. So I did the  ls -l /usr/bin/cvs and got:

-rwxr-xr-x 1 root root 700660 2008-05-19 05:44 /usr/bin/cvs

is this correct?  Thanks for your help

---

### Post by kruser on 2009-01-27
Figured it out, I took off the gk in

gksudo netstat -tap | grep cvs

and it came up.

---

### Post by badperson on 2009-01-29
oh man...I'm redoing my server, haven't messed with this in awhile,

now I'm having the same problem again, and the above stuff isn't helping....

I restarted xinetd, I double checked the cvspserver file, but nothing...

even when I do sudo /etc/initd.d/xinetd restart

nothing when I hit sudo netstat -tap | grep cvs
bp

---

### Post by badperson on 2009-01-29
Got it...I deleted the /etc/xinetd.d/cvspserver and started re-created it, and that worked.
bp

---


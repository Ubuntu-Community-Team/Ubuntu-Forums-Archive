---
title: "Installing Oracle 11g"
date: 2008-04-02
forum: Georgia Team - US
---

### Post by larryduncan on 2008-04-02
I am new to Ubuntu, and I love it it was very easy for me to install and get running.

I am trying to install Oracle 11g on my machine.  I need to know the steps that I need to do to make sure the installation goes correctly, or point me to a site.

 I installed it last night but it stated that there were errors and the installation failed.  I tried to install the x86_64 version and the x86 version

:confused:

Please Help.

---

### Post by twright on 2008-04-02
you could try this:
[http://www.pythian.com/blogs/654/installing-oracle-11g-on-ubuntu-linux-710-gutsy-gibbon](http://www.pythian.com/blogs/654/installing-oracle-11g-on-ubuntu-linux-710-gutsy-gibbon)

---

### Post by larryduncan on 2008-04-03
I checked out the documentation, are you to enter all the commands listed or are those details of what the commands will do when executed.


Also, do you need to create a Oracle_Home folder before you begin installation and where does it need to be placed.

If this is the wrong place for this post please direct correctly.

Thanks

---

### Post by twright on 2008-04-03
you only need to do the bit after the $
e.g.
```
bott@mybox:~$ **xhost +192.168.x.y**
192.168.x.y being added to access control list

```i think the wizard will create the folder for you

---


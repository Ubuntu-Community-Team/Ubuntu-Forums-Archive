---
title: "Virtual box wont work"
date: 2008-08-26
forum: General Help
---

### Post by reffu on 2008-08-26
Every time i try it asks for the ose module but when i type the code with 'uname-r' at the end i get this 
E: Couldn't find package virtualbox-ose-modules-2.6.24-21-generic
Is there an ose package for 2.6.24-21 yet? if so can someone tell me how to get it?

Thanks,

Reffu

---

### Post by jkhh07 on 2008-09-06
What type of computer are you using?

I have an AMD64 proccessor.

I used the following to make mine work. There does not seem to be any documentation at the Virtual Box website for the work around.


> A workaround for the problem is to do the following :
sudo apt-get install virtualbox-ose-source
sudo m-a update
sudo m-a prepare
sudo m-a a-i virtualbox-ose
sudo /etc/init.d/vboxdrv restart

I found this at the following website.
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/260722](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose-modules/+bug/260722)

Then Install the actual program either from command line 
> 
sudo apt-get install virtualbox-ose

or search for it in the synaptics manager.


Let me know what happens

---


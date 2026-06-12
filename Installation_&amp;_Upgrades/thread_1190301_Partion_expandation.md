---
title: "Partion expandation"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by Daniel1994 on 2009-06-17
My computer came with a 100GB hard-drive divided into two partions(50GB). Windows was installed on one of them, but the other one was empty. I desided to install Ubuntu on the empty one, but after running a full install(choosing what I belived was the empty 50GB partion) I now have Ubuntu running on a 20GB partion(taken out of the windows one) and the 50GB still empty.:S 

Is there anyway to join up the Ubuntu partion and the empty 50GB one?


I bet there is a extremly simple and apparent answer to this question, but I'm new to both Ubuntu and advanced computuring, so.....help, please?

---

### Post by merlinus on 2009-06-17
See below...[]("http://gparted.sourceforge.net/")

---

### Post by merlinus on 2009-06-17
You can use gparted on the live cd to do this.  You can also use the gparted live disk.  The website has screenshots and directions which are useful whichever one you use.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

A good idea would be to use the new partition for /home, rather than adding it to /.  Instructions here:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Daniel1994 on 2009-06-22
Thanks, I'll try that:D

---

### Post by Daniel1994 on 2009-06-25
First, I used GParted on the LiveCD to delete the partion I wanted to join up with the ubuntu partion.

I then ran the Live CD inside windows and installed a 3GB installation inside windows, to access the extended and ext3 partions.

I rebooted choosing to run from the 3GB installation, and installed GParted.

Used GParted to add the 50GB free space to extended, and then add it to ext3.

Uninstalled the 3GB installation, and then I had things set up the way I wanted:D

Again thanks for all help.

---


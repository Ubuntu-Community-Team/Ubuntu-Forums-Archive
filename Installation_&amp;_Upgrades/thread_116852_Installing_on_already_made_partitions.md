---
title: "Installing on already made partitions"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by squimmy on 2006-01-13
Following the tutorial on:[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) I see only partitioning options, how would I go about installing it without doing any partitioning?

 I plan to do all the partitioning in a windows progam. Also, if I am careful, what is the chance of losing all my data (on C:)? Without letting ubuntu even touch the C partition? and The last time I installed linux, I had serious problems with grub, what is the chance of that happening again?

Thank you for any help.

---

### Post by hillbilly on 2006-01-13
First of all the partitioning program in windows must be capable of resizing your existing partitions and merging two partitions e.t.c. (One such software is partition magic 7.0).

Well if you use a good program and select your paritions properly the chance of you losing your C is very tiny. One important thing though, is to do the partitioning steps one by one rather than group together all the partitioning tasks into one task.
For e.g. if you want to resize C partition and then merge another two paritions and then format another partition, its best to first resize C and apply the changes before doing the other partitions tasks. Thats the way I usually do. 

Well we certainly cannot predict whats going to happen, but GRUB is one kickass bootloader. So even if it screws up, chances are that you can fix it. 

Fearless is the key dude. FEARLESS ;) !!

---

### Post by squimmy on 2006-01-13
My plan is to use acronis disk director. The last time I used it (to install linux) it was great, and worked like a charm.

Looking at this image :[http://users.bigpond.net.au/hermanzone/p3/i0023op.gif](http://users.bigpond.net.au/hermanzone/p3/i0023op.gif)
 what option would I select to not resize anything, just install straight onto the partition? 

Thanks for the help!

---

### Post by hillbilly on 2006-01-13
first select "manually edit partition table". 
Then you will be shown a screen where you can view the existing paritions on your disk.
From this select the partition you want to install ubuntu on. And then you will get an option to automatically partition that. The system will then setup that partition for ubuntu and wont touch any of the other partitions.

---

### Post by squimmy on 2006-01-14
Using acronis disk director,I've created a new 30 gb ext3 partition. C : is still working fine, so im relatively pleased. Should I now let ubuntu do the rest of the partitioning, seeing as messing up C is near impossible, as hopefully ubuntu shouldn't touch it now, right?

Or should I create the swap partition through acronis disk director as well?

EDIT:: I am still confused on what to do after another read through of [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm). Do I select "Automatically partition the free space" on the my new ext3 partition, and let the installer do the rest? And it won't touch C? (I think hda1)

---

### Post by pauljwells on 2006-01-14
I used Acronis DD to set up  50GB of free space and then let the ubuntu installer do the rest, worked perfectly. I also use the Acronis OS selector, this works great, but often windows updates ad other installs can break it, so the machine boots straight into windows. It's not a problem though, you just have to pop the install disk back in and rerun the installer to repair it.

---

### Post by squimmy on 2006-01-14
Egh, it looks like I won't be using ubuntu. Unless I can figure out how to disable usb probing at boot up. At the start of the install it freezes at /etc/hotplug/usb.rc but strangely mepis boots straight in with no problems. I want to use ubuntu more :(

---


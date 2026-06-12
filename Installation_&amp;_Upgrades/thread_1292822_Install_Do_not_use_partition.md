---
title: "Install: Do not use partition?"
date: 2009-10-16
forum: Installation &amp; Upgrades
---

### Post by bit mad on 2009-10-16
I'm looking at [http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293-4.html](http://www.tomshardware.com/reviews/ubuntu-linux-guide,2293-4.html) to try to get comfortable with the install process and partitioning.

I'm puzzled by this dialog - why would you need to specify "do not use the partition"? What's that all about? I've searched the forums and googled but I'm still none the wiser what this is for... why would you create/edit a partition and not want to use it?  :confused:

[IMG]http://media.bestofmicro.com/Linux-Ubuntu-9-04,X-8-209852-13.png[/IMG]

Thanks

---

### Post by falconindy on 2009-10-16
Suppose you've got Jaunty running happily on drives sda1, sdb1, and sdb2. You decide to install a third drive, sdc, and split it into a few partitions. You're installing, say, Karmic on sdc1 and sdc2. You obviously don't want to touch any of sda or sdb.

So, you're not using those paritions...

---

### Post by bit mad on 2009-10-16
Thanks... so it just means : leave this partition alone during the install...?
Is that all there is to it? :)

---

### Post by bit mad on 2009-10-17
If the silence means Yes....

no wonder I'm confused. How are we supposed to know that it means Do Not Use in relation to the install process rather than in general afterwards? Actually it sounds obvious *NOW*... now that I know... but in my confusion it certainly wasn't :)

Wouldn't it make more sense to change this control ... ? :

Label : "**Use as:**"  changes to become "**New Filesystem:**"
Option : "**do not use the partition**"  to become "**leave unchanged (NTFS)**" where the actual filesystem is detected and shown in the brackets?

---

### Post by 3rdalbum on 2009-10-17
There are bigger problems with the installer :-)

---

### Post by bulldog on 2009-10-18
By default it won't use the partition,but you can use it if you want and change it to / , or /home or whatever.
I think this is done for safety reasons,if you change the option, partition manager assumes you know what you're doing.
You won't be the first one to overwrite the wrong partition by accident and now you'll have to think about it :)
But it can be confusing I have to admit.

---


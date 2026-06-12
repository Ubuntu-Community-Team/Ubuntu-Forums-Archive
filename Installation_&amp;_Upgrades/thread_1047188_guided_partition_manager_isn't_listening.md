---
title: "guided partition manager isn't listening"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by nunyez on 2009-01-22
I have a 160gb drive that I am using. I want to have my linux install on a 30gb partition, and the other 130gb on another partition for spare space. I cannot get this to work. I currently have a ~650mb partition with ubuntu on it, and the rest was formatted as another partition. Read below to find out everything I have already tried.

I did a fresh install last night. At first, the install wizard kept trying to use my 500gb usb external drive as the installation drive. I ended up having to power it down for the wizard to stop. I have an existing partition on my 160 that is a 30gb/130gb split. I ran the wizard again and it wanted to use the entire drive, I tried the manual config but it wouldn't allow me to set this config (30/130) either. So I tried a third time after using gparted manually to specify a 30gb/130gb ext3 setup (both primary partitions, the 2nd one following an extended partition). I forgot about the swap space and ran the wizard. It only wanted to use the 130gb side of things. So a fourth and final time, I used gparted to delete the 130gb partition, leaving a 30gb part and the rest unallocated. This the wizard picked up fine, however after install I see that it didn't do that at all. I have my OS in a ~650mb install, and the rest was formatted as another partition.

Okay so it only left enough room for the os install on the first partition, where do my apps that I have installed get installed to? The other 159gb part?

---

### Post by Pumalite on 2009-01-22
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by nunyez on 2009-01-22
I want a complete ubuntu install, no windows, no dual boot.

This is what I was going for:
[IMG]http://www.psychocats.net/ubuntu/images/partitioning7.png[/IMG]
" If you choose to create a separate /home partition, allocate between 5 and 10 GB for the / partition—that's about all you'll need for the Ubuntu system and programs. The rest should be for your personal files (in /home). "

I tried to do that... did I do something wrong?

---

### Post by Pumalite on 2009-01-22
Looks good to me.
Your system goes in '/'
Your /home, settings and the rest in the /home partition.

---


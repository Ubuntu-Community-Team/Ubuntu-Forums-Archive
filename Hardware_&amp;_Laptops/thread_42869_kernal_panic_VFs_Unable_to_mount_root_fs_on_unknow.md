---
title: "kernal panic VFs Unable to mount root fs on unknown block"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by anthony23 on 2005-06-19
I tried Ubuntu before on a pentium one machine and could not get it to get the net cause it didn't agree with my router, that was with Warty and now Hoary seems to have fixed this and I got a newer machine: pentium 2, I decided to buy a big hard disk and run it as a sever and workmachine in my house using Ubuntu. 

Everything was going fine, I had a 200gb disk storing all my music and films and accessible on the network using samba until there was a power cut that led to not one, but many problems...

First problem 
when the power came back the monitor didn't, it was old and missing pins so I threw it out and borrowed one from a friend - this one didn't work but I tested it on all the other machines in my house and it worked fine with them.  so at this point, i just want my disk with all my music and films don't really mind if its in an older machine...

so I switch it to a pentium 1 box which I tried to install Ubuntu on before (warty)

Second problem
I tried booting from the drive in normal and rescue mode, it hung-up and recieved this message: 

/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such directory
kernal panic VFD Unable to mount root fs on unknown block (0,0)

live cd wouldn't boot either

Aaahh!! despair

The disk has four partitions hda4 - Ubuntu (5gig) hda3 - music (189 gig share) hda1 (swap) and hda2 empty (5gig) 

As I remembered Damn Small Linux ran well even off the cd so I tried to use that to mount the disks and navigate around to check the files were all sound. 

After some effort I managed to do this mounting the hda4 (ubuntu) and hda3 (music)
as root. I've run fsck and there doesn't seem to be any problems with the filesystem , I can (if I buy an external hard drive) save all my data now. What I would like to know is how I go about repairing the Ubuntu filesystem and if possible getting it to boot in the machine I've moved it to, whilst preserving the partitions. 

Please let me know if anyone can help me with this or has any bright ideas about how to go about this a better way. ](*,)

---

### Post by thagame on 2005-07-01
kernal panic VFD Unable to mount root fs on unknown block (0,0) means its trying to use /dev/hda1 as your ubuntu drive. if its hda4 then grub should be using (0,3) as the root fs.check your /boot/grub/menu.lst and make sure it reads properly. for example mine is hda2 and says 

> root            (hd0,1) 

yours should be (hd0,3)

---


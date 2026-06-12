---
title: "Urgent Help Needed"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by davkasayres on 2007-09-12
Hi,

I work for a small computer firm in Borrowash, Derby.

The problem we have is that we needed a way of backing users machines up. Eg. Copying their files to another location and then back again once we had fitted a new part. I thought ubuntu would be good for this sort of thing. When you try this process in a windows environment, all you keep getting is permission errors.

So, i installed ubuntu on a machine we built for this task. Installation went well, installed and up to date but here is where i hit the bad stuff.

We have a sata pci card installed in that machine so we can access customers sata drives. Ubuntu finds it fine and finds the drive(s) plugged into it. I can mount these drives and read from them, so i can copy the data i need to get, but i cant write to the hard drive.

Now, i know of a program called ntfs-3g, something like that?

Ive installed this, and configured it. (Selected the external drive option because the internal one is grayed out).

Still cant write to NTFS.

Im using nautilus as my file manager, and im guessing that when you right click you should be able to make a new file but this is grayed out also.

I REALLY need to get this working as my workload is piling up and customers are getting unhappy.

Im not currently at that machine but ive got about 2 hours in the morning to try and fix it in the morning, else im up a certain creek without a paddle.

Please, Please, PLEASE someone help me!

Thanks,

Dan

---

### Post by frith on 2007-09-12
Okay, so I'm not an expert on this subject, but I have a few thoughts (I have Ubuntu dual booting with a winXP NTFS partition on my laptop)

I can read the NTFS drive using Nautilus, but I can't write using the default installation. The reason for this is that the support for NTFS in linux isn't 100% guaranteed, and there is a chance that writing to the drive can corrupt the whole volume!

I do know that there are drivers that support reading and writing to NTFS volumes, ntfs-3g is one of them. I assume you have gone through the process here: 
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)
If that doesn't work, (don't forget you have to start the service with gksu ntfs-config) then I'm not much help I'm afraid. I've never tried to write to the NTFS partition. I might give it a try...

On a different note, it sounds like what you are doing would be better served by a ghost type process - this is a lower level copy of the hard drive exactly (a little like a CD ISO) that reads literally everything and later you can put everything back exactly as it was. This is a fairly common procedure in corporate environments (this is the 'standard image' thing that you hear about sometimes). Try this for ideas: [http://en.wikipedia.org/wiki/Ghost_(software](http://en.wikipedia.org/wiki/Ghost_(software))

Frith.

---

### Post by davkasayres on 2007-09-13
Thanks mate,

Im at work in about 30 mins, so i'll give it a blast. Thanks for replying.

---


---
title: "Here we go again..."
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by Christos on 2006-01-11
__I really have no idea why i'm getting this error message while trying to install. Last month i downloaded Ubuntu from Europe(Greece) and i installed it on a laptop just fine. Stupid of me left the CD for my brother. Now i'm back in the States and i'm having trouble with the one i downloaded here!!! 

My partitions:

1 primary 6.4GB ntfs
2 primary 51.5GB ntfs
4 primary 35GB ext3
   logical  542.9MB free space
6 logical  1.5GB swap
5 logical 5GB fat32 

Here's the message i'm getting while tryig to install the BASE system:

[U]"The debootstrap program exited with an error (return value 1)
CHECK /target/var/log/bootstrap.log for details."[/U]


:confused: :confused: :confused: 

And i click CONTINUE, and i get another error msg:

_"Base system installation into /target/ failed."_

Can someone help me figure out what's going on please?
Can't believe i left the CD at my bro back in Greece..thought Ubuntu
would be 100% most reliable when it comes to dowloading/installing...
i guess it must be something i'm doing wrong. 
I've ordered the CDs just to be safe but that takes 5-6 weeks to arrive.

Help anyone? :(

---

### Post by miahfost on 2006-01-11
Hello there,

Your debootstrap issue is a fundamental one. Debootstrap is usually used to "take over" a machine, convert it from another distribution into debian. Perhaps Ubuntu uses this though I am not certain.

If you can download a ISO from the web and burn it to CD then re-install, or perhaps you can use the debian net image and install that to disk, those might be options.

---

### Post by Christos on 2006-01-11
ISO....? If you mean the Ubuntu distribution, i downloaded it several times and it gives me the same problem. I dodn't quite understand why "debootstrap" stands in my way...after all i'm trying to install it on a formatted partition. Nothing else is on there and my disk is completely defragmanted, so there shouldn't be any files in the way. :confused: 

> use the debian net image and install that to disk

can't figure this one out.....you mean install a Debian GNU ? 


Thanks for your response! I'm desperate to figure out what's wrong.

---

### Post by miahfost on 2006-01-11
Hi Christos,

Sorry about being vague with the debian net install thing. I will try to be clearer. One thing that might help is when you post in the forum you include a detailed subject line, this will get people to look more closely at your post. People tend to ignore posts that are like "I have a problem . . ."

What does /target/var/log/bootstrap.log say?

---

### Post by Christos on 2006-01-11
That's true...thanks for correcting me and i appreciate it.
Too late to change it though now.

---


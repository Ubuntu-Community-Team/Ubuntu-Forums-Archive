---
title: "installed 9.04, and my partitions are empty.. where did I go wrong?"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by fortyG on 2009-09-08
I just installed 9.04, and I followed these instructions 
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
hoping to " reinstall all the system files and still preserve your music, bookmarks, and photos." But it seems 9.04 installed right over all that I was hoping to preserve. 

Using terminal, "sudo fdisk -l" gives the result:[INDENT]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00014448

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4255    34178256   83  Linux
/dev/sda2            4256        9729    43969905    5  Extended
/dev/sda5            9379        9729     2819376   82  Linux swap / Solaris
/dev/sda6            4256        9378    41150434+  83  Linux

Partition table entries are not in disk order
[/INDENT]I *guess* that looks right. Does it? I had set up two partitions, / & /home, and there was also a swap partition. If I boot from the cd, there they are on the desktop, two hard drives, both virtually empty. 

I don't understand whether I did something wrong, had unrealistic expectations (did I misunderstand the purpose of this process?), or if this just doesn't work sometimes for reasons that aren't my fault. Even if I never recover my data I will feel better if I can find out why this happened.

---

### Post by raymondh on 2009-09-08
> **fortyG said:**
> I just installed 9.04

 If I boot from the cd, there they are on the desktop, two hard drives, both virtually empty. 

I don't understand whether I did something wrong, had unrealistic expectations (did I misunderstand the purpose of this process?), or if this just doesn't work sometimes for reasons that aren't my fault. Even if I never recover my data I will feel better if I can find out why this happened.

Sorry.

Prior to creating a separate /home, I am assuming you had a working Ubuntu.

When you installed 9.04 to create a separate /home, did you reformat after selecting mountpoints root and /home?  If so, then you overwrote the old Ubuntu effectively erasing your old files as both system and home files were within root.

For future reference and now that you have a /home ..... when you need to re-install root (/), just reformat the root (/).  In fact, when that time comes, you also select mountpoint /home but DO NOT REFORMAT /home.

Again, sorry if you have lost files.

---

### Post by aesis05401 on 2009-09-08
Just to clarify, you create a separate home partition so that the next time you install/reinstall for any reason you can leave the /home partition alone and all your data will live there without being touched. 

If you did not have an existing installation with either a separate /home partition or a separate data partition in general (D: or whatever in Windows) then the process you followed would not have helped you.  

Going forward you will now be safe to install/reinstall whatever OS you want so long as you do not overwrite the /home partition you have created.  

Out of curiosity, what were you installing over the top of?

---

### Post by fortyG on 2009-09-08
So that's it. It's a preparation for some future installation. 

I was installing over 7.04. 

What if I'd done this instead?
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Or something like it, anyway. Partitioned the drive before installing 9.04.

---

### Post by raymondh on 2009-09-08
> **fortyG said:**
> So that's it. It's a preparation for some future installation. 

I was installing over 7.04. 

What if I'd done this instead?
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Or something like it, anyway. Partitioned the drive before installing 9.04.

Yes.

Again ... am sorry you lost files.  Now is the time to reconsider your back-up plans/strategy.  Rsync (along with grsync - GUI based) is a good program.

'Safe Ubuntu-ing.

---

### Post by fortyG on 2009-09-08
> **raymondhenson said:**
> Yes. 

Yes to this [SIZE=2]
*>So that's it. It's a preparation for some future installation. *[/SIZE]
 or yes to this?
[I][SIZE=2]>What if I'd done this instead?
[>http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")
>Or something like it, anyway. Partitioned the drive before installing 9.04[/SIZE][/I][SIZE=2]
Or yes to both?

I am just curious whether the latter could have worked. 

[/SIZE][SIZE=2]I've been planning to buy an external drive because I will soon need to be able to bring data back & forth to work, I guess I will plan to use it for backups too, once I have accumulated some files. [/SIZE]

---

### Post by raymondh on 2009-09-09
> **fortyG said:**
> Yes to this [SIZE=2]
*>So that's it. It's a preparation for some future installation. *[/SIZE]
 or yes to this?
[I][SIZE=2]>What if I'd done this instead?
[>http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")
>Or something like it, anyway. Partitioned the drive before installing 9.04[/SIZE][/I][SIZE=2]
Or yes to both?

I am just curious whether the latter could have worked. 

[/SIZE][SIZE=2]I've been planning to buy an external drive because I will soon need to be able to bring data back & forth to work, I guess I will plan to use it for backups too, once I have accumulated some files. [/SIZE]

Yes on the psychocats tutorial.  As for pre-partitioning, you would've still lost files when you reformatted because in your previous ubuntu, /home resided within root.  Another option would be to do a network upgrade until 9.04 and then do psychocats' tutorial and separate /home.  From then on, any reinstall would be just on the root part.

For backup, I have been using a 2-pronged approach (as recommended by another forum friend).  I use rysnc to do regular back-ups and, use [PING]("http://ping.windowsdream.com/ping.html") to create and image of my installation.  That way, should I lose rsync, I can still have PING to restore everything (including how I set up Ubuntu).  If I lose PING, I can use a liveCD, reinstall and/or recover files from rsync.

---

### Post by Bartender on 2009-09-09
Something else I found out the hard way, and is rarely mentioned.

Let's say you are doing everything right.  
You manually created a separate home partition the first time you installed.
Now you're installing a newer version, and you make sure the "Format" button next to the /home partition is NOT checked.

But you decided to give yourself a different username/password.

Big mistake.  You'll end up with TWO /home folders, the existing one and a new one inside the / partition.

So, make sure to use the same username/password!

---

### Post by raymondh on 2009-09-09
> **Bartender said:**
> Something else I found out the hard way, and is rarely mentioned.

Let's say you are doing everything right.  
You manually created a separate home partition the first time you installed.
Now you're installing a newer version, and you make sure the "Format" button next to the /home partition is NOT checked.

But you decided to give yourself a different username/password.

Big mistake.  You'll end up with TWO /home folders, the existing one and a new one inside the / partition.

So, make sure to use the same username/password!

+ 1 bartender.

---


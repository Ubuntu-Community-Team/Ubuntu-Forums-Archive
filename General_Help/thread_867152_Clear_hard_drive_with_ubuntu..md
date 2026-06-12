---
title: "Clear hard drive with ubuntu."
date: 2008-07-22
forum: General Help
---

### Post by Chaoskeeper56 on 2008-07-22
How do i completely clear my hard drive on ubuntu? I just want to know this, i don't want to backup anything, i don't want to be warned not to, i just want to clear my hard drive all together. So please tell me how to do so.

---

### Post by bigken on 2008-07-22
boot from the live cd and run gparted

---

### Post by Potatoj316 on 2008-07-22
Im going to assume you want the OS gone as well.  That was clearing the HD means

Its kind of strange that you want to do this but ok.  **Be extremely with the following instructions/commands**

There are many ways to do this, first you could use this command **be extremely careful, do not execute unless you want your entire hard drive gone** sudo rm -rf /

you could also boot with your live cd and use gparted to format or partition the HD

---

### Post by Chaoskeeper56 on 2008-07-22
> **Potatoj316 said:**
> sudo rm -rf /

I then get this error (cannot remove root directory `/')

---

### Post by tamoneya on 2008-07-22
the best way to 100% wipe a drive is with dban.
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

Just pop the live CD in and point it at the drive and your data will be gone beyond any hope of recovery.

---

### Post by Potatoj316 on 2008-07-22
everyone freaks out when they see rm -rf, i use it many times (but yes still be careful) but in the previous responce runing it with root priveleges and on the root of the drive resulted in an error, what?!? if that is the case why is everyone so scared of it.  (i meant to try it last time I reinstalled, which does not happen often, if ever)

---

### Post by tamoneya on 2008-07-22
> **Potatoj316 said:**
> everyone freaks out when they see rm -rf, i use it many times (but yes still be careful) but in the previous responce runing it with root priveleges and on the root of the drive resulted in an error, what?!? if that is the case why is everyone so scared of it.  (i meant to try it last time I reinstalled, which does not happen often, if ever)

Because if you start typing it and you arent careful and you hit enter before typing the full path you could very easily wipe out your entire system unintentionally.  There are no prompts asking you whether you really mean to delete what you asked.  If you really have to use it you should consider dropping the "-f" which is force and possible adding a "-i" for prompting.  Also it can also be presented in a malicious way to a inept user who doesnt know what they are doing.  Some people find it funny to delete someone elses system.  Overall it isnt a good idea to use the command and you shouldnt ever need to use it as there are better ways to accomplish this typically.  Please try not to recommend it so lightly.

---

### Post by Rocket2DMn on 2008-07-22
I suggest just booting from either the Ubuntu LiveCD or the GParted LiveCD and deleting the partitions.  If you are on the Ubuntu LiveCD you may need to unmount the swap partition first since you can't delete mounted partitions.

---

### Post by Potatoj316 on 2008-07-22
Ok first note my first post here and note what the person wanted to acomplish.  I did not recomend it lightly and the result of the command is what the person wanted to accomplish.  Also note the error the person got, aparently it didnt work (or it did and i dont see the problem)

---

### Post by bigken on 2008-07-22
> **rocket2dmn said:**
> i suggest just booting from either the ubuntu livecd or the gparted livecd and deleting the partitions.  If you are on the ubuntu livecd you may need to unmount the swap partition first since you can't delete mounted partitions.


+1

---

### Post by Chaoskeeper56 on 2008-07-22
> **Rocket2DMn said:**
> I suggest just booting from either the Ubuntu LiveCD or the GParted LiveCD and deleting the partitions.  If you are on the Ubuntu LiveCD you may need to unmount the swap partition first since you can't delete mounted partitions.

Thing is though, i don't know how to do that! I know how to boot from the LiveCD, but then after that i'm stumped.

---

### Post by Rocket2DMn on 2008-07-22
From the Ubuntu LiveCD, go to System->Administration->Partition Editor
To unmount swap you can right click the partition and select Unmount from within GParted.

If you use the GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) - it should pop up with GParted automatically.

---

### Post by Potatoj316 on 2008-07-22
System-> Administration->GParted then choose to delete the partitions and recreate them as something else (or leave them unallocated and waste the space)

---

### Post by bigken on 2008-07-22
use gparted live cd hassel free belive me

---

### Post by Chaoskeeper56 on 2008-07-22
> **bigken said:**
> use gparted live cd hassel free belive me

i don't have a blank CD or flash drive to put it on. 

Honestly, i just want the hard drive wiped clean, But so far none of these many answers can help me. Isn't there a way to do this without downloads like you can in windows? (Don't accuse me of being a microsoft fanboy or whatnot, cause i'm just asking a question)

---

### Post by Rocket2DMn on 2008-07-22
You need some sort of CD or bootdisk since you can't delete partitions that are mounted (namely, your root partition).  This can be done with LiveCDs or programs on floppies, like killdisk or dban (Darik's Boot and Nuke)

---

### Post by Potatoj316 on 2008-07-22
you could go through carfully using rm -rf (you will need a sudo) for each directory in /, but it should work in /.  Why cant one of those people who tries to brake other people's computer be here now to help?  If its so easy why cant we do it?

---

### Post by rbc on 2008-07-22
Here's my favorite. Boot the LiveCD, go to terminal and type:
dd if=/dev/zero of=/dev/sd*x*(or however your hard drive is recognized. This will write zeros to the whole drive. In my experience, it takes about two minutes per GB

---

### Post by Potatoj316 on 2008-07-22
Would that dd command have to be root to run?

---

### Post by Chaoskeeper56 on 2008-07-22
alright, i tried the partition thing with the live disk. I can change the first one that was ext3. but then theres two more that i can't change called Extended, and then theres an arrow that opens something beneath that called Linux-swap.

But are you sure theres no way to reset my hard drive to a "Factory default" or just to make it so theres no OS on it and i can just add a new one?

---

### Post by Rocket2DMn on 2008-07-22
You need to delete the swap partition inside the extended partition first, then you can delete the extended one.
If you want to install another operating system, you can go ahead and tell it to use the whole disk, thus deleting any existing partitions.  You will likely see a partition table during the install process where you can choose to delete the existing ones.

---

### Post by bigken on 2008-07-22
why dont you go to makers web site and see what they have to wipe/format their drives

---

### Post by Elfy on 2008-07-22
You need to turn swap off, in a terminal

```
sudo swapoff -a
```

should be able to do it in partition editor now

---

### Post by bigken on 2008-07-22
you are making very hard work of a very simple thing use gparted live cd start from the  bottom of the list and delete the partitions one by one

---

### Post by Elfy on 2008-07-22
> **bigken said:**
> you are making very hard work of a very simple thing use gparted live cd start from the  bottom of the list and delete the partitions one by one

+1

---

### Post by Potatoj316 on 2008-07-23
Like someone else said, you dont need to wipe the hard drive to install a different OS, just install the OS and say use the full drive.

---

### Post by Edigido on 2008-07-23
I'm trying to get a new os on my computer as well, and when I tried to install the new OS, it came up with an error that said it couldn't recognize the hard disk.

---

### Post by bigken on 2008-07-23
> **Edigido said:**
> I'm trying to get a new os on my computer as well, and when I tried to install the new OS, it came up with an error that said it couldn't recognize the hard disk.


you may need to change a setting in the bios ie raid sata or ide

---


---
title: "How to install lots of OS's?"
date: 2008-08-22
forum: General Help
---

### Post by Gondee on 2008-08-22
So i have been using Ubuntu for a while now, and i like it, it was the first linux distro i tried and it left a good impression. But that hasn't stopped me from wanting to try the other ones..

So, i just got a 1TB drive. And i was hoping that i could install 10 Linux's Distro's on it each with about 100 gigs.

How would i go about doing that?? 

I know how to partition 4+ and i have herd of the GRUB deal.

But i dont know where to begin. So if some one could just point me in the right direction....

I have hurd that many OS's on one hard drive dosn't work to well, is there any magic number here?

Thanks

---

### Post by ugm6hr on 2008-08-22
> **Gondee said:**
> So, i just got a 1TB drive. And i was hoping that i could install 10 Linux's Distro's on it each with about 100 gigs.


You could probably get about 50 distros on that drive.  1 swap partition to share between them is all that's required.

I don't think GRUB will care how many you have.

---

### Post by Gondee on 2008-08-22
lol, i dont even know of that many. 

Would ubuntu detect and allow me to boot from all of them with Grub if i installed it last?

---

### Post by ugm6hr on 2008-08-22
> **Gondee said:**
> Would ubuntu detect and allow me to boot from all of them with Grub if i installed it last?

In theory - yes.

Ubuntu installs Grub to the MBR of the 1st HD - so if this is a second HD, be wary.  You may find your 1st HD becomes unbootable without this one installed (unless you install GRUB to the MBR of this HD, and make this HD the first boot device).

GRUB also normally auto-detects all partitions, and gives a list of options.  However, I hear from other's that it is not foolproof.  So you may have to manually add the distros if it doesn't work.

---

### Post by sandysandy on 2008-08-22
i had installed about seven linux distros at one instance.

Ubuntu is by far the best in detecting other distros, followed by OpenSuse11.

Mandriva did not detect any other OS other than Windows.

so as said in above post, u can add distros manually to menu.lst file, if required.

regards

---

### Post by Gondee on 2008-08-22
> **ugm6hr said:**
> 
GRUB also normally auto-detects all partitions, and gives a list of options.  However, I hear from other's that it is not foolproof.  So you may have to manually add the distros if it doesn't work.


Is there a guide to adding them manually. Sorry im a noob, lol


This will be my second hard drive, the first being a 750Gig that is for windows only. But i plan on Physically disconnecting it from the computer. Iv installed vista enough times this week messing with this GRUB

**Thanks for the help guys!**

---

### Post by ctswhole on 2008-08-22
This is something I've thought about doing before too.  I have a 500G HD and from what I understand it's possible to partition the hard drive in such a way that you have a separate home partition and multiple other partitions for different OS's and a swap partition that is shared by all.  I would be interested in trying out a setup like that once I get a better understanding of how to set something like that up.

---

### Post by Gondee on 2008-08-22
> **sandysandy said:**
> 
Ubuntu is by far the best in detecting other distros, followed by OpenSuse11.


Iv hurd its extra buggy when there's that many installed. Is that true? And did yours detect them or did you have to add them manually?

Thanks

---

### Post by sandysandy on 2008-08-22
> **Gondee said:**
> Is there a guide to adding them manually. Sorry im a noob, lol


This will be my second hard drive, the first being a 750Gig that is for windows only. But i plan on Physically disconnecting it from the computer. Iv installed vista enough times this week messing with this GRUB

**Thanks for the help guys!**

see these

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

[http://www.linux.com/feature/113898](http://www.linux.com/feature/113898)

regards

---

### Post by Ayuthia on 2008-08-22
> **Gondee said:**
> So i have been using Butane for a while now, and i like it, it was the first linux distro i tried and it left a good impression. But that hasn't stopped me from wanting to try the other ones..

So, i just got a 1TB drive. And i was hoping that i could install 10 Linux's Distro's on it each with about 100 gigs.

How would i go about doing that?? 

I know how to partition 4+ and i have herd of the GRUB deal.

But i dont know where to begin. So if some one could just point me in the right direction....

I have hurd that many OS's on one hard drive dosn't work to well, is there any magic number here?

Thanks

If you know how many OS's you are going to install, I would go ahead and partition the drive to support them.  If you are going to have extra space (it doesn't sound like you plan to do this), make sure that it is at the end.  I say this because shrinking a partition so that you can create a new one takes a lot of time.  And if you have a logical partition that is large and is in the middle of the group, you will have to shrink and move other partitions because you can only create a new partition at the end (not for sure if that made any sense).

I currently have four (five if you consider the recovery partition) running on my laptop (Vista (for BIOS updates), Arch, Ubuntu Hardy, and Ubuntu Intrepid.  My mistake is that my Arch partition is the largest of the four if I need to add another partition, I have to shrink Arch, move Hardy over to the new empty space, then move Intrepid over to where Hardy previously lived just so I can create the new partition.

All the distros that I have installed all use GRUB so I just installed GRUB on Arch, but I did not do it for either one of the Ubuntu distros.  I just grabbed the info from the Ubuntu distro's /boot/grub/menu.lst and added it to the menu.lst in Arch.  You should also verify the UUID of those partitions instead of identifing them as /dev/sdX.  You can find the UUID by doing:
```
ls -l /dev/disk/by-uuid
```

Sorry for being long winded and possibly confusing, but overall, it really is not too difficult to do.  It is just installing a distro and configuring the master menu.lst.

As for the maximum number of partitions, I have not found it yet.  My desktop I think has eight (5 OS, one recovery, two storage partitions) and it is still happy.

I am not for sure if you really need 100 Gb for each distro.  I don't think that there will be that many applications that you can install.  You would be better off using the space for storage of data to share with all the other partitions.

---

### Post by sandysandy on 2008-08-22
> **Gondee said:**
> Iv hurd its extra buggy when there's that many installed. Is that true? And did yours detect them or did you have to add them manually?

Thanks

with ubuntu it generally detects the other OS.

i have not faced problems in booting multiple OS. some people though advice on using different user names to obviate problems when upgrading kernel.

regards

---

### Post by Gondee on 2008-08-22
Thanks for all the help guys, these fourms are great. =)

If i were to install all the distros. Am i forced to have only one /home partiton. Or are the seprated by the install. 

Thanks again, looks like i have some learning to do =)

---

### Post by ugm6hr on 2008-08-22
> **Gondee said:**
> If i were to install all the distros. Am i forced to have only one /home partiton. Or are the seprated by the install. 

Nope.

You can have 0 /home partitions (i.e. each distro would have a  /home folder **within** their own partition.

You can have a separate /home partition for each distro (I presume).

You can also have a single /home to share between each partition, although you can run into problems doing this, unless you use a different username for each distro (which would be confusing).

---

### Post by Dutch70 on 2008-08-22
> **ugm6hr said:**
> Nope.

You can have 0 /home partitions (i.e. each distro would have a  /home folder **within** their own partition.

You can have a separate /home partition for each distro (I presume).

You can also have a single /home to share between each partition, although you can run into problems doing this, unless you use a different username for each distro (which would be confusing).

It wouldn't be confusing if your user name had the system name if front of it for each distro. ie...ubuntu Gondee, opensuse Gondee, mandriva Gondee, you get the point...:)

---

### Post by ugm6hr on 2008-08-22
> **Dutch70 said:**
> It wouldn't be confusing if your user name had the system name if front of it for each distro. ie...ubuntu Gondee, opensuse Gondee, mandriva Gondee, you get the point...:)

Simple, yet effective solution. Nice.

---

### Post by Gondee on 2008-08-22
I'll defently be doing it. Im shooting for 7-10 os's. i think ill share the /home folder so i can move data about and make use of all of them. 

This is going to be fun =)

Thanks for all the help guys. I thanked each and everyone of you =)

---

### Post by snowpine on 2008-08-22
May I suggest an alternative? You can use virtual machines (VirtualBox etc) for each distro. Then you can have multiple distros running at once (limited only by your ram) and alt-tab between them, or even tile them on the same screen. If your goal is to learn more about the distros and get some experience, this is what I'd recommend.

---

### Post by Gondee on 2008-08-22
Heres the next problem. Ubuntu didnt alutomaticly regonize them all. So i need to add them to grub. Problem is i cant open them to find out there kernal and that stuff. What to do here?

---


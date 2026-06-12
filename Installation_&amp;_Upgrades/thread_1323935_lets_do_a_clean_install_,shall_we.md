---
title: "lets do a clean install ,shall we?"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by Deicider on 2009-11-12
ok,i'v tried to upgrade,reinstall ,etc grub,but it wont work,soo
Clean install.

Want to install Windows Xp and Karmic.

I'v made installations many times that worked.
But i suppose i was lucky many times (:
Am now in live mode,formated the HD and waiting for "ideas"
So,what is the Most Right Way to do this?(was the "use largest continues space" installation type stupid?)
I have 150 gigs hd on my lap.
Share ur opinion.

---

### Post by louieb on 2009-11-12
:biggrin: control freak here.

With a clean hdd I will use Gparted and set up the partition layout before installing any OS. Both the Windows and Ubuntu have manual install options - you tell the installer - install the OS here.

---

### Post by ers11121 on 2009-11-12
Try setting up separate partitions, install each o/s to a different partition, use EasyBCD to setup boot order.
Ed

---

### Post by Deicider on 2009-11-12
hey control comrade,ok.
So,should i go.
1 partition -~70gigs ext4 (karmic)
2 partition -~4gigs swap
3 partition -~300mb boot
4 partition -~30 gigs ntfs windows
5 partition -~40 gigs of ext4 for any future other linux OS or just a safe version of linux..its for safety. (:

Is this ok?

---

### Post by Kevbert on 2009-11-12
What you'll need to do is install Windows XP first (it will use the whole disk), then resize the partition down to say 40Gb with gparted. Next using the Ubuntu install disk go for manual partitioning and set swap to a minimum of 6Gb if you want to be able to suspend and hibernate Ubuntu or any other Linux. Set the root partition (mounted /) to 40Gb ext4, home (mounted /home) to 40Gb ext4 and leave the remainder (free space) unformatted for now.  The reason for having a separate home partition is that you can then use it for other versions of Ubuntu and when you upgrade.

---

### Post by Deicider on 2009-11-12
Are you sure bout windows talking the whole disk?
Ok now,how exactly / and /home working?
The new versions will be installed in home or root?
But home needs to connect with root..or smth? 
:$

---

### Post by darkod on 2009-11-12
With all the respect to the other poster, do NOT install XP on the whole disk.

The data will not be written sequentially so when you resize you will probably have to move data. That can make XP files corrupted and even if it doesn't moving the data and resizing partitions is time consuming.

Why would you install XP on whole disk when you plan to dual boot? Why create ntfs partition of the whole disk and then plan to resize it immediately?

The idea to use Gparted (one option is from the ubuntu live cd) to create your partitions is perfect.

Boot up with ubuntu live cd, start Gparted, delete all current partitions.

Then create first primary ntfs for XP, size as per your requirements.

From there, you can continue creating partitions or just boot up with XP disc, install it on the created partition. Then boot with ubuntu disc, select Install option, and create rest of partitions in the Manual Partitioning part of the instalation process (provided you have't created them at the start).

Of course, before starting all this it is assumed you have all your data backed up.

PS. Always use manual partitioning when installing any OS. You want to control your partitions even if you're not a control freak. :)

---

### Post by audiomick on 2009-11-12
Hallo.

Go and look at this:
[http://ubuntuforums.org/showthread.php?t=1321649](http://ubuntuforums.org/showthread.php?t=1321649)

The discussion is about much the same thing.

In summary:
Use Gparted, either itself as a live CD, or from the Ubuntu Live CD to set up your disc.
Choose a size for the windows partition, and make an appropriate ntfs partition
Install Windows. The installer will only see the ntfs partition if you don't run the windows partition tool. Only giving it the room you want it to have seems to be better than trying to reduce the size of it's partition later (see link above)
Install Ubuntu into the remaining space. The Ubuntu installer will see the windows install and offer to install next it, leaving it alone.
You can have already set up your Linux partitions in the first step. If not, you can then set up the rest of the disc for Ubuntu during the install process

It is a good idea to have a separate partition for / and for /home. Dividing up more than that only seems to be an advantage for people who already know why that is a good idea. Too complicated for me...

Your / partition ( the OS lives here ) shouldn't need to be more than 10 - 15 GB. Mine, an Ubuntu Studio with everything installed and lots more additional programs over the last 18 months, has only got just under 6 GB in it.

Your /home partition ( all your data and all your personal config stuff, e.g. desktops setup, evolution settings etc., lives here ). Should be as big as you can make it. It is separate from / so that in the event of a fresh re-install sometime later, you can hopefully retain it and save your files and settings 

In order to transfer files between Windows and Linux, you will need a partition that they both can read. 
This could be a separate ntfs Data partition, which would need to exist during the windows install so that windows can find it.
Another alternative is something like this:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
in which case there needs to be an Ext2 partition somewhere. This can be created during the Ubuntu install. When you then install the fs-driver thing in windows, it will go off and find this partition.

Another thing:
Linux should be given a swap partition. This should be comfortably larger than your RAM, e.g. 2GB RAM, = ~2.5 GB swap. I am not a computer professional, I am only quoting what I have read elswhere and tried out for myself, so I can't give you a definite figure, but the reason is, the swap needs to be big enough to write the whole RAM into it so that suspend and hibernate functions can work. (Mine don't... )

Hope this is a help
Michael

---

### Post by louieb on 2009-11-12
> **Deicider said:**
> ...So,should i go....

its best to install Windows in a primary partition. 
20GB for a Ubuntu install is more than enough. Make both Linux install partitions the same size. 
Create a partition for data - keep it out of way when reinstalling or upgrading. 
Have read 2GB is the max usable size for swap.  
Why the /boot partition? 

Something like this: [IMG]http://louboldt.com/ptwocents.gif[/IMG]

[LIST]
[*]Primary partitions
[LIST]
[*]Linux 1 20GB
[*]Linux 2 20GB
[*]Windows 30GB
[/LIST]
[*]extended (logical partitions)
[LIST]
[*]data 70GB
[*]swap
[/LIST]
[/LIST]

---

### Post by Deicider on 2009-11-12
> 
It is a good idea to have a separate partition for / and for /home. Dividing up more than that only seems to be an advantage for people who already know why that is a good idea. Too complicated for me...

Your / partition ( the OS lives here ) shouldn't need to be more than 10 - 15 GB. Mine, an Ubuntu Studio with everything installed and lots more additional programs over the last 18 months, has only got just under 6 GB in it.


Even if there are in separate partitions / and /home will read eachother?
What if i have 2 / and 1 /home and vice versa?

I suppose i'll do something almost like another m8 posted:
create
3 primary paritions ; xp, root linux and another for future use.
2 extended:
1 swap 
1 boot(all linux distros share the same boot partition right?)

What about grub? where it is stored? So make sure i wont have problems.
> 
In order to transfer files between Windows and Linux, you will need a partition that they both can read. 
This could be a separate ntfs Data partition, which would need to exist during the windows install so that windows can find it.
Another alternative is something like this:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
in which case there needs to be an Ext2 partition somewhere. This can be created during the Ubuntu install. When you then install the fs-driver thing in windows, it will go off and find this partition.

Well,i remember windows can't linux while linux can.
And when i copy paste a file from linux to windows ;i boot from windows and its there fully working.
So its already cool i think.

---

### Post by darkod on 2009-11-12
You're almost there. :)
Here is my setup on 250GB drive if it helps:
Primary
C: ntfs Win7 65GB
D: ntfs Data 141GB (readable to both OS)
/   ext4 15GB
Logical
swap 2GB
/home 10GB

Adjust as you will but basically I don't think you need more than this. I am not worried if /home is smaller than / because I have the whole 141GB data partition readable to linux too.

PS. Grub is stored on the MBR (Master Boot Record) of the hard drive. Don't worry about grub, it knows where to go. :) Likewise, no need for separate /boot as partition, not unless you really need it for your purposes. There will be boot folder created in / anyway unless there is separate partition (mount point).

---

### Post by Deicider on 2009-11-12
MBR is a standard for all HDs?
Grub is stored there by linux and windows saves files there too?

Unfortunately for the whole solar system grub dont know where to go :/
Grub is the reason i reformat everything :S

Maybe installing /boot as a separated partition will work for every distro i use or try.Or maybe should be better all distros have their own boot in their root..dunno

---

### Post by audiomick on 2009-11-12
> **Deicider said:**
> Even if there are in separate partitions / and /home will read eachother?
During the installation you choose manual partitioning. In this section you tell the tool where each partition is to be mounted.
> What if i have 2 / and 1 /home
I'm guessing a bit here.
If you have an existing and functional /home partition, you should be able, during the installation, to mount it to any number of installations. That would be a bit like 20 people all using the same refridgerator.
> 
 and vice versa?
You could mount a partition that is a home folder into the file system of another installation, but it would not function as home in that sense. The installation can only deal with one "real" home, as far as I know

> I suppose i'll do something almost like another m8 posted:
create
3 primary paritions ; xp, root linux and another for future use.
2 extended:
1 swap 
a swap partition is, as far as I know, a swap partition. It is then neither a primary, nor an extended.

> 1 boot(all linux distros share the same boot partition right?)
You've lost me there. I can only say, I read recently that it is not necessary to make an additional partition for /boot. 

> What about grub? where it is stored? So make sure i wont have problems.
Don't know exactly where that ends up, but you can confidently let it take care of itself



> Well,i remember windows can't linux while linux can.
And when i copy paste a file from linux to windows ;i boot from windows and its there fully working.
So its already cool i think.
Yes, the Linux installation will be able to see the Windows partition.

---

### Post by Deicider on 2009-11-12
ok, i was playin with partitions until it said that i can't have more than 4.
I made a pri ntfs, a pri ext4 for root, a pri ext4 for home like you said,and a pri extended for boot and swap.
Should i make swap pri or exte partition?
R u sure bout boot?When i tried JJ without boot ,was not working.
Anyway,extended partitions dont suffer from speed or anything ,right?

---

### Post by darkod on 2009-11-12
You can have 4 primary partitions. The other option is 3 primary and 1 extended (with as many logical inside as you need).

No, you don't need /boot as separate partition (mount point). I just installed 9.10 3 days ago with the setup on my hdd I wrote you above.

If you decided to have pri ntfs for windows, pri ext4 for root, pri ext4 for home then for swap you can choose either pri or logical (extended). Extended partitions do not suffer with speed as far as I know. You simply have to have them if you need more than 4 partitions on a hdd.

---

### Post by Deicider on 2009-11-12
Couldn't i make a pri ntfs and an exte that would contain 3 logis -> root,home,swap.

---

### Post by audiomick on 2009-11-12
Hi. Don't know if it has worked, but I have tried to attach screens shots of gparted on my computer. On one of the two discs, there is a swap inside and extended partition, on the other as a pri. There are two ubuntus on this machine, the one that is running, and the one called test

The limit of 4 primaries is, I believe, a BIOS limit left over from the very beginnings of PC history. Extended partitions were introduced at some point to allow the creation of more than 4 partitions on one disc

---

### Post by Deicider on 2009-11-12
> 
Hi. Don't know if it has worked, but I have tried to attach screens shots of gparted on my computer. On one of the two discs, there is a swap inside and extended partition, on the other as a pri. There are two ubuntus on this machine, the one that is running, and the one called test

In the first hd you have 2 pris, ur root and systest.
So i can put the home directory in a exte.
Btw ur test root and home dont have / and /home,how do they work?

The other hd contains only a home and a swap,where is the root?

---

### Post by darkod on 2009-11-12
> **Deicider said:**
> Couldn't i make a pri ntfs and an exte that would contain 3 logis -> root,home,swap.

You definitely can. When creating the logical partitions in Gparted just make sure to select Logical type and that's it.

---

### Post by Deicider on 2009-11-12
Now i'v come to this,and i think its pretty good.

1.pri -ntfs-30 gigs for Xp-just to use some programs,and have fun (:
2.pri -ext4-15 gigs for Root (made it primary just in case)
3.pri -ntfs-30 gigs -for now data-this is ntfs only to be readable by both OS,i made it a pri actually so that later i can have the option to make it an OS.
4.exte-
 1-logi-ext4- 5 gigs for swap.
 2-logi -ext4- 70 gigs for home.

There.
Seems fine =)

---

### Post by audiomick on 2009-11-12
> **Deicider said:**
> In the first hd you have 2 pris, ur root and systest.
So i can put the home directory in a exte.

yes. In a thread I read today, somone even suggested to make an extended partition, and put the whole Ubuntu in there on various logical partitions.

> Btw ur test root and home dont have / and /home,how do they work?

The 3rd column, called "einhängepunkt" shows the mount point of the partitions. 
The 4th column, "Bezeichnung", is the name of the partition. They do not all have names, and it is not necessary, but I would recommend naming them so you know what they are when looking at them in 6 months time, e.g. with gparted, because something is playing up.

As you can see from the fact that there is not an entry in "Einhängepunkt" for every partition, they are simply not all mounted.

Another clue is the pictures of keys in the first column next to some of the partitions. These ones are mounted, and locked for Gparted, because it can't change a mounted partition.

If I were to reboot into the test system, there would then be:

a / in "Einhängepunkt" next to test-system on /dev/sda3 on the small disc /dev/sda and keys next to it

no / next to the unnamed main system partition on /dev/sda1, and no more keys next to it

> The other hd contains only a home and a swap,where is the root?
the /home on this disc is mounted, as you should be able to see after the previous explanation, as home on the currently running system, whose system partition is on the other disc at /dev/sda1

the swap on this disc is there because I read somewhere that two smaller swap files on two different discs is faster the one big one, because two get accessed alternately, like doing two things at once. Don't pay much attention to that, it may not even be true.

---

### Post by Deicider on 2009-11-12
just installed windows xp(when windows asked if i wanted to format that partition i selected 'no',cause it was formated by gparted..i think)

And now am about to install kk.
Am actually confused:
When i made the partitions as i described (in my previous post i think) the 'format' was done in few seconds...is that a format or just something visual?
And now the installer of kk asks me if i want to format the ext4 / mountpoint,i suppose is already empty.
:S

---

### Post by audiomick on 2009-11-12
Hallo
Don't know the precise process, but you can understand it like this:
If the installer is doing something to a partition, it involves a format as far as the installer is concerned, even if it is new and empty. The installer doesn't "believe" it is empty, and wants to do it itself

The only partitions that, at this point, don't get formatted are the ones that are not having there content changed. That is, if you have e.g. a pre -existing /home that you want to re-use, it will be mounted here but not formatted. If you have a partition that you are not mounting or using, it wont be formatted

If you get to a point where the installer is wanting to format something you know is to be left alone, e.g. the partition where your windows is, you need to go back a few steps and have a good look at what you have told it to do

---

### Post by louieb on 2009-11-12
> **Deicider said:**
> Now i'v come to this,and i think its pretty good...

Looks fine.

> 1 boot(all linux distros share the same boot partition right?)

Tried that once - it was a disaster come kernel upgrade time. 
> Couldn't i make a pri ntfs and an exte that would contain 3 logis -> root,home,swap.


That is one way. 

> What if i have 2 / and 1 /home 

Can run into trouble - ok if you don't use the same user names.

> and vice versa?
makes no sense.

> And now the installer of kk asks me if i want to format the ext4 / mountpoint,i suppose is already empty.

Does not matter. I usually let the installer format. 

:DLooks like your having fun today.

---

### Post by Deicider on 2009-11-12
I didn't let the installer format >.>

Anwayyy,ZOMGG i'v done it =D
It works,both work,and grub is fine 
Yay for me +_+

The funny thing is that the firs time i used dual boot (xp,ubuntu) was a year before and i had no clue of anything of this,and i did a perfect dual boot with not help from internet,just luck (:
The world is beutifull :0

until another error ruins everything...till then hurrah ;0

---

### Post by audiomick on 2009-11-12
good to hear it

---

### Post by Deicider on 2009-11-12
Many people including me have this kind of problem,from scratch install with correct background (paritions) and order is the medicine!

---


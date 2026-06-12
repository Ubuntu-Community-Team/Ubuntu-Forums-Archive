---
title: "[SOLVED] Help to Make Partitions like this..."
date: 2008-11-28
forum: General Help
---

### Post by polarworks on 2008-11-28
Hello :)
Hope that you all are doing great.
I am very new to Linux OS and just started using this Great looking Ubuntu today on my laptop acer aspire 3000. 

As I am new so I don't understand the way Ubuntu creates partitions of my drive. I have installed  Ubuntu 8.10 successfully and its working fine. During installation it has occupy all drive for Ubuntu but I want to know How can I make partitions of my drive as I use to do with Windows. My drive is 40 GB and when I use to be with Windows I have always made partitions like this:
C: for Windows Installation (20 GB)
D: for my documents and files (20 GB)

So by this way whenever I get some big problems with my Windows then I easily format the drive and install fresh windows and all my files on D: drives were safe and untouched.

So now if you can please help me to archive the same as I defined above.
C: for Ubuntu and Programs installation (20 GB)
D: for my personal files (20 GB)


Thank you for reading and looking forward for your help.

---

### Post by bruce2000 on 2008-11-28
Hi,

You can use a program called gparted to partition your hard drive the way you want, it's on the ubuntu live cd.

Have one 20gb partition for root and another 20gb partition for home. This is the equivalent to the partitions you have on windows.

btw, its a good idea to backup your data before working on partition

---

### Post by Bruce M. on 2008-11-28
> **polarworks said:**
> 
So now if you can please help me to archive the same as I defined above.
C: for Ubuntu and Programs installation (20 GB)
D: for my personal files (20 GB)


Thank you for reading and looking forward for your help.

Hi polarworks,

Forget about C: and D: ... Linux doesn't use them.

When you installed Ubuntu for the first time you probably used the default setup from tha partition manager, which means your root (/) partition has your home (/home/user_name/) partition in it.

Now from what I read here you want the /home/user_name seperate.

There is a way to do it (if you are comfortable with the terminal) as seen here: [Create a separate home partition in Ubuntu]("http://www.psychocats.net/ubuntu/separatehome").

Or if your install is new enough that you do not have a lot of personal stuff on it I'd just reinstall it. Check out QuickStart in my sig for a nice easy backup solution to backup your existing /home partition FIRST!

Then reinstall according to this thread: [reinstalling ubuntu with seperate home partition]("http://ubuntuforums.org/showthread.php?t=958968").

Just so you know:

1. the root partition (**[SIZE="5"]/[/SIZE]**) is where all the "installed" files go,
2. your home partition **[SIZE="5"]/home/user_name/[/SIZE]** is where the files are configured and all your personal files go.

Now in the future when you want to upgrade to Ubuntu 9.04 (example) you only need to install the root partition and leave your /home/user_name/ partition alone. (Be safe and back it up first though). That way, your email, bookmarks personal config files for various programs will still be active.

Hope this helps.
Bruce

---

### Post by polarworks on 2008-11-28
> **bruce2000 said:**
> Hi,

You can use a program called gparted to partition your hard drive the way you want, it's on the ubuntu live cd.

Have one 20gb partition for root and another 20gb partition for home. This is the equivalent to the partitions you have on windows.

btw, its a good idea to backup your data before working on partition

Thank you for reply bruce2000,
So what I want now is to reformat the Hard drive and install ubuntu again to get the same way as I am use to with.

C: for Ubuntu (20 GB)
D: for my Files and Data (20 GB)

I have my files backed up in USB drive so data is safe and later I can transfer them to my Laptop again running only Ubuntu.

you said that I need a program called gparted to partition but how do I use it when installing Ubuntu?

or is it the same utility /program which comes when the installation progress comes?

My laptop is with me right now and I have now inserted the Installation CD of Ubuntu 8.10 again to chive the same way of drives partition.

Thank you

---

### Post by polarworks on 2008-11-28
Hello Bruce M.
Ok I am reading yoru Quick Start. Yes I have no problem re-installing Ubuntu because I have nothing in my laptop now except Ubuntu OS which I can reinstall again now.

So in terms of Linux the 
root / is like C:/ of Windows?

and 

/home/user_name is like D: drive of Windows where i keep my emails, letters, documents etc?

---

### Post by polarworks on 2008-11-28
I am now reinstalling Ubuntu now so to achive the same as in my Windows.

---

### Post by polarworks on 2008-11-28
Ok so now I am at Install section of ubuntu and here I see Partition program and asking for differnet options.
I selected Manual option and deleted the previous partitions and now it shows the complete free space as 40007 MB.

So what should I do after now?

---

### Post by Bruce M. on 2008-11-28
> **polarworks said:**
> Hello Bruce M.
Ok I am reading yoru Quick Start. Yes I have no problem re-installing Ubuntu because I have nothing in my laptop now except Ubuntu OS which I can reinstall again now.

So in terms of Linux the 
root / is like C:/ of Windows?

and 

/home/user_name is like D: drive of Windows where i keep my emails, letters, documents etc?

I should have said this first in my previous post:

**Welcome to Ubuntu!**
Now to continue...

Close but not "quite".

C:\ for windows is either a complete drive or just another partition

If you created two partitions you'd have C:\ and D:\
However C:\WIN "could" in some respects be equated to root (**[SIZE="5"]/[/SIZE]**) for Linux if you need to think of it in that respect:


C:\WIN - has all the Operating files needed for windows to run.
**[SIZE="5"]/[/SIZE]** has all the system files for Linux to run.

D:\ is a created partition that you use for whatever you want: .DOC files, images, text files etc. etc.

/home/user_name/ for linux does two things for you.

1. configuration files:

Example: FireFox web browser is "installed" in the root directory BUT it's config files and bookmarks etc go in a hidden directory in /home/user_name/ called ~/.mozilla

~/ = shortcut for /home/user_name/
and the **[SIZE="5"].[/SIZE]** before mozilla means it is hidden.

2. a place to put all your personal files away from the system if it's in it's own partition.

Now with **[SIZE="5"]/[/SIZE]** amd **/home/user_name/** separated you'll be able to reinstall Ubuntu with just the root directory (and any other files you've installed over time) and all their configurations are still there in your home directory.

------------------------
Attached is an image of my partitions for: /dev/sda

/dev/sda1/ - is my root directory (partition)
/dev/sda2/ - is my home directory (partition) highlighted
/dev/sda3/ - is my swap directory (partition)

I also have a second drive:
/dev/sdb1 - /media/Data

hard drives are recognized as a device (dev)
the first drive: sda
the second drive sdb, etc. etc.
partitions on the drives are numbers: sda1, sda2 sda3 sdb1, sdb2 etc.

Hope this helps.
Bruce

PS: Let us know how you make out.

---

### Post by Bruce M. on 2008-11-28
> **polarworks said:**
> Ok so now I am at Install section of ubuntu and here I see Partition program and asking for differnet options.
I selected Manual option and deleted the previous partitions and now it shows the complete free space as 40007 MB.

So what should I do after now?

MB or GB?

Create a 12GB partition for ROOT
then create a partition 26GB for /home
and a 2GB SWAP partition

Bruce

---

### Post by polarworks on 2008-11-28
Thank you for your reply.

But If I am installing softwares e.g GIMP, Inskscape or OpenOffice then where the Setup files of these softwares will Go?
In / or in /home/user_name/ ?

Because what I want axactly is that Ubuntu Setup files and any software files which I will install will go in one place.

And other drive only for my own personal files like shop invoices, text files, images etc.

---

### Post by polarworks on 2008-11-28
> **Bruce M. said:**
> MB or GB?

Create a 12GB partition for ROOT
then create a partition 26GB for /home
and a 2GB SWAP partition

Bruce

It's MB 
Ok so a newbie like me dont know what is even SWAP and what I did was divided the drive space by two

Half for /
and rest of For /home

and then it says that I havent' created SWAP so I am back again.

---

### Post by polarworks on 2008-11-28
Why it all maked me confuse is because I remained only with Windows so I have a habit to use Directory structure like Windows have.
For example its very Clear in Windows

C: For Windows and Program Installation Files

D: I keep my files in this drive safely and untouched and If I install any software or programs then they don't touch even the D: drive and everything goes in C:

So this is all I want in Ubuntu Linux

---

### Post by Bruce M. on 2008-11-28
> **polarworks said:**
> It's MB 
Ok so a newbie like me dont know what is even SWAP and what I did was divided the drive space by two

Half for /
and rest of For /home

and then it says that I havent' created SWAP so I am back again.

SWAP is to Linux what "pagefile" is to Windows.

Yes but 400007 MB is a 40GB drive,

> **polarworks said:**
> Why it all maked me confuse is because I remained only with Windows so I have a habit to use Directory structure like Windows have.
For example its very Clear in Windows

C: For Windows and Program Installation Files

D: I keep my files in this drive safely and untouched and If I install any software or programs then they don't touch even the D: drive and everything goes in C:

So this is all I want in Ubuntu Linux

And you will have it, you don't need 20GB for root, 12 is enough. (I'm only using 4.? GB)

So when you get to the partition editor again ... do Like I said:

12GB = Root
26GB = /home
2GB (what's left) = SWAP

You will end up with exactly what you want.
a system partition (like C:\ or **/**)
and your own partition (like D:\ called /home/user_name/)
and a 2GB SWAP file - like "pagefile" for Windows

Still here with you.
Bruce

---

### Post by Bruce M. on 2008-11-28
> **polarworks said:**
> Thank you for your reply.

But If I am installing softwares e.g GIMP, Inskscape or OpenOffice then where the Setup files of these softwares will Go?
In / or in /home/user_name/ ?

Because what I want axactly is that Ubuntu Setup files and any software files which I will install will go in one place.

And other drive only for my own personal files like shop invoices, text files, images etc.

Installed files go into **root** configuration files for those go into **/home**

OK, now you are talking something else.

When you reach the partition editor do this:

Install UBUNTU using 1/2 of the available space: 20GB
then create another partition out of the rest of the drive (less 2GB for SWAP) give it a MountPoint of: /media/MySpace

However now you will have your /home directory in with the root directory. and you'll not have the option to keep it available in the future if you need to re-install.

Bruce

---

### Post by polarworks on 2008-11-28
Dear Bruce M.

Thank you for all your support and Help. I Successfully made the partitions as I wanted just because of your Kind help.

Just like this and as I wanted 

12GB partition for ROOT
26GB for /home
2GB SWAP partition

Hoooraaaaaaaaaay :) :)

Please accept many many Thanks from the deep of my heart.

Best Regards and Yes! have a very nice weekend. :)

---

### Post by CatKiller on 2008-11-28
> **polarworks said:**
> But If I am installing softwares e.g GIMP, Inskscape or OpenOffice then where the Setup files of these softwares will Go?
In / or in /home/user_name/ ?

The installed files (executables, documentation, and so on) will go in a subdirectory of /.

The configuration files - the preferences for your user - will go in the user's Home directory. Generic data, like documents and pictures and so on will go here too. By default, a normal user cannot write data anywhere other than in their Home folder.

As Bruce M. says, the swap partition is like the pagefile in Windows - it's where data gets put if you run out of RAM. It's also where the contents of your RAM go when you Hibernate the computer. Having your swap partition twice the size of the amount of RAM you have in your computer is a reasonable rule of thumb.

It can get as complicated as you want it, since with Linux any directory can be on a different partition, or on a different machine. The mount point (which the installer will ask you about) is the place in the filesystem tree that you want a given partition to appear.

There is some information [here]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"), if you're interested, about how the filesystem tree works.

---

### Post by Bruce M. on 2008-11-28
> **polarworks said:**
> Dear Bruce M.

Thank you for all your support and Help. I Successfully made the partitions as I wanted just because of your Kind help.

Just like this and as I wanted 

12GB partition for ROOT
26GB for /home
2GB SWAP partition

Hoooraaaaaaaaaay :) :)

Please accept many many Thanks from the deep of my heart.

Best Regards and Yes! have a very nice weekend. :)

You're more than welcome polarworks.
Happy ubuntuing!

Chimo!
Bruce

---

### Post by polarworks on 2008-11-28
Yes this is what I wanted and Its Solved as well so How do I mark this Thread as Solved? 

A Big Thanks to [Bruce M]("http://ubuntuforums.org/member.php?u=383242"). and Ubuntu Community.

---

### Post by Bruce M. on 2008-11-28
> **CatKiller said:**
> There is some information [here]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard"), if you're interested, about how the filesystem tree works.

First I've seen of that.
Thank you!

Chimo!
Bruce

---

### Post by Bruce M. on 2008-11-28
> **polarworks said:**
> Yes this is what I wanted and Its Solved as well so How do I mark this Thread as Solved? 

A Big Thanks to [Bruce M]("http://ubuntuforums.org/member.php?u=383242"). and Ubuntu Community.

Like CatKillers sig says: At the top of the page you'll see: **Thread Tools** as the person who started this thread you'll see an option in there to mark it as [Solved].

Chimo!
Bruce

---


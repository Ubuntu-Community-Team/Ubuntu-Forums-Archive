---
title: "Dual Booting, have a few questions"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by Nubi505 on 2009-06-15
I've heard and read a lot of great things about Ubuntu and I'm thinking I want to try it. However, I have a few questions about the requirements and installation. I'd like to dual boot with Windows XP (already installed) and Ubuntu. 

What I'm wondering is if my computer can handle it and how to successfully install it.

Dell Dimension DIME521
AMD Athlon (tm) 64
2.00 GHz, 2.43 GB RAM
60GB hard disk space

I'm using Windows XP Media Center currently. I also have a C and D drive if that matters with the partitioning. 

1. I'm pretty sure my computer met the requirements I found, but is there a certain version of Ubuntu that would work best with my desktop? I heard that certain versions are more friendly than others?

2. Other than the installation disc, do I need to do or acquire anything special? 

3. VGA graphics support? I have an Nvidia GeForce 6150LE, is that sufficient? 

4. How do I know where to partition or does the install disc safely do that for me?

5. Finally... what's the likeliness of my computer severely crashing during the Ubuntu installation?

Thank you for your time.

---

### Post by YldGuy on 2009-06-15
1. Your computer meets the requirements. The latest version jaunty jackalope will work fine.

2. You just need the installation disc. once installed, ubuntu wil fetch updates online and update itself.

3. I have nvidia 6100 and have had no issues with the graphics with ubuntu since i have started using (from the days of fiesty)

4. You need to create a separate partition for ubuntu to be installed or if you prefer you can use the wubi option to install it within the windows. For installation instructions look here - [https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/index.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/index.html)

5. first try out the live cd and see how well it goes on your machine. that shouldn't be any problem i guess.

---

### Post by thirunavukkarasu on 2009-06-15
welcome Nubi,

1. Their is no specific release of Ubuntu version which are meant to have greater user-experience & one which don't have. I would suggest you to try the latest version of the distro., as it will having the updated kernel, utilities, software, etc.
2. It depends upon the installation method you prefer. please go through the standard installation method in the below link as it will be easy 
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
3. The VGA card[Nvidia GeForce 6150LE] which you mentioned below is beleived to be an bit old card. so i think it will be having built-in driver by default 
4. Don't be panic of having questions that installation disc will do the partitions correctly or not. For more partitoning information [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
5. We are really sorry to hear this question this from you :(

---

### Post by presence1960 on 2009-06-15
I would run Ubuntu off the Live CD to see if all your hardware works. I have installed Jaunty as a dual boot on my 7 yo daughter's computer and it runs fine. She has AMD Athlon 64 2.4 GHz - 1 GB DDR RAM - integrated graphics - 40 GB hard drive.

Before installing I would familiarize myself with the install process and have all my ducks in a row. Here are a few links to get you started : 
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html) for a free pdf Ubuntu pocketguie which BTW has a great step by step overview of the installation process

**Also defrag windows at least once or twice to avoid corruption/data loss during resize of it's partition & back up all your data- don't be the one caught with your pants down & whining on here that you lost all your data!**

---

### Post by Nubi505 on 2009-06-15
Thank you all for the replies, they are very helpful. 

> 5. We are really sorry to hear this question this from you

Didn't intend to insult. My computer is very precious to me and would be hard to replace so I am cautious. ^.^

I see there are downloads for the Ubuntu installer and the ability to request a disc. for installation But where does one obtain the Live CD to boot from?

I'm still a little confused about the partitioning, in spite of the obscene amount of guides. Does one have to manually make the partition if they are going to select the Guided Resize option during Ubuntu installation? I also don't fully understand Wubi. I can install and uninstall Ubuntu like a program, without the partitioning and whatnot? 

Either way, I'll make sure to defrag a few times and back up my files.

---

### Post by Anger 2 on 2009-06-15
> **Nubi505 said:**
> Thank you all for the replies, they are very helpful. 



Didn't intend to insult. My computer is very precious to me and would be hard to replace so I am cautious. ^.^

I see there are downloads for the Ubuntu installer and the ability to request a disc. for installation But where does one obtain the Live CD to boot from?

I'm still a little confused about the partitioning, in spite of the obscene amount of guides. Does one have to manually make the partition if they are going to select the Guided Resize option during Ubuntu installation? I also don't fully understand Wubi. I can install and uninstall Ubuntu like a program, without the partitioning and whatnot? 

Either way, I'll make sure to defrag a few times and back up my files.

Hi,
You just download the appropriate version and burn the iso image to CD to make the live CD.You have the option to have it installed automatically or to partition manually.Read instructions carefully before you install.Best to test the live CD by running it without installing first.

---

### Post by Nubi505 on 2009-06-15
I downloaded Ubuntu and burned it to a disc. But when I went to checkout how my hard drive was partitioned I found I couldn't make new partitions. There isn't any unallocated space at all. Actually, there's like 8mb of unallocated space, but I don't think that will be very helpful.

I downloaded EASEUS Partition Master, a free program that lets you resize your partitions. I tried to resize my C drive, 69GB with 30GB free so that there was a new partition of about 10GB for Ubuntu to work with when I decided to install it. The program requires you restart. I restarted, it went to the boot screen, and then just went black and stayed that way for at least an hour. Apparently EASEUS is supposed to come up with a loading screen, and take its time, to show its doing something... But nothing happened. So I'm not sure what to do with that.

In other news, the live version worked pretty well.

---

### Post by presence1960 on 2009-06-15
> **Nubi505 said:**
> I downloaded Ubuntu and burned it to a disc. But when I went to checkout how my hard drive was partitioned I found I couldn't make new partitions. There isn't any unallocated space at all. Actually, there's like 8mb of unallocated space, but I don't think that will be very helpful.

I downloaded EASEUS Partition Master, a free program that lets you resize your partitions. I tried to resize my C drive, 69GB with 30GB free so that there was a new partition of about 10GB for Ubuntu to work with when I decided to install it. The program requires you restart. I restarted, it went to the boot screen, and then just went black and stayed that way for at least an hour. Apparently EASEUS is supposed to come up with a loading screen, and take its time, to show its doing something... But nothing happened. So I'm not sure what to do with that.

In other news, the live version worked pretty well.

Use the Ubuntu Live CD or gparted Live CD to partition your hard disk. If you can boot into windows make sure you defrag. Then using one of the methods I just mentioned you are going to have to resize your Windows partition first to get unallocated space to create the Ubuntu partition(s). This is just my opinion but I frown on all those other 3rd party partitioners- you can take that with a grain of salt! Once you shrink the Windows partition you can use the space created for Ubuntu.

If you aren't sure what you are doing, then maybe you can get in contact with someone who can help you in person. Do a google of Linux Users Group (LUG) there may be one in your area. Otherwise read, absorb and ask questions until you are ready to proceed. The install chapter of the free pdf Ubuntu Guide has a great step by step set of instructions for install.

gparted Live CD get it here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Ubuntu Live CD partitioner: choose "Try Ubuntu without any changes". When the desktop loads go System > Administration > Partition Editor

Why don't you see what you got now. boot the Ubuntu Live CD. Choose "Try Ubuntu.." When the desktop loads open a terminal (Applications> Accessories > Terminal) type or paste > sudo fdisk -l BTW that is a lowercase L. Paste the output back here. This will let us see if that partitioner worked or made a catastrophe.

P.S. it is a shame you went and downloaded that. You have all the tools you need on the Ubuntu Live CD or gparted Live CD. I just went to that EASEUS web site and it is freeware for Windows. You can use the gparted Live CD or the Ubuntu Live CD for that matter to partition a windows only machine.

---

### Post by Nubi505 on 2009-06-16
Thank you again for the response. 

I tried the Partition Editor in the Live CD earlier. It won't let me resize. 

I just now got done trying out gparted. Again, it won't let me resize my C drive. I can't make any adjustments to it... The little up/down arrows are grayed out and when I input a number of mb I want to free up it goes back to 0. 

Here's a screen shot of what my partition looks like in the Disk Management on Windows if it helps any.

[_Screenshot_]("http://s3.photobucket.com/albums/y91/anubis505/?action=view&current=partition.jpg")

Do you still want me to boot into the Live CD and enter that into the terminal, even though nothing changed in the partitions?

And is there a way to install Ubuntu on the C drive in harmony with Windows without have to wipe the drive (or partition)?

Finally, what does formatting the drive do? I noticed you could change the drive from NTFS to a version of FAT etc... Just curious. 

Thanks for all the help.

---

### Post by brncao on 2009-06-16
You can't install a partition on an existing partition. formatting lets you set up partition sizes,  create primary or extended/logical partitions, set the type of File System, and delete partitions.

If there's a file system that's tacked on at the end of C: and defragmenting has failed to catch this then that could be the source of the problem.

Have a read at this [http://technet.microsoft.com/en-us/library/cc731894.aspx](http://technet.microsoft.com/en-us/library/cc731894.aspx)

---

### Post by presence1960 on 2009-06-16
You can use wubi to install ubuntu inside windows. Boot into windows and once your desktop loads insert the Ubuntu Live CD. One thing to note: make sure you give Wubi enough space because once you set it's size it is pretty difficult to resize. Someone mentioned on here there is a way but it is difficult to do. 

Installing wubi will forego the partitioning for you. When you boot your computer you will be given the choice of windows or Ubuntu.

---

### Post by Nubi505 on 2009-06-16
Wow, compared to making a partition on this computer Wubi was painless. Installed Ubuntu inside Windows and it works and nothing blew up. <3 (Is there any real advantage to having it on its own partition?)

My only issue is that my mouse froze. At first I though Ubuntu had froze, but I could still navigate using the arrow keys and tab. I didn't get very far without my mouse though. I'm using a pretty standard addition Dell laser mouse w/cord.

But thank you everyone for answering my questions and helping me out with this! I really appreciate it.

EDIT: Well, my mouse keeps freezing after 1-5 minutes of use in Ubuntu. There seem to have been various mouse freezing problems posted around different forums, but I'm not exactly finding a solution.

---

### Post by Anger 2 on 2009-06-16
You might find this site useful in the future.
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---


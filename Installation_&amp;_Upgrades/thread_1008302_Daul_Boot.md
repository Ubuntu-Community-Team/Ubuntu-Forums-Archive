---
title: "Daul Boot"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by -Cluster- on 2008-12-11
A simple question:

I have installed ubuntu on to my laptop using the entire of my disk.

Can i install windows as well with out loosing ubuntu if so a brief description of what to do in the xp setup would be amazing

---

### Post by Libux on 2008-12-11
i think you cant install windows xp without loosing ubuntu
you can make a partition and then install xp but you will lose ubuntu

---

### Post by meindian523 on 2008-12-11
You could,AFAIK,if you had not installed Ubuntu over your entire disk.As to how it would work IF you had installed it into a partition,I dunno,because of the resellers always pre-installing Windows and I've had no experience installing Windows from a CD.Wait around for other opinions though.

EDIT: Do check the thread linked in my signature for newbies.

---

### Post by icanfly0307 on 2008-12-11
If you *already* have XP on your computer and want to install Ubuntu, you can obviously dual boot both operating systems. The good news is that you don't have to configure anything. The Ubuntu installer will automatically detect XP and give an option to boot from Ubuntu or XP when your computer starts up.

However, if you want to install XP from your system recovery disks *after* you've installed Ubuntu, your Ubuntu installation will be erased and XP will replace it.

Hope This Helps. :)

---

### Post by jenkinbr on 2008-12-11
> **meindian523 said:**
> You could,AFAIK,if you had not installed Ubuntu over your entire disk.As to how it would work IF you had installed it into a partition,I dunno,because of the resellers always pre-installing Windows and I've had no experience installing Windows from a CD.Wait around for other opinions though.

EDIT: Do check the thread linked in my signature for newbies.
This is still possible, but you will need to take other steps to resize the exsiting Ubuntu partition BEFORE you install Win~whatever on your system. After Installing Windows, you will need to Re-insert your ubuntu CD and run the grub installation steps provided [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Using%20the%20Ubuntu%20Desktop/Live%20CD").

These are the general steps that will need to be done.  If someone could expand on this, It would be great.

---

### Post by icanfly0307 on 2008-12-11
I agree with you but not entirely.:-k

If he's going to be using a System Recovery Disk that was provided with the computer when he bought it, it will wipe out the ENTIRE hard drive. And I'm sure he wouldn't be too happy about that. :)

PS. If he uses a regular Windows CD bought in a retail store, that's an entirely different scenario.

---

### Post by meindian523 on 2008-12-11
System Recovery Disk?Who said anything about a system recovery disk?To install Windows,you need an install CD,isn't it?

---

### Post by icanfly0307 on 2008-12-11
Well it's also possible to install Windows through a System Recovery Disk and in case he was thinking about that, it'll obviously erase the Ubuntu installation. :(

---

### Post by jenkinbr on 2008-12-11
> **icanfly0307 said:**
> Well it's also possible to install Windows through a System Recovery Disk and in case he was thinking about that, it'll obviously erase the Ubuntu installation. :(

Where did this System Recovery Disk business come from:confused:

> **jenkinbr said:**
> This is still possible, but you will need to take other steps to resize the exsiting Ubuntu partition BEFORE you install Win~whatever on your system. After Installing Windows, you will need to Re-insert your ubuntu CD and run the grub installation steps provided [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Using%20the%20Ubuntu%20Desktop/Live%20CD").

These are the general steps that will need to be done.  If someone could expand on this, It would be great.

Now that I have a bit more time to work on this, Here is my expansion on what I posted earlier.
[list=1]
[*]If you have any documents, settings, or anything else that you have changed, I recommend that you back them up before you begin.  Also, if you have installed any applications, I recommend that you take note of them. This step will ensure that your files are safe if something goes wrong (rare, but possible).

[*]Next, find and boot into your LiveCD.

[*]Once you are in your LiveCD desktop session, take the menu path "System" --> "Administration" --> "Partition Editor"

[list=a]
[*]At this point, you will need to decide what size you want your windows partition to be compared to your Ubuntu partition.  For me, I use 12GB for Windows, but if you plan on gaming or have to do work primarily in Window, this will/may not work.  Partition sizing is a matter of preference.  You can use the size listed for your drive to determine how much space you have to work with.

[*]Now that you have decided what sizes to use, you will need to resize your Ubuntu partition. Right-click on your Ubuntu partition - If it is indeed the only one, it should be listed as sda1 - and select "Resize/move".

[*]You should now see a window similar to this one:
[IMG]http://i5.photobucket.com/albums/y198/Miniclipunblocked/error1.png[/IMG]

[*]To resize the partition, you will need to set the size of the current partition to the apropriate number of megabytes.  The easyest way to do this is to adjust the 'free space following' value.  Note that the number is in megabytes, so you will need to multiply your value in gigabytes times 1024 to get the correct number to put here.

[*]Click on the 'resize/move' button when you are sure of the values entered.  You may be required to apply the changes immediatly. If this is the case, verify that you are ready to do this then press OK.  If you are not required to apply changes, verify that you have the correct values showing, then click on 'apply changes'.

[*]This operation may take anywhere from <1 minute to >5 hours. This is normal.

[*]When the above is completed, Right-click on the unpartitioned space and click on 'new'. A dialog like this should open:
[IMG]http://www.breakitdownblog.com/wp-content/uploads/2006/08/gparted_new_partition.jpg[/IMG]

[*]Set the following:
Max out the new size field.
Set the filesystem to be NTFS.

[*]Click 'Add' or OK.  This process may take a while, but shouldn't be as long as the resize operation above.

[*]When this finishes, we are done with the liveCD for the time being. Go ahead and restart your computer, replaceing the Ubuntu disk with your windows install disk when it is ejected.
[/list]

[*]Boot the windows Installer disk.

[*]Wait patiently as windows takes forever loading it's libraries.  When prompted, press <enter>.

[*]Read the End-User License Agreement, by far my least favorite part.

[*]When asked which disk to use, select the one that shows up as NTFS. If it doesn't show, you may need to remember the sizes you used from erlier. (It's been a while since I last had to install windows...:))
[*]After selecting the proper disk, continue installing as usual. You are now past the critical disk selection stage.

[*]After windows has been installed, you will need to re-install the GRUB bootloader.  A Guide has been posted on [this wiki page]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), but I will briefly describe what needs to be done.

[list=a]
[*]Restart your computer with the Ubuntu CD in the drive.

[*]When the desktop is loaded on the LiveCD, go to "Applications" --> "Accessories" --> "Terminal"

[*]Type the following command:```
sudo grub
```

[*]type:```
find /boot/grub/stage1
```
This will print something like (hdX,Y).  Take note of what X and Y are.

[*]Type ```
root (hdX,Y)
``` replacing X and Y with the proper values.

[*]Finally, run```
setup (hd0)
```and then ```
quit
``` to set up and exit grub.

[/list]
[*]Close the terminal and reboot the computer.  Grub should now be working.
[/list]

@all: If there is ANYTHING wrong with the above, please let me know.

Hope the OP and anyone else who sees this finds it useful.

---

### Post by -Cluster- on 2008-12-12
Thank you very much, seems this would have been a lot easier if i ask before diving in :)

---

### Post by jenkinbr on 2008-12-12
No problem. That's what the Ubuntu Community is here for!

Yes, it would have been a bit easier if you asked first, but hey! If this works, you now know enough to at least point people in the right direction.  Operating an Ubuntu machine, just like any other computer system, involves ciertain risks, such as the possiblity of accidentilly screwing something up.  I've been there and done that, and that's why backups are important.

Anyways, post back if you need further help or if this worked for you.

Happy Ubuntuing

---

### Post by icanfly0307 on 2008-12-12
I don't mean to butt in after you've understood how to do it, but there is one question that is nagging me.

How are you going to install Windows XP? Did you buy the CD at a store or did it come with the computer?

---

### Post by -Cluster- on 2008-12-12
> **icanfly0307 said:**
> I don't mean to butt in after you've understood how to do it, but there is one question that is nagging me.

How are you going to install Windows XP? Did you buy the CD at a store or did it come with the computer?

Well i am sure that some things can't be said on this forum. But i know for a fact that Torrents have made things easily available. If i owned an original copy of "windows xp oem" i would have a product code as well as a copy of xp installation disk. If i lost the disk i would at least have the product code (found on the bottom of a laptop or side of desktop computer). 
For dual boot I don't think system recovery disk are good enough as they don't have the options you need.

---

### Post by icanfly0307 on 2008-12-13
Gotcha. :)

---

### Post by -Cluster- on 2008-12-14
Wow did i just help some one......thats wierd

---

### Post by meindian523 on 2008-12-14
Cluster:
If you're done with this thread,please mark it solved.

---


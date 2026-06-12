---
title: "installation freezes"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by isacneo1 on 2009-08-25
Wheni try to install ubuntu from a live cd i get up to he point where it asks to pick keyboard layout then it jus stays there and does nothing. any help would be appreciated.

---

### Post by running_rabbit07 on 2009-08-26
Start the LiveCD and use the test disk function.

---

### Post by isacneo1 on 2009-08-26
I have done that and it says that there was no problem with it

---

### Post by running_rabbit07 on 2009-08-26
What are your system specs?

---

### Post by tal007 on 2009-08-27
It happened to me too, but in my case I found out that I did not have enough hard drive space for my installation. You have to make sure that you have enough area on your drive and not being used by any other OS ( meaning empty and unpartitioned  large enough for installation).

---

### Post by isacneo1 on 2009-08-28
ok i see how do i get rid of windows on it then because windows crashed and has an error and wont start up again so i how do i get rid of it

---

### Post by tal007 on 2009-08-28
Here is, what I would do. My assumptions : 

1.  You have messed up your system irretrievably.
2.  You will not be able to bring up the system and given up hope.
3.  You are trying to install Ubuntu afresh on your hard drive by
    erasing everything on it.

Then, this is what you should do. There are a number of ways you can do it. 

First, try to bring up your system using the Live Ubuntu CD. See if you can view the partition table. You probably will not be able to view it, because you might have damaged your file systems permanently. If you can view the table, then straight from there by highlighting the partition you can delete the partitions. When deleting the partitions keep in mind that Ubuntu requires at least 8 GB of free space for installation. If you don't set aside sufficient unused space you will run into the same problem. If you can not view you partition table, this is the second alternative.


Get a generic windows98 or Dos boot disk, save it onto a floppy.
Keep in mind, when you save a boot disk on to a floppy you have to do it the proper way. Merely copy and paste will not work. I have downloaded one several days ago from a site. It comes in a in zip format.  Nice thing about it - does it everything for you automatically when you unzip it and save it on a floppy. You will also need a utility call delpart.exe to delete your partitions. If you want to delete your partition table using FDISK, it will take  a very long time. Not recommended.  

Bring up your system using the generic boot disk. Once you get to "A>" prompt, replace the boot floppy with the "delpart.exe". Before you proceed make sure to save this file on a separate floppy. You have to execute "delpart.exe" from the floppy. It takes a very long time ( 7 or 8 minutes ) for the boot floppy to boot up once you have wrecked your file systems. So, You have to be very patient. It may look like the process has stalled. In fact, it is not.  Delpart.exe will also require some time to show up on your display screen after you you execute it. Once you the delpart menu comes up you can highlight the partitions and delete them. Very self explanatory. Make sure to save the changes before you exit the program. If not, your changes will not take effect.

Once all are done, then you can go on with your Ubuntu installation.

Files you need : 1.win_boot ( Generic Windows 98 boot )
                 2. delpart.exe

Search on the internet for them. If you can not find them, post an email adress. I will email them to you.

---

### Post by isacneo1 on 2009-08-30
well what i ended up doing was i installed DSL (damnsmall linux) from a live cd that i have been temporarily using but it did that same thing and freed up the hard drive and i was able to install ubuntu fully on the entire hardrive and ty very much for helping me out

---

### Post by tal007 on 2009-08-30
When installing a package or software, do it the proper way. First read the installation instructions. There are lots of intricacies involved in Unix. I don't know much about Linux, but on unix without Super User privilege you can not install anything and even after that you have to do so many things such as changing permission, changing file path etc.. to get it to work. Always try to do it as Super User ( sudo ). I think on Linux you can do it from the administrative menu.

---


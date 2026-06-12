---
title: "How to resize the /home partition?"
date: 2005-08-27
forum: Hardware &amp; Laptops
---

### Post by Muiske on 2005-08-27
Ok Ubuntu users, can you help a newbie to Linux out?  :)  I would like to request your attention for the following.


First of all, my hard-disk index is a mess, but that's not really the issue here.

The issue is this. I have cut the size of my NTFS partition (/dev/sda1) on which my Win XP is installed. 
My /home (/dev/sda3), that is a partition of its own, was next to this partition. Due to resizing there is approximately 30 gigs of free space between these two partitions.

Now, I want to add this free space to my /home partition, but I have not exactly a good idea on how to do that. I'm afraid that if I do this in Win XP, it will mess up the Ubuntu filesystem (I'm quite sure this will happen). I've tried using GParted, but quite logically, it was impossible to change it.

Am I delving into something that will give me nightmares?? 

Please help me. I need more space. ;)


(Oh, and I could not find a similar topic, so please forgive me if this has already been a subject once).

Muiske

---

### Post by strips on 2005-08-27
I know there are tools to resize ext2/3 partitions. But you might have to do it manually. I don't remember exactly how i did it once. But i didn't loose any of the data on it. But do make a backup of your home partition first.

I'm pretty sure I've done this with ReiserFS to some time ago. 

But.. The easiest way I can come up with now without googling is to use a Linux rescue disk. Back up the home partition -> delete it -> create a new larger one -> copy your data back.

---

### Post by Muiske on 2005-08-27
Thank you strips.


It would also seem to be the most logical course of action to me. However, since my /home is almost 40 gigs large, moving it somehwere else might take some time. I'd have to split the data to copy it to other partitions. That's why I wondered if there might be some easier way that I had not thought of....

---

### Post by Delkster on 2005-08-29
Maybe you could try a live CD Linux distro like Knoppix. The command-line parted tool and the graphical QtParted, both of which are included on the Knoppix CD, can probably do what you need, and since you're using the entire OS from the CD, you should be able to alter the partitions on the hard disks.

I would recommend reading the parted documentation and making backups of your data before trying anything but AFAIK you should be able to do it non-destructively.

---

### Post by tonysathre on 2005-08-29
ive done this before with success by using the ubuntu install cd

---

### Post by Muiske on 2005-08-31
@Delkster: Thanks. I haven't used a Live-CD yet, so I am completely new to this kind of system. I've read something about it, but I will have to know a little more before I start messing around. However, this option seems like a good idea! :)

@tonysathre: So it's possible by using the Ubuntu install CD? Then what exactly is it I have to do in order to change the partitions without screwing the whole file system? I know I can give a command in the screen you get after booting from the cd, but I'm unaware what the possibilities are. Some help would be greatly appreciated!! ;)

---

### Post by tonysathre on 2005-08-31
when u boot to the cd you get the boot options prompt, just hit enter, let the cd run its hardware checks and what not, keep going with the installation (which actually isnt installing anything) until you get to the partitioning part of the install.  from there you can view, delete, resize or add partitions on all HDDs without destroying any data. after resizing or whatever your doing, hilite the write partitions to disk and press enter.  after it writes go back to the main menu, DO NOT CONTINUE WITH THE INSTALL BECAUSE THIS WILL DESTROY DATA, and select at the main menu the exit option.   if its a dual boot like mine with xp, the next time u boot into xp you will see a blue screen that says the system must run scandisk, let it run and after its done you will finish booting into xp.  dont be alarmed when u see the blue screen, its nothing more than windows updating itself with the new partition table.

---

### Post by duan on 2005-08-31
The gparted software on the live ubuntu cd only found my mmc reader but would not allow any edits to the hard disk.

I have used knoppix's live cd v3.7 to resize windows partitions and create several linux ones with QTParted, i could fiddle with the sizes then.

I just inserted knoppix and booted from cdrom.
Running QTParted from the menus in KDE worked, from the command prompt It would not write the changes. 
Knoppix seems more agrressive in being a systems admin and rescue service, even if its a bit messy. I keep it around for just that.

I was feeling lucky and never backed up anything- and it worked.

---

### Post by tonysathre on 2005-09-01
cool, i have knoppix 3.6 and i couldnt get it to work with qtparted to repatition disk, thats why i use the ubuntu install cd, 

when u tried writing changes to the disk were you root?

---


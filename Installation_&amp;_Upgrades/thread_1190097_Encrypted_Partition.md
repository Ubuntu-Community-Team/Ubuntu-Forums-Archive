---
title: "Encrypted Partition"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by John M2009 on 2009-06-17
At the moment,  I am running windows XP with the entire OS encrypted with truecrypt,  I want to have ubuntu on a seperate (unencrypted) partition  as a dual boot arrangement,  I am just wondering if on start up,  ubuntu will recognise the encrypted partition or not,  and give me the option to boot from it,  or at least give me the option of which drive to boot from.

I also have a question about mount points...When i format a drive there is a drop down menu with a list of mount points,  im assuming i select /swap for the swap partition,  what about the installation of Ubuntu itself,  and what are all the other ones for?  I never thought I would have so many questions about how to install Ubuntu,  but then im used to windows doing everything for me!!!

Its all starting to seem very daunting lol

---

### Post by John M2009 on 2009-06-17
Bumping...in the hope someone will respond :P

---

### Post by Davsdu on 2009-07-15
Since no one has replied yet I'll try with my limited knowledge.

Here's an interesting read on Tryecrypt:
[http://forums.techguy.org/windows-nt-2000-xp/699514-truecrypt-general-encryption-questions.html](http://forums.techguy.org/windows-nt-2000-xp/699514-truecrypt-general-encryption-questions.html)

Most of the conversation they're having there is about the pros and cons of having an entire partition encrypted vs. encrypted folders and or an external drive to store data on to.

About mounting points. Usually " / " (root) is all you need when installing a new Linux OS. You can also create a seperate /home partition so your data and files and folders remain intact should you want to install another Linux distro later.

Hope it answered some of your questions. Perhaps someone else who knows more about Truecrypt and mount points can add a few comments. :)

---

### Post by Post Monkeh on 2009-07-15
i'm fairly new to linux, and this is the first time i've ever tried to post something that sounds remotely knowledgable, so bear with me.

mount points are essentially the equivilant of your windows disk partitions.

where in windows, you could partition your disk into maybe drive c, d & e, with c being for windows, d for your programs, and e for your files (or whatever), in linux, all the different "parts" of your data are stored in different folders of your file system.

while this may seem a bit restrictive, you actually do get used to it, and it does have its advantages.  you can still spilt your hard disk into partitions, and tell linux to put the different parts of your os into different parts of your hard disk. like davsdu said, the main use for this is so you can put the majority of youros on one partition, and your personal files and settings on another (your /home folder stores all this information)  
you set this up using mount points.  in theory, you could set up a different mount point for each part of your system, but as someone who did it when he first installed ubuntu, and stuffed it up - i'll tell you you don't need to.   give yourself a mount point for "/" (your *main* file system) and a seperate one for /home, as well as a couple of swap partitions (preferably one on each physical disk if you have 2 or more, if you only have one disk then just put 2 on there) and that should set your system up nicely.

---

### Post by Mark Phelps on 2009-07-15
Don't know how Truecrypt works, but I'm using a laptop with an encrypted drive and it never even gets into Windows; instead, it boots from the BIOS into a front end that prompts for the decryption info.  You don't even see the MS Windows boot until after supplying the correct info.

Ubuntu will create a boot menu with an option for MS Windows, but when you select that, all it will do is hand you over to the MS Windows boot loader. Don't know what you will see after that.

You can partition most anyway you want, but the typical scenarion require a separate Swap parition and then, generally, a separate partition for root (/) and for /home.  Don't know about using two swap partitions. Have a system with multiple drives and have seen no difference between using both (one on each drive) or only one.

---

### Post by a94060 on 2009-07-27
Im currently running a dual boot setup with ubuntu unencrypted, and windows partition fully encrypted. I would advise you to use the windows bootloader to chainload grub, rather than using the escape menu. I realize that if i were to connect my usb drive,it checks it for bootable partitions, and essential can allow malicious software to be loaded. If you need any help, feel free to post back

---


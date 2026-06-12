---
title: "Dual-booting Ubuntu and Windows 7"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by Jawadkho on 2009-10-23
Okay so I've got Windows Vista installed on my pc and I have Ubuntu installed on that using Wubi. I use Ubuntu all the time so now as I'm going to get Windows 7 I'm going to partition the drive but my main problem is as I had Ubuntu installed using Wubi how can I install it onto another partition oustide wubi and keep all my settings and everything. I also want to dual boot Windows 7 with it so to summerise:


[LIST]
[*]Currently got Windows Vista and Ubuntu installed on it using Wubi
[*]I want to keep Ubuntu and all its settings (out of Wubi) but its installed in Vista
[*]I also want to dual boot Windows 7 with Ubuntu (I'm going to partion the drive)
[/LIST]

Thanks

Jawadkho

---

### Post by Jawadkho on 2009-10-23
Anyone? I guess I'll have to bid farewell to Ubuntu :sad: seeing as no one seems to know a way to help me but Its not too late I'm still here so I'll be grateful for any help.

---

### Post by Dragonbite on 2009-10-23
Give a little more time. 2 Hours is not long enough considering the person with your answer just might be at work right now, or sleeping on the other side of the world.

Me, I don't know the answer to your question. I haven't used Wubi to even know how to begin.

---

### Post by appier on 2009-10-23
Give the guys who know what they're doing a chance to respond to you.  However, I can tell you how I did it with Win XP.

First, I backed up all of the files I wanted to keep from the Home folder onto a portable hard drive.  Then, I did a fresh install from the Live CD choosing to install the operating systems side by side, then resizing the Windows partition.  And, finally I restored my Home files to the new Home folder.

Having said that, I am new at this, and there are a couple of caveats. I booted to Windows each time in between so it could adapt to the changes--sorry, don't know if there is a technical reason to do this. I also hear that Vista does not always like to have its partition resized so you may want to use their disk manager.

What you are asking to do can be done, but I would wait until someone with more experience than yours truly weighs in with advice.

Hope it goes well!

Mark

---

### Post by ed5000 on 2009-10-23
Why not do a fresh install?  You could save your Firefox settings(favorites) by using the "settings backup" in the Firefox menu then specify a place to save (like a thumb drive) and backup all your other stuff like documents, photos, music files, etc. and do a fresh install.  I think you would like your Ubuntu better since it would be faster without runnning the 2 OSs.  Use the dual boot feature built into the Ubuntu install disk.  Of course afterwards use "restore settings" in Firefox and finally, move all your documents and files over to the new Ubuntu.  

You could also wait for Ubuntu 9.10 which is due out the end of this month as well.

---

### Post by Jawadkho on 2009-10-23
Sorry for being impatient I guess I dont need to do it right now anyway.
I dont really want to do a clean install because I've had Ubuntu for a few months (8 or something) and the documents and firefox settings are the least of my problems. What I really need are the configurations and the programs that I've got on it because installing them all over again and having to do the configs again seems a big task.

---

### Post by Dragonbite on 2009-10-23
> **Jawadkho said:**
> Sorry for being impatient I guess I dont need to do it right now anyway.
I dont really want to do a clean install because I've had Ubuntu for a few months (8 or something) and the documents and firefox settings are the least of my problems. What I really need are the configurations and the programs that I've got on it because installing them all over again and having to do the configs again seems a big task.

There is supposed to be a way for synaptic to backup a list of all of the applications installed (and depenencies, etc.) if that helps.  You can run the script and it will apt-get install everything you've already gotten.

---

### Post by Jawadkho on 2009-10-23
What about applications that weren't installed using synaptic?

---

### Post by Dragonbite on 2009-10-23
> **Dragonbite said:**
> There is supposed to be a way for synaptic to backup a list of all of the applications installed (and depenencies, etc.) if that helps.  You can run the script and it will apt-get install everything you've already gotten.

> **Jawadkho said:**
> What about applications that weren't installed using synaptic?

I don't think those are included.  But did you download and save the binary or shell script?

---

### Post by Jawadkho on 2009-10-23
No :sad:

---

### Post by Mark Phelps on 2009-10-23
> **Jawadkho said:**
> Okay so I've got Windows Vista installed on my pc and I have Ubuntu installed on that using Wubi. I use Ubuntu all the time so now as I'm going to get Windows 7 I'm going to partition the drive but my main problem is as I had Ubuntu installed using Wubi how can I install it onto another partition oustide wubi and keep all my settings and everything. I also want to dual boot Windows 7 with it so to summerise:


[LIST]
[*]Currently got Windows Vista and Ubuntu installed on it using Wubi
[*]I want to keep Ubuntu and all its settings (out of Wubi) but its installed in Vista
[*]I also want to dual boot Windows 7 with Ubuntu (I'm going to partion the drive)
[/LIST]

Thanks

Jawadkho

Then, read the following about how to migrate your Ubuntu installation to its own partition -- and show a little more patience for the FREE support your getting:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?")

---

### Post by Jawadkho on 2009-10-23
> **Mark Phelps said:**
> Then, read the following about how to migrate your Ubuntu installation to its own partition -- and show a little more patience for the FREE support your getting:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)
Sorry I was a bit rude, but thanks.

---

### Post by skyiscrying on 2009-10-23
Heck, if you use Ubuntu all the time as you say, then just stick with that. There is nothing extra special about Windows7 in my own humble opinion. Microsoft are not known for being big-hearted if you get my drift.

---

### Post by Cybie257 on 2009-10-23
I would do a system backup using the procedure from this link

[http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+restore]("http://ubuntuforums.org/showthread.php?t=81311&highlight=backup+restore")

Then, fresh install your OS('s) and use that same link to restore your Linux back to where it was. I've used that backup and restore method a few times with 100% success. All you do is fresh install the base Linux version you were using, then restore the resulting tar file created on top of that, and wholla, you are back to where you were. :)

-Cybie

---

### Post by Jawadkho on 2009-10-24
@skyiscrying

There are some things I need to do on Windows for work.

@Cybie257

Thanks but I think I'll do a clean install but can I am thinking about installing 64-bit this time is there anything to consider before I do that?

---

### Post by Cybie257 on 2009-10-25
That your Computer is capable of 64-bit is all I can think of that would be important. Anything From Pentium D (including P4-HyperThreading) all the way up for Intel should be good. As for AMD, you'll have to look it up as I don't know the scheme there. 

-Cybie

---

### Post by Jawadkho on 2009-10-25
Yh it is capable but I was thinking in terms of the programs, do most of the programs come also come in 64-bit aswell.

---

### Post by GrantBarry on 2009-10-25
For additional info:

When you perform an **UPGRADE **from Windows Vista to Windows 7. Windows will keep your original partition as the boot partition (Boot Manager and BCD files).

When you perform a **CLEAN INSTALLATION** of Windows 7. Windows will create a 100MB System Partition (not mounted/no drive letter). The System Partition is the boot partition and contains the Boot Manager and BCD files.

Watch out when if you need to configure Grub

---

### Post by Jawadkho on 2009-10-25
Ok Thanks

---

### Post by Mark Phelps on 2009-10-25
> **GrantBarry said:**
> When you perform a **CLEAN INSTALLATION** of Windows 7. Windows will create a 100MB System Partition (not mounted/no drive letter). The System Partition is the boot partition and contains the Boot Manager and BCD files.

It only does this to an unformatted drive.  If your drive already has an empty NTFS partition, it will use that without creating any other partitions.  I know -- I did that.

Also, if you have another MS Windows OS installed in a different partition, 7 will write its boot loader files to the first NTFS-formatted partition it finds.  This produces problems later when folks go to hand-edit their menu.lst file, think the 7 boot files are on partition #2 (or #3, or whatever) and find that the boot selection doesn't work.

---

### Post by billpanepinto on 2009-10-28
[FONT="Arial"]Apologies for my inability to glean this information from existing posts.


When Karmic is released, I'd like to do a clean install of both Ubuntu 9.10 and Windows 7. I primarily use Ubuntu, but need Windows for work. (When I used VirtualBox to create an XP VM, Office 2007 failed spectacularly.) I would rather dual-boot so I can have the machine's full resources available to me in either OS. I want to maximize the size of my data (vs. OS) partition, and make the dual-boot work.

My questions are these:
[LIST=1]
[*]How should I partition my 250 GB hard drive (i.e., size, left-to-right order, and file system formats)? Should I use GParted Live CD to partition before the installs or let the install DVDs take care of the partitioning?

[*]In which order should I do the OS install?

[*]What kind of post install steps do I need to take to ensure proper booting?
[/LIST]
Any help is greatly appreciated.

Thanks,
Bill[/FONT]

---

### Post by Dragonbite on 2009-10-28
> **billpanepinto said:**
> [FONT="Arial"]Apologies for my inability to glean this information from existing posts.


When Karmic is released, I'd like to do a clean install of both Ubuntu 9.10 and Windows 7. I primarily use Ubuntu, but need Windows for work. (When I used VirtualBox to create an XP VM, Office 2007 failed spectacularly.) I would rather dual-boot so I can have the machine's full resources available to me in either OS. I want to maximize the size of my data (vs. OS) partition, and make the dual-boot work.

My questions are these:
[LIST=1]
[*]How should I partition my 250 GB hard drive (i.e., size, left-to-right order, and file system formats)? Should I use GParted Live CD to partition before the installs or let the install DVDs take care of the partitioning?

[*]In which order should I do the OS install?

[*]What kind of post install steps do I need to take to ensure proper booting?
[/LIST]
Any help is greatly appreciated.

Thanks,
Bill[/FONT]

Windows is selfish and wants to be the ONLY operating system on your machine, so install Windows first.  

Ubuntu includes some good-citizen features that allows it to detect your Windows installation and offer to install Ubuntu right alongside Windows.

---

### Post by peterx2 on 2009-10-28
> **Jawadkho said:**
> Okay so I've got Windows Vista installed on my pc and I have Ubuntu installed on that using Wubi. I use Ubuntu all the time so now as I'm going to get Windows 7 I'm going to partition the drive but my main problem is as I had Ubuntu installed using Wubi how can I install it onto another partition oustide wubi and keep all my settings and everything. I also want to dual boot Windows 7 with it so to summerise:


[LIST]
[*]Currently got Windows Vista and Ubuntu installed on it using Wubi
[*]I want to keep Ubuntu and all its settings (out of Wubi) but its installed in Vista
[*]I also want to dual boot Windows 7 with Ubuntu (I'm going to partion the drive)
[/LIST]

Thanks

Jawadkho

I am currently exploring Ubuntu 9.10 which may present some problems for you. First, if you are running 2 drives it will default to a RAID setup. This implies that all of the space can be joined  in the two drives, but the provision for dual booting gets more complicated. Second is the move to Grub2 as the default boot scheme. This is probably not a problem except if something goes awry, Grub1 will not be able to find your system, because the files have changed in grub2. this makes supergrub more or less useless. I havent seen anything in the forums that discusses these things because 9.10 is too new. My impression at the moment is that 9.10 isn't all that dualboot friendly, although provision supposedly has been made for MS-windows which doesnt use Grub..If you do happen to take interest in 9.10, the live disk does provide info under the 'disk utility' menu option that will give you a pretty good idea of what the install is going to look like. If I were you, I would image the system first using partimage (sysrescue) and proceed cautiously. good luck
pete

---

### Post by billpanepinto on 2009-10-28
> **Dragonbite said:**
> Windows is selfish and wants to be the ONLY operating system on your machine, so install Windows first.  

Ubuntu includes some good-citizen features that allows it to detect your Windows installation and offer to install Ubuntu right alongside Windows.

Thanks so much for the speedy response!

Do you (or anyone else) have any advice on optimal partitioning? Right now I have the following (decidedly less-than-optimal) partitions:

100 GB ext4 (Ubuntu)
120 GB ntfs (data)
4 GB linux-swap

Should I use gparted live cd to delete all partitions prior to install? Any thoughts?

Thanks again,
Bill

---

### Post by Dragonbite on 2009-10-28
Do you have the Windows CD?  The reason why I ask is so that if anything happens, chances are it will be in the bootup process and the CD can fix that so you can boot back into Windows.

I would first install Windows, then use the partitioner in the course of installing Ubuntu. That way you can make sure it sees the Windows partition.

The first partition HAS to be Windows.. after that it can be anything.

Ubuntu is pretty good about being able to read/write NTFS, and there is a driver that allows Windows to see (mount) ext2 and ext3 partitions but from what I've heard it doesn't work with ext4 yet.  Could also use vFat which both systems can understand.

---

### Post by Robbartz on 2009-10-29
Hard drives are pretty cheap these days and there are plent of very cheap used ones on EBay. Just add a second drive and install Ubuntu on that one.

---


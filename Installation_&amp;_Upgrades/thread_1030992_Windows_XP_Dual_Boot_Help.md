---
title: "Windows XP Dual Boot Help"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by den160593 on 2009-01-04
Hi,

I tried to install Ubuntu on my Windows XP machine with dual boot. Now what I did was put the CD in and install like that, and all was going well (I think?) until I got an error on my disk. Says that some file was missing from when I burnt my disk.

This means that I have 2 partitions on my Windows that I have no clue about. I'll try and explain because i personally don't really understnad what happened.

On my computer I have a C drive and a D drive (windows) E drive (where I wanted to install Ubuntu onto... didn't work though - this drive is 20gig and empty) an F partition for programs and two more partitions for my personal storage space (G and H).

What ubuntu did was cut out most of my H drive and completely stuff up. So I was wondering. Is there any way for me to reset my partitions to the way they were before and I'll reburn the disk and then install it on my E partition that I had designated for another Operating System?

If you need any more info I can help, because I don't fully understand what happened.

Thanks
-Den

---

### Post by den160593 on 2009-01-04
Actually. Is there a way to install Ubuntu onto my E drive partition (that I have named Ubuntu) and leave the Windows drive as it is in the installation?

---

### Post by thomas228 on 2009-01-04
> **den160593 said:**
> Actually. Is there a way to install Ubuntu onto my E drive partition (that I have named Ubuntu) and leave the Windows drive as it is in the installation?

Hi 
I hesitated in answering your post as I am not a linux expert.

Edit:[COLOR="Blue"] In answer to this post yes it is possible[/COLOR] :end of edit

A number of questions about your problem

What version of ubuntu were you trying to install? 8.04 or 8.10

Does the ubuntu disk allow you to run ubuntu without affecting your system?  Livecd

In your first post you interchange drivee and partitions in your discription.

How many physical disks does your system have and how is each partitioned?

Answeres to these questions in as few postings as possible will likely bring you expert help.

There are people who monitor the forum for unanswered posts so the fewer the posts the sooner you'll get that help.

Edit:  [COLOR="Red"]Just wait for some good help It may take a while so hang tight [/COLOR]:end of edit

Good luck

Tom[COLOR="Blue"][/COLOR]

---

### Post by den160593 on 2009-01-04
Hi. Yeah I couldn't figure out how to edit my post :(


> What version of ubuntu were you trying to install? 8.04 or 8.10
8.10

> Does the ubuntu disk allow you to run ubuntu without affecting your system? Livecd
Yes, and i tried it and it worked good. however i did the initial instalation through the initial screen (Went down to install)

> In your first post you interchange drivee and partitions in your discription.
Um. I have a C drive which i don't really use. D drive is for Windows. I have E drive empty and that's where I want to install Ubuntu onto. On my previous attempt I did it all in the automatic installation, and it cut my H drive (where I store general stuff) into bits, which isn't what I wanted. As my E drive is 20gig and should be enough.

> How many physical disks does your system have and how is each partitioned?
I have one. Although I do have a separate back up physical drive.


Thanks for response. I want to ensure that I don't stuff up this time ;)

---

### Post by logos34 on 2009-01-05
Here's one way you could do it:

Delete the E: drive--either from within windows, or use gparted on the ubuntu live cd (>System>admin>partition editor).

Start the installer as before but this time select 'Manual' partitioning option instead of 'Guided'.  

Create an **extended** partition out of the empty space formerly E:

In inside the extended create a **logical** partition for swap ('linux-swap') with mountpoint '/swap'.  size 1-1.5 x installed ram (especially if you want hibernate option).  

Give the rest to root:  logical partition (ext3) with mountpoint '/'.

---

### Post by den160593 on 2009-01-05
Ok thanks. So just to clear something up before I do it. What is a mouthpoint? Will I be easily able to see how to do that during the installation?

---

### Post by logos34 on 2009-01-05
like this:

[IMG]http://www.easy-ubuntu-linux.com/images/install-new-partition-mount-pts.png[/IMG]

take a look at t[he tutorial]("http://www.easy-ubuntu-linux.com/ubuntu-installation-606-12.html")--it's for 7.04 but not much has changed.

---

### Post by teddeman on 2009-01-07
Is it possible to use the Windows Boot loader or do you have to use GRUB?

---

### Post by logos34 on 2009-01-07
You can use either bootloader to chainload the other OS, but Grub is a lot better.

If it's simply an issue of wanting ubuntu to be inconspicuous on a family windows machine, there are settings in the Grub config file (/boot/grub/menu.lst) that you can adjust--like making windows the default boot OS and 'hiddenmenu'

---

### Post by torgrot on 2009-01-07
You could also use WUBI until you get a little more familiar with Ubuntu.  It will allow you to install from Windows.  Then if you like it can be converted to its own installation or removed if you for whatever reason don't like it.  Reburn the CD and install under Windows.  There is another group here for issues relating to WUBI.

torgrot

---


---
title: "I have BOOTING problem"
date: 2008-08-08
forum: General Help
---

### Post by sendblink23 on 2008-08-08
*note... READ MY LAST PAGE POST!

.................................
Ignore this below
.................................

Well I simply had connected my lan to get internet to be able to update the stuff in ubuntu ...  well suddenly my computer automaticly shutted down ...  Well I booted it up again, and well i logged in again ... right tehre after the password ...  it stayed there with  the peach background ...  a long while all the sudden a TOP  Left White square ...     it stays like that for a few minutes. .. (i press  many keys in teh keyboard to see if it reacts) ...   then all the sudden  this ERROR  comes up
..............................

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
..................................


Well  since before i made any of the updates or connect the internet  it used to Boot up really fast, and ran smothly everything in ubuntu ...  just now...   I'm always getting that problems always  ater booting..  rigth after enterin my login and pass ..



Well if anbody could help me fix my problem .. That would be grateful ;)

---

### Post by nazish on 2008-08-08
if you are able to log into Gnome try running the command 

```
sudo apt-get update
```  in the terminal.
Hope it corrects your problem

---

### Post by thestig_992 on 2008-08-08
If you cant log in at all theres always the live cd, its probably possible to reinstall gnome from there

---

### Post by sendblink23 on 2008-08-08
> **nazish said:**
> if you are able to log into Gnome try running the command 

```
sudo apt-get update
```  in the terminal.
Hope it corrects your problem

Yes I'm always able to login and pass on to inside ubuntu, its just after  I do input the login and pass.. thats where the problm happens.. and it takes about 15 min .. to go to show the desktop and the Error message

I did ran that command before, and it really didnt change anything after doing a Restart again, yes I did put again just about now to do it again incase ..

---

### Post by sendblink23 on 2008-08-08
> **thestig_992 said:**
> If you cant log in at all theres always the live cd, its probably possible to reinstall gnome from there

can i fix the Install ...  like a Repair option from the live CD then ?, I dotn want to create another partition and stuff

---

### Post by sendblink23 on 2008-08-08
Now i want to know.. is there a way to Re-Fix everything ...I've had  already installed.. the Partition .. could I make a REFRESH  *Ubuntu  fix to it replacing the Current installed partition?

---

### Post by Mgiacchetti on 2008-08-08
i see someone told you 
sudo apt-get update

and you said that that doesnt really do much.  That is because it just updates the program versions in synaptic, (your installable programs list)  

run that above, then run this

sudo apt-get upgrade

and see if that does anything to fix your problem.


Was this a clean install, or an upgrade from a previous version of ubuntu?

---

### Post by UbuntuNerd on 2008-08-08
Read in this links the have the same problem and a solution maybe it will also work for you
[http://depratama.wordpress.com/2007/12/19/ubuntu-error-starting-the-gnome-settings-daemon/]("http://depratama.wordpress.com/2007/12/19/ubuntu-error-starting-the-gnome-settings-daemon/")

[http://ubuntuforums.org/showthread.php?t=500160]("http://ubuntuforums.org/showthread.php?t=500160")

---

### Post by sendblink23 on 2008-08-08
> **Mgiacchetti said:**
> i see someone told you 
sudo apt-get update

and you said that that doesnt really do much.  That is because it just updates the program versions in synaptic, (your installable programs list)  

run that above, then run this

sudo apt-get upgrade

and see if that does anything to fix your problem.


Was this a clean install, or an upgrade from a previous version of ubuntu?


NEW Clean Install 2 days ago, ..... anyways Tried it and yes still nothing, no changes at all....

> **UbuntuNerd said:**
> Read in this links the have the same problem and a solution maybe it will also work for you
[http://depratama.wordpress.com/2007/12/19/ubuntu-error-starting-the-gnome-settings-daemon/]("http://depratama.wordpress.com/2007/12/19/ubuntu-error-starting-the-gnome-settings-daemon/")

[http://ubuntuforums.org/showthread.php?t=500160]("http://ubuntuforums.org/showthread.php?t=500160")




it would work.. but Actually cuase i have changed so much stuff already messign around to try to fix the Wifi problem.. before.. this error started happening ...   Well I think i want to FRESH  reinstall it  (just to have everything back as Default.. with no alteration of anything i have done to it)...   now back to my Last Question

"is it safe, i mean try to do the live CD thing ...  does it Re Fix my partition I had made to this Ubuntu a currently have to REPLACE it all again over it.. FRESH new ..   not having to make another new partition ?

---

### Post by Mgiacchetti on 2008-08-08
Well, here's what you can do.  [make a list]("http://ubuntuforums.org/showthread.php?p=1990911") of all the programs you have installed. save it to usb flash drive... 

pop in your 8.04 cd and restart

in Live CD Mode, go ahead and run that list as the link says, and install all the pro's you had, Run Ubuntu Setup and this time SEPERATE THE / AND /HOME

---

### Post by sendblink23 on 2008-08-08
> **Mgiacchetti said:**
> Well, here's what you can do.  [make a list]("http://ubuntuforums.org/showthread.php?p=1990911") of all the programs you have installed. save it to usb flash drive... 

pop in your 8.04 cd and restart

in Live CD Mode, go ahead and run that list as the link says, and install all the pro's you had, Run Ubuntu Setup and this time SEPERATE THE / AND /HOME

Can you explain that last part ... "and this time SEPERATE THE / AND /HOME" ???  i dont get it

I honestly dotn really care of anything I've already installed in the Current Ubuntu .. i just want to go back FRESH default..  fresh install

---

### Post by sendblink23 on 2008-08-08
so .. can anybody tell me if i can reinstall it (from Live CD) again over  REPLACING my current partition i have with my Current ubuntu, i dont want to make a new partition ??

just Incase .. Yeah because I've separated Both partitions  Windows XP 1 Terrabyte, and Ubunto the other Terrabyte left in my Hard Drive

I'm asking because i haven't tried it.. so i just want to know Before I go straight to do it

---

### Post by linux_tech on 2008-08-08
Have you tried a Super Grub disk yet? 
Super Grub Disk is a bootable floppy or CDROM that is oriented towards system rescue, specifically for repairing the booting process.   It can activate partitions, boot partitions, boot MBRs, boot your former OS by the loading menu.lst from your hard disk

[http://forjamari.linex.org/frs/?group_id=61&release_id=632#632](http://forjamari.linex.org/frs/?group_id=61&release_id=632#632)
[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by sendblink23 on 2008-08-08
> **linux_tech said:**
> Have you tried a Super Grub disk yet? 
Super Grub Disk is a bootable floppy or CDROM that is oriented towards system rescue, specifically for repairing the booting process.   It can activate partitions, boot partitions, boot MBRs, boot your former OS by the loading menu.lst from your hard disk

[http://forjamari.linex.org/frs/?group_id=61&release_id=632#632](http://forjamari.linex.org/frs/?group_id=61&release_id=632#632)
[http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)



READ my last post broo...  I'm askign simply now.. for Reinstallation from Live CD to replace my Current ubuntu.. and my current Partition ... is that Safe  in the Live CD to re install FRESH again ?

---

### Post by sendblink23 on 2008-08-08
Well .. guys read my last Post ...  I have a 1 FULL Terrabyte *1,000gb* (which I have it as the partition of my Current Ubuntu)  that I want to replace again, Fresh RE INSTALL  with LIVE CD, .. is that Safe to do it ?

---

### Post by linux_tech on 2008-08-08
Yes the Live cd should work fine to do a clean install of Ubuntu 
It will allow you to set up partition .

---

### Post by sendblink23 on 2008-08-08
read below sorry

---

### Post by sendblink23 on 2008-08-08
> **linux_tech said:**
> Yes the Live cd should work fine to do a clean install of Ubuntu 
It will allow you to set up partition .



To set up partition ...   as in I can Replace my Current partition ??

---

### Post by linux_tech on 2008-08-08
The LiveCD (recent version) should allow you to do all of the following:

1) Delete Ubuntu
2) Delete the Ubuntu partition
3) Resize the Windows partition to fill the former Ubuntu partition.

Using fdisk you can also delete or recreate a partition also

---

### Post by sendblink23 on 2008-08-08
> **linux_tech said:**
> The LiveCD (recent version) should allow you to do all of the following:

1) Delete Ubuntu
2) Delete the Ubuntu partition
3) Resize the Windows partition to fill the former Ubuntu partition.

Using fdisk you can also delete or recreate a partition also

Thanx thats what I was looking foward to, i managed to do it right now ;)

---


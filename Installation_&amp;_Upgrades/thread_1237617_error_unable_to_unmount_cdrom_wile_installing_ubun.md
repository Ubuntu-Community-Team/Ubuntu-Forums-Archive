---
title: "error unable to unmount /cdrom wile installing ubuntu from hard disk using unetbootin"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by VACSecured on 2009-08-11
so i curently have xubuntu Xfce installed on my computer, and i am trying to swithch to ubuntu super OS using the program unetbootin and installing the ISO right on the hard drive. (i also tried this with mint linux and got the same error) i can get in the instalation menu and partition it, but when it starts to install i get and error that says it cannot unmount /cdrom please close all programs using it and try again. so i am no computer wiz or linux wiz for that matter, i am just getting into linux and i am still trying to learn as much as i can, but from what i do no i have tried to go into the terrminal and using the bash command "umount" mannually unmount /cdrom from the live boot and it says that it is busy, so now i don't know what to do. . i tried it in Xfce before i restart "sudo umount /cdrom &" and it still doesn't work sorry if i seem retarded lol but im still new to all this.
 
this is the exact error message:
failed to unmount partitions 

the installer needs to commit changes to partition tables,
 but cannot do so because partitions on the following could
 not be unmounted.

/cdrom

please close any applications using these mount points.

would you like the installer to try to unmount these partitions again

                                                              go back      continue

if anyone could share some insight as to what i am doing wrong it would be greatly appreciated!

---

### Post by YaPaY on 2009-11-08
> **VACSecured said:**
> so i curently have xubuntu Xfce installed on my computer, and i am trying to swithch to ubuntu super OS using the program unetbootin and installing the ISO right on the hard drive. (i also tried this with mint linux and got the same error) i can get in the instalation menu and partition it, but when it starts to install i get and error that says it cannot unmount /cdrom please close all programs using it and try again. so i am no computer wiz or linux wiz for that matter, i am just getting into linux and i am still trying to learn as much as i can, but from what i do no i have tried to go into the terrminal and using the bash command "umount" mannually unmount /cdrom from the live boot and it says that it is busy, so now i don't know what to do. . i tried it in Xfce before i restart "sudo umount /cdrom &" and it still doesn't work sorry if i seem retarded lol but im still new to all this.
 
this is the exact error message:
failed to unmount partitions 

the installer needs to commit changes to partition tables,
 but cannot do so because partitions on the following could
 not be unmounted.

/cdrom

please close any applications using these mount points.

would you like the installer to try to unmount these partitions again

                                                              go back      continue

if anyone could share some insight as to what i am doing wrong it would be greatly appreciated!


Same problem here Is there nobody can answer this problem exactly?

---

### Post by nisix on 2009-11-08
I ran into this problem when I was installing jaunty from 1 hdd to another.

I got around it by choosing 'use entire hdd' in the partition manager rather than manually partitioning it.

migration-assistant also has this issue with unmounting the cdrom; if you ran into it type

sudo ubiquity --no-migration-assistant

in the livecd's terminal. And lastly, the 'configuring apt' portion of the install process cannot read the packages from the mounted iso. It's just good that I have a working internet connection so it just downloaded what it needs from the net.

This is not exactly ubuntu super os but I hope my experience helps.

---

### Post by VACSecured on 2009-11-08
i couldn't ever figure it out, i ended up just burning a live cd and installing it that way. . my friend thinks it might be because i originally bought my computer from dell and it's pretty old. we think it's something with the hardware and all the crap they change in the bios. i couldn't get it to boot from a flashdrive either. so sorry im not more help im still pretty new to linux just switched over this year. lol but thanks for the tips. i will deffinatly try that the next time i switch distros!

---

### Post by burgerearl on 2009-11-20
I am also having this problem trying to install using unetbootin. I also have a dell (laptop).

I don't have access to a blank CD right now - has anyone found a workaround using unetbootin?

---

### Post by johnraff on 2009-12-11
Have you tried the "netinstall" option in unetbootin? It's worked for me a couple of times.

---

### Post by jazf78 on 2010-02-24
I am also having this problem

obviously i cannot tell the partition to use all available space since im using unetbootin and the ubuntu files are inside that ntfs partition so logic tells me where would ubuntu read the installation files from?


I am installing on a computer that does not have a cd reader.

nor does it have usb boot capabilities.


Any help??

---

### Post by bacchusmarsh on 2010-04-19
same problem, but...i found this post which has a work around which is working for me!

[http://ubuntuforums.org/showthread.php?t=1237721&highlight=the+installer+needs+to+commit+changes]("http://ubuntuforums.org/showthread.php?t=1237721&highlight=the+installer+needs+to+commit+changes")

---

### Post by Chaos234 on 2010-05-01
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/313452](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/313452)

---

### Post by irpsit on 2010-12-15
This is from my previous thread
[http://ubuntuforums.org/showthread.php?p=10241015](http://ubuntuforums.org/showthread.php?p=10241015)
 
 I ran the frugal install from Unetbootin.
 
 First thing, I went to the console and did sudo umount  -l -r -f  before clicking on the installer!
 
 Then, I start the installer, choose language, then choose partitions to  install (advanced configuration). [B]This solved the error "no root file  system defined"
[/B] 
 I choose a free partition as ext3 and mounted as /
 And a second one choosen as swap.
 The two remaining partitions were Windows (sda1) and windows recovery disk.
 **This solved the error "the installer needs to commit changes to  partition tables, but cannot do so because partitions on the following  could not be unmounted /cdrom"**
 
 Then, very important, just before I pressed "install now", I opened  again the console and typed sudo mount /dev/sda1 /cdrom (so, **this solved a fatal error that was crashing the ubuntu installation**)
 And it is copying the files now! :grin:

---

### Post by maximo360 on 2011-07-10
has anyone figured out a workaround for this I have the same problem for ubuntu11.04?

---

### Post by Pierre1976 on 2011-07-17
After encountering this problem with several ubuntu distributions that I wanted to install using a netbootin frugal install, I found that the most satisfying workaround was to use the minimal (mini.iso) install, or "netinstall" from unetbootin options. It always works like a charm, it just requires a little more interventions from the user. At the end of the installation process, you will have to pick up the exact distribution (Gnome, XFCE) that you want to use from a list. You can even install Lubuntu that way, they have a very clear how-to guide on their wiki.

---

### Post by ratan biswas on 2011-09-25
> **YaPaY said:**
> Same problem here Is there nobody can answer this problem exactly?
so  i curently have xubuntu Xfce installed on my computer, and i am trying  to swithch to ubuntu super OS using the program unetbootin and  installing the ISO right on the hard drive. (i also tried this with mint  linux and got the same error) i can get in the instalation menu and  partition it, but when it starts to install i get and error that says it  cannot unmount /cdrom please close all programs using it and try again.  so i am no computer wiz or linux wiz for that matter, i am just getting  into linux and i am still trying to learn as much as i can, but from  what i do no i have tried to go into the terrminal and using the bash  command "umount" mannually unmount /cdrom from the live boot and it says  that it is busy, so now i don't know what to do. . i tried it in Xfce  before i restart "sudo umount /cdrom &" and it still doesn't work  sorry if i seem retarded lol but im still new to all this.
 
this is the exact error message:
failed to unmount partitions 

the installer needs to commit changes to partition tables,
 but cannot do so because partitions on the following could
 not be unmounted.

/cdrom

please close any applications using these mount points.

would you like the installer to try to unmount these partitions again

                                                              go back      continue

if anyone could share some insight as to what i am doing wrong it would be greatly appreciated!
 		                   		  		  		  		  		 		 			 				 				* 					 						Last edited by VACSecured; August 12th, 2009 at 12:59 AM.. 					 					 						Reason: add error message 					 				* 			
 		 		  	   	 		[IMG]http://ubuntuforums.org/images/statusicon/user_offline.gif[/IMG]   		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7769950") 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=7769950") 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/multiquote_off.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=7769950") 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quickreply.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=7769950")

---


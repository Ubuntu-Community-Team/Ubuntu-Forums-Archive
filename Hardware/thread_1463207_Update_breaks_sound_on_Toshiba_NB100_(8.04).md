---
title: "Update breaks sound on Toshiba NB100 (8.04)"
date: 2010-04-26
forum: Hardware
---

### Post by JohnMoriarty on 2010-04-26
My NB100 (with the original installed OS, kept updated) installed a whole batch of updates today (it described itself as a distribution upgrade, but I'm still on 8.04, so this is puzzling me). 

The only problem I've found is that the sound doesn't work after update. Booting to previous kernel (2.6.24-24-lpia), everything ok; booting to new one (2.6.24-27-lpia), no sound devices found, and pavucontrol reports segmentation fault and crashes.

Is this peculiar to my computer, and if so how do I fix it? If it is a common problem, still, can it be fixed?

Thanks

---

### Post by stape on 2010-04-28
I have the same hardware and software version and the same problem, exactly.

Booting to previous kernel (2.6.24-24-lpia), everything OK also

---

### Post by JohnMoriarty on 2010-04-28
Glad to hear it is not just me.

As a temporary fix I've changed the default kernel in GRUB's menu.lst. (I don't know enough about this to recommend it but it worked for me.)

I've noticed that Update Manager has a greyed out update that won't install, linux-image-lpia. Use Synaptic I see that the installed version is 2.6.24.24.26-0netbook1 and there should be a version 2.6.24.27.29-0netbook1, but when I try to install (using Synaptic) I get the error message 
```
linux-image-lpia:
 Depends: linux-ubuntu-modules-2.6.24-27-lpia  but it is not installable
```

Any ideas for a better fix?

Thanks

---

### Post by stape on 2010-04-28
> As a temporary fix I've changed the default kernel in GRUB's menu.lst. (I don't know enough about this to recommend it but it worked for me.)

I've noticed that Update Manager has a greyed out update that won't install, linux-image-lpia.

I changed the default kernel using startup manager and also have the same greyed out update.

---

### Post by Mick_Red on 2010-05-02
I also have a Toshiba NB100 with 8.04 that has regularly updated without issue since July 2009, until 28/04/2010, when the update has resulted in the sound and web cam not working. I have found the following..........

~$ ls -la /dev/snd
ls: cannot access /dev/snd: No such file or directory
michael@TOSHIBA-User:~$ dpkg -l linux-ubuntu-modules-2.6.22-14-386
No packages found matching linux-ubuntu-modules-2.6.22-14-386.

Can someone please advise a way forward with this issue

---

### Post by Mick_Red on 2010-05-03
In addition to the sound issue, I have discovered that Skype is now broken since the update of the 28/04/2010, prior to the update the speech and video using Skype worked very well, after the update on attempting to launch skype via CLI I see the following.........................

libQtDBus.so.4 cannot be found

I assume this is a library file, have any other NB100 users on 8.04 had this happen since the update?

---

### Post by mo79 on 2010-05-05
You guys should upgrade to UNE 10.04, I did this on my NB100 and *everything* worked fine - the only thing you lose is the Toshiba logo in the UNE interface. You'll have to do a clean install as the provided 8.04 has been modified to not be upgradeable. This also of course fixes the breaks in the last 8.04 update for this machine (I too had loss of sound, webcam not working and keyboard mapping going weird).

---

### Post by dino99 on 2010-05-05
to install old kernel:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by stephenlamb on 2010-05-23
This issue has been bugging me for a few weeks.  The suggestion of booting the previous kernal works for me so thanks everyone for suggesting that.  It is not a very satisfactory fix long term though so I hope someone who is cleverer than I comes up with something better!

Thanks again to the people who posted to this thread.

---

### Post by Mick_Red on 2010-05-24
I followed the advice to upgrade to 10.04, I was a little nervous about doing this as everything including Skype had been working reliably on 8.04. Apart from 2 minor issues, one with Skype, and the other, changing back from UNE to the familiar 4 desktop Gnome front end. I am happy that the main applications are working well now with 10.04 UNE OS.
If any other NB100 owners feel uncertain about upgrading, I can write a step by step procedure on how I was able to do this with the help of a Windows PC.
The only expenditure was £4.99, buying a Sony 2Gb memory stick from Sainsbury's, which is now my dedicated "rescue disc"

---

### Post by BobC1955 on 2010-06-29
Thank goodness I've found some others with exactly the same problem as me with 8.04 on my Toshiba NB100 - loss of sound.
 
I am a complete beginner with Ubuntu and was getting close to ditching it altogether and getting windows uploaded instead. If you could explain simply how I can safely load the latest version (10.04) I'd be very grateful as I was very nervous about doing this!
 
as to the other explanations regarding booting using different kernels that is complete greek to me!
 
Thanks:confused:

---

### Post by Mick_Red on 2010-06-30
Don't give up! 10.04 UNE is a good OS; Below is how I upgraded
Mick_Red..............

  	 	 	 	 	 	  [SIZE=4]_Upgrading Toshiba NB100-11R To Ubuntu 10.04_[/SIZE]
 

 **Pre-requisites**  
 
[LIST=1]
[*]One 2Gb USB flash drive 	(a few pounds, this will be a future recovery “disc”).
[*]From Ubuntu site 	download the the 10.04 UNE ISO image (700Mb file).
[*]Following the the links 	from the Ubuntu site, download the UNETBootin program, I used the 	Windows version as I have a windows XP desktop PC it was convenient 	to use.
[*]Backup facility, i.e. 	another PC, SD card, another flash drive for bookmarks, address 	books, and all personal data off your Netbook.
[/LIST]
 [SIZE=3]_**Procedure**_[/SIZE]
 

 
[LIST=1]
[*]Back up all your 	personal data, address book, bookmarks etc. and have ready 	passwords, wireless keys etc. All the data needed to rebuild your 	Netbook.
[*]On a windows PC (or 	whatever PC is available download the Ubuntu 10.04 UNE file 700Mb, 	**DO NOT UNZIP** from here 	[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)
[*]Download UNETBootin 	from here [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) 	on Windows PC just double click on UNETBootin file to run it set it 	up so that the downloaded 10.04 UNE file is the source.
[*]Insert the 2 Gb flash 	drive into a USB socket on the Windows machine, note the drive 	letter, at the bottom of the UNETBootin window select that drive 	letter, select OK and what a few moments for UNETBootin to install 	the Ubuntu 10.04 onto the flash drive(it will indicate when 	complete, ignore the reboot now and close UNETBootin), the flash 	drive is now ready to use.
[*]Boot up the Netbook, 	pressing F2 at the point where it boot options is displayed(during 	1st few seconds of boot up), use arrow keys to select 	boot options use F7/F8 key to move USB drive to the top of the boot 	list, before saving and rebooting from the BIOS menu insert the 	flash drive prepared in step 4.
[*]The Netbook now reboots 	from the flash drive. in the application icons displayed, an install 	Ubuntu icon is shown. **BEFORE PROCEEDING: WERE ALL FILES BACKED 	UP?!**
[*]Follow 	the prompts from the Install option and install Ubuntu 10.04 on the 	80Gb hard disc, which will format and overwrite the 8.04 version, 	after setting time date etc, at the end the Netbook can be rebooted 	and will boot up to the new version from the 80Gb HDD.
[/LIST]
 

 _**PROBLEMS**_
 
[LIST=1]
[*]I 	did not like the new look layout, if like me you want to use the 	same old 4 window Gnome it can be selected from a menu bar at the 	bottom of the log in screen seen when booting up.
[*]When 	I installed Skype I did not have any sound until I opened the Skype 	option window, select sound devices and selected the sound device, I 	only  had to do this once, now Skype works every time.
[/LIST]

---

### Post by Otty DJ on 2010-08-11
> **stape said:**
> I have the same hardware and software version and the same problem, exactly.

Booting to previous kernel (2.6.24-24-lpia), everything OK also

As a total novice, how do i do this?

---

### Post by Mick_Red on 2010-08-14
I think the best way forward is to upgrade to Ubuntu 10.04 as described previously in this thread, this has the additional benefit of creating a recovery flash drive for possible future problems.
Read through the procedure I posted and see if you can follow it, and ask if unsure on any part of it.

---


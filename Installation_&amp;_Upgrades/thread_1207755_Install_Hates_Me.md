---
title: "Install Hates Me"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by ldach33 on 2009-07-08
Hi,

I am ready to slam my head between two bricks and go back to Vista.

I have a Dell Optiplex 755 that I originally installed 9.04 on without issues and then I decided to remove a pile of software that I didn't think I would use and the result on restart was a black screen after login.

Not a problem so I thought and then proceeded to just reinstall with the same disc.  NOT GOOD!!!

It has now been over 100 install attempts using every suggestion or idea I can find via google and I still receive the errno 5 error with every single install attempt of Ubuntu or any Debian based Linux that I have tried so far.

The only changes to the system from the original install where plugging in a larger wide screen monitor and changing from a wireless keyboard and mouse to a trackball and usb keyboard.

I have even gone as far as putting the old monitor, keyboard and mouse back but to no avail.

Every single install hangs with the errno 5 error at 52%.

I have re-downloaded the ISO (using 64bit) on multiple systems and re-burnt the image on several types of DVD-R, DVD+R and CDR on 3 different burners but still no luck.

I thought that maybe the HDD had died with convenient timing so I replaced the 80G SATA Western Digital drive with another SATA WD Drive but no change.

I cannot try another CD/DVD drive as the one in this system is SATA and the only other ones I have as parts are IDE.  Also, there are no free data or power cables in the machine.

Media checks and memory checks all come through with flying colours so I am out of ideas.

I even tried the memory trick where you only use a single dimm (I have 4 slots, with 2*1G and 2* 2G dims) but no luck, I have re-run the install with each dimm installed by itself in each bay.

The only thing that I can get to install is SUSE but I don't like it.  I am only new to Linux and Ubuntu recognises my USB wireless card and network printers where SUSE will not.

Please help me before I get stuck back with MS C%apola.


Cheers,
Ad

---

### Post by unlimitedz on 2009-07-08
Is there some kind of RAID configuration for the system?  Are there 2 HDD's in there or just one?

---

### Post by ldach33 on 2009-07-08
There is only a single 80G Western Digital HDD installed as well as a single Dell Slimline DVDROM installed.  Both SATA.

---

### Post by merlinus on 2009-07-08
Have you tried using gparted to delete, recreate and format your linux partitions?

---

### Post by ldach33 on 2009-07-08
Don't know if it is of any help but after the errno 5 error at 52%, I end up with the normal Ubuntu background and a mouse cursor but nothing else.

If I then restart the system, it takes me straight to the Ubuntu desktop running from the CD where I have the option of 'Install'.

If I try to install again from here, same issue where it fails at 52%.

I have also tried to install with 'acpi=off' and 'noapic', same problem.

---

### Post by merlinus on 2009-07-08
Another thing to try is the alternate text-based install cd.

---

### Post by ldach33 on 2009-07-08
At the risk of sounding like an idiot, I am only new back to Linux.  My last attempt 10 years ago was just as painful.

I don't know what gparted is or where I can get it to use.

From all of my Google searching, I gathered that it killed and rebuild the partitions.  What I have done is tried to install with a HDD that already had XP installed and selected the option to 'use entire disc' when it come to repartitioning during install as well as try with a completely new blank HDD.

---

### Post by merlinus on 2009-07-08
In that case, I would suspect the cd drive and/or disks.  The other possibility is that the installation is trying to access files from the web, and cannot connect.

---

### Post by ldach33 on 2009-07-08
That is the only other thing that has changed (didn't think of it), when the initial install happened, the PC was plugged directly into my router.
 
Have just restarted the process while plugged in and will see how it goes.
 
I am also downloading the alternate install CD as well.

---

### Post by zoomy942 on 2009-07-08
on the live cd i had a ton of troubles until i did this...

open terminal...

type this

ubiquity --no-migration-assistant

---

### Post by ldach33 on 2009-07-08
Really dumb question, how do I open terminal during the install?

---

### Post by zoomy942 on 2009-07-08
not a dumb question.

are you using a live cd?

---

### Post by ldach33 on 2009-07-08
I'm using the ISO downloaded from ubuntu.net Not too sure if that is the live CD or not.
 
PS - Install just failed again with the network cable pugged in.

---

### Post by merlinus on 2009-07-08
Worth doing a checksum on the .iso:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by zoomy942 on 2009-07-08
yes.  do a checkSUM.  but also, burn a liveCD Iso to a CD.  when you boot from it simply choose the option called "Try Ubuntu Withjout Changing My Computer"....

once you get there go to Applications at the top then accesories then terminal.

---

### Post by ldach33 on 2009-07-08
Checksum is perfect, now just waiting while the 'ubiqity --no.......' option runs.

---

### Post by zoomy942 on 2009-07-08
wait.  so you booted from the livecd and are now running that command in terminal?

---

### Post by ldach33 on 2009-07-08
yep, and holding my breath as it is now at 57% which is better than ever before.
 
If this works, I love you...  (in a not too strange way)

---

### Post by zoomy942 on 2009-07-08
lol.  excellent.  i am standing by.  update us becasue if it helps, its something we need to be sure people know about.

---

### Post by ldach33 on 2009-07-08
WOOHOO!!!!!!!!!!!!
 
If only this post had of existed before, I would have saved 4 full days of hell trying to install Ubuntu.
 
Thank you SOOOO much.  It WORKS!!!!  I have just installed and booted Ubuntu successfully thanks to your help.
 
For dexterity sake (so searches pick it up for others):
 
The error: 
 
The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.
 
In my case was resolved thanks to the fantastic advice from zoomy942 as follows:
1. Boot from the live CD
2. Choose to try Ubuntu
3. Open a terminal window
4. Enter: 'uniquity --no-migration-assistant'
5. Working install

---

### Post by running_rabbit07 on 2009-07-08
Congrats!

---

### Post by zoomy942 on 2009-07-08
im very glad i could help you.  Enjoy some ubuntu!

---

### Post by squirl1899 on 2012-01-16
> **ldach33 said:**
> WOOHOO!!!!!!!!!!!!
 
If only this post had of existed before, I would have saved 4 full days of hell trying to install Ubuntu.
 
Thank you SOOOO much. It WORKS!!!! I have just installed and booted Ubuntu successfully thanks to your help.
 
For dexterity sake (so searches pick it up for others):
 
The error: 
 
The installer encountered an error copying files to the hard disk:
 
[Errno 5] Input/output error
 
This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.
 
In my case was resolved thanks to the fantastic advice from zoomy942 as follows:
1. Boot from the live CD
2. Choose to try Ubuntu
3. Open a terminal window
4. Enter: 'uniquity --no-migration-assistant'
5. Working install
 
I know this is an OLD thread but I have been trying for FIVE days, countless downloads, Ubuntu USB installers, CD's, DVD's and USB sticks, to install Ubuntu Desktop 11.10 and have had no luck. I always get [Errno 5] Input/output error and have been searching for an answer and solution.  THIS WORKED FOR ME!!!!!!!  THANK YOU SSSSSOOOOOOOO MUCH!
 
1. Boot from the live CD
2. Choose to try Ubuntu
3. Open a terminal window
4. Enter: ubiquity --no-migration-assistant
5. Working install

---

### Post by oldos2er on 2012-01-16
Closed, necromancy.

---


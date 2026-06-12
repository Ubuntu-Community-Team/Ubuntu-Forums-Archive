---
title: "Ubuntu 11.10 on a HP dm4t 2000 (aka HP dm4x)"
date: 2012-01-29
forum: Hardware
---

### Post by amoxicillin on 2012-01-29
I've been setting up Ubuntu 11.10 on my HP dm4t 2000 and just wanted to  post some of the problems I have come across, fixes that worked for me,  and my overall opinion of this machines compatibility with Ubuntu.  I  figure this could be a general overall viewpoint for anyone interested in a HP dm4.  I posted here as opposed to the compatability/incompatability lists because the post is a little long.

The problems I have come across:

1. Too many partitions to dual boot with Windows
2. Alps touch pad is uncontrollable
3. Wireless is slow and erratic
4. Screen is black upon login screen

Solutions:

1. HP already partitions the hard drive 4 times.  Which is the limit for partitioning.  This leaves you with the awkward decision of either having to delete your recovery partition or the Fat32 HP Bios partition.  If I had to choose between the to two (I didn't) I would make a recovery USB or DVD (it is about 1.5 GB) and not delete the HP Bios partition.  I already know how to access BIOS without having to go through their Windows access partition but know how much they run updates I would imagine that clearing that partition could cause all sorts of update issues in the future.  For now I am using Wubi until Ubuntu 12.04 LTS is released and I can try again.

2.  The Alps touch pad has been giving people a lot of problems.  I tried adjusting the settings with no luck.  This video on youtube is what eventually solved my problem:

[http://www.youtube.com/watch?v=KBD9D5nA9AI&feature=fvsr](http://www.youtube.com/watch?v=KBD9D5nA9AI&feature=fvsr)

Here is what he explains in the video:

Open the terminal and type:

gedit /etc/default/grub
   
  Then it look for the section of the gedit program text that says:
   
  GRUB_DEFAULT=0
  #GRUB_HIDDEN_TIMEOUT=0
  GRUB_HIDDEN_TIMEOUT_QUIET=TRUE
  GRUB_TIMEOUT=10
  GRUB_DISTRIBUTOR=’lsb_release –I –s 2> /dev/null || echo Debian’
  GRUB_CMDLINE_LINUX_DEFAULT=”quite splash”
  GRUB_CMDLINE_LINUX=””
   
  Inside the quotations marks at the very end type:
   
  i8042.reset i8042.nomux i8042.nopnp i8042.noloop
   
  The last line should then look like this:
   
  GRUB_CMDLINE_LINUX=”i8042.reset i8042.nomux i8042.nopnp i8042.noloop”


  Afterwards, hit “ctrl S” to save
  Hit Alt F2 to run a command and type:
  update-grub (type “sudo update-grub” if this doesn’t work)
  Also try this in the terminal if it doesn’t work.


When I was doing this update my grub file was a read only and wouldn't save.  I eventually just tried to close the window and it gave me the option to "save as," which I did, and saved it to whatever folder and place that popped up.  It was all pretty sketchy for me (I am a noob) but somehow it got my touch pad working:D.  It is a little sensitive at times and I every so often accidentally move my cursor because my hand must slightly graze it (at least, that is what I think is happening).



3.  To get the wireless working I used the 2nd solution on this website:


[http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/](http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/)


It directed you to do as follows:


This method involves forcing iwlagn to not use n, the commands will disable n on the device without making it a permanant change, check first if this work for you, if you notice that the speed improved then continue to make the change permanant. If this solution didn`t work for you, then reboot your computer to revert the changes.
   
  sudo rmmod -f iwlagn
  sudo modprobe iwlagn 11n_disable=1
   
  If you notice that the wifi speed improved, then make the change permanent :
   
  gksudo gedit /etc/modprobe.d/iwlagn-disable11n.conf
   
  and add this line to the file:
   
  options iwlagn 11n_disable=1
   
  save & quit


It was all kind of sketchy as well.  I got some weird looking errors.  When I opened the "/etc/modprobe.d/iwlagn-disable11n.conf" it gave me some error that it couldn't find something then just opened a blank file.  I added the line "options iwlagn 11n_disable=1" anyway and saved.  Oddly enough, it worked anyway.  My wireless runs much faster though the little LED on my f12 key still flashes blue and orange instead of just staying consistently blue.  Not really sure what that means but I am pretty sure my wireless card isn't flickering on and off quickly because no wireless error messages pop up.


4.  The first time I dealt with the screen being black issue I just though my computer crashed.  Once I hit the f3 key (screen brighten) though everything looked good.  I need to do this every time I load Ubuntu.  It's not really a big enough problem for me at the moment to pursue a solution because fixing it requires me to hit one button once.  Just be sure when you load Ubuntu to wait an extra minute until you are sure that you must be at the login screen.  I have pressed the f3 key to early and accidentally interrupt the load and caused it to crash.  You can usually tell if your black screen is active depending on whether you see the light from the HP symbol on the back of your screen leaking through (Quality!;))


All in all I wouldn't go so far to say that the HP dm4t 2000 (dm4x) is completely compatible with Ubuntu.  I haven't tried installing outside of Wubi yet and probably wouldn't risk it with the current versions of Ubuntu.  I am really hoping things go a little easier with 12.04 LTS so I can get Ubuntu running in a partition.  I may be a noob to Linux but I am really enjoying using it.  Also, I find there is no better way to learn about your computer than having to fix its glitches.  In the future, if 12.04 isn't more compatible I will probably look into a System 76 laptop.  It pretty much doesn't get more compatible than those and their customer service looks pretty awesome.


Anyways, I hope this helps!  This is my first forum post.

---

### Post by Mark Phelps on 2012-01-29
Not trying to dash your hopes -- but there is nothing in Ubuntu 12.04 that will in any way help the "already have 4 primary partitions" problem.

But, what you CAN do now as an alternative, is the following:
1) Download and install the FREE version of Macrium Reflect in Windows.
2) Use the  MR option to create and burn a Linux Boot CD
3) Use the Win7 Disk Management feature to shrink down the Win7 OS partition to make some room.
4) Reboot into Win7 a couple of times to allow the filesystem to make any needed adjustments.  when there, copy the stuff from the HP Tools partition to a folder in your Win7 OS partition.
5) Download and burn the Partition Wizard Boot CD -- and boot from it.  This will allow you to do a lot more partitioning functions than the primitive Win7 Disk Management tool provides. Us this tool to (1) remove the HP Tools partition and move the other partitions around so the free space is all at the right side of the drive picture.
6) Once done with that, reboot back into Win7 and use MR to image off the contents of the Win7 OS and any boot partition.
NOW, you have a way of restoring your Win7 setup exactly as it was when you made the backup.
NOW, you can go ahead and do a normal separate-partition dual-boot installation of Ubuntu.

---

### Post by amoxicillin on 2012-01-30
Thanks for the heads up on the Macrium software Mark!  I'll definitely check it out.

I'm not banking on 12.04 to solve the partition problem.  I am just hoping that it is a little more stable on this computer in regards to the hardware drivers, in which case I will feel more confident changing the partition structure and making the full dive in as opposed to using Wubi.  Right now my knowledge and skills are pretty rudimentary and I still feel like a lot of the fixes I've come across were executed through luck as opposed to skill (eg: I had no idea that the locations of the partitions on the drive illustration mattered.  Man!  That could have been bad had you not mentioned it to me ;) )

Fortunately, these forums are very active and this really looks to be a tight and supportive community!

---


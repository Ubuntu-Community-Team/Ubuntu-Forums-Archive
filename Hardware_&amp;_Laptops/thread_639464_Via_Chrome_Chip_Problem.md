---
title: "Via Chrome Chip Problem"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by rsteckly7 on 2007-12-13
Hi,

I am having problems installing Ubuntu on a new Stepnote 1501.  It has a VIA Chrome video chip.  When I put in the live CD, it boots up to the welcome screen.  I try installing Ubuntu or running it in safe graphics mode and all I get is a grey screen with numbers and characters swimming across it. 

I've looked at other posts that suggest I need to download a driver.  Is that true?  Also, I don't see how I can install the driver if I can't load the live CD to install Ubuntu.  If I can't install Ubuntu, how can I change the driver?

I tried installing gOS, as I figured it was a version of Ubuntu that might have the drivers since they contract with Everex.  No go.  It just said that it couldn't detect the display and asked me to pick a driver.  Even after picking Unichrome, I still got the grey characters.

Is there no hope?

Ron

---

### Post by tgalati4 on 2007-12-13
It could be a defective video chip.  Quality control of Via-based boards is not the greatest.  Suppliers will charge $12.95 to test a board before sending it out--as an option.  It's actually worth it because of the time wasted trying to get a defective board to work.

If the board is OK, then try using the Alternate CD.  It uses a text-based installer and you might get  farther along.

---

### Post by rsteckly7 on 2007-12-13
Hi,

Thanks for the thoughts.  It came with Windows Vista preinstalled--and it booted up correctly and I could work in it. I just don't want to use Vista :(.  If Vista works, its same to assume the chip is ok, right?

As for the alternate CD, this is a dumb question, but how do I get it?  I looked at the download site and couldn't find anything.

Ron

---

### Post by tgalati4 on 2007-12-13
A simple forum search on Via and openchrome:

[http://ubuntuforums.org/showthread.php?t=636368&highlight=via+openchrome](http://ubuntuforums.org/showthread.php?t=636368&highlight=via+openchrome)

For alternate disk:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Click on "Alternate CD" under the green download button.

I assume from your original post that you were not able to boot into "safe graphics" mode.  This is troublesome as you have no guarantee that your hardware will work once you do perform the Alternate Install.  

I have only used mini Via C7 boards and they ran Feisty fine.  Haven't tried Gutsy.  

Good luck.

---

### Post by rfruth on 2007-12-13
My desktop (mini tower) MSI board (VIA chrome video) works fine but I had to do the F4 (1024x768) video thing during install (no special driver) :)

---

### Post by rsteckly7 on 2007-12-13
Okay,

I managed to get the alternate install CD.  It was actually pretty obvious how to find it (duh on my part).  I've installed the OS and it loads into a command line from the hard drive, etc.  But when it goes to load into Gnome the same problem occurs.

I've downloaded and unzipped the driver from Via mentioned in the post.  However, the problem is I'm not sure how to get it on my machine.  I downloaded it from a windows machine and burned it to a disc--although it seems that Windows formated the disc so I can't get to it via command line.

I tried putting in a USB flash drive, which it recognized.  But I can't get to it either to move the files over.

As you can tell, I'm new to Ubuntu, so any suggestions would be really appreciated. 

Thanks,

Ron

---

### Post by NordicMan on 2007-12-14
Hi I've been having similar challenges getting Gutsy Gibbon to load on my Everex Stepnote NC1510.  I've tried standard install of 7.10 as well as the alternate CD version. Also tried installing Xubuntu for the heck of it.. but every time the screen would go into a panic shortly after the initial install menu :mad:

I'm still working on the problem, but have recently made a bit of headway that might help you too.. I found if I attach an external monitor to the notebook it solves the video problem, in that both the external display AND the notebook monitor both work fine, go figure!

If someone comes up with a permanent fix for this issue it would really be appreciated!

---

### Post by rsteckly7 on 2007-12-14
HI All,

So I've solved the problem.

The first step is to download the driver from the VIA website. The link is posted above in the this thread (I think).

The second step is to download the alternate install CD.  Go through the installation.

The third step is to boot up the system from the hard disk and hit esc when the GRUB loader starts.

Select the second option (generic mode, recovery).  It will boot you to a command line.

Then type startx.

The Gnome display manager should load correctly--it will give you some weird images at first, but it usually starts to work.  You should get a message saying that Ubuntu is running restricted drivers.  If it doesn't work, you need to allow restricted drivers--I'll tell you how if it doesn't work.  Note that its important you downloaded the driver beforehand--you don't have network access in recovery mode.

Once you're in the GNOME display manager, go to the directory where you downloaded the VIA driver.  Use the Terminal application because you have to be root.  Type in sudo sh ./{the really long VIA file name}.  Follow the prompts.

Restart the machine.  The normal boot process should load GNOME correctly.

Hope this helps.  Now if I can only get the fan to turn off...

Ron

---


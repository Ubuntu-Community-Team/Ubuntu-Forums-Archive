---
title: "How Am I Going To Passed This Black Login Screen"
date: 2008-09-17
forum: General Help
---

### Post by cabanagj on 2008-09-17
I installed Ubuntu in my computer which previously using Windows.
I got the disc shipped.
The installation completed.
But now it has this black login page.
How to get rid of this black login page.

How to install Ubuntu that once loaded it will go directly to the desktop not in a black screen login page.

thanks.

---

### Post by Captain Giraffe on 2008-09-17
Did you install a server version?

The desktop versions starts the desktop by default.
The server version does not.
/Captain

---

### Post by cabanagj on 2008-09-18
> **Captain Giraffe said:**
> Did you install a server version?

The desktop versions starts the desktop by default.
The server version does not.
/Captain

nope. the desktop version i installed.

---

### Post by gkestrel on 2008-09-18
sounds like x server is not configured correctly for your graphics card, have you tried booting into recovery mode when you start up your computer. You can do this by pressing the escape key to view the grub menu and then choosing the recovery mode to boot, this should give you an option to reconfigure the x server for your computer. Try that first and see if it helps you out, if not post back here for further help.

---

### Post by cabanagj on 2008-09-18
> **gkestrel said:**
> sounds like x server is not configured correctly for your graphics card, have you tried booting into recovery mode when you start up your computer. You can do this by pressing the escape key to view the grub menu and then choosing the recovery mode to boot, this should give you an option to reconfigure the x server for your computer. Try that first and see if it helps you out, if not post back here for further help.

thanks gkestrel, i will try that after i got home. im at work right now. maybe this weekend. hope i gonna fix this. im eager to use ubuntu.

---

### Post by karmickoala on 2008-09-19
I am getting something similar with Ubuntu 7.10.  It seems that every time it updates the kernel I'm no longer able to boot.  I have to change Grub's boot entries (it resets them back to the way I originally had them which are wrong).   

Once it gets to the boot screen it shows me a black screen and it will make the sound as if it's ready to login but obviously I can't see anything to log in.  I've tried recovery mode and it does the same thing. :(

I had fixed it once before, but I can't remember how I did it.

Any help would be appreciated.

Adam

---

### Post by gkestrel on 2008-09-19
karmickoala it sounds to me like you have two different problems that are causing you problems. You would really do better to open a new thread for each problem, and to give as much details as possible, so that more people can help you.

With regard to your boot problems when the kernel updates, do you by any chance have both sata and ide drives, and with regards to the black screen are you by any chance using the nvidia drivers from nvidia website. Need to know more details about your system before i could try to help you further. But i will try my best to help you out.

---

### Post by cabanagj on 2008-09-25
I re-installed 3 times, same thing still a command prompt like screen. I think it's not working good with my display card. What would you think?

---

### Post by Ryadt on 2008-09-25
Can you give some more information on the command-line screen you get.

---

### Post by gkestrel on 2008-09-25
Did you try rebooting and choosing recovery mode at boot, by pressing the escape key to see the grub menu, to see the recovery mode, and then choosing reconfiguring the x server. After that finishes just type

startx

into the command line to see if your x server has been fixed. If not post back here any error messages you get or details of the make and model of your graphics card if you know it.

---


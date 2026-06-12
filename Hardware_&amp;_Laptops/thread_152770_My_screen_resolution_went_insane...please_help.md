---
title: "My screen resolution went insane...please help"
date: 2006-03-30
forum: Hardware &amp; Laptops
---

### Post by melissathespud on 2006-03-30
I am running Ubuntu, and I am new to Linux, so be gentle with me. (aka please try to explain as simply as possible). Last night my computer randomly locked up on me (I honestly don't even remember what I was doing, web browsing of some sort...it has been running really slowly as of late anyways). I restarted with the power button, but did not even log in last night, as I was tired and frustrated and just went to bed. I came back today and logged in, and my screen resolution is now 640x480, which is just insane and unusable. I found the place to change it under system, but it is giving me only this option...as if all the other options were deleted or something. There is nothing dropping down w/ the drop down menu. Please help, I cannot live with it like this and am considering going back to Windows (which I really don't want to do) if I can't figure it out soon.

Also, I tried xrandr stuff in terminal, and it seems to be saying that my only options are what I currently have, for some reason.

---

### Post by ispmarin on 2006-03-30
Hello melissathespud, sometimes this happens with me, but just a CRTL+ALD+DEL on the funny resolution fix the problem. (CRTL+ALT+DEL is the command to kill the windows server, called X. X creates the base for Gnome or others windows managers to run. Your X will be then started again, automatically, hopefully with the right resolution). IF the problem persists, please send to us the file xorg.conf located at /etc/X11 (you can post it here, just copy and paste), so we can try to help a little more. It helps also if you say the manufacturer of your video board, and if you tried to install any driver different from the ones that came with ubuntu installation (if you did not installed any drivers, then you are using the ubuntu ones :D )
About running slow, how much ram memory do you have? Did you make a swap partition on the installation? (If the installer partitioned your disk, you have a swap partition). When you use the computer, does it access a lot the disk, even when you are not saving or reading a file?

For now, let's try those... post here the results.

---

### Post by encompass on 2006-03-30
can you tell us what Graphics card your computer uses?  If you don't know the card... perhaps the model number of your computer.  That way we can figure out what happened.  How long have you been using your ubuntu installation before this happened?

I think the guy above means control alt backspace not delete.

---

### Post by jbennett on 2006-03-30
EDIT: About 20 seconds too late. haha. I posted a repeat of what the other two posted.

---

### Post by gymsmoke on 2006-03-30
I just got my son setup on Ubuntu, and he has the same problem.
Fresh install of Ubuntu 5.10 
The video is ATI Radeon Express 200
I had to add Option "noaccel" to his xorg.conf file for X to even start.
I'm trying to help him get setup, but his email setup screen is so huge that he can't move around on the screen... ](*,) 
I'm going to try and have him ftp the file to me (he is really new to all of this, so it'll probably take a minute) ...

---


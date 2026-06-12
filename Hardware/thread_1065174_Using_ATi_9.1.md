---
title: "Using ATi 9.1"
date: 2009-02-09
forum: Hardware
---

### Post by psychobot on 2009-02-09
I've read that the newest ATi drivers fix all the problems Linux users have had with compositing and Xv so I'd like to give them a try. However, I'm not quite sure how to get them installed. I installed the current FGLRX drivers "The Ubuntu Way" so would I just need to deactivate the driver through System ---> Administration ---> Hardware Drivers and then make an install script with the downloaded drivers? In Windows it was advised to completely remove all traces of a driver before upgrading. Is it the same case with Linux? If so, how do I need to prepare the system to properly install the new drivers?

---

### Post by mtbsoft on 2009-02-09
I don't believe you need to take any such precautions since the two are essentially separate pieces of software that just happen to deal with the same functionality - the o/s takes care of disabling the FGLRX drivers.  I certainly didn't do anything special beforehand and it all works fine.

To install, simply download the new driver (currently ati-driver-installer-9-1-x86.x86_64.run) to your desktop.

Now open a terminal and type...
```
cd Desktop
sudo sh ati-driver-installer-9-1-x86.x86_64.run
```

...enter your password and the installer should self extract and run automatically - then just follow the dialog instructions.

Sorted.

---

### Post by psychobot on 2009-02-09
thank you. Is there anything post-installation I need to do like edit xorg.config file or mkinitrd? Also, should I disable the jockey service before installing the driver?

---

### Post by Yashiro on 2009-02-10
If the auto method fails.

[http://ubuntuforums.org/showthread.php?p=6709120#post6709120](http://ubuntuforums.org/showthread.php?p=6709120#post6709120)

Applies for upgrades too. No real need to un-install anything.

---

### Post by psychobot on 2009-02-10
Updating the drivers to the newest release fixes the flicker problem when viewing visualizations with Compiz running. Now my problem is that embedded videos will not embed properly. they expand outside the window and cover other parts of the screen in bits and pieces. Is there a way to fix this?

---

### Post by mtbsoft on 2009-02-10
> **psychobot said:**
> Now my problem is that embedded videos will not embed properly. they expand outside the window and cover other parts of the screen in bits and pieces. Is there a way to fix this?

I haven't experienced that problem myself since going to 9.1 though I did have something similar before the upgrade - using dvd::rip when it fired off mplayer, the movie would come up as an undecorated window (no borders or border icons) of a default size, but that's cured now.  

It could be something to do with the media player you are using, you might want to check the settings there - something might jump out as the obvious thing to adjust.  Either that or try installing another player, set it to default in the media preferences and see if it changes the behaviour, best I can offer I'm afraid.

---

### Post by psychobot on 2009-02-10
I've installed VLC and MPlayer. VLC doesn't play well in X11 output mode. In default the video doesn't stay in it's borders. With MPlayer the video plays fine until I go fullscreen or maximize the window. Fullscreen and max window causes the computer to lock up and my only option is to hard reset the computer. 

No matter what driver I use, I cannot get DVD playback to function properly. The newest FGLRX driver fixed flicker problems but I need to disable Xv to get embedded video to stay in it's borders. Every other driver forced me to disable Xv to get the flickering fixed but I still wasn't able to play videos because the video play as if it were in slow mode, maybe 1-2 frames every couple of secs. 

Is there something with my xorg.config I'm missing? Any help with this is greatly appreciated.

---

### Post by mtbsoft on 2009-02-11
Sorry mate, you've taken my knowledge of this area to its limit, I can't think of anything else you can do.  Hopefully someone else will be able to suggest something.

---


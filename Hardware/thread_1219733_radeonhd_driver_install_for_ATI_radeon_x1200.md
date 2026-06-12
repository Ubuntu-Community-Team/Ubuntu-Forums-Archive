---
title: "radeonhd driver install for ATI radeon x1200"
date: 2009-07-22
forum: Hardware
---

### Post by aj_the_first on 2009-07-22
I have a two year old toshiba a215 (amd-64)with the ATI x1200 vid card, and I recently installed Jaunty 9.04.
The default Jaunty vid driver creates a serious screen flicker problem, so I have been trying different drivers and bug fixes and none of them quite do what I want (skype and streaming video and without screen flicker), and I wanted to try the radeonhd driver, but I just wanted to check on one thing:
 
Do the unofficial prebuilt .deb package files at the bottom of this guide do the same thing that the guide tells you to do, or do you also need to do all the steps in the guide?:
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
 
Also, I would like to turn this thread into a search for a solution to my video driver issues as I have seen a number of people with similar cards and similar problems looking for the same solution, and so far the answer semes to be back date to Intrepid or Hardy so you can use the 9.3 proprietary driver from ATI.

---

### Post by masux594 on 2009-07-22
Personally i use the same guide, step by step, not with the ".deb" file.. So, i would suggest to u to follow the "step-by-step" part.. Anyway, try with deb[only that, not the sbs].. Otherwise, follow the other.. 

Sysc, A

---

### Post by aj_the_first on 2009-07-22
Okay, so the radeonhd 1.2.5 .deb package files installed correctly with no errors, but it seems that it has not changed the screen flicker at all.
In this thread: reply #22, the reported and fixed bug modification to the xorg file  worked very well for me, in that it eliminated screen flicker, but it also took away my webcam abilities in skype and cheese.
[http://ubuntuforums.org/showthread.php?t=1174943&page=3](http://ubuntuforums.org/showthread.php?t=1174943&page=3)
I may try it again, and then just start troubleshooting the webcam, but there are already so many other problems with jaunty that I may just abandon it.
Any other suggestions?

---

### Post by giantoz on 2009-07-27
you can try this: [http://onlyubuntu.blogspot.com/2009/05/howto-enable-ati-unsupported-cards-in.html](http://onlyubuntu.blogspot.com/2009/05/howto-enable-ati-unsupported-cards-in.html)

---

### Post by nightmicu on 2009-07-30
> **giantoz said:**
> you can try this: [http://onlyubuntu.blogspot.com/2009/05/howto-enable-ati-unsupported-cards-in.html](http://onlyubuntu.blogspot.com/2009/05/howto-enable-ati-unsupported-cards-in.html)

Going to try this tomorrow but I just have this sinking feeling it won't work.. running 8.10 now and, although it's not as nice as 9.04, no flickering (in the standard GUI, anyway).

Has anyone tried this? AJ_THE_FIRST? Let me know how it went if so

Thanks

Ben

---

### Post by giantoz on 2009-07-30
let me know how it turns out.  I haven't tried it myself but I am in the same boat.

---

### Post by aj_the_first on 2009-07-31
> **giantoz said:**
> let me know how it turns out. I haven't tried it myself but I am in the same boat.
 
I did an install of the fglrx proprietary driver from ubuntu x, it apparently was an experimental compatibility package, but it totally broke the system, and I wasn't able to boot. I dropped to CLI in recovery mode, cleaned it, and re-installed radeonhd driver (not the default ati)
Then I cured the screen flicker entirely by opening the xorg.conf file and under display add these lines:
 
Driver  "radeonhd"
Option AccelMethod "XAA"
 
I also completely uninstalled/cleaned the default ati driver.  With the radeonhd driver it is EXA by default, but XAA cured all flickering, There was still a touch if you tried to run all the most difficult compiz effects, but if you can handle not having wobbly windows and beaming your windows up when you close them and no desktop cube (can't anyway because there is no 3D support in radeonhd driver yet), then it works just fine.
 
This wasn't good enough for me, because I eventually wanted to start playing Cube and Quake-engined games, so I just dropped back to Hardy.
 
But changing the accelleration method to XAA worked for the screen flicker, and as soon as the open source driver has 3D support, I will come back to Jaunty...
because I am having a hell of a time with Hardy trying to get it to recognize all my other devices. (gamepad controller, webcam, wireless card, sound issues) except for the screen flicker, EVERYTHING in Jaunty worked right out of the box.

---

### Post by aj_the_first on 2009-07-31
oh, I think "AccelMethod" was in quotes as well.
so, does anyone have a suggestion for my new issue? :) [http://ubuntuforums.org/showthread.php?t=1227502](http://ubuntuforums.org/showthread.php?t=1227502) 
I've got most everything else sorted in Hardy, but this freakin webcam is killing me.

---

### Post by paintedrealms on 2009-08-02
> **aj_the_first said:**
> oh, I think "AccelMethod" was in quotes as well.
so, does anyone have a suggestion for my new issue? :) [http://ubuntuforums.org/showthread.php?t=1227502](http://ubuntuforums.org/showthread.php?t=1227502) 
I've got most everything else sorted in Hardy, but this freakin webcam is killing me.
i would try to uninstall/reinstall webcam

```
sudo apt-get remove webcam
sudo apt-get install webcam
```

---

### Post by paintedrealms on 2009-08-02
I think I solved the problem.  I use Jaunty edition or aka 9.04. My computer is a Dell Inspiron 1721 which uses the ATI Radeon x1270. I have moved this posting to a new posting of its own to avaoid redundant information postings.  The below link has your solution.

[http://ubuntuforums.org/showthread.php?p=7730406#post7730406]("http://ubuntuforums.org/showthread.php?p=7730406#post7730406")

---

### Post by lems on 2009-08-03
> **aj_the_first said:**
> I have a two year old toshiba a215 (amd-64)with the ATI x1200 vid card, and I recently installed Jaunty 9.04.
The default Jaunty vid driver creates a serious screen flicker problem, so I have been trying different drivers and bug fixes and none of them quite do what I want (skype and streaming video and without screen flicker), and I wanted to try the radeonhd driver, but I just wanted to check on one thing:
 
Do the unofficial prebuilt .deb package files at the bottom of this guide do the same thing that the guide tells you to do, or do you also need to do all the steps in the guide?:
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
 
Also, I would like to turn this thread into a search for a solution to my video driver issues as I have seen a number of people with similar cards and similar problems looking for the same solution, and so far the answer semes to be back date to Intrepid or Hardy so you can use the 9.3 proprietary driver from ATI.


I probably have the same exact computer as you(toshiba a215-4747 i think...). I tried paintedrealms' fix and it worked PERFECTLY(fingers crossed). Everything is very nice now. The graphics with this fix is even better than when I tried ubuntu last year.

---


---
title: "intuos3 - wacomcpl not working"
date: 2009-08-01
forum: Hardware
---

### Post by capraMambrica on 2009-08-01
Okay, I'm really at my wits end.

I know the answer must be in here somewhere, but I can't find it. But first the question:


[LIST]
[*]**How do I switch my 'middle' and 'right' mouse buttons around on my intuos 3, when the 'wacomcpl' doesn't seem to work?**
[/LIST]
 
Simple aye ;) My wacom seems to work perfectly, I just am used to the buttons around the other way.

Some background: Using Ubuntu 9.04, with the latest updates to kernals and stuff this morning. It's a USB wacom, using on an old machine, pentuim 3 something. Nothing flash, but I think shouldn't have problems changing wacom settings. I believe the wacom is plugged into some kind of USB hub, in a PCI slot, meaning it's not plugged directly into the motherboard. Don't know if that makes a difference.

Also, a point of interest I should point out, the operator - me - is an idiot. I only know enough to get by, and I struggle doing all these things people tell me to, as I don't fully understand what is going on, or why.

So what have I tried?
I went here:
[http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)
And tried creating and updating .fbi files. This didn't seem to help.

I went here:
[http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)
Got the 0.8.4 drivers, and tried to install them. Added that stuff to my xorg file. This buggered my wacom all together. I then had to go into the synaptic manager and uninstall the default drivers, and the wacom worked, in a way. It would do odd things like switch from absolute to relative, when the 'left' click was activated. And wouldn't return to absolute until I moved the mouse. Also wacomcpl didn't work.

A friend told me to make a file called .xinitrc, and run >~sh /.xinitrc
This doesn't work, but it does play my ubuntu opening music and make the xserver flash around a bit. It also dumps a whole lot of stuff in the terminal like:
> Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'stylus'
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'stylus'I can also run >xinput --list , and get info I interpert saying my "Wacom Intuos3 6x8" is working as expected, or at least reconised.

------------------
So, here I am, everything works, except for the wacomcpl, but I have tried a bunch of things I don't fully understand, and have altered files all over the place.

[LIST]
[*]I have reinstalled the drivers from the synaptic manager.
[*]My xorg file has the changes from the linuxwacom site.
[*]I have the 10-wacom.fdi file from post #176 of above thread.
[*]I have an .xinitrc file in my home dir.
[/LIST]
All I want to do is change the order of those two buttons:(
Thanks you for reading this post!

---

### Post by Favux on 2009-08-01
Hi capraMambrica,

Welcome to Ubuntu forums!

As you've noticed you can't mix versions of linuxwacom or bad things can happen.

Since you have an Intuos3 the default 0.8.2-2 linuxwacom in Jaunty should work for you.  But do note that isn't a standard 0.8.2-2 linuxwacom.  It was specially patched to support Xserver 1.6 and HAL.

Do you want to go back to that or try to get 0.8.3-4 to work?  We should be able to get it working with xorg.conf if it is correctly installed.  How did you do it by the way?  Maybe with the a .fdi too.

---

### Post by capraMambrica on 2009-08-01
Thank you for your welcome!

I went back to the 0.8.2.2 that is in the synaptic manger. I can't say exactly how I did it, and it's possible that I just didn't install 0.8.4 properly. But I did mark the original for installation, and then mark it again later for installation, in the manager.

I was interested in what the linuxwacom site was saying about installing it for my kernal. I have jsut been going through the processes you have laid out for table PCs in this thread:
[http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

But I'm back at the same spot I was earlier now, with the odd 'absolute' and relative mode switching.

As for the xorg.conf, I added the lines from:
[http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)
But I removed the lines that were for Serial or Tablet PC. Also, I only saved the file. does it need 'made' or something? I'm not sure I have followed those instructions all the way through. I didn't add the serverLayout. I'm doing that now.

---

### Post by Favux on 2009-08-01
Hi capraMambrica,

Hold off on "ServerLayout" for now.  First we need to nail down the 0.8.4 stuff.  Did you download 0.8.4 from LWP and compile it and do the make install?  Do you have an unpacked tar of 0.8.4 somewhere?

---

### Post by capraMambrica on 2009-08-01
Yep, I have an unpacked tar on my desktop. 
I don't mind using the older drivers, by the way. If I can just change the buttons around.

---

### Post by capraMambrica on 2009-08-01
HUmm, I screwed something up adding the "ServerLayout" thing, and now my xorg thing has gone back to it's original status. With no mention of the wacom. Should I add the lines pre "ServerLayout" back in? I did this before I saw your reply :)

---

### Post by capraMambrica on 2009-08-01
And to further answer your question, I downloaded 0.8.4 from LWP. I followed the README which told me:

    $ bunzip2 linuxwacom.tar.bz2
    $ tar xvf linuxwacom.tar
    $ cd linuxwacom/prebuilt
    $ su
    # yum remove linuxwacom
    # ./uninstall
    # ./install
    # reboot

Obviously Yum is for Fedora or something, and I didn't know how to do it un Ubuntu, so I removed the wacom files with the synaptic manager. 

The second time around I followed your tablet PC post, and did a compile and 'make install'.

---

### Post by Favux on 2009-08-01
Hi capraMambrica,

OK, I think you also said you reinstalled the Jaunty default 0.8.2-2 linuxwacom in Synaptic.  If so go back in Synaptic and right click and tell it to do a complete uninstall.  There are two packages xserver-xorg-input-wacom (the drivers) and wacom-tools.  I think your original problem is you didn't have wacom-tools installed (it isn't by default) and it has wacomcpl.

Then go to Appendix 4 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  and uninstall 0.8.4.  I don't think you need to worry about the wacom.ko part.  Reboot.

Then go back to Synaptic and install both packages.  It would also be a good idea to comment out "#" all Wacom entries in xorg.conf and the entire "ServerLayout" if you did put it in.  Reboot.

---

### Post by capraMambrica on 2009-08-01
Okay, I did certainly have both the tools and input driver. I installed anything that came up with a search of 'wacom' :)

So i have now followed through with the unistallation of 8.2.4, and my xorg.conf file is back to it's clean state of having no mention of wacom or teh server thing.

My wacom is working perfectly, except wacomcpl dosen't display may tabet settings.

---

### Post by capraMambrica on 2009-08-01
I meant I had removed 0.8.4, not 8.2.4. It's probably obvious. I can't find the edit post button...

---

### Post by Favux on 2009-08-01
Hi capraMambrica,

Edit is on the lower right corner.

OK, probably you knocked out the new modified 10-wacom.fdi with the reinstalls.  Check with Places (Nautilus).  If it's missing reinstall it following the instructions in post #176 on the link you already have.  Reboot.  You know you have it when in a terminal:
```
xsetwacom list
```
returns linuxwacom names like stylus, eraser, etc. instead of being blank.  Now wacomcpl should work.  Follow Section 3 in the same HOW TO that has Appendix 4 to set up wacomcpl for Jaunty.  You won't need any wacom entries in xorg.conf.

---

### Post by capraMambrica on 2009-08-01
Thank you so much!
I did have to fix the .fdi file, and once I rebooted that list showed the right things, and wacomcpl picked up all my settings!

I like in the appendix 3, you show how o get it to set them permanently. My work hasn't even managed to do this, on a very customised Fedora 3.

Anyway, I guess my problem was simply trying to many different things. 
I'm now running 0.8.2-2 from the synaptic manager, Ubuntu recommended I believe, and the .fbi file. Eveything seems to be working perfectly!

Thank you so much for you help and patience Favux!

---

### Post by Favux on 2009-08-01
Hi capraMambrica,

Outstanding!  You're welcome.  Sounds like it's set up and everything is good to go.

---


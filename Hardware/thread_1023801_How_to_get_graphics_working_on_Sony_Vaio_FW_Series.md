---
title: "How to get graphics working on Sony Vaio FW Series notebooks"
date: 2008-12-28
forum: Hardware
---

### Post by igknighted on 2008-12-28
**[COLOR="Red"]THE LATEST UPDATE FIXES THIS BUG... NO NEED TO USE THE HACK DESCRIBED BELOW[/COLOR]**




This is only for those with the intel x4500 GM45 graphics chip.  By now, you have probably realized that whenever the intel driver is used, you get a spotty white screen that fades to black while the login noise plays in the background.  What is happening is that X has loaded fine, but it fails to turn on the laptop screen. If you try loading it with an external monitor plugged in, it will work perfectly.

Of course, we can't always carry around an external monitor with our laptops.  There are people working on finding a permanent solution right now, here are the bug reports.

Ubuntu: [https://bugs.launchpad.net/xorg-server/+bug/268615](https://bugs.launchpad.net/xorg-server/+bug/268615)
Xorg: [https://bugs.freedesktop.org/show_bug.cgi?id=17292](https://bugs.freedesktop.org/show_bug.cgi?id=17292)

Now, all is not lost.  There is a workaround that has been found.  It involves rebuilding the driver with a temporary fix.  You can either recompile the driver yourself, or someone was kind enough to build the drivers into a .deb package in the Ubuntu bug report (I've attached them to this thread too).  Assuming that you have already installed the system (if you haven't, just choose safe graphics mode when you boot the live CD and it will boot normally and should work fine), this is what you should do to install:

First, remove completely the current version (gets rid of all related files)
```
sudo apt-get remove --purge xserver-xorg-video-intel
```

Then go ahead and double click the .deb to install.  It will warn you that there is the same version available from a software channel (repo), ignore this.

Once that is done, open a terminal and type:
```
sudo nano /etc/X11/xorg.conf
```

You will see a section "Device", and under it a line that says "Driver" "vesa".  Change "vesa" to "intel".  Then reboot (or log out/in).

You should be all set now with native graphics.  One caveat, until you see in a bug report that a better fix has been sent out as an update, do not let Ubuntu update that package (if a newer version comes out, it will try).  Always look at what you are installing before you click OK.  If you accidentally update it, just repeat the steps here from the beginning and you should be fixed.  If you have any issues with this, feel free to post here for help.

---

### Post by aeid79 on 2008-12-28
million thanks , worked like a charm!

---

### Post by gtg694t on 2008-12-29
Finally! I've been trying for days to get various distributions to work on my Sony Vaio FW170J.

This worked wonderfully. 

Thanks much,
Chris

---

### Post by madHatterCutsTheChatter on 2009-01-03
thanks!! 

linux finally works after an entire month of woes!!

---

### Post by danielfernando on 2009-01-05
uhuuuu....

Thanks a lot..working perfectly..

Cheers
Daniel

---

### Post by Skylined on 2009-01-06
Thanks a lot, it's finally working! :D

Is there any way to remove Update Manager's notice about the "new Intel driver"?

---

### Post by igknighted on 2009-01-06
> **Skylined said:**
> Thanks a lot, it's finally working! :D

Is there any way to remove Update Manager's notice about the "new Intel driver"?

I'm trying to figure that out.  Their should be, but I don't know what it is.  When I figure it out I'll add it to the original post.

---

### Post by Skylined on 2009-01-08
Again, thanks for you work. :)

---

### Post by chex_m8 on 2009-01-09
Thanks, this also worked on my sony vaio SR290 with mobile 4 series chipset.

---

### Post by igknighted on 2009-01-09
> **chex_m8 said:**
> Thanks, this also worked on my sony vaio SR290 with mobile 4 series chipset.

Yeah, the SR series is the international (non-us) version.  At least some of them.  Sony has some really odd methods of identifying their products...

---

### Post by niceguy123 on 2009-01-10
I'm running Ubuntu 8.10 on my new Sony Vaio VGN-FW250J

The computer's screen resolution is 1600X900 ratio 16:9. How can I configure Ubuntu to work with that. The current configuration is  800X600 4:3 so every thing is stretched out un-proportional.

---

### Post by chex_m8 on 2009-01-10
System > Preferences > Screen Resolution
should be able to change it there

---

### Post by igknighted on 2009-01-11
> **niceguy123 said:**
> I'm running Ubuntu 8.10 on my new Sony Vaio VGN-FW250J

The computer's screen resolution is 1600X900 ratio 16:9. How can I configure Ubuntu to work with that. The current configuration is  800X600 4:3 so every thing is stretched out un-proportional.

If you are getting 800x600, you are almost certainly in "safe graphics mode", and this is the best you can do with that driver.  As soon as you get the proper driver installed (as detailed above), it should automatically reconfigure to 1600x900.

Oh... does your computer use the integrated intel graphics chip?  Not all FW laptops do.  If you use Nvidia or ATI, you should start a different thread.  This thread is only about specific issues on the intel chip laptops.

---

### Post by crazyprogrammer on 2009-01-11
Thank you very much BRO. I looked for it for about 6 months.

---

### Post by igknighted on 2009-01-25
The latest updates fix this bug.  No more need to use the above hack.  Good job Xorg dev team!

---

### Post by harithgeorge on 2009-01-26
I just installed ubuntu 8.10 on my sony viao vgn-fw235j yesterday..
First I got the default i386 iso. But the graphics didnt come up in the installation.  So I downloaded the alternate installer and installed ubuntu using that (I didnt realise that there was a safe graphics mode in the first one). Anyway even then graphics did not come up. 
It was then I saw this post and since igknighted had suggested that the update has it, I just did apt-get remove and then reinstall xserver-xorg-video-intel. And then there was light :)

My point is that though the update has it, the install iso images still do not have it. So ppl who do a fresh install will still not get graphics up on install.
You have to follow the following two steps from the shell
1. sudo apt-get remove --purge xserver-xorg-video-intel
2. sudo apt-get install xserver-xorg-video-intel

Hope this was helpful.

---

### Post by igknighted on 2009-01-26
harithgeorge: if you had selected "safe graphics mode" at the boot screen of the desktop CD (in the f4 "modes" menu) it would boot fine, albeit at a lower resolution.  Also, there is no reason to remove/purge the old one, as the update will simply replace it when it installs.  You can just install the updates, reboot, and be on your way.

EDIT: You might have to reconfigure the xserver... can anyone confirm?

---

### Post by zanjielee on 2009-02-02
Yes, the latest update fixes this bug, but you still need to edit /etc/X11/xorg.conf

Change vesa to intel then reboot or log out/in

:D

---

### Post by volekvolek on 2009-02-04
Does the new fix work for Sony Viao  FW140E  ?     
I had read in another thread the patch was not working for this model.  
Unfortuanly I have some deadlines and can't test the fix on mine right now. I will try it this weekend, when I don't need my laptop.

---

### Post by igknighted on 2009-02-04
> **volekvolek said:**
> Does the new fix work for Sony Viao  FW140E  ?     
I had read in another thread the patch was not working for this model.  
Unfortuanly I have some deadlines and can't test the fix on mine right now. I will try it this weekend, when I don't need my laptop.

Works perfectly, I'm posting from it right now.

---

### Post by volekvolek on 2009-02-05
Confirming, 1600x900 resolution works on Sony Viao VGN FW140E with the latest Ubuntu 8.1 update and change to the xorg.conf of 

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection


Kudos to folks who tracked this issue and resolved it.

---

### Post by nm1007 on 2009-02-23
hey quick question im new to using a terminal in ubuntu, when you get to editing the /etc/x11/xorg.cong file, how do you change the drivers from vesa to intel? what exactly do you type in plz help cuz im stuck at the 800X600 resolution and its relly annoying. thanx so much to whoever can help me, and by the way my model is the vaio vgn-fw235j if that helps

---

### Post by Starl1n on 2009-04-19
Delete this please!

---

### Post by Starl1n on 2009-04-20
First:

Dude!! finaly!! working on linux, like the old times!!, thanks a lot, i was trying to make it in opensuse but i just can't and here i get the answers faster!!!!!! 

> **nm1007 said:**
> hey quick question im new to using a terminal in ubuntu, when you get to editing the /etc/x11/xorg.cong file, how do you change the drivers from vesa to intel? what exactly do you type in plz help cuz im stuck at the 800X600 resolution and its relly annoying. thanx so much to whoever can help me, and by the way my model is the vaio vgn-fw235j if that helps

i don't know too much about this but type in a console **sudo gedit /etc/X11/xorg.config** should work fine for you, it will open the graphical interface of gedit

---

### Post by Starl1n on 2009-04-21
> **igknighted said:**
> Works perfectly, I'm posting from it right now.

Hi me again,igknighted (you're the one from opensuse forums! XD), i try by updating and putting the intel instead vesa in xorg.conf, but i don't work, it appears the same white screeen, but with the version of the driver that is attached here work perfectly, did you do something else after making the update?


Someone please edit those two post of mine!

---

### Post by niceguy123 on 2009-06-24
> **igknighted said:**
> [B]
Then go ahead and double click the .deb to install.  It will warn you that there is the same version available from a software channel (repo), ignore this.


Did that and got this message:

```
/tmp/xserver-xorg-video-intel_2.4.1-1ubuntu10_amd64-1.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.
```

What should I do.

---

### Post by decoroth on 2009-06-27
I've got a problem and I seem to be the olny one. when I try to install the .deb file it tell's me this error:
"Error: Dependency is not satisfiable: libpciaccess0"

Can anyone tell me what the hell is "not satisfiable"?

Thanks

PS.: I'm New to linux, but I know my way 'round the terminal, and google, of course.

---

### Post by saik on 2009-11-28
I recently updated my Ubuntu installation to 9.10 on vaio Fw140e laptop. After reboot xserver doesn't seem to work.  I followed the steps mentioned in the beginning of this thread but still couldn't fix it. I got following errors:

1)When I tried to purge the intel package (xorg-video-intel) and  got an error there is no such package.Previously i used to work with "vesa".
2)When i tried to install xserver-xorg-video-intel_2.4.1-1ubuntu10_amd64.deb,i got an error that it conflicts with  xserver-xorg-4 in xserver-xorg-core package, i did a force installation and it went through.
3)On reboot my graphics didn't work, i checked xorg.0 log file(/var/log/xorg.0.log) and there was an error
(EE)"module ABI major version (4) doesn't match the server's version(5) "
(II)UnloadModule: "intel".

I reveted back to "vesa" option in xorg.conf work,but even that doesn't seem to work.

Any hints what's wrong?
I have attached xorg.0.log file for refernce

---

### Post by saik on 2009-11-28
Sorry,i forgot to attach log file.

---

### Post by igknighted on 2009-11-28
> **saik said:**
> I recently updated my Ubuntu installation to 9.10 on vaio Fw140e laptop. After reboot xserver doesn't seem to work.  I followed the steps mentioned in the beginning of this thread but still couldn't fix it. I got following errors:

1)When I tried to purge the intel package (xorg-video-intel) and  got an error there is no such package.Previously i used to work with "vesa".
2)When i tried to install xserver-xorg-video-intel_2.4.1-1ubuntu10_amd64.deb,i got an error that it conflicts with  xserver-xorg-4 in xserver-xorg-core package, i did a force installation and it went through.
3)On reboot my graphics didn't work, i checked xorg.0 log file(/var/log/xorg.0.log) and there was an error
(EE)"module ABI major version (4) doesn't match the server's version(5) "
(II)UnloadModule: "intel".

I reveted back to "vesa" option in xorg.conf work,but even that doesn't seem to work.

Any hints what's wrong?
I have attached xorg.0.log file for refernce

The package you installed is for an old version of Ubuntu (as is all the information in this thread).  You should no longer have to do anything special to get the graphics on that laptop working, it should be fine out of the box.  By forcing the old driver into the new xorg, who know what may have been messed up.  If you really want to save this system, remove the latest package you installed, then try reinstalling all of Xorg.  I think a safer bet would be to start over from scratch.  FWIW, in the future, with something like Xorg and graphics drivers that change drastically in 6 months, it is rarely OK to use packages from old versions.

---

### Post by sebanezu on 2010-03-05
Hello there! I have a question: does this will work too on a fujitsu siemens laptop with intel gma 4500 card? Thanks you!

---

### Post by 007casper on 2010-09-01
>>post #15
>>The latest updates fix this bug. No more need to use the above hack. >>Good job Xorg dev team!

is there a solution for resolution settings?  I got this lonely threat where the monitor resolution is way lower than it should be... I am so anxious to fix it.  Any advice will be appreciate it.  
[http://ubuntuforums.org/showthread.php?t=1457530&highlight=Intel+GMA+4500](http://ubuntuforums.org/showthread.php?t=1457530&highlight=Intel+GMA+4500)

I have a 30" apple cinema display. The monitor handles up to 2560 x 1600 pixels which is the optimum resolution for this monitor. I found out that most apple monitors have nvidia graphic card.
 
The monitor is hooked up to a motherboard Intel BOXDG45FC. This motherboard has Onboard Video Chipset Intel GMA 4500. However, using KDE interface I dont get beyond 1280x800 resolution for the monitor.

How can I get the maximum resolution for the monitor?

Thank you.

by the way, 10.4 didnt have xorg.conf

Please, advise.

---


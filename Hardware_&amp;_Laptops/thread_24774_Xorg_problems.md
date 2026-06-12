---
title: "Xorg problems:"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by SeaClearly2005 on 2005-04-08
To start off I'm brand new to Ubuntu and Linux in general but I'm not exactly a newb with Linux.  I'm using a Dell Deminsion 2400 desktop that uses built-in i845g graphics which xorg would use i810 drivers.  My monitor is a Dell E173FP LCD monitor.  I'm using the newest version of Hoary 5.04 which was released on 4-8-05 which is today.

Now right after installing it boots up with a resolution of 640x480 @ 59hz and I can't change it at all.  So I sudo dpkg-reconfigure xserver-xorg and selected everything as default and I used the advanced option to enter in my monitors refresh rates which I got from the Dell spec sheets.  One I do this and restart X my monitor displays the message in quotes "Cannot Display Video Mode".  Now I can get a 1280x1024 @ 75hz which is what I want by first pressing CTRL-ALT-F2 which brings up a Ubuntu text based login prompt and if I press CTRL-ALT-F7 it will load up gnone and everything on its own with what I want.

I know I'm going long but how would I go about getting this resolution to work on its own at bootup instead of always having to press those two sequences because my monitor and ubuntu can work correctly using xorg because I'm doing it right now.

I attached a txt file of my xorg.conf file since that might help others help me.

---

### Post by nad on 2005-04-08
It seems that X is not autodetecting something (graphics memory?). Please see the README.i810 on your computer. This will give you suggestions to tweak your xorg.conf settings.

If you would post your /var/log/Xorg.0.log (from your last login only please) there may be additional information in it.

Dan M

---

### Post by bkm708 on 2005-04-08
I am having the same problem with the same video card i845 (i810) using a Dell Dimension 2400.

---

### Post by segrewb on 2005-04-08
Look at this thread [here](http://www.ubuntuforums.org/showthread.php?t=5318&highlight=boot+video+resolution) .  Hope it helps.

---

### Post by stoneguy on 2005-04-08
Does any of this apply to using the Live versions? An HP Pavilion 300n I've tested on also uses the 82845 chipset.  The Samsung SyncMaster 750s it's connected to is registering as Generic Monitor. The system is coming up locked to 640x480 60Hz.

Does the *sudo dpkg-reconfigure xserver-xorg* work on a live CD? And is there a boot line fix to get around this? Or other way to persist a fix?

---

### Post by nad on 2005-04-09
The post previous to yours referenced the vga=xxx boot parameter. As you boot the live CD, press the F1 key for a menu of boot options and help. Then, supply the parameter on the boot line. This may very well do it. Please post back with your results.

Good luck

Dan M

---

### Post by stoneguy on 2005-04-09
Nope. Using a vga= value changed screen resolution during boot only. Once I got to the desktop, I was still at 640x480@60Hz.

I'm attaching the Xorg log file so perhaps someone can progress this further.

---

### Post by Napper on 2005-04-09
I am facing the same problems with the i810 driver on my IBM ThinkCenter. I had mentioned this problem before while 5.04 was still in Beta but did not receive any replies, so I went back to Mandrake for the time being. Installed the official release of Hoary today after it was anounced to find that the bug was still lingering around. Is this an X.org problem or an ubuntu problem? Can we hope that it will fix itself some day? I tried fiddeling around with my configuration files for, like two weeks during the Beta phase but couldn't achieve satisfying results (resolution would eventually be up at 1280 x 1028 but at refresh rates that made it impossible to play any video file without going mad) What a shame. I was really looking forward to this release... :(

---

### Post by nad on 2005-04-09
There is an awful lot going on in that posted Xorg.0.log file. It seems that some auto configured display modes are detected as not valid at start up. Then there is a page table error. Please confirm that the agpgart module is loaded and that your display agp is bound to it (lsmod | grep agp). I would also clean up the xorg.conf file to get rid of any display modes that you are not going to use.

Dan M

---

### Post by stoneguy on 2005-04-09
output of
[INDENT]lsmod | grep agp[/INDENT] 
is
[INDENT]intel_agp   20636  1
agpgart  31784  3 drm,intel_agp[/INDENT]
Don't forget that this is the Live CD - cleaning up xorg.conf is not a useful solution.

Now, I don't know anything about Xorg, but there's all those *mode clock exceeds DDC maximum* lines for every resolution except 640x480. Is it likely that my problem is a **monitor** recognition problem rather than **vidchip**?

I tried doing ctl-alt-bksp to shut down X so I could maybe tinker with xorg.conf. Didn't work on 2 regards. 1st of all, X kept on coming back. 2nd, there 4 copies of the gdm screen until the logon finished. Is there a telinit value that does the job?

---

### Post by nad on 2005-04-09
This seems to be a combination of problems. Running from the live cd though you do not have the option of not loading the ddc module, not loading edid info and forcing a specific resolution and timing. Of course you could recompile the cd.

From a root terminal you can switch to single user mode with 'init 1'. There is also a boot option to not load the framebuffer. Have you tried this?

I assume that this whole exercise is to determine if your computer is completely compatible with this distro. So we are back to having to jump through hoops to get your display correct.
Not that I mind of course. You are doing all the work. I'm happy to oblige.

Regards,

Dan M

---

### Post by stoneguy on 2005-04-09
> I assume that this whole exercise is to determine if your computer is completely compatible with this distro.
Yes and no. It's not going to get Linux no matter what. This particular system is Sweetie@home, and doesn't get ANYTHING that's not what's on her work machine. I thought I'd just give it a whack with Live to create a success/failure datapoint for the development team. As far as I'm concerned, the matter can be closed. But if there's some more testing that could be usefully done with a Live CD I'm happy to oblige - PM me here. (Note: building my own live CD is outside both personal and system capacities.)

My own 2 machines (Dell Opteron GX1, partsbox special built around Olivetti mobo) have no vid problems whatsoever.

73

---

### Post by nad on 2005-04-09
[QUOTE=stoneguy]It's not going to get Linux no matter what. This particular system is Sweetie@home, and doesn't get ANYTHING that's not what's on her work machine.
73[/QUOTE]
 
ROTFLMAO

Actually, there is one more thing to try. What happens when you CTRL + ALT + (number pad) + ?

Dan M

---

### Post by wayne1932 on 2005-04-09
I have reported this to bugzilla.    The default color depth after installation is 24 bit.  My test machine is low end video with only 2 meg of memory.   My monitor is good for 1024x768, but with a color depth of 24 when Xorg starts I get a terribly distorted screen.   I can't even read anything on the screen 

I fixed this by changing the Xorg.conf file to default color depth to 16 bits.  this is apparently a problem for both gnome and kde.   I had tried both with similar problems.

I had tried ubuntu a few months ago and scrapped it because I never could get it to start correctly in GUI.

---

### Post by scott on 2005-04-09
I also had to change my color depth to 16 as have only a 2mb graphics card. Before changing the default depth to 16 I could only get max res of 800x600 @ 24 bit.

My desktop is working fine at 1024x768, 16bit, 75Hz but when I boot up the login screen has a refreash of 85Hz which is a bit of a mess. 

How do I get them both to be the same?

Thanks
Scott

---

### Post by nad on 2005-04-09
Edit your /etc/X11/xorg.conf file to include only the display resolutions that you wish to use. The first resolution listed in the "Screen" section of this file at the default color depth is the display used by the gdm login. You can just delete the lines refering to the color depths and resolutions that you will never use. Just make sure that the _outline_ of the file stays the same (ie: you have a EndSection for every SubSection "Display").

Your safest bet is always to copy the file first, then edit the copy. If you screw up, you may have to startup in recovery mode and copy back.

Dan M

---

### Post by nad on 2005-04-09
Message to the moderator and others:

This thread began as a discussion of Xorg problems with the LiveCD. The post previous to my last answer referenced the resolution of the login screen after an install. The previous two posts should probably be moved to a new thread.

Dan M

---

### Post by bkm708 on 2005-04-10
First, you did not start the thread.  Second, there is no mention of "Live CD" anywhere in the first few posts.  The first post referenced the 5.04 release.

---

### Post by Miguel on 2005-04-14
Just for the record, I have similar display problems... on only one of the systems I have tried. 

It has an integrated Intel vid card which uses the i810 module, but the monitor is a LG Flatron 775FT. Should I understand, then, that i810+Xorg = troubles? Because, even if I can eventually get the resolution I want, the screen behaves funny to say the least.

Has anyone solved this? How?

BTW: sudo dpkg-reconfigure xserver-xorg *does* work on the live CD.

---

### Post by bondi on 2005-04-14
Hello,

I have just installed Hoary, everything seems to work but then when I get to the login screen (it does not even come up - I just hear the sound) there is just a blank screen. If I press Ctl.Alt.F2 I can get to the prompt. How do I correct this problem. I have a cel 1.7 with nvidia MX440 - It will be something with the xorg or gnome because warty worked fine. If somebody knows how to solve this I would appreciate the help. 

bondi

---

### Post by nad on 2005-04-15
For those of you using the i810 intel driver, there is a good new HOWTO at:

[http://www.ubuntuforums.org/showthread.php?t=27029&highlight=i810](http://www.ubuntuforums.org/showthread.php?t=27029&highlight=i810)

Dan M

---

### Post by jdong on 2005-04-15
Ok, the original poster's issue has been resolved already, and now it's just getting confusing who's asking what...


As a result, I'm locking this thread. If you have unanswered questions, please start a new thread.

---


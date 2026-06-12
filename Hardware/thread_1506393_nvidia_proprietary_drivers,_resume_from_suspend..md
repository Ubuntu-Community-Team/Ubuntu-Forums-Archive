---
title: "nvidia proprietary drivers, resume from suspend."
date: 2010-06-10
forum: Hardware
---

### Post by wadam on 2010-06-10
I have found frustratingly little about this online, so I thought that I'd ask here:

I have a GeForce 250 and am running the proprietary nvidia drivers on Lucid.  I am able to suspend my computer.  But when it resumes from suspend, one of two things happen:  either I get an entirely blank display, or I get some colored blocky garbage on the screen that resembles ANSI art of old.  In either case, my display is useless, and I have to do a hard reboot to correct the problem.

Is there any way to fix this so that I can suspend and resume normally?

Thanks.

---

### Post by efflandt on 2010-06-10
I am no nVidia expert.  But I installed 10.04 on an old Dell Inspiron 8200 I had temporarily while removing Windows viruses.  And Ubuntu suggested installing the nVidia(96) driver.

I was unable to suspend or hibernate due to a different issue (polling non-existing floppy with hot swap drive bay).  I eventually resolved that, but in the process, I installed uswsusp, since some people with suspend issues had success with that.  That is not really necessary, but in reading on-line docs for uswsusp, it said that to properly suspend with nVidia binaries, you had to blacklist the agp module that Linux used and instead use the nVidia agp.  To do that:

**lsmod | grep agp** and note any module containing agp other than agpart.  In my case it was intel_agp.  Create a file in /etc/modprobe.d/ using **sudo nano** or **gksu gedit** (I called it agp.conf).  You can put a comment in that file if you want to (begin a comment line with #) and add the following, or whichever agp module you found:

blacklist intel_agp

Then using sudo or gksu for your editor, edit /etc/X11/xorg.conf and add the following to the "Device" section (you can use tabs or spaces between fields):

Option "NvAGP" "1"

Reboot and see if suspend/resume work.

I was not sure if that was necessary, but when I undid that (by commenting out the blacklist line and the line in xorg.conf, I had a problem similar to yours (resume to blank screen).  Anyway that is something to try and you can always undo it if it fails to help.

---

### Post by towheedm on 2010-06-10
One thing I initially missed after switching to Ubuntu from Windows was the hibernation support.  I had the same problem as wadam.  I compensated for this by setting my system to remember running apps when logging off.

I tried the above procedure and it worked.  However, I only needed to add the Option line to the xorg.conf file.

Thanks, now I can suspend and hibernate successfully.:p

The only problem I have though, is that it does not ask for your password when resuming from suspend or waking from hibernation.  Is there a way to set this?

OK, found it.  I had my gnome-screensaver module not loaded.  So now I get the password prompt when resuming from suspend, but now it goes to the lock screen when I try to hibernate.  Further testing tomorrow.

---

### Post by sticksabuser on 2010-06-11
> **wadam said:**
> I have found frustratingly little about this online, so I thought that I'd ask here:

I have a GeForce 250 and am running the proprietary nvidia drivers on Lucid.  I am able to suspend my computer.  But when it resumes from suspend, one of two things happen:  either I get an entirely blank display, or I get some colored blocky garbage on the screen that resembles ANSI art of old.  In either case, my display is useless, and I have to do a hard reboot to correct the problem.

Is there any way to fix this so that I can suspend and resume normally?

Thanks.
Which driver version are you using?

---

### Post by wadam on 2010-06-11
> **sticksabuser said:**
> Which driver version are you using?

Not totally sure.  The latest version available through the Hardware Drivers control panel.

---

### Post by thierry.machet on 2010-06-13
I discovered that the problem is related to the modules intel_agp and nouveau in relation to my chipset. Installing NVidia proprietary drivers did not solve the problem at first because I was doing it the wrong way.   The remedy is quite simple: install NVidia driver, have it use its agp own driver, blacklist intel_agp and associated drivers.  Though simple, the complete precise steps is much too long to post it hear. I wrote a 14 pages procedure you can read at url [http://thierrymachet.lescigales.org/opensource/procedure-linux_6005_Optimisations_Sleep-suspend.php](http://thierrymachet.lescigales.org/opensource/procedure-linux_6005_Optimisations_Sleep-suspend.php)  Sorry it is in French. In need some 4 hours to traduce it in English, witch I will do if you find it useful for the community, let me know.

---

### Post by arealityfarbetween on 2010-07-29
> **wadam said:**
> I have found frustratingly little about this online, so I thought that I'd ask here:

I have a GeForce 250 and am running the proprietary nvidia drivers on Lucid.  I am able to suspend my computer.  But when it resumes from suspend, one of two things happen:  either I get an entirely blank display, or I get some colored blocky garbage on the screen that resembles ANSI art of old.  In either case, my display is useless, and I have to do a hard reboot to correct the problem.

Is there any way to fix this so that I can suspend and resume normally?

Thanks.

Did you ever get this working? 

I've always found that you need to change the bios' suspend type from S1(POS) to S3(STR) so check that first. 

After that, I had limited success with the 173 driver, just use the hardware drivers in administration to get it installed. Suspend resume works but when i need it, it doesn't. i.e. tested last night, worked ok. Started encoding a movie but wanted to suspend and resume in the morning-screen switches back on, just no response from anything, no num lock light, ctrl-alt-del doesn't work. Cold reboot to resolve. If you have better luck with that driver than me you might notice that when playing videos colour appears green tinted to fix, look here [http://www.junauza.com/2010/03/fix-blue-and-green-tinted-video-problem.html](http://www.junauza.com/2010/03/fix-blue-and-green-tinted-video-problem.html)

Trying the newest drivers again (think that's 195) with the option in the xorg.conf but i don't think NvAGP "1" will have any effect with ours being PCI-E cards, i'm sure i tested that already but will report back with definite findings.

Anyone else with PCI express, proprietary nvidia drivers and suspend-resume working, not working or a random combination of the above?

---

### Post by robosteven on 2011-05-10
> **efflandt said:**
> I am no nVidia expert.  But I installed 10.04 on an old Dell Inspiron 8200 I had temporarily while removing Windows viruses.  And Ubuntu suggested installing the nVidia(96) driver.

I was unable to suspend or hibernate due to a different issue (polling non-existing floppy with hot swap drive bay).  I eventually resolved that, but in the process, I installed uswsusp, since some people with suspend issues had success with that.  That is not really necessary, but in reading on-line docs for uswsusp, it said that to properly suspend with nVidia binaries, you had to blacklist the agp module that Linux used and instead use the nVidia agp.  To do that:

**lsmod | grep agp** and note any module containing agp other than agpart.  In my case it was intel_agp.  Create a file in /etc/modprobe.d/ using **sudo nano** or **gksu gedit** (I called it agp.conf).  You can put a comment in that file if you want to (begin a comment line with #) and add the following, or whichever agp module you found:

blacklist intel_agp

Then using sudo or gksu for your editor, edit /etc/X11/xorg.conf and add the following to the "Device" section (you can use tabs or spaces between fields):

Option "NvAGP" "1"

Reboot and see if suspend/resume work.

I was not sure if that was necessary, but when I undid that (by commenting out the blacklist line and the line in xorg.conf, I had a problem similar to yours (resume to blank screen).  Anyway that is something to try and you can always undo it if it fails to help.

Thanks a lot, your solution solved my suspend problem on a pentium 4 computer with a old graphics card using the nvidia 96 driver.

---

### Post by techknowledge on 2012-01-25
> **efflandt said:**
> I am no nVidia expert.  But I installed 10.04 on an old Dell Inspiron 8200 I had temporarily while removing Windows viruses.  And Ubuntu suggested installing the nVidia(96) driver.

I was unable to suspend or hibernate due to a different issue (polling non-existing floppy with hot swap drive bay).  I eventually resolved that, but in the process, I installed uswsusp, since some people with suspend issues had success with that.  That is not really necessary, but in reading on-line docs for uswsusp, it said that to properly suspend with nVidia binaries, you had to blacklist the agp module that Linux used and instead use the nVidia agp.  To do that:

**lsmod | grep agp** and note any module containing agp other than agpart.  In my case it was intel_agp.  Create a file in /etc/modprobe.d/ using **sudo nano** or **gksu gedit** (I called it agp.conf).  You can put a comment in that file if you want to (begin a comment line with #) and add the following, or whichever agp module you found:

blacklist intel_agp

Then using sudo or gksu for your editor, edit /etc/X11/xorg.conf and add the following to the "Device" section (you can use tabs or spaces between fields):

Option "NvAGP" "1"

Reboot and see if suspend/resume work.

I was not sure if that was necessary, but when I undid that (by commenting out the blacklist line and the line in xorg.conf, I had a problem similar to yours (resume to blank screen).  Anyway that is something to try and you can always undo it if it fails to help.

I would like to say thank you, efflandt, for the information provided. Simply adding the Option in the xorg.conf file fixed my issue with a non-functional resume from suspend. I was expecting this problem to be fixed through a video driver/configuration modification.
I did not return any agp results with the "lsmod|grep agp" command. Regardless, I went ahead and added the line to the xorg without blacklisting and it achieved the desired outcome. Now on a different note I would like to somehow get the tvout function to work with Oneiric as it used to in Lucid. I'm using a P4 Compaq Presario with Nvidia GeForce4 MX440 AGP with Ubuntu 11.10 Oneiric Ocelot.

---

### Post by PlastikSpork on 2013-04-14
> **efflandt said:**
> 

Then using sudo or gksu for your editor, edit /etc/X11/xorg.conf and add the following to the "Device" section (you can use tabs or spaces between fields):

Option "NvAGP" "1"

Reboot and see if suspend/resume work.



This also worked for me.  Thank you!

---


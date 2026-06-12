---
title: "Inspiron 1200 problems"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by markg on 2005-09-15
Live version and install version acts the same.  All seems to be fine until X starts and the lcd screens fades to black.  Nothing but black,  No buttons or mouse movement helps.  If I push the power button the text screen appears the the laptop reboots.  Any suggestions.

---

### Post by mlomker on 2005-09-15
Edit the /etc/X11/xorg.conf file and replace the video driver with VESA as a test.  It probably didn't detect your video card properly.

```

Section "Device"
     Identifier "Device"
     Driver "vesa"

```

---

### Post by frostoftheblack on 2005-11-04
[QUOTE=mlomker]Edit the /etc/X11/xorg.conf file and replace the video driver with VESA as a test.  It probably didn't detect your video card properly.

```

Section "Device"
     Identifier "Device"
     Driver "vesa"

```[/QUOTE]

I've been having this exact same problem with the same problem.
How am I supposed to edit the xorg.conf file if I can't even see anything?

---

### Post by mlomker on 2005-11-04
> How am I supposed to edit the xorg.conf file if I can't even see anything?

Ctrl-Alt-F2 and login.  Run **sudo dpkg-reconfigure xserver-xorg** when you get to a prompt.

---

### Post by Calib on 2005-12-13
Thanks guys.  I just got a Dell Inspiron 1200... cheapest new laptop I could find...  loaded ubuntu on this laptop and the log-in screen was all black as discribed in the original thread.

The 'sudo dpkg-reconfigure xserver-xorg' worked great!

Another thing that seemed to work:

Friend of mine pointed me to a url that had an updated driver for my i810 chipset.  Logged into Recovery Mode, did a 'wget' to the url, renamed original driver: '~/usr/X111R6/lib/modules/drivers/i810_drv.o' to 'i810_drv.o.old'. Copied the newer i810_drv.o to the drivers folder. Rebooted and worked.

[http://www.bram.be/travelmate_4651lci.html](http://www.bram.be/travelmate_4651lci.html)

---->in the Recovery Mode boot
cd
wget [http://www.fairlite.demon.co.uk/i810_drv.o](http://www.fairlite.demon.co.uk/i810_drv.o)
cd /usr/X11R6/lib/modules/drivers/
sudo mv i810_drv.o i810_drv.o.old
cp ~/i810_drv.o //usr/X111R6/lib/modules/drivers

Finished. Your X.org configuration should work now. Restart gdm or kdm: sudo /etc/init.d/gdm restart


--------
I set up ubuntu for dual boot with Windows XP Home.  XP with the original ~36 GB: partitioned to 26 GB with 10 GB reserved for ubuntu.  Anyway, I hadn't booted into the XP partition for a little while was I was checking out ubuntu.  I did all the updates that were offered upfront... Logged in and out: doing different things to modify the looks of the OS and how users log-on.

After being satisfied with my ubuntu session, I booted  back into the XP partition. XP did an auto scan disk and some changes to itself (I imagine because of the changes I made to its partition size from the ubuntu install).  Windows loaded fine and then I shut down the computer as normal.

The next time I tried booting into ubuntu -- I got the black screen again at the log-in GUI -- just as I had from the beginning.  Logged in Recovery Mode, peaked in the /drivers/ directory... everything seemd the same... although I had nothing to verify with -- other then my rename of i810_drv.o.old.  I had trouble (being half lazy and new to the platform) trying to overwrite  i810_drv.o from the root directory back into the /drivers/ directory.

I did a little hunting on the web and found your thread with the problem and answer I was looking for.

'sudo dpkg-reconfigure xserver-xorg' Changing to 'vesa' mode instead of the 'i810'.  ...But I got cought up in the options and stared messing with settings out of curosity.  I dind't fix the problem at this point -- I think I created more: -- so I re-installed ubuntu.  On my 1st try, this time following instructions: 'sudo dpkg-reconfigure xserver-xorg' worked with only changing to the 'vesa'.

I'll try to update the i810 driver again soon, and then try to figure out how the black screen came back.

I suspect some of the following:
--Updates when I was in ubuntu
--When I booted back into the XP partition and XP made changes.
--Harware incompadibilities
--Or my own tooling around

---

### Post by Calib on 2005-12-13
I noticed vesa mode display was a little weird when the log-on screen loaded up -- but then corrects itself.  I also noticed the refresh rate of windows were a little slow (when dragging windows accross the screen).

I ran through the process of updating the i810_drv.o from fairlite.demon.co.uk.  Then   went into the reconfigure of xserver-xorg -- setting it to i810 and hitting enter on every screen till it stopped asking questions.

Rebooted --- much more fluent with no weird log-on screen

I also did all the updates again..rebooted into my other partition and back several times....  no issues.... so far.

---

### Post by linuxnub on 2005-12-28
sorry, but how can i change any values there?...
i'm just about being asked many many questions ... 
what to do here?
i have no clue

---


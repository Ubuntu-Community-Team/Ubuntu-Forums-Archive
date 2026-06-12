---
title: "Tutorial - Laptop Dual Head / Monitors &amp; Widescreen"
date: 2006-07-29
forum: Hardware &amp; Laptops
---

### Post by luckylucky on 2006-07-29
I wrote the following to help someone else in another post elsewhere, but thought to share it with all of you here.  This is a how to tutorial on setting up Dual Heads / Dual Monitors with your laptop, and how to get your laptop widescreen working at proper resolution.  Hope this helps someone!

LuckyLucky



Hi friends,

[COLOR="Red"]**[SIZE="4"]I'll post the solutions I've got to this here for you.[/SIZE]**[/COLOR]

I too use dual head (dual monitors) with my laptop.  A while ago I also had to figure this out, and through extensive googling & asking a friend I've finally got the solution that works for me.  I've since installed this setup numerous times and it works.

STEP 1

First of all you want to back up your xorg.conf file since you'll be modifying it.  By having a backup you'll be able to revert to your original settings just incase it doesn't work for you.

Open up "Terminal" (in Ubuntu it's in "Applications" > "Accessories" > "Terminal"

type the following in EXACTLY (note that the "X" in "X11" is capitolized, but everything else is lower case)

[COLOR="SeaGreen"]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original.backup[/COLOR]
(it'll ask for your password, so type it in)

STEP 2

Go read this page:
[http://www.wahlau.org/ubuntu_hoary_thinkpad_t43_and_xorg_dual_head_display](http://www.wahlau.org/ubuntu_hoary_thinkpad_t43_and_xorg_dual_head_display)

I've followed this guy's instructions and I've got dual heads working.  Just go around inserting all the stuff he suggests inserting in **bold**.  Just do what he says even though it's for a different configuration than yours... it should still work.

By the way, in the last paragraph of instructions he gives he tells you to insert this line:

Screen         "Default Screen" [COLOR="Red"]LeftOf[/COLOR] "Screen1"	

If your external monitor is actually on the left side of your laptop monitor then just change it to this line:

Screen         "Default Screen" [COLOR="Red"]LeftOf[/COLOR] "Screen1"	

Note:  I've tried to run xinerama but it doesn't seem to work on my machine.  The above page doesn't do anything with xinerama, but if you want to try using it then look below, I've included a section on how to get that working too.

STEP 3

Ok, you are almost there.  You'll want to be able to change around your screen resolutions, ESPECIALLY IF you have a widescreen monitor on your laptop.

Go here to set up 915 resolution, which will allow you to select the widescreen resolutions for your laptop:

[http://www.ubuntuforums.org/showthread.php?t=199424](http://www.ubuntuforums.org/showthread.php?t=199424)

STEP 4

Ok, you are actually finished, but before you go running off to restart your computer here is a BIG TIP for you.  Grab a pen and paper and write the following down:

[COLOR="SeaGreen"]sudo cp /etc/X11/xorg.conf.original.backup /etc/X11/xorg.conf[/COLOR]

It's basically the same as what you entered above in step 1, just reversed.  Hopefully you won't need this, but if after rebooting your computer you can't get your monitors working properly then you'll need this to recover.

STEP 5

Now just reboot your computer.  You could also just type Ctrl+Alt+Backspace to restart your graphical xwindows, but I personally prefer to just reboot fully.

When it reboots and you've logged in then (hopefully) you'll have both monitors actively working, though your resolution will likely be wrong.  At least your mouse cursor should now travel between the two screens.

To configure your resolution click on "System" > "Preferences" > "Screen Resolution".  Now you should see TWO options for resolution settings - one for your laptop and the second for your second monitor.  Adjust these settings now to conform to the resolutions you want.

At this point you can be done & continue your happy computing, but there are three more things I'll talk about here for you (1) how to configure your xinerama (2) how to recover if the above steps messed your computer up and it doesn't work anymore and (3) a tip on how to keep your settings for future reformats.

BONUS XINERAMA

Like I said earlier, I couldn't get xinerama working for me, so perhaps it's my computer or that I just am doing something wrong.  But here is the step that I've learned about it.

First of all go through all the above steps and make sure it's all working first.  Then back up your good configuration with this command


[COLOR="SeaGreen"]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.good.backup[/COLOR]
(it'll ask for your password, so type it in)

This way if this step messes up your computer you can restore back to this so that all the work you've done up to this point won't be wasted.

Now type the following

[COLOR="SeaGreen"]sudo gedit /etc/X11/xorg.conf[/COLOR]

It'll open up a text based editor.

Near the bottom you'll see a section titled "ServerLayout"

Add this line into the section (at the end of all the other lines but before "EndSection")

[COLOR="Purple"]Option "Xinerama" "on"[/COLOR]

Save the file, close the editor, reboot your computer and cross your fingers.  If it works then great!  If it fails then restore by following the below instructions, only use the "good.backup" copy instead of the "original.backup" copy.  Good luck!


BONUS RECOVERY OF BAD CONFIGURATION

So you tried rebooting your computer after doing all the above steps but the computer politely informs you that your graphical display xwindows settings is messed up.  No problem.  Here is how to restore:

Just click on "OK" for the couple of messages alerting you to the problem with your xorg.conf settings.  Just bypass them.  You'll get to a really user-friendly text-only display.  Log in with your user name and password.  Then you'll be in shell terminal mode.

Type in that text you wrote on the piece of paper.  It'll then ask you for your password (give it).  Ok, then type :

[COLOR="SeaGreen"]sudo reboot[/COLOR]

Your computer will now reboot and (hopefully) you should be back in the way it originally was.


TIP TO KEEP SETTINGS FOR FUTURE USE

Having reformatted my computer repeatedly and going through the fun of reconfirguring stuff I've come up with my lazy method to save a bit of time.  Once you are happy with your xorg.conf file simply copy it and upload it onto a private website for future use.  If you ever reformat your computer and want to have this exact setting again then just copy it from your website (or portable backup hard drive) over top of the xorg.conf file in the fresh install.  Now this setting will be restored for you.

---

### Post by luckylucky on 2006-07-30
Oops!  I typed something wrong.  In "step 2" in the section with the following:
Screen "Default Screen" [COLOR="Red"]LeftOf [/COLOR]"Screen1" 
The second line was meant to say [COLOR="Red"]RightOf[/COLOR]

---


---
title: "tablet help needed"
date: 2008-12-22
forum: Hardware
---

### Post by benner on 2008-12-22
I have an HP Compaq tc4400.  i followed some pretty simple instructions (can't find the thread at the moment, i will try to add it later) to get the stylus to work when i was running hardy.  the same instructions don't work in intrepid.  i just did a fresh install.  nothing.  the instructions involved downloading the wacom tools and then tweaking the xorg.conf file.  it appears that intrepid is a bit different in that department.  the xorg.conf file does not have nearly as many entries in it so the changes i was supposed to make, i couldn't make.  i just had to add in the new entries.  in any case, it isn't working.  i tried the new opensuse 11.1 because it was supposed to have out of the box support for tablets and touchscreens.  after a few days, i didn't like opensuse and without the tablet support there was no reason to stick with it so i am back to ubuntu.

so, has anyone had any luck with intrepid and a tablet?  i have read every reference i could find in the forums (lots of them there) and nothing.  it's a real bummer because when it was working in the past, i was pretty happy with it. but like everyone else, those upgrades are pretty hard to resist...

thanks in advance for any suggestions

---

### Post by benner on 2008-12-23
still nothing?

---

### Post by Favux on 2008-12-25
Hi benner,

With Intrepid came the introduction of HAL (hardware abstraction layer) it was suppose to make xorg.conf obsolete and enabled hotplugging and other stuff.  Unfortunately it turns out not to work for us tablet pc users.  We have to revert back to xorg.conf.

You need to find a copy of your old xorg.conf.  Try looking in /etc/X11.  Try hard to re-find that thread.  Good luck.

---

### Post by benner on 2008-12-26
this is now a fresh install (after trying a couple other distros, hoping they would work better.)  no old xorg.conf to be found.  i have been twiddling around with the other threads and adding to my new xorg.conf but so far nothing.  does yours work now?

---

### Post by Favux on 2008-12-26
Hi benner,

I have a HP TX2000 with a Wacom Graphire USB tablet built in.  Yes, everything works, stylus, sidebutton, eraser, touch.

If you can't find your old xorg.conf you'll have to rebuild it.  Check Loic2's thread.  It has connections to his wiki's and sample xorg.conf's.  Remember he is mainly concerned with wacom graphics tablets, not tablet pc's, so pay attention and try to figure out the differences as you go along.  He also tells you how to install the linuxwacom drivers.  I'm on 0.8.2, the latest.

[http://ubuntuforums.org/showthread.php?t=967147]("http://ubuntuforums.org/showthread.php?t=967147")

[http://ubuntuforums.org/showthread.php?t=870640&page=41]("http://ubuntuforums.org/showthread.php?t=870640&page=41")

What would be helpful is if you knew the type of graphics tablet built into your laptop.  Is it wacom, if so what type?  Is it a serial or USB tablet?  If it is a clone does it emulate wacom good enough to use the linuxwacom drivers?  Check out this site on Tuxmobile, it seems to have relevant xorg.conf stuff.

[http://www.place4sure.com/tc-4400/tc-4400.html]("http://www.place4sure.com/tc-4400/tc-4400.html")

Good luck!

---

### Post by benner on 2008-12-28
thanks for your input so far.  the last time it worked was with wacom drivers.  and i know that it is a serial tablet.  i know this because when i installed the new opensuse (11.1) it has what was supposedly out-of-the-box support for tablets and it had my hp compaq tc4400 listed as a serial tablet.  of course it didn't work in opensuse and i didn't feel like messing about to get it to work when i could just as easily mess about with my beloved ubuntu.  but opensuse did have an option for wacom and a specific option for the tc4400 so i guess people have gotten it to work.  

i will keep plugging away.  and if anyone else has any luck, please add on.  thanks in advance...

---

### Post by benner on 2008-12-31
I added the following to my xorg.conf and now the stylus is working.  (i will keep the thread open until i have some more of the tablet functions working...)

Section "ServerFlags"
Option "AutoAddDevices" "False"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
EndSection

---

### Post by Favux on 2008-12-31
Hi benner,

Did you install the linuxwacom drivers?  If so how?  Using Loic2's wiki's?

I don't think you need the ServerFlags section.  You can probably comment it out.  People were trying it when they thought xorg.conf and HAL were incompatible.  It turns out they can coexist.  Is that why you have it?

I don't understand your device input sections.  You have:
```
Option "Device" "/dev/input/wacom"
```
Which is the input for a separate USB wacom graphics tablet, not a serial tablet pc.  Shouldn't your line look more like:
```
	Option		"Device"	"/dev/ttyS0"	# SERIAL only
```

Your tablet doesn't have touch, right?  But your stylus has an eraser.  Does it work?  I ask because your stylus might be working through HAL.

Also you do not need the "cursor" section, you can comment it out.  Again that's for folks with separate Wacom Graphics pads/tablets that have a mouse built into their pad, separate from their computer mouse.

Does your stylus have a side button?  We might get it working.  See attachments.

I'll edit your xorg.conf sections to show what I mean.  It will be in an attachment (by the way attaching your whole xorg.conf might be more useful) along with generic tablet pc xorg.conf sections.  I'll also include my xorg.conf.

---

### Post by benner on 2009-01-01
so i thought it was fine the way i had it.  then, this morning, i logged in and tried the stylus again and something had changed.  when i pointed the stylus, the cursor would appear about 15cm to the right of where the stylus was touching the screen.  while i was looking around to figure out how to reconfigure it, i came back and saw that you had responded to the thread.  so i used your edited version of my xorg.conf and it is now working like it should.  thanks so much.

the eraser is not working.  and you are right, it is not a touch screen.  it only works with the stylus.

*edit: I added 
Option        "Button2"       "3"
to the stylus section and now have the button on the side of the pen working.

---

### Post by Favux on 2009-01-01
Hi benner,

Great!  I was going to suggest side button next.  You beat me to it.

Eraser only works in some programs.  You have to tell them you have an eraser.  Please see post #8 here:

[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

This should help you set up eraser.

---

### Post by benner on 2009-01-03
still no eraser.  i followed the instructions and now have a nice launcher to rotate the screen but the stylus coordinates did not rotate with them. (i used option #3 and downloaded Tom's .deb file) i did manage to read between the lines with all of this and got the side scroll on my touchpad to work and am happy as anything about that.  

i have attached my (now very messy) xorg.conf file.  maybe there is a lcue in there.  in xournal, i checked all the appropriate boxes.  with the side button i can get the highlighter, for instance but the eraser still comes up like the pen.  at least it does something...

thanks in advance

---

### Post by Favux on 2009-01-03
Hi benner,

Which method did you use to rotate the screen?  One, two or three?  Who makes your videocard/chipset?  Intel, nVidia, or ATI?  Do you know the model number?

I took the liberty of editing your current xorg.conf.  I cleared out the clutter and reorganized it into a more logical order (at least for me).  Be sure to back up your current xorg.conf and do not loose it.  Compare the new one to your current one.  Make sure I didn't leave anything out.  Or make a mistake.

You had button2 3 in eraser too.  It should only be in the stylus section.

I commented out your ServerFlags section because I don't know if you need it.  Do you need it?  If so, why do you need it?  If you need it remove my comments.

Why did you add the Synaptics Touchpad section.  Didn't HAL run your Synaptics Touchpad OK?  Does it work better than the commented out Synaptics Touchpad section?  Mine works fine commented out-which means HAL runs it.

Benner if only stylus is working, and only in landscape mode (not tablet mode), then maybe your linuxwacom module is not loaded.  The stylus may be working through HAL.  Just warning you, in case the new xorg.conf does not work.

---

### Post by benner on 2009-01-03
Thanks again for keeping the dialogue going.  I used option #3 for the rotating screen.  i installed the deb file, your instructions said that in the sessions menu it would end in -f and i should add -t after that.  in fact the command just had 'wacomrotate' so added both -f and -t to the end.  then i copied the line in your instructions listed as option #3 into a file and called it .name.sh and saved in in my home folder and made a launcher that linked to it.  when i hit the launcher, it rotates the screen but not the coordinates for the mouse or stylus.

the eraser isn't working in xournal.  in the options menu, i have buttons 2 and 3 mapped to the eraser.  the side button on the stylus does activate the eraser but when i press down with the eraser button on the back of the stylus, it is just like the pen.  it draws a line.

i included the synaptics entry in the xorg file because the side scrolling feature wasn't working.  the pad itself was set up very nicely by default but i couldn't get the scrolling to work until i added it to my xorg.conf.  now that works and i am happy but the pad doesn't quite feel the same.  i have been playing around with the sensitivity settings but it still seems different.  oh well.  not serious.

from what i am describing, does it seem that my linuxwacom module is loaded? how can i check? 

the machine is an hp/compaq tc4400.  i think the processor and stats are:

Processor: 2.0GHz Intel Core Duo processor - 667-MHz FSB, 2-MB-L2 cache
RAM: 1GB DDR2 SDRAM
Video Card: 128MB (Shared) Mobile Intel 945GM Express Chipset

again, I have seen all of the effort that you have put into helping all sorts of people out with their tablet issues.  really wonderful of you to help so much.  this is why i use linux.

---

### Post by Favux on 2009-01-03
Hi benner,

Okay, I see the source of your confusion.  In Xournal the side button is the eraser.  The eraser only works as the eraser in Inkscape and especially the Gimp, once you have set it up in them.

In method 3 you shouldn't be using the "-t" in the Sessions command.  That's only for touch, which you do not have.  Remove it and try to rotate again.  If the stylus still doesn't rotate then try removing the "-f" and try again.  If neither works we'll set you up with a script.

I think your linuxwacom module is loaded.

To check if linuxwacom is loaded let's try and calibrate your stylus through "wacomcpl".  In a terminal type:
```
wacomcpl
```
a small gui program should pop up.  On the left should be a column with two options in it.  One will be stylus and the other eraser.  Click on stylus and more options should appear.  Go ahead and calibrate the stylus.

I'm guessing you haven't done this yet.  The wacomcpl settings are then stored in a .xinitrc file.  They only apply during the current session.  You can also change your settings on the fly using the xsetwacom parameters in a terminal.  To enable the .xinitrc file to apply to Xserver through a reboot you need to:
```
chmod +x ~/.xinitrc
```
Then go to System->Preferences->Sessions  and click on add and for the command write "~/.xinitrc" (without the quotes).  And title it “Wacom Tablet Calibration Settings” or whatever you like.

Oh, and when I typed ".name.sh" I meant name=rotate or name=my_rotation or whatever.  Like ".my_rotation.sh".  Sorry for the confusion.

So you have an Intel mobile graphics.  We should be good to go with that.

---

### Post by benner on 2009-01-03
excellent!  i took off the -t and nothing.  i took off the -f and now everything rotates properly when i click on the launcher.  thanks a lot!  i played around with the stylus setup but didn't change anything so for the moment i haven't bothered with xinitrc.  but maybe in the future i will need to change something.  i will download inkscape to see how the eraser works.  then, i guess i should tag this thread as solved...  cheers!

---

### Post by Favux on 2009-01-03
Great benner!

It's nice having a functioning tablet pc isn't it!

---

### Post by benner on 2009-01-04
inkscape is kind of buggy in my machine.  when i try to click on anythng in the dropdown menu, the whole window jumps.  weird.  so i can't do anything with it just yet.  maybe reinstall.  and i can draw in gimp but haven't worked out the eraser yet.  no hurry.  i will keep the thread going for a bit and share my experiences.  

last thing...  do you know anything about connecting to a wifi projector?  i'm a teacher and we have NEC projectors in the classrooms.  in vista, there is a utility called 'presenter' that allows me to connect.  i can use a browser to turn the projector on and off but can't actually get my desktop to appear on the screen.  if i use the vga connector it works, but not through the wifi.  

i know this is a bit off topic, but i am wondering if it could be a xorg issue as well.

---

### Post by Favux on 2009-01-04
I know Xournal has some troubles in KDE.  Also I've seen an xorg.conf somewhere that had "intel" something or other in the video section.  Maybe your xorg.conf video section needs some more work.

That may or may not relate to connecting to a wifi projector.  Sorry, I don't know anything about that.  Does Intel include a video configuration utility like nVidia does?  Sounds like something to take up on the Multimedia & Video forum.

---


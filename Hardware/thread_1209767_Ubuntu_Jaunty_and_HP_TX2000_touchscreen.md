---
title: "Ubuntu Jaunty and HP TX2000 touchscreen"
date: 2009-07-10
forum: Hardware
---

### Post by kevuk on 2009-07-10
Hi all,

I'm struggling with getting my touchscreen to work on a Hewlett packard TX2000 series laptop (actually tx2530ea), running Ubuntu 9.04

I've been following the instructions posted at [http://ubuntuforums.org/showthread.php?p=5469447;](http://ubuntuforums.org/showthread.php?p=5469447;) but at the step

sudo cp ./src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

I get that the message:
cp: cannot stat `./src/2.6.27/wacom.ko': No such file or directory


Can anyone help?

---

### Post by Favux on 2009-07-10
Hi kevuk,

That's because the kernel in Jaunty is newer, 2.6.28, which is why the command is failing.  Which turns out to be a good thing.  You need to go to gali98's updated HOW TO for Jaunty.  Read Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  And follow the link in 1) to his HOW TO on post #104.

Hope this helps &

Good luck1

---

### Post by kevuk on 2009-07-11
Sorry, that post is too technical for me.

However - It Works!  And I'm not sure how?

I can now point and click/double click with my stylus on the touchscreen; although the alignment is quite a way out - so can anyone tell me how to realign where I touch on the screen with what is being projected on the screen?  At the moment, if I click on the bottom right, I just about get the tabs on a maximised firefox screen.

At some point in the instructions the command 
"xinput --list" is mentionned, this brings up:

"Wacom ISDv4 93"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 26212
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 16420
		Resolution is 10000
"

Any help most appreciated :)

---

### Post by Favux on 2009-07-11
Hi kevuk,

Sorry to hear that.  I think if you look through gali98's HOW TO a few times you'll find it isn't that technical.  Just follow the instructions step by step and copy and paste the lines into a terminal.  Make sure each line is correct and hit return after each one if needed.

This header line tells you what's going on:
```
"Wacom ISDv4 93" id=6 [XExtensionPointer]
```
[XExtensionPointer] means your digitizer is being seen as a mouse rather than a tablet.

"Wacom ISDv4 93" is what HAL is calling your stylus.  And eraser and touch are not even being seen.  This is because the new "10-wacom.fdi" file in Section 2 of the HOW TO is not installed.

That means that "wacomcpl" (the linuxwacom calibration and configuration gui) will not work.  So you cannot calibrate your digitizer.  You could go to step 3 in Jaunty Users and either use rec's script or rename the linuxwacom names in the xsetwacom commands for .xinitrc (the hidden file wacomcpl uses).  That may allow you to use wacomcpl and calibrate.  But you would still be calibrating a mouse that lacks the eraser and touch.  So I don't advise this.  And really either of these methods are as "technical" as the HOW TO.

I hope this explanation is useful.

---

### Post by kevuk on 2009-07-11
It is indeed.

Very bashfully, yes those instructions did work this time.  Previous attempts gave me various error messages, but I'm now got a touchscreen.

Many thanks, both for your patience and your initial work on solving this.

Can I be a cheeky newbie and ask if somewhere on the fifty pages of that thread, someone has sorted out how to make the button on the side of the stylus work (= right click on MS)?  Also is there a way of getting an eraser function?

Also wacomcpl brings up an empty device list?

Thanks again.

---

### Post by kevuk on 2009-07-11
Ok, I've redone some more of the steps and now got wacomcpl working - is there any guide as to what these options mean?  I can't get the stylus working for the side button or eraser still?

---

### Post by Favux on 2009-07-11
Hi kevuk,

Great!  Nice job.

While you can add the stylus button to the .fdi (and yes it's buried in there a few places) usually we use wacomcpl to configure the stylus button.  Because the device list in wacomcpl is empty, it is likely that you haven't installed the 10-wacom.fdi correctly.

So using this command in a terminal:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi
```
Make sure it exactly matches at least the .fdi glai98 has in Section 2.  Notice the sliders on the "code" box and that some of the .fdi is out of view.  Make sure all of it is copied and pasted.  And that it is the only thing in the file.  Then save and close and reboot.  All of the configuration options gali98 shows you in the .fdi in Section 3 can be done through wacomcpl.

If the original default Jaunty 10-wacom.fdi is still there you can back it up before you replace it with gali98's .fdi by doing this first:
```
sudo cp /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi /home/yourusername/Desktop/10-wacom.bak
```
Where yourusername is the user name you are using.  (nice phrase, eh?)

The eraser is a seperate issue.  It only works in programs designed to detect it like Gimp and Inkscape.  See near the bottom of:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)  In Xournal the stylus button is the eraser.

Edit:  Oh, right.  A little more on wacomcpl in Section 3 of the HOW TO on the first page:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by Favux on 2009-07-11
Hi kevuk,

Oops!  I just noticed you beat me to the punch.  In wacomcpl click on stylus and go to Tool Buttons.  Button 2 is the stylus button (Button 1 is the stylus tip).  Choose what you want Button 2 to be, usually a right (which would be a 3 in the .fdi) mouse click.  Hit OK.

---

### Post by kevuk on 2009-07-11
Thanks again, issues are tumbling down!

Ok - so far I have a functioning digitizer on which I can apply both left and right clicks with varying sensitivity (tested on GIMP).  I'm also using cellwriter to enter handwriting.

Two very minor issues remain:
1) Cellwriter - how do differentiate o, O and 0?
2) How do you change the orientation of the screen when you turn the laptop into a slate?  Windows does it automatically (sometimes...), while linux ignores both the rotate button and the rotation of the screen?

---

### Post by Favux on 2009-07-11
Hi kevuk,

Yep, you're definitely getting there!

You have to train CellWriter.  There are some tips on the CellWriter page:  [http://risujin.org/cellwriter/](http://risujin.org/cellwriter/)  And:  [http://www.linux.com/archive/feature/120867](http://www.linux.com/archive/feature/120867)

To rotate you need the Rotation HOW TO.  There was a link at the bottom of Section 3, the wacomcpl section.  It's here:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)  Method 1 or 3 should work.

---

### Post by kevuk on 2009-07-11
Again, thank you for your suggestion.  Unfortunately, again, a bit too involved and technical.

But, I have an alternative solution to screen rotation as an adaptation of 
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

Essentially I have two shell scripts:

The first rotates the screen and the digitizer to 180 degrees (i.e. tablet mode)
#!/bin/bash


        xrandr -o inverted
        xsetwacom set "stylus" Rotate HALF
    
The second rotates the screen and the digitizer to normal
#!/bin/bash

        xrandr -o normal
        xsetwacom set "stylus" Rotate NONE
       
Both are saved and I would have given them keybindings, however this is proving difficult.  So I've given them launcher icons on my panel.

Does this seem an ok solution?  It works so far.

Ta.
K.

---

### Post by Favux on 2009-07-11
Hi kevuk,

I think what's happening is you are suffering a little bit from information overload.  That's normal.  If you break it down and take it step by step you'll find it isn't anymore complicated than what you are already doing.  Try working through the eyes glazing over phase.

For example to:
```
xsetwacom set "stylus" Rotate HALF
```
you would need to add "eraser" and "touch" xsetwacom lines and the same with the NONE line.  Oops, you've basically written the rotation script in method 1.  See what I'm saying?

---

### Post by kevuk on 2009-07-12
Yes I'd agree with the overload statement.

Could you clarify what touch and eraser are supposed to do?

---

### Post by Favux on 2009-07-12
Hi kevuk,

The HP TX2000 and TX2500 have both a wacom digitizer and a touch screen built into them.  The touch screen reacts to your finger or fingernail.  The digitizer to the stylus.

The eraser works like an eraser in programs like Gimp and Inkscape.  It has pressure like the stylus so you can "smudge" etc. in addition to erasing.  Notice how the eraser nub retracts into the barrel of the stylus.

---

### Post by kevuk on 2009-07-12
Excuse my numptiness - but what I've done works equally for fingertouch and stylus pen - so what's the difference between these two?

---

### Post by zoomy942 on 2009-07-12
Favux strikes again :)

---

### Post by Favux on 2009-07-12
Hi kevuk (hey zoomy942),

Not sure what you're saying/asking.  If you look at the .fdi you'll see there's separate sections for stylus and touch.  Remove the touch section and it will go away.

But I think you're talking about rotation?  If it's working for you, great.  If you drag a launcher into the top panel, it only takes a single click to launch it.

---

### Post by kevuk on 2009-07-12
Right, I think I've sorted it.  I've had a play with option 1 as scenario as suggested and I've made it do all 3 (finger, stylus and eraser) in either inverted or normal modes.  Having the screen rotated 90 or 270 degrees won't be useful for what I've in mind.  Yes, it's now on the topbar (or as I prefer it, the bottom bar)

Thanks for advice and suggestions.

---

### Post by kevuk on 2009-07-12
Am I right in thinking the answer to my earlier question is that the screen is touch sensitive - which is where the finger touch comes in, and the stylus is also touch sensitive - which is where the stylus comes in?

---

### Post by Favux on 2009-07-12
Hi kevuk,

Good deal!  Sounds like you're all set up now.  You're welcome.

Well more like the digitizer is stylus sensitive, but yes, you have it.

---

### Post by kevuk on 2009-07-17
Me again.  For some reason it's stopped working.

The positioning seemed a bit out, so I reopened wacomcpl and now only touch is showing as an option?

I've not edited any of the settings, but have downloaded multiple updates since then.

I've gone back to the original posts and gone through the same steps to get it working, but no change.  Any advice?

---

### Post by Favux on 2009-07-17
Hi kevuk,

If one of the updates was a kernel or kernel header update that will knock out the wacom.ko you compiled for your older kernel.  You need to recompile it and copy it back into place.  In other words repeat Section 1 of gali98's HOW TO.

---

### Post by kevuk on 2009-07-17
Thanks, did so and it didn't work.  Then did so again (I guess properly this time) and it's now working fine.

Your handholding much appreciated.

---

### Post by Favux on 2009-07-17
Hi kevuk,

You're welcome.  Kernel updates only come through every 3 to 6 weeks.  After you go through it a couple more times you'll learn what to pay attention to and it will only take about 5 minutes.  So no big deal.

---

### Post by kevuk on 2009-07-17
Isn't that a big problem for non-technical linux users?  I'm borderline techie, and I can imagine that recommended updates interfering with configuration files will confuse me no end if that's common practice.

---

### Post by Favux on 2009-07-17
Well sure.  But they almost got things working out of the box with Jaunty.  Believe it or not. Hopefully with Kharmic they'll have it figured out.

---


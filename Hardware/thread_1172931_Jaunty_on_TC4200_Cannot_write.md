---
title: "Jaunty on TC4200: Cannot write"
date: 2009-05-29
forum: Hardware
---

### Post by spre on 2009-05-29
Hi, I did an upgrade from Intrepid to Jaunty and have problems with the tablet functionalities; here is the status:

Wacom: recognized
Eraser: NOT recognized
Pen: recognized, however only scribbling is possible; writing or drawing is impossible because neither start writing or stop drawing is possible -- somewhat erratic (TPCButton is set to 'on'); the pen only stops if taken away for more than one inch (>2.5cm); this happens on XOURNAL, JARNAL and GIMP; on the gnome desktop the selection function is always activated ....

I appreciate any help ...

For system analyis I attach a hardware report, xorg.conf and wacom.fdi; please let me know if you need additional information ...

Regards

spre

---

### Post by spre on 2009-05-29
Concerning the pen I observed the following on the gnome desktop:

Gnome: Touching the glass with stylus once has the same effect as if one drags the mouse with the left mouse key pressed (eg. for selecting several objects); eraser ditto

Xournal: The Stylus doesn't write a all if it touches the glass, if the stylus does not touch the glass (1-2 mm away), it draws lines -- it should be the other way around

---

### Post by Favux on 2009-05-29
Hi spre,

The first thing is to see if you can run "wacomcpl" in a terminal to calibrate and configure your tablet.  In a terminal type:
```
xsetwacom list
```
It should report your wacom input devices, which I think are stylus and eraser.  If it is blank then "wacomcpl" won't work.  So then to see what HAL is reporting stylus and eraser as in a terminal type:
```
xinput --list
```

---

### Post by spre on 2009-05-30
Hi Favux,

Thanks for your reply here you are -- glad to hear from you again:

(1) wacomcpl works with the current custom_wacom.fdi ; I mention this because although the gui opened it didn't show anything before I attached the attached the version that is currently loaded as custom_wacom.fdi ..

(2) The other requested information is attached -- (also with the current custom_wacom.fdi I get output on xsetwacom list)

(3) I have another fdi in '/usr/share/hal/fdi/policy/20thirdparty/' called '10-wacom.fdi' (also attached; I think its yours); I copied and changed the custom_wacom.fdi according to instructions in other posts -- is it necessary to have both fdi's concurrently?

New status using the current custom_wacom.fdi:
Stylus: writes if front switch is pressed and stylus is on a certain distance to the glass (does -not- touch) 
Eraser: now works like the stylus is supposed to work; activate the back switch by pressing the erasor to the glass = writing; otherwise the cursor follows; however, it does not work as eraser ....

cheers, spre

---

### Post by Favux on 2009-05-30
Hi spre,

That was my question too when I saw you were running a custom .fdi.  It looks like you got it from Wacom.fdi and running both does give the correct linuxwacom names in xinput.  That doesn't happen if you just use the default or standard 10-wacom.fdi in '/usr/share/hal/fdi/policy/20thirdparty/'.

Can it mess with with your stylus to be running both?  You could remove the custom_wacom.fdi and see if things straighten out.  Just run xinput again and we should be able to get the name thing straightened out.  But before that...

When you were in wacomcpl did you configure the stylus?  Button1 is the stylus tip and should be configured as 1.  Button2 is your first stylus button.  If it is your only one most people configure it as 3 (R mouse click).  If you have two most leave it as 2 (middle mouse click) and leave Button3 (second stylus button) as 3.  Also I think maybe we should look at your .xinitrc.  It is a hidden file in your home/username directory.  For more on wacomcpl see Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by spre on 2009-05-30
Hi Favux,

I did remove the custom fdi and I didn't see the devices in wacomcpl anymore; however I put the fdi back in place but now it doesn't work anymore (I have must have done something wrong .... will get back to you the soon I have settled my issue ;) ).

The other thing that makes me think that we have overconfigured soemwhere: on the output I sent you see the stylus and eraser twice ....

---

### Post by Favux on 2009-05-30
Hi spre,

It's probably too late, but before you put in the custom .fdi run xinput again.  That will show you the names that HAL is returning.  Then go read 3 and 3a on Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by spre on 2009-05-31
Favux,

I did (3a) and I no longer need the custom_wacom.fdi; since my wacom is a serial graphire I concluded that I don't need the development version; right?

Stylus: the cursor follows the pen but it seems that buttom 1 on/off doesn't work the way one would expect; somehow it clicks on when you touch the glas and off when you touch the glas again. Shouldn't it be like 'on' when you touch the glas and 'off' when you go away from the glas? (Xournal, Gournal)

Eraser: works

---

### Post by Favux on 2009-05-31
Hi spre,

Good deal!  So you've almost got it.

I'm sorry you lost me.  What development version?  If you mean the special compiling stuff (the wacom.ko) in 1) you're right.  Same with the .fdi.  That's usb stuff.  The native Jaunty linuxwacom packages should work for you.

Have you calibrated and configured with wacomcpl yet?  See Section 3 on the HOW TO on post#1 and page 1 (the one with Jaunty Users).  That may straighten it out.

If not there are a couple other settings you could play with in your .xinitrc.  See:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)  I'm thinking maybe:
```
   ClickForce    integer (1 - 21)         sets tip/eraser pressure threshold with clickforce scale
   Threshold     integer                  sets tip/eraser pressure threshold directly to the pressure

```
in addition to:
```
TPCButton     on|off                   turns on/off the buttons as Tablet PC buttons

```
which you've already dealt with.

Edit:  Sorry, cursor refers to the Wacom mouse so I deleted it.

---

### Post by spre on 2009-05-31
Hi Favux,

Thanks, I meant the special compiling stuff, sorry. 
(1) However, before I continue with the calibration, does wacomcpl read  different values than what is stored in the .xinitrc? eg. my installation always assumes a 3 button stylus, even though my .xinitrc has different parameters. I enclose my .xinitrc ...

--8--
xsetwacom set stylus TPCButton "on"
xsetwacom set stylus Button3 "Button 0"
xsetwacom set stylus Button2 "Button 3"
xsetwacom set stylus Button1 "Button 1"
xsetwacom set stylus TwinView "1"
xsetwacom set stylus Suppress "2"
xsetwacom set stylus RawSample "4"
xsetwacom set stylus ClickForce "6"
xsetwacom set stylus PressCurve "0 0 100 100"
xsetwacom set eraser Button1 "Button 1"
xsetwacom set eraser Suppress "2"
xsetwacom set eraser RawSample "4"
xsetwacom set eraser ClickForce "6"
xsetwacom set eraser PressCurve "0 0 100 100"
# run the primary system script
. /etc/X11/xinit/xinitrc
--8--

(2) One thing I discovered is that on output 'xinput --list' the mouse mode is set to 'relative' and both, stylus and eraser are set to 'absolute'; what's the difference?

--8--xinput --list
.....skipped ...
"PS/2 Generic Mouse"	id=2	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

"stylus"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 24780
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 18630
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"eraser"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 24780
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 18630
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
....skipped ....
"SynPS/2 Synaptics TouchPad"	id=8	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1

---

### Post by Favux on 2009-05-31
Hi spre,

No that looks correct.  Button1 is the stylus tip.  Button2 is the first stylus button.  Button3 can be the second stylus botton.  Or in some way I don't quite understand it can sort of be the eraser.

Most people want the absolute, but you have the option of setting them relative.  That more applies to the graphics tablet folks.  It has to do whether they stay in a program window or not.

---

### Post by spre on 2009-05-31
Hi Favux,

On the stylus I have a new phenomenon on Xournal and Gournal: it writes if I move it 1-2 mm above the glas and it doesn't write if I touch the glas ... shouldn't this be the opposite?

I did some research and came across the new multitouch capabilities offered by Wacom; is it possible that we have to some additional configuration to handle this new feature on an old tabletpc?

---

### Post by Favux on 2009-05-31
Hi spre,

Mutlti-touch (MPX) hasn't been added to Xserver yet.  And the Wacom digitizers don't have the hardware to support them yet.  You'd have to have an N-trig digitizer like in the Dell Latitude XT or HP TX2z.  Win 7 will have multi-touch but I doubt Ubuntu will get it until the version after Kharmic (9.10).  Although there is some hope it'll make it into Kharmic as experimental.

In terms of the stylus behavior that is the opposite.  I'm not sure what's going on.  Check in wacomcpl>stylus>tool buttons>side switch mode and see if it is set to side switch + tip.  Maybe you have it set to side switch only and are inadvertently holding down your stylus button.  Or try stylus>feel.  Record the defaults (although there is a default option) and play around with the settings.  Maybe that'll fix it.

---

### Post by spre on 2009-06-01
Hi Favux,

Tried to fiddle around but cannot get it right; I believe the options available deal more with sensitivity than whether 'on' is 'off' and otherwise around.

The writing is definitely vise versa on the stylus meaning that it writes when I move the stylus not touching the glas; however it stops writing the soon the stylus touches the glas. 

I can write my name with the eraser ... and if I select the eraser it erases when it touches the glas.

Shall I report a bug or would a re-installation help on this issue? I still hope that there is a switch somewhere that we can turn this behaviour off. 

One more thought: could it be something with the doubleclick

Peter

---

### Post by spre on 2009-06-01
Hi Favux,

I checked the wacom project and found something .... please check 'Erratic Pen movement on x41t laptop - ID: 2030106' on [http://sourceforge.net/tracker/index.php?func=detail&aid=2030106&group_id=69596&atid=525124](http://sourceforge.net/tracker/index.php?func=detail&aid=2030106&group_id=69596&atid=525124)

Bug has been fixed on the previous release but it seems that it made it back on 8.2.2.

Regards

spre

---

### Post by Favux on 2009-06-01
Hi spre,

I'm sorry but I don't know what's going on.  You could try playing with the settings that apply to the stylus some more.  It seems like '"TPCButton"  "on"' isn't being applied.  Crazy idea.  Have you tried turning it off (ie changing "on" to "off")?

One other thought.  You may be inadvertently pressing the side switch.  Most folks set it up so it works when your stylus tip is in contact with the glass.  In wacomcpl when you've selected stylus options pop up. One is "Side Switch Mode" and I have selected "Side Switch + Tip" but you can have "Side Switch Only"

Here is the LWP HOWTO page with the settings:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)  Maybe you'll see something that applies.

Before you file a bug report maybe you could consider reinstalling.  There may be a "glitch" with your installation.  You know a lot more now and it should be easier the second time around.

Good luck!

---

### Post by spre on 2009-06-29
Favux,

Got it! I was the pen; there was something wrong with the switch located at the tip; so the pen writes if hovering over the screen and when it touches the writing stops (it should be vice versa). When I borrowed my friend's pen I could even control the thickness of the line when pressing firmer (I was never able to do that).

I ordered a new pen and I am positive that this will solve the problem. My conclusion is that, if the hardware is in good shape, the new HAL based recognition works well on a TC4200.

Regards,

Peter

---

### Post by Favux on 2009-06-29
Hi Peter,

Good news.  I never even considered a hardware problem.  And you'll now have pressure too.  Good deal.

---

### Post by spre on 2009-06-29
Favux,

One more question concerning wacomcpl: is there a manual that explaines the various settings one can adjust? Particularly I am interested in the screen mapping functionality (purpose, effects).

Thanks for your help!

Regards

spre

---

### Post by Favux on 2009-06-29
Hi spre,

No specific manual per se.  I guess the manual is LWP's HOW TO here:  [http://linuxwacom.sourceforge.net/index.php/howto/main](http://linuxwacom.sourceforge.net/index.php/howto/main)  You probably want to look at sections 11.0, 5.1, and 9.0.

---


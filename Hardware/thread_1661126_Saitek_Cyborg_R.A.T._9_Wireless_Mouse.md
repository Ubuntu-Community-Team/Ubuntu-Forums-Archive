---
title: "Saitek Cyborg R.A.T. 9 Wireless Mouse"
date: 2011-01-06
forum: Hardware
---

### Post by joey89 on 2011-01-06
Hi,

I bought the R.A.T. 9 Mouse and got the most functions working on my Ubuntu 10.04LTS 64Bit.

I´m writing this thread because many people have problems with this mouse on Ubuntu and maybe we can fix the last problem i have with this mouse.

Here is how you get the most functions of the mouse working:

I found out that the Mode-Button on the mouse has access to the X-Server and disrupt it.
With the Command (in terminal) "xev | grep button" I found out that the Mode Button is registered as Button 13, 14 und 15 on my PC.
To get the mouse working i have deactivated this buttons in the Xmodmap.
Enter following command in the terminal "sudo gedit /etc/X11/Xmodmap". Usually this file is blank, so write the following text in it: "pointer = 1 2 3 4 5 6 7 8 9 10 11 12 0 0 0 0 0 0 0 0 0" and save the file. After restarting the X-Server (Logoff/Login) the mouse should work.

To use the thumbwheel and thumbbuttons i installed the program "imwheel" (from the Software-Center).

In the file startup.conf from imwheel i wrote:
[I]IMWHEEL_START=1
IMWHEEL_PARAMS='-b "0 0 0 0 8 9 10 11 12"'[/I]

And in the imwheelrc - file i wrote:
[I]".*"

#   Button 8 (Thumbbutton reverse)
None, Thumb1, Control_L|Alt_L|t

#   Button9 (Thumbbutton forward)
None, Thumb2, Alt_L|a

#   Button10 (Thumbwheel right)
None, ExtBt7, Control_L|Alt_L|Right

#   Button11 (Thumbwheel left)
None, ExtBt8, Control_L|Alt_L|Left

#   Button12 (red sniper Button)
None, ExtBt9, Alt_L|F4[/I]

So now i´m using the thumbwheel for changing desktops (i do have installed compizconfig), the sniper button for closing windows, and the other thumbbuttons for starting the terminal and my firefox internet browser.


The only function i have not yet got working is to adjust the DPI settings. The mouse can switch by herself the four DPI Settings (there are default setting on the mouse), so it works good.... but it would be nice to adjust the DPI´s.

Do you have any idea to fix that?

greetings, joey

---

### Post by yo555yo on 2011-01-19
hello, i'm trying to configure a cyborg rat 7, on ubuntu 10.10 x64.

I create the file /etc/X11/Xmodmap with: pointer = 1 2 3 4 5 6 7 8 9 10 11 12 0 0 0 0 0 0 0 0 0

Change 2 lines of inicialization file /etc/X11/imwheel/startup.conf 

IMWHEEL_START=1
IMWHEEL_PARAMS='-b "0 0 0 0 8 9 10 11 12"'

and add the lines you write for mapping extra buttons at the end of the file:

/etc/X11/imwheel/imwheelrc

but it doesn't works for me, 

I have to say that before run imwheelrc my forward and backward buttons works well on firefox or chrome but when start imwheelrc doesn't works anymore.

if i run on command line: xinput watch-props 8
```
Device 'Saitek Cyborg R.A.T.7 Mouse':
	Device Enabled (142):	1
	Coordinate Transformation Matrix (144):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (268):	0
	Device Accel Constant Deceleration (269):	1.000000
	Device Accel Adaptive Deceleration (270):	1.000000
	Device Accel Velocity Scaling (271):	10.000000
	Evdev Reopen Attempts (261):	10
	Evdev Axis Inversion (272):	0, 0
	Evdev Axes Swap (274):	0
	Axis Labels (275):	"Rel X" (152), "Rel Y" (153)
	Button Labels (276):	"Button Left" (145), "Button Middle" (146), "Button Right" (147), "Button Wheel Up" (148), "Button Wheel Down" (149), "Button Horiz Wheel Left" (150), "Button Horiz Wheel Right" (151), "Button Side" (263), "Button Extra" (264), "Button Forward" (265), "Button Back" (266), "Button Task" (267), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262), "Button Unknown" (262)
	Evdev Middle Button Emulation (277):	2
	Evdev Middle Button Timeout (278):	50
	Evdev Wheel Emulation (279):	0
	Evdev Wheel Emulation Axes (280):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (281):	10
	Evdev Wheel Emulation Timeout (282):	200
	Evdev Wheel Emulation Button (283):	4
	Evdev Drag Lock Buttons (284):	0

```

I didn't know what im doing wrong :-(

---

### Post by joey89 on 2011-01-20
I think i know what's wrong ;)

imwheel is like a converter for your pc, if you press a button which is configured in imwheel, imwheel tells your pc that the configured keypad buttons are pressed.

i simply think that your pc has other keyboard-button-combinations programmed.
(sorry, my english is not the best:D)

let me show you on a example, this is my current imwheelrc - file:
[I]
".*"

#   Button8 (Thumbbutton reverse)
None, Thumb1, Alt_L|F9

#   Button9 (Thumbbutton forward)
None, Thumb2, Alt_L|F10

#   Button10 (Thumbwheel right)
None, ExtBt7, Control_L|Alt_L|Right

#   Button11 (Thumbwheel left)
None, ExtBt8, Control_L|Alt_L|Left

#   Button12 (red sniper Button)
None, ExtBt9, Alt_L|F4


[/I]When i press the red sniper button, imwheel tells my pc i pressed the keys "Alt" and "F4" on my keyboard, which is in my computer programmed to close the actual window.

If I press the thumbbutton forward it tells my pc i have pressed "Alt" and "F10" which means to my computer to maximize thw actual window.

You can find this first keyboard-combinations in the menu system->adjustment->keyboard-combinations 

to rotate the desktop cube i use the thumbwheel. i configured imwheel that if i scroll to the right side it says "Alt" and "Right", then i then i configured compizconfig that if i press "Alt" and "Right" the cube will rotate to the right side.

You may have notified that i write "Alt_L" in the imwheel-file instead of the button "Alt".
You can find out this "digital key" of a button with the command "xev" in the terminal.
If you then press the button it will show you a large message within somewhere stand the code for the button (like Alt_L).

try it out if this will help you, and if not you can post a message and i will try to help you again.

best regards,   joey

---

### Post by yo555yo on 2011-01-21
Hi, thankyou for your help, 

 this is the output of "xev | grep button" when pushing extra buttons on mouse and imwheel is not running: 
```

    :~$xev | grep button
    state 0x10, button 8, same_screen YES
    state 0x10, button 8, same_screen YES
    state 0x10, button 9, same_screen YES
    state 0x10, button 9, same_screen YES
    state 0x10, button 10, same_screen YES
    state 0x10, button 10, same_screen YES
    state 0x10, button 11, same_screen YES
    state 0x10, button 11, same_screen YES
    state 0x10, button 12, same_screen YES
    state 0x10, button 12, same_screen YES

```It recognices all butons perfectly and works Thumb1 and Tumb2 as forward and back.

 This is the output when run comand: imwheel -b "0 0 0 0 8 9 10 11 12" 
and push the same buttons
```

~$ xev | grep button
    state 0x10, button 10, same_screen YES
    state 0x10, button 10, same_screen YES

```Only recognices second wheel turning right, the others don't print anything.

  if try the output of xev without filtering it with  "grep button" it is always the same for all the extra buttons:
```

KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  4294967219 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

MotionNotify event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb3, subw 0x0, time 9699225, (130,107), root:(133,162),
    state 0x10, is_hint 0, same_screen YES

```trying whith the Alt key the result of xev i think is ok
```

    KeyPress event, serial 36, synthetic NO, window 0x4c00001,
    root 0xb3, subw 0x0, time 9077498, (910,551), root:(913,606),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```I have try this configuration on another computer with same result, 

my version of imwheel is: imwheel 1.0.0pre12 by -=<Long Island Man>=- <jcatki@jcatki.no-ip.org>

I don't know what to try   ](*,)

---

### Post by thothommy on 2011-02-02
Hi, ich habe das Problem mit einem separaten Skript gelöst,

--------------------------------------------------------------------------
#!/bin/bash
sleep 20 && imwheel -k -b "0 0 0 0 8 9 10 11 12" ;
--------------------------------------------------------------------------
und in der /etc/X11/imwheel/startup.conf

# Configuration file for setting imwheel startup parameters.
# Set this to "1" to have imwheel start along with your X session.
#IMWHEEL_START=1

# Specify the command line parameters to pass to imwheel when it is started
# along with your X session (above). Simply uncomment the bottom line, and
# if necessary replace the default options with your own. A button spec of
# "0 0 0 0 8 9" will grab the thumb buttons of most mice, while skipping over
# the mouse wheel (both the vertical and horizontal axes, whether or not they
# exist on your mouse). Keep in mind that each button number must be separated
# by a space.
#IMWHEEL_PARAMS='-k -b "0 0 0 0 8 9 10 11 12"'
#imwheel -k -b "0 0 0 0 8 9 10 11 12"
--------------------------------------------------------------------
und in die imwheelrc folgendes eingefügt

".*"

None, ExtBt7, Control_L|Alt_L|Right
None, ExtBt8, Control_L|Alt_L|Left
None, ExtBt9, Alt_L|F4

#"^Firefox-bin$"
None,Thumb1,Alt_L|Left
None,Thumb2,Alt_L|Right
--------------------------------------------------------------------

es funktioniert vielleicht nicht sauber aber es klappt

---

### Post by mcai8sh4 on 2011-02-02
Thanks to everyone who has posted, after reading through, I realised it was worth getting a RAT9 now I knew I could get funtionality in Linux!

I'm having a little problem, I have repeated all the steps, and had a play around, but the thumb wheel and the red button just threw up errors. 

After trying thotommys suggestion (although I dont understand German) I found it worked. It seems to have something to do with the sleep 20 - WHY??

Anyway, it seems to be working now I just have to configure how to start the cube rotate when I press the red button.
-EDIT- I can't get the rotate cube in compiz to use button12 (the red button) to initiate - anyone any ideas?

Any explanations would be appreciated.

Thanks again!

-Steve

Figured it out - I just removed the lines for button12 in imwheelrc, launch imwheel using "sleep 20 $$ imwheel -k -b "0 0 0 0 8 9 10 11"; " then edited compiz in gconf-editor.

Winner!

Now just to figure out why the sleep part is needed. Thanks

---

### Post by mcai8sh4 on 2011-02-05
After getting everything working, I realised that I could configure my mouse to do exactly as I wanted just using CompizConfigSettingsManager. Ah well, at least I've learnt a few new things.

I was wondering if anyone knew how to find the battery level of the mouse? Would just be handy to have on my conky settings, so I can see the battery usage.

Thanks

---

### Post by awc_ on 2011-02-09
> **mcai8sh4 said:**
> .....

I was wondering if anyone knew how to find the battery level of the mouse? Would just be handy to have on my conky settings, so I can see the battery usage.

Thanks
I'm not sure its really worth having a battery indicator... the battery needs to be changed ever 8-9 hours irrespective of use.

I want to use IMWHEEL to shift between workspaces like the OP stated, but I still want to use the forward and back buttons for travelling forwards and backwards within firefox. How can I do this?

Thanks

---

### Post by weeman7007 on 2011-03-15
Has anyone tested this in 11.04 yet?

Also is there any way of making the mode button work to switch the functionality across?

---

### Post by wildmanne39 on 2012-07-04
Hi, this is an old thread so it has been closed, it has been moved to a thread of it's own .
Thanks

---


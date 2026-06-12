---
title: "Trouble with Tablet PC rotation and input."
date: 2011-04-01
forum: Hardware
---

### Post by tristram60 on 2011-04-01
Hey guys I'm new so beginner talk please.  Anyways, I installed ubuntu on my school tablet pc because I like it better the windows 7.  It doesnt automatically go into tablet mode (rotate screen) which is pretty important for me.  I can manual rotate screen but then the pen input is totally thrown off.  Any suggestions?  I know that ubuntu isnt really designed for tablet pc's but there has to be some kind of calibration tool, right?

Thanks in advance

---

### Post by Favux on 2011-04-01
Hi tristram60,

Welcome to Ubuntu forums!

Could you tell us the maker and model of your tablet pc?

---

### Post by tristram60 on 2011-04-02
I thought someone might say that sorry I didn't put it in.  

I have a toshiba portege m780 tablet pc.  I'm not sure if you need specs but here they are

Intel core i5 (not sure which model)
6gb ram ddr3
250gb hd 37gb given to ubuntu

Thanks for replying!

---

### Post by Favux on 2011-04-02
OK, we should be able to get it to rotate for you.  Which release of Ubuntu are you using, Lucid or Maverick?  I forgot to ask.


Also it looks like you can order it with and without touch.  If you got the touch screen along with the Wacom digitizer how may fingers does the touch screen recognize?

---

### Post by tristram60 on 2011-04-02
I am using ubuntu maverick.  When I am in windows 7 or ubuntu the touchscreen works with my fingers but only recognizes one finger at a time (resistive touchscreen).  If I manually rotate the screen the pen input gets thrown off.

---

### Post by Favux on 2011-04-02
Alright.  What you need to do is rotate the Wacom input tools like touch, eraser, and the stylus when you rotate the screen.  Usually you use a rotation script and set it up in a launcher.  That will rotate the screen and the input tools for you.  See the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830").  Ask if you have questions.  A method 1 script will work for you and maybe some of the other methods.

---

### Post by tristram60 on 2011-04-02
I have seen you reccomend that to people before I just dont really know what to do.  I tried to do it once but all it did was get my screen stuck rotating sideways.  Could you do a really easy step by step on how to do that?

---

### Post by Favux on 2011-04-02
Sure.  The stylus, eraser, and touch are working for you correct?

If so just enter in a terminal:
```
xinput list
```
and post the output.  That will give us the "device names" of the input tools.

Is there any particular way you want the screen to rotate when in tablet mode?  Portrait to the right say?

---

### Post by tristram60 on 2011-04-02
Just so were clear, the stylus works when I am just clicking around with it and the right click works but I have no idea if eraser works since I cant find a linux program that supports it.  Stylus doesnt work very well when screen is manually rotated using the monitors tool under preferences.  Also, I wish to rotate the screen so that after I put my computer into tablet mode the screen is facing toward me.  Upside down in regular mode.  I can't boot up into ubuntu right now for some reason but I think I know the problem... Stand by :D

---

### Post by Favux on 2011-04-02
Eraser will work in programs that support it like Gimp, Xournal, Inkscape if you configure the support for it.  With Gimp and Inkscape you configure the extended input devices as shown in some screen shots near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

Right you don't want to use the monitor tool unless you use something like Tom Jaeger's wacomrotate (method 3).  You want to rotate the screen and input tools together to the same orientation.

OK, I think you are saying you want to rotate it to landscape not portrait when in tablet mode so you would want the screen inverted.  Correct?

---

### Post by tristram60 on 2011-04-02
That is correct, I want the screen to be inverted and the input tools to rotate with the screen.  Which method should I use?

---

### Post by tristram60 on 2011-04-02
sorry to post again but I typed the code into the terminal and this is what I got


```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=11	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet eraser              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet touch               	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Serial Wacom Tablet stylus              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; HID 1241:1166                           	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; CNA7157                                 	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Toshiba input device                    	id=16	[slave  keyboard (3)]

```

---

### Post by Favux on 2011-04-02
Right click on your Desktop and choose Create Document.  Copy and paste the entire contents in the box below into it.
```
#!/bin/sh 

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    normal) 
#    -rotate to inverted 
    xrandr -o inverted 
    xsetwacom set "Serial Wacom Tablet stylus" rotate HALF
    xsetwacom set "Serial Wacom Tablet touch" rotate HALF
    xsetwacom set "Serial Wacom Tablet eraser" rotate HALF
    ;; 
    inverted) 
#    -rotate to normal 
    xrandr -o normal 
    xsetwacom set "Serial Wacom Tablet stylus" rotate NONE 
    xsetwacom set "Serial Wacom Tablet touch" rotate NONE 
    xsetwacom set "Serial Wacom Tablet eraser" rotate NONE 
    ;; 
esac
```
Save the file as say *rotateM780.sh*.  Then right click on the new file and choose Properties.  In the permission tab check the box for *Allow executing files as program*.

Now right click on the Desktop and choose Create folder and call it *bin*.  Drag rotateM780.sh into the new bin folder.  Then open Places and drag the bin folder onto /home/yourusername.  Where yourusername is your user name of course.  The bin folder should appear there.  You've created a bin (binary) directory to store scripts in.

Now right click on the Desktop and choose Create Launcher.  Give it a name.  In the Command box enter the path to rotateM780.sh, i.e. /home/yourusername/rotateM780.sh.  Choose an icon if you want and Save.  Now your script will be run if you double click on the Launcher.  If you drag the Launcher into a panel it will only take a single click to run the script.

---

### Post by tristram60 on 2011-04-02
YOU ARE A GOD!!!! Thank you so much!  Also, do you recommend any programs for taking notes that are similar to microsoft onenote?

---

### Post by Favux on 2011-04-03
You're welcome.

You'll want to look at Xournal and Jarnal.

You'll also want CellWriter and want to look at EasyStroke.

---

### Post by jcracken on 2011-04-03
Hi, I go too the same school as tristram60, and he referred me to this page. I have the same laptop, but it doesn't work for me? I followed your instructions exactly, but when i run it, even without a launcher, it doesn't work. If I run it when I'm in tablet mode, nothing happens. If I run it in a terminal, it makes the computer think that the screen is upside down, but the screen is in the same orientation and even changing it it is still the same. Am I doing anything wrong?

---

### Post by Favux on 2011-04-03
Hi jcracken,

I don't quite follow you but...

I'm assuming your stylus, eraser, and touch work.  What version/release of Ubuntu are you using?

First make sure the script is executable:
> Then right click on the new file and choose Properties. In the permission tab check the box for *Allow executing files as program*.

Second check that the "device names" for your input tools are the same.  Enter in a terminal:
```
xinput list
```
and post the output.

---

### Post by jcracken on 2011-04-03
> **Favux said:**
> Hi jcracken,

I don't quite follow you but...

I'm assuming your stylus, eraser, and touch work.  What version/release of Ubuntu are you using?

First make sure the script is executable:


Second check that the "device names" for your input tools are the same.  Enter in a terminal:
```
xinput list
```
and post the output.

It is executable, and, as you said, the touch, stylus, and eraser all work. I'm using 10.10, and when I put xinput list in a terminal, I got the same as tristram60, save for the HID device with id 17. I confirmed with him that that's a usb mouse, so I doubt that's the reason it isn't working.

---

### Post by Favux on 2011-04-03
OK, what do you see when you enter just an xsetwacom command in a terminal?:
```
xsetwacom set "Serial Wacom Tablet stylus" rotate HALF

```
Does it work or do you get errors in the output?

---

### Post by jcracken on 2011-04-03
> **Favux said:**
> OK, what do you see when you enter just an xsetwacom command in a terminal?:
```
xsetwacom set "Serial Wacom Tablet stylus" rotate HALF

```
Does it work or do you get errors in the output?
It works, and now when I rotate the screen it works correctly. Even the eraser works, and the right click button too. However, when in normal mode, though, the stylus is messed up. Maybe it can be fixed by setting two different binaries, one for in tablet mode, and one for in laptop mode.

---

### Post by Favux on 2011-04-03
Right, you would have to repeat the xsetwacom command but use for the value of the *Rotate* parameter NONE.

So the script should work for you.  Make sure you copied it exactly and the whole contents.  If that isn't it try changing the line:
```
#!/bin/sh
```
to
```
#!/bin/bash
```

---

### Post by jcracken on 2011-04-03
> **Favux said:**
> Right, you would have to repeat the xsetwacom command but use for the value of the *Rotate* parameter NONE.

So the script should work for you.  Make sure you copied it exactly and the whole contents.  If that isn't it try changing the line:
```
#!/bin/sh
```
to
```
#!/bin/bash
```
Ok, so I rechecked the file and it is exact. However, I tried it both with sh and bash and there seems to be no difference. The command I ran before still works, meaning that in laptop mode the stylus is messed up and in tablet mode the stylus works. Should I restart?

---

### Post by Favux on 2011-04-03
I would.  See if that shakes something up.  Xsetwacom commands are runtime.  They don't last through an X restart or reboot or hotplug.

Right now what you are describing to me doesn't make much sense.  If the xsetwacom command works the script should.  Try running the script in a terminal after you've changed to the /bin directory and see if it throws errors, *./yourscriptname.sh*.

---

### Post by jcracken on 2011-04-04
> **Favux said:**
> I would.  See if that shakes something up.  Xsetwacom commands are runtime.  They don't last through an X restart or reboot or hotplug.

Right now what you are describing to me doesn't make much sense.  If the xsetwacom command works the script should.  Try running the script in a terminal after you've changed to the /bin directory and see if it throws errors, *./yourscriptname.sh*.
Well, restarting didn't work, and running it through a terminal didn't either. It didn't recognize that the file was there at all. It gave me a "no such file or directory" error.

---

### Post by vedovatti on 2011-06-16
Hi

I just updated to Natty. I have a touchsmart tm2. I followed the guide to rotate and always used the method 4. 

On the Ubuntu 10.10 it work without problems, but in 11.04 the rotation is inverted. When is in portrait mode the rotation goes instead of left, the pointer appears on the right and the same up and down.

Any ideas how to solve this?

Thanks

---

### Post by Favux on 2011-06-16
Hi vedovatti,

That's a bug in Natty's default xf86-input-wacom-0.10-11.  It's been fixed in later versions so you can update your xf86-input-wacom.  Use the [Bamboo P&T HOW]("http://ubuntuforums.org/showthread.php?t=1515562") TO part II.

---

### Post by vedovatti on 2011-06-17
Favux, thanks you really make magic :guitar: with the tablets PC! It worked! Is the second time you help me! :)

---


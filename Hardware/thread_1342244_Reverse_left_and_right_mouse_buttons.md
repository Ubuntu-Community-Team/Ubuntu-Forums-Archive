---
title: "Reverse left and right mouse buttons"
date: 2009-11-30
forum: Hardware
---

### Post by opaygo on 2009-11-30
Hello

I am using a wacom mouse that came with the tablet and it is working perfectly in Xubuntu 9.10. The only problem is the left mouse button does work very well then the right button.

So is there anyway to reverse the right and left buttons so I can click with right and right-click with the left?

Thanks for your time,

---

### Post by SeriousName on 2009-11-30
You might be able to do this with wacomcpl. It's a program in the package wacom-tools. I can't check right now to see if it can do what you're asking, but I remember it does have some options for things like that.

---

### Post by opaygo on 2009-11-30
> **SeriousName said:**
> You might be able to do this with wacomcpl. It's a program in the package wacom-tools. I can't check right now to see if it can do what you're asking, but I remember it does have some options for things like that.

When I run "wacomcpl" from the terminal, It can not find any devices.

I installed my wacom by following[ this guide]("https://help.ubuntu.com/community/Wacom")

EDIT: I am using wacom graphire 4.

---

### Post by MrQuincle on 2009-12-01
> **opaygo said:**
> When I run "wacomcpl" from the terminal, It can not find any devices.

I installed my wacom by following[ this guide]("https://help.ubuntu.com/community/Wacom")

EDIT: I am using wacom graphire 4.

It is not possible to use wacomcpl anymore.

Use this instead:
```
xinput --list
```

For example:
```

xinput --list | grep -B 1 -A 7 tylus
	"Wacom Graphire4 6x8"	id=2	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256

```

And then to set the thing relative (you see that I use "Wacom Graphire4 6x8" from above):
```

xsetwacom set "Wacom Graphire4 6x8" mode relative

```
It works directly.

You have to figure out how to exchange the buttons, but you are on the right track now. ;-)

---

### Post by MrQuincle on 2009-12-01
Some other options, like you see it is added to .xinitrc to remain valid over reboots.
```

cat ~/.xinitrc
echo 'xsetwacom set "Wacom Graphire4 6x8" mode relative' >> ~/.xinitrc
echo 'xsetwacom set "Wacom Graphire4 6x8 pad" RelWDn "key core Up"' >> ~/.xinitrc
echo 'xsetwacom set "Wacom Graphire4 6x8 pad" RelWUp "key core Down"' >> ~/.xinitrc
cat ~/.xinitrc

```

---

### Post by MrQuincle on 2009-12-01
Okay final answer: :-)

:popcorn:

Read your current settings:
```
xsetwacom get "Wacom Graphire4 6x8" button1 button2 button3
```

Now, to inverse you probably need to do:
```

xsetwacom set "Wacom Graphire4 6x8" button1 "button 1"
echo "The following are reversed because you like it that way:"
xsetwacom set "Wacom Graphire4 6x8" button2 "button 3"
xsetwacom set "Wacom Graphire4 6x8" button3 "button 1"

```
About the first field: button1 is the actual tip of the stylus, button2 is the button near the tip of the stylus, button3 is the second button a bit further removed from the tip.

About the second field: "button 3" is the popup menu you get with right mouse click, "button 1" is the left mouse button, you can select text with it, "dblclick 1" has the same behaviour in my case.

Oh, and last thing "button 2" has the same functionality as the middle button on a mouse. I didn't use it in the example. But it does paste text. Normal configuration is of course:
```

xsetwacom set "Wacom Graphire4 6x8" button1 "button 1"
xsetwacom set "Wacom Graphire4 6x8" button2 "button 2"
xsetwacom set "Wacom Graphire4 6x8" button3 "button 3"

```

---

### Post by Favux on 2009-12-01
Hi,

With the right .fdi you can use wacomcpl.  Please see the .fdi in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

Or you can add it to the wacom.fdi:
```
<merge key="input.x11_options.Button2" type="string">3</merge>
<merge key="input.x11_options.Button3" type="string">1</merge>
```

---

### Post by opaygo on 2009-12-01
Thanks for all of your help

This forum quicker then I thought! :D

---

### Post by Simian Man on 2009-12-01
Can't you just launch Preferences->Mouse and select "Left Handed" for your mouse?

---

### Post by opaygo on 2009-12-01
I tried that but the left and right hand settings just change the way the mouse's wheel moves. It doesn't change the left and right buttons.

---

### Post by Simian Man on 2009-12-01
> **opaygo said:**
> I tried that but the left and right hand settings just change the way the mouse's wheel moves. It doesn't change the left and right buttons.

Strange.  For me, it reverses the buttons but does nothing to the mouse wheel.  Well at least you got it fixed.

---

### Post by opaygo on 2009-12-01
> ```

xsetwacom set "Wacom Graphire4 6x8" button1 "button 1"
echo "The following are reversed because you like it that way:"
xsetwacom set "Wacom Graphire4 6x8" button2 "button 3"
xsetwacom set "Wacom Graphire4 6x8" button3 "button 1"

```
I managed to set my button 1 and my button 3.
But when I close my terminal the settings remain the same

---

### Post by Favux on 2009-12-01
Hi opaygo,

Are you using wacomcpl's .xinitrc?  Or have you made a script that you can run at boot?  To see what I'm talking about look at "Section 3: Calibrating your Tablet" in this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by opaygo on 2009-12-01
> **opaygo said:**
> I managed to set my button 1 and my button 3.
But when I close my terminal the settings remain the same

Oh wait it configured my pen.
Let me try"Wacom Graphire4 cursor"

Oh and Favux I am using MrQuincle method because it is working for me.
I might try your method later.

---

### Post by opaygo on 2009-12-01
Thanks I finally got everything working.

---

### Post by MrQuincle on 2009-12-03
> **Favux said:**
> Hi opaygo,

Are you using wacomcpl's .xinitrc?  Or have you made a script that you can run at boot?  To see what I'm talking about look at "Section 3: Calibrating your Tablet" in this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Yes, if you want the things to be still valid over a reboot, you need to chmod a+x .xinitrc and put it in Systems - Preferences - Startup Applications (just refer to /home/YOURUSERNAME/.xinitrc).

However, all this is far simpler than trying to fix wacomcpl. I have respect for that post! It's a monster. :P

---


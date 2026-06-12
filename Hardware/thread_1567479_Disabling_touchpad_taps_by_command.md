---
title: "Disabling touchpad taps by command"
date: 2010-09-03
forum: Hardware
---

### Post by jjjjeremy on 2010-09-03
I would like to know how to turn off touchpad taps by command. I turn "click by tapping" off and on throughout the day, depending on what I am doing, and I would like to make it into a keyboard shortcut but I don't know the command.

Thanks for the help

---

### Post by jjjjeremy on 2010-09-04
bump

---

### Post by 73ckn797 on 2010-09-04
Have you looked in the Configuration Editor? If you do not have that enabled under Applications/System Tools try opening terminal and entering: ```
gconf-editor
```From there go to apps/metacity/global-keybindings. You may be able to configure a keyboard shortcut there. I have not messed around with it much but it might do what you are wanting.

---

### Post by jjjjeremy on 2010-09-04
Nothing, thanks for the help though.

---

### Post by jjjjeremy on 2010-09-05
bump

---

### Post by sam_scott89 on 2010-09-05
Ok, a bit of info to start with will help.

```
xinput list
```

To find a list of your devices. 

For me this returns:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93 eraser                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93                          	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 93                          	id=13	[slave  pointer  (2)]
[COLOR="Red"]&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)][/COLOR]
&#9116;   &#8627; Macintosh mouse button emulation        	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; CNF7060                                 	id=10	[slave  keyboard (3)]

```

With the highlighted line being the one I want.

Then ```
xinput list-props <device id>
```

e.g. ```
xinput list-props "SynPS/2 Synaptics TouchPad"
```
or
```
xinput list-props 15
```

To bring up a list of properties you can set.

For example, with my Synaptics touchpad I can issue the command:

```
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap Time" 0
```

To turn off taps, and

```
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Tap Time" 180
```

To restore it (based on my existing config values).

Note: you can also replace the device names with the id. 

```
xinput set-prop 15 296 0
``` also worked, though I'm not sure if there is any issue with new devices added.

Let me know if that works. Then you can write a script to detect if it's 'on' or 'off' based on that value and switch it to the other.

---

### Post by jjjjeremy on 2010-09-05
Hi, I got to list-props, then changed the tapping in the GUI from no tap clicking to tap clicking, and noticed this change in list-props


```
Synaptics Off (285):	1

and

Synaptics Tap Action (289):	0, 0, 0, 0, 0, 0, 0

```

became

```
Synaptics Off (285):	1

and

Synaptics Tap Action (289):	2, 3, 0, 0, 1, 3, 2
```

I tried changing it back through terminal, but nothing changed after entering ```
 xinput set-prop 10 285 1 
```, but the numbers after "tap action" did change.

Nevertheless, none of the commands I tried worked.

---

### Post by jjjjeremy on 2010-09-05
I got it

```
xinput set-prop 10 289 0, 0, 0, 0, 0, 0, 0
```

turns it off, and 

```
xinput set-prop 10 289 2, 3, 0, 0, 1, 3, 2
```

turns it back on again.

Now, how about writing that script!

---

### Post by jjjjeremy on 2010-09-05
For the moment, I have the two separate commands set to two separate shortcuts. How do I write the script?

---

### Post by sam_scott89 on 2010-09-05
For future reference,

```
xinput watch-props <...>
``` is also quite useful, will wait for property changes and print to the terminal/stdout. 

But yes, this changes the line that you showed.

As for the script.

Now, these values you are changing stand for:

RT, RB, LT, LB, F1, F2, F3

Right top, right bottom, left top, left bottom, finger 1,2,3.
[(Source)]("http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html")

Technically speaking we can change any of these, but we'll just keep it simple.

Pattern matching and this kind of thing isn't my strong point.. but:
```
xinput get-props <device> | grep <property> 
```
returns the relevant line.

so we can do something like this:

```
#!/bin/bash

device=10
property=123
mode="$(xinput list-props $device | grep $property | cut -d',' -f5)"

if [ $mode -eq "1" ] ;
then
xinput set-props $device $property 0, 0, 0, 0, 0, 0, 0
else
xinput set-props $device $property 2, 3, 0, 0, 1, 3, 2
fi
```

So this basically checks that the 5th argument (finger 1) is enabled, i.e. set to 1 and changes if not

save it as something, 
```
chmod +x <filename>
```
to make it runnable.

I'm sure there's a much more elegant script that could be written... but it's functioning.

---

### Post by vezolmi on 2011-05-13
The solution can be achieved without scripts:
+ While you hold the ALT key push F2
+ Put gnome-keybinding-properties and push enter key
+ Click on Add
+ In Name put mouse_clicks_off
+ In Command put synclient MaxTapTime=0
+ Click on Apply
+ Click on Disabled under Shortcut
+ Hold CTRL key and push 7
+ Click on Add
+ In Name put mouse_clicks_on
+ In Command put synclient MaxTapTime=180
+ Click on Apply
+ Click on Disabled under Shortcut
+ Hold CTRL key and push 8
+ Click on Close

Now CTRL+7 disables mouse clicks with touchpad and CTRL+8 enables them.

Instead of synclient MaxTapTime=0 we can use synclient TapButton1=0 TapButton2=0 TapButton3=0
And instead of synclient MaxTapTime=180 we can use synclient TapButton1=1 TapButton2=3 TapButton3=2
We can use also/instead the xinput commands shown in previous posts.

All these commands can be run from the Run dialog (ALT+F2), without using scripts nor gnome-keybinding-properties.

NB: in the previous post, instead of
```
xinput get-props <device> | grep <property>
```it should say
```
xinput list-props <device> | grep <property>
```

---

### Post by vezolmi on 2011-05-14
I've tried the script by sam_scott89. It works if you solve a couple of problems:

a) Where it says device you have to put the number of your particular case (10 for jjjjeremy, 12 for me). The same for property (289 for jjjjeremy, 313 for me).
b) It says twice:
```
xinput set-props
```But it should say:
```
xinput set-prop
```So the code for jjjjeremy should be:
```

#!/bin/bash

device=10
property=289
mode="$(xinput list-props $device | grep $property | cut -d',' -f5)"

if [ $mode -eq "1" ] ;
then
xinput set-prop $device $property 0, 0, 0, 0, 0, 0, 0
else
xinput set-prop $device $property 2, 3, 0, 0, 1, 3, 2
fi

```For me is:
```

#!/bin/bash

device=12
property=313
mode="$(xinput list-props $device | grep $property | cut -d',' -f5)"

if [ $mode -eq "1" ] ;
then
xinput set-prop $device $property 0, 0, 0, 0, 0, 0, 0
else
xinput set-prop $device $property 2, 3, 0, 0, 1, 3, 2
fi

```You can place the script inside /usr/bin (as administrator or root) so you can call it from a keyboard shortcut (gnome-keybinding-properties)

---

### Post by jjjjeremy on 2011-05-22
Thanks for post #11. Works for me!

---

### Post by vezolmi on 2011-05-22
Congratulations!

GNOME can do this via GConf. This makes an easier script possible, without having to make previous inquiries:

```

#!/bin/bash

mode="$(gconftool-2 -g /desktop/gnome/peripherals/touchpad/tap_to_click)"

if [ $mode == "true" ] ;
then
gconftool-2 -s -t bool /desktop/gnome/peripherals/touchpad/tap_to_click false
else
gconftool-2 -s -t bool /desktop/gnome/peripherals/touchpad/tap_to_click true
fi

```NB: you can place the script wherever you want, but if you do it normally you have to put the location of it before its name in gnome-keybinding-properties. If you place it inside  /usr/bin (as administrator or root) you don't need to put the location, just the name.

NB2: The text "Instead of synclient MaxTapTime=0 we can use synclient TapButton1=0 TapButton2=0 TapButton3=0", to be more precise should be:
Instead of synclient MaxTapTime=0 we can use synclient RTCornerButton=0 RBCornerButton=0 TapButton1=0 TapButton2=0 TapButton3=0

NB3: The text "And instead of synclient MaxTapTime=180 we can use synclient TapButton1=1 TapButton2=3 TapButton3=2", to be more precise should be:
And instead of synclient MaxTapTime=180 we can use synclient RTCornerButton=2 RBCornerButton=3 TapButton1=1 TapButton2=3 TapButton3=2

---


---
title: "Two finger Scrolling on Dell M1530 XPS, Can any one do it?"
date: 2008-10-24
forum: Hardware
---

### Post by vbabiy on 2008-10-24
The title explains my question, has any one been able to get two finger scrolling to work on Ubuntu 8.04 or 8.10 with the DELL XPS M1530?

---

### Post by htrex on 2008-10-26
Dell XPS M1530 ships with an ALPS touchpad that doesn't seem to support two finger recognition but....

Be sure to have 

```
    Option         "SHMConfig" "true"
```

in your /etc/X11/Xorg.conf InputDevice section and type

```
synclient -m 10 output
```

if you touch the pad now can see current pad values on the terminal.

Please note how on the fifth column (f) you always get 1 (finger) despite how many fingers you put on the touchpad.

Anyway if you look at the fourth column (z) you can see that actual pressure values change from 75 to 90 when using only one finger to > 90 when using 2 fingers. 

Then add the following options to Xorg.conf InputDevice section

```

    Option         "VertTwoFingerScroll"   "1"
    Option         "HorizTwoFingerScroll"  "1"
    Option         "EmulateTwoFingerMinZ"  "90"

```

restart X and enjoy two finger scrolling.

bye

---

### Post by zdux0012 on 2008-12-07
Although you have a very descriptive subject please explain to me what you mean by two fingers?

Is it that the touch pad can detect two fingers such as the iphone. A feature which is uncommon in touch pads, or are you talking about horizontal scrolling?

---

### Post by masterclam on 2008-12-12
well, this took me a few months of looking around to finally get the solution

First, open a terminal and ```
sudo gedit /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```

find ```
<match key="info.product" contains="AlpsPS/2 ALPS">
```

and type ```
<merge key="input.x11_options.SHMConfig" type="string">On</merge>
	<merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">90</merge>
	<merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
	<merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
```

above the </match>

the SHMConfig allows you to change settings on the fly and use the synclient and syndaemon functions. The EmulateTwoFingerMinZ sets the minimum pressure applied to the touchpad to emulate two fingers to 90 (it is almost impossible to get that high with one finger, but when you put two fingers on in the right place relative to each other it automatically set to above that). Vert and Horiz twofingerscroll set to 1 turns those on. If it seems like this doesnt work after you have put those lines in and restarted, open your terminal and type ```
synclient -m 10
``` this will give you the input info for your touchpad. play around with two fingers in different locations until the fourth column (z) registers above 90 (this usually requires your fingers to be in a horizontal line, close together. Just play around until it works)

Good Luck!

---

### Post by damis648 on 2008-12-13
Good suggestion, but I would suggest using 100 instead of 90; just one finger seems to trigger it much too often.

---

### Post by htrex on 2009-01-24
when upgraded from Hardy to Intrepid I've found my xorg.conf custom parameters were commented and stopped working as now they must be on HAL... but couldn't figure out where the new configuration file is.

thanks to masterclam for pointing this.

---

### Post by warrenis1234 on 2009-03-04
so this worked absolutely perfect on this toshiba laptop i had, but then after accidentally kneeling on it, i used the excuse to upgrade to an asus x83v.  

only problem is that the touchpad isnt pressure sensitive like the other, it responds to movement.  What this means is that although synclient -m 10 does show some pressure, it hovers in the 50 area and i have to press hard on it to even get it to 65.

there HAS to be a way to get 2 finger scrolling using movement and not pressure.  any ideas?  it would be great if this has been figured out already

---

### Post by warrenis1234 on 2009-03-05
> **masterclam said:**
> well, this took me a few months of looking around to finally get the solution

First, open a terminal and ```
sudo gedit /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```

find ```
<match key="info.product" contains="AlpsPS/2 ALPS">
```

and type ```
<merge key="input.x11_options.SHMConfig" type="string">On</merge>
	<merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">90</merge>
	<merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
	<merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
```

above the </match>

the SHMConfig allows you to change settings on the fly and use the synclient and syndaemon functions. The EmulateTwoFingerMinZ sets the minimum pressure applied to the touchpad to emulate two fingers to 90 (it is almost impossible to get that high with one finger, but when you put two fingers on in the right place relative to each other it automatically set to above that). Vert and Horiz twofingerscroll set to 1 turns those on. If it seems like this doesnt work after you have put those lines in and restarted, open your terminal and type ```
synclient -m 10
``` this will give you the input info for your touchpad. play around with two fingers in different locations until the fourth column (z) registers above 90 (this usually requires your fingers to be in a horizontal line, close together. Just play around until it works)

Good Luck!

masterclam, emulateTwoFingerMinZ sets it for pressure.. what makes it so that it is specifically pressure?  

Is there a way to change it so that it is dependent on another factor that can be found in synclient, like finger width?

does anyone know

---

### Post by warrenis1234 on 2009-03-05
i'm actually trying to do it by changing emulate... to EmulateTwoFingerMinW.   i was hoping someone would give me confirmation on this being a good idea before i did it cause God knows i've F'ed up my ubuntu too many times already.   oh well, i cant wait

---

### Post by warrenis1234 on 2009-03-06
Didnt work by the way.   Sucks that no one is paying attention to this thread anymore

---

### Post by Humphreybas on 2009-04-27
I need to alter the EmulateTwoFingerMinZ too.

I have a toshiba u400 and the touchpad doesn't respond to multifinger input (f=0 or 1 but not 2) but the z ("force") is +/- 64 with one finger and 59 with two (don't ask why).
But the w (width of the touch) is 4 for one finger and 15 for two. That would be an excellent criterium to test.

Isn't it possible to alter the synaptics driver like they did ([http://ubuntuforums.org/showpost.php?p=639943&postcount=7](http://ubuntuforums.org/showpost.php?p=639943&postcount=7)) when TwoFingerScroll wasn't standard option. We just need to add a parameter EmulateTwoFingerMin**W**
I myself wouldn't know how to start.. anybody else?

---

### Post by nexxus07 on 2009-05-11
After a morning of trying I finally have my AlpsPS/2 ALPS DualPoint TouchPad working with two finger scrolling on my Dell Latitude E6400 / E6500 .. Here is my .fdi file which I put into /etc/hal/fdi/policies/

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
        <match key="info.product" string="DualPoint Stick">
                <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
                <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
                <merge key="input.x11_options.EmulateWheelTimeout" type="string">200</merge>
        </match>
        <match key="info.product" string="AlpsPS/2 ALPS DualPoint TouchPad">
                <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
                <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
                <merge key="input.x11_options.EmulateTwoFingerMinZ" type="string">90</merge>
        </match>
        <match key="input.x11_driver" string="synaptics">
                <merge key="input.x11_options.SHMConfig" type="string">True</merge>
        </match>
  </device>
</deviceinfo>
```

I think the SHMConfig can be disabled again I just put it in there so I could use synclient -m 100 to track input.
My model has also a Stick, the options under DualPoint Stick are to allow for wheel scrolling when holding down the middle mouse button.

These settings first were not working because I didn't declare the xml document correctly. If it is not working for you check in your /var/log/Xorg.0.log for messages regarding your settings. You should see customized options being applied and if not there is probably something wrong in your .fdi file.

```

...
(**) Option "SHMConfig" "True"
(II) ALPS touchpad detected: AlpsPS/2 ALPS DualPoint TouchPad. Applying customised settings...
(**) Option "EmulateTwoFingerMinZ" "90"
(**) Option "VertTwoFingerScroll" "1"
(**) Option "HorizTwoFingerScroll" "1"
...

```

---


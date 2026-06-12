---
title: "Can't disable touchpad in ubuntu 10.10 on asus g72gx"
date: 2010-10-10
forum: Hardware
---

### Post by muddymind on 2010-10-10
Hi!

I can't disable the touchpad in ubuntu on my asus g72gx laptop. There is no option in preferences->mouse like in older versions of ubuntu and the disable touchpad button on the laptop doesn't work also. Even if I try 

> synclient TouchpadOff=1

it will remain on :S Is there a way to disable/enable it? 

thanks in advance ;)

---

### Post by muddymind on 2010-10-11
anyone?

---

### Post by zeating on 2010-10-11
Same problem, asus k50id 

you can try this in terminal 
```
sudo modprobe -r psmouse

```
to enable ```
sudo modprobe psmouse
```

---

### Post by muddymind on 2010-10-12
> **zeating said:**
> Same problem, asus k50id 

you can try this in terminal 
```
sudo modprobe -r psmouse

```
to enable ```
sudo modprobe psmouse
```

Lol! that's what I call to cut the problem from the root - literally :lolflag:

but it solves the problem for now ;) thanks for the tip :)

---

### Post by samn76022 on 2010-10-25
> **muddymind said:**
> Hi!

I can't disable the touchpad in ubuntu on my asus g72gx laptop. There is no option in preferences->mouse like in older versions of ubuntu and the disable touchpad button on the laptop doesn't work also. Even if I try 



it will remain on :S Is there a way to disable/enable it? 

thanks in advance ;)

Probably am not a lot of help for you, but your terminal command worked for me on my Lenova Laptop. Thanks for the information. Now I can type without shooting the cursor all over. I tried the commands listed down the page, but for whatever reason, they didn't work. Glad to get the touchpad disabled.In Ubuntu 9.04 you simply go to Mouse Properties and click on Touchpad and disable. I just installed 10.10 a few days ago and am glad to find your post. 
      synclient TouchpadOff=1

---

### Post by hawthornso23 on 2010-11-23
Sorry to reopen this old thread, however a less nuclear option involves the following commands


```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 0
```to disable the touchpad, and 

```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 1
```to enable it again. I have these commands associated with keyboard shortcuts.

You don't need sudo and you don't have to mess with the kernel if you do it this way.

---

### Post by jangari on 2011-01-01
> 

```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 0
```

to disable the touchpad, and

```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 1
```

to enable it again. I have these commands associated with keyboard shortcuts.

You don't need sudo and you don't have to mess with the kernel if you do it this way. 
This hasn't worked for me. Running xinput list returns this:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; ImPS/2 Generic Wheel Mouse              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Mouseemu virtual mouse                  	id=17	[slave  pointer  (2)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP Webcam-50                            	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=15	[slave  keyboard (3)]
    &#8627; Mouseemu virtual keyboard               	id=16	[slave  keyboard (3)]
```
And I've tried disabling each device under 'pointer', and the only one that worked was 17, but it also disabled an external USB mouse. 

Using modprobe to disable the mouse as suggested above worked, but had severe unintended consequences when re-enabling it.

I'm sick of tapping my unfortunately positioned trackpad with my thumb every couple of lines. Any other suggestions?

Ubuntu 10.10 on HP Pavilion dm1

---

### Post by Colper on 2011-02-13
Thank you for posting this thread. It works!  

Is there a way that I can make this command permanent?

I use a USB mouse 99% of the time, so there is really no need for my touch pad.  


FYI, I'm new to the Linux Community, and loving it :-) thanx for the help!

---

### Post by yanike on 2011-02-21
Thanks to [**ubuntuguide.net**]("http://www.ubuntuguide.net")

Touchpad-Indicator is a small indicator provides quickly enable and disable touchpad functionality in Ubuntu laptop and netbook. It is written by Lorenzo Carbonell and only supported in Ubuntu 10.10 Maverick now.

To install it, open up a terminal from Applications -> Accessories and run following three commands:

```

sudo add-apt-repository ppa:lorenzo-carbonell/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator

```

After installation, open the indicator from Applications -> Accessories -> Touchpad Indicator and set your touchpad in top-right via this icon:

[img]http://ubuntuguide.net/wp-content/uploads/2010/11/Touchpad-Indicator.png[/img]

---

### Post by TedinOz on 2011-05-13
> **yanike said:**
> Thanks to [**ubuntuguide.net**]("http://www.ubuntuguide.net")

Touchpad-Indicator is a small indicator provides quickly enable and disable touchpad functionality in Ubuntu laptop and netbook. It is written by Lorenzo Carbonell and only supported in Ubuntu 10.10 Maverick now.

To install it, open up a terminal from Applications -> Accessories and run following three commands:

```

sudo add-apt-repository ppa:lorenzo-carbonell/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator

```

After installation, open the indicator from Applications -> Accessories -> Touchpad Indicator and set your touchpad in top-right via this icon:

[img]http://ubuntuguide.net/wp-content/uploads/2010/11/Touchpad-Indicator.png[/img]

This was great! Indicator installed and working perfectly! Thanks :)

---

### Post by MPacheco on 2011-06-10
Hello All,

New user here.  Like the others, I'm having the same touchpad issue with my Asus (A52F), but have Ubuntu 11.04.  Is Maverick a flavor of Ubuntu and how do I know if I have it to see if this solution will work on my laptop?

Thank you, in advance, for helping another user make the switch.

- MP

---

### Post by puterg33k on 2011-06-18
I tried to install this, but it always tells me:


root@ZEN:~#sudo add-apt-repository ppa:lorenzo-carbonell/atareao
Error: can't find signing_key_fingerprint at [https://launchpad.net/api/1.0/~lorenzo-carbonell/+archive/atareao](https://launchpad.net/api/1.0/~lorenzo-carbonell/+archive/atareao)


Any ideas? Thanks for the help. :p

---

### Post by GuniAta on 2011-07-10
I couldn't install it either.. same problem.
however, i found another solution - go to software center and install "Pointing devices". nice GUI tool that allows you to enable and disable the touchpad. 

but still - if anyone can tell me how to enable the keyboard shortcut that controls the touchpad it would be great!!

---

### Post by djkadu on 2011-08-14
> **hawthornso23 said:**
> Sorry to reopen this old thread, however a less nuclear option involves the following commands


```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 0
```to disable the touchpad, and 

```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 1
```to enable it again. I have these commands associated with keyboard shortcuts.

You don't need sudo and you don't have to mess with the kernel if you do it this way.

Great tip. Had to adapt it to use the name of my device and it worked fine.

Thanks
Kadu

---

### Post by djkadu on 2011-08-14
Quick script to toggle the trackpad on/off
Just change the value of DEVICE to match yours, save it to a file and bind a key to it

```

#!/bin/sh
DEVICE="ImPS/2 ALPS GlidePoint"
if [ `xinput list-props "$DEVICE" |awk '/Device Enabled/ { print $4}'` -eq 0 ]; then
        xinput --set-prop "$DEVICE" "Device Enabled" 1
else
        xinput --set-prop "$DEVICE" "Device Enabled" 0
fi


```Kadu

---

### Post by Insperatus on 2011-08-23
> **djkadu said:**
> Quick script to toggle the trackpad on/off
Just change the value of DEVICE to match yours, save it to a file and bind a key to it

```

#!/bin/sh
DEVICE="ImPS/2 ALPS GlidePoint"
if [ `xinput list-props "$DEVICE" |awk '/Device Enabled/ { print $4}'` -eq 0 ]; then
        xinput --set-prop "$DEVICE" "Device Enabled" 1
else
        xinput --set-prop "$DEVICE" "Device Enabled" 0
fi


```Kadu

Oh man this worked perfectly on my ASUS UL30VT running Ubuntu 10.10 64-bit.

 hawthornso23's commands worked as well.  With both of these solutions I just had to use my touchpad's own device name: ETPS/2 Elantech Touchpad

You can find your device name with:
```
xinput list
```
BTW I first tried a GUI approach with the suggested 'Pointing devices' program.  This seemed to work great until I realized the touchpad was somehow reenabling itself within under a minute.  I'm sure there's a reasonable explanation for that but after months of foiled typing I really felt like my touchpad was haunting me.  NO MORE!

THANKS to you all!!

---

### Post by Dmitko on 2011-09-05
> **hawthornso23 said:**
> 
```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 0
```to disable the touchpad, and 

```
xinput --set-prop "PS/2 Generic Mouse" "Device Enabled" 1
```to enable it again. I have these commands associated with keyboard shortcuts.

You don't need sudo and you don't have to mess with the kernel if you do it this way.

Did the job for me!

Attempting : 
```
 
sudo modprobe [-r]psmouse 
```  messed up mu laptop & ubuntu 11.04 - somehow disabled all input (keyboard & mouses)

A short shell script bound to a key combination is sufficient.
```
 
if 
    xinput list-props "ImPS/2 ALPS GlidePoint" | grep "Device Enabled" | grep 0
then  
    xinput --set-prop "ImPS/2 ALPS GlidePoint" "Device Enabled" 1
    echo MousePad enabled;
else 
    xinput --set-prop "ImPS/2 ALPS GlidePoint" "Device Enabled" 0
    echo MousePad disabled;
fi 

```Thank you for the help!

---

### Post by dano2 on 2011-09-08
> **GuniAta said:**
> I couldn't install it either.. same problem.
however, i found another solution - go to software center and install "Pointing devices". nice GUI tool that allows you to enable and disable the touchpad. 

but still - if anyone can tell me how to enable the keyboard shortcut that controls the touchpad it would be great!!

System -> Preferences -> Pointing Devices
Select Touchpad Off
Click OK
Touchpad still on!

---

### Post by dano2 on 2011-09-08
> **zeating said:**
> Same problem, asus k50id 

you can try this in terminal 
```
sudo modprobe -r psmouse

```
to enable ```
sudo modprobe psmouse
```

Thanks. That one worked for me :)

---

### Post by gsanders99 on 2011-10-27
I was able to set two keystroke combinations to turn the touchpad on and off.

First I found the device id number with xinput:

[IMG]http://www.gasanders.org/projects/xinput_touchpad.jpg[/IMG]

I opened System/Preferences/Keyboard Shortcuts, clicked Add and assigned this command to CTRL-F9:

xinput --set-prop 14 "Device Enabled" 0

[IMG]http://www.gasanders.org/projects/xinput_keyboard_shortcut.jpg[/IMG]

Then I clicked Add again and assigned this command to CTRL-Shift-F9:

xinput --set-prop 14 "Device Enabled" 1

Works for me.  :)

g

---

### Post by Peetii on 2011-12-07
> **djkadu said:**
> Quick script to toggle the trackpad on/off
Just change the value of DEVICE to match yours, save it to a file and bind a key to it

```

#!/bin/sh
DEVICE="ImPS/2 ALPS GlidePoint"
if [ `xinput list-props "$DEVICE" |awk '/Device Enabled/ { print $4}'` -eq 0 ]; then
        xinput --set-prop "$DEVICE" "Device Enabled" 1
else
        xinput --set-prop "$DEVICE" "Device Enabled" 0
fi


```Kadu

 Thanks Kadu,

Here below is my version of your mouse pad toggle script, that worked for me as of this date with my ASUS G72GX and LinuxMint 12 Lisa/Oneiric Ocelot:

```

#!/bin/sh

if 
    xinput --list "SynPS/2 Synaptics TouchPad" | grep -c "disabled"
then  
    xinput --set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 1
    echo MousePad enabled;
else 
    xinput --set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 0
    echo MousePad disabled;
fi


```I think this code construct is also partly from Dmitko, but I had to change it to work on my system.

-- Charles

---

### Post by JohnnyB98604 on 2011-12-10
> **dano2 said:**
> System -> Preferences -> Pointing Devices
Select Touchpad Off
Click OK
Touchpad still on!

I'm trying to get Pointing Devices to work...it's installed but I can't figure out how to launch it.  Obviously, I'm quite new to Ubuntu, so please be gentle.  I'm trying to find the right thread or my answer and this looks as close to any.

I go to "Dash Home" and type in "Pointing" and the only thing that comes up is the native "Mouse and Touchpad" settings (which are lacking in feature functionality).

Any advice or direction would be greatly appreciated.

---

### Post by Peetii on 2011-12-21
> **JohnnyB98604 said:**
> I'm trying to get Pointing Devices to work...it's installed but I can't figure out how to launch it.  Obviously, I'm quite new to Ubuntu, so please be gentle.  I'm trying to find the right thread or my answer and this looks as close to any.

I go to "Dash Home" and type in "Pointing" and the only thing that comes up is the native "Mouse and Touchpad" settings (which are lacking in feature functionality).

Any advice or direction would be greatly appreciated.



I just came across this software that is handy for mouse pad enable disable.  It is pretty nifty about letting you turn mouse-pad on/off, but it should be upgraded to show a red mouse pad icon when off and a green one when on, then its name will make more sense ... to me.  ;p

link:  [http://www.ubuntubuzz.com/2011/05/how-to-disable-enabletouchpad-in-ubuntu.html](http://www.ubuntubuzz.com/2011/05/how-to-disable-enabletouchpad-in-ubuntu.html)


-- Charles

---


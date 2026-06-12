---
title: "Ubuntu 11.04 with Gnome on Dell 6510: cannot disable touchpad"
date: 2011-05-13
forum: Hardware
---

### Post by vincegata on 2011-05-13
I cannot disable touchpad. If I go to mouse preferences, there is no Touchpad tab. 

I used this package but it does not install at all.

sudo add-apt-repository ppa:atareao/atareao
[FONT=&quot]sudo apt-get install touchpad-indicator[/FONT]

Do you have any other suggestions, please?

TIA!!

---

### Post by vincegata on 2011-05-13
This command:

sudo synclient TouchpadOff=1

gives me:

Couldn't find synaptics properties. No synaptics driver loaded?


Any other suggestions, please?

---

### Post by Joliea on 2011-05-25
I also have the same problem!

---

### Post by eyedeal on 2011-05-25
I own a DELL INSPIRON N5110. It uses Alps touchpad, and that's a problem because it's recognized as a mouse. So touchpad cannot be disabled and/or configured as a touchpad.

I'm not sure how to solve this issue, but it might be the real issue for you two as well.

If you do `xinput list` and see:

```
....
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                  	id=19	[slave  pointer  (2)]
....
```

it means you have the crappy ALPS touchpad.

---

### Post by d.burba on 2011-05-29
This is the script I use on my N5110 on every startup (in order to set correct touchpad state) and assigned it for touchpad enable/disable keyboard shortcut. Customize it for your needs as I did :)

---

### Post by vincegata on 2011-06-19
@d.burba, the script does not work on my Dell E6510 :(

Is there anything else, please?

---

### Post by alex.ukf on 2011-06-21
@d.burba thanks sooo much, it works on my dell n5110, and it was really pissing me off.
@vincegata i'm sure it has to be something very similar to this, but i'm sorry i can't help you.

alex

---

### Post by mikejonesey on 2011-06-22
@vincegata

try this;

```
#!/bin/bash
cd $HOME

function messageUser()
{
    if [ "$(which notify-send)" == "" ]; then
        echo "requires... libnotify-bin for messages..."
    elif [ "$1" == "on" ]; then
        notify-send -t 800 -i /home/mike/myicon.png "Touchpad enabled..." "mike reprogramed the calculator button :)"
    elif [ "$1" == "off" ]; then
        notify-send -t 800 -i /home/mike/myicon.png "Touchpad disabled..." "mike reprogramed the calculator button :)"
    fi
}

touchPadId=$(xinput list | grep -i synaptics | grep -i touch | grep PS | cut -d "=" -f 2 | cut -b 1-2)
if [ "$touchPadId" == "" ]; then
    echo "Unable to identify device id..."
else
    if [ -a ".mike-touchPadOnOff" ]; then
        rm -rfv ".mike-touchPadOnOff"
        xinput set-prop $touchPadId 125 1
        messageUser "on"
    else
        touch ".mike-touchPadOnOff"
        xinput set-prop $touchPadId 125 0
        messageUser "off"
    fi
fi

```i wrote this to use across multiple partitions of linux systems, which could mount the same code/files but would have different device ids... (it greps xinput for touch, get's it's id and disables or enables based on that...), you can disable the message stuff i just like a sys message poping up telling me whats going on (shortcutted to my calculator button :) )

note, you should change some of the greps to match the device you have, (if you don't have a synap touchp)

---

### Post by vincegata on 2011-06-22
All got is Unable to identify device id... :( Does not work either.

I have ALPS.

---

### Post by alex.ukf on 2011-06-29
@vincegata:
your original solution also works for me.

if i run a ```
sudo find / -name "touchpad-indicator"
```
it returns:
```

/usr/share/touchpad-indicator
/usr/share/doc/touchpad-indicator
/home/user/.gconf/apps/touchpad-indicator
```

and i can use it properly.

---

### Post by vincegata on 2011-06-29
@ukf you have different Dell than mine.

---

### Post by mikejonesey on 2011-06-30
sorry for late reply, type; 

```
xinput list
```

in a terminal and paste your output here...

---

### Post by vincegata on 2011-06-30
Here we go:


 Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                  	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_3M             	id=10	[slave  keyboard (3)]
    &#8627; Logitech USB Receiver                   	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=15	[slave  keyboard (3)]

---

### Post by mikejonesey on 2011-07-01
so the device you want to toggle has id 14 i believe, you can get more details by typing;

xinput --list-props 14

which will tell you all the props for that device, there should be one like enabled which can be toggled 0/1

with;

xinput set-prop [device id (14)] [enabled propery id (usualy 125)] [on/off (0/1)]

if you still can't work it post the feedback of the props;

or if you want to get it done try the pointed id eg;

xinput set-prop 2 125 0

and

xinput set-prop 2 125 1

that would disable the maser device pointer, ie disable all of these;
Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                  	id=14	[slave  pointer  (2)]

neways hope that sorts it for you...

---

### Post by vincegata on 2011-07-01
YAY!! It worked!! Thanks a lot!! 

It was: Device Enabled (122):	1

I posted this almost two months ago, I thought I'd have to wait till next Ubuntu.

No more annoying touchpad getting in the way!

Thanks again!!!!

---

### Post by teotihuacano on 2011-07-03
> **mikejonesey said:**
> so the device you want to toggle has id 14 i believe, you can get more details by typing;

xinput --list-props 14

which will tell you all the props for that device, there should be one like enabled which can be toggled 0/1

with;

xinput set-prop [device id (14)] [enabled propery id (usualy 125)] [on/off (0/1)]

if you still can't work it post the feedback of the props;

or if you want to get it done try the pointed id eg;

xinput set-prop 2 125 0

and

xinput set-prop 2 125 1

that would disable the maser device pointer, ie disable all of these;
Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                       id=12    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                      id=14    [slave  pointer  (2)]

neways hope that sorts it for you...
Ubuntu God may bless you... I don't understand much of code but 
xinput set-prop 11 127 0 
worked for me. I was going insane with this issue...
Muchas gracias

---

### Post by leokemps on 2011-07-03
Excelent!

I tried 'xinput set-prop 13 126 0' and works perfectly!

To turn on 'xinput set-prop 13 126 1'

In may case:

xinput --list so the results:

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Notebook Receiver v2.0    id=11    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                      id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_0.3M               id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]

Then a typed 'xinput --list-props 13' and the result was:
Device 'ImPS/2 ALPS GlidePoint':
    Device Enabled (126):    1
    Coordinate Transformation Matrix (128):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (248):    0
    Device Accel Constant Deceleration (249):    1.000000
    Device Accel Adaptive Deceleration (250):    1.000000
    Device Accel Velocity Scaling (251):    10.000000
    Evdev Axis Inversion (252):    0, 0
    Evdev Axes Swap (254):    0
    Axis Labels (255):    "Rel X" (136), "Rel Y" (137)
    Button Labels (256):    "Button Left" (129), "Button Middle" (130), "Button Right" (131), "Button Wheel Up" (132), "Button Wheel Down" (133), "Button Horiz Wheel Left" (134), "Button Horiz Wheel Right" (135)
    Evdev Middle Button Emulation (257):    0
    Evdev Middle Button Timeout (258):    50
    Evdev Wheel Emulation (259):    0
    Evdev Wheel Emulation Axes (260):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (261):    10
    Evdev Wheel Emulation Timeout (262):    200
    Evdev Wheel Emulation Button (263):    4
    Evdev Drag Lock Buttons (264):    0

Then i checked the prop important in this case was the 'Device Enable(126)'

So taking the command suggested by @[mikejonesey]("http://ubuntuforums.org/member.php?u=909035") 

'xinput set-prop [device id (14)] [enabled propery id (usualy 125)] [on/off (0/1)]'

I typed  'xinput set-prop 13 126 0' and so far so good.

Is there any way to set a shortcut or hot key with this command, because i have a inspiron 14 in my keyboard after the key F12 i have a hot key that should enable and disable as a typed, but dont work,this is why i using the command suggested. But i could forget this command, you know.... for me as a newbie looks like a cake recipe if u know what i mean....

Anyone suggest a tech guide or book to becames a pro on Ubuntu?

Thanks, all the best.

---

### Post by mikejonesey on 2011-07-03
this should work for all (my scipt from earlyer but tweeked to find ps2 pointers and find the enabled id)

```
#!/bin/bash
cd $HOME

function messageUser()
{
    if [ "$(which notify-send)" == "" ]; then
        echo "requires... libnotify-bin for messages..."
    elif [ "$1" == "on" ]; then
        notify-send -t 800 -i /home/mike/myicon.png "Touchpad enabled..." "mike reprogramed the calculator button :)"
    elif [ "$1" == "off" ]; then
        notify-send -t 800 -i /home/mike/myicon.png "Touchpad disabled..." "mike reprogramed the calculator button :)"
    fi
}

touchPadId=$(xinput list | grep -i Point | grep "PS/2" | cut -d "=" -f 2 | cut -b 1-2)
if [ "$touchPadId" == "" ]; then
    echo "Unable to identify device id..."
else
    enabledId=$(xinput --list-props 11 | grep -i enabled | sed 's/.*(//' | sed 's/).*//')
    if [ -a ".mike-touchPadOnOff" ]; then
        rm -rfv ".mike-touchPadOnOff"
        xinput set-prop $touchPadId $enabledId 1
        messageUser "on"
    else
        touch ".mike-touchPadOnOff"
        xinput set-prop $touchPadId $enabledId 0
        messageUser "off"
    fi
fi
```

just edit for your own logo/image in libnotify, n change the lockfile name to remove "mike" :) ... 

should have a trap to catch interupts n a couple more ifs but it does the job fine...

re: resoureces to become a pro on ubuntu, dunno about specific to ubuntu but i recommend books on linux from wiley

---

### Post by teotihuacano on 2011-07-03
Well, I was happy too fast. Now when I execute xinput set-prop 11 127 0 from a console the computer goes crazy like I if I was holding the Enter down. I had to turn it off each time. I've tried 3 times and it's happened again. 
I see now that my ALPS touchpad has moved to id=12 ¡?¡? How could that happen?
~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Genius Optical Mouse                        id=10    [slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                      id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_0.3M               id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]

So now I've just tried xinput set-prop 12 127 0 and the touchpad is dead again... uffff

_[U]Mikejonesey_[/U]: sorry for being so ignorant , but what should I do with the script? How do I turn that into a executable file? It looks like it'll find the touchpad wherever it is, right?
Just in case: I have an Inspiron 14.
Thanks

---

### Post by mikejonesey on 2011-07-04
you can paste it into gedit then save as mouse-on-off.sh (or whatever you prefer), these sort of scripts usually reside in ~/bin (home directory->bin directory), to use nautilus to change the permissions so you can run it, right click and check to box under the permissions tab, via command line chmod +x scriptname.sh.

also run 
```
sudo apt-get install libnotify-bin
```to get system popup messages when you disable or enable the touchpad

then you can add a keyboard shortcut via the system->pref menu and select that script... :)

---

### Post by moonport on 2011-07-04
> **vincegata said:**
> I cannot disable touchpad. If I go to mouse preferences, there is no Touchpad tab. 

I used this package but it does not install at all.

sudo add-apt-repository ppa:atareao/atareao
[FONT=&quot]sudo apt-get install touchpad-indicator[/FONT]

Do you have any other suggestions, please?

TIA!!

I've the same issue in my Lenovo Laptop.

---

### Post by moonport on 2011-07-04
> **mikejonesey said:**
> so the device you want to toggle has id 14 i believe, you can get more details by typing;

xinput --list-props 14

which will tell you all the props for that device, there should be one like enabled which can be toggled 0/1

with;

xinput set-prop [device id (14)] [enabled propery id (usualy 125)] [on/off (0/1)]

if you still can't work it post the feedback of the props;

or if you want to get it done try the pointed id eg;

xinput set-prop 2 125 0

and

xinput set-prop 2 125 1

that would disable the maser device pointer, ie disable all of these;
Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=12	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                  	id=14	[slave  pointer  (2)]

neways hope that sorts it for you...

It worked for me.
Thanks a lot.
Regards.

---

### Post by teotihuacano on 2011-07-05
> **mikejonesey said:**
> you can paste it into gedit then save as mouse-on-off.sh (or whatever you prefer), these sort of scripts usually reside in ~/bin (home directory->bin directory), to use nautilus to change the permissions so you can run it, right click and check to box under the permissions tab, via command line chmod +x scriptname.sh.

also run 
```
sudo apt-get install libnotify-bin
```to get system popup messages when you disable or enable the touchpad

then you can add a keyboard shortcut via the system->pref menu and select that script... :)

Awesome! Works beatifully... You've saved me so much time trying to find out where the hell did the pointer gone to...
Ik'm going to set it up in two other friends computers who had the same problem.

---

### Post by vincegata on 2011-07-05
I've noticed that mine turns back on after I close the lid / suspend. So I hooked up the shortcut key to turn it on.

---

### Post by dilidon on 2011-07-24
> **mikejonesey said:**
> 
just edit for your own logo/image in libnotify, n change the lockfile name to remove "mike" :) ... 


Thanks a bunch. Running a brand new Dell n5110 with the same ALPS touchpad here. Nvidia Optimus technology related booting woes together with the touchpad issues created a lot of headache. Your script saved the day on the mouse side (had to mod it a bit because of an error it produced on my system). :)

To those not familiar with where icons are being stored, two icons perfect for this script can be found here:

> /usr/share/icons/hicolor/32x32/actions/touchpad-enabled.png
/usr/share/icons/hicolor/32x32/actions/touchpad-disabled.png

I'm wondering though, is there/will there be a way to actually get the pad working properly (ie. horizontal scrolling, tap-clicking, automatic switching off on keyboard activity etc)? I found this patching tutorial: 
[http://budts.be/weblog/2010/12/dell-latitude-e6510-screen-and-touchpad]("http://budts.be/weblog/2010/12/dell-latitude-e6510-screen-and-touchpad")
but I still haven't gotten into learning patching myself. Worth trying?

---

### Post by hipogrito on 2011-08-26
Hello,

Thank you so much for the script.

It works like a charm in my Dell Inspiron 17.

Regards,
Fran

---

### Post by mfergo on 2011-09-11
I too have the Alps touchpad (Dell Inspiron 15R) and this did not work for me so I made 2 very simple scripts as follows:
I used xprint list to identify the Alps id (14 in my case).

to enable it:
```

#!/bin/bash
xinput --set-prop 14 'Device Enabled' 1

```

and to disable it:
```

#!/bin/bash
xinput --set-prop 14 'Device Enabled' 0

```

Bear in mind that I am quite ignorant of these matters. I don't know why, in [d.burba]("http://ubuntuforums.org/member.php?u=1216466")'s script, there is an '8' between the 'Device Enabled'  and the 1/0. It does not seem to be in the man pages for xinput.

---

### Post by bluepicaso on 2011-10-26
> **mfergo said:**
> I too have the Alps touchpad (Dell Inspiron 15R) and this did not work for me so I made 2 very simple scripts as follows:
I used xprint list to identify the Alps id (14 in my case).

to enable it:
```

#!/bin/bash
xinput --set-prop 14 'Device Enabled' 1

```and to disable it:
```

#!/bin/bash
xinput --set-prop 14 'Device Enabled' 0

```Bear in mind that I am quite ignorant of these matters. I don't know why, in [d.burba]("http://ubuntuforums.org/member.php?u=1216466")'s script, there is an '8' between the 'Device Enabled'  and the 1/0. It does not seem to be in the man pages for xinput.

thank you this worked for me.
one more thing i have dell 5110 and i found that ubuntu11.10 has some problem detecting the touchpad.. its detects it as a mouse.

---

### Post by mikejonesey on 2011-10-26
> **mfergo said:**
> I too have the Alps touchpad (Dell Inspiron 15R) and this did not work for me so I made 2 very simple scripts as follows:
I used xprint list to identify the Alps id (14 in my case).

to enable it:
```

#!/bin/bash
xinput --set-prop 14 'Device Enabled' 1

```and to disable it:
```

#!/bin/bash
xinput --set-prop 14 'Device Enabled' 0

```Bear in mind that I am quite ignorant of these matters. I don't know why, in [d.burba]("http://ubuntuforums.org/member.php?u=1216466")'s script, there is an '8' between the 'Device Enabled'  and the 1/0. It does not seem to be in the man pages for xinput.

the 8 would have been the property id

ie... device id : property id : property value = 14 8 0

same way i coded my script, par i made the 8 dynamic to a variable... (not always 8, on my current machine it's a 127)

11 127 0

11 127 1

@bluepicaso
> one more thing i have dell 5110 and i found that ubuntu11.10 has some  problem detecting the touchpad.. its detects it as a mouse.
please run xinput search script and paste output;
./xinput-checker.sh ps/2
or
./xinput-checker.sh pad

[http://www.mikejonesey.co.uk/articles/pci-and-xinput-device-checker-scripts.html](http://www.mikejonesey.co.uk/articles/pci-and-xinput-device-checker-scripts.html)

---

### Post by fujisan on 2011-12-01
Here is the script of burba improved because it could not work for me.

```

#!/bin/bash

# this script queries the status of the ImPS/2 ALPS GlidePoint device
# via xinput and disables / enables the device accordingly.

#get touchpad id
XINPUTNUM=`xinput list 'ImPS/2 ALPS GlidePoint' | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`

TPSTATUS=$(gconftool-2 -g /desktop/gnome/peripherals/touchpad/touchpad_enabled)

#if status fails, exit 1
test -z $TPSTATUS && exit 1
if [[ $TPSTATUS == true ]]; then
    xinput set-int-prop $XINPUTNUM "Device Enabled" 8 0;
    gconftool-2 --type bool -s /desktop/gnome/peripherals/touchpad/touchpad_enabled false
else
    xinput set-int-prop $XINPUTNUM "Device Enabled" 8 1;
    gconftool-2 --type bool -s /desktop/gnome/peripherals/touchpad/touchpad_enabled true
fi

```

---

### Post by almikul on 2011-12-21
> **mikejonesey said:**
> with;

xinput set-prop [device id (14)] [enabled propery id (usualy 125)] [on/off (0/1)]
Thank you very much, mikejonesey! It worked great, mate! :D

---

### Post by hannnndy on 2011-12-31
**@mfergo:** I have another question dude!

yes your following script works properly bud how can we integrate it with the our keyboard shortcuts?
for example in my Dell 5110 how can we define the script for FN+F3 to enable and disable the touchpad?

this is my problem why it does not work in the normal way here quality of work becomes important

---

### Post by shevek. on 2012-01-07
In a brand new Dell Inspiron N5110 (and Ubuntu 11.10 64bits), the scripts of @d.burba, @mikejonesey and @fujisan did not work properly for me, so I did another version that did. Hope it helps:
```

#!/bin/bash
cd $HOME
touchPadId=$(xinput list | grep -i Point | grep "PS/2 Generic Mouse" | cut -d "=" -f 2 | cut -b 1-2)
#echo Device ID: $touchPadId

if [ "$touchPadId" = "" ]; then
    echo "Unable to identify device id..."
else
    enabledId=$(xinput --list-props $touchPadId | grep -i enabled | sed 's/.*(//' | sed 's/).*//')
    #echo Property ID: $enabledId
    status=$(xinput --list-props $touchPadId | grep -i enabled | sed 's/.*://')
    #echo Status: $status 
    if [ $status = 0 ]; then
        xinput set-prop $touchPadId $enabledId 1
        echo Trackpad Enabled
    else
        xinput set-prop $touchPadId $enabledId 0
        echo Trackpad Disabled
    fi
fi

```

---

### Post by talha06 on 2012-07-20
thank you so much **shevek** for this script; I've been looking for this.. Unfortunately neither Jupiter nor Touchpad Indicator didn't work for my Inspiron 5110..

---

### Post by D007a on 2012-10-26
hi, i´m completely new to linux and i have the same problem, i need to disable the touchpad

i have Dell inspiron n5110 

[B]&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Genius Optical Mouse                        id=11    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD                 id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)][/B]


what shall i do

---

### Post by D007a on 2012-10-26
This works great thank you very much in ubuntu 12.10 64x  >>> what programming language is this 


> **shevek. said:**
> In a brand new Dell Inspiron N5110 (and Ubuntu 11.10 64bits), the scripts of @d.burba, @mikejonesey and @fujisan did not work properly for me, so I did another version that did. Hope it helps:
```

#!/bin/bash
cd $HOME
touchPadId=$(xinput list | grep -i Point | grep "PS/2 Generic Mouse" | cut -d "=" -f 2 | cut -b 1-2)
#echo Device ID: $touchPadId

if [ "$touchPadId" = "" ]; then
    echo "Unable to identify device id..."
else
    enabledId=$(xinput --list-props $touchPadId | grep -i enabled | sed 's/.*(//' | sed 's/).*//')
    #echo Property ID: $enabledId
    status=$(xinput --list-props $touchPadId | grep -i enabled | sed 's/.*://')
    #echo Status: $status 
    if [ $status = 0 ]; then
        xinput set-prop $touchPadId $enabledId 1
        echo Trackpad Enabled
    else
        xinput set-prop $touchPadId $enabledId 0
        echo Trackpad Disabled
    fi
fi

```

---


---
title: "how do i disable the touchpad and use only usb mouse"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by oDin420 on 2005-08-24
i have an inspiron 4000. i picked it up at a garage sale for $30. it works fine. asside from a broken hinge and a damaged trackstick.

i installed ubunto 5.04 on it. went fine. every thing works except the trackstick/touchpad. when i type, i think because of the impact on the keypad, the pointer drifts away and i am not able to control it until i fiddle with the trackstick.

the trackstick is broken. there is no actual stick there.

what i want to do is disable the trackstick.

i have spent some time on google. and in these forums but, what i have found doesn't work or doesn't make sense.

i have commented out the sections in the xorg.conf file that refer to the touchpad/trackstick. but they both still work.

    ```


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection
#Section "InputDevice"
#        Identifier      "Synaptics Touchpad"
#        Driver          "synaptics"
#        Option          "SendCoreEvents"        "true"
#        Option          "Device"                "/dev/psaux"
#        Option          "Protocol"              "auto-dev"
#        Option		"HorizScrollDelta"	"0"
#EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice	"Synaptics Touchpad"


```

what i want to do it disable the trackstick and touchpad so that i can use only my usb mouse.

what do i have to do to disable it???

do you need anymore info?


thanks

---

### Post by MdaG on 2005-08-25
I'm also wondering about this. When I ran Gentoo I used Syndaemon to disable the tapping feature one second after each key hit. That worked well for me, but I can't seem to be able to use syndaemon now I only get the following:

```
$ syndaemon
Can't access shared memory area. SHMConfig disabled?
```

---

### Post by s_p_a_r_k_y on 2005-08-25
to the prior poster, does your df output have a line like this
tmpfs                   518188        16    518172   1% /dev/shm
 If not you may want to mount tmpfs onto /dev/shm which is shared memory I believe.

I actually was able to disable my internal mouse by mistake while I was trying to get its scroll to work. Not sure what I did, but you could set it up and then not enter it in the ServerLayout section or you could try to specify the usb mouse instead of /dev/input/mice

not really sure what else

---

### Post by oDin420 on 2005-08-25
ok so i figured out how to disable the touchpad. **BUT** i still need to disable the track stick. it is what is causing me problems.

this is how u disable the touchpad.

 We just have to set our touchpad as "CorePointer", and our USB mouse as "SendCoreEvents". But, we have to add the "TouchpadOff" option in touchpad section.

```


Section "ServerLayout"
    Identifier "Default Layout"
    Screen "Default Screen"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse" "SendCoreEvents" 
    InputDevice "Synaptics Touchpad" "CorePointer"
EndSection

```

    
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	#Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        #Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
        Option		"TouchpadOff"         "1"
        Option		"SHMConfig"            "on"
EndSection

```

Also, I added "SHMConfig" just in case i have to enable my touchpad on the fly using synclient command :D.
Oo... ya.. but, we have to load synaptics driver to xorg.conf

    code:

Section "Module"
...
Load "synaptics"

---

### Post by oDin420 on 2005-08-25
[QUOTE=s_p_a_r_k_y]...you could try to specify the usb mouse instead of /dev/input/mice

[/QUOTE]

how do it do that?

---

### Post by amastronardi on 2005-08-25
You should have either /dev/input/mouse0, /dev/input/mouse1, /dev/input/mouse2. /dev/input/mice uses to be a symlibk to one of mouse* devices.

Cheers, Adrian.

---

### Post by MdaG on 2005-08-30
[QUOTE=s_p_a_r_k_y]to the prior poster, does your df output have a line like this
tmpfs                   518188        16    518172   1% /dev/shm
[/QUOTE]

Yes I have... I've enabled SHMConfig in my xorg.conf also...

---


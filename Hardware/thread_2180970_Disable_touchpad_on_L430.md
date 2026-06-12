---
title: "Disable touchpad on L430"
date: 2013-10-15
forum: Hardware
---

### Post by john_s3 on 2013-10-15
Hello

how can I disable the touchpad on my L430, because sometimes I accidently press it, when I use the trackpoint.
In the forum some suggest you should find out the id of the touchpad, but it is not listed with xinput?

```
-ThinkPad-L430:~$  xinput --list&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=11	[slave  keyboard (3)]

```
Disabling the touchpad with the dconf-editor in org/gnomesettings-daemon/peripherals/touchpad with touchpad-enabled key does not work either.
What else can I do, I have Ubuntu 12.04?

---

### Post by sudodus on 2013-10-15
Welcome to the Ubuntu Forums :-)

1. Try Touchpad Indicator according to [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

```
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator
```

2. Use a simple touchpad-toggle that you run from a terminal window.

You can add the following lines to the end of your .bashrc file (and in new terminal windows you can toggle the touchpad (on/off) with either touchpad-toggle or TT).

```
alias TT='touchpad-toggle'

###

function touchpad-toggle {

# toggle synaptic touchpad on/off

# get current state
SYNSTATE=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')

# change to other state
if [ $SYNSTATE = 0 ]; then
    synclient touchpadoff=1
    echo "touchpad OFF"
elif [ $SYNSTATE = 1 ]; then
    synclient touchpadoff=0
    echo "touchpad ON"
else
    echo "Couldn't get touchpad status from synclient"
    exit 1
fi
}

####

alias TT

```

---

### Post by john_s3 on 2013-10-15
thank you very much for the answer

1. disabled both the touchpad and the trackpoint and I want to only use the trackpoint

2. said after I copied it into to.sh and run it

 $ ./to.sh 
./to.sh: line 25: alias: TT: not found

when I disabled the last line the script runs but it has no effect

I tried to use the cmd from the script and got

$ synclient touchpadoff=1
Couldn't find synaptics properties. No synaptics driver loaded?

---

### Post by sudodus on 2013-10-16
Those things have been working for me in several computers, new (bought this year), middle-age and old (ten years old) and different brands, also old IBM Thinkpads (but no new Lenovo Thinkpad). I'm sorry, I don't know what is different. Maybe some new driver system is used for your touchpad. [COLOR=#ff0000]We need help from someone else.[/COLOR]

---

### Post by john_s3 on 2013-10-16
yes it is a new thinkpad

if it helps here is the dmesg output for input

```
bash$ dmesg |grep input[    0.835845] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.836010] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.836038] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.899533] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    2.292906] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input4
[    2.508405] input: Integrated Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input5
[    3.745365] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    3.782100] input: HDA Intel PCH HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    3.782192] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    3.782263] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    3.782378] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    3.782493] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   12.804518] input: PS/2 Generic Mouse as /devices/platform/i8042/serio1/input/input12
[ 2900.197710] input: 00:22:37:03:0E:40 as /devices/virtual/input/input13
[ 5213.866341] input: 00:22:37:03:0E:40 as /devices/virtual/input/input14
[ 5337.617620] input: 00:22:37:03:0E:40 as /devices/virtual/input/input15



```

---

### Post by sudodus on 2013-10-16
> **john_s3 said:**
> thank you very much for the answer

1. disabled both the touchpad and the trackpoint and I want to only use the trackpoint

2. said after I copied it into to.sh and run it

 $ ./to.sh 
./to.sh: line 25: alias: TT: not found

when I disabled the last line the script runs but it has no effect

I tried to use the cmd from the script and got

$ synclient touchpadoff=1
Couldn't find synaptics properties. No synaptics driver loaded?

I see that you made a file to.sh (which I think is invoking ***sh***), but this script needs to be run by ***bash***, so either put it into the end of .bashrc file and start a new terminal window or 

```
source ~/.bashrc
```

or if you want a separate shell-script add crunchbang/bin/bash at the beginning of it

```
#!/bin/bash
```

Maybe it will work for you ...

---

### Post by john_s3 on 2013-10-19
sorry that does work either
I put the [COLOR=#000000][FONT=Ubuntu Mono]#!/bin/bash 
at the beginning but it does not make a difference[/FONT][/COLOR]

---

### Post by linrunner on 2013-10-19
I reckon you used the package from my PPA or a similar workaround in **/usr/share/X11/xorg.conf.d/** to enable the trackpoint?

Unfortunately the workaround results in trackpoint and touchpad being assigned to the same logical device
>   &#8627; PS/2 Generic Mouse                      	id=12	[slave  pointer  (2)]
and therefore it is impossible to disable the touchpad separately.

---


---
title: "Trackpoint on Lenovo X1 Carbon 3rd Gen"
date: 2016-06-05
forum: Hardware
---

### Post by grappler on 2016-06-05
I am trying to  configure the trackpoint on the  machine in the title using the latest Ubuntu (16.04  Xenial) with Gnome as my desktop and running systemd. I've read around online and cannot find any conversation that seems to come close to solving the problem. The device does not seem to appear in any of the /sys/devices/platform/i8042/serio* directories, for instance -  search for TrackPoint in these directories fails. Also xinput list is as follows:

Virtual core pointer                    	id=2	[master pointer  (3)]   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
   &#8627; PS/2 Synaptics TouchPad                 	id=11	[slave  pointer  (2)]
 Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]

I have disabled the TouchPad. The trackpoint is working but is far too sluggish and it is quite difficult to push the cursor round the screen. I've tried to set it according to this:
 
 [http://askubuntu.com/questions/599477/lenovo-x1-carbon-2015-3rd-gen-20-bs-trackpoint-clickpad-and-wifi](http://askubuntu.com/questions/599477/lenovo-x1-carbon-2015-3rd-gen-20-bs-trackpoint-clickpad-and-wifi)

and this:
 
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)
 
One issue that has arisen is to find out which driver my system is using for the trackpoint. There appear to be two available  - a synaptics one and an evdev one. How do I find the driver in use, and how do I switch to the other driver? When I do lsmod I see psmouse but nothing else that would seem to be a trackpoint driver. Thanks in advance for any assistance in this.

---

### Post by Linuxisfast on 2016-06-05
[https://launchpad.net/~linrunner/+archive/ubuntu/thinkpad-extras](https://launchpad.net/~linrunner/+archive/ubuntu/thinkpad-extras) would this help?

---

### Post by grappler on 2016-06-06
Thanks for your help but I tried that. Sorry should have mentioned but I tried many methods I found on the web without success.  After installing configure-trackpoint from the linrunner  repository, when I ran it I got the message that the trackpoint was not detected. But trackpoint is working -  just not as I'd like.

---

### Post by grappler on 2016-06-07
I've made a little progress - for those of you with similar problems. When I run "sudo evtest" I see the following:

No device specified, trying to scan all of /dev/input/event*
Available devices:
/dev/input/event0:    Lid Switch
/dev/input/event1:    Sleep Button
/dev/input/event2:    Power Button
/dev/input/event3:    AT Translated Set 2 keyboard
/dev/input/event4:    Video Bus
/dev/input/event5:    PS/2 Synaptics TouchPad
/dev/input/event7:    ThinkPad Extra Buttons
/dev/input/event8:    HDA Intel HDMI HDMI/DP,pcm=3
/dev/input/event9:    HDA Intel HDMI HDMI/DP,pcm=7
/dev/input/event10:    HDA Intel HDMI HDMI/DP,pcm=8
/dev/input/event11:    HDA Intel PCH Mic
/dev/input/event12:    HDA Intel PCH Headphone
Select the device event number [0-12]:

When I selected 5, I could see the events created by moving the trackpoint and pressing the touchpad buttons. Evidently the word to search for in the serio directories is not "TrackPoint" but "TouchPad" - and so I did:

find /sys/devices/platform/i8042 -name name | xargs grep -Fl TouchPad | sed 's/\/sys\(.*\)\/name/\1/'


and discovered that it is in 

/sys/devices/platform/i8042/serio1/input/input5


Now to work out how to configure - need to find where attributes like speed and sensitivity are set.

---

### Post by grappler on 2016-09-03
I seem to be the only one interested in this problem but in case there is someone else out there with similar problems, I'll give the fix I found. 
I haven't yet discovered how to do this at start-up but I just type this:

xinput --set-prop 11 "libinput Accel Speed" 0.7

into the command line and it fixes the problem. The number 0.7 might be a bit high (or low) for some people but you can adjust. 
The default setting - and the reason for the problem - is negative so the more I move the cursor 
the harder it gets! I found the number 11 by typing  xinput --list 
The output was:


&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Synaptics TouchPad                 	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]

---

### Post by grappler on 2016-09-14
I'll reply to myself again. It appears that the device number is not statically assigned and 
if you add a device or turn one off as I did the device number changes. 

I found a shell script on the web that with a minor modification fixes the problem.

#!/bin/bash
# ~/bin/cursor_speed.sh


SEARCH="TouchPad"


if [ "$SEARCH" = "" ]; then 
    exit 1
fi


ids=$(xinput --list | awk -v search="$SEARCH" \
    '$0 ~ search {match($0, /id=[0-9]+/);\
                  if (RSTART) \
                    print substr($0, RSTART+3, RLENGTH-3)\
                 }'\
     )



for i in $ids
do
    xinput set-prop $i 'libinput Accel Speed' 0.7
done

I don't claim any optimality (or robustness) for this but it does the job on my laptop. 
Again you can replace 0.7 with any other number (between +1 and -1 I think). 
I made it executable and put it in my startup applications.

---


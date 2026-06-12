---
title: "Dell Inspiron Fan Speed"
date: 2007-03-28
forum: Hardware &amp; Laptops
---

### Post by mertle on 2007-03-28
I have a Dell Inspiron 9300,  w/ a 1.6 Ghz Intel Centrino with SpeedStep enabled. I just updated my BIOS from A02 to A05. Whenever my CPU fan kicks on, it stays on full tilt until I reboot, regardless of the CPU temperature (which is, at this very moment, at 36 degrees C and still the fan is running on high). I had also just tested Fiesty on my system and had thought maybe it was Fiesty that was causing the fan speed problem, but even after I reverted back to Edgy, the problem continues... so, it must have been the BIOS flash that did it. Does anyone know...

A) A link to Dell Bios A02 so I may revert back, or
B) A way to control the fan speed

- mertle

---

### Post by nachotronics on 2007-03-29
Hello

Fan and temp control
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds in settings - plugins - Dell i8k

Worked for me

Hope this helps :wink:

---

### Post by mertle on 2007-03-30
I actually started messing around with i8kutils last night, but couldn't get it to work... the whole "i8k force=1" thang did the trick, though. Thanks bunches! I've also just installed gkrell, as you suggested, but haven't played around with thresholds as of yet. Do ya happen to know what are some safe settings for it? I do know that the fan never kicked on till around 58 C, give or take a degree or two. Having been using conky for a while (and loving it) I prolly won't have kgrell startup with KDE, but it's damned useful to configure the fans with.

Thanks again.

- mertle

---

### Post by nachotronics on 2007-03-31
It's great to hear it worked, i left the settings as they were when i installed, and that is:

ALL CELSIUS

On AC power
left fan     ---   low 40    -    high 45
right fan  ---    low 45    -    high 50
hysteresis 5

Running on battery
left fan     ---   low 50    -    high 55
right fan  ---    low 55    -    high 65
hysteresis 5

My Inspiron 6400 has only 1 fan, the left one, but works perfectly. With these settings I hardly ever see temps above 55 C

---

### Post by Surgeon General on 2007-04-20
> **nachotronics said:**
> It's great to hear it worked, i left the settings as they were when i installed, and that is:

ALL CELSIUS

On AC power
left fan     ---   low 40    -    high 45
right fan  ---    low 45    -    high 50
hysteresis 5

Running on battery
left fan     ---   low 50    -    high 55
right fan  ---    low 55    -    high 65
hysteresis 5

My Inspiron 6400 has only 1 fan, the left one, but works perfectly. With these settings I hardly ever see temps above 55 C

what is recommended temp settings? mine was set to:

On AC power
left fan     ---   low 30    -    high 35
right fan  ---    low 35    -    high 40
hysteresis 5


Is that fine or paranoid?

---

### Post by sergeimolotov on 2007-04-20
Also mine dell inspiron fan is running at full speed!!

Only with feisty....i think there is a problem with the last updates....

---

### Post by Beastie Boy on 2007-04-21
I have the same problem after upgrading to Feisty, using an Acer 9114 WLMi.
Under Edgy, in the power options, there was an option to 'Prefer performance over power saving' when connected to AC, and 'Prefer Power saving over performance' when on battery. I can't find that after the upgrade.

Any ideas?

Cheers, Beastie.

---

### Post by morgengenuss on 2007-04-22
i have a dell inspiron 9400 and one of my fans seems to work continuosly, no matter what temperature.

this only seems to be the case since i upgraded from edgy to feisty. installed gkrellm according to nachotronics howto, worked fine. now i can see that one fan is on all the time. any ideas what that's all about?

---

### Post by jmccarthy14 on 2007-04-23
some fixd

---

### Post by jmccarthy14 on 2007-04-25
Same

no problems until upgrading to feisty, and then i reinstalled fiesty the problem still exists.  not present on windows, however.

its obnoxious, definately

---

### Post by nachotronics on 2007-04-27
> **morgengenuss said:**
> i have a dell inspiron 9400 and one of my fans seems to work continuosly, no matter what temperature.

this only seems to be the case since i upgraded from edgy to feisty. installed gkrellm according to nachotronics howto, worked fine. now i can see that one fan is on all the time. any ideas what that's all about?

My Dell Inspiron 6400 has only one fan the "right one" in feisty, or the "left one" in edgy, the fan is actually on the left side, anyway, there's only one of the two fans that works because there's ONLY ONE REAL FAN, and shows the real speed, you can test it changing the speed by clicking over the fan on gkrellm, at full speed its quite loud. The other fan just shows a meaningless speed, keeping in mind THERE IS NO SECOND FAN!! The i8kutils was developed for the Dell Inspiron 8000, wich has 2 real fans, thats why you see the second one.

Hope this helps :wink:

---

### Post by morgengenuss on 2007-04-29
yeah, already checked out changing the fan speed (the 9400 has two fans as well), but this doesn't really solve my problem.
of course i could simply switch off the fan that's working all the time via gkrellm, but i fear that it might overheat then (actually i don't know whether it will switch on on it's own again) and that's why i don't wanna try.

---

### Post by atselby on 2007-04-30
I've got an Inspiron 8600 and it is always on just not always at it's max speed but it tends to stay at max once it getsthere. Are any of these apps compatible with the 8600?

---

### Post by jmccarthy14 on 2007-05-06
i'm wondering if this is going to be fixed.  even when overclocking or playing oblivion for hours the fan would only go on briefly in windows -- its very annoying to have this loudly begin with every rhythmbox open (maybe cause i have 60gb music/)

what can be done -- its clearly software, windows doesn't do this, edgy never did

---

### Post by faust99 on 2007-05-06
> **nachotronics said:**
> It's great to hear it worked, i left the settings as they were when i installed, and that is:

ALL CELSIUS

On AC power
left fan     ---   low 40    -    high 45
right fan  ---    low 45    -    high 50
hysteresis 5

Running on battery
left fan     ---   low 50    -    high 55
right fan  ---    low 55    -    high 65
hysteresis 5

My Inspiron 6400 has only 1 fan, the left one, but works perfectly. With these settings I hardly ever see temps above 55 C

It's odd, but on my Inspiron 710m, Gkrellm threshold settings only work if I adjust the settings for running on battery, even when I am on AC. In other words, the 'On AC power' settings don't make any difference. I can only get the fans to kick in at different temperatures by adjusting the 'Running on battery' thresholds. Does anyone know a fix for this?

---

### Post by nachotronics on 2007-05-07
Here's a radical solution, using the i8k kernel module monitor daemon included in the i8kutils package, this way you are not using any applet or external tool to set the thresholds.
This howto was extracted from the [**_complete i8kutils manual_**]("http://people.debian.org/~dz/i8k/00-README")

> THE I8KMON APPLET/DAEMON
========================

The i8kmon program can be used to monitor the CPU temperature and control automatically the fans accordingly to user-defined temperature thresholds.
The program can be run as daemon or as an applet which can be embedded in the Gnome panel (No, I don't use KDE). The program requires Tcl/Tk (>= 8.0).

The program has builtin defaults and temperature thresholds but users can specify their own settings in configuration files /etc/i8kmon and ~/.i8kmon.
The daemon defines 4 states with different fan speeds ({0 0}, {1 0}, {1 1}, {2 2}) and for each state are defined the temperature thresholds which cause the switching to a higher or lower state. Furthermore each state can have different thresholds for operation on ac power or battery. 
For example the following configuration:

    set config(0) {{0 0}  -1  60  -1  65}
    set config(1) {{1 0}  50  70  55  75}
    set config(2) {{1 1}  60  80  65  85}
    set config(3) {{2 2}  70 128  75 128}

defines state 0 with both fans off, high threshold of 60 degrees (65 on battery) and low threshold -1, which is actually never reached since 0 is the lowest state. When the high threshold is reached the program switches to state 1 (left low, right off) which has a high threshold of 70 degrees and a low threshold of 50 degrees. If the temperature drops below 50 the program will switch back to state 0, if it rises above 70 it will enter state 2, and so on.
For better operation the temperature ranges should be overlapping with an hysteresis of at least 10 degree, i.e. 1={50 70},2={60 80} is better than 1={50 70},2={70 80}. It must be rembered that the low threshold of state 0 must be -1 and the high threshold of state 3 must be 128.

If your laptop has only one fan you should specify a '-' instead of the fan speed of the missing fan, for example:

    set config(2) {{1 -}  60  80  65  85}

**Note the the /etc/i8kmon configfile is not installed by the i8kutils package because the program is designed to be run by normal users. If you want to use it as daemon you must create the config file yourself**.

Create the configuration file running:
```
sudo gedit /etc/i8kmon
```

On my Inspiron 6400 (right fan only) I'm using:
```
    set config(0) {{- 0}  -1  60  **-1  50}**
    set config(1) {{- 1}  50  70  **35  65}**
    set config(2) {{- 2}  60  80  **55  75}**
    set config(3) {{- 2}  70 128  75 128}
```
It never gets to level 2 (high) and most of the time the fan is off(even when my values are more paranoid than the suggested ones)

I have only one fan, which is really on the left side, but on Feisty, i8k treats it as if it was the one on the right(on Edgy it was the left one), you can test this using the command i8kfan followed by -r or -l (right or left) and any of these values 0, 1 or 2 (off, low speed, high speed) 

Example:
```
i8kfan -r 2
i8kfan -l 1
```
should set the right fan to high speed and the left one to low speed. Use this tool to find out which is which.


In order for this to work you will need to run the i8kmon daemon on startup. So we need to add the following: System - Preferences - Sessions - Startup programs:
```
i8kmon -d -a
```


**[B]NOTE: Make sure you are not using any other fan control daemon such as gkrellm, because these are independent to i8kmon and work by reading the temp value and using the i8kfan command directly.**[/B]

Hope this helps :wink:

---

### Post by faust99 on 2007-05-07
Thank you. I actually already installed i8kmon earlier, but even though I can get it to work, changing the threshold values seems to make no difference so my fan is constantly running on low speed, even when the computer is idling.

---

### Post by vs292 on 2007-05-07
> **nachotronics said:**
> Hello

Fan and temp control
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds in settings - plugins - Dell i8k

Worked for me

Hope this helps :wink:
I was wondering if there's a KDE-specific solution to this, or if it's worth using the GNOME app. I've got an uber-noisy Inspiron 9300 too. In windows, I just used to start SpeedFan when it got too noisy and it would cut the fans until the next reboot.

---

### Post by faust99 on 2007-05-07
> **nachotronics said:**
> 

**[B]NOTE: Make sure you are not using any other fan control daemon such as gkrellm, because these are independent to i8kmon and work by reading the temp value and using the i8kfan command directly.**[/B]

Hope this helps :wink:

Thanks again. I got fed up with it and removed both gkrellm and 18kutils. I figured they might interfere with each other so I didn't have them running at the same time, but even still I was getting inconsistent behaviour when I varied the parameters,

I don't have either now but my laptop seems to be running a decent temperature, with the fan kicking in on low every now and then if it gets too hot. Perhaps there is another temp. control utility running? I'm too much of noob to work it out :)

---

### Post by faust99 on 2007-05-08
I think my config file for the daemon was messed up which is why adjusting the parameters seemed to make no difference. I have re-written it as outlined kindly below by nachotronics and it seems to be working a little more predictably....

---

### Post by NooneReally on 2007-05-08
I just went over this a bit ago in this thread: [controlling fan speed]("http://ubuntuforums.org/showthread.php?t=432180")

one vital bit of info that has been left out is that i8kmon *MUST* be started in daemon mode for anything to be happening, so add it to your sessions->startup.

---

### Post by faust99 on 2007-05-08
> **NooneReally said:**
> I just went over this a bit ago in this thread: [controlling fan speed]("http://ubuntuforums.org/showthread.php?t=432180")

one vital bit of info that has been left out is that i8kmon *MUST* be started in daemon mode for anything to be happening, so add it to your sessions->startup.

When I start it in auto mode as you suggested, the fan keeps running all the time, with the cpu temperature below what I set in the config...

---

### Post by faust99 on 2007-05-08
Ok, Ignore that bit about auto mode over-riding my config settings. What really seems to be happening is that i8kmon is following the settings in the config that are supposed to be for battery, rather than ac mode....

---

### Post by nachotronics on 2007-05-09
Thanks! **NooneReally**, I edited and added the autostart part. 

**faust99:** I don't understand what you meant on your last post, when added at startup, created config file, etc: Does it work at all? What do you mean by ac and battery settings, do you want different ones for each case??

---

### Post by faust99 on 2007-05-09
nachotronics: It is working, but somewhat erratically-the temperature is not always what I think it should be according to the settings. In the config file, I was under the impression that the temperature settings on the left are for AC mode, and the ones on the right are for battery mode (c.f.  [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Temperature_and_Fan_Sensors)](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Temperature_and_Fan_Sensors)). 

I have set up the daemon mode to start up as outlined in that link above. When I had it set up to run via the Sessions menu, it seemed to be even more erratic, with the fan coming in and out of high setting for no apparent reason (but maybe coincidence??)

Is temperature control not automatically controlled by Feisty on installation? Why is it necessary to set this up yourself?

---


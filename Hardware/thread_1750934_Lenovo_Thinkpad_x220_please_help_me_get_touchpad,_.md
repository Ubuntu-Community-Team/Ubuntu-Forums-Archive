---
title: "Lenovo Thinkpad x220: please help me get touchpad, trackpoint, fan control working"
date: 2011-05-06
forum: Hardware
---

### Post by unagimiyagi on 2011-05-06
Hi,

I have an X220 with Ubuntu 11.04.

I have read as far as I can understand with getting the various thinkpad fan control programs working, but the instructions are not clear to me still.  I have installed from ubuntu software center, so I am expecting to see a program that I can just graphically manipulate.  tpfan, simple thinkfan, etc.  

I am not sure if I need thinkpad_acpi anymore because it's built-in now to ubuntu?  

Same deal with the touchpad and trackpoint.  They do not work nearly as smoothly as they do in windows.  The one-button touchpad is horrible, and it works nowhere near like it does on a mac.  It gets confused if you ever rest your thumb and click.  

Would appreciate some updated instructions, what is or isn't needed as of 11.04.
What's needed to get the trackpoint to work better?

Thanks!

---

### Post by maciej234 on 2011-05-08
> **unagimiyagi said:**
> Hi,

I have an X220 with Ubuntu 11.04.

I have read as far as I can understand with getting the various thinkpad fan control programs working, but the instructions are not clear to me still.  I have installed from ubuntu software center, so I am expecting to see a program that I can just graphically manipulate.  tpfan, simple thinkfan, etc.  

I am not sure if I need thinkpad_acpi anymore because it's built-in now to ubuntu?  

Same deal with the touchpad and trackpoint.  They do not work nearly as smoothly as they do in windows.  The one-button touchpad is horrible, and it works nowhere near like it does on a mac.  It gets confused if you ever rest your thumb and click.  

Would appreciate some updated instructions, what is or isn't needed as of 11.04.
What's needed to get the trackpoint to work better?

Thanks!

you can install 'Point Devices' from the USC and enable 'Wheel Emulation' and Set to button 2, to get the middle button working - I have mine set to scroll with the trackpoint

---

### Post by unagimiyagi on 2011-05-12
Hi, I am trying my best but I can't get a fan control program to work.  

1.  Is thinkpad_acpi even needed anymore? I can't tell from my reading. 
2.  How do you install it?

see this:  

This is [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue ! important][FONT=inherit ! important]program[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.thinkwiki.org/wiki/How_to_control_fan_speed#") for controlling fans speed on IBM/Lenovo ThinkPads. It is written for Linux only. This program is written in C, using GTK GUI. 
You are required to have the [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]Linux [/FONT][/COLOR][COLOR=blue !important][FONT=inherit !important]kernel[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.thinkwiki.org/wiki/How_to_control_fan_speed#") with 'thinkpad-acpi' patch. You must also enable manual control for your fans. For Linux 2.6.22 and above, you must add 'fan_control=1' as a module parameter to 'thinkpad-acpi'. For example, in Debian Lenny (and Ubuntu 8.04), you must add the following to "/etc/modprobe.d/options": 
        options thinkpad_acpi fan_control=1  

For a newbie, this is what I go through when reading this:  I've found a program for controlling the fan.
I need to get a file called thinkpad-acpi.  OK, where is it?  And then
how and where do I install it once I find this file?  Next, I do in fact
have kernel version > 2.6.22, so I need to add a parameter to a file.
I can find the /etc/modprobe.d/options file, but what does this do?
Does this enable the thinkpad fan control to run on start up?  But then I see 
that these instructions reference ubuntu 8.04, which makes me wonder
if certain drivers and files are already included in 11.04.  So I'm
not sure if what I am reading is now obsolete.


If someone can tell me how to learn to follow these tutorials better, I'd
be happy.  I find that you kind of have to be "in the know" already to 
follow most tutorials that I have read.

---

### Post by williumbillium on 2011-05-13
A lot of people, using both windows and linux, are having fan management issues with this machine.  Lenovo support seems to be aware.  See [this thread]("http://forums.lenovo.com/t5/X-Series-ThinkPad-Laptops/X220-fan-constantly-on-revving-up-and-down/td-p/425965") for more info.

---

### Post by kenneth.koontz on 2011-05-13
To get your trackpoint more responsive you need to modify a few things.

Install sysfsutils first.

```
sudo apt-get install sysfsutils
```

After this you can modify the sensitivity and speed of the trackpoint. The problem with this is that when you reboot on 9.10 or above your settings are overwritten. I have also tried to update the rc.local to run the script but to no luck. I created a script and attached it to startup applications. This seems to work and the settings stick.

Find your path to your trackpoint, run:
```
/lib/udev/path_id $(find /sys/devices/platform/i8042 -name name | xargs grep -Fl TrackPoint | sed 's/\/sys\(.*\)\/name/\1/')
```

The output of this will be something like:
```
ID_PATH=platform-i8042-serio-5

```

NOTE: Your path may be different.

Now that you have an idea where the path may be, you should look for the exact path. From the above ID_PATH, take the serio<number> and use 'find' to look for it under your /sys/devices dir. 

Run:
```
find /sys/devices -name serio5
```

NOTE: Your serio number may be different.

Your output should be something like:
```
/sys/devices/platform/i8042/serio4/serio5
```

Now from here, create the script.

Run:
```

mkdir ~/bin
cd ~/bin
vi trackpoint

``` 

Add the following to trackpoint and save.
```

#!/bin/sh

# Set the trackpoint speed and sensitivity to 120 and 250 respectively. 
# Need chmod for this to work correctly as speed and sensitivity 
# are not writeable upon reboot.
sudo echo -n 120 > /sys/devices/platform/i8042/serio4/serio5/speed
sudo echo -n 250 > /sys/devices/platform/i8042/serio4/serio5/sensitivity

exit 0

```

Make trackpoint executable.

Run:
```
chmod +x ~/bin/trackpoint
```

Now we need to get this script to startup during startup applications. Only problem is that this script requires su. 

Run:
```
sudo visudo
```

At the end of this file, add:
```
<your_username> ALL=NOPASSWD: /home/<your_username>/bin/trackpoint
```

Lastly, add the startup script to startup applications.
1) Launch Startup Applications.
2) Click 'Add'.
3) In 'Name:', name this anything.
4) In 'Command:' Add 'sudo /home/<your_username>/bin/trackpoint'
5) In 'Comment:' comment this anything.
6) Click 'save'.
7) Click 'Close'.

Log out and log back in.

Enjoy! 

If you have any questions please shoot me a message.

---

### Post by unagimiyagi on 2011-05-14
Hi Kenneth,

Thanks alot for your tutorial.  This actually works, and there is no way that I would have ever figured this out without your instructions.  Now onto my next issue, the fan :>

Thanks!

---

### Post by corrytonapple on 2011-05-14
It may be a while, but I am working on a Fan Control program, for my laptop, the Toshiba L455.  It is to be written in Python, have a GUI (something you can click, and be open source.  It will be made for the many Toshiba Laptop users that have had issues with fan control.  Hopefully, it will work with your model laptop too, and if not, I will make it work with it.  It will be running off of lm-sensors, creating a GUI over it for newbies to pros to use.  IDK when it will be ready, but when it is I will PM you.

Good Luck!

---

### Post by kenneth.koontz on 2011-05-14
> **unagimiyagi said:**
> Hi Kenneth,

Thanks alot for your tutorial.  This actually works, and there is no way that I would have ever figured this out without your instructions.  Now onto my next issue, the fan :>

Thanks!

No problem! Your welcome.

---

### Post by kenneth.koontz on 2011-05-14
> **corrytonapple said:**
> It may be a while, but I am working on a Fan Control program, for my laptop, the Toshiba L455.  It is to be written in Python, have a GUI (something you can click, and be open source.  It will be made for the many Toshiba Laptop users that have had issues with fan control.  Hopefully, it will work with your model laptop too, and if not, I will make it work with it.  It will be running off of lm-sensors, creating a GUI over it for newbies to pros to use.  IDK when it will be ready, but when it is I will PM you.

Good Luck!

@corrytonapple I'd love to see what you have so far. Do you have the code available? The fan on my system is constantly running. I'd like to get this thing working properly. I don't think this thing is supposed to be running constantly.

---

### Post by corrytonapple on 2011-05-14
Well, I have divided the work up.  I came up with the idea, and a friend is doing the main structure of the Python, which I do not know what all he has done.  I am working on the GUI, and the actual Python code that will interact with lm-sensors.  At the time, it is all a jumble.  If you would like to see what I have done, check out this page:
4535.a.hostable.me/codelab/
On that page, you will see the Python heading.   Right below it will be the application code so far.  I will add it to the site in 30 minutes or so.  What makes this project unique is, I am working with lm-sensors, which has not been attempted.  If lm-sensors won't work, I will have to find how to work with the hardware via Python myself.

---

### Post by nrundy on 2011-05-17
At least with Ubuntu, I think the problems with the fan might be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

---

### Post by kenneth.koontz on 2011-05-17
> **corrytonapple said:**
> Well, I have divided the work up.  I came up with the idea, and a friend is doing the main structure of the Python, which I do not know what all he has done.  I am working on the GUI, and the actual Python code that will interact with lm-sensors.  At the time, it is all a jumble.  If you would like to see what I have done, check out this page:
4535.a.hostable.me/codelab/
On that page, you will see the Python heading.   Right below it will be the application code so far.  I will add it to the site in 30 minutes or so.  What makes this project unique is, I am working with lm-sensors, which has not been attempted.  If lm-sensors won't work, I will have to find how to work with the hardware via Python myself.

@corrytonapple, I don't see the code. Is this the correct page?

---

### Post by corrytonapple on 2011-05-18
Yup, I am yet to put it up.  I will review with my friend and see if we can put it up for you.  Currently, I am quite busy, and it turns out some links on the site are wrong. Since it is a beta site, until it is done, you might not see the changes.  Hopefully I can get it up soon.

---

### Post by marcoscdlf on 2011-05-31
I've just get my new x220 and i found the fan issue something anoying so these are the steps, FOLLOW THEM AT YOUR OWN RISK

-first install lm-sensors and thinkfan: sudo apt-get install lm-sensors thinkfan
-configure lm-sensors: sudo sensors-detect
-edit /etc/modprobe.d/thinkpad_acpi.conf (it probably doesn't exists): sudo nano /etc/modprobe.d/thinkpad_acpi.conf and add this: "options thinkpad_acpi fan_control=1" (whitout the ")
-save and restart your thinkpad.
-now edit /etc/default/thinkfan: sudo nano /etc/default/thinkfan and change "START=no" to "START=yes"
-finally edit /etc/thinkfan.conf adding this line:
    "sensor /sys/class/hwmon/hwmon0/temp1_input"
 and configure the list of values (is common sense but a bad configuracion of this values should be a disaster for your laptop...)
-start daemon: sudo thinkfan

Next time you restart your computer the thinkfan daemon will start automatically. This works for me.

---

### Post by da7oom on 2011-06-02
> **marcoscdlf said:**
> I've just get my new x220 and i found the fan issue something anoying so these are the steps, FOLLOW THEM AT YOUR OWN RISK

-first install lm-sensors and thinkfan: sudo apt-get install lm-sensors thinkfan
-configure lm-sensors: sudo sensors-detect
-edit /etc/modprobe.d/thinkpad_acpi.conf (it probably doesn't exists): sudo nano /etc/modprobe.d/thinkpad_acpi.conf and add this: "options thinkpad_acpi fan_control=1" (whitout the ")
-save and restart your thinkpad.
-now edit /etc/default/thinkfan: sudo nano /etc/default/thinkfan and change "START=no" to "START=yes"
-finally edit /etc/thinkfan.conf adding this line:
    "sensor /sys/class/hwmon/hwmon0/temp1_input"
 and configure the list of values (is common sense but a bad configuracion of this values should be a disaster for your laptop...)
-start daemon: sudo thinkfan

Next time you restart your computer the thinkfan daemon will start automatically. This works for me.

Hey 

is ur x220 now working fine ? 

i'm confused about buying x220 and it's computability  with Linux

---

### Post by unagimiyagi on 2011-06-02
> **da7oom said:**
> Hey 

is ur x220 now working fine ? 

i'm confused about buying x220 and it's computability  with Linux

I haven't gotten around to trying fix the fan issue. 

However, compared to a macbook pro, the x220 is so much more stable and works out of the box.  I can confirm that much at least.  For whatever I was complaining about earlier, the macbook pro is far far less compatbile with ubuntu 11.04

In fact, the only people I've ever seen with Ubuntu on their laptops as their every day OS were thinkpad users.  I would absolutely not recommend Ubuntu as your only OS on a mac.  There is no way I'd recommend it.  Hey, but ubuntu is free, so I can't complain (though I do).  I'm starting to think that there's just limits to what open source can do when it comes to complex systems like maintaining an OS.  Someone has got to pay people in order to produce stable products. ubuntu is commercially sponsored, but their workforce must be so much smaller than MS or Apple's.  It seems to show with regards to compatibility.  I wonder if the thinkpad is Ubuntu's reference laptop.  It truly seems to be much more compatible compared to everything else.

---

### Post by da7oom on 2011-06-03
> **unagimiyagi said:**
> I haven't gotten around to trying fix the fan issue. 

However, compared to a macbook pro, the x220 is so much more stable and works out of the box.  I can confirm that much at least.  For whatever I was complaining about earlier, the macbook pro is far far less compatbile with ubuntu 11.04

In fact, the only people I've ever seen with Ubuntu on their laptops as their every day OS were thinkpad users.  I would absolutely not recommend Ubuntu as your only OS on a mac.  There is no way I'd recommend it.  Hey, but ubuntu is free, so I can't complain (though I do).  I'm starting to think that there's just limits to what open source can do when it comes to complex systems like maintaining an OS.  Someone has got to pay people in order to produce stable products. ubuntu is commercially sponsored, but their workforce must be so much smaller than MS or Apple's.  It seems to show with regards to compatibility.  I wonder if the thinkpad is Ubuntu's reference laptop.  It truly seems to be much more compatible compared to everything else.


Once i bought an Asus notebook and it was horrible with Linux, I ended up selling it. Because of that i don't repeat the same mistake. 

I know thinkpad is cool and got a high quality, but why i should take it and suffering with compatibility problems.

In the the other hand, Dell got a high compatibility rate with Ubuntu

---

### Post by da7oom on 2011-06-06
btw if your interested fedora is working fine with x220

[http://forums.fedoraforum.org/showthread.php?t=261444](http://forums.fedoraforum.org/showthread.php?t=261444)

---


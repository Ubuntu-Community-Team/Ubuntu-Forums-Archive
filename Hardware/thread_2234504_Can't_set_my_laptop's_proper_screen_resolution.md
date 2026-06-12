---
title: "Can't set my laptop's proper screen resolution"
date: 2014-07-15
forum: Hardware
---

### Post by Auroraw on 2014-07-15
Hey guys, i'm new to Lubuntu and I really like the OS but for the past days the only thing i've been trying to accomplish is changing my resolution from 1024x768 to 1440x900 and it's so frustrating. It makes me wonder why you have to be a computer mastermind to set the resolution on this "very simple and intuitive system".

OS: Lubuntu v14.04
Computer: Sony Vaio VGN-AR15J (max screen resolution is 1440x900)
GPU: NVIDIA GeForce 8400M GT

I have tried using xrandr in accordance with tutorials to add a new resolution (--newmode, --addmode etc) and then the new mode does show up in the resolution menu though when i click it the screen flickers for a moment but stays at 1024x768.
 After that I tried to force it to change with xrandr --output, I got an error message saying something along the lines of "maximum resolution is 1024x768 (trying to use 1440x900)" and nothing happened. So that doesn't work either.
Oh I also tried the whole xorg.conf change but the mode I added was never still in the resolution menu after rebooting (not that my added resolution worked anyways)

I am thinking this must be some kind of driver problem, the maximum resolution of the screen is limited to 1024x768.

It would be very much appreciated if you help me solve this because it's really ruining my day haha

---

### Post by Auroraw on 2014-07-16
Anyone?

---

### Post by WinEunuchs2Unix on 2014-07-16
I'll have a kick at the can :D.

First off my Laptop best resolution is 1280 x 800 and that resolution was automatically used by Ubuntu.  I did hook up a used TV to the VGA port and that required quite a bit of experimenting over a couple of weeks (hobby time) to get it perfect.

I put it in a start up script which looks like this:
```
~/scripts$ cat 1360x768.sh

#!/bin/sh -e
#======== Call TV mode awhile after booting because it doesn't work on initial boot.
#
# Generate 1366x768 (true 16:9 ratio)
xrandr --newmode "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
xrandr --addmode VGA1 "1368x768_60.00"



```

Now to get thexrandr  --newmode 1368x768 .... line you need to generate it with the command cvt or gtf from the command prompt in "Terminal" using "gtf" or "cvt".

I don't use the "output" command just by going into System Settings, Display I can pick the resolution I want from the drop down menu and it "remembers" it the next time I boot up.  There is a brief delay on the TV between default resolution and high resolution when the startup script is run.

The boot script is located in /etc/rc.local but X11 isn't running during initial boot so xrandr won't work at that time.  This is why I put it in ~/scripts/1360x768.sh and called it in the startup applications menu.

The Toshiba TV says it only supports 1360x768 max resolution (which is how the script file got it's name) but I was getting a one inch border on the left and right of the screen so I used 1368x768 resolution instead to get perfect picture (well for the year 2007).

I'll follow this thread in e-mail notification and answer any questions you have.

---

### Post by WinEunuchs2Unix on 2014-07-16
Poking around I found this site that doesn't provide a direct link to your question but which might have other useful information.  The site's author might have pointers I can't provide.  Unlike some posts from 2004 to 2008 this site is recent.

[http://www.linux.it/~malattia/wiki/index.php/Sony_Vaio_Control_device_drivers](http://www.linux.it/~malattia/wiki/index.php/Sony_Vaio_Control_device_drivers)

[COLOR=#000000][FONT=sans-serif]Sony Vaio notebooks contain some proprietary devices (for which there doesn't exist any public official documentation) that allow extended notebook controls:[/FONT][/COLOR]

[LIST]
[*]Fn keys (hotkeys)
[*]Jogdial
[*]Motion Eye camera (C1VE/C1VN series)
[*]display brightness control
[*]display brightness on boot
[*]sound card poweron/poweroff
[*]NIC poweron/poweroff
[*]GPRS/EDGE modem power
[*]Bluetooth power
[*]Fan speed
[/LIST]

---

### Post by Auroraw on 2014-07-17
Thanks guys, i'll give it another try today!

---

### Post by Auroraw on 2014-07-17
> **WinEunuchs2Unix said:**
> I'll have a kick at the can :D.

First off my Laptop best resolution is 1280 x 800 and that resolution was automatically used by Ubuntu.  I did hook up a used TV to the VGA port and that required quite a bit of experimenting over a couple of weeks (hobby time) to get it perfect.

I put it in a start up script which looks like this:
```
~/scripts$ cat 1360x768.sh

#!/bin/sh -e
#======== Call TV mode awhile after booting because it doesn't work on initial boot.
#
# Generate 1366x768 (true 16:9 ratio)
xrandr --newmode "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
xrandr --addmode VGA1 "1368x768_60.00"



```

Now to get thexrandr  --newmode 1368x768 .... line you need to generate it with the command cvt or gtf from the command prompt in "Terminal" using "gtf" or "cvt".

I don't use the "output" command just by going into System Settings, Display I can pick the resolution I want from the drop down menu and it "remembers" it the next time I boot up.  There is a brief delay on the TV between default resolution and high resolution when the startup script is run.

The boot script is located in /etc/rc.local but X11 isn't running during initial boot so xrandr won't work at that time.  This is why I put it in ~/scripts/1360x768.sh and called it in the startup applications menu.

The Toshiba TV says it only supports 1360x768 max resolution (which is how the script file got it's name) but I was getting a one inch border on the left and right of the screen so I used 1368x768 resolution instead to get perfect picture (well for the year 2007).

I'll follow this thread in e-mail notification and answer any questions you have.


I copied your script and changed it according to my situation:
```
 ~/scripts$ cat 1440x900.sh

#!/bin/sh -e
#======== Call TV mode awhile after booting because it doesn't work on initial boot.
#
# Generate 1440x900 (true 16:9 ratio)
xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode default "1440x900_60.00"
```
I just  saved it on my desktop. When I execute it a new mode shows up in the  monitor preferences menu though when I apply it nothing happens
Do you have any idea why it doesn't work on this laptop?

---

### Post by WinEunuchs2Unix on 2014-07-17
> **Auroraw said:**
> I copied your script and changed it according to my situation:
```
 ~/scripts$ cat 1440x900.sh

#!/bin/sh -e
#======== Call TV mode awhile after booting because it doesn't work on initial boot.
#
# Generate 1440x900 (true 16:9 ratio)
xrandr --newmode "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
xrandr --addmode default "1440x900_60.00"
```
I just  saved it on my desktop. When I execute it a new mode shows up in the  monitor preferences menu though when I apply it nothing happens
Do you have any idea why it doesn't work on this laptop?

Well you didn't have to copy my script comments about the TV too...LOL. 

I noticed your -addmode line says "default" but I believe it should read "LVDS1" for your built in display.  If you type "xrandr" by itself it will list all the names of possible screens to reference, even ones you don't have connected.

After picking a new resolution from the drop down menu you need to click the "Apply" button and the screen resolution should change with a count down message telling you to click "ok" to accept the new settings.

---

### Post by WinEunuchs2Unix on 2014-07-17
Something else I just discovered is you can check Xorg (the subsystem that runs keyboards, mice and displays) for messages.  For example I changed my built in display from 1280x800 to 1024x768 like yours.  Then I changed it back to 1280x800 and looked at the subsystem's log file:

```
~$ tail --lines=1 /var/log/Xorg.0.log
[  5339.418] (II) intel(0): switch to mode 1280x800@60.0 on LVDS1 using pipe 0, position (0, 0), rotation normal, reflection none

~$ 


```

On your system change the "--lines"=1 to "--lines=20" or something large enough to see the error messages, if any, that Xorg reports.  Note you do not type the "~$" which is the command prompt on my system.

---

### Post by WinEunuchs2Unix on 2014-07-17
There are special drivers for your GPU graphics chipset written by the "[COLOR=#666666][FONT=Open Sans]Ubuntu-X team and xorg crack pushers team[/FONT][/COLOR]" available at: [http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)

It is written for Ubuntu 14.04 LTS and released on April 17, 2014.  If you don't have it already installed it might be worth installing it.

---


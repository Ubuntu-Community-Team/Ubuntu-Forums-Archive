---
title: "How to: Close Lid without going into suspend/hibernate mode?"
date: 2006-01-21
forum: Hardware &amp; Laptops
---

### Post by gimpologist on 2006-01-21
**Situation**: Dell Latitude CPi laptop running ubuntu 5.1.  Want to make into server otherwise it will just sit in the laptop case.

**Problem**: I don't want the lid always open while it's on. I want to be able to close the lid, but ONLY turn off the monitor and not affect the performance of the computer.

**My data collected**: I know it has to do with the ACPI and/or the APM scripts and lid.sh script, but alas, I'm a noob when it comes to Linux commands and scripting. What do I need to change in the lid.sh file so that it only turns off the monitor on lid close and obviously on lid open, turn on the monitor?

**Experience**: Not much with linux, but have tooled around with various distro's in the last five years, but never really used it primarily for desktop/server use.

**Goal**: Learn more about linux and terminal usage while mirroring my winxp pro setup to see how it compares as a desktop and a server (both of which I do on my winxp machine). I've always pirated stuff for my winxp needs, but I noticed that these last few years there have been great OSS or free products out there on linux so I wanted to give it another try and in the process use some my old laptop to be my primary web server.

Any help is appreciated!

---

### Post by Botond on 2006-01-21
How does your lid.sh look like?
My laptop doesn't sleep automatically, and I like it this way.
Here's my /etc/acpi/events/lidbtn (it simply calls lid.sh):
```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh

```

And here's my /etc/acpi/lid.sh (it doesn't call sleep.sh):
```
#!/bin/sh

. /usr/share/acpi-support/power-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"	    
	    . /usr/share/acpi-support/screenblank
	fi
    done
else
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"
	    grep -q off-line /proc/acpi/ac_adapter/*/state
	    if [ $? = 1 ]
		then
                su $user -c "xscreensaver-command -unthrottle"
		
	    fi
	    if [ x$RADEON_LIGHT = xtrue ]; then
		[ -x /usr/sbin/radeontool ] && radeontool light on
	    fi
	    su $user -c "xscreensaver-command -deactivate"
	    su $user -c "xset dpms force on"
	fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

```

---

### Post by davinci on 2006-01-21
Try changing the action line in the /etc/acpi/events/lidbtn file.

action=/etc/acpi/screenblank.sh

This should turn off the monitor if you close the lid

---

### Post by Botond on 2006-01-21
[QUOTE=davinci]Try changing the action line in the /etc/acpi/events/lidbtn file.

action=/etc/acpi/screenblank.sh

This should turn off the monitor if you close the lid[/QUOTE]

That's no-go! lidbtn will be called on lid open and lid close events too. The actual lid state must be 1st evaluated, see my lid.sh:
```
grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    ...
else
    ...

```

Btw, my files are not hacked, come from acpi-support-0.50.

---

### Post by gimpologist on 2006-01-21
Thanks for the replies...

Here's what my lidbtn looks like:

```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh
```

Here's what my lid.sh looks like:
```

#!/bin/sh

. /usr/share/acpi-support/power-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"	    
	    . /usr/share/acpi-support/screenblank
	fi
    done
else
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"
	    grep -q off-line /proc/acpi/ac_adapter/*/state
	    if [ $? = 1 ]
		then
                su $user -c "xscreensaver-command -unthrottle"
		
	    fi
	    if [ x$RADEON_LIGHT = xtrue ]; then
		[ -x /usr/sbin/radeontool ] && radeontool light on
	    fi
	    su $user -c "xscreensaver-command -deactivate"
	    su $user -c "xset dpms force on"
	fi
    done
fi
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

```

Looks the same to me. 

So when you close your lid, your laptop doesn't suspend or hibernate? Do you get a login prompt when you open back up your lid?

I have a webserver on this guy so when I tested from my other comp the pages were served up fine with the lid open and closed, but I'm worried because I don't want this machine to ever go in to suspend or hibernation when the lid is down as the machine (if everything goes as planned) will be my primary web server.

---

### Post by jarno on 2006-01-22
Install gnome-power-manager with apt or synaptic, and choose from the options tab 'do nothing' into 'when laptop lid is closed', and then your laptop won't suspend nor hibernate when you close the lid.

---

### Post by Botond on 2006-01-23
[QUOTE=gimpologist]
So when you close your lid, your laptop doesn't suspend or hibernate?[/QUOTE]
No.

[QUOTE=gimpologist]Do you get a login prompt when you open back up your lid?
[/QUOTE]

No. I think that's a bug. It was working some updates ago.
lid.sh calls the function "getXuser" which calls "finger" which doesn't work anymore. If you execute "finger" and see yourself logged in then that login promt thing should work for you.
BTW, I don't have gnome-power-manager installed.

---

### Post by Botond on 2006-01-24
OK, yesterdays updates have fixed my "finger". Now I have to unlock xscreensaver when I open the lid.

---

### Post by gimpologist on 2006-02-04
Thanks for the replies.

I've been keeping the lid closed on the laptop without changing anything and it seems to behave as I want it to.

Basically, the screen powers off, but the laptop doesn't go into hibernation/sleep .

---

### Post by jchau on 2006-09-30
Your lid.sh is too complicated.  If you want to have a simpler one, see [http://ubuntuforums.org/showthread.php?t=134319](http://ubuntuforums.org/showthread.php?t=134319) .  It just turns off the screen when the lid closes & turns it back on when the lid opens.

---

### Post by Z(L)o on 2006-11-05
Hello, everyone 
I have the same question as subj title, but using APM. 
thank you in advance

---


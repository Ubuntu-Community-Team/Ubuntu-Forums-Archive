---
title: "[SOLVED] DPMS issues with suspend and laptop lid"
date: 2008-04-25
forum: Hardware
---

### Post by tamias on 2008-04-25
A problem which began on installing the Hardy Beta, and which still persists into the final release, involves my Dell Inspiron 6000 laptop screen waking up from resume when it is suspended by closing the lid.

_To cause the problem:_

Invoke laptop suspend mode by closing the lid (this is set in my power management properties). Open the lid once again to resume the laptop.
NOTE: The problem only occurs when suspending the laptop by closing the lid. Choosing suspend from the log-out menu does not invoke the problem.

_What happens:_

DPMS mode of the monitor remains OFF and the screen will not display anything until the system is left for its idle timeout period (5 mins on my laptop). After this period has elapsed, any keypress will wake up the monitor correctly.

_Attempted fixes, by typing blind at a text console:_

xset dpms force on  -- fails to fix the problem when entered at a TTY as xset is `unable to open display ""'

vbetool dpms on  -- causes DPMS mode to switch on.


NOTE: The laptop does not necessarily have to be put into suspend mode; setting the power management prefs to 'Do Nothing' also causes the screen to blank on closing the lid, and not unblank on re-opening it. Interestingly, setting the action to 'Blank screen' invokes the correct behaviour of DPMS blanking when closing the lid and unblanking it when opening again.


How can I get this command to execute automatically on resume when opening the laptop lid? I am reluctant to just fashion in a 'quick hack' when this is an issue that only surfaced with Hardy -- which package should I file a bug against?

---

### Post by tamias on 2008-04-25
Update: Thinking back, quite often when this problem manifests itself, on waking from suspend mode the laptop also issues a fast series of high-pitched beeps for about a second. I notice that Power Management Preferences has a 'Use sound to notify in event of an error' option.

If this is related to the power management profiles, as outlined above, is it possible there is a bug in gnome-power-manager? Or am I looking in the wrong place?

---

### Post by tamias on 2008-04-28
Is anyone able to help, or at least give me a pointer as to which packages I should investigate?

---

### Post by tayroni on 2008-04-28
You can try add "vbetool dpms on" to /etc/acpi/lid.sh

I'm not sure this will work, but you post here if so

Modify lines as indicated below:

Look for the lines:

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
		if pidof xscreensaver > /dev/null; then 
		    su $user -c "xscreensaver-command -unthrottle"
		fi
	    fi
	    if [ x$RADEON_LIGHT = xtrue ]; then
		[ -x /usr/sbin/radeontool ] && radeontool light on
	    fi
	    if [ `pidof xscreensaver` ]; then
		su $user -c "xscreensaver-command -deactivate"
	    fi
	    su $user -c "xset dpms force on"
	fi
    done
fi

and add a new line "vbetool dpms on" where is indicated

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
		if pidof xscreensaver > /dev/null; then 
		    su $user -c "xscreensaver-command -unthrottle"
		fi
	    fi
	    if [ x$RADEON_LIGHT = xtrue ]; then
		[ -x /usr/sbin/radeontool ] && radeontool light on
	    fi
	    if [ `pidof xscreensaver` ]; then
		su $user -c "xscreensaver-command -deactivate"
	    fi
	    su $user -c "xset dpms force on"
	fi
    done
#   NEW LINE HERE
    vbetool dpms on 
fi

---

### Post by tamias on 2008-04-28
Thanks for your suggestion. Unfortunately this doesn't have the desired effect; it looks like the new line of code doesn't get executed at all, and I still have to blindly-type the command at a terminal to regain use of my monitor.

I wonder what also causes the occasional loud, high-pitched repeated beeping noise on some occasions, such as resuming from suspend, and if it's related? Perhaps one of the power-management scripts or programs is crashing before it gets around to enabling DPMS? If so, can anyone help me to debug the issue?

I do find it strange that this behaviour only started when I upgraded to Hardy. What changes to power-management have been made since Gutsy?

---

### Post by tayroni on 2008-04-28
You can try this after undo what I saw previously?

Create /etc/acpi/events/backlight (new file) with the following content: (keep it as exactly 2 lines)

event=button[ /]lid
action=[[ "$(cat /proc/acpi/button/lid/LID/state)" == *open ]] && { vt=$(fgconsole);chvt 15;vbetool post;sleep 1;chvt $vt; }

If you want it to take effect before reboot, run: /etc/init.d/acpid reload

Post if that solves your problem. If not solve, Undo by using

rm /etc/acpi/events/backlight

---

### Post by tamias on 2008-04-29
Thank you for your suggestion. Unfortunately it still has no effect, and my screen remains switched off when opening the lid.

Is there a way I can add a command to the end of that script to get it to create a file in my home directory, for example, to indicate whether or not the script is actually running?

---

### Post by djst on 2008-05-01
Interesting. I'm getting the same problem on my Dell Inspiron 6000 too. Argh, why does hibernation/standby always have to be the one thing that's buggy?

---

### Post by tamias on 2008-05-04
Anyone?

---

### Post by lazyron on 2008-05-04
I'm having the same problem on a Dell e1405. Sorry I don't have any answers, but wanted to tag the thread and let others know that the e1405 is having trouble too.

Any suspend seems to kill it, laptop close or key press. I also get the quick succession of beeps (5, I think).

---

### Post by tamias on 2008-05-13
Is no one able to help at all? Not even to suggest somewhere to start debugging?

I'm a relatively experienced user and I've already fixed many other things on my laptop which Hardy broke, but this bug has just got me stumped. I'm not looking for a hand-holding walkthrough, just somewhere to get started on a bug report!

---

### Post by thomseddon on 2008-05-13
same problem with my inspiron 6000


i do the typing blind thing aswell lol

---

### Post by tamias on 2008-05-27
I seem to have been able to fix this problem by executing

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

The replacement /etc/X11/xorg.conf is very much shorter than the previous version which the dpkg reconfigure replaced: in particular, it contains no information about available screen modes. Yet, it seems to work. I assume something in my older xorg.conf was breaking the DPMS resume.

---

### Post by tripss734 on 2008-09-16
I have the same issues with my acer.  I have also noticed that my cpu and system load were both pegged when trying to resume.  Any ideas?

---

### Post by evolipel on 2008-12-24
This seems to be exactly the same issue as the one experienced here:

[http://ubuntuforums.org/showthread.php?t=358432](http://ubuntuforums.org/showthread.php?t=358432)

If you follow that advice, the screen comes back on beautifully. You would get the same thing if you either follow the advice verbatim or just edit /etc/acpi/lid.sh to include
```
grep -q open /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    vbetool dpms on
fi
```
before
```
if [ `CheckPolicy` == 0 ]; then exit; fi
```

I'm guessing the reason for the OP's original suggestion not working is because the script never actually gets past the above policy check.

The policy check apparently checks whether gnome-power-manager or any other similar power manager is set to handle lid events. Even if you set the lid action to "Do Nothing" in "System>Preferences>Power Management", the script /etc/acpi/lid.sh still aborts at the policy check.

The following bugs are related to this issue:
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/22987](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/22987)
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/44393](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/44393)
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/49521](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/49521)
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/67231](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/67231)

I'm actually quite surprised this hasn't been fixed yet for so long, seeing as how it's quite noticeable and it seems to affect many Dell laptops.

(For the record, I'm on a Dell Inspiron 8100 running Hardy and have experienced this issue.)

---


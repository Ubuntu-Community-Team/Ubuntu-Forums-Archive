---
title: "Hibernate on lid close"
date: 2005-11-13
forum: Hardware &amp; Laptops
---

### Post by akniss on 2005-11-13
When I close the lid on my Dell Inspiron 600m, the display dims to off just as it is supposed to.  Is there a way I can customize the lid close button so that it automatically hibernates the system?  I think this is a handy little customization that I had available in windows.  Hibernating on log off works perfectly on this machine, so i would assume there must be a way to associate the hibernate capability with the screen close button.  Any ideas?

I'm using Breezy.

---

### Post by giftnudel on 2005-11-13
Hi,

in order for that to work, you need either a lid close event (which probably does not work) or some other way to find out whether your lid is closed. There might be problems with the acpi settings which you can't fix. 

So first, try to find out, if your acpi events are working. Start acpi_listen, close your lid and see if something happens. If you see something with LID in it, thats great and you can easily solve your idea. Check the skripts in /etc/acpi/, especially the lid.sh, and add a line to hibernate (echo 3 > /proc/acpi/sleep) where appropriate and it should work.  If not, and that's more likely, you must find some other way. 

On my Inspiron 1100, I don't get any events. However, I can check /proc/acpi/buttons/LID0/state and I can see, if the lid is open or closed. (To see if it is closed, run "sleep 3 && cat /proc/acpi/buttons/LID0/state", close the lid rather quickly, count to 3, open it, and you should see something like state: closed.

If this is the case, you could write a shellskript that checks the state every 10-15 seconds and which hibernates your laptop when it detects a closed state.

Otherwise, you just out of luck and the only chance is to complain to DELL ....

I hope I could help you,

giftnudel

---

### Post by akniss on 2005-11-13
Results of acpi_listen:
button/lid LID 00000080 00000013
button/lid LID 00000080 00000014

I assume this means that I have a lid close event.
Could you show me where and what I should try to paste into the script files.  (Some explanation of why would also be appreciated so I can begin to learn what it is I'm doing...  Below I have pasted the content of lid.sh and hibernate.sh

Here is the content of lid.sh:
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



Content of hibernate.sh:
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

if [ x$ACPI_HIBERNATE != xtrue ] && [ x$1 != xforce ]; then
  exit;
fi

# Unset video posting - it's not needed for suspend to disk
unset POST_VIDEO

. /etc/acpi/prepare.sh

if [ x$LOCK_SCREEN = xtrue ]; then
    for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXuser;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"
	    . /usr/share/acpi-support/screenblank
	fi
    done
fi

echo -n $HIBERNATE_MODE >/sys/power/disk
echo -n "disk" >/sys/power/state

. /etc/acpi/resume.sh

---

### Post by JLB on 2005-11-13
[QUOTE=akniss]When I close the lid on my Dell Inspiron 600m, the display dims to off just as it is supposed to.  Is there a way I can customize the lid close button so that it automatically hibernates the system?  I think this is a handy little customization that I had available in windows.  Hibernating on log off works perfectly on this machine, so i would assume there must be a way to associate the hibernate capability with the screen close button.  Any ideas?

I'm using Breezy.[/QUOTE]

edit /etc/acpi/events/lidbtn

change the line 
action=/etc/acpi/lid.sh to:

action=/etc/acpi/sleep.sh (for suspend to ram) OR...

action=/etc/acpi/hibernate.sh (for suspend to disk)

Cheers!
JL

---

### Post by akniss on 2005-11-14
[QUOTE=JLB]edit /etc/acpi/events/lidbtn

change the line 
action=/etc/acpi/lid.sh to:

action=/etc/acpi/sleep.sh (for suspend to ram) OR...

action=/etc/acpi/hibernate.sh (for suspend to disk)

Cheers!
JL[/QUOTE]


That worked perfectly!!! Thank you so much.
Andrew

---

### Post by JLB on 2005-11-14
great to hear that! yw!
JL

---

### Post by ibanez88 on 2005-11-14
Yes that's an easy solution to what I thought was a difficult problem also.  Thank you!

---


---
title: "Catch 22: ATI Graphics"
date: 2013-01-29
forum: Hardware
---

### Post by jcobban on 2013-01-29
I have a problem on 12.10.  I can either support suspend/resume on my laptop or HDMI attached displays, but not both.

If I use the default open driver for ATI graphics my laptop suspends when I close the laptop and resumes when I open the lid, but the screen remains black.  I have tried restarting Xorg by issuing "sudo restart lightdm" through a telnet session, but that is not enough.  I have to power the laptop off and back on to get the display back.

If I use the proprietary driver fglrx the display works properly during suspend/resume, but the maximum virtual screen resolution is only 1600x1600, which means I cannot use an external 1080p display at its full resolution.

lspci returns:

00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Mobility Radeon HD 6620G]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:10.1 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices [AMD] Hudson SD Flash Controller
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

With the open driver xrandr returns:

Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+   40.1  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 disconnected (normal left inverted right x axis y axis)

How do I resolve this catch 22?

---

### Post by tgalati4 on 2013-01-29
I would think you want maximum resolution, so let's work with the open source driver.  In theory if there was a command to wake up the secondary display after resume from sleep then you could insert that command in the resume script that is called after the "lid switch" is detected.  These scripts are generally located in /etc/acpi.  If you look through the individual scripts you will see work-arounds for various laptops to get ideas for things to try.

Initially, I would try xrandr to try to wake up the second display.

```
man xrandr
xrandr --verbose --query
xrandr --screen 2  --auto
```

What does the above do?

---

### Post by jcobban on 2013-01-29
> **tgalati4 said:**
> I would think you want maximum resolution, so let's work with the open source driver.  In theory if there was a command to wake up the secondary display after resume from sleep then you could insert that command in the resume script that is called after the "lid switch" is detected.  These scripts are generally located in /etc/acpi.  If you look through the individual scripts you will see work-arounds for various laptops to get ideas for things to try.

Initially, I would try xrandr to try to wake up the second display.

```
man xrandr
xrandr --verbose --query
xrandr --screen 2  --auto
```

What does the above do?

The **primary** display is black.  How do I issue the xrandr command with no working display?

/etc/acpi/lid.sh contains:

#!/bin/bash
# TODO:  Change the above to /bin/sh

test -f /usr/share/acpi-support/state-funcs || exit 0

. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs
. /etc/default/acpi-support

[ -x /etc/acpi/local/lid.sh.pre ] && /etc/acpi/local/lid.sh.pre

if [ `CheckPolicy` = 0 ]; then exit; fi

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
[ -x /etc/acpi/local/lid.sh.post ] && /etc/acpi/local/lid.sh.post

---

### Post by tgalati4 on 2013-01-29
That would be a problem.  You could type the command in a terminal, but don't hit return.  Change the 2 above to 1 for primary display.  On the terminal's window, put "Always on Top" and "Maximize".  Then put the laptop to sleep.  Wait for 5 minutes.  Then bring up and hit return.  That should send the command and wake up the display.

Do you have a Function code to cycle the display, like Fn-F8?  Have you tried it?  Sometimes cycling through the primary and secondary will wake them up.  There might be a setting in BIOS which affects the behavior of your cycle switch.

Have you turned modesetting to off?  Search nomodeset.

---

### Post by jcobban on 2013-01-29
> **tgalati4 said:**
> That would be a problem.  You could type the command in a terminal, but don't hit return.  Change the 2 above to 1 for primary display.  On the terminal's window, put "Always on Top" and "Maximize".  Then put the laptop to sleep.  Wait for 5 minutes.  Then bring up and hit return.  That should send the command and wake up the display.

Do you have a Function code to cycle the display, like Fn-F8?  Have you tried it?  Sometimes cycling through the primary and secondary will wake them up.  There might be a setting in BIOS which affects the behavior of your cycle switch.

Have you turned modesetting to off?  Search nomodeset.

I tried your suggestion for using the terminal but got no results.

I am trying to get the main display to work.  I am not going on to the issue of multiple displays until I get the first display working.  I cannot for the life of me find the operator's guide for my laptop on the Dell website, but the F1 key has a picture of an open laptop separated from a picture of a display by an or bar, so I tried holding down the function shift and pressing F1 a few times.  Nothing happened.

I know about nomodeset but you lose a lot of functionality when you use it and I do not see anything in any of the recent posts to indicate that there are any systems requiring it except for those with very old graphics cards.

I am still stuck with the catch 22:  I can have full resolution on the display or I can be able to close the lid on my laptop, but I cannot have both.

---


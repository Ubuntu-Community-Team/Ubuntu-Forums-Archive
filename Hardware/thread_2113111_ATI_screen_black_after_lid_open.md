---
title: "ATI screen black after lid open"
date: 2013-02-06
forum: Hardware
---

### Post by jcobban on 2013-02-06
If I use the proprietary driver for the AMD/ATI graphics on my laptop when I close and then reopen the lid of my laptop the display comes back on.  However that driver supports a maximum virtual display of 1600x1600, so I cannot run an attached full HD (1920x1080) display at full resolution.

If I use the open Xorg driver it gives me a virtual display of 8192x8192 so I can use an attached full HD display.  However in that case if I close the laptop and then reopen it, the system suspends and resumes but the display remains dark.  The only recovery I have found is to reboot, which defeats the point of the suspend/resume.

I am looking for suggestions to try and resolve this problem with the open driver.

I suspect that there is some issue with the configuration scripts, either Xorg or lid.sh:

With the open driver loaded xrandr --verbose returns:

```
$ sudo xrandr --verbose
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x51
	Timestamp:  23137
	Subpixel:   no subpixels
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	load detection: 1 (0x00000001)	range:  (0,1)
LVDS connected 1366x768+0+0 (0x55) normal (normal left inverted right x axis y axis) 344mm x 194mm
	Identifier: 0x52
	Timestamp:  23137
	Subpixel:   horizontal rgb
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       0
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID:
		00ffffffffffff0030e4e30200000000
		00140104902213780a09159d5f599b27
		19505400000001010101010101010101
		010101010101b01d56c650002a302430
		350058c210000019ec1356c650002e30
		2430350058c210000019000000fe0050
		50435446803135365748340a00000000
		00004131960000000001010a202000ef
	scaling mode:	Full
		supported: None         Full         Center       Full aspect 
  1366x768 (0x55)   76.0MHz -HSync -VSync *current +preferred
        h: width  1366 start 1402 end 1450 total 1564 skew    0 clock   48.6KHz
        v: height  768 start  771 end  776 total  810           clock   60.0Hz
  1366x768 (0x56)   51.0MHz -HSync -VSync
        h: width  1366 start 1402 end 1450 total 1564 skew    0 clock   32.6KHz
        v: height  768 start  771 end  776 total  814           clock   40.1Hz
  1280x720 (0x57)   74.5MHz -HSync +VSync
        h: width  1280 start 1344 end 1472 total 1664 skew    0 clock   44.8KHz
        v: height  720 start  723 end  728 total  748           clock   59.9Hz
  1152x768 (0x58)   71.8MHz -HSync +VSync
        h: width  1152 start 1216 end 1328 total 1504 skew    0 clock   47.7KHz
        v: height  768 start  771 end  781 total  798           clock   59.8Hz
  1024x768 (0x59)   63.5MHz -HSync +VSync
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   47.8KHz
        v: height  768 start  771 end  775 total  798           clock   59.9Hz
  800x600 (0x5a)   38.2MHz -HSync +VSync
        h: width   800 start  832 end  912 total 1024 skew    0 clock   37.4KHz
        v: height  600 start  603 end  607 total  624           clock   59.9Hz
  848x480 (0x5b)   31.5MHz -HSync +VSync
        h: width   848 start  872 end  952 total 1056 skew    0 clock   29.8KHz
        v: height  480 start  483 end  493 total  500           clock   59.7Hz
  720x480 (0x5c)   26.8MHz -HSync +VSync
        h: width   720 start  744 end  808 total  896 skew    0 clock   29.9KHz
        v: height  480 start  483 end  493 total  500           clock   59.7Hz
  640x480 (0x5d)   23.8MHz -HSync +VSync
        h: width   640 start  664 end  720 total  800 skew    0 clock   29.7KHz
        v: height  480 start  483 end  487 total  500           clock   59.4Hz
HDMI-0 disconnected (normal left inverted right x axis y axis)
	Identifier: 0x53
	Timestamp:  23137
	Subpixel:   horizontal rgb
	Clones:    
	CRTCs:      0 1
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	underscan vborder: 0 (0x00000000)	range:  (0,128)
	underscan hborder: 0 (0x00000000)	range:  (0,128)
	underscan:	off
		supported: off          on           auto        
	coherent: 1 (0x00000001)	range:  (0,1)

```

lid.sh contains:

```
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
```

---

### Post by jcobban on 2013-02-06
Things I have tried, and which do not work:
[LIST=1]
[*]Ctrl-Alt-T does not open a visible terminal session.
[*]telnet into the system and issue "sudo restart lightdm" results in hearing the bongo drums, but the screen remains black.
[*]telnet into the system and issue "radeontool light on".  Returns "cannot find ctrl region".
[/LIST]

---


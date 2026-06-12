---
title: "Touchscreen calibration and direction problems"
date: 2008-10-29
forum: Hardware
---

### Post by maddis on 2008-10-29
I know there is have been already tons of threads regarding touchscreen problems, but I couldn't find anything that would help me with this current problem.

I have pc with built-in touchscreen. It's running Ubuntu 8.04. Xorg is configured to use evtouch driver and touch is working at some level. X- and Y-axis are inverted and calibration is off.

The biggest difference to other instructions are that in my hardware there isn't any specific touchscreen driver, but instead the touchscreen is shown as USB serialport and I use modified inputattach to make the device that evtouch uses. Inputattach is modified by adding support for gunze - protocol. 

Touchscreen USB-serial is in device /dev/ttyUSB0 and after inputattach the binary data can be read from /dev/input/mouse2.

I tried to run the ev_calibrate, but it failed saying something about invalid ioctl, which I think, is because inputattach and not the real device. Also that's why the udev doesn't regocnice it and device node is not generated.

These are the pages I've tried:

[http://ubuntuforums.org/showpost.php?p=4782599&postcount=862]("http://ubuntuforums.org/showpost.php?p=4782599&postcount=862")
[http://ubuntuforums.org/showpost.php?p=4784444&postcount=869]("http://ubuntuforums.org/showpost.php?p=4784444&postcount=869")

Have someone got touchscreen working with inputattach and how did you do it? Or any idea what to do to get X- and Y-axis correct direction and calibration fixed? It seems that no matter what values I give in xorg.conf they don't do anything.

Here is the touchscreen part of the xorg.conf

```

Section "InputDevice"
	Identifier 	"touchscreen"
	Driver		"evtouch"
	Option		"Device" "/dev/input/mouse2"
	Option		"DeviceName" "touchscreen"
	Option		"MinX" "2"
	Option		"MaxX" "1000"
	Option		"MinY" "2"
	Option		"MaxY" "1000"
	Option		"SwapXY" "1"
#	Option		"SwapY" "1"
	Option		"ReportingMode" "Raw"
#	Option		"Calibrate" "1"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"touchscreen"
EndSection

```

---

### Post by maddis on 2008-10-30
Some new info.

I deleted everything related to touchscreen from xorg.conf and still cursor moves when touching the screen. So it seems that Xorg takes the /dev/input/mouse2 device as mouse device when ever inputattach is running.

I'm guessing this might be the cause why it seems that no options goes through to actual driver. I tried evtouch and plpevtch. In log I can see that both drivers are installed(of course not at the same time), but both seems to ignore options. plpevtch should print calibration values there when enabled, but no.

This might not be so much hardware related anymore after all.

---

### Post by maddis on 2008-10-30
Good news. I finally got it working. I was using wrong device. inputattach creates two device. /dev/input/mouse2 and /dev/input/event8 and the later one was the correct one. I noticed that second device by accident.

With plpevtch driver touch was working ok, but with evtouch there is only 4 points in X-axis and 5 in Y-axis. I'm guessing that is just configuration issue. Or then I'll use the plpevtch driver instead.

---

### Post by hugoinventore on 2008-11-26
Hello maddis.

I'm having exactly the same problem but I'm didn't understand how you correct the problem. Could you explain the exact steps?

I install the evtouch and done the calibration but when I touch in one place in the screen the mouse shows in the opposite side.

thank you in advance.

hugo

---

### Post by maddis on 2009-01-09
> **hugoinventore said:**
> Hello maddis.

I'm having exactly the same problem but I'm didn't understand how you correct the problem. Could you explain the exact steps?

I install the evtouch and done the calibration but when I touch in one place in the screen the mouse shows in the opposite side.

thank you in advance.

hugo

Sorry for late answer. Didn't noticed that someone has posted here.

I didn't use evtouch, but ploptouch instead. That's some sort of variant from evtouch. Not sure how it is different, but it works. You can find it here: [http://www.plop.at/en/touchscreen.html]("http://www.plop.at/en/touchscreen.html")

I also used bit modified inputattach to attach the serialport-touchscreen so that the ploptouch understands it. Then it was just matter of finding the correct device that inputattach just made. I used following command: cat /proc/bus/input/devices | egrep -A 4 "Gunze AHL-51S TouchScreen" | egrep -o event[0-9]*

That device can be found in /dev/input - directory. Then gave that device to ploptouch configuration. 

That way I was able to get the touchscreen working just fine.

---


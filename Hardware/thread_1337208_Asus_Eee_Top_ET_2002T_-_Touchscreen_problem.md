---
title: "Asus Eee Top ET 2002T - Touchscreen problem"
date: 2009-11-25
forum: Hardware
---

### Post by tdunk on 2009-11-25
Hi

I have problems calibrating the touchscreen on my new Asus Eee Top ET2002T with Ubuntu 9.04 (same problem with Ubuntu 9.10).

The touchscreen is working, but calibration is of.

Doing:

```
cat /proc/bus/input/devices
```

shows that the panel is a IDEACO IDC 6681.

Accourding to this thread [http://doc.ubuntu-fr.org/asus_eee_top_et2002]("http://doc.ubuntu-fr.org/asus_eee_top_et2002") the panel should be using the evtouch driver.

I have installed the driver like this:

```
sudo apt-get install evtouch*
```

and rebooted.

Unfortunately after evtouch installation the touchscreen does not work at all!

Manually adding

/etc/udev/69-touchscreen.rules

with this line:

```
KERNEL==„event*“, SUBSYSTEM==„input“, ATTRS{idVendor}==„1cb6“, ATTRS{idProduct}==„6681“, SYMLINK+=„input/evtouch“
```

and the following in /etc/X11/xorg.conf:

in section "Serverlayout":

```
InputDevice	"Touch0"
```

and 

```
Section "InputDevice"
	Identifier	"Touch0"
	Driver		"evtouch"
	Option		"device"	"/dev/input/evtouch"
	Option		"MinX"	"1"
	Option		"MinY"	"1"
	Option		"MaxX"	"4096"
	Option		"MaxY"	"4096"
	Option		"ReportingMode" "Raw"
	Option		"Emulate3Buttons" "false"
	Option		"Emulate3Timeout" "50"
	Option		"SendCoreEvents" "on"
	Option		"MoveLimit" "0"
EndSection
```

doesn't help. The touchscreen is still dead.

Trying to run the evtouch calibration tool reports that no evtouch device is found.

Removing the evtouch driver and reebooting makes the touchscreen work again, but still not calibrated!

Any help is very appreciated!

Thanks!

TDUNK

---

### Post by tdunk on 2009-11-27
Found a solution!

Evtouch works on Asus Eee ET2002T!

The event wasn't configured correctly on my xorg.conf, and that was why it didn't work.

Here is my settings that works:

Add this to ServerSection in xorg.conf:

```

    InputDevice    "dummy"
    InputDevice    "touchscreen"

```

and below the SeverSection add this:

```

Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection

Section "InputDevice"
	Identifier	"touchscreen"
	Driver		"evtouch"
	Option		"device"	"/dev/input/event3"
	Option		"TapTimer"	"10"
	Option		"LongTouchTimer"	"1500"
	Option		"MinX"	"10"
	Option		"MinY"	"10"
	Option		"MaxX"	"8196"
	Option		"MaxY"	"8196"
	Option		"ReportingMode" "Raw"
	Option		"Emulate3Buttons" "false"
	Option		"Emulate3Timeout" "50"
	Option		"SendCoreEvents" "on"
	Option		"MoveLimit" "0"
EndSection


```

Please note that my TapTimer and LongTouchTimer is a little special. Default values are TapTimer=200ms, LongTouchTimer=400ms.

Now the Asus Eee ET2002T rocks with a resolution of 1600x900 and perfect touch functionality :D

Rdgs

---

### Post by randomas on 2009-12-02
Hallo, I'm considerring buying one of these machines, but I cannot find any information as to weather the webcam is working under linux, and for me this would be a showstopper.

Is your webcam working? Did you have to jump through hoops to get it working? If so what did you have to do?

Thanks in advance

---

### Post by tdunk on 2009-12-02
I havn't had a look at the webcam, since i'm not using it.

The 2002t is right now running Win7, so I can't check it out, but in Windows/ the webcam identifies as "SPCA2080 PC Camera". 

I hope it helps.

I'll return when the terminal is back to Ubuntu again.

---

### Post by randomas on 2009-12-02
Hmmm ok, from the name alone it would seem logical for it work with the gspca driver, unfortunately googling for that particular hardware code only returns this forum thread! :o

If you manage to check it out and give it a spin that'd be great, thanks a lot! :)

---

### Post by charasoverride on 2010-05-22
Hi, i am trying to install the ET2002T touchscreen and the fact is that ubuntu lucyd detects the touchscreen out of the box using the evtouch drivers. The issue I'm having is that the device often notices a click before it notices a move; that is, if I have the mouse positioned over a button, and then press elsewhere on the screen the button will often be pressed anyway. In fact sometimes only a click is noticed. Do you experience the same behaviour?

In the other hand, the reason why the evtouch symlink was not working is because the file was not good at all.. try this:

```
KERNEL=="event*", SUBSYSTEM=="input", SYSFS{idVendor}=="1cb6", SYSFS{idProduct}=="6681", SYMLINK+="input/evtouch"
```

---


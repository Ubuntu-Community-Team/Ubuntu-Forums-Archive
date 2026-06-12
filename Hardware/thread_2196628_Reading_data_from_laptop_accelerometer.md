---
title: "Reading data from laptop accelerometer"
date: 2013-12-30
forum: Hardware
---

### Post by ferguson.stewart on 2013-12-30
I bought a tablet-laptop hybrid and it's working pretty well.  I'd like  to rotate the screen automatically based on the built-in accelerometer.   I know the accelerometer exists because Windows 8 was using it for this  purpose right before I wiped the machine.  However, when I run **dmesg | grep input** or **hardinfo**, it does not appear in my list if devices.

I searched **/usr/src/linux-headers-3.11.0-14/drivers/input/misc** and **Kconfig** shows that there are a few accelerometer drivers out there already.  

1) How can I make my accelerometer show up in **/dev/** or in udev?
2) One it is set up, how can I identify it and/or apply a specific driver to it?

This is my introduction to hardware integration, so I'm really hoping for some help at the start here.  

Thanks,

---

### Post by tgalati4 on 2013-12-30
Typically what is done is a teardown of the hardware and the chips are examined.  Do a web search and see if anyone has done a teardown for your model tablet.  Once the accelerometer chip is identified, then you can do a web search for linux modules.  If none have been written, then you can search for the cut sheet on the chip and figure out how it is wired to the motherboard.  You might send an email to the tablet manufacturer asking for linux drivers.  Those are always humorous reading.

---

### Post by waterhead on 2013-12-30
Tablet rotation has been a thorn in my side ever since they came out. It seems there isn't always a common bus used for them all. You can first look to see if it is recognized and mapped by your system, with this command:

```
cat /proc/bus/input/devices | grep "Name\|Sysfs"
```

Or just look through the file /proc/bus/input/devices.

---

### Post by coldraven on 2013-12-31
Install Neverball from the Software Centre. You should be able to steer the balls by tilting your machine.
Then do some Googling and find out how Neverball does that. I did this about five years ago when I got this HP laptop but I cannot remember the answer.

---

### Post by waterhead on 2013-12-31
> **coldraven said:**
> Install Neverball from the Software Centre. You should be able to steer the balls by tilting your machine.
Then do some Googling and find out how Neverball does that. I did this about five years ago when I got this HP laptop but I cannot remember the answer.

I believe that game uses the accelerometer as a joystick. That assumes that a driver has been loaded and a joystick node has been created (/dev/input/js0)),and we haven't determined that yet. besides, my tablet does have a /dev/js0, and I can't control the ball by moving the tablet, so it will prove nothing.

If, by using the command in my previous post, you determine it does recognize the accelerometer and creates a device node (event), you can check it using the terminal program 'evtest'. But first you must install it:

```
sudo apt-get install evtest
```

Then, using the event number that the accelerometer is listed under, run it. On my tablet this event number is not persistant, meaning it changes after every reboot. (I used event6 here as an example)

```
sudo evtest /dev/input/event6
```

Rotating the tablet will then change the X/Y/Z coodinate outputs. Use the Control+c key combonation to stop the test. This goes by very quickly, so you can output it to a file for easier reading:

```
sudo evtest /dev/input/event6 > evtest.log
```

Another method to determine the input nodes that may have been created is to probe udev. Again, use the input number that you believe is assigned to your accelerometer:

```
/lib/udev/accelerometer --debug /devices/platform/asus_laptop/input/input6
```

The file 'evtest.log' would then be found in your home folder

These commands are only to determine if your accelerometer is recognized, it will not make auto-rotation work. In fact, auto-rotation has to rotate three things to work properly. The screen, the touchscreen and the mouse.

Anyway, if your system doesn't even load the driver for your accelerometer, you will need to find out what make/model it is. The best way is to first check Windows, in the Device manager. Here you can get some info on the device itself.

Also, when asking for help, you should always give the make/model of your PC/laptop/tablet, and the version of Ubuntu that you are using.

Good Luck!!

---

### Post by djahma on 2014-01-01
This is interesting stuff here.
When I do lsusb I can see the sensor hub containing the accelerometer is there, it's the STMicroelectronics line:
```
[gman@ThinkManjaro ~]$ lsusb
Bus 001 Device 004: ID 056a:00ec Wacom Co., Ltd 
Bus 001 Device 003: ID 0483:91d1 STMicroelectronics 
...

```
but when I do "$ cat /proc/bus/input/devices | grep "Name\|Sysfs" STMicro does not show up. 
However, I can find it under /sys hierarchy. Here the content of /sys/bus/hid/devices/0003:0483:91D1.0002/uevent 
```
DRIVER=hid-sensor-hub
HID_ID=0003:00000483:000091D1
HID_NAME=STMicroelectronics ST_SENSOR_HUB
HID_PHYS=usb-0000:00:1d.0-1.7/input0
HID_UNIQ=ST_SENSOR_HUB
MODALIAS=hid:b0003g0003v00000483p000091D1
```
Does that mean the driver hid-sensor-hub is the best fit for STMicro on my current system? and is the reason why I am not seeing it under /proc/bus/input/devices because STMicro must be speaking a language of its own that the driver does not understand?

---

### Post by waterhead on 2014-01-01
And on my tablet (ExoPC) it is the exact opposite.

To be honest, I am not really knowledgeable on this HID stuff. When I look at the HID subsytem it makes my head spin!

Does it create a device node (/dev/input/eventX)? Or a joystick node (/dev/input/jsX)? You can test if any of the events are associated by using evtest, as I mention earlier. Just test each event, and rotate the tablet looking for output. The joystick node would be tested by installing and using the jstest-gtk program.

In the end, I would think that you would look for a file the shows the "state" of the accelerometer. Then you could make a script that would rotate to the needed orientation determined by the state. That sounds simple, but it still eludes me.

---

### Post by djahma on 2014-01-01
> **waterhead said:**
> 
Does it create a device node (/dev/input/eventX)? Or a joystick node (/dev/input/jsX)? You can test if any of the events are associated by using evtest, as I mention earlier. Just test each event, and rotate the tablet looking for output. The joystick node would be tested by installing and using the jstest-gtk program..

I've tested all files from /dev/input and none matched the sensor. Alala! Some time ago I tested arm Fedora on a basic tablet and rotation worked out of the box with kernel 3.4. Now I have 3.10 on a x86_64 machine, surely the kernel developpers could have gotten this to work!

---

### Post by ferguson.stewart on 2014-01-03
Unfortunately it's not listed here. That list seems to be the same as the output of lsinput.

---

### Post by ferguson.stewart on 2014-01-03
Thanks for the response.  I ran evtest on each event and none of them gave me an accelerometer output.  My keyboard, touchpad, touchscreen, lid switch all worked, but not the accelerometer.

---

### Post by tgalati4 on 2014-01-03
What accelerometer chip does your tablet have?  [http://www.st.com/web/catalog/sense_power/FM89/SC444](http://www.st.com/web/catalog/sense_power/FM89/SC444)

Others seem to be having trouble talking to the sensor hub:

[http://forum.manjaro.org/index.php?topic=9669.0](http://forum.manjaro.org/index.php?topic=9669.0)

Some drivers available for Android:  [http://mydragonboard.org/blog/](http://mydragonboard.org/blog/)

---

### Post by pfpschneider on 2014-02-05
One way to proceed is to use the Industrial IO system to set up the sensors under your sensor hub.

I have code that does this more-or-less-correctly for a Yoga 2 Pro, but with any luck your laptop will work in a very similar fashion.  The code is under heavy development but is getting close to being distributable.  If you want a copy, send me email at [email]pfpschneider@gmail.com[/email]

Note that the IIO system is not a simple one, particularly in its current state, and is not guaranteed to work well.  It is also not enabled in all Linux distributions.  I'm using Fedora 20, which has everything correctly set up.  If you see hid_sensor_accel_3d in lsmod then the kernel modules are available and correctly enabled.

---

### Post by pfpschneider on 2014-04-07
This code is available from [https://github.com/pfps/yoga-laptop](https://github.com/pfps/yoga-laptop)

> **pfpschneider said:**
> One way to proceed is to use the Industrial IO system to set up the sensors under your sensor hub.

I have code that does this more-or-less-correctly for a Yoga 2 Pro, but with any luck your laptop will work in a very similar fashion.  The code is under heavy development but is getting close to being distributable.  If you want a copy, send me email at [EMAIL="pfpschneider@gmail.com"]pfpschneider@gmail.com[/EMAIL]

Note that the IIO system is not a simple one, particularly in its current state, and is not guaranteed to work well.  It is also not enabled in all Linux distributions.  I'm using Fedora 20, which has everything correctly set up.  If you see hid_sensor_accel_3d in lsmod then the kernel modules are available and correctly enabled.

---

### Post by kwoby on 2014-05-22
Does somebody know how to enable the keyboard mouse touchscreen rotation after having rotated manually the screen in Systems ?
 Automatically rotate everything would be better but I do not know how to read out the accelerometer.

---

### Post by kwoby on 2014-05-24
somebody an idea?

---


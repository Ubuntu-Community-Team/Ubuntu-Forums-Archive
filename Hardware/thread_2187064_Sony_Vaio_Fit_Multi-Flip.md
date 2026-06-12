---
title: "Sony Vaio Fit Multi-Flip"
date: 2013-11-10
forum: Hardware
---

### Post by solars on 2013-11-10
I hope this is in the right section.

This thread is intended to collect information on how to setup a **Sony Vaio Fit Multi-Flip** under Ubuntu.
I will extend the information more and more .. please share your information/corrections.

[B]Enable Silent Mode
[/B]
> echo 'silent' | sudo tee /sys/devices/platform/sony-laptop/thermal_control

The available modes are listed in the file thermal_profiles:
balanced, silent, performance


**Stylus Input**

The touch display is recognized, however, to get it working under the wacom driver
we need to match the Multi-Flip's stylus to the Wacom driver:

> sudo mkdir /etc/X11/xorg.conf.d


edit /etc/X11/xorg.conf.d/52-wacom.conf

and add:
> Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "ID 1b96:0f04|N-trig DuoSense Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection

and restart X (logout or reboot).

xinput in the console should not return these devices among others (IDs can be different)
&#9116;   &#8627; N-trig DuoSense Pen stylus              	id=18	[slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense Pen eraser              	id=19	[slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense Pen pad                 	id=20	[slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense                         	id=21	[slave  pointer  (2)]


**Dualscreen and Screen Rotation**

I've got an external monitor connected and the dispaly of my Vaio flipped back.
I wanted to limit the stylus Input to the Laptop Monitor and needed to invert it.

This can be done with:

1. use **arandr** or **xrandr** to invert the laptop screen (eDP1 in my case)
2. map the stylus device to the laptop screen:

```
xsetwacom --set "N-trig DuoSense Pen stylus" MapToOutput eDP1                                                                              

```

3. rotate the axis
> xsetwacom --set "N-trig DuoSense Pen stylus" Rotate half

**Enable Touch in a Dual Monitor Setup**

For this you need the CTM Method and provide a matrix to transform the coordinates.
This is explained in detail here: [http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)

My setup is:
LEFT External Monitor 1680 x 1050
RIGHT Laptop Touch Display Inverted 1920 x 1080

The matrix I came up with is:
xinput set-prop "N-trig DuoSense" --type=float "Coordinate Transformation Matrix" -0.53333333333333333333 0 1 0 -1.02857142857142857142 1.02857142857142857142 0 0 1


**TODO**

- find out how to read out the Accelerometer to automate rotation when flipping the display
- multi touch?
- how to use NFC (neard recognizes the sensor, but I have no idea how to actually execute scripts with this)

---

### Post by Favux on 2013-11-10
I don't see it in the new output either.  If you still have a windows partition try to get its name and its usb Vendor and Product ID.  That will help us figure out if there is a kernel driver or if it needs a udev rule or something.  It still might be in /sys/devices/platform somewhere.

I was talking about the swivel hinge switch on convertible tablet PCs.  When you find the file and cat it it'll return 0 or 1.  An acclerometer is probably returning degrees.

With xsetwacom Rotate you only have to specify one device.  I would just use the stylus in the commands.  And since eraser and pad are spurious you don't need them in MapToOutput either.  You'll just use a xinput CTM command for touch along side the xsetwacom Rotate command for the stylus.

---

### Post by solars on 2013-11-10
Updated the first message with the changes
I'll try to find out more about the accelerometer under windows

---

### Post by solars on 2013-11-10
do you know a tool to read out the hardware info from windows? I'm not very familiar with it :)

---

### Post by solars on 2013-11-10
I used sisoft sandra, here is the information I found:

[https://gist.github.com/solars/4658a67b8474e7105692](https://gist.github.com/solars/4658a67b8474e7105692)

---

### Post by Favux on 2013-11-10
Attached is  a sample accelerometer script called hdapsrotate from evilphish (attached).  You want to change .txt to .sh although evilphish just had it hdapsrotate.  That accelerometer was located at /sys/devices/platform/hdaps/position.  Degrees expressed as delta x and y I gather.  Don't know if you'd want yours integrated into Magick.

We need to make a custom .conf for a user to match to Wacom instead of telling them to alter a Distro file in /usr/share.  Instructions follow.

To match the Multi-Flip's stylus to the Wacom driver.

Check in /etc/X11/ for a directory folder called xorg.conf.d.  If it is not there create it with:
```
sudo mkdir /etc/X11/xorg.conf.d
```

Then run:
```
gksudo gedit /etc/X11/xorg.conf.d/52-wacom.conf
```
and add as its contents:
```

Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "ID 1b96:0f04|N-trig DuoSense Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection
```
* Note:  for Saucy 13.10 you may need to install the package **gksu**.
Save and Close..  Log out and in or restart.

We still need to check if "ID 1b96:0f04" actually matches.


OK, we know its name now; STM (or STMicroelectronics) Accelerometer Sensor, Model : LSM303DLHC.  Somewhere in Control Panel where the drivers are in one of the many tabs on the driver you should find the name and the usb serial numbers for Vendor and Product ID.  Example for the N-Trig digitizer you found ID 1b96:0f04.  The first is the vendor N-Trig and after the : is the product.

---

### Post by solars on 2013-11-10
Sisoft Sandra is the program I used under windows to get this information.

Unfortunately I can't find this device in the Windows Hardware Manager, there is a HID Hub, some HID devices, but I cannot find this above Model ID anywhere...
No idea how I could get to these details..

---

### Post by Favux on 2013-11-10
lol  Sure I've used Sisoft Sandra before.  Guess it has been a while since I was getting into Window's guts.  I have no idea how to describe how I found that kind of information.  Wandered around in Control Panel's device drivers I think.

STM (or STMicroelectronics) Accelerometer Sensor, Model : LSM303DLHC
[http://www.st.com/web/catalog/sense_power/FM89/SC1449/PF251940](http://www.st.com/web/catalog/sense_power/FM89/SC1449/PF251940)
Vendor ID:  0483  - looks like, from:  [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)

Product ID might be in one of the PDFs.


Looks like name was:  SGS Thomson Microelectronics

---

### Post by solars on 2013-11-10
well this was in lsusb: Bus 002 Device 005: ID 0483:91d1 STMicroelectronics 
but I'm not sure to which device this belongs

damn windows is annoying, this UEFI stuff keeps overwriting my grub

---

### Post by Favux on 2013-11-10
Alright, looks like there are kernel drivers for at least some of their accelerometers:  [http://lxr.linux.no/#linux+v3.12/drivers/misc/lis3lv02d/Kconfig](http://lxr.linux.no/#linux+v3.12/drivers/misc/lis3lv02d/Kconfig)

Location from that link is /sys/devices/platform/lis3lv02d.  Not getting a lot of relevant looking hits to 0483:91d1.  But it is probably worth looking in a current kernel for it.  That should be fun.  Better check in sys/devices first.  You're in 3.10 i.e. kernel 3.11?

Also see name as ST Microelectronics.

---

### Post by solars on 2013-11-10
it's been at least 5 years since I last compiled a Kernel haha, too lazy
but I will look into it, thanks a lot

the current kernel is 3.11 yes
I didn't find anything relevant in /sys/devices/platform
but I cannot grep there, so it's a bit difficult

---

### Post by solars on 2013-11-11
in the meantime: does anyone know how to use neard and those nfc tools to actually use nfc tags?

---

### Post by solars on 2013-11-11
looks like there is a wifi problem

if I connect to the wifi directly, speedtest.net shows 0.6mbit
if I connect the wifi router (sony accessory) to ethernet, and then to this wifi, speedtest.net shows 0.6mbit
if I connect my tablet to the wifi, then use usb tethering to the laptop, I get 15mbit...

I heard that there are wifi problems with the vaio pro as well..

---

### Post by man-brunner on 2013-11-12
Problem of not working touchpad and keyboard after suspend:

For touchpad, change /etc/default/grub:
```

# old: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
# new:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash atkbd.reset" 

```
then run update-grub, reboot
([source]("http://askubuntu.com/questions/38797/keyboard-not-working-after-suspend-to-ram-sleep"))

Keyboard:
create /etc/pm/sleep.d/keyboard_wake_hack-resume:
```

xinput set-prop 12 "Device Enabled" 0
xinput set-prop 12 "Device Enabled" 1

```
(you keyboard device id may vary, check xinput)

---

### Post by Favux on 2013-11-12
Hi man-brunner,

Welcome to Ubuntu forums!


Since ID # can change, especially if you plug in another usb device, I'd suggest it would be better to use the "device name" from **xinput list** (in quotes) for the xinput commands.

---

### Post by naruto2mars on 2013-11-13
Speedtest never gives reel estimation (at least for me, always givin me about 50mb when I know I have 200mb). Download a file you'll see if there is really a difference.
As far as I know the wifi problems on the others vaio were the strength of the signal and the lost of signal.

---

### Post by naruto2mars on 2013-11-13
For multitouch look [here]("https://wiki.ubuntu.com/Multitouch"). You could try touchegg or easystroke.

---

### Post by solars on 2013-11-14
what would be very important is a driver/way to control this annoying fan..

---

### Post by naruto2mars on 2013-11-14
You should try pwmconfig to see if it can detect your fan and more importantly stop it.
You need to install lm-sensors to execute the command. If it works, install fancontrol to create a configuration file to control your fan.

---

### Post by solars on 2013-11-14
There is no pwmconfig cmd on my installation or in the lm-sensors package. Only sensors-detect which I used and doesn't return any fans :(

Edit: seems to be in fancontrol
[B]/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
[/B]

---

### Post by naruto2mars on 2013-11-14
Change your grub config by changing this line : 
```
GRUB_CMDLINE_LINUX_DEFAULT= "quiet splash **acpi_osi=Linux**"
```

---

### Post by solars on 2013-11-14
I changed it, but what does it do?

---

### Post by naruto2mars on 2013-11-14
I suppose you've done : 
```
sudo update-grub
```
and reboot your computer. Now retry pwmconfig or fancontrol to see if it works.

---

### Post by solars on 2013-11-15
Yes, that's what I did
but there is still nothing recognized.. :(

---

### Post by solars on 2013-11-15
for me it seems as if there are problems with the wifi as well, I think I've often got a very bad connection but I'm not sure
if it's caused by the laptop

however, there have been similar reports for the vaio pro etc.. so if anyone knows a solution, please post

---

### Post by solars on 2013-11-16
using the silent mode (see first post) it's a lot more silent.
the fan turns off below 48C for me

I wonder if laptop mode tools help further and how to configure powertop etc in general for this device..

---

### Post by solars on 2013-11-16
> **Favux said:**
> Alright, looks like there are kernel drivers for at least some of their accelerometers:  [http://lxr.linux.no/#linux+v3.12/drivers/misc/lis3lv02d/Kconfig](http://lxr.linux.no/#linux+v3.12/drivers/misc/lis3lv02d/Kconfig)

Location from that link is /sys/devices/platform/lis3lv02d.  Not getting a lot of relevant looking hits to 0483:91d1.  But it is probably worth looking in a current kernel for it.  That should be fun.  Better check in sys/devices first.  You're in 3.10 i.e. kernel 3.11?

Also see name as ST Microelectronics.

The module seems to be enabled already:

lsmod|grep lis                                                                                                           
lis3lv02d              20156  0 
input_polldev          13896  1 lis3lv02d


However, there is no such file:
/sys/devices/platform/lis3lv02d

any idea?

---

### Post by Favux on 2013-11-16
input_polldev does maybe sound like a joystick.  So maybe looking for /joystick somewhere in /platform?

---

### Post by solars on 2013-11-16
no luck either..

---

### Post by bkloppenborg on 2013-11-16
I'm considering buying a Sony Vaio 15a, but have read a series of mixed reviews. Most of the issues relate to the fan being loud on the 13a and 14a models and some issues relating to the Windows 8.1 installation messing up the touchscreen.

Solars, could you update your original post to include which model you purchased, what works, what doesn't work, and what you haven't tried? This would really help me decide if this is the machine for me. Thanks!

---

### Post by solars on 2013-11-17
the model is the 13A with i7 - I've tried everything mentioned in the post and follow up messages
everything in the first post is not a problem

the stylus works perfectly under linux, silent mode results in an acceptable level of the fan
it turns off at 47C but usually is around 50C, so it's still not silent, but better than in the normal mode

anyone know how to test pressure sensitivity (if this works under linux)? I didn't test that

---

### Post by Favux on 2013-11-17
Pressure sensitivity of the stylus should work right away with MyPaint.  Other app.s such as Xournal require some setup.  Gimp and Inkscape need the extended input device configured.

Gimp:  Edit > Preferences > Input Devices > Configure Extended Input Devices.  In the Device drop down select the device with stylus appended to it and then in the Mode drop down set it to Screen.


Looks like it might be worthwhile to download Saucy's 3.11 kernel and look in it.  There seems to be at least one module since two of the manufacturer's accelerometers are supported.  Even if yours isn't yet sometimes you can get lucky and the module just needs to have a match for yours to support it.  Which might be simple to do, again with luck.  We've even been lucky enough, for example with serial to usb cable support modules, to steal code from another manufacturer’s driver and put it in the one we want if it is simple and obvious enough.  The main requirement is the driver/module needs to be a stand alone module and not an inbuilt one.  If stand alone you can compile it by itself.  If inbuilt then you have to compile the kernel, which probably isn't worth it.  Also if stand alone you want everything in one file not distributed in several that other modules use like with the HID part of the kernel.  Then you've got to compile multiple modules.

I just finished adding touch icons to Magick's app indicator and adding gnome-shell 3.8 extension support.  So there may be a lull and I'll have a little time to look.  The kernel support for [Non-Wacom Tablets HOW TO]("http://ubuntuforums.org/showthread.php?t=1946486") shows you how to download the kernel and prepare for compiling.

---

### Post by nise-designer on 2013-11-17
Hello, I just bought a Sony VAIO TAP 11 and installed Ubuntu 13.10.  I found that mouse and touch screen difficult to control and paused occured.  It resumed after follow you instruction to correct X-window setting.  thanks

> **solars said:**
> I hope this is in the right section.

This thread is intended to collect information on how to setup a **Sony Vaio Fit Multi-Flip** under Ubuntu.
I will extend the information more and more .. please share your information/corrections.

[B]Enable Silent Mode
[/B]


The available modes are listed in the file thermal_profiles:
balanced, silent, performance


**Stylus Input**

The touch display is recognized, however, to get it working under the wacom driver
we need to match the Multi-Flip's stylus to the Wacom driver:



edit /etc/X11/xorg.conf.d/52-wacom.conf

and add:


and restart X (logout or reboot).

xinput in the console should not return these devices among others (IDs can be different)
&#9116;   &#8627; N-trig DuoSense Pen stylus                  id=18    [slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense Pen eraser                  id=19    [slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense Pen pad                     id=20    [slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense                             id=21    [slave  pointer  (2)]


**Dualscreen and Screen Rotation**

I've got an external monitor connected and the dispaly of my Vaio flipped back.
I wanted to limit the stylus Input to the Laptop Monitor and needed to invert it.

This can be done with:

1. use **arandr** or **xrandr** to invert the laptop screen (eDP1 in my case)
2. map the stylus device to the laptop screen:

```
xsetwacom --set "N-trig DuoSense Pen stylus" MapToOutput eDP1                                                                              

```

3. rotate the axis


**Enable Touch in a Dual Monitor Setup**

For this you need the CTM Method and provide a matrix to transform the coordinates.
This is explained in detail here: [http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)

My setup is:
LEFT External Monitor 1680 x 1050
RIGHT Laptop Touch Display Inverted 1920 x 1080

The matrix I came up with is:
xinput set-prop "N-trig DuoSense" --type=float "Coordinate Transformation Matrix" -0.53333333333333333333 0 1 0 -1.02857142857142857142 1.02857142857142857142 0 0 1


**TODO**

- find out how to read out the Accelerometer to automate rotation when flipping the display
- multi touch?
- how to use NFC (neard recognizes the sensor, but I have no idea how to actually execute scripts with this)

---

### Post by Favux on 2013-11-17
Downloaded the current Saucy kernel source and looked in its 3.11.0 folder.  Found the STM accelerometers we knew about at linux-3.11.0/drivers/misc/lis3lvo2d.  Looking at the header file lis3lvo2d.h and a couple of the specific accelerometer files, adding the lsm doesn't look obvious.  We'd need a clue as to how close the capabilities/spec.s of the LSM are to the existing ones.  Need to look at it a bit more I suppose.  Don't see anything for the LSM (your model accelerometer) anywhere else.  That needs more searching too.

But if I strike out (and anyone who cares to join me) then we need to download the current kernel from kernel.org and look in there.  With luck someone's added support for your accelerometer.  If so it is possible we could backport it to Saucy's 3.11.


Edit:  **[SIZE=3]Found it![/SIZE]**
According to the st_accel.h its there and called "lsm303dlhc_accel".  It's located at linux-3.11.0/drivers/iio/accel.  From the Makefile whatever the name of the kernel object or .ko (i.e. driver) is it should have accel in it.  So:
```
lsmod | grep accel
```
If it isn't there it just may be a case of compiling and installing it.  If it is there it may be a udev rule is lacking to match it.

Edit2:
It's in 3 files:  st_accel_core.c, st_accel_i2c.c, st_accel_spi.c.  The names in the Makefile that should apply look to be:
```
st_accel-y := st_accel_core.o
st_accel-$(CONFIG_IIO_BUFFER) += st_accel_buffer.o

obj-$(CONFIG_IIO_ST_ACCEL_I2C_3AXIS) += st_accel_i2c.o
obj-$(CONFIG_IIO_ST_ACCEL_SPI_3AXIS) += st_accel_spi.o
```
So just add a 'k' in front of the 'o' and you should have a name to modprobe with, e.g.  st_accel_buffer.ko.  My guess is that it would be a two module driver the buffer one and one of the last two.

---

### Post by solars on 2013-11-17
Hi there,

Not sure if I understood right :) I found:

/lib/modules/3.11.0-13-generic/kernel/drivers/iio/accel/st_accel.ko
/lib/modules/3.11.0-13-generic/kernel/drivers/iio/accel/st_accel_i2c.ko
/lib/modules/3.11.0-13-generic/kernel/drivers/iio/accel/st_accel_spi.ko

and loaded them:

 lsmod|grep accel                                                                                                
st_accel_spi           12651  0 
st_sensors_spi         12909  1 st_accel_spi
st_accel_i2c           12651  0 
st_sensors_i2c         12823  1 st_accel_i2c
st_accel               13708  2 st_accel_i2c,st_accel_spi
st_sensors             16465  1 st_accel
industrialio_triggered_buffer    12882  1 st_accel
industrialio           52374  6 st_accel_i2c,st_accel_spi,st_sensors,industrialio_triggered_buffer,st_accel,kfifo_buf

but I didn't see any output in /sys/devices.. not sure where this should go then?

---

### Post by Favux on 2013-11-17
Now that you've modprobed and loaded the modules if working it looks like it should be showing in platform.  I'm seeing code like:
```
	if (!plat_data)
		plat_data =
			(struct st_sensors_platform_data *)&default_accel_pdata;
```
and:
```
	err = st_accel_common_probe(indio_dev, client->dev.platform_data);
```
Can't tell where.

I guess it could be because there isn't a udev rule.  I see a 61-accelerometer.rules in /lib/udev/rules.d and a accelerometer binary at /lib/udev.  My 61-accelerometer.rules only has one rule in it.
```
SUBSYSTEM=="input", ACTION!="remove", ENV{ID_INPUT_ACCELEROMETER}=="1", IMPORT{program}="accelerometer %p"
```
When you loaded the modules did a new node(s) show up in /dev/input?


Edit:  From this link:  [https://wiki.archlinux.org/index.php/STMicroelectronics_LSM303DLH_Accelerometer/Magenetometer](https://wiki.archlinux.org/index.php/STMicroelectronics_LSM303DLH_Accelerometer/Magenetometer)  I found Luke Ross who claims he got it working for rotation.  See:  [http://lukeross.name/static/dell/](http://lukeross.name/static/dell/)

Hopefully his patch is out of date.  The current code seems to have axis stuff and is hopefully working.

---

### Post by solars on 2013-11-18
I guess you mean this driver: [http://www.st.com/web/catalog/tools/FM147/CL1818/SC1885/PF258119](http://www.st.com/web/catalog/tools/FM147/CL1818/SC1885/PF258119)

Can you tell me how to compile/use it? :)

---

### Post by Favux on 2013-11-18
That driver is from 6/12.  Doubt it would compile on a current kernel.  It might but there is no README so nothing tells us where we are suppose to place the module(s) or anything.  Still in /lib/modules/3.11.0-13-generic/kernel/drivers/iio/accel I guess.  I think it might be a detour.  I'm hoping the current kernel driver has all of that capability and it is a question of us figuring out where the input is and how to read it.

We are basically duplicating this thread from January 2011:  [http://ubuntuforums.org/archive/index.php/t-1658480.html](http://ubuntuforums.org/archive/index.php/t-1658480.html)

As you can see Luke got it working with his patch.  Not real optimistic an almost 3 year old patch and driver/module would work now.  I found out where the output was after the patch from his perl script.  It was at /sys/bus/i2c/devices/i2c-2/2-0019/data.  That or a similar place is worth a look.  Which brings up another issue.  I'm not sure which modules need to be loaded.  He's using the /lib/modules/3.11.0-13-generic/kernel/drivers/iio/accel/st_accel_i2c.ko.  So maybe you need to reboot and modprobe only st_accel_i2c?  Don't know if that will bring along any other module it needs.

This explains what we are up against:  [https://bbs.archlinux.org/viewtopic.php?id=132849](https://bbs.archlinux.org/viewtopic.php?id=132849)

Now someone suggests the data might be in a WMI (or acpi I suppose).  If so we might be able to read that.  That's what Magick Rotation does.  The WMI or ACPI creates a "hotkeys" input node for the keyboard and the swivel hinge signal is in there with the keys.  I know how to read that.  So it is important to know if there is a new input node in /dev/input when you modprobe the accelerometer driver.  It would also show up in the xinput list command run in a terminal.  So post that before you modprobe and let's see what's there.  With Magick we use a udev rule to create an input node for the swivel hinge signal in "hotkeys" and then read that.


Edit:  **[SIZE=3]Think I have it.[/SIZE]**
IIO is a new kernel subsystem.  This talks about it and how to read:  [https://archive.fosdem.org/2012/schedule/event/693/127_iio-a-new-subsystem.pdf](https://archive.fosdem.org/2012/schedule/event/693/127_iio-a-new-subsystem.pdf)  That's where the input should be, /sys/bus/iio/devices/iio:deviceX.  But does that produce human readable output or is that where a code hook from an app. reads it?  Also if it uses the buffer module is position data in the buffer and we need to trigger a dump from it?

---

### Post by solars on 2013-11-19
ok now I was a bit confused what to try next :)

I've loaded the modules (st_accel_i2c loads st_accel) but there is nothing in /sys/bus/iio/devices

---

### Post by Favux on 2013-11-19
> ok now I was a bit confused what to try next
You're not alone.  Do you see a st_accel_buffer in /lib/modules/3.11.0-13-generic/kernel/drivers/iio/accel or **lsmod**?  Because your output from **lsmod** in post #35 talked about the buffer being triggered.

Near as I can tell the file you're looking for should be called "data".

Currently my take is either one of two things is going on.
1)  The user readable file is there, we just haven't found it.  This is our only hope I'm thinking.
2)  The accel's kernel drivers don't actually report to file you can cat and determine the value of.  Only two of the four OEM's drivers Magick supports do that.  All 4 do report the swivel hinge state through the "hotkeys".  I gather that was why Luke wrote his patch, to get the accel chip reporting in a way he could use.  Otherwise the values are being reported but over a bus and we have to figure out how to read that.  Need to know the bus # and so on.  Near as I can tell this is the i2c or SM Bus.  So we need i2cget I think and figure out how to use it.  I went ahead and installed i2c-tools:
```
sudo apt-get install i2c-tools
```
To get i2cget and more importantly the manuals.  But looking at **man i2cdetect** wasn't too encouraging.  And **man i2cget** was scary with its chip damage warning.  I think we need a hardware guru if we try this route.

So we really need a user readable data file.  If one isn't there already we need someone who knows enough C and knows enough about the kernel to patch the module to get it reporting to a file like Luke did.

---

### Post by miatawnt2b on 2013-11-24
Are there any updates on this?

---

### Post by riccardosl45 on 2013-11-25
Hello, I'm also searching info about compatibility with this laptop, are soundcard and wirless working fine under ubuntu?

---

### Post by solars on 2013-11-29
I don't have time enough to try it, at the moment

The soundcard and wireless is working fine and out of the box.

---

### Post by yarmiganosca on 2013-12-02
I have a Flip 13A, and while the sound and wifi work fine, Ubuntu 13.10 doesn't recognize my touchpad. Has anyone else encountered similar problems?

---

### Post by amendezsoto on 2014-01-06
> **yarmiganosca said:**
> I have a Flip 13A, and while the sound and wifi work fine, Ubuntu 13.10 doesn't recognize my touchpad. Has anyone else encountered similar problems?
I have the same model and the same problem. Any idea how to fix it?, I am using Ubuntu gnome 13.10.

---

### Post by miatawnt2b on 2014-01-07
Notebookreview has a pretty big flip community. Maybe try posting there to find the manufacturer and go from there.

---

### Post by miatawnt2b on 2014-02-04
Has anyone had luck getting multitouch working on the touchscreen. 13.10 out of the box only registers what would be the equivlent of a left mouse click and drag.  I can't scroll.
Ideas?

---

### Post by Johan Gambolputty on 2014-02-04
> **man-brunner said:**
> Problem of not working touchpad and keyboard after suspend:

For touchpad, change /etc/default/grub:
```

# old: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
# new:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash atkbd.reset" 

```
then run update-grub, reboot
([source]("http://askubuntu.com/questions/38797/keyboard-not-working-after-suspend-to-ram-sleep"))

Keyboard:
create /etc/pm/sleep.d/keyboard_wake_hack-resume:
```

xinput set-prop 12 "Device Enabled" 0
xinput set-prop 12 "Device Enabled" 1

```
(you keyboard device id may vary, check xinput)

Running xubuntu 14.04 daily build, using a sony vaio 13 fit 13A (SVF13N1L2ES), I could not get the keyboard to work after resuming from suspend even using the above (although the grub change did fix the touchpad after suspend).
In fact the above wake hack prevented my machine from suspending.
Instead, I changed /etc/pm/sleep.d/keyboard_wake_hack-resume to be:

```

#! /bin/sh
case $1 in
     suspend|suspend_hybrid|hibernate)
    echo suspend > /dev/null
        ;;
     resume|thaw)
xinput set-prop 12 "Device Enabled" 0
xinput set-prop 12 "Device Enabled" 1
    :
        ;;
esac

```

then run

```

sudo chmod aug+x /etc/pm/sleep.d/keyboard_wake_hack-resume

```

Next time you suspend and resume, your keyboard should be good to go.

---

### Post by amendezsoto on 2014-02-13
Any idea how to fix this problem with the touchpad?, supposedly it was resolved with the Kernel 3.11 but it doesn't work 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442)

---

### Post by miatawnt2b on 2014-02-14
I was able to get multitouch working on the touchscreen by installing "touchegg" in synaptic. I had to edit to conf file for 2 finger scrolling to get the scroll direction correct.
```
<touchégg>
    
    <settings>
        <property name="composed_gestures_time">0</property>
    </settings>
    

    <application name="All">
        
        <gesture type="TAP" fingers="2" direction="">
            <action type="MOUSE_CLICK">BUTTON=3</action>
        </gesture>
    
        <gesture type="TAP" fingers="3" direction="">
            <action type="MOUSE_CLICK">BUTTON=2</action>
        </gesture>

        <gesture type="TAP" fingers="5" direction="">
            <action type="CLOSE_WINDOW"></action>
        </gesture>

        <gesture type="DRAG" fingers="2" direction="ALL">
            <action type="SCROLL">SPEED=7:INVERTED=true</action>
        </gesture>


        <gesture type="DRAG" fingers="3" direction="UP">
            <action type="MAXIMIZE_RESTORE_WINDOW"></action>
        </gesture>
        
        <gesture type="DRAG" fingers="3" direction="DOWN">
            <action type="MINIMIZE_WINDOW"></action>
        </gesture>
        

        <gesture type="DRAG" fingers="3" direction="LEFT">
            <action type="MOVE_WINDOW"></action>
        </gesture>
        
        <gesture type="DRAG" fingers="3" direction="RIGHT">
            <action type="MOVE_WINDOW"></action>
        </gesture>

        <gesture type="DRAG" fingers="4" direction="UP">
            <action type="SEND_KEYS">Super+W</action>
        </gesture>
        
        <gesture type="DRAG" fingers="4" direction="DOWN">
            <action type="SHOW_DESKTOP"></action>
        </gesture>


        <gesture type="PINCH" fingers="3" direction="ALL">
            <action type="RESIZE_WINDOW"></action>
        </gesture>
        
        <gesture type="PINCH" fingers="5" direction="ALL">
            <action type="SEND_KEYS">Alt+F1</action>
        </gesture>

    </application>


    <application name="Okular, Gwenview">

        <gesture type="PINCH" fingers="2" direction="IN">
            <action type="SEND_KEYS">Control+KP_Add</action>
        </gesture>

        <gesture type="PINCH" fingers="2" direction="OUT">
            <action type="SEND_KEYS">Control+KP_Subtract</action>
        </gesture>

        <gesture type="ROTATE" fingers="2" direction="LEFT">
            <action type="SEND_KEYS">Control+L</action>
        </gesture>

        <gesture type="ROTATE" fingers="2" direction="RIGHT">
            <action type="SEND_KEYS">Control+R</action>
        </gesture>

    </application>


    <application name="Chromium-browser, Dolphin">

        <gesture type="DRAG" fingers="2" direction="LEFT">
            <action type="SEND_KEYS">Alt+Left</action>
        </gesture>

        <gesture type="DRAG" fingers="2" direction="RIGHT">
            <action type="SEND_KEYS">Alt+Right</action>
        </gesture>
        
    </application>


</touchégg>
```

I am still having an issue though that screen touches on the gnome title bar don't work at all.  (Activities/username/volume, etc)
Seems very strange since the rest of the screen works fine.

---

### Post by craig9 on 2014-03-08
Sony Vaio Fit Flip Sensors

I realize this is an older thread.   But since its one of the few threads on this I could find I just wanted to add my limited knowledge on the subject to the thread it case it helps someone to actually put together a working solution:

The sensor package in the Sony Vaio Fit Flip (at least the 15inch model I have) lives on the USB bus:
0483:91d1 STMicroEletronics

Interface to it is through the hid-sensor-hub and associated kernel modules via an IIO device interface.

The same chip is used in a many of these convertible laptops including the Yoga 2 and I believe the Yoga.

The kernel modules in the 3.11 kernel has numerous bugs in it that don't make it friendly when talking to the chip.  But have had some success with 3.14.0-rc5 and its hid-sensor-hub modules.

There is a project over on github with some work with initializing the chipset and reading the chip to change orientation for the yoga tablets:
[https://github.com/pfps/yoga-laptop/](https://github.com/pfps/yoga-laptop/)

While running a 3.14.0-rc5 kernel and using the "generic_buffer" utility from that package I was able to see changes in position through the accelerometer by running:
     generic_buffer -C 10 -n accel_3d

It would appear that accelerometer reflections the orientation of the base part of the 2 in 1:
-Z = keyboard is pointing up
+Z = keyboard is pointing down (device upside down)
-X = side near delete key is pointing up (device right side it up)
+X = side near escape key is pointing up (device left side is up)
-Y = front edge w/led is pointing down  (hinge side is up)
+Y = front edge w/led is pointing up (hinge side is down)

There orientation program is the yoga-laptop project is fairly rough but is a good start.   It would appear that the sensor isn't oriented the same in the yoga as the vaio flips, so the orientation application rotates the screen the wrong direction.   But its a good place to start if someone has the time.

There seems to be more that a few sensors in the sensor package:
accel_3d   HID-SENSOR-200073.1       Accelerometer               Can Read x,y,z from it, seems to relate to position/orientation of keyboard part (sensor in base?)
acl           HID-SENSOR-200041.6       Ambient Light sensor       Values seem to change with light level
magna_3d  HID-SENSOR-200083.3      Magnetometer/Compass   Can read x,y,z values
gyro_3d     HID-SENSOR-200076.2      Gyro Sensor                   Values seem random when read
incli_3d      HID-SENSOR-200086.4      Incline Meter                  Seems to relate to Orientation of the screen/hidge part.  (sensor in screen?)

Since the incli_3d sensor measures the orientation of the display, there must be a sensor in the display.   So when base is steady the accel_3d remains unchanged but you see a change in incli_3d when you move the LED screen.   Would have to do more testing to determine which sensor is most accurate in determining when a screen orientation change should occur.   But have to stop playing with laptop for a while as have to do actual work.   Just wanted to document what I had so save some other develop some trouble down the road.

---

### Post by duanekaufman on 2014-03-23
Hello,

I recently purchased a Sony Multi-Flip 15, and I would like to install Linux on it, in a dual-boot configuration.

Could you please provide pointers on _how_ you went about installing Linux?

Things I have found out so far:
I am trying to install from a Debian Live iso, placed on a USB stick using the Universal USB Installer ([http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)In](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)In) order to get the VAIO Flip to boot from the USB stick, I had to get into the BIOS (boot by pressing the Assist button from a shut-down state), and change the UEFI boot option to 'Legacy', then save, exit, reboot again using the Assist button, and choose to boot from USB.

I couldn't re-partition my hard-drive from the install (I need to do it a different way I guess, as the installer couldn't shrink the largest partition on my disk)

I had to switch the BIOS UEFI option back to UEFI so that Windows could boot. So even if I get the partitioning sorted out, how does one dual-boot this machine?

Your insight is appreciated!

Thanks,
Duane

> **solars said:**
> I hope this is in the right section.

This thread is intended to collect information on how to setup a **Sony Vaio Fit Multi-Flip** under Ubuntu.
I will extend the information more and more .. please share your information/corrections.

[B]Enable Silent Mode
[/B]


The available modes are listed in the file thermal_profiles:
balanced, silent, performance


**Stylus Input**

The touch display is recognized, however, to get it working under the wacom driver
we need to match the Multi-Flip's stylus to the Wacom driver:



edit /etc/X11/xorg.conf.d/52-wacom.conf

and add:


and restart X (logout or reboot).

xinput in the console should not return these devices among others (IDs can be different)
&#9116;   &#8627; N-trig DuoSense Pen stylus                  id=18    [slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense Pen eraser                  id=19    [slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense Pen pad                     id=20    [slave  pointer  (2)]
&#9116;   &#8627; N-trig DuoSense                             id=21    [slave  pointer  (2)]


**Dualscreen and Screen Rotation**

I've got an external monitor connected and the dispaly of my Vaio flipped back.
I wanted to limit the stylus Input to the Laptop Monitor and needed to invert it.

This can be done with:

1. use **arandr** or **xrandr** to invert the laptop screen (eDP1 in my case)
2. map the stylus device to the laptop screen:

```
xsetwacom --set "N-trig DuoSense Pen stylus" MapToOutput eDP1                                                                              

```

3. rotate the axis


**Enable Touch in a Dual Monitor Setup**

For this you need the CTM Method and provide a matrix to transform the coordinates.
This is explained in detail here: [http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)

My setup is:
LEFT External Monitor 1680 x 1050
RIGHT Laptop Touch Display Inverted 1920 x 1080

The matrix I came up with is:
xinput set-prop "N-trig DuoSense" --type=float "Coordinate Transformation Matrix" -0.53333333333333333333 0 1 0 -1.02857142857142857142 1.02857142857142857142 0 0 1


**TODO**

- find out how to read out the Accelerometer to automate rotation when flipping the display
- multi touch?
- how to use NFC (neard recognizes the sensor, but I have no idea how to actually execute scripts with this)

---

### Post by amw2 on 2014-04-24
Hi all.
And thank you all for these investigations :)

I've just bought Sony Vaio Fit multi-flip SVF13N2J2RS and installed kubuntu 14.04.
I've applied the keyboard hack below but keyboard still not resumed correctly aftre suspend.
More, I have a very strange behaviour, it resumes OK once, then not resumed on next suspend/resume, next resumed on third suspend/resume and so on.
More detailed is as the following:

1. boot-up and login - OK
2. close lid - wait for suspend (LED off) - open lid - resumed - keyboard OK.
3. close lid - wait for suspend (LED off) - open lid - resumed - keyboard is not working.
4. close lid - wait for suspend (LED off) - open lid - resumed - keyboard OK.
5. close lid - wait for suspend (LED off) - open lid - resumed - keyboard is not working.
6. close lid - wait for suspend (LED off) - open lid - resumed - keyboard OK.
...

Additionaly, sometimes keyboard is not working few suspend/resume cycles and sumtimes it resumed but after typing few keys last key seems autorepeated continuously forever.
Any idea what to check to fix the issue?

> **Johan Gambolputty said:**
> Running xubuntu 14.04 daily build, using a sony vaio 13 fit 13A (SVF13N1L2ES), I could not get the keyboard to work after resuming from suspend even using the above (although the grub change did fix the touchpad after suspend).
In fact the above wake hack prevented my machine from suspending.
Instead, I changed /etc/pm/sleep.d/keyboard_wake_hack-resume to be:

```

#! /bin/sh
case $1 in
     suspend|suspend_hybrid|hibernate)
    echo suspend > /dev/null
        ;;
     resume|thaw)
xinput set-prop 12 "Device Enabled" 0
xinput set-prop 12 "Device Enabled" 1
    :
        ;;
esac

```

then run

```

sudo chmod aug+x /etc/pm/sleep.d/keyboard_wake_hack-resume

```

Next time you suspend and resume, your keyboard should be good to go.

---

### Post by amw2 on 2014-05-10
> **amw2 said:**
> Hi all.
And thank you all for these investigations :)

I've just bought Sony Vaio Fit multi-flip SVF13N2J2RS and installed kubuntu 14.04.
I've applied the keyboard hack below but keyboard still not resumed correctly aftre suspend.
More, I have a very strange behaviour, it resumes OK once, then not resumed on next suspend/resume, next resumed on third suspend/resume and so on.
More detailed is as the following:

1. boot-up and login - OK
2. close lid - wait for suspend (LED off) - open lid - resumed - keyboard OK.
3. close lid - wait for suspend (LED off) - open lid - resumed - keyboard is not working.
4. close lid - wait for suspend (LED off) - open lid - resumed - keyboard OK.
5. close lid - wait for suspend (LED off) - open lid - resumed - keyboard is not working.
6. close lid - wait for suspend (LED off) - open lid - resumed - keyboard OK.
...

Additionaly, sometimes keyboard is not working few suspend/resume cycles and sumtimes it resumed but after typing few keys last key seems autorepeated continuously forever.
Any idea what to check to fix the issue?

I didn't find the real reason of the problem but each time when keyboard is not resumed I have a log
```

Apr 29 21:12:30 fox kernel: [  144.478981] atkbd serio0: Spurious ACK on isa0060/serio0. Some program might be trying to access hardware directly.

```
So it looks like a race condition in atkbd driver.

On the other hand after recent kernel update to linux-image-3.13.0-26-generic from trusty-proposed the problem washed away and keyboard resumed successfully each time. I don't use any additional scripts, it just working as is.
The only minor issue left is the touchscreen, touchpad and keyboard resumed with little delay of some 2 or 3 seconds.

---

### Post by accolyte on 2014-05-19
I can only get the keyboard to work after every other resume from suspend.

---

### Post by kwoby on 2014-05-22
After resume I can access the keyboard but neither the mouse nor the touch screen nor the keybad do work.
I have Sony PRO 13.
I also tried several kernels, the kernels from the Ubuntu distribution but also 3.14 and 3.15 (actually rc6). Always the same problem.

---

### Post by ppp0 on 2014-06-05
Hi! I have Laptop vaio fit 15a (SVF15n2z2rb) and i've lost wifi! Here is my lshw:

```

vaio-fit
    description: Notebook
    product: SVF15N2Z2RB (54679216)
    vendor: Sony Corporation
    version: C10KN24B
    serial: 54679216-0000518
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall32
    configuration: boot=normal chassis=notebook family=SVF15N2 sku=54679216 uuid=C0871260-5DA3-E311-9099-3C0771688E3C
  *-core
       description: Motherboard
       product: VAIO
       vendor: Sony Corporation
       physical id: 0
       version: N/A
       serial: N/A
     *-firmware
          description: BIOS
          vendor: Insyde Corp.
          physical id: 0
          version: R1130DD
          date: 04/22/2014
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci pnp upgrade shadowing cdboot bootselect edd int9keyboard int10video acpi biosbootspecification netboot uefi
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-4500U CPU @ 1.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-4500U CPU @ 1.80GHz
          serial: N/A
          slot: N/A
          size: 768MHz
          capacity: 768MHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1 Cache
             size: 128KiB
             capacity: 128KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2 Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous internal write-back unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3 Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM DDR3
             physical id: 0
             slot: SODIMM1
             size: 8GiB
             width: 64 bits
        *-bank:1
             description: SODIMM DDR3
             physical id: 1
             slot: SODIMM2
             size: 8GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Haswell-ULT DRAM Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 09
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: Haswell-ULT Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:67 memory:b5000000-b53fffff memory:c0000000-cfffffff ioport:6000(size=64)
        *-multimedia:0
             description: Audio device
             product: Haswell-ULT HD Audio Controller
             vendor: Intel Corporation
             physical id: 3
             bus info: pci@0000:00:03.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:69 memory:b5610000-b5613fff
        *-usb:0
             description: USB controller
             product: Lynx Point-LP USB xHCI HC
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:61 memory:b5600000-b560ffff
        *-communication
             description: Communication controller
             product: Lynx Point-LP HECI #0
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:65 memory:b5618000-b561801f
        *-multimedia:1
             description: Audio device
             product: Lynx Point-LP HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 04
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:68 memory:b5614000-b5617fff
        *-pci:0
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:56
        *-pci:1
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:57 memory:b5500000-b55fffff
[B]           *-network
                description: Wireless interface
                product: Wireless 7260
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlan0
                version: 73
                serial: ac:7b:a1:44:00:e8
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-29-generic firmware=22.24.8.0 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
                resources: irq:66 memory:b5500000-b5501fff[/B]
        *-pci:2
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:58 ioport:5000(size=4096) memory:b5400000-b54fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: eth0
                version: 10
                serial: 3c:07:71:68:8e:3c
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:64 ioport:5000(size=256) memory:b5404000-b5404fff memory:b5400000-b5403fff
        *-pci:3
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:59 ioport:4000(size=4096) memory:b4000000-b4ffffff ioport:a0000000(size=301989888)
           *-display
                description: 3D controller
                product: GK208M [GeForce GT 735M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:04:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=nvidia latency=0
                resources: irq:70 memory:b4000000-b4ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128)
        *-pci:4
             description: PCI bridge
             product: Lynx Point-LP PCI Express Root Port 6
             vendor: Intel Corporation
             physical id: 1c.5
             bus info: pci@0000:00:1c.5
             version: e4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:60 ioport:3000(size=4096) memory:b3000000-b3ffffff ioport:b2000000(size=16777216)
           *-generic
                description: Unassigned class
                product: RTS5227 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:62 memory:b3000000-b3000fff
        *-usb:1
             description: USB controller
             product: Lynx Point-LP USB EHCI #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:b561c000-b561c3ff
        *-isa
             description: ISA bridge
             product: Lynx Point-LP LPC Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-storage
             description: SATA controller
             product: Lynx Point-LP SATA Controller 1 [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 04
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:63 ioport:6088(size=8) ioport:6094(size=4) ioport:6080(size=8) ioport:6090(size=4) ioport:6060(size=32) memory:b561b000-b561b7ff
        *-serial UNCLAIMED
             description: SMBus
             product: Lynx Point-LP SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 04
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:b5619000-b56190ff ioport:6040(size=32)
     *-scsi
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD10S12X-55J
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: WD-WX11AC3L8878
             size: 946GiB (1016GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=4096 signature=000ef83f
           *-volume:0
                description: Windows NTFS volume
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                version: 3.1
                serial: 34eeddec-ba69-5748-9639-1ad5d3809601
                size: 198GiB
                capacity: 198GiB
                capabilities: primary bootable ntfs initialized
                configuration: clustersize=4096 created=2014-06-02 23:48:49 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
           *-volume:1
                description: Windows NTFS volume
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                logical name: /media/id/TRASH
                version: 3.1
                serial: 005f-e72c
                size: 587GiB
                capacity: 587GiB
                capabilities: primary ntfs initialized
                configuration: clustersize=4096 created=2014-06-03 16:17:06 filesystem=ntfs mount.fstype=fuseblk mount.options=rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096 state=mounted
           *-volume:2
                description: Extended partition
                physical id: 3
                bus info: scsi@0:0.0.0,3
                logical name: /dev/sda3
                size: 160GiB
                capacity: 160GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux filesystem partition
                   physical id: 5
                   logical name: /dev/sda5
                   logical name: /
                   capacity: 144GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered state=mounted
              *-logicalvolume:1
                   description: Linux swap / Solaris partition
                   physical id: 6
                   logical name: /dev/sda6
                   capacity: 15GiB
                   capabilities: nofs
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: c6:19:b3:91:61:56
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.131 link=yes multicast=yes

```

So the version of ubuntu is 14.04 LTS (with kernel 3.13.0-29-generic), what's wrong? 

I tried to update firmware like this: [http://wireless.kernel.org/en/users/Drivers/iwlwifi#Firmware](http://wireless.kernel.org/en/users/Drivers/iwlwifi#Firmware)

But with no result :-/

---

### Post by ppp0 on 2014-06-05
Oh my bad, my card is working but there is no indicator network applet

---

### Post by MoonBlossom on 2014-06-07
I recently bought a Vaio Flip 15A. I installed Kubuntu 14.04 on it. I would like the silent fan profile but when I try to run
```
echo 'silent' | sudo tee /sys/devices/platform/sony-laptop/thermal_control
```
I get this error
```
tee: /sys/devices/platform/sony-laptop/thermal_control: No such file or directory
silent

```

I went to the directory /sys/devices/platform/sony-laptop/ and thermal_control is missing. How can I add it?

Thank you!

---

### Post by ppp0 on 2014-06-09
> 
tee: /sys/devices/platform/sony-laptop/thermal_control: No such file or directory


i have the same issue and don't know how to do it

---

### Post by mizou2 on 2014-06-20
Just found a fix for multi touch for the touchpad using this bug report which works for a yoga (and also my vaio flip 13)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442) comment #137

sudo dkms ldtarball psmouse-elantech-x551c.tar.gz
sudo dkms install -m psmouse -v elantech-x551c
 sudo rmmod psmouse
sudo modprobe psmouse

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442/+attachment/3941591/+files/psmouse-elantech-x551c.tar.gz](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442/+attachment/3941591/+files/psmouse-elantech-x551c.tar.gz)

still looking for auto rotate or at least rotate with keyboard/touchscreen working, if found I will definitely get rid of this W8 c**** hope somebody will find a fix to this as this all why the vaio flip is such a good device

hope it helps

---

### Post by mizou2 on 2014-06-20
Hi again Vaio friends :)

After some research I found a quite nice workaround to get the screen rotation with the touchscreen rotating as well! using a script (each execution does a 90° turn of screen+touchscreen :D)

based on this script:
[https://gist.github.com/rubo77/daa262e0229f6e398766#file-rotate-screen-sh-L73](https://gist.github.com/rubo77/daa262e0229f6e398766#file-rotate-screen-sh-L73)

You need to change those parameters to match the vaio flip inputs as this script was made for yoga laptops at first:

TouchscreenDevice='ELAN Touchscreen'
TouchpadDevice='SynPS/2 Synaptics TouchPad'

to:

TouchscreenDevice='N-trig DuoSense'
TouchpadDevice='ETPS/2 Elantech Touchpad'

make the script runable (chmod u+x) then run it with no argument on a terminal:

 # ./script.sh

there you go, 90° turn with touchscreen every time you run it!

So now you have a functional touchpad and the possibility to use the rotation via a command!

---

### Post by amendezsoto on 2014-07-01
Thanks a lot Mizou2, this is really great, works fine. In my case I am using Ubuntu 14.04 with my Vaio fit 13, the only issues is that I had to put this in a script to run as root in the init.d, becouse otherwise when I reboot the module is not loaded.
In the case of the screen rotation sometimes it appears black and I have to try it several times

> **mizou2 said:**
> Just found a fix for multi touch for the touchpad using this bug report which works for a yoga (and also my vaio flip 13)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442) comment #137

sudo dkms ldtarball psmouse-elantech-x551c.tar.gz
sudo dkms install -m psmouse -v elantech-x551c
 sudo rmmod psmouse
sudo modprobe psmouse

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442/+attachment/3941591/+files/psmouse-elantech-x551c.tar.gz](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442/+attachment/3941591/+files/psmouse-elantech-x551c.tar.gz)

still looking for auto rotate or at least rotate with keyboard/touchscreen working, if found I will definitely get rid of this W8 c**** hope somebody will find a fix to this as this all why the vaio flip is such a good device

hope it helps

---

### Post by marius-dot42 on 2014-07-17
Thanks a lot! That and upgrading the kernel to 3.15 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15-utopic/) made it possible to finally ditch Windows 8! :D

---

### Post by lynx_deb on 2014-09-24
some one can help me?
i'm facing a lot of issue installing Ubuntu or Mint into Vaio Multi Flip 11A (Bay-trail based) :(
sometime it boots with ACPI, otherwise i need to put "acpi=off" to get it boot

it's driving me crazy.. i've also recompiled the ACPI table but thisn't seem to fix the issues

---

### Post by mizou2 on 2014-10-05
What is the message you're getting when trying to boot? 

I didn't ge this kind of issue nor needed to play with acpi settings.

Only issue I still face sometimes is when hardware doesn't seem to realise that fans need to be turn on and so the laptop is shutting down after a while because of the heat. I was facing the same issue with Windows8 which makes me think that it's more a bios/hardware issue.

---

### Post by cathalgarvey-p on 2014-10-21
In case it helps anyone with this laptop get up and going, [I've written a guide]("http://letters.cathalgarvey.me/fit-for-purpose-linux-mint-debian-edition-on-sony-vaio-flip-13/") which draws in part from suggestions on this thread. The guide is for LMDE but should apply to Ubuntu as well, provided you have build-essential installed for the stage where you build a kernel module for the touchpad!

There's a lot of stuff there that isn't here, too; I tore-down the little router that comes with some variants of this laptop, for example, so there are some further hardware details available on its innards, now. Looking forward to being able to hack the little router too, someday. :)

Thanks to all the people on this thread who offered great suggestions.

---

### Post by mizou2 on 2014-10-27
Thanks for the tip on the configuration about touchegg, works like a charm even though I just tested it for a couple minutes. Keeping it as a simple terminal command for the moment as I'm not using so often the "tablette mod" plus terminator is always near by :)

Thanks a mil'!

---

### Post by jmz_52 on 2014-11-07
Sony Vaio Fit 15A, kernel 3.16.7-200.fc20 (latest version from Fedora 20 updates).
Modules hid_sensor_iio_common and his_sensor_hub seems to have support for STMicroelectronics sensor chip.
There are special modules for lsm330dlc chip - st_accel_i2c, st_magn_i2c, st_gyro_i2c and st_sensors_i2c, but these modules are not loaded on my system.

There are 6 devices in /sys/bus/iio/devices - iio:device[0-5]
Sensor names (/sys/bus/iio/devices/iio:device[0-5]/name) are:
accel_3d
als (light sensor)
magn_3d
gyro_3d
incli_3d (inclinometer ?)
dev_rotation

Nodes are available at /dev/iio:device[0-5]

Raw values can be read from /sys/bus/iio/devices/iio:device[0-5]/in_*_raw files.
I've tested accel_3d and asl devices, both provides reasonable raw data, but some calibration will be required for futher usage.

Downsize is that sensors seems to be whithin "keyboard" part of laptop and cann't be used to detect presentation and tablet mode.
Additional observation here - I've disabled all sensors devices (usb bus) in windows device manager, but vesmgr service was still able to detect screen flip and switch to and from presentation mode.
No other screen rotation was working until I've re-enabled the sensor devices.
I suspect that flip events are acpi events (like it is for Thinkpad Yoga and HP Elitebook Revolve).

**Update**: screen flip was not defected by vesmgr after I've disabled the ACPI\SNY5001 device driver in windows (Sony Firmware Extension Parser).
sony_laptop kernel module is responsible for this device, but my version seems to be unaware about screen flipping events.
Module is located in drivers/platform/x86 in 3.16 vanilla kernel source.

---

### Post by jmz_52 on 2014-11-17
I've managed to get flip events delivered to sony-laptop driver on my Vaio Fit 15A.
Stable patch should be ready in about a week, but I cannot test it myself on any other model.

I would appreciate any ACPI and DMI data (output of "acpidump" and "dmidecode -t bios -t system") you can send me for other models.

---

### Post by kwoby on 2014-11-17
I cannot suspend to disk, at wake up keyboard, mouse, touchpad and touchscreen are frozen.
I modified my grub config  : such as

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=linux acpi_backlight=vendor i8042.reset atkbd.reset"

```
 
as found elswhere. It did not help.

the modules that block waking up are

  i2c_designware_platform
  i2c_designware_core

when I blacklist them suspend works, but I have not touchpad and no touchscreen.

And, of course, the rotate_screen scrip does not work!

Any idea for help?


Here is the output from 
sudo dmidecode -t bios -t system 


```
 dmidecode 2.12
# SMBIOS entry point at 0x9bebef98
SMBIOS 2.7 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: Insyde Corp.
        Version: R1080S7
        Release Date: 09/13/2013
        Address: 0xE0000
        Runtime Size: 128 kB
        ROM Size: 4096 kB
        Characteristics:
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                8042 keyboard services are supported (int 9h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                Smart battery is supported
                BIOS boot specification is supported
                Targeted content distribution is supported
                UEFI is supported
        BIOS Revision: 10.80
        Firmware Revision: 10.80

Handle 0x0001, DMI type 1, 27 bytes
System Information
        Manufacturer: Sony Corporation
        Product Name: SVD1323Y9EB
        Version: J5008AP0
        Serial Number: 54679546-0000412
        UUID: CADB3A1C-546F-4E5B-A722-17FB11BC0D01
        Wake-up Type: Power Switch
        SKU Number: 54679546
        Family: SVD1323

Handle 0x0009, DMI type 13, 22 bytes
BIOS Language Information
        Language Description Format: Long
        Installable Languages: 1
                en|US|iso8859-1
        Currently Installed Language: en|US|iso8859-1

Handle 0x0010, DMI type 32, 20 bytes
System Boot Information
        Status: No errors detected


```

---

### Post by jmz_52 on 2014-11-18
Sorry, cann't help with i2c_designware issue - these modules are not used on my Fit 15a and from what I can see you have Vaio Duo model which is quite different.

---

### Post by jmz_52 on 2014-11-21
Patched version of sony-laptop driver available at [https://github.com/jmz52/sony-laptop](https://github.com/jmz52/sony-laptop)
Mind the Secure Boot limitations.

Current mode can be read from /sys/devices/platform/sony-laptop/tablet
0 - laptop
1 - presentation
2 - tablet

_acpi_listen output_
sony/hotkey SNY5001:00 00000004 00000001* [COLOR=#a9a9a9]                           presentation mode[/COLOR]*

video/tabletmode TBLT 0000008A 00000001*                               [COLOR=#a9a9a9]tablet mode on[/COLOR]*
sony/hotkey SNY5001:00 00000004 00000002*                            [COLOR=#a9a9a9]tablet mode[/COLOR]*

video/tabletmode TBLT 0000008A 00000000*                               [COLOR=#a9a9a9]tablet mode[/COLOR]*[COLOR=#a9a9a9]* off*[/COLOR]
sony/hotkey SNY5001:00 00000004 00000001*                            [COLOR=#a9a9a9]presentation mode[/COLOR]*

sony/hotkey SNY5001:00 00000004 00000000*                            [COLOR=#a9a9a9]laptop mode[/COLOR]*
[U]

evtest output[/U]
Input driver version is 1.0.1
Input device ID: bus 0x10 vendor 0x104d product 0x0 version 0x0
Input device name: "Sony Vaio Keys"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
[COLOR=#a9a9a9]*<cut>*[/COLOR]
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
  Event type 5 (EV_SW)
    Event code 1 (SW_TABLET_MODE)
Properties:
Testing ... (interrupt to exit)
Event: time 1416558184.961217, type 5 (EV_SW), code 1 (SW_TABLET_MODE), value 1
Event: time 1416558184.961217, -------------- SYN_REPORT ------------
Event: time 1416558191.241382, type 5 (EV_SW), code 1 (SW_TABLET_MODE), value 0
Event: time 1416558191.241382, -------------- SYN_REPORT ------------

---

### Post by voland66 on 2015-01-13
Thanks for your patch, works great on SVF14N11CXB, 14in version (running it on Fedora)
A somewhat related question -- does anyone have an idea whether sony's battery care function can work with this line of laptops on linux? I found some info about /sys/device/platform/sony-laptop/battery_charge_limiter file but it is not created by sony-laptop module on my machine.

---

### Post by behdin on 2015-02-20
hi dear 
how can apply this patch on ubuntu 14.10 kernel 
does has any nfc driver for this labtop ?

---


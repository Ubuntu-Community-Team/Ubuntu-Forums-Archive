---
title: "Dell Inspiron 1090 (Duo) Accelerometer Magnetometer Driver"
date: 2011-01-02
forum: Hardware
---

### Post by DFarmerTX on 2011-01-02
I'm hoping that by starting this thread, we can gather information and solve the issues associated with getting auto-rotation working on the Dell Duo convertible laptop.

There are minor issues with other devices on the system, but so far, everything is pretty much solved.  However, the netbook has a chip to detect orientation and location that works in Windows to (among other things) automatically change the rotation of the screen (4 ways) and orientation of the touch screen to match the orientation of the system.

The part is listed by Dell as "ST Microelectronics ST DL303DLH Sensor".  I can't find this on my system in Ubuntu.  I suspect it is hidden in WMI or something.

Also, I can't find any reference to this chip from anywhere except the Dell site.

So, what do we have to do to get this working?

---

### Post by garwal on 2011-01-10
If you get any information on this please let me know. I have done a lot of looking and can not find any information on this sensor. I spent some time searching the companies site trying to find information on the 3 axis sensor but could find no reference to this device. I know we can do it but first we need to find information on Linux and these types of devices, I will be happy to help.
garwal

---

### Post by DFarmerTX on 2011-01-12
> **garwal said:**
> If you get any information on this please let me know. I have done a lot of looking and can not find any information on this sensor. I spent some time searching the companies site trying to find information on the 3 axis sensor but could find no reference to this device. I know we can do it but first we need to find information on Linux and these types of devices, I will be happy to help.
garwal
Found this:
[URL="http://code.google.com/p/ldd6410-2-6-28/source/browse/trunk/linux-2.6.28-samsung/include/linux/i2c/lsm303dlh.h?r=23"]http://code.google.com/p/ldd6410-2-6-28/source/browse/trunk/linux-2.6.28-samsung/...
[/URL]

Which I think is the chip.

Also, looks like someone has proposed adding support to Linux for it here:

[http://groups.google.com/group/linux.kernel/...]("http://groups.google.com/group/linux.kernel/browse_thread/thread/520109b77a99b9d7/f5f338b4c337a341?lnk=raot&fwc=1")

So, maybe it's just a matter of time.  Does anyone know if we can do anything with the above information now?

I feel like such a n00b!

---

### Post by DFarmerTX on 2011-01-12
delete duplicate

---

### Post by lukeross on 2011-04-06
I run Fedora on my Inspiron Duo, and after a fair bit of fiddling have got the Accelerometer working. I've got some hastily-written notes here: [http://lukeross.name/dell/#accelerometer](http://lukeross.name/dell/#accelerometer) - but in a nutshell I took the driver mentioned, patched it a bit further and then it can be poked into the kernel and the values read out.

I've since put together a perl script which reads the accelerometer and uses it to xrandr the display along with some xinput to rotate the touchscreen - it's under the heading "Screen and touchpad rotation".

It'll probably need some amendment for Ubuntu, but I mention it here in the hope it proves useful.

---

### Post by w1ll1am on 2011-04-14
> **lukeross said:**
> I run Fedora on my Inspiron Duo, and after a fair bit of fiddling have got the Accelerometer working. I've got some hastily-written notes here: [http://lukeross.name/dell/#accelerometer](http://lukeross.name/dell/#accelerometer) - but in a nutshell I took the driver mentioned, patched it a bit further and then it can be poked into the kernel and the values read out.

I've since put together a perl script which reads the accelerometer and uses it to xrandr the display along with some xinput to rotate the touchscreen - it's under the heading "Screen and touchpad rotation".

It'll probably need some amendment for Ubuntu, but I mention it here in the hope it proves useful.

Great job. Do you think there is anyway you could try to get it to work in ubuntu or talk me threw trying to set it up?

---

### Post by lukeross on 2011-04-15
I'll see if I can bodge together the kernel module on 10.10 this weekend. If that works the perl rotation script should work unaided. I'll report back as to how things go once done.

Regarding my work-in-progress mock-DuoStage UI, I'm having fun with the virtual keyboard. The UI comes up when I flip the screen, and I can web browse on it (thanks Webkit), but all the gnome virtual keyboard (eg. Florence) get hidden because the UI is always on top (to hide the panels and other such things). I think I'll have to roll my own within the app, irritatingly.

---

### Post by w1ll1am on 2011-04-15
> **lukeross said:**
> I'll see if I can bodge together the kernel module on 10.10 this weekend. If that works the perl rotation script should work unaided. I'll report back as to how things go once done.

Regarding my work-in-progress mock-DuoStage UI, I'm having fun with the virtual keyboard. The UI comes up when I flip the screen, and I can web browse on it (thanks Webkit), but all the gnome virtual keyboard (eg. Florence) get hidden because the UI is always on top (to hide the panels and other such things). I think I'll have to roll my own within the app, irritatingly.

alright sounds awesome and again great work!

Also I tried to get the flipping screen to run a command and it is not working? I did everything you said to and still nothing happens? any ideas why? 

I checked the kernel log and it says the same thing as yours.

---

### Post by lukeross on 2011-04-16
OK, I've built the kernel modules under 10.10 32-bit and they're available here:

[INDENT][http://lukeross.name/dell/ubuntu-accel.tar.bz2](http://lukeross.name/dell/ubuntu-accel.tar.bz2)[/INDENT]

There's a version for 2.6.35-22-generic-i686 (the kernel that is on the distribution CD) and 2.6.35-28-generic-i686 (which is the kernel that apt installed when I asked for an upgrade). You can find your kernel version with the command "uname -r".

Change into the right directory as root, and then load the module with:

[INDENT]insmod lsm303dlh_a.ko[/INDENT]

Then follow that up with the following commands:

[INDENT]modprobe i2c_i801
echo lsm303dlh_a 25 > /sys/bus/i2c/devices/i2c-2/new_device
echo 1 > /sys/bus/i2c/devices/i2c-2/2-0019/mode
[/INDENT]

Check the module's working with this command:

[INDENT]cat /sys/bus/i2c/devices/i2c-2/2-0019/data
[/INDENT]

You should get 3 values (which are in hexadecimal) separated with colons. If so, all is good. If not, the bottom few lines of the "dmesg" command may explain what went wrong.

Then as a normal user, you can download my autorotate script and run it with "perl autorotate.pl". It'll print something like "Z up" (depending on orientation). Turn the whole netbook sharp to the right and it should say that it is turning the screen, which should rotate shortly after. You should be able to turn the it to the left and upside down too.

---

### Post by lukeross on 2011-04-16
I tried the run-on-flip bit on 10.10 and it did work, but you do need to make sure you've run setkeycodes prior, and set both the "run_command_1" and "command_1" entries in gconf. Make sure the command is valid - if the command isn't runnable metacity silently does nothing. And of course, if Metacity isn't your window manager it won't work.

apps/metacity/global_keybindings/run_command_1 should be set to the value "XF86Launch1" and apps/metacity/keybinding_commands/command_1 I set to "/usr/bin/gedit" for testing.

---

### Post by w1ll1am on 2011-04-16
Okay I got the driver installed it worked great. There is one problem though the mouse did not rotate with it. do you have any idea how to fix this?

I still can not get the flipping screen to work. I am not sure why. I have done everything that you said so... ya got any other ideas I can try. Why am i setting run_command_1 to XF86Launch1 how did you know to do that?

---

### Post by lukeross on 2011-04-17
Hmm, by "mouse" do you mean the touchscreen or the touchpad? Assuming it's the touchscreen, how have you configured it? As far as I could see, in 10.10 the touchscreen doesn't initially work, so I suspect to make it work you've either added quirks for it or changed the driver - how you rotate the touchscreen depends on which of these you've opted for. I've used quirks myself, which means no multitouch sadly.

As regards XF86Launch1, I found a spare keycode for use with setkeycodes by googling, then back in X I fired up "xev" to monitor events. I rotated the screen and noted that it said there had been a KeyPress event on the XF86Launch1 key.

---

### Post by minchal on 2011-04-17
Hi,
I have dell vostro 3350 with "ST Microelectronics" accelerometer. On windows 7 i installed driver which stops drive when falling (and it work fine).

How to find what model of accel I have? 

On windows in "device manager" there's only "SMO8800".

In /var/log/udev i found:
```
KERNEL[1303046128.395383] add      /devices/LNXSYSTM:00/device:00/PNP0A08:00/SMO8800:00 (acpi)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/LNXSYSTM:00/device:00/PNP0A08:00/SMO8800:00
SUBSYSTEM=acpi
MODALIAS=acpi:SMO8800:
SEQNUM=1457
```

I loaded modules i2c-i801, i2c-dev, but 
```
echo lsm303dlh_a 25 > /sys/bus/i2c/devices/i2c-2/new_device
 echo 1 > /sys/bus/i2c/devices/i2c-2/2-0019/mode
```
doesn't work (file '2-0019/mode' not exists) and this same for other devices: i2c-0, i2c-1...

Now i'm on ubuntu 11.04 (2.6.38-8 ).

---

### Post by w1ll1am on 2011-04-17
> **lukeross said:**
> Hmm, by "mouse" do you mean the touchscreen or the touchpad? Assuming it's the touchscreen, how have you configured it? As far as I could see, in 10.10 the touchscreen doesn't initially work, so I suspect to make it work you've either added quirks for it or changed the driver - how you rotate the touchscreen depends on which of these you've opted for. I've used quirks myself, which means no multitouch sadly.

As regards XF86Launch1, I found a spare keycode for use with setkeycodes by googling, then back in X I fired up "xev" to monitor events. I rotated the screen and noted that it said there had been a KeyPress event on the XF86Launch1 key.


Sadly I have also done the same thing. No multitouch for me. I edited the grub.cfg file and single touch works. The touch screen does everything opposite of what my finger is doing. 

If I use setkeycodes in /ect/rc.local and then run xev and flip the screen I get no activity?

---

### Post by lukeross on 2011-04-18
> **minchal said:**
> How to find what model of accel I have? 

On windows in "device manager" there's only "SMO8800".


Appears to be a different chip, possibly the LIS33DETR according to Google. I haven't seen a driver for it. It would be possible to query it via ACPI I suspect, but beyond my skills to write such a driver.

---

### Post by minchal on 2011-04-18
Where did you find that info?

Maybe this is something like P11? On windows drivers are in directory:
Program Files/STMicroelectronics/AccelerometerP11/stdcfltn/...

---

### Post by joey-elijah on 2011-04-20
> **lukeross said:**
> OK, I've built the kernel modules under 10.10 32-bit and they're available here:

[INDENT][http://lukeross.name/dell/ubuntu-accel.tar.bz2](http://lukeross.name/dell/ubuntu-accel.tar.bz2)[/INDENT]

There's a version for 2.6.35-22-generic-i686 (the kernel that is on the distribution CD) and 2.6.35-28-generic-i686 (which is the kernel that apt installed when I asked for an upgrade). You can find your kernel version with the command "uname -r".

Change into the right directory as root, and then load the module with:

[INDENT]insmod lsm303dlh_a.ko[/INDENT]

Then follow that up with the following commands:

[INDENT]modprobe i2c_i801
echo lsm303dlh_a 25 > /sys/bus/i2c/devices/i2c-2/new_device
echo 1 > /sys/bus/i2c/devices/i2c-2/2-0019/mode
[/INDENT]

Check the module's working with this command:

[INDENT]cat /sys/bus/i2c/devices/i2c-2/2-0019/data
[/INDENT]

You should get 3 values (which are in hexadecimal) separated with colons. If so, all is good. If not, the bottom few lines of the "dmesg" command may explain what went wrong.

Then as a normal user, you can download my autorotate script and run it with "perl autorotate.pl". It'll print something like "Z up" (depending on orientation). Turn the whole netbook sharp to the right and it should say that it is turning the screen, which should rotate shortly after. You should be able to turn the it to the left and upside down too.

Ace work my friend! Almost makes me regret blitzing Maverick off my Duo for 11.04 :P

---

### Post by lukeross on 2011-04-20
Righty,

You'll only see output in xev if you've run setkeycodes, but *haven't* configured metacity (as that traps the keypress before xev can see it).

So I booted off the 10.10 Desktop CD again, and at the desktop opened a root prompt and ran:

[INDENT]setkeycodes e073 148[/INDENT]

I didn't configure any of the gconf, and then ran xev as the normal user. On flipping the screen it shows this:

[INDENT]
KeyRelease event, serial 36, synthetic NO, window 0x3e00001,
    root 0xad, subw 0x0, time 407242, (82,50), root:(1081,105),
    state 0x0, keycode 156 (keysym 0x1008ff41, XF86Launch1), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
[/INDENT]

So on line 3, this is where I got "XF86Launch1".

I then went and configured the gconf, and at that point xev no longer shows the keypress, but gedit starts instead.

So likely the failure to work is either because you haven't run setkeycodes as root beforehand, or because metacity is trying and failing to start the program you selected (or that gedit, if you're using that, is already running - you can't have multiple instances of gedit open at once).

As regards 11.04, the modules are fairly easy to compile out-of-tree. I may chuck together a pre-patched source if I get a chance, but if you've experience of module building it'll build without hassle.

Regarding the Vostro 3350, my source was [http://ubuntuforums.org/showpost.php?p=9767008&postcount=10](http://ubuntuforums.org/showpost.php?p=9767008&postcount=10) - found by googling for SMO8800.

---

### Post by lukeross on 2011-04-20
I had to reboot again to try out the touchscreen-not-rotating, as it needed the usbhid quirks on the command line.

You may want to check you have the xinput command installed ("xinput list") should confirm this. Without it, there's no way easy to control the touchscreen from external programs.

The egalax touchscreen presents itself as 3 "mice" on the xinput list:

[INDENT]
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=11	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController         	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
[/INDENT]

Here they are IDs 10, 11 and 12. Because they share a name, I don't know how you address them except by IDs.

Each of these appear to be enumerated in a random order, so which is the "active" one varies between 10, 11 and 12 depending on the whim of the USB layer. So my script attempts to poke all three each time, two of which are futile and one is meant to have the desired effect.

Each of the 3 has properties called "Evdev Axes Swap" which flips the X and Y co-ordinates and "Evdev Axis Inversion" which controls whether the X and/or Y are working backwards.

So the following commands change the orientation (replace "10" with 11 or 12 depending on which ID is active. I have to try all three each time to work it out).

Flip X and Y:

xinput set-prop --type=int --format=8 10 "Evdev Axes Swap" 1

undo this with:

xinput set-prop --type=int --format=8 10 "Evdev Axes Swap" 0

X axis is right-to-left instead of left-to-right:

xinput set-prop --type=int --format=8 10 "Evdev Axis Inversion" 1 0

X normal, Y axis inverted:

xinput set-prop --type=int --format=8 10 "Evdev Axis Inversion" 0 1

Return axis inversion to normal:

xinput set-prop --type=int --format=8 10 "Evdev Axis Inversion" 0 0

All autorotate does is do this in combination with the xrandr command (to control how the screen is displayed), so you can play with these commands for full manual control.

All assumes you're using the stock driver with the usbhid.quirks and your mouse is configured to use evdev under X (which is how a fresh Ubuntu install seems to do it under 10.10). All bets are off with the later usb-egalax and eGalax's own driver - as the params are evdev-specific.

---

### Post by ninjaaron on 2011-04-21
Woo!

You're sending this stuff upstream, right?

---

### Post by semidark on 2011-05-02
hi.

the driver works great. but where can I download the autorotate.pl script that you mentioned. I don't want to reinvent the wheel :)

thnx semidark

---

### Post by lukeross on 2011-05-03
Script is here: [http://lukeross.name/dell/autorotate.pl](http://lukeross.name/dell/autorotate.pl)

It's linked under the heading of "Screen and touchpad rotation" here: [http://lukeross.name/dell/#accelerometer](http://lukeross.name/dell/#accelerometer)

---

### Post by paulomuggler on 2011-05-08
hey, nice work on those drivers, I tested them on 2.6.22 kernel and it works good! I`m interested in compiling the stuff you posted, but I don`t have much experience working with diff files, would you mind talking me through it, or just pointing me in the right direction? Is it by any chance possible to compile this stuff for later kernel revisions, such as 2.6.38 (11.04)? Many thanks!

---

### Post by corsair1564 on 2011-05-09
So far, this is working great. thank you for all the work you guys have put into this.
Only problem I've noticed is that i have to go through the entire set up process each time I start the machine, and I have to restart if I've just closed the cover and set the machine to sleep.  Is there any way to set this up as a permanent driver install?

Thanks
Alan

---

### Post by corsair1564 on 2011-05-13
Well, I've made some progress, with the help of a friend.  I made a shell script with the commands LukeRoss provided, which I called 'accelerometerload', then made another shell script; 'accelerometerrun', that would call out the first one as a sudo.  For some reason, using the sudo prefix on the individual commands didn't work. I can now run that script whenever I'm going to set up in tablet mode, and open Luke's perl script in a terminal. It's a little clunky, but it works. The lsm303dlh_a.ko file was placed in the /lib/modules/2.6.35-XX-generic/kernel/ folders.

accelerometerload.sh
```
#! /bin/bash
 cd /lib/modules/2.6.35-28-generic/kernel/
   modpropbe lsm303dlh_a
   modprobe i2c_i801
   echo lsm303dlh_a 25 > /sys/bus/i2c/devices/i2c-2/new_device
   echo 1 > /sys/bus/i2c/devices/i2c-2/2-0019/mode
```accelerometerrun.sh
```
#! /bin/bash
  cd /home/<user>
  sudo ./accelerometerload.sh
  ./autorotate.pl
```The two things I'd like to be able to do is reduce the sensitivity of the accelerometer, and use the screen flip event to trigger/kill the autorotate script.  The current sensitivity causes random rotation events while the unit is laying flat. If anyone could help with those issues, that would be great.  My friend is intrigued by the project, and if we could get the codes for the screen-flip events, we might be able to come up with a solution.

Alan

---

### Post by JaseP on 2011-05-16
What I would suggest is making an orientation change dependant on the tilt sensor being more than 30 deg. from flat, and not switch until the rotation was more than 45 deg. from the current orientation, using some sort of if-then statement. That way, the tablet has to be held somewhat upright for the change to be made.

I've been meaning to jump in and help, but haven't had the time. Maybe tonight...

---

### Post by corsair1564 on 2011-05-17
That sounds like a good idea. Will have to look into modifying the script for that.  The other thing that might help is to set it up so that the system can read the flip and cover sensors and start the accelerometer script when the screen is flipped and the cover closed. Does anyone know the codes we'd need to read to do this?

Alan

---

### Post by JaseP on 2011-05-17
The lid switch is mapped on my systems as:

/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2/event2

There are two other "buttons" that are mapped on my machine at:

/dev/input/event5

&

one related to the video system at:

/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input13/event13

I am guessing that they are the flip sensor switch and the video one a "kill" switch to turn off the screen if the unit is closed,... but I can be wrong...

I remember seeing something on lukeross's web-page about activating these switches, but I don't seem to be able to access his page any more...

Keep in mind that events get remapped at every boot,... so you need a udev rule to get them working properly.

---

### Post by corsair1564 on 2011-05-17
Shiny!  I'll be seeing the friend who helped get the script set up going tonight, so hopefully we can come up with something to make this work even better. :)

---

### Post by JaseP on 2011-05-19
The following is on Lukeross's website:

> 
Tablet/un-tablet detection

When you rotate the screen round the latch it onto the body a "keypress" is generated, and ditto when you move it back again. The kernel reports these as:

```

[  254.523974] atkbd serio0: Use 'setkeycodes e073 <keycode>' to make it known.
[  256.970245] atkbd serio0: Unknown key pressed (translated set 2, code 0xf4 on isa0060/serio0).
[  256.970258] atkbd serio0: Use 'setkeycodes e074 <keycode>' to make it known.
[  256.982229] atkbd serio0: Unknown key released (translated set 2, code 0xf4 on isa0060/serio0).

```
...so you can track e073 for enter-tablet and e074 for leave-tablet.

I added to my /etc/rc.local this line: setkeycodes e073 148

evdev translates this to key XF86Launch1, which in gconf-editor under apps/metacity/global_keybindings I bound to the action run_command_1, and then under the nearby keybinding_commands I configured it to run a program of my choice. Now, as I enter tablet mode the program is run automatically.


Leads me to believe that you can develop an activate rotation and deactivate rotation script to be based on the "translated" keystrokes"

That, & my suggestion above should yield a workable & automatic screen rotation function.

---

### Post by lukeross on 2011-06-03
In autorotate you can vary the sensitivity by fiddling with the line:

[INDENT]my $tipping_point = 200;[/INDENT]

Try values larger than 200, as these should (from memory) require a greater tilt.

Working out the angle of the laptop requires assessing the relative values of the X, Y and Z axis. The maximum figure depends on the force on the sensor (which may be higher than gravity if the laptop is moved suddenly).

The script's directional analysis is rather dumb - it looks for an one of the axes being more than a certain value, and the other corresponding axis being less than that "tipping point" value. By analyzing $x, $y and $z a more robust decision could be made.

---

### Post by JaseP on 2011-06-06
> 
By analyzing $x, $y and $z a more robust decision could be made.


I'd like that,... As in not rotating unless the vertical tilt is closer to horizontal, & that only when in tablet mode...

Oh, I think that "nicing" the script so that it doesn't make itself a CPU hog is in order.

---

### Post by gjahuja on 2011-07-04
Hi, I compiled the lsm303dlh_a driver in 11.04 and was able to load it, but I've encountered problems with the following commands:
```
echo lsm303dlh_a 25 > /sys/bus/i2c/devices/i2c-2/new_device
echo 1 > /sys/bus/i2c/devices/i2c-2/2-0019/mode

```
I'm able to execute the first one as root (using sudo -i) or as 
```
echo lsm303dlh_a 25 | sudo tee /sys/bus/i2c/devices/i2c-2/new_device
```
but I can't make sure it is working as I get a Permission Denied warning when I'm trying to open the file.
When I run the second one I get a No such file or directory warning.

Any help is appreciated. Thanks

-

It seems the first command is working, as the folder /sys/bus/i2c/devices/i2c-2/2-0019 is created but it only contains the following files/folders
```
modalias  name  power  subsystem  uevent
```

Also, I get the follwing output from dmesg
```
[  212.416486] lsm303dlh_a 2-0019: failed to get regulator
[  212.480079] lsm303dlh_a 2-0019: i2c_smbus_read_byte_data failed error -6	 Register (WHO_AM_I)
[  212.480092] lsm303dlh_a 2-0019: probe function fails fffffffa
[  212.480137] i2c i2c-2: new_device: Instantiated device lsm303dlh_a at 0x19

```

---

### Post by w1ll1am on 2011-08-09
So has anyone got the script to run automatically and have an easy to follow guide to set it up?

---

### Post by beastrace91 on 2011-08-25
Is there kernel source around somewhere for the compiled module that works with 2.6.35? I've got the 3.0 variation of the kernel I'd like to build the module for.

~Jeff

---

### Post by harshen_r on 2012-01-14
There might be automatic screen rotation in ubuntu 12.04, since they want to port the os to tablets and smartphones.

---

### Post by lukeross on 2012-01-31
> **gjahuja said:**
> Also, I get the follwing output from dmesg
```
[  212.416486] lsm303dlh_a 2-0019: failed to get regulator
[  212.480079] lsm303dlh_a 2-0019: i2c_smbus_read_byte_data failed error -6	 Register (WHO_AM_I)
[  212.480092] lsm303dlh_a 2-0019: probe function fails fffffffa
[  212.480137] i2c i2c-2: new_device: Instantiated device lsm303dlh_a at 0x19

```

I hit this myself recently. For a long time the i2c-i801 driver appeared as /sys/bus/i2c/i2c-2 (the graphics card taking 0 and 1), but later intel graphics drivers seem to claim all the way up to i2c-13, pushing the i2c-i801 into /sys/bus/i2c/i2c-14. Once updated it seems to load OK. For reliability I suppose I really should inspect /sys/bus/i2c/i2c-*/name to figure out where the i2c-i801 has appeared.

The lsm303dlh module sadly seems to be slowly rotting, as under kernel 3.2 I've had to add some ```
#include <linux/module.h>
``` to the two .c files to get them to compile.

I seem to have managed to get the (Fedora) Gnome 3 desktop to work acceptably well on a touchscreen, as the new virtual keyboard based on eekboard seems substantially better than the ones I tried before. Gnome 3 is not exactly slick, but it is usable for my purposes. I hooked up the screen flip to a tweaked version of the autorotate script which also puts an icon in the systray which I can kill it by, so it'll rotate the web browser as I rotate the machine.

---

### Post by MadnessRed on 2012-09-18
> **lukeross said:**
> I hit this myself recently. For a long time the i2c-i801 driver appeared as /sys/bus/i2c/i2c-2 (the graphics card taking 0 and 1), but later intel graphics drivers seem to claim all the way up to i2c-13, pushing the i2c-i801 into /sys/bus/i2c/i2c-14. Once updated it seems to load OK. For reliability I suppose I really should inspect /sys/bus/i2c/i2c-*/name to figure out where the i2c-i801 has appeared.

The lsm303dlh module sadly seems to be slowly rotting, as under kernel 3.2 I've had to add some ```
#include <linux/module.h>
``` to the two .c files to get them to compile.

I seem to have managed to get the (Fedora) Gnome 3 desktop to work acceptably well on a touchscreen, as the new virtual keyboard based on eekboard seems substantially better than the ones I tried before. Gnome 3 is not exactly slick, but it is usable for my purposes. I hooked up the screen flip to a tweaked version of the autorotate script which also puts an icon in the systray which I can kill it by, so it'll rotate the web browser as I rotate the machine.

Sorry to resurrect a dead thread.

I have a Samsung Series 7 Slate with the same accelerometer.
I have managed to compile the driver, with a bit of jiggery pokery and your mods. And insert it with insmod.

The bit I am stuck on is the writing the mode file as I can't find it.

Here is what I have

```
[anthony@AnthonySlate ~]$ sudo lsmod | grep lsm
lsm303dlh_a             7794  0 
i2c_core               20508  7 drm,i915,i2c_i801,lsm303dlh_a,drm_kms_helper,i2c_algo_bit,videodev
[anthony@AnthonySlate ~]$ ls /sys/bus/i2c/devices/
0-0019  1-0019  2-0019  3-0019  4-0019  5-0019  6-0019  i2c-0  i2c-1  i2c-2  i2c-3  i2c-4  i2c-5  i2c-6
[anthony@AnthonySlate ~]$ cat /sys/bus/i2c/devices/i2c*/name
i915 gmbus ssc
i915 gmbus vga
i915 gmbus panel
i915 gmbus dpc
i915 gmbus dpb
i915 gmbus dpd
DPDDC-B
[anthony@AnthonySlate ~]$ ls /sys/bus/i2c/devices/i2c-2/2-0019/
modalias  name  power  subsystem  uevent
[anthony@AnthonySlate ~]$ cat /sys/bus/i2c/devices/i2c-2/2-0019/*
i2c:lsm303dlh_a
lsm303dlh_a
cat: /sys/bus/i2c/devices/i2c-2/2-0019/power: Is a directory
cat: /sys/bus/i2c/devices/i2c-2/2-0019/subsystem: Is a directory
MODALIAS=i2c:lsm303dlh_a
[anthony@AnthonySlate ~]$
```

The "0-0019  1-0019  2-0019  3-0019  4-0019  5-0019  6-0019" were created when I tried to do the:
echo lsm303dlh_a 25 > /sys/bus/i2c/devices/i2c-2/new_device
for each of the i2c devices. 

dmesg shows: (Order i2c-2, i2c-1, i2c-0, i2c-3, i2c-4, i2c-5, i2c-6)

```

[  457.844171] lsm303dlh_a 2-0019: i2c_smbus_read_byte_data failed error -6			 Register (WHO_AM_I)
[  457.844184] lsm303dlh_a 2-0019: probe function fails fffffffa
[  457.844207] i2c i2c-2: new_device: Instantiated device lsm303dlh_a at 0x19

[  559.082456] [drm] GMBUS [i915 gmbus vga] timed out, falling back to bit banging on pin 2
[  559.095661] lsm303dlh_a 1-0019: i2c_smbus_read_byte_data failed error -6			 Register (WHO_AM_I)
[  559.095665] lsm303dlh_a 1-0019: probe function fails fffffffa
[  559.095677] i2c i2c-1: new_device: Instantiated device lsm303dlh_a at 0x19

[  623.193644] [drm] GMBUS [i915 gmbus ssc] timed out, falling back to bit banging on pin 1
[  623.206915] lsm303dlh_a 0-0019: i2c_smbus_read_byte_data failed error -6			 Register (WHO_AM_I)
[  623.206925] lsm303dlh_a 0-0019: probe function fails fffffffa
[  623.206946] i2c i2c-0: new_device: Instantiated device lsm303dlh_a at 0x19

[  708.190127] [drm] GMBUS [i915 gmbus dpc] timed out, falling back to bit banging on pin 4
[  708.203333] lsm303dlh_a 3-0019: i2c_smbus_read_byte_data failed error -6			 Register (WHO_AM_I)
[  708.203337] lsm303dlh_a 3-0019: probe function fails fffffffa
[  708.203348] i2c i2c-3: new_device: Instantiated device lsm303dlh_a at 0x19

[  711.822048] lsm303dlh_a 4-0019: i2c_smbus_read_byte_data failed error -6			 Register (WHO_AM_I)
[  711.822058] lsm303dlh_a 4-0019: probe function fails fffffffa
[  711.822074] i2c i2c-4: new_device: Instantiated device lsm303dlh_a at 0x19

[  715.308362] [drm] GMBUS [i915 gmbus dpd] timed out, falling back to bit banging on pin 6
[  715.321645] lsm303dlh_a 5-0019: i2c_smbus_read_byte_data failed error -6			 Register (WHO_AM_I)
[  715.321654] lsm303dlh_a 5-0019: probe function fails fffffffa
[  715.321678] i2c i2c-5: new_device: Instantiated device lsm303dlh_a at 0x19

[  719.133334] lsm303dlh_a 6-0019: i2c_smbus_read_byte_data failed error -110			 Register (WHO_AM_I)
[  719.133344] lsm303dlh_a 6-0019: probe function fails ffffff92
[  719.133354] lsm303dlh_a: probe of 6-0019 failed with error -110
[  719.133364] i2c i2c-6: new_device: Instantiated device lsm303dlh_a at 0x19

```

Was hoping perhaps someone could provide some more hints?


Running kernel 3.5.3-1-ARCH
Driver, unchanged from the lkml, except for your patch, and I included linux/kernel.h and linux/module.h at the top of the file to make it compile.
Once compiled, I just ran sudo insmod lsm303dlh_a.ko

I have also tried different numbers, ie echo lsm303dlh_a 30 > ... but nothing yet.


Any help would be awesome.

Thanks

Anthony

---


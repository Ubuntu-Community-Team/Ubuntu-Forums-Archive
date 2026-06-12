---
title: "Experiences with acer 1825 ?"
date: 2010-05-18
forum: Hardware
---

### Post by lrohr on 2010-05-18
Hi everyone,

I just want to ask if anyone hase experiences with the acer 1825 multitouch ? 
And if so, what is working and what's not ?

I think the netbook edition with the multitouch display would be a great combination, nice looking desktop with direct access to the most important programms, combined with multi touch and the power of a dual core cpu ...

Hope some one made it work

greetings

lrohr

---

### Post by tomfrancart on 2010-07-02
Hi,

I recently acquired an Acer Aspire Timeline 1825ptz. It is very similar to the 1810, except of course for the touch screen.

**Power saving etc**
I found a lot of good and useful information about the 1810 on
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1341325](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1341325)

Note that to get the acerhdf ([http://piie.net/?section=acerhdf](http://piie.net/?section=acerhdf)) kernel module working, you need to add the bios version of the 1825ptz to it:
/* Acer 1825xx */
       {"Acer", "Aspire 1825PTZ",  "V1.3118", 0x55, 0x58, {0x9e, 0x00} },

To be able to compile the module, you need to install linux-headers-<your version> *and * linux-headers-<your version>-generic 


**Touch screen**
I got the touch screen working with a few tricks:

- Installed kernel 2.6.35 from ppa
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-rc1-lucid/")

- The touch screen is now recognised by X11/evdev, but as a touch *pad* instead of a touch *screen*. I fixed this by applying the patch described here:
[https://bugzilla.redhat.com/show_bug.cgi?id=518494](https://bugzilla.redhat.com/show_bug.cgi?id=518494)
( modify evdev.c: replace
if (num_buttons || TestBit(BTN_TOOL_FINGER, pEvdev->key_bitmask)) {
by
if (TestBit(BTN_TOOL_FINGER, pEvdev->key_bitmask)) {
)
(using apt-get source xserver-xorg-input-evdev)

I also filed a bug on launchpad:
[https://bugs.launchpad.net/bugs/604097](https://bugs.launchpad.net/bugs/604097)

- Now the touch screen needs to be calibrated. I used xinput_calibrator:
[http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)

**Screen rotation**
I haven't found out yet how to use the G sensor for automatic screen rotation. However, I remapped the P-button next to the touch screen to rotate the screen. 
I attached the script used to rotate the screen. Note that it includes the calibration values. It is probably possible to retrieve them from X. Also, I wonder why it is necessary to change the calibration when rotating the axes, shouldn't this be automatic?

To be able to use the P button, I added the following to /etc/rc.local :
setkeycodes e070 112
Then used gnome-keybinding-properties to execute the rotate script when it is pressed

** Still to do:**
- Get multitouch or other gestures working and configure it such that the panel becomes useful without a keyboard. Especially two-finger scroll would be very useful. (some more info here: [http://blogs.gnome.org/carlosg/2010/01/29/multi-touch-support-in-linuxxorggtk/](http://blogs.gnome.org/carlosg/2010/01/29/multi-touch-support-in-linuxxorggtk/) )
- Figure out how to use the G sensor. 

best regards,
Tom

---

### Post by arobase40 on 2010-07-29
> **tomfrancart said:**
> Hi,

I recently acquired an Acer Aspire Timeline 1825ptz. It is very similar to the 1810, except of course for the touch screen.

I found a lot of good and useful information about the 1810 on
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1341325](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1341325)

I got the touch screen working with a few tricks:

- Installed kernel 2.6.35 from ppa
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-rc1-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.35-rc1-lucid/")

- The touch screen is now recognised by X11/evdev, but as a touch *pad* instead of a touch *screen*. I fixed this by applying the patch described here:
[https://bugzilla.redhat.com/show_bug.cgi?id=518494](https://bugzilla.redhat.com/show_bug.cgi?id=518494)
( modify evdev.c: replace
if (num_buttons || TestBit(BTN_TOOL_FINGER, pEvdev->key_bitmask)) {
by
if (TestBit(BTN_TOOL_FINGER, pEvdev->key_bitmask)) {
)
(using apt-get source xserver-xorg-input-evdev)

- Now the touch screen needs to be calibrated. I used xinput_calibrator:
[http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)

- I haven't found out yet how to use the G sensor for automatic screen rotation. However, I remapped the P-button next to the touch screen to rotate the screen. I will edit this post later and describe how I did this.

Still to do:
- Get multitouch or other gestures working and configure it such that the panel becomes useful without a keyboard. Especially two-finger scroll would be very useful. (some more info here: [http://blogs.gnome.org/carlosg/2010/01/29/multi-touch-support-in-linuxxorggtk/](http://blogs.gnome.org/carlosg/2010/01/29/multi-touch-support-in-linuxxorggtk/) )
- Figure out how to use the G sensor. 

best regards,
Tom

Hi Tom,

How did you get the touchscreen working with kernel-2.6.35-rc1 while there is no touchscreen drivers for the 1825ptz in this version ???

The hid-cando driver exists only in 2.6.35-rc2 and newer version... ^^

You also said that you got screen rotation, but do the axes follow the rotation ?

---

### Post by tomfrancart on 2010-07-30
> **arobase40 said:**
> Hi Tom,

How did you get the touchscreen working with kernel-2.6.35-rc1 while there is no touchscreen drivers for the 1825ptz in this version ???

The hid-cando driver exists only in 2.6.35-rc2 and newer version... ^^

You also said that you got screen rotation, but do the axes follow the rotation ?

I used a kernel  >2.6.35-rc2, the link in my post was wrong. I corrected it.
I also attached the rotation script.

best regards,
Tom

---

### Post by arobase40 on 2010-07-30
Arf, That's what I thought... and do you know that from rc3 et above you shoud'nt need calibration anymore (no need for xinput-calibrator) ? ;)
Your pach should be sufficient, but if you use xf86-input-evdev 2.4 it works as well the same way, but the drawback is that the touchscreen will only be a monotouch one, for the moment... :(

I'm working also on xf86-input-evdev from the ENAC, and if it shows multitouch there is still a problem with calibration... ^^
From rc3 to rc6 the behaveviour sounds really different... ^^

I tested your rotate script and it looks very nice ! :p 
Good job Tom !!!

---

### Post by Aidenairel on 2010-08-01
Wow tom, haha, I have a very little background and experience when it comes to programming..

So this looks quite scary.

How do I start, since I have already installed Ubuntu NE LL.?

---

### Post by arobase40 on 2010-08-02
> **Aidenairel said:**
> Wow tom, haha, I have a very little background and experience when it comes to programming..

So this looks quite scary.

How do I start, since I have already installed Ubuntu NE LL.?


You have all the necessary informations here :

[http://ubuntuforums.org/showthread.php?p=9671569&posted=1#post9671569](http://ubuntuforums.org/showthread.php?p=9671569&posted=1#post9671569)
;)

Install your (x)buntu 10.04 Lucid as normal and accept all the localization if needed. after that do all the initial upgrades proposed by the system.

At last, apply all the "extended upgrades" as notified above, and all should be fine...

You can also launch gconf-editor (with Alt-F2) : apps -> panel -> toplevels -> top_panel -> size

Change the value from 24 to 36 or any other value that suite to your finger... :D

---

### Post by lrohr on 2010-08-17
Thanx for the full thread, I finally did it and bought the 1825ptz I'm running ubuntu 10.4 netbook edition right now and things work great !

I noticed some things:

when the display is turned around, the angle of which you can see things on the screen is crappy, except you invert the display...
So I changed the script to make the inversion possible.

How ever, just after using your rotation script the first time the brightness buttons lost their functions. Before that they worked right out of the box... Do you have any idea why ?

Is it possible somehow to change the fanspeed it self ? I would like to toggle the speed of the fan rather than just turn it on and off again ...

And does anybody now what the acerhdf-virtual-0 temperature is ?

```
1825:~# sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +50.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +54.0°C  (high = +105.0°C, crit = +105.0°C)  

acerhdf-virtual-0
Adapter: Virtual device
temp1:       +61.0°C  (crit = +63.0°C)   
```

Greetings

---

### Post by arobase40 on 2010-08-25
> **lrohr said:**
> Thanx for the full thread, I finally did it and bought the 1825ptz I'm running ubuntu 10.4 netbook edition right now and things work great !

I noticed some things:

when the display is turned around, the angle of which you can see things on the screen is crappy, except you invert the display...
So I changed the script to make the inversion possible.

How ever, just after using your rotation script the first time the brightness buttons lost their functions. Before that they worked right out of the box... Do you have any idea why ? 

No idea about this as I don't have this problem...
Maybe this depends on your kernel version ?!?!?!

The sole problem I have sometimes is that the Desktop get scrambled after rotations and when I get back to the standard display. This problem does not occur with firefox, the Terminal... ^^
I guess a one solution could be to kill the script and then to reload it after the rotation finish. To be tested...


> **lrohr said:**
> Is it possible somehow to change the fanspeed it self ? I would like to toggle the speed of the fan rather than just turn it on and off again ...

No idea either...

> **lrohr said:**
> And does anybody now what the acerhdf-virtual-0 temperature is ?

```
1825:~# sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +50.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +54.0°C  (high = +105.0°C, crit = +105.0°C)  

acerhdf-virtual-0
Adapter: Virtual device
temp1:       +61.0°C  (crit = +63.0°C)   
```Greetings

I don't even have this last value (acerhdf-virtual-0) as I don't use acerhdf... ^^

Best regards

---

### Post by arobase40 on 2010-08-25
Hi,

I think I have found some informations about the G sensor for this 1825(ptz)...

I first watch at the Acer drivers for Windows and found a reference : SMO8800. I poke around google but found nothing useful except this is a sensor made by ST Micro... :(
But I watch again in the drivers located in the "C:\OEM\Preload\Autorun\DRV\MISC G sensor LIS33DETR" directory and found another reference LIS33DETR, which looks like to be the real reference of the ScreenDetection device for autoscreen rotation.
There is no source code reference at all in any versions of linux kernel (I watched at 2.6.36-rc1), but after a deep search with google, I found 2 things : a script which was supposed to read informations about a 3D Accelerator on Palo35 device and using a LIS33DE with i2c-dev module... But this script does not work as it could even not read the registers... May be I missed something... ??? Some differences between the lis33DE and lis33DETR ??? ^^

[http://permalink.gmane.org/gmane.linux.distributions.gumstix.general/49727](http://permalink.gmane.org/gmane.linux.distributions.gumstix.general/49727)

At least, I then found all the C source code for the list33DE driver in the Android-kernel trunk... ^^ :)
I have not integrated this code in a linux kernel nor have I tested it, yet !

[http://code.google.com/p/m8-android-kernel/source/browse/trunk/drivers/i2c/chips/lis302dl.c](http://code.google.com/p/m8-android-kernel/source/browse/trunk/drivers/i2c/chips/lis302dl.c)

I will try to compile it and see if I can get if work, but if you are quicker than me, you can use it at your own risk... ^^

Best regards,

---

### Post by arobase40 on 2010-08-27
Some new informations about the accelerometor used by the Acer 1825ptz...

I found out a few 2 years old codes used by a other model : lis3lv02DL  (in HTC Shift) but closed to the one use by the 1825pt(z).

[http://pof.eslack.org/blog/2008/06/0...hift-g-sensor/]("http://pof.eslack.org/blog/2008/06/03/i2c-gsensor-lis3lv02dl-accelerometer-on-htc-shift-g-sensor/")

Just download i2c-gsensor file, edit the i2c-gsensor.c file and change the line :

#define WHO_AM_I    0x3a

by 

#define WHO_AM_I    0x3b

Compile and play with it under Terminal ! :razz:

As you will notice, this is a 3 axis only accelerometor. That means you   won't be able to make difference between Left and Right... ^^ :sad:

After a deep search in  the linux source code, I finally found the same  reference (lis3lv02DL) in driver/hwmon and probably the magic number  under lis3lv02d.h . That means that the code and modules are already  there, but I don't know how to use them yet... ^^
I will let you know as soon I have more informations.

regards

---

### Post by arobase40 on 2010-09-02
Hi again,

I forgot to mention you need to load i2c-i801 and i2c-dev modules first before you can use the i2c-gsensor util... ^^

I'm surprised about nobody's reactions about this...

---

### Post by lrohr on 2010-09-04
Hi ):P

and sorry for not responding, did you manage the sensors to work ?

I didn't have the time yet to play with the sensors jet. 

And I also have some issues with the Desktop freezing somehow maybe because of some compiz action, not shure jet, but I can always go to the terminal with strg+alt+f1 and do a restart gdm.

---

### Post by greenjeeper on 2010-09-10
Hi 

Great Job !! :D

Best regards,
Alex

---

### Post by modemlamer on 2010-09-10
i got multitouch working!

what works: more than one MouseCursor on screen
what not: marcos identifying mousemoves and firing marcos 4 : rotating window / zoon (in/out) / 3tip= right-click / scroll(up/down)

how did it works:

Hardware: Acer 1825PTZ

OS: Ubuntu 10.04 64 Bit

-> update&&upgrade 
described here:

[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

replace kernelversion : 2.6.35-20

-> get the multitouch drivers:
[http://lii-enac.fr/en/projects/shareit/xf86-input-evdev.tar.bz2](http://lii-enac.fr/en/projects/shareit/xf86-input-evdev.tar.bz2)

patch:
> 
( modify xf86-input-evdev/src/evdev.c:Line:2312 replace
if (num_buttons || TestBit(BTN_TOOL_FINGER, pEvdev->key_bitmask)) {
by
if (TestBit(BTN_TOOL_FINGER, pEvdev->key_bitmask)) {
)


$ sudo ./autogen.sh -prefix=/usr
$ sudo make && sudo make install

reboot

now u have:
 a kernel handling the cando 11.6 correct
 latest inteldrivers
 latest X server

upgrading from  single 2 multitouch

get the multitouch-"i call it deamon"-d

[http://lii-enac.fr/en/projects/shareit/multitouchd.tar.bz2](http://lii-enac.fr/en/projects/shareit/multitouchd.tar.bz2)

to compile this this tool u need the following packages

$ sudo apt-get install libxtst6 libxtst-dev libxcursor1 xcursor-themes

in the multitouchd dir:

$ make

finally: 
$ ./multitouchd

now u hopefully can see alt least 2 cursors following your fingers at a time

REF: [http://lii-enac.fr/en/projects/shareit/xorg-howto.html](http://lii-enac.fr/en/projects/shareit/xorg-howto.html)
REF: [http://ubuntuforums.org/showpost.php?p=9538094&postcount=2](http://ubuntuforums.org/showpost.php?p=9538094&postcount=2)
REF: [http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)
PS: this is my first how-to-like post

---

### Post by arobase40 on 2010-09-13
> **lrohr said:**
> Hi ):P

and sorry for not responding, did you manage the sensors to work ?

I didn't have the time yet to play with the sensors jet. 

And I also have some issues with the Desktop freezing somehow maybe because of some compiz action, not shure jet, but I can always go to the terminal with strg+alt+f1 and do a restart gdm.

Sorry not, I had no time to work on it for the moment as I work on different projects at the same time :
1) Still working on the multitouch issue.
2) I'm also working on a mod of my Wind U115 trying to make it a touch tablet with an accelorometer... ^^
3) For the sensor of the 1825ptz, I have to contact the authors of the lis3lv02d module to modify their modules to take in account the specification of this sensor.
4) I have to write a specific script for auto-rotation as the one I have use the Wacom modules...

Concerning your specific problem with the Desktop freeze, I guess it is due to the rotate manual script with the P-button, isn't it ? Nothing specific about compiz, I think...
I think I have a solution, but again it is a matter if time : the issue is to write two separate scripts. This will be my first priority !
 
regards,

---

### Post by arobase40 on 2010-09-13
> **modemlamer said:**
> i got multitouch working!

what works: more than one MouseCursor on screen
what not: marcos identifying mousemoves and firing marcos 4 : rotating window / zoon (in/out) / 3tip= right-click / scroll(up/down)

how did it works:

Hardware: Acer 1825PTZ

OS: Ubuntu 10.04 64 Bit

-> update&&upgrade 
described here:

[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

replace kernelversion : 2.6.35-20

-> get the multitouch drivers:
[http://lii-enac.fr/en/projects/shareit/xf86-input-evdev.tar.bz2](http://lii-enac.fr/en/projects/shareit/xf86-input-evdev.tar.bz2)

patch:


$ sudo ./autogen.sh -prefix=/usr
$ sudo make && sudo make install

reboot

now u have:
 a kernel handling the cando 11.6 correct
 latest inteldrivers
 latest X server

upgrading from  single 2 multitouch

get the multitouch-"i call it deamon"-d

[http://lii-enac.fr/en/projects/shareit/multitouchd.tar.bz2](http://lii-enac.fr/en/projects/shareit/multitouchd.tar.bz2)

to compile this this tool u need the following packages

$ sudo apt-get install libxtst6 libxtst-dev libxcursor1 xcursor-themes

in the multitouchd dir:

$ make

finally: 
$ ./multitouchd

now u hopefully can see alt least 2 cursors following your fingers at a time

REF: [http://lii-enac.fr/en/projects/shareit/xorg-howto.html](http://lii-enac.fr/en/projects/shareit/xorg-howto.html)
REF: [http://ubuntuforums.org/showpost.php?p=9538094&postcount=2](http://ubuntuforums.org/showpost.php?p=9538094&postcount=2)
REF: [http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)
PS: this is my first how-to-like post

Your workaroud for multitouch, I guess, is some kind of "false positive"... I have experiment it myself more or less the same way, but what you get (2 cursors following the fingers at the same time) is due to a wrong detection of the characteristics. I have contacted Benjamin Tissoire, the author of the [http://lii-enac.fr/en/projects/shareit/xf86-input-evdev.tar.bz2](http://lii-enac.fr/en/projects/shareit/xf86-input-evdev.tar.bz2) multitouch driver who confirm  this problem...

You will have to wait for a further version... ^^ and futur release of utouch...

Sorry.

---

### Post by arobase40 on 2010-09-23
Here is a new version of the manual rotation script.

Rename rotate.sh to rotate and rotate-screen.sh to rotate-screen
It is written in 2 parts and both files are to be placed in the same dir (part of your env variables).
Only the rotate script is to be binded to the P-button.

If someone can propose better optimization...

I "may" post a first version of an auto-rotate script soon... Hopefully... ^^

---

### Post by arobase40 on 2010-09-26
Great news !!!

For the most adventurious geeks, here is an **experimental** "driver" for auto-rotation of the screen panel for the Acer 1825(PT-PTZ) :

[http://forum.ubuntu-fr.org/viewtopic.php?pid=3750522#p3750522](http://forum.ubuntu-fr.org/viewtopic.php?pid=3750522#p3750522)

This is not really a driver nor a module, but a small program based on  the i2c-gsensor program I have previously given a link to and which have  been modified by imarune, a french guy. You will also find a script to  be loaded at startup time and which call this program every time you  turn the computer in any four directions.

As I mentioned above, this is experimental and it need some  modifications as it has been written for the Fedora version of Linux,  and for what I have tested, it only works if you turn the computer  around, but not if you only turn the panel... ^^

The program and the script should work with other machines than the Acer  1825 with little modifications as long as it use a 8 bits "lis3llv02d"  based accelerometer.

I will publish the the modified script that suit the Ubuntu system (with  the c source code) with english explanations if imarune allow me to do  it, unless he does it himself.

About the "lis3llv02d module, it contains all the code needed to handle  the accelerometer of the Acer 1825, but it must be called by another  module, hp_accel, which a glue between the system and the module. But  the problem is that it is harded coded for HP computers. I'm  experimenting a modified version and I'm compiling it at the present  time. Hopefully it will work... ^^

---

### Post by lrohr on 2010-10-02
Hi arobase40,

I modified your code a little bit, maybe your interested in it.

first I changed the lines 
```
xinput set-int-prop "$id" "Evdev Axis Calibration" 32 $calibx $caliby
```
to
```
xinput set-prop --type=int --format=32 "$id" "Evdev Axis Calibration" $caliby $calibx
```
because set-int-prop is deprecated.

I also tried to work with onboard as a on screen keyboard. I used your old skript, the new one looks like you did this to, but may be in a nicer way than I did, not shure yet.

I frirst do a ps -ef | grep to look if a onboard is running and kill it than. And afterwards I start it new, always in the downer left corner, except when I go back to "normal".

So the changes looks like this
```
# search for the process ids (pid) of running on screen keyboard called onboard
pids="$(ps -ef | grep  onboard | awk '{print $2}')"

#for each pid
for pid in ${pids[@]}
do
    kill $pid 
# kill the onboard process 
# since the "grep onboard" also gives a pid which is no longer available when kill is called
# this line produces an error which isn't oft intrest anyway
done


if [ "$dir" == "normal" ]
then
    xinput set-prop "$id" "Evdev Axis Inversion" 0, 0
        xinput set-prop "$id" "Evdev Axes Swap" 0
        xinput set-prop --type=int --format=32 "$id" "Evdev Axis Calibration" $calibx $caliby
# I don't want onboard in normal mode if you like uncomment the line below
#    onboard -x 0 -y 500 -s 1366x268 &
fi

if [ "$dir" == "left" ]
then
    xinput set-prop "$id" "Evdev Axis Inversion" 1, 0
        xinput set-prop "$id" "Evdev Axes Swap" 1
    xinput set-prop --type=int --format=32 "$id" "Evdev Axis Calibration" $caliby $calibx
    #produce the onboard keyboard 
    onboard -x 0 -y 1100 -s 768x266 & 
fi

if [ "$dir" == "right" ]
then
    xinput set-prop "$id" "Evdev Axis Inversion" 0, 1
        xinput set-prop "$id" "Evdev Axes Swap" 1
        xinput set-prop --type=int --format=32 "$id" "Evdev Axis Calibration" $caliby $calibx
    #produce the onboard keyboard 
    onboard -x 0 -y 1100 -s 768x266 & 
fi

if [ "$dir" == "inverted" ]
then
    xinput set-prop "$id" "Evdev Axis Inversion" 1, 1
        xinput set-prop "$id" "Evdev Axes Swap" 0
        xinput set-prop --type=int --format=32 "$id" "Evdev Axis Calibration" $calibx $caliby
    #produce the onboard keyboard 
    onboard -x 0 -y 500 -s 1366x268 & 
fi
```

maybe you like it.

Now I take a look at your link to use the gsensors.

Greetings

lrohr

---

### Post by arobase40 on 2010-10-03
> **lrohr said:**
> Hi arobase40,

I modified your code a little bit, maybe your interested in it.
...

I also tried to work with onboard as a on screen keyboard. I used your old skript, the new one looks like you did this to, but may be in a nicer way than I did, not shure yet.

...

maybe you like it.

Now I take a look at your link to use the gsensors.

Greetings

lrohr

Sure, any improvement of the code is of interess.

I have not tested your changes yet, but they look nice, specially the change of the size and position of the onboard keyboard depending of the rotation. :)

But when you talk about the old (and first) script, it's not mine but Tomfrandcart's one. ^^
The rotate.sh script version I published is quite different from the one written by Tom and it works together with rotate-screen.sh.
This is an important point as I notice that rotate.sh has been viewed twice while rotate-screen.sh four times... ^^

Give me some more days and I will publish the codes for the gsensor and the changes for Ubuntu.
The codes have been taken from i2c-gsensor and gsensor-joy-1.1.

---

### Post by ceh-photo.de on 2010-10-11
has anybody got the touchscreen working under new ubuntu 10.10?

I used the howto on the last thread page. tried it with the newest xserver-xorg-input-evdev from github and also with the sources from the ubuntu repo.

I am struggling 2 days, put the result is, that the initial support of ubuntu 10.10 which detects the touchscreen as touchpad does not work either.

Can anybody help?

It seems as the touchscreen is recognized correct - Xorg.log

[PHP]16.073] (II) config/udev: Adding input device Cando      11.6  (/dev/input/event5)
[    16.073] (**) Cando      11.6 : Applying InputClass "evdev touchscreen catchall"
[    16.073] (**) Cando      11.6 : Applying InputClass "touchscreen catchall"
[    16.073] (**) Cando      11.6 : Applying InputClass "tslib touchscreen"
[    16.073] (II) LoadModule: "tslib"
[    16.074] (II) Loading /usr/lib/xorg/modules/input/tslib_drv.so
[    16.074] (II) Module tslib: vendor="X.Org Foundation"
[    16.074]    compiled for 1.8.99.905, module version = 0.0.1
[    16.074]    Module class: X.Org XInput Driver
[    16.074]    ABI class: X.Org XInput driver, version 11.0
[    16.074] (**) Cando      11.6 : always reports core events
[    16.112] (II) XINPUT: Adding extended input device "Cando      11.6 " (type: TOUCHSCREEN)
[    16.112] xf86TslibControlProc
[    16.112] xf86TslibControlProc
[    16.112] (II) config/udev: Adding input device Cando      11.6  (/dev/input/mouse0)
[    16.112] (**) Cando      11.6 : Applying InputClass "touchscreen catchall"
[    16.112] (**) Cando      11.6 : Applying InputClass "tslib touchscreen"
[    16.112] (**) Cando      11.6 : always reports core events
[    16.151] (II) XINPUT: Adding extended input device "Cando      11.6 " (type: TOUCHSCREEN)
[/PHP]


[PHP]
~$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Cando      11.6                         	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Cando      11.6                         	id=11	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; CNF9011                                 	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]

[/PHP]

---

### Post by arobase40 on 2010-10-12
Hi,

First, I don't think the input-tslib drivers is needed and maybe it could cause some incompatibilies with input-evdev.. Not sure, but you could try uninstalling it...

If that does not solve the problem, try a different version, but not below 2.4 unless you apply Tomfrancart's patch.

BUT, I think Ubuntu 10.10 is still buggy. I have not tested the final version just the RC one and whatever the version of input-evdev you use there are still problems. :(

If you use input-evdev 2.4, the touchscreen is correctly recognized and calibrated, but if you open a terminal you can't revert back to the desktop touching the upper left corner (with Ubuntu Netbook Edition), unless you close the terminal or Alt-Tab.

Not quite sure there are much differences between rc and final version and I just tested the Netbook Edition...

---

### Post by greenjeeper on 2010-10-12
Hi,
input-tslib is not needed and should be removed. 
Touchscreen work fine with Ubuntu 10.10 and patcht evdev-driver.:smile:

Alex

---

### Post by ceh-photo.de on 2010-10-12
> **greenjeeper said:**
> Hi,
input-tslib is not needed and should be removed. 
Touchscreen work fine with Ubuntu 10.10 and patcht evdev-driver.:smile:

Alex

Which source to you use for patching evdev? the current version from the ubuntu repository?

Yet I ppa:purge everything new x-stuff and then downloaded evdev 2.4 build and installed it, put nothing changed. What did you do?

---

### Post by greenjeeper on 2010-10-12
Hi,
i installed Ubuntu, xorg-dev and evdev-source (2.3.2) from the ubuntu repository.
Then I unpacked the evdev-source. The file evdev.c as in post 2 edited, compiled, and installed the driver (copy to /usr/lib/xorg/...). 
Thats all :)

 input-tslib and evtouch should be removed

PS:Sorry for my bad English that I never properly learned.
I have taught myself

Alex

---

### Post by arobase40 on 2010-10-12
> **greenjeeper said:**
> Hi,
i installed Ubuntu, xorg-dev and evdev-source (2.3.2) from the ubuntu repository.
Then I unpacked the evdev-source. The file evdev.c as in post 2 edited, compiled, and installed the driver (copy to /usr/lib/xorg/...). 
Thats all :)

 input-tslib and evtouch should be removed

PS:Sorry for my bad English that I never properly learned.
I have taught myself

Alex

Which version of Ubuntu do you use ?

I installed Ubuntu 10.10 Netbook Edition, but there is still problems even after the patch... Impossible to use the left applications bar with the finger.

Otherwise many shortcuts have been removed (ALT-F2, for instance), multiple instances of applications do not work, impossible to resize the top status bar, ... ^^ :mad:

---

### Post by greenjeeper on 2010-10-12
Ubuntu 10.10 Desktop.
netbook I have not tested.

Alex

---

### Post by greenjeeper on 2010-10-12
Now I have installed netbook and it works. A quick touch opens the application.:)
But close to the buttons are too small.

Alex

---

### Post by ceh-photo.de on 2010-10-12
Nice singletouch works now correct on my acer. but i do not understand why the xorg-tslib must be deleted?Is it a bug?

If I compare the xinput --list with and without xorg-tslib I see, that with tslib I have two cando interfaces 

Then I have compared the manual patched evdev driver 2.32 and 2.4. The 2.32 version works much better. 2.4 does not start the applications on one click.

(I use Ubuntu 10.10 Netbook Edition)

Is it possible to get multitouch working?

---

### Post by arobase40 on 2010-10-12
> **greenjeeper said:**
> Now I have installed netbook and it works. A quick touch opens the application.:)
But close to the buttons are too small.

Alex

Really strange.... I could'nt get it fully working. But I don't like this version anyway that's why I won't insist with it... ^^ 

About the close button, you'll have to change the theme, something like Clearlooks-large...

---

### Post by arobase40 on 2010-10-12
> **ceh-photo.de said:**
> Is it possible to get multitouch working?

Not yet... ^^

---

### Post by ceh-photo.de on 2010-10-13
Exists some possibility to get a right click on the touchscreen? Some script? If it does not exists where is the right place to implement something like this?

---

### Post by arobase40 on 2010-10-13
> **ceh-photo.de said:**
> Exists some possibility to get a right click on the touchscreen? Some script? If it does not exists where is the right place to implement something like this?

Of cource, this is possible... Just open up the source code of input-evdev 2.3.2 and compare it with version 2.4 or 2.5. All is implemented and can be "freely" customized...
:guitar:

---

### Post by greenjeeper on 2010-10-13
> **ceh-photo.de said:**
> Exists some possibility to get a right click on the touchscreen? Some script? If it does not exists where is the right place to implement something like this?

System->Preferences->Mouse->Accessibility

Set the Checkbutton by "Simulate Secondary Click" :)

Alex

---

### Post by ceh-photo.de on 2010-10-13
> **greenjeeper said:**
> System->Preferences->Mouse->Accessibility

Set the Checkbutton by "Simulate Secondary Click" :)

Alex

Year, I found it before you posted. this works nice.

Thanks

Put I have found another problem: If I use Ubuntu Unity some times I am unable to click the program icons with touch, this problem occurs with evdev drivers 2.32 with 2.4 2.5.I have the problem all the time.  In Ubuntu Desktop this problem is not visible.

---

### Post by greenjeeper on 2010-10-13
The problem is, the touch must be very short.
Oder auf Deutsch sehr kurz! 

Alex

---

### Post by ceh-photo.de on 2010-10-14
> **greenjeeper said:**
> The problem is, the touch must be very short.
Oder auf Deutsch sehr kurz! 

Alex

Mmh but why exists this behavior only on the application button bar. Every other button reacts normal (useable for touch). Is some where a configuration for this timeout...?

Has somebody tried the g-sensor implementation from the french ubuntu forum?

---

### Post by arobase40 on 2010-10-14
> **ceh-photo.de said:**
> Mmh but why exists this behavior only on the application button bar. Every other button reacts normal (useable for touch). Is some where a configuration for this timeout...?

Has somebody tried the g-sensor implementation from the french ubuntu forum?

Really sorry ! I know I promised to publish the g-sensor and lis3lv02d/lis3lv02d_i2c implementation, but I was sick and really tired during the same week. I will start to do it this evening or this night.

There are 3 different ways to handle the accelerometer and that's partly the reason why it took me some time to decide which is the better.

So I'll publish the 3 ways and you'll decide which one suit to you...

---

### Post by ceh-photo.de on 2010-10-14
> **arobase40 said:**
> Really sorry ! I know I promised to publish the g-sensor and lis3lv02d/lis3lv02d_i2c implementation, but I was sick and really tired during the same week. I will start to do it this evening or this night.

There are 3 different ways to handle the accelerometer and that's partly the reason why it took me some time to decide which is the better.

So I'll publish the 3 ways and you'll decide which one suit to you...
Hey cool thats sound really promising. If you need some help for what ever... write how I could help.

---

### Post by arobase40 on 2010-10-14
_**G-SENSOR / ACCELEROMETER for the Acer 1825PT(Z)**** : Part I**_
(This should also works with some Dell machines, Samsung  NB30, Acer1410, 1810TZ, 1810T (?), and some Packard Bell clones of the Acer Tablet PC laptops)

Here we go !!!

_**1° way :**_
 
 The first code is based on i2c-gsensor and gsensor-joy-1.1, so you'll  have to get the i2c-gsensor tar ball in order to use the i2c-dev.h and  the Makefile, then replace the i2c-gsensor.c with the code below.
The gsensor-joy-1.1 is not needed unless you want to study it...

[http://pof.eslack.org/blog/2008/06/0...hift-g-sensor/]("http://pof.eslack.org/blog/2008/06/03/i2c-gsensor-lis3lv02dl-accelerometer-on-htc-shift-g-sensor/")

```

/*
    HTC Shift G-Sensor Reader
    Reads data from i2c interface, chip STMicroelectronics LIS3LV02DL

    Copyright (C) 2008       Esteve Espuna <esteve@eslack.org>
                             Pau Oliva <pof@eslack.org>

    Based on i2cget.c:
    Copyright (C) 2005       Jean Delvare <khali@linux-fr.org>

    Based on i2cset.c, i2cbusses.c:
    Copyright (C) 2001-2003  Frodo Looijaard <frodol@dds.nl>, and
                             Mark D. Studebaker <mdsxyz123@yahoo.com>
    Copyright (C) 2004-2005  Jean Delvare <khali@linux-fr.org>
    
    Modified by Arobase Chac (arobase40) and Imarune for the Acer 1825PT(Z).
    May work with some Dell machine, Samsung NB30, Acer 1410, 1810TZ, 1810T and some Packard Bell clone of the Acer tablet pc laptops...

    This program is free software; you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation; either version 2 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program; if not, write to the Free Software
    Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
    MA 02110-1301 USA.
*/

#include <sys/types.h>
#include <sys/stat.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <stdio.h>
#include <fcntl.h>
#include "i2c-dev.h"

#define WHO_AM_I    0x3b

int open_i2c_dev(const int i2cbus, char *filename, const int quiet)
{
    int file;

    sprintf(filename, "/dev/i2c/%d", i2cbus);
    file = open(filename, O_RDWR);

    if (file < 0 && errno == ENOENT) {
        sprintf(filename, "/dev/i2c-%d", i2cbus);
        file = open(filename, O_RDWR);
    }

    if (file < 0 && !quiet) {
        if (errno == ENOENT) {
            fprintf(stderr, "Error: Could not open file "
                    "`/dev/i2c-%d' or `/dev/i2c/%d': %s\n",
                    i2cbus, i2cbus, strerror(ENOENT));
        } else {
            fprintf(stderr, "Error: Could not open file "
                    "`%s': %s\n", filename, strerror(errno));
            if (errno == EACCES)
                fprintf(stderr, "Run as root?\n");
        }
    }
    
    return file;
}

int main(int argc, char *argv[])
{
    int res, i2cbus = 0, address, file, loop=0, dir=-1;
    int xl,xh;
    int yl,yh;
    int zl,zh;
    short x,y,z;
    int magic;
    char filename[20];

    if ( argc >= 2 ) {
        i2cbus = atoi(argv[1]);
        if (argc == 3 && strcmp(argv[2], "loop") == 0)
            loop = 1;
    }    
    else {
        fprintf(stderr, "Usage : %s i2cbus [loop]\n", argv[0]);
        exit (1);
    }


    address = 0x1d;
    file = open_i2c_dev(i2cbus, filename , 0);

    ioctl(file, I2C_SLAVE, address);
    i2c_smbus_write_byte_data(file, 0x20, 0x47);
    i2c_smbus_write_byte_data(file, 0x21, 0x63);

    magic = i2c_smbus_read_byte_data(file, 0xf);
    if (magic != WHO_AM_I ) {
        printf("Accelerometer not found\n");
        exit(-1);
        }
    while (1)
        {
        sleep(2);
        xh = i2c_smbus_read_byte_data(file, 0x28);
        xl = i2c_smbus_read_byte_data(file, 0x29);
        x = (xh<<8) | ( xl );
        yh = i2c_smbus_read_byte_data(file, 0x2a);
        yl = i2c_smbus_read_byte_data(file, 0x2b);
        y = (yh<<8) | ( yl );
        zh = i2c_smbus_read_byte_data(file, 0x2c);
        zl = i2c_smbus_read_byte_data(file, 0x2d);
        z = (zh<<8) | ( zl );
        printf("x = %d y = %d z = %d", x, y, z);
        if ( x < 128 ) {
            /* printf("Normal orientation\n"); */
            dir=0;
            }
        else
            {
            if ( y < 128 ) {
                /* printf("Left orientation\n"); */
                dir=1;
                }
            else
                {
                if (  z < 128 ) {
                    /* printf("Right orientation\n"); */
                    dir=2;
                    }
                else {
                    /* printf("Inverted orientation\n"); */
                    dir=3;
                    }
                }
            }
        if ( !loop )
            break;
        }
    close(file);

    exit(dir);
}

```Just compile it and copy it somewhere in /usr/bin or /usr/local/bin.
Put "i2c-i801" and "i2c-dev" in your /etc/modules, then reboot.
 Finally call i2c-gsensor as root or with sudo, passing 0 and optionally "loop" as parameter.

The loop parameter is just for testing mode (not needed in the script), while the i2cbus may vary  from 0 to 7 depending of the linux distribution and the loading order of  the previous modules (at boot time or loaded by the script).

With Ubuntu, the i2cbus parameter **should** be 0, but I can't guarantee this is always the case.

In Part II, you will find the script which use this pseudo-driver and  which will rotate the display according to the return value of  i2c-gsensor.
In the same script there will be an optional tip to find out the entry point to the i2c bus (for the i2cbus parameter)...

_**2° way :**_

Now, a patch to modify the kernel lis3lv02d_i2c module.
cd  [dir_source_kernel]/drivers/hwmon; patch -p0 < [dir_patch]/lis3lv02d_i2c.patch)
Then recompile the whole kernel and when all is done, you just need to write down "lis3lv02d_i2c" in the /etc/modules file.

```

--- lis3lv02d_i2c_orig.c 2010-09-29 03:01:22.000000000 +0200
+++ lis3lv02d_i2c.c 2010-10-06 15:18:30.521867001 +0200
@@ -33,6 +33,9 @@
 
#define DRV_NAME "lis3lv02d_i2c"
 
+/* Addresses to scan */
+static const unsigned short normal_i2c[] = { 0x1d, I2C_CLIENT_END };
+
static inline s32 lis3_i2c_write(struct lis3lv02d *lis3, int reg, u8 value)
{
struct i2c_client *c = lis3->bus_priv;
@@ -60,6 +63,26 @@
return lis3->write(lis3, CTRL_REG1, reg);
}
 
+/* Return 0 if detection is successful, -ENODEV otherwise */
+static int lis3lv02d_i2c_detect(struct i2c_client *client,
+ struct i2c_board_info *info)
+{
+ int val;
+ struct i2c_adapter *adapter = client->adapter;
+
+ if (!i2c_check_functionality(adapter,
+ I2C_FUNC_SMBUS_BYTE_DATA))
+ return -ENODEV;
+
+ val = i2c_smbus_read_byte_data(client, WHO_AM_I);
+ if (!((val & WAI_12B) || (val & WAI_8B)))
+ return -ENODEV;
+
+ strlcpy(info->type, "lis3lv02d", I2C_NAME_SIZE);
+
+ return 0;
+}
+
/* Default axis mapping but it can be overwritten by platform data */
static struct axis_conversion lis3lv02d_axis_map = { LIS3_DEV_X,
LIS3_DEV_Y,
@@ -157,12 +180,15 @@
.name = DRV_NAME,
.owner = THIS_MODULE,
},
+ .class = I2C_CLASS_HWMON, 
.suspend = lis3lv02d_i2c_suspend,
.shutdown = lis3lv02d_i2c_shutdown,
.resume = lis3lv02d_i2c_resume,
.probe = lis3lv02d_i2c_probe,
.remove = __devexit_p(lis3lv02d_i2c_remove),
+ .detect = lis3lv02d_i2c_detect,
.id_table = lis3lv02d_id,
+ .address_list = normal_i2c,
};
 
static int __init lis3lv02d_init(void)
 

```If everything is correctly initialized, you should see a new "p-data" platform here :

/sys/devices/platform/lis3lv02d
The "position" parameter contains the x, y, z axis coordinates...

Again, this is useless without a script to interpret theses values.
But again, you'll have to be patient... :razz:

_**3° way :**_

Here is the most fancy and weird way to initialize the lis3lv02d_i2c  module and to initialize the gsensor/accelerometer for the 1825PT(Z) !!!
It is also the quickest, uncommon and shortest way to do it !!! [IMG]http://ubuntuforums.org/images/icons/icon10.gif[/IMG]

This is mostly an unknown workaround while this has been implemented for a while... ^^
This was implemented for development purposes so nobody can guarantee it will exist in this form in the future...
You will need a 2.6.35 or 2.6.36 kernel (no need for the source code).  This should also work with kernel 2.6.34 even if of little interest as  the touchscreen doesn't work fine with this latter version.

Finallly here is the workaround :

 Load the standard and unmodified i2c-i801, i2c-dev and lis3lv02d_i2c modules in /etc/modules, then reboot...

If you can find i2c-0 in /sys/devices/pci0000:00/0000:00:1f.3 then apply as root :
#echo lis3lv02d 0x1d>/sys/devices/pci0000:00/0000:00:1f.3/i2c-0/new_device

To verify if that works :

#cat /sys/devices/pci0000:00/0000:00:1f.3/i2c-0/0-001d/name
You should see : 

#lis3lv02d 
That's it !!!!

No need to recompile the whole kernel.
When you're sure that all is correct, put the line (echo lis3lv02d 0x1d>/sys/devices/pci0000:00/0000:00:1f.3/i2c-0/new_device) in your /etc/rc.local

To follow in part II, for the scripts...

---

### Post by ceh-photo.de on 2010-10-15
nice work! I will try it this afternoon. At the moment I am unsure which option I would give a try... In your opinion which one is the most energy saving option? part 3?

[update]
Hey I decided to choose the 3. version. Everything works like described. 

Thank you for your work.

Now I am happily waiting on the next part with the scripts :D

[update]
third version: I have determined huge problems with suspend,shutdown and reboot with this configuration, I think the problem is the module lis3lv02d_i2c. I will try next the first version.

[update] first version seems to work. suspend with loaded modules etc is ok

---

### Post by arobase40 on 2010-10-16
> **ceh-photo.de said:**
> nice work! I will try it this afternoon. At the moment I am unsure which option I would give a try... In your opinion which one is the most energy saving option? part 3?

[update]
Hey I decided to choose the 3. version. Everything works like described. 

Thank you for your work.

Now I am happily waiting on the next part with the scripts :D

[update]
third version: I have determined huge problems with suspend,shutdown and reboot with this configuration, I think the problem is the module lis3lv02d_i2c. I will try next the first version.

[update] first version seems to work. suspend with loaded modules etc is ok

The scripts are not finished and not quite accurate for the moment. So be patient... unless you want them "as is" and want to work on them by yourself.
Let me know...

---

### Post by ceh-photo.de on 2010-10-16
> **arobase40 said:**
> The scripts are not finished and not quite accurate for the moment. So be patient... unless you want them "as is" and want to work on them by yourself.
Let me know...

Hey,
I am interested in the unstable/version, but I dont know if I have enough time to work on them. But I will try. Maybe we could improve it together.

I had problems with your version of i2c-gesensor and the loop option. I fixed it(missing \n in printf, dont know why its a problem). All in All 3 minor changes to your version
[PHP]
/*
    HTC Shift G-Sensor Reader
    Reads data from i2c interface, chip STMicroelectronics LIS3LV02DL

    Copyright (C) 2008       Esteve Espuna <esteve@eslack.org>
                             Pau Oliva <pof@eslack.org>

    Based on i2cget.c:
    Copyright (C) 2005       Jean Delvare <khali@linux-fr.org>

    Based on i2cset.c, i2cbusses.c:
    Copyright (C) 2001-2003  Frodo Looijaard <frodol@dds.nl>, and
                             Mark D. Studebaker <mdsxyz123@yahoo.com>
    Copyright (C) 2004-2005  Jean Delvare <khali@linux-fr.org>
    
    Modified by Arobase Chac (arobase40) and Imarune for the Acer 1825PT(Z).
    May work with some Dell machine, Samsung NB30, Acer 1410, 1810TZ, 1810T and some Packard Bell clone of the Acer tablet pc laptops...

    This program is free software; you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation; either version 2 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program; if not, write to the Free Software
    Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston,
    MA 02110-1301 USA.
*/

#include <sys/types.h>
#include <sys/stat.h>
#include <string.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <stdio.h>
#include <fcntl.h>
#include "i2c-dev.h"

#define WHO_AM_I    0x3b

int open_i2c_dev(const int i2cbus, char *filename, const int quiet)
{
    int file;

    sprintf(filename, "/dev/i2c/%d", i2cbus);
    file = open(filename, O_RDWR);

    if (file < 0 && errno == ENOENT) {
        sprintf(filename, "/dev/i2c-%d", i2cbus);
        file = open(filename, O_RDWR);
    }

    if (file < 0 && !quiet) {
        if (errno == ENOENT) {
            fprintf(stderr, "Error: Could not open file "
                    "`/dev/i2c-%d' or `/dev/i2c/%d': %s\n",
                    i2cbus, i2cbus, strerror(ENOENT));
        } else {
            fprintf(stderr, "Error: Could not open file "
                    "`%s': %s\n", filename, strerror(errno));
            if (errno == EACCES)
                fprintf(stderr, "Run as root?\n");
        }
    }
    
    return file;
}

int main(int argc, char *argv[])
{
    int i2cbus = 0, address, file, loop=0, dir=-1;
    int xl,xh;
    int yl,yh;
    int zl,zh;
    short x,y,z;
    int magic;
    char filename[20];

    if ( argc >= 2 ) {
        i2cbus = atoi(argv[1]);
        if (argc == 3 && strcmp(argv[2], "loop") == 0)
            loop = 1;
    }    
    else {
        fprintf(stderr, "Usage : %s i2cbus [loop]\n", argv[0]);
        exit (1);
    }


    address = 0x1d;
    file = open_i2c_dev(i2cbus, filename , 0);

    ioctl(file, I2C_SLAVE, address);
    i2c_smbus_write_byte_data(file, 0x20, 0x47);
    i2c_smbus_write_byte_data(file, 0x21, 0x63);

    magic = i2c_smbus_read_byte_data(file, 0xf);
    if (magic != WHO_AM_I ) {
        printf("Accelerometer not found\n");
        exit(-1);
        }
    while (1)
        {
        sleep(1);
        xh = i2c_smbus_read_byte_data(file, 0x28);
        xl = i2c_smbus_read_byte_data(file, 0x29);
        x = (xh<<8) | ( xl );
        yh = i2c_smbus_read_byte_data(file, 0x2a);
        yl = i2c_smbus_read_byte_data(file, 0x2b);
        y = (yh<<8) | ( yl );
        zh = i2c_smbus_read_byte_data(file, 0x2c);
        zl = i2c_smbus_read_byte_data(file, 0x2d);
        z = (zh<<8) | ( zl );
        printf("x = %d y = %d z = %d\n", x, y, z);
        if ( x < 128 ) {
            /* printf("Normal orientation\n"); */
            dir=0;
            }
        else
            {
            if ( y < 128 ) {
                /* printf("Left orientation\n"); */
                dir=1;
                }
            else
                {
                if (  z < 128 ) {
                    /* printf("Right orientation\n"); */
                    dir=2;
                    }
                else {
                    /* printf("Inverted orientation\n"); */
                    dir=3;
                    }
                }
            }
        if ( !loop )
            break;
        }
    close(file);

    exit(dir);
}
[/PHP]

---

### Post by arobase40 on 2010-10-16
> **ceh-photo.de said:**
> nice work! I will try it this afternoon. At the moment I am unsure which option I would give a try... In your opinion which one is the most energy saving option? part 3?

[update]
Hey I decided to choose the 3. version. Everything works like described. 

Thank you for your work.

Now I am happily waiting on the next part with the scripts :D

[update]
third version: I have determined huge problems with suspend,shutdown and reboot with this configuration, I think the problem is the module lis3lv02d_i2c. I will try next the first version.

[update] first version seems to work. suspend with loaded modules etc is ok

I think the problems you encountered with suspend,shutdown and reboot, as well as the printf are due to your Ubuntu 10.10 configuration.
I don't have theses problems with Ubuntu 10.04. But maybe it is because I also use a 2.6.36rcx kernel...

Each version of the g-sensor driver has pros and cons :

i2c-gsensor is really energy saving regarding the battery as there is no disk access and all is working "in-memory". But it is not quite accurate for the moment...

The lis3lv02d_i2c patch need a complete recompilation of the kernel but you it is a good solution if you want to use the latest version of the kernel and/or lis3lv02d/lis3lv02d_i2c modules with the most recent modifications.

With the scripts, you will better understand the pros and cons of each solution...

---

### Post by arobase40 on 2010-10-16
[U]**G-SENSOR / ACCELEROMETER for the Acer 1825PT(Z)**[B] : Part II
[/B]
[/U]The script below is to be use with the i2c-gsensor driver. It has no daemonize functions and is simply a skeleton. As already mentioned, this driver is not quite accurate. You may have to modify the sleep value...
Read carefully the script if you wan to use some functions and remove some others...
Both the script and the driver have to be in the same directory.
```

#!/bin/bash

# Uncomment theses two lines below if theses 2 modules are not loaded through your /etc/modules
# /sbin/modprobe i2c_i801
# /sbin/modprobe i2c_dev

i2cbus=0
i2cbus_ok=0
new_orientation=""
old_orientation=""
dir=0

[ "$id" ] || id="`xinput list | grep 'Cando      11.6' | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`"
[ "$id" ] || id="`xinput list | grep 'touchscreen' | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`"
[ "$id" ] || exit 0

oskb_bin=/usr/bin/onboard 
[ "$oskb_bin" ] || oskb_bin="`type -p cellwriter`"
[ "$oskb_bin" ] || oskb_bin="`type -p onboard`"
[ "$oskb_bin" ] || oskb_bin="`type -p xvkbd`"
[ "$oskb_bin" ] || exit 0

killbyname () 
{
  local killpid="$( ps xuw | grep ^$USER | grep $1 | awk '{print "kill -TERM "$2";"}' )"
  if [ "$killpid" ]; then
    eval $killpid
  fi
}

# To be able to use systool utility, install sysfsutils with your packages manager
get_i2cbus()
{    
    i2cbus_ok=0

    while [ ${i2cbus_ok} -eq 0 ] && [ ${i2cbus} -le 16 ]
    do
# uncomment this line below if you want to use this fonctionnality
#         systool -b i2c -A name i2c-${i2cbus} | grep -q SMBus 
        if [ $? = 0 ]
        then
            i2cbus_ok=1
            echo "i2cbus = ${i2cbus}"
        else
            ((i2cbus=i2cbus+1))
        fi
    done
}

turn ()
{
caliby="180 10772"
calibx="65 18854"
#caliby="274 10772"
#calibx="273 18854"

xrandr -o $1

case $new_orientation in
    normal)
    xinput set-prop "$id" "Evdev Axis Inversion" 0, 0
        xinput set-prop "$id" "Evdev Axes Swap" 0
        xinput set-prop "$id" "Evdev Axis Calibration" $calibx $caliby
    ;;

    left)
    xinput set-prop "$id" "Evdev Axis Inversion" 1, 0
        xinput set-prop "$id" "Evdev Axes Swap" 1
        xinput set-prop "$id" "Evdev Axis Calibration" $caliby $calibx
#    "$oskb_bin" -x 0 -y 1100 -s 768x266 &
    ;;

    right)
    xinput set-prop "$id" "Evdev Axis Inversion" 0, 1
        xinput set-prop "$id" "Evdev Axes Swap" 1
        xinput set-prop "$id" "Evdev Axis Calibration" $caliby $calibx
#    "$oskb_bin" -x 0 -y 1100 -s 768x266 &
    ;;

    inverted)
    xinput set-prop "$id" "Evdev Axis Inversion" 1, 1
        xinput set-prop "$id" "Evdev Axes Swap" 0
        xinput set-prop "$id" "Evdev Axis Calibration" $calibx $caliby
#    "$oskb_bin" -x 0 -y 500 -s 1366x268 &
    ;;
    esac
}

# uncomment this line below if you can't find the correct i2cbus value
# get_i2cbus

old_orientation="$(xrandr --query --verbose | grep LVDS1 | awk '{print $5}')"

while :
 do

./i2c-gsensor ${i2cbus}
dir=$?

    case $dir in
      0) new_orientation="normal" ;;
      1) new_orientation="left" ;;
      2) new_orientation="right" ;;
      3) new_orientation="inverted" ;;
    esac

if [ "$new_orientation" != "$old_orientation" ]; then
    killbyname $oskb_bin
    turn
fi
    old_orientation=$new_orientation
#    old_orientation="$(xrandr --query --verbose | grep LVDS1 | awk '{print $5}')"

done


```Next part will be the script to be used with lis3lv02d/lis3lv02d_i2c driver...

---

### Post by xvilar on 2010-10-19
I've installed Ubuntu 10.10 Desktop in my Acer 1825PTZ... and:

- Is it normal that the touch screen don't follow my finger? I mean that cursor is centered and i can move it with my finger touching screen but the cursor don't goes where my finger goes, it goes to the direction I move my finger but with some inches 'in advance' ... in order to get the corner i just have to move two or three inches and the cursor gets at top of the corner ¿?

- When I boot ubuntu 10.10 i cannot use the left click touchpad button, it doesn't make anything... but right click works aswell. I've to 'sleep' the notebook, with FN + F4 and then when i wake up it, the left click button of the touchpad begins to work ¿?¿?

Thnx! Cheers!

---

### Post by ceh-photo.de on 2010-10-19
> **xvilar said:**
> I've installed Ubuntu 10.10 Desktop in my Acer 1825PTZ... and:

- Is it normal that the touch screen don't follow my finger? I mean that cursor is centered and i can move it with my finger touching screen but the cursor don't goes where my finger goes, it goes to the direction I move my finger but with some inches 'in advance' ... in order to get the corner i just have to move two or three inches and the cursor gets at top of the corner ¿?

- When I boot ubuntu 10.10 i cannot use the left click touchpad button, it doesn't make anything... but right click works aswell. I've to 'sleep' the notebook, with FN + F4 and then when i wake up it, the left click button of the touchpad begins to work ¿?¿?

Thnx! Cheers!

1. yes this is normal, because 10.10 detects the touchscreen as touchpad... you need to patch the driver or use a newer one.
I have tried to sum up the necessary steps for enabling the touchpad on Ubuntu 10.10 on my blog: [http://www.ceh-photo.de/blog/?p=175](http://www.ceh-photo.de/blog/?p=175)

2. After doing the above howto I still have the same problem, but to enable the left button you need to press the touchscreen one time after boot up. After touching the touchpad works well. If you are interested in the multitouch features of the touchpad check my sum up on my blog:[http://www.ceh-photo.de/blog/?p=196](http://www.ceh-photo.de/blog/?p=196)

At the moment I check the gyrosensor implementations from arobase40 and will post another sumup, if everything works well.

---

### Post by xvilar on 2010-10-19
> **ceh-photo.de said:**
> 1. yes this is normal, because 10.10 detects the touchscreen as touchpad... you need to patch the driver or use a newer one.
I have tried to sum up the necessary steps for enabling the touchpad on Ubuntu 10.10 on my blog: [http://www.ceh-photo.de/blog/?p=175](http://www.ceh-photo.de/blog/?p=175)

2. After doing the above howto I still have the same problem, but to enable the left button you need to press the touchscreen one time after boot up. After touching the touchpad works well. If you are interested in the multitouch features of the touchpad check my sum up on my blog:[http://www.ceh-photo.de/blog/?p=196](http://www.ceh-photo.de/blog/?p=196)

At the moment I check the gyrosensor implementations from arobase40 and will post another sumup, if everything works well.


Thanks a lot my friend! I'll try it! Some problems wiht autogen, i needed to apt-get install autoconf and apt-get install libtool :-) 

Now i got at autogen command:

```

configure.ac:25: warning: AC_INIT: not a literal: https://bugs.freedesktop.org/enter_bug.cgi?product=xorg
autoreconf2.50: running: /usr/bin/autoconf
configure.ac:25: warning: AC_INIT: not a literal: https://bugs.freedesktop.org/enter_bug.cgi?product=xorg
autoreconf2.50: running: /usr/bin/autoheader
configure.ac:25: warning: AC_INIT: not a literal: https://bugs.freedesktop.org/enter_bug.cgi?product=xorg
autoreconf2.50: running: automake --add-missing --copy --no-force
configure.ac:25: warning: AC_INIT: not a literal: https://bugs.freedesktop.org/enter_bug.cgi?product=xorg

...

configure: error: Package requirements (xorg-server xproto inputproto) were not met:
No package 'xorg-server' found
No package 'xproto' found
No package 'inputproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

And make tells me No makefile ... ¿? So please, help me, thnx!

---

### Post by ceh-photo.de on 2010-10-19
Ok it seems there is missing some install. I need to check this at home. I will post in the afternoon/evening (now for me its noon).

---

### Post by xvilar on 2010-10-19
> **ceh-photo.de said:**
> Ok it seems there is missing some install. I need to check this at home. I will post in the afternoon/evening (now for me its noon).

Ok my friend! No problem... cu later! thnx!

By the way, what i do i my Ubuntu 10.10 in my 1825ptz, boot and then:

- sudo su

- apt-get install build-essential xutils-dev

- sudo apt-get remove xserver-xorg-input-evtouch xserver-xorg-input-tslib

[COLOR=Red]*I think it told me that i haven't these packages, so nothing to remove...*[/COLOR]

- wget [http://cgit.freedesktop.org/xorg/driver/xf86-input-evdev/snapshot/xf86-input-evdev-2.5.0.tar.gz](http://cgit.freedesktop.org/xorg/driver/xf86-input-evdev/snapshot/xf86-input-evdev-2.5.0.tar.gz)

- tar xvfz xf86-input-evdev-2.5.0.tar.gz

- cd xf86-input-evdev-2.5.0/

- ./autogen.sh -prefix=/usr

[I][COLOR=Red] I got an error here, because it cannot be found autoreconf and then i'd to: "apt-get install autoconf" and then "apt-get install libtool" because i got some libtool errors too..

Before installing those packages, i got errors running autogen (ones i've posted before)[/COLOR][COLOR=Red]
[/COLOR][/I]  
- make

*[COLOR=Red] I cannot do the make because no makefile ....[/COLOR]*

- sudo make install


Thanks again! regards!

---

### Post by ceh-photo.de on 2010-10-19
Hey,
try: 
apt-get install xserver-xorg-dev

and redo  ./autogen.sh -prefix=/usr

and make



I tried the same procedure with this package removed and I have the same errors like you. Let me know if it works.

---

### Post by xvilar on 2010-10-19
> **ceh-photo.de said:**
> Hey,
try: 
apt-get install xserver-xorg-dev

and redo  ./autogen.sh -prefix=/usr

and make



I tried the same procedure with this package removed and I have the same errors like you. Let me know if it works.

Now I was able to do the make and make install... rebooted and... it doesn't runs, the touchscreen dont work... I think i'v done too many things... so i'll reinstall 10.10 again and i'll say to you something about! thanks again! cheers!

---

### Post by ceh-photo.de on 2010-10-19
Hey,
calm down! Linux is not Windows, you do not need to reinstall. Everything could be fixed. 

Do you have a /etc/X11/xorg.conf? than remove or move it and reboot/or restart the xserver

after that please post

/var/log/Xorg.0.log

and xinput --list

---

### Post by xvilar on 2010-10-19
No problem my friend, I've reinstalled because it was faster ... :-)

Reinstalled and following the steps you have explained, with the new step you told me , and now it works so well!!! thnx my friend!!!

_** So the final steps to follow:**_

```

0. sudo su

1. apt-get install build-essential xutils-dev

2. apt-get remove xserver-xorg-input-evtouch xserver-xorg-input-tslib *(it tells me that i've not xserver-xorg-input installed, so nothing to remove)*

3. apt-get install xserver-xorg-dev

4. apt-get install autoconf

5. apt-get install libtool

6. wget http://cgit.freedesktop.org/xorg/driver/xf86-input-evdev/snapshot/xf86-input-evdev-2.5.0.tar.gz

7. tar xvfz xf86-input-evdev-2.5.0.tar.gz

8. cd xf86-input-evdev-2.5.0/

9. ./autogen.sh -prefix=/usr

10. make

11. make install

12. reboot

```

And now the touchsreen runs as a touchscreen and not as a touchpad!!

Thanks ceh-photo.de!!!

---

### Post by ceh-photo.de on 2010-10-19
> **xvilar said:**
> No problem my friend, I've reinstalled because it was faster ... :-)

Reinstalled and following the steps you have explained, with the new step you told me , and now it works so well!!! thnx my friend!!!

_** So the final steps to follow:**_

```

0. sudo su

1. apt-get install build-essential xutils-dev

2. apt-get remove xserver-xorg-input-evtouch xserver-xorg-input-tslib *(it tells me that i've not xserver-xorg-input installed, so nothing to remove)*

3. apt-get install xserver-xorg-dev

4. apt-get install autoconf

5. apt-get install libtool

6. wget http://cgit.freedesktop.org/xorg/driver/xf86-input-evdev/snapshot/xf86-input-evdev-2.5.0.tar.gz

7. tar xvfz xf86-input-evdev-2.5.0.tar.gz

8. cd xf86-input-evdev-2.5.0/

9. ./autogen.sh -prefix=/usr

10. make

11. make install

12. reboot

```

And now the touchsreen runs as a touchscreen and not as a touchpad!!

Thanks ceh-photo.de!!!

No problem. I am happy that it works now for you. I updated my blog post too.

---

### Post by arobase40 on 2010-10-20
_**G-SENSOR / ACCELEROMETER for the Acer 1825PT(Z)**** : Part III and final.**_

Here is the last and final script that works with the lis3lv02d/lis3lv02d_i2c driver/module. This works as long as the module is loaded AND initialized, so wether you compiled the kernel with the previous patch or you initialized the module with the workaround (3° way)...

This script has been written by Imarune (from the french Ubuntu forum) and is quite sophisticated. It has not been published elsewhere yet as it needs some little modifications.
I publish it "as is" and I will explain what is the problem with this version, where and how to modify it so it meets your need.

```

#!/bin/bash
#
# set -x
DEBUG=""

[ $UID != 0 ] && { echo "$0 must be run as root" & exit 1; }

# redirect stdin, stdout and stderr
[ ! "${DEBUG}" ] && exec>/dev/null 2>&1 </dev/null
# daemonize and exit
[ ! "${DEBUG}" ] &&  [ -z "$PPID" ] && { PPID=$$ $0 & exit 0; }

shall_i_stay()
{
    # ... or shall i go
    # the first program's instance rotates screen
    # according to the accel chip values
    # the second one kills the first instance and exit
    # purpose : closing the program when not needed
    instances=`pgrep ${prog}`
    if [ "${instances}" != "$$" ]
    then
        # a previous instance is running; kill it
        # restore "normal" orientation then exit
        for instance in ${instances}
        do
            if [ "${instance}" != $$ ]
            then
                kill ${instance}
            fi
        done 
        xrandr -o normal
          xinput set-prop "$id" "Evdev Axis Inversion" 0, 0
            xinput set-prop "$id" "Evdev Axes Swap" 0
            xinput set-prop "$id" "Evdev Axis Calibration" $calibx $caliby
        exit 0
    fi
}

init_lis3lv02d()
{
    Product_name=`dmidecode | \
        awk ' ($1=="Product") && ($3~"Aspire")  { print $4} '`
    case ${Product_name} in
        1825PTZ|1425PTZ)
            [ "${DEBUG}" ] && \
                 echo "Notebook ${Product_name} : OK"
            ;;
        *)
            [ "${DEBUG}" ] && \
                echo "Unknown notebook ${Product_name} : exit"
            exit 1
            ;;
    esac
    smbus_loaded=`grep i2c_801 /proc/modules`
    [ -z "${smbus_loaded}" ] && modprobe i2c_801 >/dev/null 2>&1
    Module="0"
    Device="0"
    SMBus=""
    for device_name in `find /sys/devices -name name`
    do
        name=`cat ${device_name}`
        case $name in
            "ST LIS3LV02DL Accelerometer")
                # lis3lv02d module already loaded
                Module=1
                ;;
            "lis3lv02d")
                # device already enumerated
                Device=1
                ;;
            SMBus*)
                SMBus=`dirname ${device_name}`
                ;;
        esac    
    done
    [ "${DEBUG}" ] && \
        echo "Module: $Module  Device: $Device  SMBus: $SMBus"
    if [ "${Module}" = 0 ]
    then
        if [ "${Device}" = 1 ]
        then
            # should not happened
            modprobe lis3lv02d_i2c >/dev/null 2>&1
        else
            echo lis3lv02d 0x1d >${SMBus}/new_device
            sleep 2
            if [ ! -f /sys/devices/platform/lis3lv02d/position ]
            then
                # should not happened
                modprobe lis3lv02d_i2c >/dev/null 2>&1
            fi
        fi
    fi
    if [ -f /sys/devices/platform/lis3lv02d/position ]
    then
        [ "${DEBUG}" ] && \
            echo "Accelerometer successfully initialised !"
    else
        [ "${DEBUG}" ] && \
            echo "Accelerometer not found !"
        exit 1
    fi
}

rotate()
{
    xrandr -o $1
    case $1 in
    normal)
          xinput set-prop "$id" "Evdev Axis Inversion" 0, 0
            xinput set-prop "$id" "Evdev Axes Swap" 0
            xinput set-prop "$id" "Evdev Axis Calibration" $calibx $caliby
        ;;
    inverted)
          xinput set-prop "$id" "Evdev Axis Inversion" 1, 1
            xinput set-prop "$id" "Evdev Axes Swap" 0
            xinput set-prop "$id" "Evdev Axis Calibration" $calibx $caliby
        ;;
    left)
          xinput set-prop "$id" "Evdev Axis Inversion" 1, 0
            xinput set-prop "$id" "Evdev Axes Swap" 1
            xinput set-prop "$id" "Evdev Axis Calibration" $caliby $calibx
        ;;
    right)
          xinput set-prop "$id" "Evdev Axis Inversion" 0, 1
        xinput set-prop "$id" "Evdev Axes Swap" 1
            xinput set-prop "$id" "Evdev Axis Calibration" $caliby $calibx
    esac
}

get_orient()
{
    set - `sed -e 's/(//' -e 's/)//' -e 's/,/ /g' \
        /sys/devices/platform/lis3lv02d/position`
    x=$1
    y=$2
    z=$3

    if [ $x -lt -512 ]
    then
        # laptop mod = inverted tablet mode = normal
        new_orientation="normal"
    elif [ $x -gt 512 ]
    then
        # laptop mod = normal tablet mode = inverted
        new_orientation="inverted"
    elif [ $y -lt -512 ]
    then
        # laptop mod = right tablet mode = left
        new_orientation="left"    
    elif [ $y -gt 512 ]
    then
        # laptop mod = left tablet mode = right
        new_orientation="right"    
    fi
}

loop()
{
    while [ 1 ]
    do
        sleep 2
        get_orient
        if [ "${new_orientation}" != "${orientation}" ]
        then
            rotate ${new_orientation}
            orientation=${new_orientation}
        fi
#    echo "x: $x y: $y z: $z"
    done
}

# MAIN
#-----
trap - EXIT

PATH="$PATH:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"
prog=`basename $0`
caliby="0 10751"
calibx="0 18943"
[ "$id" ] || id="`xinput list | grep Cando \
    | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`"
[ "$id" ] || id="`xinput list | grep touchscreen \
    | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`"
[ "$id" ] || { echo " Touch screen not found..." & exit 1; }
orientation=`xrandr --query --verbose | awk ' ($1=="LVDS1") {print $5} '`
new_orientation="${orientation}"

shall_i_stay
init_lis3lv02d
loop
exit 0

```Now, some explanations : as is, you will have to flip the laptop 45° backward and wait about 2 sec to revert in normal mode after a rotation.
So to change the behaviors of the script, you can change the sleep value in the loop() function if you consider the script not responsive enough, and the way to interpret the x, y and z values in the get_orient() function.

What I did was to modify the default value as the value for "normal mode" if the other values can't be interpreted as a directional position other than "normal mode". ^^

Here is an example of the changes you can apply to this function so you can understand what I mean :

```


# Dummy function
do_nothing ()
{
echo >/dev/null
}

get_orient()
{
    set - `sed -e 's/(//' -e 's/)//' -e 's/,/ /g' \
        /sys/devices/platform/lis3lv02d/position`
    x=$1
    y=$2
    z=$3

# Trying to find the "flat" position of the laptop independent of the orientation
# if you find the correct values, the remaining of the test will work fine
    if [ $x -lt 256 ] && [ $y -lt 256 ] && [ $z -gt 512 ]
    then
        do_nothing
# The remaining tests should work if you operate with the laptop with a slight angle.
# Once the laptop rotates in a direction (normal, inverted, left or right), it should stay in that position 
# when you flip back in "flat" position and if you find the correct value in the first test.
    elif [ $x -gt 512 ] && [ $y -lt 256 ] && [ $z -gt 512 ]
    then
        # laptop mod = normal tablet mode = inverted
        new_orientation="inverted"
    elif [ $y -lt -512 ]
    then
        # laptop mod = right tablet mode = left
        new_orientation="left"    
    elif [ $y -gt 512 ]
    then
        # laptop mod = left tablet mode = right
        new_orientation="right"
    else    
        # laptop mod = inverted tablet mode = normal
        new_orientation="normal"
    fi
}


```I hope you will appreciate the hard work we did to make this accelerometer operational for the Acer 1825PT(Z) laptop.
Let me know if you like it and how you modify the different codes...
:)

---

### Post by 1825ptz on 2010-10-21
> **xvilar said:**
> 
_** So the final steps to follow:**_

```

...
6. wget http://cgit.freedesktop.org/xorg/driver/xf86-input-evdev/snapshot/xf86-input-evdev-2.5.0.tar.gz
...

```And now the touchsreen runs as a touchscreen and not as a touchpad!!


So evdev_drv.so from ubuntu gets replaced by a newer official one from freedesktop.
But if I look at the ubuntu sources for evdev (2.3.2-ubuntu3), they apply some patches
which are not in the freedesktop sources, e.g. a new files evdev-grail.[ch] etc.
I was a bit sceptical about this way and manually patched the ubuntu source as described earlier.

Now, calling "gesturetest 0 0 0xffffffff" as explained in the ubuntu multitouch wiki shows
me gestures like "Pinch - Two Fingers", "Drag Two Fingers", "Tap - Two Fingers", so
from the driver point of view, multitouch with two fingers seems to work. However these
events are not handled as such in the applications, e.g. two finger scroll does not work
in firefox etc.

But as two finger scrolling works for the synaptic touchpad (with the "xinput set-int-prop" settings described elsewhere), we cannot be far from using two finger
gestures. There are no xinput properties for the Cando touchscreen similar to the
synaptics settings (except perhaps 'Evdev Wheel Emulation').

So what is missing to get this to work for the touch screen? The utouch wiki talks a lot
about testing it, but I do not see what's required to use it in firefox or gtk2, just in the
same way it works for the touchpad. What am I missing?

---

### Post by ceh-photo.de on 2010-10-24
I don't know if this is needed by utouch, but if you install xserver-xorg-input-tslib xinput list shows two Cando Devices (sounds good, because its dual touch), but the problem is, the touchscreen does not work any more (don't know why).

You asked in term of the evdev driver from my small howto, you could patch the current ubuntu version too. I could not figure out any differences. (at the moment I have this solution working on my laptop). I choosed the described way for my howto, because it seems easier for less experienced users.

If somebody know, what is missing for multitouch...please post a comment.

---

### Post by tim290280 on 2010-10-24
> **xvilar said:**
> No problem my friend, I've reinstalled because it was faster ... :-)

Reinstalled and following the steps you have explained, with the new step you told me , and now it works so well!!! thnx my friend!!!

_** So the final steps to follow:**_

```

0. sudo su

1. apt-get install build-essential xutils-dev

2. apt-get remove xserver-xorg-input-evtouch xserver-xorg-input-tslib *(it tells me that i've not xserver-xorg-input installed, so nothing to remove)*

3. apt-get install xserver-xorg-dev

4. apt-get install autoconf

5. apt-get install libtool

6. wget http://cgit.freedesktop.org/xorg/driver/xf86-input-evdev/snapshot/xf86-input-evdev-2.5.0.tar.gz

7. tar xvfz xf86-input-evdev-2.5.0.tar.gz

8. cd xf86-input-evdev-2.5.0/

9. ./autogen.sh -prefix=/usr

10. make

11. make install

12. reboot

```And now the touchsreen runs as a touchscreen and not as a touchpad!!

Thanks ceh-photo.de!!!
I've also just picked up an acer 1820 and am having a few problems with getting the touchscreen running. I don't have any problems running the above list to configure things, but as soon as I reboot there is an error and the OS won't load. Looks like it does a basic scan prior to loading and gets stuck at "battery check".

Anyone else had this issue? Anyone know what is going wrong with the config?

Oh and thanks for all the info so far.

---

### Post by ceh-photo.de on 2010-10-25
> **tim290280 said:**
> I've also just picked up an acer 1820 and am having a few problems with getting the touchscreen running. I don't have any problems running the above list to configure things, but as soon as I reboot there is an error and the OS won't load. Looks like it does a basic scan prior to loading and gets stuck at "battery check".

Anyone else had this issue? Anyone know what is going wrong with the config?

Oh and thanks for all the info so far.

Which Ubuntu version do you have? 10.10 or 10.04?

---

### Post by tim290280 on 2010-10-25
> **ceh-photo.de said:**
> Which Ubuntu version do you have? 10.10 or 10.04?
 
I'm running 10.10 the netbook version.
 
Although I haven't tried the standard desktop version with touch.
 
I don't want to have to go back to Windows as I've only just moved over with the Meerkat release.

---

### Post by arobase40 on 2010-10-26
> **tim290280 said:**
> I'm running 10.10 the netbook version.
 
Although I haven't tried the standard desktop version with touch.
 
I don't want to have to go back to Windows as I've only just moved over with the Meerkat release.

Can you be more specific about your problems ?

Do you have access to the login screen, or does your system lock up at boot time : before or after grub ?

Can you indicate what type of touchscreen is with the 1820 : capacitive or resistive ? And the brand of this panel (Cando or MosArt) ???

Before you return to Windows, give more detailed informations about your problems, and you can also try to install Ubuntu 10.04 Lucid and see if that work...

---

### Post by tim290280 on 2010-10-26
> **arobase40 said:**
> Can you be more specific about your problems ?
Sorry I thought I had been clear.
 
> Do you have access to the login screen, or does your system lock up at boot time : before or after grub ?
Locks up at boot time. Essentially it stalls at grub load (I think, newb talking)
 
> Can you indicate what type of touchscreen is with the 1820 : capacitive or resistive ? And the brand of this panel (Cando or MosArt) ???
The touchscreen is capactive but I have no idea (nor could I easily find) the brand of the panel. I would assume it is the same as the 1825PT (which I also couldn't find details on).
 
> Before you return to Windows, give more detailed informations about your problems, and you can also try to install Ubuntu 10.04 Lucid and see if that work...
Don't worry, I'm not going to jump straight back to the dark side, I'm just going to have a double boot so I can use the touchscreen easily until we have the touch fully supported with the updates.
 
I'll have a go at 10.04. I should point out that everything else has worked very well under 10.10. Literally just want the touchscreen running as that was the main reason for the purchase. I also tried the desktop version of Meerkat and had the same problem.

---

### Post by Cobuntu on 2010-10-30
I got the touchscreen on the 1825 of my girlfiend working. About multitouch: as far as I understand you need to have GINN running to translate multitouch gestures into keyboard commands. This way I have several gestures working on my HP tx2, especially 2-Finger-scrolling is great. For achieving this I did exactly what post #1272 and the upgrade in #1274 on [http://ubuntuforums.org/showthread.php?t=1252492&page=128](http://ubuntuforums.org/showthread.php?t=1252492&page=128) suggested. 
I'm just a copy/paste guy, so to all the experts here: Would that work on the 1825 as well?  Edit: After installing on my tx2 it only worked when GINN is started manually via terminal but it can be put into autostart.

---

### Post by ceh-photo.de on 2010-10-30
I have continued arobase work to finish version one of enabling gyro-sensor without compiling kernel...

if you are interested check my blog post:
[http://www.ceh-photo.de/blog/?p=186](http://www.ceh-photo.de/blog/?p=186)

---

### Post by arobase40 on 2010-10-31
> **tim290280 said:**
> Sorry I thought I had been clear.
 

Locks up at boot time. Essentially it stalls at grub load (I think, newb talking)
 

The touchscreen is capactive but I have no idea (nor could I easily find) the brand of the panel. I would assume it is the same as the 1825PT (which I also couldn't find details on).
 

Don't worry, I'm not going to jump straight back to the dark side, I'm just going to have a double boot so I can use the touchscreen easily until we have the touch fully supported with the updates.
 
I'll have a go at 10.04. I should point out that everything else has worked very well under 10.10. Literally just want the touchscreen running as that was the main reason for the purchase. I also tried the desktop version of Meerkat and had the same problem.

After some research the 1820 is mostly based on the same hardware than the 1825 except for the processor and the memory. So I think that the problems you encountered may be due to a corrupted iso or the way you did the install (whatch out at the grub configuration depending on the way you did the install : standard install ou via Wubie)...

---

### Post by arobase40 on 2010-10-31
> **Cobuntu said:**
> I got the touchscreen on the 1825 of my girlfiend working. About multitouch: as far as I understand you need to have GINN running to translate multitouch gestures into keyboard commands. This way I have several gestures working on my HP tx2, especially 2-Finger-scrolling is great. For achieving this I did exactly what post #1272 and the upgrade in #1274 on [http://ubuntuforums.org/showthread.php?t=1252492&page=128](http://ubuntuforums.org/showthread.php?t=1252492&page=128) suggested. 
I'm just a copy/paste guy, so to all the experts here: Would that work on the 1825 as well?  Edit: After installing on my tx2 it only worked when GINN is started manually via terminal but it can be put into autostart.

For what I know the multi-touch feature works only for a few sets of touchscreen laptops as the developpers own HP tx2 laptops and none own a Acer 1825/1820 Laptop (or any Cando based touchscreen such as the Lenovo S10-3T). That's the reason this machine is not well supported at the moment... ^^
I'm not myself an expert and I already spent many weeks just to find informations about the Acer G-sensor and to develop the drivers and the scripts with Imarune. As already mentionned I have other projects to handle so it will take time before multi-touch works with the Acer 1825 unless a specific team work on this specific task...

---

### Post by arobase40 on 2010-10-31
> **ceh-photo.de said:**
> I have continued acrobase work to finish version one of enabling gyro-sensor without compiling kernel...

if you are interested check my blog post:
[http://www.ceh-photo.de/blog/?p=186](http://www.ceh-photo.de/blog/?p=186)

Just to mention my nickname is arobase and not acrobase... [IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]

And btw don't forget to quote Imarune (the other french guy from the french Ubuntu forum) as we work together on the gyro-sensor.

---

### Post by ceh-photo.de on 2010-11-01
> **arobase40 said:**
> Just to mention my nickname is arobase and not acrobase... [IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]

And btw don't forget to quote Imarune (the other french guy from the french Ubuntu forum) as we work together on the gyro-sensor.
Sorry! I edited it.

---

### Post by arobase40 on 2010-11-03
Some news about multitouch support for hid-multitouch: a first step towards multitouch unification !

It looks like active discussions and a experimental multitouch project for touchscreens supports for panels such as Cando, Quanta, MosArt, Cypress, GeneralTouch and Pixcir are on the way, with a new module called hid-multitouch.c for the linux community...

The patches are quite experimental...

[http://www.spinics.net/lists/linux-input/msg11837.html](http://www.spinics.net/lists/linux-input/msg11837.html)

[http://comments.gmane.org/gmane.linux.kernel.input/15926](http://comments.gmane.org/gmane.linux.kernel.input/15926)

The patchworks start here :

[https://patchwork.kernel.org/patch/251471/](https://patchwork.kernel.org/patch/251471/)

I Guess there is still a lot of works to do before these drivers will become operational. For what I have noticed none of these patchworks have been integrated in any existing kernel source code so we have to patch one by ourself in order to test them...

---

### Post by ceh-photo.de on 2010-11-10
> **arobase40 said:**
> Some news about multitouch support for hid-multitouch: a first step towards multitouch unification !

It looks like active discussions and a experimental multitouch project for touchscreens supports for panels such as Cando, Quanta, MosArt, Cypress, GeneralTouch and Pixcir are on the way, with a new module called hid-multitouch.c for the linux community...

The patches are quite experimental...

[http://www.spinics.net/lists/linux-input/msg11837.html](http://www.spinics.net/lists/linux-input/msg11837.html)

[http://comments.gmane.org/gmane.linux.kernel.input/15926](http://comments.gmane.org/gmane.linux.kernel.input/15926)

The patchworks start here :

[https://patchwork.kernel.org/patch/251471/](https://patchwork.kernel.org/patch/251471/)

I Guess there is still a lot of works to do before these drivers will become operational. For what I have noticed none of these patchworks have been integrated in any existing kernel source code so we have to patch one by ourself in order to test them...

Has someone tested it? And another problem: Does for anybody the internal mic work? I tested several tipps around the net, but my mic does not work. The maximum I got is some noise if i touch directly on the mic.

---

### Post by arobase40 on 2010-11-11
> **ceh-photo.de said:**
> Has someone tested it? And another problem: Does for anybody the internal mic work? I tested several tipps around the net, but my mic does not work. The maximum I got is some noise if i touch directly on the mic.

I have too much work for the moment so someone else has to volunteer...  :P

About your problem with the internal mic, may be you should look at the sound & video properties or System and sound properties. Mine is working perfectly...

Here is a snapshot of my settings :

[]("http://img168.imageshack.us/img168/6729/microphone.png")[http://img576.imageshack.us/img576/9901/microphoneb.png](http://img576.imageshack.us/img576/9901/microphoneb.png)
[IMG]http://yfrog.com/4omicrophonep[/IMG]

---

### Post by ceh-photo.de on 2010-11-16
Hey arobase sorry for my late reply, I am very busy, but big thanks for your screeshot:

On this tab I have the same configuration... does not work. Could you please make a screenshot of the tab hardware/materiel.

Another question:
I wanted to use the button above the ESC (I don't know his real functionality), but I was not able to detect a signal from it with
acpi_listen or xev. Does somebody know how tu use this button?

---

### Post by arobase40 on 2010-11-17
> **ceh-photo.de said:**
> Hey arobase sorry for my late reply, I am very busy, but big thanks for your screeshot:

On this tab I have the same configuration... does not work. Could you please make a screenshot of the tab hardware/materiel.

Another question:
I wanted to use the button above the ESC (I don't know his real functionality), but I was not able to detect a signal from it with
acpi_listen or xev. Does somebody know how tu use this button?

The screenshot of my hardware/materiel won't help in anyway... ^^

If you can move the slider in the input Tab of the sound properties, then the mic should work. Move the input and ouput slider to the max just to be sure.

If it doesn't work, modify your /etc/modprobe.d/alsa-base.conf and pass options to the snd-hda-intel module. Something like options snd-hda-intel model=acer. And maybe you'll have to add linux-backports-modules.

I used the "snd-hda-intel model=acer" option at the very beginning and just forgot it when I re-installed Lucid, so just adding linux-backports-modules  maybe enought...

Here is the link to french Ubuntu doc and look at the Acer section. You may find the same in the english doc...

[http://doc.ubuntu-fr.org/audio_intel_hda](http://doc.ubuntu-fr.org/audio_intel_hda)

EDIT : [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

For the button above the ESC key, this is used to restaure Windows 7 from the hidden partition. So under Linux, you can use it for whatever you want just like the P-button. PM Tomfrancart to ask him as I forgot how to determine the keycode (or google for it).

---

### Post by ceh-photo.de on 2010-11-18
> **arobase40 said:**
> The screenshot of my hardware/materiel won't help in anyway... ^^

If you can move the slider in the input Tab of the sound properties, then the mic should work. Move the input and ouput slider to the max just to be sure.

If it doesn't work, modify your /etc/modprobe.d/alsa-base.conf and pass options to the snd-hda-intel module. Something like options snd-hda-intel model=acer. And maybe you'll have to add linux-backports-modules.

I used the "snd-hda-intel model=acer" option at the very beginning and just forgot it when I re-installed Lucid, so just adding linux-backports-modules  maybe enought...

Here is the link to french Ubuntu doc and look at the Acer section. You may find the same in the english doc...

[http://doc.ubuntu-fr.org/audio_intel_hda](http://doc.ubuntu-fr.org/audio_intel_hda)

EDIT : [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

For the button above the ESC keyboard, this is used to restaure Windows 7 from the hidden partition. So under Linux, you can use it for whatever you want just like the P-button. PM Tomfrancart to ask him as I forgot how to determine the keycode (or google for it).

Thanks for your links,tipps and reply.
The mic: It is still not working. 

Whats your output on:
 cat /proc/asound/card0/codec#* | grep Codec

is it?
Codec: Realtek ALC269
Codec: Intel Cantiga HDMI

At the moment I use options snd-hda-intel model=basic, which provides me most options for the audio input.(I could choose between mic1,mic2 and line in(mic1 is the external mic)) A external mic works fine with this configuration. with mode=acer the internal speakers does not work.

I installed linux-back-ports-alsa, but I do not really understand what it does..? How I understood this package is just for kernel updates?

In term of the button above the ESC: I know under linux I could do everythink with buttons (thats what I want), but with the methods which are mentioned in my posted link I was not able to determine the code of this button. All other buttons could be recognized with xev, but this not. Has somebody an advice?

---

### Post by arobase40 on 2010-11-20
About : cat /proc/asound/card0/codec#* | grep Codec

I have exactly the same result as you

Codec: Realtek ALC269
Codec: Intel Cantiga HDMI

So I don't how I can help you as everything is just working fine "out-of-the-box" every time I do a new install... ^^

Did you update since your first install ?

For the button above the ESC key, did you PM Tomfrancart as I told you ?

---

### Post by ceh-photo.de on 2010-11-20
> **arobase40 said:**
> About : cat /proc/asound/card0/codec#* | grep Codec

I have exactly the same result as you

Codec: Realtek ALC269
Codec: Intel Cantiga HDMI

So I don't how I can help you as everything is just working fine "out-of-the-box" every time I do a new install... ^^

Did you update since your first install ?

For the button above the ESC key, did you PM Tomfrancart as I told you ?

Hmm maybe a difference between 10.04 and 10.10. You are using 10.04, aren`t you? I use 10.10.

No I did not PM Tomfrancart, I forgot to do it. I will catch up on this now.

---

### Post by ceh-photo.de on 2010-11-21
> **ceh-photo.de said:**
> Hmm maybe a difference between 10.04 and 10.10. You are using 10.04, aren`t you? I use 10.10.

No I did not PM Tomfrancart, I forgot to do it. I will catch up on this now.

hmm no diffence is the problem, it seems to be a hardware problem. In windows the mic does not work either. :-(

---

### Post by arobase40 on 2010-11-21
> **ceh-photo.de said:**
> hmm no diffence is the problem, it seems to be a hardware problem. In windows the mic does not work either. :-(

Schade... ^^
That was so surprising you had so much problem with your mic under Ubuntu...

I hope you will fix it.

Good luck.

---

### Post by 2beers on 2010-11-25
> **tim290280 said:**
> I've also just picked up an acer 1820 

Following a linux magazine the 1820 simply has a different Monitor from a different vendor. So i'm quite positive that any help given for the 1825pt monitor wont work on the 1820 series.
At least not out of the box

---

### Post by arobase40 on 2010-11-26
> **2beers said:**
> Following a linux magazine the 1820 simply has a different Monitor from a different vendor. So i'm quite positive that any help given for the 1825pt monitor wont work on the 1820 series.
At least not out of the box

Oh yeah, I just forgot about this model...

I watch at the Acer download center and found out this is a resistive touch panel. The problem is that they propose 2 kind of drivers : a EETI (eGalax) driver and a Mosart driver !!!
So the best way to be sure is that if someone has Windows 7 installed is to check in the devices properties to figure out the type of touch panel is in use.

Concerning the G-sensor, I'm almost quite sure it is the same as the 1825PT(Z).

If someone can confirm about these two things...

At least the EETI (eGalax) and Mosart touch panels are better documented that the Cando one... ^^

EDIT : about the EETI (eGalax) driver for linux it can be found on the EETI web site and is easy to install, at least for the touchscreen kit I had installed on my MSI U115 Netbook.

[http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)

The touch panel kit I bought was a monotouch one, so I don't know if a multitouch drivers exists or not. The best is to ask EETI. They are very responsive and very kind.

Rare enought to be quoted.

---

### Post by dcavagar on 2010-11-26
Hi ceh-photo.de, I had the same problem than you with the mic in my acer 1825 with maverick x86 version. Searching and trying a lot of workarounds to solve it I realize that the mic was working fine with the gnome sound recorder, but not with skype, ekiga or any other software like these. In this forum I found the solution from steve-o1983 user:

[http://ubuntuforums.org/showthread.php?t=1601922](http://ubuntuforums.org/showthread.php?t=1601922)

The only annoying thing now is that if you try to adjust the mic gain through the integrated sound mixer in maverick the problem come again, but you only have to launch the Pulseaudio volume control and repeat the workaround.

Hope this help you.

David.

---

### Post by javadude on 2010-11-28
I bought the 1825PT yesterday and thanks to this thread I got the touch stuff running.
My remaining problem: Turning the screen manually does not "turn" the touchscreen input coordinates. All upside down.
I also tried the auto gyro thingy, but resulting in
[FONT=Courier New]root@Aspire1825PTZ:/tmp/i2c-gsensor# i2c-gsensor 0 [loop]
Accelerometer not found[/FONT]

Any ideas ? Or did I missed the solution along the way here.
Thanks !
Sven

---

### Post by arobase40 on 2010-11-28
> **javadude said:**
> I bought the 1825PT yesterday and thanks to this thread I got the touch stuff running.
My remaining problem: Turning the screen manually does not "turn" the touchscreen input coordinates. All upside down.
I also tried the auto gyro thingy, but resulting in
[FONT=Courier New]root@Aspire1825PTZ:/tmp/i2c-gsensor# i2c-gsensor 0 [loop]
Accelerometer not found[/FONT]

Any ideas ? Or did I missed the solution along the way here.
Thanks !
Sven

First : which version of Ubuntu do you use and what is your kernel version (uname -r) ?

Second have you red all all the section concerning the G-sensor ?

If you use the i2c-gsensor way you have to preload 2 modules ("i2c-i801" and "i2c-dev") or by hand or in your /etc/modules files (best is the /etc/modules).
Then you have to determine the entry point of the i2c modules (whatch at the script).
Otherwise try the 3° way (no need to recompile the kernel) with the last script...

I don't understand your problem with manual screen rotation. Can you explain again and tell me which script did you use ?

---

### Post by javadude on 2010-11-28
Ubuntu 10.10
Linux Aspire1825PTZ 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:15:35 UTC 2010 i686 GNU/Linux

Manual: System|Preferences|Monitors> Rotation...

Think I need to carefully look at the modules again.

Thanks
Sven

---

### Post by javadude on 2010-11-28
Found it !

the parameter is **7** not 0 (at least in my case)

[B]root@Aspire1825PTZ:/usr/bin# i2c-gsensor 0
Accelerometer not found
root@Aspire1825PTZ:/usr/bin# i2c-gsensor 7
x = 4 y = 2 z = 58[/B]

Need to adjust the parameter also in the **gyro-auto-rotate.run** script.

[B]get_orientation()
{
    set `i2c-gsensor 7`[/B]
...

and exchange left and right (otherwise I have it upside down)

...
   then
        # laptop mod = right tablet mode = left
        new_orientation="**right**"
    elif [ $y -lt 60 ] && [ $y -gt 10 ]
    then
        # laptop mod = left tablet mode = right
        new_orientation="**left**"
    else
...


Thanks anyway for the infos!
Sven

---

### Post by arobase40 on 2010-11-29
Yep, all the test and developement ****were done with Lucid. That may be the reason for a different i2c entry point, and kernel 2.6.35 may also be the cause ?!?!?!

I don't like marverick and consider it too buggy for the moment...

Finally, for what I understand, you don't use one of a script published by me, right ? ;)

---

### Post by ceh-photo.de on 2010-11-29
> **arobase40 said:**
> Yep, all the test and developement ****were done with Lucid. That may be the reason for a different i2c entry point, and kernel 2.6.35 may also be the cause ?!?!?!

I don't like marverick and consider it too buggy for the moment...

Finally, for what I understand, you don't use one of a script published by me, right ? ;)

The reason is not maverick or the kernel, I have although maverick and 2.6.35 and my i2c bus is 0 like yours on lucid

I think he uses the edited script from me, I deleted some of your parts, because of problems, misunderstandings, like the bus detetection

@dcavagar: Thanks for your hint, I will try it these days. Had your mic worked under Windows?

---

### Post by arobase40 on 2010-11-29
> **ceh-photo.de said:**
> The reason is not maverick or the kernel, I have although maverick and 2.6.35 and my i2c bus is 0 like yours on lucid

I think he uses the edited script from me, I deleted some of your parts, because of problems, misunderstandings, like the bus detetection

@dcavagar: Thanks for your hint, I will try it these days. Had your mic worked under Windows?

No problem.

Codes and scripts can freely be modified. It's just that if some functions were commented, they were there for informations, in case they are needed...

I recognized your signature with the name of the script... :p

EDIT : Oh yey, if you modprobe or load the module via scripts can also change the i2c bus number. Forgot to mention this.

---

### Post by dcavagar on 2010-11-29
> **ceh-photo.de said:**
> The reason is not maverick or the kernel, I have although maverick and 2.6.35 and my i2c bus is 0 like yours on lucid

I think he uses the edited script from me, I deleted some of your parts, because of problems, misunderstandings, like the bus detetection

@dcavagar: Thanks for your hint, I will try it these days. Had your mic worked under Windows?

Yes, it works fine. In fact, I run the voice control wizard to test it and all seems to work fine.

---

### Post by ceh-photo.de on 2010-11-30
> **dcavagar said:**
> Yes, it works fine. In fact, I run the voice control wizard to test it and all seems to work fine.

Hmm it seems my mic is really broken. Does not work with your tipps either. In Windows its the same situation. I think I need to contact the customer support in my vacations.

---

### Post by arobase40 on 2010-12-01
> **ceh-photo.de said:**
> Hmm it seems my mic is really broken. Does not work with your tipps either. In Windows its the same situation. I think I need to contact the customer support in my vacations.

Are you sure you didn't mute the loud speaker with fn F8 or fn Down key, or something like that ??? ^^

---

### Post by ceh-photo.de on 2010-12-01
> **arobase40 said:**
> Are you sure you didn't mute the loud speaker with fn F8 or fn Down key, or something like that ??? ^^

year i am almost sure, because I got some clicks and noise from the mic if I tip with my fingers on it, but with high latency. But no clear sound.

---

### Post by Meezcore on 2010-12-01
I'm not sure if this is of topic, but I'm having problems with installing Ubuntu on my 1825PTZ.
First of all I'm new to Linux, but because the touchscreen functionality sucks in windows I want to switch to Ubuntu, with Unity as the desktop.
 
I made an USB stick with Ubuntu 10.10 Netbook Edition. I can boot it and try the desktop and it looks great. But as soon as I start the installation to the harddrive then it wil not continue any further then after selecting the continue button in the installer. After selecting quit installer I got an error that the installer crashed.
 
I tried fedora, SuSE to and both could'nt start the installation. In Fedora I got the message that it had something to do with the BIOS.
 
A few questions:
1. Has anybody have the same problem?
2. Where can i find extra information to continue my search on the web?
 
After I have installed Ubuntu I'm going to follow this whole thread about the 1825.
Just for fun and experience.
 
If someone can help me on the right path then I'm very greatfull.

---

### Post by arobase40 on 2010-12-01
> **ceh-photo.de said:**
> year i am almost sure, because I got some clicks and noise from the mic if I tip with my fingers on it, but with high latency. But no clear sound.

Do a last test before bringing your laptop to repair : try to play an audio file and see if that works... That may seem silly but just in case... ^^

---

### Post by arobase40 on 2010-12-01
> **Meezcore said:**
> I'm not sure if this is of topic, but I'm having problems with installing Ubuntu on my 1825PTZ.
First of all I'm new to Linux, but because the touchscreen functionality sucks in windows I want to switch to Ubuntu, with Unity as the desktop.
 
I made an USB stick with Ubuntu 10.10 Netbook Edition. I can boot it and try the desktop and it looks great. But as soon as I start the installation to the harddrive then it wil not continue any further then after selecting the continue button in the installer. After selecting quit installer I got an error that the installer crashed.
 
I tried fedora, SuSE to and both could'nt start the installation. In Fedora I got the message that it had something to do with the BIOS.
 
A few questions:
1. Has anybody have the same problem?
2. Where can i find extra information to continue my search on the web?
 
After I have installed Ubuntu I'm going to follow this whole thread about the 1825.
Just for fun and experience.
 
If someone can help me on the right path then I'm very greatfull.

If you are new to Linux, this is really not the good place...
There are many ways to install linux and you'd better try another page (Ubuntu Documentation) or another site...

Just a few tips :

Your problem might be that you have no free partition to install linux : (Windows 7 uses at least 3 primary partitions : A hidden restore partition, a small 100 Mo partition for the bootloader, and the systeme Windows partition). So if you have another data partition, there is no way to install something else !!!

That mean that you have to resize one the your partition (Windows system, if you have no data partition) or your data partition if you have one. The drawback is that one disk can't have more than 4 primary partitions so you have to backup it up, delete one or convert it to logical... Well not really a good job for a newbie.

Then all depend if you want to keep Windows on your disk or not...

In any  way and a good advice is that you SHOULD backup your entire disk on an external disk, before you try anything !!! Use Acronis True Image, Ghost, or RedoBackup (free sofware). With RedoBackup, you can either backup a whole disk, one or more partitions, and resize the disk or the partitions.

The quick and "easy" way is to use Wubi (located in any iso file of any Ubuntu distribution) as it installs Ubuntu in the same way as any application and can be uninstall the same way if you don't like it. Better is to install Ubuntu in your data partition if you have one.

If you use Wubi, after the first install finishes, it will ask you if you want to install localized file if you use another language than english. At the end it will ask you to install some update files. Do so (it will take some minutes depending of your network : ethernet, DSL or WiFi).
Here is a critical point you should NOT miss or your bootloader (Grub) will be messed up !!!
A pop-up windows will appear for the configuration of grub-pc : check or tick the line "Continue without installing GRUB" !!!!!!!!!!!!!!!

You must not allow the system to install or modify GRUB !

This is only for a Wubi based install. If you install Ubuntu the standard way, leave the line uncheck.

After you decided for a strategy on the way to install Ubuntu or any Linux distribution and you finish to install it, come back here... :D

Best regard and welcome to the Ubuntu world,

@

---

### Post by ceh-photo.de on 2010-12-02
> **arobase40 said:**
> Do a last test before bringing your laptop to repair : try to play an audio file and see if that works... That may seem silly but just in case... ^^

Hmm I do not unterstand. Could you please explain it further? 
The speaker (playing sounds) works well, a external mic too. My only problem is, that the internal mic gives me only clicks and noise and nothing else(on Windows and Linux)...

Or is it possible, that I damage the mic with linux settings? So it is not working unter linux anymore?

---

### Post by Meezcore on 2010-12-02
I will check other topics for this problem. I posted it here, because I wasn't sure if this wasn't a 1825ptz based problem.
I have found out trough the forum that it has something to do with SD cards and memory sticks.
I will try an external Harddrive tonight and hope this works.
Else I will try wubi.

---

### Post by Meezcore on 2010-12-03
> **Meezcore said:**
> I will check other topics for this problem. I posted it here, because I wasn't sure if this wasn't a 1825ptz based problem.
I have found out trough the forum that it has something to do with SD cards and memory sticks.
I will try an external Harddrive tonight and hope this works.
Else I will try wubi.
 
For informational purposes:
I could'nt install by using a USB Memory Stick.
But the installation worked for me with an USB External DVD-Player.
And I got messages that there are some USB Memory Sticks can work, but I dont know wich.

---

### Post by howtieatie on 2010-12-03
well thanks for that lovely information

---

### Post by ceh-photo.de on 2010-12-20
Hey,
some of you followed our development for the gyro autorotation and maybe read the linked blog post about the guy who uses the gyro sensor as a joystick with the HTC Shift. I have migrated this old kernel module(his module does not work on current ubuntu versions) to the current i2c architecture in the kernel and do some more modifications. If you want to try it check my blog post:

[http://www.ceh-photo.de/blog/?p=252](http://www.ceh-photo.de/blog/?p=252)

---

### Post by arobase40 on 2010-12-21
HI ceh-photo.de !

Very good news ! In fact I got that g-sensor old module working as a joystick but I did not know if it would be of interess to anyone, as the priority was to get it working as an auto-rotate function. That's the reason I did not publish it... ^^

Anyway, it's nice you found out how to modify and compile this module. And it's a good idea to use the "restore button" (button above the ESC key), as a way to enable or disable auto-rotation... :D

---

### Post by mgies on 2011-01-25
Is anyone he involved in bugsquashing over at launchpad? I have already found two bugreports about the cando touchscreen built into the 1825, but they have not even been classified or assigned for months.
I have two PackardBell Butterfly Touch here, which are identical to the Acer 1825, but I am not quite useful with code and stuff. So the only thing I could do, was to mark them as "also affects me"
Does anyone have more "ability" than me, and could speed-up the process of including these fixes here a bit? Or even just do it? Or is the actual bugsquashing done by the canonical employees?

I have already contacted Peter, the creator of the acerhdf module, and asked him to update the BIOS list.

It would be great to have at least touchscreen and fancontrol working out of the box for 11.04. autorotation by g-sensor would be a brilliant addition, of course.

---

### Post by ceh-photo.de on 2011-01-26
> **mgies said:**
> Is anyone he involved in bugsquashing over at launchpad? I have already found two bugreports about the cando touchscreen built into the 1825, but they have not even been classified or assigned for months.
I have two PackardBell Butterfly Touch here, which are identical to the Acer 1825, but I am not quite useful with code and stuff. So the only thing I could do, was to mark them as "also affects me"
Does anyone have more "ability" than me, and could speed-up the process of including these fixes here a bit? Or even just do it? Or is the actual bugsquashing done by the canonical employees?

I have already contacted Peter, the creator of the acerhdf module, and asked him to update the BIOS list.

It would be great to have at least touchscreen and fancontrol working out of the box for 11.04. autorotation by g-sensor would be a brilliant addition, of course.

HHey mgies,
in term of the touchscreen it should be very easy to add these bugfix. In term of the autorotation it depends on your preferred solution of the three presented possibilities. My used solution does not need much from the kernel/distro.
What I am interested in is your problem with fancontrol? I do not have such problems, the fan only speeds up with high load, maybe you have the same problems like me with ubuntu one and its very high workload. Please check the cpu load of your ubuntu one client.
But in general I think we have made a good/easy describtion of what is need to do to got the mentioned stuff working.

Question from me: Has anybody tried the  multi-touch "solution" yet?

---

### Post by arobase40 on 2011-01-27
Hi all,

I never had any problem at all with fan control since I got this machine, even since I first installed Ubuntu... But I never use Ubuntu One if it does affect in any way the Acer Fan control... ???

For the "new" multitouch driver, a friend of mine tried it with no result, but it was some weeks ago... I wrote to  Benjamin Tissoires, the guy who wrote the driver trying to get some explanations, but he never answer since now. Guess he is too busy...

I just had a look some minutes ago at this new driver and found out there was some great modifications. So I'll try to see if it works or not.

Amazing, when i came back here it was to announce you that I was about to leave this forum for a while and that I'm working on the Android version for the 1825PT(Z) !!!

Since yesterday, the Gingerbread-x86 source code was not available and I was working on Froyo-x86 as it contains all the available drivers for our machine. But the Intel 4 series graphic card seems more complicated to handle than the Radeon 4330 HD contained in my new MSI X600 laptop :P (as my old Asus M51Vr is broken  :() ! 

The display is working fine with my MSI X600 while I just have a black display with the 1825PTZ ! Looks like many other guys have the same problem than me with Android with the 1825PTZ.. ^^

But I found out that the Gingerbread-x86 source code was baked up to the git servers since yesterday and I'm downloading it right now...

Lucky guys, I'm still here for a while... :lolflag:

I'll tell you when I will create a new thread for the Android version and where it will be... :popcorn:

---

### Post by ceh-photo.de on 2011-01-27
> **arobase40 said:**
> Hi all,

I never had any problem at all with fan control since I got this machine, even since I first installed Ubuntu... But I never use Ubuntu One if it does affect in any way the Acer Fan control... ???

For the "new" multitouch driver, a friend of mine tried it with no result, but it was some weeks ago... I wrote to  Benjamin Tissoires, the guy who wrote the driver trying to get some explanations, but he never answer since now. Guess he is too busy...

I just had a look some minutes ago at this new driver and found out there was some great modifications. So I'll try to see if it works or not.

Amazing, when i came back here it was to announce you that I was about to leave this forum for a while and that I'm working on the Android version for the 1825PT(Z) !!!

Since yesterday, the Gingerbread-x86 source code was not available and I was working on Froyo-x86 as it contains all the available drivers for our machine. But the Intel 4 series graphic card seems more complicated to handle than the Radeon 4330 HD contained in my new MSI X600 laptop :P (as my old Asus M51Vr is broken  :() ! 

The display is working fine with my MSI X600 while I just have a black display with the 1825PTZ ! Looks like many other guys have the same problem than me with Android with the 1825PTZ.. ^^

But I found out that the Gingerbread-x86 source code was baked up to the git servers since yesterday and I'm downloading it right now...

Lucky guys, I'm still here for a while... :lolflag:

I'll tell you when I will create a new thread for the Android version and where it will be... :popcorn:

In term of fan control: I mean that ubuntu one causes some exorbitant cpu load which results into a never stopping fan; The fan control on its own is working fine.

The android news sound very promising. I am as more as interested in, unfortunately I am very busy in the moment with my studies. But in around 3 weeks my term will end... :D Please tell more about that android stuff!

Nice Regards

---

### Post by arobase40 on 2011-01-27
In 3 weeks, I guess all the works will be done... :lolflag:

I'm just kidding !

I finally got the display working but only in Vesa mode for the moment, that mean no accelerated functions and no 3D...

So I'll try to test the multitouch feature tonight, but that means I'll have to do a complete compile of the kernel !!! ^^

---

### Post by ceh-photo.de on 2011-01-27
> **arobase40 said:**
> In 3 weeks, I guess all the works will be done... :lolflag:

I'm just kidding !

I finally got the display working but only in Vesa mode for the moment, that mean no accelerated functions and no 3D...

So I'll try to test the multitouch feature tonight, but that means I'll have to do a complete compile of the kernel !!! ^^

I wish you good luck! Please let us stay tuned of your progress!

Do you install android on hdd or do you use some usb media or something like this? Supports android all hardware components? like wlan, cpu suspend...

---

### Post by arobase40 on 2011-01-27
The android source code is on my ubuntu partition and this is where I compile le code and generate an iso or img file. Then this iso or img file can be written on an USB key or burned on a CD. Y ou can then run it as a live system or install it on a HDD just like a traditional Ubuntu distro.

Froyo use a standard 2.6.35 Linux kernel + some extra files for the Android part which is based on some specific config files and Java for the visual interface. ^^ Java will be the hardest part for me as I don't know anything about java.

Gingerbread is based on 2.6.36 or 2.6.37 (can't remember : I guess it is 2.6.37) kernel.

CY

---

### Post by ceh-photo.de on 2011-01-28
> **arobase40 said:**
> The android source code is on my ubuntu partition and this is where I compile le code and generate an iso or img file. Then this iso or img file can be written on an USB key or burned on a CD. Y ou can then run it as a live system or install it on a HDD just like a traditional Ubuntu distro.

Froyo use a standard 2.6.35 Linux kernel + some extra files for the Android part which is based on some specific config files and Java for the visual interface. ^^ Java will be the hardest part for me as I don't know anything about java.

Gingerbread is based on 2.6.36 or 2.6.37 (can't remember : I guess it is 2.6.37) kernel.

CY
OK that sounds cool and it seems to be the optimal fun (not work) os for our acer 1825. It would be a dream if multitouch and gyro rotation and all default hardware works in android. If everything would be run fine it should be the most powerful android device, because of the much better hardware in contrast to regular tablets.

In the matter of java I could be a help for you, because I have some/good experiences in programming with java. If you need some help please contact me, with the restriction that in the next three weeks I do not have much time.

---

### Post by arobase40 on 2011-01-28
> **ceh-photo.de said:**
> OK that sounds cool and it seems to be the optimal fun (not work) os for our acer 1825. It would be a dream if multitouch and gyro rotation and all default hardware works in android. If everything would be run fine it should be the most powerful android device, because of the much better hardware in contrast to regular tablets.

In the matter of java I could be a help for you, because I have some/good experiences in programming with java. If you need some help please contact me, with the restriction that in the next three weeks I do not have much time.


No problemo, in fact I think I would need more time to make the whole kernel functionning as I work on different projects at the same time.

I tried the whole night to compile a custom Ubuntu kernel in the Ubuntu way ! Just a nightmare !!!

But in fact, I think I found out a way to compile and install the multitouch driver without having to compile the whole kernel...

I'll let you know when it's done.

---

### Post by perpe on 2011-01-28
He Guys,
 
working on my first Ubuntu installation, got touch working, but not the gyro....argh

@arobase40
I have also installed Android x86. The generic Version runs well if you change the grub commandline with dpi=96 nomodeset. On booting add modprobe hid-cando. The bad thing is that wifi doesn't work. Modprobe iwlagn on boot brings also a wifi error.
If you use the prebuild Version for Asus Laptop, you don't need to set nomodset, graphic and wifi working, but no touch and bluetooth.

I have installed Asus and the generic Version, copied the generic files  other the Asus, very quick and dirty, cause i don't want to built the kernel. WiFi works, touch works(still in debug with nomodeset for graphic  and modprobe hid-cando), bluetooth works. For WiFi you have to disable ethernet first in the Android gui. 
It's ok, but my fan is running continuously, screen is too bright and the battery drains to fast.

---

### Post by arobase40 on 2011-01-28
Back again,

I just discovered that there are some news versions of Froyo-x86 that work partly with the 1825PTZ. You can use the [android-x86-2.2-asus_laptop.iso]("http://android-x86.googlecode.com/files/android-x86-2.2-asus_laptop.iso") or the [android-x86-2.2-generic.iso.]("http://android-x86.googlecode.com/files/android-x86-2.2-generic.iso")

You can then use a Liveusb-creator utility to copy the content of the iso on the USB key.

When booted select the second option "**Live CD - Run Android-x86 without installation (MDPI)**" to have a better resolution. The first one also works but with a lower resolution.

_**What work**_ :

Display
WiFi
Ethernet (kind of)
Bluetooth (should work, but hard to get paired)
Webcam (an SDCard must be inserted to function). Why ??? Don't know...
Mouse and Touchpad.
You can change the language of the display
Language for the keyboard is limited to english when in live mode.
First thing to do is to set the screen timeout to the max : 30 mn, else the wake up is quite impossible
MP3 files and Sound works but very low sound even when set to the max
SDcard : but very difficult to mount.

_**What do not work**_ :

Touchscreen (even with the [MTTest.apk    ]("http://code.google.com/p/android-x86/downloads/detail?name=MTTest.apk&can=2&q=") apk which is supposed to handle multitouch)
Gyro-sensor
Tested 4 video format but none could played. Should be missing some codec.

Untested or unsure functions :

USB key
HDMI
VGA port
Microphone

Want to test by youself ? Go here :

[http://code.google.com/p/android-x86/downloads/list](http://code.google.com/p/android-x86/downloads/list)

Binary version of Gingerbread is not yet available. Only source code !

---

### Post by arobase40 on 2011-01-28
> **perpe said:**
> He Guys,
 
working on my first Ubuntu installation, got touch working, but not the gyro....argh

@arobase40
I have also installed Android x86. The generic Version runs well if you change the grub commandline with dpi=96 nomodeset. On booting add modprobe hid-cando. The bad thing is that wifi doesn't work. Modprobe iwlagn on boot brings also a wifi error.
If you use the prebuild Version for Asus Laptop, you don't need to set nomodset, graphic and wifi working, but no touch and bluetooth.

I have installed Asus and the generic Version, copied the generic files  other the Asus, very quick and dirty, cause i don't want to built the kernel. WiFi works, touch works(still in debug with nomodeset for graphic  and modprobe hid-cando), bluetooth works. For WiFi you have to disable ethernet first in the Android gui. 
It's ok, but my fan is running continuously, screen is too bright and the battery drains to fast.

hehe you were quicker than me at typing. :P

I don't understand how you managed to mix up the Asus and the Generic version ???

Can you explain it again ?
You said also that the touchscreen is functionning ?

So that said, what version of Ubuntu do you use and with which kernel version ?
Which method have you tried for the gyro-sensor ?

---

### Post by perpe on 2011-01-28
> **arobase40 said:**
> hehe you were quicker than me at typing. :P

I don't understand how you managed to mix up the Asus and the Generic version ???

Can you explain it again ?
You said also that the touchscreen is functionning ?

So that said, what version of Ubuntu do you use and with which kernel version ?
Which method have you tried for the gyro-sensor ?


Yes, touch is working, also with the generic LiveCD, select the debug version and call modprobe hid-cando. Ok, here is my very dirty way: First I have i&#324;stalled the Asus Version on an externel HDD, then the generic Version, copied the android2-2 folder of the generic version over my Asus insallation, overwriting all same files. Changed  the grub command line to boot the generic version with debug=1 and nomodeset, still need to type modprobe hid-cando. Is this clear enough, sorry for my english.


For gyro I'm trying the Version from [http://www.ceh-photo.de/blog/?p=186](http://www.ceh-photo.de/blog/?p=186), still searching the right number for i2c-gsensor 0, nothing between 0 and 27 works. Don't know which kernel I have, downloaded Ubuntu today
The touchscreen, does it support multitouch with Ubuntu? Seems like I habe only one touch working:confused:

---

### Post by arobase40 on 2011-01-28
> **perpe said:**
> Yes, touch is working, also with the generic LiveCD, select the debug version and call modprobe hid-cando. Ok, here is my very dirty way: First I have i&#324;stalled the Asus Version on an externel HDD, then the generic Version, copied the android2-2 folder of the generic version over my Asus insallation, overwriting all same files. Changed  the grub command line to boot the generic version with debug=1 and nomodeset, still need to type modprobe hid-cando. Is this clear enough, sorry for my english.

Humm, I'll try your way !?!?!?!

Don't worry about your english, mine is not so good either. ^^

> **perpe said:**
> For gyro I'm trying the Version from [http://www.ceh-photo.de/blog/?p=186](http://www.ceh-photo.de/blog/?p=186), still searching the right number for i2c-gsensor 0, nothing between 0 and 27 works. Don't know which kernel I have, downloaded Ubuntu today
The touchscreen, does it support multitouch with Ubuntu? Seems like I habe only one touch working:confused:

You should at least know if you use Ubuntu Lucid 10.04 or Maverick 10.10 !

The number for the i2c-gsensor is between 0 to 7. So no need to try other numbers.

I guess you forgot to include two modules in your modules conf file... Is that right ??? :P

And don't forget to execute the driver with root permission !!!

If you have other problems I'll try to help.

Best regards

EDIT : I forgot to mention about multitouch : I'm working on it at the moment as I said to [B]ceh-photo.de.

[B]So you have to be patient...

[/B][/B]

---

### Post by perpe on 2011-01-28
It's Ubuntu 10.10 Maverick :P

Tried as root to get the gyro working, but I still think it's my fault somewhere, will try it tomorrow again. Hey, this is my frist ubuntu experience, manged to install it without grub beside windows 7, booting with easybcd, pqservice is also still alive, one touch works...enough for a day :P

No problem, i only asked because i don't used files for touch from this thread. Installed this ones [http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html)
wondered about one touch because it says multitouch, mybe your touch drivers are better.

Edit: Now, my gyro is working :-)  But it's always on in laptop and tablet mode. In Windows 7 the hinge acts like a key controled by the launchmanger,  anyway bring this to work in Ubuntu? 
Read a little bit about multitouch on ubunto. Found [ginn]("https://launchpad.net/ginn"), some videos can be found at [http://www.omgubuntu.co.uk/2010/08/ginn-forcing-non-multitouch-aware-applications-to-support-multitouch-in-ubuntu/](http://www.omgubuntu.co.uk/2010/08/ginn-forcing-non-multitouch-aware-applications-to-support-multitouch-in-ubuntu/)
Built and installed it, but don't know how to configure. Read a little bit on this board and end up in the thread [Lenovo Ideapad S10-3t]("http://ubuntuforums.org/showthread.php?t=1415915&page=35"), look at the 346 post. So i ran geistest and ginn an found out that my acer recognizes 2 touch not one! Now, i only have to create my own wishes.xml for ginn. Has anyone of you guys tried it on his acer 1825ptz?

---

### Post by arobase40 on 2011-01-30
Hi perpe,

Obviously you are not a newbie as you may suggest, unless for the Linux part... ^^

Concerning the hinge for the Gyro-sensor and the touch panel, this is the hardest part to handle. I found nowhere any information about this feature. Look likes this is due to a buggy ACPI with the ACER.

I really don't know how Windows 7 handle this, but this is undocumented !!!

I'm suching hard during many months but could not find anything. The french guy who helps me to write the driver and the script for gyro-sensor who know much better the ACPI aspect did'nt find anything for the moment either, and he is very busy at the moment.
We were also in contact with the devs of the lis3lv02d/lis3lv02d_i2c modules, but they have either no idea on how this is implemented.

If you find anything, please let us know...

Regarding : xml for ginn, I don't know much about xml myself...

---

### Post by perpe on 2011-01-30
Hi arobase40,

this is my frist Linux sytem! So I'm a newbie, but I have some programming experience. It's helpful to understand and setup my system right.

For the hinge, in Windows 7 I suggest, that it ist manged by the LaunchManger appliication, because in the config file MMKEYBD.CFG are the entries:
Key 27 = 1,E0,70,E0,F0,F800,Tablet Panel Button
Key 28 = 1,E0,39,E0,B9,F801,Tablet Mode 
Key 29 = 1,E0,01,E0,81,F802,Notebook Mode

Found an outdated Acer keyboard driver, acerhk, in the Software Center, this is from his readmie:
> [If you have one of the newer models with the dritek hardware, use kernel 2.6
and get (after enabling it) kernel messages of the form:

    atkbd.c: Unknown key pressed (translated set 2, code 0xf4 on 
    isa0060/serio0). 
    atkbd.c: Use 'setkeycodes e074 <keycode>' to make it known.

then you should do exactly what your told. In this case you could do

    setkeycodes e074 158

to map the button with scancode e074 (hex) to keycode 158 (decimal). To find
out the scancodes of the buttons either look into the kernel log or into the
file MMKEYBD.CFG of the windows launch manager package. There you should find
lines like this:

Key 1 = 1,E0,74,E0,F4,F500,P1
          ** **            **

The important information is marked in the example above. The numbers give the
scancode produced by the button which's name is given last.That means we have to setkeycodes for e039 - tablet mode and e001 notebook mode.It this works managing that the keycode start and stop your script should be the easy part.

I need to have some deeper look into ginn, if i get it working right and write my own xml config file, than i can say more about it.
Edit: tested ginn with the examples wishes.xml and inkscape, two finger zooming works and two finger scrolling with firefox!

---

### Post by arobase40 on 2011-01-30
> **perpe said:**
> Hi arobase40,

this is my frist Linux sytem! So I'm a newbie, but I have some programming experience. It's helpful to understand and setup my system right.

For the hinge, in Windows 7 I suggest, that it ist manged by the LaunchManger appliication, because in the config file MMKEYBD.CFG are the entries:
Key 27 = 1,E0,70,E0,F0,F800,Tablet Panel Button
Key 28 = 1,E0,39,E0,B9,F801,Tablet Mode 
Key 29 = 1,E0,01,E0,81,F802,Notebook Mode

Found an outdated Acer keyboard driver, acerhk, in the Software Center, this is from his readmie:
That means we have to setkeycodes for e039 - tablet mode and e001 notebook mode.It this works managing that the keycode start and stop your script should be the easy part.

I need to have some deeper look into ginn, if i get it working right and write my own xml config file, than i can say more about it.
Edit: tested ginn with the examples wishes.xml and inkscape, two finger zooming works and two finger scrolling with firefox!

If the above informations are correct, then well done...

Have to see how to use them.

Concerning ginn and your wishes.xml, two fingers zooming is nice, but why two fingers  for scrolling ??? ;)

I prefer to use only one finger for that feature !?!?!?! :lolflag:

I have to test my new compiled Froyo iso file for the 1825PTZ, and I'll see what to do about the informations you gave at first....

Can you at least publish your wishes.xml file and make a tuto on how to use it ?

Thx

---

### Post by arobase40 on 2011-02-01
We (another guy and I) have made a custom Android Iso file than works perfectly regarding the display, touchscreen (monotouch though), with working wifi, ethernet, BT, SD Card, a new sleep time-out option set to NEVER, and some other stuffs.

Looks very nice and promising.

I'll try to add g-sensor and "MAY-BE" multitouch...

We need a java developer ^^ to handle le AVI video format, and MKV (as only sound is working)... ):P

---

### Post by perpe on 2011-02-02
Hey arobase40,

This is a good news, maybe I like your Froyo version more than the generic one :wink:

I have also good news for you.
Got the hinge working!

Tried to find unknown keys, but only found the P and backup Button in  dmesg as unrecognized. Read a lot about finding unknown keys(must do  this, because I'm new :wink:) Nothing worked.configureted other things like my touchpad(now, works better than with windows) and so on.
Had again a look to get that damn hinge working, I'm pretty sure that in  windows it's managed with the keyboard driver. I rememberd that acer  has a Bios update, decided to give it a try. updated my bios to v  1.3127, looked again into dmesg and saw two new keys!!! They are the  hnge(e039 and e001)! Assigned the first one to run the   gyro-auto-rotate.run script and wrote a new script for the second key:
```
#!/bin/bash

pid=$( pgrep gyro-auto-rotat )
xrandr -o normal
kill -9 $pid
fi
```(hope it's right, my frist bash script)

Now, my hinge is working, rotation starts then i move to tablet mode,  stops and rotates my screen to normal then i go back to laptop mode. 

I didn't wrote the xml file for ginn, yet. Will do it this weekend. But ginn manages only two and more touches, no one touch. For one touch gestures we have to use easystroke.

EDIT: My script was very wrong. Hope this is better:
```

#!/bin/bash

pid=$( pgrep gyro-auto-rotat )
if [ $pid  ]; then
    caliby="0 10751"
    calibx="0 18943"
    xrandr -o normal
    [ "$id" ] || id="`xinput list | grep Cando \
            | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`"
    [ "$id" ] || id="`xinput list | grep touchscreen \
            | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`"
    [ "$id" ] || { echo " Touch screen not found..." & exit 1; }

         xinput set-prop "$id" "Evdev Axis Inversion" 0, 0
         xinput set-prop "$id" "Evdev Axes Swap" 0
         xinput set-prop "$id" "Evdev Axis Calibration" $calibx $caliby

    
    kill -9 $pid
fi

```
(mostly copy & paste from your script)

---

### Post by arobase40 on 2011-02-02
> **perpe said:**
> Hey arobase40,

This is a good news, maybe I like your Froyo version more than the generic one :wink: 

I'll see if I can upload it somewhere... The problem is that I have a very bad internet connection and very low...

I'll tell you when it will be available.

> **perpe said:**
> I have also good news for you.
Got the hinge working!

Tried to find unknown keys, but only found the P and backup Button in  dmesg as unrecognized. Read a lot about finding unknown keys(must do  this, because I'm new :wink:) Nothing worked.configureted other things like my touchpad(now, works better than with windows) and so on.
Had again a look to get that damn hinge working, I'm pretty sure that in  windows it's managed with the keyboard driver. I rememberd that acer  has a Bios update, decided to give it a try. updated my bios to v  1.3127, looked again into dmesg and saw two new keys!!! They are the  hnge(e039 and e001)! Assigned the first one to run the   gyro-auto-rotate.run script and wrote a new script for the second key:
```
#!/bin/bash

pid=$( pgrep gyro-auto-rotat )
xrandr -o normal
kill -9 $pid
fi
```(hope it's right, my frist bash script)

Now, my hinge is working, rotation starts then i move to tablet mode,  stops and rotates my screen to normal then i go back to laptop mode. 

I didn't wrote the xml file for ginn, yet. Will do it this weekend. But ginn manages only two and more touches, no one touch. For one touch gestures we have to use easystroke.

EDIT: My script was very wrong. Hope this is better:
```

#!/bin/bash

pid=$( pgrep gyro-auto-rotat )
if [ $pid  ]; then
    caliby="0 10751"
    calibx="0 18943"
    xrandr -o normal
    [ "$id" ] || id="`xinput list | grep Cando \
            | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`"
    [ "$id" ] || id="`xinput list | grep touchscreen \
            | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`"
    [ "$id" ] || { echo " Touch screen not found..." & exit 1; }

         xinput set-prop "$id" "Evdev Axis Inversion" 0, 0
         xinput set-prop "$id" "Evdev Axes Swap" 0
         xinput set-prop "$id" "Evdev Axis Calibration" $calibx $caliby

    
    kill -9 $pid
fi

```(mostly copy & paste from your script)

Nice news endeed ! Have you tested this function by downgrading the bios ? ^^

Just to see if it still works using the actual bios or if everybody has to upgrade to the new bios to get it functionning under Ubuntu ???

I just bought a book for Programming  Android. It may help me to implement the gyro-sensor under Android, and change the actual visual : creating the four virtual buttons, so we won't need to use the the keyboard unless really needed... ^^

I'll try your script when I have time as it takes me a long time to be accustomed with Maverick 10.10... ^^

Thanks for your help.

---

### Post by perpe on 2011-02-02
I have to thank you and the other guys here, you did the hard work...I'm learning from you :)
Android can wait for my, I have a new toy: Ubuntu!

Didn't try that script with a downgraded Bios ^^ Should work with the V1.3118(I had this before my update), but you can't assign it to the hinge, because the hinge keys are not availible in Ubuntu with it. Searched everywhere in my system before the update. In dmesg, with acpi_listen, with keytouch and so on. Only the new bios brings the hinge as keys to Ubuntu.

Before i forget, need also to add
{"Acer", "Aspire 1825PTZ", "V1.3127", 0x55, 0x58, {0x9e, 0x00} }
into acerhdf.c and reinstall it to get the fan quiet again,

---

### Post by arobase40 on 2011-02-02
> **perpe said:**
> I have to thank you and the other guys here, you did the hard work...I'm learning from you :)
Android can wait for my, I have a new toy: Ubuntu!

Didn't try that script with a downgraded Bios ^^ Should work with the V1.3118(I had this before my update), but you can't assign it to the hinge, because the hinge keys are not availible in Ubuntu with it. Searched everywhere in my system before the update. In dmesg, with acpi_listen, with keytouch and so on. Only the new bios brings the hinge as keys to Ubuntu.

Before i forget, need also to add
{"Acer", "Aspire 1825PTZ", "V1.3127", 0x55, 0x58, {0x9e, 0x00} }
into acerhdf.c and reinstall it to get the fan quiet again,

Yes I already know about acerhdf, but did not need it as I never had any problem with fan, as I never use Ubuntu One anyway... ;)

I'll get the new bios. It won't hurt me anyway ! :p

---

### Post by perpe on 2011-02-03
Was too late yesterday...what do you mean with:
> I just bought a book for Programming  Android. It may help me to  implement the gyro-sensor under Android, and change the actual visual :  creating the four virtual buttons, so we won't need to use the the  keyboard unless really needed... ^^You already have 3 virtual buttons:
> 
There are touch only devices that neither have a keyboard, a menu button  nor a home button . For these devices, we have added some touch actions  to simulate menu key, home key and back key. To enable this feature,  you need to touch the right end of the status bar. After enabled the  feature, you can touch the right end of the status bar again to disable  the feature. Below is the list of touch actions simulate the different  keys.


[LIST]
[*] Home: Touch the status bar.
[*] Menu: Touch the statusBar from left to right.
[*] Back: Touch the statusBar from right to left.
[/LIST]

from [http://www.android-x86.org/documents/touch-only-device-howto](http://www.android-x86.org/documents/touch-only-device-howto)

---

### Post by arobase40 on 2011-02-03
Yeah, I know but the way this status bar is handled is not very intuitive.

First, it is too small, then this a 2 steps pushing ! We have to tap it once and wait for the system to allow us to tap a second time to get to the home. Same for the right and left.

What I intended to do was to draw big icons on the right of the screen just as with the real tablet, so we could access directly to the HOME, Previous screen, Menu button and Search button. A long touch on the Home button would let us access to programs "in memory".

See what I mean ? ;)

---

### Post by arobase40 on 2011-02-04
Here is my custom iso file for the 1825PT(Z). Might also work with the 1425P.


[http://rapidshare.com/files/446220918/Acer-1825ptz_laptop.iso](http://rapidshare.com/files/446220918/Acer-1825ptz_laptop.iso)

Tell me please what does work and what don't...

Enjoy.

---

### Post by arobase40 on 2011-02-06
About 15 downloads since 2 days and still not feed backs ??? !!! :confused:

Is that mean that my Android version for the 1825PTZ is 'perfect" and needs no changes ??? ^^

So just some informations in case some of you had problems booting the ISO file.

If you have a message saying : "vesamenu .c32 : not a COM32R image, this is due to the Live USB/CD creator you use. I had this problem with Fedora LiveUSB Creator > 3.9.0 and some other programs (syslinux issue).

With Fedora 3.9.0 or Lili LiveUSB Creator : no such problem.

With Fedora 3.9.0, you may encounter a "cosmetical" issue with 
**[B]tons of ".ERROR: idle with IF=0" on boot.**[/B]

But after a while, it loads and is working fine !

Again a syslinux issue...

With Lili LiveUSB Creator, you should not have these virtual errors !!!

Just a little word about Bluetooth fonctionnality, it works but is a little hard to get paired with some devices : I got a BT keyboard with touchpad fonctionning, but not with an BT audio receiver. I guess this is still an issue in the actual code on Android-x86. I'll try to see if I can fix it with other codes from different sources.

EDIT : this ISO file is bigger than the "official" one from Android-x86  as it is more "generic" as I managed to get it working both on my  1825PTZ, a MSI-X600 Laptop (Radeon GPU), and a MSI U115...  :)

EDIT 2 : I'm working on this version so it should also work on the Acer 1820 series (not the same touchscreen).

---

### Post by perpe on 2011-02-06
Hi arobase40,

Wasn't at home this weekend, so I hadn't the time to test it enough, but have installed it and looks good. Bluetooth, Wifi, Cam, One Touch are workjing. Changing brightness from the Setting menu didn't work for me, but I can change the brigntness with my keyboard. Powermanagments seems to be better then with the generic, my fan is quiet and my book didn_t get hot.
Downloade and installed a Voice Recording App, Mic seems not working, no, i think it works but to quiet, so i can't here anything. The Youtube App, that is included in the generic image, is missing on my installation from your iso.

More tomorrow, i need to test it a little bit more.
Yours is definitely better for our 1825 then  the gereric image, thank you.

Edit:Created a bootable USB Stick with Unetbootin without errrors.

---

### Post by arobase40 on 2011-02-06
Thanks very much for your feed back ! :p

Yes I was very surprised about the fact the fan was so silent.

I did'nt test the microphone as I still use it as Live and could'nt install applications on it.

I did'nt even know there was the YouTube application on the generic ISO ^^

Don't know why it isn't installed on mine ???

Nice to know it works with Unetbootin.

Could you test the VGA port, and battery life, please...

---

### Post by perpe on 2011-02-07
VGA works if I connect my screen before booting and only output on the external monitor. The laptopscreen is black but touch works :p
HDMI output don't work. 
I need more freetime to test the battery life.

Have you tested Fennec( Firefox Mobile [http://www.mozilla.com/en/mobile]("http://www.mozilla.com/en/mobile/%29?") )? Found it today, i like it, could be a great touchscreen browser. Android feeling on Ubuntu. The only disadvantage is that it doesn't support flash (or is it my fault?) Couldn't get flash videos running.

---

### Post by arobase40 on 2011-02-07
> **perpe said:**
> VGA works if I connect my screen before booting and only output on the external monitor. The laptopscreen is black but touch works :p
HDMI output don't work. 
I need more freetime to test the battery life.

Have you tested Fennec( Firefox Mobile [http://www.mozilla.com/en/mobile]("http://www.mozilla.com/en/mobile/%29?") )? Found it today, i like it, could be a great touchscreen browser. Android feeling on Ubuntu. The only disadvantage is that it doesn't support flash (or is it my fault?) Couldn't get flash videos running.

VGA output was not working fine with me, very unstable (may be due to a downgrad with my new version). HDMI Output won't work at all as this feature is not implemented in the main Google repo and so in the Android-x86 as well. Kinda a problem about licencing problem. Only with propriaties Android systems.

I asked to Android-x86 to put at least the option in the parameters, in case I could find some source codes for it... ^^

I can wait for the battery life test. No problem.

Many things are not yet implemented and for what I know fennec mobile is still unstable (or am I wrong ?).
I'll try to install Android above Ubuntu so I could do better tests.

Finally, I'm very close to implement the G-sensor function !!!

More about this soon...

I'll send you a PM later to ask you something, as I'll be away for some hours.

---

### Post by andrekua on 2011-02-09
Hi arobase40,

I just tried your Froyo today and it works really well. Touch and WiFi works very well by default. 

I do experience problem with installing apps. Only very few works. Those that dont work force Android to restart (screen went black, back to Android boot screen and loading Android just fine, but apps werent installed). After it did this, AppStore would refuse to download anything else. Even apps that are downloaded using BROWSER wont install. Does this have anything to do with installing Android in a NTFS partition? I remembered the generic works fine but WiFi is broken.

BTW, do you notice that sometimes after using it for a certain period, it starts to lag a lot? Everything just slows down to a crawl. A force reboot solved it just fine.

Thanks you so much for sharing your hard work. I'm primarily booting into Android nowadays unless I need to use Windows based apps.

---

### Post by arobase40 on 2011-02-09
> **andrekua said:**
> Hi arobase40,

I just tried your Froyo today and it works really well. Touch and WiFi works very well by default. 

I do experience problem with installing apps. Only very few works. Those that dont work force Android to restart (screen went black, back to Android boot screen and loading Android just fine, but apps werent installed). After it did this, AppStore would refuse to download anything else. Even apps that are downloaded using BROWSER wont install. Does this have anything to do with installing Android in a NTFS partition? I remembered the generic works fine but WiFi is broken.

BTW, do you notice that sometimes after using it for a certain period, it starts to lag a lot? Everything just slows down to a crawl. A force reboot solved it just fine.

Thanks you so much for sharing your hard work. I'm primarily booting into Android nowadays unless I need to use Windows based apps.

Did you really install it on a NTFS partition ?
What does it show when you go to the Storage parameters ?
Do you see your global partition or a small space dedicated to Android ?

I don't remember if I activated the NTFS option or not in the version I shared and that you use... ^^

I have not tested the install option yet as I'm still developping to intégrate the missing hardwares.

Wait for perpe to answer to this question when he has  time to...

About the lag, I just noticed a locked up after 2 hours, may be a problem with PM or APM ???

For the moment, I'm working to integrate most of the functionnalities I can. The optimisation will come later...

Don't forget, this just an Alpha version...
And I'm almost alone on the project. Another guy is working on the multitouch option, but he is a newbie at programming.

---

### Post by andrekua on 2011-02-12
> **arobase40 said:**
> Did you really install it on a NTFS partition ?
What does it show when you go to the Storage parameters ?
Do you see your global partition or a small space dedicated to Android ?

I don't remember if I activated the NTFS option or not in the version I shared and that you use... ^^

I have not tested the install option yet as I'm still developping to intégrate the missing hardwares.

Wait for perpe to answer to this question when he has  time to...

About the lag, I just noticed a locked up after 2 hours, may be a problem with PM or APM ???

For the moment, I'm working to integrate most of the functionnalities I can. The optimisation will come later...

Don't forget, this just an Alpha version...
And I'm almost alone on the project. Another guy is working on the multitouch option, but he is a newbie at programming.

I'm a newbie when it comes to linux codes. What do you mean by storage parameters? According to the SD Card and Phone Storage settings in Android, both are reported correctly and even files that were downloaded from browser were saved without a problem in the fake SD.

I dont think mine last for 2hours before stalling. Its more like every restart after using for 30minutes of continuous web browsing.

I really wish that P button could be used as HOME instead of restarting the device. Therefore waiting for good news from you.

---

### Post by arobase40 on 2011-02-12
> **andrekua said:**
> I'm a newbie when it comes to linux codes. What do you mean by storage parameters? According to the SD Card and Phone Storage settings in Android, both are reported correctly and even files that were downloaded from browser were saved without a problem in the fake SD.

I dont think mine last for 2hours before stalling. Its more like every restart after using for 30minutes of continuous web browsing.

I really wish that P button could be used as HOME instead of restarting the device. Therefore waiting for good news from you.

Very sorry andrekua if I don't understand your problems... May be if you could report them another way ?

You can use the "windows" touch keyboard as HOME. Don't know if this would help in anyway.

For the rest, PM to Perpe, may be he can help you as he installed Android on disk and I think he installed some applications too...

---

### Post by drnessie on 2011-02-15
May I ask how you update your BIOS? It doesn't wipe your system does it? It's just that the autorotate in laptop mode is really startin to annoy me...

---

### Post by ceh-photo.de on 2011-02-15
> **drnessie said:**
> May I ask how you update your BIOS? It doesn't wipe your system does it? It's just that the autorotate in laptop mode is really startin to annoy me...
No I does not wipe your system. It does nothing with your harddisk. Check the instructions on acer-homepage. I think it is not a complex operation.

---

### Post by drnessie on 2011-02-15
Seems they only supply Windows .exe files - wine is throwing up errors about how I'm not running Windows.

How did others manage it?

Oh and I read in  this thread someone got pinch n' zoom working on the touchpad, could someone please gimme the code?

---

### Post by ceh-photo.de on 2011-02-15
I do the bios update from the windows installation, I have installed both win and linux, although I am only using linux. But If you have not installed windows, make a bootable dos usb stick an do the update from the stick

---

### Post by arobase40 on 2011-02-15
> **ceh-photo.de said:**
> I do the bios update from the windows installation, I have installed both win and linux, although I am only using linux. But If you have not installed windows, make a bootable dos usb stick an do the update from the stick

Not sure this works as this is a Windows application...

May be with Bart PE ???

---

### Post by arobase40 on 2011-02-15
> **drnessie said:**
> Seems they only supply Windows .exe files - wine is throwing up errors about how I'm not running Windows.

How did others manage it?

Oh and I read in  this thread someone got pinch n' zoom working on the touchpad, could someone please gimme the code?

Read back the message... ^^

---

### Post by arobase40 on 2011-02-15
> **andrekua said:**
> Hi arobase40,

I just tried your Froyo today and it works really well. Touch and WiFi works very well by default. 

I do experience problem with installing apps. Only very few works. Those that dont work force Android to restart (screen went black, back to Android boot screen and loading Android just fine, but apps werent installed). After it did this, AppStore would refuse to download anything else. Even apps that are downloaded using BROWSER wont install. Does this have anything to do with installing Android in a NTFS partition? I remembered the generic works fine but WiFi is broken.

BTW, do you notice that sometimes after using it for a certain period, it starts to lag a lot? Everything just slows down to a crawl. A force reboot solved it just fine.

Thanks you so much for sharing your hard work. I'm primarily booting into Android nowadays unless I need to use Windows based apps.

Here is a sample list of Applications working and not working. As said in the below link your alternative is to use SlideMe SAM :

[http://groups.google.com/group/android-x86/browse_thread/thread/9b303e513d55dc75](http://groups.google.com/group/android-x86/browse_thread/thread/9b303e513d55dc75)

Best regards

---

### Post by drnessie on 2011-02-16
Ok, I went back to the post, downloadsed gin etc, but when I tried to configure it it says:

"no package x11 found"

so i tried "sudo apt-get install x11" and "sudo apt-get install x11-lib" but no packages exist. How do I get past this stage?

I have no windows installed or available - forget about it I'll just use the button above ESC...

EDIT: The package was libx11-dev

---

### Post by perpe on 2011-02-16
> **drnessie said:**
> Ok, I went back to the post, downloadsed gin etc, but when I tried to configure it it says:
 
"no package x11 found"
 
so i tried "sudo apt-get install x11" and "sudo apt-get install x11-lib" but no packages exist. How do I get past this stage?
 
I have no windows installed or available - forget about it I'll just use the button above ESC...
 
EDIT: The package was libx11-dev
 
Hi,
 
ginn isn't for the touchpad, it is for multitouch gestures on the touchscreen. The missing librarys are all lib...-dev, like libx11-dev.
I have played around with ginn, it works, but you need to have the enac touchscreen drivers installed. I have tried it with the method here and CEH-Photo's blog ([http://www.ceh-photo.de/blog/?p=175](http://www.ceh-photo.de/blog/?p=175)), but couldn't get ginn with it working. Installing the enac drivers after doing that changes also didn't work for my. But I'm a linux newbie, mybe someone of you can solve that. Only a clean install + enac drivers brings my screen to recognize multitouch for me.
To test if your screen supports multitouch, download utouch from the Software center and run geistest. If geistest shows two touches your touchscreen works right, if not, than you have to install the touchscreen drivers first.

---

### Post by drnessie on 2011-02-16
Awesome.. got the multitouch working! Gonna add loads of new gestures in my wishes.xml!

ToDo:
     Rotate to Rotate screen
     Two fingers slid back to go back
     Two fingers slid forward to go forward
     Press two fingers for right-click
     Press n' hold two fingers to bring up some kind of menu

OK, so now we're officially -eq Win7, is there any way we could beat them by adding support for more fingers? I hear it's just software, aslong as the screen is capacitive...

---

### Post by perpe on 2011-02-16
No, you can't add support for more fingers, because the screen supports only two fingers.
You can try easystroke. It's only for one touch, but you can create advance gestures, not only right, left down, up. It's a very neat solution in combination with ginn.

---

### Post by drnessie on 2011-02-16
Dont worry im already using easystroke...

Why doesnt the screen support it? i thought all capacitivescreens could support infinite touches, as long as the driver / software allows...

---

### Post by arobase40 on 2011-02-16
No, it's a hardware limitation !

I guess Acer  chose a dual touch capacitive screen for its low price... ^^

---

### Post by drnessie on 2011-02-16
Darn... those three and four fingered gestures looked real nice...

I've seen people emulate multi-touch pads by getting a webcam and a pice of paper, that supports as many fingers as the algorithm allows. Might setup one of those for when the laptop is on my desk :popcorn:

---

### Post by ceh-photo.de on 2011-02-18
drnessie. I used this guide [http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html)

for enabling multitouch. I think everything works fine, could you explain, how I could use gestures? Which applications supports which gestures? What must be configured?

If someone is interested in, I have updated my scripts for using the auto enabling and disabling of gyro rotation like perpe found it out.
[http://www.ceh-photo.de/blog/?p=309](http://www.ceh-photo.de/blog/?p=309)

---

### Post by drnessie on 2011-02-18
> **ceh-photo.de said:**
> drnessie. I used this guide [http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html](http://lii-enac.fr/en/architecture/linux-input/multitouch-ubuntu-howto.html)

for enabling multitouch. I think everything works fine, could you explain, how I could use gestures? Which applications supports which gestures? What must be configured?

If someone is interested in, I have updated my scripts for using the auto enabling and disabling of gyro rotation like perpe found it out.
[http://www.ceh-photo.de/blog/?p=309](http://www.ceh-photo.de/blog/?p=309)

Do you mean the comment I posted on your blog?

If you mean my above post, there's a project called MTMini, made for people like us who want to dev or arent happy with thier built in multitouch

Search it on google, or on utube to get a tutorial.

To get normal gestures working, use ginn - there are many tutorials on a nice google search.

---

### Post by arobase40 on 2011-02-22
> **drnessie said:**
> Darn... those three and four fingered gestures looked real nice...

I've seen people emulate multi-touch pads by getting a webcam and a pice of paper, that supports as many fingers as the algorithm allows. Might setup one of those for when the laptop is on my desk :popcorn:

Yey, simply connect a Kinect on your machine and you'll have the same result. :lolflag:

---

### Post by drnessie on 2011-02-23
Hey, my acer gets quite hot... any suggestions? I dont use Ubuntu One - Dropboxall the way!

Ubuntu is able to spin down the harddisk 'cos it does it whenever I close the lid, so I dont think the acerhdf thing'll do anything.

I think my 5:30 battery life might be something to do with that to... Ubuntu is supposed to be efficient, yet it takes away 3 hours from my battery life!

---

### Post by aeolu on 2011-02-23
Hello there. :)

I got the single touch working after a few trial and errors.

Problem is, when Ubuntu opens, the Mouse and Touchpad click isn't working. I have to first click on the screen before I can use the LMC on the Mouse and touchpad.

Anybody else encountered this? Thanks.

-RAF

---

### Post by ceh-photo.de on 2011-02-23
> **aeolu said:**
> Hello there. :)

I got the single touch working after a few trial and errors.

Problem is, when Ubuntu opens, the Mouse and Touchpad click isn't working. I have to first click on the screen before I can use the LMC on the Mouse and touchpad.

Anybody else encountered this? Thanks.

-RAF
Yes this behavior is "normal". Because I seldom shut down(suspend) I don't care about it.

---

### Post by arobase40 on 2011-02-23
> **drnessie said:**
> Hey, my acer gets quite hot... any suggestions? I dont use Ubuntu One - Dropboxall the way!

Ubuntu is able to spin down the harddisk 'cos it does it whenever I close the lid, so I dont think the acerhdf thing'll do anything.

I think my 5:30 battery life might be something to do with that to... Ubuntu is supposed to be efficient, yet it takes away 3 hours from my battery life!

I don't know much about maverick 10.10 as I still don't use it, so I don't know the difference between the 2 versions in regard of power management.

Is acer-wmi module loaded in your machine ?

I don't know how much RAM you have, but if if have at least 4 GB RAM you can disable swap use, configuring swappiness to 0 or 1 in your rc.local file (could make a try with 3 GB RAM ?!?!?!). Not to be done with 2 GB or less...

That way swap file will only be use for hybernate function.

---

### Post by arobase40 on 2011-02-23
> **aeolu said:**
> Hello there. :)

I got the single touch working after a few trial and errors.

Problem is, when Ubuntu opens, the Mouse and Touchpad click isn't working. I have to first click on the screen before I can use the LMC on the Mouse and touchpad.

Anybody else encountered this? Thanks.

-RAF

That may depend on your kernel version...

Have you done an update ?

As above stated I don't use Maverick 10.10 because I encountered such problems and could not get accustomed with this new interface...

If you don't mind about multitouch, you can install Lucid 10.04 which is more stable and works better. The accelerometor will work fine and all the rest, but only single touch for the moment... You will need at least 2.6.35 kernel...

Otherwise, may be someone else can help you.

---

### Post by arobase40 on 2011-02-24
> **aeolu said:**
> Hello there. :)

I got the single touch working after a few trial and errors.

Problem is, when Ubuntu opens, the Mouse and Touchpad click isn't working. I have to first click on the screen before I can use the LMC on the Mouse and touchpad.

Anybody else encountered this? Thanks.

-RAF

I was just thinking about something "new"...

Can you watch at your /var/log/Xorg.0.log file ? And if you find your Cando panel as a Touchpad, then it's your real problem !!! ^^
:popcorn:

---

### Post by drnessie on 2011-02-24
> **arobase40 said:**
> I don't know much about maverick 10.10 as I still don't use it, so I don't know the difference between the 2 versions in regard of power management.

Is acer-wmi module loaded in your machine ?

I don't know how much RAM you have, but if if have at least 4 GB RAM you can disable swap use, configuring swappiness to 0 or 1 in your rc.local file (could make a try with 3 GB RAM ?!?!?!). Not to be done with 2 GB or less...

That way swap file will only be use for hybernate function.

3GB RAM.

No, the acer-wmi module isn't loaded, because as I say, Ubuntu is able to spin down the harddisk. I'll try both things you said.


Isn't acer-wmi installed with Ubuntu? The first search result says it is...

---

### Post by ceh-photo.de on 2011-02-24
> **arobase40 said:**
> That may depend on your kernel version...

Have you done an update ?

As above stated I don't use Maverick 10.10 because I encountered such problems and could not get accustomed with this new interface...

If you don't mind about multitouch, you can install Lucid 10.04 which is more stable and works better. The accelerometor will work fine and all the rest, but only single touch for the moment... You will need at least 2.6.35 kernel...

Otherwise, may be someone else can help you.

I am using 10.10 since it was released.  It works fine on my Acer 1825PT. Please check with a system monitor the cpu load of your system. Maybe some process is in a endless loop or something like this.

---

### Post by arobase40 on 2011-02-24
> **drnessie said:**
> 3GB RAM.

No, the acer-wmi module isn't loaded, because as I say, Ubuntu is able to spin down the harddisk. I'll try both things you said.


Isn't acer-wmi installed with Ubuntu? The first search result says it is...

Acer-wmi may be installed with Ubuntu but may not auto-load.

Acer-wmi has nothing to do with the HDD, as it supports everything in regard with wireless, BT, brightness, and such... So that means that has incidence with your battery life.

For the other aspect of power management, I can't remember all the optimizations I did, but even without all of them I never had problem with heat, battery, noise or such. My actual Ubuntu is on rebuilt for some reasons, and I have no time at the moment to retreave the informations.

In any way the much you can do with power management, the better it is, even if you have the feelin that the system is able to spin down the HDD...
Add acerhdf if you can, it doesn't hurt... ^^


What you can do is to backup your actual system, and do a reinstall with Lucid 10.04 and see if that makes a difference. May be yes, may be not...

---

### Post by arobase40 on 2011-02-24
> **ceh-photo.de said:**
> I am using 10.10 since it was released.  It works fine on my Acer 1825PT. Please check with a system monitor the cpu load of your system. Maybe some process is in a endless loop or something like this.

I guess you didn't quote the correct message Toffer... ^^ :P

**aeolu **has no problem with cpu load or endless loop. I think that his touch panel is recognized as a touchpad and not as a touchscreen ! :guitar:

---

### Post by drnessie on 2011-02-24
I have some additions to the AWESOMENESS that isceh-photos onboard script - with my addition, the window will be resized to incorporate for the space taken up by the onscreen keyboard.

If the code doesnt work, just change it to work with you.

```
#!/bin/bash
running=$(pgrep onboard | wc -l)
echo $running
if [ $running -gt 0 ] ;then
	if [ $running -eq 2 ] ;then
		echo "opening"
		wmctrl -r :ACTIVE: -b remove,maximized_vert
		wmctrl -r :ACTIVE: -e 3,0,0,1336,410
		onboard
	else
	     	echo "killing"
	     	wmctrl -r :ACTIVE: -b add,maximized_vert
	     	pkill onboard
	fi
else
     echo "opening"
     onboard
fi
```


you need to install wmctrl

```
sudo apt-get install wmctrl
```

tutorials are online!

---

### Post by drnessie on 2011-02-24
> **arobase40 said:**
> Acer-wmi may be installed with Ubuntu but may not auto-load.

Acer-wmi has nothing to do with the HDD, as it supports everything in regard with wireless, BT, brightness, and such... So that means that has incidence with your battery life.

For the other aspect of power management, I can't remember all the optimizations I did, but even without all of them I never had problem with heat, battery, noise or such. My actual Ubuntu is on rebuilt for some reasons, and I have no time at the moment to retreave the informations.

In any way the much you can do with power management, the better it is, even if you have the feelin that the system is able to spin down the HDD...
Add acerhdf if you can, it doesn't hurt... ^^


What you can do is to backup your actual system, and do a reinstall with Lucid 10.04 and see if that makes a difference. May be yes, may be not...

lucid doesnt support multitouch. meerkat does.

my brightness / other control works fine... however, i will install acerhdf, but if nothing happens I'll uninstall it as I like to keep my memory clean

5 hours isnt too bad, it just isnt  the 8 i expected.

Wait... turning off WiFi gives about an hour more battery life! Brightness on lowest, things getting better & better!

hmm... the only looped process i can think of is the autorotate code.

---

### Post by arobase40 on 2011-02-24
> **drnessie said:**
> lucid doesnt support multitouch. meerkat does.

my brightness / other control works fine... however, i will install acerhdf, but if nothing happens I'll uninstall it as I like to keep my memory clean

5 hours isnt too bad, it just isnt  the 8 i expected.

Wait... turning off WiFi gives about an hour more battery life! Brightness on lowest, things getting better & better!

hmm... the only looped process i can think of is the autorotate code.

I know Lucid is single touch only ! It's just that you mentioned your hard disk got pretty hot, so I just proposed a test to knw if this has something to do with Maverick or not, or if this a hardware issue of your own laptop...

For the autorotate code, what you can do is to write a script that disable the touch panel and kill the autorate process when you close the lid, and enable them both back when you open it... ^^

---

### Post by drnessie on 2011-02-24
> **arobase40 said:**
> I know Lucid is single touch only ! It's just that you mentioned your hard disk got pretty hot, so I just proposed a test to knw if this has something to do with Maverick or not, or if this a hardware issue of your own laptop...

For the autorotate code, what you can do is to write a script that disable the touch panel and kill the autorate process when you close the lid, and enable them both back when you open it... ^^

Thanks for the preposition, but I amn't confident with partitions... last time, I accidently wiped Win7! (I selected my secondary partition, I swear :( )

acerhdf is supposed to be installed with the latest kernels anyway. I'm thinking maybe I should get rid of bluetooth from startup, because the laptop doesnt actually have a radio...

---

### Post by perpe on 2011-02-24
> **drnessie said:**
> Thanks for the preposition, but I amn't confident with partitions... last time, I accidently wiped Win7! (I selected my secondary partition, I swear :( )
 
acerhdf is supposed to be installed with the latest kernels anyway. I'm thinking maybe I should get rid of bluetooth from startup, because the laptop doesnt actually have a radio...
 
If you have updated your bios to the latest version, then you have to edit acerhdf to work with your new bios. I recommend to download the source from the acerhdf homepage ([http://piie.net/index.php?section=acerhdf](http://piie.net/index.php?section=acerhdf)), make the changes and add it to your modules file.
You have to add this to the acerhdf.c file:
```
{"Acer", "Aspire 1825PTZ", "V1.3127", 0x55, 0x58, {0x9e, 0x00} },

```
Follow the installation introductions of acerhdf.

---

### Post by drnessie on 2011-02-24
I havent updated the BIOS.

---

### Post by ceh-photo.de on 2011-02-24
> **drnessie said:**
> I have some additions to the AWESOMENESS that isceh-photos onboard script - with my addition, the window will be resized to incorporate for the space taken up by the onscreen keyboard.

If the code doesnt work, just change it to work with you.

```
#!/bin/bash
running=$(pgrep onboard | wc -l)
echo $running
if [ $running -gt 0 ] ;then
	if [ $running -eq 2 ] ;then
		echo "opening"
		wmctrl -r :ACTIVE: -b remove,maximized_vert
		wmctrl -r :ACTIVE: -e 3,0,0,1336,410
		onboard
	else
	     	echo "killing"
	     	wmctrl -r :ACTIVE: -b add,maximized_vert
	     	pkill onboard
	fi
else
     echo "opening"
     onboard
fi
```


you need to install wmctrl

```
sudo apt-get install wmctrl
```

tutorials are online!
Hey drnessie, I think awesome is not the right adjective, its a quite simple script ;-) But it seems to be a nice addition from you, I will try it these days.

---

### Post by ceh-photo.de on 2011-02-24
> **perpe said:**
> If you have updated your bios to the latest version, then you have to edit acerhdf to work with your new bios. I recommend to download the source from the acerhdf homepage ([http://piie.net/index.php?section=acerhdf](http://piie.net/index.php?section=acerhdf)), make the changes and add it to your modules file.
You have to add this to the acerhdf.c file:
```
{"Acer", "Aspire 1825PTZ", "V1.3127", 0x55, 0x58, {0x9e, 0x00} },

```
Follow the installation introductions of acerhdf.
What could I get from the acerhdf module?

---

### Post by perpe on 2011-02-24
> **ceh-photo.de said:**
> What could I get from the acerhdf module?
 
With acerhdf you can make the temperatur sensors availble and cotrol the fan. I'm using it with gnome sensor applet. 
I know you're from Germany  so have a look on [http://wiki.ubuntuusers.de/ACer_aspire_one#acerhdf](http://wiki.ubuntuusers.de/ACer_aspire_one#acerhdf). Müsste alles nötige zu acerhdf da stehen. Bin ganz frisch in der Linuxwelt, überfordere mich nicht :D

---

### Post by drnessie on 2011-02-25
> **ceh-photo.de said:**
> Hey drnessie, I think awesome is not the right adjective, its a quite simple script ;-) But it seems to be a nice addition from you, I will try it these days.

Maybe _not_ awesome, but *incredibly* useful

---

### Post by ceh-photo.de on 2011-03-02
> **drnessie said:**
> I have some additions to the AWESOMENESS that isceh-photos onboard script - with my addition, the window will be resized to incorporate for the space taken up by the onscreen keyboard.

If the code doesnt work, just change it to work with you.

```
#!/bin/bash
running=$(pgrep onboard | wc -l)
echo $running
if [ $running -gt 0 ] ;then
	if [ $running -eq 2 ] ;then
		echo "opening"
		wmctrl -r :ACTIVE: -b remove,maximized_vert
		wmctrl -r :ACTIVE: -e 3,0,0,1336,410
		onboard
	else
	     	echo "killing"
	     	wmctrl -r :ACTIVE: -b add,maximized_vert
	     	pkill onboard
	fi
else
     echo "opening"
     onboard
fi
```


you need to install wmctrl

```
sudo apt-get install wmctrl
```

tutorials are online!

hey tom,
I tried your script and I can see you intention, but it does not work well. My active window is resized vertically to give space for the keyboard,but the keyboard is shown above the window and not in the freespace. If I kill the keyboard my window is maximized independed from former status. But the idea is nice and until now I does not know the wmctrl tool, if you check my blog I used wmiface for a similar problem which seems to have nearly the same features. I will try to build a better working script next days.

---

### Post by drnessie on 2011-03-02
> **ceh-photo.de said:**
> hey tom,
I tried your script and I can see you intention, but it does not work well. My active window is resized vertically to give space for the keyboard,but the keyboard is shown above the window and not in the freespace. If I kill the keyboard my window is maximized independed from former status. But the idea is nice and until now I does not know the wmctrl tool, if you check my blog I used wmiface for a similar problem which seems to have nearly the same features. I will try to build a better working script next days.
To make onboard be at the bottom of the screen, move it down and then kill it with the close(x) button, and do the same to resize.

Maybe I should have put that in the code...

---

### Post by ceh-photo.de on 2011-03-10
> **drnessie said:**
> To make onboard be at the bottom of the screen, move it down and then kill it with the close(x) button, and do the same to resize.

Maybe I should have put that in the code...

I write a new script which should cover your whole idea. Check:
[http://www.ceh-photo.de/blog/?p=336](http://www.ceh-photo.de/blog/?p=336)

---

### Post by drnessie on 2011-03-19
The new kernel upgrade has completely removed all multitouch! I can't even reinstall it from the git!

hid-multitouch not found!

(PS: I said yes, con tinue cos whats thw worst that could happen? I need to reinstall ubuntu? but it still don't work. Gonna backup and restart and tell you what happens

---

### Post by arobase40 on 2011-03-19
> **ceh-photo.de said:**
> I write a new script which should cover your whole idea. Check:
[http://www.ceh-photo.de/blog/?p=336](http://www.ceh-photo.de/blog/?p=336)

Hi, Toffer,

It's nice that you have the feeling to discover "new features" by yourself with Tom and drnessie, but ain't you reinventing the wheel ?

I followed your different adventures, trials about this function, but sounds like this was already documented by Irohr on october 2nd 2010, even if it was not binded to a specific key...

[http://ubuntuforums.org/showthread.php?t=1486671&page=2](http://ubuntuforums.org/showthread.php?t=1486671&page=2)

;) :D

---

### Post by arobase40 on 2011-03-19
> **drnessie said:**
> The new kernel upgrade has completely removed all multitouch! I can't even reinstall it from the git!

hid-multitouch not found!

(PS: I said yes, con tinue cos whats thw worst that could happen? I need to reinstall ubuntu? but it still don't work. Gonna backup and restart and tell you what happens

This is quite normal !!!

May be the Enac Organisation did not mention about this, but the multitouch procedure is actually binded to the default 2.6.35-x kernel supplied with Maverick 10.10.

To use a different kernel, you'll have to use a different procedure which is not yet supplied and this is more complicated...

No need to reinstall Ubuntu, but you have to remove the new kernel and reinstall the previous one !!! ^^

---

### Post by ceh-photo.de on 2011-03-19
> **arobase40 said:**
> Hi, Toffer,

It's nice that you have the feeling to discover "new features" by yourself with Tom and drnessie, but ain't you reinventing the wheel ?

I followed your different adventures, trials about this function, but sounds like this was already documented by Irohr on october 2nd 2010, even if it was not binded to a specific key...

[http://ubuntuforums.org/showthread.php?t=1486671&page=2](http://ubuntuforums.org/showthread.php?t=1486671&page=2)

;) :D

Year I know he did something like that, but I think it is not as cool as mine.:) Did you try my script?

---

### Post by drnessie on 2011-03-20
> **arobase40 said:**
> Hi, Toffer,

It's nice that you have the feeling to discover "new features" by yourself with Tom and drnessie, but ain't you reinventing the wheel ?

I followed your different adventures, trials about this function, but sounds like this was already documented by Irohr on october 2nd 2010, even if it was not binded to a specific key...

[http://ubuntuforums.org/showthread.php?t=1486671&page=2](http://ubuntuforums.org/showthread.php?t=1486671&page=2)

;) :D

If we mix Irohr's code with ours, we get a pretty perfect onboard combo! What Irohrs' code doesn't do is resize the current window, so it's not like *re*-inventing the wheel, it's helping invent it in the first place

And with the kernel upgrade scare, I took the liberty of removing all the old versions of the kernel along with the new one. However, isn't it a bit stupid that the kernel wouldn't be backwards compatible?

---

### Post by arobase40 on 2011-03-21
> **ceh-photo.de said:**
> Year I know he did something like that, but I think it is not as cool as mine.:) Did you try my script?

Nope, as I don't use my Acer 1825PTZ with Ubuntu anymore at the moment. At least, it has not been rebuilt with touch feature.
As you know, I'm working on the Android-x86 build and only use the 1825PTZ only to test the Android iso.

But when I used Irohr modified script, I just remember it was working fine either in portrait or landscape mode placing onboard in the right place and the right size...

So I can't figure out what's the difference with what he did ??? Just wondering if the changes are worth the effort ? ;)

BTW, still waiting after you, if you have time to do some java development ? :D

---

### Post by arobase40 on 2011-03-21
> **drnessie said:**
> If we mix Irohr's code with ours, we get a pretty perfect onboard combo! What Irohrs' code doesn't do is resize the current window, so it's not like *re*-inventing the wheel, it's helping invent it in the first place

And with the kernel upgrade scare, I took the liberty of removing all the old versions of the kernel along with the new one. However, isn't it a bit stupid that the kernel wouldn't be backwards compatible?

Hmm... May be... Don't really know as I did not test your changes and don't understand the meaning of them...

I don't either understand what you mean when you said " isn't it a bit stupid that the kernel wouldn't be backwards compatible?" ???

"backwards compatible?" with what ???

Are you talking about the multitouch procedure ?

You didn't not even mention which kernel you were talking about or last used. If I remind well you use Ubuntu Maverick 10.10, right ? And the multitouch procedure was written for plain Maverick 10.10, so why are you talking about backward compatibility ???

Or do you mean "forward compatibility" ??? ^^
And if that is, try to guess why !!! ^^ 
):P

---

### Post by ceh-photo.de on 2011-03-21
> **arobase40 said:**
> Nope, as I don't use my Acer 1825PTZ with Ubuntu anymore at the moment. At least, it has not been rebuilt with touch feature.
As you know, I'm working on the Android-x86 build and only use the 1825PTZ only to test the Android iso.

But when I used Irohr modified script, I just remember it was working fine either in portrait or landscape mode placing onboard in the right place and the right size...

So I can't figure out what's the difference with what he did ??? Just wondering if the changes are worth the effort ? ;)

BTW, still waiting after you, if you have time to do some java development ? :D

My script does not only place the keyboard, my script resizes and places the active app too and it also restores former configuration after using it again. Moreover it works with all display resolutions (because its not hardcoded) and therefore can be used by all people which want a onscreen keyboard. 

In terms of java help! Year I could help you, write me mail,pn...
Last time I asked you said, that you are busy and are waiting for some help of a androidx86 developer!

---

### Post by arobase40 on 2011-03-21
Hi all,


 This is my second Android-x86 beta for the Acer Aspire 1825PT(Z) and probably for the Acer 1425P*, 1420P*, and 1820P*….
 Result with Packard Bell is unsure.
 This is a quick hack as I lost my previous settings and I had to rebuild it from scratch. 
 The iso file is quite big (588 MB) so I compress it with Winrar, so don’t forget to uncompress it before uses.
 It contains deux Readme files : one for french users and the second for english speaking users.
 The goal of this Android-x86 second beta is mainly a proof of concept  as it supports MULTITOUCH feature, but as any Acer laptops users should  know is that due to hardware limitation, this means dual-touch only !
 Otherwise, the multitouch feature has mainly tested with the  “Gallery” photos application. I don’t know which other applications is  supported. “Pinch to zoom” works, but not rotation AFAK.
 As already mentioned in previous posts, the multitouch drivers have  been written by Stephane Chatty and Benjamin Tissoires from the Enac  Organisation, and they spent a long time helping me to implement this  feature in the present build. So I must thank them for all the helps  they provided me and for their patience !
 

Any report is welcome.
 

Best regards and have fun with it,
 

Arobase
 

Here is the link :
 [http://rapidshare.com/files/453623042/Aspire1825_laptop.rar](http://rapidshare.com/files/453623042/Aspire1825_laptop.rar)
 

PS 1 : Already working on the third beta which hopefully will be more “polished”…
PS 2 : If you know a better place to host this file, let me know.

---

### Post by arobase40 on 2011-03-21
> **ceh-photo.de said:**
> My script does not only place the keyboard, my script resizes and places the active app too and it also restores former configuration after using it again. Moreover it works with all display resolutions (because its not hardcoded) and therefore can be used by all people which want a onscreen keyboard. 

In terms of java help! Year I could help you, write me mail,pn...
Last time I asked you said, that you are busy and are waiting for some help of a androidx86 developer!

Explained in that way, sounds nice... :D

About java developpment, I'll write you later this evening or this night. It's about a small application called softkey which replace physical keyboard for the Home, Back, Menu and Search options and that has to be customized... ^^

---

### Post by fat_tony on 2011-03-21
Hi,

I just got myself an Acer 1825PTZ and decided to give Ubuntu 10.10 a go as the new interface looked quite touch screen friendly. I think i've applied most of the suggestions in this thread and I had a couple of questions.

1) In windows the rotation only seems to work if you have the screen fully in 'tablet' mode? Can I get the same behavior in linux? At the moment when its on my knees and not quite flat it turns upside down occasionally I've played with the script thresholds and more or less eliminated this but im still curious as to what windows is doing.

2) Multi-touch. I have installed the ENAC driver which is loaded at least. How do I now go on to create some gestures? Maybe thats in this thread someplace, its go rather long one to join in the end of.

3) Android. Im quite tempted to give Android-x86 a test run but at the moment im dual booting with Windows, a situation that probably needs to remain stable for work purposes. Is Android going to add itself quite happily to my existing boot setup or is it not yet the kind of thing that I should be doing if I want my computer to boot reliably.

---

### Post by arobase40 on 2011-03-21
> **fat_tony said:**
> Hi,

I just got myself an Acer 1825PTZ and decided to give Ubuntu 10.10 a go as the new interface looked quite touch screen friendly. I think i've applied most of the suggestions in this thread and I had a couple of questions.

1) In windows the rotation only seems to work if you have the screen fully in 'tablet' mode? Can I get the same behavior in linux? At the moment when its on my knees and not quite flat it turns upside down occasionally I've played with the script thresholds and more or less eliminated this but im still curious as to what windows is doing.

2) Multi-touch. I have installed the ENAC driver which is loaded at least. How do I now go on to create some gestures? Maybe thats in this thread someplace, its go rather long one to join in the end of.

3) Android. Im quite tempted to give Android-x86 a test run but at the moment im dual booting with Windows, a situation that probably needs to remain stable for work purposes. Is Android going to add itself quite happily to my existing boot setup or is it not yet the kind of thing that I should be doing if I want my computer to boot reliably.

Just about Android-x86 and as already mentioned do NOT add it to an existing system and don't even try to install it on HDD ! Just use it as a Live system or install it to an USB stick or SD Card so it won't harm your system. Installing it on an USB stick or SD Card, you'll need a small 1 GB stick for the Live system and another (bigger) one for the installed version, so you could save your settings, the android applications and your datas.

---

### Post by drnessie on 2011-03-21
> **fat_tony said:**
> Hi,

I just got myself an Acer 1825PTZ and decided to give Ubuntu 10.10 a go as the new interface looked quite touch screen friendly. I think i've applied most of the suggestions in this thread and I had a couple of questions.

1) In windows the rotation only seems to work if you have the screen fully in 'tablet' mode? Can I get the same behavior in linux? At the moment when its on my knees and not quite flat it turns upside down occasionally I've played with the script thresholds and more or less eliminated this but im still curious as to what windows is doing.

2) Multi-touch. I have installed the ENAC driver which is loaded at least. How do I now go on to create some gestures? Maybe thats in this thread someplace, its go rather long one to join in the end of.

3) Android. Im quite tempted to give Android-x86 a test run but at the moment im dual booting with Windows, a situation that probably needs to remain stable for work purposes. Is Android going to add itself quite happily to my existing boot setup or is it not yet the kind of thing that I should be doing if I want my computer to boot reliably.

1) You need to update your BIOS. After you have done that (contact Acer and ask for an upgrade, you will need to boot into windows to install it), you can bind a keypress to enable / disable the auto-rotate script. You must now go here: [http://www.ceh-photo.de/blog/?p=309](http://www.ceh-photo.de/blog/?p=309) and follow the instructions to enable auto killing of the rotate script.

If you cannot be bothered to update your BIOS, there is also a way of doing the same with the "Auto Recover" button situated above the keyboard.

2) Install ginn [http://www.ceh-photo.de/blog/?p=320](http://www.ceh-photo.de/blog/?p=320)

3) Live USB / SD Card, as described by arobase40.


Most working "hacks" are located at: 
[http://www.ceh-photo.de/blog/?tag=acer-1825](http://www.ceh-photo.de/blog/?tag=acer-1825)

---

### Post by arobase40 on 2011-03-28
Hi all,


 Third Beta for Froyo Android-x86 for the Acer 1825PT(Z) already available !!!
 All explanation in the README file ! All debug informations have been stripped out so the file is quite smaller.


 [http://rapidshare.com/files/454751186/Aspire1825MT.rar](http://rapidshare.com/files/454751186/Aspire1825MT.rar)


[:guitar:]("http://rapidshare.com/files/454751186/Aspire1825MT.rar")
[URL="http://rapidshare.com/files/454751186/Aspire1825MT.rar"]
[/URL]
 Best regards,
 Arobase

---

### Post by drnessie on 2011-03-28
I is downloading!
> **arobase40 said:**
> hi all,


 third beta for froyo android-x86 for the acer 1825pt(z) already available !!!
 All explanation in the readme file ! All debug informations have been stripped out so the file is quite smaller.


 [http://rapidshare.com/files/454751186/aspire1825mt.rar](http://rapidshare.com/files/454751186/aspire1825mt.rar)


[:guitar:]("http://rapidshare.com/files/454751186/aspire1825mt.rar")
[url="http://rapidshare.com/files/454751186/aspire1825mt.rar"]
[/url]
 best regards,
 arobase

---

### Post by Meezcore on 2011-03-29
Thanks for this one.
I will try this asap on my 1825ptz, I almost can't wait.
Nice work.

---

### Post by arobase40 on 2011-03-31
Just forgot to mention, If have used a previous beta, don't forget to format your "old" USB stick ou SD Card, before proceeding with the new beta !

---

### Post by tomfrancart on 2011-09-09
Regarding the rotate script: It seems that in ubuntu Natty the "evdev axes swap" option stopped working. You can now use the following commands instead:

```

if [ "$dir" == "normal" ]
then
        xinput set-prop "$id" "Evdev Axis Inversion" 0, 0
#        xinput set-prop "$id" "Evdev Axes Swap" 0
        xinput set-prop "$id" "Coordinate Transformation Matrix" 1 0 0 0 1 0 0 0 1
        xinput set-int-prop "$id" "Evdev Axis Calibration" 32 $calibx $caliby
fi

if [ "$dir" == "left" ]
then
        xinput set-prop "$id" "Evdev Axis Inversion" 1, 0
#       xinput set-prop "$id" "Evdev Axes Swap" 1
        xinput set-prop "$id" "Coordinate Transformation Matrix" 0 -1 1 1 0 0 0 0 1
        xinput set-int-prop "$id" "Evdev Axis Calibration" 32 $caliby $calibx
fi

if [ "$dir" == "right" ]
then
        xinput set-prop "$id" "Evdev Axis Inversion" 0, 1
#        xinput set-prop "$id" "Evdev Axes Swap" 1
        xinput set-prop "$id" "Coordinate Transformation Matrix" 0 1 0 -1 0 1 0 0 1
        xinput set-int-prop "$id" "Evdev Axis Calibration" 32 $caliby $calibx
fi

```See also:
[https://wiki.ubuntu.com/X/InputCoordinateTransformation](https://wiki.ubuntu.com/X/InputCoordinateTransformation)
[http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)

---

### Post by AmaniL on 2011-09-09
Help! I have a Acer Aspire 6530 and I am trying to install ubuntu 11.04 32bit. Download the ISO and burned it on my Desktop. That worked well, but when I tried installing it on my laptop it gives me this:

```
udevd[72]: worker [79] unexpectedly returned with status 0x0100

udevd[72]: worker [79] failed while handling ‘/devices/pci0000:00/0000:00:14.1/host0/target0:0:0

```

Then:

```
BusyBox V1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter ‘help’ for a list of built-in commands.

(initramfs) Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

undevd[72]: worker [77] unexpectedly returned with status 0x0100

undevd[72]: worker [77] failed while handling ‘/devices/virtual/block/loop0’

```

I thought it was a bad burn so I had burned another copy using my work PC no change so I had the IT dept at my school burn version 10.10 same problems. I thought it could be the HDD so I replaced that same old problem. I then thought it could be the DVD/CD drive so I created a bootable ubuntu flsh drive and this is what I get:

```
ISOLINUX 5.02 debian-20101016 ETCD Copyright © 1994-2010 H. Peter Anvin et al
```

And that’s it, nothing else!

Can someone help me?

---

### Post by fgossart on 2011-11-22
has someone experience ubuntu 11.10 and acer 1825 ?
I can't enable multitouch.

---

### Post by ceh-photo.de on 2011-12-08
Maybe some people are still interested in the progress of android-x86 on Acer1825. I have made a honeycomb build for this device.

Check here:
[http://www.ceh-photo.de/blog/?p=401](http://www.ceh-photo.de/blog/?p=401)

---

### Post by Cobuntu on 2011-12-25
I'd also be interested if someone has managed to get multitouch with 11.10? OR if there is at least a way to get Easystroke recognized?

---

### Post by Cobuntu on 2012-08-05
WIth 12.04 single touch works very well and Easystroke Gestures can be used with it now.

---

### Post by fridgecow on 2012-08-08
Hi everyone. Fridgecow (previously drnessie) here.

So, my acer is getting gradually and gradually worse. I'm sure you've all moved on to better hardware, but I'm stuck using my battered horse.

Recently, I've encountered a problem. **I dropped my laptop** some time ago and at first, everything continued to work, but with a **small crack in the casing** (around the border of the screen).

A few weeks ago, the **far right of the screen** (where the crack is) has **stopped responding to touches**. This was *managable*.

Now, however, the screen started to send **phantom touches** and also the very **top of the screen is unusable** (like the right).

I'm attaching a **picture**. You may not be able to help, but considering all the incredible android work you've done here you seem to know a lot about the hardware (Thanks, btw :D).

Also, I'm loving Win8 - We are officially hipsters, having touchscreen laptops before it was cool.

PS: Sorry for the bad quality image, I did my best :/

---


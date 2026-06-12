---
title: "Helpfull Hints for a tx1000 (tx1120)"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by diatribex on 2007-05-13
If you are like me, after you installed the latest Ubuntu, some things just didn't work (TM).  After much humming and hawing, here are some things you might find helpful...

As far as wireless, I was forced to the NDIS.  Instructions for that can be found right here

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

Don't worry about te fact that it says Dell...i didnt :)


Next comes audio.  Seems it had some trouble because of the Jack sensing on the front jacks...

Try adding this to /etc/modprobe.d/alsa-base

options snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0


Then comes the touchscreen...This took the most time, but seems to be working well now.  Try this.. [http://www.cartft.com/support/drivers/TFT/Linux_HowTo](http://www.cartft.com/support/drivers/TFT/Linux_HowTo)  

Yes, it is in German, but easy to follow...

There are a couple of additional things.  If you use the latest  pre-compiled version of the driver like I did, you might run into this *bug*.  When you get to the calibration step, you run a tool called calibrate.sh .  It references a file called empty_cursor.xbm. The path to that file is supposed to be ./ but in the compiled version it is / .  You try to fix it in the compiled version with bvi, or just copy empty_cursor.xbm to / for the calibration step. then just follow the steps as listed.

I did run the calibration step, but found that my pen worked better if I just used the new min and max values in my xorg.conf, and commented out the additional new values.  The most important thing was to make sure you comment out or otherwise null the Calibrate option from xorg.conf after you are done calibrating.  It seems that this is what was causing most of my grief..ie "krazy Kourser" 

There is still some work to do...like the fingerprint scanner, and making the display sense the orientation switch...perhaps my brothers and sisters here can help with that.

Good luck! 

Jordan Crombie...

---

### Post by mlf on 2007-05-14
[QUOTE=diatribex;2648256]If you are like me, after you installed the latest Ubuntu, somthings just didnt work (TM).  After much humming and hawing, here are some things you might find helpful...

Are you running the AMD64 version? I haven't got that to work, or the 32 bit version to work. The MEPIS 32 bit version works, including the wireless without any changes. No audio, though. I'll try your solution.

I'd like to get Ubuntu 64 bit installed on my tx1119, dual booting with Vista.

Good news that there is a solution for the audio. I'd like to get the web cam working as well, but that is not essential.

Michael

---

### Post by diatribex on 2007-05-14
32bit...  There is nothing the 64bit version offers me that 32bit wont handle.  Besides, there are to many hoops you have to jump around over and through to get some of the applications working (Flash I think...)

Good luck...

Jordan

---

### Post by farbird on 2007-05-15
to get nvidia drivers working proper
to get into the login screen [ gui ]
try this

click escape before it boots..

edit the line which have the "uuid=xxxxxx" text..

append to the same line with these codes " noapic vga=0x317"
it should get it up to the gfx login screen.


once u get in...
nano edit your /boot/grub/menu.lst file and make the line permanent..

---

### Post by farbird on 2007-05-15
to get your wifi broadcom working, try this

sudo apt-get install bcm43xx*

sudo gedit /etc/iftab

change the interface name of the wifi interface to "wlan0"
it may be eth0 or eth1 initially [ check to ensure which is the wifi one ]

sudo gedit /etc/network/interfaces
remove all lines which make references to the old "ethx" that has been replaced above to "wlan0"

now in console, do this

sudo rmmod bcm43xx
sudo modprobe bcm43xx

this should get it working...
if the rmmod doesnt work, just reboot the laptop....

if still cannot work... post reply here

---

### Post by farbird on 2007-05-16
> **diatribex said:**
> 

Next comes audio.  Seems it had some trouble because of the Jack sensing on the front jacks...

Try adding this to /etc/modprobe.d/alsa-base

options snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0
Jordan Crombie...

tried the audio hack above..

headphone jack still not working..


anyway to get the jacksense to work??

can't watch porn without alarming the whole office!

hahah

---

### Post by bofu on 2007-05-26
> **diatribex said:**
> 

Then comes the touchscreen...This took the most time, but seems to be working well now.  Try this.. [http://www.cartft.com/support/drivers/TFT/Linux_HowTo](http://www.cartft.com/support/drivers/TFT/Linux_HowTo)  

Yes, it is in German, but easy to follow...

There are a couple of additional things.  If you use the latest  pre-compiled version of the driver like I did, you might run into this *bug*.  When you get to the calibration step, you run a tool called calibrate.sh .  It references a file called empty_cursor.xbm. The path to that file is supposed to be ./ but in the compiled version it is / .  You try to fix it in the compiled version with bvi, or just copy empty_cursor.xbm to / for the calibration step. then just follow the steps as listed.

I did run the calibration step, but found that my pen worked better if I just used the new min and max values in my xorg.conf, and commented out the additional new values.  The most important thing was to make sure you comment out or otherwise null the Calibrate option from xorg.conf after you are done calibrating.  It seems that this is what was causing most of my grief..ie "krazy Kourser" 


could you post your min and max values? or even your entire xorg.conf?

im having a hard time getting the initial values from the calibrate.sh... 

everytime i try to calibrate i get some outrageously high numbers (ie. min x: 1658439) and they NEVER change as im moving teh pen around the screen. 

ty in advance! :D

---

### Post by farbird on 2007-05-31
yeah..
can post your values?

---

### Post by netvampire on 2007-05-31
thank you for sharing your succesful hints. i have this laptop and am going to give them a shot. i appreciate you sharing .

---

### Post by netvampire on 2007-06-01
the wireless fix suggested worked. but the audio did not.

i tried to follow the german instructions for hte screen but they are not clear at all, can someone do some converting for us. thanks

---

### Post by bofu on 2007-06-04
it looks like my module is not loading properly... 


bofu@Hpizo:~$ grep evtouch /var/log/Xorg.0.log 
(II) LoadModule: "evtouch"
(WW) Warning, couldn't open module evtouch
(II) UnloadModule: "evtouch"
(EE) Failed to load module "evtouch" (module does not exist, 0)


i ran through the german/doiche how-to and follwed it pretty well, the module location that they referred to does not exist on my ubuntu install, so i modified it:

host:~/src/ # cd evtouch-0.6.1 # 
host:~/src/evtouch-0.6.1 # cp evtoch_drv.o /usr/X11R6/lib/modules/input/

Instead of /usr/X11R6/lib/modules/input/ (which i dont have), i used /usr/lib/xorg/modules/input/ since its the closest matching directory structure i could find.

anyone get this working with Xorg 7.2?

anyone have any luck with their express slots?

---

### Post by necrolin on 2007-06-04
Thanks for the tips. I had enough of Vista and decided to install Linux on my machine. Sound works... just got to get that wireless working now.... erghhh.

Update: Everything works..... =)

---

### Post by necrolin on 2007-06-04
> **mlf said:**
> [QUOTE=diatribex;2648256
Good news that there is a solution for the audio. I'd like to get the web cam working as well, but that is not essential.

Michael

Webcam works right out of the box. Choose V4L2 through, because it doesn't work under V4L1.

---

### Post by farbird on 2007-06-06
audio works without headphone jack working..

did u get your headphone jack working?

hibernate doesnt work as well..

yours works?

---

### Post by farbird on 2007-06-06
i managed to get the touchscreen to work..
however, is there a way to edit xorg.conf such that a prolonged tap can be translated as a right click?

i will post my method later

---

### Post by farbird on 2007-06-06
as promised..
here's how i got it working with feisty kernel 2.6.20.16-generic

downloaded the 0.85 version of evtouch here
[http://www.stz-softwaretechnik.de/~ke/touchscreen/evtouch-0.8.5.tar.gz](http://www.stz-softwaretechnik.de/~ke/touchscreen/evtouch-0.8.5.tar.gz)

tar it to /usr/bin
copy the evtouch_drv.o to this folder
"/usr/lib/xorg/modules"

do a
cat /proc/bus/input/devices

find out the event number which the touchscreen is using..
for my tx1005au, it is using event2

for event2, go edit this file
/etc/modprobe.d/alias

add this line
alias char-major-13-66 evdev

add in these lines in /etc/X11/xorg.conf
```

Section "Files"
...
  InputDevices "/dev/input/event2" 	## correspond to the touchscreen event number
...
EndSection

Section "InputDevice"   		#  neue Section anlegen
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event2"  # correspond to the touchscreen event number
    Option "DeviceName" "touchscreen"
    #########################################
    # ein guter Anfang, wird später editiert:
    #########################################
    Option        "MinX"        "0"
    Option        "MinY"        "0"
    Option        "MaxX"        "2000"
    Option        "MaxY"        "2000"
    #########################################
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents"
    Option "Calibrate"  "1"		# wird nur zur Kalibrierung gebraucht!
EndSection

Section "ServerLayout"
...
  InputDevice  "touchscreen" "CorePointer"	#Zeile hinzufügen
 ...
EndSection

```

once this is done, gdm or kdm must be stopped

run in terminal
"/etc/init.d/kdm stop" or
"/etc/init.d/gdm stop"

in the tty screen, login and go into the folder where the evtouch0.85 was extracted.

run this
./calibrate.sh

this should run the calibration tool .
make sure u tap all the corners of the screen..
u should be able to see the minimum and maximum X and Y values.
write it down somewhere.

once that is done, press "ctrl,alt.bckspc" together, this will kill the calibration tool.

now go edit /etc/X11/xorg.conf

place the min/max X,Y values in.

comment the line which says
Option calibrate 1
by adding a # in front of it.

save and quit.

now run gdm or kdm by typing
/etc/init.d/gdm start
or
/etc/init.d/kdm start.

your touchscreen should work..

---

### Post by farbird on 2007-06-06
these are my values

    Option        "MinX"        "44"
    Option        "MinY"        "105"
    Option        "MaxX"        "3985"
    Option        "MaxY"        "3994"

---

### Post by farbird on 2007-06-16
anyone managed to get the headphone jack working?

---

### Post by farbird on 2007-06-16
> **farbird said:**
> i managed to get the touchscreen to work..
however, is there a way to edit xorg.conf such that a prolonged tap can be translated as a right click?



anyone can give some pointers?

on the above?

---

### Post by netvampire on 2007-06-16
i wish i could help but i can't farbird.
However, thanks for the post on getting the touch screen to work. I will try it out later and post my results. Take care,

---

### Post by farbird on 2007-06-17
funny how the /proc/bus/input/devices sometimes will allocate event2 for my touchscreen and sometimes it will be event4..

anyway to permanently let system decide it to be event2 for good>?

---

### Post by bofu on 2007-06-17
> **farbird said:**
> funny how the /proc/bus/input/devices sometimes will allocate event2 for my touchscreen and sometimes it will be event4..

anyway to permanently let system decide it to be event2 for good>?

i am seeing the same thing happen on mine - events will switch around at the drop of a reboot..

my touchpad, egalax and usb mouse switch events around.. weird!


just a note: i have deleted vista because its terrible and at one point just would not boot. i tried installing XP pro.. im deleting that too because the drivers just are not there... most of them are. (graphics, wifi) but the chipset drivers are a pain to install and the ethernet will not work in xp.


back to ubuntu:

has anyone had any luck with headphone jack sensing/switching?

and it seems we need to create a conclusive how-to for getting the touchscreen working properly

everything else is pretty much solid (?)

---

### Post by bofu on 2007-06-17
awesome.... i just had a breakthrough with the module... i had to CREATE the modulse/input directory and then copy the module into it and it actually loads;

note: on my system, /usr/X11R6/lib/ did not have a modules/input directory.. but Xorg was STILL looking there to load modules... so i did this:

mkdir /usr/X11R6/lib/modules/input -p && cp evtouch_drv.so /usr/X11R6/lib/modules/input/

and now the module loads... now just getting the appropriate event number will be the trick...

---

### Post by v.cecchetto on 2007-07-03
To correct associate the touchscreen event in the xorg.conf:

- download and open (evtouch sources)

[http://stz-softwaretechnik.com/~ke/touchscreen/xf86-input-evtouch-0.8.6.tar.bz2](http://stz-softwaretechnik.com/~ke/touchscreen/xf86-input-evtouch-0.8.6.tar.bz2)

- inside the zipped file you find a file (rules for udev, [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html))

69-touchscreen.rules 

- copy this file in
 
/etc/udev/rules.d/

-restart the system, your device is automatically associated to 

/dev/input/evtouch_event

- you can view the association looking in the dev directory

ls -l /dev/input

- now you can write in your /etc/X11/xorg.conf the correct string

Section "InputDevice"
 ...
   Option "Device" "/dev/input/evtouch_event"
 ... 

Also with this solution my laptop (tx1020) touchscreen sometimes doesn't work... I'm still looking for a better solution.

My first post... :popcorn:

---

### Post by arivero on 2007-07-03
I have tried to use the original eGalax drivers for the touchscreen. No success, because xorg 7.2 does not find touchkit_drv.o

Amusingly, I have found also that usbhid conflicts with tkusb but there is a workaround: to start the machine with the touchpad button switched off. In this way, and I do not know why, the usbhid does not load at startup (and just in case I have blacklisted it in later modprobes, via /etc/modprobe.d/blacklist, but it is probably not needed).

It should be interesting if somebody learns how to load the touchkit driver into xorg, It seems it works with 7.1 according a lot of forums.

What about the sound? It is not working with a kubuntu out of the box.

---

### Post by v.cecchetto on 2007-07-04
For all using xrandr, i write a simple bash script to rotate the screen:

cd /home

touch rotate.sh

chmod +x rotate.sh

gedit rotate.sh

...........................................................................................
#!/bin/bash          

STR=`xrandr | awk '/Current rotation/{print $NF}' `

case "$STR" in
     'normal')
	 xrandr -o left
         ;;
     'left')
         xrandr -o inverted
         ;;
     'inverted')
         xrandr -o right
         ;;
     'right')
         xrandr -o normal
         ;;
esac
...........................................................................................

Associate an icon to the script in the top panel.
Everytime you click the icon your monitor will rotate :roll: 90 degree anticlockwise.

---

### Post by RaZoR1394 on 2007-07-05
> **arivero said:**
> I have tried to use the original eGalax drivers for the touchscreen. No success, because xorg 7.2 does not find touchkit_drv.o

Amusingly, I have found also that usbhid conflicts with tkusb but there is a workaround: to start the machine with the touchpad button switched off. In this way, and I do not know why, the usbhid does not load at startup (and just in case I have blacklisted it in later modprobes, via /etc/modprobe.d/blacklist, but it is probably not needed).

It should be interesting if somebody learns how to load the touchkit driver into xorg, It seems it works with 7.1 according a lot of forums.

What about the sound? It is not working with a kubuntu out of the box.

Did you try adding the line into /etc/modprobe.d/alsa-base as adviced in the first post? This worked for me for a while but now sound is dead again. Damn.

There's something else that annoys me very much. The pointer slows down to a crawl with the pen after using the touchscreen for a while. I really don't know how to fix it. Another annoyance is that the laptop refuses to shut down at certain times. I have to use ALT-SYSRQ-U and ALT-SYSRQ-B. :( I'm going to try the udev rules solution posted here above. I hope it fixes the rotating event locations.

---

### Post by RaZoR1394 on 2007-07-05
> **v.cecchetto said:**
> For all using xrandr, i write a simple bash script to rotate the screen:

cd /home

touch rotate.sh

chmod +x rotate.sh

gedit rotate.sh

...........................................................................................
#!/bin/bash          

STR=`xrandr | awk '/Current rotation/{print $NF}' `

case "$STR" in
     'normal')
	 xrandr -o left
         ;;
     'left')
         xrandr -o inverted
         ;;
     'inverted')
         xrandr -o right
         ;;
     'right')
         xrandr -o normal
         ;;
esac
...........................................................................................

Associate an icon to the script in the top panel.
Everytime you click the icon your monitor will rotate :roll: 90 degree anticlockwise.


Thanks, but how do I enable XRANDR? I've searched across the forums and I've found that putting:

    Option "RandRRotation"

under Devices (there is no Devices so I put it under Device) or Screen makes it load. However I get this error when trying to work with XRANDR:

> 
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12


And could someone tell of how to get rid of all the double clicks? I tried adding the dummy mouse driver as told on the evtouch page but it doesn't work!

Maybe it has something to do with this:

> 
razor1394@viper:~$ cat /var/log/Xorg.0.log | grep core
(WW) Duplicate core pointer devices.  Removing core pointer attribute from "touchscreen"
(**) Synaptics Touchpad: always reports core events
(**) touchscreen: always reports core events


---

### Post by v.cecchetto on 2007-07-05
My complete xorg.conf

............................................................................
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
    InputDevice    "touchscreen" "CorePointer"
EndSection

Section "Files"
	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "it"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mouse0"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
    Identifier     "touchscreen"
    Driver         "evtouch"
    Option         "Device" "/dev/input/evtouch_event"
    Option         "DeviceName" "touchscreen"
        Option        "MinX"        "48"
        Option        "MinY"        "110"
        Option        "MaxX"        "4006"
        Option        "MaxY"        "4002"
        Option        "x0"        "-1"
        Option        "y0"        "-3"
        Option        "x1"        "-6"
        Option        "y1"        "-4"
        Option        "x2"        "-2"
        Option        "y2"        "-6"
        Option        "x3"        "-2"
        Option        "y3"        "-3"
        Option        "x4"        "-4"
        Option        "y4"        "-3"
        Option        "x5"        "2"
        Option        "y5"        "-1"
        Option        "x6"        "-5"
        Option        "y6"        "-3"
        Option        "x7"        "-2"
        Option        "y7"        "1"
        Option        "x8"        "5"
        Option        "y8"        "2"
    Option "TapTimer" "0"
    Option "LongTouchTimer" "250"
    Option "ReportingMode" "Raw"
    Option "SendCoreEvents" "On"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 60.0
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x800 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800_60 +0+0"
    Option         "RandRRotation" "on"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
............................................................................

With this configuration i solved for double-click.

To right-click, i do:

short-tip, long-tip

Settings for right-click are in the lines:

 Option "TapTimer" "0"
 Option "LongTouchTimer" "250"
 Option "ReportingMode" "Raw"
 Option "SendCoreEvents" "On"

Notice also the line:

Option         "Device" "/dev/input/mouse0"

I changed from the previous

Option         "Device" "/dev/input/mice"

Hope this helps you. :)

---

### Post by v.cecchetto on 2007-07-05
> **RaZoR1394 said:**
> Did you try adding the line into /etc/modprobe.d/alsa-base as adviced in the first post? This worked for me for a while but now sound is dead again. Damn.

There's something else that annoys me very much. The pointer slows down to a crawl with the pen after using the touchscreen for a while. I really don't know how to fix it. Another annoyance is that the laptop refuses to shut down at certain times. I have to use ALT-SYSRQ-U and ALT-SYSRQ-B. :( I'm going to try the udev rules solution posted here above. I hope it fixes the rotating event locations.

In different forum ([http://www.webservertalk.com/archive245-2004-6-281481.html](http://www.webservertalk.com/archive245-2004-6-281481.html)) i found that the suggested sequence is 

 ALT-SYSRQ-S (to write down the cache memory on disk)
 ALT-SYSRQ-U (to unmount all the file systems)
 ALT-SYSRQ-B (to reboot)

to save also the cache memory before quit.

---

### Post by arivero on 2007-07-05
Option RanrRRotation On works for me, dont forget the "on", or perhaps "yes".

Sound under kubuntu seems to work with OSS, but not Alsa. I keep trying.

---

### Post by arivero on 2007-07-06
Ok I see, the sound works both with alsa and oss. It was simply that I had been playing with the Kmix controls. The main problem, and it can be related to the jack problem, is that sound is routed to the "Front" controler. Via alsa, both PCM and Front can control the volume of the output, but no PC Speaker, which is a different line. But the buttons in the laptop control PC Speaker, so I can not control the volume of the sound without using kmix.

---

### Post by arivero on 2007-07-06
Ok I saw the point... "Select Master Channel" and then "Front", and now volume keys are OK, and silent works, except for the "beep" in the console and in firefox search box.

I note that kmix has a parameter labeled "headphones".

---

### Post by farbird on 2007-07-06
anyone got the headphone jack working yet?

btw, i cannot hibernate using nvidia,nv,vesa with my kdm..

the moment i press "alt-f1" to go terminal screen, the kdm quits and restarts itself..

same effect when i hibernate...

---

### Post by RaZoR1394 on 2007-07-06
> **v.cecchetto said:**
> My complete xorg.conf

............................................................................
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
    InputDevice    "touchscreen" "CorePointer"
EndSection

Section "Files"
	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "it"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mouse0"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
    Identifier     "touchscreen"
    Driver         "evtouch"
    Option         "Device" "/dev/input/evtouch_event"
    Option         "DeviceName" "touchscreen"
        Option        "MinX"        "48"
        Option        "MinY"        "110"
        Option        "MaxX"        "4006"
        Option        "MaxY"        "4002"
        Option        "x0"        "-1"
        Option        "y0"        "-3"
        Option        "x1"        "-6"
        Option        "y1"        "-4"
        Option        "x2"        "-2"
        Option        "y2"        "-6"
        Option        "x3"        "-2"
        Option        "y3"        "-3"
        Option        "x4"        "-4"
        Option        "y4"        "-3"
        Option        "x5"        "2"
        Option        "y5"        "-1"
        Option        "x6"        "-5"
        Option        "y6"        "-3"
        Option        "x7"        "-2"
        Option        "y7"        "1"
        Option        "x8"        "5"
        Option        "y8"        "2"
    Option "TapTimer" "0"
    Option "LongTouchTimer" "250"
    Option "ReportingMode" "Raw"
    Option "SendCoreEvents" "On"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 60.0
    Option "AddARGBGLXVisuals" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x800 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800_60 +0+0"
    Option         "RandRRotation" "on"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
............................................................................

With this configuration i solved for double-click.

To right-click, i do:

short-tip, long-tip

Settings for right-click are in the lines:

 Option "TapTimer" "0"
 Option "LongTouchTimer" "250"
 Option "ReportingMode" "Raw"
 Option "SendCoreEvents" "On"

Notice also the line:

Option         "Device" "/dev/input/mouse0"

I changed from the previous

Option         "Device" "/dev/input/mice"

Hope this helps you. :)

Thanks. This solves the double click problem but requires you to press really hard with the pen. Taking notes is also nearly impossible to do in Xournal.

edit: Sorry seems to work fine after I changed the mouse to mice. However I'm getting double clicks in xvkbd (X virtual keyboard).

Has anyone tried xstroke or onestroke? I don't see it in the repositiories.

---

### Post by Cuppa-Chino on 2007-07-07
> **v.cecchetto said:**
> My complete xorg.conf

............................................................................


Section "InputDevice"
    Identifier     "touchscreen"
    Driver         "evtouch"
    Option         "Device" "/dev/input/evtouch_event"
    Option         "DeviceName" "touchscreen"
        Option        "MinX"        "48"
        Option        "MinY"        "110"
        Option        "MaxX"        "4006"
        Option        "MaxY"        "4002"
        Option        "x0"        "-1"
        Option        "y0"        "-3"
        Option        "x1"        "-6"
        Option        "y1"        "-4"
        Option        "x2"        "-2"
        Option        "y2"        "-6"
        Option        "x3"        "-2"
        Option        "y3"        "-3"
        Option        "x4"        "-4"
        Option        "y4"        "-3"
        Option        "x5"        "2"
        Option        "y5"        "-1"
        Option        "x6"        "-5"
        Option        "y6"        "-3"
        Option        "x7"        "-2"
        Option        "y7"        "1"
        Option        "x8"        "5"
        Option        "y8"        "2"
    Option "TapTimer" "0"
    Option "LongTouchTimer" "250"
    Option "ReportingMode" "Raw"
    Option "SendCoreEvents" "On"
EndSection

............................................................................

With this configuration i solved for double-click.

To right-click, i do:

short-tip, long-tip

Settings for right-click are in the lines:

 Option "TapTimer" "0"
 Option "LongTouchTimcer" "250"
 Option "ReportingMode" "Raw"
 Option "SendCoreEvents" "On"

Notice also the line:

Option         "Device" "/dev/input/mouse0"

I changed from the previous

Option         "Device" "/dev/input/mice"

Hope this helps you. :)

first of all THANK YOU - your work has been INVALUABLE, thank you, mille gracie, danke, etc.

so a couple of question - I am still more newbie than anything else:

*have you managed to associate the rotate button on the panel with xrandr ?

*could you explain a bit more about the tapping and so I do not quite understand what the parameters mean

*your xorg conf contains a long list of x1 x2 x3 for the touchscreen, what do these do and how did you get them ?  -- <<nb  I cannot calibrate the touchscreen I always get error messages


also I sometimes get this error message:
> Message from syslogd@Media-laptop at Sat Jul  7 21:46:24 2007 ...
Media-laptop kernel: [  462.608000] Disabling IRQ #7

 -- irqpoll off option at boot to fix this ?


thank you again for all your help

---

### Post by Cuppa-Chino on 2007-07-07
> **necrolin said:**
> [QUOTE=mlf;2650937]

Webcam works right out of the box. Choose V4L2 through, because it doesn't work under V4L1.

really ? I cannot find my webcam under dev -- how did you install it or where did you find it

---

### Post by v.cecchetto on 2007-07-08
> **Cuppa-Chino said:**
> first of all THANK YOU - your work has been INVALUABLE, thank you, mille gracie, danke, etc.

Happy to help you! :)

> so a couple of question - I am still more newbie than anything else:

*have you managed to associate the rotate button on the panel with xrandr ?

Right click on the top panel > Add to Panel > Custom Application Launcher.

Now put in the "Name" field something (eg. "Rotate screen") and in the Command field put the position of the script in your hard disk, for examples: 

/home/rotate.sh

> *could you explain a bit more about the tapping and so I do not quite understand what the parameters mean

Look at the site of evtouch for better explanation of parameters

[http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html](http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html)

> *your xorg conf contains a long list of x1 x2 x3 for the touchscreen, what do these do and how did you get them ?  -- <<nb  I cannot calibrate the touchscreen I always get error messages

From the link above you can download the file containing the source code of the program:

[http://stz-softwaretechnik.com/~ke/touchscreen/xf86-input-evtouch-0.8.6.tar.bz2](http://stz-softwaretechnik.com/~ke/touchscreen/xf86-input-evtouch-0.8.6.tar.bz2)

Inside you can find the README.calibration file that explains you the calibration process and the meaning of the x1 x2 x3 parameters.

...
The x- and y-values in out.txt should be reasonable low numbers
(something between -20 to 20 maybe even lower). These values are the
amount of pixels the cursor has to be corrected on a certain
position. 
...

Which error message? Too difficult to help if you don't explain better, sorry...

> also I sometimes get this error message:
 -- irqpoll off option at boot to fix this ?

Try to read this:

[http://www.stearns.org/doc/hp-dv9225us-fedora-6.html](http://www.stearns.org/doc/hp-dv9225us-fedora-6.html)


> thank you again for all your help

:)

---

### Post by RaZoR1394 on 2007-07-08
Nice work, v.cecchetto . The touch screen works better (when it works :() than in Windows Vista. In Vista (and Ubuntu with a standard evtouch config) there is a offset that gets bigger the lower you get on the screen in portrait mode. Though maybe there's a need for a little little adjustment to get perfect input.

Xrandr works too btw. However I'm having one problem however with portrait mode. When I'm taking notes the lines are zig-zagging (back and forth to the left and right). This happens with both Gournall and Xournal.

I got sound to work by enabling "Front". Seems like I didn't pay attention to the colored radio button. I only checked the volume. Unfortunately the volume buttons don't work.

---

### Post by Cuppa-Chino on 2007-07-09
> **RaZoR1394 said:**
> Though maybe there's a need for a little little adjustment to get perfect input.

I got sound to work by enabling "Front". Seems like I didn't pay attention to the colored radio button. I only checked the volume. Unfortunately the volume buttons don't work.

evtouch README says that calibration is broken in 0.86 version, so cannot calibrate - trying to do it manually but also considering to install older version just for calibration.

Your offset issue should be solved by the x1,y1 x2,y2, x3,y3 etc in *v.cecchetto's* xorg.conf -- now as I cannot run the calibration I do not know exactly where these points are but I am guessing they are 9 points around the screen

0 = top left, 1 = centre top, etc etc to 8 = bottom right (could someone confirm this order).

On your volume buttons that is odd - mine worked out of the box - try going into Admin --> Keyboard Shortcuts and assigning them manually. What are you volume links show in that menu?

Also has anyone managed to get the light to go off on the mute button ?
How do I associate the rotate button on the panel with the rotate script ?

---

### Post by v.cecchetto on 2007-07-09
> **Cuppa-Chino said:**
> 
How do I associate the rotate button on the panel with the rotate script ?

Yuo find the answer in my previous post. :)

Right click on the top panel > Add to Panel > Custom Application Launcher.

- Name:           Rotate screen
- Command:    /home/rotate.sh

You only have to know where your script is. Mine is located in /home directory, for all users sharing.

---

### Post by Cuppa-Chino on 2007-07-09
> **v.cecchetto said:**
> Yuo find the answer in my previous post. :)

Right click on the top panel > Add to Panel > Custom Application Launcher.

- Name:           Rotate screen
- Command:    /home/rotate.sh

You only have to know where your script is. Mine is located in /home directory, for all users sharing.

Sorry I had phrased my question badly correctly - your previous answer helped my get a shortcut onto the Gnome Panel. Thanks again for your help.

What I was actually trying to ask is: **Has anybody been able to link the rotate script with the hardware button on the display (the blue led light up button on the bottom right of the lcd pane - the one with the two arrows on it)?l**

If so please post --- thanks again for your help

---

### Post by v.cecchetto on 2007-07-09
> **Cuppa-Chino said:**
> Sorry I had phrased my question badly correctly - your previous answer helped my get a shortcut onto the Gnome Panel. Thanks again for your help.

What I was actually trying to ask is: **Has anybody been able to link the rotate script with the hardware button on the display (the blue led light up button on the bottom right of the lcd pane - the one with the two arrows on it)?l**

If so please post --- thanks again for your help

Well, i tried to capture the rotate button event with 

xev

but nothing happen, ghost button for now... :)

---

### Post by Cuppa-Chino on 2007-07-10
has anyone managed to use the calibration tool on evtouch -- on a version newer than 0.6.1 -- which is the last that does not speak of a broken calibration

---

### Post by Cuppa-Chino on 2007-07-10
> **farbird said:**
> these are my values

    Option        "MinX"        "44"
    Option        "MinY"        "105"
    Option        "MaxX"        "3985"
    Option        "MaxY"        "3994"

what version did you calibrate with? because I tried calibrating with 0.61 and i get this mess:

```
        Option        "MinX"        "20000"
        Option        "MinY"        "20000"
        Option        "MaxX"        "0"
        Option        "MaxY"        "0"
        Option        "x0"        "1072466"
        Option        "y0"        "6550183"
        Option        "x1"        "1073101"
        Option        "y1"        "6550183"
        Option        "x2"        "1073736"
        Option        "y2"        "6550183"
        Option        "x3"        "1072466"
        Option        "y3"        "6550578"
        Option        "x4"        "1073101"
        Option        "y4"        "6550578"
        Option        "x5"        "1073736"
        Option        "y5"        "6550578"
        Option        "x6"        "1072466"
        Option        "y6"        "6550973"
        Option        "x7"        "1073101"
        Option        "y7"        "6550973"
        Option        "x8"        "1073736"
        Option        "y8"        "6550973"
```

any ideas will try calibrating with the newer one again

EDIT the problem was that the driver did not compile for the older one , hundreds of errors become clear on second try, newer driver still does not work at all

---

### Post by Cuppa-Chino on 2007-07-11
maybe an odd quesiton has anybody tried the drivers at [http://www.eeti.com.tw/web20/eg/drivers.htm#ub]("http://www.eeti.com.tw/web20/eg/drivers.htm#ub")

any impressions compared to the one discussed in the thread

---

### Post by RaZoR1394 on 2007-07-11
> **Cuppa-Chino said:**
> has anyone managed to use the calibration tool on evtouch -- on a version newer than 0.6.1 -- which is the last that does not speak of a broken calibration

I managed to calibrate with 0.8.6 without any problems.

---

### Post by Cuppa-Chino on 2007-07-11
> **RaZoR1394 said:**
> I managed to calibrate with 0.6.8 without any problems.

and also guess you mean **0.[COLOR="Red"]8[/COLOR].6**

are you using **nv** or **nvidia driver**?

I get an error about xorg not being able to release files -- will copy it when I am at home again

---

### Post by RaZoR1394 on 2007-07-11
> **Cuppa-Chino said:**
> and also guess you mean **0.[COLOR="Red"]8[/COLOR].6**

are you using **nv** or **nvidia driver**?

I get an error about xorg not being able to release files -- will copy it when I am at home again

Yes sorry, I meant 0.8.6 and I'm using the "nvidia" proprietary driver.

---

### Post by v.cecchetto on 2007-07-11
> **Cuppa-Chino said:**
> what version did you calibrate with? because I tried calibrating with 0.61 and i get this mess:

```
        Option        "MinX"        "20000"
        Option        "MinY"        "20000"
        Option        "MaxX"        "0"
        Option        "MaxY"        "0"
        Option        "x0"        "1072466"
        Option        "y0"        "6550183"
        Option        "x1"        "1073101"
        Option        "y1"        "6550183"
        Option        "x2"        "1073736"
        Option        "y2"        "6550183"
        Option        "x3"        "1072466"
        Option        "y3"        "6550578"
        Option        "x4"        "1073101"
        Option        "y4"        "6550578"
        Option        "x5"        "1073736"
        Option        "y5"        "6550578"
        Option        "x6"        "1072466"
        Option        "y6"        "6550973"
        Option        "x7"        "1073101"
        Option        "y7"        "6550973"
        Option        "x8"        "1073736"
        Option        "y8"        "6550973"
```

any ideas will try calibrating with the newer one again

EDIT the problem was that the driver did not compile for the older one , hundreds of errors become clear on second try, newer driver still does not work at all


I know this kind of mess, not a valid calibration naturally. When i get this kind of result, i uppose, is because touchscreen not function properly and calibration module gets input from other sources, like touchpad or mouse. x1, y1, x2,... are little number, indicating pixel correction when you touch one of the nine cross on the screen.

I put other screen of my configuration:

master@etabeta:~$ ls -l /dev/input
totale 0
drwxr-xr-x 2 root root      80 2007-07-11 13:16 by-id
drwxr-xr-x 2 root root     140 2007-07-11 13:16 by-path
crw-rw---- 1 root root 13,  64 2007-07-11 13:16 event0
crw-rw---- 1 root root 13,  65 2007-07-11 13:16 event1
crw-rw---- 1 root root 13,  66 2007-07-11 13:16 event2
crw-rw---- 1 root root 13,  67 2007-07-11 13:16 event3
crw-rw---- 1 root root 13,  68 2007-07-11 13:16 event4
crw-rw---- 1 root root 13,  69 2007-07-11 13:16 event5
crw-rw---- 1 root root 13,  70 2007-07-11 13:16 event6
crw-rw---- 1 root root 13,  71 2007-07-11 13:16 event7
lrwxrwxrwx 1 root root       6 2007-07-11 13:16 evtouch_event -> event2
crw-rw---- 1 root root 13,  63 2007-07-11 15:16 mice
crw-rw---- 1 root root 13,  32 2007-07-11 15:16 mouse0
crw-rw---- 1 root root 13,  33 2007-07-11 15:16 mouse1
crw-rw---- 1 root root 13,  34 2007-07-11 13:16 mouse2
crw-rw---- 1 root root 13, 128 2007-07-11 13:16 ts0
crw-rw---- 1 root root 13, 129 2007-07-11 13:16 ts1
crw-rw---- 1 root root 13, 130 2007-07-11 13:16 ts2

You can see the correct event2 association with evtouch_event.
(for fun you can try to capture touchscreen output to the console with 
cat /dev/input/evtouch_event 
:))

If this is your case you are on the good way to solve, try calibration with:

./calibrate.sh /dev/input/evtouch_event

to point touchscreen directly.

Hope you solve this way.

---

### Post by Cuppa-Chino on 2007-07-11
> **v.cecchetto said:**
> 
You can see the correct event2 association with evtouch_event.
(for fun you can try to capture touchscreen output to the console with 
cat /dev/input/evtouch_event 
:))

yes I can confirm this

> **v.cecchetto said:**
> If this is your case you are on the good way to solve, try calibration with:

./calibrate.sh /dev/input/evtouch_event

to point touchscreen directly.

Hope you solve this way.

nope calibration with 0.8.6 still fails with error message:
```
waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing
```

I had # out the fonts, synaptic touchpad, changed mice to mouse 0 in the xorg.conf but all to no use -- I keep getting the above error

here is my xorg.conf (well most of it):
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"

  InputDevice  "touchscreen" "CorePointer"	#Zeile hinzufügen

EndSection

Section "Files"

	# path to defoma fonts
   FontPath        "/usr/share/fonts/X11/misc"
   FontPath        "/usr/share/fonts/X11/cyrillic"
   FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
   FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
   FontPath        "/usr/share/fonts/X11/Type1"
   FontPath        "/usr/share/fonts/X11/100dpi"
   FontPath        "/usr/share/fonts/X11/75dpi"
   FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

  InputDevices "/dev/input/evtouch_event" 	## correspond to the touchscreen event number manual add

EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"   		#  neue Section anlegen
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/evtouch_event"  # correspond to the touchscreen event number
    Option "DeviceName" "touchscreen"
    #########################################
    # ein guter Anfang, wird später editiert:
    #########################################
    Option        "MinX"        "50"
    Option        "MinY"        "100"
    Option        "MaxX"        "4000"
    Option        "MaxY"        "4000"
    #########################################
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents"
    Option "Calibrate"  "1"		# wird nur zur Kalibrierung gebraucht!
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation C51 [Geforce 6150 Go]"
    Driver         "nvidia"
	Option "AddARGBGLXVisuals" "True" ## added for compiz compliance ##
	Option "DisableGLXRootClipping" "True" ## added for compiz compliance ##
	Option "Coolbits" "1" ## added for GPU clockspeed info ##
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation C51 [Geforce 6150 Go]"
    Monitor        "Generic Monitor"
	Option "RandRRotation" "on" ## added for rotation ##
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

```

_**So items left to sort out (on my machine at least):**_
in order of importance
* touchscreen calibration
* headphone jack & jack sensing (does SPDIF work - I have seen the button in ALSA config)
* hibernate & standbye - anybody got any success with those
* Media card reader
* the hardware buttons on the LCD panel that are used to rotate the screen in Vista etc
* Express slot TV card (DVB-T)
* Remote control
* Webcam - last install failed so badly I reinstalled root completely
* Fingerprint reader

any tips on those

---

### Post by v.cecchetto on 2007-07-12
> **Cuppa-Chino said:**
> 
nope calibration with 0.8.6 still fails with error message:
```
waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing
```

I had # out the fonts, synaptic touchpad, changed mice to mouse 0 in the xorg.conf but all to no use -- I keep getting the above error


Ok, that message tells you that your X server still running. 

You need stopping X server before calling calibrate.sh.

To stop it:

- logout from current user

- CTRL + ALT + F1 

- now that you are in text mode, the X server may be still running, we now go hunting to kill it (no violence please)

- you have to obtain a list of graphic processes still running (install psmisc from repository):

pstree -p | less

- near every running process you find is proper number 

eg. gdm(5290)&#9472;&#9472;&#9472;gdm(5291)&#9472;&#9516;&#9472;Xorg(5294)

- time to kill (both gdm and Xorg)

kill -9 5290
kill -9 5291
kill -9 5294

- ok recontrol again, gdm is difficult to kill, it restarts :)

pstree -p |less

- ...so on till you kill it

- Congratulation! :KS Now you can start calibrate.sh

---

### Post by Grard on 2007-07-12
@v.cecchetto:
You can stop gdm a lot easier on the console (ctl+alt+F1) with:
sudo /etc/init.d/gdm stop
when you're done calibrating you can start it again with:
sudo /etc/init.d/gdm start

@Cuppa-Chino:
on some of your points:
* hibernate & standbye - anybody got any success with those
   standby worked out-of-the-box. I haven't got hibernation working yet 
* Media card reader
  worked ootb, only tested a SD card though
* Express slot TV card (DVB-T)
  works once you tune it with kaffeine
* Webcam - last install failed so badly I reinstalled root completely
  works ootb if you select a v4l2 device in ekiga, gstreamer-properties, etc. microphone doesn't work :(

---

### Post by Cuppa-Chino on 2007-07-12
> **Grard said:**
> @v.cecchetto:
You can stop gdm a lot easier on the console (ctl+alt+F1) with:
sudo /etc/init.d/gdm stop
when you're done calibrating you can start it again with:
sudo /etc/init.d/gdm start

no luck -- I tried killing every process on the list that did not start with k and it seemed to make no difference I still keep getting the same error.  I also tried starting in recovery mode so that GDM would not be loaded at all but that did not help either.

one other error that I have noticed is that it claims it cannot open empty_cursor.xbm

any ideas who the Noob (that being me) can get a better /fuller  error output and put it into a file 


> **Grard said:**
>  @Cuppa-Chino:
on some of your points:
* hibernate & standbye - anybody got any success with those
   standby worked out-of-the-box. I haven't got hibernation working yet 
* Media card reader
  worked ootb, only tested a SD card though
* Express slot TV card (DVB-T)
  works once you tune it with kaffeine
* Webcam - last install failed so badly I reinstalled root completely
  works ootb if you select a v4l2 device in ekiga, gstreamer-properties, etc. microphone doesn't work :(

okay first round of tests:
* media card reader works with SD card :)
* express slot TV card (DVB-T Kaffeine finds [SIZE=-1]**DiBcom 3000**-MC/P[/SIZE]) seems to works  :) (no channel lock yet but need adapter for roof aerial)
* webcam not tried again -- due to me having to reinstall last time
* standbye -- click suspend button and the screen goes blank, fans start going to max and then nothing happens, computer does not react to ctrl+alt+del, ctrl+alt+f1 or any other key, have to FORCE off with power switch

* microphone - does yours not work in EKIGA or in generell?

---

### Post by v.cecchetto on 2007-07-13
> **Cuppa-Chino said:**
> no luck -- I tried killing every process on the list that did not start with k and it seemed to make no difference I still keep getting the same error.  I also tried starting in recovery mode so that GDM would not be loaded at all but that did not help either.

one other error that I have noticed is that it claims it cannot open empty_cursor.xbm

any ideas who the Noob (that being me) can get a better /fuller  error output and put it into a file 



You have to copy it in root directory (it is a bug of calibrate.sh)

sudo cp empty_cursor.xbm /


I guess now it works...

---

### Post by Cuppa-Chino on 2007-07-13
Dear Mr v.cechetto,

I bow before you greatness - now it does work, thank you very much indeed. You have been so patient.

So now on to other things on the list.... (well actually going to try enjoy it for awhile and then do a complete backup before I mess anymore)

Suspend / Hibernate next.... oh dear that could take some time.

---

### Post by Cuppa-Chino on 2007-07-13
> **Grard said:**
> 
@Cuppa-Chino:
on some of your points:
* hibernate & standbye - anybody got any success with those
   standby worked out-of-the-box. I haven't got hibernation working yet 
* Webcam - last install failed so badly I reinstalled root completely
  works ootb if you select a v4l2 device in ekiga, gstreamer-properties, etc. microphone doesn't work :(

* guess nobody got ideas on hibernate / standbye but as said that is for tomorrow
* webcam dito am working on the reinstall- too scarred and uninterested to try at the moment

* MICROPHONE worked fine on the previous install (1 week ago which I wrecked with trying to configure the webcam), I have no reinstalled using the same disc and method --- exactly the same !!!--- and now I can no longer record!

```
options snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0
```when I look at the recording level monitor it clearly shows that sounds is turning up somewhere, because pending my volume and the amount of boost I use the spikes change.... annoying any help

EDIT SOLVED -- a beer jogged my memory :D

* in SYSTEM-----PREFERENCES------SOUND----AUDIO CONFERENCING 
choose ALC861VD for both drop downs.

* in VOLUME CONTROL (can be accessed via the volume control button & right click (also possible via ALSAMIXER command in terminal))
x ENABLE ALL items in PREFERENCES
x INPUT choose FRONT MIC
x RECORDING boost up the Capture volume
x PLAYBACK boost up FRONT MIC and FRONT MIC BOOST -- I have also muted the FRONT MIC to avoid feedback, not sure if necessary

Now skype et al work fine

---

### Post by Grard on 2007-07-14
Cuppa-Chino, I had the microphone volume turned down too. Thanks for the tip!

I also managed to boot without the noapic parameter, now I have IOAPIC support which solves the problem with interrupts (IRQ7 disabled)

As a kernel parameter in /boot/grub/menu.lst I now use:
```
acpi_osi="!Linux"
```

---

### Post by Cuppa-Chino on 2007-07-14
> **Grard said:**
> Cuppa-Chino, I had the microphone volume turned down too. Thanks for the tip!

I also managed to boot without the noapic parameter, now I have IOAPIC support which solves the problem with interrupts (IRQ7 disabled)

As a kernel parameter in /boot/grub/menu.lst I now use:
```
acpi_osi="!Linux"
```

Hmm now I am confused:

my understanding was that APIC and ACPI are fundamentally different:

**Advanced Programmable Interrupt Controller** (**APIC**)

**Advanced Configuration and Power Interface** (**ACPI)**

So just to be clear with > acpi_osi="!LINUX" you can boot without any probelms and use suspend ? 

where did you get the info about this boot option from ? just so I can learn where to search in future

Do you have the *feared* Kernel Interrupt error 
> kernel: [  462.608000] Disabling IRQ #7
What is your full line of parameters after UUID reference?
I am currently using:
```
vga=0x317 noapic irqpoll noirqdebug splash
```

---

### Post by operatorone on 2007-07-14
I've been lurking in this forum because it's the most complete guide for my tx1120us to date. I just wanted to kick in that this forum rocks hard and I have been able to resolve some of my tx1120us issues by following these forums and a few others. 

I am not using ubuntu but have chosen Backtrack 2 instead as it gives me the most functionality "out of the box" so to speak. After failing to get Fedora Core running properly (it installs and then everyone says a "yum update" will resolve most of the issues but of course "yum update" does not work properly sigh). 

I was curious if someone might be able to compare the two briefly? I have heard alot about ubuntu but haven't tried it yet as I have so much to do I like to stick with the distro I have been using (fedora core), however as stated above it's not going to happen right now on my notebook, and the hardware is too sweet to allow Vista as my only OS. 

cheers and hope I can contribute on some level as time moves on. thanks for letting me lurk in your forums. 

:guitar:

---

### Post by operatorone on 2007-07-15
Here's a pretty detailed instruction set for the touchscreen, and it's written in english for those who don't read German.

cheers

---

### Post by Grard on 2007-07-15
> **Cuppa-Chino said:**
> Hmm now I am confused:

my understanding was that APIC and ACPI are fundamentally different:

**Advanced Programmable Interrupt Controller** (**APIC**)

**Advanced Configuration and Power Interface** (**ACPI)**

APIC and ACPI are definitely not the same thing but they are related. ACPI is needed to access the APIC, else you can only use the XT-PIC. 

> 
So just to be clear with  you can boot without any probelms and use suspend ? 

where did you get the info about this boot option from ? just so I can learn where to search in future

Do you have the *feared* Kernel Interrupt error 
Nope, no more IRQ problems and each device gets its own IRQ from the APIC
Suspend works most of time, sometimes it failes to wake up. I needed to disable 'sync to vblank' in compiz and somewhere else I can't remember right now :/
> 
What is your full line of parameters after UUID reference?
I am currently using:
```
vga=0x317 noapic irqpoll noirqdebug splash
```

after the UUID:
```
ro quiet splash acpi_osi="!Linux" acpi_os_name="Windows 2006"
```
I got the 'acpi_osi' line from dmesg (I had to put quotes around the !Linux part):
```

ACPI: System BIOS is requesting _OSI(Linux)
ACPI: Please test with "acpi_osi=!Linux"

```
As I understand it, the tx1000's ACPI BIOS asks the OS for its name and if Linux answers truthfully ACPI breaks APIC, when Linux lies about its name ACPI & APIC work. The acpi_os_name="Windows 2006" tells the kernel it should identify as MS Vista.

There is more info about this in /usr/share/doc/linux-doc-<kernel-version>/Documentation/kernel-parameters.txt.gz
(sudo aptitude install linux-doc)

==EDIT==
:( I spoke too soon, yesterday and this morning booting without 'noapic' worked fine but since this afternoon it hangs a lot again. :(

Now it works without 'noapic'. I'll try more boot options and see if I can get it to boot reliable.

---

### Post by blubbi321 on 2007-07-16
i followed your setup intructions till calibration and am now unable to see the lower three crosses.

in my out.txt there are insanely low values (-1000 and lower)

guess i found out why they call it broken ;-)

anybody got any hints on this one?

thanks in advance :)

---

### Post by danielbr on 2007-07-16
Hello guys,

That's my first post.
I would like to know if somebody got any luck on making the earphones jacks work.

Thank you all for your posts.

And I also would like to contribute showing the way I made my wireless work. This steps were based on some tutorials I've found on google.

1) Download the driver and unzip the driver on your desktop

------------------------------------------------------------------------------------------------
$ wget http:// ftp.us.dell.com/ network/ 151517.EXE
$ unzip -a R151517.EXE
------------------------------------------------------------------------------------------------

2) Clearing previous setups

------------------------------------------------------------------------------------------------
$ modprobe -r bcmwl5
$ sudo rmmod ndiswrapper
$ sudo apt-get remove ndiswrapper-utils
$ sudo rm -r /etc/ndiswrapper/
$ sudo rm -r /etc/modprobe.d/ndiswrapper
------------------------------------------------------------------------------------------------

3) Installing the driver
------------------------------------------------------------------------------------------------
$ sudo apt-get install ndiswrapper-utils
$ sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
$ sudo ndiswrapper -m
$ sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5/*.conf
------------------------------------------------------------------------------------------------

---

### Post by Cuppa-Chino on 2007-07-16
> **blubbi321 said:**
> i followed your setup intructions till calibration and am now unable to see the lower three crosses.

in my out.txt there are insanely low values (-1000 and lower)

guess i found out why they call it broken ;-)

anybody got any hints on this one?

thanks in advance :)

as you can see from all my posts I needed more than just a bit of help.
is the line with calibration=1 in your xorg.conf active?
did you kill all gdm active threads ?
 could you post your xorg.conf ? then I can check and let you know if I see any odditiies.

do you get any error messages?

---

### Post by Cuppa-Chino on 2007-07-17
> **Grard said:**
> 
```
ro quiet splash acpi_osi="!Linux" acpi_os_name="Windows 2006"
```I got the 'acpi_osi' line from dmesg (I had to put quotes around the !Linux part):
```

ACPI: System BIOS is requesting _OSI(Linux)
ACPI: Please test with "acpi_osi=!Linux"

```As I understand it, the tx1000's ACPI BIOS asks the OS for its name and if Linux answers truthfully ACPI breaks APIC, when Linux lies about its name ACPI & APIC work. The acpi_os_name="Windows 2006" tells the kernel it should identify as MS Vista.

There is more info about this in /usr/share/doc/linux-doc-<kernel-version>/Documentation/kernel-parameters.txt.gz
(sudo aptitude install linux-doc)

==EDIT==
:( I spoke too soon, yesterday and this morning booting without 'noapic' worked fine but since this afternoon it hangs a lot again. :(

Now it works without 'noapic'. I'll try more boot options and see if I can get it to boot reliable.

ah okay so where did yours hang ? mine crashed three times while checking the HD. 

also the first message the kernel pumps out is:

> acpi_osi="!Linux" ignored


but suspend does work with that, have you tried 

```
acpi_os_name="Windows 2006"  irqpoll noirqdebug noapic
```


last but not least to answer danielbr: the headphone & mic jacks are one of things we are all still searching for
.

anybody got either the big remote with USB sensor or the small remote to work ?
is the big remote programable, ie can you control other devices with it as well?

---

### Post by farbird on 2007-07-17
the remote works by triggering the media buttons on your tx1000 cover.
if u assign the physical buttons to the apps, the remote should activate them accordingly as if u actually pressed those buttons on your laptop

---

### Post by farbird on 2007-07-17
headphone jack and mic jack..

anyone tried?

was thinking of trying to boot the windows vista partition, plug in headphone and shutdown and replace hdd with linux hdd and see if the headphone works....

not sure if the acpi will retain this setting after shutdown..

i strongly suspect the routing of the power to the headphone jack is done by acpi..

---

### Post by Cuppa-Chino on 2007-07-18
> **farbird said:**
> headphone jack and mic jack..

anyone tried?

was thinking of trying to boot the windows vista partition, plug in headphone and shutdown and replace hdd with linux hdd and see if the headphone works....

not sure if the acpi will retain this setting after shutdown..

i strongly suspect the routing of the power to the headphone jack is done by acpi..

if that was the case then the option 
```
ro quiet splash acpi_osi="!Linux" acpi_os_name="Windows 2006"
```
should help or not? is it should enable acpi...

---

### Post by kyrox on 2007-07-19
Anyone got any problems with the temperature of the graphics card running too high? I'm using the latest nvidia drivers and it idles at 68 C and under some load at 71-73 ... This can't be normal.. What's your temperature?

I have a tx1020ea,  so all components should be almost the same.
thanks

---

### Post by Cuppa-Chino on 2007-07-20
> **kyrox said:**
> Anyone got any problems with the temperature of the graphics card running too high? I'm using the latest nvidia drivers and it idles at 68 C and under some load at 71-73 ... This can't be normal.. What's your temperature?

I have a tx1020ea,  so all components should be almost the same.
thanks

components are all the same

a) I will check mine (if I manage) today in both vista and 'buntu

b) what are you running when you stress the system

---

### Post by matth45 on 2007-07-20
I've found this thread very helpful - thanks all.

I have tx1000, on which I'm running Fedora 7 x86_64, but I've run into many of the same issues.

That said, I have a couple comments that you may (or may not :-P) find helpful.

This may have been mentioned, but the evtouch driver seems to segfault on 64-bit systems.  I emailed the author with debug info, but he hasn't replied.  I saved a core file from this crash and took a quick look through it, but I won't have time to do any hacking around in the driver for a couple weeks at least...

The headphone problems are due to the fact that alsa doesn't have the right codec driver for the sound chip in the tx1000's.  The snd-hda-intel module is a somewhat generic interface to many very similar audio chips.  You can ```
cat /proc/asound/card0/codec#0
```, and check out all the nodes that say "Vendor Defined Widget" ... I'm not certain, but I suspect at least some of these are unrecognized controls for the sound chip in the tx1000.  I don't have any other computer with a working snd-hda-intel family chip to compare it to.  

At any rate, I talked to an alsa developer who pointed me to  [ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/]("ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/") where you can get the latest development snapshots of the driver.  The last one I tried added the models 3stack-660-digout, lenovo, and dallas for me. Currently 3stack, 3stack-660, 3stack-660-digout and lenovo all produce sound from the speakers, but none from the headphones.  I hope, in time, they will support the chip correctly.

The acpi_osi="string" stuff is new in the kernel. I have a 2.6.21 kernel that doesn't yet support it.  If you get a message about the !Linux string being ignored, then your kernel doesn't support it.  (Reference this patch in the 2.6.22 kernel: [http://lkml.org/lkml/2007/7/2/244]("http://lkml.org/lkml/2007/7/2/244")).

So what kernel are you using in Ubuntu when you get this working?  I tried it with a 2.6.22 fedora testing kernel and still had problems.

If you're interested in getting the built in modem working, I believe the smartlink driver from linmodems will work.  Just run the scanModem script and follow the instructions.

Also... if you're interested in getting the screen to rotate with the one of the buttons on the bottom right corner of the screen, you could, for example if you're using beryl in gnome, put a command like
```
/usr/bin/xmodmap -e "keycode 129=XF86LaunchF"
```
in your gnome startup (gnome-session-properties) and then map XF86LaunchF to your Run Command0 in Beryl Settings -> General Options -> Shortcuts -> Commands, and set Command0 to run a script that might look something like:

```
 #!/bin/tcsh

#script to rotate the screen on button push

set statefile = "/tmp/.screen_orientation"
set XRANDR = xrandr

if ( -r $statefile ) then
        set current_orientation = `cat $statefile`
else
        set current_orientation = normal
endif

switch ( $current_orientation )
case normal:
        $XRANDR -o right
        echo right > $statefile
        breaksw
case right:
        $XRANDR -o inverted
        echo inverted > $statefile
        breaksw
case inverted:
        $XRANDR -o left
        echo left > $statefile
        breaksw
case left:
        $XRANDR -o normal
        echo normal > $statefile
        breaksw
default:
        $XRANDR -o normal
        echo normal > $statefile
        breaksw

exit 0

```

You'll also need to add 
```
Option      "RandRRotation" "on"
```
to the Device section of your xorg.conf file to get xrandr working.

This approach works for running any arbitrary command you'd like with just about any of the media buttons.  Use xev, which is in the xorg-x11-utils-7.1-4.fc7 package in fedora, to find the keycode for the above.  Keycode 129 is the code for the circle button next to the DVD button.

Sorry this was sooo long.  Hope it was helpful to someone!

---

### Post by kyrox on 2007-07-21
> **Cuppa-Chino said:**
> components are all the same

a) I will check mine (if I manage) today in both vista and 'buntu

b) what are you running when you stress the system

Ok thanks. When under 0-5% cpu load the system idles at 62% (just using firefox). When I run, for instance, zsnes or anything else it rises. I went afk to answer a phone call for a few minutes and came back when zsnes was running and it was up to 80 C and I panicked and shut the computer off :P

I read on a another thread that there is a bug with the nvidia drivers for this specific video card (Geforce 6150 Go) and that the gpu fan is totally silent in linux. However, when the gpu temp rises to about 71-73 a fan (I don't know which, might be the cpu) starts to run faster.

Also, in nvidia-settings the "Slowdown Threshold" is set to 130 C. Isn't that a bit high?

I tried using Coolbits to underclock to 3D gpu freq, but whenever I try to set a new frequency and hit apply, it bounces back to the default 425 MHz. The memory frequency is at 0 MHz. Is it because it shares the RAM?

thanks

---

### Post by Cuppa-Chino on 2007-07-21
> **kyrox said:**
> Ok thanks. When under 0-5% cpu load the system idles at 62% (just using firefox). When I run, for instance, zsnes or anything else it rises. I went afk to answer a phone call for a few minutes and came back when zsnes was running and it was up to 80 C and I panicked and shut the computer off :P

I read on a another thread that there is a bug with the nvidia drivers for this specific video card (Geforce 6150 Go) and that the gpu fan is totally silent in linux. However, when the gpu temp rises to about 71-73 a fan (I don't know which, might be the cpu) starts to run faster.

Also, in nvidia-settings the "Slowdown Threshold" is set to 130 C. Isn't that a bit high?

I tried using Coolbits to underclock to 3D gpu freq, but whenever I try to set a new frequency and hit apply, it bounces back to the default 425 MHz. The memory frequency is at 0 MHz. Is it because it shares the RAM?

thanks


ok tested mine in Ubuntu with glxgears: got up to 90° in the glxgears test, my threshold also shows 130° now I still need to check if this is the same in Windo$...

could it be °F ???? should not but could be I guess would make more sense...

then threshold would be 130°F = 55°C a bit low maybe...

---

### Post by Cuppa-Chino on 2007-07-21
> **matth45 said:**
>  This approach works for running any arbitrary command you'd like with just about any of the media buttons.  Use xev, which is in the xorg-x11-utils-7.1-4.fc7 package in fedora, to find the keycode for the above.  Keycode 129 is the code for the circle button next to the DVD button.

Sorry this was sooo long.  Hope it was helpful to someone!

not too long at all --- how does xev work I am having no luck, I start and press the various media buttons like the circle and I get output on only a few.

---

### Post by matth45 on 2007-07-23
Sorry.  I did this a couple weeks ago, so I left out a step.

Some of the media keys don't have kernel driver keycodes by default, and some (like the brightness buttons) don't produce scancodes at all, but rather talk directly to some piece of hardware.  I'll give the DVD button as an example, but the rest that work, work this way:

The basic idea is that any key that produces as scancode, can be assigned a kernel keycode.  Once it has a kernel keycode it can be assigned a meaning in the kernel via loadkeys or in the x server, via xmodmap.

So, if you don't see a xkeysym from xev, check dmesg.  You should see something like:
```
atkbd.c: Unknown key pressed (translated set 2, code 0x?? on isa0060/serio0).
atkbd.c: Use 'setkeycodes e00e <keycode>' to make it known.
```

We have to find an unused keycode to map the DVD button to.  Use the dumpkeys command to do this.  I picked 89 for this button.  So I added the following to /etc/rc.local:

```
setkeycodes e00e 89
```

You can run this command now to map the scancode right away.  Once it's mapped, you should be able to see output from xev.  It should look something like this:

```
KeyPress event, serial 29, synthetic NO, window 0x4000001,
    root 0x1a5, subw 0x0, time 4044877368, (94,-17), root:(1026,122),
    state 0x0, keycode 211 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 29, synthetic NO, window 0x4000001,
    root 0x1a5, subw 0x0, time 4044877370, (94,-17), root:(1026,122),
    state 0x0, keycode 211 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

The important part is this:

```
keycode 211 (keysym 0x0, NoSymbol)
```

Then you can run

```
usr/bin/xmodmap -e "keycode 211=XF86LaunchF"
```

Like in my other post.

---

### Post by Cuppa-Chino on 2007-07-23
> **matth45 said:**
> 
So, if you don't see a xkeysym from xev, check dmesg.  You should see something like:
```
atkbd.c: Unknown key pressed (translated set 2, code 0x?? on isa0060/serio0).
atkbd.c: Use 'setkeycodes e00e <keycode>' to make it known.
```We have to find an unused keycode to map the DVD button to.

I do not see anything with **atkbd.c** this with this command:
```
dmesg
```is the line of code missing something ?

---

### Post by Cuppa-Chino on 2007-07-23
also I have noticed this odd behaviour:

sometimes (mostly now) it seems that FRONT setting in volume control is the important one and not PCM, I have trimmed PCM just now in a java applet and volume stayed loud, when I trimmed FRONT then decreased and I could increase PCM again...

anybody else have that?

also I have found this very useful link:

[http://www.ubuntugeek.com/disable-synaptics-touchpad-while-typing-in-ubuntu.html](http://www.ubuntugeek.com/disable-synaptics-touchpad-while-typing-in-ubuntu.html)

heaven sent, the keyboard on the tx1000 is so small my right thumb kept hitting the slider, it does exactly what it says on the tin

---

### Post by farbird on 2007-07-23
this laptop is perfect for linux if we can get the input/output audio jacks resolved..

---

### Post by Cuppa-Chino on 2007-07-24
> **farbird said:**
> this laptop is perfect for linux if we can get the input/output audio jacks resolved..

and the suspend and hibernate -- or does that work for you?? if so which boot options are you using?

---

### Post by Cuppa-Chino on 2007-07-24
> **Cuppa-Chino said:**
> ok tested mine in Ubuntu with glxgears: got up to 90° in the glxgears test, my threshold also shows 130° now I still need to check if this is the same in Windo$...

could it be °F ???? should not but could be I guess would make more sense...

then threshold would be 130°F = 55°C a bit low maybe...

checked in vista, also hot similar to ubuntu just fans starts up earlier, max temp went to nearly 80°C in Ubuntu and nearly 77°C in Vista.... oddly hot but so be it....

anybody got the issue on FRONT and PCM I described? how do I assign the VOLUME KEYS to control FRONT and not PCM ???

---

### Post by matth45 on 2007-07-25
I have the same issue with the sound buttons.  The settings in System -> Preferences -> Hardware -> Sound under Gnome seem to have no effect.

I'm not sure why you wouldn't see the atkb.c messages.  I'm not familiar with Ubuntu, so maybe we have different versions of the keyboard driver.  You could also try running showkey in both scancodes and keycodes modes to see if you get a scancode or a keycode for the buttons you're interested in.  You'll probably have to run it from a console (rather than an xterm).

Note that showkey grabs your keyboard input, and may scroll a lot of text by at once, so you may miss the message telling you that it will quit after 10 seconds without any keyboard button presses.

Another interesting note: I took a look through this page [http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)

Here's a segment from the disassembly of the tx1000 DSDT in the BIOS F.13:

            ```
Method (_INI, 0, NotSerialized)
            {
                Store (0x07D0, OSYS)
                If (CondRefOf (\_OSI, Local0))
                {
                    If (\_OSI ("Linux"))
                    {
                        Store (0x03E8, OSYS)
                    }

                    If (\_OSI ("Windows 2001"))
                    {
                        Store (0x07D1, OSYS)
                    }

                    If (\_OSI ("Windows 2001 SP1"))
                    {
                        Store (0x07D1, OSYS)
                    }

                    If (\_OSI ("Windows 2001 SP2"))
                    {
                        Store (0x07D2, OSYS)
                    }

                    If (\_OSI ("Windows 2006"))
                    {
                        Store (0x07D6, OSYS)
                    }
                }
            }
```

If you look through the rest of the disassembly, it definitely pays attention to the value of the OSYS register, though I can't say what exactly it's doing.  Has anyone tried any of the other options listed in there?

Also, I got the following warnings when I recompiled it:
```

dsdt.dsl  3794:                 Method (_Q16, 0, NotSerialized)
Warning  1086 -                            ^ Not all control paths return a value (_Q16)

dsdt.dsl  5839:                             And (CTRL, 0x1E)
Warning  1104 -                                     ^ Result is not used, operator has no effect

dsdt.dsl  6096:                             And (CTRL, 0x1E)
Warning  1104 -                                     ^ Result is not used, operator has no effect

dsdt.dsl  6220:                             And (CTRL, 0x1E)
Warning  1104 -                                     ^ Result is not used, operator has no effect

```

Though I'm inclined to think that these are harmless.  It's kind of irksome to know that it is in fact a Microsoft DSDT that's causing some of the problems with this laptop:

```
ACPI: DSDT 37F0ADF3, 8D23 (r1 HP       MCP51M  6040000 MSFT  3000000)
```

You just can't get away! :-P

---

### Post by Cuppa-Chino on 2007-07-25
_matth45_ does your suspend & hibernate work? i guess not but if so let us know.

has anybody tried using suspend2 or uswsusp?

---

### Post by matth45 on 2007-07-25
It does actually suspend or hibernate on mine.... It just never comes back. :grin:

I haven't tried anything but swsusp, which is built into my kernel.

---

### Post by farbird on 2007-07-25
> **Cuppa-Chino said:**
> and the suspend and hibernate -- or does that work for you?? if so which boot options are you using?

both doesnt work for me...

---

### Post by matth45 on 2007-07-26
Actually, I have had some limited success with hibernate and suspend using the swsusp built into the fedora kernel (2.6.22.1-27.fc7).  I'm using the following boot parameters:

```
acpi_osi="!Linux" acpi_os_name="Windows 2006" noapic
```

If I don't use noapic I still get random lockups.

The biggest problem I see is with the LCD.  When going into and out of hibernate, and out of suspend I see analog artifacts on the LCD (THIS IS BAD), probably caused by something driving the LCD at the wrong refresh rate.  At first I thought it had crashed, but now I just close the lid so that the screen is off and wait it out.  After no more than a minute, it comes through.

I'm using the ndiswrapper, and had some problems with the network coming back on resume, so I created a file

```
/etc/pm/config.d/unload_modules
```

containing:

```
SUSPEND_MODULES="ndiswrapper"
```

Also, the USB system doesn't seem to come back correctly.  For example, after coming back from hibernate lsusb doesn't see the touchscreen.

There's an ATRpms suspend 2 kernel package available for fedora, but when I try it it segfaults immediately when I give it the noapic argument.

---

### Post by Cuppa-Chino on 2007-07-26
> **Cuppa-Chino said:**
> checked in vista, also hot similar to ubuntu just fans starts up earlier, max temp went to nearly 80°C in Ubuntu and nearly 77°C in Vista.... oddly hot but so be it....

anybody got the issue on FRONT and PCM I described? how do I assign the VOLUME KEYS to control FRONT and not PCM ???

On the sound side some more remarkable observations:

when I run these program individually:
[java bloobowl - fumbbl]("http://fumbbl.com")-- a great little fantasy sports game -- then the FRONT vol setting is important
Skype -- then PCM is important

when I run both the java application and skype then skype cannot find the sound device -- NB I have a desktop with a audigy 2 that can handle both at the same time fine


I have now set both FRONT & PCM (at the same time) in the control menu under GNOME--> PREFERENCES --> SOUND

------
TV-OUT have not tried...

another thing: has anybody used s-video out successfully ?

---

### Post by blubbi321 on 2007-07-26
> **Cuppa-Chino said:**
> as you can see from all my posts I needed more than just a bit of help.
is the line with calibration=1 in your xorg.conf active?
did you kill all gdm active threads ?
 could you post your xorg.conf ? then I can check and let you know if I see any odditiies.

do you get any error messages?

thanks for your response.

in the meantime i fixed the "no crosses" problem myself. i just had to set the correct (native) resolution for the screen.

i can now run trough the calibration process but if i use the configuration it seems to "scale" wrong.

what i am trying to say is that a click on 100,100 positions the coursor at 10,10 while pointing at 110,110 moves it to 1000,1000

(i made up those values, it is just to show my problem)

so i got a little window in the center of my screen but my "clicks" on the screen still move the coursor to a wrong position.

xorg.conf is as follows:

```
Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mouse3"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5 6 7"
	Option		"Buttons"	"15"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

#Section "Device"
#	Identifier	"ATI RADEON X700"
#	Driver		"vesa"
#	Busid		"PCI:3:0:0"
#EndSection

Section "Device"
        Identifier        "ATI RADEON X700"
        Driver            "ati"
        BusID             "PCI:3:0:0"
        Option            "XAANoOffscreenPixmaps"
        Option 		  "AGPMode" "4"
        Option 		  "AGPFastWrite" "true"
        Option 		  "DisableGLXRootClipping" "true"
        Option 		  "AddARGBGLXVisuals" "true"
        Option 		  "AllowGLXWithComposite" "true"
        Option 		  "EnablePageFlip" "true"

#################
	Option "DynamicClocks" "on" 

#################
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON X700"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x800"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x800"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Option          "AIGLX"         "true"
	Identifier	"Default Layout"
  	screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
	Inputdevice	"touchscreen" "CorePointer"
	Inputdevice	"dummy"
###########################
EndSection


Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection




Section "InputDevice"
	Identifier "touchscreen"
	Driver "evtouch"
	Option "Device" "/dev/input/evtouch_event"
	Option "DeviceName" "touchscreen"
        
	#Option        "MinX"        "3"
        #Option        "MinY"        "0"
        #Option        "MaxX"        "2100"
        #Option        "MaxY"        "2100"

        Option        "MinX"        "163"
        Option        "MinY"        "112"
        Option        "MaxX"        "1964"
        Option        "MaxY"        "1920"
        Option        "x0"        "-794"
        Option        "y0"        "-593"
        Option        "x1"        "4"
        Option        "y1"        "-586"
        Option        "x2"        "792"
        Option        "y2"        "-585"
        Option        "x3"        "-791"
        Option        "y3"        "5"
        Option        "x4"        "7"
        Option        "y4"        "1"
        Option        "x5"        "792"
        Option        "y5"        "4"
        Option        "x6"        "-789"
        Option        "y6"        "594"
        Option        "x7"        "7"
        Option        "y7"        "589"
        Option        "x8"        "794"
        Option        "y8"        "587"


	Option "TapTimer" "0"
	Option "LongTouchTimer" "250"
	Option "ReportingMode" "Raw"
	Option "SendCoreEvents" "On"
	Option "SwapX" "1"
	Option "SwapY" "0"

	Option "Calibrate" "1"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

#Section "ServerFlags"
#	Option		"AIGLX"	"off"
#EndSection
```

ps: if i am through with all this if would be nice to have a working setup with my laptop (touchscreen and normal screen running in some kind of parallel mode)
but that can (has to) wait till the touchscreen config is finished ;-)

---

### Post by Cuppa-Chino on 2007-07-26
> **blubbi321 said:**
> 



```

Section "InputDevice"
	Identifier "touchscreen"
	Driver "evtouch"
	Option "Device" "/dev/input/evtouch_event"
	Option "DeviceName" "touchscreen"
        
	Option        "MinX"        "3"                [COLOR="Red"]#These four lines should NOT be commented out[/COLOR]
        Option        "MinY"        "0"
        Option        "MaxX"        "2100"
        Option        "MaxY"        "2100"

        Option        "MinX"        "163"
        Option        "MinY"        "112"
        Option        "MaxX"        "1964"
        Option        "MaxY"        "1920"
        Option        "x0"        "-794"   COLOR="Red"]#Your calibration data looks wrong, these numbers are too high, -30 to +30 should be the max.[/COLOR]
        Option        "y0"        "-593"
        Option        "x1"        "4"
        Option        "y1"        "-586"
        Option        "x2"        "792"
        Option        "y2"        "-585"
        Option        "x3"        "-791"
        Option        "y3"        "5"
        Option        "x4"        "7"
        Option        "y4"        "1"
        Option        "x5"        "792"
        Option        "y5"        "4"
        Option        "x6"        "-789"
        Option        "y6"        "594"
        Option        "x7"        "7"
        Option        "y7"        "589"
        Option        "x8"        "794"
        Option        "y8"        "587"


	Option "TapTimer" "0"
	Option "LongTouchTimer" "250"
	Option "ReportingMode" "Raw"
	Option "SendCoreEvents" "On"
	Option "SwapX" "1"
	Option "SwapY" "0"

	#Option "Calibrate" "1"    [COLOR="Red"]#This line should be commented out after calibration[/COLOR]
EndSection
```

[COLOR="Red"]Comment out or delete (with backup of course) the entire wacom section [/COLOR]
[COLOR="Magenta"]Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection[/COLOR]





Ok couple of things have been changed and commented in the above xorg fragement - do the things in RED  your xorg conf - delete or comment out all wacom references **#** .

Couple of question and comments:

a) _what computer do you have? _-- if you are using Radeon x700 then it is probably not a tx1000 -- touchscreen guide should still work if you are using right touchscreen

b) _what touchscreen does your computer have? _the **evtouch driver** is for the galaxy type device / not the wacom (as far as I can tell) --
please run lsusb to confirm what device you have (check for a line with galaxy)

---

### Post by blubbi321 on 2007-07-26
> **Cuppa-Chino said:**
> Ok couple of things have been changed and commented in the above xorg fragement - do the things in RED  your xorg conf - delete or comment out all wacom references **#** .

Couple of question and comments:

a) _what computer do you have? _-- if you are using Radeon x700 then it is probably not a tx1000 -- touchscreen guide should still work if you are using right touchscreen

b) _what touchscreen does your computer have? _the **evtouch driver** is for the galaxy type device / not the wacom (as far as I can tell) --
please run lsusb to confirm what device you have (check for a line with galaxy)

i am sorry ... i just saw that the tx1000 is a computer an not a specific touchscreen. i dont know my touchscreens type by hard but it is somehting very similar.

```
lsusb
Bus 002 Device 009: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
```

i will try your comments tomorrow

thank you ... and sorry again :/

---

### Post by Cuppa-Chino on 2007-07-27
> **blubbi321 said:**
> i am sorry ... i just saw that the tx1000 is a computer an not a specific touchscreen. i dont know my touchscreens type by hard but it is somehting very similar.

```
lsusb
Bus 002 Device 009: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
```

i will try your comments tomorrow

thank you ... and sorry again :/

hey no apolgoies, that looks like the right touchscreen give the stuff a spin. what computer do you have if I may ask?

---

### Post by Cuppa-Chino on 2007-07-27
> **Cuppa-Chino said:**
> 
TV-OUT have not tried...

another thing: has anybody used s-video out successfully ?

Still not working, still searching.

nvtv does not help as the faq says:

> 2.  ISSUES WITH SOME CARD TYPES

2.1 I have a GeForce4 MX, GeForce4 GO or GeForce MX GPU card, and nvtv 
    doesn't work. 

Well reading the driver man helped:

USE the nvidia-settings tool! either from console **gksudo nvidia-settings** or from the applications--system menu...

or manually (obsolete ?? maybe ? maybe not ?) in xorg.conf

---

### Post by blubbi321 on 2007-07-30
> **Cuppa-Chino said:**
> hey no apolgoies, that looks like the right touchscreen give the stuff a spin. what computer do you have if I may ask?

ive got an asus z9200va with the touchscreen attached at the external vga port of the ati x700 (the xconf shows the right name)

---

### Post by guttersnipe on 2007-07-31
Wow, this is an awesome thread.  Thanks so much to the contributors.  I found this page while searching for a way to get the headphone jacks working on my new HP tx1000z laptop.

In order to get the sound from the built-in speakers, I had to add a line to
/etc/modprobe.d/alsa-base
```
options snd-hda-intel model=3stack
```
...that got the built-in speakers working (the microphone(s) as well), but the audio jacks (no matter what I try in alsamixer) just won't work.  Following this guide, I changed it to
```
options snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0
```
...but I can't tell a difference between the two.  Anyone get the audio jack to put out sound yet?

Just FYI, I had the following working out-of-the-box.
webcam
sound buttons (though the mute button works, it does not change color)
dvd media button (opens rhythmbox)
wired network
remote control (yeah, believe it)
touch screen (though it wasn't calibrated)
usb ports

I haven't fiddled with S-video or the VGA out yet.

---

### Post by i_like_debian on 2007-07-31
Got a HP tx1000 last week and found the discussions on this thread very helpful.  I first tried Debian etch, but some drivers wouldn't work and I didn't want to go to lenny.  So I though I'd give Ubuntu a try.


Here is a list of the things I had to do to get it to work.  Most of them are culled from this thread and numerous other google searches.  The list is mainly for newbies and not experts.  It walks you through the installation step-by-step.  This procedure includes the [COLOR="Red"]hibernation[/COLOR], which no one seem to have mentioned before.




1. INSTALLING UBUNTU

- Use the Disk Manager in Vista to shrink the primary partition

- Use Ubuntu live CD to boot, hit F6 on the default install option 
  "Ubuntu: Start or install Ubuntu" and place boot option "vga=791" 
  at the end of the line (don't turn off acpi though!)

- Once the desktop appears, double click on Install and follow the 
  on-screen installation instructions to install Ubuntu.  Choose guided 
  disk partitioning, using the largest continuous free space 

- Restart after installation
  On boot, hit "e" on the first option.  Go to "kernel ..." and 
  hit "e" again.  Type "vga=791" at the end of the line and hit return.  
  Then hit "b" to boot.

- Once logged in, edit /boot/grub/menu.lst to add the boot option "vga=791" 
  to the end of the lines starting with "kernel ..."



2. SOUND

- Edit /etc/modprobe.d/options and insert "options snd_hda_intel model=3stack"
  (Should also try 3stack-660.)

- Reboot the system.  You should now have sound, but headphone jack still 
  doesn't work.

- Also tried the following but jack still didn't work.

  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#2)

- Some have suggested that fixes in alsa will appear in future daily development 
  snapshots.  Will see.



3. WIRELESS

- In a terminal issue the following command:

  sudo -s
  rmmod bcm43xx
  echo 'blacklist bcm43xx' >> /etc/modprobe.d/blacklist
  apt-get update
  apt-get install ndiswrapper-common
  apt-get install ndiswrapper-source
  apt-get install ndiswrapper-utils-1.9
  module-assistant prepare
  module-assistant build ndiswrapper
  wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)
  unzip -a R151517.EXE
  cd DRIVER
  ndiswrapper -i bcmwl5.inf
  ndiswrapper -m
  modprobe ndiswrapper
  exit

- To check that the wireless is working, do "iwconfig".  You should see a line
  with "wlan0 ..." followed by information about the wireless environment.

- Use the Network Manager (button next to the volume at the top) 
  to configure your wireless access.

- References:
  [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
  [http://www.debian-administration.org/articles/401](http://www.debian-administration.org/articles/401) 



4. HIBERNATE (aka suspend to disk)

- Download uswsusp by "sudo apt-get install uswsusp".

- To see if this works, do "sudo s2disk".  The system will report the 
  progress of the suspension and then power off.  Next time you power on, 
  the system will resume.

- Replace the two existing files in /usr/lib/hal/scripts/linux/ by 
  the new ones given here...
  [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

- Hibernate works but suspend to memory does not.  And of course, you need 
  to have a large enough swap space to accomodate the used memory image.



5. HAVEN'T TRIED YET

- touch screen (some have reported success here)
- mic (both front and jacks)
- webcam
- remote (some say it works out of the box)



6. TRIED BUT NOT WORKING

- external display: fn-f6 doesn't work
- headphone jack (see above)

---

### Post by Cuppa-Chino on 2007-07-31
> **i_like_debian said:**
> Got a HP tx1000 last week and found the discussions on this thread very helpful.  I first tried Debian etch, but some drivers wouldn't work and I didn't want to go to lenny.  So I though I'd give Ubuntu a try.


Here is a list of the things I had to do to get it to work.  Most of them are culled from this thread and numerous other google searches.  The list is mainly for newbies and not experts.  It walks you through the installation step-by-step.  This procedure includes the [COLOR="Red"]hibernation[/COLOR], which no one seem to have mentioned before.




1. INSTALLING UBUNTU

- Use the Disk Manager in Vista to shrink the primary partition



2. SOUND

- Also tried the following but jack still didn't work.

 - Some have suggested that fixes in alsa will appear in future daily development 
  snapshots.  Will see.



3. WIRELESS


- References:
  [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
  [http://www.debian-administration.org/articles/401](http://www.debian-administration.org/articles/401) 



4. HIBERNATE (aka suspend to disk)

- Download uswsusp by "sudo apt-get install uswsusp".

- To see if this works, do "sudo s2disk".  The system will report the 
  progress of the suspension and then power off.  Next time you power on, 
  the system will resume.

- Replace the two existing files in /usr/lib/hal/scripts/linux/ by 
  the new ones given here...
  [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/](http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/)

- Hibernate works but suspend to memory does not.  And of course, you need 
  to have a large enough swap space to accomodate the used memory image.



5. HAVEN'T TRIED YET

- touch screen (some have reported success here)
- mic (both front and jacks)
- webcam
- remote (some say it works out of the box)



6. TRIED BUT NOT WORKING

- external display: fn-f6 doesn't work
- headphone jack (see above)

Ok nice summary:

2) jacks are the problem of the day
3) would add that I would not recommend using network manager if you are using WPA ! -- gotta remember to post the link I use here
4) thank you!
5) touch screen works, mic works (see this thread for settings), webcam cracked my install, 
6) for second display install nvidia-settings (see my post above where I activated TV out should work as well

---

### Post by isachan on 2007-07-31
I just ordered my tx1000, and still have to wait another 2 weeks to get it, but this thread has been really informational that I could base my buying decision for the same tablet.

Anyway, phone jack issue is rather a pain, and I was looking for a lead. Then I stumbled into this page :

[http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?module=hda-intel](http://www.alsa-project.org/alsa-doc/doc-php/asoundrc.php?module=hda-intel)

Scroll down to "JACK plugin" section, it states :

This plugin allows the user to connect applications that support alsa natively to the JACK daemon.

to compile and install jack, you need to move to src/pcm/ext
directory, and run "make jack" and "make install-jack".
this is intentional.

To use the JACK plugin you will need to add the following to your .asoundrc.

	pcm.jackplug {
	        type plug
	        slave { pcm "jack" }
	}

	pcm.jack {
	        type jack
	        playback_ports {
 	               0 alsa_pcm:playback_1
 	               1 alsa_pcm:playback_2
 	       }
 	       	capture_ports {
 	               0 alsa_pcm:capture_1
                	1 alsa_pcm:capture_2
        	}
	}

Now, you can use:

	aplay -Djackplug somefile
	arecord -Djackplug somefile

I hope I'm on the right spot.
Was this helpful ?

Isao

---

### Post by guttersnipe on 2007-08-02
> **i_like_debian said:**
> 
1. INSTALLING UBUNTU

- Use the Disk Manager in Vista to shrink the primary partition

- Use Ubuntu live CD to boot, hit F6 on the default install option 
  "Ubuntu: Start or install Ubuntu" and place boot option "vga=791" 
  at the end of the line (don't turn off acpi though!)

- Once the desktop appears, double click on Install and follow the 
  on-screen installation instructions to install Ubuntu.  Choose guided 
  disk partitioning, using the largest continuous free space 

- Restart after installation
  On boot, hit "e" on the first option.  Go to "kernel ..." and 
  hit "e" again.  Type "vga=791" at the end of the line and hit return.  
  Then hit "b" to boot.

- Once logged in, edit /boot/grub/menu.lst to add the boot option "vga=791" 
  to the end of the lines starting with "kernel ..."


I bought a custom tx1000z, and the vga=791 bit does nothing but make the screen look bad during the ubuntu splash loading screen...then it freezes on that screen during the bootup (I'm not even able to ctr+alt+del to reboot)

For my model, I had to add this to the end of my kernel line in grub:
```
noapic irqpoll
```

also, some people earlier suggested the use of:
```
acpi_osi="!Linux" acpi_os_name="Windows 2006"
```
...but I haven't noticed anything beneficial from it (my kerenel even rejects the "acpi_osi="!Linux"" bit).  It might help with the suspend and hibernation issues people were having though...

---

### Post by i_like_debian on 2007-08-02
It's clear there are still a number of resolved issues with installing linux on the tx1000, and it seems that everyone has slightly different hardware so any one solution is not universal.


Ever thought about using MVware?  This is not for those who detest Microsoft.  But here's my thinking if you can live with Windows...

After spending a lot of time in the last few days on it, I got most of the basic stuff working (video, sound, wireless).  That's essentially all I need for work.  And the rest (blustooth, webcam, touch screen, sd reader, etc.) I haven't tried.  But to get linux to completely replace wiindows on this machine, there is still a long way.

This reminds me of the last time I got a laptop and tried to put debian on it.  That took me many more hours.  And the reason why I have held on to it for 6 years is because I didn't want to go through the same pain again.  And now with the tx1000, I am reliving it.

At work, I need my linux for programming and writing.  So I don't need a lot of functionalities.  But I often need to use MS Office too (there are just some things OOffice don't do well).  So when I travel, I had to bring along two laptops (after a while, reboot to switch OS just gets too tiring).

So why not have the best of both worlds?  With VMware, you can boot Windows and have Ubuntu as a virtual machine, and you can transfer files between them.  I can have Office runing, with my linux in another window compiling codes.  With the tx1000, the speed is certainly good enought for that.  The linux won't run at top speed, but I can live with that (it's certainly faster than my last laptop -- an Inspiron 4000).


I tried the VMware Player yesterday with a Ubuntu VM last night.  I seems to work fine.  All the hardware are patched through Windows, so everything works in Ubuntu out of the box, and no tweeking!

And next time I migrate to a new computer, I can bring my entire Ubuntu VM over.  No more struggle with setting up your hardware in linux.

---

### Post by guttersnipe on 2007-08-02
I still can't seem to get the touchscreen calibration to work.  I tried the values posted by others, but there were slight offsets.

When I run ./calibrate.sh, X never comes up and gives me errors:
```

dlopen: /usr/lib/xorg/modules//evtouch_drv.so
(EE) Failed to load module "evtouch" (loader failed, 7)
...
(EE) No Input driver matching 'evtouch'
...
/usr/bin/ev_calibrate: 1: Syntax error: "(" unexpected

```
```

#ls /usr/lib/xorg/modules/
...
evtouch_drv.so

```
```

#ls /
...
calibrate.sh
empty_cursor.xbm

```

I'm using the "nv" driver.
I'm running 64-bit, could that be the problem?
Any ideas?

Thanks in advance.

EDIT:
I reinstalled ubuntu from scratch with the 32-bit version, and the calibration loads fine now.  Anyone get it to run in 64??
Something I noticed:
In 32-bit, every time I go to any tty (ctrl+alt+fX), gdm crashes.  This NEVER happened in 64-bit.

My Values:
Min: 31/89
Max: 4012/3987

---

### Post by MildSauce on 2007-08-03
Great work, have just completed a read through of this, and I hope to start trying out some of the things that have worked, (touchscreen). However, one things stands out is that there are multiple touchscreen guides here, it does appear that one is working, and although I can't remember the guide at the current moment, I'll be finding it. (if someone could point to it, I'm sure that it would save some people time.)

With a look at the activity history it looks like most of the development is happening within the last 3 weeks.

Grats to the front runners.

---

### Post by Cuppa-Chino on 2007-08-03
> **guttersnipe said:**
> I bought a custom tx1000z, and the vga=791 bit does nothing but make the screen look bad during the ubuntu splash loading screen...then it freezes on that screen during the bootup (I'm not even able to ctr+alt+del to reboot)

For my model, I had to add this to the end of my kernel line in grub:
```
noapic irqpoll
```

also, some people earlier suggested the use of:
```
acpi_osi="!Linux" acpi_os_name="Windows 2006"
```
...but I haven't noticed anything beneficial from it (my kerenel even rejects the "acpi_osi="!Linux"" bit).  It might help with the suspend and hibernation issues people were having though...

_try this CODE to boot_:

```
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID='your UUID' ro quiet acpi_osi="!Linux" acpi_os_name="Windows 2006" noapic vga=0x317 splash
```

note that I use vga=0x317 this has worked fine for me

_on the hibernate side_:

```
sudo s2disk
```

just gives me a corrupted screen and a crash.

_wrt to two screens: _
if you are prepared to use Nvidia restricted drivers, then the **nvidia-settings** works a treat, auto recognises tvout etc.

---

### Post by RaZoR1394 on 2007-08-03
> **guttersnipe said:**
> I still can't seem to get the touchscreen calibration to work.  I tried the values posted by others, but there were slight offsets.

When I run ./calibrate.sh, X never comes up and gives me errors:
```

dlopen: /usr/lib/xorg/modules//evtouch_drv.so
(EE) Failed to load module "evtouch" (loader failed, 7)
...
(EE) No Input driver matching 'evtouch'
...
/usr/bin/ev_calibrate: 1: Syntax error: "(" unexpected

```
```

#ls /usr/lib/xorg/modules/
...
evtouch_drv.so

```
```

#ls /
...
calibrate.sh
empty_cursor.xbm

```

I'm using the "nv" driver.
I'm running 64-bit, could that be the problem?
Any ideas?

Thanks in advance.

EDIT:
I reinstalled ubuntu from scratch with the 32-bit version, and the calibration loads fine now.  Anyone get it to run in 64??
Something I noticed:
In 32-bit, every time I go to any tty (ctrl+alt+fX), gdm crashes.  This NEVER happened in 64-bit.

My Values:
Min: 31/89
Max: 4012/3987

Hi. I think there is a bug with the source. I had similar problems with 64bit too but with 32bit it worked fine.

---

### Post by i_like_debian on 2007-08-03
> **Cuppa-Chino said:**
> 
...

_on the hibernate side_:

```
sudo s2disk
```

just gives me a corrupted screen and a crash.




At s2disk, the system switches to a text vga screen and reports hibernation progress.  Sometime I do see a garbled screen, that's probably what you mean by a "corrupted screen", but the hibernation does work.  After that it powers off the machine.

When you say "crash", does the machine powers off?   (A crash is usually a hung system.)  If the machine does power off, it probably did work.  Next time when you boot, on the Ubuntu splash screen you will see the progress bar appears to stall at the very beginning.  This is because the boot is loading the memory image from the hibernation.  Give it a little time and the session should resume.

And has anyone else gotten s2disk to work?

---

### Post by guttersnipe on 2007-08-03
> **i_like_debian said:**
> 
I tried the VMware Player yesterday with a Ubuntu VM last night.  I seems to work fine.  All the hardware are patched through Windows, so everything works in Ubuntu out of the box, and no tweeking!


I agree.  vmware-server is a must for me and my laptop.  I just installed it the other day.  Now, since the touchscreen sends signals to X at such a low level, one would imagine that there wouldn't be issues with using the tablet inside your virtual machine.  One would be wrong.  Somehow it gets screwed up in calibration within the virtual machine.  Did this happen to you?  Does anyone know of a fix?

---

### Post by Cuppa-Chino on 2007-08-03
> **i_like_debian said:**
> At s2disk, the system switches to a text vga screen and reports hibernation progress.  Sometime I do see a garbled screen, that's probably what you mean by a "corrupted screen", but the hibernation does work.  After that it powers off the machine.

When you say "crash", does the machine powers off?   (A crash is usually a hung system.)  If the machine does power off, it probably did work.  Next time when you boot, on the Ubuntu splash screen you will see the progress bar appears to stall at the very beginning.  This is because the boot is loading the memory image from the hibernation.  Give it a little time and the session should resume.

And has anyone else gotten s2disk to work?

no crash? it is a crash alright: fans blasting on, screen hangs, lights on, power stays on, that is called crash in my book. I am using Nvidia proprietary drivers, are you?

---

### Post by i_like_debian on 2007-08-03
> **Cuppa-Chino said:**
> no crash? it is a crash alright: fans blasting on, screen hangs, lights on, power stays on, that is called crash in my book. I am using Nvidia proprietary drivers, are you?

ok, I believe you.
The Nvidia driver would crash mine big time too.  I'm just using nv.

---

### Post by i_like_debian on 2007-08-03
> **guttersnipe said:**
> I agree.  vmware-server is a must for me and my laptop.  I just installed it the other day.  Now, since the touchscreen sends signals to X at such a low level, one would imagine that there wouldn't be issues with using the tablet inside your virtual machine.  One would be wrong.  Somehow it gets screwed up in calibration within the virtual machine.  Did this happen to you?  Does anyone know of a fix?


I didn't check the touch screen inside vmware (since I don't plan to use touch in linux).  I just checked my xorg.conf and didn't find anything about wacom, so I wouldn't expect mine to work right either.

---

### Post by RaZoR1394 on 2007-08-04
> **guttersnipe said:**
> I agree.  vmware-server is a must for me and my laptop.  I just installed it the other day.  Now, since the touchscreen sends signals to X at such a low level, one would imagine that there wouldn't be issues with using the tablet inside your virtual machine.  One would be wrong.  Somehow it gets screwed up in calibration within the virtual machine.  Did this happen to you?  Does anyone know of a fix?

Touch screen works fine in Windows XP with Virtualbox. You need to use usb host or whatever It's called and install the official Windows driver for it.

---

### Post by guttersnipe on 2007-08-04
> **RaZoR1394 said:**
> Touch screen works fine in Windows XP with Virtualbox. You need to use usb host or whatever It's called and install the official Windows driver for it.

Ah, I prefer virtualbox to vmware when I'm in gentoo, but it's not in standard ubuntu repos, so I just went with what's easier.  I'll use virtualbox then, thanks!

---

### Post by guttersnipe on 2007-08-05
In case anyone else tries virtualbox on this computer and your Virtual Machine freezes at "Starting the virtual machine...", you have to enable AMD hardware visualization in BIOS.

I'm running a tx1000z, and it shipped with the option disabled.

More info [here]("http://forums.virtualbox.org/viewtopic.php?p=3860#3860")

---

### Post by i_like_debian on 2007-08-06
> **i_like_debian said:**
> I didn't check the touch screen inside vmware (since I don't plan to use touch in linux).  I just checked my xorg.conf and didn't find anything about wacom, so I wouldn't expect mine to work right either.


Instead of the VMware Server, I downloaded VMware Workstation 6.  The touchscreen now works without any tweaking and runs with no glitches.  The culprit was the old VMware Tools in the free VMware Server version.  The new VMware Tools actually detects the hardware you have and automatically builds a proper xorg.conf file for you!


VMware Workstation allows me to run a 64-bit OS inside the virtual machine.  (I have tried the 32-bit Debian too.  The 64-bit system definitely runs faster inside the virtual machine.)  It also permits easy file sharing between linux and Windows.  I have successfully installed AMD64 Debian Etch from the network install CD. I can read/write files from my Windows directories like I use to on my old dual-boot system.  Just restored all my user files from my old Dell laptop and was able to recompile my programs with the 64-bit compiler.  I finally feel like I've been re-integrated into the real world again!


But as for all good things, there is a catch:  VMware Workstation 6 costs real money, $189 of it.  But since I need it for work, I was able to get my boss to pay for it:)

---

### Post by i_like_debian on 2007-08-06
> **i_like_debian said:**
> Instead of the VMware Server, I downloaded VMware Workstation 6.  The touchscreen now works without any tweaking and runs with no glitches.  The culprit was the old VMware Tools in the free VMware Server version.  The new VMware Tools actually detects the hardware you have and automatically builds a proper xorg.conf file for you!


VMware Workstation allows me to run a 64-bit OS inside the virtual machine.  (I have tried the 32-bit Debian too.  The 64-bit system definitely runs faster inside the virtual machine.)  It also permits easy file sharing between linux and Windows.  I have successfully installed AMD64 Debian Etch from the network install CD. I can read/write files from my Windows directories like I use to on my old dual-boot system.  Just restored all my user files from my old Dell laptop and was able to recompile my programs with the 64-bit compiler.  I finally feel like I've been re-integrated into the real world again!


But as for all good things, there is a catch:  VMware Workstation 6 costs real money, $189 of it.  But since I need it for work, I was able to get my boss to pay for it:)



Actually, I am not sure now if it is linux that is managing the touch screen or Windows.  (Don't see anything related to touch in xorg.conf.)  But the bottom line is that it works inside the Debian virtual machine now.

---

### Post by WHO8 on 2007-08-07
i_like_debian and everyone else here:

Thanks big-time for the help! I was starting to get really frustrated trying to get Ubuntu up and running at all on my tx1127cl until I found this forum -- you guys rock. 

i_like_debian, everything in your compilation worked like a charm for me except now, for some reason, I don't have WiFi anymore. At first I could connect, then it was more difficult to connect, and now I can't connect at all and I really have no idea where to start.

Nothing wrong on the router end, it's definitely with the setup on this particular box (dual-boot w/Windoze). If it makes a difference, I'm using WPA  and unlike the other two boxes I have set up with Feisty, the keyring isn't asking for a PW to logon to the network... Can you give a noob a few ideas to begin chasing down, please?

---

### Post by i_like_debian on 2007-08-07
> **WHO8 said:**
> i_like_debian and everyone else here:

Thanks big-time for the help! I was starting to get really frustrated trying to get Ubuntu up and running at all on my tx1127cl until I found this forum -- you guys rock. 

i_like_debian, everything in your compilation worked like a charm for me except now, for some reason, I don't have WiFi anymore. At first I could connect, then it was more difficult to connect, and now I can't connect at all and I really have no idea where to start.

Nothing wrong on the router end, it's definitely with the setup on this particular box (dual-boot w/Windoze). If it makes a difference, I'm using WPA  and unlike the other two boxes I have set up with Feisty, the keyring isn't asking for a PW to logon to the network... Can you give a noob a few ideas to begin chasing down, please?


Are you running Ubuntu inside a virtual machine?  Or are you booting Ubuntu from a partition on your drive?

If you are running VMware and Ubuntu as a virtual machine, then you don't need to set up any wifi at all.  Inside the Ubuntu virtual machine you will have a network connection through your Windows.  As long as you are connected through Windows, your Ubuntu virtual machine will have a live connection to the net too.  No wifi setup needed.  (That is, connect to your wifi WPA in windows, fire up your Ubuntu virtual machine which should then have a net connection automatically.)

But if you are booting Ubuntu from disk, you should try to get your WEP working first.  If your wifi works with WEP as described in my post from last week, I imagine it should also work with WPA.  (I haven't tried  WPA, but some others on this thread have gotten WPA working.  You should consult their posts.)

Again, I have switched entirely to the virtual machine set up now.  I no longer have to boot Ubuntu from disk.

---

### Post by i_like_debian on 2007-08-07
> **WHO8 said:**
> i_like_debian and everyone else here:

Thanks big-time for the help! I was starting to get really frustrated trying to get Ubuntu up and running at all on my tx1127cl until I found this forum -- you guys rock. 

i_like_debian, everything in your compilation worked like a charm for me except now, for some reason, I don't have WiFi anymore. At first I could connect, then it was more difficult to connect, and now I can't connect at all and I really have no idea where to start.

Nothing wrong on the router end, it's definitely with the setup on this particular box (dual-boot w/Windoze). If it makes a difference, I'm using WPA  and unlike the other two boxes I have set up with Feisty, the keyring isn't asking for a PW to logon to the network... Can you give a noob a few ideas to begin chasing down, please?


Sorry, I didn't read your post carefully before I answered.  I guess you are booting Ubuntu from disk.  And you must be using ndiswrapper.


The first thing to do is to check that your wireless is in fact working.  This is best done in a terminal.

Open a terminal.  Type "sudo -s" and then "iwlist scan".  This will scan all the available wireless interfaces.  If all the entries say  "Interface doesn't support scanning", then your ndiswrapper isn't set up right (because your wireless interface isn't active).  Hopefully, this isn't your problem, because you said you had wifi working previously.  But if it is, you will want to go back and set up your ndiswrapper fresh, and reboot and try again.


If your scan returns a list of available wireless networks, then your wireless interface is working.  If you have one or more active wireless routers in the area, they should show up on the list.  If you examine each entry, you will see the name of the network, its encription protocol (none, WEP or WPA), the available bit rates and the signal quality.  (In fact, the wireless management modules in Gnome interpret the results of iwlist to give you info about the wireless environment.)  You should be able to see your router on this list.  Make sure that WPA is on and the signal quality is ok (i.e. not zero).  If your router is reachable according to iwlist scan, you should be able to connect, and the rest of the problem must be then related to how you set up the WPA or software.


If your router is indeed on the list, I would try to check it by first turning off all encription (i.e. no WPA or WEP).  This will allow you to check whether your laptop is talking to the router.  So turn off the encription on your router first and restart it.  Then on your laptop, do "iwonfig wlan0 essid=xxxx", where xxxx is the name of your wireless network (make sure you type it exactly the same way you saw it on the scan, and unfortunately no spaces allowed in the essid, so if you named it with spaces, you will have to rename it).  Then do "/etc/init.d/networking restart".  This should restart the networking and your wireless should be connected on DHCP.  Try to connect to some site on the net.



If this all works, then all the hardware is working and the rest is WPA config issues, which I can't help you with, since I don't use WPA.  Please consult the other posts on this thread.


Finally, in case you don't have a router under your control (i.e. you are at a Starbucks or something), then you obviously can't turn off their WPA.  But all of their routers also have a non-encripted channel.  In that case you an try "iwconfig wlan0 essid=any".  That will connect you to any router available without encription.

---

### Post by i_like_debian on 2007-08-07
> **i_like_debian said:**
> Sorry, I didn't read your post carefully before I answered.  I guess you are booting Ubuntu from disk.  And you must be using ndiswrapper.

...


Sorry, a typo in this post --  iwoncfg should have been iwconfig

---

### Post by isachan on 2007-08-11
I finally got my tx1000 last week, having fun playing with it.

Thanks to i_like-debian, by following his last installation instruction I got most of the stuff working gracefully except...

1. Wireless Connection :

It can see my wireless router and all the info comes up with "iwconfig", however, the progress bar on the network manager stops at 28%, and quietly stops.

I have looked at "dmesg", "/var/log/syslog", "/var/log/messages", and the results are as following :

dmesg
[192292.836000] wlan0: no IPv6 routers present

/var/log/syslog
[snip]
Aug 11 19:01:01 isao-tpc02 avahi-daemon[5237]: Registering new address record for fe80::21a:73ff:fe7b:7316 on wlan0.*.
Aug 11 19:01:10 isao-tpc02 kernel: [192292.836000] wlan0: no IPv6 routers present
[snip]

/var/log/messages
[snip]
Aug 11 18:58:55 isao-tpc02 kernel: [192157.720000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 11 18:58:56 isao-tpc02 kernel: [192158.688000] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 11 18:59:02 isao-tpc02 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
[snip]

I have no idea what to do at this point on. Do I have to change the driver for ndiswrapper ?

2. Suspend / Hibernate

The suspend works until after X reboots, but the screen is completely blank, not even the backlight doesn't come up. I can hear some sound effects after the desktop start-up. When I press the DVD button on the right side of the screen, the Amarok comes up and by pressing the play button on the side, I can hear the intro voice.

Another words, I think everything is working except X windows. Is something missing from suspend script to correctly reload the driver ? I'm using nv driver.  

Hibernation is not working nicely. For the very first time, I saw a few messages on the screen saying saving memory images to disk and after that, I never got to resume successfully. No screen, no reaction by pressing keyboard, touchpad, screen buttons, loud fan noise...

3. Touchscreen

I got it to work for a while at the first day, but after so many machine reboot, can't get it to work anymore. I'm using evtouch 0.8.6. Strangely, it was working out of calibration with wacom entries in xorg.conf. Initially eventX was set to event1, but doing "cat /proc/bus/input/devices" revealed eGalax is on event3.

I can live without 2 and 3, but I really need the wireless problem to be solved. Please help me !

Isao

---

### Post by i_like_debian on 2007-08-12
> **isachan said:**
> I finally got my tx1000 last week, having fun playing with it.

Thanks to i_like-debian, by following his last installation instruction I got most of the stuff working gracefully except...

1. Wireless Connection :

It can see my wireless router and all the info comes up with "iwconfig", however, the progress bar on the network manager stops at 28%, and quietly stops.

...

Isao


Please attach results from these three commands...

iwconfig
iwlist scan
cat /etc/network/interfaces

---

### Post by isachan on 2007-08-12
Here is iwconfig :
isao@isao-tpc02:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"isao"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:49:4C:54
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Here is iwlist scan :
isao@isao-tpc02:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:49:4C:54
                    ESSID:"isao"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

It's not protected for now, for the troubleshooting purpose.

cat /etc/network/interfaces :
isao@isao-tpc02:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid isao

Sorry after this posting, but after I tried changing the driver to SP34167, it's started working. However, it had affected suspend / hibernate, that it doesn't work anymore. I'll try changing back to R151517, to see if it had been a glitch caused by my pilot error.

---

I think web cam is almost working for me, because I see the LED light blinks with "streamer", "webcam", "camE" apps. Some kind of argument is set wrong right now, that I can't grab any images. I think I set my file permission correctly.

Here is the result when I tried with streamer app.

isao@isao-tpc02:~$ streamer -o test.ppm
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x0 [];^C - one moment please
;field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=unknown): Invalid argument

or for JPEG output

isao@isao-tpc02:~$ streamer -o test.jpeg
files / video: JPEG (JFIF) / audio: none
no way to get: 320x240 JPEG (JFIF)
movie writer initialisation failed

/dev/video0 is assigned for the webcam.

Someone in the list had success with web cam. How did you pull it out ? What settings and apps did you used ?

Isao

---

### Post by i_like_debian on 2007-08-12
> **isachan said:**
> Here is iwconfig :

...

auto wlan0
iface wlan0 inet dhcp
>>wireless-essid isao

...
Isao


Everything looks fine, except the line "wireless-essid isao" is not supposed to be in /etc/network/interface. You should remove that line.


Try the following (with WEP or WPA turned off on your router):

sudo -s
iwconfig essid=isao
/etc/init.d/networking stop
/etc/init.d/networking start

This will go thru all the networking interfaces listed in /etc/network/interface and try to start them one by one.  Some of them can't be started because there is no interface attached to it (eth1, eth2, ath0) and they will say something like "dhcp can't be started, going to sleep" or something similar.  But wlan0 should come up saying something like "obtaining dhcp lease ..." and when it is successful, wlan0 will be bound to a particular IP address such as 192.168.xxx.xxx (where xxx are numbers based on how the dhcp on your router is set up).  You should be able to at least ping your router.


Try this and see if it works on your machine first.

---

### Post by Shaydog on 2007-08-12
Matth45, thank you for your tutorial on how to map the rotate button to a rotate command script.  I am a real newbie with Linux, and I was wondering how you mapped the XF86LaunchF command to Beryl's command0, and then I'm also wondering how you could specify the command0 to run a script.

How would we map a script to a specific command name?

Thanks!

---

### Post by Shaydog on 2007-08-12
Never mind, I was able to get this one myself :)

For everyone's future reference, after you assign a symkey as mentioned above, you can then open up Beryl, and under the shortcuts section, just map that key to command0.

The next thing you must do is create a script file, place it somewhere (possibly your home directory), and then in Beryl Settings Manager, in the General Options -> Commands area, just place the full path of that file in for command0.

---

### Post by WHO8 on 2007-08-14
> **i_like_debian said:**
> Sorry, I didn't read your post carefully before I answered.  I guess you are booting Ubuntu from disk.  And you must be using ndiswrapper.


The first thing to do is to check that your wireless is in fact working.  This is best done in a terminal.

Open a terminal.  Type "sudo -s" and then "iwlist scan".  This will scan all the available wireless interfaces.  If all the entries say  "Interface doesn't support scanning", then your ndiswrapper isn't set up right (because your wireless interface isn't active).  Hopefully, this isn't your problem, because you said you had wifi working previously.  But if it is, you will want to go back and set up your ndiswrapper fresh, and reboot and try again.


If your scan returns a list of available wireless networks, then your wireless interface is working.  If you have one or more active wireless routers in the area, they should show up on the list.  If you examine each entry, you will see the name of the network, its encription protocol (none, WEP or WPA), the available bit rates and the signal quality.  (In fact, the wireless management modules in Gnome interpret the results of iwlist to give you info about the wireless environment.)  You should be able to see your router on this list.  Make sure that WPA is on and the signal quality is ok (i.e. not zero).  If your router is reachable according to iwlist scan, you should be able to connect, and the rest of the problem must be then related to how you set up the WPA or software.


If your router is indeed on the list, I would try to check it by first turning off all encription (i.e. no WPA or WEP).  This will allow you to check whether your laptop is talking to the router.  So turn off the encription on your router first and restart it.  Then on your laptop, do "iwonfig wlan0 essid=xxxx", where xxxx is the name of your wireless network (make sure you type it exactly the same way you saw it on the scan, and unfortunately no spaces allowed in the essid, so if you named it with spaces, you will have to rename it).  Then do "/etc/init.d/networking restart".  This should restart the networking and your wireless should be connected on DHCP.  Try to connect to some site on the net.



If this all works, then all the hardware is working and the rest is WPA config issues, which I can't help you with, since I don't use WPA.  Please consult the other posts on this thread.


Finally, in case you don't have a router under your control (i.e. you are at a Starbucks or something), then you obviously can't turn off their WPA.  But all of their routers also have a non-encripted channel.  In that case you an try "iwconfig wlan0 essid=any".  That will connect you to any router available without encription.


i_like_debian:

Thanks for the reply and suggestions. WiFi just "started working" again one day after I booted into Ubuntu from a windows session. I -suspect- my problem had to do with ACPI: I had the WLAN off in a windoze session and hibernated and booted into Ubuntu. This was when I was having issues. I haven't had this issue any more (haven't had the WiFi off in windoze during hibernation, and I haven't tried to repeat the problem).

LOL -- after this problem was "resolved" I ran into another. fsck began insisting on doing a force check on boot-up -- which failed (hung my machine) every time before completion. Booting with a gparted live-cd and checking the drive that way took care of that but still... I have no prob with the force check for consistency but after looking around it seems that our little TX1000 series isn't the only one that hangs on this operation.

The virtual machine is sounding really good though... I haven't tried this route yet. How much of a performance hit do you see?

Thanks very much

---

### Post by isachan on 2007-08-15
Thanks, i_like_debian. The original driver from R151517.exe package is working now. Only thing I had to skip was "ndiswrapper -m". Is this absolutely necessary ? With it, I couldn't get it to work. I deleted the line "wireless-essid isao" in /etc/network/interface, and feels a bit speedier on the page loading.

My suspend-to-ram came back to the way it was before. Complete recovery with a totally blank screen. I think it's a progress because I think I'm almost there. This is with uswsusp with "sudo s2ram -f" command.

My BIOS version is 1.8F, and now that I see the firmware upgrade on the HP support page, you'll see what I mean after the BIOS upgrade.

Isao

---

### Post by i_like_debian on 2007-08-16
> **WHO8 said:**
> i_like_debian:

Thanks for the reply and suggestions. WiFi just "started working" again one day after I booted into Ubuntu from a windows session. I -suspect- my problem had to do with ACPI: I had the WLAN off in a windoze session and hibernated and booted into Ubuntu. This was when I was having issues. I haven't had this issue any more (haven't had the WiFi off in windoze during hibernation, and I haven't tried to repeat the problem).

LOL -- after this problem was "resolved" I ran into another. fsck began insisting on doing a force check on boot-up -- which failed (hung my machine) every time before completion. Booting with a gparted live-cd and checking the drive that way took care of that but still... I have no prob with the force check for consistency but after looking around it seems that our little TX1000 series isn't the only one that hangs on this operation.

The virtual machine is sounding really good though... I haven't tried this route yet. How much of a performance hit do you see?

Thanks very much



Glad to hear the wifi is working again.


If the boot process forces fsck, there is very likely something wrong with your file system (may be you powered off the machine without properly unmounting the file system previously).  If you don't fix this, it will insist on fsck every time.  I suggest booting into recovery (aka single-user) mode and running fshk manually to resolve any file system inconsistency.  (It goes without saying, one should NEVER run fsch with the filesystem mounted.)  My machine usually goes through fsck with no problem.


Regarding the virtual machine. since VMware is not just emulating linux in windows (unlike cygwin), the performance is not bad.  But you will take a hit for sure, though I don't have any firm numbers.  I am running Amd64 Debian Etch inside the virtual machine, and I seem to be getting about 80% of the clock speed running an old code I recomplied using the 64-bit Intel compiler.

Since I switched over to running linux inside the virtual machine, I don't have any hardware issues anymore.  If your linux performance is not critical, I would definitely go that route.  And be sure to install the 64-bit linux in your virtual machine, it seems to run faster (may be it's just psychological).

---

### Post by i_like_debian on 2007-08-16
> **isachan said:**
> Thanks, i_like_debian. The original driver from R151517.exe package is working now. Only thing I had to skip was "ndiswrapper -m". Is this absolutely necessary ? With it, I couldn't get it to work. I deleted the line "wireless-essid isao" in /etc/network/interface, and feels a bit speedier on the page loading.

My suspend-to-ram came back to the way it was before. Complete recovery with a totally blank screen. I think it's a progress because I think I'm almost there. This is with uswsusp with "sudo s2ram -f" command.

My BIOS version is 1.8F, and now that I see the firmware upgrade on the HP support page, you'll see what I mean after the BIOS upgrade.

Isao


'ndiswrapper -m' checks to make sure that the microcode from the windows driver for the wifi card is inserted correctly (I think I just reads the data written to /etc/ndiswrapper by 'ndiswrapper -i' and make a report).  It isn't necessary but shouldn't break anything either.  But if it works without 'ndiswrapper -m', I won't worry.  The good thing is once ndiswrapper is set up, you will never need to do 'ndiswrapper -i' or '-m' ever again.  So if it works, just leave it.


About suspend,  's2ram' definitely does not work.  You can forget about it.  The more useful function is suspend to disk (aka hibernatino).  That works for me.  Give that a try.

---

### Post by isachan on 2007-08-16
Turned out the line "wireless-essid isao" in /etc/network/interface was added by the network manager. It is acting funny that the icon in the tray doesn't change correctly after a successful wireless connection.

As far as the hibernation goes, I think something happened to my swap partition when I first tried to hibernate. The very first time, it succeeded to save the snapshot image, then it failed to resume. After that it doesn't let me hibernate anymore. Comes back with messages like "suspend: Invalid snapshot device" or  "suspend: Could not stat the resume device file". I checked /etc/uswsusp.conf, and it looks good. Let me post it here :

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
resume device = /dev/sda3
compress = y
early writeout = y
image size = 916218019
RSA key file = /etc/uswsusp.key
shutdown method = platform
snapshot device = /dev/sda3

I partitioned a plenty 8GB (!) for my swap space.
Is there a way to reset my swap partition ?

Isao

---

### Post by i_like_debian on 2007-08-16
> **isachan said:**
> Turned out the line "wireless-essid isao" in /etc/network/interface was added by the network manager. It is acting funny that the icon in the tray doesn't change correctly after a successful wireless connection.

As far as the hibernation goes, I think something happened to my swap partition when I first tried to hibernate. The very first time, it succeeded to save the snapshot image, then it failed to resume. After that it doesn't let me hibernate anymore. Comes back with messages like "suspend: Invalid snapshot device" or  "suspend: Could not stat the resume device file". I checked /etc/uswsusp.conf, and it looks good. Let me post it here :

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
resume device = /dev/sda3
compress = y
early writeout = y
image size = 916218019
RSA key file = /etc/uswsusp.key
shutdown method = platform
snapshot device = /dev/sda3

I partitioned a plenty 8GB (!) for my swap space.
Is there a way to reset my swap partition ?

Isao


I don't think you can mess up your swap partition too badly (it gets overwritten repeatedly anyway) and I don't see anything wrong with your conf file either.  Of course, you want to make sure that sda3 is in fact the correct swap partition.  Also a 8-GB swap is way too large.  I think < 1 GB is best (assuming you have 2 GB of RAM).  If you want to resize your partitiion(s), do it with the gparted CD and with caution (unless you don't mind losing your data).

(There is also a way to resize the swap on the fly.  But gpated has a easy user-friendly interface.)

---

### Post by isachan on 2007-08-16
Aarrgghh. Wasted half a day trying to make it work. Tried Gparted to reformat the swap partition but no avail. Tried "dpkg-reconfigure uswsusp", it didn't work.

Funny thing is s2ram is more of a reality than s2disk for me. I looked around this forum and seems like the backlight is the only thing doesn't come up on the resume from RAM. But of course, with no avail.

I'm almost giving up.

Isao

---

### Post by i_like_debian on 2007-08-16
> **isachan said:**
> Aarrgghh. Wasted half a day trying to make it work. Tried Gparted to reformat the swap partition but no avail. Tried "dpkg-reconfigure uswsusp", it didn't work.

Funny thing is s2ram is more of a reality than s2disk for me. I looked around this forum and seems like the backlight is the only thing doesn't come up on the resume from RAM. But of course, with no avail.

I'm almost giving up.

Isao


I can understand.  It took me a week to get the most basic things working on my tx1000.  (And the tx100 isn't bad.  It took me more than two weeks to get my last laptop working.)

Again, have you considered running linux as a virtual machine in windows?  This would be the easiest way to get all the hardware working under linux.

---

### Post by isachan on 2007-08-16
VMWear would be nice but I bought this machine to convert to sole linux machine. I have really old tablet pc Toshiba M205, and that too is running on Kubuntu LiveCD almost all the time. I became so tired of M$ at this point. I guess I have to wait till 7.10 comes out and see how it does things on my machine.

Well, overall not too bad for a portable linux tablet. I'm loving it.

Things that are working so far:
Wireless (b/g)
Touchscreen (Calibration is tough)
Bluetooth OBEX stuff
Hardware buttons (Sound volume buttons, DVD button and playback control buttons)
Flash memory card slot (tried Memory Stick Pro, MMC Plus)
Remote
Microphones on the screen
External Line-In
Webcam (See my next post)

Things that are ALMOST working:
Suspend to ram

Things haven't tried
Fingerprint reader
Any Express card stuff
Internal Modem
External VGA / S-Video
SPDIF

Thing just doesn't work:
Headphone jack
Hibernate (for me)

Isao

---

### Post by isachan on 2007-08-16
A miracle just happened ! Webcam works !

Go to this site and download a "luvcview" i386 .deb package :
[http://packages.debian.org/unstable/x11/luvcview](http://packages.debian.org/unstable/x11/luvcview)

Right click on the .deb icon and select Kubuntu package menu -> Install Package. It will complain about libc6 toward the end of installation, but ignore it. The luvcview will be installed anyway.

Type the following from a command line :
"luvcview -d /dev/video0 -f yuv -s 640x480" ( I tested til 1280x1024)

Voila ! I get 7 fps of speed out of this. Most of the image manipulating button at the bottom of the window doesn't work though.

Ref:
[https://lists.berlios.de/pipermail/linux-uvc-devel/2006-December/001084.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2006-December/001084.html)
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

First time I made anything work on linux !

Isao

UPDATE:

Now Ekiga from Ubuntu repository works nicely with the following plug in
"sudo apt-get install ekiga libpt-plugins-v4l2"

Ignore many warning / error dialog boxes to get to the video device setting. Choose V4L2, USB Camera 2.0, and NTSC.
However, the audio for Ekiga is not working. I'll investigate some more.

Refs:
[http://openfacts.berlios.de/index-en.phtml?title=HowTo_install_Ekiga_to_Ubuntu](http://openfacts.berlios.de/index-en.phtml?title=HowTo_install_Ekiga_to_Ubuntu)
[http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC](http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC)

Isao

---

### Post by thorMX on 2007-08-17
Hey all, somewhat of a noob here, but I still can't get wifi on my tx1000. I got NDIS up and running and it says I have the hardware present, however when I run iwconfig I just get lo and eth0. There is no other network device showing up. I've got the broadcom b/g/draft-n card and I'm wondering if thats whats causing the problem. I've read this whole thread (and love all the info - got video, audio, touchscreen... ) but I can't find any more steps for the wifi. Does anyone have any thoughts? Thanks!

(edit for spelling)

---

### Post by danesh on 2007-08-18
same issue here, been fighting with wireless for quite a long time now and nothing has worked, exactly the same bgn card

---

### Post by isachan on 2007-08-18
Well, basically if you look back to this discussion at page 10, you'll see i_like_debian posted how to make the wireless work. Let me post it here :

3. WIRELESS

- In a terminal issue the following command:

sudo -s
rmmod bcm43xx
echo 'blacklist bcm43xx' >> /etc/modprobe.d/blacklist
apt-get update
apt-get install ndiswrapper-common
apt-get install ndiswrapper-source
apt-get install ndiswrapper-utils-1.9
module-assistant prepare
module-assistant build ndiswrapper
wget [http://ftp.us.dell.com/network/R151517.EXE](http://ftp.us.dell.com/network/R151517.EXE)
unzip -a R151517.EXE
cd DRIVER
ndiswrapper -i bcmwl5.inf
ndiswrapper -m
modprobe ndiswrapper
exit

- To check that the wireless is working, do "iwconfig". You should see a line
with "wlan0 ..." followed by information about the wireless environment.

- Use the Network Manager (button next to the volume at the top)
to configure your wireless access.

- References:
[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
[http://www.debian-administration.org/articles/401](http://www.debian-administration.org/articles/401) 

Try this one (maybe you have to look for your specific model of tx1000, mine is a custom order, so it's called CTO).

Look in here : 
[http://h20180.www2.hp.com/apps/Lookup?h_lang=en&h_cc=us&cc=us&h_page=hpcom&lang=en&h_client=S-A-R163-1&h_pagetype=s-001&h_query=Pavilion+tx1000&submit.x=6&submit.y=9](http://h20180.www2.hp.com/apps/Lookup?h_lang=en&h_cc=us&cc=us&h_page=hpcom&lang=en&h_client=S-A-R163-1&h_pagetype=s-001&h_query=Pavilion+tx1000&submit.x=6&submit.y=9) 

For the Windows Vista Driver for the wireless network as of June 2007, download from here :
[ftp://ftp.hp.com/pub/softpaq/sp36001-36500/sp36077.exe](ftp://ftp.hp.com/pub/softpaq/sp36001-36500/sp36077.exe)

Sometimes unzipping Windows executable with unzip dosn't work, but there is a handy utility called "cabextract" is already installed in 7.04. So you have to type in a terminal console like "cabextract sp36077.exe" and it will decompress the content. The rest of the steps are the same.

Isao

---

### Post by isachan on 2007-08-18
I got a partial success with suspend to ram. That's right, I said s2ram ! But with a caviats (as always !).

While a bunch of lsmod actions, I noticed the modules "sony_acpi" and "asus_acpi" are loaded. Especially, "asus_acpi" was tied to "backlight" module. since I was once a good programmer, then I thought that's gotta be it and blacklisted the asus_acpi and rebooted.

Verified there no asus_acpi in lsmod, and I did "sudo s2ram -f". (I don't know why I have to force it.) Everything went dark and the power button and lights started to flash as usual. A little prayer and turned it on again, and lo and behold, the backlight ! Looks more brighter than usual when you're emotional. And within 3 seconds, I was back in business. I was happy until I discovered about the CAVIATS !

I noticed ONLY ONE CPU had been resumed ! Argh ! I have to re-associate my ESSID from console ! Argh ! Internet connection is really slow at first and comes back normal, but after about 15minutes when I type in new URL and hit enter, it doesn't respond ! Also, the screen doesn't get turned off after some time anymore. I have to reboot to bring back those features. Argh !

Anybody knows what's causing it or how to fix / debug these problems ?

BTW, I think the reason my machine can't do s2disk is that my swap partition is encrypted. I see 
some message lines when I boot, something like :

Loading, please wait...
resume : libcrypt version 1.2.3.
resume : Could not read the image.

Anybody knows how to clear / flush the encryption on the swap ?

Isao

---

### Post by jolan_jj on 2007-08-19
I just discovered a funny thing... I replaced rhythmbox with amarok as a default player. Så I played with it to try uot the remote control and I pushed the on/off button on the remote. The screen goes black and it looks like the system goes over to suspended mode. All the lights go out except the on/off led which lights blue. The system wakes up and demands a password, I type it and everything goes fine... Is this this kind of suspend you were talking about?

*Edit:* OK, it wasn't that good. It worked until I closed the lid. Then when I open it it looks like the system wolud get up but it doesn't... Well, at least it works with the lid open :)

---

### Post by pauharo on 2007-08-21
First of all, I want to thank everybody who has been posting in this thread. Thanks to them I have Debian (due to its similarity to Ubuntu) running on my HP tx1151ea.

I am collecting all the information on configuring this laptop in GNU/Linux and preparing a web page on it, for new owners to have a place where they can easily find the solutions to the problems with this laptop.

You can find it in: [http://www.tx1151ea.tk/]("http://www.tx1151ea.tk/")

It is based on the model I own and using Debian, but most of the information should apply to Ubuntu users, as I've used some of the posts of this thread to solve my problems.

I will be thankful for any comment or correction or extra information. You can email me at pauharo @ gmail . com

Thanks again to everyone who has contributed!

---

### Post by Cuppa-Chino on 2007-08-23
> 
[QUOTE]Quote:
Originally Posted by matth45 View Post
So, if you don't see a xkeysym from xev, check dmesg. You should see something like:
Code:

```
atkbd.c: Unknown key pressed (translated set 2, code 0x?? on isa0060/serio0).
atkbd.c: Use 'setkeycodes e00e <keycode>' to make it known.
```

We have to find an unused keycode to map the DVD button to.
I do not see anything with atkbd.c this with this command:
Code:

```
dmesg
```

is the line of code missing something ?[/QUOTE]

I am still struggling to assign the rotate key to the little key on the screen.

what keyboard layout have people selected?

any other tips, I still do not get any output from either xev or dmesg

can anyone give me any pointers how to solve this, thanks

---

### Post by matth45 on 2007-08-23
Headphone jacks are working!

I just downloaded the latest alsa development snapshot ([ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/alsa-driver-hg20070824.tar.bz2](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/alsa-driver-hg20070824.tar.bz2)) and they now have a HP TX 1000 model for the ALC861VD/660VD chip!
> 
        ALC861VD/660VD
          3stack        3-jack
          3stack-dig    3-jack with SPDIF OUT
          6stack-dig    6-jack with SPDIF OUT
          3stack-660    3-jack (for ALC660VD)
          3stack-660-digout 3-jack with SPDIF OUT (for ALC660VD)
          lenovo        Lenovo 3000 C200
          dallas        Dallas laptops
          hp            HP TX1000
          auto          auto-config reading BIOS (default)

I built and installed this on my system, and the headphone jacks both work (once you unmute them)!  The mute light turns off when I unmute the headphones too. But it strangely turns back on under some circumstances. This doesn't seem to affect the audio at all though.

**REMEMBER if you have added another model to the snd-hda-intel module in the /etc/modprobe.conf file, you must delete it and re-insert the snd-hda-intel module before the audio will work.

I don't know what else to say about the buttons on the monitor. I'll give it some thought though.

You may also want to check this out, if you're trying to get the touchscreen working with 64-bit:
[http://www.fedoraforum.org/forum/showthread.php?t=161866](http://www.fedoraforum.org/forum/showthread.php?t=161866)

---

### Post by farbird on 2007-08-23
u just revived my love for the tx1000...

now i can watch porn without disturbing my wife or colleagues..!!!

---

### Post by farbird on 2007-08-24
I'd built it but the headphone jack still arent working for my tx1000

in my modprobe line..

it says

options snd-hda-intel index=0 model=hp

i tried to remove model=hp..

also didnt work..

maybe u'd wanna show us your line..


> **matth45 said:**
> Headphone jacks are working!

I just downloaded the latest alsa development snapshot ([ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/alsa-driver-hg20070824.tar.bz2](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/alsa-driver-hg20070824.tar.bz2)) and they now have a HP TX 1000 model for the ALC861VD/660VD chip!


I built and installed this on my system, and the headphone jacks both work (once you unmute them)!  The mute light turns off when I unmute the headphones too. But it strangely turns back on under some circumstances. This doesn't seem to affect the audio at all though.

**REMEMBER if you have added another model to the snd-hda-intel module in the /etc/modprobe.conf file, you must delete it and re-insert the snd-hda-intel module before the audio will work.

I don't know what else to say about the buttons on the monitor. I'll give it some thought though.

You may also want to check this out, if you're trying to get the touchscreen working with 64-bit:
[http://www.fedoraforum.org/forum/showthread.php?t=161866](http://www.fedoraforum.org/forum/showthread.php?t=161866)

---

### Post by farbird on 2007-08-24
it worked..

needed to restart system..


mine was done in /etc/modprobe.d/alsa-base

the line to edit was 

options snd-hda-intel index=0 model=hp

if u do not have this line..

append it to the end of the file

---

### Post by matth45 on 2007-08-24
Yeah... I'm actually running Fedora (I mentioned that a couple posts back) so there may be some things that are different on my distro.  Anyway, you shouldn't need the model=hp argument. Mine works with no arguments, since ALSA will auto detect the chip if it knows about it.

My understanding was that we needed the model before because none of the models ALSA knew about actually matched our hardware, so ALSA just took a "random" guess.

Give it a try without specifying any model at all.

---

### Post by Sollen on 2007-08-25
EDIT: Ok, I installed Ubuntu instead, added the noapic kernel options and booted, but x-server won't start up (no screen found), and when I'm booting, I get something about BIOS error 81.

---

### Post by jjordan on 2007-08-26
math45,

Thanks for the info on sound, got the headphone jacks working, the two on the front work, the one on the quickdock does not.  Haven't tried the digital out yet.  

Has anyone gotten a microphone working with Skype?  I know the mic is working because I can hear it through the speakers but I can't pass any audio to Skype.

Searched everthing I can think of, but haven't found anything.

I'm using Kubuntu Fiesty on a tx1220us.

Thanks, -j

---

### Post by Sollen on 2007-08-27
> **matth45 said:**
> Headphone jacks are working!

I just downloaded the latest alsa development snapshot ([ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/alsa-driver-hg20070824.tar.bz2](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/alsa-driver-hg20070824.tar.bz2)) and they now have a HP TX 1000 model for the ALC861VD/660VD chip!


I built and installed this on my system, and the headphone jacks both work (once you unmute them)!  The mute light turns off when I unmute the headphones too. But it strangely turns back on under some circumstances. This doesn't seem to affect the audio at all though.

**REMEMBER if you have added another model to the snd-hda-intel module in the /etc/modprobe.conf file, you must delete it and re-insert the snd-hda-intel module before the audio will work.

I don't know what else to say about the buttons on the monitor. I'll give it some thought though.

You may also want to check this out, if you're trying to get the touchscreen working with 64-bit:
[http://www.fedoraforum.org/forum/showthread.php?t=161866](http://www.fedoraforum.org/forum/showthread.php?t=161866)

Err...How do I build it? When I try 'make' MAH 'PUTER just says I need to run the configuration scripts first, but I don't know how to do that.
/r/ help.
Found out, but GCC won't create an executable for me.

Lol, I built it, and I have rebooted, but I still get no sound?
Why is this? Doesn't it work for tx1020ea?

---

### Post by Sollen on 2007-08-27
Do I have to edit the modprobe.d stuff?

---

### Post by Cuppa-Chino on 2007-08-27
> **Sollen said:**
> Do I have to edit the modprobe.d stuff?

to be edited as in the very first post in thread:

Next comes audio. Seems it had some trouble because of the Jack sensing on the front jacks...

Try adding this to /etc/modprobe.d/alsa-base

**options snd-hda-intel model=hp**

I am wondering about the microphones at the moment, I think a mic boost switch is missing or something, I can get mic recorder to show minimum change when I speak into the mic but not enough to record anything...

---

### Post by farbird on 2007-08-27
u need to do

sudo -s
./configure
make
make install

in the folder that u'd extracted the alsa drivers

---

### Post by Sollen on 2007-08-28
How do I install the drivers? ._.
Do I only have to compile it?

---

### Post by jjordan on 2007-08-28
The last step farbird listed "make install" actually does the installation.  I would recommend using "checkinstall" instead as it will keep .deb database updated.

You can install Checkinstall with Apt-get, or Synaptic or  Adept.

Once it is installed type sudo checkinstall instead of sudo make install as the last step.  Checkinstall will ask if it can create a documentation directory, just press enter and then ask for a description.  Press enter on a blank line to exit the description editor and then press enter again.  Checkinstall will create and install a .deb which you can then share with your friends.  Best of all, it does not break your package manager.

One last point make sure you have exited Synaptic or Adept before running checkinstall or you will have to install the .deb manually.

-j

---

### Post by Sollen on 2007-08-29
I installed it, lol.
It worked for a while, but after 2-3 boots it just stopped working.
(I installed beryl too, and I had to pull the plug of the computer)
Why is this?

---

### Post by Walter Nebisher on 2007-08-30
Hi all

first of all many thanks to the people of this thread. I got a great help from reading this.

Im running ubuntu feisty all upgraded to the last version of everything

I read the whole thread many times and I got some more questions:

-sometimes the mouse pointer is terribly slow when used with the touchscreen, and moves correctly if moved with the touchpad.  Does anybody know why this happens?

-the touchscreen is quite unusable. I can't get it calibrated. if I touch the display in a place the pointer appears away.. if I drag the pointer under my finger with the touchpad it goes better.. but when I tap in another place the problem araises ... moreover the pointer when moved by the touchscreen seems to gain some kind of acceleration, even if in the mouse settings the acceleration is set at the minimum. Can you spot out some more hint?

-the jack for earpieces simply doesn't work, I can't hear nothing and the hp is still using speakers.

-with the notebook keys for controlling volume I control the mic sensitivity and enable/disable the mic (I think this is a gnome trick, I swear): this feature works in your setup?

-the display rotation simply doesn't work, is there some trick to apply with xrandr or it's such a "standard" feature of xorg and I made some silly mistake? (I don't use neither beryl nor compiz now)

finally, do you use the nv driver or nvidia driver for xorg? what's the best driver?

many thanks to all of you.

---

### Post by Sollen on 2007-08-31
Has anyone tried installing OpenSuse?
According to some friends it should work almost flawlessly.

---

### Post by Shaydog on 2007-09-01
Hey guys, just wanted to bring up the standby/hibernate issue once more.  I was wondering if anyone has had any luck with either of these?  Particularly if they're using Beryl?

---

### Post by guttersnipe on 2007-09-01
first of all, I love you matth45

I ran some updates to ubuntu recently, and when I rebooted (as it requested I do so), my mute button was curiously blue, and my audio stopped working in entirety.  I first came to this thread to see if there have been any similar issues when I read matth45's fix for the headphone jack.

The link was broken, so I went to [ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/](ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/) and instead obtained the alsa-driver-hg20070828.tar.bz2 file.  It worked flawlessly.  Here's what I did to install
```

$ wget ftp://ftp.suse.com/pub/projects/alsa/snapshot/driver/alsa-driver-hg20070828.tar.bz2
$ tar xjf alsa-driver-hg20070828.tar.bz2
$ cd alsa-driver-hg20070828
$ ./configure
$ make
$ sudo make install

```
Now, if you've fooled with alsa before and you've added the "options..." line (ie options snd-hda-intel model=3stack) to /etc/modprobe.d/alsa-base file, then you need to delete it before continuing.  If you have no idea what I'm talking about, then don't worry about it.
```

$ sudo nano /etc/modprobe.d/alsa-base

```
Now, hit page down till you've reached the bottom of the file, and append this new line as the last line of the file.
```

options snd-hda-intel model=hp

```
Press CTRL+O <enter> to save.  Reboot the computer, and you'll have sound from the speakers and the headphone jack(s).

I have a tx1000z with two headphone jacks--both work flawlessly.  Sound coming from the speakers is muted as soon as I plug in the headphones.  Here's my only (minor) complaints.

The volume buttons work, but the mute button always stays blue.  It is SUPPOSED to turn orange/red when it is muted, but it stays blue after it toggles the muting.

The volume buttons do not act on the master volume.  The volume up, volume down, and mute buttons affect the "Front" only.  The "Font" affects the built-in speakers under the monitor.  This means that when I have my headphones plugged in, I can change the volume of "Front" with the volume buttons, but I cannot change the sound coming to the headphones with the volume buttons.

---

### Post by danielbr on 2007-09-01
Hi guys,

First of all thank you very much for the informations posted here. This topic is a marvelous example of the linux comunity spirit.

Does anybody have any problem with the disk checking (fsck) ? My notebook has been trying to check the disk for almost 20 times now and it freezes at randon percentages (the farest I've got was 61%). 
Since it neve gets complete I can't go thru my sistem, everytime I reboot I get the checking again, it freezes and I have to shutdown manually.

This is driving me crazy :twisted:

Thank you all

Dan

---

### Post by jjordan on 2007-09-03
Got Skype working:

Install Alsa-oss, the one from repos will work.

-j

---

### Post by guttersnipe on 2007-09-04
Every time I watch a movie on a TV (using my laptop as the DVD player), I loose my touchscreen calibration settings :-/

I was watching a move on my tx1000z laptop the other day, so I hooked it up to a TV.  I needed to hook it up via SVIDEO or VGA.  Because I was watching a movie, I wanted to be able to fullscreen to just the "right monitor" (the tv).  In order to do this, I could not use twinview.  So, I did a `sudo nvidia-settings` > X Server Display Configuration > Detect Displays > Click on TV screen > Configure... > Separate X screen (as opposed to TwinView) > OK > Save to X Configuration File > Restart X.

It was that second to last step (Save to X Configuration File) that screwed me up.  Unfortunately, this is the only way (to my knowledge at least) to have nvidia-settings create a separate X screen out of the second monitor.  By doing this, however, nvidia-settings removed my calibration settings >:O

Does anyone know any clever work-arounds so that I can watch a movie on my big screen every other night without it interrupting my touchscreen calibration?

I thought of creating a good xorg.conf.backup file and having it overwrite the xorg.conf file at bootup, but this seems like too much of a hack.

Anyone else have this problem? Any ideas?

[EDIT]
I also lost the ability to scroll with the right part of the touchpad :(

[EDIT2]
I've found that if you shut down the computer, plug in the VGA cable, and turn on the computer, it auto-detects the secondary screen.  It will disable your laptop screen, and only run from the secondary screen (whatever is connected to the vga port [ie your tv]).  This is how I got around my problem.

---

### Post by phenolholic on 2007-09-06
hello, i'm having problems with my touchscreen. namely, i installed feisty and it worked fine. i used the Section "InputDevice" that someone posted earlier on this thread. i was very happy. my only flaw with that setup was i couldnt get compiz to work, and had to resort to beryl. and in beryl, i couldnt get the windows decorator working (neither with gtk or emerald). i then decided to upgrade to gutsy. after the upgrade, i found my touchscreen was responsive, but not working. what that means is if i touched anywhere on the screen, it  positioned the cursor to the center of the screen, despite where i touched. fiddling around with the settings, i'm now on a machine with no touchscreen at all and still no compiz/beryl (window decorator). any information would be appreciated. thanks

---

### Post by jcase008 on 2007-09-07
I managed to get the touchscreen (mostly) working on my TX1000Z without using the evtouch drivers.  I was having problems with it crashing X when I remembered evtest.  It turns out that the kernel reports all the events properly, and the evdev driver in X will work to register those as mouse movements.  The only problem at the moment is a border of about 10 pixels around the edge where I can't tap.

[QUOTE=xorg.conf]
...
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
#       Option          "Device"                "/dev/input/mice"
        Option          "Device"                "/dev/input/mouse0"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
#       Option          "Device"                "/dev/psaux"
        Option          "Device"                "/dev/input/mouse2"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
    Driver "evdev"
    Identifier "touchscreen"
    Option "Device" "/dev/input/event2"
    Option "DeviceName" "touchscreen"
    Option "MinX" "95"
    Option "MinY" "3977"
    Option "MaxX" "3975"
    Option "MaxY" "120"
    Option "ReportingMode" "Raw"
#    Option "Emulate3Buttons"
#    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents"
EndSection

...

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
  InputDevice "touchscreen" 
  InputDevice "dummy"
EndSection
[/QUOTE]

I'm working on getting the ACPI events for the lid flip, fn-F4, fn-F7 and fn-F8 to work.  Compiling the kernel with ACPI debug messages gives these ns_print_pathname.  Some of the messages arrive twice, and there may be some noise from the rest of the system:

Lid Flip:
[list=1]
[*]_SB_.WMID.Z010
[*]_SB_.WMID.Z011
[*]_SB_.WMID.Z011
[*]_SB_.WMID
[*]_SB_.WMID
[*]TLDP (I  think this is the actual lid flip button)
[*]TLDP
[/list]
This same sequence repeats when rotating back.

fn-F4:
[list=1]
[*]_SB_.PCI0.UVGA.LCDA
[*]_SB_.PCI0.UVGA.TVAF
[*]_SB_.PCI0.UVGA
[*]_SB_.PCI0.UVGA.SWIT
[*]_SB_.PCI0.UVGA.SWIT
[/list]

fn-F7 and fn-F8 are much more complicated, I haven't figured them out yet.

---

### Post by ovalenzu on 2007-09-07
hi i have a tx1110 it's very similar to tx1120
when i installed the new driver from alsa for the headphone the front mic don't work any more.
the big problem it's with the cpu frequency scaling, when i work with battery the cpu don't work more than 800 mhz, how i can fix this ???

---

### Post by phenolholic on 2007-09-08
hello. i have a problem with my touchscreen. it responds, but it doesnt work like it should. when i touch my touchscreen, it automatically positions the cursor to the center of the screen, and not where i touch. obviously, its responding to my touch, but not the correct way. my touchscreen is an eGalax touchscreen that comes with HP Pavilion TX1000 model notebooks. i linked evtouch_event in /dev/input with whichever event the touchscreen loads up on. my xorg entry for the touchscreen device is:
Section "InputDevice"
Identifier "touchscreen"
Driver "evtouch"
Option "Device" "/dev/input/evtouch_event"
Option "DeviceName" "touchscreen"
Option "MinX" "48"
Option "MinY" "110"
Option "MaxX" "4006"
Option "MaxY" "4002"
Option "x0" "-1"
Option "y0" "-3"
Option "x1" "-6"
Option "y1" "-4"
Option "x2" "-2"
Option "y2" "-6"
Option "x3" "-2"
Option "y3" "-3"
Option "x4" "-4"
Option "y4" "-3"
Option "x5" "2"
Option "y5" "-1"
Option "x6" "-5"
Option "y6" "-3"
Option "x7" "-2"
Option "y7" "1"
Option "x8" "5"
Option "y8" "2"
Option "TapTimer" "0"
Option "LongTouchTimer" "250"
Option "ReportingMode" "Raw"
Option "SendCoreEvents" "On"
EndSection


i also put the following in Section "ServerLayout"
InputDevice "touchscreen" "CorePointer"

any info would be appreciated. thanks

---

### Post by simplyw00x on 2007-09-09
My testing report for the tx1000 (tx1020ea to be exact) is [https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1020ea](https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1020ea)

It includes instructions on how to get the jack sensing working. 

Remaining problems:
**Graphics card fan never turns on**
**Lid flip generates no ACPI events**
**Some buttons generate no showkey/xev events**
**Fingerprint reader does nothing**

To calibrate the touchscreen far more easily: [http://www.xs4all.nl/~sozonko/asus_r2h_howto/index.html#33](http://www.xs4all.nl/~sozonko/asus_r2h_howto/index.html#33)

---

### Post by Cuppa-Chino on 2007-09-09
has anyone tried what bios F.18 does for us?

> My testing report for the tx1000 (tx1020ea to be exact) is [https://wiki.ubuntu.com/LaptopTestin...viliontx1020ea](https://wiki.ubuntu.com/LaptopTestin...viliontx1020ea)

It includes instructions on how to get the jack sensing working.

Remaining problems:
Graphics card fan never turns on
Lid flip generates no ACPI events
Some buttons generate no showkey/xev events
Fingerprint reader does nothing


check the thread above, have you compared your solution for sound to the model=hp alsa?

---

### Post by simplyw00x on 2007-09-09
> check the thread above, have you compared your solution for sound to the model=hp alsa?
As far as I can tell my solution is working perfectly (apart from the mute light never going orange and the volume buttons not changing headphone volume) so I see no reason to poke around and potentially brea my set-up :D

---

### Post by travisimo on 2007-09-10
I dont even think my wired ethernet is operational. were would you start in that case?

---

### Post by phenolholic on 2007-09-10
simplyw00x : could you have easier instructions, a howto like, to get the headphone jack working?

---

### Post by phenolholic on 2007-09-10
> **travisimo said:**
> I dont even think my wired ethernet is operational. were would you start in that case?

it worked OOTB for me. check your connection settings

---

### Post by phenolholic on 2007-09-10
> **simplyw00x said:**
> My testing report for the tx1000 (tx1020ea to be exact) is [https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1020ea](https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1020ea)

It includes instructions on how to get the jack sensing working. 

Remaining problems:
**Graphics card fan never turns on**
**Lid flip generates no ACPI events**
**Some buttons generate no showkey/xev events**
**Fingerprint reader does nothing**

To calibrate the touchscreen far more easily: [http://www.xs4all.nl/~sozonko/asus_r2h_howto/index.html#33](http://www.xs4all.nl/~sozonko/asus_r2h_howto/index.html#33)

could you make an easier set of instructions (howto like) on getting the audiojack working? thanks

---

### Post by Sollen on 2007-09-10
Sup Ubuntuforums?

I've decided to install Sabayon instead (I'm asking here because the sabayon forums are slow)
and I wonder if anyone here have tried installing the alsa-drivers?
when I try to install mine it just says alsa is built-in, so I can't install it.
HALP PLOX

---

### Post by Cuppa-Chino on 2007-09-10
> **Sollen said:**
> Sup Ubuntuforums?

I've decided to install Sabayon instead (I'm asking here because the sabayon forums are slow)
and I wonder if anyone here have tried installing the alsa-drivers?
when I try to install mine it just says alsa is built-in, so I can't install it.
HALP PLOX

[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

worked fine for me.

just do this:
cd alsa-driver-1.0.14
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install

Now, if you've fooled with alsa before and you've added the "options..." line (ie options snd-hda-intel model=3stack) to /etc/modprobe.d/alsa-base file, then you need to delete it before continuing. If you have no idea what I'm talking about, then don't worry about it.
Code:

$ sudo gedit /etc/modprobe.d/alsa-base

Now, hit page down till you've reached the bottom of the file, and append this new line as the last line of the file.
Code:

options snd-hda-intel model=hp

that should work .----- think I that is listed above as well

---

### Post by Francis Pereira on 2007-09-11
> **simplyw00x said:**
> My testing report for the tx1000 (tx1020ea to be exact) is [https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1020ea](https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1020ea)

How did you get Hibernate and Sleep to work ? What graphic driver are you using ? Are you using compiz ? 
I can confirm that the following works :
[LIST]
[*]wlan works with ndiswrapper @  54Mbps
[*]the CD / DVD writes media
[/LIST]
Is it just me or has anyone else noticed that the touchscreen does not always work. I have binded to touchscreen to evtouch_event. 
I have a tx1003au, love it . Its sweet as Hell .
My First Post Here:popcorn:
Cheers,
Francis

---

### Post by phenolholic on 2007-09-11
i'm having trouble with the headphone jack. i compiled the latest alsa snapshot (9/11/07), and appended: options snd-hda-intel index=0 model=hp
on /etc/modprobe.d/alsa-base ..i went to alsamixer and boosted the headphone level to 100%. i rebooted, and i still have no sound from my headphone jack. one thing i noticed different was the LED for mute is now blue. when i plug in the headphones, the sound from the speaker goes mute (as it should), but sound never picks up from the headphones. any suggestion is appreciated. thanks

---

### Post by simplyw00x on 2007-09-12
> How did you get Hibernate and Sleep to work ?
IIRC, sleep worked ootb and hibernate worked after a couple of small changes to the acpi configuration file (the name and nautre of which I sadly forget).

> What graphic driver are you using ?
nvidia-glx, and now the Envy version of that because I accidentally hosed my drivers.

> Are you using compiz ? 
No, because I like battery life and my GPU fan never turns on so compiz would be toasty.

> Is it just me or has anyone else noticed that the touchscreen does not always work.
Mine is calibrated using the above scripts, udev'd to evtouch_event and works fine after changing the /dev/input/mice entry in xorg.conf to /dev/input/usb_mouse (another device I created myself). This means that a single tap is a single click but sadly means that only mice plugged in at the start of Xorg work. Bah.

> [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

worked fine for me.

just do this:
cd alsa-driver-1.0.14
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
This will not give you jack-sensing.

> could you make an easier set of instructions (howto like) on getting the audiojack working? thanks
[LIST]
[*]Grab the alsa-driver and alsa-kernel sources from [here]("http://www.alsa-project.org/main/index.php/Download#Developers:_HG_access")
[*]Add "{0x15, AC_VERB_SET_EAPD_BTLENABLE, 0x02}" to alc861vd_dallas_verbs in patch-realtek.c in alsa-kernel
[*]Compile and install, then put 'model=dallas' in /etc/modprobe.d/alsa-base
[/LIST]

I am unable to offer support for these instructions, so if they don't work, try the otheres mentioned earlier in the thread.

---

### Post by Walter Nebisher on 2007-09-12
I solved the problem of screen calibration in a better, faster and cleaner way than posted before in this and other forums.

I use Ubuntu Feisty.

I got a long mail exchange with William Chang from eGalax. (cat /proc/input/devices shows the egalax name..).

After some analisys and test, William sent me a new release of drivers for 32 and 64 bit Operating System. He sent me also a management utility, a kernel module and some source code.
The utility is named TouchKit and it gives the possibility to calibrate the display, set touch intervals and timers. It's a better and cleaner solution respect calibrate.sh.

With this software and William hints the touchscreen works great.

Moreover if you use kernel 2.6.20-16 you could boot the tablet with the only option vga=0x317. No other option is necessary.
Software version is: TouchKit_1.07.0831 It's not available, at most at the time of this post, on the web site of eGalax.
Asap I will post all my configuration information on line. Stay tuned.

Thanks William.

---

### Post by Cuppa-Chino on 2007-09-12
> **Walter Nebisher said:**
> I solved the problem of screen calibration in a better, faster and cleaner way than posted before in this and other forums.

I use Ubuntu Feisty.

I got a long mail exchange with William Chang from eGalax. (cat /proc/input/devices shows the egalax name..).

After some analisys and test, William sent me a new release of drivers for 32 and 64 bit Operating System. He sent me also a management utility, a kernel module and some source code.
The utility is named TouchKit and it gives the possibility to calibrate the display, set touch intervals and timers. It's a better and cleaner solution respect calibrate.sh.

With this software and William hints the touchscreen works great.

Moreover if you use kernel 2.6.20-16 you could boot the tablet with the only option vga=0x317. No other option is necessary.
Software version is: TouchKit_1.07.0831 It's not available, at most at the time of this post, on the web site of eGalax.
Asap I will post all my configuration information on line. Stay tuned.

Thanks William.

anyway you can make the software available?

---

### Post by Francis Pereira on 2007-09-14
> **Cuppa-Chino said:**
> anyway you can make the software available?
Not sure if this is the one, I came across this after reading the last few posts . [del]Haven't tried it out yet .[/del] Anyways [http://www.eeti.com.tw/web20/eg/drivers.htm]("http://www.eeti.com.tw/web20/eg/drivers.htm")
Hope this helps

Cheers .:)

Update  : I  used the driver provided . The touch screen works after restarting X . Though the Calibration utility does not work. Just throws out errors for every line in xorg.conf. example ./TouchKit: 21: Identifier: not found
./TouchKit: 22: Screen: not found

---

### Post by hvymtlsteve on 2007-09-16
Hi guys, looks like Circuit City has a similar model , the Pavilion tx1205us, for 850 after rebate (950 up front)... 
I was going to go with Dell 1420n and get Ubuntu preloaded by factory but it's not too late to change my mind... 
For a little over 100 bucks more than the dell I can get this HP... the specs are comparable but at the end of the day this one is smaller and a couple pounds lighter, always a bonus. 

On one hand, getting Ubuntu loaded by the factory takes some of the fun out of it, not as much tweaking to do.. on the other hand if I'm spending 7-900 bucks on a piece of hardware, at the end of the day I really want it to *work*. 
I played with one in the store for a minute and kind of liked it, poked around in Windows device manager to see that the wireless was broadcom which made me frown, but if it can be made to work I guess that's fine...

Anyway, is it worth spending the extra money on this sleek/sexy hardware and the extra time trying to get things to work, or should I stick with the Dell?
For the time being my my primary concerns are getting proper screen resolution, wireless network. 
Sound/headphones, and suspend/hibernate are nice bonuses but I can live without those for the time being. 

Also the people at my local circuit city were not willing to let me try testing out a LiveCD on their floor-demo hardware, so I'd have to bring one home to do any tinkering at all. Do these computers come with a Vista reinstall CD so I can put the crap back in case I decide to return the machine?

Sorry for the long rambling... Any comments appreciated. Cheers!

Steve

---

### Post by Walter Nebisher on 2007-09-17
Hi all


Here is my xorg.conf

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

#Section "Device"
#	Identifier	"nVidia Corporation C51 [Geforce 6150 Go]"
#	Driver		"nv"
#	BusID		"PCI:0:5:0"
#EndSection

Section "Device"
        Identifier      "nVidia Corporation C51 [Geforce 6150 Go]"
        Driver          "nvidia"
        Busid           "PCI:0:5:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51 [Geforce 6150 Go]"
	Monitor		"Generic Monitor"

    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    Option "TwinView" "0"
    Option "metamodes" "1280x800_60 +0+0"
 
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection

Option         "RandRRotation" "on"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	InputDevice	"EETI"		"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "InputDevice"
	Identifier "EETI"
	Driver	   "egalax"
#	Option	   "Device"	"/dev/input/mouse2"
	Option	   "Device"	"usbauto"
	Option	   "Parameters" "/etc/egalax.cal"
	Option	   "ScreenNo"	"0"

EndSection

the egalax drivers I used are here: 

[www.get-in-touch.it/egalax/TouchKit64_1.07.0831.tgz](www.get-in-touch.it/egalax/TouchKit64_1.07.0831.tgz)
[www.get-in-touch.it/egalax/TouchKit_1.07.0831.tgz](www.get-in-touch.it/egalax/TouchKit_1.07.0831.tgz)

I compiled usbkit kernel module and configured in /etc/modules for automatic loading at boot time.

To calibrate the display I used TouchKit during an Xorg session as root.

enjoy

---

### Post by hvymtlsteve on 2007-09-17
Hmmm.. a thought. 
Would it be possible to swap out the broadcom wireless mini-PCI card for an Intel?
Or is this notebook subject to the whitelist on the BIOS?

---

### Post by Cuppa-Chino on 2007-09-17
> **hvymtlsteve said:**
> Hmmm.. a thought. 
Would it be possible to swap out the broadcom wireless mini-PCI card for an Intel?
Or is this notebook subject to the whitelist on the BIOS?

if you do not like the broadcom you are pretty stuck I guess. I have not tried to crack open the case but that might void warranty depending on how and where its located -- what do you want to do with the laptop that should be the decision point...

---

### Post by Cuppa-Chino on 2007-09-17
> **simplyw00x said:**
> My testing report for the tx1000 (tx1020ea to be exact) is [https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1020ea](https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1020ea)

It includes instructions on how to get the jack sensing working. 

Remaining problems:
**Graphics card fan never turns on**
**Lid flip generates no ACPI events**
**Some buttons generate no showkey/xev events**
**Fingerprint reader does nothing**

To calibrate the touchscreen far more easily: [http://www.xs4all.nl/~sozonko/asus_r2h_howto/index.html#33](http://www.xs4all.nl/~sozonko/asus_r2h_howto/index.html#33)

have you tried a newer BIOS?
> 	 Release Date: 2007-07-24           Version: F.18  		
Description 
This package contains the WinFlash utility and a System BIOS image for the supported notebook models and operating systems. The WinFlash utility is used to locally flash the System BIOS (ROM) on notebooks operating in a MicrosoftWindows or Microsoft Windows Vista Operating System environment.

PURPOSE: Recommended
Fixes 
# Resolves issue where the audio skips with some WLAN cards.
# Resolves issue where the notebook unexpectedly shuts down due to an incorrect system temperature report. 

> Release Date: 2007-07-09           Version: F.14  		
Description 
This package contains the WinFlash utility and a System BIOS image for the supported notebook models and operating systems. The WinFlash utility is used to locally flash the System BIOS (ROM) on notebooks operating in a MicrosoftWindows or Microsoft Windows Vista Operating System environment.
PURPOSE: Recommended
Enhancements 
# Improves the AMD CPU P-state control in Over Current Protection (OCP), which provides increased system stability.
# Improves DDR memory stability.
# Shortens the following string "Internal Network Adapter boot" for the Spanish language. 

> Release Date: 2007-06-18           Version: F.13  		
Description 
This package contains the WinFlash utility and a System BIOS image for the supported notebook models and operating systems. The WinFlash utility is used to locally flash the System BIOS (ROM) on notebooks operating in a MicrosoftWindows or Microsoft Windows Vista Operating System environment.
PURPOSE: Recommended
Fixes 
Resolves intermittent issue where some notebooks configured with some AMD processors may stop responding (lock up) during the startup (boot up) process.


and has anybody been able to solve this:
[SIZE="3"]**Some buttons generate no showkey/xev events**[/SIZE]

I cannot get the **_[SIZE="4"]rotate button[/SIZE]_** to work at all, any help is REALLY appreciated thanks

---

### Post by hvymtlsteve on 2007-09-17
> **Cuppa-Chino said:**
> if you do not like the broadcom you are pretty stuck I guess. I have not tried to crack open the case but that might void warranty depending on how and where its located -- what do you want to do with the laptop that should be the decision point...

Basically I want good working wireless and overall functionality. 
No intention of using Windows at all unless I really really have to. 
I've been told it's advisable to stay away from the broadcom devices if you intend to use Linux so I guess I might pass on the tx notebook and stick with Dell... I kind of wanted the extra compactness/portability of this notebook, but I suppose I can settle for 14" and 6 lbs...

Thanks for the reply :)

---

### Post by damawa42 on 2007-09-18
Someone earlier said "everything" works - does that include touchscreen?

---

### Post by Cuppa-Chino on 2007-09-18
> **damawa42 said:**
> Someone earlier said "everything" works - does that include touchscreen?

touchscreen does work, there is a nice how to available, will post the link later

couple things do still cause problems, rotate button for instance, but nothing major

---

### Post by Sollen on 2007-09-18
'sup?
When I try to install the wifi drivers with ndiswrapper, I get this:
DSFARGEG@tx1020ea:~$ sudo rmmod ndiswrapper
Password:
ERROR: Module ndiswrapper does not exist in /proc/modules
What should I do?

---

### Post by simplyw00x on 2007-09-18
> When I try to install the wifi drivers with ndiswrapper, I get this:
Broadcom wireless works fine with the bcm43xx driver; no need for ndiswrapper.

> Basically I want good working wireless and overall functionality. 
Definitely available with this computer.

> have you tried a newer BIOS?
I haven't, but nothing in the changelogs you posted necessarily would solve any of my problems and I believe the standing advice is "don't upgrade unless it'll fix something". Has anyone else had any success with this?

> touchscreen does work, there is a nice how to available, will post the link later
Personally [http://www.xs4all.nl/~sozonko/asus_r2h_howto/index.html#33](http://www.xs4all.nl/~sozonko/asus_r2h_howto/index.html#33) was the easiest HOWTO I found.

---

### Post by mrh015 on 2007-09-18
> **farbird said:**
> to get nvidia drivers working proper
to get into the login screen [ gui ]
try this

click escape before it boots..

edit the line which have the "uuid=xxxxxx" text..

append to the same line with these codes " noapic vga=0x317"
it should get it up to the gfx login screen.


once u get in...
nano edit your /boot/grub/menu.lst file and make the line permanent..


tanks for the info, the "noapic vga=ox317" worked for me.after i got in, i went to system>preferences>desktop effects,i enabled desktop effects,system prompted me to download nvdia restricted driver.i clicked ok,download completed and i restarted the system.i was able to log back in without editing  /boot/grub/menu.lst file

---

### Post by Cuppa-Chino on 2007-09-18
> **Cuppa-Chino said:**
> have you tried a newer BIOS?
and has anybody been able to solve this:
**Some buttons generate no showkey/xev events**

I cannot get the **_[SIZE="3"]rotate button[/SIZE]_** to work at all, any help is REALLY appreciated thanks

Well I am officially a bit thick.
the laptop has two buttons with "rotate printed on them"
a) the windows one -- little square on the bottom edge, this is still useless for me 
b) the one under the DVD button.... I finally got what was said above, it can be assigned to the rotate script as described here:
[how to assign multimedia keys]("http://ubuntuforums.org/showpost.php?p=132591&postcount=1")

I called my XF86RotateWindows and then added that in gconf-editor as described, keycode for the CIRCLE with ARROW button below the DVD button is **205** on mine. now I can finally rotate when in tablet mode....

-------------------------------------------------------------------------------------

I have just discovered that all buttons are disable when the screen is tablet mode, xev does not return any info for anything but the touchscreen. so pushing the media buttons to rotate the view etc while in tablet mode does not work....

---

### Post by Sollen on 2007-09-19
I have trouble installing bcm43xx-fwcutter with Synapse and apt-get.
Is there an alternate source where I can download it?
Or, could anyone please tell me how to download Ndiswrapper and get me a how-to or something?

---

### Post by phenolholic on 2007-09-19
> **simplyw00x said:**
> IIRC, sleep worked ootb and hibernate worked after a couple of small changes to the acpi configuration file (the name and nautre of which I sadly forget).


nvidia-glx, and now the Envy version of that because I accidentally hosed my drivers.


No, because I like battery life and my GPU fan never turns on so compiz would be toasty.


Mine is calibrated using the above scripts, udev'd to evtouch_event and works fine after changing the /dev/input/mice entry in xorg.conf to /dev/input/usb_mouse (another device I created myself). This means that a single tap is a single click but sadly means that only mice plugged in at the start of Xorg work. Bah.


This will not give you jack-sensing.


[LIST]
[*]Grab the alsa-driver and alsa-kernel sources from [here]("http://www.alsa-project.org/main/index.php/Download#Developers:_HG_access")
[*]Add "{0x15, AC_VERB_SET_EAPD_BTLENABLE, 0x02}" to alc861vd_dallas_verbs in patch-realtek.c in alsa-kernel
[*]Compile and install, then put 'model=dallas' in /etc/modprobe.d/alsa-base
[/LIST]

I am unable to offer support for these instructions, so if they don't work, try the otheres mentioned earlier in the thread.


i make & make install'ed the latest alsa drivers. didnt find this patch-realtek.c file you speak highly of.

---

### Post by simplyw00x on 2007-09-20
> i make & make install'ed the latest alsa drivers. didnt find this patch-realtek.c file you speak highly of.
It's in alsa-kernel, which you need to unpack in the alsa-driver folder for the compile to work.

> I have just discovered that all buttons are disable when the screen is tablet mode, xev does not return any info for anything but the touchscreen. so pushing the media buttons to rotate the view etc while in tablet mode does not work....
This is not the case for me.

> the laptop has two buttons with "rotate printed on them"
If you ever booted the windows, the circular 'rotate' button is in fact the HP quickplay button. The square one (which no-one can get to work) is rotate. My rotate button doesn't even light up...

---

### Post by guttersnipe on 2007-09-22
Has anyone else noticed that if you press the button above the touchpad (the one that turns the touchpad on and off) 2 times fast, it brings up "Ubuntu Help Center"?

what  the hell.

---

### Post by simplyw00x on 2007-09-23
> Has anyone else noticed that if you press the button above the touchpad (the one that turns the touchpad on and off) 2 times fast, it brings up "Ubuntu Help Center"?
In fact, pressing it to turn it from "orange" to "blue", regardless of how fast, generates an F1 keypress event. Teh suck.

---

### Post by hvymtlsteve on 2007-09-23
I just brought one of these home (tx1205us), and popped in my feisty liveCD. Here's my experience so far:

Broadcom wireless has obvious issues on liveCD (I'll see if I can't poke around and hack that up). 

First try booting up liveCD was a failure... after boot messages and such, the screen faded to white. Had to go to a meeting for work, so I came back, dug up the thread for the dv9000 series, and per the first post, I added "noapic nolapic irqpoll noirqdebug" to the boot options and tried again...  

At first the screen faded to white, and I thought to myself "ahhh man, no dice."
Then after less than a second, I saw a nice familiar creamy orange color and a smile came to my face. Success!

lsusb shows the Microdia webcam, a cypress semiconductor USB hub, and something from AuthenTec Inc, which I presume to be the fingerprint reader. lspci shows SATA, memory controllers, USB controllers, audio, the usual... the wireless shows up but I am sure the driver is not working at the moment.

Screen resolution-- 1280x800 out of the box! And looks quite beautiful. Crisp and clean, nicer than the 1024x768 on my desktop :D

EDIT-- No sound. I'm sure we can fix that. 
Checking memory usage, it looks like there is no shared memory... perhaps there really is shared memory and it's just not showing up as such?

I will try making a partition on the hard drive for an install, and perhaps report back.
After that, I believe I intend to replace the hard drive and keep the original with vista as from the factory and have it tucked away in case I ever have to send the notebook in for service or anything...

---

### Post by hvymtlsteve on 2007-09-23
Update-- 

Dual boot install was a success! I simply used Vista's disk manager to shrink the main 140 gig partition, leaving approximately 60 or 70 gigs of unused space (more than I need for the moment...) 
My vista installation appears to be unharmed, which (I guess) is good. 

The install took a little longer than on my desktop for some reason, but at any rate it works! 
Graphics still fine. There is a little temporary glitch (horizontal white line) for a second or so when logging in and out, but no big deal as far as I'm concerned. 
Still no sound, but I will work on that... ethernet works, and it's time to investigate wireless as well. 

There is something about a BIOS bug but it doesn't keep feisty from starting up... so I'll look into it later.

EDIT-- last update for now... I used the script on [this thread]("http://ubuntuforums.org/showthread.php?t=405990&highlight=broadcom+43xx") to install wireless... the program selected windows driver + ndiswrapper as the appropriate method, so I went with it. I am posting from wireless right now! 
If I find this to be unsatisfactory for any reason I might try to get it to work without ndiswrapper, but at the moment it works, which works for me.

---

### Post by hvymtlsteve on 2007-09-24
Aha, last observation... as for the sound. 
When in Ubuntu, the mute button is stuck on orange... I presume this is why I'm not getting sound. 
I left a Vista partition and when I use it, sound works and the mute button is blue. 

Any ideas how to fix this?

Cheers

---

### Post by Cuppa-Chino on 2007-09-24
on sound this post in the current thread helped me [http://ubuntuforums.org/showpost.php?p=3292524&postcount=158]("http://ubuntuforums.org/showpost.php?p=3292524&postcount=158")

others have said this works 
```
This will not give you jack-sensing.
Quote:
could you make an easier set of instructions (howto like) on getting the audiojack working? thanks

    * Grab the alsa-driver and alsa-kernel sources from here
    * Add "{0x15, AC_VERB_SET_EAPD_BTLENABLE, 0x02}" to alc861vd_dallas_verbs in patch-realtek.c in alsa-kernel
    * Compile and install, then put 'model=dallas' in /etc/modprobe.d/alsa-base


I am unable to offer support for these instructions, so if they don't work, try the otheres mentioned earlier in the thread.
```
even better

if in doubt try and search this thread it has solutions for most things in it

---

### Post by hvymtlsteve on 2007-09-24
Thanks, Cuppa-Chino!
*hits self on forehead for overlooking that post*
I thought I had looked through most of this thread...

That worked nicely! I now have sound through both the speakers and the headphones, and jack sensing mutes the speakers!
Graphics good... wireless is on ndiswrapper but works well, sound good, the only thing left is VGA output, which I can probably save for another time. That, and getting all my fave software up and running... done that before so no problem there.

I am liking this lappy... it runs a tad warm, but I'm hoping that's not too big a deal.

Thanks again for the help!

---

### Post by Cuppa-Chino on 2007-09-24
> **hvymtlsteve said:**
> Graphics good... wireless is on ndiswrapper but works well, sound good, the only thing left is VGA output, which I can probably save for another time. That, and getting all my fave software up and running... done that before so no problem there.

I am liking this lappy... it runs a tad warm, but I'm hoping that's not too big a deal.


wrt to vga out -- if you are using Nvidia proprietary drivers should work right off the mark (use "envy" to install)

wrt to warm -- gkrellm is able to identify the thermal zones correctly (with Nvidia driver at least) and yes the laptop does get warm, the GPU/Northbridge gets smoking hot if stressed (limit in Nvidia driver is set above 100°C !!)

---

### Post by guadafan on 2007-09-24
The first problem of this laptop is that it has a bad and buggy BIOS. It is the reason that we have to introduce severals params to the kernel.

For example, it can't boot from a CD/DVD USB device or a Hard Disk USB device. This characteristic is normal since 5 years ago in all PCs.

I wrote to HP to ask an update for that firmware BIOS, but I don't know if they will do something. I suppouse that they will need several complains about it.

---

### Post by simplyw00x on 2007-09-24
> Aha, last observation... as for the sound. 
... just because it's a >10-page thread doesn't mean you should skim over it all :)

---

### Post by hvymtlsteve on 2007-09-25
> **simplyw00x said:**
> ... just because it's a >10-page thread doesn't mean you should skim over it all :)

I was trying to be thorough, but with such a long thread I started to get into the habit of passing over stuff that didn't pertain to me (for example, I don't have a touch screen). 
All better now, anyway :) I appreciate all the sharing you guys have done, I got everything up and running on the first night because it was all here! 


> **guadafan said:**
> The first problem of this laptop is that it has a bad and buggy BIOS. It is the reason that we have to introduce severals params to the kernel.

For example, it can't boot from a CD/DVD USB device or a Hard Disk USB device. This characteristic is normal since 5 years ago in all PCs.

I wrote to HP to ask an update for that firmware BIOS, but I don't know if they will do something. I suppouse that they will need several complains about it.

Yeah I don't know what the deal is with the BIOS... On boot-up (right after GRUB) I get a message about some BIOS bug being detected, it goes by pretty quickly so I'll have to watch it a couple times before I can get it all... once I'm sure of the error number I'll do some poking around and see if I can't find out what it is. I will send a comment to HP on it, but the Vista side doesn't display any bug so they probably don't give a crap :rolleyes:

---

### Post by guadafan on 2007-09-25
> **hvymtlsteve said:**
> Yeah I don't know what the deal is with the BIOS... On boot-up (right after GRUB) I get a message about some BIOS bug being detected, it goes by pretty quickly so I'll have to watch it a couple times before I can get it all... once I'm sure of the error number I'll do some poking around and see if I can't find out what it is. I will send a comment to HP on it, but the Vista side doesn't display any bug so they probably don't give a crap :rolleyes:

Other strange thing is that it is not ACPI compatible: have you tryed booting windows from an emulator like qemu? It gives this error:

0xc0000225
Firmware BIOS is not ACPI compatible

---

### Post by hvymtlsteve on 2007-09-26
> **simplyw00x said:**
> In fact, pressing it to turn it from "orange" to "blue", regardless of how fast, generates an F1 keypress event. Teh suck.

Actually I don't think it's F1. On my machine I found that it has its own key code, which is for some reason by default assigned to open Ubuntu help... if you go into the keyboard shortcuts editor in your preferences menu, you can make it stop doing that!

---

### Post by hvymtlsteve on 2007-09-26
> **guadafan said:**
> Other strange thing is that it is not ACPI compatible: have you tryed booting windows from an emulator like qemu? It gives this error:

0xc0000225
Firmware BIOS is not ACPI compatible

Hmm, I haven't tried that... 
I did some looking around, the BIOS bug #81 message that I am seeing has been discussed before, and nobody seems to know what it is.. it apparently doesn't disturb anything so I won't worry about it but I'll keep an eye out.

---

### Post by simplyw00x on 2007-09-26
> Actually I don't think it's F1. On my machine I found that it has its own key code, which is for some reason by default assigned to open Ubuntu help... if you go into the keyboard shortcuts editor in your preferences menu, you can make it stop doing that!
My mistake; it's Fn+F1 - i.e. the little 'help' icon. Which *should* open help. But thanks for the tip about keyboard shortcuts. Now we just need to figure out why that button sends ANY event.

---

### Post by dodgy_geeza on 2007-09-26
Hi all, firstly wanted to say thanks to everyone who has posted here, as it has saved me a lot of time with my new laptop. I figured I would list the stuff I have working, and the stuff that is still a pain...

FYI, the lappy is a tx1250ea, still labelled on the front as a tx1000 though :S It's also running the F18 BIOS, and Ubuntu 7.10 Pre-release (this has support for the acpi_os_name boot option.

Working
- Touchscreen (Using the closed-source driver, also have rotate playing nicely now, using one of the buttons on the screen)
- Wireless (Using ndiswrapper until the bcm43xx driver has support
- Sound (Using the SuSE CVS snapshot, jack detection works a treat, as do the headphones)

Work-in-Progress
- Webcam (Device is there, but camstream can't open it, gives some weird errors, still workin on it)

A big issue that I have atm, which might be related to posts from other people, is that the noapic option needs to be used, otherwise the system hangs. This however causes my 2nd cpu to run at 100% constantly. I've been through a whole multitude of boot options in various combo's, but none of them seem to work properly without the noapic.

I know a few of you have mentioned the heat of your laptop, have any of you checked to see the CPU usage. Note. "ps" will not show you kernel activity (or at least i dont know the option for it), use htop and look for red bars for the cpu.

Not sure if any of that will help, and I will carry on trying to get this 100% cpu issue sorted, will keep you all posted :-)

Dodgy

---

### Post by simplyw00x on 2007-09-26
> - Webcam (Device is there, but camstream can't open it, gives some weird errors, still workin on it)
Mine worked out-of-the-box, but it only works in certain programs. Try 'cheese'

> - Touchscreen (Using the closed-source driver, also have rotate playing nicely now, using one of the buttons on the screen)
Exactly which closed-source driver, and what's your xorg.conf like?

> - Sound (Using the SuSE CVS snapshot, jack detection works a treat, as do the headphones)

What was your install process like, because I get conflicts with the snd-hda-intel modules from linux-ubuntu-modules (since installing gutsy).

---

### Post by dodgy_geeza on 2007-09-27
Cheers for the advice on Cheese, will give that a try tonight.

Ask for the drivers, im using the nvidia-glx-new package from Ubuntu so that I have 3D support. I have noticed that if I enable Compiz, rotating the screen crashes X. If you disable Compiz it works fine. I will prolly adjust the rotate script (had to anyway as xrandr gives different info now) so that it stops Compiz, rotates the screen, then brings it back up.

The touchscreen driver im using is the evtouch one, version 0.8.7. It's actually in the Gutsy repository, so I didn't need to install it from a tar.gz, though I did experiment with both of them.

The sound was straightforward. All I did was follow the instructions posted here, (tar -xvzf, make, make install), and that was it. Once done I just rebooted and the sound was done, all I had to do was use alsamixer and alsactl to unmute the headphone volume etc.

I will have another look at the webcam tonight given I would like to use it with aMSN. Might give the infra-red a go as well, see if I can get LIRC to play nice with the remote. Just wish I could sort the 100% CPU issue given it kills my battery life and gets the lappy VERY hot :-(

I can post my configs online if needed.

Dodgy

---

### Post by mikedep333 on 2007-09-27
Well, I just got my tx1000z and decided to run Gutsy (x86) on it.

My first big problem is with the touchscreen. I am using the evtouch included with gutsy. Whenever I go to calibrate it, it never registers me touching the screen (the text never appears.) Without calibrating, touching the screen causes the cursor to go to the bottom right of the screen.

Here is what my xorg.conf looks like:

```
Section "Files"
InputDevices "/dev/input/event2"
EndSection

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event2"
    Option "DeviceName" "touchscreen"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"e
    Option "MaxY" "925"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "TapTimer" "0"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
    Option "Calibrate" "1"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mouse0" #formerly set to /dev/input/mice as one person had on the forums
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	InputDevice "touchscreen" "CorePointer"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

...

Section "Module"
	Load		"glx"
EndSection
```

cat /proc/bus/input/devices
```
...
I: Bus=0003 Vendor=0eef Product=0001 Version=0210
N: Name="eGalax INC. USB TouchController"
P: Phys=usb-0000:00:0b.1-2.3/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=b
B: KEY=401 0 30000 0 0 0 0 0 0 0 0
B: ABS=f
...

```

I seem to have everything configured fine based on what other people did, but still the calibration never registers a single touch. I have been running the calibration as root too.

Secondly, I can't get ndiswrapper to work with my broadcom draft 802.11n card. I have  tried using 3 different drivers. One from a Dell draft-n card dated in june 06 labeled bcmwl5, the one that came with this system from december 06 labeled bcmwl6, and one very recent one from july also labeled bcmwl6. With all of them, ndiswrapper loads them fine but despite following a lot of instructions like unloading and loading the kernel module, no eth1 or wlan0 device shows up that I can use.

---

### Post by simplyw00x on 2007-09-27
> The sound was straightforward. All I did was follow the instructions posted here, (tar -xvzf, make, make install), and that was it. Once done I just rebooted and the sound was done, all I had to do was use alsamixer and alsactl to unmute the headphone volume etc.
Hmm might have to play around with that some more then, because those steps stopped working for me on gutsy.

> Might give the infra-red a go as well, see if I can get LIRC to play nice with the remote.
The remote generates keystrokes on a hardware level; the IR capabilities can't be accessed from the OS. You can map the buttons in gnome-keybinding-properties, however.

> I can post my configs online if needed.
xorg.conf and modules.dep would be wonderful :) Thanks,

---

### Post by dodgy_geeza on 2007-09-27
simplyw00x, cheers for the info, I see what you mean about the remote. It maps most of the buttons to common keys (up/down/left/right etc) which play nice with mythtv. I need to configure a couple of the buttons so that I have an escape button for returning to the previous menu etc.

As for the xorg.conf, here goes...

```

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	#Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Identifier	"Touchscreen"
	Driver		"evtouch"
	#Driver		"evdev"
	Option		"Device"		"/dev/input/evtouch_event"
	Option		"DeviceName"		"touchscreen"
	Option		"MinX"			"40"
	Option		"MinY"			"90"
	Option		"MaxX"			"4015"
	Option		"MaxY"			"4000"
	#Option 	"TapTimer" 		"0"
	#Option 	"LongTouchTimer" 	"250"
	Option 		"ReportingMode" 	"Raw"
	Option 		"SendCoreEvents" 	"On"	
	#Option		"Calibrate"		"1"
EndSection

Section "Device"
	Identifier	"NVIDIA"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"		"True"
	Option		"RenderAccel"		"True"
	Option		"AllowGLXWithComposite"	"True"
	Option		"DRI"			"True"
	Option		"Coolbits"		"1"
	Option		"HWCursor"		"True"
	Option		"BackingStore"		"On"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA"
	Monitor		"LCD"
	Defaultdepth	24
	Option		"RandRRotation" 	"on"
	SubSection "Display"
		Depth	24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
	Inputdevice	"Touchscreen"		"CorePointer"
EndSection

```

The modules.dep is pretty hefty, I can post it if really needed, but what do you need from it?

On a more amusing note, my touchscreen works better in Linux than it does in Windows, not really that much of a suprise ;)

Dodgy

---

### Post by dodgy_geeza on 2007-09-27
> **mikedep333 said:**
> Well, I just got my tx1000z and decided to run Gutsy (x86) on it.

My first big problem is with the touchscreen. I am using the evtouch included with gutsy. Whenever I go to calibrate it, it never registers me touching the screen (the text never appears.) Without calibrating, touching the screen causes the cursor to go to the bottom right of the screen.

Here is what my xorg.conf looks like:

```
Section "Files"
InputDevices "/dev/input/event2"
EndSection

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event2"
    Option "DeviceName" "touchscreen"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"e
    Option "MaxY" "925"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "TapTimer" "0"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
    Option "Calibrate" "1"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mouse0" #formerly set to /dev/input/mice as one person had on the forums
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	InputDevice "touchscreen" "CorePointer"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

...

Section "Module"
	Load		"glx"
EndSection
```

cat /proc/bus/input/devices
```
...
I: Bus=0003 Vendor=0eef Product=0001 Version=0210
N: Name="eGalax INC. USB TouchController"
P: Phys=usb-0000:00:0b.1-2.3/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=b
B: KEY=401 0 30000 0 0 0 0 0 0 0 0
B: ABS=f
...

```

I seem to have everything configured fine based on what other people did, but still the calibration never registers a single touch. I have been running the calibration as root too.

Secondly, I can't get ndiswrapper to work with my broadcom draft 802.11n card. I have  tried using 3 different drivers. One from a Dell draft-n card dated in june 06 labeled bcmwl5, the one that came with this system from december 06 labeled bcmwl6, and one very recent one from july also labeled bcmwl6. With all of them, ndiswrapper loads them fine but despite following a lot of instructions like unloading and loading the kernel module, no eth1 or wlan0 device shows up that I can use.

Mike, after numerous attempts at this with Gutsy, I had this problem also. In my case it came down to boot options, I think it was the irqpoll option. Without it, both the touchpad and the wireless wouldn't work. I've had to use some creative options to get it all to work, as sometimes the wireless would work but not the touchpad, other times it would be in reverse.

In my case I now boot with..

```

title           Ubuntu gutsy (development branch), kernel 2.6.22-12-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-12-generic root=UUID=e87e0fc8-a542-4590-96f6-ac68e20684ff ro noapic acpi_osi="!Linux" acpi_os_name="Windows 2006" pci=biosirq pci=nomsi irqpoll
initrd          /boot/initrd.img-2.6.22-12-generic
quiet

```

I tried various combinations of the assorted boot options, and this is the combination  I found that works. On a downside, one of the two CPU's sits at 100% all of the time :@ due to the noapic option. Removing this however leads to a system freeze usually after 60 seconds.

noapic - disable the advanced programmable interrupt controller (it doesnt work(buggy bios?)
acpi_osi - not sure if this is needed with F18 bios, ive ran it without before, might remove it and try again
acpi_os_name - same as above
pci=biosirq - use the bios irq table, fixes the unable to assign IRQ 0 issue when using ndiswrapper, and the edge-triggered problem with nvidia graphics
pci=nomsi - from prior experience, msi + nforce chipsets = a bad idea, doesnt play nice
irqpoll - fix broken interrupts and routing, needed for the touchscreen (USB on IRQ 7)

I'm also running the modified UDEV rule which gives me /dev/input/evtouch_event. This is useful given it changes event number on most reboots. The code for it is in this topic, not sure of what page.

To calibrate the touchscreen I used the evtouch 0.8.7 tarball, and disabled GDM from booting at startup. This also allowed me to test numerous boot options, and to make sure the touchscreen worked without using GDM. One thing I did need to do was change the startup position of GDM. For some reason (possibly UDEV), if GDM started up at its usual position (30), the touchscreen was hit and miss, changing it to 90 on runlevel 3 and 5 now means it works every time :D

Hope this helps

Dodgy

---

### Post by Stonesphere on 2007-09-28
I followed the audo jack settings to the T.  I am still not getting sound from the headphone jacks.  In the alsa mixer I can check headphones under preferences, and it gives me the switch tab so I can <check> headphones, but there is no volume bar or mute to un-check.  Any suggestions?

BTW, you all kick @ss, I have learned a lot so far from this forum, and trying to get this funky HP Vista built beast working. How much harder could this have been.  Thank God I didn't have a touch screen or I would have gone back to Vista screaming, and the only reason I'd go back to Vista is because HP isn't supporting XP on this lappy, and I didn't want to waste the bandwidth tracking down XP drivers. Plus, I really want to love Linux.

VIVA UBUNTU !!

---

### Post by dodgy_geeza on 2007-09-28
Just another quick update... after playing around last night and some midnight searching I found a few interesting sites detailing similar problems with other HP laptops. It seems that HP has some serious issues when writing BIOS's for their laptops, and that the problems we are experiencing arent just limited to this model.

A few of the "interesting" things I found was that there are a couple of boot options which should solve the problem.

pci=conf1 / irqfixup / acpi_irq_balance

I hate to say that I tried all three of these and to no avail. The pci=conf1 option crashes when ndiswrapper loads, just after IRQ9 is used. The other two options I have tried in various combinations with no good results :-( I also tried the nosmp option which while disabling one of the two cpu cores, should solve the 100% issue, unfortunatly my laptop fails to boot if i use this :''(

One thing I have noticed is that at least in Ubuntu, it seems to be using the HPET for the clocksource instead of ACPI_PM. IIRC, if your system has speedstepping/powernow, you need to use the ACPI_PM module otherwise the clocksource can't cope with the CPU frequency changing. Im not sure if the HPET is troubled by this, just something I noticed.

Hopefully I can have a longer play with this lappy this weekend, see if I can solve anything.

Dodgy

---

### Post by Cuppa-Chino on 2007-10-01
> **dodgy_geeza said:**
> Mike, after numerous attempts at this with Gutsy, I had this problem also. In my case it came down to boot options, I think it was the irqpoll option. Without it, both the touchpad and the wireless wouldn't work. I've had to use some creative options to get it all to work, as sometimes the wireless would work but not the touchpad, other times it would be in reverse.

In my case I now boot with..

```

title           Ubuntu gutsy (development branch), kernel 2.6.22-12-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-12-generic root=UUID=e87e0fc8-a542-4590-96f6-ac68e20684ff ro noapic acpi_osi="!Linux" acpi_os_name="Windows 2006" pci=biosirq pci=nomsi irqpoll
initrd          /boot/initrd.img-2.6.22-12-generic
quiet

```

I tried various combinations of the assorted boot options, and this is the combination  I found that works. On a downside, one of the two CPU's sits at 100% all of the time :@ due to the noapic option. Removing this however leads to a system freeze usually after 60 seconds.

noapic - disable the advanced programmable interrupt controller (it doesnt work(buggy bios?)
acpi_osi - not sure if this is needed with F18 bios, ive ran it without before, might remove it and try again
acpi_os_name - same as above
pci=biosirq - use the bios irq table, fixes the unable to assign IRQ 0 issue when using ndiswrapper, and the edge-triggered problem with nvidia graphics
pci=nomsi - from prior experience, msi + nforce chipsets = a bad idea, doesnt play nice
irqpoll - fix broken interrupts and routing, needed for the touchscreen (USB on IRQ 7)

I'm also running the modified UDEV rule which gives me /dev/input/evtouch_event. This is useful given it changes event number on most reboots. The code for it is in this topic, not sure of what page.

To calibrate the touchscreen I used the evtouch 0.8.7 tarball, and disabled GDM from booting at startup. This also allowed me to test numerous boot options, and to make sure the touchscreen worked without using GDM. One thing I did need to do was change the startup position of GDM. For some reason (possibly UDEV), if GDM started up at its usual position (30), the touchscreen was hit and miss, changing it to 90 on runlevel 3 and 5 now means it works every time :D

Hope this helps

Dodgy

I tried putting Gutsy Beta i386 on the laptop and must say it just would not respond properly, key issues:
a) wireless, call me stupid but could not get WPA to work at all, used the ndiswrapper included and compile from source I had no chance of getting wpasupplicant to work proper, any pointers welcome
b) heat, heat, HEAT -- the fans were always on and the laptop seemed to be much hotter than on feisty (100% cpu issue?)

I booted with **noapic irqpoll noirqdebug **options. Any help thoroughly appreciated, especially on the WPA?

---

### Post by mikedep333 on 2007-10-01
Hey guys. Shouldn't we create launchpad bug reports for some of this trouble with gutsy?

---

### Post by hvymtlsteve on 2007-10-02
Here's another little tidbit I thought I'd throw in. 

I got the webcam to work in aMSN by using version .97RC which can be installed with the distribution independent auto installer on their website. 
Last night I tried sudo apt-get install amsn, and got version .96 and my webcam didn't work (I could receive somebody else's feed but my own did not work).

---

### Post by benguin on 2007-10-02
Hello all,
I should thank the people posting  their experiences here up front. I got myself a HP TX1305CA this weekend, and I've been playing with it, trying to get Gutsy beta to work. Issues like the video screen messing up from the livecd got me a little shocked, but thanks to the vga=0x317 kernel option, I got through that. Now, here's where I stand. 

1. I do not have to pass any kernel arguments for Gutsy to boot properly. It works, although in the last 3 days, it failed twice to boot up. I've been running the laptop on Linux for over  8 hours a day now, so that's not too bad.

2. Broadcom didn't work with bcm43xx. I got ndiiswrapper, and manually installed the Windows XP drivers which I downloaded and cab-extracted from the HP support website for my version of the laptop. It works like a charm, although not as fast as it should be. Better that than nothing. (The wireless indicator light turns blue when I load the ndiswrapper module).

3. NVidia proprietary drivers are working, from Gutsy repos. That was painless, and I also have Compiz (aka "Visual Effects") working. I haven't tried anything over the normal configuration, but its stable and does not do anything weird, pleasantly. I have the negative plugin working, which is great, since I spend a significant amount of time coding.

4. Sound. Here's the bad news. The alsa snapshot trick as posted here did not work for me. sudo modprove snd-hda-intel fails with an  "unknown symbol in module" message. I have quite a few such symbols, one of them being (as an example) snd_pcm_hw_cinstraint_step, and the message says it disagrees about the version of the symbol. I looked at the compiler version of my kernel, and its gcc 4.1.3 20070929 (4.1.2.-16ubuntu2), and cat /proc/version shows kernel compiled with gcc 4.1.3  20070831 (4.1.2.-16ubuntu1). Is that the reason? I tried getting back to the kernel compiler, but I can't find it in Synaptic. Do I have to compile the entire kernel again for this to work?

5. Touchpad. Works, I used dodgy_geeza's xorg.conf as a reference, and it works out of the post . lol. Have not tried handwriting or any other app, but I can surely tap and click with the pointer.

6. Have not tried suspend or hibernate, or the remote control. 

7. Video out has not been tested either, but I will soon.

Thanks again for the assistance, everyone. If anyone has any questions, hardware specs and all, I'll be happy to share.

Ciao,
-J-

---

### Post by rsclark3 on 2007-10-02
Gutsy 7.10

If you use NOLAPIC, does the CPU issue continue?  I use NOAPIC and NOLAPIC.  I don't have heat or CPU 100% issues.

ALSA 1.0.15RC3 sets up sound correctly.  Install and make is a pain.

-Rich

---

### Post by dodgy_geeza on 2007-10-02
Rich, I tried using both noapic and nolapic, but both leave me with 100% CPU on the 2nd core. What bios version are you using? and what is your exact bootline in grub?

I'm hoping at some point this week to build a custom kernel and see if it is a problem with the Ubuntu kernel. Might also have a go at 64-bit while im there, but it depends on Uni work etc.

On a different note, has anybody noticed that when typing pretty fast, it occasionally seems to repeat keys (as if they were stuck down)? I think its to do with the 100% CPU issue, and the IRQ's being hammered, but im not sure. I might see if I can video it in action, to give people an idea of what I mean.

Dodgy

---

### Post by benguin on 2007-10-02
Rich, did you have to install all alsa ALSA 1.0.15RC3 packages? Or just the alsa driver? sorry for the dumb question, but just compiling and installing the alsa-driver tarball didn't help my cause there.

Thanks.

-J-

---

### Post by sauronsmatrix on 2007-10-04
I tried to run calibration program and this happens:

> root@woohoo:/home/linus/Desktop/evtouch-0.8.7# sh ./calibrate.sh
./ev_calibrate
evalibrate located at ./ev_calibrate
xinit located at /usr/bin/xinit
xserver located at /usr/bin/X
Creating FIFO...
Starting calibration program...

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


---

### Post by sauronsmatrix on 2007-10-04
also, my xorg.conf
> # xorg.conf (xorg X Window System server configuration file)
#
# This help file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"nv"
	Busid		"PCI:0:5:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Modelname	"Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1280x960@60"	"1280x1024@60"	"1152x864@75"	"1400x1050@60"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:0:5:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	#Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Identifier	"Touchscreen"
	Driver		"evtouch"
	#Driver		"evdev"
	Option		"Device"		"/dev/input/evtouch_event"
	Option		"DeviceName"		"touchscreen"
	Option		"MinX"			"40"
	Option		"MinY"			"90"
	Option		"MaxX"			"4015"
	Option		"MaxY"			"4000"
	#Option 	"TapTimer" 		"0"
	#Option 	"LongTouchTimer" 	"250"
	Option 		"ReportingMode" 	"Raw"
	Option 		"SendCoreEvents" 	"On"	
	#Option		"Calibrate"		"1"
EndSection

Section "Device"
	Identifier	"NVIDIA"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"		"True"
	Option		"RenderAccel"		"True"
	Option		"AllowGLXWithComposite"	"True"
	Option		"DRI"			"True"
	Option		"Coolbits"		"1"
	Option		"HWCursor"		"True"
	Option		"BackingStore"		"On"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA"
	Monitor		"LCD"
	Defaultdepth	24
	Option		"RandRRotation" 	"on"
	SubSection "Display"
		Depth	24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
	Inputdevice	"Touchscreen"		"CorePointer"
EndSection

and, this line:
Option		"Device"		"/dev/input/evtouch_event"

I looked, and there is no file /dev/input/evtouch_event there.

---

### Post by dodgy_geeza on 2007-10-04
Sauronsmatrix, for your first problem, the output tells you that X is already running. Chances are you have left GDM running in the background. You need to switch to a proper VT (Ctrl+Alt+F1), log in, and then stop GDM. Once done, that should allow you to run the calibrate script.

For your second problem, the /dev/input/evtouch_event is a symbolic link to one of the event files under /dev/input. It is created by udev and is needed because the touchscreen is not always event2 or event3 etc. Udev doesnt create the link automagically, you need to read this thread from the start, and the udev code is listed. Once you have edited udev, either reboot or run udevtrigger as root, and that should create the evtouch_event file for you :-)

Dodgy

---

### Post by sauronsmatrix on 2007-10-04
ok things I did:
copied 69-touchscreen.rules to the proper directory.

I couldn't find the udev script thingy that makes the evtouch_event file

Is it possible to use someone else's evtouch_event, or is each one unique?

Thanks,

Saurons

---

### Post by benguin on 2007-10-04
hi,
Just wondering, anybody else faced problems with loading the manually compiled alsa-driver module ? I'm still getting symbol version mismatches and  unrecognized symbol errors. A hint about your kernel compiler and module compiler would be greatly appreciated. thanks!

-J-

PS: I outlined the problem in post #223.

---

### Post by dodgy_geeza on 2007-10-04
Hi all, just a progress update, and some advice...

Firstly, Saurons, the evtouch_event is simply a symlink to one of the files in /dev/input. We use it because depending on how the system comes up, the touchscreen might appear as a different event. This way, we have a fixed file to point X at. The touchscreen udev rule you have installed should work correctly (have you rebooted?), and should give you /dev/input/evtouch_event. If it hasn't, what model laptop & distro are you using?

Secondly, i've been playing around with some more boot options in the hope of getting the lappy to play nice. Im currently using:

   acpi_osi=!Linux acpi_os_name="Windows 2006" pci=usepirqmask pci=nomsi acpi_skip_timer_override irqpoll clocksource=acpi_pm

The above seems to be working, and my 100% cpu issue has gone. Im still not convinced though, and shall continue to do some more testing. It seems that the keyboard is still laggy from time to time, need to figure out what that is really.

Prolly the most interesting option in the above is the "pciuseirqmask", which according to some documentation I found is listed as "Honor the possible IRQ mask stored in the BIOS $PIR table. This is needed on someystems with broken BIOS's, notably the HP Pavilion 5400 and Omnibook XE3 notebooks." Figured it might be worth a shot.

I shall carry on testing some different options int he hope of finding a working combo that fixes the issues. I can state for sure on mine that booting without the irqpoll option disables the touchscreen, and prolly other USB devices.

Dodgy (Posted from a TX1250ea :D )

---

### Post by sauronsmatrix on 2007-10-04
Hey man, 

I had this problem too.

You need to have these packages first (use synaptic package manager):
po-debconf
debhelper
quilt

Then, try to install the alsa-driver.

I know the whole process with sound, so ask me and I will guide you through it. :)

---

### Post by benguin on 2007-10-04
> **sauronsmatrix said:**
> Hey man, 

I had this problem too.

You need to have these packages first (use synaptic package manager):
po-debconf
debhelper
quilt

Then, try to install the alsa-driver.

I know the whole process with sound, so ask me and I will guide you through it. :)

I'd be really happy if you took the trouble :). Just a brief outline of the process should be good to get me started. 

Thanks
-J-

---

### Post by sauronsmatrix on 2007-10-04
This applies only to Ubuntu 7.10 and lower. Ubuntu 8.04 beta and higher will support the sound problem.
------------------------------------------
Okay, so install these five, (e.g. using Synaptic Package Manager).[INDENT]po-debconf
debhelper
quilt
alsa-base
libc6-dev
[/INDENT]Then, install [alsa-driver]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.16.tar.bz2"):

1) Extract archive to some[COLOR=Red] folder[/COLOR].

2) Open up a terminal.
make yourself the root user with "su"

3) go to the [COLOR=Red]folder[/COLOR] with the "cd" command

4) Run these commands in this order:[INDENT]./configure
make
make install
[/INDENT]Note: Yes, this process can take like** 3 minutes**.

When its installed, add this line to/etc/modprobe.d/alsa-base [use command "gedit /etc/modprobe.d/alsa-base" under "su" priveleges]:[INDENT]
options snd-hda-intel model=hp[/INDENT]If your sound isn't working at startup (e.g. you cannot hear the ubuntu login noise, then do this:

gedit /etc/modules

Add these lines to the bottom:
```
snd-hwdep
snd-hda-intel
```
Restart your computer, and bam. It should be working. If you do not understand my instructions, feel free to ask me to clarify.

***_[COLOR=Navy]NEW PROBLEM! It seems that when you update the kernel, the drivers stop working. A solution is at hand:[/COLOR]_***

**NOTE**: Change the [COLOR=Blue]kernel version [/COLOR]as necessary.

There are two copies of the snd_hda_intel,ko file lurking in /lib/modules:
```
[COLOR=Blue]/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
[COLOR=DarkGreen]/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko[/COLOR]
```To solve this problem, run these commands in the a terminal under "su" privileges
```
rm [COLOR=Blue]/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
ln -s [COLOR=DarkGreen]/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko[/COLOR] [COLOR=Blue]/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
```gedit /etc/modules

Add these lines to the bottom:
```
snd-hwdep
snd-hda-intel
```Restart, and it should be working.

A HUGE thanks to [benguin]("http://ubuntuforums.org/member.php?u=9893"), who framed the solution for the kernel update bug.

---

### Post by benguin on 2007-10-04
Thanks for the info. I've been trying this process for the last few days. After reboot, the system cannot find a sound device. Trying to run alsamixer says this:

```
alsamixer: function snd_ctl_open failed for default: No such device
```

So I try to load the module manually...
```
sudo modprobe snd-hda-intel

FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.22-12-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

And finally, dmesg says the following:
```
[  115.424000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[  115.424000] snd_hda_intel: Unknown symbol snd_ctl_add
[  115.424000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[  115.424000] snd_hda_intel: Unknown symbol snd_pcm_new
[  115.424000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[  115.424000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  115.424000] snd_hda_intel: disagrees about version of symbol snd_card_register
[  115.424000] snd_hda_intel: Unknown symbol snd_card_register
[  115.424000] snd_hda_intel: disagrees about version of symbol snd_card_free
[  115.424000] snd_hda_intel: Unknown symbol snd_card_free
[  115.424000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  115.424000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  115.424000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[  115.424000] snd_hda_intel: Unknown symbol snd_card_proc_new
[  115.424000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[  115.424000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[  115.424000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[  115.424000] snd_hda_intel: Unknown symbol snd_ctl_new1
[  115.424000] snd_hda_intel: disagrees about version of symbol snd_component_add
[  115.424000] snd_hda_intel: Unknown symbol snd_component_add
[  115.424000] snd_hda_intel: disagrees about version of symbol snd_card_new
[  115.424000] snd_hda_intel: Unknown symbol snd_card_new

```

Any ideas?

Thanks!

---

### Post by sauronsmatrix on 2007-10-04
see [this]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235")

---

### Post by benguin on 2007-10-04
it is a tx1000 -- a tx1305ca to be exact.

sauronsmatrix, thanks for the assistance, but, the module is not loading, and as a result no devices are showing up. That means I have nothing to choose from.

could someone who has sound working with this methiod please post the outputs of ```
cat /proc/version
``` and ```
gcc -v
``` ? Thanks!

-J-

---

### Post by sauronsmatrix on 2007-10-04
output of "cat /proc/version"

```
Linux version 2.6.22-12-generic (buildd@vernadsky) (gcc version 4.1.3 20070831 (prerelease) (Ubuntu 4.1.2-16ubuntu1)) #1 SMP Sun Sep 23 18:11:30 GMT 2007
```

output of "gcc -v"

```
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

```

Hope it helps man

---

### Post by benguin on 2007-10-04
thanks. at least that tells me that compiler versions aren't an issue. I have the exact same compiler/build-tools. Maybe it's my particular hardware. I'm thinking of going hardcore on this and do some low-level investigation.

i appreciate the help. seems painful when its so easy for everyone else and doesn't work at all for me.

cheers,
-J-

---

### Post by ewangr on 2007-10-05
OK, I'm getting beaucoup tired of it taking three minutes for Vista Ultimate to wake up if I have the photo screensaver turned on, and five minutes to transfer a file over my home network to my two Buffalo Terrastation drives.

Used Ubuntu for a while a year or so back, and since I'm not using iClone any more, I really don't have any reason to stay on Windows. Although if there's an easy way to setup a virtualized Windows under Ubuntu I'd appreciate pointers to that.

Anyway, I have the touchscreen version of the tx1000 with 2 gigs of RAM, and I also have the nice docking station. After reading through this thread, I'm having second (and third) thoughts about converting. How much trouble am I really looking at here if I load the latest version of Ubuntu (or Kubuntu)?

TIA,
Ewan

---

### Post by Cuppa-Chino on 2007-10-05
thread looks worse than it is:

I would recommend using i386 feisty cd and load with **vga=0x317 noapic irqpoll noirqdebug** options, that will see you nicely underway 

and of course there are enough of us here to help

---

### Post by benguin on 2007-10-05
Okay, finally I figured out and fixed the sound issue. I had two copies of the snd_hda_intel,ko file lying around under /lib/modules. The location where Ubuntu stores it is  /lib/modules/2.6.22-12-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko, and manual compilation leaves a copy of it in  /lib/modules/2.6.22-12-generic/kernel/sound/pci/hda/snd-hda-intel.ko. I deleted the old one and made a symlink from that location to the new driver. It would still not load, so I had to put  these two lines in /etc/modules:

```
snd-hwdep
snd-hda-intel
```

That's fixed it. I have jack sensing, built-in mics are working as well. the mute light doesnt turn amber when its muted, but thats not a major issue for me at all. Thanks everyone for the help. 

Next in line: external monitor/projector support.

-J-

---

### Post by ewangr on 2007-10-05
> **Cuppa-Chino said:**
> thread looks worse than it is:

I would recommend using i386 feisty cd and load with **vga=0x317 noapic irqpoll noirqdebug** options, that will see you nicely underway 


The i386 one? I presumed that since it has the AMD Turion X2 TL-60 dual core processor that I would want one of the 64 bit versions. No?

---

### Post by benguin on 2007-10-05
> **ewangr said:**
> The i386 one? I presumed that since it has the AMD Turion X2 TL-60 dual core processor that I would want one of the 64 bit versions. No?

Sure, you could use that. But as far as my (mostly outdated) knowledge goes, you'll have issues with application software not supporting a 64-bit platform (Adobe Flash being one that comes into my   mind right away, correct me if I'm wrong). I am running the 32-bit edition, and as of now the fingerprint reader aside, things are working well. Have not tested suspend/hibernate, or external display (as in a projector) yet. 

Good luck Ubuntufying :)

-J-

---

### Post by ewangr on 2007-10-05
OK, 386 version it is. Last question would be, should I DL the current stable, or wait two weeks for the new release? IOW, are there fixes in the latest version that would make installing easier?

Thanks again,
Ewan

---

### Post by benguin on 2007-10-05
> **ewangr said:**
> OK, 386 version it is. Last question would be, should I DL the current stable, or wait two weeks for the new release? IOW, are there fixes in the latest version that would make installing easier?

Thanks again,
Ewan

Definitely go for Gutsy (7.10), even the Beta works well. Mind you, the sound needs a manual driver installation anyways. But if you wanna wait two weeks for the final release, that's always better. I haven't tried Feisty (the latest stable) on it, but I have a gut feeling you'll face more driver issues.

Cheers.
-J-

---

### Post by sauronsmatrix on 2007-10-05
glad your sound is working beguin!

cheers!

summarized the whole process [here]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235")

---

### Post by benguin on 2007-10-06
> **sauronsmatrix said:**
> glad your sound is working beguin!

cheers!

Thanks and also for the help. I'll work on getting the external display to work. By the way, the Authentec website says they have linux support for the fingerprint scanner. anyone know where and how to get a driver, if there's one at all?

Cheers,
-J-

---

### Post by jjordan on 2007-10-06
External display is almost PNP, I have been using a ViewSonic at 1680X1050 for weeks, set it up as twinview, casue I like it that way.   Install and run nvidia-settings but make sure you backup your xorg.conf because it will trash it if you save. It has no respect for touchscreen or other settings in xorg.conf so beware.   Even had TV out working through the docking station in the hotel a couple weeks ago to watch my .avi's

-j

---

### Post by sauronsmatrix on 2007-10-06
the definitive sound [solution ]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235")[especially on tx1000z's]

---

### Post by reinderien on 2007-10-07
> **sauronsmatrix said:**
> 
4) Run these commands in this order:
[INDENT]./configure
make
make install
[/INDENT]


So when I try make, I get this output:

```

if [ ! -d include/sound -a ! -L include/sound ]; then \
          ln -sf ../alsa-kernel/include include/sound ; \
        fi
cp -puvf include/version.h include/sound/version.h
`include/version.h' -> `include/sound/version.h'
make dep
make[1]: Entering directory `/home/greg/alsa-driver-1.0.15rc3'
make[2]: Entering directory `/home/greg/alsa-driver-1.0.15rc3/acore'
copying file alsa-kernel/core/info.c
/home/greg/alsa-driver-1.0.15rc3/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/home/greg/alsa-driver-1.0.15rc3/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/greg/alsa-driver-1.0.15rc3'
make: *** [include/sndversions.h] Error 2

```

What am I doing wrong?

Thanks Sauron

---

### Post by sauronsmatrix on 2007-10-07
That is very strange....
are you logged in as the root account?

If not, use "su"
and type the root password,

then start over.

if that isnt the case, please let me know.

EDIT: I tried compiling the driver from the non-root account, and I'm pretty sure this is your problem.
If you do not know your root password, go to "System>Administration>Users and Groups"

Click on "root" and choose "Properties". Set the password by hand, and press OK.

Re-extract the driver source.

Open a terminal, type "su", without quotes

type the root password

run
./configure
make
make install

and again, this can take a little while.

If there is another problem or the same problem, please let me know, I want everyone's sound in this thread to work :D

---

### Post by reinderien on 2007-10-07
> **sauronsmatrix said:**
> That is very strange....
are you logged in as the root account?


I wasn't the first time I tried, but when I tried all of the commands again with root, I had the same output.

---

### Post by sauronsmatrix on 2007-10-07
are all of these installed?

po-debconf
debhelper
quilt
alsa-base
libc6-dev

They are required for the compilation process

---

### Post by reinderien on 2007-10-07
Well, after installing quilt, make, make install, and reboot, dmesg gives:

```

(...)
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   17.312000] snd_hda_intel: Unknown symbol snd_ctl_add
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   17.312000] snd_hda_intel: Unknown symbol snd_pcm_new
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   17.312000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_card_register
[   17.312000] snd_hda_intel: Unknown symbol snd_card_register
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_card_free
[   17.312000] snd_hda_intel: Unknown symbol snd_card_free
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   17.312000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   17.312000] snd_hda_intel: Unknown symbol snd_card_proc_new
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   17.312000] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_dma_free_pages
[   17.312000] snd_hda_intel: Unknown symbol snd_dma_free_pages
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   17.312000] snd_hda_intel: Unknown symbol snd_ctl_new1
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_component_add
[   17.312000] snd_hda_intel: Unknown symbol snd_component_add
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_card_new
[   17.312000] snd_hda_intel: Unknown symbol snd_card_new
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   17.312000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   17.312000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   17.312000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   17.312000] snd_hda_intel: Unknown symbol snd_ctl_elem_read
[   17.312000] snd_hda_intel: Unknown symbol snd_ctl_elem_write
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   17.312000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   17.312000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   17.316000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   17.316000] snd_hda_intel: disagrees about version of symbol snd_device_new
[   17.316000] snd_hda_intel: Unknown symbol snd_device_new
[   17.316000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   17.316000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   17.316000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   17.316000] snd_hda_intel: Unknown symbol snd_card_disconnect
[   17.316000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   17.316000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   17.316000] snd_hda_intel: disagrees about version of symbol snd_dma_alloc_pages
[   17.316000] snd_hda_intel: Unknown symbol snd_dma_alloc_pages
[   17.316000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   17.316000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   17.316000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   17.316000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
(...)

```

---

### Post by sauronsmatrix on 2007-10-07
WIRELESS IS WORKING!!! :guitar::guitar::guitar:

**[COLOR=Red]Things in red can differ from computer to computer[/COLOR]**

Heres how to do it on our HP's! :P (Huge thanks to [paperdiesel]("http://ubuntuforums.org/member.php?u=44591") for this)

As always, type su, and enter the root password.

1) [COLOR=Red]Get rid of all traces of older versions, if they exist.[/COLOR]
```
sudo rmmod ndiswrapper
sudo ndiswrapper -e bcmwl5
sudo apt-get remove ndiswrapper-utils
```2) Download ndiswrapper [here]("http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.52.tar.gz?modtime=1201988892&big_mirror=0"),

3) Download drivers for [tx1000z]("http://rapidshare.com/files/79251578/driver.zip"), or [[COLOR=Red]others[/COLOR]]("http://welcome.hp.com/country/us/en/support.html").

4) Get necessary dependencies.
```
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
```5) Extract ndiswrapper to some [COLOR=Red]folder[/COLOR], blacklist bcm43xx firmware.
```
sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
```6) Compile ndiswrapper.
```
cd [COLOR=Red](FOLDER YOU EXTRACTED IT TO)[/COLOR]
sudo make uninstall
sudo make uninstall
sudo make uninstall
sudo make uninstall
```**(YES, do the uninstall several times)**
```

sudo make
sudo make install
```7) Extract wireless drivers **(SKIP STEP IF YOU HAVE A TX1000z and you took the rapidshare driver)**: note this step can differ between models.
Note: The unzip command does not work. Instead, use wine to emulate it in the Windows API
```

wine spxxxxx.exe
```8) Install the drivers!```

cd [COLOR=Red]DRIVER-DIRECTORY[/COLOR]
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
```9) Add ndiswrapper to system```

sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo echo ndiswrapper >> /etc/modules
```10) RESTART, Very important.

11) Test it out!
```
sudo iwlist scanning
```12) Ask away if you get any problems.

-----------------------------------------------------------------------------------------------------

Hardy Heron.

Additional steps that must be performed:
1) Add the new hardy driver to the blacklist (/etc/modprobe.d/blacklist):
```
blacklist ssb
```2) Add these lines to the etc/rc.local file.
```
rmmod ohci_hcd
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ohci_hcd
```

---

### Post by sauronsmatrix on 2007-10-07
reinderien my friend, you are in luck! that is a good error message as weird as that sounds.

First, type  in a terminal
```
uname -a
```

It is VERY important that you write down the number. Mine happens to be 2.6.22-13.

From my earlier [post]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235"):
---------------------
> 
There are two copies of the snd_hda_intel,ko file lurking in /lib/modules:
```
[COLOR="Blue"]/lib/modules/2.6.22-13-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
[COLOR="DarkGreen"]/lib/modules/2.6.22-13-generic/kernel/sound/pci/hda/snd-hda-intel.ko[/COLOR]
```

To solve this problem, run these commands in the a terminal under "su" privileges
```
rm [COLOR="Blue"]/lib/modules/2.6.22-13-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
ln -s [COLOR="DarkGreen"]/lib/modules/2.6.22-13-generic/kernel/sound/pci/hda/snd-hda-intel.ko[/COLOR] [COLOR="Blue"]/lib/modules/2.6.22-13-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
```

gedit /etc/modules

Add these lines to the bottom:
```
snd-hwdep
snd-hda-intel
```

--------------------------
that should do it, after one restart. If it doesnt, just continue asking away.

---

### Post by reinderien on 2007-10-07
Okay, well after those, dmesg says

```

[   17.412000] snd_hda_intel: Unknown symbol snd_hwdep_new

```

---

### Post by sauronsmatrix on 2007-10-07
awww this is becoming a real brain teaser now

did you add both 
```
snd-hwdep
snd-hda-intel
```
to /etc/modules?

---

### Post by reinderien on 2007-10-07
> **sauronsmatrix said:**
> 
did you add both 
```
snd-hwdep
snd-hda-intel
```
to /etc/modules?

Yep.

---

### Post by sauronsmatrix on 2007-10-07
[Sound]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235") working
[Wireless]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257") working

Cheers

---

### Post by reinderien on 2007-10-07
> **sauronsmatrix said:**
> [Sound]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235") working
[Wireless]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257") working

Cheers

That's.. what I did..?

---

### Post by Armein Z. R. Langi on 2007-10-07
> **dodgy_geeza said:**
> .

A big issue that I have atm, which might be related to posts from other people, is that the noapic option needs to be used, otherwise the system hangs. This however causes my 2nd cpu to run at 100% constantly. I've been through a whole multitude of boot options in various combo's, but none of them seem to work properly without the noapic.

Dodgy

I noticed similar problem with Ubuntu 7.10 beta while using the default nvdia driver. However after I installed new nvidia restricted driver, both CPUs run normally, and the computer was not too hot.  Not sure why, though :-)

---

### Post by sauronsmatrix on 2007-10-07
AWESOME!!!!!!!!11

I just got my tablet touch screen function working!

I can try to help people with those issues! Fire away.:popcorn::popcorn::popcorn:

---

### Post by dodgy_geeza on 2007-10-08
> **Armein Z. R. Langi said:**
> I noticed similar problem with Ubuntu 7.10 beta while using the default nvdia driver. However after I installed new nvidia restricted driver, both CPUs run normally, and the computer was not too hot.  Not sure why, though :-)

It happens even on a virgin system, you can boot with init=/bin/bash , and you still have the 100% cpu issue. It seems to be the USB2 controller generating a shed-load of interrupts, which because of the disabled APIC, one of the CPU's gets hammered.

I've still yet to find a workable conbination of boot options for my lappy to remove the 100% issue, which is a nightmare :'( I will be having another go this weekend coming, or at some point tomorrow (time permitting). I'm also going to try some different operating systems, as I read on another forum that it is something to do with the Ubuntu kernel, and how they have compiled USB support. Might role a vanilla kernel to see if there is a difference ;)

Dodgy

---

### Post by reinderien on 2007-10-08
> **sauronsmatrix said:**
> Okay, so install these five, (e.g. using Synaptic Package Manager).
[INDENT]po-debconf
debhelper
quilt
alsa-base
libc6-dev
[/INDENT]

Then, install [alsa-driver]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2"):

1) Extract archive to some[COLOR="Red"] folder[/COLOR].

2) Open up a terminal.
make yourself the root user with "su"

3) go to the [COLOR="Red"]folder[/COLOR] with the "cd" command

4) Run these commands in this order:
[INDENT]./configure
make
make install
[/INDENT]

Note: Yes, this process can take like** 3 minutes**.

When its installed, add this line to/etc/modprobe.d/alsa-base [use command "gedit /etc/modprobe.d/alsa-base" under "su" priveleges]:
[INDENT]
options snd-hda-intel model=hp[/INDENT]

Restart your computer, and bam. It should be working. If you do not understand my instructions, feel free to ask me to clarify.

***_[COLOR="Navy"]NEW PROBLEM! It seems that when you update the kernel, the drivers stop working. A solution is at hand:[/COLOR]_***

**NOTE**: Change the [COLOR="Blue"]kernel version [/COLOR]as necessary.

There are two copies of the snd_hda_intel,ko file lurking in /lib/modules:
```
[COLOR="Blue"]/lib/modules/2.6.22-13-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
[COLOR="DarkGreen"]/lib/modules/2.6.22-13-generic/kernel/sound/pci/hda/snd-hda-intel.ko[/COLOR]
```

To solve this problem, run these commands in the a terminal under "su" privileges
```
rm [COLOR="Blue"]/lib/modules/2.6.22-13-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
ln -s [COLOR="DarkGreen"]/lib/modules/2.6.22-13-generic/kernel/sound/pci/hda/snd-hda-intel.ko[/COLOR] [COLOR="Blue"]/lib/modules/2.6.22-13-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
```

gedit /etc/modules

Add these lines to the bottom:
```
snd-hwdep
snd-hda-intel
```

A HUGE thanks to [benguin]("http://ubuntuforums.org/member.php?u=9893"), who framed the solution for the kernel update bug.

To this, you must add:
```

depmod -e -F /boot/System.map-[your kernel name]

```

Otherwise the module dependencies are messed up when you reboot.

---

### Post by Hitnrun on 2007-10-08
Has someone tried to use the bluetooth adapter? I can't find it on lspci neither usbview, does someone knows which hardware is used for it?

---

### Post by sauronsmatrix on 2007-10-08
two things,
one, i dont see how this command helps:
depmod -e -F /boot/System.map-[your kernel name]

two,

my paging file is 4.6 GB, and its never used. How do turn it off?

---

### Post by Armein Z. R. Langi on 2007-10-08
> **sauronsmatrix said:**
> AWESOME!!!!!!!!11

I just got my tablet touch screen function working!

I can try to help people with those issues! Fire away.:popcorn::popcorn::popcorn:

Mine too, thanks for the sugestions to use egalax TouchKit USB.  I think this is the best way.  Now I have a real Linux Tablet PC. :)

Anyway, my TX 1209 AU still has problems with wireless LAN though.  Ubuntu 7.10 beta allows me to get restricted broadcom driver.  Although I have switched the wireless button on, but still cannot find and connect to an access point.  Maybe I will go back to ndiswrapper solution.

---

### Post by sauronsmatrix on 2007-10-08
the ndiswrapper solution definitely works.

I can help you with it.

---

### Post by Armein Z. R. Langi on 2007-10-08
> **dodgy_geeza said:**
> It happens even on a virgin system, you can boot with init=/bin/bash , and you still have the 100% cpu issue. It seems to be the USB2 controller generating a shed-load of interrupts, which because of the disabled APIC, one of the CPU's gets hammered.

I've still yet to find a workable conbination of boot options for my lappy to remove the 100% issue, which is a nightmare :'( 

Dodgy
fther
Yes I know, it is a nightmare indeed. I don't know what the solution is.

After following this thread, I suspect there is a bug with tx1000 bios, forcing us to use noapic boot option, hence creating a bunch of problems.  I am wondering if there is any latest bios upgrade from HP.

Other possibility is the problem with the kernel.  I have quadraple boot on my tx1209AU: vista, ubuntu 7.04, ubuntu 7.10, and puppy linux. I can then try several kernels to see if the problem is consistent across platforms.   If Puppy Linux (or alternatively Damn Small Linux) does not have that 100% processor load issue, then it is ubuntu kernel the needed to be fixed, right?

Side notes:
1. I find Puppy Linux is handy when everything else fails :-) , although its superuser privillage by default is so dangerous in messing ups ubuntu files.

2. On my tx 1209AU I think it is best to have two partitions for two ubuntus with different versions (mine 7.04 and 7.10), but both ubuntus share the same /home directory.  This is to anticipate new version that comes every 6 months.  When 8.04 arrives, I will delete 7.04 for that 8.04 etc, while keep on having at least one working system :-)

Good luck man

---

### Post by reinderien on 2007-10-08
> **sauronsmatrix said:**
>  [...] i dont see how this command helps:
depmod -e -F /boot/System.map-[your kernel name]


As I understand it, depmod changes the dependencies of kernel modules to make sure that the proper modules are loaded, and that they're loaded in the correct order. My alsa driver didn't start until I did this.

---

### Post by Armein Z. R. Langi on 2007-10-09
> **sauronsmatrix said:**
> the ndiswrapper solution definitely works.

I can help you with it.

Thanks, I got it working with ndiswrapper.  BCM 4312 can reach 54 Mbps with this solution.  The restriction driver solution fails to work on my computer.

So Gutsy 7.10 beta AMD 64 runs well and fast on tx1209AU, with following features

1. nvidia new restricted driver runs well.    I can run compiz.  With AC power, glxgears gives me 1716.144 bps.  With baterry power, it runs 1014.885 FPS.

2. wireless: 54 mbps with ndiswrapper.

3. Sound, headphone, button control function well with alsa driver, downloaded from suse, and compile locally.

4. touchscreen: run well with egalax touchkit.

5. All special Fn buttons work..

Problems:
- boot must use noapic option
- camera stil not working yet
- fingerprint: no idea yet

BTW: I have intalled ubuntu studio splash, and the computer now looks great!  

Overall: tx1000 + gutsy is a lovely notebook/ Linux tablet PC!  I though I had made a mistake purchasing this computer when I discovered so many ubuntu running problems.  But thanks to you guys in this forum (I have been following this for two months), this machine is now my favourite.. :-)

Cheers!

---

### Post by Cuppa-Chino on 2007-10-09
> **Armein Z. R. Langi said:**
> Thanks, I got it working with ndiswrapper.  BCM 4312 can reach 54 Mbps with this solution.  The restriction driver solution fails to work on my computer.

4. touchscreen: run well with egalax touchkit.

5. All special Fn buttons work..



Hi Armein:

wrt 5 : does that include all buttons around the screen including the square circle on the bottom edge?

if so how did you configure that, it does not provide any xev output for me

thx

---

### Post by sauronsmatrix on 2007-10-09
recent kernel update has once again disabled sound.

[fix it]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235").

---

### Post by sauronsmatrix on 2007-10-09
VERY STRANGE THING I OBSERVED!!!!

When I turn on my computer with a USB mouse plugged in, the touchscreen fails to work.... And the USB mouse sensitivity is sluggish and low.

However, when it isnt plugged in, the touchscreen works perfectly, and I can then plug in the USB mouse and it will work.

:( any idea why this happens or how to fix this?

---

### Post by Cuppa-Chino on 2007-10-09
> **sauronsmatrix said:**
> WIRELESS IS WORKING!!! :guitar::guitar::guitar:

**[COLOR="Red"]Things in red can differ from computer to computer[/COLOR]**

As always, type su, and enter the root password.

7) Extract wireless drivers: note this step can differ between models.
```
unzip -a [COLOR="Red"]sp36684.exe[/COLOR]

```

11) Test it out!
```
sudo iwlist scanning
```

12) Ask away if you get any problems.

couple of things --- gutsy problems again!
7) does not work for me>
```
Desktop$ unzip -a sp36542.exe 
Archive:  sp36542.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of sp36542.exe or
        sp36542.exe.zip, and cannot find sp36542.exe.ZIP, period.

```

11) finds my network

but then I CANNOT connect to my WPA WLAN, I just connect, any pointers are welcome

---

### Post by sauronsmatrix on 2007-10-09
that is strange.

try using "wine" to extract the files

---

### Post by mikedep333 on 2007-10-09
> **sauronsmatrix said:**
> that is strange.

try using "wine" to extract the files

Yeah, that's what I had to do also. Install the package "wine" and then browse to the directory with sp36684.exe and run ```
wine sp36684.exe
``` (or right click on it, chose open with, open with other application, custom command, "wine".

---

### Post by dodgy_geeza on 2007-10-10
Just thought I would give some quick input...

Saurons, in regards to the USB mouse issue... which device is labelled as your CorePointer in your xorg.conf? I've labelled the touchscreen as mine, and don't have any issues with a USB mouse being connected.

Cuppa-Chino, chances are that it's a packed exe file, install both cabextract and unshield, the latter being the one you prolly want to use. That should unpack the file for you. I can confirm on mine that using ndiswrapper I can connect to WEP/WPA/WPA2 networks with no hassle.

Dodgy

---

### Post by Cuppa-Chino on 2007-10-10
as said in my post I have wirless half working:

```
sudo iwlist scanning
```

shows all my neighbours networks and mine, but I just cannot make a connection to **_my_** WPA .... it would be really helpful if people could give me pointers, as this is the one area where I am struggling to make gutsy work (and its frustrating as whathaveyounot)

NOW WPA is not working in feisty either, I have tears in my eyes this stink beyond comprehension

---

### Post by sauronsmatrix on 2007-10-10
dodgy, this is my xorg.conf section:
```

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
	Inputdevice	"touchscreen"	"CorePointer"
EndSection
```

thanks,

saurons

---

### Post by doryphore on 2007-10-10
Hi to all,

i haven't yet installed ubuntu on my notebook ; but i can boot with a livecd (with some options like nopaic i think) and i don't get this 100% CPU issue.
So a question is : if i install gutsy on my hp, how will th cpu behave ?

Thank you

Doryphore

---

### Post by sauronsmatrix on 2007-10-10
mine is fine. it is fully functional, and the cpu is almost never under pressure due to ubuntu's awesomeness.

---

### Post by Armein Z. R. Langi on 2007-10-10
> **Cuppa-Chino said:**
> Hi Armein:

wrt 5 : does that include all buttons around the screen including the square circle on the bottom edge?

if so how did you configure that, it does not provide any xev output for me

thx

No they do not work yet.. only those Fn keys on the keyboard.
Sorry for late reply. cheers

---

### Post by Armein Z. R. Langi on 2007-10-10
> **sauronsmatrix said:**
> VERY STRANGE THING I OBSERVED!!!!

When I turn on my computer with a USB mouse plugged in, the touchscreen fails to work.... And the USB mouse sensitivity is sluggish and low.

:( any idea why this happens or how to fix this?

Maybe replace the mouse with new one... :-)

One possibility is that the mouse draws too much electrical current from the USB chip, causing the USB circuit to function abnormally.

I experience similar situation when I used a USB CDMA modem.  To get around that, I had to use a USB cable with two plugs, to draw extra current from the other port.

If this is true in your case, perhaps something wrong with the mouse you have, because a normal USB mouse is not suppose draw current too much.

---

### Post by Armein Z. R. Langi on 2007-10-10
> **doryphore said:**
> Hi to all,

i haven't yet installed ubuntu on my notebook ; but i can boot with a livecd (with some options like nopaic i think) and i don't get this 100% CPU issue.
So a question is : if i install gutsy on my hp, how will th cpu behave ?

Thank you

Doryphore

Hi, If the livecd works, the hard-drive install should work fine.

Mine does not have the 100% CPU problem, especially after I updated the nvidia driver to use restricted driver suggested by gutsy. 

Another option to consider is whether to install 32 bit version or AMD 64 bit version.  I installed both Fiesty 32 bit and, two months later, Gutsy 64 bit, and I found Gutsy 64 bit is much pleasant and fast to work with.  And all applications I need is available in the 64 bit edition.

Good luck...

---

### Post by sauronsmatrix on 2007-10-10
actually, the buttons do work.

Configure them in System>Preferences>Keyboard Shortcuts

---

### Post by dodgy_geeza on 2007-10-11
Saurons, looking at the order of your InputDevices, move the touchscreen to the top. It should take precidence this way. I've posted my xorg.conf file on here previously, have a looksie at that one as I don't have the problem.

Cuppa-chino, are you using NetworkMangager or the cmdline to connect to access points? I'm assuming that the access point you are trying to connect to is configured correctly and if it does have MAC filtering, has your card's MAC address added to the allow list. If you can give some specifics, we should be able to help you.

Also, what model lappy do you all have? Im interested in what models/boot options people are using, that don't have the 100% CPU issue. Mine is a tx1250ea, which unfortunatly suffers from the 100% CPU bug when booting with noapic :-(

Dodgy

---

### Post by Cuppa-Chino on 2007-10-11
> **sauronsmatrix said:**
> actually, the buttons do work.

Configure them in System>Preferences>Keyboard Shortcuts

ok, earlier in the thread we discussed the various media keys. most work on my laptop (with exception of the cog wheel and the squared circle with arrows on the lower edge of the screen), is this what you mean

---

### Post by sauronsmatrix on 2007-10-11
yea the media keys. someone said theyre not working, but they work fine for me.

---

### Post by sauronsmatrix on 2007-10-12
Yesterday, a [release candidate]("http://www.ubuntu.com/news/ubuntu-7.10rc") for Ubuntu 7.10 was released.


Does anyone know if 7.10 Beta with upgrades will become this version?

And later down the road, will our 7.10 Beta's become 7.10 Finals?

---

### Post by guadafan on 2007-10-12
HEY!!  I have just tested Ubuntu Mint and detects the touchscreen but I need calibrate because the mouse is desplazated. I think that it detected like a tablet WACOM and I works very smooth.

I supouse that calibrate.sh will not work, or am I wrong?


Other thing, I haven't read this ENORMOUS thread, could someone post a message with the most important steps for configure all TX1000 hardware?

We could do a little script for automatic configuring of this laptop under Ubuntu.

---

### Post by sauronsmatrix on 2007-10-12
hey man

[sound]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235")
[wireless]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257")
[touchscreen]("http://ubuntuforums.org/showpost.php?p=2792971&postcount=16")

hope it helps.

---

### Post by alan_lin on 2007-10-13
I have faced some problem as following config.log while install sound driver and type "./configure" :(

The /home/alan/ location where i placed dirver alsa-dirver-hg20071012  
I have also tried this alsa-driver-1.0.15rc3.tar.bz2 version,but result was same. 
Could someone tell me how to do solve it? Thanks

Config.log
---------------------------------------------------------------
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.61.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = alan-laptop
uname -m = x86_64
uname -r = 2.6.22-14-generic
uname -s = Linux
uname -v = #1 SMP Wed Oct 10 05:28:36 GMT 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:2101: checking for gcc
configure:2117: found /usr/bin/gcc
configure:2128: result: gcc
configure:2366: checking for C compiler version
configure:2373: gcc --version >&5
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2376: $? = 0
configure:2383: gcc -v >&5
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release x86_64-linux-gnu
Thread model: posix
gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
configure:2386: $? = 0
configure:2393: gcc -V >&5
gcc: '-V' option must have argument
configure:2396: $? = 1
configure:2419: checking for C compiler default output file name
configure:2446: gcc    conftest.c  >&5
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status
configure:2449: $? = 1
configure:2487: result: 
configure: failed program was:
| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:2494: error: C compiler cannot create executables
See `config.log' for more details.

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_prog_ac_ct_CC=gcc

## ----------------- ##
## Output variables. ##
## ----------------- ##

AR=''
ARCH=''
AS=''
CC='gcc'
CFLAGS=''
CONFIG_AC97_BUS=''
CONFIG_ALPHA=''
CONFIG_ARCH_AT91=''
CONFIG_ARCH_PXA=''
CONFIG_ARCH_S3C2410=''
CONFIG_ARCH_SA1100=''
CONFIG_ARM=''
CONFIG_ARM_AMBA=''
CONFIG_ATMEL_SSC=''
CONFIG_BROKEN=''
CONFIG_CPU_SUBTYPE_SH7760=''
CONFIG_EXPERIMENTAL=''
CONFIG_FW_LOADER=''
CONFIG_GSC=''
CONFIG_HAS_DMA=''
CONFIG_HAS_IOMEM=''
CONFIG_HAS_IOPORT=''
CONFIG_HIGH_RES_TIMERS=''
CONFIG_HPET=''
CONFIG_I2C=''
CONFIG_I2C_POWERMAC=''
CONFIG_I2C_SENSOR=''
CONFIG_INPUT=''
CONFIG_ISA=''
CONFIG_ISAPNP=''
CONFIG_ISAPNP_KERNEL=''
CONFIG_ISA_DMA_API=''
CONFIG_L3=''
CONFIG_MACH_ETI_B1=''
CONFIG_MACH_ETI_C1=''
CONFIG_MACH_NEO1973_GTA01=''
CONFIG_MACH_POODLE=''
CONFIG_MACH_SMDK2443=''
CONFIG_MACH_TOSA=''
CONFIG_MIPS=''
CONFIG_PARISC=''
CONFIG_PARPORT=''
CONFIG_PCI=''
CONFIG_PCMCIA=''
CONFIG_PM=''
CONFIG_PNP=''
CONFIG_PNP_KERNEL=''
CONFIG_PPC32=''
CONFIG_PPC64=''
CONFIG_PPC=''
CONFIG_PPC_PMAC=''
CONFIG_PROC_FS=''
CONFIG_PS3_PS3AV=''
CONFIG_PXA_SHARP_C7XX=''
CONFIG_PXA_SHARP_CXX00=''
CONFIG_RTC=''
CONFIG_SBUS=''
CONFIG_SGI=''
CONFIG_SH_DMABRG=''
CONFIG_SH_DREAMCAST=''
CONFIG_SND=''
CONFIG_SND_AC97_CODEC=''
CONFIG_SND_AC97_POWER_SAVE=''
CONFIG_SND_AC97_POWER_SAVE_DEFAULT=''
CONFIG_SND_AD1816A=''
CONFIG_SND_AD1848=''
CONFIG_SND_AD1848_LIB=''
CONFIG_SND_AD1889=''
CONFIG_SND_ADLIB=''
CONFIG_SND_AICA=''
CONFIG_SND_ALI5451=''
CONFIG_SND_ALS100=''
CONFIG_SND_ALS300=''
CONFIG_SND_ALS4000=''
CONFIG_SND_AOA=''
CONFIG_SND_AOA_FABRIC_LAYOUT=''
CONFIG_SND_AOA_ONYX=''
CONFIG_SND_AOA_SOUNDBUS=''
CONFIG_SND_AOA_SOUNDBUS_I2S=''
CONFIG_SND_AOA_TAS=''
CONFIG_SND_AOA_TOONIE=''
CONFIG_SND_ARMAACI=''
CONFIG_SND_ASIHPI=''
CONFIG_SND_AT73C213=''
CONFIG_SND_AT73C213_TARGET_BITRATE=''
CONFIG_SND_AT91_SOC=''
CONFIG_SND_AT91_SOC_ETI_B1_WM8731=''
CONFIG_SND_AT91_SOC_ETI_SLAVE=''
CONFIG_SND_AT91_SOC_SSC=''
CONFIG_SND_ATIIXP=''
CONFIG_SND_ATIIXP_MODEM=''
CONFIG_SND_AU1X00=''
CONFIG_SND_AU8810=''
CONFIG_SND_AU8820=''
CONFIG_SND_AU8830=''
CONFIG_SND_AZT2320=''
CONFIG_SND_AZT3328=''
CONFIG_SND_BIT32_EMUL=''
CONFIG_SND_BT87X=''
CONFIG_SND_BT87X_OVERCLOCK=''
CONFIG_SND_CA0106=''
CONFIG_SND_CMI8330=''
CONFIG_SND_CMI8788=''
CONFIG_SND_CMIPCI=''
CONFIG_SND_CS4231=''
CONFIG_SND_CS4231_LIB=''
CONFIG_SND_CS4232=''
CONFIG_SND_CS4236=''
CONFIG_SND_CS4281=''
CONFIG_SND_CS46XX=''
CONFIG_SND_CS46XX_NEW_DSP=''
CONFIG_SND_CS5530=''
CONFIG_SND_CS5535AUDIO=''
CONFIG_SND_DARLA20=''
CONFIG_SND_DARLA24=''
CONFIG_SND_DATE=''
CONFIG_SND_DEBUG=''
CONFIG_SND_DEBUG_DETECT=''
CONFIG_SND_DEBUG_MEMORY=''
CONFIG_SND_DT019X=''
CONFIG_SND_DUMMY=''
CONFIG_SND_DYNAMIC_MINORS=''
CONFIG_SND_ECHO3G=''
CONFIG_SND_EMU10K1=''
CONFIG_SND_EMU10K1X=''
CONFIG_SND_ENS1370=''
CONFIG_SND_ENS1371=''
CONFIG_SND_ES1688=''
CONFIG_SND_ES18XX=''
CONFIG_SND_ES1938=''
CONFIG_SND_ES1968=''
CONFIG_SND_ES968=''
CONFIG_SND_FM801=''
CONFIG_SND_FM801_TEA575X=''
CONFIG_SND_FM801_TEA575X_BOOL=''
CONFIG_SND_GINA20=''
CONFIG_SND_GINA24=''
CONFIG_SND_GUSCLASSIC=''
CONFIG_SND_GUSEXTREME=''
CONFIG_SND_GUSMAX=''
CONFIG_SND_GUS_SYNTH=''
CONFIG_SND_HARMONY=''
CONFIG_SND_HDA_CODEC_ANALOG=''
CONFIG_SND_HDA_CODEC_ATIHDMI=''
CONFIG_SND_HDA_CODEC_CMEDIA=''
CONFIG_SND_HDA_CODEC_CONEXANT=''
CONFIG_SND_HDA_CODEC_REALTEK=''
CONFIG_SND_HDA_CODEC_SI3054=''
CONFIG_SND_HDA_CODEC_SIGMATEL=''
CONFIG_SND_HDA_CODEC_VIA=''
CONFIG_SND_HDA_GENERIC=''
CONFIG_SND_HDA_HWDEP=''
CONFIG_SND_HDA_INTEL=''
CONFIG_SND_HDA_POWER_SAVE=''
CONFIG_SND_HDA_POWER_SAVE_DEFAULT=''
CONFIG_SND_HDSP=''
CONFIG_SND_HDSPM=''
CONFIG_SND_HPET=''
CONFIG_SND_HWDEP=''
CONFIG_SND_ICE1712=''
CONFIG_SND_ICE1724=''
CONFIG_SND_INDIGO=''
CONFIG_SND_INDIGODJ=''
CONFIG_SND_INDIGOIO=''
CONFIG_SND_INTEL8X0=''
CONFIG_SND_INTEL8X0M=''
CONFIG_SND_INTERWAVE=''
CONFIG_SND_INTERWAVE_STB=''
CONFIG_SND_KERNELDIR=''
CONFIG_SND_KORG1212=''
CONFIG_SND_KORG1212_FIRMWARE_IN_KERNEL=''
CONFIG_SND_LAYLA20=''
CONFIG_SND_LAYLA24=''
CONFIG_SND_LOOPBACK=''
CONFIG_SND_MAESTRO3=''
CONFIG_SND_MAESTRO3_FIRMWARE_IN_KERNEL=''
CONFIG_SND_MIA=''
CONFIG_SND_MIRO=''
CONFIG_SND_MIXART=''
CONFIG_SND_MIXER_OSS=''
CONFIG_SND_MONA=''
CONFIG_SND_MPU401=''
CONFIG_SND_MPU401_UART=''
CONFIG_SND_MSND_PINNACLE=''
CONFIG_SND_MTPAV=''
CONFIG_SND_MTS64=''
CONFIG_SND_MVERSION=''
CONFIG_SND_NM256=''
CONFIG_SND_OPL3SA2=''
CONFIG_SND_OPL3_LIB=''
CONFIG_SND_OPL4_LIB=''
CONFIG_SND_OPTI92X_AD1848=''
CONFIG_SND_OPTI92X_CS4231=''
CONFIG_SND_OPTI93X=''
CONFIG_SND_OSSEMUL=''
CONFIG_SND_PC98_CS4232=''
CONFIG_SND_PCM=''
CONFIG_SND_PCM_OSS=''
CONFIG_SND_PCM_OSS_PLUGINS=''
CONFIG_SND_PCM_XRUN_DEBUG=''
CONFIG_SND_PCSP=''
CONFIG_SND_PCXHR=''
CONFIG_SND_PDAUDIOCF=''
CONFIG_SND_PDPLUS=''
CONFIG_SND_PORTMAN2X4=''
CONFIG_SND_POWERMAC=''
CONFIG_SND_POWERMAC_AUTO_DRC=''
CONFIG_SND_PS3=''
CONFIG_SND_PS3_DEFAULT_START_DELAY=''
CONFIG_SND_PXA2XX_AC97=''
CONFIG_SND_PXA2XX_I2SOUND=''
CONFIG_SND_PXA2XX_PCM=''
CONFIG_SND_PXA2XX_SOC=''
CONFIG_SND_PXA2XX_SOC_AC97=''
CONFIG_SND_PXA2XX_SOC_CORGI=''
CONFIG_SND_PXA2XX_SOC_I2S=''
CONFIG_SND_PXA2XX_SOC_POODLE=''
CONFIG_SND_PXA2XX_SOC_SPITZ=''
CONFIG_SND_PXA2XX_SOC_TOSA=''
CONFIG_SND_RAWMIDI=''
CONFIG_SND_RIPTIDE=''
CONFIG_SND_RME32=''
CONFIG_SND_RME9652=''
CONFIG_SND_RME96=''
CONFIG_SND_RTCTIMER=''
CONFIG_SND_S3C2410=''
CONFIG_SND_S3C2443_SOC_AC97=''
CONFIG_SND_S3C24XX_SOC=''
CONFIG_SND_S3C24XX_SOC_I2S=''
CONFIG_SND_S3C24XX_SOC_NEO1973_WM8753=''
CONFIG_SND_S3C24XX_SOC_SMDK2443_WM9710=''
CONFIG_SND_SA11XX_UDA1341=''
CONFIG_SND_SB16=''
CONFIG_SND_SB16_CSP=''
CONFIG_SND_SB16_CSP_FIRMWARE_IN_KERNEL=''
CONFIG_SND_SB16_DSP=''
CONFIG_SND_SB8=''
CONFIG_SND_SB8_DSP=''
CONFIG_SND_SBAWE=''
CONFIG_SND_SB_COMMON=''
CONFIG_SND_SC6000=''
CONFIG_SND_SEQUENCER=''
CONFIG_SND_SEQUENCER_OSS=''
CONFIG_SND_SEQ_DUMMY=''
CONFIG_SND_SEQ_RTCTIMER_DEFAULT=''
CONFIG_SND_SERIALMIDI=''
CONFIG_SND_SERIAL_U16550=''
CONFIG_SND_SGALAXY=''
CONFIG_SND_SH7760_AC97=''
CONFIG_SND_SOC=''
CONFIG_SND_SOC_AC97_BUS=''
CONFIG_SND_SOC_AC97_CODEC=''
CONFIG_SND_SOC_CS4270=''
CONFIG_SND_SOC_CS4270_HWMUTE=''
CONFIG_SND_SOC_CS4270_VD33_ERRATA=''
CONFIG_SND_SOC_PCM_SH7760=''
CONFIG_SND_SOC_SH4_HAC=''
CONFIG_SND_SOC_SH4_SSI=''
CONFIG_SND_SOC_WM8731=''
CONFIG_SND_SOC_WM8750=''
CONFIG_SND_SOC_WM8753=''
CONFIG_SND_SOC_WM9712=''
CONFIG_SND_SONICVIBES=''
CONFIG_SND_SSCAPE=''
CONFIG_SND_SUN_AMD7930=''
CONFIG_SND_SUN_CS4231=''
CONFIG_SND_SUN_DBRI=''
CONFIG_SND_SUPPORT_OLD_API=''
CONFIG_SND_TIMER=''
CONFIG_SND_TRIDENT=''
CONFIG_SND_USB_AUDIO=''
CONFIG_SND_USB_CAIAQ=''
CONFIG_SND_USB_CAIAQ_INPUT=''
CONFIG_SND_USB_USX2Y=''
CONFIG_SND_VERBOSE_PRINTK=''
CONFIG_SND_VERBOSE_PROCFS=''
CONFIG_SND_VERSION='1.0.15rc3'
CONFIG_SND_VIA82XX=''
CONFIG_SND_VIA82XX_MODEM=''
CONFIG_SND_VIRMIDI=''
CONFIG_SND_VX222=''
CONFIG_SND_VXPOCKET=''
CONFIG_SND_VX_LIB=''
CONFIG_SND_WAVEFRONT=''
CONFIG_SND_WAVEFRONT_FIRMWARE_IN_KERNEL=''
CONFIG_SND_YMFPCI=''
CONFIG_SND_YMFPCI_FIRMWARE_IN_KERNEL=''
CONFIG_SOC_AU1000=''
CONFIG_SOC_AU1100=''
CONFIG_SOC_AU1500=''
CONFIG_SOUND=''
CONFIG_SOUND_PRIME=''
CONFIG_SPARC32=''
CONFIG_SPARC64=''
CONFIG_SPARC=''
CONFIG_SUPERH64=''
CONFIG_SUPERH=''
CONFIG_USB=''
CONFIG_VIDEO_DEV=''
CONFIG_VIDEO_V4L1=''
CONFIG_X86=''
CONFIG_X86_32=''
CONFIG_X86_64=''
CONFIG_X86_PC9800=''
CONFIG_X86_PC=''
CPP=''
CPPFLAGS=''
CROSS_COMPILE=''
DEFS=''
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP=''
EXEEXT=''
EXTRA_INCLUDES=''
GENKSYMS=''
GREP=''
INSTALL_DATA=''
INSTALL_PROGRAM=''
INSTALL_SCRIPT=''
KERNEL_INC=''
KLD=''
LDFLAGS=''
LIBOBJS=''
LIBS=''
LTLIBOBJS=''
MAKE_ADDS=''
NEW_KBUILD=''
OBJEXT=''
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
RANLIB=''
SHELL='/bin/bash'
SRCDIR=''
ac_ct_CC='gcc'
bindir='${exec_prefix}/bin'
build_alias=''
c_opts=''
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE}'
dvidir='${docdir}'
exec_prefix='NONE'
host_alias=''
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
kaversion=''
kextraversion=''
kpatchlevel=''
ksublevel=''
kversion=''
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localedir='${datarootdir}/locale'
localstatedir='${prefix}/var'
m_opts=''
mandir='${datarootdir}/man'
moddir=''
moddir_tree=''
modsubdir=''
msmp=''
oldincludedir='/usr/include'
pdfdir='${docdir}'
prefix='NONE'
processor=''
program_transform_name='s,x,x,'
psdir='${docdir}'
sbindir='${exec_prefix}/sbin'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define PACKAGE_NAME ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define PACKAGE_STRING ""
#define PACKAGE_BUGREPORT ""

configure: exit 77

---

### Post by sauronsmatrix on 2007-10-13
you are logged in as root,

and have the** 5 dependencies** right?

---

### Post by sauronsmatrix on 2007-10-13
help!

I reinstalled ubuntu, and everything works fine, except the remote.

The battery is good, cuz it works on my friend's computer.

Also, my recepter is good, cuz it worked in the previous install.

Any clue how to get it to work?

---

### Post by Zamboniman on 2007-10-14
After I looked at a TX1000 in the store last week I thought I'd check the forums to see what kind of issues people might be having installing Ubuntu on them.  I was a bit concerned with all the hoops to jump through but the machine kept calling me so I broke down and bought one a couple of days ago.

Well, thanks to the wonderful help I've found in this thread I'm happy to report a resounding success!

My particular model is a TX1314ca.

Installed the RC of Gutsy.

Wireless:  works after using ndiswrapper - bcm43xx didn't work for me, even with fwcutter

Audio: works after compiling my own alsa module as mentioned in this thread.

Touchscreen:  works well thanks to the hints found here, with one issue (see below). I used Gutsy's evtouch driver and it seems to do the trick without having to compile or install my own.

Screen Rotate:  works fine.

Bluetooth: works in the limited testing I've done so far.

Booting/hanging/apic issues:  more or less sorted out. With noapic I was getting the 100% CPU issue, but managed to get the thing stable without noapic and with a whackload of other kernel options.  Seems OK so far, but I gotta keep on eye on this. I know others here have reported intermittent issues so we'll see.

Suspend: Works.  I didn't need to do anything special here.  It just worked.  Comes back up perfectly, with full usb, network, screen, backlight, etc.  This one was a major factor for me in not returning the laptop to the store.  I was sick of my old laptop never suspending properly in any linux distro I tried on it.  I'm wondering if it would come up so nicely with noapic.

Webcam: haven't tried it yet.  I suspect it'll work.  I doubt I'll use it much anyway.

Card Reader: haven't tried this yet either, but I suspect it'll work fine too.


Ok, now the touchscreen issue I mentioned above.  Everything works great but when I try and use the touchscreen to type something in xvkbd or any other on-screen keyboard I keep getting repeated letters.  Very annoying and so far I haven't been able to figure out a way to get this to work properly. 


Once again, thanks to all of the contributors to this thread that saved me probably days and days of googling and swearing getting some of these issues sorted out.

---

### Post by alan_lin on 2007-10-14
> **sauronsmatrix said:**
> you are logged in as root,

and have the** 5 dependencies** right?

Yes,I logged in as root,but i dont understand what "5 dependencies" is ? :confused:

Thanks

---

### Post by sauronsmatrix on 2007-10-14
the five dependencies are:

po-debconf
debhelper
quilt
alsa-base
libc6-dev

After installing these, try compiling the alsa driver.



Does anyone know how to make screen rotation work?

---

### Post by Cuppa-Chino on 2007-10-15
> **Armein Z. R. Langi said:**
> Thanks, I got it working with ndiswrapper.  BCM 4312 can reach 54 Mbps with this solution.  The restriction driver solution fails to work on my computer.

So Gutsy 7.10 beta AMD 64 runs well and fast on tx1209AU, with following features

1. nvidia new restricted driver runs well.    I can run compiz.  With AC power, glxgears gives me 1716.144 bps.  With baterry power, it runs 1014.885 FPS.

2. wireless: 54 mbps with ndiswrapper.

4. touchscreen: run well with egalax touchkit.

5. All special Fn buttons work..

Problems:
- boot must use noapic option
- camera stil not working yet
- fingerprint: no idea yet


couple of questions:
a) what are your boot parameters? just noapic? I am struggling to get ndiswrapper to load and I think its the boot parameters
==>> what do I mean with that: I install ndiswrapper and driver, ndiswrapper -l reports it all but it is never available
b) egalax touchkit, any pointers needed for that? could you put up the relevant xorg.conf sections

thanks

---

### Post by Cuppa-Chino on 2007-10-15
> **Zamboniman said:**
> 
Installed the RC of Gutsy.

Wireless:  works after using ndiswrapper - bcm43xx didn't work for me, even with fwcutter

Booting/hanging/apic issues:  more or less sorted out. With noapic I was getting the 100% CPU issue, but managed to get the thing stable without noapic and with a whackload of other kernel options.  Seems OK so far, but I gotta keep on eye on this. I know others here have reported intermittent issues so we'll see.

Suspend: Works.  I didn't need to do anything special here.  It just worked.  Comes back up perfectly, with full usb, network, screen, backlight, etc.  This one was a major factor for me in not returning the laptop to the store.  I was sick of my old laptop never suspending properly in any linux distro I tried on it.  I'm wondering if it would come up so nicely with noapic.


Hi are you using i386 or amd64 kernel ?

what are the boot options you use, thanks

---

### Post by Zamboniman on 2007-10-16
> **Cuppa-Chino said:**
> Hi are you using i386 or amd64 kernel ?

what are the boot options you use, thanks

Using the i386 kernel, Gutsy Gibbon release candidate.

My kernel options are as follows:

quiet splash irqpoll irqdebug pci=biosirq pci=nomsi acpi_osi="!Linux" acpi_os_name=
"Windows 2006"

Notice the lack of noapic and nolapic  Every now and then I'm getting a problem if I log out.  The machine locks up while attempting to go back to the gdm screen.  Maybe one in every 7 to 10 times. However, since I'm the only user and really never log out until I shut the thing down, this isn't an issue.  I only noticed it one time and then tested it by logging out and in a bunch of times in a row.  Suspend is still working great.  Since my last post I've tested the webcam and the card reader, and both work perfectly.

I still have to figure out the repeating letters thing with the touchscreen and xvkbd.

I'm liking this little computer more each day.

---

### Post by knodalyte on 2007-10-16
I have a tx1000z with 2 GB RAM, running Gutsy RC1, and have made good progress with major help from this thread.

I am using a boot option I have not seen mentioned before (plus several that have been recommended) and have interesting results.  It is probably too early to be sure, so perhaps other might like to try this combination and report back.

**acpi_os=**
    - disables all supported OS interface strings - this one is the real weird one - my hypothesis is that if the bios can't determine which OS quirks it should honor, it runs quirkfree:)
**irqfixup **
    - supposedly does more than irqpoll
**pci=irqfixup**
**pci=biosirq**
**acpi_os_name="Windows 2006"**
    - given what I said above, this should be removed

So what do I get?
 - stable in very limited testing (under 12 hours) despite not using noapic option
 - both CPUs running at low load (note: nosmp option worked for me to eliminate CPU2, no problem booting)


Touchscreen seems to be working OK with evtouch, the secret was a udev rule to make the touchscreen always at the same symlink.

YMMV

- cba

---

### Post by Zamboniman on 2007-10-17
I've been doing more playing around.

Without adding noapic things seem pretty stable unless I switch to console (ctl-alt-f1).  When I do this about every 7th time or so, either switching to console or switching back to X, the machine will hang.

I can live with this really, since otherwise things are working well, but I decided to try a few other things, after a bunch of googling and reading kernel argument docs.  Here's my results:

with noapic I also added acpi_irq_balance to the kernel options.  This stopped the 100% cpu issue but clobbered my touchscreen, which is completely unresponsive with this kernel option. I may try this again though.

Tried using default kernel arguments with pci=conf1 added.  The first time I tried this the machine hung during boot.  Removed quiet from kernel args and the machine booted fine, but again no touchscreen.  Hmmm, seems odd. 

Tried the irqfixup argument but this didn't help me. I may try this again combining it with something else.

I also tried the pci=routeirq option without noapic but this didn't seem to help.

One other thing I tried was to change the real time clock timer.  I read somewhere where the rtc timer can be buggy on some hp machines, so I added the following line to /etc/sysctl.conf and rebooted:

dev.rtc.max_user_freq=1024

which changes the clock timer from 64 to 1024.  This didn't seem to really help stability much without noapic when changing to and from console mode.  YMMV

Anyway, maybe somebody else will have some luck with something here, but no magic answers so far.

---

### Post by Zamboniman on 2007-10-17
[SIZE="4"]**Woo Hoo!!!!!!!  I think I've got it!!!!!!!!!!!!**[/SIZE]  :guitar: :guitar:

I hate to get too excited, because other things I've tried seem to have worked for a bit and then failed, but, so far so good and I've been testing for a couple of hours.  I've leaned heavily on the things that have caused it to lock up before and so far it's been working perfectly.

I now have no lockups or hangs, no 100% cpu issue, touchscreen, camera, card reader, etc all working perfectly, and, most importantly, **suspend to ram works perfectly.**  htop shows 1 to 2 % cpu use on both cores while idle. Fan runs either slowly or off when idle.

I'm using Gutsy Gibbon with all the latest updates as of this date.

Ok, here's what I've done:

Used the following kernel flags
 
```
quiet splash noapic acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi="!Linux" acpi_os_name="Windows 2006"
```

Now, initially this caused the touchscreen to not work, so I switched to the proprietary egalax drivers mentioned here in this thread with the following caveat:  I had to use the hiddev device instead of the input/event device or the tkusb device.   This also had the nice side benefit of fixing all of my repeating letters issues when using xvkbd or onboard.  The relevant part of my xorg.conf is as follows:

```
Section "InputDevice"
        Identifier      "EETI"
        Driver          "egalax"
        Option          "Device"        "/dev/usb/hiddev0"
        Option          "Parameters"    "/etc/egalax.cal"
        Option          "ScreenNo"      "0"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
#       Inputdevice     "touchscreen"   "CorePointer"
#       Inputdevice     "dummy"
        InputDevice     "EETI"  "SendCoreEvents"
EndSection

```

and I also blacklisted the usbtouchscreen modules as well as the tkusb module by adding the following to /etc/modprobe.d/blacklist

```
#dtk 10-17-07 - now using egalax proprietary drivers with hiddev device so blacklist
#kernel module usbtouchscreen and proprietary module tkusb
blacklist usbtouchscreen
blacklist tkusb
```

Of course, for sound to work right with jack sensing working I compiled my own alsa drivers as explained earlier in this thread.
Also, I'm using ndiswrapper for the broadcom card, which works fine at full speed, the bcm module didn't work for me, even with fwcutter.

And it seems, with this combination, we're good to go.

I'd like to hear how this combination works for everyone else.

---

### Post by Cuppa-Chino on 2007-10-17
> **Zamboniman said:**
> [SIZE="4"]**Woo Hoo!!!!!!!  I think I've got it!!!!!!!!!!!!**[/SIZE]  :guitar: :guitar:

I'd like to hear how this combination works for everyone else.

That sounds terrific, I guess you are using Bios F.18 and still i386 -- I think I will put another install on my machine with i386 with those criteria.

Just FYI I finally got NDISWRAPPER to work, fresh (formatted) install of Gutsy AMD64 RC1 and ndiswrapper 1.49rc4 plus dell driver r151517.exe worked for me, still has the bug that it cannot remember passwords but that is fine for the moment.

---

### Post by sauronsmatrix on 2007-10-17
[Wireless]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257")

---

### Post by Cuppa-Chino on 2007-10-17
;)

---

### Post by Zamboniman on 2007-10-17
> **Cuppa-Chino said:**
> That sounds terrific, I guess you are using Bios F.18 and still i386 -- I think I will put another install on my machine with i386 with those criteria.

Just FYI I finally got NDISWRAPPER to work, fresh (formatted) install of Gutsy AMD64 RC1 and ndiswrapper 1.49rc4 plus dell driver r151517.exe worked for me, still has the bug that it cannot remember passwords but that is fine for the moment.

Yes, I'm using the i386 version and yes, I have bios F18 on my machine.

Glad to hear you have NDISWRAPPER working.  For myself, I used gutsy's version of ndis, didn't have to compile my own, and for the driver I downloaded the WinXP driver from HP for the TX1000's, which seems to work fine for me, but I'm not using wpa an haven't tried it with wpa yet.

---

### Post by guadafan on 2007-10-17
Why with ubuntu Mint with kernel 2.6.20, I ONLY have to pass "vga=791" to the kernel?. ONLY and because I like that resolution for the console. And I haven't got any problem with ACPI. CPU speedstep works ok and batery monitor too. I can pass to console and back to X perfectly. USB works ok. Sound works with 3stack option...

I don't know why new kernels are worse than others older for this laptop.

It could be some option or module in compile time of the kernel. Has someone compilated his own kernel with this laptop?

I compiled debian lenny kernel from source and got several results depend on the options with acpi modules.

Sometimes the loading stoped with the message "...IOAPIC" and I had to TURN OFF the laptop for continuing the load of linux!!!  Yes, to turn off for turning on :-) 

But I could not discover the exactly option in .config for getting the perfect load, like in Ubuntu Mint.

Any ideas?

---

### Post by knodalyte on 2007-10-17
Zamboniman, that's lookin' good.

I used your boot params, and my touchscreen works using evtouch.  I did notice I experienced some "key bounce" using xvkbd, but there may be some xorg.conf settings to deal with that (like "TapTimer", maybe).

The udev rule I mentioned in my earlier post I named 
/etc/udev/rules.d/01-evtouch.rules 

and it's contents are:

SUBSYSTEM!="input", GOTO="evtouch_end"
SYSFS{idVendor}=="0eef", SYSFS{idProduct}=="0001", SYMLINK="input/touchscreen"
LABEL="evtouch_end"

In my xorg.conf stanza for the touchscreen, I use
Option   "Device"   "/dev/input/touchscreen"

The effect is to have a consistent device reference for the touchscreen.

Little by little... 

- cba

---

### Post by Zamboniman on 2007-10-17
> **knodalyte said:**
> 
I used your boot params, and my touchscreen works using evtouch.  I did notice I experienced some "key bounce" using xvkbd, but there may be some xorg.conf settings to deal with that (like "TapTimer", maybe).

The udev rule I mentioned in my earlier post I named 
/etc/udev/rules.d/01-evtouch.rules 


Glad to hear your touchscreen is working with evtouch.  I tried mine again with evtouch earlier once again and for some reason this time it was working too.  Still with the keybounce though.  I did already have an evdev rule to ensure it always picked the right device. 

I have played around with some of the evtouch options like taptimer, but haven't found anything that's works so far.  I did get one combo that eliminated the bounce, but it also eliminated right clicking, so that was no good.

I've noticed one unfortunate issue using the proprietary egalax drivers.  When I rotate the screen, the egalax driver doesn't recognize this and thus the new x and y coords are inverted, rendering it basically unusable when rotated.  Evtouch handles this fine.  I've emailed the egalax guys to find out if I'm missing a xorg.conf option to fix this but so far I have to choose between rotating fine, but with keybounce, or no keybounce but inverted x and y when rotated. Ugh. 

Everything else is still working perfectly with the new parameters though.

---

### Post by jcase008 on 2007-10-19
> **Zamboniman said:**
> [SIZE="4"]**Woo Hoo!!!!!!!  I think I've got it!!!!!!!!!!!!**[/SIZE]  :guitar: :guitar:

Used the following kernel flags
 
```
quiet splash noapic acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi="!Linux" acpi_os_name="Windows 2006"
```

```
Section "InputDevice"
        Identifier      "EETI"
        Driver          "egalax"
        Option          "Device"        "/dev/usb/hiddev0"
        Option          "Parameters"    "/etc/egalax.cal"
        Option          "ScreenNo"      "0"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
#       Inputdevice     "touchscreen"   "CorePointer"
#       Inputdevice     "dummy"
        InputDevice     "EETI"  "SendCoreEvents"
EndSection

```

and I also blacklisted the usbtouchscreen modules as well as the tkusb module by adding the following to /etc/modprobe.d/blacklist

```
#dtk 10-17-07 - now using egalax proprietary drivers with hiddev device so blacklist
#kernel module usbtouchscreen and proprietary module tkusb
blacklist usbtouchscreen
blacklist tkusb
```

...

I'd like to hear how this combination works for everyone else.

These settings work for me on Gutsy with updates from 19 Oct and the (as yet unreleased) eGalax proprietary drivers.  I'm running the stock SMP x86_64 kernel.  The only issue I currently have is the touchscreen coordinates are inverted, and the "center" of the screen is off to the left side.  Any ideas how to adjust the calibration parameters to the touchscreen?

---

### Post by Zamboniman on 2007-10-19
> **jcase008 said:**
> These settings work for me on Gutsy with updates from 19 Oct and the (as yet unreleased) eGalax proprietary drivers.  I'm running the stock SMP x86_64 kernel.  The only issue I currently have is the touchscreen coordinates are inverted, and the "center" of the screen is off to the left side.  Any ideas how to adjust the calibration parameters to the touchscreen?

You should be able to use the included Touchkit utility to calibrate your screen. This worked perfectly for me. Just run it from a terminal.

change directory into wherever you untarred the egalax package and then run the utiltiy

```
cd /whereever/your/package/is/Touchkit
gksudo ./Touchkit

```

---

### Post by jjordan on 2007-10-20
I am currently on the Internet using my Vodafone 3g+ account via an Option GEO201 also known as a Globetrotter Express 7.2.  or a Vodafone Mobile Connect Card. I'm connected at 3.6Mb/s with an 80Kb/s throughput, I have a really crappy signal here. Yeaa, free weekends!  

Anyway this means that at least the USB section of the Expresscard slot works.  

There is a "driver" here for the card:

[https://forge.vodafonebetavine.net/](https://forge.vodafonebetavine.net/)

That is a Vodafone Spain site but it works fine here in Italy after figuring out the right settings.  I am actually using Kppp to manage my connections so that I can use the accounting features but I recommend you download and install the one from the site first as it will do most of the heavy lifting of getting things set up.

-j

---

### Post by vishalrao on 2007-10-20
Is there any hope for the fingerprint reader? I believe mine is an AuthenTec AES 1610 and I've seen some online links for the AES 2510. Anyone had any luck getting fingerprint authentication working? :)

---

### Post by Francis Pereira on 2007-10-21
Does suspend and hibernate work on 7.10 with nVidia proprietary driver and Compiz Fusion ???:popcorn:
Cheers ,
Francis

---

### Post by dodgy_geeza on 2007-10-21
Hi all, just thought I would give you a bit of an update on what i've been doin...

Im now on my 2nd tx1250ea, as the first one died (charging circuit blew up). As a result, I thought i'd have a go at using a different distro to see how far I could get. I gave OpenSuSE 10.3 a go, and it actually worked pretty well. I still needed to creative boot options to get it to play nice, but it did work in the end. I couldn't get the touchscreen to work though, although I didn't give it much of a try.

Im now back on Ubuntu, though 64-bit this time. For me at least this seems to run smoother, though it does have issues (as always). Firstly, the touchscreen driver evtouch segfaults whenever you touch the screen. Apparantly this is a known issue, so I will probably give the egalax driver a go as it supposidly works.

Secondly, and this kinda relates to previous posts of mine, I have the 100% cpu issue. This time it's slightly different though. On mains power, the CPU runs nice and cool, with virtually no load, and is clocked down to 800MHz. If I unplug the mains however, one of the CPU's hits 100% constantly, and the other idles at about 50%. The load is kernel-space, so not really loaded software.

I did some quick testing on this a few minutes ago, and it seems to be the powernow/cpufreq modules. If I boot the system with init=/bin/bash, load up htop, and pull out the power cable, the cpu's stay idle, though at this point, there is no frequency scaling driver loaded. If I load the driver, load the ondemand governor, then unplug the power cable, I get 100% load. I've tried manually changing the governor in a fully-booted system, but something in the background keeps changing the governor back. 

My idea is to set it to run fixed at 800/1200MHz when on battery, or even 1800 if needbe, and then to switch back up when the mains is reconnected. I'm going to have another go thisafternoon to see if I can locate the exact source of this, but I think im pretty close to the mark.

Other than that, everything else seems to work. I've also noticed that I don't have the skipping issue that I did before, where the system would seem to freeze for a few seconds, then play catchup.

Will keep you posted.

Dodgy

---

### Post by manu456 on 2007-10-22
I've been following this thread since the beginning and I HAD been able to get everything working with fesity on my laptop. BUT i decided to move to gutsy and i wanted to cleanup everything and start afresh. 

So i installed gutsy(32 bit) on a brand new formatted partition. I had to use a handful of kernel parameters to get the live cd to boot as discussed in previous posts.

My problem is that I just can't get the system to be stable and run beyond 10-15 mins without freezing or becoming very slow and unresponsive. X sometimes takes upto 10 minutes to load after a boot. I'm not able to shutdown the system cleanly as well.

The only way things get stable is if i use noacpi as a kernel parameter. 

I want to know what can be the ill effects of using noacpi and from my understanding i wont be able to use any power saving / management features. Is that true? 

Has anybody trying installing gutsy afresh on a tx1xxxx laptop and got a stable system? Please share your kernel parameters.

---

### Post by benguin on 2007-10-22
Hi there,
Unlike most of the tx1XXX owners here, I've been using Gutsy for a while now, without any special kernel boot parameters. The LiveCD needs the vga=something line to boot though. My tx1305ca is running well, almost everything works (except the fingerprint reader, and the touchscreen has a bit of a lag but I haven't investigated that issue too much to be honest). The only two major problems I have are with the vga-out driving multimedia projectors, and system lock ups when using a tty command shell. That again, is not too frequent or regular, but once a while, if I'm using the shell for a while, the system goes into hard lockup, and even the magic sysrq doesn't work.

Just my two cents. If anyone has a better experience (where the resolutions are detected automatically) driving projectors with your tx1000 series laptop, I'll be very interested to take your advice.


regards,
-J-

> **manu456 said:**
> I've been following this thread since the beginning and I HAD been able to get everything working with fesity on my laptop. BUT i decided to move to gutsy and i wanted to cleanup everything and start afresh. 

So i installed gutsy(32 bit) on a brand new formatted partition. I had to use a handful of kernel parameters to get the live cd to boot as discussed in previous posts.

My problem is that I just can't get the system to be stable and run beyond 10-15 mins without freezing or becoming very slow and unresponsive. X sometimes takes upto 10 minutes to load after a boot. I'm not able to shutdown the system cleanly as well.

The only way things get stable is if i use noacpi as a kernel parameter. 

I want to know what can be the ill effects of using noacpi and from my understanding i wont be able to use any power saving / management features. Is that true? 

Has anybody trying installing gutsy afresh on a tx1xxxx laptop and got a stable system? Please share your kernel parameters.

---

### Post by tuscani20001 on 2007-10-22
Hello there. I'm a new user to ubuntu os. I recently installed Ubuntu 7.10 amd64 on my tx1250EA using unetbootin. My problem now is that I cannot boot to the system at all. 

When I select to boot ubuntu my laptop stalls at "loading hardware drivers". When I boot from recovery mode it shows that it actually stalls at eth0 no link during initialization. 

Then after reading through some posts of this thread I think I managed (I'm a newbie to ubuntu) to edit the kernel by adding these instructions Zamboniman suggested:
noapic acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi="!Linux" acpi_os_name="Windows 2006"

Now when I tried to boot ubuntu the system stalled at "setting the system clock". Any help will be much appreciated, thanks in advance.

---

### Post by doryphore on 2007-10-22
hi,

i wanted to use the vga-out for projections too ; haven't tried yet. I'll let you know as soon as i can. But does the Fn+f4 button give you anything ? 
For gutsy, without options i could get only a black screen (the i386 version) ; i wish i had installed the 64-bits version.
I couldn't manage to fix the event problem for the touchscreen. The udev rules given earlier in this post didn't work for me (with evtouch, haven't tried egalax).

---

### Post by sauronsmatrix on 2007-10-23
my additional boot options in **/boot/grub/menu.lst** are
```
noapic irqpoll
```

Edit the **boot options**:
```
sudo gedit /boot/grub/menu.lst
```


This is my Regular Ubuntu 7.10 Kernel 2.6.22-14 Boot ***Section***:
```
title		Ubuntu 7.10, kernel 2.6.22-14
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=506fd4b8-6a80-444a-a8a8-76a5b7af99be ro quiet splash noapic irqpoll
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14 (command line)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=506fd4b8-6a80-444a-a8a8-76a5b7af99be ro single noapic irqpoll
initrd		/boot/initrd.img-2.6.22-14-generic
```


My comp:
> 
Model: [tx1000z]("http://www.shopping.hp.com/series/category/notebooks/tx1000z_series/3/computer_store")
CPU: AMD Turion(TM) 64 X2 TL-64 2.2GHz
Display: 12.1" WXGA High-Definition HP BrightView Widescreen Display(1280 x 800) with Integrated Touch-screen
Graphics: NVIDIA(R) GeForce(R) Go 6150 
DVD: Lightscribe
Build: HP Imprint Finish + Fingerprint Reader + Webcam + Microphone
Wireless: 802.11b/g WLAN 
RAM: 2 GB DDR2
HDD: 120 GB 


---

### Post by manu456 on 2007-10-23
> **sauronsmatrix said:**
> my additional boot options in **/boot/grub/menu.lst** are
```
noapic irqpoll
```


Thank you sauronsmatrix. noapic and irqpoll seem to work just right for me.

I now have a stable system with most of the hardware working thanks to everybody who have posted on this thread. I have made notes of my gutsy installation on a clean, formatted system and posted them on my blog at 
[http://www.codepencil.com/?p=9]("http://www.codepencil.com/?p=9")

Hopefully they will be of help to someone with a similar system. 

I have been using my laptop with gutsy for 2 days. I'm facing a strange issue with wireless. Wireless works fine for a while but it stops working randomly and then im not able to connect to any networks. If I try iwlist scan I get no results. I have to restart my system and it works fine again. I did not have this problem with feisty. Has anyone faced this before?

---

### Post by kstan_79 on 2007-10-23
Hi all,
I have Ubuntu 7,10 AMD64 (Stable version) install in mmy HP Pavilion tx1000, so far I have few problem can't solve:
1. Sound Card, (I'd try to reinstall from alsa source code, or modprobe mdoel=3stack)
2. Touch screen.
3. Remote control (at initial stage it work fine, after some tuning with the OS then it become not detected)
4. webcam


Anybody can point me a good direction to solve above problem? I'd go through a lot of try in this forum but still no luck.

Regards,
Ks

---

### Post by sauronsmatrix on 2007-10-23
[sound]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235")
[touchscreen]("http://ubuntuforums.org/showpost.php?p=2792971&postcount=16")
webcam - install "cheese"

for the remote, i have same problem. sorry

---

### Post by kstan_79 on 2007-10-23
Thanks sauronsmatrix,
I'd install cheese, seems like its only a webcam photo capture program, I don't have the driver.

Anyway, you solve the sound, webcam & touch screen problem?
I'd test the touchscreen tutorial, it doesn't work(is  it work for 64bit?).

---

### Post by sauronsmatrix on 2007-10-23
yes i solved the problems.

click on the links in my previous post to see the solution.

---

### Post by tuscani20001 on 2007-10-23
Sauronsmatrix I have added the noapic irqpoll and here is what I get (note: I'm a newbie to linux):
When I boot ubuntu normally, my system still stacks at "setting the system clock". 
When I boot ubuntu using recover mode, everything seems to work ok and the last line I get is root@ubuntu:~#. I'm supposed to type something there? What shall I type? Sorry if my question is very childish but I'm a newbie.

---

### Post by kstan_79 on 2007-10-23
Hi sauronsmatrix,
No luck all solution you'd posted doesn't work at my hp pavilion tx 1000.

Any suggestion for me?
Regards,
ks

---

### Post by jcase008 on 2007-10-23
> **Zamboniman said:**
> You should be able to use the included Touchkit utility to calibrate your screen. This worked perfectly for me. Just run it from a terminal.

change directory into wherever you untarred the egalax package and then run the utiltiy

```
cd /whereever/your/package/is/Touchkit
gksudo ./Touchkit

```

Ha!  I've been away from this long enough that I forgot about that app.  After doing the 25 pt cal, it works perfectly.  Thanks.

---

### Post by leftyfb on 2007-10-23
HP Pavilion tx 1000(1200) here running the final release of Gutsy. 

I have wifi working via ndiswrapper, no problems

sound works using the manual editing found toward the beginning of this thread.

webcam - cheese says unable to find webcam as does Ekiga

fingerprint read - haven't messed with it yet.

My biggest problem, touchscreen!

I have followed all the different evtouch instructions on here with all different results. It detects the touch, but the calibration is WAY off and cannot be calibrated. The calibration tool show numbers when touching the screen, but they are static numbers and only change to some number based off whatever numbers are already in the xorg.conf. I had this calibrated at one point accidentally, but the lag was insane. I immidiately backed up the xorg.conf and kept messing with it, only to lose everything and never to get back to a calibrated state with tons of lag. Also, the event # changes sometimes on reboot.

My current xorg file along with the backup, lsusb and proc devices output are below. Please help!


current xorg.conf
```

Section "Files"
  InputDevices "/dev/input/event2" 	## correspond to the touchscreen event number
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"   	
	Identifier "touchscreen"
 	Driver "evtouch"
	Option "Device" "/dev/input/event2"  # correspond to the touchscreen event number
	Option "DeviceName" "touchscreen"
	#########################################
	Option "MinX" "44"
	Option "MinY" "105"
	Option "MaxX" "3985"
	Option "MaxY" "3994"    
        Option "x0" "-1"
        Option "y0" "-3"
        Option "x1" "-6"
        Option "y1" "-4"
        Option "x2" "-2"
        Option "y2" "-6"
        Option "x3" "-2"
        Option "y3" "-3"
        Option "x4" "-4"
        Option "y4" "-3"
        Option "x5" "2"
        Option "y5" "-1"
        Option "x6" "-5"
        Option "y6" "-3"
        Option "x7" "-2"
        Option "y7" "1"
        Option "x8" "5"
        Option "y8" "2"
        #########################################
       #Option "ReportingMode" "Raw"
        Option "Emulate3Buttons"
        Option "Emulate3Timeout" "50"
       #Option "SendCoreEvents"
        ######################
        Option "TapTimer" "0"
        Option "LongTouchTimer" "250"
        Option "ReportingMode" "Raw"
        Option "SendCoreEvents" "On"
	Option "SendCoreEvents"
    Option "Calibrate"  "1"
EndSection

 Section "InputDevice"
 	Driver		"wacom"
 	Identifier	"stylus"
 	Option		"Device"	"/dev/input/wacom"
 	Option		"Type"	"stylus"
 	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
 EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation C51 [Geforce 6150 Go]"
	Driver		"nvidia"
	Busid		"PCI:0:5:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51 [Geforce 6150 Go]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
		InputDevice     "stylus"	"SendCoreEvents"
		InputDevice     "cursor"	"SendCoreEvents"
		InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
        InputDevice  "touchscreen" "CorePointer"
EndSection

Section "Module"
	Load		"glx"
EndSection

```
-------------------------------------------------------------

xorg.conf.touch.works.no.cal
```

Section "Files"
  InputDevices "/dev/input/event3" 	## correspond to the touchscreen event number
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"   	
	Identifier "touchscreen"
 	Driver "evtouch"
	Option "Device" "/dev/input/event3"  # correspond to the touchscreen event number
	Option "DeviceName" "touchscreen"
	#########################################
	Option "MinX" "44"
	Option "MinY" "105"
	Option "MaxX" "3985"
	Option "MaxY" "3994"    
	#########################################
	Option "ReportingMode" "Raw"
	Option "Emulate3Buttons"
	Option "Emulate3Timeout" "50"
	Option "SendCoreEvents"
    Option "Calibrate"  "1"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation C51 [Geforce 6150 Go]"
	Driver		"nvidia"
	Busid		"PCI:0:5:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
#	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51 [Geforce 6150 Go]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	Option "RandRRotation" "on"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
		InputDevice     "stylus"	"SendCoreEvents"
		InputDevice     "cursor"	"SendCoreEvents"
		InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
        InputDevice  "touchscreen" "CorePointer"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

```
-------------------------------------------------------------

cat /proc/bus/input/devices
```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=120013
B: KEY=1004 2200002 3802078 f950d401 feffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=0eef Product=0001 Version=0210
N: Name="eGalax INC. USB TouchController"
P: Phys=usb-0000:00:0b.1-2.3/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=b
B: KEY=401 0 30000 0 0 0 0 0 0 0 0
B: ABS=f

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=mouse2 event4 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=4000 0 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input8
U: Uniq=
H: Handlers=event8 
B: EV=21
B: SW=1

```

--------------------------------------------

lsusb
```

Bus 002 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 005: ID 08ff:1600 AuthenTec, Inc. 
Bus 001 Device 004: ID 0c45:62c0 Microdia 
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 0000:0000

```

---

### Post by kstan_79 on 2007-10-24
my poor laptop after hacking it 1 whole day still not able to product any audio. I doing multimedia job, without sound it can killing me.

So far I'd test add 
options snd-hda-intel model=hp (and 3 stack, and ) at /etc/modprobe.d/alsa-base

I'd recompile the alsa-driver,lib,utils. 

At the end I still get the same result at dmesg. 
> ACPI:  PCI interrupt for device  0000:00:10.1 disabled
I suspect noapic kernel parameter cause this error, but without noapic my notebook won't boot.

Currently I'm been force to use "noapic" parameter because all others kernel parameter doesn't work. With irqpool even make my laptop can't boot. 

Any help is greatly appreciated.
Regards,
Ks

---

### Post by sauronsmatrix on 2007-10-24
THOse solutions DEFINITELY work.

If you are getting errors, POST them here and I can sort them out for you.

saurons

---

### Post by ghonz on 2007-10-24
Hey hey,
thanks to everyone on this forum I have Ubuntu 7.10 on a HP tx1138ea.
I have wireless working perfectly and sound is working.
What I do have issues with are:
heaphone jack - not working sound keeps coming through the speakers
inbuilt microphone - I just get static when I test it or try it on skype
microphone jack - not working

I'm also having issues with the touchscreen and I havent even thought about looking at the fingerprint reader.

---

### Post by kstan_79 on 2007-10-24
sauronsmatrix,

Thanks for your support,
I'm using HP Pavilion tx 1000 (I don't know whether Malaysia's notebook exactly  same spec with others country or not), below is my lspci result(Hope exactly same with yours):
> 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)


my lsusb result:

> Bus 001 Device 006: ID 08ff:1600 AuthenTec, Inc. 
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 007: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0c45:62c0 Microdia 
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard 
Bus 002 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c03d Logitech, Inc. **(my mouse)**

 
As my previous post, I only able to boot with kernel parameter **noapic**, sound not working. After ** rmmod snd-hda-intel**[B] 
modprobe snd-hda-intel model=hp[/B] (I'd test with 3stack as well)

dmesg return this result:
> ACPI: PCI interrupt for device 0000:00:10.1 disabled

No improvement when I use acpi_os_name, and etc kind of parameter.
If I use **irqpool noapic** or **only irqpool**, the boot process freeze and return me not enough buffer.

By the way, my USB port can't detect new device which is insert after boot.
Hope this information enough for you.
Regards,
Ks

---

### Post by sauronsmatrix on 2007-10-24
ok ppl with sound issues....
go [here]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235")

This method so far is foolproof. No one with an hp tx1000 series who followed this guide failed.

---

### Post by kstan_79 on 2007-10-24
> **sauronsmatrix said:**
> ok ppl with sound issues....
go [here]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235")

This method so far is foolproof. No one with an hp tx1000 series who followed this guide failed.

Unfortunately, I'd follow this method before and it failed in my laptop. Remove snd_hda_intel.ko in kernel and install the new 1 won't help.

---

### Post by napster2500 on 2007-10-25
hi there and thanks for the help.
i only need a command that can show me the model of my sound card. is there such a command? if you know please help me... :)

---

### Post by kstan_79 on 2007-10-25
Hi napster2500,
this command?
** lspci  | grep -i audio**

regards,
Ks

---

### Post by sauronsmatrix on 2007-10-25
> **kstan_79 said:**
> Unfortunately, I'd follow this method before and it failed in my laptop. Remove snd_hda_intel.ko in kernel and install the new 1 won't help.

Well, what about it fails? I expect errors to happen. Post the error message here!

---

### Post by kstan_79 on 2007-10-25
sauronsmatrix,
This is the error message at dmesg:

> [  190.663731] irq 7: nobody cared (try booting with the "irqpoll" option)
[  190.663738] 
[  190.663739] Call Trace:
[  190.663742]  <IRQ>  [<ffffffff8026aaae>] __report_bad_irq+0x1e/0x80
[  190.663794]  [<ffffffff8026ad93>] note_interrupt+0x283/0x2c0
[  190.663805]  [<ffffffff8026bb8c>] handle_level_irq+0x10c/0x140
[  190.663814]  [<ffffffff8020c6ab>] do_IRQ+0x7b/0x100
[  190.663818]  [<ffffffff80209010>] default_idle+0x0/0x40
[  190.663824]  [<ffffffff8020a3a1>] ret_from_intr+0x0/0xa
[  190.663827]  <EOI>  [<ffffffff80422150>] unix_poll+0x0/0xb0
[  190.663841]  [<ffffffff80209039>] default_idle+0x29/0x40
[  190.663847]  [<ffffffff802090c0>] cpu_idle+0x70/0xc0
[  190.663867] 
[  190.663869] handlers:
[  190.663871] [<ffffffff8802ed30>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  190.663904] Disabling IRQ #7


but lsmod show that the snd-hda-intel is loaded
> Module                  Size  Used by
ipv6                  317192  10 
af_packet              28172  4 
vmnet                  45344  15 
vmmon                 150124  0 
binfmt_misc            14860  1 
rfcomm                 47656  2 
l2cap                  28672  11 rfcomm
ppdev                  11272  0 
powernow_k8            16608  1 
cpufreq_powersave       3072  0 
cpufreq_userspace       6048  0 
cpufreq_ondemand       10896  1 
cpufreq_conservative     9608  0 
cpufreq_stats           8160  0 
freq_table              6464  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
container               6400  0 
battery                12424  0 
ac                      7304  0 
button                 10400  0 
video                  21140  11 
sbs                    21520  0 
bay                     7936  0 
dock                   12264  1 bay
ndiswrapper           233632  0 
parport_pc             41896  0 
lp                     15048  0 
parport                44172  3 ppdev,parport_pc,lp
loop                   21764  0 
snd_hda_intel         378664  0 
snd_pcm_oss            48128  0 
snd_mixer_oss          20352  1 snd_pcm_oss
snd_pcm                94600  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13584  2 snd_hda_intel,snd_pcm
snd_hwdep              12680  1 snd_hda_intel
snd_seq_oss            39168  0 
snd_seq_midi_event     10240  1 snd_seq_oss
joydev                 13440  0 
snd_seq                63904  4 snd_seq_oss,snd_seq_midi_event
snd_timer              27784  2 snd_pcm,snd_seq
snd_seq_device         10772  2 snd_seq_oss,snd_seq
uvcvideo               52228  0 
usbtouchscreen         12036  0 
ide_cd                 35488  0 
cdrom                  41768  1 ide_cd
compat_ioctl32         11136  1 uvcvideo
videodev               31360  1 uvcvideo
usb_storage            81728  0 
libusual               22824  1 usb_storage
snd                    71848  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
v4l1_compat            15364  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
usbhid                 32576  0 
k8temp                  7680  0 
hci_usb                21020  2 
psmouse                45596  0 
hid                    33408  1 usbhid
pcspkr                  4608  0 
bluetooth              63876  7 rfcomm,l2cap,hci_usb
soundcore              10272  1 snd
serio_raw               9092  0 
nvidia               7013492  36 
i2c_nforce2             7808  0 
shpchp                 38300  0 
i2c_core               30208  2 nvidia,i2c_nforce2
pci_hotplug            36612  1 shpchp
evdev                  13056  7 
ext3                  146576  1 
jbd                    69360  1 ext3
mbcache                11272  1 ext3
sg                     41384  0 
sd_mod                 32512  4 
amd74xx                17328  0 [permanent]
ide_core              141200  3 ide_cd,usb_storage,amd74xx
forcedeth              55048  0 
ohci_hcd               25092  0 
sata_nv                24068  3 
ata_generic             9988  0 
ehci_hcd               40076  0 
libata                138928  2 sata_nv,ata_generic
scsi_mod              172856  4 usb_storage,sg,sd_mod,libata
usbcore               161584  10 ndiswrapper,uvcvideo,usbtouchscreen,usb_storage,libusual,usbhid,hci_usb,ohci_hcd,ehci_hcd
thermal                16528  0 
processor              36232  2 powernow_k8,thermal
fan                     6920  0 
capability              7048  0 
commoncap               9472  1 capability
fuse                   52528  3 

---

### Post by sauronsmatrix on 2007-10-25
try booting with only noapic and irqpoll

---

### Post by kstan_79 on 2007-10-25
Hi,

I'd tried this parameter before, the OS freeze at boot.(my laptop can't work with irqpool)
> noapic irqpool

To boot with option irqpool, I use following options(with irqfixup):
> noapic acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi="!Linux" acpi_os_name="Windows 2006"


after boot up, the sound still didn't come out, so i check dmesg found something new, here it is:
> [  449.511433] ACPI: PCI interrupt for device 0000:00:10.1 disabled
[  454.991574] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 11 (level, low) -> IRQ 11
[  454.991735] PCI: Setting latency timer of device 0000:00:10.1 to 64


Currently I boot with alsa driver version 1.0.15 (drivers+util+lib) from alsa-project website.
Editied:
When I remove all alsa-utils, alsa-driver,alsa-lib which I install from alsa website earlier, and reinstall ubuntu own package (linux-image, linux-ubuntu-modules,alsa-utls + etc), with kernel parameter "noapic irqfixup", i get this:
**hda_codec: Unknown model for ALC660VD/ALC861VD, trying auto-probe from BIOS...**

Regards,
ks

---

### Post by sauronsmatrix on 2007-10-25
dude, i didnt say irqpool, i said irqpoll

try using irqpoll and noapic now, and then do the installation for stuff taht doesnt wrok. it should work now

---

### Post by kstan_79 on 2007-10-25
I'm sorry, typing error, noapic + irqpoll still return same result, no sound.  The result is still can't find the device (alsamixer). After asoundconf set-default-card NVidia still doesn't help.

Except the sound, I need to say thank because now my remote control working.

---

### Post by VincenzoAMD64 on 2007-10-26
Hello,
I have a HP TX1000,
Feisty works very well,
Gutsy -> sound problem, usb disk problem

I have two kernels:
2.6.20-16 sound Ok, usb disk problem
2.6.22-14 sound KO, usb disk problem

So, using the same binaries and configuration, but changing the kernel at boot time the sound problem is not present. This means that is related to kernel and alsa module.

With both kernels, when I connected my usb disk no disk was found and mounted. Looking for a solution a discover that:
booting using the irqpoll option and adding to fstab:
/dev/sdb1 /mnt/usbdiskb auto rw,user,umask=000 0 0
/dev/sdc1 /mnt/usbdiskc auto rw,user,umask=000 0 0
the disk are mounted.

Anyone have same problems?
Thank you Vincenzo

---

### Post by kstan_79 on 2007-10-26
I use same hardware with you, same problem with you, However seems many people have working solution, you can read from 1st post of this topic

---

### Post by VincenzoAMD64 on 2007-10-26
Thank you,
sorry for having proposed an already solved problem.
The solution has worked for me with the new kernel.

Greetings
Vincenzo

---

### Post by kstan_79 on 2007-10-26
then you are lucky, until now my sound card still doesn't work.

---

### Post by jjordan on 2007-10-27
Benguin,

Install nvidia-settings from the repository, you can controll a hotplugged projector, if you still have problems connect the projector before you start xwindows.  I am using a 1680X1050 external monitor on a daily basis, I have also used television via the video connection on the docking station.  The latest nvidia-settings solves the problem of destroying your old xorg.conf but still be careful and make a backup.

-j

---

### Post by kstan_79 on 2007-10-27
can somebody who have working audio for exactly model HP Pavilion tx 1000 compare their lspci -v with me? I'd done everything I can but my sound still doesn't work.


Using this command
**sudo lspci -v**

> 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [e0] HyperTransport: MSI Mapping

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] #00 [00fe]
        Capabilities: [fc] #00 [0000]

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: c4000000-c7ffffff
        Prefetchable memory behind bridge: 00000000c9000000-00000000c91fffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: c8000000-c8ffffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at c2000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c1000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 50000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [e0] HyperTransport: MSI Mapping

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 3040 [size=64]
        I/O ports at 3000 [size=64]
        Capabilities: [44] Power Management version 2

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at c0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at c0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 7
        Memory at c0005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 3080 [size=16]
        Capabilities: [44] Power Management version 2

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1) (prog-if 85 [Master SecO PriO])
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        I/O ports at 30b0 [size=8]
        I/O ports at 30a4 [size=4]
        I/O ports at 30a8 [size=8]
        I/O ports at 30a0 [size=4]
        I/O ports at 3090 [size=16]
        Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        Capabilities: [b8] Subsystem: Gammagraphx, Inc. Unknown device 0000
        Capabilities: [8c] HyperTransport: MSI Mapping

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 30b8 [size=8]
        Capabilities: [44] Power Management version 2

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1371
        Flags: bus master, fast devsel, latency 0, IRQ 9
        Memory at c8000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint IRQ 0



I just want to make sure my laptop exactly same with people.

Thank you and Regards,
Ks

---

### Post by simplyw00x on 2007-10-28
I'd just like to say that I finally got rotation and touchscreen working satisfactorily with evtouch drivers. I will post my resultson my LaptopTestingTeam page.

---

### Post by Francis Pereira on 2007-10-28
Whats your GPU temperature . According to nvidia.settings my GPU is running at 88C. Is it jsut me. Is my system frying ???:popcorn:

---

### Post by Cuppa-Chino on 2007-10-29
hmm mine does not go up that high -- I mean 88°C, did you leave a windows partition just go there and check in windows to confirm
also what were you running at the time? did you have visual effects on? or were you running some 3d application?

mine shows a throttle level of 110°C -- which appears crazy... but it has gotten very hot before plus 80°C intermittently

--------------------------------------------------------------------------------------------------------------------

I have a new problem: cannot get DHCP to connect....

---

### Post by sauronsmatrix on 2007-10-29
sick! my remote is working again!

---

### Post by thagame on 2007-10-29
I used this site for the touchscreen for mine, it works perfect.

[http://www.cnpbagwell.com/Tx1000/HomePage](http://www.cnpbagwell.com/Tx1000/HomePage)

---

### Post by sauronsmatrix on 2007-10-29
kstan_79, this is the output of my lspci -v

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [e0] HyperTransport: MSI Mapping

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] #00 [00fe]
        Capabilities: [fc] #00 [0000]

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
        Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: c4000000-c7ffffff
        Prefetchable memory behind bridge: 00000000c9000000-00000000c91fffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: c8000000-c8ffffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0000
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0

00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at c2000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at c1000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [e0] HyperTransport: MSI Mapping

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 3040 [size=64]
        I/O ports at 3000 [size=64]
        Capabilities: [44] Power Management version 2

00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at c0040000 (32-bit, non-prefetchable) [size=256K]

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at c0004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 7
        Memory at c0005000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 3080 [size=16]
        Capabilities: [44] Power Management version 2

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1) (prog-if 85 [Master SecO PriO])
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 5
        I/O ports at 30b0 [size=8]
        I/O ports at 30a4 [size=4]
        I/O ports at 30a8 [size=8]
        I/O ports at 30a0 [size=4]
        I/O ports at 3090 [size=16]
        Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        Capabilities: [b8] Subsystem: Gammagraphx, Inc. Unknown device 0000
        Capabilities: [8c] HyperTransport: MSI Mapping

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: Hewlett-Packard Company Unknown device 30bf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at c0007000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 30b8 [size=8]
        Capabilities: [44] Power Management version 2

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 1374
        Flags: bus master, fast devsel, latency 0, IRQ 9
        Memory at c8000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [d0] Express Endpoint IRQ 0

---

### Post by kstan_79 on 2007-10-30
the result for command:
**diff yourresult myresult ** 

< [virtual] Expansion ROM at 50000000 [disabled] [size=128K]
---
> [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
161,162c161,162
< 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
< Subsystem: Hewlett-Packard Company Unknown device 1371
---
> 03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
> Subsystem: Hewlett-Packard Company Unknown device 1374



sees like it our hardware is almost same, except Virtual Expansion ROM, Wifi, and HP unknown Device(Is it remote control?)

And their hardware address is same, I assume their is no conflic the IRQ.

So, I can assume your solution should be work in my laptop, just my OS or my setting got something wrong?

The few thing I can only guess about is I'd install 32bit environment in my Ubuntu 64bit, to fire up javaws, vmware and etc. Is it effect?

Regards,
Ks

---

### Post by Francis Pereira on 2007-10-30
I used a thermal infrared sensor to test the temperature of the laptop. Turns out it was very close to the temperature reported by the CPUs. I dont think there is a temperature sensor on  the GPU as it is  on-board! Think nvidia-settings is a generic GUI also the maximum temperature textbox is grayed out  


Cheers .
Francis Pereira

---

### Post by spikermn on 2007-10-30
I'm not sure if anyone actually solved the 100% cpu usage problem, but here's my $.02 worth:

My cpus idles at 4% before I started working on getting hibernate to work. I edited my xorg.conf file and when I restarted X, one of the cpus ideled at 50%. There was no user process causing this. When I edit xorg.conf and delete the entry I just added, the problem was solved. 

I'm not sure which of these entries caused the problem, but it was fixed by deleting this from my Device section:

```
Option "Coolbits" "1"
Option "HWCursor" "True"
Option "BackingStore" "On"
```

Hope this helps someone and if anyone has any more insight, let me know. Still don't have suspend/hibernate working...:lolflag:

---

### Post by jcase008 on 2007-11-01
**DSDTs Wanted**

I'm looking for the DSDTs for everyone's system to compare to mine.  I'm trying to get the rotate and settings buttons (at the bottom right corner of the screen) to work.  I think they are ACPI buttons, but with acpi=debug and a modified DSDT I still can't get any debug messages to print when the buttons are pressed.  I'd like to see what the device configurations are for those buttons from everyone.

To get the dsdt:

```
sudo cat /proc/acpi/dsdt > /tmp/dsdt.hex
```

I'll take the raw hex files.  Or, if you want to decompile them into .dsl files:

```
sudo apt-get install iasl
iasl -d /tmp/dsdt.hex
```

That should produce ~/dsdt.dsl.  The specific sections that I'm looking for are for the buttons:

```

        Device (QBTN)
        Device (DBTN)
        Device (MUBN)
        ...

```

---

### Post by simplyw00x on 2007-11-01
My DSDT [http://pastebin.com/m540ce32f](http://pastebin.com/m540ce32f)

---

### Post by kstan_79 on 2007-11-02
Finally I'd solve my tx 1000 laptop no sound issue.

Previously I'd add parameter model=3stack, or recompile the alsa the result still can play audio, because of my Ubuntu 7.10 installation method=oem
the user I'd created not belong to many group, include audio, admin and etc,

AfterI add my user to necessary group =, logout+login the the audio running well.

regards,
Ks

---

### Post by phattyacid on 2007-11-02
First post for me

I've got a 1320us with Gusty 64bit and managed to get the the Wifi working in 54mbps with ndiswrapper and the dell drivers.  The sound I have gotten as far as having sound with the speakers but no luck on the jacks.  The jacks are sensing the headphones (the sound turns off at the speakers), but no sound in the headphones.

if anyone has an idea of where to look in the config, I'm listening

cheers

---

### Post by Zamboniman on 2007-11-02
> **jcase008 said:**
> **DSDTs Wanted**

I'm looking for the DSDTs for everyone's system to compare to mine.  I'm trying to get the rotate and settings buttons (at the bottom right corner of the screen) to work.  I think they are ACPI buttons, but with acpi=debug and a modified DSDT I still can't get any debug messages to print when the buttons are pressed.  I'd like to see what the device configurations are for those buttons from everyone.




Here's mine:

 ```


Device (QBTN)
        {
            Name (_HID, EisaId ("PNP0C32"))
            Name (_UID, 0x01)
            Method (_STA, 0, NotSerialized)
            {
                If (LEqual (OSYS, 0x07D6))
                {
                    Return (0x0F)
                }
                Else
                {
                    Return (0x00)
                }
            }

            Method (GHID, 0, NotSerialized)
            {
                If (LEqual (HOTB, 0x04))
                {
                    Notify (QBTN, 0x02)
                    Store (0x00, HOTB)
                }

                Return (Buffer (0x01)
                {
                    0x01
                })
            }
        }

 Device (DBTN)
        {
            Name (_HID, EisaId ("PNP0C32"))
            Name (_UID, 0x02)
            Method (_STA, 0, NotSerialized)
            {
                If (LEqual (OSYS, 0x07D6))
                {
                    Return (0x0F)
                }
                Else
                {
                    Return (0x00)
                }
            }

            Method (GHID, 0, NotSerialized)
            {
                If (LEqual (HOTB, 0x05))
                {
                    Notify (DBTN, 0x02)
                    Store (0x00, HOTB)
                }

                Return (Buffer (0x01)
                {
                    0x02
                })
            }
        }
  Device (MUBN)
        {
            Name (_HID, EisaId ("PNP0C32"))
            Name (_UID, 0x03)
            Method (_STA, 0, NotSerialized)
            {
                If (LEqual (OSYS, 0x07D6))
                {
                    Return (0x0F)
                }
                Else
                {
                    Return (0x00)
                }
            }

            Method (GHID, 0, NotSerialized)
            {
                If (LEqual (HOTB, 0x03))
                {
                    Notify (MUBN, 0x02)
                    Store (0x00, HOTB)
                }

                Return (Buffer (0x01)
                {
                    0x03
                })
            }
        }


```

---

### Post by alentz on 2007-11-02
> **sauronsmatrix said:**
> try booting with only noapic and irqpoll

hi!with noapic irqpoll I get an error: bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed. I remember I had problems with my wifi with 7.04...but at least it let me boot...

---

### Post by ghonz on 2007-11-03
Hey hey,
I'm having one or two niggly problems with my Tx1138ea.

Touchscreen - after installing evtouch from the package manager, if i touch the screen then wherever the cursor is will work, but I can't move the cursor to another point on the screen, unless I use the mouse.

Sound - the sound works fine I'm getting sound out of the speakers, but if i try to plug in my external speakers or headphones then the headphone jack doesnt work.

mic - inbuilt mic works but the microphone jack doesnt seem to work for external mic's either.

rotate screen button - doesn't work

remote control - doesn't work

usb - the usb ports seem to have issues, they work if something is plugged in at startup but post startup they dont recognized new things being plugged in.

Anyone got any suggestions?

Jon - a relative newbie

---

### Post by kstan_79 on 2007-11-03
> **ghonz said:**
> 
I'm having one or two niggly problems with my Tx1138ea.

Touchscreen - after installing evtouch from the package manager, if i touch the screen then wherever the cursor is will work, but I can't move the cursor to another point on the screen, unless I use the mouse.

Sound - the sound works fine I'm getting sound out of the speakers, but if i try to plug in my external speakers or headphones then the headphone jack doesnt work.

mic - inbuilt mic works but the microphone jack doesnt seem to work for external mic's either.

rotate screen button - doesn't work

remote control - doesn't work

usb - the usb ports seem to have issues, they work if something is plugged in at startup but post startup they dont recognized new things being plugged in.

Anyone got any suggestions?

Jon - a relative newbie

Hi ghonz,
boot with this kernel parameter
noapic irqpoll

then you will have remote control, usb working.
rotate, touch screen won't work  for my laptop as well.

---

### Post by ghonz on 2007-11-03
> **kstan_79 said:**
> Hi ghonz,
boot with this kernel parameter
noapic irqpoll

then you will have remote control, usb working.
rotate, touch screen won't work  for my laptop as well.

I just tried that and alas no joy with the remote control :(

USB works though :)

---

### Post by phattyacid on 2007-11-03
DST 1320us : [http://pastebin.com/f7d5d0d1a](http://pastebin.com/f7d5d0d1a)

---

### Post by kstan_79 on 2007-11-04
Hi all,
This is the best handwriting tool I saw in Linux. Now my tablet look much better.

[http://risujin.org/cellwriter/](http://risujin.org/cellwriter/)

regards,
Ks

---

### Post by doryphore on 2007-11-06
Hi Kstan,
i can't have cellwriter working with evtouch. It just writes dots and not lines. The sme thing happens with xournal and not with gournal. 
Do you use a 64-bit version of gutsy ? Could you put your xorg.conf to see the evtouch part ?

Moreover, i can't have sound working. I didn't try to compile the new drivers, i just wanted to test the speakers. So i'll fix this issue later ...
Thank you

---

### Post by dancingfool on 2007-11-06
First post in this thread has worked for tx1320us running gutsy32 for wireless and sound (have not had time to try touchscreen yet).  I did need to recompile ndiswrapper from source after running the uninstall MANY times to remove ndiswrapper, but the dell drivers are working fine now even with wpa. Thanks to all in this thread for this great assistance.

---

### Post by dancingfool on 2007-11-06
It looks like I will need to recompile the kernel to use both turion64 processors.  Has anyone done this for the tx1000 series of notebooks?    I do not really need the speed (Ubuntu already screams past the pathetically slow Vista that came on this laptop), but there are two processors.

---

### Post by Cuppa-Chino on 2007-11-08
With Skype Beta now supporting Video, I have gone back to trying to get my webcam to work.

I have tried this:

[http://thesorcerer.wordpress.com/2007/09/25/yaht-yet-another-how-to-install-webcam-on-pavilion-dv6000-dv9000-series/]("http://thesorcerer.wordpress.com/2007/09/25/yaht-yet-another-how-to-install-webcam-on-pavilion-dv6000-dv9000-series/")

but with this I only get a small bit of the window in Ekiga, most of picture is green and some various bits of code fluttering about (NB I am using V4L2 and NTSC picture as all other settings do not work)

what drivers have people used here and has anybody got it working with skype video?

lsusb
Bus 002 Device 006: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 002 Device 005: ID 08ff:1600 AuthenTec, Inc. 
**Bus 002 Device 004: ID 05ca:1810 Ricoh Co., Ltd **
Bus 002 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 03f0:171d Hewlett-Packard 
Bus 001 Device 001: ID 0000:0000

---

### Post by ghonz on 2007-11-08
> **Cuppa-Chino said:**
> With Skype Beta now supporting Video, I have gone back to trying to get my webcam to work.

I have tried this:

[http://thesorcerer.wordpress.com/2007/09/25/yaht-yet-another-how-to-install-webcam-on-pavilion-dv6000-dv9000-series/]("http://thesorcerer.wordpress.com/2007/09/25/yaht-yet-another-how-to-install-webcam-on-pavilion-dv6000-dv9000-series/")

but with this I only get a small bit of the window in Ekiga, most of picture is green and some various bits of code fluttering about (NB I am using V4L2 and NTSC picture as all other settings do not work)

what drivers have people used here and has anybody got it working with skype video?


Mine worked out of the box with both ekiga and skype.

---

### Post by ghonz on 2007-11-08
> **diatribex said:**
> 
Next comes audio.  Seems it had some trouble because of the Jack sensing on the front jacks...

Try adding this to /etc/modprobe.d/alsa-base

options snd-hda-intel index=0 model=3stack position_fix=0 single_cmd=0

I've tried doing this but I keep getting told 'permission denied' what an I doing wrong?

Jon

---

### Post by lovell88 on 2007-11-08
Sorry, I am a complete newb to Ubunty and mostly linux.  I do have some Terminal experience but l have never install a Linux distro before.

I have the tx1120us and decided that I was going to install Gutsy to try it out.  I downloaded the 32 bit ISO, burnt it to a CD, inserted it and it booted up.  Now when I choose any of the start or install option, it gets past the GUI loading screen and goes into the text base screen that I assume is doing boot/install related stuff.  It seems to be going fine and then quits.  It goes to a black screen. the CD stops spinning and I cant eject.  There is no blinking cursor of any sort and no HDD activity at all for a long time.  After a long time of patience to see if something happens, nothing does and I am forced to slide and hold the power button to turn it off.

Any advice to get this working?  I got it installed and running perfectly on VMWare and this seems soo odd.

Thansk in advance. :)

---

### Post by Francis Pereira on 2007-11-09
I seem to have a rather different experience installing ubuntu 7.10 on a tx1003au. [COLOR=Red]I don't need noapic[/COLOR]. vga=someValidMode seems mandatory without which the kernel stops just after enabling APIC IRQ support. I use the following kernel parameters  "ro  vga=0x317 acpi_osi="!Linux" pci=routeirq". I got the acpi_osi="!Linux" and pci=routeirq after looking at the logs. The following work

CPU => yes => frequency scaling and twin cores enabled
Touchscreen =>  yes  =>  have to calibrate it with touchkit though
Usb  =>  yes
webcam  => yes  => v4l2
audio  =>  yes  => compiled alsa drivers
wifi  => yes => driver that the redistricted driver manager had to offer
graphic card  => yes  =>  with proprietor nvidia drivers from the redistricted driver manager
Remote => yes

vga=317 gives me a screen which is completely blank ! I think its not the correct value. Even my consoles f1-f6 are just blank, though I can flip back to f7. Hibernate seems to work as well. My notebook resumes though the display is corrupted. I think its because of the wrong vga parameter.  after resume only the display is corrupted the system is completely responsive. I am going to try vbetest to get the right vga mode value as soon as I find a live Fedora cd. 

Does this work for anyone else ??

Will keep you updated. :popcorn:


Cheers ,
Francis

---

### Post by kstan_79 on 2007-11-09
> **doryphore said:**
> Hi Kstan,
i can't have cellwriter working with evtouch. It just writes dots and not lines. The sme thing happens with xournal and not with gournal. 
Do you use a 64-bit version of gutsy ? Could you put your xorg.conf to see the evtouch part ?

Moreover, i can't have sound working. I didn't try to compile the new drivers, i just wanted to test the speakers. So i'll fix this issue later ...
Thank you

in that situation I guess your evtouch is not yet configure properly. for myself cellwriter is only a tool interact with your screen, you even can use it with mouse. Below is my xorg.conf.


# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
InputDevices "/dev/input/evtouch_event"
EndSection

Section "InputDevice"   		#  neue Section anlegen
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/evtouch_event"  # correspond to the touchscreen event number
  #  Option "Device" "/dev/input/event3"  # correspond to the touchscreen event number
    Option "DeviceName" "touchscreen"
    #########################################
    # ein guter Anfang, wird später editiert:
    #########################################
    Option        "MinX"        "48"
    Option        "MinY"        "97"
    Option        "MaxX"        "4015"
    Option        "MaxY"        "3974"
    #########################################
   Option "ReportingMode" "Raw"
   Option "Emulate3Buttons"
   Option "Emulate3Timeout" "50"
   Option "SendCoreEvents"
# Option "Calibrate"  "1"		# wird nur zur Kalibrierung gebraucht!
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation C51 [Geforce 6150 Go]"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-60
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51 [Geforce 6150 Go]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
Option "TwinView" "0"
Option "metamodes" "1280x800_60 +0+0"
Option "RandRRotation" "on"
	SubSection "Display"
		Modes		"1200x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
 InputDevice  "touchscreen" "CorePointer
# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by VincenzoAMD64 on 2007-11-09
Hello everybody,

my hard disk is writing few bytes every 5 sec, I see it from the HD led and also from the System Monitor application.
My wireless interface is turned off, I can't understand if the problem is related to some service running..
I have Ubuntu Gutsy 64, on HPTX1000 TURION 64x2.

I started the following thread, looking for a solution...
[http://ubuntuforums.org/showthread.php?t=607642](http://ubuntuforums.org/showthread.php?t=607642)

do you have the same problem?

Vincenzo

---

### Post by Cuppa-Chino on 2007-11-09
> **ghonz said:**
> Mine worked out of the box with both ekiga and skype.

do you have the same in built camera?

what shows when you do lsusb?

EDIT:  not sure if I even had to install the drivers mentioned above -- I still have them on the system though, what I have now done is (simple really) to edit **System-->Preferences-->Multimedia Systems Selector | Video tab | Default input = V4L2 Device = HP Pavilion Webcam1 (pipeline show v4l2 and /dev/video0 ** 

> **Francis Pereira said:**
> I seem to have a rather different experience installing ubuntu 7.10 on a tx1003au. [COLOR=Red]I don't need noapic[/COLOR]. vga=someValidMode seems mandatory without which the kernel stops just after enabling APIC IRQ support. I use the following kernel parameters  "ro  vga=0x317 acpi_osi="!Linux" pci=routeirq". I got the acpi_osi="!Linux" and pci=routeirq after looking at the logs. The following work

Usb  =>  yes
webcam  => yes  => v4l2

vga=317 gives me a screen which is completely blank ! I think its not the correct value. Even my consoles f1-f6 are just blank, though I can flip back to f7. Hibernate seems to work as well. My notebook resumes though the display is corrupted. I think its because of the wrong vga parameter.  after resume only the display is corrupted the system is completely responsive. I am going to try vbetest to get the right vga mode value as soon as I find a live Fedora cd. 

Does this work for anyone else ??

Cheers ,
Francis

I shall try your boot settings, odly enough I now had to include vga=0x317 again...

---

### Post by Cuppa-Chino on 2007-11-09
> **lovell88 said:**
> Sorry, I am a complete newb to Ubunty and mostly linux.  I do have some Terminal experience but l have never install a Linux distro before.

I have the tx1120us and decided that I was going to install Gutsy to try it out.  I downloaded the 32 bit ISO, burnt it to a CD, inserted it and it booted up.  Now when I choose any of the start or install option, it gets past the GUI loading screen and goes into the text base screen that I assume is doing boot/install related stuff.  It seems to be going fine and then quits.  It goes to a black screen. the CD stops spinning and I cant eject.  There is no blinking cursor of any sort and no HDD activity at all for a long time.  After a long time of patience to see if something happens, nothing does and I am forced to slide and hold the power button to turn it off.

Any advice to get this working?  I got it installed and running perfectly on VMWare and this seems soo odd.

Thansk in advance. :)

you should try using the noapic boot option, when the cd startup window comes up, press F6 and add
**noapic vga=0x317** 
and see if it starts, please check earlier parts of this thread as well

---

### Post by Francis Pereira on 2007-11-09
I forgot to mention I am using the F18 bios. Flashed in from Vi$Ta

---

### Post by VincenzoAMD64 on 2007-11-11
Hello,
is there someone can help me with TX1000 Hard Disk writing issue?

my hard disk is writing few bytes every 5 sec visible from the HD led,
1) I used the command "top" but there is no info about disk I/O usage.
2) I tried also: sudo hdparm -B 255 /dev/sda following the thread suggestion:
[http://ubuntuforums.org/showthread.php?t=531866](http://ubuntuforums.org/showthread.php?t=531866)
but it does not work for our HP model.

I am worried about this activity because it causes my hard disk working also when I do not use my notebook. This behaviour could reduce the life of my disk.
(my notebook is power on every day for 8 hours)
Could it be the cause that I read somewhere in internet about Ubuntu Gutsy damage hard disks?
starting the laptop this morning I noticed that when I am at the initial login screen the HD activity is not present. This means that it is related to some Desktop application and not to HD Kernel handling.
Some suggestions?

I love my Ubuntu HP mini notebook
Vincenzo

---

### Post by Francis Pereira on 2007-11-11
[COLOR=SlateGray]With noapic all seems good so far !! Though the touchscreen is a tricky one . Sometimes it registeres as a hid device and can be found at /dev/usb/hiddev0. It is only when it is registered as hid that I can use the touchscreen. It is never responsive when its on /dev/input/event2 or event3 or event4. Any idea as to how i can get it to register as a HID device on every reboot ??? Maybe blacklist the other driver, though I not sure which other driver it used 
[/COLOR] 
Ciao ,
Francis

EDIT : blacklisted the usbtouchscreen module and all works well now . Will post a How to later today

---

### Post by VincenzoAMD64 on 2007-11-12
Ok,
I solved the problem about the HD writes every 5 seconds issue.
[http://ubuntuforums.org/showthread.php?t=607642&page=2](http://ubuntuforums.org/showthread.php?t=607642&page=2)

thank you to all
Vincenzo

---

### Post by dehuszar on 2007-11-12
Is anyone else noticing ridiculously long load times with Inkscape on the tx1000 series?  I have a 1320us and Inkscape literally takes over a minute to load.  I can't tell if it's because of the noapic, irqpoll, etc... kernel options, or some bug somewhere, but as I use Inkscape several times a week to get my design work done, it's really making me crazy.

Thanks in advance,
Sam

---

### Post by wyue013 on 2007-11-13
Hello, I am new to Linux, and is having trouble installing a working driver for my sound card. I initially used the solution of adding "options snd-hda-intel model=3stack" to "/etc/modprobe.d/alsa-base.conf", but I wasn't pleased with not having my headphones to work. I followed a guide - [http://www.kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z#_Sound]("http://www.kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z#_Sound") that told me to try out alsa-driver-1.0.15rc3, but my sound card ended up undetectable, worse than not having this driver.

Can someone please show me how to return the sound card driver to default, so that I can atleast get my sound card detected? I have tried using "sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils" and reinstall them by "sudo apt-get install linux-sound-base alsa-base alsa-utils", and rebooted, but didn't work.

Thanks a bunch!

---

### Post by miknix on 2007-11-13
> **jcase008 said:**
> **DSDTs Wanted**

```

        Device (QBTN)
        Device (DBTN)
        Device (MUBN)
        ...

```

These devices are part of "Direct App Launch" used on Vista.
<<The Windows Vista(TM) operating system provides built-in support for a fast system startup experience that boots or resumes directly into media or other applications. This support, called direct application launch, is possible on PCs that are running Windows Vista by making simple changes to platform firmware and underlying platform wake circuitry.>>

I made a ACPI linux driver to support these buttons. Read more on the project page: [http://quickstart.sourceforge.net/]("http://quickstart.sourceforge.net/")

**ATTENTION: Project name changed from hotstart-acpi to quickstart to avoid legal issues with trademark Hotstart registered by Microsoft.**

Please let me know (or report to the mailing list) if the driver works for you.

Thanks

---

### Post by avik on 2007-11-13
Searching this thread, I found numerous references to the 100% cpu problem, and that was what I thought my problem was.  Upon actually monitoring the cpu usage, as well as the frequency scaling, everything seems normal.

The only problem is that the fans kick into overdrive whenever I boot up the LiveCD or start an application.

I'm going to install Ubuntu today or tomorrow, but the fan issue is a bit problematic, with my desk shaking a bit.  Has this happened to anybody, and if so, has installing Ubuntu had any effect?  Note that I have *had* to use noapic in order to boot the LiveCD at all.

Thanks.

EDIT: It's a good thing I took a shot.  The fan problem is gone after installation!  CPU wise, everything is great.

---

### Post by phattyacid on 2007-11-13
> **miknix said:**
> These devices are part of "Direct App Launch" used on Vista.
<<The Windows Vista(TM) operating system provides built-in support for a fast system startup experience that boots or resumes directly into media or other applications. This support, called direct application launch, is possible on PCs that are running Windows Vista by making simple changes to platform firmware and underlying platform wake circuitry.>>

I made a ACPI linux driver to support these buttons. Read more on the project page: [http://hotstart-acpi.sourceforge.net/]("http://hotstart-acpi.sourceforge.net/")

Please let me know (or report to the mailing list) if the driver works for you.

Thanks

listing the ACPI buttons seemed to work, but when I press the buttons I still have "none" showing up.  gutsy 64bit on a tx1320us

---

### Post by VincenzoAMD64 on 2007-11-14
> **wyue013 said:**
> Hello, I am new to Linux, and is having trouble installing a working driver for my sound card. I initially used the solution of adding "options snd-hda-intel model=3stack" to "/etc/modprobe.d/alsa-base.conf", but I wasn't pleased with not having my headphones to work. I followed a guide - [http://www.kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z#_Sound]("http://www.kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z#_Sound") that told me to try out alsa-driver-1.0.15rc3, but my sound card ended up undetectable, worse than not having this driver.

Can someone please show me how to return the sound card driver to default, so that I can atleast get my sound card detected? I have tried using "sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils" and reinstall them by "sudo apt-get install linux-sound-base alsa-base alsa-utils", and rebooted, but didn't work.

Thanks a bunch!

Hi,
I had the same problems,
follow the instruction inside this thread:
[http://ubuntuforums.org/showpost.php?p=3475485&postcount=235](http://ubuntuforums.org/showpost.php?p=3475485&postcount=235)

My boot options are:
ro quiet splash acpi_osi=!Linux acpi_os_name="Windows 2006" noapic irqpoll

Bye
Vincenzo

---

### Post by miknix on 2007-11-15
> **Zamboniman said:**
> Here's mine:

 ```

Device (QBTN)
        {
            Name (_HID, EisaId ("PNP0C32"))
            (...)
        }

 Device (DBTN)
        {
            Name (_HID, EisaId ("PNP0C32"))
            (...)
        }
(...)

```

These devices are part of "Direct App Launch" used on Vista.
<<The Windows Vista(TM) operating system provides built-in support for a fast system startup experience that boots or resumes directly into media or other applications. This support, called direct application launch, is possible on PCs that are running Windows Vista by making simple changes to platform firmware and underlying platform wake circuitry.>>

In Vista this technology is called Hotstart(TM). You can google for hotstart, there is some propaganda about it.

Anyway, I made a ACPI linux driver to support these buttons. Read more on the project page: [http://quickstart.sourceforge.net/](http://quickstart.sourceforge.net/)

Please let me know (or report to the mailing list) if the driver works for you.

Thanks

---

### Post by miknix on 2007-11-15
> **phattyacid said:**
> listing the ACPI buttons seemed to work, but when I press the buttons I still have "none" showing up.  gutsy 64bit on a tx1320us

This driver is not intended to make the hotkeys work in runtime, but to support some underlying mechanisms instead that makes work the so called "Direct App Launch" (PNP0C32) which is used in Vista Hotstart(TM).

To have hotkeys working in runtime you may look to other devices other than those detected as PNP0C32. Although, there is a way to make the quickstart driver reporting run-time button events. I'll soon upload a new driver that reports them.

You can read more at [http://quickstart.sourceforge.net/]("http://quickstart.sourceforge.net/")

---

### Post by cueball1981 on 2007-11-16
hi guys im a noob in linux and install ubunto7.1 amd64 on my tx1222au.. and installin if fine.. chk cd for error before installing but after the splash screen clear but laptop gut show a black screen?? (process bar is completed)

---

### Post by Cuppa-Chino on 2007-11-16
dsdt thingy

---

### Post by phattyacid on 2007-11-16
> **miknix said:**
> This driver is not intended to make the hotkeys work in runtime, but to support some underlying mechanisms instead that makes work the so called "Direct App Launch" (PNP0C32) which is used in Vista Hotstart(TM).

To have hotkeys working in runtime you may look to other devices other than those detected as PNP0C32. Although, there is a way to make the quickstart driver reporting run-time button events. I'll soon upload a new driver that reports them.

You can read more at [http://quickstart.sourceforge.net/]("http://quickstart.sourceforge.net/")

OK, that's cool.  I was just saying that I tested, it worked as per what you said, but the "reporting" part wasn't there yet.

I assume that for the reporting stuff, the end-game is that when you get the event you can delegate to some external code (shell script, java, bin, whatever)

---

### Post by Cuppa-Chino on 2007-11-17
btw I now got the webcam working also in skype, how do I change brightness and such for it, I am bit lost for that at the moment

---

### Post by v.cecchetto on 2007-11-17
Only for your information.

My kernel parameter (/boot/grub/menu.lst):

ro quiet splash noapic acpi_irq_balance vga=0x0318

For framebuffer issue i solved with

 (/etc/modprobe.d/blacklist-framebuffer): 

# blacklist vesafb

(/etc/initramfs-tools/modules):

fbcon
vesafb

I got a TX1020ea. :KS

---

### Post by v.cecchetto on 2007-11-17
Brightness Applet.

Using the touchscreen once i dropped down the brightness to zero in the Brightness Applet.

With the screen completly black it's difficult to reach the applet and set the brightness.

- First solution:

restart in safe mode and edit this file

vi ~/.gconf/apps/gnome-power-manager/backlight/%gconf.xml

and modify the brightness to 100 in the line

<entry name="brightness_ac" mtime="1194971002" type="int" value="100">

- Second solution:

shut down the computer brutally, so the new brightness parameter are not saved, when you restart you find the old brightness level

:popcorn:

---

### Post by avik on 2007-11-17
Out of the people who have gotten the touchscreen working, is anyone using 64 bit Ubuntu?  If so, how did you get it working.

The evtouch driver (from the xserver-xorg-input-evtouch) package segfaults, the downloadable binary is 32bit only, and I can't compile from source due to errors.

I found the TouchKit drivers, and that was the closest I got to getting the touchscreen to work.  The driver recognizes my taps on the screen, but they all map to the bottom-left of the touchable area (which can be changed using the driver configuration tool).  I need to use noapic, otherwise the computer doesn't boot up.

Any tips?

---

### Post by phattyacid on 2007-11-18
> **avik said:**
> Out of the people who have gotten the touchscreen working, is anyone using 64 bit Ubuntu?  If so, how did you get it working.

The evtouch driver (from the xserver-xorg-input-evtouch) package segfaults, the downloadable binary is 32bit only, and I can't compile from source due to errors.

I found the TouchKit drivers, and that was the closest I got to getting the touchscreen to work.  The driver recognizes my taps on the screen, but they all map to the bottom-left of the touchable area (which can be changed using the driver configuration tool).  I need to use noapic, otherwise the computer doesn't boot up.

Any tips?

used TouchKit (egalax) drivers and followed their instructions for installation (not any random stuff on this thread).  compiled tkusb as specified in instructions and then calibrated using TouchKit GUI.  it works, but could be a lot better.

---

### Post by waspbr on 2007-11-18
think it may be helpful to compile the working information for gutsy into a single manual

---

### Post by avik on 2007-11-18
> **phattyacid said:**
> used TouchKit (egalax) drivers and followed their instructions for installation (not any random stuff on this thread).  compiled tkusb as specified in instructions and then calibrated using TouchKit GUI.  it works, but could be a lot better.

That's exactly what I did, even before posting.  I tried it again, following the included instructions exactly, but still the issue persists.

Everything else is fine.  I can technically click, and even right-click by holding down the stylus.  The only thing I can't do is actually move the cursor out of the bottom-left corner using the touchscreen.

What are your boot parameters?  And what exactly do you mean by "could be a lot better?"

Thanks.

---

### Post by thagame on 2007-11-18
does anyone here have the touchscreen drivers from the EETI site. I need the 32bit one and the site doesnt work anymore for some reason.

---

### Post by avik on 2007-11-18
> **thagame said:**
> does anyone here have the touchscreen drivers from the EETI site. I need the 32bit one and the site doesnt work anymore for some reason.

The EETI site does work, but you have to go through the main page (eeti.com).  Otherwise, here's the page with the Linux drivers on it: [http://210.64.17.161:1182/web20/TouckDriver/linuxDriver.htm]("http://210.64.17.161:1182/web20/TouckDriver/linuxDriver.htm").

---

### Post by avik on 2007-11-19
Okay, so since I seem to be having more of an issue with the touchscreen than anyone else, can anyone using the TouchKit driver send me his or her /etc/egalax.cal file?  I tried to edit mine with a hex editor, but I couldn't find any discernible patterns other than the header.  Perhaps a working reference point would be useful.  You can PM me if you want.  Be sure to include your resolution if you do send me the file.  Thanks.

---

### Post by fubenkyou on 2007-11-20
> **avik said:**
> Okay, so since I seem to be having more of an issue with the touchscreen than anyone else, can anyone using the TouchKit driver send me his or her /etc/egalax.cal file?  I tried to edit mine with a hex editor, but I couldn't find any discernible patterns other than the header.  Perhaps a working reference point would be useful.  You can PM me if you want.  Be sure to include your resolution if you do send me the file.  Thanks.

Hey, did you ever figure out the issue you're having? I'm having it too. The screen register the taps but I'm unable to move the cursor from the bottom left.

---

### Post by avik on 2007-11-20
> **fubenkyou said:**
> Hey, did you ever figure out the issue you're having? I'm having it too. The screen register the taps but I'm unable to move the cursor from the bottom left.

Nope.  I'm still hoping someone might give his or her egalax.cal so I can try to figure out what's going on.  Until then, I pretty much have nothing to go on.

---

### Post by PTGreg on 2007-11-21
Hi,

I have a Tx1320 US.

I installed Ubuntu 7.10 AMD64

I have the touchscreen working with the Egalax drivers:
[http://210.64.17.161:1182/web20/TouckDriver/linuxDriver.htm](http://210.64.17.161:1182/web20/TouckDriver/linuxDriver.htm)

the only problem is that when I invert my screen using:
```
xrandr -o inverted
```
the touchscreen become inverted. 

I figured that the configuration file for the calibration is:
```
/etc/egalax.cal
```

So I created one version when my screen is normal and one when my screen is inverted.
My idea was to switch between them while rotating my screen using a simple script.

The problem is that this file are not accessed all the time, it is only "loaded", for exemple, when you save your configuration using ./TouchKit.

I was wondering if anyone had an idea, on how to manually load those configuration when needed. Or if anyone has a better solution for this problem.



and does anyone managed to make the circles arrow ake Rotate button on screen work? 

Cheers,

PTGreg

---

### Post by farbird on 2007-11-21
anyone managed to get fn-f7 and fn-f8 working for screen brightness?
I couldnt control the brightness on my tx1005au
I am on kubuntu gutsy gibbon

---

### Post by MadMax08 on 2007-11-22
First off, thanks for all the help everyone. Any way we could Sticky this thread?

i've got everything working except for my headphone jacks. i followed one of the instructions on this thread, but i didn't see any results. I'm running Gutsy 64.

any suggestions?

---

### Post by avik on 2007-11-22
> **MadMax08 said:**
> First off, thanks for all the help everyone. Any way we could Sticky this thread?

i've got everything working except for my headphone jacks. i followed one of the instructions on this thread, but i didn't see any results. I'm running Gutsy 64.

any suggestions?

Try the second method here: [http://www.kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z#_Sound]("http://www.kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z#_Sound").

---

### Post by farbird on 2007-11-23
anyone managed to get screen rotation to work the way it worked on vista on these tx series?

---

### Post by PTGreg on 2007-11-24
here is my egalax

[http://files-upload.com/files/639288/egalax.cal](http://files-upload.com/files/639288/egalax.cal)

Hope it helps.

---

### Post by avik on 2007-11-25
> **PTGreg said:**
> here is my egalax

Thanks, PTGreg.  I've been messing around with it, and it's interesting.  Replacing my egalax.cal with yours results in the cursor going to the *top* left, instead of the bottom.  Then, changing *any* byte, no matter how seemingly insignificant, causes the cursor to go to the bottom left, as before.

I'll try some more messing around, but this is really weird.

---

### Post by simplyw00x on 2007-11-25
Any ideas about the previously-reported issue with the graphics card fan never turning on? Kind of a problem when my lap starts melting...

---

### Post by Francis Pereira on 2007-11-26
> **simplyw00x said:**
> Any ideas about the previously-reported issue with the graphics card fan never turning on? Kind of a problem when my lap starts melting...

Just wondering, how do you know there is a fan on the graphic card and that is does not turn on. HP's documentation shows only one fan ! 

Though I must agree the laptop feels cooler while running it on vista.

I checked the temperature using a infrared sensor and it seems normal at about 45-50C

---

### Post by phenolholic on 2007-11-26
anyone connect a bluetooth mouse? i'm having problems. i followed other threads but mine wont connect. i have a logitech v470 bluetooth laser mouse. i used the 69*.rules file in some earlier thread to make a dynamic link to /dev/input/evtouch_event to the correct instance. posted is my xorg.conf.. maybe something there (or lack thereof) is not allowing my mouse to be functional. i used `hidd --connect (mac address of mouse)` and it connects, but nothing happens. below is my xorg. thanks



# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
        Load    "dbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
Identifier "touchscreen"
Driver "evtouch"
Option "Device" "/dev/input/evtouch_event"
Option "DeviceName" "touchscreen"
Option "MinX" "48"
Option "MinY" "110"
Option "MaxX" "4006"
Option "MaxY" "4002"
Option "x0" "-1"
Option "y0" "-3"
Option "x1" "-6"
Option "y1" "-4"
Option "x2" "-2"
Option "y2" "-6"
Option "x3" "-2"
Option "y3" "-3"
Option "x4" "-4"
Option "y4" "-3"
Option "x5" "2"
Option "y5" "-1"
Option "x6" "-5"
Option "y6" "-3"
Option "x7" "-2"
Option "y7" "1"
Option "x8" "5"
Option "y8" "2"
Option "TapTimer" "2"
Option "LongTouchTimer" "100"
Option "ReportingMode" "Raw"
Option "SendCoreEvents" "On"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mouse0"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection


Section "Device"
        Identifier      "nVidia Corporation C51 [Geforce 6150 Go]"
        Driver          "nvidia"
        BusID           "PCI:0:5:0"
        Option          "AddARGBGLXVisuals" "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
        Option          "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation C51 [Geforce 6150 Go]"
        Monitor         "Generic Monitor"
        Option          "AddARGBGLXVisuals" "True"
        Option          "RandRRotation" "on"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x800"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "touchscreen" "CorePointer"
        InputDevice     "Synaptics Touchpad"
EndSection

---

### Post by simplyw00x on 2007-11-26
> Just wondering, how do you know there is a fan on the graphic card and that is does not turn on. HP's documentation shows only one fan !
Because the laptop gets incredibly hot (conky shows 70C and it's painful to touch the GFX card area) and there is clearly a fan blowing out of that vent before GRUB is loaded.

---

### Post by Francis Pereira on 2007-11-26
> **simplyw00x said:**
> Because the laptop gets incredibly hot (conky shows 70C and it's painful to touch the GFX card area) and there is clearly a fan blowing out of that vent before GRUB is loaded.

I would agree that the laptop seems warmer that in vista . Tough HP documentation [http://h10032.www1.hp.com/ctg/Manual/c00853874.pdf](http://h10032.www1.hp.com/ctg/Manual/c00853874.pdf) shows that there is only one fan ! Since its a on board card I doubt it would have a GFX fan . The vents blow out air during POST

---

### Post by simplyw00x on 2007-11-28
My acpi fans directory is empty. There is definitely some temperature-control issue with this laptop that occurs uniquely on linux.

---

### Post by v.cecchetto on 2007-11-28
A new version of the script to rotate the screen. For the new xrandr version.

rotate.sh
..........................................................
#!/bin/bash          

STR=`xrandr --verbose | awk '/default/{print $5}'`

case "$STR" in
     'normal')
	 xrandr -o left
         ;;
     'left')
         xrandr -o inverted
         ;;
     'inverted')
         xrandr -o right
         ;;
     'right')
         xrandr -o normal
         ;;
esac
..........................................................

:KS

---

### Post by simplyw00x on 2007-11-29
Love that script; I was using:
```
#!/bin/sh

# Change System Input orientation for Tablet Mode
if [ -n "$(xrandr | grep 800x1280)" ]||[ -n "$(xrandr | grep 1024x2560)" ]; then
        xrandr -o normal
        #sudo /usr/bin/touchscreen_switch.sh 
else
        xrandr -o left
        #sudo /usr/bin/touchscreen_switch.sh l
fi
```

---

### Post by steinkaare on 2007-11-30
> **sauronsmatrix said:**
> Okay, so install these five, (e.g. using Synaptic Package Manager).
[INDENT]po-debconf
debhelper
quilt
alsa-base
libc6-dev
[/INDENT]

Then, install [alsa-driver]("http://alsa.cybermirror.org/driver/alsa-driver-1.0.15.tar.bz2"):

1) Extract archive to some[COLOR="Red"] folder[/COLOR].

2) Open up a terminal.
make yourself the root user with "su"

3) go to the [COLOR="Red"]folder[/COLOR] with the "cd" command

4) Run these commands in this order:
[INDENT]./configure
make
make install
[/INDENT]

Note: Yes, this process can take like** 3 minutes**.

When its installed, add this line to/etc/modprobe.d/alsa-base [use command "gedit /etc/modprobe.d/alsa-base" under "su" priveleges]:
[INDENT]
options snd-hda-intel model=hp[/INDENT]

If your sound isn't working at startup (e.g. you cannot hear the ubuntu login noise, then do this:

gedit /etc/modules

Add these lines to the bottom:
```
snd-hwdep
snd-hda-intel
```


Restart your computer, and bam. It should be working. If you do not understand my instructions, feel free to ask me to clarify.

***_[COLOR="Navy"]NEW PROBLEM! It seems that when you update the kernel, the drivers stop working. A solution is at hand:[/COLOR]_***

**NOTE**: Change the [COLOR="Blue"]kernel version [/COLOR]as necessary.

There are two copies of the snd_hda_intel,ko file lurking in /lib/modules:
```
[COLOR="Blue"]/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
[COLOR="DarkGreen"]/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko[/COLOR]
```

To solve this problem, run these commands in the a terminal under "su" privileges
```
rm [COLOR="Blue"]/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
ln -s [COLOR="DarkGreen"]/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko[/COLOR] [COLOR="Blue"]/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
```

gedit /etc/modules

Add these lines to the bottom:
```
snd-hwdep
snd-hda-intel
```

Restart, and it should be working.

A HUGE thanks to [benguin]("http://ubuntuforums.org/member.php?u=9893"), who framed the solution for the kernel update bug.

Im having trouble with the command "su" su: Authentication failure Sorry.
I type "sudo -i" and im listed as root, but i dont know if that command has the same function. but i ttype "cd" and nothing happens

---

### Post by xpelaox on 2007-11-30
HI guys, i own this awsome notebook and i installed Ubuntu 7.10, and i can't manage to make the touch screen work. i tried to look up in this thread but it is too large and i couldn't find "THE ANSWER" could sombody tell me exactly how to install the Touchscreen, and also the Rotation stuff? Thanks a lot!!!

---

### Post by steinkaare on 2007-12-01
sauronsmatrix your tip worked perfect, except the headphones mute, but i'll fix it thanks a lot

---

### Post by jcase008 on 2007-12-01
> **miknix said:**
> 
Please let me know (or report to the mailing list) if the driver works for you.


The driver successfully complies and can be loaded at boot time.  New devices show up in /sys/devices/acpi_system:00/device:00, but no button presses are reported in dmesg or /var/log/messages.  Also, the file power/state never seems to change when a button is pressed.  I have enable_runtime_btns=1 as one of my kernel parameters.

I haven't looked for ACPI subsystem programming docs.  How did you create this module?  What documentation did you read (i.e. how do I get started to help?)  I've created other drivers before for work and play, but haven't played with the ACPI subsystem yet.

---

### Post by sauronsmatrix on 2007-12-04
For the touchscreen, I used [these directions]("http://ubuntuforums.org/showpost.php?p=2792971&postcount=16") and they worked perfectly.

---

### Post by zzandman on 2007-12-05
> **sauronsmatrix said:**
> Okay, so install these five, (e.g. using Synaptic Package Manager).
[INDENT]po-debconf
debhelper
quilt
alsa-base
libc6-dev
[/INDENT]

Then, install [alsa-driver]("http://alsa.cybermirror.org/driver/alsa-driver-1.0.15.tar.bz2"):

1) Extract archive to some[COLOR="Red"] folder[/COLOR].

2) Open up a terminal.
make yourself the root user with "su"

3) go to the [COLOR="Red"]folder[/COLOR] with the "cd" command

4) Run these commands in this order:
[INDENT]./configure
make
make install
[/INDENT]

Note: Yes, this process can take like** 3 minutes**.

When its installed, add this line to/etc/modprobe.d/alsa-base [use command "gedit /etc/modprobe.d/alsa-base" under "su" priveleges]:
[INDENT]
options snd-hda-intel model=hp[/INDENT]

If your sound isn't working at startup (e.g. you cannot hear the ubuntu login noise, then do this:

gedit /etc/modules

Add these lines to the bottom:
```
snd-hwdep
snd-hda-intel
```


Restart your computer, and bam. It should be working. If you do not understand my instructions, feel free to ask me to clarify.

***_[COLOR="Navy"]NEW PROBLEM! It seems that when you update the kernel, the drivers stop working. A solution is at hand:[/COLOR]_***

**NOTE**: Change the [COLOR="Blue"]kernel version [/COLOR]as necessary.

There are two copies of the snd_hda_intel,ko file lurking in /lib/modules:
```
[COLOR="Blue"]/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
[COLOR="DarkGreen"]/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko[/COLOR]
```

To solve this problem, run these commands in the a terminal under "su" privileges
```
rm [COLOR="Blue"]/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
ln -s [COLOR="DarkGreen"]/lib/modules/2.6.22-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko[/COLOR] [COLOR="Blue"]/lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko[/COLOR]
```

gedit /etc/modules

Add these lines to the bottom:
```
snd-hwdep
snd-hda-intel
```

Restart, and it should be working.

A HUGE thanks to [benguin]("http://ubuntuforums.org/member.php?u=9893"), who framed the solution for the kernel update bug.


Hello!
I've done this now and got my sound working including the headphones :) BUT after this procedure it takes 1-2 minutes longer to boot the desktop... After I enter username and password I just get a orange screen and a mouse cursor for about 1 minute and after that everything loads as it should... Could someone pleeease help me! :confused:

---

### Post by Vineus on 2007-12-06
Thanks everyone for this thread, it helped me a lot.

If you want to see the fingerprint reader working:

[http://www.reactivated.net/fprint/wiki/Main_Page](http://www.reactivated.net/fprint/wiki/Main_Page)

The detection is not that good for now but they jsut started development. And at least its a driver :-)

use the AES 1610 driver

---

### Post by dmarinescu on 2007-12-06
hi everyone!

got great news, not only for ubuntu users but actually for everyone using hp tx 1000 (tx 1xxx) series!

i'll get right to the point:

1. there is NO need to disable apic and / or lapic! the bios  asks the kernel for os name. if not windows, then apic is disabled by the bios (and of course, you have to also disable it from kernel params, using nolapic. again, this is not the way to use this machine!
2. there is a problem with IRQ7! fixirq or irqpool will not really work, unless you enable acpi_irq_balance and, most important you make pci relate to bios irq! specially the last kernel param is crucial in avoiding the 100% second core cpu usage comming from irqpool!

so, to make the whole story short, the following combination of kernel params fixes the irq#7 issues, without disabling lapic! 

noapic acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi="!Linux" acpi_os_name="Windows 2006"

you get the irq fixed and both cores are at almost 0%!

enjoy,
   daniel

---

### Post by dmarinescu on 2007-12-06
perfect kernel params combination for tx1000 series!
allows fully functional apic and lapic and fixes irq(s) with 100% idle for both cores! (applies to all 2.6. kernels, not only to ubuntu stock kernels) 

super important, go like:

acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi="!Linux" acpi_os_name="Windows 2006"

of course, you don't need irqdebug (could go like irqnodebug)

hey, it works!

enjoy,
   daniel

---

### Post by guttersnipe on 2007-12-06
I just upgraded to Gutsy.  Suddenly, I'm swimming in bugs and errors--but at least my computer boots--sort of (it's more to say than the last Ubuntu upgrade, anyway)

When I turn on my computer, after POST, it grub or the kernel or something gives a BIOS error.  It gets STUCK on this error, and does not continue to boot--unless I press the power button.  If I press the power button (no other key works), but don't hold it down as that would turn off the laptop, the booting progresses to the ubuntu load screen.

Does anyone else get this ridiculous problem?

---

### Post by guttersnipe on 2007-12-06
> **dmarinescu said:**
> hi everyone!

got great news, not only for ubuntu users but actually for everyone using hp tx 1000 (tx 1xxx) series!

i'll get right to the point:

1. there is NO need to disable apic and / or lapic! the bios  asks the kernel for os name. if not windows, then apic is disabled by the bios (and of course, you have to also disable it from kernel params, using nolapic. again, this is not the way to use this machine!
2. there is a problem with IRQ7! fixirq or irqpool will not really work, unless you enable acpi_irq_balance and, most important you make pci relate to bios irq! specially the last kernel param is crucial in avoiding the 100% second core cpu usage comming from irqpool!

so, to make the whole story short, the following combination of kernel params fixes the irq#7 issues, without disabling lapic! 

noapic acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi="!Linux" acpi_os_name="Windows 2006"

you get the irq fixed and both cores are at almost 0%!

enjoy,
   daniel

Great, now I get 95% processor usage as opposed to 5%

EDIT: the culprit is "irqfixup."  I deleted that, and I'm idling 5-15% CPU usage.  I didn't even really need to add these options, but who knows? maybe I was missing out on some awesome feature. *shrug*

---

### Post by phattyacid on 2007-12-09
> **dmarinescu said:**
> hi everyone!

got great news, not only for ubuntu users but actually for everyone using hp tx 1000 (tx 1xxx) series!

i'll get right to the point:

1. there is NO need to disable apic and / or lapic! the bios  asks the kernel for os name. if not windows, then apic is disabled by the bios (and of course, you have to also disable it from kernel params, using nolapic. again, this is not the way to use this machine!
2. there is a problem with IRQ7! fixirq or irqpool will not really work, unless you enable acpi_irq_balance and, most important you make pci relate to bios irq! specially the last kernel param is crucial in avoiding the 100% second core cpu usage comming from irqpool!

so, to make the whole story short, the following combination of kernel params fixes the irq#7 issues, without disabling lapic! 

noapic acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi="!Linux" acpi_os_name="Windows 2006"

you get the irq fixed and both cores are at almost 0%!

enjoy,
   daniel

tried this on 1320us with no luck.. without noapic in my boot params, system will not even make it past loading the hardware drivers.

---

### Post by phattyacid on 2007-12-09
> **Vineus said:**
> Thanks everyone for this thread, it helped me a lot.

If you want to see the fingerprint reader working:

[http://www.reactivated.net/fprint/wiki/Main_Page](http://www.reactivated.net/fprint/wiki/Main_Page)

The detection is not that good for now but they jsut started development. And at least its a driver :-)

use the AES 1610 driver

no luck getting it to compile.  Configure with CFLAGS=-fPIC and doesn't seem to pass them to compiler since linker error says to try and recompile with that very flag.

---

### Post by Vineus on 2007-12-09
> **phattyacid said:**
> no luck getting it to compile.  Configure with CFLAGS=-fPIC and doesn't seem to pass them to compiler since linker error says to try and recompile with that very flag.

I don't know, I'm a gentoo guy so I just "emerge fprint_demo" and it worked. The only dependency on the ebuild is imagemagick (so basically at some point it will try to link with imagemagick, so you should have it installed)

---

### Post by belerophonte on 2007-12-10
People,

   I think everything is working properly, except fingerprint. Has anyone managed to make the rotate buttons working as it did in Vista? I was reading some stuff about it and found that in windows you can disable the auto-rotate by renaming the "MCSVActn.dll" file. Perhaps that is the one responsible for those buttons we can't control and the auto-rotate when you rotate the screen. I don't know...

Sincerely,

belerophonte.

---

### Post by v.cecchetto on 2007-12-11
Fingerprint

following the instruction in this link: ([http://www.geekplanet.fr/index.php?option=com_content&task=view&id=25&Itemid=35](http://www.geekplanet.fr/index.php?option=com_content&task=view&id=25&Itemid=35)) 
now i can log in without using password. 

I only insert my username and  i roll my left thumb.

Download all the three new source files from:

[http://sourceforge.net/project/showfiles.php?group_id=208521](http://sourceforge.net/project/showfiles.php?group_id=208521)

--------------------------------------------------------------------
LIBFPRINT - main library
--------------------------------------------------------------------	
	
	sudo apt-get install libmagick9-dev

	sudo ldconfig

	tar xvjf libfprint-0.0.5.tar.bz2

	cd libfprint-0.0.5

	./configure

	make
	
	sudo checkinstall

	sudo ldconfig

--------------------------------------------------------------------	
FPRINT_DEMO - tool to play with your fingers images :)
--------------------------------------------------------------------	
       
        tar xvjf fprint_demo-0.4.tar.bz2

	cd  fprint_demo-0.4

	./configure

	make

	sudo checkinstall

	sudo ldconfig

(i abuse with sudo ldconfig, someone please correct where is not necessary!) :)

--------------------------------------------------------------------	
PAM_FPRINT - if you want to use it at your login
--------------------------------------------------------------------	

	sudo apt-get install libpam0g-dev

	sudo ldconfig
 
        tar xvjf pam_fprint-0.2.tar.bz2

	cd  pam_fprint-0.2

	./configure

	make

	sudo checkinstall

--------------------------------------------------------------------
PAM 
--------------------------------------------------------------------

Add a line in your PAM configuration file

	gksudo gedit /etc/pam.d/gdm

..........................................................
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    sufficient      pam_fprint.so
..........................................................
 
	the important line to add is:

..........................................................
auth    sufficient      pam_fprint.so
..........................................................

	now is time to record your left thumb image
 
	sudo pam_fprint_enroll --enroll-finger 1

..........................................................
1 left thumb
2 left index finger
3 left middle finger
4 left ring finger
5 left little finger
6 right thumb
7 right index finger
8 right middle finger
9 right ring finger
10 right little finger
..........................................................

To record your finger image, you can also use 

        sudo fprint_demo

After you have recorded your (for examples) left thumb, logout.

Next time you login, you have to insert your username. Now the system let you choose: you can roll your left finger or insert your password.

Learn the correct way to roll your finger using the tool:

sudo fprint_demo

Enjoy!
:KS

---

### Post by Vineus on 2007-12-11
Note to gentoo users lost on this huge thread: I started a HOWTO to agregate usefull information.

It can be found here: [http://gentoo-wiki.com/HARDWARE_HP_tx1000](http://gentoo-wiki.com/HARDWARE_HP_tx1000)

(can be useful for others to even if everything is gentoo oriented)

---

### Post by belerophonte on 2007-12-11
v.cecchetto, 
   
   I tried your approach, but after everything installed, it asks me for libWand.so.10.
Can't find it. Well, perhaps I'll try again later.

Thanks...

---

### Post by v.cecchetto on 2007-12-11
Try

sudo ln -s /usr/local/lib/libWand.so.10  /usr/lib/libWand.so.10

as is written in the link

[http://www.geekplanet.fr/index.php?option=com_content&task=view&id=25&Itemid=35](http://www.geekplanet.fr/index.php?option=com_content&task=view&id=25&Itemid=35)

---

### Post by phenolholic on 2007-12-11
any luck with getting a bluetooth mouse to work? i'm using evtouch (for touchscreen) and made a symbolic link to evtouch_event, but cant get my bluetooth mouse (or any usb mouse for that matter) to work. thanks

---

### Post by darky0505 on 2007-12-12
> **v.cecchetto said:**
> Try

sudo ln -s /usr/local/lib/libWand.so.10  /usr/lib/libWand.so.10

like is written in the link

[http://www.geekplanet.fr/index.php?option=com_content&task=view&id=25&Itemid=35](http://www.geekplanet.fr/index.php?option=com_content&task=view&id=25&Itemid=35)

yes, or just do ```
ldconfig
```

---

### Post by rosspoko on 2007-12-13
I'm no expert, so I don't know if this helps or not, but I use the doscsi boot option, and I can suspend and hibernate successfully.

---

### Post by Cuppa-Chino on 2007-12-13
> **rosspoko said:**
> I'm no expert, so I don't know if this helps or not, but I use the doscsi boot option, and I can suspend and hibernate successfully.

sorry to bother you but what are you running exactly:

* gutsy or feisty
* 32bit or 64bit
* open, vesa or nvidia driver
* full line of boot options, what is it you use exactly?

sorry to be a pain but I have tried and tried and tried and this bit has still alluded me so far....

thanks

---

### Post by VincenzoAMD64 on 2007-12-14
Hello guys,
yesterday I have updated my Gutsy64 using the usual "update manager",
the sound card does not work anymore... (it was fully functional)
I have restored back my Gutsy from a recent image and the sound work, after installing the updates the problem occurs again!
is this problem related to my notebook or someone has the same problem?

Thank you
Vincenzo

---

### Post by VincenzoAMD64 on 2007-12-14
Ok,
I solved the problem, the update overwrites the link that I have created to solve the initial Sound Card installation problem...
see
[http://ubuntuforums.org/showpost.php?p=3475485&postcount=235](http://ubuntuforums.org/showpost.php?p=3475485&postcount=235)
it is necessary to recreate it again.

Thank you
Vincenzo

---

### Post by belerophonte on 2007-12-14
Amazing..."doscsi" actualy works.

Using Gutsy on a AMD_64 TX1320us

My question is ... Why?

---

### Post by Cuppa-Chino on 2007-12-14
> **belerophonte said:**
> Amazing..."doscsi" actualy works.

Using Gutsy on a AMD_64 TX1320us

My question is ... Why?

just **doscsi **? whats the full line you used ?

---

### Post by belerophonte on 2007-12-14
Uhmm...

kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d859f6bb-d984-40b7-b60a-1e4b8647678cro quiet splash noapic irqfixup doscsi


And that is it...but still can't find the libWand.so.10 for the fingerprint reader.

---

### Post by waspbr on 2007-12-16
hi everyone ,  I got a tx1320us  and I am running gutsy amd64. 
I have managed to get a bunch of stuff working thanks to this thread and I have you guys to thank for that. 

Although I have hit a bump on the road that I cannot seem to shake. it has to do with the wireless.

I follow sauronsmatrix method described on the link he posted on page 31([http://ubuntuforums.org/showpost.php?p=3491929&postcount=257]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257")) and everything seems to work beautifully well.

that is until restart, than there's no more wireless, thankfully I also have a wired connection. So as far as I can tell the method works however it I cannot manage to save it onto the system.

ndiswrapper does have the drivers installed even after reboot, when i do:
[COLOR="Blue"]
ndiswrapper -l [/COLOR]

I can see the driver installed and yes I have blacklisted the appropriate files.

I manage to get the wireless up again by reinstalling the drivers (-r) and reinstalling (-i), then I do
[COLOR="Blue"]
sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo echo ndiswrapper >> /etc/modules [/COLOR]

the first command  (-m) gives me the message:

[COLOR="Red"]module configuration already contains alias directive[/COLOR]

the last command gives me a bash message: 

[COLOR="Red"]bash: /etc/modules: Permission denied[/COLOR]

what files do I have to do or what file do i have to gedit to make the wireless permanent and how?


thanks

 update  : the wireless seems to activate once I use

[COLOR="Blue"]sudo modprobe ndiswrapper[/COLOR]

any idea how to set it to do it automatically?

---

### Post by avik on 2007-12-16
> **waspbr said:**
> ```
sudo echo ndiswrapper >> /etc/modules
```

Try doing a

```
gksudo gedit /etc/modules
```

and add in the line "ndiswrapper" (no quotes) at the end of the file.

---

### Post by david412 on 2007-12-16
The sound can be fixed by following the instructions in this link: [http://ubuntuforums.org/showpost.php?p=3475485&postcount=235](http://ubuntuforums.org/showpost.php?p=3475485&postcount=235) This also fixes the two front headphone jacks. BUT they are muted my default so be careful. 

Does anyone know how I can get the microphones to work? I would really like to use Skype with video (the webcam works out of box) AND audio

thanks,

-david

---

### Post by ovalenzu on 2007-12-16
> **dmarinescu said:**
> hi everyone!

got great news, not only for ubuntu users but actually for everyone using hp tx 1000 (tx 1xxx) series!

i'll get right to the point:

1. there is NO need to disable apic and / or lapic! the bios  asks the kernel for os name. if not windows, then apic is disabled by the bios (and of course, you have to also disable it from kernel params, using nolapic. again, this is not the way to use this machine!
2. there is a problem with IRQ7! fixirq or irqpool will not really work, unless you enable acpi_irq_balance and, most important you make pci relate to bios irq! specially the last kernel param is crucial in avoiding the 100% second core cpu usage comming from irqpool!

so, to make the whole story short, the following combination of kernel params fixes the irq#7 issues, without disabling lapic! 

noapic acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi="!Linux" acpi_os_name="Windows 2006"

you get the irq fixed and both cores are at almost 0%!

enjoy,
   daniel

and the best conbination it's 
noapic acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi="!Linux" acpi_os_name="Windows 2006"
or
acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi="!Linux" acpi_os_name="Windows 2006"

I don't understand becouse you said  there is NO need to disable apic.

---

### Post by waspbr on 2007-12-17
thanks for the reply on the wireless,now with that out of the way, has any one been ablle to set up the touchscreen  on gutsy 64? I tried to follow the egalax manufacturer' s guide and use the drivers from the website, and now I have the " cursor won' t leave the botton left side of the screen but it senses the stylus" bug.

If anyone has made the touchscreen work on gutsy 64 pls don't hesitate to post it

l8er

---

### Post by mcsimon on 2007-12-18
> **waspbr said:**
> thanks for the reply on the wireless,now with that out of the way, has any one been ablle to set up the touchscreen  on gutsy 64? I tried to follow the egalax manufacturer' s guide and use the drivers from the website, and now I have the " cursor won' t leave the botton left side of the screen but it senses the stylus" bug.

If anyone has made the touchscreen work on gutsy 64 pls don't hesitate to post it

l8er


have it working great on  64-bit gutsy with egalax touchkit.

use /dev/usb/hiddev0 for your device and then calibrate with touchkit. should work sweet.

---

### Post by avik on 2007-12-18
> **mcsimon said:**
> use /dev/usb/hiddev0 for your device and then calibrate with touchkit. should work sweet.

EDIT: Forget what I said earlier.  This works great!  Thank you *so* much!  Now I can finally show off to my friends.

---

### Post by waspbr on 2007-12-18
I tried the touchscreen solution  and at first it didn't work, so I tried to use the " dev/input/event#" again, just to realise that it wouldn't work and that the events would change after every reboot. 

so i tried the "/dev/usb/hiddev0" and for my surprise the bugger worked,  and I gotta say i was pretty happy about it so like the guy in the previuos post i could gloat about having fully installed ubuntu in my new notebook with full features.

but of course my happiness was short lived , cos apparently my /dev/usb seems to disappear on restart and only pops up whenever it feels like it. I've rebooted countless times to check this and yes, it keeps on disappearing. 

Does anyone know why? or better, does anyone have a fix for this?

thanks  in advance
[COLOR="Red"]Problem solved

Apparently the reason why my USB folder was disappearing was these two buggers

usbtouchscreen
 tkusb


the problem was finally solved by  blacklisting them at /etc/modprobe.d/blacklist:

[/COLOR]

---

### Post by v.cecchetto on 2007-12-19
Again about kernel parameter.

Have you solved all your kernel parameter problem?

..............................................................................
1) PCI: BIOS BUG #81[49435000] found
..............................................................................
Test your system:

dmesg | grep BIOS | grep BUG

(Is it a kernel parameter problem? I red somewhere it should be that bios found 32bit operating system running on a 64bit system, someone could clarify?)

..............................................................................
2) irq 7: nobody cared (try booting with the "irqpoll" option)
..............................................................................
Test your system:

dmesg | nobody
 
..............................................................................
3) USB not workin
..............................................................................
Test your system:

Are your usb devices, like pen drives, working on Ubuntu?

(it should be correlated to irq 7 problem)

..............................................................................
4) 100% CPU issue
..............................................................................
Test your system:

Install htop

apt-get install htop

run it

htop

see if one of your two cpus is overused (constantly close 100% usage), you find CPU % in the upper part, on the left, cpu are numbered 1 and 2 

..............................................................................
5) SUSPEND AND HIBERNATE
..............................................................................
Test:

try suspend and hibernate mode

(Which program are you using? 
- SWSUSP (default)
- USWSUSP
- TUXONICE (ex SUSPEND 2))

Bad part, it should be in part correlated to nvidia closed driver problem... 

..............................................................................
6) TTY CONSOLE
..............................................................................
Test:

go in console mode, press
CTRL+ALT+F1

Can you see the correct console mode or you see garbage, strange color and so on?  

Another nvidia closed driver problem...

..............................................................................
PARTIAL SOLUTION
..............................................................................

Install the latest nvidia driver 100.14.19 (with the new beta driver i have problem)

After this:

        sudo -i

	gedit /etc/modprobe.d/blacklist-framebuffer

..........................................................
# blacklist vesafb
..........................................................

	gedit /etc/initramfs-tools/modules

add at the end

..........................................................
fbcon
vesafb
..........................................................

	update-initramfs -u -k all

        gksudo gedit /boot/grub/menu.lst

use for kernel parameters
..........................................................
... ro quiet splash noapic acpi_irq_balance vga=0x0318
..........................................................

I solved problem 2) 3) 4) 6)
I don't care about 1) but i would like to solve 5)
During boot, the splash screen is oversized, part go out of the screen, but it's not a real problem
I have a partial success in hibernating, using 

     sudo s2disk

but during hibernation process the screen is filled in a rainbow of beautiful color (is it not the screen saver ;) )... I think is it another nvidia closed driver problem. 

A lot of question, sorry, but most of them are correlated and when i solve one problem i broke something else, im going crazy! :)

Have a nice day
:popcorn:

---

### Post by stealthc on 2007-12-19
I'm pretty new but I can tell you from my own issues with it that it has nothing to do with the cpu.  The very fact that it says PCI should be the first hint....lol...cpu isn't a pci device,  U know it could be a bios setting....lol

---

### Post by miknix on 2007-12-20
> **jcase008 said:**
> The driver successfully complies and can be loaded at boot time.  New devices show up in /sys/devices/acpi_system:00/device:00, but no button presses are reported in dmesg or /var/log/messages.  Also, the file power/state never seems to change when a button is pressed.  I have enable_runtime_btns=1 as one of my kernel parameters.

I haven't looked for ACPI subsystem programming docs.  How did you create this module?  What documentation did you read (i.e. how do I get started to help?)  I've created other drivers before for work and play, but haven't played with the ACPI subsystem yet.

[http://quickstart.sourceforge.net/](http://quickstart.sourceforge.net/)
See /sys/devices/platform/quickstart/buttons for a list of supported buttons.
If you turn on your laptop with one of your hotkeys, the hotkey name should appear
on /sys/devices/platform/quickstart/pressed_button

With enable_runtime_btns=1 runtime keys (if your acpi code implements it) are reported
as kernel messages (for testing).
Do dmesg to see latest kernel messages.

Then you can make a simple script to check if some key was pressed and launch applications at boot time.

* *
I really appreciate any comments about this driver on the project forum (Don't forget to mention your laptop brand/model). This way we could get it stabilized and maybe move it into the kernel tree.
* *

You can get latest ACPI specs from here:
[http://www.acpi.info/](http://www.acpi.info/)

Also, acpi4linux has a lot of resources:
[http://www.lesswatts.org/projects/acpi/](http://www.lesswatts.org/projects/acpi/)

And of course.. You can always look at acpi drivers located on latest kernels.. (toshiba-acpi is a good one).

---

### Post by TheMarshall on 2007-12-21
Thanks to this thread my tx1000z is up and running wonderfully on a brand new 7.10 install.

I had to use "noapic" to get the livecd to boot, but other than that I havent needed it.

Once it was initially running, I installed the nvida drivers via the restricted driver dialog. I rebooted and suddenly my windows were all wobbly.

After the reboot, wireless was my top priority. I used sauronsmatrix's instructions [post=3491929]here[/post] and it worked without a hitch. Then I got my audio working using, again, sauronsmatrix's instructions [post=3475485]here[/post], and again, it worked immediately on reboot.

After that, I decided to get my touchscreen working. There are a couple different methods for this in the thread. I tried the evtouch drivers, but i was having issues with extra clicks and a lack of right click. I read up some more, and found a link to [here](http://210.64.17.162), the touchscreen manufacturers website. I found the drivers [here](http://210.64.17.162/web20/TouckDriver/linuxDriver.htm). I downloaded, extracted, and followed the instructions. After rebooting the touchscreen was working, but the y-axis was inverted. I calibrated using the TouchKit app in the archive, and now it works perfectly.

Now that I'm all setup, I don't know what to do with it.

Again, thanks to everyone in this thread for the excellent research and help.

---

### Post by NOVATO1029384756 on 2007-12-21
[COLOR="DarkOrange"][B]I have a HP Pavilion tx1320us with vista 32 and ubuntu 7.10 (64)  
The problem is, the wireless doesn't work (broadcom 4321AG 802.11 a/b/g draft-n Wi-Fi Adapter)
and many things but the most important is the internet
Some one can help me out whit this???
I can see me router and the neigbordhood wireless :lolflag:  but I can't conect  
I can't  conect to my own router :( 
I tried many tutorials but nothing works 
[/B][/COLOR]

[IMG]http://news.zdnet.co.uk/i/z5/illo/nw/story_graphics/january07/HP_tx1000.jpg[/IMG]

---

### Post by waspbr on 2007-12-21
okay, I know exactly how you feel, I am also on gutsy 64 and everything works. okay there's a very good tutorial on how to get the wireless working at the botton of page 31 of this thread, by sauronsmatrix and it should work well, the only thing that didn't work so well was that the setting were disappearing after reboot, which was always solved by quick edit, look back a few pages (its in the 40s bit). 

anyway the wireless works

the only thing i am having trouble with is making the screen rotate with one of the scripts posted here(the most recent), i will post my xorg so some can tell me what I am missing, and sorry my xorg looks messy i was trying to make the screen rotate and i got the good "new" start up X (which was a first for me ) so any suggestions are more then welcome.


thanks 

This is what i managed to savage from my xorg.conf (i know i should have backed it up)

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
      	Identifier 	"EETI"
      	Driver 		"egalax"
      	Option 		"Device"    		"/dev/usb/hiddev0"
      	Option 		"Parameters" 		"/etc/egalax.cal"
      	Option 		"ScreenNo"   		"0"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"NVIDIA GeForce 6 Series"
	Busid		"PCI:0:5:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	800
		Modes		"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
	InputDevice    "EETI"      "SendCoreEvents"
EndSection
Section "device" #    
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 6 Series"
	Busid		"PCI:0:5:0"
	Driver		"nvidia"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" #    
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x800@60"
	EndSubSection
EndSection
Section "monitor" #    
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  		modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
 		modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync

	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

#cheers

---

### Post by VincenzoAMD64 on 2007-12-22
Hello,
I am again in troubles with my sound card...
after the last kernel update:
2.6.22-14 (2.6.22-14.46) to 2.6.22-14.47

in the previous kernel update, it was necessary to recreate a link as suggested by the post of SauronMatrix:
[http://ubuntuforums.org/showpost.php...&postcount=235](http://ubuntuforums.org/showpost.php...&postcount=235)

This time the solution seems to be not effective.
Help help!

---

### Post by waspbr on 2007-12-22
weird, haven't received that update yet

---

### Post by dehuszar on 2007-12-22
Just recompile the latest Alsa to the new kernel again.  Worked for me.

---

### Post by mcsimon on 2007-12-23
[quote]) PCI: BIOS BUG #81[49435000] found[quote]

i recieved this error as well until i updated my bios to the newest version and it fixed it :)

---

### Post by qhimq on 2007-12-24
mine heats up to 90C and then I'm worried. (shows this from nvidia-settings)...

i think the computer has two fans.  One the heatseak (cpu fan) and another for the graphics.  I feel the air movement much more in vista.

PLEASE someone work on a solution.  I can't leave my computer running something hardcore without it going over 90C.

Thanks.

---

### Post by sauronsmatrix on 2007-12-26
do you have compiz-fusion on?

---

### Post by sauronsmatrix on 2007-12-26
An update for tx1000 series users, if you are still having difficulties, use the Ubuntu 8.04 Alpha 2 Desktop Edition, available for direct download [here]("http://cdimage.ubuntu.com/releases/hardy/alpha-2/hardy-desktop-i386.iso").

So far, these have worked, OUT OF THE BOX:
BIOS bug (This is actually not due to Ubuntu. As pointed out by mcsimon, a simple BIOS update [here]("http://ftp.hp.com/pub/softpaq/sp38001-38500/sp38013.exe") clears up the problem.)
Booting (No "noapic" or "irqpoll" options necessary)
Sound (Quite a nice thing, as sound used to be a pain in the *** to solve)
Graphics (Nvidia 6150 Go Drivers Installed Properly)

What still does not work:
Wireless (Although [my solution]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257") still works.)
Touchscreen ([This solution]("http://ubuntuforums.org/showpost.php?p=2792971&postcount=16") still works.)

Conclusion: If you're still having problems, or even if you got everything working, I'd recommend 8.04 Alpha 2. A lot of stuff works out of the box now.

EDIT: Also, the CPU temp is noticably cooler. It is running at 20 Celsius Lower than average when I have 7.10. Definitely recommend upgrading now.

---

### Post by Cuppa-Chino on 2007-12-26
> **sauronsmatrix said:**
> An update for tx1000 series users, if you are still having difficulties, use the Ubuntu 8.04 Alpha 2 Desktop Edition, available for direct download [here]("http://cdimage.ubuntu.com/releases/hardy/alpha-2/hardy-desktop-i386.iso").

So far, these have worked, OUT OF THE BOX:
BIOS bug (This is actually not due to Ubuntu. As pointed out by mcsimon, a simple BIOS update [here]("http://ftp.hp.com/pub/softpaq/sp38001-38500/sp38013.exe") clears up the problem.)
Booting (No "noapic" or "irqpoll" options necessary)
Sound (Quite a nice thing, as sound used to be a pain in the *** to solve)
Graphics (Nvidia 6150 Go Drivers Installed Properly)

What still does not work:
Wireless (Although [my solution]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257") still works.)
Touchscreen ([This solution]("http://ubuntuforums.org/showpost.php?p=2792971&postcount=16") still works.)

Conclusion: If you're still having problems, or even if you got everything working, I'd recommend 8.04 Alpha 2. A lot of stuff works out of the box now.

EDIT: Also, the CPU temp is noticably cooler. It is running at 20 Celsius Lower than average when I have 7.10. Definitely recommend upgrading now.

fyi bios update is heaven sent, just managed my first suspend &return on this laptop ever!

**[COLOR="Red"]IT WORKED ONLY ONCE, NOW CRASHING AGAIN WHEN I TRY AND SUSPEND; GO FIGURE.[/COLOR]**

---

### Post by Cuppa-Chino on 2007-12-26
> **qhimq said:**
> mine heats up to 90C and then I'm worried. (shows this from nvidia-settings)...

i think the computer has two fans.  One the heatseak (cpu fan) and another for the graphics.  I feel the air movement much more in vista.

PLEASE someone work on a solution.  I can't leave my computer running something hardcore without it going over 90C.

Thanks.

have you checked temperature in vista, I have upto 90°C intermittently but same in vista, what is your desktop running temp -- ie no COMPIZ / Desktop effects on, mine is high 50s°C sometimes 60°C, NB the choke temperature that nvidia puts on is 115°C (in both linux and vista)

---

### Post by bradleyb01 on 2007-12-26
Thank you to everyone in this thread, by using it, I have my tx1220us running beautifully on gutsy (it even boots to vista or xp when work requires it). My last issue was setting the touchscreen to /dev/usb/hiddev0 NOT /dev/input/event2.

I love this forum!:)

---

### Post by qhimq on 2007-12-26
> **Cuppa-Chino said:**
> the choke temperature that nvidia puts on is 115°C (in both linux and vista)

mine is set to 130C for the slowdown threshold and it won't let me change it. :(
Furthermore, if I run glxgears, i see the temp go over 95C and I quit because I'm scared.

these are the outputs I'm getting.
```

7056 frames in 5.0 seconds = 1407.170 FPS
7206 frames in 5.0 seconds = 1440.941 FPS
7192 frames in 5.0 seconds = 1438.293 FPS
7346 frames in 5.0 seconds = 1469.083 FPS
7255 frames in 5.0 seconds = 1450.900 FPS
7409 frames in 5.0 seconds = 1481.746 FPS
7386 frames in 5.0 seconds = 1477.080 FPS

```


<<<<<<<<<<<<<>>>>>>>>>>>>>>>>>>

I have also been researching on the random freeze i get once in awhile.  I think all dual-core with 6150go has this problem.

it seems like the freeze comes from the xorg process.  also in the system log, Xorg.0.log it posts WAIT NVIDIA messages.

[http://www.nvnews.net/vbulletin/showthread.php?t=95804&page=1](http://www.nvnews.net/vbulletin/showthread.php?t=95804&page=1)
^this is where I heard a lot of people complaining.

seems like no one has found a solution to it.

---

### Post by Francis Pereira on 2007-12-27
> **sauronsmatrix said:**
> 
EDIT: Also, the CPU temp is noticably cooler. It is running at 20 Celsius Lower than average when I have 7.10. Definitely recommend upgrading now.

At what temperature does the CPU ideal ? My processor is running at 47 Celsius :popcorn:

---

### Post by sauronsmatrix on 2007-12-27
Sexy Perfect: 30 C 
Very Nice: 40-50 C
Warm, But okay... 60 C
Reaching the Edge, and VERY hot 70 C
Turn off your computer danger zone 70 C +

---

### Post by phenolholic on 2007-12-27
my setup is working good except mouse support. i have touchscreen via evtouch, but whether i use a bluetooth mouse (following other tutorials) or a usb mouse, it just won't operate. i know its an xorg issue. anyone have evtouch & a usb/bluetooth mouse, and can point (no pun) to the right direction?

---

### Post by qhimq on 2007-12-28
In vista I can't get the graphics card over 80C however in ubuntu i continually can have it climb up over 95C.  I don't think the graphics fan is going.  :confused:

---

### Post by waspbr on 2007-12-29
has anyone tried to create a virtual machine in this computer yet? well i normally use virtualbox and I am confused about the graphics card settings, does anyone have any suggestions?

---

### Post by waspbr on 2007-12-30
sauron, what drivers did you use to install the graphics card in hardy, I tried the one for the 6 series since i can't find geforce go 6 in the nvidia site, but now my X is broken...

[COLOR="Red"]problem solved, sometimes I am  in complete awe at my noobiness, installed the drivers by  installing the restricted drivers manager in synaptic[/COLOR]

---

### Post by King_Louie on 2007-12-31
> **sauronsmatrix said:**
> do you have compiz-fusion on?
I took sauronsmatrix advice and isntalled the Ubuntu 8.04 Alpha 2 Desktop Edition on my HP Pavilion tx1205us. Mostly fantastic, however, there are still issues with the Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02) wireless.

I managed to load a working bcmwl5 driver via ndiswrapper.

"ndiswrapper -l" output is:
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

But the only way the wireless actually fires up (light on) is if I do the following:
rmmod ohci_hcd
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper

then all is go.

"ssb" and "ohci_hcd", whatever they are, are causing problems. Blacklisting them (and bcm43xx) in /etc/modprobe.d/blacklist has no effect.

Any clues as to where I should look next to resolve this? thanks.

---

### Post by paddlaren on 2008-01-01
Hi!

My tx1345oe are equiped with a different webcam from Ricoh and requires a different driver.

My lsusb reports:
```
Bus 001 Device 007: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 006: ID 08ff:1600 AuthenTec, Inc.
Bus 001 Device 005: ID 05ca:1810 Ricoh Co., Ltd
Bus 001 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 003: ID 03f0:171d Hewlett-Packard
Bus 002 Device 002: ID 046d:c044 Logitech, Inc.
Bus 002 Device 001: ID 0000:0000

```

The solution for this seems to be to download another driver, r5u870-0.10.0.tgz, as described in [http://www.linuxdriverproject.org/twiki/bin/view/Main/OutOfTreeDrivers#Web_Cams]("http://www.linuxdriverproject.org/twiki/bin/view/Main/OutOfTreeDrivers#Web_Cams")

As I for the moment does not run kubuntu on the machine I will not make the kubuntu-style installing instruction right now but I'd like to hint others where the webcam does not work to try it out. 
There is lot of links to follow up in this if you try searching. 

Regards,
Erik

---

### Post by waspbr on 2008-01-01
King_Louie, i think you forgot to blacklist bcm43xx, this is in sauron's method.

All in all , I am glad I have installed hardy, it does seem more robust with some minor forgiveable quirks, I still have gutsy on a separate partition just in case. Ubuntu certainly seems to be the right linux distro for this lappy, i tried fiddling with pclinuxos, and the wireless is just a nightmare...

---

### Post by netvampire on 2008-01-02
i followed the guide here 

[http://ubuntuforums.org/showpost.php?p=3491929&postcount=257]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257")

to get sound working. It works great, and I have sound, and the headphones sensing works fine.

My problem though is the volume up and volume down buttons on the notebook are used to control the "headphones" tab (as outlined by kmix) ...so because it only controls the headphones tab, if no headphones are plugged in then the volume up and down buttons do nothing. 

Does anyone know of a solution?

---

### Post by manu456 on 2008-01-03
netvampire try this

go to system -> preferences -> sound

make sure HDA NVidia(Alsa Mixer) is selected in default mixer tracks

select "front" from the list under it

now your volume buttons should control the audio of the speakers

the trade off is that when you plug in headphones then your volume buttons wont work...

---

### Post by manu456 on 2008-01-03
oh i just realised that you are using KDE... my previous steps were for gnome... but you should have a similar preference in KDE... I will try and check this on a kubuntu installation a little later in the day.

---

### Post by waspbr on 2008-01-03
Sauronsmatrix

 did your hardy's xorg already have a "ServerLayout" Section or did you add it yourself?

I added 
```
Section "ServerLayout"
        InputDevice    "EETI"      "SendCoreEvents"
EndSection
```


I used the eeti's solution (the vendor)to install the touchscreen, which seems to work fine in my gutsy partition but seems to crash my xorg... I am asking cos in the solution you used you had to add a "ServerLayout" Section,

thanks for the help

---

### Post by oar on 2008-01-03
(I'm brand new to linux/Ubuntu, so bare with me.. :))

I have a problem installin Ubuntu on my tx1128ea. I've downloaded Ubuntu 7.10 Desktop Edition, and burnt it to a CD. I insert the CD in my laptop, and boot. The menu appears where you can select "Start or install Ubuntu" (and I press enter), and the install appears to start. It's loading the Linux Kernel, the Ubunto logo appears with the horizontal bar graph thing moving, then it starts listing various actions with a followin "[ OK ]" at the end. After a while, the screen goes black (It's still backlit, not turned off...),I can hear  the CD stops turning, and nothing happens.

I've also tried choosing "Start Ubuntu in safe graphics mode" with the same results. Both "Check CD for defects" and "Memory test" give OK results.

The PC has a preinstalled Windows Vista, and it's own recovery part of the disk. The disk is not formatted as I assume Ubuntu will do this.

Anyone got a clue as to why I can't get into the Ubuntu CD Desktop thingy..?

---

### Post by manu456 on 2008-01-03
> **oar said:**
> 
Anyone got a clue as to why I can't get into the Ubuntu CD Desktop thingy..?

Oar you need to follow the following steps

After inserting the cd and restarting your computer when you get the menu press F6 for “other options”. 

Now a line of text would be visible at the bottom of the screen. Type “noapic irqpoll” at the end of the line(before the –) and press enter. 

You should be able to boot into and install ubuntu.

Good luck!

---

### Post by King_Louie on 2008-01-03
> **waspbr said:**
> King_Louie, i think you forgot to blacklist bcm43xx, this is in sauron's method.


waspbr- thanks for the response. I did blacklist bcm43xx and verified that it does not get loaded at boot. I tried again, reinstalling Hardy from scratch and following sauronsmatrix suggestions for wireless ([http://ubuntuforums.org/showpost.php?p=3491929&postcount=257](http://ubuntuforums.org/showpost.php?p=3491929&postcount=257)). Same result. Wireless only jumps up if I rmmod ohci_hcd, ssb, and ndiswrapper and then modprobe ndiswrapper. Then everything is groovy. So, again "ohci_hcd" and "ssb" are interfering with ndiswrapper, but I don't know what that means.

---

### Post by oar on 2008-01-03
> **manu456 said:**
> Oar you need to follow the following steps

After inserting the cd and restarting your computer when you get the menu press F6 for &#8220;other options&#8221;. 

Now a line of text would be visible at the bottom of the screen. Type &#8220;noapic irqpoll&#8221; at the end of the line(before the &#8211;) and press enter. 

You should be able to boot into and install ubuntu.

Good luck!

Thanks alot sir! :) That worked like a charm! And I even investigated what [_APIC means_]("http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller"). And a bit of googling led me to [_this guide_]("http://linux1.no/node/2952") (norwegian) which tells me to press [e] in the "grub menu" after restart, and [e] on the line "*kernel /boot/vmlinuz-2.6...*" and add "noapic irqpoll" at the end of that line too. Can't wait to test it out. The install is transfering files as we speak! :)

Thanks again, have a nice day!

---

### Post by waspbr on 2008-01-03
King_Louie, I think I had a similar problem, the following code just would not work with me... ```
sudo echo ndiswrapper >> /etc/modules/
```

since you have already installed the driver with ndiswrapper, which should show with ndiswrapper -l
 and then u did ndiswrapper -m, the the module is already created you just need to load it up.

you can manually load the module by using

```
sudo modprobe ndiswrapper
```

in order to have the module do that automatically just do 

```
sudo gedit /etc/modules
```

and add the line [COLOR="Blue"]ndiswrapper[/COLOR] to it 


let me know how that works out

---

### Post by King_Louie on 2008-01-03
waspbr- right. all that has been done. the ndiswrapper module actually does load with the correct driver at boot. It's just that the "ohci_hcd" and "ssb" modules seem to be interfering. If I kill them all and modprobe ndiswrapper, the wireless works. But blacklisting "ohci_hcd" and "ssb" in /etc/modprobe.d/blacklist seems to make no difference. They still load at boot. I wonder if this in an irq conflict of some sort. 

What model tx1000 and wireless card are you using? You have Hardy installed and wireless is working at boot?

---

### Post by waspbr on 2008-01-03
this is weird...
Yep, I have installed hardy, and its wireless is working at boot, I have used these drivers [http://rapidshare.com/files/79251578/driver.zip]("http://rapidshare.com/files/79251578/driver.zip") 

from sauron's howto and they seem to work fine, I have the tx1320us, and I can't really imagine the your broadcoam would be any different then mine. from sauron's file everything, with the exception of the echo command should work.

does your [COLOR="Red"]sudo modprobe ndisrapper [/COLOR] work without killing those files that you mentioned,? try doing the [COLOR="Blue"]sudo modprobe ndiswrapper[/COLOR] without killing anything? does it activate the wireless? In a worse case scenario you may have more then one ndiswrappers installed, in the worst case scenario I am completely clueless and u should wait for the next hardy update in a week or so. I would tho recomment to keep a gusty partition just in case, cos, all in all, gusty is the stable version truth be told. 

otherwise i might suggest using different driver, more compatible to your build... 

in any case this is still weird

lemme know how it works out

---

### Post by gabesword on 2008-01-04
> **v.cecchetto said:**
> A new version of the script to rotate the screen. For the new xrandr version.

rotate.sh
..........................................................
#!/bin/bash          

STR=`xrandr --verbose | awk '/default/{print $5}'`

case "$STR" in
     'normal')
	 xrandr -o left
         ;;
     'left')
         xrandr -o inverted
         ;;
     'inverted')
         xrandr -o right
         ;;
     'right')
         xrandr -o normal
         ;;
esac
..........................................................

:KS

I have tried using this script for screen rotation and I'm having some trouble.  The screen does rotate, but part of the screen is black and not used and part of the desktop is not being displayed.  Also, the touchpad doesn't behave as expected, when I slide my finger up on the pad the pointer moves up (which is now left).

I am using gutsy Kubuntu, if it makes any difference.

Does anyone have some advice?

---

### Post by netvampire on 2008-01-04
> **manu456 said:**
> oh i just realised that you are using KDE... my previous steps were for gnome... but you should have a similar preference in KDE... I will try and check this on a kubuntu installation a little later in the day.

thanks for the response. can u please tell me how to do it on kde (kubuntu). I am unable to find any options similar to that of which you described for gnome. I appreciate you responding and your guidance. thanks/

---

### Post by Cuppa-Chino on 2008-01-04
odd I am having NO joy what so ever with hardy, for me its hardly works at all 

a) kubuntu would boot every time but could do nothing with networking

b) ubuntu hardly boots sometimes, crashes sometimes on avahi demon, networking with static address does not work, wpa key is not possible when manually configured, all manual configurations are not saved properly

so no joy there what so ever

---

### Post by waspbr on 2008-01-05
weird, on my first hardy install, everything worked beautifully, now on my second install, sometimes I may get a freeze, ie, mouse works but  can't click, but that is forgivable considering that it is still alpha2. Couldn't get the touchscreen to work on hardy using eeti's method. but everything works well (except for the webcam and fingerprint reader that i really haven't bothered with yet)


so my advise is don't commit 100% to hardy, keep another partition with a stable version.

for gutsy

Other than that I am having a small problem with the screen rotation, while I do get it to rotate using the script posted above, in the 800x1280 resolution  the lower half of the screen is not being used, that is I have my awn dock bar lying somewhere in the middle of the screen... anyone got a solution for that?

also, the touch screen does not see the rotation, so it acts as if the screen is still in its default position. any fixes for that.

thanks for the help

gabesword - i have the same issue in (gnome) ubuntu gutsy

ciao

---

### Post by waspbr on 2008-01-06
cuppa chino, this is very weird since the new xorg updates hardy doesn't even freeze any more, it is working extremely well with me  except for the touch-screen that I haven't sorted out yet.

I have to connect to a wpa protected network in my university and network manager seems to handle it, after doing sauron's method and nm searches for the connection I just left clicked in the nm applet and selected the option connect to other wireless networks.

that gives you a whole set of options to choose from,  in my case the wpa2 enterprise was exactly what i needed.

hope that helps

---

### Post by Cuppa-Chino on 2008-01-06
> **waspbr said:**
> cuppa chino, this is very weird since the new xorg updates hardy doesn't even freeze any more, it is working extremely well with me  except for the touch-screen that I haven't sorted out yet.

I have to connect to a wpa protected network in my university and network manager seems to handle it, after doing sauron's method and nm searches for the connection I just left clicked in the nm applet and selected the option connect to other wireless networks.

that gives you a whole set of options to choose from,  in my case the wpa2 enterprise was exactly what i needed.

hope that helps


totally with hardy alpha 2 I cannot do any network installations at all, I need static IP and everytime I try and change something these things happen

a) I try to start sudo network-admin --> basically a crash 
b) I start network-admin as me --> can manipulate all the items, but then loops eternally through "configuring network" if I force quit nothing saved
c) if I manually write into /etc/network/interfaces it is shown in network-admin but does not get used

any ideas? (I am meanwhile have downloaded hardy a2 again am trying a different cd)

--------------------------------------------------------

one of the problems appears to be that the avahi daemon fails, so I cannot get any ip4 ip addresses, does anyone have any ideas?

---

### Post by RaZoR1394 on 2008-01-06
The wireless b43 driver in Hardy is great. It's much better than the old bcm43xx. Sound also works great now. I'm only having three problems:

1. I get black filled window on certain apps like the Synaptics. I guess this is because compiz-fusion.
2. Egalax driver doesn't work anymore. This worked great on Gutsy. On Hardy I get:

```

(II) LoadModule: "egalax"
(II) Loading /usr/lib/xorg/modules/input//egalax_drv.so
(II) Module egalax: vendor="X.Org Foundation"
(II) UnloadModule: "egalax"
(II) Unloading /usr/lib/xorg/modules/input//egalax_drv.so
(EE) Failed to load module "egalax" (module requirement mismatch, 0)
(EE) No Input driver matching `egalax'

```

3. I can't install flashplugin-nonfree due to some error with ndiswrapper.

> 
Download done.
Flash Plugin installed.
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libselinux.so.1: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: fel vid hantering av flashplugin-nonfree (--configure):
 underprocess post-installation script gav felkod 1
Fel uppstod vid hantering:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)


I hope someone can help.

---

### Post by Cuppa-Chino on 2008-01-06
razor to help me, sorry egoistic,

a) what hardy alpha are you running? 1 or 2? i386 or amd64?

b) what network do you run, wpa or wep, static or dhcp?

---

### Post by phenolholic on 2008-01-06
any success with a bluetooth mouse? i cant get mine to work (or any usb for that matter). have touchscreen working, maybe thats the conflict?

---

### Post by RaZoR1394 on 2008-01-07
> **Cuppa-Chino said:**
> razor to help me, sorry egoistic,

a) what hardy alpha are you running? 1 or 2? i386 or amd64?

b) what network do you run, wpa or wep, static or dhcp?

alpha 2 amd64. I upgraded from Gutsy amd64

wpa2 personal mixed TKIP + AES

edit:

Wireless was however not working from the start. As usual you have to install the firmware but that didn't work with the GUI tools. I noticed that I needed b43-fwcutter and not bcm43xx-fwcutter. After that it worked fine.

---

### Post by simplyw00x on 2008-01-07
Not sure why people are still using ndiswrapper, hardy's b43 driver works at full-speed with no problems. Some black windows for me but only on, e.g. new open epiphany windows. possibly a bug in epiphany...

Error on ABI mismatch for egalax is really annoying as the egalax driver works much better than the evtouch, and doesn't need "dummy" input devices. If only they would open-source it, and maybe and xrandr support...

Speaking of xrandr support, nvidia-glx *still* doesn't support xrandr 1.2, so dispalyconfig-gtk is basically worthless. 

Sound worked completely out-of-box on hardy. Definitely a plus.

---

### Post by Pechorin on 2008-01-08
nm

---

### Post by waspbr on 2008-01-08
has anyone noticed that hardy has been running a little hot lately, since the last few updates, just internet browsing is making both my cpus near 100%...

I am a little worried, hardy used to be a lot more temp friendly, before it usually stayed in the 40s, now its gone to 50s and when ac power is on, it's not really uncommon to see it in the 70s...

actually i am very worried...

---

### Post by Cuppa-Chino on 2008-01-08
> **RaZoR1394 said:**
> The wireless b43 driver in Hardy is great. It's much better than the old bcm43xx. Sound also works great now. I'm only having three problems:

1. I get black filled window on certain apps like the Synaptics. I guess this is because compiz-fusion.
2. Egalax driver doesn't work anymore. This worked great on Gutsy. On Hardy I get:


how did you get the wireless to install, no matter what I do I cannot get the device to turn up

---

### Post by manu456 on 2008-01-09
I performed the bios update as mentioned in an earlier post a few days back. I tried suspend to ram it did not work as in my computer was suspended but it could not recover.

I had forgotten about it but today I just randomly decided to try hibernate. The moment I pressed hibernate my screen lit up with some vertical stripes of different colors and the intensity of the lines kept increasing till the point my screen was completely white and then my computer shut down.

I restarted my machine and the same pattern of lines was repeated. And eventually my computer woke up in the same state!!!!!! so Hibernate it seems is working now (YAY) but I have never seen this colored pattern before. Is that normal?

I haven't been able to hibernate any of my machines on linux ever so I don't know.....

---

### Post by simplyw00x on 2008-01-09
> I restarted my machine and the same pattern of lines was repeated. And eventually my computer woke up in the same state!!!!!! so Hibernate it seems is working now (YAY) but I have never seen this colored pattern before. Is that normal?
That pattern is an nvidia driver issue. I have managed (on feisty) to get this laptop to suspend, hibernate and resume with no graphical corruption. At all. Now it suspends and hibernates fine, but doesn't always wake up and there's graphical corruption a fair bit.

> how did you get the wireless to install, no matter what I do I cannot get the device to turn up
Look at the output of dmesg - it tells you where to get the firmware for the device. Then install (probably having downloaded on another computer) b43-fwcutter and use it on the downloaded driver. ????. Profit.

---

### Post by jalone on 2008-01-11
hi! i'm on 7.10
i've a problem!
TOUCHSCREEN
 i'm trying to set the touchscreen but after installing evtouch on event2 and i've followed all the guide, i can touch the screen but the only effect is like i click where the pointer is. for example if the mouse is over an icon and i touch the screen evrywhere i click on the icon but the pointer doesn't move!
changing the event couse only similar effects (for example the pointer move to the screen center)

OTHER minor  PROBLEM ARE:
-the system don't mount usb pen or usb mouse after i've turn on

EDIT:
i resolved the configuration fingerprint problem installing the dev packages required

ps: pardon for my bad english...i'm foreigner

---

### Post by RaZoR1394 on 2008-01-11
> **Cuppa-Chino said:**
> how did you get the wireless to install, no matter what I do I cannot get the device to turn up

1. Upgrade to Hardy.
2. Install b43-fwcutter.
3. Reboot.

That's all that should be needed. However I did:

1. Upgrade to Hardy from Gutsy.
2. Downloaded firmware cutter and firmware pack from the restricted driver manager. The manager downloaded the wrong firmware package (bcm43xx-fwcutter).
3. Downloaded b43-fwcutter which prompted me to install b43 firmware.
4. Rebooted.
5. Enter pass for wireless network.

I don't think I can help you more than that.

---

### Post by waspbr on 2008-01-12
jalone:

for the usb, what did you add to the boot up line? In my tx1320us this worked:

noapic irqfixup doscsi

some people add irqpoll, but if you look back a few post you may see some comments on this.


as for the touchscreen, I had a similar problem with the events and all, I realised I had to blacklist some things. You can find this on my post on page 47 of this thread.


hope it helps, good luck

on a different subject, does anyone have any feedback on hardy alpha 3?

---

### Post by Francis Pereira on 2008-01-13
There was talk about a fan for the graphics card that did not turn on. I came across this [http://forum.tabletpcreview.com/showthread.php?t=8875]("http://forum.tabletpcreview.com/showthread.php?t=8875")
From the pictures its clear that there is none. 
Interestingly:
francis@iBook:~$ cat /proc/acpi/processor/CPU0/info 
processor id:                    0
acpi id:                              0
bus mastering control:     yes
[B]power management:        no
throttling control:              no[/B]
limit interface:                  no

Notice power management and throttling control are no. Something with the acpi ?? 
My kernel line:
/boot/vmlinuz-2.6.22-14-generic root=UUID=c07ed3fe-f4af-4407-a12d-9e77db1c704d ro vga=0x317
for some reason I don't have to use all the extra parameters. vga=somevalidmode is a must though .

I can suspend and hibernate successfuly . All this on gusty .

---

### Post by yakobbmatrix on 2008-01-15
hello everyone, I think I need your help.
well I recently install gutsy in my HP Pavilion tx1000 PC and everything work find except my sound card. the upper right volume control show this error message when I click it.

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

so I got no sound eventhough my sound LED light had turn blue, and I think there must be something wrong with gutsy,  actually I didn't have this problem when I installed opensuse 10.3. but I don't want to switch back to opensuse untill I found out how to solve this issues.
hope you all can help me.
thanks

ps: I also had included the screenshot.

---

### Post by jalone on 2008-01-15
> **waspbr said:**
> jalone:

for the usb, what did you add to the boot up line? In my tx1320us this worked:

noapic irqfixup doscsi

some people add irqpoll, but if you look back a few post you may see some comments on this.

as for the touchscreen, I had a similar problem with the events and all, I realised I had to blacklist some things. You can find this on my post on page 47 of this thread.

hope it helps, good luck

on a different subject, does anyone have any feedback on hardy alpha 3?

thanks a lot waspbr! now i'll try to all the combination editing menu.lst...
my actual configuration is:

/boot/vmlinuz-2.6.22-14-generic root=UUID=e23724fe-003e-44fe-9ee6-848e008f6b47 ro splash noapic irqpoll locale=it_IT

if you think there's any mistake please told me!! :D
thanks a lot again

edit:
i tryied with
/boot/vmlinuz-2.6.22-14-generic root=UUID=e23724fe-003e-44fe-9ee6-848e008f6b47 ro splash noapic  irqfixup doscsi locale=it_IT
but now for each point i touch the screen the pointer evry time go to the center of the screen!!
ps i'm on gutsy

---

### Post by sauronsmatrix on 2008-01-16
sooooooo, im considering kde via kubuntu 8.04 alpha 3. 

any thoughts? better or worse than gnome?

---

### Post by sauronsmatrix on 2008-01-16
ahh kde is very pretty. it will take a bit to get used to the equivalents for the gnome commands/proggies though. :(

---

### Post by sauronsmatrix on 2008-01-16
For the people who are having trouble with wireless in Hardy Heron:
[http://ubuntuforums.org/showpost.php?p=3491929&postcount=257]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257")

For the graphics drivers, go to add/remove programs, and install the
```
NVidia binary X.Org driver
```
or run this in a terminal
```
sudo apt-get install nvidia-glx
```

When done installing that, you must run
```
sudo nvidia-glx-config enable
```

**RESTART**, and enjoy accelerated graphics, your experience should be MUCH faster! :)

---

### Post by RaZoR1394 on 2008-01-17
> **sauronsmatrix said:**
> For the people who are having trouble with wireless in Hardy Heron:
[http://ubuntuforums.org/showpost.php?p=3491929&postcount=257]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257")

For the graphics drivers, go to add/remove programs, and install the
```
NVidia binary X.Org driver
```
or run this in a terminal
```
sudo apt-get install nvidia-glx
```

When done installing that, you must run
```
sudo nvidia-glx-config enable
```

**RESTART**, and enjoy accelerated graphics, your experience should be MUCH faster! :)

Why would you use ndiswrapper on Hardy? The native b43 module works great at least on Ubuntu. KDE4 is horrible at the moment. The nvidia module is also installable just by using the restricted drivers manager.

---

### Post by sauronsmatrix on 2008-01-17
i had to use ndiswrapper because the b43 module doesn't work! and the restricted drivers manager is nonexistent ??? as of 7.10 i think.

whats bad about KDE?

---

### Post by sauronsmatrix on 2008-01-17
oh P.s. im not using KDE 3.5, I'm using KDE 4. It is quite beautiful, and much more fun than gnome, give it a try ;)

---

### Post by simplyw00x on 2008-01-18
The KDE4 packages in Ubuntu are broken at the moment, or so I hear. And b43 is working perfectly as long as you have the firmware, however the wireless status light now no longer changes colour.

---

### Post by sauronsmatrix on 2008-01-18
ahhh im so confused! kde4 is up and running perfectly fine on mine, but can someone teach me how to use the b43 modules? i would rather have those than ndiswrapper. 

thanks a bunch!

---

### Post by waspbr on 2008-01-19
same here, did you guys use b43 or b43legacy?

---

### Post by simplyw00x on 2008-01-20
b43. Install b43-fwcutter and it should automatically download and install the firmware, then modprobe b43 and rmmod ndiswrapper. if the changes work, make them permenant by modifying /etc/modules and /etc/modprobe.d/blacklist

---

### Post by ShawnG on 2008-01-20
Hi - I am a Ubuntu newbie, so please bear with me.

I installed Ubuntu desktop in my HP tx1119. I had to use noapic for the live CD, but otherwise it installed fine. Now while loading Ubuntu from my hard disk it stops at a point showing "Loading hardware drivers". It doesn't show any error ... just stops there.

Any hints will be greatly appreciated.

Thanks in advance.

Shawn

---

### Post by Cuppa-Chino on 2008-01-20
> **ShawnG said:**
> Hi - I am a Ubuntu newbie, so please bear with me.

I installed Ubuntu desktop in my HP tx1119. I had to use noapic for the live CD, but otherwise it installed fine. Now while loading Ubuntu from my hard disk it stops at a point showing "Loading hardware drivers". It doesn't show any error ... just stops there.

Any hints will be greatly appreciated.

Thanks in advance.

Shawn

no problem shawn, we all started once knowing little (or nothing like me).

ok when the boot screen comes, select the ubuntu boot line and press **e** - to edit this line - than select the line that begins with something like this */boot/vmlinuz-2.6.22-14-generic root=* and add noapic to the end of the line, once done press **b** to boot and it should get you into ubuntu

when you get into ubuntu, you might want to add this boot parameter permanently to your *grub boot files*. to do this:
go to applications--> accessories --> terminal

type in **sudo gedit /boot/grub/menu.lst**
type in you login password

find the paragraph
> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ba6ff0f-2e09-4470-be86-f843bb974519 ro **noapic** splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=7ba6ff0f-2e09-4470-be86-f843bb974519 ro **noapic **single
initrd		/boot/initrd.img-2.6.22-14-generic


and add noapic as shown, I would also delete the word *quiet* to get more feedback during the boot

lets us know if this helps

---

### Post by ShawnG on 2008-01-20
Wow, it worked like a charm.

Thanks much Cuppa-Chino.

---

### Post by nvrpunk on 2008-01-21
Noticed the the irqfix makes keys randomly repeat for no reason.  irqpoll looks like a better fix.  Thanks for all the info, new laptop got everything working just fine.

Usually run Gentoo but didn't want to bother compiling.  Pretty experienced user, nice answers and easy to follow, many thanks :)

---

### Post by creatureofthedark on 2008-01-22
Hey i have managed to get Ubuntu fully installed but i am still stuck on the touch screen working
 i followed the guide on page 3 but when i tried to calibrate i got errors and when i tried to reload GUI the x server had problems and wouldn’t like my graphics card until i put the xorg.conf file back to normal

Here is my xorg file


```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:0:5:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection


#####################################################################################
# user added ########################################################################
#####################################################################################



Section "Files"
...
  InputDevices "/dev/input/event2" 	## correspond to the touchscreen event number
...
EndSection

Section "InputDevice"   		#  neue Section anlegen
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event2"  # correspond to the touchscreen event number
    Option "DeviceName" "touchscreen"
    #########################################
    # ein guter Anfang, wird später editiert:
    #########################################
    Option        "MinX"        "0"
    Option        "MinY"        "0"
    Option        "MaxX"        "2000"
    Option        "MaxY"        "2000"
    #########################################
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents"
    Option "Calibrate"  "1"		# wird nur zur Kalibrierung gebraucht!
EndSection

Section "ServerLayout"
...
  InputDevice  "touchscreen" "CorePointer"	#Zeile hinzufügen
 ...
EndSection

```

---

### Post by creatureofthedark on 2008-01-22
Ok I have managed to run the calibration tool using  

```
sudo ./calibrate.sh /dev/input/evtouch_event
```

When the xorg.conf file is unchanged and I have not added the touch screen bit. This leads me to think that it is the xorg.conf file I have messed up some how! 


I get this error when I add the touch screen section to the xorg.conf file

```

(==) Using  config file: “/etc/X11/xorg.conf
Parse error on line 119 of section Files in file /etc/X11/xorg.conf
	“...” is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
No screens found
XI0:	 fatal IO error 104 (Connection reset by peer) on X server “:0.0”
	After 0 requests (0 known processed) with 0 events remaining

```

Hear is my xorg.conf file when I have not added the touch screen section and it runs the calibration 

```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:0:5:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

```


And hear is when I add the touch screen section and the calibration dose not work


```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:0:5:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection


#####################################################################################
# user added ########################################################################
#####################################################################################



Section "Files"
...
  InputDevices "/dev/input/event2" 	## correspond to the touchscreen event number
...
EndSection

Section "InputDevice"   		#  neue Section anlegen
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event2"  # correspond to the touchscreen event number
    Option "DeviceName" "touchscreen"
    #########################################
    # ein guter Anfang, wird später editiert:
    #########################################
    Option        "MinX"        "0"
    Option        "MinY"        "0"
    Option        "MaxX"        "2000"
    Option        "MaxY"        "2000"
    #########################################
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents"
    Option "Calibrate"  "1"		# wird nur zur Kalibrierung gebraucht!
EndSection

Section "ServerLayout"
...
  InputDevice  "touchscreen" "CorePointer"	#Zeile hinzufügen
 ...
EndSection

```


i am now 100% stumped as i can’t see anything wrong with it!! but i am a noob so i wasn’t really expecting to :P

---

### Post by isachan on 2008-01-23
Sorry, I'm still a noob for some stuff with Ubuntu.

I'm using Kubuntu 7.10, but I'd like to upgrade to 8.04 Alpha 3 for the b43-fwcutter driver. (the real reason for the upgrade)

I tried "sudo apt-get dist-upgrade", but it doesn't seem it changed much except it updated a few dozen critical system apps. My kernel is still 2.6.22-14-generic.

So how do I upgrade from 7.10 to 8.04 Alpha 3 ?

Please help me.

Isao

---

### Post by immi on 2008-01-23
Hi there
I am a total beginner to Linux
I have installed Ubuntu 7.10 and managed to install audio and wireless drivers . Video is working fine as well but
when ever i try to make changes to xorg.conf for touch screen i always used to get some sort of error like once my keyboard stopped working when i restarted the laptop and i had no way to log in to and some times the video stops working and i used to get the error message that Ubuntu is running on low graphics . anyway i did manage to restore the back up file of xorg.conf.

I need to make my touch screen working and i had no idea how to make it work
I have tried almost every thing given on the web site
I am sure i will be doing some thing wrong but if some one can please post me the instruction of a working touch screen with all the commands for terminal i would be really thankful.

i will post my xorg.conf details as well

PS i know this might look harsh but if some can please explain it to me here because i have tried almost all the threads so if some one will send me a link to web site that might not be helpful
because i tried all and i couldnt work my way out

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "nVidia Corporation C51 [Geforce 6150 Go]"
Driver "nv"
BusID "PCI:0:5:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-64
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "nVidia Corporation C51 [Geforce 6150 Go]"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Modes "1280x800"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection


Please explain me what do i have to do to have my touch screen working

---

### Post by waspbr on 2008-01-24
okay, since there have been many people asking about the touchscreen on gutsy I have decided to make a small HowTo, bear in mind that for some reason this doesn't work in hardy yet:

the first thing to do is to download the drivers

the drivers can be found here: [http://210.64.17.162/web20/TouckDriver/linuxDriver.htm]("http://210.64.17.162/web20/TouckDriver/linuxDriver.htm")

there are both the 64 and 32 bit versions available, anyway you should download the ones for the 2.6 kernel.

After that, decompress and copy the files to the appropriate folders. The extracted file is the "TouchKit" folder, I find it handy to keep it in the home folder directory.

```
tar xvfz TouchKit_1.07.0831.tar.gz
cd TouchKit
sudo cp egalax_drv.so /usr/lib/xorg/modules/input/

```

if you are using gutsy amd64 then these are the commands for u

```

tar xvfz TouchKit64_1.07.0907.tar.gz
cd TouchKit64
su
cp egalax_drv.so /usr/lib64/xorg/modules/input/
```

note that the only difference is that gutsy 64 uses /usr/lib64/ instead of /usr/lib/

if you are like I was in the beginning  and don't like to use the tar command, just double click it, extract to desktop, go to terminal type

```
sudo nautilus
```

and manually copy the file  egalax_drv.so to the  [COLOR="Red"]/usr/lib/xorg/modules/input/[/COLOR]  folder. just be careful not to change anything  else.

next edit your xorg

```
sudo gedit /etc/X11/xorg.conf
```

there add to the "ServerLayout" Section near the bottom of your xorg  the following line (without the ... )
```
...
InputDevice    "EETI"      "SendCoreEvents"
...

```

the add this somewhere else in the file, I like to keep things sorted so I put mine next to the other InputDevices near the top

```

Section "InputDevice"
      Identifier "EETI"
      Driver "egalax"
      Option "Device"    "/dev/usb/hiddev0"
      Option "Parameters" "/etc/egalax.cal"
      Option "ScreenNo"   "0"
EndSection

```

Alternatively if you experience any problems, like conflicts with other usb devices, you may wanna make a small modification in the device option above as follows

```
Option "Device" "usbauto"
```

okay then, moving on...

you are almost done,  I found out that a few modules make it hard for the pc to detect the device so what you do is to blacklist some of them

I noticed that the  /dev/usb/  folder was disappearing because of  these two buggers

usbtouchscreen
tkusb

 
this is easily solved by 

```
 sudo gedit /etc/modprobe.d/blacklist
```


add the following lines to the end of the document

```

#cause touchscreen drivers to malfunction
blacklist usbtouchscreen
blacklist tkusb  
```

reboot, then go to terminal (I assume that you have placed the TouchKit folder into your home folder if not just cd to it)

```
cd TouchKit
sudo ./TouchKit
```

this is going to open a dialog, if you see a tools tab, then it worked, if not then review what you did and post here if u get stuck.

This method worked on gutsy amd64 as well as the 32 bit version.So far it still does not work for hardy alpha 6.

good luck

---

### Post by creatureofthedark on 2008-01-24
YAAAAAAAAAAAAAAAAAAAAAAAAAAAY thankyou soooooooo much i spent ages working on this!! and thax to your post i did it in 5 mins!!

---

### Post by sauronsmatrix on 2008-01-24
woowowwo thanks for that post i've never seen a tutorial for the touchscreen so easy to use.

i will give it a try in hardy, although i will not expect much because xorg 7.3 doesnt use the xorg.conf that much I hear.

:( wish i had this tut in 7.10!

---

### Post by manu456 on 2008-01-24
This is brilliant waspbr. Thanks a lot! :-D

---

### Post by qhimq on 2008-01-24
Yeah wow, it works!  Just did the calibration, it took me awhile to figure it out for some reason...reading usually helps.  PRESS AND HOLD until beep.

Yeh this works better than on vista now.  Much lighter press to activate.

---

### Post by waspbr on 2008-01-24
I am glad I could help, and sauron I should thank you instead, I got my wireless and sound working in gutsy cos of ur Howto.

anyway when I tried to get the touchscreen working in hardyy i noticed that there was no "ServerLayout" section and any attempt of trying to modify it crashed my X. so since i have two distros running, I backed up my hardy xorg and copied the one from gutsy into it. 

I was surprised to find that it works, aside from a small change I had to make in the serverlayout, in there the word screen was written with a lower case s which caused the crash. Changing screen into Screen made a huge difference.

anyway, i think gutsy's xorg is more mature more complete plus the touchpad scroll works in it...

If anyone is interested in trying it out I am posting my xorg, with the touchscreen changes included. It should work since i am typing from my hardy... so yeah, good luck

---

### Post by qhimq on 2008-01-25
hi,

I tried to install the new graphics driver NVIDIA-Linux-x86_64-169.07-pkg2 however with failure.

I installed it had xorg.conf run 'nvidia' driver, but it refuses to run, and puts on the vesa generic driver.

now i'm running on 'nv' driver because I couldn't get the old driver working again.  I get nasty keyboard freezes, and a random new Data/Audio disc notices even though no disc has been inserted.

:lolflag:  :mad:


I also ran envy in manual installation however the product was the same as with how I installed it without envy.

Now I would even like to just have my previous driver working if at all possible.

---

### Post by waspbr on 2008-01-25
nvidia drivers are always tricky, i prefer to let synaptic handle them since my overall experience with them hasn't been great.

---

### Post by qhimq on 2008-01-26
I used envy to uninstall the nvidia driver.  Then used the package manager to install nvidia-glx.  The problem still exists where the driver is not run, but vesa is ran.

Any hints? :(

---

### Post by immi on 2008-01-26
Hey thanks alot for your help with touch screen found out i was actually downloading the incorrect Kernal version lol
anyway thanks alot 

PS i used this code for rotate screen but it is not working 
I actually added Custom Application launcher to the panel and used this code 
but it is not working 

#!/bin/sh

# Change System Input orientation for Tablet Mode
if [ -n "$(xrandr | grep 800x1280)" ]||[ -n "$(xrandr | grep 1024x2560)" ]; then
        xrandr -o normal
        #sudo /usr/bin/touchscreen_switch.sh 
else

        xrandr -o left
        #sudo /usr/bin/touchscreen_switch.sh l
fi

Any suggestions

PS i have tried this script as well 

#!/bin/bash

STR=`xrandr --verbose | awk '/default/{print $5}'`

case "$STR" in
'normal')
xrandr -o left
;;
'left')
xrandr -o inverted
;;
'inverted')
xrandr -o right
;;
'right')
xrandr -o normal
;;
esac

---

### Post by lut4rp on 2008-01-27
I have a HP Pavilion tx1000 (tx1016AU). Audio is by Realtek ALC861-VD.
I was having problem with sound outputs from speakers and headphones, both. I tried a lot of things, and I have found a bug report on the ALSA bug tracker. The url is [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3161](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3161)

It shows the problem was resolved for the reporter. The solver has added a note saying "The patch to support this hardware is now applied to HG tree.". Scroll down on the page and you see it. 

Can anybody tell me what this means? Patch applied to HG tree?

---

### Post by simplyw00x on 2008-01-27
> Can anybody tell me what this means? Patch applied to HG tree?
Hg (mercurial) is the version control system they use --- it means that the problem is fixed in a yet-to-be-released version of ALSA. This version is in fact in the next release of Ubuntu, "Hardy" but there is a guide further up the thread to get the latest ALSA for Gutsy.

---

### Post by waspbr on 2008-01-27
yep, the sound solution for gutsy is posted here:
[http://ubuntuforums.org/showpost.php?p=3475485&postcount=235]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235")

---

### Post by sauronsmatrix on 2008-01-27
hi lut4rp, if the sound solution [here]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235") doesn't work, which is highly unlikely, consider an upgrade to the beta version of Ubuntu (8.04 alpha three) if you really want sound.

I've installed it and the sound works straight out of the box, so thats a big plus.

If you decide to do that, type this in a terminal:
```
sudo apt-get upgrade -d
```

---

### Post by hvymtlsteve on 2008-01-27
Hey, have you guys completely wiped your original Windows installations off these computers or did you leave 'em there?
I originally decided to shrink the vista partition to half and install Feisty in the remaining space, the main reason I left vista there being that HP won't do warranty repair on the hardware if you happen to need it and you don't have the original OS on there, and you probably get jerked around a bit for using an OS other than what they designed the notebook for. But I'm probably gonna be outta the country for a good long while in a coupla months and wouldn't be able to get warranty hardware repair if I ever needed it anyway, so I'm wondering if I shouldn't just go ahead and wipe it clean, recovery partition and all and just put Hardy on and use the whole disk in EXT3.
There are not really many things I plan on using that I would really need Windows for, and as a matter of principle I'd like to just plain not have it there.

I'm possibly getting pretty close to pulling the trigger on an eeePC as a cool toy and secondary comp, too, so if this one ever farts out on me I won't be stuck with nothing...

---

### Post by avik on 2008-01-27
> Hey, have you guys completely wiped your original Windows installations off these computers or did you leave 'em there?

I got rid of everything but the recovery partition.

> as a matter of principle I'd like to just plain not have it there.

Exactly the case.

---

### Post by hvymtlsteve on 2008-01-27
Why did you keep the recovery partition?
Do you know if it even works? I've read elsewhere that HP has some generic cookie cutter crap that they put in there for all the computers even though it's not necessarily configured for whatever hardware you happen to have, so for some people it doesn't work...

---

### Post by manu456 on 2008-01-28
I've been using this laptop for 8 months now. My problem is not ubuntu related but I thought I might post it here since this where everyone with a tx1000 series hangout... I rarely use the touchscreen but the glass/plastic in front of my screen seems to be coming off at the bottom and there is a lot of play while opening or closing the lid. It feels wobbly and delicate. I'm going to contact HP support but it's a pity if a new laptop doesnt even last a year. And I take a lot of care of my laptop. Because it's my work, it's everything for me.

Is anybody else facing this problem? How are your screens holding on?

---

### Post by creatureofthedark on 2008-01-28
i have tried the rotate screen script but its not working. i have found out that it is the 

```
xrandr -0 *"normal, left, right, invert"* 
```

that is not working! any ideas why??


things that are working

touch screen
sound (including headphone jacks)
wireless

things to fix

rotate screen
web cam (not that i have tried yet)
finger print reader (not exactly at the top of my priority list)

---

### Post by simplyw00x on 2008-01-28
> Why did you keep the recovery partition?
Do you know if it even works?
Yes it does, I've tested.

> the main reason I left vista there being that HP won't do warranty repair on the hardware if you happen to need it and you don't have the original OS on there
They will do warranty repairs --- I left only the recovery partition and they fixed my laptop under warranty. Installing a new OS does not IIRC void the warranty.

---

### Post by RaZoR1394 on 2008-01-28
> **hvymtlsteve said:**
> Hey, have you guys completely wiped your original Windows installations off these computers or did you leave 'em there?
I originally decided to shrink the vista partition to half and install Feisty in the remaining space, the main reason I left vista there being that HP won't do warranty repair on the hardware if you happen to need it and you don't have the original OS on there, and you probably get jerked around a bit for using an OS other than what they designed the notebook for. But I'm probably gonna be outta the country for a good long while in a coupla months and wouldn't be able to get warranty hardware repair if I ever needed it anyway, so I'm wondering if I shouldn't just go ahead and wipe it clean, recovery partition and all and just put Hardy on and use the whole disk in EXT3.
There are not really many things I plan on using that I would really need Windows for, and as a matter of principle I'd like to just plain not have it there.

I'm possibly getting pretty close to pulling the trigger on an eeePC as a cool toy and secondary comp, too, so if this one ever farts out on me I won't be stuck with nothing...

Yes I removed exactly everything just as I did with my previous portable and it was a stupid mistake. Now I can't create restore discs. Remember to always create restore discs before you wipe the computer clean or else if you want them you'll have to pay. Sad isn't it. And it isn't exactly a small sum they want either. If you sell your computer the buyer is probably not interested in using Ubuntu but instead the original OS.

---

### Post by waspbr on 2008-01-29
okay, now I am tempted to restore windows, I am sending my tx1320 back for repairs in a bit, cos there was an "accident" and the touch screen sorta cracked, called HP and they said they would fix it for free, which is nice.  however I am not sure if they are going to like to grub loading, eventhough I kept the windows partition.  In any case I made recovery disks which I have already tested.

I guess, I am gonna fully restore windows just in case the support people are picky

---

### Post by twistadias on 2008-01-30
i donno if this has been posted but I got the wireless drivers working is less than a minute on 7.04 using this  [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Hes created an installer that does all the dirty work for you. You need to update the first post with this link

can you also update the first post with installing webcam drives. having trouble with mine

---

### Post by qhimq on 2008-01-30
hi

has anyone installed a frame limiter (fps limit) ? is there such a thing? if any graphics are let lose on my system, it gets hot way too fast.  I get about 1500fps from glxgears.

i have 169.09 driver.

---

### Post by brainsqueezer on 2008-01-30
I'm trying to join efforts. HP dv6000 series seem to have exactly the same problem:

[http://ubuntuforums.org/showthread.php?t=288867](http://ubuntuforums.org/showthread.php?t=288867)

I think a firmware update (that won't appear in next months or maybe never) or a kernel workaround must be the only one real solution. Here is the only related bug report that has not been given much importance:

[http://bugzilla.kernel.org/show_bug.cgi?id=8870](http://bugzilla.kernel.org/show_bug.cgi?id=8870)

At comment #27 a developer talk about a possible patch:

[http://bugzilla.kernel.org/show_bug.cgi?id=8870#c27](http://bugzilla.kernel.org/show_bug.cgi?id=8870#c27)

---

### Post by avik on 2008-01-30
> **hvymtlsteve said:**
> Why did you keep the recovery partition?
Do you know if it even works? I've read elsewhere that HP has some generic cookie cutter crap that they put in there for all the computers even though it's not necessarily configured for whatever hardware you happen to have, so for some people it doesn't work...

Well, I didn't know that.  I just kept it.  I'll probably be changing partitions around later anyway.

---

### Post by generalj on 2008-01-30
Hi everyone,

Just wanted to post some of things I have been experiencing.

I am using a tx1320us
ubuntu 7.10

I got the touchscreen working but it only works flawlessly right after boot. After about 10 mins it gets horribly slow and lags worse then it did on vista. Just wondering if anyone else has this as well.

I also had my webcam working once in skype beta but now it does not seem to work. When I go into skype options and select to test video the blue led on for my webcam turns on but the picture stays black..

Also my laptop seems to run really hot, I tried using the nv and nvidia drivers for these problems to see if anything changes but they don't. I also tried the different desktop visual effect settings, ie. none, normal and Extra with no changes.

regards,

---

### Post by waspbr on 2008-01-30
okay, I have the same model as you and the touchscreen runs great, I use the laptop consistently for hours and there's no lag. So what method did you use to activate it?

as for the temperature problem, well, it does get a little warm when it is on AC power but it doesn't get warm at all when i battery

In hardy however it runs extremely cool,but no touchscreen yet

---

### Post by generalj on 2008-01-30
The method I used for touchscreen was I downloaded a zip called TouchKit. I then copied egalax_drv.so to /usr/lib/xorg/modules/input/ 

Then I entered   
                          Inputdevice         "EETI"     "SendCoreEvents"
into the serverlayout in xorg.conf

then I entered   Section "InputDevice"
                                        Identifier         "EETI"
                                        Driver             "egalax"
                                        Option            "Device"             "/dev/usb/hiddev0"
                                        Option            "Parameters"      "/etc/egalax.cal"
                                        Option            "ScreenNo"        "0"
                            EndSection


I then ran the Touchkit excutable and ran the 4pt calibration which worked awesome. Then I tried the drawing test in the touchlit app and it was working awesome too. Like above it works awesome for a few mins after booting ubuntu but then gets horribly slow and laggy and I mean horribly.

I may of entered a Synaptics entry into xorg.conf to but not sure. I do have that in there but not sure if I entered it for this or not.

I also have a lot of wacom stuff in there that I am thinking of commenting out.

---

### Post by waspbr on 2008-01-30
have you tried the 25 point calibration?
the complete method on how to install the touchscreen was posted on page 55 of this thread.
check if there's anything you  might have missed.

---

### Post by generalj on 2008-01-30
Just finished a 25pt calibration, so I'll see how it goes. Going to go to post 55 and check if I missed anything. Thanks. Also do you know how to get something working so I can enter text into fields using the pen like in Vista where you get a little icon when you select a field that opens up a handwriting/keyboard tool to enter into?

Oh yeah that is the method I used on page 55, I was trying to pull it up again. I realise now that it was you that posted that, thanks because atleast it is working lol. I will do some more testing. I am wondering if my vid card is getting to hot and is causing this or something.


EDIT* Ok I just set the laptop aside for like 5 mins just to write this and it is all laggy again. hmmm. I wonder if it is some sort of standby power option or something, I have it dim the screen maybe something else is going on.

---

### Post by generalj on 2008-01-30
What boot options are you using? I am only using the noapic option. You thinkI need to add the irq one?

---

### Post by generalj on 2008-01-30
Well i have been using the touchscreen now for 20 mins without problems and actually using cellwriter to type this post. I didnt do anything but keep using the touchscreen without a pause over a few mins long. so it seems to have problems after 
not using the touch screen for longer then a few mins.

---

### Post by waspbr on 2008-01-30
I use 
```
noapic irqfixup doscsi
```

---

### Post by generalj on 2008-01-30
well is deffinatly goes to crap after not using it after a few mins. If i continue to use it its fine but stop using it for 5 mins its crap and does not get better untill a reboot. really odd. I

---

### Post by qhimq on 2008-01-31
i have this issue as well.

---

### Post by generalj on 2008-01-31
Well, so far my touchscreen seems to be working now a lot better, I did some things to get rid of a clicking noise my hard drive kept doing and it seems to of made the touchscreen better now. I will do more testing and let you know if this was actually a fix or not.

Also Anyone have luck getting rotation all figured out yet?

Oh I also managed to get my fingerprint scanner working, I can use it to log on through GDM to the system. Just cant get it to be used in gksudo. I pretty much have everything setup now cept for the touchscreen rotation. I better do a disk image to back this configuration up lol. Anyone have recommendations on how to backup my whole ubuntu system so that I can just recover it and be off?


I think someone should compile everything for their exact model (ie. tx1320us) that they got working and consolidate it somewhere.. lol no I am not volunteering. Well if I got time I will do one somewhere for the tx1320us and what I had to get all I have working so far. I will post it on my site and get a link here if I get some more time.

---

### Post by waspbr on 2008-01-31
the rotation scripts posted somewhere in this forum work,  I think the latest one is somewhere in the 40s pages. Actually I will post it here :
[http://ubuntuforums.org/showpost.php?p=3857097&postcount=427]("http://ubuntuforums.org/showpost.php?p=3857097&postcount=427")

In xorg you need to add this line to the 'Screen" section

```
Option "RandRRotation" "on"
```

then copy the script bit into gedit and save it as rotate.sh in your home directory

then to test it run it in terminal 

sudo sh rotate.sh 

after that you can create a launcher and add the command sudo sh rotate.sh to the command line (I think that's what I did) 

The problem with it is that the touchscreen is calibrated to the standard screen so it doesn't see the rotation.  The solution would be to create 4 calibration files "egalax.cal" and switch them every time you use the rotate script. I would try to do it, but I really haven't had the time to look into that, someone that is more experienced with scripting and has more time may do it.


I am glad to hear things are running better, what did u change?

---

### Post by generalj on 2008-01-31
Well the touchscreen going to crap and being really laggy is not fixxed after all. It still goes to crap, it does seem a little better but still crap.

oh yeah when my computer shuts the screen off or goes in to some kind of power saving mode the graphics come back all garbled and the screen is shifted to the left a couple inches with a black bar on the right. I have to reboot to fix it. I am beggining to think if the vid card in this laptop is bunk. I tried different drivers etc. but same thing.

---

### Post by waspbr on 2008-02-01
not exactly sure how this relates to the touchscreen, but it may have something to do with your display drivers maybe? graphics drivers are still a three headed monster that scares the crap out a me, so I am afraid I won't be much help.

If you are really concerned about this, trying out another distro or a fresh install maybe a good idea just to see if you get the same problems

---

### Post by stream303 on 2008-02-01
THANK YOU EVERYONE!!

Just picked up a tx1410us and got my Gutsy system stable thanks to the forum members.  To make a long story short, here are my kernel parameters:

```
ro quiet splash showopts **noapic acpi_irq_balance fb=false**
```

I crashed my machine about 50 times before I got this working well for a few days.  I'll reread the messages for further tweaking, but for now everything is stable and snappy.  I'll keep an eagle-eye on it and see.

I love htop!  I had added the cpu frequency scaling applets to the top bar and set them to cpu 0 and cpu1 respectively and found that they were lying!  HTOP revealed the true nature which led me to run acpi_irq_balance.  The applets just pegged, whereas htop showed that cpu 0 was doing fine, but cpu1 was max'ed out at 100%.  With this parameter, my scaling applets are running normally.

Since I use the standard "nv" video driver, I always add dithering so my fonts are nice and crisp.  I check to make sure that subpixel smoothing is enabled in font prefs, but also add the following to my device section following the nv driver in /etc/X11/xorg.conf:

```
Option   "FPDither"  "true"
```

Now that screen looks great. (Man nv for further details)  I also used the fb=false kernel parameter.  Snappier than usual!

Thanks to you guys, I have totally wiped the drive including the recovery partition and installed Gutsy with much success.  The quickie sound fix was applied and will install the touchscreen drivers soon, but had to get some sort of stability first.

Hope this helps some other tx1000 users, especially the 1410us owners.  Hibernate and suspend aren't working, but I'll do more homework with the messages.  Ten-smilies all around!

---

### Post by stream303 on 2008-02-01
> **dodgy_geeza said:**
> It happens even on a virgin system, you can boot with init=/bin/bash , and you still have the 100% cpu issue. It seems to be the USB2 controller generating a shed-load of interrupts, which because of the disabled APIC, one of the CPU's gets hammered.

I've still yet to find a workable conbination of boot options for my lappy to remove the 100% issue, which is a nightmare :'( I will be having another go this weekend coming, or at some point tomorrow (time permitting). I'm also going to try some different operating systems, as I read on another forum that it is something to do with the Ubuntu kernel, and how they have compiled USB support. Might role a vanilla kernel to see if there is a difference ;)

I *knew* I had seen this somewhere before.  Your parameters were in my subconsciousness I guess.

noapic alone got the machine to boot, but freaked out the cpus.  Adding balance seemed to restore sanity and a little video speed up to boot Gutsy:

```
ro quiet splash showopts noapic acpi_irq_balance fb=false
```

is what I use on my new tx1410us model.

Dmesg seems pretty clean.

Thanks again for putting acpi_irq_balance in my head for when I actually purchased the machine!

---

### Post by stream303 on 2008-02-01
Great - got my hibernation back with **doscsi**

Unfortunately, suspend doesn't work that great - it goes to sleep, but upon wakening, it either reboots or just sits in a dark screen.  Either way, my kernel paramaters are this since I now have hibernation back.

(So THAT explains why I ended up with an SDA5 partition on the disk when I allowed Gutsy to use the whole disk in guided partitioning...)

```
ro quiet splash showopts **noapic acpi_irq_balance fb=false doscsi**
```

I tried some of the s3 sleep modes to no avail, but great info about it here:

[http://www.linuxquestions.org/questions/linux-hardware-18/acpi-problem-when-debian-starts-533133/](http://www.linuxquestions.org/questions/linux-hardware-18/acpi-problem-when-debian-starts-533133/)

Progress!

---

### Post by brainsqueezer on 2008-02-01
**2.6.24-git9 patch**

Latest git versions of the kernel include a patch for tx1000, dv6000 and dv9000 series. I have tryed it with NO KERNEL PARAMETERS and everything seems ok. Doing a cat /proc/interrupts gives me only 1 error. Could anybody else test it?

You have to download 2.6.24 from [http://www.kernel.org/](http://www.kernel.org/) and patch [1] it with last git version (currently git10) with:

cd /usr/src/linux; bzip2 -dc ../patch-2.6.24-git10.bz2 | patch -p


I had problems with CDROM so add a blacklist line ("echo blacklist ide-cd >> /etc/modprobe.d/blacklist") or remove CDROM drive. Also ndiswrapper and nvidia propietary driver stopped working or were unable to compile. Un result by now this version is only for testing but it is important to TRY IT for reporting problems. If so write a post here.




[2] [http://kernel.org/pub/linux/kernel/v2.6/snapshots/patch-2.6.24-git10.bz2](http://kernel.org/pub/linux/kernel/v2.6/snapshots/patch-2.6.24-git10.bz2)

---

### Post by generalj on 2008-02-01
> **waspbr said:**
> not exactly sure how this relates to the touchscreen, but it may have something to do with your display drivers maybe? graphics drivers are still a three headed monster that scares the crap out a me, so I am afraid I won't be much help.

If you are really concerned about this, trying out another distro or a fresh install maybe a good idea just to see if you get the same problems

OMG! Another Distro? ME? Use another distro? maybe kubuntu or ubuntustudio? Lol. No I actually waiting for alpha4 or going to openSuse. I hear openSuse works really well out of box with this laptop. anyway I really dont want to leave ubuntu for this. I mean its like all working pretty much cept the touchscreen gets laggy when not using it. That has to be an easy fix. I will maybe try a fresh install and see what happen. joy*

---

### Post by GiraffeNecktie on 2008-02-01
> **stream303 said:**
> 

```
ro quiet splash showopts **noapic acpi_irq_balance fb=false doscsi**
```



Thanks Stream for the tip about htop!  It shows that one of my CPUs is also pinned at near 100%. 

But being a Linux noob, I'm not sure what to make of the above code.  Is this a change that you made in a config file somewhere?

LATER EDIT: Found a tutorial here: [http://blogs.techrepublic.com.com/geekend/?p=228](http://blogs.techrepublic.com.com/geekend/?p=228) which gave me enough info to make the change. It seems to have worked. The CPUs are now showing normal levels. Also the fan does not seem to be running as hard so perhaps this is helping with the heat issues.

---

### Post by generalj on 2008-02-01
OK Just an update on my tx1320us

I am running the following kernal options.

noapic - needed to install properly 

nolapic - not sure what this one is doing

acpi_irq_balance - this fixxed one of my cpu cores from being pegged at around 80% usuage and cpu scaling not working 

irqfixup - not sure what it is doing yet either

pci=nommconf - helped with video card supposedly

rootflags=data=writeback, nobh, commit=100   - these fixxed my hdd from clicking every 5 secs ****note that I had to edit some other things along with these options to work, please dont add these without knowing what you are doing I dont want to be blamed***

hda=ide=scsi - this was an attempt to get dvddecrypter in wine to see my dvd drive (did not work though)

anyways anyone see anything that I may not need there or anything i may want to add please let me know. 

My system seems to be running really stable now. Touchscreen issue I had was fixxed with either nolapic, irqfixup, or pci-nommconf, as I added these all at the same time my touchscreen started working better. I will do more testing to see what one actually fixxed it. BTW the problem with my touchscreen was if I did not use it after a few mins it would get really laggy and unusable.


***edit*** I have not tested my standby or hibernation yet in fear of data loss or system breakage. If I get time I will try to backup my system and then see if I want to dabble with hibernation/standby. Looks like I will need to add dosci option to kernal for it though not sure yet.

I also have the fingerprint scanner working, not really all that great yet as the program used is in beta, it does work though and I can log onto the system thorugh GDM using my fingerprint. However gksudo does not accept fingerprint yet. Anyone know how to get that to work or if it is available to work yet please let me know.

Another thing I just noticed, cpu scaling does not work on battery. I understand why it stays at my 800mhz setting but it would be nice to have it scale or let me choose the full cpu freq. if I do need to use the cpu power if I am on battery. Since I run a pc repair biz I would like to be able to step up my cpu if running a quick diagnostic or test on battery power while in a customers home etc.

---

### Post by generalj on 2008-02-02
anyone brave to test alpha 4 on tx1000 series yet?

---

### Post by brainsqueezer on 2008-02-02
> **generalj said:**
> anyone brave to test alpha 4 on tx1000 series yet?

HardyHeron/Alpha4 includes a 2.6.24-rc8 [1]. I think it does not include tx1000 patch [2]. Anybody could confirm it?

Version 2.6.24.1 should be first stable version  not needing kernel attributes. Anybody else is trying patched kernel versions?


**generalj:** Don't have any problems with egalax module in latest xorg versions?
> (EE) Failed to load module "egalax" (module requirement mismatch, 0)

[1] [https://wiki.ubuntu.com/HardyHeron/Alpha4](https://wiki.ubuntu.com/HardyHeron/Alpha4)
[2] [http://kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.24-rc8](http://kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.24-rc8)

---

### Post by generalj on 2008-02-03
Well trying to get the screen rotation working (as it should be working, ie. screen calibrates with rotation) I tried grandr applet, well it install and I can use the app but only to change my resolution. The function to rotate the screen that it should have just is not available, I am guessing it supports some other device/driver then the ones we have. 

Anyways, I hope we can get a rotate screen method soon. It sucks having the battery dig into my lap when using it in tablet mode. 

Also, do not try hardy alpha 4, lol. I had to reinstall Gutsy. The policy kit in it is way to buggy. ie. trying to change/configure network and it wont let you bug. Also very hard to find anything 64bit to work on it ie. wifi drivers, etc. anyways gutsy is running really well for me cept for the rotation part. Everything else is running and working well. I am running 64bit Gutsy now so the reinstall was for a good reason.

---

### Post by stream303 on 2008-02-03
> **generalj said:**
> anyways anyone see anything that I may not need there or anything i may want to add please let me know. 

Thanks for pointing those out!  Here is what another owner used on his and explains it a little.

[http://kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z](http://kellyandsopho.com/tiki/tiki-index.php?page=LinuxOnHpPaviliontx1000z)

I have since added the pci=nommconf and my random screen freezes are gone too.

From what I've seen the irqfixup is supposed to help out with those errant IRQ7's, especially when using usb.  I've seen that a time or two, so it goes in.  I'm not sure how important nolapic is when combined with all of these others, but I've tried it with no problems so far.

So, my 1410us is now running:

```
ro quiet splash showopts noapic nolapic irqfixup acpi_irq_balance doscsi pci=nommconf
```

> ***edit*** I have not tested my standby or hibernation yet in fear of data loss or system breakage. If I get time I will try to backup my system and then see if I want to dabble with hibernation/standby. Looks like I will need to add dosci option to kernal for it though not sure yet.

Hibernation is rock solid here.  The screen antics look scary at first, but after reboot it always comes back nice and clean prompting for a password to get back in.  Seeing the gnome screen just "pop" to life is reassuring.

Suspend/sleep still doesn't wake back up properly, but I'm not going to waste much more time on it.  It's a legendary problem not specific to our tablets.  Can't get my mac to sleep either. :)

> Another thing I just noticed, cpu scaling does not work on battery. I understand why it stays at my 800mhz setting but it would be nice to have it scale or let me choose the full cpu freq.

I see that too and agree that we should be able to scale it up.  I can deal with it for now.

Thanks again for sharing your kernel parameters.  It solved a few problems.  AND I haven't heard that nasty click in quite awhile, without having to apply your solution - I'll keep an eye (ear) out for it.

---

### Post by mikedep333 on 2008-02-03
If anybody here is going to use Wubi on Ubuntu hardy alpha4, you need to select "use acpi workarounds" at the grub menu.

Get Wubi for 8.04 here.
[http://ubuntuforums.org/showthread.php?t=683787](http://ubuntuforums.org/showthread.php?t=683787)

---

### Post by GiraffeNecktie on 2008-02-05
It seems that noapic causes one CPU to run near 100% whereas  irqpoll allows them to run normally. I have no idea what either option is supposed to do, but I noticed that this morning when there was sort of kernel-related update (I wasn't paying much attention) that wiped out my settings.

---

### Post by sauronsmatrix on 2008-02-05
Yo guys, 8.04 beta runs perfectly fine without any additional grub options. And its not too buggy, in fact the only bugs I'd been having were fixed in [Alpha 4]("http://cdimage.ubuntu.com/releases/hardy/alpha-4/").

---

### Post by isachan on 2008-02-05
Just for an info.

Today I got it to rotate the screen to portrait orientation (800x1280) by adding
Option "Rotate" "CW"
in
Section "Device"
of /etc/X11/xorg.conf

I think CCW, left, right, normal, inverted option works as well.

However, you'll be stuck in the specified orientation and the rotation script I got from this thread doesn't work.

I post this so that somebody knowledgeable about xorg.conf and xrandr can make some progress from here.

Isao

---

### Post by generalj on 2008-02-05
> **sauronsmatrix said:**
> Yo guys, 8.04 beta runs perfectly fine without any additional grub options. And its not too buggy, in fact the only bugs I'd been having were fixed in [Alpha 4]("http://cdimage.ubuntu.com/releases/hardy/alpha-4/").


Can you tell us your exact model and if you using 32bit or 64bit hardy alpha 4?

I tried it and could not really get anything to work. Wifi was having problems as well as Ethernet. The policy kit kept telling me I did not have permission to change settings in network config.

---

### Post by isachan on 2008-02-05
Just for an info.

Today I got it to rotate the screen to portrait orientation (800x1280) by adding
Option "Rotate" "CW"
in
Section "Device"
of /etc/X11/xorg.conf

I think CCW, left, right, normal, inverted option works as well.

However, you'll be stuck in the specified orientation and the rotation script I got from this thread doesn't work.

I post this so that somebody knowledgeable about xorg.conf and xrandr can make some progress from here.

Isao

---

### Post by isachan on 2008-02-05
Just for an info.

Today I got it to rotate the screen to portrait orientation (800x1280) by adding
Option "Rotate" "CW"
in
Section "Device"
of /etc/X11/xorg.conf

I think CCW, left, right, normal, inverted option works as well.

However, you'll be stuck in the specified orientation and the rotation script I got from this thread doesn't work.

I post this so that somebody knowledgeable about xorg.conf and xrandr can make some progress from here.

Isao

---

### Post by magicfab on 2008-02-05
I am using Hardy alpha 4 (32 bit) and compared to my initial trials with Gutsy:
- Webcam now works out of the box
- Booting/ installing does not require additional grub / kernel options

However, nvidia proprietary drivers can' t be used (so no compiz fusion for now).

I just played with this system (a tx1220ca) for  afew hours, I am updating this laptop testing page as I go:
[https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1220ca](https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1220ca)

Cheers,

---

### Post by stream303 on 2008-02-06
> **magicfab said:**
> I am using Hardy alpha 4 (32 bit) and compared to my initial trials with Gutsy:

Ok, you got me interested.  I loaded the 32 bit live-cd alpha 4 on my tx **1410us,** dedicated the whole drive.

So far so good, except that I don't have any vertical scrolling.  I didn't check this before I performed the latest updates.  I guess I should go to bug reporting but this was humorous:

What was funny was that during the fresh install from CD, I heard the Ubuntu theme while partitioning, and while system was finishing up.  Rebooted for first hd boot, and all ok.  Wanted to shutdown before installing all the new updates, and system locked with Ubuntu audio theme in a quick feedback mode on "Stopping Avahin mDNS/dns-sd Daemon Avahi Daemon".

Downloaded the updates and after a reboot I got the dreaded black screen, so I booted with noapic and it worked.  I couldn't believe this to be true, so I rebooted again without any kernel parameters and all ok, except for the lack of vertical scrolling.

Trackpad acceleration is too high - needs a tender, tender touch.

But this is a promising alpha and I'm pleased to watch the progress!

---

### Post by waspbr on 2008-02-06
I guess alpha 4's xorg is still incomplete, I had the same issue with the previous alpha versions and the solution was surprisingly simple, just copy the xorg from gutsy to hardy, they are compatible, onky difference is that that in gutsy'd xorg in the serverlayout section the option screen is wrtitten with a small case "s" instead of a capital "S" which made hardy crash on the first try  but it was easily fixed.

 I posted my xorg from alpha 3 which should still work on alpha 4, it is on page 55 of this thread, it already has the screen correction on serverlayout so you don't need to worry about any other changes.

If you choose to do that back up your xorg just in case.

---

### Post by waspbr on 2008-02-06
magicfab 


did you try installing the "restricted drivers manager" using synaptic?

---

### Post by outferno on 2008-02-06
Hey guys, I'm a total noob here, but anyway - I'm trying to understand how to get this working on my tx1000z.  I read all 61 pages, starting at page 1 before posting and re-asking the same question that has already been answered.

My question is pretty simple, I think.

But before that, let me give you some specs.
My tx1000z is configured as so:
[COLOR="Red"]I forgot to mention, mine came with the latest BIOS: F.1D
I went to HP's website and they were released in January.[/COLOR]
AMD Turion 64x2 TL-58 1.9GHz
2GB RAM
160GB SATA
Touchscreen
Webcam, Fingerprint Scanner, Microphone
802.11 b/g w/ Bluetooth

I ran into some problems when I first tried to install.  I had to first do a chkdks /f in Windows Vista in order to resize the drive.  I figure this is probably due to HP imaging their hard drives rather than doing a full format, they do a quick format and then have the image copied.

After that, in order to boot into Ubuntu's 7.10 Gutsy [COLOR="Red"]AMD64 [/COLOR]LiveCD, I had to use the noapic option (hit f6 and then I added it behind the double hyphens).

I installed and resized the drive.  40GB partition for Windows, 40GB for root, and a 4gb swap.  I left 75 gb unpartitioned for later use.

Once I had the system running, I installed htop.  It showed my CPU at close to 100% on both CPUs.  After I edited my grub boot up file under /boot/grub/menu.lst (I made a backup of it just in case), I added the irqpoll to the end.  Now my CPU usage is not at 100% and stays under 4% for both CPUs at idle. [COLOR="Red"]Update, I went to using Ubuntu 32bit... because I wanted flash.  In any case, irqpoll didn't seem to fix the 100% usage on one CPU when I switched to 32bit.  However, adding the stuff below from Zamboniman did the trick.  Unfortunately, I do not know what parameter caused the fix.[/COLOR]

I also then added all the options that Zamboniman posted up, here are his options:

[quote=Zamboniman]quiet splash noapic acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi="!Linux" acpi_os_name="Windows 2006"[/quote]

Notice, his does not have irqpoll.  I rebooted using his configuration and ran htop again, once again my system idle and CPU usage was near 100%.  I then modified his and added irqpoll to the end of it.  I rebooted, and the CPU usage is down again.

I also took off quiet, since I wanted to see what was running.

So, here are my questions:
1) Whenever I start or shut down the computer, I have white lines that run horizontally and vertically across the screen.  Is this normal?  Or do I need to load something else?
2) Does anybody else hear the hard drive clicking a lot?  This scares me, but not that much - I figure if it does this and dies within the 1 year warranty, it'll get replaced.

So, I still haven't messed with the other settings - but I'll start working on getting my sound, wireless, and tablet working by using the great posts in this thread.

---

### Post by generalj on 2008-02-06
Hi,

Well I get some lines and artifacts when shutting down and starting too, I think this is comman and not to big to worry about, I think it is just the video driver and kernel not perfected but should not be of any concern.

For question 2, I had this same issue, 

here is a link to help determine if you need this fix and how to apply it.
 
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)


please let me know if you need more help with question 2 but that link above should square you away.

---

### Post by outferno on 2008-02-06
[Wireless fix tutorial by sauronsmatrix](http://ubuntuforums.org/showpost.php?p=3491929&postcount=257)

Awesome, this works, however, 2 things to mention.
> 
5) Extract ndiswrapper to some [COLOR="Red"]folder[/COLOR], blacklist bcm43xx firmware.
```
sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
```
This, if you can't get it to work, (which I couldn't), I had to use an editor, like vi, to edit the file manually.

I just added the "blacklist bcm43xx" to the end of "blacklist" in /etc/modprobe.d

For this:
> 9) Add ndiswrapper to system```

sudo ndiswrapper -m
sudo modprobe ndiswrapper
sudo echo ndiswrapper >> /etc/modules/
```
It has a slash at the end, that should be taken out.  I also couldn't get that to work, so I went in manually and added "ndiswrapper" to the end of the modules file under /etc/

Great fix!  It works!

---

### Post by outferno on 2008-02-06
> **generalj said:**
> Hi,

Well I get some lines and artifacts when shutting down and starting too, I think this is comman and not to big to worry about, I think it is just the video driver and kernel not perfected but should not be of any concern.

For question 2, I had this same issue, 

here is a link to help determine if you need this fix and how to apply it.
 
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)


please let me know if you need more help with question 2 but that link above should square you away.

Hrm, I checked out the link, did you use the quick temporary work around?  [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14)

Also, I think another user mentioned indexing of the hard drive, I found it temporarily but now I don't know where it is, lol.

Actually, I re-read it.  I looked at my count and its at 600.  It clicks about 3 times per minute - but I'm not sure if I should apply the updated ugly fix.

---

### Post by outferno on 2008-02-06
[Sound fix tutorial by sauronsmatrix.](http://ubuntuforums.org/showpost.php?p=3475485&postcount=235)

Awesome!  This sound fix works.  I tried it on my fresh clean install of Ubuntu 7.10 AMD 64 Gutsy.

For those of you that can't log into the super user account, you may have to enable it by using this:

sudo passwd

It will ask for your password, and then it will ask you to type in a new password for the root account twice.  After its done, you can then use "su" and log in as root through the terminal.

Which brings me to another question, say I want to install a new user, and I hope this isn't a hijack, but if I install a new user, how do I change who gets to use the "sudo" command?  Thanks!

---

### Post by generalj on 2008-02-06
> **outferno said:**
> Hrm, I checked out the link, did you use the quick temporary work around?  [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14)

Also, I think another user mentioned indexing of the hard drive, I found it temporarily but now I don't know where it is, lol.

Actually, I re-read it.  I looked at my count and its at 600.  It clicks about 3 times per minute - but I'm not sure if I should apply the updated ugly fix.

Ya that is the ugly fix I used. after applying it my count stays low my hard drive clicking that was about 3 or 5 a min stopped, although it still goes when on battery which is a good thing. But while on AC power it dont.

**edit** BTW If you right click you start menu and click edit menus, in their you will find an option to add "control panel" to your menu, click it and then select control panel from you menu and it will have an indexing option in it. I disabled it but it did not help me, i left it disabled sine I really dont have the use for it though.

---

### Post by qhimq on 2008-02-07
> **Francis Pereira said:**
> There was talk about a fan for the graphics card that did not turn on. I came across this [http://forum.tabletpcreview.com/showthread.php?t=8875]("http://forum.tabletpcreview.com/showthread.php?t=8875")
From the pictures its clear that there is none. 
Interestingly:
francis@iBook:~$ cat /proc/acpi/processor/CPU0/info 
processor id:                    0
acpi id:                              0
bus mastering control:     yes
[B]power management:        no
throttling control:              no[/B]
limit interface:                  no

Notice power management and throttling control are no. Something with the acpi ?? 
My kernel line:
/boot/vmlinuz-2.6.22-14-generic root=UUID=c07ed3fe-f4af-4407-a12d-9e77db1c704d ro vga=0x317
for some reason I don't have to use all the extra parameters. vga=somevalidmode is a must though .

I can suspend and hibernate successfuly . All this on gusty .

You make a good point.  However windows tells me there are two fans.  Aux and nForce have different RPMs going at the same time.

---

### Post by outferno on 2008-02-07
> **generalj said:**
> Ya that is the ugly fix I used. after applying it my count stays low my hard drive clicking that was about 3 or 5 a min stopped, although it still goes when on battery which is a good thing. But while on AC power it dont.

**edit** BTW If you right click you start menu and click edit menus, in their you will find an option to add "control panel" to your menu, click it and then select control panel from you menu and it will have an indexing option in it. I disabled it but it did not help me, i left it disabled sine I really dont have the use for it though.

Hello generalj,

I tried out the ugly fix and followed them.  I've been paying attention to my hard drive temp as well.  The highest its gotten so far, is about 43 degrees centigrade.  I'll take a look at it again when I try out more applications.

Thanks for that link though!  The clicking is gone! :)

Oh, also forgot to mention: operating temperatures for my drive (I believe is the WD1600BEVS) is 41 degrees centigrade minimum and 140 degrees centigrade maximum.  However, at that point anywhere near 100, I'll probably be shutting it down.

---

### Post by outferno on 2008-02-08
Ok, I just noticed something from this thread:

[Modding the tx1000z part 1 (changing the thermal compound)](http://forum.tabletpcreview.com/showthread.php?t=8875)

To clear up the confusion with the question: is there a second fan on the GPU?

The answer is there isn't.  You can clearly see from the photos of the OP that the GPU shares the same heat sink and fan as the CPU.  :)  I'll be doing this guys mod in the near future.

---

### Post by Lambenttelos on 2008-02-09
First of all thank you to everyone who has contributed here, I was solving problems before I even knew I had them! (such as the cpu maxed at 100%)  I have a tx1115nr and for some reason my sound just is not quite right. Following some of the instructions found earlier in the discussion I was able to get sound out of my speakers but not the headphone jacks by using "options snd-hda-intel model=3stack".  Seeing that the newer alsa drivers should support the tx1000's now I followed the new guide and changed my etc/modprobe.d/alsa-base to "options snd-hda-intel model=hp"  This however broke everything and left me with no sound out of either the speakers or the headphone jacks.  

So, at this point I have gone back to using model=3stack so I have at least some audio, but any suggestions on the headphones would be appreciated.

Note I've tried both versions 1.0.15 and 1.0.16 of ALSA

Thanks again guys!

---

### Post by magicfab on 2008-02-10
Hi, I posted a few days ago. I have a tx1220 and I am documenting my progress at:
[https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1220ca](https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1220ca)

I now have working headphones (both jacks,sensing), using Ubuntu Hardy (8.04) alpha 4, upgraded as of today. My reasoning behind using Hardy is I'd rather spend time fixing things there than on an already released version. This is my main working computer now so it's a nice challenge :)

I discovered if using Xinerama compiz won't work. In any case there are important daily updates to compiz and other related packages so I have disabled it. I am OK wiating a few weeks until everything is a bit more stable. Xorg was also broken for a day or two, I expect that during development.

I really didn't want to install anything manually (download/compile/install), particularly drivers as kernel upgrades may break them, and, well, I hate chasing that. Anyways, notes on how my audio works are on the above URL. 

I am now looking for information on mapping those nice buttons, particularly screen rotation :) Did you know QuickPlay used to be powered by Linux ?

---

### Post by Francis Pereira on 2008-02-11
> **outferno said:**
> Ok, I just noticed something from this thread:

[Modding the tx1000z part 1 (changing the thermal compound)](http://forum.tabletpcreview.com/showthread.php?t=8875)

To clear up the confusion with the question: is there a second fan on the GPU?

The answer is there isn't.  You can clearly see from the photos of the OP that the GPU shares the same heat sink and fan as the CPU.  :)  I'll be doing this guys mod in the near future.

How does M$ manage to run cooler ? Why does it show two fans ? Where does it get the values from. There is certainly some acpi  issue with the new HP machines . Its just not the TX1000 , I have a couple of HP DL 380's they too don't report any fan activity in the /proc/acpi

Anyone, any clue as to whats with the apci ??

ps I don't use noacpi 

Cheers ,
Francis Pereira

---

### Post by outferno on 2008-02-11
To be honest, I do not know the software commands to see the fan operation for the GPU.

If you could tell me, I can probably mull it over and come up with a good reason, lol.  The hardware for the second fan is definitely not there though.

---

### Post by ir0nman on 2008-02-11
Well I was having the egalax problem with it not loading in Hardy. I sent part of my xorg.0.log to them and they replied that they are going to test against Hardy, and recompile new drivers. they said they would let me know when they had it ready for me. I'll keep you guys posted, as I hear more.

-Rick

---

### Post by outferno on 2008-02-12
Just an update, I decided to try out the [touchscreen tutorial using in this thread.](http://ubuntuforums.org/showpost.php?p=4197376&postcount=542)

It works!  I went through the calibration and it works much better than the Vista touch screen.

Does anybody know how to rotate the screen though?  I tried using the xandr script and I guess it wasn't made for Gutsy i386 or perhaps I'm missing something?

---

### Post by crazystar on 2008-02-12
I have a Tx1410us,wireless is working with ndiswrapper and bcm drivers ,Can somebody please help me or direct me towards getting  WPA enabled.

I am frustrated and about to give up on ubuntu.I really dont want to go back to vista..

Thanks

---

### Post by stream303 on 2008-02-12
> **crazystar said:**
> I am frustrated and about to give up on ubuntu.I really dont want to go back to vista

Do what I did:  wipe out the disk completely and refuse to make windows restore disks. :)
(running and ducking...)

Are you installing Gutsy or Hardy Alpha?  Although I'm not a wireless guru I can't help you there, but Hardy Alpha seems to be doing great so far on my 1410us without any special kernel parameters etc.  I used the Hardy daily "alternate" for the install:

[http://cdimage.ubuntu.com/daily/](http://cdimage.ubuntu.com/daily/)

Hopefully somebody smarter than me when it comes to wireless can pop in..

---

### Post by manu456 on 2008-02-13
The update manager showed a new kernel update today and after installing that for the first time ever I'm able to boot without any kernel flags! I was using 'noapic' before this.

I have been using my laptop(tx1003au) for a couple of hours and it seems very stable. :D

---

### Post by waspbr on 2008-02-13
Thanks Ir0nman (rick), we really appreciate you going out of your way to get the egalax issue on hardy solved. Keep us posted if you receive anything back.

---

### Post by waspbr on 2008-02-13
Outferno: for the screen rotation try this
[http://ubuntuforums.org/showpost.php?p=4241341&postcount=579]("http://ubuntuforums.org/showpost.php?p=4241341&postcount=579")

---

### Post by Cuppa-Chino on 2008-02-13
> **manu456 said:**
> The update manager showed a new kernel update today and after installing that for the first time ever I'm able to boot without any kernel flags! I was using 'noapic' before this.

I have been using my laptop(tx1003au) for a couple of hours and it seems very stable. :D

what kernel did you upgrade to?

---

### Post by manu456 on 2008-02-13
> **Cuppa-Chino said:**
> what kernel did you upgrade to?

My /boot folder says 2.6.22-14-generic. Although I think I spoke too soon. My laptop gets stuck on alternate boots so I'm back to using noapic :(

---

### Post by outferno on 2008-02-13
> **waspbr said:**
> Outferno: for the screen rotation try this
[http://ubuntuforums.org/showpost.php?p=4241341&postcount=579]("http://ubuntuforums.org/showpost.php?p=4241341&postcount=579")

Thanks!  That worked out great! :)

---

### Post by ex17 on 2008-02-13
Hello all I've got a strange problem and I haven't found anyone else having it.
I've got Gutsy 7.1 right on a tx1325ep.
The thing is there seems to be a problem with the Ethernet board. when I plug a cable, the lights blink and all but I can't seem to connect anything.
when I do ifconfig I see eth0, mac adress and all. So I presume Linux can actually find it right?
I don't know help me out, if you need any additional output let me know.
Thank from a Linux No0B :confused:

---

### Post by GiraffeNecktie on 2008-02-13
Help!

The latest kernel update seems to be completely incompatible with my system. Previously I just had irqpoll in my boot parameters. Now it doesn't boot at all no matter what parameters I add. I don't mind spending a bit of time getting things set up but it's totally disheartening when simple updates knock me back to the beginning. 

Looks like it's back to Vista for me. I hate it with a passion but it least it's halfway stable and it frickin works on the TX1000.

LATER UPDATE: Oh never mind. Nominate me for moron of the month. Actually the kernel update is working very well WITHOUT ANY BOOT PARAMETERS.

 I simply forgot that I was plugged into a KVM switch so it looked like the laptop screen was going blank when I actually just had to flick the switch and it shows up on my big monitor.
Sheesh. What an idiot.

---

### Post by GiraffeNecktie on 2008-02-14
LATER UPDATE: Well like manu456 I've found that the kernel update is not reliable without the boot parameters. It worked great for the first 3 or 4 boots and then this morning it wouldn't boot at all until I added irqpoll.

---

### Post by magicfab on 2008-02-14
Argh! I don't have time to test these right now but there are new drivers for egalax touchscreens as of Feb 13 available here:
[http://210.64.17.162/web20/TouckDriver/linuxDriver.htm](http://210.64.17.162/web20/TouckDriver/linuxDriver.htm)

If anyone gives them a try under Hardy, I'd like to read about it here :)

---

### Post by ir0nman on 2008-02-15
I got no change, but then again the gentleman I was talking to for support has not emailed me back to say that they finished, so hopefully that means these are just an intermediate set of drivers.
-Rick

---

### Post by crazystar on 2008-02-16
WPA help anyone???

---

### Post by Cuppa-Chino on 2008-02-16
> **crazystar said:**
> WPA help anyone???

what guide did you use to get wireless up ? 
this one [http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092") ?

have you check with wpa_supplicant is installed in synaptic ?

have you tried installing wicd [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php") it works really well as a network manager for many folk --- after upgrading to all the latest versions it now does the trick on my tx1000 series

---

### Post by RaZoR1394 on 2008-02-16
> **magicfab said:**
> Argh! I don't have time to test these right now but there are new drivers for egalax touchscreens as of Feb 13 available here:
[http://210.64.17.162/web20/TouckDriver/linuxDriver.htm](http://210.64.17.162/web20/TouckDriver/linuxDriver.htm)

If anyone gives them a try under Hardy, I'd like to read about it here :)

> 
razor1394@viper:~$ cat /var/log/Xorg.0.log
Xorg.0.log      Xorg.0.log.old  
razor1394@viper:~$ cat /var/log/Xorg.0.log | grep egalax
(II) LoadModule: "egalax"
(II) Loading /usr/lib/xorg/modules/input//egalax_drv.so
(II) Module egalax: vendor="X.Org Foundation"
(II) UnloadModule: "egalax"
(II) Unloading /usr/lib/xorg/modules/input//egalax_drv.so
(EE) Failed to load module "egalax" (module requirement mismatch, 0)
(EE) No Input driver matching `egalax'


no go...

---

### Post by outferno on 2008-02-17
Just wondering if anybody else is having a problem with the touchscreen.  I did the 25 point calibration and after a restart, I lose all of my settings in the calibration.  Anybody else? :)

---

### Post by waspbr on 2008-02-17
did u remember to blacklist the 2 modules? are you using the new drivers or the previous ones?

---

### Post by crazystar on 2008-02-19
> **Cuppa-Chino said:**
> what guide did you use to get wireless up ? 
this one [http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092") ?

have you check with wpa_supplicant is installed in synaptic ?

have you tried installing wicd [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php") it works really well as a network manager for many folk --- after upgrading to all the latest versions it now does the trick on my tx1000 series

ahhhh.....you are awesome!!!!

---

### Post by outferno on 2008-02-19
> **waspbr said:**
> did u remember to blacklist the 2 modules? are you using the new drivers or the previous ones?

Hrm, I have the modules blacklisted - but how do I check the driver version?

---

### Post by magicfab on 2008-02-19
BTW, for those of you having read all the way through here, I found a nice offer from HP. You can get a free SkinIt skin for your HP laptop by going to:
[http://hp.skinit.com/direct1/?affiliate=hpCTO](http://hp.skinit.com/direct1/?affiliate=hpCTO)

(the affiliate code is not mine nor do I know where it came from, I am pasting that as I found it via Google)

Once there choose the tx1000z as your model and provide your serial number. You can find out your serial number without looking under your laptop by issuing this command from a terminal window:
```
sudo dmidecode -s system-serial-number
```

I went through the process for my tx1220ca (Canadian) laptop and completed my order ($0 total), many countries are listed and seem valid destinations for this.

---

### Post by Predius on 2008-02-20
Hey guys, I managed to make the touchscreen work, and the rotate work. However, when I rotate, the calibration goes crazy and i have to recalibrate every time I rotate. Any way of fixing this?

---

### Post by magicfab on 2008-02-20
Predius, care to share how you got it working and how you do rotation ? What exact model do you have ?

---

### Post by waspbr on 2008-02-21
Fabian , check out my post on page 63 about rotation of the screen.

The way to fix the "every time I rotate the screen I have to calibrate the touchscreen again"problem  would be to calibrate the screen in all four diferent positions, this would produce 4 calibration files, the way to do this would be to make a script that changes the xorg reference to the calibration file. One way to do this would be to make a script that edits xorg every time the screen rotates, although I think xorg would have to be restarted every time for setting to take effect (not sure). Another way would be to make a script that overwrites the calibration file with the calibration file of the respective orientation.


Outferno, I guess it shouldn't really matter which version you have, since you after restarting you lose your calibration but  still are able to re-calibrate, then it is not the case that the screen isn't reading the calibration files correctly, just that it can't seem to save it... I am really not sure on this one... does anyone have any suggestions?

---

### Post by necrolin on 2008-02-22
I updated my Bios to the latest version and now Ubuntu won't boot (not from the live cd nor from the hard drive). Vista works fine though... strange.

Can someone let me know which version of bios they are running on their machines. I've got F1D and it just won't work with Ubuntu. :confused:

---

### Post by cabernet54 on 2008-02-22
> **necrolin said:**
> I updated my Bios to the latest version and now Ubuntu won't boot (not from the live cd nor from the hard drive). Vista works fine though... strange.

Can someone let me know which version of bios they are running on their machines. I've got F1D and it just won't work with Ubuntu. :confused:

My last bios update is F1C (for my tx1140ea in Italy - same of TX1120us) and in my treboot (Vista - XP - Ubuntu 7.04) all is working well !!! :guitar:

---

### Post by necrolin on 2008-02-22
Thanks I'll revert back to that version of the BIOS and see what happens.

---

### Post by dugald on 2008-02-22
I read your post as part of setting up a TouchKit touchscreen on a POS terminal.  I couldn't get it to work at first.

BTW I am installing this on a Partner PT6900 Point of Sale touchscreen unit, NOT A TX1000.

This is how I got mine to work in case anyone else is reading this and has a similar setup.
It turns out my touchscreen is connected on COM5.  i.e. ttyS4.  However, Linux doesn't seem to pick this up correctly.  Tried doing some research on this but it was a load of dead ends.

In the end I got it working by DISABLING COM4 and COM6 in the BIOS. I set COM5 to have an IRQ of 3 (or 4 - can't remember).  Strangely this sets COM5 to ttyS0. and "dmesg | grep tty" command tells me that it has IRQ0  - a bit wierd.    In xorg.conf, in the input device section, "device" should be /dev/ttyS0:
```

Section "InputDevice"
      Identifier "EETI"
      Driver "egalax"
      Option "Device"    "/dev/ttyS0"
      Option "Parameters" "/etc/egalax.cal"
      Option "ScreenNo"   "0"
EndSection

```
The exact BIOS configuration was this:
```

Serial Port 1   |   2E8/IRQ3
Serial Port 2   |   3E8/IRQ4
Parallel Port   |  Disabled
Serial Port 3   |   2F8/IRQ5
Serial Port 4   |   Disabled/IRQ10
Serial Port 5   |   4E8/IRQ4
Serial Port 6   |   Disabled/IRQ7

```

It works for me.  I hope this helps someone. :)

---

### Post by crazystar on 2008-02-25
I have a tx1410us with gutsy gibbon.

- Sound is working great
- Touch screen better than vista
- Wireless works so-so

Here is the deal,I have Wireless working with wpa1/2.But when i am in my university(WPA Enterprise) doesnot recoginze the ssid.I have also tried wicd but no luck there.

Any suggestions?

---

### Post by waspbr on 2008-02-26
WPA Enterprise 2 works for me while I access eduroam at my uni at the netherlands

---

### Post by outferno on 2008-02-26
> **waspbr said:**
> Outferno, I guess it shouldn't really matter which version you have, since you after restarting you lose your calibration but  still are able to re-calibrate, then it is not the case that the screen isn't reading the calibration files correctly, just that it can't seem to save it... I am really not sure on this one... does anyone have any suggestions?

Hello,

Thanks for helping. The version I have is 1.07.0725 which looks like it was compiled in August of 2007, and I had recently gotten my laptop in 2008.  I'm not sure why it's not saving, I did a 4 point calibration and saved it and did a 25 point calibration and saved it.  However, after a restart, the calibration is lost :(.

I also noticed this in your code:
```
Section "InputDevice"
      Identifier "EETI"
      Driver "egalax"
      Option "Device"    "/dev/usb/hiddev0"
      Option "Parameters" "/etc/egalax.cal"
      Option "ScreenNo"   "0"
EndSection
```

I don't seem to have an egalax.cal file, is this specific to the  64 bit version?  When I look for egalax using "locate egala*" I get these items:

```

/home/uname/TouchKit/egalax_drv.o
/home/uname/TouchKit/egalax_drv.so
/usr/src/linux-headers-2.6.22-14-generic/include/config/touchscreen/usb/egalax.h
/usr/lib/xorg/modules/input/egalax_drv.so
```

maybe that has something to do with it?

---

### Post by inernets on 2008-02-27
Hello, i am about to install linux for the first time, and i would really like to run ubuntu.  I see theres 60+ pages of replies, could someone please point me to a good spot to start from? 

I think i need to install Fedora 7 first.  Can i install Fedora 8?  

Also, i have a partion for Vista,  how do i get rid of it?

---

### Post by waspbr on 2008-02-27
Outferno, are you using gutsy 64?

---

### Post by waspbr on 2008-02-27
inernets

First of all, since this is your first time with linux I advise you to keep you vista partition, remember to burn the recovery disks before installing Ubuntu or any linux distro (better safe than sorry). Again, since this is your first time, I would advise you to make a dual boot with vista, since there is a learning curve to Ubuntu.

It may be a good idea to update your BIOS while you still have vista

[B][U]Installing Ubuntu 7.10 Gutsy  Gibbon
[/U][/B]
1 - for running the Live CD you should edit the boot command adding, "noapic". .

you can do that by pressing F6 at the liveCD main menu screen.


You will have to edit a file called boot/grub/menu.lst afterwards, I added "noapic irqfixup doscsi", some other people use different stuff, but start with this one

2-wireless

[http://ubuntuforums.org/showpost.php?p=3491929&postcount=257]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257")

3- Sound

[http://ubuntuforums.org/showpost.php?p=3475485&postcount=235]("http://ubuntuforums.org/showpost.php?p=3475485&postcount=235")

4- Touchscreen

[http://ubuntuforums.org/showpost.php?p=4197376&postcount=542]("http://ubuntuforums.org/showpost.php?p=4197376&postcount=542")

5 - Screen Rotation

[http://ubuntuforums.org/showpost.php?p=4241341&postcount=579](http://ubuntuforums.org/showpost.php?p=4241341&postcount=579)

[B][U]
installing Ubuntu 8.04 Hardy Heron[/U][/B]


Well hardy is a little more friendly, although it is still in alpha phase, so not everything is polished and done. No boot line codes need to be added for Hardy.

the only thing that needs some tinkering in hardy is the wireless, you need to have a land connection, go to System => Administration => Synaptic Package Manager (your new best friend), search for b43, something like fw-b43cutter should come up (something like that) install it and  your wireless should work.

Those who are lucky to have the bcm 4328/29 wireless cards, the b43 drivers won't work just yet. The alternative is using ndiswrapper through sauron's method:

1-wireless

[http://ubuntuforums.org/showpost.php?p=3491929&postcount=257]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257")


**Alternative installation**

You may want to consider installing hardy via Wubi (Windows Ubuntu Installer), it install ubuntu on vista as a program, without creating a partition, if you wish to remove it, then you just have to unnistall Wubi in vista. Wubi is in the latest Ubuntu 8.04 Hardy Heron live CD

You don't need Fedora to try Ubuntu, but you may install  it as another distro in another partition that you make, keep in mind that you can only have a total of 4 partitions in a hard drive. 

Touchscreen, is not working in hardy (yet?)

Anyway guess this sums it up, post any questions you might have

---

### Post by outferno on 2008-02-27
> **waspbr said:**
> Outferno, are you using gutsy 64?

I'm using the i386 version.

---

### Post by waspbr on 2008-02-27
okay...

when you run the touch kit program for the calibration , try becoming root first. 

```
su
cd TouchKit
./TouchKit
```

then do the calibration

it's  a long shot, but it might be it

---

### Post by outferno on 2008-02-27
> **waspbr said:**
> okay...

when you run the touch kit program for the calibration , try becoming root first. 

```
su
cd TouchKit
./TouchKit
```

then do the calibration

it's  a long shot, but it might be it

I get this when I run it as root: 
```
Qt: Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

I restarted and it didn't work.  Hrm... this is really strange.

One thing I do notice is that the pointer goes to the opposite part of the screen when I move the stylus across the screen.  E.g. if I am moving my stylus left, the pointer goes right.  If I move my stylus up, the pointer goes down.  That's always after the restart as well.

I forgot to mention, I updated to the latest drivers last night to see if it would make a difference - it hasn't changed anything, still can't save my calibration after a restart.  :(

---

### Post by waspbr on 2008-02-27
try 

```
sudo su
```

to login as root, and try to calibrate again...

---

### Post by outferno on 2008-02-28
> **waspbr said:**
> try 

```
sudo su
```

to login as root, and try to calibrate again...

Hello waspbr, I really appreciate the help.  I tried it again using sudo su, and unfortunately it still gave me the same error and it didn't save.

---

### Post by waspbr on 2008-02-28
No problem Outferno, I feel I am missing something here, but I can't put my finger on it.

I remember that once I got an error too, it got solved when I re-downloaded the file and repeated the install procedure, apparently the file (the Touchkit folder including the drivers) got corrupted somehow, repeat the installation procedure in page 55.

Assuming it you are able to calibrate the screen, try doing that, then go to the /etc folder and copy the egalax.cal file, if you manage to calibrate it, then it should be there. Restart. If the screen is not working then, modify xorg 

```
sudo gedit /etc/X11/xorg.conf
```

and modify the parameters line, where it reads "/etc/egalax.cal" to "whateverfolderlocation/egalax.cal", the homefolder should be a good choice for a trial run

alternatively

after copying the file to another location, after restart, if the calibration is gone again,  copy the to the  folder /etc/

an easy way is just by doing 

```
sudo nautilus
```

and the rest is just copy and paste

if that still doesn't work...then perhaps a fresh install might solve it... just might

I don't know exactly but could it be an IRQ problem?

---

### Post by outferno on 2008-02-28
Hrm, I think you may be onto something.  I recalibrated and I can't find a egalax.cal file anywhere.  I used "locate egalax.cal" and it returned nothing :(

Would it matter if the files in TouchKit were owned by root or not?

Also, where did you put your TouchKit directory?

---

### Post by inernets on 2008-02-28
Hey guys, I made a serious Boo-Boo and i'm trying to run back to windows.  Linux is too much for me to do on my own, i need a friend who knows what he's doing to help me out, which i dont have now so i need to go back to windows.  

I have a problem though, and i am pretty desperate. I installed Fedora thinking i needed that, and it crashed everytime during the instalation process.  I gave up and i want to go back to windows.

 I DID NOT make Vista back up cds, but i do have windows XP tablet edition cds.  WHen i put the cd in for windows XP, right after i hit "press any key to run from cd.."  it says "inspecting Hardware" and goes black and nothing happens.

i am guess it cant copy the files to my computer, what should i do?  I still have the vista partition, is there anyway i can download a vista CD from torrents to recover the partition?  Or is there some kind of CD i can download to reformat my drive to let me install windows XP?  I am very desperate, thanks for anyones help.

---

### Post by vinc386 on 2008-02-28
hi ppl, im new here n i dont know much about ubuntu.
are u guys talking about the hp tx1000z tablet? 
i have one, and i was about to install ubuntu on it. is this a good idea? is it terribly hard to get all drivers? the thing i most concerned is the screen, will i still be able to write on the screen after i install ubuntu??

---

### Post by outferno on 2008-02-28
So, I decided to look at my menu.lst again to see what kind of parameters to run on my Ubuntu system for the tx1000z and I narrowed it down to these options:

noapic and acpi_irq_balance

With noapic, it has to be on in order to boot on Gutsy (I believe that's what it was for) and acpi_irq_balance will keep both cores at around 0-5% usage at idle.  I haven't seen any bad effects from running just these two options.  I believe my sound, networking, etc, all still work.

I just have to get the touchscreen calibration to save now.

---

### Post by GiraffeNecktie on 2008-02-29
> **inernets said:**
>  I still have the vista partition, is there anyway i can download a vista CD from torrents to recover the partition?  Or is there some kind of CD i can download to reformat my drive to let me install windows XP?  I am very desperate, thanks for anyones help.

Try calling HP and asking for a Vista restore CD, that's what I did before I installed Ubuntu. Fortunately everything's worked ok (knock on wood).

---

### Post by Cuppa-Chino on 2008-02-29
> **vinc386 said:**
> hi ppl, im new here n i dont know much about ubuntu.
are u guys talking about the hp tx1000z tablet? 
i have one, and i was about to install ubuntu on it. is this a good idea? is it terribly hard to get all drivers? the thing i most concerned is the screen, will i still be able to write on the screen after i install ubuntu??

yes this is the (long) thread for the tx1*** series of laptops, a couple of posts above

[I]2 Days Ago 09:42 AM
waspbr 	
Re: Helpfull Hints for a tx1000 (tx1120)[/I] 

a summary of actions was written, you can get everything to work but it might require some patience, it is recommended that you do NOT delete your vista partition if you do not feel that you are a linux savant, also make your recover cd/dvd with the tool from hp, if all else fails this will get you back to scratch -- mind you with a bit of care and this thread you should get there without that problem !

---

### Post by Cuppa-Chino on 2008-02-29
> **magicfab said:**
> BTW, for those of you having read all the way through here, I found a nice offer from HP. You can get a free SkinIt skin for your HP laptop by going to:
[http://hp.skinit.com/direct1/?affiliate=hpCTO](http://hp.skinit.com/direct1/?affiliate=hpCTO)

(the affiliate code is not mine nor do I know where it came from, I am pasting that as I found it via Google)

Once there choose the tx1000z as your model and provide your serial number. You can find out your serial number without looking under your laptop by issuing this command from a terminal window:
```
sudo dmidecode -s system-serial-number
```

I went through the process for my tx1220ca (Canadian) laptop and completed my order ($0 total), many countries are listed and seem valid destinations for this.

out of stock :(

---

### Post by EddieGuarraro on 2008-02-29
Lol, you just have to email the support email that's provided, and they'll send you a code the next day that you apply to the checkout page. :) I made my own, and it's sick awesome. Ubuntu skin FTW!!!111one!!11!!!eleven!!! (just kidding with that exclamation marks....) They're flash editor is amazing. Good luck and happy skinning!

---

### Post by vinc386 on 2008-03-02
> **Cuppa-Chino said:**
> yes this is the (long) thread for the tx1*** series of laptops, a couple of posts above

[I]2 Days Ago 09:42 AM
waspbr 	
Re: Helpfull Hints for a tx1000 (tx1120)[/I] 

a summary of actions was written, you can get everything to work but it might require some patience, it is recommended that you do NOT delete your vista partition if you do not feel that you are a linux savant, also make your recover cd/dvd with the tool from hp, if all else fails this will get you back to scratch -- mind you with a bit of care and this thread you should get there without that problem !

thx for ur concern!
thats very helpful information, i may try to do that on my own tablet

---

### Post by ccw127 on 2008-03-02
So here is where I am; this laptop is frustrating the heck out of me. I went with the hardy method of getting my tx1320us running. But this means that my touchscreen is useless. Also, I apparently ended up with a bcm4328 in mine, so I am stuck with ndiswrapper (which just broke as of today; hey I don't need wireless anyway, right?). Hardy is getting better by the day (except for today's kernel update) but I am starting to go mad. And I am at the point that I am stuck between a rock and a real nasty place (Vista). 

To fix my wireless, should I reinstall the whole thing (clean install), or try and clean out fwcutter and ndiswrapper and start from there?

Anyone think the touchscreen will work in time for April, or should I just go back to Gutsy? I am concerned with all the boot options that are required just to get it running, and I love how most everything (sans touch and wireless) worked from the get go for hardy.

Chris

---

### Post by waspbr on 2008-03-03
hey there, I have the same computer as you do.

So far there has been no solution for the hardy touchscreen problem. And the tx1320us has the bcm4328 with is not yet supported by the b43 drivers (yet)...
 I keep  hearing that hardy and  ndiswrapper don't get along very well.it used to work well up to alpha 3...but I have a wireless USB dongle anyway (a lifesaver when distro hopping)

So my advice is that, until they release a more stable version of hardy, stick with gutsy.I myself just keep hardy to test some stuff every now and then or to edit gutsy in case I break something.

---

### Post by doctor628 on 2008-03-03
Hi all,

I am relatively new with Ubuntu, but I have been able to get Hardy working very well on my laptop.  There are minor things not working that I don't really worry too much about.  I can wait for a simpler fix for the touchscreen.  The thing that is driving me crazy is the touchpad.  It is waaaaaaaay too sensitive.  Just dragging around the screen selects everything the cursor is over.  I googled and found many solutions involving shm enabling in xorg.conf.  This does not work for me.  Gsynaptics, Qsynaptics, and synclient all complain about shmconfig not being enabled even though I have enabled this.  Anyone know of a solution to this?
Thanks
Heres my xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
	Option          "SHMConfig"             "on"
        Option          "HorizScrollDelta"      "0"	
	Option		"MaxTapTime"		"0"
EndSection


Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by hojthojt on 2008-03-03
Hi,
I have read through this thread, and without the info found here I wouldn't have had a chance to get Gutsy 7.10 AMD64 working on my tx1151ea.

Now almost everything works that I need to get working (I'll post the complete story later).

One thing that still puzzles me though, is the kernel options. Even though I have read all posts in this thread, I do not get a clear picture of which kernel options to use. I have HP BIOS version F.1D and use the kernel options:

  noapic irqpoll noirqdebug

to boot. This seems to be stable for me except for suspend / hibernate. The odd thing is that it works when running on battery, bet if I try to wake it up when the power cable is connected, the screen is never turned on (even though it seems like the rest of the computer starts).

What are you other people out there currently use as your kernel options to make Gutsy 7.10 run well? Does suspend / hibernate work for you? 

Regards and thanks for all the help!

---

### Post by GiraffeNecktie on 2008-03-03
> **hojthojt said:**
> 

One thing that still puzzles me though, is the kernel options. Even though I have read all posts in this thread, I do not get a clear picture of which kernel options to use. I have HP BIOS version F.1D and use the kernel options:

  noapic irqpoll noirqdebug



For a while I'd been running with just irqpoll but I was getting really frustrated because I couldn't even shut down reliably. On the weekend, I changed to 

noapic acpi_irq_balance irqfixup irqdebug pci=biosirq pci=nomsi acpi_osi="!Linux" acpi_os_name="Windows 2006" irqpoll

This seems to have fixed the shutdown problem and it even seems to be hibernating properly (although I've only tried it once or twice since the change).

My biggest remaining issue is that the computer frequently freezes up for about five or ten seconds at a time, especially when using Firefox with certain websites. I'm not sure if this is a problem with Firefox, with Ubuntu or with the way Ubuntu is configured for the TX1000.

---

### Post by waspbr on 2008-03-09
hey everyone, 

so i finally got around installing hardy 6, the installation was very smooth and showed no hic ups. The only problem for me was that the b43 drivers don't support bcm4328 yet, but sauronsmatrix solution for the wireless using ndiswrapper seemed to fix it... so far so good. 

The only complaint I have is the temperature, , right now Ktemperature reads 50 degrees, which is not ideal. I wanted to see how the computer would handle some extra load, so I tried a small game of "Glest"(free rts game available at synaptic). And the temperature just went up, it registered 78 degrees, which is really worrisome.


Did anyone else get high temeperatures in hardy? I know this is not a gaming pc, but i thought it would handle glest a little better(temperature wise).

I did this while plugged in to the A/C.

haven't tried the touchscreen yet... will do that later

---

### Post by RaZoR1394 on 2008-03-09
> **waspbr said:**
> hey everyone, 

so i finally got around installing hardy 6, the installation was very smooth and showed no hic ups. The only problem for me was that the b43 drivers don't support bcm4328 yet, but sauronsmatrix solution for the wireless using ndiswrapper seemed to fix it... so far so good. 

The only complaint I have is the temperature, , right now Ktemperature reads 50 degrees, which is not ideal. I wanted to see how the computer would handle some extra load, so I tried a small game of "Glest"(free rts game available at synaptic). And the temperature just went up, it registered 78 degrees, which is really worrisome.


Did anyone else get high temeperatures in hardy? I know this is not a gaming pc, but i thought it would handle glest a little better(temperature wise).

I did this while plugged in to the A/C.

haven't tried the touchscreen yet... will do that later

I get about 50C +-5C on both cores with Hardy. I'm personally not worried. 78C on full load isn't that much. I would be worried if it would start reaching 90 or 100C. But of course, lower temperature is always better (just not too low) for cpu and gpu. When my warranty runs out  I may try to change cooling paste like described in a post on I think a tablet forum. I hope b43 will work with your card soon because It's a really awesome driver.

---

### Post by GiraffeNecktie on 2008-03-09
What are you guys using to monitor your temperature in Alpha 6? I've tried several temp monitoring applications and I can't seem to get any of them to run.

So far the basics seem to work well in Alpha 6 except for the wireless although I haven't tried ndiswrapper yet. The "Screens and Graphics" app keeps crashing but it doesn't seem to make a difference since the nvidia-settings program has been working well (maybe I should remove the screens and graphics app).

One weird thing that's happened a few times is that my keyboard has suddenly, like in mid-sentence,  switched to a different language (Amharic and Arabic!).

---

### Post by GiraffeNecktie on 2008-03-09
Can't seem to get the wireless card working under Hardy alpha 6 even after twice trying Sauronsmatrix's instructions ([http://ubuntuforums.org/showpost.php?p=3491929&postcount=257](http://ubuntuforums.org/showpost.php?p=3491929&postcount=257)).

The card is recognized by the system: 03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

Anybody have any suggestions?

---

### Post by matashman on 2008-03-09
Had to additionally blacklist b43 in Hardy Heron to make it work in my tx1003 au model, thanks for the rest of the information!.

Hardy Heron.

Additional steps that must be performed:
1) Add the new hardy driver to the blacklist (/etc/modprobe.d/blacklist):
```
blacklist ssb
```
```
blacklist b43
```

2) Add these lines to the etc/rc.local file.
```
rmmod ohci_hcd
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ohci_hcd
```[/QUOTE]

---

### Post by GiraffeNecktie on 2008-03-09
> **matashman said:**
> Had to additionally  ...


Seems like that nailed it!

Thanks.

---

### Post by waspbr on 2008-03-10
for the temperature I use Ktemperature, you can find it in synaptic.

Although I would be happy to hear about any other temperature gauge programs in ubuntu.

---

### Post by GiraffeNecktie on 2008-03-10
My new problem (does it ever end?) with hardy alpha 6 is that the laptop doesn't recognize my external mouse and keyboard (although it seemed to have no problem with the keyboard and mouse connected to the docking station).

Also the sound has stopped working.

---

### Post by mkarnicki on 2008-03-10
I went through like 40-64 page of this thread so forgive me skipping last ones.


**@waspb**

I know you haven't checked, so I'm responding. Your tutorial for the touchscreen doesn't work under Hardy Heron (latest alfa) with 2.6.24-10-generic kernel. That's sad :( (I went back to this kernel to have fully working wi-fi and compiz)

**@generalj**

WOW! So I'm not the only one to hear this tickin' thing thing of my hard drive? You mean that this can be fixed just like that? I hear this strange noise from time to time (by that I mean intervals at least 10-15 min, not 3times a minute) under both vista and ubutnu (but somehow I think little less under ubuntu..). Could you tell more about:
>  rootflags=data=writeback, nobh, commit=100 - these fixxed my hdd from clicking every 5 secs ****note that I had to edit some other things along with these options to work, please dont add these without knowing what you are doing I dont want to be blamed*** and where did you get that?

What's more, vista makes my disk spin-up ~5 times, each about 1.5 seconds, every time I shut down the computer :/ Worry about damaging my tx1320us was one of those things made me move to ubuntu and feel safe(r)

I also, like you, have problems after recovering from this power saving state.. but I just get blank screen (no shifting or other crashes). I use Ctrl+Alt+BackSp to re-login or (better!) **EDIT** hit Ctrl+Alt+F8 and then back to Ctrl+Alt+F7 (I don't know why it works, but it works. I'm a noob).

**@stream303**

On Hardy htop shows, that both cores work properly. So I think that has been fixed (at least in Hardy) What does fb=false do exactly?

Has the fix to the cause shortening disk life been applied in Hardy or should I do it manually? (This is quite important.. since adding these "click" sounds from time to time makes me worry about my hdd).

To conclude, I still didn't manage to have my touchscreen working (webcam doesn't work with Skype beta, but at least I actually can receive video).

Well, that covers at lest some of my thoughts.. Happy hacking

**EDIT** I'm not using my ICQ now in case some1 wanted to contact me. I've subscribed to this thread.

**EDIT** I forgot, the attached is a message I got when executing sudo ./TouchKit

---

### Post by outferno on 2008-03-10
Hey guys, I still haven't gotten my laptop to save a egalax.cal successfully :(.

I even emailed the guys who make the driver - they sent me no reply.

Second, someone mentioned their computer freezing for about 2-5 seconds every few minutes - mine does that too, mostly noticeable in Firefox.  Anybody get this one figured out?  It's starting to irritate me.

---

### Post by avik on 2008-03-11
> **outferno said:**
> Hey guys, I still haven't gotten my laptop to save a egalax.cal successfully :(.

What's in your xorg.conf?  The breakthrough for me was setting the device to ```
/dev/usb/hiddev0
```.

---

### Post by mkarnicki on 2008-03-11
**@avik**
You are talking about Gutsy, right? Any one managed to make touchscreen work with Hardy?

---

### Post by outferno on 2008-03-11
> **avik said:**
> What's in your xorg.conf?  The breakthrough for me was setting the device to ```
/dev/hiddev0
```.

Hrm, when I checked out my xorg.conf it was set as this:

```

Section "InputDevice"
        Identifier "EETI"
        Driver          "egalax"
        Option          "Device"        "/dev/usb/hiddev0"
        Option          "Paramenters"   "/etc/egalax.cal"
        Option          "ScreenNo"      "0"
EndSection

```

Also, when I do an lsusb I get this:
```

Bus 002 Device 006: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen

```

Unfortunately, when I changed it - the touch screen no longer worked.  I've now switched it back.

---

### Post by avik on 2008-03-11
> **mkarnicki said:**
> **@avik**
You are talking about Gutsy, right? Any one managed to make touchscreen work with Hardy?

Yes, it's Gusty.

> **outferno said:**
> Hrm, when I checked out my xorg.conf it was set as this:

It was /dev/usb/hiddev0 (I was posting from another computer).  My bad.  I fixed it.

---

### Post by jjordan on 2008-03-12
I actually had to change my touchscreen device to:

Option "Device" "usbauto"

to get the touchscreen working.

-j

---

### Post by jjordan on 2008-03-12
Predius,

What video driver are you using?  Are you getting a full screen of video when rotated, no wide black bar on one side?

If I can get my rotation working properly, I'll write a script to rotate and juggle touchscreen calibration files.  I had to do something  similar for my Fujitsu P1510.

-j

---

### Post by waspbr on 2008-03-13
did you do that in gutsy or hardy?

As far as the rotation goes, no black bars, just awn manager need to be refreshed so it goes to the bottom of the page, the method I posted in page 66 should work, at least it worked with me.

---

### Post by jjordan on 2008-03-13
Gutsy

Yeah, I'm pretty familiar with RandR,  I saw today on Nvidia's site that rotation will not work with Twinview, so I will try that next.  Really sucks because I like to be able to just grab my laptop and go without having to restart X.  I'll post back if removing Twinview solves the rotation issue.  Guess I'll have to write a script to switch between dual monitor and rotation enabled.

Are you using the Nvidia driver or the NV driver?  

-j

---

### Post by jjordan on 2008-03-13
OK,

I disabled Twinview in my xorg.conf, removed all references to the external monitor and still no joy with rotation.

I have tried the:
Nvidia-glx
Nvidia-glx-legacy
Nvidia-glx-new
drivers.

I cannot get X to start with the NV driver, if someone has that working could they please post their xorg.conf file.

This is all in the interest of getting rid of the black bar on the left when I rotate my screen to the right.

-j

---

### Post by waspbr on 2008-03-13
As far as I recall it was NV(restricted drivers manager default), I switched to hardy a while back so I haven't tried to make the screen rotate since the touchscreen doesn't work yet.

---

### Post by jjordan on 2008-03-14
Here are the keycodes returned by XEV for the various keys on my tx1220us:

fn+f1 (?) = 245
fn+f2 (print) = 37
fn+f3 (www) = 178
fn+f4 (screen) = no keycode
fn+f5 (moon) = no keycode (acpi hibernate or suspend?)
fn+f6 (lock) = 146
fn+f7(bright-down) = 101
fn+f8(bright-up) = 212
fn+f9(play/pause) = 162
fn+f10(stop) = 164
fn+f11(rewind) = 144
fn+f12(fast forward) = 153
fn+pgup(pause) = 110
fn+pgdn(break) = 110 
fn+home(scroll) = 78
fn+end(numlk) = 77
fn+insert(prt sc) = 111
fn+delete(sys rq) = 111
WinKey = 115
MenuKey = 117

Bezel Buttons
rotate (two arrows) = No keycode
gear = No keycode
Undo (1 arrow in circle) = 205
DVD = 237
Rewind = 144
Play/Pause = 162
fast forward = 153
stop = 164
screen latched in slate position = No keycode

I'm working on scripts to control screen brightness so I figured I would go ahead and document keycodes.   Notice that the multimedia control keys on the Bezel return the same keycodes as the multimedia function keys.  I prefer to assign everything to functions keys above F20 as I find it more versatile than assigning them to the Xorg multimedia functions.  For example by assigning the Bezel fast-forward key to F35 in .Xmodmap I can use it as 'Next Song' in Amarok and 'Page Down' in FBreader.

-j

---

### Post by hojthojt on 2008-03-14
Hi,
jjordan:
I'm using Gutsy 7.10 on my tx1151ea. My screen rotates fine with the solution posted earlier in this thread. I'm using the Nvidia prop. drivers. As I have posted earlier, I still haven't found a good way of rotating the touch screen calibration together with the display without restarting X.

I have attached my xorg.conf in case you can find any hints there.

regards

---

### Post by jjordan on 2008-03-14
Thank you!

Your xorg provided the key to my figuring out the problem!  My xorg.conf was fine, it works even with Twinview enabled! 

The problem is .....

Drum roll please....

**KDE**

Hmmmm...  I started up Windowmaker and rotation worked fine.  I have KDE 4.0 installed on top of 3.5 so I will uninstall KDE 4.0 next even though that really screws up 3.5 and forces you to reinstall almost everything manually.  If all else fails, I guess I will load up Gnome and give it try.

As soon as I get rotation working reliably, I promise a script to take care of swapping pen configuration files around.

BTW, I have completed scripts for controlling the screen brightness if anyone is interested.

Thanks again.

-j

---

### Post by hojthojt on 2008-03-14
I'm glad it helped.

I'm curious how you plan on swapping the calibration files for the touch screen? I have have tried to find a solution myself, but the problem I ran into was that I can't get the touch screen driver to re-read the calibration file without restarting X.

What's your idea to solve this?

---

### Post by ccw127 on 2008-03-14
So here I am...

Admittedly I have not read all 70 pages, but from what I have seen (about half) my four question/comments have not surfaced.

I am using a daily build of hardy from two days ago; almost everything works. Still have to use ndiswrapper since bcm4328 is not yet supported. My USB mouse refuses to work now (I tried two different ones in all ports). Also my bluetooth is not showing up anymore (worked great with a daily from about a month ago.

Also, when using nvidia-glx-new, if I switch to a virtual console the screen is quite messed up (but mostly readable). Almost feels like a refresh rate issue.

Solutions/ areas to explore?

As a comment, my touch screen will register a tap as a mouse click but moving around does nothing. Ideas?

Chris

---

### Post by jjordan on 2008-03-14
I am still using Gutsy but I had a similar symptom.  You might try changing the line

Option "Device"    "/dev/usb/hiddev0" 

in your xorg.conf to:

Option "Device" "usbauto"

I believe that worked for me because I am using an external mouse and keyboard and depending on what order they loaded the HID device would be different.

- j

---

### Post by jjordan on 2008-03-14
:(

---

### Post by jjordan on 2008-03-14
The basic idea to reload the egalax cal file didnot work so I removed the script I wrote!

-j

---

### Post by jjordan on 2008-03-14
DOES NOT WORK, TouchKit DOES NOT automatically reload cal file!!!

---

### Post by akan01n on 2008-03-14
Hi, i have the touchscreen working, but it isnt working correctly, orientation left-right ok, but up-down is inverted, when i drag bottom-top the cursor goes top-bottom, the opposite direction.

I have HP tx1127cl, ubuntu 7.10

I have tried to insert Option "SwapY" "1" inside InputDevice xorg.conf, but it does nothing.

I have followed this tutorial: [http://ubuntuforums.org/showthread.php?t=442483&page=55](http://ubuntuforums.org/showthread.php?t=442483&page=55)

I have no more ideias what to do.

Some one help.. :(

---

### Post by jjordan on 2008-03-14
Did you run the calibration program TouchKit?

-j

---

### Post by akan01n on 2008-03-14
Actually i did, but i didnt realize that i have to press and not tap... its working now!

Thanks, jjordan

---

### Post by mkarnicki on 2008-03-15
**@ccw127**
As I have mentioned little before, I didn't manage to make my touchscreen working with latest egalax drivers (using tx1320us) with Hardy. I'm waiting for some good news about it over here, but I guess I'll hit no progress until Hardy's stable and more ppl try using it. Cheers.

---

### Post by akan01n on 2008-03-15
Hi, my contribution to this wonderful post!!

How to rotate the screen using the Front Panel Button (with blue color).

Im going to use the button under the DVD, that one with a circle rotating CCW.

But first you need to have the script working.

(this code is not mine, im quoting, but i dont remember the name of the guy, sorry)
> 
#!/bin/bash

STR=`xrandr --verbose | awk '/default/{print $5}'`

case "$STR" in
'normal')
xrandr -o left
;;
'left')
xrandr -o inverted
;;
'inverted')
xrandr -o right
;;
'right')
xrandr -o normal
;;
esac


Create a file called rotate inside your home, i use gvim, so fell free to use another text editor, and paste this code inside the rotate file

```

gvim ~/rotate

```

Done that, run this another cmd.

```

sudo chmod +x rotate

```

Ok, so far so good, now test your file type:

./rotate

and see if its working, if not, you have to add:

Option		"RandRRotation"

Inside your "Device" section, inside /etc/X11/xorg.conf

Restart X and test rotate script again.

Ok, everything working, if not maybe you are missing something, read other solutions on the forum, there is a lot.

Let's move on:

Now go to Terminal and run:

```

xev

```

This cmd captures the keys you press, so press the key under DVD.

You need to know the keycode of the button
Press the key
This information appears on the third line

My example:
state 0x0, keycode 205 (...................)

my model has a keycode 205

Ok, so now you can close "xev" clicking the X (the upper-right icon) on the window that has the square inside.

Now type this another cmd:

```
xmodmap -pk
```

And search for the number corresponding to your model (mine 205)

This is my line:
> 
205         0x1008ff4c (XF86LaunchC)


Ok, so far so good!

You will need the information inside the (), mine XF86LaunchC

Now type:

```
gconf-editor

```

(Obs.: this command does not have sudo, its only gconf-editor)

The editor will open go to:

> apps > metacity > keybinding_commands


There is a list like command_* (where * are numbers)

Pick the first one if empty, in my case:

> command_1

Right click, Edit key...

Write the path of the rotate script, ~/rotate does not work, must be the whole path

> /home/(your user)/rotate


Now go to:

> apps > metacity > global_keybindings (its in the same tree)

Look for the correspondent in my case:

> run_command_1


Right click, Edit key...

Paste the code from the keycode found with the xmodmap -pk command, the string inside ()

My example: 

> XF86LaunchC

Close gconf-editor (configuration editor)

and its done!

> 
Restart X and good rotating... heheh =)


You can create another rotate script inverting left and right positiong inside the script and assign inside gconf-editor the key with a modifier like <Alt> to make the same button rotate CW (normal) and CWW (alt + normal)

Bye! any problem post questions!

PS - Problems to solve, rotate screen does not work with other orientation, need to re-calibrate, if anyone know how to set 4 different calibrations, let me know!

---

### Post by waspbr on 2008-03-16
Nice work, having the extra buttons working is a real treat thanks...

It is a little disappointing that the touchscreen still doesn' t work in hardy, I really hope that it will work in the actual hardy release in April...

I tried posting a bug a launchpad ([https://bugs.launchpad.net/bugs/198911]("https://bugs.launchpad.net/bugs/198911"))

as well as posting here in the forums:
[http://ubuntuforums.org/showthread.php?t=716159&highlight=touchscreen]("http://ubuntuforums.org/showthread.php?t=716159&highlight=touchscreen")
 
but so far no solution has surfaced. perhaps we should contact EETI and ask if there's a fix for this. the more people request this the better.[http://www.eeti.com.tw/]("http://www.eeti.com.tw/")

---

### Post by waspbr on 2008-03-17
okay I was brainstorming about this whole touchkit rotation issue in gutsy. 

After rotating the desktop, the touchscreen calibration file remain in the old configuration, that is inverted by n time 90 degrees. 

If we then run touchkit, and we need to run it as root(since it has to replace a file at the /etc/ folder) and calibrate again, the screen then readjusts itself to the new orientation. In this process two things (may) occur

1- X restarts or reloads the egalax.cal file, perhaps touch kit runs 
[COLOR="Red"]UPDATE: the code actually opens a dialog that should reconfigure xorg, which is not quite what we want...so no cake.  [/COLOR]
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

this code is on the top of your xorg.conf file, which should automatically update xorg.

2- Touchkit reloads the egalax.cal file onto itself. 

here's what I find confusing, I am not sure if it is xorg or touchkit that is not being updated.One way to test this would be to replace the egalax.cal file with that of another orientation and run the code above. If that does the trick then problem solved(I won't have my computer with me for like a week...). 

If not then the key to solving this would be to take a look at the Touchkit code to see what exactly  the program does with the calibration data. However this is very much beyond my programing skils, it's a lot easier to talk...:lolflag:
[COLOR="Red"]The best option may still be to llook at what the Touchkit program does, but ..  yeah... I know[/COLOR]

---

### Post by jjordan on 2008-03-17
Ok, I have been working this quite a bit over the weekend.  I have tried both TouchKit and TKCal, the command line calibration utility.  As far as I can tell both have a routine within them that reinitilizes the driver with the new calibration file.  Unfortunately this is only triggered when you tap the screen at the end of the calibration process.

I have emailed EETI and asked them to give us a command line utiity to reload the calibration file or expose the routine through a command switch on TKCal.   No response as yet.

Part of the problem is that all we have is a binary file, no source code.  I did find source code for a very old egalax driver on the net but could not identify any routine within it to load the calibration file or even read a calibration file. 

Another thought I had was to kill the USB device or the HID device and then reload it.  That should force it to read the calibration file but I have not been able to make that work either.  

Is there a USB device driver programer in the house? 

I'll keep working this, I hope EETI responds, it would literally take like one line of code to expose the calibration-file-read routine to a command line switch.  Then we could just call TKCal -r or something and it would reload the calibration.
-j

---

### Post by ccw127 on 2008-03-17
As a follow up to my post on page 70, I got my usb working again by removing the blacklisting of ssb (how weird is that?); even with that removal, ndiswrapper is still working fine to get the bcm 4328 running. Still haven't gotten my bluetooth working again (even though it was working with an earlier build of hardy.

I have all but given up on touch for now. going to have to try and map the hardware buttons so i can page up and down for reading in tablet mode.

Chris

---

### Post by jjordan on 2008-03-17
There are 6 buttons on the bezel that we can access, the "DVD", the circle with an arrow (beside the DVD) and the the four media control buttons.

The keycode for the DVD button is 237
The keycode for circle-arrow button is 205

Create a file in your home directory called 
> .Xmodmap 
notice the . and that is a capital X.

You need two lines in the file to map the buttons (and two to comment):

> ! DVD button on bezel - page up
keycode 237 = Prior
! circle-arrow button on bezel - page down
keycode 205 = Next


That's it.
the exclamation point denotes a comment.

-j

---

### Post by jjordan on 2008-03-17
p.s. You can kick the mapping in by running the command

> xmodmap ~/.Xmodmap
 (really good for testing)

or restart Xwindows

> Ctrl+Alt+Bkspc


It will automatically be used on future startups.

-j

---

### Post by jjordan on 2008-03-17
As promised a couple of days ago here are some scripts to control screen brightness.  I use KDE so some of these directions are KDE specific.  I will try to annotate those parts. 

The first thing we need to do is make the brightness file writable:
> Open a terminal

We can make the file writable interactively by typing the command:
> sudo chmod 0666 /proc/acpi/video/UVGA/LCD/brightness

We can test that by typing:
> echo -n 39 > /proc/acpi/video/UVGA/LCD/brightness

Your screen should get noticeably dimmer. 

We don't want to leave it dim  so type in:
> echo -n 100 > /proc/acpi/video/UVGA/LCD/brightness

Every time we boot. Linux "fixes" the permissions for this file so we need a script to "unfix" them each time we boot.  There are several ways to do that but since we are messing with acpi we might as well do it there.  WARNING: this will make your computer less secure, some malicious code could brighten or dim your screen.  I think it is safer than suid and numbers out of range are ignored anyway so the worst some malicious code could do is set your screen brightness to maximum.

Start your favorite editor as root
> sudo kate
for me, probably:
> sudo gedit
for you.

Type the following lines of code in:
> # put this script in /etc/acpi/start.d and call it 75-bright.sh
# permissions should be 0755
chmod 0666 /proc/acpi/video/UVGA/LCD/brightness

There is really only one command there and it should look familiar.
Save the file to:
>  /etc/acpi/start.d/75-bright.sh

Now we need to correct the permissions, probably not really needed but we are going to give the same permissions as the other acpi scripts.
> sudo chmod 0755 /etc/acpi/start.d/75-bright.sh

We need two scripts, one to increase brightness and one to decrease (dim).

Close your editor, we don't want to have to worry about permissions later.

Open your editor from the menu.

**The first script is a KDE specific version, it will work in Gnome if you have the KDE libraries loaded along with the program kdialog.  A word of warning, if you are using Gnome and choose this script the first time you run it, it will be very slow because it will have to load the KDE libraries into memory.**

Copy and paste this code into your editor
> 
#! /bin/bash
CURRENT=$(grep "current:" /proc/acpi/video/UVGA/LCD/brightness |awk '{print $2}')
 
case "$CURRENT" in
 
100)
echo -n 80 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 90%" 3 &
;; 
80)
echo -n 71 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 80%" 3 &
;;
71)
echo -n 61 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 70%" 3 &
;; 
61)
echo -n 55 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 60%" 3 &
;; 
55)
echo -n 48 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 50%" 3 &
;; 
48)
echo -n 39 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 40%" 3 &
;; 
39)
echo -n 34 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 30%" 3 &
;; 
34)
echo -n 29 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 20%" 3 &
;; 
29)
echo -n 24 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 15%" 3 &
;; 
24)
echo -n 19 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 10% and will reset to 100% on next press" 3 &
;; 
1)
echo -n 100 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness at 100%" 3 &
;; 
*)
echo -n 100 > /proc/acpi/video/UVGA/LCD/brightness ;
;;
esac

Save the file as hp-dim.sh in your home directory or someplace else if you wish.

correct the permissions:
> Chmod 0777 ./hp-dim.sh

The nice thing about this version of the script is that it pops a little balloon up telling you approximately how bright you screen is.  Notice also that it goes back to 100% if you try to set it to 0%, this allows you to control the brightness with a single button, very handy in slate mode.

The second version of the script gives no feedback so it is environment independent:

> #!/bin/bash
 
CURRENT=$(grep "current:" /proc/acpi/video/UVGA/LCD/brightness |awk '{print $2}')
 
 
case "$CURRENT" in
 
100)
echo -n 80 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
80)
echo -n 71 > /proc/acpi/video/UVGA/LCD/brightness;
;;
71)
echo -n 61 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
61)
echo -n 55 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
55)
echo -n 48 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
48)
echo -n 39 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
39)
echo -n 34 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
34)
echo -n 29 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
29)
echo -n 24 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
24)
echo -n 19 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
1)
echo -n 100 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
*)
echo -n 100 > /proc/acpi/video/UVGA/LCD/brightness ;
;;
esac

don't forget to change the permissions.

The brighten scripts stay at 100% if you try to increase when you are already there.

All four scripts will put you at 100% if they find an undefined value in the file.

KDE version:
> #!/bin/bash
 
CURRENT=$(grep "current:" /proc/acpi/video/UVGA/LCD/brightness |awk '{print $2}')
 
 
case "$CURRENT" in
 
100)
echo -n 100 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness already set to 100%" 3 &
;; 
80)
echo -n 100 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 100%" 3 &
;;
71)
echo -n 80 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 90%" 3 &
;; 
61)
echo -n 71 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 80%" 3 &
;; 
55)
echo -n 61 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 70%" 3 &
;; 
48)
echo -n 55 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 60%" 3 &
;; 
39)
echo -n 48 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 50%" 3 &
;; 
39)
echo -n 48 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 40%" 3 &
;; 
34)
echo -n 39 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 30%" 3 &
;; 
29)
echo -n 34 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 20%" 3 &
;; 
24)
echo -n 29 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 15%" 3 &
;; 
19)
echo -n 24 > /proc/acpi/video/UVGA/LCD/brightness;
kdialog --passivepopup "Brightness set to 10%" 3 &
;; 
*)
echo -n 100 > /proc/acpi/video/UVGA/LCD/brightness ;
;;
esac

**save it as hp-brt.sh**

And here is the non-kde version:
> #!/bin/bash
 
CURRENT=$(grep "current:" /proc/acpi/video/UVGA/LCD/brightness |awk '{print $2}')
 
 
case "$CURRENT" in
 
100)
echo -n 100 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
80)
echo -n 100 > /proc/acpi/video/UVGA/LCD/brightness;
;;
71)
echo -n 80 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
61)
echo -n 71 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
55)
echo -n 61 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
48)
echo -n 55 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
39)
echo -n 48 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
39)
echo -n 48 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
34)
echo -n 39 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
29)
echo -n 34 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
24)
echo -n 29 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
19)
echo -n 24 > /proc/acpi/video/UVGA/LCD/brightness;
;; 
*)
echo -n 100 > /proc/acpi/video/UVGA/LCD/brightness ;
;;
esac

OK, you can assign those scripts to menu entries and use them from there.  This post is getting way too long so I will go into how to assign them to the Fn-F7 and Fn-F8 keys in the next post.

-j

---

### Post by jjordan on 2008-03-17
[SIZE="4"][B]Assigning the scripts to the Function Keys:
[/B][/SIZE]

The keycode for the FN-F7 key is 101 
The keycode for the FN-F8 key is 212
(this should be the same for all the versions of the tx1000) see akan01n's excellent post above for more in depth info or if your keyboard is different.

Create a .Xmodmap file in your home directory (or edit the one already there).
Add the lines:
> ! fn+f7(screen Dim) 
! assigned to dim screen in menu
keycode 101 = F27
! fn+f8(screen brighten)
!assigned to brighten screen in menu
keycode 212 = F28

At a prompt type:
> xmodmap ~/.Xmodmap  
This will install your key definitions.  (They will be loaded automatically the next time you start Xwindows.)

The remainder is KDE specific but Gnome should be pretty similar.  

Right click on the menu button and open the menu editor.  Add the scripts we created in the last post if you have not already done so.  Turn off launcher feedback, it is irritating and slows things down.  Choose the Dim entry. Near the bottom of the dialog box is the line:
Current shortcut key:  with a button over to the right.
Click the button (another dialog opens)
Click the mouse in the input area and Press the **FN key and the F7 key** 

F27 will appear in the input area.

Click OK and save your menu.

Give it a try press Fn+F7 a couple of times and your screen will dim.

Perform the same procedure for the Bright key.

I also assigned the DVD bezel button to the dim script so that I can control the brightness in slate mode.

-j

---

### Post by confuded92 on 2008-03-18
OK, So here is me with my tx1340ea., I haven't read the whole 72 page thread, but read most of it.

I am running Gutsy, latest. Here is what I have configured so far:

audio - no earphone jack

touchscreen - using TouchKit; slows down with compiz on after a few minutes of usage,                           .                   sometimes goes back to normal. Anyone know how to fix this?

camera - how do you test it? Skype doesn't recognize it...

wireless - using ndiswrapper... lame but wokrs

What worked out of the box: buttons (except the ones that don't work), card reader, bluetooth.

I am having trouble with the touchscreen using touchkit. It becomes slow after some time. Anyone know why? 

Also how do you test the camera?

Thanks.

---

### Post by jjordan on 2008-03-18
Confuded92

I have a tx1220us, my camera works fine with the Skype beta.  I can also use it in Kdetv.  Make sure you have the libpt-plugins-v4l2 package installed. 

There is a good HowTo on setting up sound to work with the headphone jack.

[http://ubuntuforums.org/showpost.php?p=3475485&postcount=235](http://ubuntuforums.org/showpost.php?p=3475485&postcount=235)

You still cannot control the headphone and speakers separately and the jacks on the port-replicator do not work.

TouchKit, look back a couple of pages, someone recommended some possible solutions.

Hopefully HP will do some ACPI work and get  all of our buttons working along with easy brightness control and better sound support.   Are you listening HP?

-j

---

### Post by avik on 2008-03-18
> **confuded92 said:**
> Also how do you test the camera?

I never tried it with Skype, but I knew it was working because of this.  I went to System->Preferences->Multimedia Systems Selector (you might have to add it in the Edit Menu dialog).  Go to the Video Tab, select v4l2 as the input and test it.

It also works with the program Cheese, though it never worked with Camorama, etc.

I'm on the 1320us.

---

### Post by hojthojt on 2008-03-18
Hi,
the webcamera works for me also. I have tried both with cheese and the "Multimedia Systems Selector".

I have not been able to get the built in microphone to work though.

I'm on a tx1151ea

regards

---

### Post by hojthojt on 2008-03-18
btw,
if someone stumble across this thread wondering if you dare to try to install Ubuntu on your tx1000  (I did just that a few weeks ago). You might actually be put off by the number of posts in this thread :-). Anyway, I collected my findings during my installation of Gutsy 7.10 and posted it in here:

[http://ubuntuforums.org/showpost.php?p=4452489&postcount=18]("http://ubuntuforums.org/showpost.php?p=4452489&postcount=18")

---

### Post by akan01n on 2008-03-18
> 
waspbr

sudo dpkg-reconfigure -phigh xserver-xorg


Ok, the cmd is great, but reset xorg.conf configuration :confused:

Apart from this problem i did a little test with a script i've made using this cmd

> 
sudo dpkg-reconfigure -phigh xserver-xorg


it worked flawlessly!! Everything automatic... rotate + set new calibration orientation!

But we need a better solution without reseting xorg.conf to original configuration, because when you run the cmd you think its everything fine, but when you reboot you see the mess.

---

### Post by jjordan on 2008-03-18
How about building a script and adding another line that copies your original xorg.conf back over the newly created one? 

> cp /etc/X11/xorg.conf.correct /etc/X11/xorg.conf

Then when you reboot, it should be OK.

(No, I have not tried it, I'm using KDE which has additional issues.)

-j

---

### Post by wanderprediger on 2008-03-18
Hey , i'm trying to get the wireless to work, but somehow it doesn't. i did everything like discribed with the ndiswrapper, there is already the wlan and with iwconfig it says:

> 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11a  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:270 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


but by iwlist scanning i get no results,no networks, though i should have 4-5 results .. i have an hp tx1220us by the way. any idea?
btw:and i git wiccd installed

---

### Post by confuded92 on 2008-03-19
> **avik said:**
>   I went to System->Preferences->Multimedia Systems Selector (you might have to add it in the Edit Menu dialog).  Go to the Video Tab, select v4l2 as the input and test it.


I don't have that in Gutsy. How do I get it or edit it in menu? Thanks.

EDIT: Also bluetooth is a bit funny. I can receive files, but when I try to connect to my phone it instantly sais can open ,MAC-address. folder...

---

### Post by waspbr on 2008-03-19
confuded92:

right click on the applications tab that should be in the top left corner of ur screen. this should give you the "edit menu" option

---

### Post by hojthojt on 2008-03-19
@confuded regarding bluetooth.

I also had issues like yours, but fixed it.

The first time I tried to connect to my Sony Ericsson K610i with bluetooth, 
the tx1000 found it when browsing for BlueTooth devices, but when connecting 
to it I got the following error message:

"OBEX [mac address] is not a valid location"

Googled and found a tip to install the following:

```
sudo apt-get install gnome-vfs-obexftp
```

Now it works to connect and browse files on the phone.
regards

---

### Post by mikedep333 on 2008-03-19
> **wanderprediger said:**
> Hey , i'm trying to get the wireless to work, but somehow it doesn't. i did everything like discribed with the ndiswrapper, there is already the wlan and with iwconfig it says:



but by iwlist scanning i get no results,no networks, though i should have 4-5 results .. i have an hp tx1220us by the way. any idea?
btw:and i git wiccd installed

This may sound stupid, but hit the physical wireless switch on the front of your computer, regardless of what color it is.

---

### Post by confuded92 on 2008-03-19
> **waspbr said:**
> confuded92:

right click on the applications tab that should be in the top left corner of ur screen. this should give you the "edit menu" option

Thanks! It works now in the test utility and cheese (the webcam). I just hope it works in skype...

hojthojt:

Thanks for the sugestion. I will obtain the package tomorow and test it :).

I cant find the fix about touch function using touchkit being slow (under compiz). Can someone please be kind and link it or point to a page? Thanks :).

Some one, on the previous page, had directed where suposibly the earphone jack would be fixed. I had folowed the instructions with no luck of getting my earphone jack to work. Does anyone know how to fix it or why doesnt it work? Its a bit weird... Maybe because there are 2 earphone jacks?

Anothere, rather unnecesary hardware, is the fingerprint reader. Has anyone got it to work? Do you guys have it on the older version?

Very anoying problem: turning on bluetooth and wifi together. There is one switch. How do i fully turn off bluetooth without wifi?

Also talking of wifi: i am using ndiswrapper (through the UI). Every time i reboot, hit the switch and it doesnt detect the adapter! (network utility) I have to delete the installed driver in the ndis UI and install it again... The switch doesnt work (wireless switch) sometimes... Weird... Any help would be apreciated!

Thats about it with problems :).
Many thanks.

P.S. Why does hardinfo close when i make another selection? Its a bit off topic, but does anyone know?

---

### Post by becxjo on 2008-03-20
Hello everybody. It's a long time that I follow this thread. Lastly I installed egalax driver on my HP1120us which is working under Gusty. I followed the instructions of the page 55 of this thread. I also blacklisted tkusb and usbtouchscreen. When I boot, at the begining the speed of the touchscreen is very well but after a while it becomes very sllow and malfunctions. Did you have a same problem before? Can you help me please?

---

### Post by waspbr on 2008-03-20
Hey, there was someone else with a problem like that... I am not sure if that was solved, I think that was somewhere in the 50-60s pages. 

It is curious that some laptops develop that problem and others don't, 

there are a few things you could try, I would try them myself but I don't have my lappy with me atm. 

change the  device line to:

```
Option "Device" "usbauto"
```

See if that works: 

You could also try removing the two blacklists and see if the touchscreen still works (you would have to reboot after making the changes) or we could ask **jjordan** if he blacklisted anything with this option on.

so the procedure would be like this

1 after modifying xorg, do

```
sudo  gedit /etc/modprobe.d/blacklist
 
```

now the end of your code should look like this

```
 blacklist tkusb
 blacklist usbtouchscreen
```


change it to 


```
#blacklist tkusb
#blacklist usbtouchscreen
```

reboot, does it work? yes, reboot again? if it works then yay, if not then alternate between them

```
 blacklist tkusb
 #blacklist usbtouchscreen
```

reboot

```
# blacklist tkusb
 blacklist usbtouchscreen
```

reboot

if there are no changes then just keep as it was without the comments "#" before the blacklists.

I can't vouch that is going to fix your problem, but at least it is something, otherwise you can just wait for  **jjordan** to respond

---

### Post by confuded92 on 2008-03-20
My camera had just stopped working. It was before. I went to the multimedia selector and tried testing it, but it just gave me an error saying it "failed to construct pipeline". It's set to v4l2 usb 2.0... Thanks!

---

### Post by jjordan on 2008-03-20
I blacklisted both tkusb and usbtouchscreen.

I think the reason usbauto works better for me is because I have an external mouse and keyboard connected which throws off the HID device number.

-j

---

### Post by waspbr on 2008-03-20
cheers buddy

So confuded, just try out the changing your xorg without changing the blacklist file.


On a different subject, I stumbled upon this video on youtube 

[http://www.youtube.com/watch?v=4eqcW-A7yKc]("http://www.youtube.com/watch?v=4eqcW-A7yKc")

This guy uses mandriva and well he's able to rotate his touchscreen and all...

---

### Post by RaZoR1394 on 2008-03-20
Has anyone tried BIOS F1E? It seems to have been released this month. Does it make the Ubuntu experience better? Do you think it would be dangerous to flash from a Windows live dvd?

---

### Post by becxjo on 2008-03-21
About the problem that the touchscreen after a while become slow; I remember that some posts here were about changes that happened in events associated to the touchscreen. For myself that event sometimes was event2 sometimes event3. Also I read before that evtouch has conflict with mouse driver configured by xorg. So I went to xorg.conf and commented out the section "configured mouse" in serverlayout. It seems that it worked and I enjoyed a long lasting of touchscreen response!

---

### Post by jjordan on 2008-03-21
**I  got a response from EETI.  There is a 2.0 version of the Egalax driver coming that supports rotation!**

-j

(late for work)

---

### Post by ghonz on 2008-03-21
Hey
I'm using a tx1138ea and I done the upgrade to hardy.
However I still cant get touchscreen, wireless, headphones, rotate screen or the remote control to work,
Anyone got any advice.
Jon

---

### Post by hojthojt on 2008-03-21
@ghonz:
I'm personally still on Gutsy, but you might find something useful at:
[https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1220ca](https://wiki.ubuntu.com/LaptopTestingTeam/HPPaviliontx1220ca)

magicfab seem to be using hardy on his tx1220.

---

### Post by outferno on 2008-03-21
I was thinking about something: my TouchKit says the utility version is 1.08.0925 but the version I downloaded from EETI is 1.08.1227 and my module version says 1.12 - can someone let me know what theirs says?  It shows this right when I start up TouchKit.  It still won't save an egalax.cal though :(

---

### Post by jjordan on 2008-03-22
Same here module Version 1.12
Utility Version 1.08.0925

I think they failed to update the numbers.

Are you running the utility as root, you cannot save a configuration if you don't.  Another problem people have had is just clicking on the crosses's, you have to press and hold until it jumps to the next location.  Follow the instructions on the blue screen.

> sudo ./TouchKit

2.0 is in Beta and supports rotation, no file swapping, required.

-j

---

### Post by outferno on 2008-03-22
I followed the directions and I also ran it as root.  It just doesn't save the file for some odd reason.  I'm not even sure why.

---

### Post by jjordan on 2008-03-22
Waspbr,

I am beta testing the 2.0 driver but I am having one frustrating problem.  Every time I touch one area of the screen, lift the pen and then touch another area I get a drag instead of discrete taps.  This is driving me crazy because it makes it completely unusable.  I dropped back to the 1.12 version and I get the same thing.  You can see what I am talking about very easily by opening a paint program and writing some letters with the pen.  I get a line connecting each letter together, it seems that the screen cannot  detect the pen being picked up.

-j

---

### Post by jjordan on 2008-03-22
Outferno,

What location for the cal file do you have set in your xorg.conf?

-j

---

### Post by RaZoR1394 on 2008-03-22
> **jjordan said:**
> Waspbr,

I am beta testing the 2.0 driver but I am having one frustrating problem.  Every time I touch one area of the screen, lift the pen and then touch another area I get a drag instead of discrete taps.  This is driving me crazy because it makes it completely unusable.  I dropped back to the 1.12 version and I get the same thing.  You can see what I am talking about very easily by opening a paint program and writing some letters with the pen.  I get a line connecting each letter together, it seems that the screen cannot  detect the pen being picked up.

-j

Hello!

May I ask how you become a beta tester of the experimental Touchkit driver?

---

### Post by waspbr on 2008-03-22
Jjordan, 

Razor may remember this from the first 5 pages of the thread, a dude named v.cecchetto  had been tweaking with an older version of the touchscreen driver for xorg 7.2 , he refered to this website, 
[http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html#config%22]("http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html#config%22")

The advanced configuration section may help but I am not sure what you are dealing with, do you still have the Touchkit software to configure the touchscreen?

This may have to do with some timer, from what you are saying the screen is able to register a touch  but is not able to turn i t off, so it does not seem to switch from "touch" to "untouch" after a determined time, may be the timer is wrongly set or something else. 

since you said it  the previous version of the driver also presented the same problem after that, then I   would figure that the problem is with the configuration software (TouchKit) and not the driver, some of the settings may be wrong.

---

### Post by jjordan on 2008-03-22
I sent them an email asking them to help us out getting rotation working and they wrote back asking if I wanted to test 2.0.

-j

---

### Post by jjordan on 2008-03-22
I agree that it is a timing issue of some kind.  Perhaps I need to do a fresh install and try Gnome.  There is some weird interaction between KDE and the xorg.conf that can cause some really strange things to happen.  I am really getting frustrated with Kubuntu. I think they disabled screen rotation in the the last Kwin build, even my Fujitsu P1510 has stopped rotating properly and it worked perfectly before I updated a few days ago.

-j

---

### Post by avik on 2008-03-22
> **waspbr said:**
> On a different subject, I stumbled upon this video on youtube 

[http://www.youtube.com/watch?v=4eqcW-A7yKc]("http://www.youtube.com/watch?v=4eqcW-A7yKc")

This guy uses mandriva and well he's able to rotate his touchscreen and all...


[He's using Metisse, not Compiz.]("http://www.mandriva.com/archives/en/projects/metisse.html")  It's the window manager associated with Mandriva, and it can rotate the windows.  You'll notice that only the windows rotated, not the panels, etc.

[Here's another video.]("http://www.youtube.com/watch?v=BPdn4DBTB00&feature=related")

---

### Post by meustrus on 2008-03-23
I know there's a thread to the conversation here, and I'll try to pick it up before saying my peace with this: The screen rotation "feature" in Windows pisses me off, mostly because I can't configure it.  I would prefer just to use the panel button to change the screen rotation when I feel like it, because a lot of things will get screwed up by switching the aspect ratio.  So far the "feature" has killed any usefulness I had for converting the computer into slate mode.

Anyway...with a tx1420us, which seems to be the top of this line, the Ubuntu live CD does not properly boot.  I think it has to do with the Geforce Go card.  When it finishes with the loading screen with the progress bar, the screen turns pretty colors with scanlines and flashes different pretty colors until it gradually fades to black.  I've tried this with both x86 and x64 7.10 install disks as well as x86 7.04.  I've been able to get Ubuntu working (thankfully) using the 8.04 beta disk, which still goes into rainbow mode for a bit but manages to start the Ubuntu desktop GUI after a few seconds.  I just wanted to mention this in case somebody knew more about it than I.  It was more of an issue before I was able to get a Hardy disk.  The entire situation has been a bit taxing because I needed to get to GParted to cut down the NTFS partition in order to create partitions for Linux and OSX86 (which will take a miracle to get working), as well as a common fat32 data partition.  If only Windows had something as useful as GParted, but no, that OS is just too complicated for me.

---

### Post by waspbr on 2008-03-23
In all due fairness vista's partition manager works better than it the XP version did, at least you can resize stuff now, however you have to disable the page files, and it takes ages if it does not hang. 

Windouze bashing aside, gutsy live CDs should run if you include the term "noapic" (no quote marks) into the command line, (press F6 in the LiveCD menu screen).

Other then that the hardy liveCD should work fine, Gparted should work fine as well.

here's a few summary posts:

[http://ubuntuforums.org/showpost.php?p=4413930&postcount=652]("http://ubuntuforums.org/showpost.php?p=4413930&postcount=652")

[http://ubuntuforums.org/showpost.php?p=4452489&postcount=18]("http://ubuntuforums.org/showpost.php?p=4452489&postcount=18")

why you wanna install OSX is very much beyond me, but hey you go do your thing. 

hope this helps

---

### Post by outferno on 2008-03-23
> **jjordan said:**
> Outferno,

What location for the cal file do you have set in your xorg.conf?

-j

Hello,

This is what I have:

```
Option          "Paramenters"   "/etc/egalax.cal"
```

---

### Post by phattyacid on 2008-03-24
> **outferno said:**
> Hello,

This is what I have:

```
Option          "Paramenters"   "/etc/egalax.cal"
```

maybe because Parameters is spelled wrong?

---

### Post by waspbr on 2008-03-24
:lolflag:

---

### Post by outferno on 2008-03-24
> **phattyacid said:**
> maybe because Parameters is spelled wrong?

Holy crap, lol, good eye.  I feel so dumb now. :lolflag:

---

### Post by georgew77 on 2008-03-24
Hi new ubuntu user with a tx1100 (tx1138ea) and got the wireless setup as per the thread, although it took a bit of frigging to get it going again after a reboot.

But, I tried the sound as per post 235, seemed to go ok(ish) I couldnt find po-debconf or quilt on synaptic anywhere, the other three I already had install.

Anyway I did the ./configure make and make install which seemed to go without a hitch, added the line as per instruction and rebooted.

Now the mute light on the laptop is orange permanently, when I press it it stays orange but brings up, the volume window in the middle of the screen, and appears to mute un-mute on that, also the increase/decrease buttons work but I have no sound :|

Any tips on how to proceed would be gratefully received.

G.

---

### Post by waspbr on 2008-03-25
First of all, did you ever get around installing quilt and po-debconf? I am on gutsy too and I can find them on synaptic. perhaps you need to enable some repositories.

so open synaptic, got to Settings => Repositories

You should see a bunch of boxes under the ubuntu software tab, I have enabled them all, then go to the third party software and enable them too... This should broaden your search

search for quilt and po-debconf again and then you may wanna repeat the process, make sure you follow exactly what sauron's tutorial says, specially the last bit that has to do with the fix because of the kernel change. 

let us know how it goes, I am not sure how new you are so if there' s something you didn't understand don't hesitate to ask

you can get 'su' (root/admin) privileges by entering the following command



```
sudo su
```


su alone doesn't seem to work anymore

good luck

---

### Post by georgew77 on 2008-03-25
Thanks, im very new but understand a bit of what im supposed to do, installed the quilt and po-debconf by checking the boxes on synaptic menus and did it all again and now the sound works :)

On a second point, it seems like it forgets my WPA wireless key every reboot, when it first boots it is not connected to the web but the "sudo iwlist scanning" works dandy.  When I go in to system->administration->network and re-enter the key it connects instantly.

On a third sometimes it doesnt shut down clean, the screen gets a funny white expanding border and basically the machine is frozen and needs a hard popo, is that a known problem?

G.

---

### Post by waspbr on 2008-03-25
Glad to hear your sound works now, get yourself a nice and cold beer and celebrate. 

wish I could help ya with the whole WPA thing but it is really not my area of expertise, ie, never had a problem with it since at home I have WEP and at uni I have dynamic WEP, so no cake there.

As for the funky screen when u turn off, maybe a different boot parameter may solve it, it seems to very  with respect to the different version of this computer series. 

One thing you should do though is update your bios, that may help

---

### Post by outferno on 2008-03-25
After getting almost everything working - I ran into a new problem.  I thought my sound was fine but my headphone jacks don't work.  I checked the post by Sauronsmatrix here:

[http://ubuntuforums.org/showpost.php?p=3475485&postcount=235](http://ubuntuforums.org/showpost.php?p=3475485&postcount=235)

I followed every step, but no sound from the front jacks.  :(

Can anybody help me? :)

---

### Post by mkarnicki on 2008-03-25
Hardy makes the sound pain-in-the-*** go away, that's for sure, including the headphone jack. However, I can't help with gutsy, as I've already upgraded. (I hope in 30 days we'll finally start crunching on the hardy's problems, eg touchscreen problems revisited).

---

### Post by ir0nman on 2008-03-26
I've got the 2.0 beta driver installed as well, and everything loads, but my calibration utility crashes mid way through the calibration most times, and I'm having a weird issue where I can't drag anything, but I can make selection boxes everytime I drag lol. I'm going to report these to egalax and see what they say, but was wondering if anyone else was getting this.
Thanks,
Rick

Oh yeah, ROTATION WORKS NOW :popcorn:

---

### Post by mkarnicki on 2008-03-26
Rick, you're on gutsy or hardy? // should this topic concern only gutsy, please let me know. I hope in 30 days I won't have to ask this question again ;) Or you guys configuring your gutsy to stay with it longer?

---

### Post by outferno on 2008-03-26
> **waspbr said:**
> First of all, did you ever get around installing quilt and po-debconf? I am on gutsy too and I can find them on synaptic. perhaps you need to enable some repositories.

so open synaptic, got to Settings => Repositories

You should see a bunch of boxes under the ubuntu software tab, I have enabled them all, then go to the third party software and enable them too... This should broaden your search

search for quilt and po-debconf again and then you may wanna repeat the process, make sure you follow exactly what sauron's tutorial says, specially the last bit that has to do with the fix because of the kernel change. 

let us know how it goes, I am not sure how new you are so if there' s something you didn't understand don't hesitate to ask

you can get 'su' (root/admin) privileges by entering the following command



```
sudo su
```


su alone doesn't seem to work anymore

good luck

Hey waspbr, did you try doing a ```
sudo passwd
```?  That will change the password for the root account and you should be able to use the "su" command.  I've been able to use my root account since doing "sudo passwd"

:)

---

### Post by ir0nman on 2008-03-26
I'm on Hardy, egalax is coming out with a new 2.0 version on their driver that also supports rotation, but it's still got some bugs it seems.There is hope on the horizon I can see though lol.
-Rick

---

### Post by CyberLeader on 2008-03-26
Hello all, new poster here... I'm using hardy beta 64 on a tx1250ea, it's been a lot less hassle than gusty was to get everything running, it's just a real shame that the touchkit driver doesn't work for hardy yet :( - other than that, everything else works fine.

I'm still having this weird issue where the screen goes funny with vertical blue lines and distortions when i close the screen and open it again. It will go back to normal if i swap out of gdm and back in using ctrl+alt+f1, ctrl+alt+f7. anyone have any idea what this is about, it didn't start till i installed hardy and i'm slightly worried that it's screwing up my graphics card or something. btw i'm using nvidia proprietary driver, installed via restricted drivers manager.

I think a few other users here might still be having temperature issues like I was, i was regularly getting cpu temp reading of around 80 degrees and the fan was very noisy, even when not doing anything! I think i've finally sorted this by adding a few lines to /etc/modules, from the instructions in this thread: [http://www.ubuntu-forum.com/showthread.php?t=539365]("http://www.ubuntu-forum.com/showthread.php?t=539365") . Now, the temp idles around 50-60 degrees, still not great, but at least i don't have to worry about being scalded anymore! :lolflag:

Thanks to everyone who has contributed to this thread, Ubuntu serves my needs very well and i don't miss vista!

---

### Post by waspbr on 2008-03-27
@ outferno : cheers buddy

@ the dude above: The overheating seems to show a problem with the CPU scaling, some other people have complained about it in other systems :

[http://ubuntuforums.org/showthread.php?p=4594126#post4594126]("http://ubuntuforums.org/showthread.php?p=4594126#post4594126")

So what needs to be done is to figure out what frequency the CPU is running and scale it back when/if needed, I haven't had the time to look into this but I will once my schedule clears up

---

### Post by simplyw00x on 2008-03-27
> **waspbr said:**
> 
@ the dude above: The overheating seems to show a problem with the CPU scaling, some other people have complained about it in other systems :

Nope, the overheating is caused by the complete and fundamental lack of C-states (which should exist on our processor) because HP couldn't be arsed to write such support into the bios. Forcing cpufreq to powersave doesn't prevent the temperature going above 60.

Anyone feel like sending me the EETI 2.0 driver? I'm on hardy and no touchscreen makes me a sad panda :(

---

### Post by CyberLeader on 2008-03-27
all i know is that since i added those modules, the running temp drops by about 20c, it seems like the frequency scaling governor was set to max performance by default when on ac power, but now it is set to 'on demand' by default.

Any word on when the new touchkit driver will be available, is it worth trying the beta driver cos people seem to he having issues with it. it's gonna be fun to play with the touchscreen again, especially now that rotation is supported and the tablet isn't too hot to hold!

---

### Post by waspbr on 2008-03-27
my GPU temperature worries me, it is always at 80 and sometimes goes close to 90... not good, the CPU however stays in the 50-60 zone most of the time going to a little over 70 when in heavy duty... not great :(

---

### Post by confuded92 on 2008-03-27
Where do you guys are getting all this temperature from? Are you using any 3D desktop animation like compiz?

Ubuntu is acting weird at times (Gutsy). After some time: 


[LIST]
[*]USB's stop working, no flash drives are recognized nor external HDD's
[/LIST]
[LIST]
[*]Touch Screen using TouchKit becomes slow (still can't solve it)
[/LIST]
[LIST]
[*]Wireless switch doesnt work
[/LIST]

All of the above require a reboot and it works for some time again. I suspect these problems might be because of the compiz 3D desktop or the chipset.

The web cam works at random! Once its ok even in Skype. I reboot and it cant cunstruct the pipeline! Is this the compiz's fault?

Audio jack isnt working obviously jet. Can't we use Jack to route the speakers so the audio jack (a newb of a suggestion).

Thank you. 

P.S. I am on Gutsy. What is hardy anyway? Anyone can point to where to look for the ubuntu types? Thanks.

---

### Post by waspbr on 2008-03-28
yeah I am using compiz, but I reckon this is not the problem, the computer runs considerably cooler when on battery power but quite hot when on AC . Strangely enough I get the impression that windows runs a little cooler... get back to you on that.

Hardy is the newest version of ubuntu, Hardy heron to be precise,  it is a lot more friendly to this PC then gutsy, except for the touch screen, but that should be fixed with the new egalax drivers that are coming out. So far there haven't been any irq related problem in hardy  at least on my part, so your problems should disappear in hardy (aside from the touch screen)

But, (there's always a but) Hardy is a month away from becoming stable, it is still beta, although it runs pretty smoothly so far. If you want to be on the safe side wait for its release on the 24 of april and try is out.

UPDATE: the cpu scaling is working well for me, now that it is set on "on demand"the temperature has remained stable around 50 degrees, dunno if the gpu temperature is right tho, 82 seems a little hight to me

---

### Post by hojthojt on 2008-03-28
Hi,
thanks to CyberLeader for your tip regarding the temp problem.

Before making the changes to /etc/modules the CPU temp on my tx1151ea was around 80 deg. when connected to power and doing nothing (both processors running between 1-3%).

When checking the CPU frequency settings (with cpufreq-info) it said that the current policy was "ondemand" and that the current CPU frequency was 2.00 GHz (from the available frequency steps: 2.00 GHz, 1.80 GHz, 1.60 GHz, 800 MHz).

After applying the changes to /etc/modules the CPU temp on my tx1151ea was around 50 deg. when connected to power and doing nothing.

Now when checking the CPU frequency settings it says that the current policy still is "ondemand" but that the current CPU frequency now is 800 MHz.

Now the big question, will the frequency scaling work if I put some pressure on the CPU?
I started a HD movie in Totem which push both CPU:s up (averaging around 40 %). 

cpufreq-info now tells me that the current cpu frequency is correctly scaled up to 2.00 GHz. YES! After watching the movie for about 10 minutes, the CPU temp is up to 79 deg.
When stopping the movie, the frequency is immediately switched down to 800 MHz and the temp quickly goes down again :-)

My GPU temp is around 82 deg. when idle and around 103 deg. when watching the movie (and that doesn't change because of the /etc/module fix).

regards
HojtHojt

PS 
The CPU temperature can be monitored with the KTemperature application.
The GPU temperature can be monitored with the nvidia-settings application.
The CPU frequency control settings can be checked by running cpufreq-info at the command prompt..

---

### Post by waspbr on 2008-03-29
if ya want you can get yourself applets for all that.
[B]
Temperature applet[/B]

 if you are in gnome just go to synaptic and search for

```
sensors-applet
```

then go to one of your panels, and right click,  select "add to Panel..."  and  then select "*Hardware Sensors Monitor*" .


**CPU frequency applet**

just right click in one of you panels again, "add to panel", and then select "*CPU frequency scaling monitor*". I did that twice so i got one applet for each core but they behave very much the same.

**Setup**

for scaling I have installed "*cpufreqd*" in synaptic, then I went to terminal, in root and did


```
cpufreqd -h
```

to get the help on that, the sine mode seemed to fit what I wanted so i did

```
cpufreqd -m 0
```


this should do it, the CPU frequency applets should show "on demand" when u pass the mouse over them.

---

### Post by waspbr on 2008-03-30
for the hardy beta testers out there, 


has the computer shutdown been "funky" lately? The screen starts fading from black to a white-noise static whitish-colorful appearance.The screen also goes nuts when, hardy turns it off, when u close the lid, or hibernate. when the screen comes back on and it is all funky, ctrl+alt+backspace seems to solve the problem (most of the time) so it has to do with our good old friend X.

any pointers about how to fix this?

how's he beta testing for the touchscreen drivers going?

---

### Post by confuded92 on 2008-03-30
Ah, so hardy is 8.04 LTS or what ever the version number is... I see... I am changing to hardy then :). 

Will i gave to reinstall Hardy as the stable release comes out or it will be available in updates?

I read a few pages agon that egalax has some beta drivers. Did anyone sucesfully use them on hardy?

Thanks.

confuded

---

### Post by waspbr on 2008-03-30
nope you won't have to install the stable version. The updates should be enough.

---

### Post by outferno on 2008-03-31
Hey guys, does anybody else get the intermittent freezing?  I really wanted to use Ubuntu 100% of the time, but I've had to go back to Vista for the purpose of having the front head phones working and for watching video or browsing the internet on my laptop.  It's almost unbearable to watch movies in Ubuntu since the video freezes for 10-30 seconds while the audio plays and then finally refreshes when the scene is almost over.  It's quite frustrating.  :(

In any case, I know that Ubuntu wasn't quite meant for our laptops in the first place, but it would have been nice to use Ubuntu 100% of the time without these strange quirks.

---

### Post by waspbr on 2008-03-31
nope, no freezing here, don't remember any freezing actually, perhaps you oughta try different players. Like any other coffee and green tea addict I use kaffeine. I think your problem is either player related or graphics drivers related, either way not nice.

that's weird tho, however there's hope in the horizon, sound and webcam work really well in hardy,  and tjhe video has been behaving well, except for the screen issue when shutting down.

---

### Post by mikedep333 on 2008-03-31
> **outferno said:**
> Hey guys, does anybody else get the intermittent freezing?  I really wanted to use Ubuntu 100% of the time, but I've had to go back to Vista for the purpose of having the front head phones working and for watching video or browsing the internet on my laptop.  It's almost unbearable to watch movies in Ubuntu since the video freezes for 10-30 seconds while the audio plays and then finally refreshes when the scene is almost over.  It's quite frustrating.  :(

In any case, I know that Ubuntu wasn't quite meant for our laptops in the first place, but it would have been nice to use Ubuntu 100% of the time without these strange quirks.

Yes, I am noticing this sometimes, although I don't use mine for media much so I can't say I've noticed that exactly.

---

### Post by mikedep333 on 2008-03-31
> **waspbr said:**
> for the hardy beta testers out there, 


has the computer shutdown been "funky" lately? The screen starts fading from black to a white-noise static whitish-colorful appearance.The screen also goes nuts when, hardy turns it off, when u close the lid, or hibernate. when the screen comes back on and it is all funky, ctrl+alt+backspace seems to solve the problem (most of the time) so it has to do with our good old friend X.

any pointers about how to fix this?

how's he beta testing for the touchscreen drivers going?

Yes, I am experiencing this too.

More info here:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/190526](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/190526)

---

### Post by Jeisson on 2008-04-02
I feel so thankful with all people talking in this post. With your help I am writing these words in Ubuntu 8.04 beta with a tx1410us.

I did the [ugly fix]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14") to get rid of the repetitive ugly hard disk sounds, and it worked successfully. The laptop is now very quiet. But, I close the lid or manually get the suspend/hibernate state and when the computer resumes, ugly hard drive sounds return again.

Is somebody experiencing this behavior? Is there any solution?

I want to thank all of you again so much
(Pd.: Pardon me if my English is not clear)

---

### Post by inXistant on 2008-04-02
> **Jeisson said:**
> I feel so thankful with all people talking in this post. With your help I am writing these words in Ubuntu 8.04 beta with a tx1410us.

I did the [ugly fix]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14") to get rid of the repetitive ugly hard disk sounds, and it worked successfully. The laptop is now very quiet. But, I close the lid or manually get the suspend/hibernate state and when the computer resumes, ugly hard drive sounds return again.

Is somebody experiencing this behavior? Is there any solution?

I want to thank all of you again so much
(Pd.: Pardon me if my English is not clear)

Hi there,

What you experience is normal; when the laptop is back from sleep, it resets the default value. You should write a script that will reset the power-management level to 255 every time you come out of sleep; I've been doing this, however, I'm on Fedora so I can't really help you as per the exact script as I'm not well aware of power-management in Ubuntu.

---

### Post by outferno on 2008-04-02
> **Jeisson said:**
> I feel so thankful with all people talking in this post. With your help I am writing these words in Ubuntu 8.04 beta with a tx1410us.

I did the [ugly fix]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14") to get rid of the repetitive ugly hard disk sounds, and it worked successfully. The laptop is now very quiet. But, I close the lid or manually get the suspend/hibernate state and when the computer resumes, ugly hard drive sounds return again.

Is somebody experiencing this behavior? Is there any solution?

I want to thank all of you again so much
(Pd.: Pardon me if my English is not clear)

hello Jeisson, you can use these two scripts that I wrote so I could change the hard drive parking without having to type out a lot of parameters.

You can cut and paste using your text editor of choice.  I used vi.

I created a file called "hdnopark.sh" and this is the code for it:
```
#!/bin/bash
sudo hdparm -B 254 /dev/sda
sudo hdparm -B 255 /dev/sda
echo "\nDrive will not park.  Use hdonbat.sh to turn back on."

```

The other file I created is called "hdonbat.sh"
```
#!/bin/bash
sudo hdparm -B 128 /dev/sda
echo "\nHD will now park once in a while."

```

In order to run these, just open a terminal and go to the path where the files are and type "sh hdnopark.sh" or "sh hdonbat.sh".

It's not really a fix, but more of a short cut.  I hope this helps out and saves you some time.

---

### Post by waspbr on 2008-04-02
Hey hardy users, 

Ive found this thread in the forums where other people were complaining about the high temperatures they have been experiencing in hardy. for those that have not been happy with it, it may be a good idea to check it out.

[http://ubuntuforums.org/showthread.php?t=736681]("http://ubuntuforums.org/showthread.php?t=736681")

in the third page of the thread this guy talks about some ' possible acpi related'problems", he figure that adding some parameters to the boot line may help, actually I think it has , I used the second parameter and my temperature now is at 45 degrees. So give you might wanna give it a shot and post your findings. I will leave a direct link to the guy's post below.

[http://ubuntuforums.org/showpost.php?p=4632914&postcount=28]("http://ubuntuforums.org/showpost.php?p=4632914&postcount=28")

go nuts with it.

---

### Post by outferno on 2008-04-02
> **waspbr said:**
> nope, no freezing here, don't remember any freezing actually, perhaps you oughta try different players. Like any other coffee and green tea addict I use kaffeine. I think your problem is either player related or graphics drivers related, either way not nice.

that's weird tho, however there's hope in the horizon, sound and webcam work really well in hardy,  and tjhe video has been behaving well, except for the screen issue when shutting down.

Hey waspbr, I figured it might be compiz fusion - so I turned off the rotating cube portion and it seems to not do it anymore... at least I haven't noticed.  Do you have compiz running?

---

### Post by Jeisson on 2008-04-02
Thanks inXistant and outferno for your affability.

I copied both scripts and put them into a folder under my $PATH scope. I tested the hdonpark.sh after a suspend state and it worked perfectly!. I was reading the man page of hdparm command, and I feel so impressed about your knowledge. Really I need to read and research a lot more to get enough domain in this OS :).

Reading the advice of inXistant. Can be this script executed automatically any time the system resumes from a suspend or hibernation state? How can I detect by software the system is resuming?

Thanks folks. Of course, it will save me a lot of time and worries. Hard disk is the most valuable piece of hardware, in my opinion :D.

---

### Post by ir0nman on 2008-04-04
Well I sent my bugs to egalax over a week ago, but they haven't gotten back to me at all. I don't know if they are working on them or ignoring them. They seem to take our needs into account though so hopefully they will have some new drivers soon. How are the other testers doing with the beta drivers? 
-Rick

---

### Post by outferno on 2008-04-05
> **waspbr said:**
> if ya want you can get yourself applets for all that.
[B]
Temperature applet[/B]

 if you are in gnome just go to synaptic and search for

```
sensors-applet
```

then go to one of your panels, and right click,  select "add to Panel..."  and  then select "*Hardware Sensors Monitor*" .


**CPU frequency applet**

just right click in one of you panels again, "add to panel", and then select "*CPU frequency scaling monitor*". I did that twice so i got one applet for each core but they behave very much the same.

**Setup**

for scaling I have installed "*cpufreqd*" in synaptic, then I went to terminal, in root and did


```
cpufreqd -h
```

to get the help on that, the sine mode seemed to fit what I wanted so i did

```
cpufreqd -m 0
```


this should do it, the CPU frequency applets should show "on demand" when u pass the mouse over them.

I'm curious about the cpu frequency stepping.  Is this for Hardy or for Gutsy?

Jeisson: no problem :)

---

### Post by waspbr on 2008-04-05
I did this in hardy, but as far as I know the same package is available in gutsy.

on a different subject, has anyone been experiencing usb problems lately? my front (right side) usb port has been on and off lately, i think since kernel 26-14.  or perhaps it is a little underpowered, I dunno, sometimes I plug in a USB drive in the and it works other times it doesn't. 

Sometimes I used a little generic usb mouse to do stuff, and it does not get recognized by hardy, even in the back usbs which do not have any issues.

I tried running, lsusb, but it did not register. anyone else experiencing that problem?

any tips?

---

### Post by MadMax08 on 2008-04-05
So, I think i've been through this thread pretty thoroughly, but i've been trying to figure out why my USB ports wont recognize any devices (mice, flash drives, external drives...anything) unless they are plugged in when i turn the computer on. I have a tx1110us.

Has anyone run into this/found a fix?

---

### Post by outferno on 2008-04-05
> **waspbr said:**
> I did this in hardy, but as far as I know the same package is available in gutsy.


I tried it out and both my cpu's shot up to maximum usage and my cpu temp stayed at 79 degrees C, so I decided to switch back.  Now both my cpu's are scaled down and the temp is 47 degrees C.  Hehe, I guess it doesn't work in Gutsy or I just don't know how to use the program.  When I rebooted with cpufreqd installed, it said my cpu's were not scalable.  *shrug*

---

### Post by Jeisson on 2008-04-06
> **waspbr said:**
> on a different subject, has anyone been experiencing usb problems lately? my front (right side) usb port has been on and off lately, i think since kernel 26-14.  or perhaps it is a little underpowered, I dunno, sometimes I plug in a USB drive in the and it works other times it doesn't. 

Sometimes I used a little generic usb mouse to do stuff, and it does not get recognized by hardy, even in the back usbs which do not have any issues.

I tried running, lsusb, but it did not register. anyone else experiencing that problem?

any tips?

I confirm. I am using Hardy beta and I have installed all updates aptitude found. About 4 days ago, all my USB ports stopped working. I looked for a solution and I found [this post of Gwasanaethau]("http://ubuntuforums.org/showpost.php?p=3862880&postcount=21"). I changed the value of MODULES from empty to this one:

```
#in /etc/default/acpi-support file, change MODULES="" to
MODULES="ehci_hcd"
```

After a restart, my USB memory drive revived, but my USB mouse did not. I thought it happened for other changes I made in that file, so I restored a backup but no effect. My USB mouse is not working in Hardy (in Windows does and other computers too). I searched in the ubuntuforums for some solution, and no luck yet.

I was wondering if the USB mouse dead was caused for any of all changes I did to the system. I thought in reinstalling Ubuntu (I prefer waiting until the next release in 18 days). Waspbr, if you did not changes in the system and your USB stopped working, then, changes by the updates were the cause, I think.

Thanks waspbr for asking that.

---

### Post by simplyw00x on 2008-04-06
I postulate that everyone with USB problems in hardy either uses ndiswrapper and is screwing around with ehci_hdc in /etc/rc.local (in which case restarting udev will re-enable hotplug, or is using dodgy kernel options (which have no place in Hardy IIRC).

---

### Post by Jeisson on 2008-04-06
> **simplyw00x said:**
> I postulate that everyone with USB problems in hardy either uses ndiswrapper and is screwing around with ehci_hdc in /etc/rc.local (in which case restarting udev will re-enable hotplug, or is using dodgy kernel options (which have no place in Hardy IIRC).

Great! I undid the changes I made to try get wireless working and the USB mouse is working again! :D Thanks, thanks a lot simplyw00x.

The steps to try wireless working are [documented here]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257"). So, steps I used to undo them were:
```

sudo ndiswrapper -r bcmwl5
sudo rmmod ndiswrapper
```

and I edited the /etc/rc.local file and removed these lines:
```

#rmmod ohci_hcd
#rmmod ssb
#rmmod ndiswrapper
#modprobe ndiswrapper
#modprobe ohci_hcd
```
I restarted the system and USB devices are working again. I did not modified /etc/modprobe.d/blacklist and /etc/modules files. But I think, I should restore them.

I have wicd because ndiswrapper trick never worked for me. But, I am far from a wireless network now, so I have not tested wicd neither :(.

Thanks again simplyw00x

---

### Post by waspbr on 2008-04-07
? I thought that ndiswrapper was supposed to make windows drivers compatible with ubuntul, does wicd do that? does it install the wireless card drivers too?

---

### Post by moob on 2008-04-07
Hi, 
i was "playing" with nvidia drivers for a display and its rotating funcion. I cautch two things what I can't solve. 
1] My left Control key go crazy. When press it I get dialog for printing (in FireFox). When i want to assign shortcut it tells that i'm pressing 0xb9 button.
2] When i leave NB without any action more than 2 hours (don't know how long) my cursor goes away. It is just hidden. I can use it, i can click... but i can't see where it is. Hebernation solve this problem but it happens again after that 2 hours.

Thank you.

For those who use gnome power manager brightness applet: [partial solution]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/137598") (search patch) 
or another solution is to SET following in Power Management Preferences: In "On Ac Power" tab uncheck "Dim display when idle" and in "On Battery Power" tab uncheck the same and "Dim display brightness by:" set to 0%.

---

### Post by ccw127 on 2008-04-07
Hello all,

I can't seem to get my bluetooth working. A couple of times it worked when installing different Hardy alpha's and daily builds. But with the current it will not. I am not using any boot parms. I am using ndiswrapper to get the wireless working (bcm4328... alas, no linux driver yet). The only modules that I have disabled is ssb and b43. I can even load the rfcomm mod. myself,  but it doesn't seem to have an effect.

Suggestions?

Chris

---

### Post by ghonz on 2008-04-08
Actually it doesn't i'm on hardy and still can't get the jacks to work. I've tried everything i've seen on here but no joy.
> **mkarnicki said:**
> Hardy makes the sound pain-in-the-*** go away, that's for sure, including the headphone jack. However, I can't help with gutsy, as I've already upgraded. (I hope in 30 days we'll finally start crunching on the hardy's problems, eg touchscreen problems revisited).

---

### Post by simplyw00x on 2008-04-08
> I am using ndiswrapper to get the wireless working
Restart udev. If that fixes it, then remove the lines in /etc/rc.local that do things to ohci_hcd

> Actually it doesn't i'm on hardy and still can't get the jacks to work. I've tried everything i've seen on here but no joy.
Tried *what* exactly? The alsa included with hardy should work, and if you've modified modprobe options or anything it won't.

---

### Post by inXistant on 2008-04-08
Hi Guys, 

Load of stuff usefull here but 80 pages... It starts to get really long to read it all. In addition, it covers 3 releases. Any of you had the opportunity to write down a complete installation procedure for Feisty and or Gusty -- I exclude hardy because it is still beta and the install not seems to be perfect yet? 

Cheers, 

X

---

### Post by waspbr on 2008-04-08
a summary  of what has been talked about can be found in these links

[http://ubuntuforums.org/showpost.php?p=4413930&postcount=652]("http://ubuntuforums.org/showpost.php?p=4413930&postcount=652")


[http://ubuntuforums.org/showpost.php?p=4452489&postcount=18](http://ubuntuforums.org/showpost.php?p=4452489&postcount=18)

---

### Post by ccw127 on 2008-04-09
Two things:

1. How to properly restart udev so I can try to get my bluetooth working?

More importantly...

2. _[COLOR="Red"]Heat[/COLOR]_. I know this was talked about a couple of times earlier in the thread, but I want to get some clarification (Cause I am crazy worried). 

At idle ==> My CPU is reported as ~45 degrees Celsius, and my GPU as between ~70 and ~75. My GPU is reported as high as 100 degrees Celsius when under moderate load, with the CPU up in the 60's. Now I just installed the Nvidia config tool the other day and under the heat tab it says that 130 degrees (seems crazy hot) is the slowdown speed and is unchangeable. Whats going on here? My case doesn't burn my hand, so is the reporting in Ubuntu just wrong?

I dont have vista anymore (and the restore partition is gone), so I can't check this under windows. Can someone who still has vista on their laptop tell me what temps are being reported? I just finished talking to online HP support and they are telling me normal temps should be: CPU --> 10 to 30 and GPU --> -20 to 60. Now I may have poor math skills (only a B in calc) but 100 degrees celcius, or even 70 to 75, is somewhat over the 60 max I was told for my GPU.

Please help... my love for linux is 'slightly' outweighed by my hatred for HP support and Fedex to get a toasted laptop repaired.

Chris

P.S. I have scoured all the online sources I could think of and have found no printed information on this topic.

---

### Post by simplyw00x on 2008-04-09
> 1. How to properly restart udev so I can try to get my bluetooth working?
sudo /etc/init.d/udev restart

It won't be permenant, but if thast doesn't fix bluetooth **immediately** then that's not your problem anyway.

---

### Post by mkarnicki on 2008-04-10
I found a funny thing. I'm a noob, so you guys probably know about that already.
When entering /dev/input/event2 and touching the screen I produce bytes of information that come up to console as ascii characters. Is this _that_ area where guys making drivers to tx1000 series touchscreen get data from? 

I haven't heard that touchscreen worked on Hardy yet (anyone?) and thought that.. possibly.. some nerdy geek could crack this data and write us a touchscreen driver! * laughs out loud * muahahah Cuz I'm not geek enough. But this looks kinda funny :lolflag:

Since I'm already here I'll ask one question. Did latest hardy updates brake your microphone's? I can skype no more.. and whenever I want, I have to switch to vista * cries out for help! *

**EDIT:** The funny part is.. that I found this file through... Audacious -> Preferences -> Plugins -> General -> EvDev-Plug eGalax INC USB TouchController hahahah *wicked*

**EDIT:** Yesterday I downloaded and reinstalled my Hardy (yeah yeah I know, 12 days left to official release) and.. My computer hung both on the "Install" mode and "Try wihtout changing anything ... " on 15% progress bar. In the installation mode it displayed header "Installing system" and "Detecing file systems" subtitle, when it hung. In "Try without..." mode it just hung with no clue, but at the same progress (but during bootup! not the installation in live mode itself). I'm using tx1320us, but thought it would be **troublesome** for new users trying out ubunutu. It worked when I added every boot option I recalled ("noapic nolapic noacpi doscsi irqfixup"). I might only guess it was acutally doscsi that made it work, but I'm a noob, so still I'm not sure. Nevertheless, this would make a potential new user go away after trying for the first time live CD.. not good. **By the way** does your built-in webcam work? I tried it with cheese, but no go. Do I have to install drivers?

---

### Post by waspbr on 2008-04-12
To make sure you webcam is the systems default in hardy go to: System => Preferences => Multimedia Systems Selector, you should be able to sort out the webcam on the video part.

If you can't find you Multimedia systems selector, right click on your ubuntu menu bar (by default on the upper left corner of the screen) , select the edit menu option, then go to  System => Preferences and activate your Multimedia Systems Selector.

At least that is what I did to sort out my webcam

---

### Post by mkarnicki on 2008-04-12
whops.. I thought I have replied. I thought my post didn't go to wrong thread :D But hey, waspr. After isntalling uvc drivers ([http://ubuntuforums.org/showthread.php?t=634393](http://ubuntuforums.org/showthread.php?t=634393) though I just knew the way from doing it before), it works like a charm. Multimedia systems selector also. Using v4l driver now. But the cheese app doean's work for me :_: and it looks so fun.. I wonder why. It looks like it has a wrong source (this camera test with coloured boxes), but it also doesn't have any preferences, so I don't know what I can do :D Nevertheless, webcam problem solved. Thanks.

---

### Post by parmendil on 2008-04-12
Hi you all!

First of all, great work! :)

Now, for something completely different, I have two problems with USB:
a.- When i unmount an external drive it doesn't mount back automatically when I plug it in back again.
b.- I'm getting a lot of "duplicates" directories on the /media/ directory. I mean

```
4 drwxr-xr-x 11 root root 4096 2008-04-12 13:31 .
4 drwxr-xr-x 22 root root 4096 2008-04-11 19:44 ..
0 lrwxrwxrwx  1 root root    6 2008-03-16 06:46 cdrom -> cdrom0
4 drwxr-xr-x  2 root root 4096 2008-03-16 06:46 cdrom0
4 drwx------  2 root root 4096 2008-04-07 16:50 disk
4 drwx------  2 root root 4096 2008-04-09 16:39 disk-1
4 -rw-r--r--  1 root root   94 2008-04-12 13:31 .hal-mtab
0 -rw-------  1 root root    0 2008-04-12 13:31 .hal-mtab-lock
4 drwx------  2 root root 4096 2008-04-11 18:25 LaCie160
4 drwx------  2 root root 4096 2008-04-12 01:10 LaCie160_
4 drwx------  2 root root 4096 2008-04-12 09:10 LaCie160__
4 drwx------  2 root root 4096 2008-04-12 13:28 LaCie160___
4 drwxrwxrwx  1 root root 4096 2008-04-11 12:05 LaCie160____
4 drwxr-xr-x  2 root root 4096 2008-03-20 22:05 sdd5
```

Does anybody has a clue about this? 

Btw, I was forgetting about this: a few days ago I noticed that the External USB drive is too slow on Ubuntu (and is not so slow in other machines/operative systems). Does anybody has got problems with this.

Tnx a lot.

F.

---

### Post by parmendil on 2008-04-12
Another thing that I forgot: Has anybody worked on the front headphone jacks? Don't work on my system.

F.

---

### Post by RaZoR1394 on 2008-04-12
> **parmendil said:**
> Another thing that I forgot: Has anybody worked on the front headphone jacks? Don't work on my system.

F.

It works with the Hardy beta.

---

### Post by parmendil on 2008-04-12
I'm on Hardy Beta, with all the system updated, and is not working. Perhaps I need to put it somehow on the defaults? How should it be?

---

### Post by mkarnicki on 2008-04-12
I have tried to mout, unmount, and insert again my Kingston pendrive. It mounted propely. (I'm on Hardy, 2.6.24-15).

Guys, I have a **problem**. About my frequency scaling problem few post forward.

---

### Post by mkarnicki on 2008-04-12
Make sure your Headphones are not muted in the audio mixer (volume control). Sorry if this sounds funny, but this may be the case. Headphone jack works for me.

**[COLOR="Red"]EDIT[/COLOR]**
Cr*p, I lost my post. Have to rewrite it again:

Someone before mentioned problems with [COLOR="Blue"]bluetooth.[/COLOR] I know it's a silly way, but I have a workaround (the shell command didn't work for me also). When I boot ubuntu and already see desktop, I turn the wi-fi switch on my laptop case to off and back on. Bluetooth notices me "Device has been made connectable" and then I can use my bluetooth.

I recently had problems with my CPU scaling. I was very sure it was nvidia drivers fault, but now I noticed this:
[B]-> when I unplug my laptop, and switch to battery mode I get 800MHz both cores
-> when I plug my laptop in, and charge battery, I get 2GHz both cores, even with low system load (<5% both cores)[/B]

I won't mention the fan kicking in while working on with 2GHz.. What can I do?

// by the way, anyone got "Cheesse" app working? I have webcam installed with r5u870 driver, but cheese fails on me

---

### Post by waspbr on 2008-04-13
hmm, by default cpu power is set on full when the pc is on AC so, maybe something in this post is helpfull for u.

[http://ubuntuforums.org/showpost.php?p=4609189&postcount=772]("http://ubuntuforums.org/showpost.php?p=4609189&postcount=772")

as for the camera, I was very pleased that it worked out of the box in hardy , at least in my tx1320us, i just did that procedure i suggested a few posts back and it worked, cheese works too, wait... there's a handsome devil on my lappy screen....

stuff other then that is a little out of my scope i am afraid.

get yourself a beer and drown your sorrows :D

---

### Post by mkarnicki on 2008-04-13
> **waspbr said:**
> hmm, by default cpu power is set on full when the pc is on AC so, maybe something in this post is helpfull for u.

[http://ubuntuforums.org/showpost.php?p=4609189&postcount=772]("http://ubuntuforums.org/showpost.php?p=4609189&postcount=772")

I'm not sure if you get what I mean. You don't need 2GHz scaling even if I'm plugged in. I know the system receives more power when plugged in, but the scaling should still work. I have now disabled nvidia drivers and my scaling works perfect (I'm plugged in now and I'm at 800MHz both cores)

> 
as for the camera, I was very pleased that it worked out of the box in hardy , at least in my tx1320us, i just did that procedure i suggested a few posts back and it worked, cheese works too, wait... there's a handsome devil on my lappy screen....

Heheheheh nice. Well.. I installed uvc drivers and my webcam works in skype for example, but in cheese I get this... testing screen (coloured squares, you might have even never seen them if your webcam worked ootb).

Thanks for your reply. I might be the only one having problems, I'm used to it ;) I'll just wait few days and then install nvidia drivers to check, if they don't break my CPU scaling. (I'm using powernowd for my AMD processor, it's ubuntu supported. I think I have tried cpufreqd, and it claimed my cpu didn't support cpu scaling hahaha (it does ;) ).

---

### Post by CyberLeader on 2008-04-14
Is anyone else having the annoying issue where the keyboard will randomly lock up  and the same key keeps repeating over and over again? it really gets in the way of my work sometimes. I think this is the same problem discussed in **[this]("http://ubuntuforums.org/showthread.php?t=599978")** thread, but the fixes don't work for me, so maybe not. Have any other tx users managed to fix this?

Oh yeah, i've also noticed that sometimes if i switch the wireless of by the hardware switch, it won't come back on again without a restart,,,

Man, i really can't wait to get the touchscreen back, I hope the new drivers are out soon :cry:

---

### Post by mkarnicki on 2008-04-14
I don't have any of those two problems. Considering the touchscreen, one of us managed to make it work under Hardy! *shhhhhhhhhhhhh whispers* He'll write the instructions as soon as he has time for us.

How can I brighten my webcam picture? It's very dark. I'm using uvc drivers.

---

### Post by farbird on 2008-04-14
> **mkarnicki said:**
> I don't have any of those two problems. Considering the touchscreen, one of us managed to make it work under Hardy! *shhhhhhhhhhhhh whispers* He'll write the instructions as soon as he has time for us.

How can I brighten my webcam picture? It's very dark. I'm using uvc drivers.

quickly now......share.....

---

### Post by mkarnicki on 2008-04-15
> 
[QUOTE] Originally Posted by mkarnicki
Hello,

Have you managed to get touchscreen to work on Hardy?

Cheers,
Michal

I have indeed. I will post how in a couple of days, I'm really busy atm. The key is getting hold of the beta drivers.
[/QUOTE]

I won't give his name away because I know you wouldn't let him live in peace, you ubuntu addicts! :lolflag: I'm waiting for this as much as you are. I just keep my fingers crossed he writes these instructions soon ^-^

By the way: I hope egalax drivers work better on ubuntu than on vista. Because, just for curiosity, I installed them yesterday on vista, and there where way less accurate then original vista touchscreen "Human interface" drivers.

You gutsy users, is that true touchscreen with egalax is more accurate then vista with vista drivers?

---

### Post by waspbr on 2008-04-15
you evil , evil person

yeah, the gutsy touchscreen uses up to 25 calibration points, which makes it a lot more accurate then vista's 4 points. so yeah, it is more accurate

so that you don't forget

you evil, evil person

---

### Post by ghonz on 2008-04-15
Hey hey again,
I'm running hardy on a tx1138ea I've tried the suggestions for Wireless and can't get wireless to work.
My headphone jacks don't work and my touchscreen doesn't work, does anyone have any advice at all?

---

### Post by mkarnicki on 2008-04-15
Right, and now I'm evil ! :lolflag: If it wasn't for me, we wouldn't even know that these drivers somehow work in hardy! If you guys tell me how to brighten my webcam, I'll concider giving away the mysterious man! Maybe he'll then tell us faster how to make this da*mn drivers to work :lolflag:

EDIT: by the way.. egalax drivers --> the calibration on vista make a very LOUD SPEAKER sound out of my laptop. This is seriously annoying if I want to touch all 25 points not waking up everybody in the flat. I hope doesn't work similar in hardy.. (or gutsy)

---

### Post by ccw127 on 2008-04-15
So um... dont know if this could be of some use to someone...

I installed evtouch via package manager and restarted (also I was playing with randr in my xorg.conf file)

Now, if I play with the touch screen it actually will move the cursor (dont get too excited though, the movement seems almost random).

The only reason I point this out is because it never even did that before (with the exact same configuration).

Chris

On another topic... any ideas about my heat issue from page 81 or 80? I am really worried that I am slowly destorying my laptop.

---

### Post by mkarnicki on 2008-04-16
OK - mine didn't even move. What did you modify in xorg.conf? (And now lame question: I never remember - where I can find it? :lolflag: )

---

### Post by Yellow Pasque on 2008-04-16
> **ghonz said:**
> Hey hey again,
I'm running hardy on a tx1138ea I've tried the suggestions for Wireless and can't get wireless to work.
My headphone jacks don't work and my touchscreen doesn't work, does anyone have any advice at all?
Try configuring your alsa-base file. Details here:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by ccw127 on 2008-04-16
mkarnicki:

What I did in xorg.conf should have had no effect what so ever. All I did was add *Option "RandRRotation" "On"* to the screen section so I could get my rotation working. The only other thing I did was to install (via Synaptic) the xserver-xorg-input-evtouch package.

xorg.conf is at /etc/X11/xorg.conf

Chris

---

### Post by parmendil on 2008-04-16
Thanks to that link I got the headphones jacks working on my tx1030la. 
The line on my alsa-base file:
```

options snd-hda-intel index=0 model=**3stack-dig** position_fix=0 single_cmd=0

```

note the "3stack-dig" as the model (before that I was using just "3-stack").

---

### Post by parmendil on 2008-04-16
I'm still dealing with some problems:
* Bluetooth, has anybody worked on this? Sometimes I saw the Bluetooth icon working, but I wasn't needing it yet. Today, when I need to connect to it I can't, the device apparently is gone.
* Automount for the USB drives. How can I don't connect the external drive before booting, I can't access to it. 

Thanks for the help!

F.

---

### Post by ccw127 on 2008-04-16
I am having a similar problem with my bluetooth, not sure what the solution might be. You could try restarting udev? It didn't work for me though.

The usb automount thing is weird. I think I had a similar problem at one point... try blacklisting ssb? I can't remember...

Chris

---

### Post by WildcatWhiz on 2008-04-17
Soooo. Anyone wanna give the scoop on touchscreen in Hardy? :)

---

### Post by hannibaal2 on 2008-04-18
I read almost most of the post   about my "tx1410us" but u guys are lucky; at least your laptop will load ubuntu, mine does not do it at all, after loading the Kernel then  checking all the devices, networks, cups, etc...from the live cd, my screen will lighten up in purple color, then pink, then white and my laptop will freeze. i have no other operating system on it now. so it is empty...

I have no idea what to do? any suggestion, please? :confused:
I cannot stand vista, I want a linux on my new laptop. help, help...

---

### Post by outferno on 2008-04-18
Hey guys, I just ran across something in Gutsy.  This is completely typical of what happens when you don't look in the most obvious of places.  I was wondering why  my head phones didn't work or why my head phone jacks didn't work - when all along, they did work.  All I had to do was right click the volume icon and click on "Open Volume Control Ctl+O" and then unmute the head phones.  

Now my dilemma: anybody know how to make the laptop volume controls work for the head phones and not the speakers?

---

### Post by Jeisson on 2008-04-18
> **hannibaal2 said:**
> I read almost most of the post   about my "tx1410us" but u guys are lucky; at least your laptop will load ubuntu, mine does not do it at all, after loading the Kernel then  checking all the devices, networks, cups, etc...from the live cd, my screen will lighten up in purple color, then pink, then white and my laptop will freeze. i have no other operating system on it now. so it is empty...

I have no idea what to do? any suggestion, please? :confused:
I cannot stand vista, I want a linux on my new laptop. help, help...

Second time I write this. Firefox is not the best browser to write messages (it crashed), and spell checking does not work in Opera :mad:

Don't use the Live CD in order to install Ubuntu. You should use the alternative CD and do a text mode installation. Then, you should change the kernel parameters in **/boot/grub/menu.lst** file. I am using the following parameters, suggered by others in this thread:

```
ro single **showopts noapic nolapic irqfixup acpi_irq_balance doscsi pci=nommconf**
```

You need to boot Ubuntu first to edit that file. So, you can change the boot parameteres temporary when you are choosing the operating system in the Grub menu. Press E (or F6?) in the menu and add the parameters. I believe, **noapic** is enough. After you modify the menu.lst file, the change will be permanent.

I hope this helps.
Best regards.

---

### Post by hannibaal2 on 2008-04-19
[/QUOTE]
Don't use the Live CD in order to install Ubuntu. You should use the alternative CD and do a text mode installation. Then, you should change the kernel parameters in **/boot/grub/menu.lst** file. I am using the following parameters, suggered by others in this thread:

```
ro single **showopts noapic nolapic irqfixup acpi_irq_balance doscsi pci=nommconf**
```

You need to boot Ubuntu first to edit that file. So, you can change the boot parameteres temporary when you are choosing the operating system in the Grub menu. Press E (or F6?) in the menu and add the parameters. I believe, **noapic** is enough. After you modify the menu.lst file, the change will be permanent.

I hope this helps.
Best regards.[/QUOTE]

thanks I will try it when the weekend is over, I will see then, but thanks again

---

### Post by waspbr on 2008-04-19
or you can try hardy instead which does not need any boot parameters.At this point I reckon the beta version is stable enough but if ya wanna be on the safe side the stable version is coming out next Thursday. It is more pavilion friendly then gutsy

---

### Post by mkarnicki on 2008-04-19
Hey **simplyw00x**, we can't wait no longer.. I'm sooo waiting for touchscreen to work on hardy. It's time you reveal the secret and do some magic. Please let us bring our touchscreens to life ! :biggrin:

---

### Post by CyberLeader on 2008-04-19
For anyone who cares, i've managed to get the microphone working again (they stopped when i installed hardy). I realised that the stereo mics on the lid weren't working but the mic jack on the front was if i plugged the headphones into that...

if i start the volume control  applet and hit Edit -> Preferences, and check 'Input Source', a tab shows up that lets me switch between the front jack or the lid mics... 

I don't even know why i'm so bothered by the microphones, i hardly even use them, It's just one of those things (like the touchscreen ;) that you really miss once it's gone!)

---

### Post by tarsius4 on 2008-04-20
> **outferno said:**
> Hey guys, does anybody else get the intermittent freezing?  I really wanted to use Ubuntu 100% of the time, but I've had to go back to Vista for the purpose of having the front head phones working and for watching video or browsing the internet on my laptop.  It's almost unbearable to watch movies in Ubuntu since the video freezes for 10-30 seconds while the audio plays and then finally refreshes when the scene is almost over.  It's quite frustrating.  :(

In any case, I know that Ubuntu wasn't quite meant for our laptops in the first place, but it would have been nice to use Ubuntu 100% of the time without these strange quirks.

This sounds EXACTLY the same as my experience with Ubuntu so far.  My tx1000 CTO is now about 13 months old and I used Vista exclusively for the first ~10 months, though on two separate occasions (both consisting of several long nights) I attempted to install 3 different versions of Ubuntu (Feisty, Feisty 64-bit, and Gutsy), but every install CD gave me the same issue:  the progress bar of the initial "kernel load" would freeze at 22%.  On the third thrust at installing, I reluctantly tried the alternate CD (my impression was that it would fail similarly given the fact that I couldn't get past 22% of the kernel load), but this time it loaded the setup.  I took a leap of faith here by backing up my data and completely formatting over Vista (Vista's partition resizing wasn't working).

Now enter Ubuntu.  Initially I was extremely satisfied and optimistic, but the little hiccups I had in the beginning weren't being resolved as I had thought they would be.  I brought various features to life thanks to this thread (I owe my entire Ubuntu install to this thread), like webcam, audio, wireless, etc.  However, my computer continued to (A) crash frequently (generally everything freezes, sometimes the mouse is left alive...[Ctrl-Alt-Backspace] and [Ctrl-Alt-Delete] both have no effect, so I must hold the power for 5 seconds to shutdown), (B) "stall" _all the time_ (when playing video clips, the video will often freeze for 5-10 seconds but the audio and "playback" continue... also experienced in other intensive tasks like playing a game, but stalls also occur less frequently when doing non-intensive tasks), (C) "keyboard stutter" (Whhhhen typingggg it lllllooks lllikkke thissss... but I've heard this is not exclusive to Ubuntu... some kind of xorg/gnome/compiz issue--but don't quote me on that).

So eventually I was fed up with the lack of stability and I installed a dual-boot of XP (which I'm currently using).  Like outferno, I REALLY want Ubuntu to work and I want to use it most of the timer, but I haven't found any combination of boot parameters that resolves my issues. [note: I saw that outferno experienced some improvements after deactivating the Compiz cube... I have yet to try that but I would gladly turn over all of the nice Compiz/Compiz Fusion features if that will give some amount of basic stability--not having nVidia support for other applications would be a deal-breaker though]  So now here is the meat of my post... I have identified some possible issues that might differentiate various tx1000-series owners--my suspicion is that there are some significant hardware differences (potentially different motherboard versions) that prevent us from arriving at a one-size-fits-all recipe for successful Ubuntu installation.

Here are some questions that I would like people to consider...  First, tell whether each point does or does not apply to you, then tell whether or not you are experiencing "stalls" and/or full crashes.

1) Crashes in Vista (Please be objective... turn down the MS/Vista hate)
First of all, Vista was very, very slow on my computer.  But even worse, applications crashed frequently.  Particularly Firefox.  I noticed a pattern of Firefox sucking up huge amounts of memory if I browsed many sites while it was running.  Even after I closed tabs and navigated away from sites, the memory would not be freed.  So with 1Gb of ram, it would typically reach about 200mb-300mb of memory use (even with tabs closed) and then it would crash.  But that was just the most common crash, as it would happen with other programs as well. On one occasion I had written a long email in Notepad++ without saving frequently and Notepad++ crashed.  I find this Vista instability very suspicious given the fact that the tx1000 was supposed to be one of the first laptops designed specifically for Vista.

2) I purchased my tx1000 *as soon as* it came on the market...LITERALLY
I believe this was my biggest mistake of all.  Not only did I pay quite a bit, but I *suspect* that I may have purchased a buggy early version of the tx1000 series.  This is a likely culprit for my Vista and Ubuntu woes. I bought it on March 10th, 2007, after canceling an order for a Gateway tablet.  The HP tablet was introduced just as I was getting fed up with my eternal wait for the Gateway order... when I saw the tx1000, I figured it would be nice to have the latest-and-greatest for a change, but I ended up paying a lot and _probably_ getting a buggy version.

3) I could not get very far with the regular install CD
It seems suspicious to me that some of us have been able to install with the ordinary Ubuntu CD while others must use the alternative CD.  That points to differences in hardware, but more critically, differences in very low-level hardware as opposed to high level components like hard drives and displays.  As I said before, my computer froze at 22% of the initial kernel load.  Did anyone else experience a freeze at 22%?  If not, did you experience consistent freezes as the kernel was loading?  Did your computer freeze after the kernel loaded but before the full live CD booted?

4) Intermittent "stalls"
This could actually be considered two things: general stalling where the PC is unusable for a period of 5-30 seconds or stalling of the video during playback.  I haven't seen many specific posts about this issue in the thread so far, so if you've been running into this, please report it to the thread (particularly the lurkers like me who have said nothing thus far).

5) Complete lock-ups/crashes
If you're still crashing... How are you crashing?  Like I said, the screen tends to freeze (with and without mouse support), but then I have no way to recover... I can't click and I can't restart using any keyboard combinations.  Also, sometimes the CPU graph GNOME applet (sorry, I can't remember the exact name) will continue to scroll, usually showing that my CPU is running 100%.  On other crashes, the meter freezes.

6) Xorg/GNOME crashes when minimizing Firefox
I remembered this one at the last minute, but that's because it happens infrequently.  Occaisonally when using Firefox, the instant I press the minimize button, Xorg and/or GNOME will crash and restart, taking me back to the login screen.  After I login, the applications that were previously running will be gone. From my perspective, this crash appears identical to pressing [Ctrl-Alt-Backspace]

Please post any similar experiences and/or other criteria that may differentiate our laptops.  Has anyone disassembled their computer to the point of locating some kind of version or revision number marking on the motherboard?  Perhaps that info alone would allow us to categorize and identify which install procedures are necessary for any given tx1000 series laptop.  Also, I am interested in picking through code to find out what condition is actually leading to my stalls and crashes...  does anyone have any good links to get me started (tools, tutorials, etc).

---

### Post by twistadias on 2008-04-20
Just upgraded to hardy LTS
I use this code to turn the monitor off when im downloading
```
xset dpms force off
```

The problem is when I wake up the screen, its all blurry and laggy. I have to restart X to use the laptop.

The laptop woke up fine in 7.10  . Anyone know how to fix this? 

Also im having with the front mic. its not on mute. When i try it in the sound recorder, all I hear is static

---

### Post by mkarnicki on 2008-04-20
Volume Control -> Edit -> Preferences -> check Input source, close window
in Volume Control (mixer) switch to Options tab and switch between your built-in mic and front panel (jack) mic.

---

### Post by outferno on 2008-04-20
> **tarsius4 said:**
> 
1) Crashes in Vista (Please be objective... turn down the MS/Vista hate)

2) I purchased my tx1000 *as soon as* it came on the market.

3) I could not get very far with the regular install CD.

4) Intermittent "stalls"

5) Complete lock-ups/crashes

6) Xorg/GNOME crashes when minimizing Firefox


Hello Tarsius, I'm glad to see (though rather unfortunate) that I'm not the only one suffering from issues.

To answer your questions.

1)  My computer runs Vista okay (for the record, I'm a systems admin and I mostly work with Windows machines, so I've heard it all from different people in the office and outside about Vista vs XP.  Bottom line, you're going to have to adapt to Vista some day, it's just ahead of it's time on resources and probably runs beautifully on a Quad Core w/ a premium graphics card.  I can some what attest this as I use a Core 2 Duo w/ a very high end graphics card, it runs just like XP did when it first came out, it has quirks here and there, but I'm adjusting).  I recently upgraded it to Service Pack 1.  I noticed zero differences using service pack 1.  This is likely due to the fact that my laptop is more of a learning tool than anything else.  I just use it for internet, movies, music, and the occasional multimedia manipulation (music).  I haven't experienced any crashes in Vista.  I do know that some things may run slow, but it seems to be very stable on my end.  I've also made it a point to grab all the latest HP drivers for Vista and to update the firmware religiously.  They recently updated the firmware for the motherboard just a few weeks ago.

2)  I purchased mine on sale some time in November or December.  I don't think it's faulty hardware that is causing this, I think it's just the fact that the tx1000z CTO may have unsupported drivers in Linux.

3)  I used the CD downloaded from the Ubuntu website.  At first I used the AMD64 version of Gutsy, but after being frustrated with finding compatible software for the 64bit version, I decided to just run the i386 version.  I was also able to resize the hard drive.  I think I had to do a Microsoft scandisk in order to let it fix itself for resizing, this is most likely due to the hard drives being cloned from images during assembly.

4)  I get the stalling a lot.  I even thought it may have been from CPU scaling, but it isn't.  Even after having the CPU run at 100% of it's capability, it still had the little stalls.  This is frustrating when trying to watch video, but surfing the web, it's just a nuisance.  Even after turning off Compiz Cube, it still had stalling.  I'm not sure if it has to do with Emerald being installed, but it seems to work at a tolerable level with random stalls every 5-10 minutes.

5)  For the lock ups, I haven't experienced one in a while.  I'm not sure what causes it, but I am unable to back out X and I also can't force a terminal (ctl + f1-6).  I too have to do a hard reset, but once it comes back, it doesn't seem to have any negative side affects from the reset, other than lost time.

6)  I can't say I've experienced the minimizing of FireFox crashing Gnome or X itself - but I have had a lot of issues just in FireFox.  I don't think this is because of FireFox though, I think it's due to the fact that there are intermittent stalls during use of Ubuntu and it just happens that FireFox is my most used application.

I think what I'm going to do from this point on is to wait for Hardy.  Hopefully these problems will be ironed out... or if not, I'll have to figure out what exact boot parameters are needed or required for it to run smoothly.  For the time being, I'm happy with dual booting Vista & Ubuntu, but I'd be much happier if everything just "worked" without the stalls.  So, for now, it's dual boot or I use my other PC's at home.

---

### Post by ramlak on 2008-04-20
Hi everybody

I'm happy user of tx1220

I was newbie at the beginning of this topic, but now sometimes i know what the system does, and where to look, when it doesn't :) (this is my first linux adventure :P and i like it so much, that, i'm switching completly to linux)

I'm using Gutsy, and not rushing Hardy (you know - i like my touchscreen:))

some issues that occures to me:

hibernate+suspend - ununtu hangs after hibernate, and doesn't wake up after suspend (yeah - it wakes up, but screen is blank) i recall someone made it work, after enormous ist of boot options, but i can't find it now....

sound, or rather microphones, or rather poor quality of recorded sound
i don't mean hiss (which is normal using build-in mic), but series of cracks through the recording. I guess it's hardware connected, because cracks occur even if i mute everything in alsamixer.
i'm using alsa 1.0.16 (i guess the newest), and recording was made using ardour2

thanks to all contributing to this topic. without your help i wouldn't be where i am:)

ps. and forgive me my english :P

---

### Post by twistadias on 2008-04-21
> **mkarnicki said:**
> Volume Control -> Edit -> Preferences -> check Input source, close window
in Volume Control (mixer) switch to Options tab and switch between your built-in mic and front panel (jack) mic.

I did what you mentioned above but all I hear is static

BTW im getting a white screen with lots of multicolored lines when i wake up from suspend. Does anyone else have this problem?

---

### Post by mkarnicki on 2008-04-21
Have you tried recording from both Front MIC and ATAPI MIC ?

I get those black'n'white stripes when I boot my OS for 1,5 ~ 2 seconds. They look ulgy, but thankfully it works (simplyw00x please help us with this touchscreen please please please).

---

### Post by twistadias on 2008-04-22
okay the atapi mic works, but nothing gets recorder with the sound recorder not even static. I can hear myself through the speakers though. 
I read in earlier posts that the front mic worked with hardy and thats why I upgraded. Is there any other way?

---

### Post by mkarnicki on 2008-04-22
I'm not sure, sorry. Both of my mic's work (built in and front) on Hardy. I still use some boot flags in grub, but many ppl say there's no need to, so I doubt it would help with the mic.. Maybe there's some1 more competent to help you. Guys?

---

### Post by ir0nman on 2008-04-22
Hey guys, I just got a new version of the beta driver from egalax, now it even has it's own install script. I'm going to install it now, and I'll try to get back to you guys tomorrow on how it's working.
-Rick

btw here are the new versions, so if yours are less you should email them to get updates, or pm me, and I can probably forward it on.

Driver version: 2.02.1615-32b-k26-x14
Module version: 2.01
Utilty version: 2.02.1610

---

### Post by simplyw00x on 2008-04-22
My (almost-complete) guide to installing the Hardy beta driver on Hardy, complete with (as-yet unfinished) evdev hotplug information, is here:

[http://moho.frihost.net/dta/?page_id=194](http://moho.frihost.net/dta/?page_id=194)

I've jumped ship to fedora now but I'll try and finish the guide (just had exams).

---

### Post by ir0nman on 2008-04-22
Cool, you'll have to let us know if you have any lock-ups with Fedora, It's probably not ubuntu specfic, but I had them in Gutsy, and after a couple months of not having them in Hardy I've started having them again. I'm sure a lot of us having these issues would like to hear your experiences. I've been considering fedora, and also suse, since they are working with AMD to get better power savings.
Thanks,
-Rick

---

### Post by ghonz on 2008-04-22
> **Temüjin said:**
> Try configuring your alsa-base file. Details here:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

hey hey, I tried this and for the first time my mute button is now light blue, however I have no more sound and when I try to open volume control I get
"No volume control GStreamer plugins and/or devices found."

Any advice?

---

### Post by mkarnicki on 2008-04-22
[deleted]

EDIT: I messed up my graphics after adding some lines to xorg.conf from simplyw00x'es tutorial, but I managed to recover.

---

### Post by CyberLeader on 2008-04-22
I think I've made some progress getting the evtouch drivers working... Like ccw127 mentioned before [here]("http://ubuntuforums.org/showpost.php?p=4724424&postcount=821"), you can install xserver-xorg-input-evtouch using synaptic, but it doesn't work too well straight off

I've gotten things a little better following the advice on page 2 - 3 onwards of this thread, such as [this]("http://ubuntuforums.org/showpost.php?p=2792971&postcount=16") post and [this]("http://ubuntuforums.org/showpost.php?p=2957448&postcount=24") one which explains how to get a reliable touchscreen event so you can set it up in xorg.conf

An important setting for xorg.conf that i don't think is mentioned in the earlier pages is the Option "MoveLimit", which I currently have at "5", the default option is way too high and results in really blocky motion. I also had to unblacklist "usbtouchscreen" and "tkusb".
 

Unfortunately, i can't get the calibration program running so i'm stuck with editing xorg.conf by trial-and-error. Also, the co-ordinates don't seem to scale propperly under rotation, they're way off... Can anyone help with that?

---

### Post by yrabinov on 2008-04-22
Hey Guys,

Installed Hardy last night, here is what I have yet to get to work, any help would be appreciated:

1) External monitor.  It is a samsung syncmaaster 760V, the driver is available online in a zip file.  Not sure what to do to install it.  When I was installing ubuntu it was on with random lines, now just blank.

2) My mute button is always blue... not a big issue but mildly annoying.

3) Webcam.  I can go to multimedia system selector, video, do the test, the webcam turns on for like half a second and I see its working, then the window closes.  Camorama cannot find the webcam.

4) Speakers through dock.  When I plug my speakers into the jack in the computer they work fine, however if I use the jack on the HP notebook quickdock, the speakers don't work and the computer speakers stay on.  Has anyone encountered this?

5) Touchscreen.  Duh.

Thanks

---

### Post by simplyw00x on 2008-04-22
> Cool, you'll have to let us know if you have any lock-ups with Fedora, It's probably not ubuntu specfic, but I had them in Gutsy, and after a couple months of not having them in Hardy I've started having them again. I'm sure a lot of us having these issues would like to hear your experiences. I've been considering fedora, and also suse, since they are working with AMD to get better power savings.
Thanks,
-Rick 
So far Fedora is... different. MP3 support was a **pain**, and the xserver in FC9 is too new for the nvidia driver, but on the plus side:
[LIST]
[*]uses hal input hotplug by default
[*]sound works out of the box
[*]start-up graphic is MUCH nicer
[*]random pulseaudio freezes when scrolling are gone (might be because I'm not using compiz though)
[/LIST]

So yeah. I will post updates when I've tried the new egalax drivers on it (prognosis not so good, but meh).

---

### Post by ir0nman on 2008-04-23
Is the evdev hotplugging how you stopped the beta driver triggering a double click? It's kind of useless when every touch sends a double click lol.
Thanks,
-Rick

---

### Post by simplyw00x on 2008-04-23
> Is the evdev hotplugging how you stopped the beta driver triggering a double click? It's kind of useless when every touch sends a double click lol.
Thanks,
-Rick
Yes. In short, remove all input devices apart from EETI from xorg.conf, add 
```
Option             "AllowEmptyInput"
```
to ServerFlags, copy /usr/share/doc/hal/examples/10-x11-input.fdi (not sure about the exact filename) to /etc/hal/fdi/policy/, then add the following as **/etc/hal/fdi/preprobe/10-egalax.fdi**:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
		<match key="info.product" string="eGalax TouchScreen">
			<merge key="info.ignore" type="bool">true</merge>
		</match>
	</device>
</deviceinfo>
```
and rejoice. If you need any funky keyboard-layout-fu (I need gb layout), add it in the 10-x11-input file like so:
```
<merge key="xkb_layout" type="string">gb</merge>
```
and you can also have different layouts per-keyboard with this (which is SWEET).

---

### Post by yrabinov on 2008-04-23
More Hardy stuff:  Ok I have my external working after turning on the screens and graphis button and configuring from there.  However it has a few problems.. I can't scroll from desktop to desktop or just move windows right across desktops, which was a really nice feature.  Also, in vlc when I hit full screen on the external monitor, it goes full on my main monitor.

Need help with all this stuff!

---

### Post by ir0nman on 2008-04-23
SimplyW00x,
     Well, I must be doing something wrong, I'm still getting double clicks, and I don't know how to get my trackpad to support scrolling now, that is no longer working, and I have tap to click on now as well.
Thanks for all your help so far,
-Rick

---

### Post by simplyw00x on 2008-04-23
> **ir0nman said:**
> SimplyW00x,
     Well, I must be doing something wrong, I'm still getting double clicks, and I don't know how to get my trackpad to support scrolling now, that is no longer working, and I have tap to click on now as well.
Thanks for all your help so far,
-Rick
Gah, sorry. Touchpad stuff should also stay in xorg.conf, otherwise it'll use evdev for that too (probably not what you want). Could you pastebin your Xorg.0.log and lshal output so I can have a shuftie?

---

### Post by ir0nman on 2008-04-23
Ok, got my log up here [http://paste.ubuntu.com/7897/](http://paste.ubuntu.com/7897/) and my lshal output starts at line 572. I had never heard of pastebin before, so hopefully that is what you meant. I appreciate all your help, I've asked egalax about the double click, and they never get back to me lol.
-Rick

p.s. this should be my current xorg config, added it as an after thought
[http://paste.ubuntu.com/7898/](http://paste.ubuntu.com/7898/)

---

### Post by simplyw00x on 2008-04-23
> **ir0nman said:**
> Ok, got my log up here [http://paste.ubuntu.com/7897/](http://paste.ubuntu.com/7897/) and my lshal output starts at line 572. I had never heard of pastebin before, so hopefully that is what you meant. I appreciate all your help, I've asked egalax about the double click, and they never get back to me lol.
-Rick

p.s. this should be my current xorg config, added it as an after thought
[http://paste.ubuntu.com/7898/](http://paste.ubuntu.com/7898/)
Your log suggests, and your xorg.conf confirms, that 'AllowEmptyInput' is in the wrong section --- it should be in ServerFlags (which is currently empty) and you have it in Extensions.

Hopefully fixing that should do the trick!

---

### Post by ir0nman on 2008-04-23
duh... thats what I get for doing it in a hurry and running off to class. Thanks man it works great now. i can finally use the touchscreen in hardy :-).
-Rick

---

### Post by WildcatWhiz on 2008-04-24
So, I've been tracking the Touchscreen development for Hardy via this thread. Simply and Iron have been putting in a LOT of work (props dudes). I, too, was going to dive in, until...

I realized that you all were talking 32-bit :(

I emailed egalax asking for 64-bit. 

So if anyone hears anything, or gets it working on 64-bit, let me know.

---

### Post by gborzi on 2008-04-24
> **WildcatWhiz said:**
> 
So if anyone hears anything, or gets it working on 64-bit, let me know.

Hello WildcatWhiz,
I have installed Hardy 64bit on my new tx1350el and after some struggling I got the touchscreen to work using the evtouch driver.
I did the following:
1) installed the xserver-xorg-input-evtouch
```
sudo apt-get install xserver-xorg-input-evtouch
```
2) downloaded the evtouch source from this [site]("http://www.conan.de/touchscreen/evtouch.html"), extraceted the file named  69-touchscreen.rules, put it in /etc/udev/rules.d and restarted udev ```
sudo /etc/init.d/udev restart
```
this will create a symbolic link named evtouch_event in /dev/input to the actual event input device.
3) Added the following section in my xorg.conf ```
Section "InputDevice"
        Identifier "touchscreen"
        Driver "evtouch"
        Option "Device" "/dev/input/evtouch_event"
        Option "ReportingMode" "Raw"
        Option "Emulate3Buttons"
        Option "Emulate3Timeout" "50"
        Option "SendCoreEvents" "On"
        Option "Calibrate" "1"
EndSection
```
and this line in the ServerLayout section ```
InputDevice "touchscreen"
```
stopped X and made the calibration as is explained in many places in the net, so I won't repeat it.
3) After the calibration I modified the above xorg.conf section as ```
Section "InputDevice"
        Identifier "touchscreen"
        Driver "evtouch"
        Option "Device" "/dev/input/evtouch_event"
        Option "MinX"        "66"
        Option "MinY"        "154"
        Option "MaxX"        "4002"
        Option "MaxY"        "3987"
        Option "ReportingMode" "Raw"
        Option "Emulate3Buttons"
        Option "Emulate3Timeout" "50"
        Option "SendCoreEvents" "On"
        Option "MoveLimit"    "4"
#        Option "Calibrate" "1"
EndSection
```
note the "MoveLimit" option above, it sets your touchscreen resolution.
4) Restarted X and it works like a charm.

Hope this helps.

---

### Post by CyberLeader on 2008-04-24
i managed to get evtouch working on hardy 64 as well, the touchscreen doesn't work propperly when the screen is rotated, are you having the same problem?

---

### Post by WildcatWhiz on 2008-04-24
I actually *don't* know how to run calibrate.sh. In Gutsy, I didn't need to stop X to calibrate...

I googled around and so far I've tried ctrl-alt-F1, killed X, cd-ed the folder, and ./calibrate.sh

And that doesn't do anything. It says something about not being able to find ev_touch

Help?

---

### Post by WildcatWhiz on 2008-04-24
Let me get specific...

"ev_calibrate not found exiting..."

What the heck am I doing wrong? 

Here's my Xorg.conf


# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@yellow)  Tue Mar  4 20:28:57 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Synaptics Touchpad"
InputDevice "touchscreen"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
        Identifier "touchscreen"
        Driver "evtouch"
        Option "Device" "/dev/input/evtouch_event"
        Option "ReportingMode" "Raw"
        Option "Emulate3Buttons"
        Option "Emulate3Timeout" "50"
        Option "SendCoreEvents" "On"
        Option "Calibrate" "1"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 61.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6150"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0, CRT: nvidia-auto-select +1280+0"
EndSection

---

### Post by waspbr on 2008-04-24
for gutsy related solutions check out this post
[http://ubuntuforums.org/showpost.php?p=4413930&postcount=652]("http://ubuntuforums.org/showpost.php?p=4413930&postcount=652")

---

### Post by waspbr on 2008-04-24
first of all, cheers to simplywoox and ironman for the brilliant work, I finally got my touchscreen working in hardy:), which is nice and I will celebrate with a cold beer shortly. 

however not, the Touchkit program has not been doing so well, I have only managed to do the 4 pt celibration, the program seems to quit during the 25 pt calibration.Actually now, the program takes like 5 minuted to open after i entered the sudo ./Touchkit command in terminal...

any tips or shoudl we just wait for eeti to give us a stable version?

---

### Post by mikedep333 on 2008-04-24
How are people doing with the blank/corrupted screen upon opening the lid or switching to the console? I have had to resort to NVIDIA 100.14.19 driver to resolve this.

More info on using the old driver here:
[http://ubuntuforums.org/showthread.php?t=745839&highlight=tx1000z](http://ubuntuforums.org/showthread.php?t=745839&highlight=tx1000z)

NVIDIA 100.14.19:
[http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html)

Bug Report:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/190526](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/190526)

---

### Post by gborzi on 2008-04-24
@CyberLeader
For me the touchscreen works fine when it is rotated by 180 degress, i.e. upside-down, doesn't work properly for 90 degrees, clockwise or counterclockwise. Tried the "Rotate" option for evtouch but no luck.
@WildcatWhiz
After switching to the text console, stop gdm ```
sudo /etc/init.d/gdm stop
```go to /usr/lib/xf86-input-evtouch ```
cd /usr/lib/xf86-input-evtouch
``` copy /usr/share/xf86-input-evtouch/empty_cursor.xbm to / ```
sudo cp /usr/share/xf86-input-evtouch/empty_cursor.xbm /
``` and start calibrate.sh as root ```
sudo ./calibrate.sh
``` for the calibration. That is to say, when the X server has started and is showing the little x-shaped symbols press Enter and the upper-left symbol will became red. Touch it with your pen in the center, it will turn black and the next symbol will turn red. Go ahead until the X server closes. Now you should have a file named out.txt in /usr/lib/xf86-input-evtouch. Open your /etc/X11/xorg.conf file with your preferred text editor, comment out the calibrate option and paste the first four lines of out.txt (those with MinX, MinY, MaxX and MaxY) in the touchscreen section, like in my previous post. Now restart X and if the touchscreen works you may want to delete /empty_cursor.xbm and /usr/lib/xf86-input-evtouch/out.txt.

Regards.

---

### Post by ir0nman on 2008-04-24
Waspbr, What version of the driver are you using, I was having calibration problems until I got the latest driver from egalax. Their earlier betas all gave me problems, If you want the latest just send me a PM, and I'll email it to you. That should take care of all your problems.

---

### Post by WildcatWhiz on 2008-04-24
FINALLY!!! Touchscreen in Hardy lives...Much much thanks.

---

### Post by mkarnicki on 2008-04-25
I'm happy more of you guys managed to make it work. I would like to calibrate my screen, but both "/etc/init.d/gdm stop" and "init 1" close my gdm and.. don't bring the command line but just a black screen. I can't see anything. I typed blind sudo /etc/init.d/gdm start, and it did. But I just can't see anything, simply a black screen. Please help :(

EDIT: I turned of nvidia and somehow managed to get to the command line.

---

### Post by gborzi on 2008-04-25
I too had problems with the nvidia closed source drivers. When I enabled them, the nvidia-glx-new package got installed and X worked well, but I had 2 problems:
1) the text console flickered and was almost useless. Perhaps on some model it symply appears blank;
2) after a screen blanking (e.g. after closing the lid) also X was flickering.
I fixed these issues by installing the nvidia-glx package, i.e. using the previous nvidia closed source drivers. However, hibernate stopped working and I had to disable compiz to have window decorations.
The hibernate issue was solved using the configuration suggested [here]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend"), the compiz problem adding this line ```
Option      "AddARGBGLXVisuals" "True"
``` in the device section of xorg.conf. Suspend to RAM (i.e. sleep) doesn't work properly, I still have to fix it.

Hope this helps.

---

### Post by mkarnicki on 2008-04-25
My touchscreen works yay! I-am-so-happy!

I would like to thank **simplyw00x,** who seems to be the first who made it work, and to thank **gborzi** for his post on detailed steps how to make it work on 64bit. I'm so glad fellas, this is what we needed. Indeed, a good start along Hardy's release ;) Good work!

EDIT: I would like to experiment a little and add these lines to my xorg.conf in the inputdevice touchscreen section:
```

#	Option		"LongTouchTimer"	50
#	Option		"maybetapped_action"	"click"
#	Option		"maybetapped_button"	1
#	Option		"longtouch_action"	"down"
#	Option		"longtouch_button"	1
#	Option		"oneandahalftap_action"	"down"
#	Option		"oneandahalftap_button"	3

```
If I uncomment any of them (eg the first line with LongTouchTimer) then when I reboot my gnome resolution drastically drops. When I comment it out again, everything's back to normal. What's wrong?

2nd question: how do I restart X fast? Before I used telinit1 , but when I use nvidia I can't see anything. It only works for me when I use open drivers..

EDIT: solved, look for next post

---

### Post by gborzi on 2008-04-25
Quick answer to question number 2: press Ctrl-Alt-Backspace. It kills your Xserver which is then restarted by gdm.

---

### Post by mkarnicki on 2008-04-25
Thank you **gborzi**, that's very convenient. For anyone interested in more natural-like touchscreen behavior, especially if you want to use cellwriter or such, I suggest lowering the value of LongTouchTimer so you get a left-mouse-down event faster (I had previously problems, since the numeric values also have to be quoted):

```

...
	Option		"ReportingMode"	"Raw"
	Option		"Emulate3Buttons"
	Option		"Emulate3Timeout"	"50"
	Option		"SendCoreEvents"	"On"
	Option		"MoveLimit"	"6"
#misc:
	Option		"LongTouchTimer"	"10"
	Option		"maybetapped_action"	"click"
	Option		"maybetapped_button"	"1"
	Option		"longtouch_action"	"down"
	Option		"longtouch_button"	"1"
	Option		"oneandahalftap_action"	"down"
	Option		"oneandahalftap_button"	"3"
...

```

I just can't tweak those values to get secondary click when I want to (so called one and a half tap). I'll look into that l8r, it's 3:51AM over here.

By the way, I'm using evtouch. As far as I know it doesn't have much in common with egalax (but I can be wrong), since I still can't get touchkit to work :D (and I will probably try no more).

---

### Post by pmaconi on 2008-04-26
Is there a way to make the sound/mute button responsive to the setting (i.e. turn orange when muted and blue when not muted)? My sound works fine and the button toggles the mute setting correctly. It just doesn't change color. It is a minor annoyance that I can live with, but would love to fix.

---

### Post by mkarnicki on 2008-04-26
**gborzi**, how to you cope with the fact, that (using evtouch) after rotating we loose calibration? You re-calibrate every time or is there an equvalent to egalax.cal file somewhere we could swap?

Thanks in advance.

---

### Post by gborzi on 2008-04-26
> **mkarnicki said:**
> **gborzi**, how to you cope with the fact, that (using evtouch) after rotating we loose calibration? You re-calibrate every time or is there an equvalent to egalax.cal file somewhere we could swap?

Thanks in advance.
This is still a problem for me, so I filed a bug in launchpad, see [here]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/222164"). To anyone having the same problem, please confirm this bug in launchpad.

---

### Post by isaacjun16 on 2008-04-26
Hello, I have a Pavilion tx1332la with Ubuntu 8.04 and everything seems to work except that when I restart the computer the screen give me a colour well, different colours that look like an Aurora and then the splash screen the one with the logo of Ubuntu looks weird. It those the same with the vesa drivers and the restricted driver that in this case are Nvidia, anyway I hope some one can help, thank for your time, bye bye. :guitar:

---

### Post by guiriman on 2008-04-26
hello guy.just a quick thank you fortst for all the inflrmation on ubuntu herel
following it i have installed hardy on my tx1000 without to many problems.
i have touchscreen and rotation workin more or less from all the info here
whatt i do have a problem with is the that my computer freezes after mayb 20 seconds of usin the touchscreen 
if i dont use it at all then my computer is fine
i am really confused about that as i believe that the touchscreen is always on for lack of better words
so as soon as i touch the screen i have a 20 sec countdown
if anyone can help please let me knw
thankin u all again
guiriman


EDIT
sorry forgot to mention that the mouse still works even though the screen is frozen.dont know if that helps anything at all  thanks again

EDIT2
i just tried my 4point calibration and this is the reply from the program.never got this b4
TouchKit: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted

can anyone help.i want my touchscreen haha

---

### Post by gborzi on 2008-04-26
Hello guys,
I fixed the left/right rotation calibration problem for evtouch driver. I had to do a small hack to the source code of the driver, but now it's working. The patch attached to this post has been sent to the developers in launchpad [here]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/222164"). Hopefully, they'll fix the package soon.
In the meantime you can recompile the driver using the patch, and if you're lucky enough to run an x86_64 system download the evtouch_drv.so.gz attachment, gunzip it, put it under /usr/lib/xorg/modules/input and restart X.

Hope this helps and works.

---

### Post by phattyacid on 2008-04-27
Anyone know how to configure acpi/powernowd so that the CPU's run at 800Mhz when the laptop is plugged in?  Mine peg at 2Ghz when plugged in and causes the fan to run constantly (annoying the heck out me).  If I unplug they drop to 800Mhz and everyone is happy.

This is a new "feature" since upgrading to Hardy.

Thanks.

---

### Post by CyberLeader on 2008-04-27
great stuff, the touchscreen is working propperly when rotated, thanks gborzi!

---

### Post by mkarnicki on 2008-04-27
**@phattyacid** I had the same problem. I decided to download Hardy and make a fresh install, as previously I have just updated and updated. Now my CPU works great. If you don't need compiz (nevertheless I still think nvidia driver is overall better), you can go to System -> Adm -> Hardware drivers, uninstall nvidia (untick it), and after reboot you will probably have your CPU scaling right as it should. I looked for an answer making a new thread and replying in other threads, but nobody knew. So I made a fresh install and it helped me. Hope this gives you an image.

**@gborzi** Thanks for your effort! Since I barely use vertical tablet position, I didn't check your patch, but since the post above - I'm glad it works :)

Gborzi - how you you trigger right click using touchscreen? It's my only problem for now.. I just can get it. Managed 2 times. I might have tweaked some values bad..

---

### Post by gborzi on 2008-04-27
@Phattyacid
On my system frequency scaling works out of the box. I made a fresh install with 8.04 beta, like Mkarnicki.
@Mkarnicki
I still have to fix this problem, but I remember that before putting MoveLimit to 10 sometimes I was able to get a right-click. I'll try with some other value, perhaps 30 will do. BTW, the default values reported in the driver homepage are quite different from those you can find in the code, which are as follows
```
TapTimer  	 90
LongTouchTimer   160
Emulate3Buttons    true -- enabled
Emulate3Timeout    50
MoveLimit 	180 Pixels
Rotate    None

```
Thanks for confirming the bug.

---

### Post by phattyacid on 2008-04-27
crud on the fresh install

thanks mkarnicki and gborzi

---

### Post by mkarnicki on 2008-04-27
**@phattyacid** Your welcome :)

**@gborzi** These values seem very unnatural for my touchscreen (tx1320us). I configured it as follows not to drop taps, selections, and handwritting (playing around with cellwriter)

```

...
	Option		"ReportingMode"	"Raw"
	Option		"Emulate3Buttons"
	Option		"Emulate3Timeout"	"30"
	Option		"SendCoreEvents"	"On"

#MoveLimit > 10 - visible line distortion
	Option		"MoveLimit"	"4"
#TapTimer = 10 - dropped taps
	Option		"TapTimer"		"5"
#LongTouchTimer > 20 - to slow for screen handwriting
	Option		"LongTouchTimer"	"20"

*(i'm not sure if the following are necessary or help with anything, but i'm still experimenting)*
	Option		"maybetapped_action"	"click"
	Option		"maybetapped_button"	"1"
	Option		"longtouch_action"	"down"
	Option		"longtouch_button"	"1"
	Option		"oneandahalftap_action"	"click"
	Option		"oneandahalftap_button"	"3"
...

```

I'm still struggling with the right-click. I think I'll finally have a look at the code.

---

### Post by thornythepirate on 2008-04-27
Hello all,
H
OK, here is my setup and progress so far.

tx1000 with the **final release of 8.04 Hardy Heron (64-bit)**:

**Sound: works right out of the box.**
Not much to say. headphone jack works, built-in microphones work (although very quietly, but that was always the case, even in windows), the mute button does not turn orange when muted, but that's not a huge issue.

**Wireless: Restricted Drivers Manager**
The Driver Manager installation of b43 and the firmware was a breeze. However, I don't use the wireless or bluetooth, but it seems like it's working fine and the wireless switch seems to activate and deactivate the wireless and bluetooth correctly.

**NVIDIA Graphics: Restricted Drivers Manager**
Again, easy installation with the Driver Manager. However, I am experiencing that crazy colored, blurry, distorted, laggy screen effect in the console and after closing and opening my lid.
[B]
I am able to get around this *somewhat* by making my way into System -> Preferences -> Screen Resolution, changing it to something else, and the restoring the previous settings.[/B] This makes my screen normal again without restarting X.

I understand that this is an issue with the new NVIDIA driver, I haven't tried using the old one yet.

**Touchscreen: evtouch with gborzi's evtouch_drv.so**
It took me awhile to figure out how to calibrate the evtouch driver, but then I read somewhere that you needed to press enter once in the calibration tool, then hit the red X's, and use the out.txt file.

Now it is working wonderfully thanks to the settings provided by other users (in terms of TapTimer, LongTouchTimer, etc.)

However, I cannot right click either. But for now, I'm just happy with it working at all. I also have not tried to rotate the screen yet, but I hear that with gborzi's evtouch_drv.so, it should work fine.

**Hibernation/Suspend: not working for me at all**
Before it would just hang in the console for both, then I went and changed some acpi settings, and now it suspends, but hangs on recovery.
[B]
Webcam: I don't have one[/B]
Not a built-in one at least, I haven't tried my USB one yet though.

**Fingerprint Reader: haven't tried it yet**
I don't know how to even start using it with Hardy in the first place. Are there any programs, modules or drivers I need?


[INDENT]tl;dr
**This works (for me) on x64 Hardy (Final):**
NVIDIA, Sound, Wireless, Bluetooth, Touchscreen

**This doesn't work:**
Hibernate, Suspend, corrupted graphics with NVIDIA drivers, right click for Touchscreen, orange mute button[/INDENT]



All in all, the progress you guys and Ubuntu have made with the tx1000 series is incredible, I first tried almost a year ago, and it was a mess. I went back to Vista grudgingly, and with Hardy's release I decided to try again. I'm very pleased, I'm probably going to stay now (:

[I]
P.S. CellWriter = WAY better than Microsoft's Input Panel IMO. (at least, with the touchscreen more or less calibrated and the timer settings you guys provided)[/I]

---

### Post by mkarnicki on 2008-04-27
**@thornythepirate** Glad you feel better with ubuntu now :)

I found maybetapped option to work as a right-click (just for testing), but didn't manage to set longtouch to execute right-click, and I'm not sure why. It's late over here, but I have enjoyed peeping the evtouch code. I hope we'll fix it soon.

I personally think it would be better to tune it to get right-click after touching the screen for a longer while not moving the cursor to much (yes, vista style), since it would be more comfortable then one and a half tap - I managed only to get few right clicks, but it was darn hard and I'm even not sure if it was with already tweaked settings or not :lolflag:

EDIT: I haven't trained my cellwriter well yet, but it at least recognizes my language! (which by the way varies from English alphabet by approx 8 symbols lol). Vista has English, Chinese and Japanese recognition. Well, that's nice, ok, I do learn Japanese. But crap I wanted my language option :D Finally! Since cellwriter was a master's thesis, maybe some one will write us a full handwriting recognition for linux one day :)

---

### Post by gborzi on 2008-04-27
Hello,
after some failed attempts at understanding the configuration options and making them work, I went straight the dumb way and symply copied a piece of the example configuration found in the /usr/share/doc/xserver-xorg-input-evtouch/changelog.gz file so that my touchscreen section look like this
```
Section "InputDevice"
        Identifier "touchscreen"
        Driver "evtouch"
        Option "Device" "/dev/input/evtouch_event"
        Option "MinX"        "66"
        Option "MinY"        "154"
        Option "MaxX"        "4002"
        Option "MaxY"        "3987"
        Option "ReportingMode" "Raw"
        Option "Emulate3Buttons"
        Option "Emulate3Timeout" "50"
        Option "SendCoreEvents" "On"
#   Behaviour
        Option "longtouched_action" "down"
        Option "longtouched_button" "3"
        Option "maybetapped_action" "click"
        Option "maybetapped_button" "1"
        Option "touched_drag" "1"
        Option "oneandahalftap_button" "0"
        Option "TapTimer" "30"
        Option "LongtouchTimer"  "500"
        Option "MoveLimit"  "18"
EndSection
```

Now I have right-click events when I make a long touch on the screen. Possibly the MoveLimit option can be set to smaller values without losing the right click.
@Mkarnicki
Just out of curiosity, which is your language?

---

### Post by benguin on 2008-04-28
It's reallly great to see so many people contributing to get the TX1000's more Ubuntu-ready, and yes, I am a big benficiary of this thread. That said, I am in a bit of a bother after upgrading to Hardy. The newer NVidia drivers corrupt the terminals to  nearly-unraedable quality, after a screen blanking event, I have the same issues. Going back to the nvidia-glx package does solve the problem (instead of using nvidia-glx-new), but suspend and hibernate are both broken, and they used to work smoothly under Gutsy. On top of that, I cannot get keyless ssh logins to remote machines like I used to with Gutsy after login on to GNOME. ssh from a terminal keeps asking me for my password, even after if keyring manager has the ssh login keys stored (imported).

I do not use the touchscreen much, but I have to admit it is a handy tool. My biggest gripe so far is the nvidia driver issue, closely followed by the suspend-hibernate breakage. I have a TX1305CA, with lspci reporting a GeForce Go 6150 video card.

Any ideas/pointers or suggestions to contribute would be really helpful!

Thanks,
-J-

---

### Post by thornythepirate on 2008-04-28
> **gborzi said:**
> Now I have right-click events when I make a long touch on the screen. Possibly the MoveLimit option can be set to smaller values without losing the right click.

Cool! now I can cross-out my right click issue. It's working just as functionally as windows now :)

benguin pretty much nailed the only issues left now in Hardy. I just wish I was smart enough to contribute :lolflag:

---

### Post by gborzi on 2008-04-28
@Benguin
I had the same problems with the nvidia-glx-new driver, so I installed nvidia-glx instead. This broke the hibernation but I have fixed it using the configuration suggested [here]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend").
I hope it'll also work on your system.

---

### Post by benguin on 2008-04-28
> **gborzi said:**
> @Benguin
I had the same problems with the nvidia-glx-new driver, so I installed nvidia-glx instead. This broke the hibernation but I have fixed it using the configuration suggested [here]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend").
I hope it'll also work on your system.

Thanks for the heads up gborzi. The newer drivers are actually helpful for a much stable compiz experience, as far as I have seen. I guess I'll just have to wait while a fix is found. By the way, the 173.xx beta has the same issues; I tried.

---

### Post by mkarnicki on 2008-04-28
**ghborzi** Your values work fine! I am actually handwriting this with cell writer just for fun and some testing. I have set MoveLimit to 10 and my right click still works well :)! Thanks to your contributions we can finally enjoy our touchscreens :) Also my thanks go to simplyw00x! I am so happy :)

By the way, I'm Polish.  I need to practice my English more :), cuz I haven't been using it mucn lately. By the way... I'm impressed with cellwriter :) (whole post handwritten!)

---

### Post by Exile71x on 2008-04-28
I just installed the new release of Hardy Heron and have tried several different ways to get my wireless working on my tx1000z. Any help would be greatly appreciated. Also i installed the amd64 version.

---

### Post by Hitnrun on 2008-04-28
> **Exile71x said:**
> I just installed the new release of Hardy Heron and have tried several different ways to get my wireless working on my tx1000z. Any help would be greatly appreciated. Also i installed the amd64 version.

I am running this script manually

```

#!/bin/sh

rmmod ohci_hcd
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe ohci_hcd

```

While waiting for an official fix in the future. This enables wireless on my tx1204au.

---

### Post by Exile71x on 2008-04-28
Thanks that worked. I just had to install ndiswrapper and ndisgtk from synaptic and download the drivers from [http://rapidshare.com/files/79251578/driver.zip](http://rapidshare.com/files/79251578/driver.zip). after installing the drive i just ran that and didn't have any more trouble.

---

### Post by bradleyb01 on 2008-04-28
Thank you everybody so much foe your posts on this thread, I now have my touchscreen working after upgrading to Hardy thumped it on my tx1220us. 

I have noticed that several people have tried th 64 bit version and sounded reasonably happy with it. I know that there were several compatibility issues with gutsy involving flash and other things. Have these been resolved in th interim? I am considering trying 64 bit this weekend if it is worth it.

Thanks!

---

### Post by gborzi on 2008-04-28
I have noticed a strange and unpleasant behaviour in my tx1350el when I rotate and close the screen (i.e. the tablet position): all screen multimedia buttons stop working :( . In normal position the DVD button and quickmedia button (the one with the circular arrow) work and also the Prev/Next Track, Play/Pause and Stop buttons have the desired effect. But when the lid is closed with the screen up neither of these buttons work. Has anyone noticed the same problem? Perhaps it is so to avoid the consequences of inadvertently pressing them while writing on the touchscreen, but I find it quite annoying.
BTW, two screen buttons (the one with two arrows on a square and that with a gear) don't work at all.
@mkarnicki
Still I don't understand how the evtouch buttons configuration works. I had tried a very similar configuration, only missing the touched_drag option, slightly different values for the timers and a different order for the options but it didn't work. Perhaps the order is important. Also, I would like to get the middle mouse button click but still no success.
@bradleyb01
I installed the 64bit version and haven't seen any problem with flashplayer. You'll have to install ubuntu-restricted-extras to have flashplayer installed and configured.

---

### Post by mkarnicki on 2008-04-28
@gborzi
I recall that in vista there was similar behaviour - the rev/play/fwd/stop buttons didn't work when the laptop was in tablet mode. Hope this isn't hardware matter, since it's really dumb. I agree with you that they would be still usefull in tablet mode. BTW bro, I'm really glad we finally have this right click, makes life easier :D

I only use normal and inverted screen rotation - having said that, my dvd and arrow in a circle buttons both still work after rotation (I barely use vertical tablet mode, so maybe that's why I haven't experienced what you have).

I'm a lazy *** so I'm gonna use you AMD64 guys and ask it here: have you lately experienced problems with updating/installing new software? It really bothers me. I want to configure my compiz, as I have before..

Pasted from "Add/remove apps"
```
 Advanced Desktop Effects Settings (ccsm)

This application is provided by the Ubuntu community.
Advanced Desktop Effects Settings (ccsm) cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.
```

This post features AD lol:
CellWriter - highly recommended for your tablet mode. Try it out, apart from handwriting recognition it also has a built it onscreen keyboard. When docked on the bottom of the screen (you can hide/unhide it by clicking the icon in the system tray), when you turn on the onscreen keyboard it spans like on a half of the screen - you can type with your fingers on the screen almost as you would on normal keyboard hahaha. Only what's buggin me is that Cellwriter when docked at the bottom hides behind the gnome bottom panel. But there are few ways to go around :) Damn that post was long.. goodnight guys :lolflag:

BTW Giuseppe I'd like to help you out, but.. what do you use middle button for? I just.. even don't know how to test it. Oh, and the order of the options in xorg for touchscr is rather not important, I did reorganize them little bit myself.

---

### Post by avik on 2008-04-28
> **bradleyb01 said:**
> I have noticed that several people have tried th 64 bit version and sounded reasonably happy with it. I know that there were several compatibility issues with gutsy involving flash and other things. Have these been resolved in th interim? I am considering trying 64 bit this weekend if it is worth it.

64 bit works great.  In the beginning of this thread, many people were using 32 bit, but by now, many people are using 64 bit.  Ubuntu has made it astonishingly easy, and everything works as expected.  I'm pretty sure all the problems in this thread apply to both 32 and 64 bit versions equally, so you won't be losing anything.

Also, has anyone gotten a second screen or projector working.  I would like to use this laptop to give a presentation, but I can never get it to recognize the projector.  The projector in question happens to be a Hitachi (forgot the exact model), but I can't seem to get it working.  Any tips?

---

### Post by martiman on 2008-04-29
@Avik:
Yes, i've got a second screen working (Philips monitor).
With 8.04, 32bit i haven't got any problems with nvidia-xgl-new drivers, everything works like expected (i think).

For dualscreen:
* Install **nvidia-settings** (not already there)
* start **sudo nvidia-settings**
* Second screen is automatically recognized here, otherwise click **Detect Displays**
* Click second screen, configure.
I've tried Twinview and both Seperate Xscreen with and without Xinerama. Only **Seperate Xscreen without Xinerama** works good. You get a second Desktop on monitor 2, compiz gives you to cubes (if not, choose in **CCSM -> Desktop cube -> Multi output mode -> Multible cubes**).
With Twinview there are also 2 cubes, but if you rotate cube 1, cube 2 is also rotating (??). 

In ooimpress choose Presentation -> Presentation settings
and choose presentation monitor.

*testing touchscreen now..

---

### Post by mkarnicki on 2008-04-29
By the way.. my problem with "... cannot be installed on your computer type (amd64)." was solved - had to remove "web" from sources.list (Nobody knows how did it get there :D ).

---

### Post by martiman on 2008-04-29
Well, seems like i've found a new problem (haven't seen it before here)

Everytime i reboot and login, i get a gnome-desktop with black background (no icons) and white panels (have set them to 50% transparant).
When i kill X (ctrl+alt+backspace) and login again, everything is OK.
Nvidia-glx-new with compiz enabled.


Who knows whats wrong?

---

### Post by gborzi on 2008-04-29
> **mkarnicki said:**
> @gborzi
BTW Giuseppe I'd like to help you out, but.. what do you use middle button for? I just.. even don't know how to test it. Oh, and the order of the options in xorg for touchscr is rather not important, I did reorganize them little bit myself.
Middle button is used to paste the text you have selected. E.g. it can be used to paste an internet address in firefox address bar or to paste commands in the terminal. It is also possible to cut and paste using the right-click menu, but the middle button is faster.
About the non-working screen buttons, perhaps the way they work changes from model to model. Mine is the tx1350el, which is the specific model you are using?

---

### Post by simplyw00x on 2008-04-29
The 'rotate' and 'gears' buttons do not work, and do not generate acpi events in Ubutu feisty, gutsy, hardy or fedora 9. The others all work fine (more or less, VGA-out still does nada).

---

### Post by mkarnicki on 2008-04-29
I'm using tx1320us, but as I have mentioned before, I have modified our ./rotate script to switch between -o normal and -o inverted modes only, so I haven't tried those two buttons in -o left or -o right mode. Thanks for explaining the middle click. I also have no info about "gears" and "arrows" buttons.

---

### Post by gborzi on 2008-04-29
@simplyw00x
It's the same on Gentoo, according to [this page]("http://gentoo-wiki.com/HARDWARE_HP_tx1000"). It won't be easy to get them to work.
@mkarnicki
The rotate and gear buttons are the two horizontal screen buttons located on the bottom right of the screen. I checked if my buttons work with the unrotated screen, they don't.

EDIT: Googling on the problem of the non-working buttons, I discovered that for some laptop models (e.g. sony and thinkpad) there are kernel modules to get extra keys working. Maybe our laptops need a similar module to be developed.

---

### Post by mkarnicki on 2008-04-30
> **gborzi said:**
> 
@mkarnicki
The rotate and gear buttons are the two horizontal screen buttons located on the bottom right of the screen. I checked if my buttons work with the unrotated screen, they don't.


I know which buttons they are ;) And I do know they don't work. I did only say that DVD button and the one next to it work after rotating to -o inverted. Arrows and gears never worked :lolflag: I didn't claim otherwise.

You said that you had problems with them after rotating if I got you right (and I may have not). And you where talking about these two that do work, right? So I said mine work fine (no, not the arrows and gears ;) ).

---

### Post by gborzi on 2008-04-30
> **mkarnicki said:**
> I know which buttons they are ;) And I do know they don't work. I did only say that DVD button and the one next to it work after rotating to -o inverted. Arrows and gears never worked :lolflag: I didn't claim otherwise.
Sorry, I misunderstood the "I have no info" for "I don't know which buttons you are talking about" and thought these buttons were not available on your model.

> **mkarnicki said:**
> 
You said that you had problems with them after rotating if I got you right (and I may have not). And you where talking about these two that do work, right? So I said mine work fine (no, not the arrows and gears ;) ).
My DVD and quickplay buttons only work when the screen is in normal laptop position, stops working when the screen is in tablet position i.e. covering the keyboard with the screen up, regardless of the randr rotation.

---

### Post by Cuppa-Chino on 2008-04-30
Short question - am wondering if I should risk it and take Hardly Plunge on the tx1000 I have. Current key thing that bugs me in Gutsy (which otherwise works just fine...) is problems with the graphics, had started another thread somewhere but that has been lost in the winds of time, so can someone confirm that this is not happening in Hardy and what config they are using to prevent it:

a) display corruption after screensaver, I currently always have to change refresh rate in Nvidia settings manager to get out of that, the screen is all "contorted", this is also visible when I power down the machine, once it leaves gdm it goes contorted

b) the poweroff on the display can completely lock the screen, ie I close the lid and voila I can only get back in with CTRL+ALT+DEL to restart Gnome

Any help, might just risk it anyhow but pointers always welcome....

---

### Post by mkarnicki on 2008-04-30
omg I am so lame, sorry gborzi.. I did check these two with lid flat on the keyboard.. they don't work for me also. At first I thought this problem was the matter of randr and I did test it.. without converting to tablet mode :D Sorry again, I'm so lame.. They don't work for me in tablet mode also. But this is also lame.. why the heck did they design these like that? I'd still want to use them as well.

Misunderstanding, my fault.

---

### Post by Cuppa-Chino on 2008-04-30
> **Cuppa-Chino said:**
> Short question - am wondering if I should risk it and take Hardly Plunge on the tx1000 I have. Current key thing that bugs me in Gutsy (which otherwise works just fine...) is problems with the graphics, had started another thread somewhere but that has been lost in the winds of time, so can someone confirm that this is not happening in Hardy and what config they are using to prevent it:

a) display corruption after screensaver, I currently always have to change refresh rate in Nvidia settings manager to get out of that, the screen is all "contorted", this is also visible when I power down the machine, once it leaves gdm it goes contorted

b) the poweroff on the display can completely lock the screen, ie I close the lid and voila I can only get back in with CTRL+ALT+DEL to restart Gnome

Any help, might just risk it anyhow but pointers always welcome....

oh one more thing, my computer keeps going to maximum performance on the gpu ie 425mhz, even when I use xfce without composition, anyone know how to fix this?

---

### Post by mkarnicki on 2008-04-30
Me and someone else did find reinstalling the system solve the issue of maxing the cpu performance (yes, i'm on hardy)

---

### Post by Cuppa-Chino on 2008-04-30
> **mkarnicki said:**
> Me and someone else did find reinstalling the system solve the issue of maxing the cpu performance (yes, i'm on hardy)

sorry to be persistent: but did a fresh hardy (32 or 64bit?  -  do you use nvidia binary drivers or the open source nv drivers or vesa driver) install help you with the 

GPU -- clock problem

or with 

CPU -- clock problem

my cpu clocks fine, up and down etc, gpu is just stuck on max performance when I am on ac power, tried enabling coolbits and forcing down the max frequency but that did not work eiter.

looks like I will try a fresh install maybe straight xubuntu to minimise the issues

---

### Post by mkarnicki on 2008-04-30
I'm really tired lately, excuse my lapse. I thought you were talking about CPU, not General Processing Unit. How did you get to know that anyways? Even if I had the same problem, I would probably live unaware that my GPU maxes.

I'm using Hardy on AMD64bit. Previously if I used open graphic drivers my CPU scaling worked fine, but when I installed nvidia drivers, my CPU maxed to 2GHz all the time when I was on AC power. I wanted to use nvidia (&compiz), but I didn't want to hear that fan kickin' in all the time. So I thought I'd give it a try and after making a fresh Hardy install (a day or two after official release) my CPU and nvidia drivers stopped making problems. I've got scaling and I've got compiz. And I don't know how's my GPU :D :lolflag:

---

### Post by gborzi on 2008-05-01
@Cuppa-Chino
On my fresh Hardy 64bit install *nvclock -s* reports ```
Card: 		Unknown Nvidia card
Card number: 	1
Memory clock: 	-2147483.750 MHz
GPU clock: 	-1073741.875 MHz

```
Yes, it reports negative numbers, don't know why. Also nvidia-settings and /var/log/Xorg.0.log reports 512 MB video memory :shock:. It looks like there is something wrong with the data reported by the driver. How did you check the GPU clock?
@Mkarnicki
I know that older version of this laptop shipped with [QuickPlay]("http://en.wikipedia.org/wiki/Quickplay") and perhaps the screen button were "reserved" to it. This may explain their deactivation in tablet mode and also gives some hope on getting them to work. Earlier versions of QuickPlay were GNU/Linux based.

Finally a question for everyone. I've been struggling with Suspend to RAM, but still no results. Has anyone succeeded?

---

### Post by CyberLeader on 2008-05-01
I've had a look through my notes and i remember following this post made suspend to ram work a better but still not perfect, it still sometimes crashes on waking: [http://ubuntuforums.org/showthread.php?p=3699685]("http://ubuntuforums.org/showthread.php?p=3699685")

As for the GPU speed issue, a quick google turned up this page : [http://owened.net/2008/04/23/how-to-force-nvidia-powermizer-performance-in-linux/]("http://owened.net/2008/04/23/how-to-force-nvidia-powermizer-performance-in-linux/"), it didn't work for me though :(. Although i remember reading somewhere else that the powermizer monitor might not actually be reporting the true performance level though, so we can't be sure about this one

I can't get the screen rotate button to work either, I tried mapping the quickplay button to the rotate script using gconf-editor -> apps -> metacity... but that didn't work, anyone know a better way?

---

### Post by gborzi on 2008-05-01
Thanks for the answer CyberLeader, I'll try it. As for quickplay button, I configured it in this way:
1) run xev and press the button to get its keycode (205 on my system);
2) run ```
xmodmap -pke > xmodmap.conf
```open xmodmap.conf with your preferred text editor, search for the above keycode (on my system the line reads *keycode 205 =*) and add an unused X keysim after the = sign. X keysims are stored in /usr/share/X11/XKeysymDB. I used XF86Launch0 so that I have ```
keycode 205 = XF86Launch0
```
3) put this file somewhere (I used /etc/X11);
4) run ```
xmodmap <path to xmodmap.conf>/xmodmap.conf
``` at the login, I added an entry to System -> Preferences -> Session;
5) configure your WM (metacity, compiz or wathever) to bind your script to the X keysim.
Maybe you can find [this page]("https://help.ubuntu.com/community/MultimediaKeys") worth reading.

Hope this helps.

---

### Post by mkarnicki on 2008-05-01
My nvclock on tx1320us displays the same values as GBorzi's. Thanks for these instructions about xmodmap. I have seen them also somewhere else, but this time they worked for me ^ - ^ !

As for suspending, I did exactly the instructions given in the link and indeed my computer did suspend (previously it didn't even do that). But it didn't resume, turned on with black screen, nothing more. It would be really nice to have suspend/hibernate work.

---

### Post by gborzi on 2008-05-01
> **mkarnicki said:**
> My nvclock on tx1320us displays the same values as GBorzi's. Thanks for these instructions about xmodmap. I have seen them also somewhere else, but this time they worked for me ^ - ^ !
At first I put the xmodmap command in /etc/gdm/PostLogin/Default but it didn't worked, so I used the Sessions GUI.

> **mkarnicki said:**
> 
As for suspending, I did exactly the instructions given in the link and indeed my computer did suspend (previously it didn't even do that). But it didn't resume, turned on with black screen, nothing more. It would be really nice to have suspend/hibernate work.
I still have to try the instructions linked by CyberLeader, but hibernate works for me, see post #893 on how to fix them. As for sleep, the laptop suspends, resumes to a blank screen and I can go to a text console with Ctrl-Alt-F1 and also switch among text consoles using Alt-FX (X=1,2,3,4,5,6). But I can't type anything, the keyboard seems dead :confused:.

---

### Post by mkarnicki on 2008-05-01
To be honest I didn't use the Sessions GUI, because I forgot. And Gnome asked me at the next boot which modmap should it load (I had xmodmap.conf and xmodmap.conf~ so it got confused). I selected xmodmap.conf previously editet by me, and it worked fine :) So I guess.. you don't need to use the Sessions window. Still, the question about which to load was in GUI little window ^ ^

Thanks for giving exact post numer. I'll try it soon. Goodnight.

---

### Post by mkarnicki on 2008-05-01
**@GBorzi** The hibernation thing still doesn't work for me after doing these steps. I'll look into it some time later :)

Do you guys use hdparm for head parking issues on your tx laptop series? Today I realized my load cycle increments in a crazy speed like.. 1 time per 5 seconds, this is crazy.. I manually executed so called 'ugly fix', but I'm quite comfortable after reading a lot of man and info under console about hdparm and smartctl. What's your load_cycle? You can check it with:
```
sudo smartctl --all /dev/sda|grep Load_Cycle_Count
```
The last numer is what we're interested in. I've got my laptop for at most 4 months and my load cycle is 59158. In this pace I would kill my hdd faster then 3 years. I've got many exams right now, but until they do fix it in Hardy I've got some idea for a nice little app..

By the way, if you have the same problems, I have noticed that in the mainstream thread about head parking and howto's there's a script:

99-hdd-ugly-fix.sh :
========================
#/bin/bash
if on_ac_power = 1 ; then
hdparm -B 254 /dev/sda
else
# possibly on battery
hdparm -B 128 /dev/sda
fi
=========================

But hdparm man says it won't spin down for -B parameter >= 128, so I don't get it. The author wanted to park heads to be secure against bumps and so on, but -B 128 doesn't spin down the disc. -B 127 already does.

---

### Post by gborzi on 2008-05-02
> **mkarnicki said:**
> **@GBorzi** The hibernation thing still doesn't work for me after doing these steps. I'll look into it some time later :)
Sorry, I forgot to add that probably you need to increase /sys/power/image_size. When a computer hibernates, its state is written in the swap partition, but the amount of data that can be written is limited by the value in /sys/power/image_size, which by default is 512MB (the number is given in kB). So, when RAM is above 512MB and more than 512MB are in use, hibernation doesn't work. This is easily fixed by raising the above value to the amount of RAM in kB you have. For 2GB RAM this command will do ```
echo 2115985408 > /sys/power/image_size
```
obviously, it must be run as root. Please note that at each reboot the /sys/power/image_size will go back to its default value, to make it permanent put the above line in /etc/rc.local.

> **mkarnicki said:**
> 
Do you guys use hdparm for head parking issues on your tx laptop series? Today I realized my load cycle increments in a crazy speed like.. 1 time per 5 seconds, this is crazy.. I manually executed so called 'ugly fix', but I'm quite comfortable after reading a lot of man and info under console about hdparm and smartctl. What's your load_cycle? You can check it with:
```
sudo smartctl --all /dev/sda|grep Load_Cycle_Count
```
The last numer is what we're interested in. I've got my laptop for at most 4 months and my load cycle is 59158. In this pace I would kill my hdd faster then 3 years. I've got many exams right now, but until they do fix it in Hardy I've got some idea for a nice little app..

By the way, if you have the same problems, I have noticed that in the mainstream thread about head parking and howto's there's a script:

99-hdd-ugly-fix.sh :
========================
#/bin/bash
if on_ac_power = 1 ; then
hdparm -B 254 /dev/sda
else
# possibly on battery
hdparm -B 128 /dev/sda
fi
=========================

But hdparm man says it won't spin down for -B parameter >= 128, so I don't get it. The author wanted to park heads to be secure against bumps and so on, but -B 128 doesn't spin down the disc. -B 127 already does.

Thanks for pointing at this problem. I had read about it in the past, but forgot to check in my new laptop. In just 3 weeks my Load_Cycle_Count is already above 13000. I disable Advanced Power Management with ```
sudo hdparm -B 255 /dev/sda
```and applied the "ugly fix" as suggested [here]("http://ubuntuforums.org/showpost.php?p=3675960&postcount=26"). I noticed that "sudo hdparm -B 254 /dev/sda" only slows down the Load_Cycle_Count growth doesn't stop it.

---

### Post by mkarnicki on 2008-05-02
Thanks for the additional info about hibernation, I will try it out.

Since this whole parking thing is an important issue, I will let myself notice that it works differently for me then it works for you. It may depend on the disk type, I don't know. My disk type is in the last line. I'm pasting this for you to see how it works for me:

```
mkarnicki@michal-laptop:~$ sudo smartctl --all /dev/sda|grep 193
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       **59265**
mkarnicki@michal-laptop:~$ sudo hdparm -B **255** /dev/sda

/dev/sda:
 setting Advanced Power Management level to **disabled**
mkarnicki@michal-laptop:~$ sudo smartctl --all /dev/sda|grep 193
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       **59265**
mkarnicki@michal-laptop:~$ sudo smartctl --all /dev/sda|grep 193
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       **59266**
mkarnicki@michal-laptop:~$ sudo smartctl --all /dev/sda|grep 193
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       **59267**
mkarnicki@michal-laptop:~$ sudo hdparm -B **254** /dev/sda

/dev/sda:
 setting Advanced Power Management level to **0xfe (254)**
mkarnicki@michal-laptop:~$ sudo smartctl --all /dev/sda|grep 193
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       **59267**
[after some time]
mkarnicki@michal-laptop:~$ sudo smartctl --all /dev/sda|grep 193
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       **59267**
mkarnicki@michal-laptop:~$ sudo hddtemp /dev/sda
/dev/sda: SAMSUNG HM250JI: 45°C
```

..which means that 254 works and 255 doesn't work for me (even if it wrote setting Advanced Power Management level to **disabled** I heard the disk to spin down few seconds later). So if anyone uses this ugly fix, make sure you choose the right value.

EDIT: after these commands I checked -B 255 again (apm disabled), and it still worked (I mean the load cycle didn't increase). This would explain why the author included both lines in:
```
#!/bin/bash
if on_ac_power; then
  # on AC so don't do any head parking
  hdparm -B 254 /dev/sda
  hdparm -B 255 /dev/sda
```, right? I think it makes the ugly fix work for us both.

---

### Post by gborzi on 2008-05-02
According to hdparm manpage, not all HD support disabling Advanced Power Management (APM). This could be the reason for the two hdparm lines: the first line puts APM at the lowest level, the second one disables APM if possible. To me it looks like the value 255 reports APM disabled but actually does nothing for your samsung HD.
On my laptop there is a different HD, a WDC WD2500BEVS-60UST0 as reported by hdparm using option -I.

EDIT: I forgot a question about xmodmap.conf. You said that gnome asked which file to use between xmodmap.conf and xmodmap.conf~. Where they placed in your home directory or under /etc/X11?

---

### Post by mkarnicki on 2008-05-02
Yes, it seems you're right about my samsung hdd. Remember to check temperature of your disk if you're using the ugly fix and that we have to avoid bumps to not corrupt the hardware. My hdd temperature is ok, yet - it reaches rather high temperatures, since lately it had 50 C degrees and max is 54.. so I'll be careful.

Yep, I remember I have put a copy in /etc/X11, but actually yes - the to files I mentioned, xmodmap.conf and xmodmap.conf~ where in my home directory. I just today broke it, but I was glad to recover just by removing both of them ^ - ^ hahaha.. I like this kind of recovering under linux. Something doesn't work.. remove it and reboot, it'll work :lolflag: hahaha

By the way.. your tip about hibernation helped - it did dump my memory on the hdd, turned off the display and hdd, but it stayed on, I had to manually turn it of. I didn't expect it to wake from hibernation when I boot next time, but it did :D Nevertheless bluetooth stopped working until reboot.

Does your tx shutdown completely when you hibernate? Oh.. do I have to have LAPTOP_MODE enabled? I got little scared with this hdd issue and disabled laptop_mode in acpi..

Thanks for your valuable hints GBorzi

---

### Post by gborzi on 2008-05-03
Thanks for your advice about the temperature. In order to monitor it, I installed hddtemp and sensors-applet. The latter is very handy, it's a gnome panel applet that show your GPU, CPU and HD temperature. After two hours on on AC power it shows 63C, 41C, 45C (room temperature is 22C). GPU temperature seems high, but nvidia-settings reports a "Slowdown Threshold" at 130C and a green bar for this temperature.
**But now a bad new**: the ugly fix for the Load_Cycle_Count doesn't work :(. Today I heard a click from the HD, checked the Load_Cycle_Count that increased by around 100 in just 15 minutes. Also *Advanced Power Management* was on (it can be checked with *sudo hdparm -I /dev/sda |grep "Advanced Power Management"*, if there is a * it is on). I have found another fix [here]("http://vale.homelinux.net/wordpress/2007/10/24/potential-risk-for-your-nx6325s-harddrive/"), I'm checking if it works.

EDIT: Sorry, I forgot to mention that my TX powers off when hibernates. In the meantime I checked the above fix, it doesn't work :(. When resuming from hibernate APM is on.

---

### Post by pmaconi on 2008-05-03
I'm having some problems with nvidia-glx and nvidia-glx-new. The new version messes up the terminals for ctrl-alt-F*, but the older version removes all window frames and messes up my gui terminal (it appears as a white box with no writing - but is still usable, just not readable). I would really like to get the older driver working so that I can use ctrl-alt-F* and hibernate. Any ideas?

---

### Post by david412 on 2008-05-03
I am having trouble suspending on my laptop. I am running the 64b bit version of 8.04. When i try to resume from suspend, my screen does a weird line thing with a bunch of colors and then eventually goes white. I have to do a hard shut down to restart. I have been trying this with the s2ram command.I believe this is a problem with nvidia drivers. I am using the restricted nvidia drivers.

Thanks 
-David

---

### Post by gborzi on 2008-05-03
@pmaconi
Just add this line >       Option      "AddARGBGLXVisuals" "True"
to the "Device" section in /etc/X11/xorg.conf. It worked fine for me.

---

### Post by david412 on 2008-05-03
> **mkarnicki said:**
> 
By the way.. your tip about hibernation helped - it did dump my memory on the hdd, turned off the display and hdd, but it stayed on, I had to manually turn it of. I didn't expect it to wake from hibernation when I boot next time, but it did :D Nevertheless bluetooth stopped working until reboot.

Does your tx shutdown completely when you hibernate? Oh.. do I have to have LAPTOP_MODE enabled? I got little scared with this hdd issue and disabled laptop_mode in acpi..

Thanks for your valuable hints GBorzi 

I am having the exact same problem with hibernate. Have you had any luck with suspend? I really need one of these features to work because I move my laptop alot at school and I don't want to do a full shutdown each Time i move.
Thanks,
-David

---

### Post by pmaconi on 2008-05-03
Thanks! That fixed it.

---

### Post by pmaconi on 2008-05-03
The older driver is working for me now, but I can't hibernate. I followed the steps [here]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend") as well as echo 4294967296 > /sys/power/image_size for my 4GB of RAM. Whenever I attempt to hibernate, my computer restarts.

---

### Post by mkarnicki on 2008-05-03
**@david412** If you follow GBorzi instructions scrambled in posts on last 2-3 pages, you can get your hibernation working - but I mean that scenario with shutting down it manually when it finishes dumping the memory. I know this is awkward, but no, I have not better idea. I also haven't succeeded with suspend, my screen turns blank and I just have to do a hard restart to make it shutdown/work again.

**@GBorzi** OK, now I'm worried. But I simply don't use suspend nor hibernation, so this scenario doesn't apply to me, does it? I checked my load_cycle and it didn't increase (I'm on vista now so I can't check it again..). I'll hopefully drop in here soon. Later guys.

---

### Post by v0lZy on 2008-05-03
Hi, its my 1st time posting here after reading all of the stuff that applies to Hardy Heron in this topic.

First of all I would like to thank everyone for contributing solutions to problems with Ubuntu and the tx1000 laptop/tablet PC (which I among other users here own).

I installed Hardy Heron 64-bit from a live cd version and so far I am very pleased with it.

Thanks to the guides mentioned here, I have been able to make good progress with the touchscreen, but no gold medal for me yet.

Following gborzi`s example, I managed to get the ./calibrate.sh going, but I can not make the calibration. I press enter and the upper left cross turns red. I try touching it but I can not get it to register consistently. If I run my pen in circles i somehow get lucky and after quite a lot of hardship manage to get through the whole process of what appers to be 9 point calibration... unfortunately the calibration is useless; while it results in the ability to move the cursor around the screen (and after using some more settings written here on the forum, the ability of calling rightclicks) I have little control over it. The cursor seems to jump rather then slide from point to point, not to mention that it is offset from where the pen actually is and not necesserily moving in the direction the pen is traveling.

1) Has anyone else encountered the same problem? 
2) If so, has anyone found a solution or some default settings that should work?
3) I would really appreciate a step by step solution for it.

Apart from that,

I have very little experience with ubuntu (or linux in general), but me and my friend got the touchscreen working perfectly in opensuse 10.3 using this link [http://hackerforum.devil.it/viewtopic.php?p=46319&sid=45519586e0af2c4d73937489c490e102]("http://hackerforum.devil.it/viewtopic.php?p=46319&sid=45519586e0af2c4d73937489c490e102") and some google translator magic. What we found out (and was the key to getting the whole thing working) was that the newer versions of the driver were missing some files which we needed to get from older versions... (we compiled some sources and used some binaries provided as well in order to get it working)

Anyway, using the above page's and the touchscreen's driver's page's instructions, we were able to calibrate it and make it work without difficulty in opensuse... so it should, i suppose, work with ubuntu too.

My friend moved out to Japan and we're in touch via e-mail but its difficult to repeat the whole process as neither of us recalls it completely.

Anyway, I hope this insight might give some help to those of u who are a bit more comfortable with tinkering with linux.

Cheers, V

---

### Post by pmaconi on 2008-05-03
I just used the values that other people posted in this forum. I couldn't get the calibration to work with any more success than you did. But these values worked great.

My xorg.conf looks like this:

> Section "ServerLayout"
[INDENT]Identifier	"Default Layout"
screen 		"Default Screen"
Inputdevice	"Synaptics Touchpad"
InputDevice 	"Touch Screen"[/INDENT]
EndSection

> Section "InputDevice"
       [INDENT]Identifier "Touch Screen"
       Driver "evtouch"
        Option "Device" "/dev/input/evtouch_event"
        Option "MinX"        "66"
        Option "MinY"        "154"
        Option "MaxX"        "4002"
        Option "MaxY"        "3987"
        Option "ReportingMode" "Raw"
        Option "Emulate3Buttons"
        Option "Emulate3Timeout" "50"
        Option "SendCoreEvents" "On"[/INDENT]

#   Behaviour

      [INDENT]  Option "longtouched_action" "down"
        Option "longtouched_button" "3"
        Option "maybetapped_action" "click"
        Option "maybetapped_button" "1"
        Option "touched_drag" "1"
        Option "oneandahalftap_button" "0"
        Option "TapTimer" "30"
        Option "LongtouchTimer"  "500"
        Option "MoveLimit"  "18"[/INDENT]
EndSection


---

### Post by v0lZy on 2008-05-03
Thanks for your settings but unfortunately nothing changes for me, my touch screen is still miscalibrated.

any other solutions?

V

---

### Post by gborzi on 2008-05-03
I think to have found a fix for the "ugly fix" for the Load_Cycle_Count growth problem. The old fix didn't worked because Hardy use pm-utils to suspend/hibernate, acpi is only used to manage battery states. Use this f```

```ix at your own risk, there isn't any guarantee that it will work and won't damage your system. If you're not scared, here is the fix:
1) Open /etc/hdparm.conf with your text editor of choice and add these lines at the end ```
/dev/sda {
      apm = 254
      apm = 255
}
```
or if there is already a /dev/sda block add the above *apm =* lines to the block. This first step ensures that when you boot your laptop it'll disable APM or at least put it at the least aggressive level.
2) Put an executable file named 99-hdparm.sh in /etc/acpi/battery.d ```
sudo touch /etc/acpi/battery.d/99-hdparm.sh
sudo chmod 755 /etc/acpi/battery.d/99-hdparm.sh
``` edit its content so that it reads as ```
#! /bin/sh
/sbin/hdparm -B 128 /dev/sda
```This ensures that on battery power the APM of your disk will be set to 128. You may change this number if you prefer a different level.
3) Put an executable file named 99-hdparm.sh in /etc/acpi/ac.d ```
sudo touch /etc/acpi/ac.d/99-hdparm.sh
sudo chmod 755 /etc/acpi/ac.d/99-hdparm.sh
``` edit its content so that it reads as ```
#! /bin/sh
/sbin/hdparm -B 254 /dev/sda
/sbin/hdparm -B 255 /dev/sda

```This ensures that on AC power the APM of your disk will be set to 254 and possibly disabled.
4) Put an executable file named 99-hdparm.sh in /etc/pm/sleep.d ```
sudo touch /etc/pm/sleep.d/99-hdparm.sh
sudo chmod 755 /etc/pm/sleep.d/99-hdparm.sh
``` edit its content so that it reads as ```
#!/bin/bash

case $1 in
   thaw|resume)
   if /sbin/on_ac_power; then
      /etc/acpi/ac.d/99-hdparm.sh
   else
      /etc/acpi/battery.d/99-hdparm.sh
   fi
   ;;
   *)
   echo "Nothing to do"
   ;;
esac
```This ensures that when exiting from hibernation the appropriate APM level will be selected.
As for hibernate/suspend, it is useless to hack /etc/default/acpi-support, this file is ignored by pm-utils. I'm reading pm-utils docs, I'll post my solution for suspend, if I'll ever find it.

EDIT: I corrected the last script adding *|resume* to the case statesment.

---

### Post by gborzi on 2008-05-03
Finally I fixed the suspend to RAM problem :popcorn:. After long readings, searching, and trying I found the solution, which is rather simple: add vga=0 to the kernel boot option. This disables the framebuffer device. First I tried it by editing the boot options at boot, to make it permanent open /boot/grub/menu.lst with your preferred text editor, go to this line ```
# defoptions=quiet splash
``` change it as ```
# defoptions=quiet splash vga=0
``` finally run ```
sudo update-grub
```
I hope this fix will work on other TX1000 variants, and that it will continue to work on mine.

---

### Post by brian.t on 2008-05-03
The vga=0 in my boot parameters allowed me to suspend and resume!
I have a weird problem with the video when suspending, I get thin blue lines and on resume I see the multicolored pattern start and then quickly go away.  Before the vga=0 the screen would stay multicolored on resume and then I had to reboot to undo.

I found through more experimenting that it won't consistently resume. I don't know why. I think I might go back to 7.04

I am using a tx1127cl

---

### Post by mkarnicki on 2008-05-04
GBorzi, since you're one of the most active and competent persons here in this area, it would be cool if you glanced this web page:

[http://www.samwel.tk/laptop_mode/faq](http://www.samwel.tk/laptop_mode/faq)

It may have some valuable news. I just don't have enough time right now, although I've quickly went through it already.

EDIT: By the way, your vga=0 tip worked for me to suspend and resume. But it didn't work again. I'll check l8r if it works consistent, but you already got few 'thank you's from me :)

---

### Post by gborzi on 2008-05-04
I claimed success too soon for suspend to RAM. I did some more experiment and never suspended two times in a row, except when I did the first suspend from the login window and the second one from a gnome session. The third one didn't resumed.
Possible causes and solutions:
1) Compiz => disable desktop effects (Never!).
2) The framebuffer modules loaded for the splash screen => disable the splash screen and enjoy reading the scrolling lines (Possible?).
3) VGA mode is activated once you login => Use vidmode to hardcode vga=0 in the kernel (dangerous? and possibly useless).
4) other ideas...
@mkarnicki
Thanks for the link, at a first read it seems that the package in Ubuntu is outdated and possibly broken. It is suggested to use the Debian package instead.

---

### Post by sleepingcell on 2008-05-04
> **gborzi said:**
> I claimed success too soon for suspend to RAM. I did some more experiment and never suspended two times in a row, except when I did the first suspend from the login window and the second one from a gnome session. The third one didn't resumed.
Possible causes and solutions:
1) Compiz => disable desktop effects (Never!).
2) The framebuffer modules loaded for the splash screen => disable the splash screen and enjoy reading the scrolling lines (Possible?).
3) VGA mode is activated once you login => Use vidmode to hardcode vga=0 in the kernel (dangerous? and possibly useless).
4) other ideas...
@mkarnicki
Thanks for the link, at a first read it seems that the package in Ubuntu is outdated and possibly broken. It is suggested to use the Debian package instead.

It worked for me at least three times! in a row! Thank you so much. 
However, it stoped working somehow after that. ..
Thank you very much anyway, it make me so happy for two hours.

---

### Post by sleepingcell on 2008-05-05
> **gborzi said:**
> I claimed success too soon for suspend to RAM. I did some more experiment and never suspended two times in a row, except when I did the first suspend from the login window and the second one from a gnome session. The third one didn't resumed.


Hi, it now works again, 4 times in a row. I just reinstalled package uswsusp and powersaved, and suspend (from source, because i can not get s2ram from the two deb package), and it works again today! Is the problem because of automatic change of settings for the related packages?
Thank you very much! The suspend works on my machine... at least now

---

### Post by gborzi on 2008-05-05
Hello sleepingcell,
just a few question about your experiments with sleep. Do you use compiz? I mean, did you activeted sleeping while logged into compiz or from the login window? Have you tried how it works without powersaved? Which version of suspend have you used? The last one, that is to say 0.8? BTW the uswsusp package is the name Debian gives to suspend, don't know why they changed the name. The uswsusp package version in Hardy is 0.6~cvs20070618. Strangely there is no version 0.6 for suspend from its site.

---

### Post by sleepingcell on 2008-05-05
> **gborzi said:**
> Hello sleepingcell,
just a few question about your experiments with sleep. Do you use compiz? I mean, did you activeted sleeping while logged into compiz or from the login window? Have you tried how it works without powersaved? Which version of suspend have you used? The last one, that is to say 0.8? BTW the uswsusp package is the name Debian gives to suspend, don't know why they changed the name. The uswsusp package version in Hardy is 0.6~cvs20070618. Strangely there is no version 0.6 for suspend from its site.
I am new to Ubuntu, so I can only try my best to answer your questions. My previous experiments were with using compiz (I installed compiz-fusion plugins and enabled desktop effects). Today, I tried more than 10 times, all sleeping/suspend worked except once (but I did not do anything after the failed try, but it continued to work after that). I just tried to to suspend from the login window after reading your post, and it worked. But i do not think i will log out and then suspend, so I did not do more experiments from the login screen.
I did not try without powersaved. I am using suspend version 0.8. I understand uswsusp is suspend, but I can not get s2ram program by installing uswsusp. However, powersaved seems not happy without uswsusp (I forgot the warning/error message), so I installed both suspend (from  source) and uswsusp. 
by the way, I am using the nvidia-glx-new driver, with kernal option vga=0 as you suggested. 
I hope my information could help you to develop more sophisticated solution.

---

### Post by moob on 2008-05-05
> **v0lZy said:**
> Thanks for your settings but unfortunately nothing changes for me, my touch screen is still miscalibrated.
any other solutions?

Try to change xorg.conf like this:
```

#   Behaviour
        Option "longtouched_action" "down"
        Option "longtouched_button" "3"
#        Option "maybetapped_action" "click"
#        Option "maybetapped_button" "1"
        Option "touched_drag" "1"
        Option "oneandahalftap_button" "0"
        Option "TapTimer" "30"
        Option "LongtouchTimer"  "500"
        Option "MoveLimit"  "3" # [COLOR="Red"]THIS IS THING WHAT YOU NEED TO CHANGE[/COLOR], I THINK
```

I get calibrate script to work but i recognized as better to play with these numbers manually (trust me I many times switched to tty2 and typed /etc/init.d/gdm restart ... :))
My final calibration work perfect (except bottom left corner - don't know why):
```
        Option "MinX"        "30"#"60" These values were measured by calib.
        Option "MinY"        "100"#"142"
        Option "MaxX"        "4000"#"4001"
        Option "MaxY"        "3970"#"3969"
```

---

### Post by gborzi on 2008-05-05
Thanks a lot sleepingcell, it seems that suspend (the last version or even 0.7) can be the solution for sleep and hibernate. I'll try to make a package for suspend 0.8 using debian package for 0.7.

---

### Post by outferno on 2008-05-05
Hey guys, I finally updated to 8.04 Hardy Heron (32bit).  A few things I've noticed: 

1)  Whenever I boot into Ubuntu, I get a bunch of lines going across my screen and up and down.  This also happens on shut down.

2)  The nVidia drivers mess up the terminals when I use ctl-alt-f1 etc.

3)  The nVidia drivers also mess up the shut down splash, the Ubuntu logo is not centered and everything looks strange.

Anybody have a solution to the drivers?  I'm working on getting the wireless and touch screen working ATM and I know there are fixes for that :)

---

### Post by pmaconi on 2008-05-05
As an answer to your second question, if you mean that ctrl-alt-f1 shows a blank screen, you can use nvidia-glx instead of nvidia-glx-new (you can install it through synaptic). Once that is done, open up /etc/X11/xorg.conf and add the following line to the "Device" section.> Option "AddARGBGLXVisuals" "True" This may also fix your first problem, but I'm not 100% sure.


The third problem can be fixed by editing /boot/grub/menu.lst. Add the following value to the kernel line of your normal boot parameters.> vga=729 That value isn't perfect (I couldn't find a vga equivalent for 1200x800), but it is equivalent to a 1024x768 resolution. That section of my menu.lst looks like the following.
> title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1e9ff759-fd3f-4fcb-9020-5b71e3a9c556 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

---

### Post by moob on 2008-05-06
> **v0lZy said:**
> Thanks for your settings but unfortunately nothing changes for me, my touch screen is still miscalibrated.
any other solutions?
V
Well, I think I can help you. I used both egalax and evtouch drivers on my touchscreen. 
What it is doing when you press the screen? Nothing; just click; just moving on bottom horizontal panel; moving in bad orientation; jumping over about 50 pixels; moving fine but in another place than your cursor is? I had to find solutions for listed errors during my success story. ;)

---

### Post by WildcatWhiz on 2008-05-06
Does anyone have an update to getting touchscreen to work on 64 bit? I got some help back on page 87 but it seems the methods might have changed since gborzi's post with evtouch_drv.so.gz and patch. How does this change things?

BTW, I wouldn't ask twice, but I had to do a fresh install. 

Thanks!

---

### Post by moob on 2008-05-06
If you want I can help you with evtouch driver. But I don't know if it is working correctly on 64x. Where did you end in installation? If it is callibration, there are few thing where can i help you.

---

### Post by WildcatWhiz on 2008-05-06
That's just it. I don't know where to start. Gborzi posted a walk-thru for me a few pages back, but now there's the new evtouch driver he posted. I installed input-evtouch from Synaptic. Now what?

Thanks.

---

### Post by gborzi on 2008-05-06
> **WildcatWhiz said:**
> That's just it. I don't know where to start. Gborzi posted a walk-thru for me a few pages back, but now there's the new evtouch driver he posted. I installed input-evtouch from Synaptic. Now what?

Thanks.
After installing from synaptic you should do the configuration as explained before. After your configuration is OK, you may want to use the evtouch_drv.so I posted previously. This new driver (for 64 bit) fixes the rotation problem reported [here]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-evtouch/+bug/222164"), it is not needed to configure the driver.

---

### Post by WildcatWhiz on 2008-05-06
What do you mean by use evtouch_drv.so? Also, to calibrate, must I run that horrible 5 X thing? Does TouchKit work like it did in Gutsy? That 25 point calibration rocked. Thanks again.

---

### Post by gborzi on 2008-05-06
> **WildcatWhiz said:**
> What do you mean by use evtouch_drv.so?
I mean download and gunzip it and place it under /usr/lib/xorg/modules/input, which will fix the touchscreen when it is left or right rotated. If you don't use these rotations you don't need evtouch_drv.so.

> Also, to calibrate, must I run that horrible 5 X thing?
Yes, you need the horrible 9 X thing (not 5).
> Does TouchKit work like it did in Gutsy? That 25 point calibration rocked. Thanks again.
I don't know, I've never used egalax drivers.

---

### Post by moob on 2008-05-06
Hello,
for those who wants to try new TouchKit 2 there is pre-release:
[TouchKit-2.02.1615-64b-k26-x14]("http://share.honoris-rytiri.cz/TouchKit-2.02.1615-64b-k26-x14.tar.gz")

Sir GIUSEPPE BORZI was faster... ;o)

Dear WildcatWhiz try to follow again his tutorial. It is all in it. If you will have some identifiable problem, tell to us.

---

### Post by FreakyT on 2008-05-06
> **moob said:**
> Hello,
for those who wants to try new TouchKit 2 there is pre-release:
[TouchKit-2.02.1615-64b-k26-x14]("http://share.honoris-rytiri.cz/TouchKit-2.02.1615-64b-k26-x14.tar.gz")


Do you have the 32-bit version, by any chance?

---

### Post by mohawk.drummer on 2008-05-06
Alright i don't know what i'm doing wrong. I'm running hardy 8.04(32-bit). I've followed the various steps as closely as possibly... I've had to recover from some sort of mishap with my nvidia drivers. Even after all that i still can't get the touchscreen to full work. I get a successful click event but nothing else. no movement or anything. i've done calibration (although i don't think it worked since i got min 20000 and max 0 x and y). I have a feeling it's something i've done wrong in my xorg.conf file so i'll post it (for now i've used other people's calibration). Maybe a quick recap or step by step instruction for hardy 32-bit would help greatly(if anyone has the time) thanks for the help ```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg



Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	
	Defaultdepth	24
EndSection

Section "Device"
	Identifier "Videocard0"
	Driver "nvidia"
	VendorName "NVIDIA Corporation"
	BoardName "GeForce Go 6150"
	Option	"NoLogo"	"True"
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x800 +0+0"
	Identifier "Screen0"
	Device "Videocard0"
	Monitor "Monitor0"
	DefaultDepth 24
	Option "TwinView" "0"
#	Option "metamodes" "1280x800_60 +0+0"
	Option "RandRRotation" "on"
	SubSection "Display"
		Depth 24
		Modes "nvidia-auto-select"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
#  screen "Default Screen"
	Screen 0 "Screen0" 0 0
	Inputdevice	"Synaptics Touchpad"
	InputDevice	"touchscreen"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "InputDevice"
        Identifier "touchscreen"
        Driver "evtouch"
        Option "Device" "/dev/input/evtouch_event"
        Option "MinX"        "66"
        Option "MinY"        "154"
        Option "MaxX"        "4002"
        Option "MaxY"        "3987"
        Option "ReportingMode" "Raw"
        Option "Emulate3Buttons"
        Option "Emulate3Timeout" "50"
        Option "SendCoreEvents" "On"
        Option "MoveLimit"    "4"
#        Option "Calibrate" "1"
EndSection
```

---

### Post by WildcatWhiz on 2008-05-07
Alright, now it's my turn to give back...

Attention all Hardy 64 users! The new TouchKit drivers work WONDERFULLY. 

> **moob said:**
> Hello,
for those who wants to try new TouchKit 2 there is pre-release:
[TouchKit-2.02.1615-64b-k26-x14]("http://share.honoris-rytiri.cz/TouchKit-2.02.1615-64b-k26-x14.tar.gz")


-Save the folder. 
-Cd to the place you saved it. 
-Run sudo ./setup.sh. Do NOT tell it to blacklist anything. -Gedit your xorg and make sure the egalax is included as the following

```
Section "InputDevice"
    Identifier     "EETI"
    Driver         "egalax"
    Option         "Device" "/dev/usb/hiddev0"
    Option         "Parameters" "/var/lib/eeti.param"
    Option         "ScreenNo" "0"
EndSection
```

The make-or-brake for me was adding the Device Option "/dev/usb/hiddev0"

Good luck.

(P.s. I hate using evtouch drivers because it is absolutely ridiculous that to calibrate you have to kill X and press 9 ugly little X's. Egalax Touchkit calibration is a breeze. )

---

### Post by dhjort on 2008-05-07
Thanks WildcatWhiz ! It worked straight up for me ! :-) 

Finally a simple and straight installation and working without glitches. 

Did have to change the "usbauto" to "/dev/usb/hiddev0" also, but other than that it just works ! 

Now most things actually works ! :guitar:

---

### Post by moob on 2008-05-07
> **FreakyT said:**
> Do you have the 32-bit version, by any chance?
If you want it, you have to send message to the creator like me. Thats all. He will send it to you. After that you could post it here. 

@mohawk.drummer:
Hey, I think you modified /etc/modprobe.d/blacklist aren't you?
There must NOT be this:
blacklist usbtouchscreen
blacklist tkusb
blacklist touchkitusb

If you have it there, comment it or just delete.

---

### Post by moob on 2008-05-07
For those who are playing with "s2ram thing", here is a package I have tested and it is working propertly:
[uswsusp_0.8-0.1_i386.deb]("http://www.teco.edu/~biebl/debian/uswsusp/1-split-patches/uswsusp_0.8-0.1_i386.deb")

---

### Post by CyberLeader on 2008-05-07
thanks moob for the 64 hardy bit touchkit drivers, has anyone found a solution to the issue where it keeps registering taps as double clicks? Other than that it's great, i sure do miss the accuracy of 25 point calibration. :)

---

### Post by WildcatWhiz on 2008-05-07
> **dhjort said:**
> Thanks WildcatWhiz ! It worked straight up for me ! :-) 

Finally a simple and straight installation and working without glitches. 

Did have to change the "usbauto" to "/dev/usb/hiddev0" also, but other than that it just works ! 

Now most things actually works ! :guitar:

Ack! That's what I meant. Change it in the device option AND change usbauto (the latter is the more important, I believe.)

Thanks!

---

### Post by moob on 2008-05-07
> **CyberLeader said:**
>  i sure do miss the accuracy of 25 point calibration. :)
As George Li (george[A]eeti.com) said: This is some cind of pre-release. If there will be final 2 version it will be placed on website. 
As Egalax team wrote:
Please feel free to contact our touch_fae[A]eeti.com if you need .

---

### Post by mohawk.drummer on 2008-05-07
Thanks for the response moob but no luck. I do remember modifying the blacklist file but it just made things worse so i undid that. I checked through it again but couldn't find anything. Any other suggestions? this is really bugging me. I might just do a fresh install and try again. Also i forget to mention before i'm using the 0.8.7 evtouch drivers. Hope someone can figure out what i've done. Even if someone could make a checklist or something of the steps for 32 bit hardy... thanks again

---

### Post by moob on 2008-05-07
You don't need no, re-installation...:rolleyes:
try this and repeat:
```
sudo apt-get purge xserver-xorg-input-evtouch
sudo apt-get install xserver-xorg-input-evtouch
```
Elsewhere I can't help you. I had a lot of problems during my installation. But you found another.

---

### Post by mohawk.drummer on 2008-05-07
Well it recognizes my click events but it won't move the cursur at all. Only my touchpad will move the cursur. any ideas?

---

### Post by outferno on 2008-05-07
Hey guys, so I got the wireless working using sauronsmatrix's post over here:

[Get Wireless Working]("http://ubuntuforums.org/showpost.php?p=3491929&postcount=257")

However, one thing I'm trying to figure out and it's a total noob thing: every time I start up Hardy, even with my power adapter plugged in... my screen is dimmed to 50%.  Anybody know how to change this to always be at 100% brightness when plugged in?

---

### Post by moob on 2008-05-07
@mohawk.drummer:
I had the same problem. It goes away after I removed row 
```
Option "Calibrate" "1"
```
from /etc/X11/xorg.conf. Or was it with blacklist as I post page before?

> **outferno said:**
> 
However, one thing I'm trying to figure out and it's a total noob thing: every time I start up Hardy, even with my power adapter plugged in... my screen is dimmed to 50%.  Anybody know how to change this to always be at 100% brightness when plugged in?
I don't know if is that bug in Power Manager Brightness Applet 2.22.1 what I know. But. If you use that applet and drag rider to the bottom creen is dark "forever". You have to change it's config... For another talking.
You have to click on System/Preferences/Power Management and uncheck **Dim display when idle** (both) and "**Put computer to sleep...**" set to Never. I googled it and it helps me.
Send me a report.

---

### Post by fuzzyLogicXtrm on 2008-05-07
I want to install Ubuntu on my TX1410US and I was reading that some of you uses the 32 bits version and others the 64 bits.

Which is better in order to make the installation easier? I mean, I don't care to install the 32 bit if all the process of installation is more straightfoward.

---

### Post by mkarnicki on 2008-05-07
I'm using evtouch drivers. On the previous page I read that there is a new pre-release of egalax drivers. But does it still recognize taps always as double clicks? Cose with GBorzi we managed to get evtouch working very well (click, double click, rightclick) and I'd totally loose myself if I found installing egalax would make my touchscreen work worse :D I mean, I'm really feeling well with what I've got now.

How is egalax better then evtouch (forget the 'ugly' calibration, I'm OK with that)?

---

### Post by outferno on 2008-05-07
> **moob said:**
> I don't know if is that bug in Power Manager Brightness Applet 2.22.1 what I know. But. If you use that applet and drag rider to the bottom creen is dark "forever". You have to change it's config... For another talking.
You have to click on System/Preferences/Power Management and uncheck **Dim display when idle** (both) and "**Put computer to sleep...**" set to Never. I googled it and it helps me.
Send me a report.

Hrm - I'm not sure if it's the same bug - but after a restart my screen is still dim and I have to turn the brightness up manually.

Edit:  I'm not sure what I did, but maybe because I shut down after changing t he brightness and then let did booted the machine up - the brightness level has stayed at maximum.

---

### Post by mohawk.drummer on 2008-05-07
> **moob said:**
> @mohawk.drummer:
I had the same problem. It goes away after I removed row 
```
Option "Calibrate" "1"
```
from /etc/X11/xorg.conf. Or was it with blacklist as I post page before?

Neither worked. thanks for your help though. anyone have anymore ideas...i might try out the egalex drivers or install a fresh copy of hardy (it's possible i did something when my xorg.conf got all messed up. hopefully someone can help me out

---

### Post by waspbr on 2008-05-08
hello everyone,  damn i've been away for a few weeks and this thread is already close to 100 pages. anyway, I am on a 64 bit hardy now and things have been working rather well, wireless was fixed with ndiswrapper and all , however I gto a a small issue with the touch screen.

I used the touchkit method posted a few pages back, which seemed to work wonderfully, however i keep getting some little blocks everytime I do stuff in the desktop

[[IMG]http://img291.imageshack.us/img291/360/blocksjz9.th.png[/IMG]](http://img291.imageshack.us/my.php?image=blocksjz9.png)

I  am not sure why this is happening but does anyone have a fix for this? thanks

l8er

---

### Post by cabernet54 on 2008-05-08
> **waspbr said:**
> 
I  am not sure why this is happening but does anyone have a fix for this? thanks

l8er

Perhaps you have the "nvidia-glx-new" with hardy restricted driver?

If yes, is better "nvidia-glx", older driver but work very well with our graphic hardware. (thank Gborzi ):P )

:)

---

### Post by outferno on 2008-05-08
So I'm still having video driver problems - I suspect others are as well.  I tried to download a set of drivers from the nvidia website that were older made for the GeForce 6, but they didn't work :(.  I want to love Ubuntu, but it won't let me :(

---

### Post by daniel-amristar on 2008-05-08
Anyone care to comment on suspend/hibernate under Hardy for the tx1000?

I have a tx1000 (tx1222au) and both suspend and hibernate are broken.

Both appear to work and the laptop shuts down. However, both hang when attempting to restart...

---

### Post by mohawk.drummer on 2008-05-08
before i go and install hardy again, can anyone confirm that evtouch drivers work under hardy 32-bit? it's obvious it works on 64 but maybe theres some sort of bug in the 32-bit. If anyone has managed to get it working let me know please. thanks

---

### Post by tarsius4 on 2008-05-08
> **outferno said:**
> So I'm still having video driver problems - I suspect others are as well.  I tried to download a set of drivers from the nvidia website that were older made for the GeForce 6, but they didn't work :(.  I want to love Ubuntu, but it won't let me :(

I just looked back at your old posts and I'm confused... is your "nVidia problem" just the ctrl-alt-Fx terminal garbling?  I ask because just today I fixed a problem with my tx1000 where I couldn't get an nVidia driver installed... I could select it in the System>Administration>HW Drivers panel, and it SAID that the proprietary driver was in use.  However, when I attempted to run nvidia-settings, I was told that the driver was not configured and that I should run nvidia-xconfig. Running nvidia-xconfig had no effect and I believe that the computer was *trying* to load the nvidia drivers at power-on, but the screen would flicker three times over the course of 10-15 seconds, and ultimately I would brought into GNOME at 800x600 w/no hardware acceleration.

If this sounds like the problem you are having, try these instructions to get the driver off the nVidia website to work: 
[http://ubuntuforums.org/showpost.php?p=4841674&postcount=21](http://ubuntuforums.org/showpost.php?p=4841674&postcount=21)

I know you mentioned that you already tried the driver from the website, but maybe this time it will work.

---

### Post by zackymcharvest on 2008-05-08
How do you calibrate the touch screen using touchkit pre-release? I did the install but I am a noob so I don't know how to calibrate.

---

### Post by alex sun on 2008-05-09
Hi, everyone!
I'm a new user of Hardy 64 on tx1000.
Thanks a lot to everyone in this thread - my wi-fi works now! :)
Could you please also help with touchscreen?

As proposed several posts above, I downloaded TouchKit-2.02.1615-64b-k26-x14 and run ./setup
Then I chose option 3 - USB and did NOT blacklist anything.
The next step I edited my xorg, so now InputDevice section now looks:

```

Section "InputDevice"
    Identifier     "EETI"
    Driver         "egalax"
    Option         "Device" "/dev/usb/hiddev0"
    Option         "Parameters" "/var/lib/eeti.param"
    Option         "ScreenNo" "0"
EndSection

```

After that I tried to touch the touchscreen and my X nearly died (only mouse worked, all windows became frozen).
Then after restarting X, I launched TouchKit and successfully calibrated the touchscreen (both 4 and 25 precision).
After 3 minutes of work with wonderfully calibrated touchscreen, X died again.
And after the reboot I realized that TouchKit doesn't run anymore - simply nothing happens when I try to run it.
My touchscreen is non calibrated at all now and using it kills X in 5 minutes.
When I don't touch the touchscreen, X works fine for hours.
System is new, I just installed it 2 days ago and didn't change anything except wi-fi and touchscreen.

What should I do to make the touchscreen work?
Thanks in advance!

---

### Post by moob on 2008-05-09
> **outferno said:**
> So I'm still having video driver problems - I suspect others are as well.  I tried to download a set of drivers from the nvidia website that were older made for the GeForce 6, but they didn't work :(.  I want to love Ubuntu, but it won't let me :(

There is another thing, what you can try. 
```
sudo apt-get install envyng-gtk
```
It can do everything with just few clicks. 


> **mohawk.drummer said:**
> before i go and install hardy again, can anyone confirm that evtouch drivers work under hardy 32-bit? it's obvious it works on 64 but maybe theres some sort of bug in the 32-bit. If anyone has managed to get it working let me know please. thanks

I'm using 32-bit and evtouch. I had problems with installation but it is because of problems between my keyboard and my chair.


**QUESTION FOR 64-bit users:**
You who are using 64-bit, why did you choose this. I don't think there are so much benefits for me in it (I have just 1GB RAM). Do you have any problems with installed software? Thx

---

### Post by outferno on 2008-05-09
> **tarsius4 said:**
> I just looked back at your old posts and I'm confused... is your "nVidia problem" just the ctrl-alt-Fx terminal garbling?  I ask because just today I fixed a problem with my tx1000 where I couldn't get an nVidia driver installed... I could select it in the System>Administration>HW Drivers panel, and it SAID that the proprietary driver was in use.  However, when I attempted to run nvidia-settings, I was told that the driver was not configured and that I should run nvidia-xconfig. Running nvidia-xconfig had no effect and I believe that the computer was *trying* to load the nvidia drivers at power-on, but the screen would flicker three times over the course of 10-15 seconds, and ultimately I would brought into GNOME at 800x600 w/no hardware acceleration.

If this sounds like the problem you are having, try these instructions to get the driver off the nVidia website to work: 
[http://ubuntuforums.org/showpost.php?p=4841674&postcount=21](http://ubuntuforums.org/showpost.php?p=4841674&postcount=21)

I know you mentioned that you already tried the driver from the website, but maybe this time it will work.

YES!  Thank you, that fix worked!  Hardy Heron now recognizes the hardware and has no driver conflict!  Last time I tried it, I didn't know that I could disable a certain set of drivers, but that link showed me how.  Now when I boot up, the nvidia logo comes up!  :)

Thanks again!

Edit: Ah crud, I spoke too soon.  I still have the issue with ctl+alt+fn1-6 being strange.  Also, when I come back from a screen saver, I have to go to tty(1-6) and back to ctl+alt+fn7 to get everything to look right.  Then when I shutdown, I get wavy lines and the splash isn't centered.  Weird problem, it didn't do this in Gutsy :(

---

### Post by mohawk.drummer on 2008-05-09
alright so i've had some slight success with my touch screen. I've managed to get uncalibrated movement but when i use the output from calibrate.sh it results in just click events and no movement what so ever(which was my problem before). Now either calibrate.sh still doesn't work since 0.8.6 or i'm not entering the settings properly or something. I also found that when trying to calibrate it is difficult to actually get a click event on the x. One more thing. When i did run calibrate.sh i tried to calibrate properly then i also tried calibrating by just doing circles on the screen and it gave me the exact same out which i'll post. Any one have an idea as to whats going on? 
```
        Option        "MinX"        "20000"
        Option        "MinY"        "20000"
        Option        "MaxX"        "0"
        Option        "MaxY"        "0"
        Option        "x0"        "-1275"
        Option        "y0"        "-795"
        Option        "x1"        "-640"
        Option        "y1"        "-795"
        Option        "x2"        "-5"
        Option        "y2"        "-795"
        Option        "x3"        "-1275"
        Option        "y3"        "-400"
        Option        "x4"        "-640"
        Option        "y4"        "-400"
        Option        "x5"        "-5"
        Option        "y5"        "-400"
        Option        "x6"        "-1275"
        Option        "y6"        "-5"
        Option        "x7"        "-640"
        Option        "y7"        "-5"
        Option        "x8"        "-5"
        Option        "y8"        "-5"
```
thanks

---

### Post by twistadias on 2008-05-09
anyone managed to get spidf sound working. I got it working with this:
[http://ubuntuforums.org/showthread.php?p=4451132](http://ubuntuforums.org/showthread.php?p=4451132)

But after that all the sound gets routed through the spdif jack. Is there anyway I can switch between spdif and the laptop speakers??
Any help would be appreciated

---

### Post by v0lZy on 2008-05-10
Thanks for the information moob.

I tried the pre-released driver and I got the same problem as waspbr (with the selection rectangles, however i believe that to be an nvidia issue). However, my Y axis is inverted. When I slide the pen from the top of the screen (landscape mode) down, the cursor starts moving from the bottom (not where i touched the screen) and meets the pen in the middle... and passes it upwards as i drag the pen down. X axis is ok.

Apart from that, the cursor is a bit short from all the edges of the actual display area.

I do not know how to make a calibration using egalax drivers. As far as i understand, one driver is evtouch and the other is egalax. Egalax responds way better and smoother but im experiencing the problems mentioned above. evtouch i could not even calibrate (as per my previous post).

Also i noticed i have a:

Option "Parameters" "/var/lib/eeti.parm"

listed in the input device section of the EETI identifier, but I wasnt able to locate that file. I suppose that has something to do with the calibration?

Any ideas how to get some kind of calibration utility for egalax pre released driver? i tried in combination with evtouch but either thats impossible or I was doing it wrong.

Im using hardy 64.

help appreciated

cheers,

V

PS> someone mentioned running 25 point calibration with TouchKit after restarting X... is that something else that runs inside X or part of the evtouch driver (the ./calibrate.sh thing?) I cant see a 25 point calibration, just the standard 9 i get by default. If its an entirely different thing, where can i get it?

PS> Found the TouchKit is the tar.gz file inside the first one. Trying to figure out how to install/run the thing. Any advice?

PS> Never mind, found the binary there too :D

PS> WORKS LIKE A CHARM!

---

### Post by v0lZy on 2008-05-10
Spending a few hours with the working touchscreen by use of egalax drivers and included TouchKit utility, i have the following to report>

1. Clicking behavior is somewhat strange... not exactly sure how to describe it but menus from the panels (applications, places, system) close when i lift the pen. Also I cant open files by taping on them twice.

2. The selection squares on the desktop mess everything up

3. I think the issues may be interconnected.

Anyone with similar issues who has been able to resolve this... and how?

Cheers, this is the best community ever

V

---

### Post by jsast21 on 2008-05-11
problem with setting up the touchscreen - I tried the steps from the link to the German instructions (with the helpful translate.google.com to make sure my German was not that rusty) and they did not work for me. Nothing failed, but the touchscreen just did not work. But now I have a problem in that for some reason my HD light will not turn off. It is blinking all the time. Not a big deal if the touchscreen doesn't work - but I'm concerned about this new problem.

---

### Post by gudwin on 2008-05-11
Hi ! Do someone know which is the latest beta Egalax driver (TouchKit) which is being referred in this thread ? The only one I could grab from internet was 2.01.1512, which someone made available somewhere for download (I cannot find the exact link right now, but I arrived there from a post at this thread). But it seems there is a newer driver circulating also, 2.02.1615, at least for the 64bits (not sure if for the 32 bits also). I wrote to [email]touch_fae@eeti.com[/email] asking for some information, but they didn't replied. I'm looking for the 32 bits version of the driver. I tried, but couldn't manage to make evtouch driver to work, so I gave up on it. The egalax driver works (at least the 2.01.1615 which I could get), but still with the problem of having 1 tap = double click, which forbids any serious work with the touchscreen. I was also having a strange delay when moving the cursor around the touchscreen with the pen. It takes 1 or 2 seconds to move the mouse cursor to the right position, just as if there was a delay in getting the touchscreen coordinates. Maybe the newer beta version that is circulating already solved these problems ? I have a tx1320us with Hardy Heron Kubuntu - 32 bits. Do someone know where we can get these newer beta drivers for 32 bits ? Is it the [email]touch_fae@eeti.com[/email] the right address to ask for the beta drivers ? Those of you who could get a reply from Egalax would post this information for us ? Best regards !

---

### Post by saltynay on 2008-05-12
I have tried following several guides to setting up my TX1000 with hardy heron but can't seem to get the touchscreen nor the wireless to work :confused:

---

### Post by mkarnicki on 2008-05-12
Geee, I'm using evtouch driver on tx1320us and I'm glad my touchscreen works fine :) (Cheers GBorzi :) ).

---

### Post by waspbr on 2008-05-12
yo mkarnicki


i got the same model as you do you have this problem with the touchcreen?
[http://ubuntuforums.org/showpost.php?p=4908472&postcount=979]("http://ubuntuforums.org/showpost.php?p=4908472&postcount=979")

as always the problem is compiz related since i dont have that issue in kubuntu or xubuntu... i am using the glx new drivers , tried selecting the glx old in synaptic but they did not adjust well... (should i use envy?) my cairo dock got all fuzzy and my windows headers got weird too.

saltynay

do 
```
lspci
```

in terminal and post which versio of the wireless card u have 
it will say broadcom 43## where the ## should defined the version of your card.

as for the touchscreen, the method that has been discussed in the past couple of pages works. though i am on hady 64 and not 32

---

### Post by gborzi on 2008-05-12
I've not posted in these days because I've tried to fix the suspend to RAM issue. I tried everything, from kernel options to uswsusp 0.8, but nothing works consistently, i.e. sometimes the laptop resumes, sometimes not. Anyway, I learned something on kernel options and suspend :lolflag:. Between a failed resume and a reboot I managed to make a package for the evtouch driver that includes my patch for the left and right rotation and adds a udev rules for the device, like the 69-touchscreen.rules. The package is attached to this post. Before installing it remove the file 69-touchscreen.rules from /etc/udev/rules.d. It doesn't change the calibration procedure, also known as "the horrible 9 X thing" :) (I like this name for evtouch calibration, no offence WildcatWhiz).
I would like to update my BIOS, currently I have version F.1B and the latest one is F.1F. Unfortunately, HP releases the new BIOS with a program that requires Vista to work (and I razed it to the ground just after I got the laptop), so it is not possible to use the method that employs a CD with a dos image. Does anyone have a suggestion on how to make the BIOS update?

---

### Post by v0lZy on 2008-05-13
waspbr, I have the same problem as you do with the image you posted. The problem is not compiz related. I've set my window manager to Metacity (in gnome) and the problem with the selection squares persists.

I think its an nvidia thing. I can replicate it with the mouse sometimes when logging into gnome and clicking and dragging my mouse. What happens is that the selection bracket stays on screen, but other than that once the initial startup is complete, it is no longer an issue and i cant replicate it.

If u get the same thing under KDE as I do under gnome, then i suppose its an nvidia driver issue since I've been noticing this before I installed the egalax drivers.

Do u get the same with the NV driver? 
Does anyone have a solution to dealing with the egalax drivers mouse behavior? 

Every time i touch the screen it registers what i think is a doubleclick which is also perhaps among the reasons for the brackets. 
In a sense a touchscreen is slightly different from a touchpad since u have to simulate buttons > doubletap should be a double click, single tap should be a single click (the difference between 2 singleclicks/taps and 1 doubleckick/tap being the time interval they are preformed in). By that i guess that touching the screen and moving the pen without lifting it should represent movement the same as moving a mouse or sliding a finger on the touchpad. However, how does then one click & hold and drag? > I suppose its a matter of doubletapping where u do not lift the pen on the second tap but proceed to drag it as you would when moving the cursor ... and that is exactly what appears to be happening when i touch my screen and get those rectangles. My touch represents a click and hold event of a normal mouse or touchpad because i hold the pen to it. On the other hand it could represent what i believe was mentioned in connection with the evtouch drivers as one-and-a-half click.  

Can anyone provide any help on this issue? Could it have to do with the fac thtat we were using evtouch before and are now using egalax and the "uninstall" was somehow not "clean" ?

Cheers,

V

---

### Post by saltynay on 2008-05-13
> **waspbr said:**
> yo mkarnicki
saltynay

do 
```
lspci
```

in terminal and post which versio of the wireless card u have 
it will say broadcom 43## where the ## should defined the version of your card.

as for the touchscreen, the method that has been discussed in the past couple of pages works. though i am on hady 64 and not 32

I tried to follow your guide but on of the links was broken so I manually found the egalax page got the latest driver and followed you instructions
[http://ubuntuforums.org/showpost.php?p=4413930&postcount=652](http://ubuntuforums.org/showpost.php?p=4413930&postcount=652)
I then got the About dialogue but the apply button is shaded out :confused:
I cant seem to get the calibration to work either tried doing sudo full root name and sudo TKCal /dev/ttySO Linz

---

### Post by moob on 2008-05-13
Ciao,
I don't have much time for now. Sorry that I can't reply all the things you'we asked.
> **gborzi said:**
> 
...suspend to RAM issue...
..."the horrible 9 X thing"...
...update BIOS. Does anyone have a suggestion on how to make the BIOS update?...
I wish you a lot of luck during your suspend-times. :) I can't do progress any more in this thing.
"*the horrible 9 X thing*" =D>
I have installed WinXp because of that BIOS update (and because I can't run Wiedzmin (game) under the Ubuntu and my girlfriend likes it). That XP's are not so huge if you cut off all that unimportant things. I still hope that HP will rapair that silly BIOS BUG.


> **v0lZy said:**
> 
...In a sense a touchscreen is slightly different from a touchpad since u have to simulate buttons > doubletap should be a double click, single tap should be a single click (the difference between 2 singleclicks/taps and 1 doubleckick/tap being the time interval they are preformed in). By that i guess that touching the screen and moving the pen without lifting it should represent movement the same as moving a mouse or sliding a finger on the touchpad. However, how does then one click & hold and drag?...

I think there is a some device you have to disable (somehow) in xorg.conf. I can't tell you more now because I don't have my little Pauline nearby. Maybe tomorrow.

---

### Post by tarsius4 on 2008-05-13
> **outferno said:**
> YES!  Thank you, that fix worked!  Hardy Heron now recognizes the hardware and has no driver conflict!  Last time I tried it, I didn't know that I could disable a certain set of drivers, but that link showed me how.  Now when I boot up, the nvidia logo comes up!  :)

Thanks again!

Edit: Ah crud, I spoke too soon.  I still have the issue with ctl+alt+fn1-6 being strange.  Also, when I come back from a screen saver, I have to go to tty(1-6) and back to ctl+alt+fn7 to get everything to look right.  Then when I shutdown, I get wavy lines and the splash isn't centered.  Weird problem, it didn't do this in Gutsy :(

I get the blue lines too, but it's worth it since before I had no nvidia hardware acceleration.

---

### Post by tarsius4 on 2008-05-13
Hi everyone,

Here's some info FYI in case any of this is relevant to someone else.  I've got a tx1000z and I've upgraded to Herdy 32-bit.  I started with Gutsy installed from the alternative CD.  I'd be glad to help anyone who wants more details about my setup.


Here's a list of problems I have:
-------------------------------------------------
* Crash often when using firefox, particularly when using flash to watch videos (youtube)

* Crashes involving peripherals "disconnecting" from the computer... most often wireless, also USB peripherals, and sometimes built-in keyboard and mouse.
 
* Crashes where the computer can no longer access the hard drive.  If I try to restart GNOME or switch to a terminal with Ctrl-Alt-F1, I often see a series of error messages every ~15 seconds that start with "ata1.0 ..."


...And here's problems I have but I haven't attempted to solve yet
------------------------------------------------------------------------------------
* Can't play audio simultaneously from multiple sources (I heard this is a solvable PulseAudio issue)

* Blue lines in ctrl+alt+fx consoles

* Blue lines in GNOME when screen turns on (only if the screensaver runs for several minutes)... can be temporarily solved by switching to a ctrl+alt+fx terminal then back to GNOME

* Cannot standby. Upon return, screen does not turn on

* GPU temperature (apparently my GPU temperature is 165 F right now, and it's gone as 190 F)

* Hard drive temperature is 108 F - 115 F  (is this too high)

* DVD playback was funky... HDD light blinked in a strange way (bright/dim/bright/dim/...) and the video played slowly and very choppy

* I haven't configured the touch screen yet


Some things I have gotten working
---------------------------------
* Hibernation works right from the shutdown menu (but not Standby)

* 3D hardware acceleration with the driver downloaded from the nVidia site

* Compiz Fusion works with many effects activated (in Gutsy this caused stalls and crashes, so I turned it off)

* Audio works (it was gone for a while after I installed the nVidia drivers)

---

### Post by Cuppa-Chino on 2008-05-13
[QUOTE=tarsius4;4951743


Some things I have gotten working
---------------------------------
* Hibernation works right from the shutdown menu (but not Standby)

* 3D hardware acceleration with the driver downloaded from the nVidia site

* Compiz Fusion works with many effects activated (in Gutsy this caused stalls and crashes, so I turned it off)

* Audio works (it was gone for a while after I installed the nVidia drivers)[/QUOTE]
currently on Hardy x64 xubuntu (using xfce to minimise system resource drain)
all still am struggling with the wretched nvidia drivers so here are my current aims:

a) get nvidia drivers (or other drivers) to work and to run the GPU at less than 425Mhz -- am running xubuntu do not have any composition or other stuff going, just trying to save battery power - powermizer in nvidia settings always shows maximum although it works fine on my desktop with geforce 7900gto // if I can get temp readout and low mhz on the nv driver then I do not need the nvidia driver
b) get screensaver to work with nvidia, the repository nvidia driver and the screensaver do not work -- I have to ctrl+alt+del to get out of blank screen, this is no issue with nv drivers
c) suspend and hibernate work wiht any video driver

---

### Post by alex sun on 2008-05-14
Hurray!
My touch screen started working on its own.
I did nothing at all - I simply waited for several days - and it started working perfectly calibrated absolutely without my interference.
Previously I tried to make it work with Egalax 64, but didn't succeed.
Seems, that it is required to simply do 100 reboots to make it work ))))))
Ubuntu is CRAZY system!!!!!!! ))))))))))))))))))))

Could anyone help with hibernate now?
It worked until I decided to enlarge swap from 512 to 2000 Mb.
So previously it worked only when I had not much memory to write to swap.
And after the swap enlargement hibernate doesn't work any more.
Swap is swaponed, correctly enlisted in fstab and correctly determined in system monitor.

Thanks in advance!

---

### Post by bradleyb01 on 2008-05-14
> **gborzi said:**
> I've not posted in these days because I've tried to fix the suspend to RAM issue. I tried everything, from kernel options to uswsusp 0.8, but nothing works consistently, i.e. sometimes the laptop resumes, sometimes not. Anyway, I learned something on kernel options and suspend :lolflag:. Between a failed resume and a reboot I managed to make a package for the evtouch driver that includes my patch for the left and right rotation and adds a udev rules for the device, like the 69-touchscreen.rules. The package is attached to this post. Before installing it remove the file 69-touchscreen.rules from /etc/udev/rules.d. It doesn't change the calibration procedure, also known as "the horrible 9 X thing" :) (I like this name for evtouch calibration, no offence WildcatWhiz).
I would like to update my BIOS, currently I have version F.1B and the latest one is F.1F. Unfortunately, HP releases the new BIOS with a program that requires Vista to work (and I razed it to the ground just after I got the laptop), so it is not possible to use the method that employs a CD with a dos image. Does anyone have a suggestion on how to make the BIOS update?
gborzi,

I had the same desire so I actually dual booted my tx1220 with both Vista and Ubuntu, which was the only way around the issue that I could find. A word of caution, I ended up using Vista's bcd rather than grub as a boot manager as I always was rendered unbootable (.. is that a word?) if I booted to Vista at all.

By the way, I just wiped my 386 install and went to 64 bit and am even happier with Ubuntu than I was before. I would like to see a native wireless driver though, but I will settle for ndis for now.

---

### Post by gborzi on 2008-05-14
@alex sun
I had a similar problem but it was a some time ago, so I'm not sure if the fix I'm going to suggest will work. Ubuntu uses UUID to identify partions instead of the the devices in /dev. The problem is that the UUID changes when you change the partition.
Open the file in /etc/initramfs-tools/conf.d/resume, it contains something like ```
RESUME=UUID=<letters, numbers and dashes>
``` and search for the line containing swap in /etc/fstab, then put the first field of this line after the RESUME= in the initramfs config file. Finally, run ```
sudo update-initramfs
```
hope it works.
@bradleyb01
Thanks for your answer.
I have found a Live CD with Vista (named Vista Portable Edition), it's about 135 MB and it worked fine, i.e. booted from the CD and the BIOS utility seems to work. I have made a backup of the BIOS, but I'm a little bit scared to make an update using VistaPE.

---

### Post by me.home on 2008-05-15
> **moob said:**
> There is another thing, what you 


**QUESTION FOR 64-bit users:**
You who are using 64-bit, why did you choose this. I don't think there are so much benefits for me in it (I have just 1GB RAM). Do you have any problems with installed software? Thx

I have it running on kubuntu 8.04, 64bit, 4gb ram.
no touch screen so far....

---

### Post by praveen_sreekumar on 2008-05-16
Hi all,

I'm completely new to linux, so can someone please help me with setting up drivers, etc.

I'm using TX1219au. I've installed ubuntu 8.04 within windows. What next? How to get the wireless working? Also, what else will i need to install to get the touchscreen working? Please help.

Cheers,

Praveen

---

### Post by alex sun on 2008-05-16
2 gborzi:
thanks a lot!
hibernate works fine now! :-)

By the way does anybody know how to make WEBCAM work?

2 praveen:
here is your wireless: [http://ubuntuforums.org/showpost.php?p=3491929&postcount=257](http://ubuntuforums.org/showpost.php?p=3491929&postcount=257)
and here is 64bit touchscreen: [http://ubuntuforums.org/showpost.php?p=4900007&postcount=963](http://ubuntuforums.org/showpost.php?p=4900007&postcount=963)
Good luck!

---

### Post by praveen_sreekumar on 2008-05-16
2 alex
thanks heaps buddy. just a thought, not sure if i installed the 64bit version of ubuntu. so what version should i use for the touch screen? any alternate link?

Cheers,

Praveen

---

### Post by bradleyb01 on 2008-05-16
Okay,

I was happy as a clam with Hardy 64 bit, but now, all of a sudden, my USB started acting crazy. Here is what i know to date:

USB drives and devices (USB mouse) work fine in both Vista and XP on the same machine every time I boot into either OS.

USB mouse won't work at all after logging in to Gnome, ever. I see that it is attached and lit up until I login, then it goes blank. dmesg doesn't show it as attaching at any time.

Every third or fourth time I shutdown and start up Hardy, any given USB drive will work, but if I unmount it or remove and try to reinsert it, it will not work. When it works dmesg shows that it is attached and recognized but when it doesn't, dmesg shows nothing.

Occasionally, when a drive mounts, the mouse input goes away until I remove the drive.

Any suggestions would be appreciated.

---

### Post by rikardocarvajal on 2008-05-16
you can use rmmod ehci-hcd to enable de usb dispositives

---

### Post by rikardocarvajal on 2008-05-16
I downloaded the egalax new beta 2 driver, but when i tried to compile the .ko module i have a problem

root@rikardo-laptop:/home/rikardo/Drivers/TouchScreen/32bits/TouchKit107/USBSrc# make all
make -C /lib/modules/2.6.24-17-generic/build SUBDIRS=/home/rikardo/Drivers/TouchScreen/32bits/TouchKit107/USBSrc modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-17-generic'
  Building modules, stage 2.
  MODPOST 1 modules
/home/rikardo/Drivers/TouchScreen/32bits/TouchKit107/USBSrc/tkusb: struct usb_device_id is 20 bytes.  The last of 6 is:
0x03 0x00 0x23 0x38 0x02 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 
FATAL: /home/rikardo/Drivers/TouchScreen/32bits/TouchKit107/USBSrc/tkusb: struct usb_device_id is not terminated with a NULL entry!
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-17-generic'
make: *** [all] Error 2
root@rikardo-laptop:/home/rikardo/Drivers/TouchScreen/32bits/TouchKit107/USBSrc# 

somebody know whats happen.?

---

### Post by gborzi on 2008-05-16
@bradelyb01
I have had a similar problem with USB with my older laptop (a Compal HEL81) when I repeatedly connected and disconnected a 7-ports usb hub (actually this is made by two 4-ports hubs packaged toghether) or when I connected/disconnected a problematic device, like my old DL-204 USB DSL modem. In these cases dmesg gave an error message ending with -110. The only way to fix the problem for me was to unload and reload usb modules.
I hope the fix suggested by rikardocarvajal, which is simpler to apply, will work on your system. As for the problem of the non-working mouse when a drive (I suppose you mean an usb disk or dvd drive) is connected, it can be a power issue, i.e. the drive needs so much power that none is left for the mouse. Note that the touchscreen, camera, bluetooth and fingerprint reader are all internally connected usb devices.
Just my 2 cents.

---

### Post by generalj on 2008-05-16
Could someone with Ubuntu 64 bit that has touchscreen working with the prerelease egalax touchkit drivers post their xorg.conf and /etc/modprobe/blacklist ?

I am having the same problems as wasbr with the blue squares staying on the screen and then the desktop going unresponsive. 

Desktop stays fine if I dont use the touchscreen but as soon as I use it it freezes and I have to goto a console and restart gdm.

Anyways I tried nividia-glx and nvidia-glx-new from envy and they both caused the same problems. I am wondering if my blacklist and/or xorg.conf is setup wrong.

Thanks.

---

### Post by edu90cb on 2008-05-17
Hello guys.! I've got a Tx1000z series, mine is the tx1332la, i'm in Venezuela. I'll talk you a little of my experience.

First, I wanna dual boot Linux - Windows, so I tried OpenSuse, the results? A MESS, no boot, no sound, no wifi, no nothing.! so. Recovered partitions, mbr, etc.

Second, Downloaded Ubuntu 8.04 x86_64, Burn it, Boot it (without disabling acpi or any other thing), Installed it without error, Re-Boot, Install Ndiswrapper and download windows driver form hp, Connected to wireless, Updating the system, and that's it.!

It was really harder taking of the laptop from it's box than installing ubuntu on to it.!

---

### Post by Jeisson on 2008-05-17
> **bradleyb01 said:**
> I was happy as a clam with Hardy 64 bit, but now, all of a sudden, my USB started acting crazy. [...]

I remember, I had problems in Hardy *beta* with USB ports and simplyw00x gave us this suggestion:

> **simplyw00x said:**
> I postulate that everyone with USB problems in hardy either uses ndiswrapper and is screwing around with ehci_hdc in /etc/rc.local (in which case restarting udev wirll re-enable hotplug, or is using dodgy kernel options (which have no place in Hardy IIRC).

I don't know if it could help.

@gborzi
I am really thankful for you kindness. I am using touchscreen following your steps, and I wish you the best results with Suspend function. I miss this capability. I would like to have enough knowledge to collaborate, but I am really new in this OS. Well, I just want to thank you a lot.

Best regards.

---

### Post by alex sun on 2008-05-17
Hi, everyone!
Could someone help with my USB mouse?
It stopped working after I didn't use it for several days.
In Windows the mouse works fine.
In Hardy 64 USB power is OK - mouse lights give flashes while I move the mouse.
But cursor on the screen doesn't move and mouse buttons do not work.
Several days before it worked.
Could you help, please?..
It's really difficult to work without mouse...
Especially when my touchpad crashes too - this happens from time to time...
Help, please...

And one more general question..
How to save DNS servers used in my local network?
After each usage of DHCP wireless if I want to connect to my local network by eth0, I have to rewrite DNS servers, because they are deleted every time.
Sorry for bothering, but I really need some help...

2 praveen: sorry, I don't really know, never tried 32 ubuntu.

---

### Post by gborzi on 2008-05-18
Hello, I succeeded in updating the BIOS without installing Windows. As I wrote before, I used a Vista Live CD. The 135 MB Vista image I mentioned before wasn't able to execute the bios update executable distributed by HP, so I searched for another, more complete Vista Live CD. The one I've found that works is a 273 MB image named VistaPE.iso (MD5SUM a3c1083baaf18c7ab701470a107fc064) which is available through torrent.
To update the bios you can follow these steps:
1) download the above mentioned Vista Live CD image;
2) download the bios update executable from HP, currently it's sp39050.exe;
3) burn the image to a CD and put the bios update file in an USB pen;
4) boot from the burned CD, choose VistaPE in the initial menu and open a terminal window;
5) insert the USB pen with the bios update and go to it *cd C:*;
6) execute the bios update file and follow the on screen instructions. It'll put a backup of your current bios in your USB pen.

Use these instruction at your own risk.

---

### Post by gborzi on 2008-05-18
Finally I've been able to fix suspend to RAM. Searching for a solution, I found [this bug report]("https://bugs.launchpad.net/ubuntu/+bug/218760") where it is suggested to unload the ehci_hcd module (although for fixing a different problem). Reading the docs about this module I found that > There are some issues with power management; suspend/resume doesn't
behave quite right at the moment.

so I configured pm-utils to unload this module (by putting the line *SUSPEND_MODULES="ehci_hcd"* in /etc/pm/config.d/modules) and now it's consistently working. There are still two minor problems:
1) the touchscreen doesn't work correctly after resume => fixed by switching to the text console and back;
2) sometimes the camera doesn't wake up => hibernate and resume fix this.
Hope this helps.

---

### Post by pmaconi on 2008-05-18
My pm folders are currently empty (/etc/pm/config.d/, /etc/pm/power.d/, and /etc/pm/sleep.d/). Should I create the modules file?

---

### Post by gborzi on 2008-05-18
@pmaconi
Yes, you can give to this file the name you like, but it must be in /etc/pm/config.d. Let me know if it works.

---

### Post by guiriman on 2008-05-19
heya guys
lots of good info here thanks in advance
i am an unexperienced user of ubuntu and i have been tryin to get the tx1000 touchscreen to work
i had success with the new drivers and everything worked fine till i did an update and now i have a seg fault
i try to calibrate,it takes forever and when it finally appears when i pick the 4point option it freezes and then about 2mins laters exits with a seg faault.no more info
can anyone please help a little with some info
thankin you all again
guiriman

---

### Post by pmaconi on 2008-05-19
@gborzi:
No such luck. The screen goes dark, the buttons stay lit, and the fan starts freaking out. After about 5 minutes of waiting for it to work, I was forced to reset it manually. Hibernation doesn't work for me either (normally it causes my computer to restart, with s2disk it locks the computer up like suspend).

---

### Post by bradleyb01 on 2008-05-19
@rikardocarvajal-
Thanks for the suggestion, I didn't see any results but I appreciate it.

@gborzi-
Thanks sharing your experience, your posts are always helpful.

@Jeisson & simplyw00x-
Thanks for the post, I re-setup ndiswrapper for wireless about a week ago and had edited rc.local but usb devices were working after the install so I didn't connect the two events as I didn't use my laptop for a few days. When I restarted udev, I could get usb, so I fixed up rc.local and all seems calm for the moment..

---

### Post by gborzi on 2008-05-19
@pmaconi
I'm sorry that sleep is still not working on your tablet. I have found this [page]("http://www.thinkwiki.org/wiki/Problems_with_ACPI_suspend-to-ram") about suspend problems. It was useful for me, I hope it'll be the same for you.

---

### Post by pmaconi on 2008-05-19
Thanks. I'll test it as soon as I get home. Any ideas for getting my hibernate to work?

---

### Post by gborzi on 2008-05-19
@pmaconi
After the computer restarts for a failed hibernation, do you have the /var/log/pm-suspend.log file? If so, take a look at it or post it here, it can contain useful informations about the problem.

---

### Post by LazyEngineer on 2008-05-19
To get the wireless working on my TX1000 (TX1308 ) using Ubuntu 8.04 64 bit, I followed the instructions here:

[http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

---

### Post by praveen_sreekumar on 2008-05-19
Anyone having trouble with USB sound?

I'm using the logitech notebook premium headset, works fine with skype, but no sound while playing videos, or youtube. Any tips?

Thanks,

---

### Post by pmaconi on 2008-05-20
@gborzi:

My /var/log/pm-suspend.log shows the following:> Tue May 20 09:29:29 EDT 2008: running hibernate hooks.
===== Tue May 20 09:29:29 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Tue May 20 09:29:29 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Tue May 20 09:29:29 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Tue May 20 09:29:29 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
===== Tue May 20 09:29:29 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Tue May 20 09:29:29 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Tue May 20 09:29:29 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Tue May 20 09:29:31 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Tue May 20 09:29:31 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Tue May 20 09:29:31 EDT 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Tue May 20 09:29:31 EDT 2008: done running hibernate hooks.

---

### Post by gborzi on 2008-05-20
@pmaconi
Your pm-suspend.log doesn't report any error and stops right after executing hibernation. I think your best option to solve the problem is to install the linux-doc package and read the files in /usr/share/doc/linux-doc-2.6.24/Documentation/power. The file basic-pm-debugging.txt.gz explains how to debug the suspend process.
Hope this helps.

---

### Post by gabesword on 2008-05-20
> **gborzi said:**
> Between a failed resume and a reboot I managed to make a package for the evtouch driver that includes my patch for the left and right rotation and adds a udev rules for the device, like the 69-touchscreen.rules. The package is attached to this post. Before installing it remove the file 69-touchscreen.rules from /etc/udev/rules.d. It doesn't change the calibration procedure, also known as "the horrible 9 X thing" :) (I like this name for evtouch calibration, no offence WildcatWhiz).

Thanks for sharing this package with everyone.

I do have a couple of questions though.  I have installed the above package but the touchscreen isn't working.  This is a fresh install of Hardy 64.  What else do I need to do to get the touchscreen working besides installing the above package?  My other question is how do I use the screen rotation?

Thanks in advance for any answers.

---

### Post by gborzi on 2008-05-20
@gabesworld
You need to configure the touchscreen driver in order to use it. To do the configuration you must add a section in your /etc/X11/xorg.conf file like this one ```
Section "InputDevice"
        Identifier "touchscreen"
        Driver "evtouch"
        Option "Device" "/dev/input/evtouch_event"
        Option "ReportingMode" "Raw"
        Option "Emulate3Buttons"
        Option "Emulate3Timeout" "50"
        Option "SendCoreEvents" "On"
        Option "Calibrate" "1"
EndSection
``` and this line in the ServerLayout section ```
InputDevice "touchscreen"
``` then follow the steps I wrote in post #869 in this thread. If you want to configure the behaviour of the touchscreen, take a look at post #890.
If you want to rotate the screen add this line > Option         "RandRRotation" "on" in your monitor section and restart X. Then you can use the xrandr command line program to rotate the screen or install grandr if you want a GUI.

---

### Post by praveen_sreekumar on 2008-05-21
Can someone please help with fprint installation? after ./configure, when i type make, it comes up with

/libfprint-0.0.5# make
make: *** No targets specified and no makefile found.  Stop.

i was on root when i did all this. any tips? please help.

cheers,

praveen

---

### Post by gborzi on 2008-05-21
@praveen
Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=760018").

---

### Post by alex sun on 2008-05-21
My USB mouse still doesn't work at all - doesn't matter if I reboot or not.

lsusb returns:
```

Bus 001 Device 007: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 006: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 001 Device 005: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 001 Device 003: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 0000:0000 

```
I'm running Ubuntu Hardy Heron 64bit and have tried A4-TECH OP-35D mouse and several other ones (Asus, Acer and HP) with same results.
In previous version of Ubuntu (Gusty 64bit) everything worked.

In log by grep there are only 2 mouse-related strings:
```

[ 18.457701] input: A4Tech PS/2+USB Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-1/2-1:1.0/input/input2
[ 18.472509] input,hidraw0: USB HID v1.10 Mouse [A4Tech PS/2+USB Mouse] on usb-0000:00:0b.0-1

```
On connecting\disconnecting mouse during work grep returns nothing.

I heard that Ndiswrapper has a reputation for hijacking USB ports and I use Ndiswrapper for my Wireless. However all other USB devises (like USB flash cards) work fine. 
I really need some help with my mouse ;)

---

### Post by gborzi on 2008-05-21
@alex sun
To my knowledge, the kernel module that handles usb mouse is usbhid. Is it loaded? When I unload it my external mouse stops working.

---

### Post by praveen_sreekumar on 2008-05-21
> **gborzi said:**
> @praveen
Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=760018").

@gborzi

Thanks for that.

Just confused with something. It says edit common-auth to contain
auth sufficient pam_fprint.so
auth required pam_unix.so nullok_secure 

Do i replace the original lines with these? or do i just include them? if so, before the original lines? or after?

---

### Post by pmaconi on 2008-05-21
@gborzi

If you run /etc/acpi/hibernate.sh in terminal, is it successful? Mine has an error: FATAL: Module acpi_sbs not found. I'm wondering if this is causing my hibernation problems.

---

### Post by gborzi on 2008-05-22
@praveen
Sorry, I haven't installed and configured libfprint, I can't help here. I only suggest you to ask in that thread.
@pmaconi
Unlike previous versions of Ubuntu, Hardy uses pm-utils for suspend/resume, so the correct command is pm-hibernate, i.e. you should not use the nibernate script provided by acpi. Note that when you hibernate using gnome-power-manager, it actually calls pm-hibernate or pm-suspend.
I don't think the above error message has anything to do with your hibernation problem. As I said before, that's not the command used when you hibernate using the GUI.

---

### Post by v0lZy on 2008-05-22
Any news on the egalax driver? still in beta, still with the same clicking issues? 

Can anyone help me with my config, I think im supposed to remove stuff from xorg.conf so that I wont be getting a double click every time i touch the screen but im unsure of what i should remove and if i need to do anything else beside removing whatever it is i should remove. What functionality do i possibly lose in favor of having proper clicks?

Thanks,

V

---

### Post by alex sun on 2008-05-22
@gborzi:
Already tried rmmod then again modprobe usbhid as adviced here:
[https://lists.ubuntu.com/archives/ubuntu-users/2006-March/071497.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-March/071497.html)
At the moment in /etc/modprobe.d/blacklist:
```

blacklist usbmouse
blacklist usbkbd
#blacklist usbhid

```

Also tried using usbmouse with usbkbd instead of usbhid, as advised there further.
in /etc/modprobe.d/blacklist:
```

#blacklist usbmouse
#blacklist usbkbd
blacklist usbhid

```

What else?..

@gborzi: could you show your xorg mouse section please?

---

### Post by gborzi on 2008-05-22
This is my xorg.conf mouse section ```
Section "InputDevice"
      Identifier  "Configured Mouse"
      Driver            "mouse"
#      Option            "CorePointer"
EndSection

```
and I also have this line in the ServerLayout section
```
      InputDevice "Configured Mouse"

```
but I don't the problem is in X, given that your mouse doesn't show up in lsusb.

---

### Post by toastermm on 2008-05-23
> **waspbr said:**
> sauron, what drivers did you use to install the graphics card in hardy, I tried the one for the 6 series since i can't find geforce go 6 in the nvidia site, but now my X is broken...

[COLOR="Red"]problem solved, sometimes I am  in complete awe at my noobiness, installed the drivers by  installing the restricted drivers manager in synaptic[/COLOR]

Hrm, I am having the same problem. I'm running Hardy Heron, and have an HP tx1000 Laptop with the Nvidia 6 series card.  But under synaptic manager, there's plenty of options for drivers... which one worked for you?  Any thoughts?

---

### Post by toastermm on 2008-05-23
err sorta fixed it.

I just selected another nvidia driver from the synaptic manager, The "nvidia glx" driver instead of the "nvidia glx new" driver.  It works better, That is to say, I can now up the resolution to 1024 by 768, Which is good enough.

Anyway to tell if this is the optimal driver/solution for the card?

now to get started on fixing the wireless card...

---

### Post by alex sun on 2008-05-24
@v0lZy,

Try this: remove all input devices apart from EETI from xorg.conf, add
Code:

Option             "AllowEmptyInput"

to ServerFlags, copy /usr/share/doc/hal/examples/10-x11-input.fdi to /etc/hal/fdi/policy/, then add the following as /etc/hal/fdi/preprobe/10-egalax.fdi:

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
		<match key="info.product" string="eGalax TouchScreen">
			<merge key="info.ignore" type="bool">true</merge>
		</match>
	</device>
</deviceinfo>

Reboot :)

p.s. maybe someone knows how to make USB mouse work? ;)

---

### Post by Jeisson on 2008-05-24
> **gborzi said:**
> Finally I've been able to fix suspend to RAM. Searching for a solution, I found [this bug report]("https://bugs.launchpad.net/ubuntu/+bug/218760") where it is suggested to unload the ehci_hcd module (although for fixing a different problem). Reading the docs about this module I found that 
so I configured pm-utils to unload this module (by putting the line *SUSPEND_MODULES="ehci_hcd"* in /etc/pm/config.d/modules) and now it's consistently working. There are still two minor problems:
1) the touchscreen doesn't work correctly after resume => fixed by switching to the text console and back;
2) sometimes the camera doesn't wake up => hibernate and resume fix this.
Hope this helps.

Giuseppe, your recommendations are light into the tunnel. It worked for me. Really, infinite thanks :-D.

After a suspend action, I had to apply manually the ugly fix for the hard drive. Are you running the alternative to the ugly fix you suggested in [this post]("http://ubuntuforums.org/showthread.php?p=4872313#post4872313"). Is it working well? I want to apply it (but I am a little bit afraid, because the introductory paragraph :-D).

> **pmaconi said:**
> My pm folders are currently empty (/etc/pm/config.d/, /etc/pm/power.d/, and /etc/pm/sleep.d/). Should I create the modules file?

pmaconi, my /etc/pm/config.d directory was empty also. I just did the following

```
cd /etc/pm/config.d
sudo nano modules
# paste the following two lines and save the file
SUSPEND_MODULES="ehci_hcd"

# reboot the computer
```

I don't know if the line feed is needed in the modules file or the reboot is mandatory, but it worked on my tx1410us! Note that I did not changed the power.d and sleep.d directories.

Best regards :)

---

### Post by gborzi on 2008-05-25
Hello Jeisson,
I'm running the alternative ugly fix and it works nicely. I have made a small change to the fix since the post you mentioned. I renamed 99-hdparm.sh to 97hdparm which follows the pm-utils style while the previous name followed the acpi style. It's only an aesthetic change. In case you apply this fix, I suggest you to check for a few days that it works properly.
Have you noticed any problem after a suspend to RAM/resume? As I wrote earlier my problems are with the camera (it's not seen anymore) and the evtouch driver.

---

### Post by v0lZy on 2008-05-25
Thanks alex sun, my touchscreen finally works!

However, I have a new problem with the GDM key layout. Its ok in the console and its ok i gnome, but in the login window i get when x starts up, my keyboard layout is set to US english... and this is totally different then the japanese keyboard I have (bought the pc in japan).

I tried with the funky-keyboard-fu stuff simplywoox wrote ... but im lost as to what line to add it in at and weather or not i should delete something. In any case, what i tried so far doesnt work.. any idea how to fix it?

cheers 

V

Ps: Sorry about the mouse thing, hope u get it working

---

### Post by isachan on 2008-05-25
Thanks for Jeisson, your suspend-to-RAM fix is working like a charm on my TX1000 CTO too !

My set up is :
2GB RAM
Kubuntu 8.04 AMD64
eGalax latest beta driver works after resume
nVidia driver you get from Hardware Drivers Manager

Only thing to be fixed is my wireless with b43 driver,
which doesn't even build from source code as of today.

Check this site for Linux native Broadcom driver :
linuxwireless.org

Isao

---

### Post by thanthese on 2008-05-26
I've been running 8.04 since it came out.  All the updates have been working for me just fine, until now.

Today's updates required a restart.  When the computer came back up, the external keyboard and mouse weren't working.  I switched which USB ports they were plugged into, but no help.  I tested the USB ports with a flashdrive, they don't seem to be working at all.

This the the log I got from Synaptic:

Commit Log for Mon May 26 11:47:30 2008


Upgraded the following packages:
apport (0.108.1) to 0.108.2
apport-gtk (0.108.1) to 0.108.2
gdm (2.20.6-0ubuntu1) to 2.20.6-0ubuntu2
gnome-keyring (2.22.1-1) to 2.22.1-1ubuntu1
libgnome-keyring0 (2.22.1-1) to 2.22.1-1ubuntu1
libpam-gnome-keyring (2.22.1-1) to 2.22.1-1ubuntu1
linux-generic (2.6.24.16.18) to 2.6.24.17.19
linux-headers-generic (2.6.24.16.18) to 2.6.24.17.19
linux-image-generic (2.6.24.16.18) to 2.6.24.17.19
linux-libc-dev (2.6.24-16.30) to 2.6.24-17.31
linux-restricted-modules-common (2.6.24.12-16.34) to 2.6.24.12-17.36
linux-restricted-modules-generic (2.6.24.16.18) to 2.6.24.17.19
nvidia-glx (1:96.43.05+2.6.24.12-16.34) to 1:96.43.05+2.6.24.12-17.36
python-apport (0.108.1) to 0.108.2
python-problem-report (0.108.1) to 0.108.2

Installed the following packages:
linux-headers-2.6.24-17 (2.6.24-17.31)
linux-headers-2.6.24-17-generic (2.6.24-17.31)
linux-image-2.6.24-17-generic (2.6.24-17.31)
linux-restricted-modules-2.6.24-17-generic (2.6.24.12-17.36)
linux-ubuntu-modules-2.6.24-17-generic (2.6.24-17.25)


I'm afraid to try rolling back the updates without having a better idea about what I'm doing.  "linux-headers" looks like too important a file to go playing with willy-nilly.  Is there a manual way to remount the USB ports, or something?  Should I wait for a fix from the update manager?

I can't work without my full-size keyboard and mouse.  Any ideas would be greatly appreciated.

---

### Post by gborzi on 2008-05-26
@thanthese
You don't need to roll back the updates, simply reboot your computer and at the grub prompt press escape and select the previous 2.6.24-16 kernel. When the kernel is updated the old one is not uninstalled. You can make the 2.6.24-16 kernel the default boot kernel by editing /boot/grub/menu.lst.

---

### Post by thanthese on 2008-05-26
@gborzi
Thank you so much!  Selecting the previous kernel worked like a charm, and editing /boot/grub/menu.lst went smoothly and had the right effect.  You're a life-saver!

---

### Post by tarsius4 on 2008-05-26
Related to the most recent kernel update, I want to share a warning to others to make sure they aren't suffering for no reason (like I did):

**AFTER THE KERNEL UPDATE, YOU SHOULD PROBABLY ALLOW YOUR /boot/grub/menu.lst TO BE REPLACED**

Until today, I always kept my old menu.lst because I figured it would save me the hassle of adding in extra boot options (noapic, nolapic, etc...).  What I did not realize is that I had been running an old kernel from Ubuntu 7.10 (2.6.22-14... today's update was 2.6.24-17).

Also until today, I have been experiencing intermittent crashes, freezing, stalling, wifi, and USB problems. However, after updating and using **no boot options**, I have not experienced a single issue yet. (It's been about 6 hours so far, let's no problems come up).

The one bump in the road was that my wireless and nvidia graphics drivers failed to work after the update, but this was solved by a trip to the System>Administration>Hardware Drivers (for wifi) and by installing Envy through Synaptic.

So in short, I recommend **allowing your menu.lst to be updated automatically** AND **trying to boot with no extra options**. Extra info: I still have blue lines when I flip to the Ctrl-Alt-Fx consoles and I have not tried hibernation or standby yet. Maybe some folks out there are having trouble hibernating because they've added some boot options that prevent it.

---

### Post by edmondt on 2008-05-26
Grab the beta driver from here:

[http://210.64.17.162/web20/TouchKitDriver/linuxDriver.htm](http://210.64.17.162/web20/TouchKitDriver/linuxDriver.htm)

For 32 bit:
wget [http://210.64.17.162/web20/drivers/touch_driver/Linux/v2.03/TouchKit-2.03.1712-32b-k26-x14.tar.gz](http://210.64.17.162/web20/drivers/touch_driver/Linux/v2.03/TouchKit-2.03.1712-32b-k26-x14.tar.gz)

For 64 bit:
[http://210.64.17.162/web20/drivers/touch_driver/Linux/v2.03/TouchKit-2.03.1712-64b-k26-x14.tar.gz](http://210.64.17.162/web20/drivers/touch_driver/Linux/v2.03/TouchKit-2.03.1712-64b-k26-x14.tar.gz)

Then:
tar -xvf TouchKit-2.03.1712-*
sudo cp egalax_drv.so /usr/lib/xorg/modules/input/
sudo nano /etc/X11/xorg.conf


Add the following:

Section "InputDevice"
      Identifier "EETI"
      Driver "egalax"
      Option "Device"    "/dev/usb/hiddev0"
      Option "Parameters" "/etc/egalax.cal"
      Option "ScreenNo"   "0"
EndSection

...and add the following in Section "ServerLayout":

InputDevice     "EETI"


Save and reboot...run TouchKit to configure the touchscreen and calibrate.

Check this post as well: [http://ubuntuforums.org/showpost.php?p=4197376&postcount=542](http://ubuntuforums.org/showpost.php?p=4197376&postcount=542)

---

### Post by edmondt on 2008-05-27
I just want to attach the rotate script I modified.

1. rotate-screen-clockwise.sh
2. rotate-screen-anticlockwise.sh
3. flip-screen.sh

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=71776&stc=1&d=1211903649[/IMG]

The screenshot attached shows that I added 3 custom launchers with the command "sh rotate-screen-clockwise.sh", must add the following to the screen section of your /etc/X11/xorg.conf and restart X in order for it to work:

Option "RandRRotation" "on"

I have also programmed the DVD and Quickplay buttons to rotate clockwise/anticlockwise from previous post.

Followed by these useful tools:

sudo apt-get install xournal celwritter

---

### Post by toastermm on 2008-05-27
Working on the wireless card with the tx1000 Hp Laptop.  I see that I only have to install the B43-fwcutter package instead of the BCM43-fwcutter.  I did that.  And am getting an error during the install:

"b43-fwcutter: subprocess post-installation script returned error exit status 1"

With the details as follows:

"Setting up b43-fwcutter (1:011-1) ...
Error parsing prozy URL [http://:8080/:](http://:8080/:) Invalid host name.
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b430-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up b43-fwcutter (1:011-1) ...
Error parsing prozy URL [http://:8080/:](http://:8080/:) Invalid host name.
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1"

I'm running Hardy on the AMDX64 system.  I've had problems before on the "invalid host name" and my internet connection IS working, and sometimes I have to manually go to the sites and get the packages, but that site does not look good.

Any suggestions?

---

### Post by toastermm on 2008-05-28
Hrm, sorta figured it out- I completely removed b43-fwcutter and reinstalled it.  No more errors.  But still no more wireless card.  I have no idea now.  I've tried both b43** and bcm43** and neither recognize the wireless card.

How to force hardy to find it?

-no idea.

---

### Post by moob on 2008-05-28
Hello everybody,
I wasn't here for a long time. :( Sorry for that. :)

If is still here somebody who has "blue lines" on tty or just it isn't looking as you like. I know it was here many times (not ...glx-new but ..glx). I have very simple solution for you. Just install envyNG. For example this way:
```
sudo apt-get install envyng-gtk
```
Run it. It is in applications/system tools/ or type:
```
envyng-gtk
```
Then select NVIDIA and you need to choose 96.43.05 (or similar).
Apply.

It will install nvidia-glx (exactly nvidia-glx-envy) instead of nvidia-glx-new which causes that problems.

Now I have well-looking ttys in 1024x768 resolution.

---

### Post by Jeisson on 2008-05-29
> **gborzi said:**
> Hello Jeisson,
I'm running the alternative ugly fix and it works nicely. I have made a small change to the fix since the post you mentioned. I renamed 99-hdparm.sh to 97hdparm which follows the pm-utils style while the previous name followed the acpi style. It's only an aesthetic change. In case you apply this fix, I suggest you to check for a few days that it works properly.
Have you noticed any problem after a suspend to RAM/resume? As I wrote earlier my problems are with the camera (it's not seen anymore) and the evtouch driver.

Hello Giuseppe. I have not applied the "alternative ugly fix" yet. I will feedback you when I have made the change.

You are right. Both the camera and the touchscreen are working perfectly before a suspend action. After that, Cheese shows color bars and touchscreen stops working.

> **isachan said:**
> Thanks for Jeisson, your suspend-to-RAM fix is working like a charm on my TX1000 CTO too !
Isao, thanks for your words, but the real credits are for gborzi. He discovered that and a lot of tips for making Ubuntu more wonderful in our loved laptops.

Best regards
-Jeisson

---

### Post by gborzi on 2008-05-29
> **toastermm said:**
> Hrm, sorta figured it out- I completely removed b43-fwcutter and reinstalled it.  No more errors.  But still no more wireless card.  I have no idea now.  I've tried both b43** and bcm43** and neither recognize the wireless card.

How to force hardy to find it?

-no idea.

Have you checked if your wireless chip is supported by b43? The chip can be seen by running ```
lspci|grep  Broadcom
``` and the list of supported chips is available [here]("http://linuxwireless.org/en/users/Drivers/b43"). If your chip is not supported you need to use ndiswrapper.

---

### Post by tarsius4 on 2008-05-29
Hey moob, thanks for the advice.  I tried it but it unfortunately did not work.

Under Gutsy I believe I had been using nvidia-glx-new without problems, but when I upgraded to Hardy, the graphics driver no longer worked.  When booting, I would be thrown to a console after the ordinary Ubuntu loading screen.  From there, I would see three "false starts" (screen goes black then back to the console), and finally I would see a message box in 800x600 that said something like "would you like to permanently use this driver?"--which meant the software driver, not the nvidia-glx-new.  From there I discovered that nvidia-glx ALSO did not work (same symptoms), and eventually I tried nvidia-glx-new-envy, which WORKED, but put blue lines on my console.

I tried EnvyNG yesterday, but it did not work. Turns out it was installing either nvidia-glx-new (v169) or nvidia-glx (v96), both of which failed. Finally I tried installing nvidia-glx-envy, which WORKS WITHOUT blue lines.

to summarize:
```
nvidia-glx           v96...   - Fails (uses SW driver @ 800x600)
nvidia-glx-new       v169...  - Fails (uses SW driver @ 800x600)
nvidia-glx-envy      v96...   - Works fine
nvidia-glx-new-envy  v169...  - Works, but BLUE LINES
```

If anyone is still experiencing problems, I recommend installing nvidia-glx-envy manually.  Good luck.

---

### Post by moob on 2008-05-29
Interesting... I'm telling it day by day: Stupid linux. ;o) (Or am I stupid, who knows?)
But I have to tell I spent more time to find drivers for Windows XP for this laptop. I have them. And working. 

Maybe funny thing with XP's: I was 2 hours on internet. No downloading porn, no googling. Just downloading, installing and using AVR Studio (assembler). After that comes popup about antivirus... Freezing and no next boot up. No recovery mode. I don't have Win XP CD here. I'm out of the game. Stupid linux. :-)

---

### Post by ccw127 on 2008-05-29
@Toast

Are you sure you have a compatible broadcom card? My 1320us came with a bcm4328 which is not currently supported by the b43 drivers. I have to use ndiswrapper.

Chris

---

### Post by edmondt on 2008-05-29
After updating the kernel to 2.6.24-17-generic, bluetooth stopped working. I think it might have been caused by TouckKit, but who knows... 

The fix to get everything working again, including touchscreen, wifi etc is:

sudo gedit /etc/modprobe.d/blacklist

Search for these lines you have added to make wifi and touckscreen work and comment the following:


blacklist bcm43xx
#blacklist ssb

#cause touchscreen drivers to malfunction
blacklist usbtouchscreen
#blacklist tkusb

reboot and it will work again.

---

### Post by toastermm on 2008-05-30
Thanks for the replies-  I found a thread that installs the Broadcom driver for the Hardy version here:

[http://ubuntuforums.org/showthread.php?t=760568]("http://ubuntuforums.org/showthread.php?t=760568")

I had an issue with updating the server version of my kernel, but fixed it in a later post on that thread.  Read that thread if you have problems with your wireless, and if it doesn't work, read the resulting pages of posts.  Worked for me.

---

### Post by benguin on 2008-06-01
> **tarsius4 said:**
> Hey moob, thanks for the advice.  I tried it but it unfortunately did not work...

To tarsius4 and others who are having nvidia issues with weird terminals and distorted screens after closing the lid and such: I just upgraded to the official NVidia driver 173.14.05, and lo and behold! My screen issues are all gone. No more flaming terminals, nor do I have a distorted screen after a power saving mode. This is great. Actually the NVidia driver release notes do mention they fixed this issue:

> Fixed a regression causing some GeForce 6100/6150 systems to fail to restore the screen after DPMS cycles.

I did a manual upgrade to the 173.14.05 driver; the nvnews.net Linux users forums have instructions on doing that, as they do I'm sure in the Ubuntu Wiki and elsewhere on this forum.

Just thought I share this good news. I have a TX1305ca variant, FYI.

-J

---

### Post by haegar2008 on 2008-06-04
Hello everybody,
  i've tried to get my touchscreen working, but i failed...
I use Ubuntu 8.04 in 32-bit mode with the HP Pavilion tx 1345e.
I followed the instruction for the evtouch driver but i get no feedback from the touchscreen. 
The driver for the kernel (2.6.24-18-generic) seems to be loaded and to work. The evtouch module for xorg is loaded an the Xorg.0.log says that EVTouch Touchscreen is there.

When I also configure the "generic mouse" at /dev/mouse0 then the Xorg.0.l0g says:
EVTouch TouchScreen: doesn't report core events

I tried to run "evtest". It shows some configuration variables and then stops wit the line:
Testing... (interrupt to exit)

I touch the screen, but nothing happens.

I am now unsure if there is a touchscreen at all...it is a refurbished hp and maybe there is the chipset for the touchscreen but maybe ist is not connected? Does anybody know how i could figure out if the touchscreen really works? Are there any basic tools for touchscreen testing? Is there a live-cd which could be used to test the touchscreen? 

Or should i go to the shop and complain about the non-functioning touchscreen?...i bought the notebook without OS, so I really don't know if the tochscreen works with another OS...

Any help appreciated!

Thanks in advance!

---

### Post by isachan on 2008-06-04
If you installed any drivers (in Linux term, kernel modules) MANUALLY by compiling and installing from source code, you have to recompile against the new kernel-headers and reinstall the driver, whenever there is kernel / kernel-header update comes along.

Happened to me today, after 2.6.24-18 kernel-update, X window couldn't start at all. I had just installed Nvidia 173.14.05 yesterday. And today, after the update I had to reinstall the same driver all over again.

But it's working now.

I think same thing applies for evtouch driver as well.

Isao

---

### Post by gborzi on 2008-06-04
@haegar2008
Have you tried the official binary drivers? If the touchscreen doesn't work with them then probably the it is broken.
@isachan
My touchscreen is working fine after the latest kernel update. The evtouch driver isn't in the kernel.

---

### Post by edmondt on 2008-06-04
For some reason, recently the wireless stopped working after another kernel update. After digging a bit I found this solution from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

Assuming you already have ndiswrapper configured previously, issue this command: sudo lshw -C network

My output was:

  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=**ssb**

The last part says ssb, that's where the problem is according to the article. Try the Hardy Bug Fix:

sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy #this step added Apr 27 2008
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44 #this step added May 1 2008

If it works, make it permanent:

comment out the following in /etc/rc.local:

#rmmod ohci_hcd
#rmmod ssb
#rmmod ndiswrapper
#modprobe ndiswrapper
#modprobe ohci_hcd

then:

echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper

Reboot and see if it works :) I hope this helps someone...

---

### Post by tkmunzwa on 2008-06-05
thx dude. just installed on pt8900. had spent the whole day looking for solns until i bumped into your post. again - thx

---

### Post by Cuppa-Chino on 2008-06-05
> **isachan said:**
> If you installed any drivers (in Linux term, kernel modules) MANUALLY by compiling and installing from source code, you have to recompile against the new kernel-headers and reinstall the driver, whenever there is kernel / kernel-header update comes along.

Happened to me today, after 2.6.24-18 kernel-update, X window couldn't start at all. I had just installed Nvidia 173.14.05 yesterday. And today, after the update I had to reinstall the same driver all over again.

But it's working now.

I think same thing applies for evtouch driver as well.

Isao

how did you install it and did you manage to survive more than one boot, my machine is doing my head in again (why why why does this keep hapening -sorry for that) but I can install the nvidia 173.14.05 with the nvidia script but after the boot it just fails outright and goes back to low graphics....
please help thanks

---

### Post by isachan on 2008-06-05
Cuppa-Chino,

Follow these steps here:
[http://ubuntuforums.org/showpost.php?p=4841674&postcount=21](http://ubuntuforums.org/showpost.php?p=4841674&postcount=21)

I think the most important step is to edit DISABLED_MODULES line in  /etc/default/linux-restricted-modules-common file to look like this DISABLED_MODULES="nv nvidia_new".

Isao

---

### Post by LazyEngineer on 2008-06-06
It took me 3 days, but by God I've read every post in this thread!  See attached spreadsheet for the post numbers for common issues and where I noted they were discussed.  Note - most of the discussions were for Gutsy, so don't apply to Hardy (maybe).  [added - drat, can't attach it]

My own machine: TX1308nr.  64 bit version 8.04 install of Ubuntu.    Installed on a freshly wiped machine, which I then installed XP prior to installing Ubuntu.

[COLOR="Blue"]The good
[/COLOR]
**wireless**
works great - followed some of the advice posted herein.
[http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

**touchscreen**
moot, my glass screen cracked, so had to open bezel and remove it altogether.  So no glass = no touchscreen.  The silver lining is the LCD screen looks much clearer now that the glass is no longer in front of it.

**video drivers**
I started with EnvyNG - that didnt' work and actually created problems.  After uninstalling EnvyNG, uninstalling anything I could find related to the drivers.  Reboot and did add/remove programs: Hardware Drivers.  Video now seems to be working very well.  Only concern is this video card runs hot - normally around 70C and jumps to 100C under load.  Looks like this is not unusual, and eventually I'm going to try this:
[http://forum.tabletpcreview.com/showthread.php?t=8875](http://forum.tabletpcreview.com/showthread.php?t=8875)


**gaming**
Obviously this rig is not to be a dedicated gaming rig, but I will use it for such as backup and during travels.  I installed World of Warcraft using WINE.  This was done by following the various condensed instruction pages via google.  Works GREAT - better than it works native in Windows on this machine.  But hot - video card spikes up to 100 C.  scary.

**Sound**
works great right out of the box.  my only complaint is that it seems a bit soft coming through the speakers.  I haven't tested the microphones yet.  Headphone jacks both work fine.

**HDD cycling**
Apparently this is a serious problem for some - but I'm not hearing anything on mine to indicate I'm having this issue.  Is there a utility I should run to check this out?


[COLOR="Red"]
The bad[/COLOR]

**5in1 card reader**
Not so good.  The electronics and drivers may be fine, but mechanically it doesn't work because the SD cards won't lock into place.  Need to open up the case and fix (I hope it's easily fixable).

**Mouse**
My own USB optical mouse works great.  Touchpad works well - but a bit too well.  Too sensitive for my tastes and randomly activates while I'm typing - very annoying.  Not sure what to do about that.  


**gaming**
Unfortunately, I can't get my copy of Civ IV to run.  Not sure what's going on there.  Right where about when it gets to "Init Engine", it crashes back to desktop. :(

[COLOR="Purple"]**Suspend/hybernate/closing the lid**
HELP!  I think gbonzi has figured it out and posted pieces on how to do it, but could you please please resummarize, along with a list of suggested terminal instructions on how to actually do this?  This is important, I leave my machine on all the time.  Hybernate should help it from burning itself out prematurely. 
[/COLOR]

**Webcam**
It knows it's there, but something is not right.  Preferences/Multimedia program will start it, for about half a second, then it crashes out back to desktop and the image disappears.

[BIOS flashing]
Can this be done in XP?  The updates on the HP website all look to be exclusive to Vista to run.


I'd be much obliged for some tips on my trouble areas.

---

### Post by hvymtlsteve on 2008-06-06
I just now got around to upgrading to Hardy from Feisty. 
I was trying to go from Feisty to Gutsy through an upgrade, but that screwed things up terribly so I just wiped out and freshly installed Hardy from live CD. So far things are looking good.
I was rather pleased to find that piklab is now in the repository, so I didn't have to mess around to get it to work! Not that it was really hard to do before, but...

The wireless did not work as stated earlier in the thread (I downloaded b43-fwcutter and let it do its auto thing, but the light is stuck on orange and I don't see any wireless stuff in my networking). 
I'm not heartbroken on the wireless at the moment, as my new campus only has a wired network anyway.

EDIT 
*removed buncha crap about nvidia drivers*

NM, nvidia drivers seem to be ok now! 
I was having problems on lid close and reopen, and the consoles were looking crummy, but I looked one page back and another user said that this stuff was fixed by installing 173.14.05 so I did a little bit of digging around the forum and found this rather fresh post:
[http://ubuntuforums.org/showpost.php?p=5123595&postcount=9](http://ubuntuforums.org/showpost.php?p=5123595&postcount=9)
Worked like a charm!

---

### Post by Cuppa-Chino on 2008-06-06
> **isachan said:**
> Cuppa-Chino,

Follow these steps here:
[http://ubuntuforums.org/showpost.php?p=4841674&postcount=21](http://ubuntuforums.org/showpost.php?p=4841674&postcount=21)

I think the most important step is to edit DISABLED_MODULES line in  /etc/default/linux-restricted-modules-common file to look like this DISABLED_MODULES="nv nvidia_new".

Isao

done, works for one boot but as soon as I reboot I am back to low graphics mode, exactly same issue as before :cry:

other link also does not help...

no dice when ever my computer starts up it finds Nvidia drivers on first boot but then goes into "low graphics mode" tx1000 hewlett packard, cannot get even get back to a nv driver now... 

anybody else had the one time nvidia driver boot issue?..

how do I get back to nv driver? cannot seem to get back to that now ...

---

### Post by ccw127 on 2008-06-06
Hello all,

I noticed something today that got me thinking... I have been using ndiswrapper because I have a bcm4328 in my tx1320us (and the 4328 isn't' supported by the b43 driver). Well, today I was looking under the wireless plate and I noticed a curiosity; the wireless card and the sticker on the plate identify my card as a bcm4321 (sure enough, the chipset says the same. In software, the card identifies as a 4328. Ideas?

Maybe I could somehow shoe-horn the b43 driver even though the card identifies as a bcm4328. Maybe there is something in the firmware?

Chris

---

### Post by ovalenzu on 2008-06-07
Hi all,
I have a problem with the leds of keyboard, when press de caps lock button the led doesn't turn on. any one have the same problem?. Any idea how can I resolve this?

Thanks!!

---

### Post by LazyEngineer on 2008-06-07
> **LazyEngineer said:**
> 

**gaming**
Unfortunately, I can't get my copy of Civ IV to run.  Not sure what's going on there.  Right where about when it gets to "Init Engine", it crashes back to desktop. :(

[COLOR="Purple"]**Suspend/hybernate/closing the lid**
HELP!  I think gbonzi has figured it out and posted pieces on how to do it, but could you please please resummarize, along with a list of suggested terminal instructions on how to actually do this?  This is important, I leave my machine on all the time.  Hybernate should help it from burning itself out prematurely. 
[/COLOR]

**Webcam**
It knows it's there, but something is not right.  Preferences/Multimedia program will start it, for about half a second, then it crashes out back to desktop and the image disappears.

[BIOS flashing]
Can this be done in XP?  The updates on the HP website all look to be exclusive to Vista to run.


I'd be much obliged for some tips on my trouble areas.

OK, some progress!  For Civ IV I followed the instructions posted elsewhere which can be summarized as (Note, the more popular Google hit does NOT specify all the needed .dll's, and so didn't work)

> The game dosen't work unless you have the following DLLs in your system32 folder: d3dx9_26.dll d3dx9_32.dll mscoree.dll msxml3.dll d3dx9_31.dll d3dx9_33.dll msvcp71.dll msxml3r.dll mscoree.dll and msvcp71.dll. Notice that you need mscoree and msvcp71 only for BTS, vanilla doesn't require them. Also, you don't need any additional DLL overrides except for msxml3 (native).Note, you'll need to go to gamecopyworld.com and get the noCD crack to run the game.  I'd feel guilty - but since I bought the game, I think I'll sleep fine.

For the lid closing/hibernate issue - sounds like Nvidia released some new drivers to fix it, and in a little while those are going to be incorporated by the Ubuntu staff - if I'm reading that right.  So I'll just sit tight and let them fix it for me.

For the Webcam, I still don't have a good fix for that.  Kind of annoying, but I never use such anyway.

BIOS flashing - anyone successfully do such using WinXP?  Looks like it's Vista specific, and the techniques to finagle it through Vista, if you don't already have Vista on the machine, sound cumbersom.

---

### Post by gborzi on 2008-06-07
I have added an [entry]("https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionTX1350el") for the HP TX1350el in the wiki.

---

### Post by ccw127 on 2008-06-07
Question...

Has anyone figured out this heat/ temp. issue??? I am sitting here at a table (good air flow), with an ambient air temperature of somewhere around 80 degrees Fahrenheit; my GPU is reading 78 degrees Celsius, my CPU as 52 degrees Celsius, and I actually got a SMART warning for HD temp. All of this with my CPU auto-throttled to 800mhz most of the time. Now even without the semi-high room air temp, I have always been getting these ridiculously high temperature readings once I installed Ubuntu; heck, I can't even turn on too many desktop effects cause everything goes through the roof!

What is going on?!?! Can I maybe get some input?

(srry to seem a bit forceful, but I have raised this question a few times before in this thread but people seem to ignore it)

Chris

tx1000z (tx1320us) -- Everything is working (except crazy high heat)

---

### Post by ovalenzu on 2008-06-07
> **LazyEngineer said:**
> 
For the Webcam, I still don't have a good fix for that.  Kind of annoying, but I never use such anyway.
... .

For the webcam problem 
I fix from this way
first check if is detected
$lsusb
if you get something like 
0c45:62c0 Microdia
everything it's ok,

now check if have charged the module ucvvideo
$lsmod |grep  ucv

if you get 

uvcvideo               59912  0 
compat_ioctl32         13312  1 uvcvideo
videodev               38144  2 uvcvideo,compat_ioctl32
v4l1_compat            16516  2 uvcvideo,videodev

the webcam should work.
if not

to this.

$mkdir temp
$cd !$
$svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk
$make
$sudo make install
$modprobe uvcvideo

add uvcvideo to /etc/modules to charge on boot

for me this work.

I hope this help you.

---

### Post by mbliu on 2008-06-07
Hey everyone, I'm new here.

I'm trying to get my touchscreen to work but neither the evtouch or egalax drivers have worked for me so far.

For the evtouch driver, when I try to run the calibration utility, it gives me errors that the module isn't loaded.

For the egalax driver, when I try to run TouchKit, it gives me a dialog box with "No Touch Controller Found."

When I press on the touch screen it registers a mouse click event but does nothing else. 

Any ideas? I'm using 32bit Hardy.

Thanks!

---

### Post by dudafmendes on 2008-06-08
Hi, 

I'd like to thank all the people in this forum. Apart from some small features, my Tx1215 w/ Hardy 64 is working pretty well. 

I don't know if it is a issue, but the problem with the webcam stop working after suspending, I solved by suspending uvcvideo, by adding the following line in /etc/pm/config.d/modules

```
#/etc/pm/config.d/modules
SUSPEND_MODULES="ehci_hcd uvcvideo"

#try suspending now
```

I also had to install the envyNG driver 96.* (thanks to moob), which instructions can be found here, for the suspend to work fine.


---EDIT---
I just realized that sometimes the camera is just not detected, obviously that was the problem with some of you guys.
sorry.

Bests D.

---

### Post by gborzi on 2008-06-08
@dudafmendes
Thanks for the suggestion to suspend uvcvideo. It works fine on my tx1350el, I'm going to update the wiki.

---

### Post by samygarib on 2008-06-08
> **tarsius4 said:**
> I get the blue lines too, but it's worth it since before I had no nvidia hardware acceleration.

Hey,

I just wanted to say that I also had the problem of the blue lines. Ubuntu Hardy amd64 and it was fixed with the new nvidia driver: 173.14.05
It was a little bit painfull though cause you can not upgrade the driver with envy, so you have to install the original nvidia driver after uninstall the other with envy. Don't make the same mistake than me, and DO uninstall the previous one.

Good luck.

---

### Post by dudafmendes on 2008-06-08
> **ccw127 said:**
> Question...

Has anyone figured out this heat/ temp. issue??? I am sitting here at a table (good air flow), with an ambient air temperature of somewhere around 80 degrees Fahrenheit; my GPU is reading 78 degrees Celsius, my CPU as 52 degrees Celsius, and I actually got a SMART warning for HD temp. All of this with my CPU auto-throttled to 800mhz most of the time. Now even without the semi-high room air temp, I have always been getting these ridiculously high temperature readings once I installed Ubuntu; heck, I can't even turn on too many desktop effects cause everything goes through the roof!

What is going on?!?! Can I maybe get some input?

(srry to seem a bit forceful, but I have raised this question a few times before in this thread but people seem to ignore it)

Chris

tx1000z (tx1320us) -- Everything is working (except crazy high heat)

I have the same problem. When I'm running some simulations the CPU temp jumps to 77C. I checked on vista and on the internet and some people have the same issues on using Vista. I think it is a hardware issue, not a linux issue.


(SOLVED) Something I just noticed: when I'm using EnvyNG driver version 96.*, my compiz sometimes uses 100% processing and halts for a couple of seconds. Does anyone have the same problem?

(SOLUTION) download the latest nvidia driver from their site. works fine, but it is a bit painful to install if you are a novice (like me). 

D.

---

### Post by dudafmendes on 2008-06-09
> **samygarib said:**
> Hey,

I just wanted to say that I also had the problem of the blue lines. Ubuntu Hardy amd64 and it was fixed with the new nvidia driver: 173.14.05
It was a little bit painfull though cause you can not upgrade the driver with envy, so you have to install the original nvidia driver after uninstall the other with envy. Don't make the same mistake than me, and DO uninstall the previous one.

Good luck.

After some problems installing the drive I got it working. The Hibernate/Suspend still working fine, Compiz is using much less processing and is not halting, and the GPU temperature is <70F, which is acceptable.



-------------xxxx------------xxxx--------------------

I don't know if anyone has the problem that only one application can use the sound a time. It is fixed by following this tutorial:

(i removed the link... tutorial deprecated although it works, my problem still happening when i'm using skype+ any other software)

Bests,
D.

---

### Post by gborzi on 2008-06-09
@dudafmendes
that tutorial is outdated, although it may work. Hardy uses pulseaudio as sound server, [here]("http://www.pulseaudio.org/wiki/PerfectSetup") there is a web page about setting up pulseaudio.

---

### Post by dudafmendes on 2008-06-10
> **gborzi said:**
> @dudafmendes
that tutorial is outdated, although it may work. Hardy uses pulseaudio as sound server, [here]("http://www.pulseaudio.org/wiki/PerfectSetup") there is a web page about setting up pulseaudio.

Thanks, it is working now, including in skype; I found this guide which is simpler to follow (more like a summary actually)

[http://ubuntuforums.org/showthread.php?t=789578&highlight=skype+Pulse](http://ubuntuforums.org/showthread.php?t=789578&highlight=skype+Pulse)

Duda.

---

### Post by cta16 on 2008-06-12
I feel dumb for asking this but how can I find out what version of Ubuntu I'm using? I know I'm using Hardy but I'm but sure if it's 32-bit or 64-bit. 

The reason I want to know this is because I'm trying to get my touchscreen to work and I've found a tutorial for 64-bit. Not sure if it will work on the 32-bit.

---

### Post by gborzi on 2008-06-12
@cta16
Type *uname -a* at the shell prompt, if you see **x86_64** in the output you're in a 64-bit installation, if you see **x86** then it's 32-bit.

---

### Post by mkarnicki on 2008-06-13
Hi guys,

I haven't written here for a while, but was following you from time to time. I wanted to ask if anyone of you guys has the same problem as I:

It's very easy to spot it while watching any youtube clip. When my tx1320us is unplugged, my CPU stays at 800MHz and the fan stays quite. Now try pluging your HP to AC during any clip. Now the CPU scales to 2GHz (if it drops, no less then 1.6GHz) and the fan kicks-in in a while.

That's quite annoying, since why would I want it to heat up, since while it's unplugged I can watch clips with no hustle and problems. Even if it's npviewer, it doesn't give me any clue what can I do about it.

The only thought which comes to my mind would be tricking my HP it isn't on AC, when it actually is. But that sounds fun, I know that. Any ideas/ppl sharing my problem?

---

### Post by Cuppa-Chino on 2008-06-13
> **mkarnicki said:**
> Hi guys,

I haven't written here for a while, but was following you from time to time. I wanted to ask if anyone of you guys has the same problem as I:

It's very easy to spot it while watching any youtube clip. When my tx1320us is unplugged, my CPU stays at 800MHz and the fan stays quite. Now try pluging your HP to AC during any clip. Now the CPU scales to 2GHz (if it drops, no less then 1.6GHz) and the fan kicks-in in a while.

That's quite annoying, since why would I want it to heat up, since while it's unplugged I can watch clips with no hustle and problems. Even if it's npviewer, it doesn't give me any clue what can I do about it.

The only thought which comes to my mind would be tricking my HP it isn't on AC, when it actually is. But that sounds fun, I know that. Any ideas/ppl sharing my problem?

yes also how do you make the GPU go slow, mine never goes into power save AC - it heats up so much for simple 2d the low speed is surely enough

---

### Post by gborzi on 2008-06-13
@Mkarnicki and Cuppa-Chino
AFAIK, CPU frequency scaling is governed by powernowd. The configuration file is in /etc/default/powernowd and the only option there is "-q" (means quite mode). The frequency scaling behaviour can be changed with the "-m" option. By default it uses the aggressive mode, which means >  Mode 1, AGGRESSIVE, changes frequency by a sawtooth function.     Imme&#8208;
       diately jumps to the highest frequency whenever  CPU  usage  goes  over
       80%,  and decreases by "step" Hz as usage drops below 20%.  This is the
       default behavior.
Read the manpage (man powernowd) for a description of other modes.
Hope this helps.

---

### Post by mkarnicki on 2008-06-13
**@Cuppa-Chino** I have HP tx1320 and I'm on Hardy, powernowd is installed by default, so I didn't do anything to have scaling (yeah, I do like when the fan gets more silent). If you lack this package, you'll find it in synaptic.

**@Gborzi** Thanks for your tips. Helpful as usual. I know it's lame to do with AMD64 2GHz 2core CPU, but I tried scaling it down to 800MHz with
*sudo powernowd -m 2*
and it now behaves as it did while unplugged. It doesn't jump to 2GHz whenever I watch any youtube clip, and I don't feel any slowdowns. And whenever I'll need it, I'll just switch the scaling mode via powernowd :) Thanks!

What I love about ubuntu forums is the support you get. Basically any question finds here it's answer.

---

### Post by cta16 on 2008-06-14
> **gborzi said:**
> @cta16
Type *uname -a* at the shell prompt, if you see **x86_64** in the output you're in a 64-bit installation, if you see **x86** then it's 32-bit.

When I type that in, here's what I get:

```
Linux chris-laptop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

```


**[Solved]**
On another note, I've been wondering how to use an external screen/projector as my main screen instead of the built-in one on the tx1000. I went into the Nvidia Xserver settings and enabled the external one and disabled the current built in one. Then it says I have to restart X server for it to work. I typed in:

```
sudo /etc/init.d/gdm restart

```

After that, a bunch of text were dispayed on a black screen with an [OK] at the end. Does anyone know what is wrong?

**[Solution]**
Whenever I tried to save the configuration file in the Nvidia X Server Settings, I get an error and I'm assuming it does not have the privileges to edit the xorg.conf file. I'm a ubuntu newbie so I don't know how to give privileges to that program. So here's what I did:

1. Copy the xorg.conf file to two different places(from /etc/X11/). For simplicity's sake, I'm going to call them Backup1 and Backup2. I put Backup1 in my home folder and the other on my Desktop
```
sudo cp /etc/X11/xorg.conf /home/YOURNAMEHERE/
sudo cp /etc/X11/xorg.conf /home/YOURNAMEHERE/Desktop/
```
2. When saving the configuration file in the Nvidia X Server Settings, browse to Backup1 and save it there. This will overwrite Backup1 with the xorg.conf that you want.
3. Replace your original xorg.conf with the one that was modified(Backup1). This will replace your current xorg.conf file.
```
sudo mv /home/YOURNAMEHERE/xorg.conf /etc/X11/
```
4. Restart computer and the new monitor should be working if you configured the external monitor right.

When you want to use your old monitor again, use Backup2 and replace your current xorg.conf.
```
sudo mv /home/YOURNAMEHERE/Desktop/xorg.conf /etc/X11/
```

---

### Post by RaZoR1394 on 2008-06-14
Was there any solution to this: [http://ubuntuforums.org/showthread.php?t=711450&highlight=tx1000](http://ubuntuforums.org/showthread.php?t=711450&highlight=tx1000) ?

---

### Post by Thelazygoose on 2008-06-17
Does anybody know how i can get my webcam and mic working in hardy. i am on a tx1000. Also if anyone knows how to fix the  touchscreen yet i would much apretiate it. kind of a newbie to the whole ubuntu, but love it so far. so simple instructions would be  good. Thanks

---

### Post by mkarnicki on 2008-06-17
> **Thelazygoose said:**
> Does anybody know how i can get my webcam and mic working in hardy. i am on a tx1000. Also if anyone knows how to fix the  touchscreen yet i would much apretiate it. kind of a newbie to the whole ubuntu, but love it so far. so simple instructions would be  good. Thanks
Hey Thelazygoose, don't be too lazy ;) You'll find how to fix those in this great (yet long) thread. Search this thread for "uvc" (for webcam), make sure you're mic is not muted in the mixer, and you'll find how to make your touchscreen work somewhere between pages 85-98 (look for "evtouch", I use them. egalax don't work for me).

Edit: by the way, you can also search all posts in this thread by Gborzi, the guy rules and his tips took great part in helping us sort out many issues.

---

### Post by waspbr on 2008-06-23
hmmm seems like things are going to remain quiet until the next distro...

---

### Post by mkarnicki on 2008-06-23
I have solved so many problems by reading this thread I already feel comfortable with my ubuntu 8.04 and I hope very few of us still have problems.

By the way, does anybody know how to automatically enable bluetooth when the computer is turned on? Since I have to turn off and on the "wi-fi" with the switch to enable my bluetooth (I'm using a bluetooth mouse). So it would be cool, if it turned on without having to turn off the wi-fi for a sec.

Cheers to everybody,
Mike

---

### Post by Jeisson on 2008-06-23
> **gborzi said:**
> I have added an [entry]("https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionTX1350el") for the HP TX1350el in the wiki.
I want to thank you again GBorzi. I was silently waiting for that guide :). In fact, I wanted to write one, but my knowledge and my English are not the best for accomplishing the task. I think we can write a shell script that execute all the steps in order to get a fresh Hardy (64?) configured to these series of laptops. That script could help to close new people to Linux. For the moment, I do not have enough knowledge to edit text files by commands (sed) and my time does not help in the learning...

Giuseppe. I implemented your alternative to the ugly fix. It is working well and I feel very comfortable anytime I wake up my HP after a siesta (suspend). Thanks so much, sincerely.

---

### Post by Jeisson on 2008-06-23
I just want to share an information that could be nasty or obvious; but it could save to somebody a headache or something worse.

I still have to use Windows to compile programs for that platform and Palm OS. My development environments got corrupted (nothing new on that) and I had to reinstall Windows again (nothing new on that). Some time ago, I did it using the recovery partition, and everything went as usual. Some months after, I removed the recovery partition to recover space. So, last time I had to use the recovery DVD... And it destroyed all! Windows, data, Linux, documents, music...

If you plan to recover Windows using the DVD, keep on mind, it will format the hard drive to get the computer in "factory condition". No red bold warnings will inform you about it. If you want to make a non-destructive recovery, you will have to use the recovery partition on hard drive instead of the DVD.

Thanks to God Linux exists :D

---

### Post by mkarnicki on 2008-06-24
Ops! Thanks Jaisson. I know some of guys have removed the recovery partition to save space, but I left it in place - and I see that was the right step. Hopefully your post will prevent some of us clean-sweeping our hard drives with the recovery dvds!

---

### Post by gborzi on 2008-06-24
@Jeisson
I'm pleased to know that people, like you and Mkarnicki, appreciate my contribution. As for the script, it will be very difficult to do because the tx1000 is not a single model but a whole series with different hardware. Some wireless devices only work with ndiswrapper, others with b43, hard disks are different, so the Load Cycle Count problem is not an issue for everyone. Also, many of the suggested fixes did not always worked. Problems with hibernate, sleep and the nvidia drivers are still reported.
Finally, some user interaction is needed for calibrating the touchscreen and downloading the Windows drivers for ndiswrapper.
That said, I've to add that I'm cautiously optimistic about the easiness of installing and using GNU/Linux. Before buying the laptop I read that it was Linux-unfriendly with a lot of problems, but actually most of these were solved by newer kernel and newer drivers.

---

### Post by Jeisson on 2008-06-24
Another tip about Windows. Keeping the Recovery Partition plus Windows Vista, requires a lot of space of the hard drive. Around 40GB without installing your applications [I love to remember Ubuntu requires just 4GB with all my programs installed]. So I researched how to free more space and these tips could help somebody to have more space for Windows, Linux, programs and your data. Follow these steps at your own risk:
[LIST]
[*]After installing Windows, you can remove several programs: HP (Demo) Games, MsWorks, MsOfficeDemo, ...
[*]You can remove the redundant installers of those programs: erase the folder C:\SwSetup
[*]Configure the virtual memory to start using a little file (256MB or 0MB). I have 2GB of RAM, virtual memory is not used a lot.
[*]Boot Linux, mount the Vista partition and remove the "C:\System Volume Information" folder. It wastes around 18GB, but Windows hides it and reports 0MB of using, although it increments itself every minute and your hard drive seems to lose space magically.
[*]Removing the "System Volume Information" deletes all your restore points. Boot Vista and make a restore point. It will comsume 1.8GB (10 times less than before).
[*]At this point, your Vista will use around 13GB instead of 30GB. More room to your programs or Linux partitions.
[/LIST]
I don't like to talk about Windows here. I just hope it could help to people running both OS better.

---

### Post by Jeisson on 2008-06-24
@gborzi
You are right. The script could fail from one model to another. I would hope it will work in computers of the same model. So people could report "it is working in my tx####", and other people could improve it if doesn't. All your suggestions have worked for my tx1410us :).

In anycase, I don't know if the effort could be valuable. If other people report interest on the idea, it could be implemented... But, when a new release is made, it could become useless.

I agree with you. Linux is so sweet to install. I recover all my programs running scripts. They download, install and recompile libraries automatically. Although my shell programming knowledge is very limited.

Thanks, another time more Giuseppe.

---

### Post by gborzi on 2008-06-24
> **Jeisson said:**
> @gborzi
You are right. The script could fail from one model to another. I would hope it will work in computers of the same model. So people could report "it is working in my tx####", and other people could improve it if doesn't. All your suggestions have worked for my tx1410us :).

In anycase, I don't know if the effort could be valuable. If other people report interest on the idea, it could be implemented... But, when a new release is made, it could become useless.
I think that even starting now such script, it may get a long time to fix, so that in the meantime there is Ubuntu 8.10...
Also, there are the updates that can make the script obsolete. Today I noticed envy has been updated to use nvidia drivers 173.14.05.

---

### Post by Jeisson on 2008-06-25
Giuseppe. Your answer convinced me. I took advantage of your notice about envy and I am enjoying the new nVidia driver :D.

By the way. Are you using the fingerprint reader in login/sudo/gksudo?

Best regards ;)

---

### Post by gborzi on 2008-06-25
@Jeisson
I'm not using the fingerprint reader. I've tried it, but it often fails to recognize my fingerprint, perhaps because it's so small.

---

### Post by beavermml on 2008-06-25
hello... 

can someone GUIDE me how to make the rotation button works?
my touchscreen works perfectly and i love it. 

im using hardy on my tx1121au.. 

please help me..

---

### Post by pmaconi on 2008-06-25
It seems that this laptop is prone to [bug #203537]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537"), which occasionally corrupts the entire filesystem on a resume from suspend or hibernate. I've had it happen to me twice so far, in the past week. 

According to the bug report, a work around is to add iommu=soft to the boot options. This may or may not lower performance slightly, which is a hit I'm personally willing to take. Hopefully this doesn't happen to any of you.

---

### Post by gborzi on 2008-06-25
@Pmaconi
Thanks for the warning. I've checked my /var/log/dmesg* files for the IOMMU string, but found none. From the bug report you mentioned, it seems that this problem arises if you have more than 2GB RAM. Is this your case?

---

### Post by pmaconi on 2008-06-25
Yeah. I forgot to mention that. I have 4GB of RAM.

---

### Post by isachan on 2008-06-25
My hard drive was totally hosed 2 weeks ago also, and exactly when I tried to wake up my tx1000 CTO from suspend. I just upgraded my RAM to 4GB too. The bug even had corrupted Vista and Recovery partitions.
(I can take off the Vista sticker from my machine !)

My only worry is the future BIOS update without Vista.

I had to reinstall Kubuntu 8.04, but now it seems to run a little better than before (by the feeling).

Oh well.

Isao

---

### Post by gborzi on 2008-06-25
> **isachan said:**
> 
My only worry is the future BIOS update without Vista.

You can use a Vista Live CD to update the BIOS, as I mentioned [here]("http://ubuntuforums.org/showpost.php?p=4986158&postcount=1020"). I'm going to update the wiki page for the tx1350el about this bug which is a serious issue.

---

### Post by OniShiro on 2008-06-26
I just bought a tx1320, I installed ubuntu 8.04 and after a lot of suffering managed to make work the broadcom wifi.

I also installed the egalax touchscreen driver but I'm having some trouble with it.

I calibrated the touchscreen and it works but I can't move windows or open menus. When I click on the window bar and drag, the hand cursor turns into the normal cursor right way and the window doesn't move, and when I click on a menu it closes right away. I think it's sending a double click instead of a click.

Any help on how to fix my touchscreen would be really appreciated.

Thanks in advance.

---

### Post by isachan on 2008-06-26
You can change the strange double click effect on the touchscreen with TouchKit if you're using eGalax driver.

Just select the last tab (or somewhere close) on the top of the content panel, and you can choose either mouse button press and release for one tap on the screen, just a press, or just a release.

I tried all three, but I just left it at the default press+release setting.

I hope this works.

Isao

---

### Post by OniShiro on 2008-06-26
What version of the drivers are you using? I'm using the non-beta ones and tried the 3 options but none fixed my problem.

> **isachan said:**
> You can change the strange double click effect on the touchscreen with TouchKit if you're using eGalax driver.

Just select the last tab (or somewhere close) on the top of the content panel, and you can choose either mouse button press and release for one tap on the screen, just a press, or just a release.

I tried all three, but I just left it at the default press+release setting.

I hope this works.

Isao

---

### Post by isachan on 2008-06-26
Like I said on my previous post, I just reinstalled my Hardy a few days ago, and I haven't got around to reinstall my eGalax.

Before, I was using version 2.20.x or something, and I think that is a beta version.

Search for egalax beta driver in this thread and download the last one.

Isao

---

### Post by pmaconi on 2008-06-27
Could someone tell me how to correctly setup uswsusp? s2disk works perfectly for me, but the hibernate button doesn't use it (and also doesn't work... it doesn't resume for me).

---

### Post by FirstByté on 2008-06-29
> **waspbr said:**
> okay, since there have been many people asking about the touchscreen on gutsy I have decided to make a small HowTo, bear in mind that for some reason this doesn't work in hardy yet:

the first thing to do is to download the drivers

the drivers can be found here: [http://210.64.17.162/web20/TouckDriver/linuxDriver.htm]("http://210.64.17.162/web20/TouckDriver/linuxDriver.htm")

there are both the 64 and 32 bit versions available, anyway you should download the ones for the 2.6 kernel.

After that, decompress and copy the files to the appropriate folders. The extracted file is the "TouchKit" folder, I find it handy to keep it in the home folder directory.

```
tar xvfz TouchKit_1.07.0831.tar.gz
cd TouchKit
sudo cp egalax_drv.so /usr/lib/xorg/modules/input/

```

if you are using gutsy amd64 then these are the commands for u

```

tar xvfz TouchKit64_1.07.0907.tar.gz
cd TouchKit64
su
cp egalax_drv.so /usr/lib64/xorg/modules/input/
```

note that the only difference is that gutsy 64 uses /usr/lib64/ instead of /usr/lib/

if you are like I was in the beginning  and don't like to use the tar command, just double click it, extract to desktop, go to terminal type

```
sudo nautilus
```

and manually copy the file  egalax_drv.so to the  [COLOR="Red"]/usr/lib/xorg/modules/input/[/COLOR]  folder. just be careful not to change anything  else.

next edit your xorg

```
sudo gedit /etc/X11/xorg.conf
```

there add to the "ServerLayout" Section near the bottom of your xorg  the following line (without the ... )
```
...
InputDevice    "EETI"      "SendCoreEvents"
...

```

the add this somewhere else in the file, I like to keep things sorted so I put mine next to the other InputDevices near the top

```

Section "InputDevice"
      Identifier "EETI"
      Driver "egalax"
      Option "Device"    "/dev/usb/hiddev0"
      Option "Parameters" "/etc/egalax.cal"
      Option "ScreenNo"   "0"
EndSection

```

Alternatively if you experience any problems, like conflicts with other usb devices, you may wanna make a small modification in the device option above as follows

```
Option "Device" "usbauto"
```

okay then, moving on...

you are almost done,  I found out that a few modules make it hard for the pc to detect the device so what you do is to blacklist some of them

I noticed that the  /dev/usb/  folder was disappearing because of  these two buggers

usbtouchscreen
tkusb

 
this is easily solved by 

```
 sudo gedit /etc/modprobe.d/blacklist
```


add the following lines to the end of the document

```

#cause touchscreen drivers to malfunction
blacklist usbtouchscreen
blacklist tkusb  
```

reboot, then go to terminal (I assume that you have placed the TouchKit folder into your home folder if not just cd to it)

```
cd TouchKit
sudo ./TouchKit
```

this is going to open a dialog, if you see a tools tab, then it worked, if not then review what you did and post here if u get stuck.

This method worked on gutsy amd64 as well as the 32 bit version.So far it still does not work for hardy alpha 6.

good luck

Hey! I dont know how better to thank you mate...! 

You resurrected my hp tx1417cl [tx1000]. Would continue the battle of the fingerprint reader I loved so much on vista.

[I'm a noob to linux who might say wasted over 17yrs on windows...chased down here by vista :-D]

Thanks once again!

---

### Post by Cuppa-Chino on 2008-07-01
is performance better with the EETI driver ?

also has anybody else had the touchpad freeze ? I had a total mouse freeze yesterday and ended up using the touchscreen, not very fun of course...

---

### Post by creatureofthedark on 2008-07-04
hi iv just upgraded to 8.04 hardy. 

I'm half way threw reading all 113 pages but i was just hopping that some one could give me a link to fix the touch screen and the wireless card (assuming it has been done).

my laptop model is Tx120ea

i have also just noticed a problem when closing the lid! the screen goes strange and flashes a lot

any help would be greatly appreciated

---

### Post by creatureofthedark on 2008-07-04
just got wifi to work!!!

[http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

just touch screen now and i will have the essentials :P

---

### Post by crazyness003 on 2008-07-04
> **creatureofthedark said:**
> just got wifi to work!!!

[http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

just touch screen now and i will have the essentials :P

Well actually depending on what kernel number you have and what wi-fi card you got, wireless will work through restricted drivers.

I have a Broadcom BCM4311 rev2 and i have wirless only using the 2.6.24-19 kernel. And that was using point and click in the restricted modules. So NDISwrapper isnt the only way. For extensive Broadcom Driver setup and troubleshooting, see this: [http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

As for the touchscreen, i was wondering if anyone can gimme a link to the best working touchscreen How To. There seems to be a lot on this thread (btw: This thread is WAY too big)

Thanks

---

### Post by avik on 2008-07-04
creatureofthedark,

[I used this post to get the touchscreen working, thanks to gborzi.]("http://ubuntuforums.org/showpost.php?p=4782599&postcount=862")

> 
i have also just noticed a problem when closing the lid! the screen goes strange and flashes a lot


Many people have complained about that.  I'm looking at the latest developments to see if there's been any progress, and I'll edit this if I find anything.

EDIT: The only thing I could find is that NVIDIA was supposed to release some new drivers, but even with the latest updates, I'm having the same issue.

---

### Post by gborzi on 2008-07-04
@avik
with latest NVIDIA update you mean version 173.14.05? I installed them (by means of envyng) and they work fine. In case this version doesn't work correctly on you tablet, try the older driver, i.e. nvidia-glx.

---

### Post by avik on 2008-07-04
> 
with latest NVIDIA update you mean version 173.14.05? I installed them (by means of envyng) and they work fine. In case this version doesn't work correctly on you tablet, try the older driver, i.e. nvidia-glx.

I see.  So nvidia-glx-new doesn't have the latest driver yet?  I might look into using Envy, but ever since the driver (even a slightly older version) entered the repos, I've avoided manual methods as much as possible.

---

### Post by gborzi on 2008-07-04
The nvidia-glx-new package is still at version 169.12. It's not much older then the latest but it suffer from the flickering bug.

---

### Post by creatureofthedark on 2008-07-05
thanks avik iv managed to get to the calibration stage but i cant work it out. iv been using this guide [http://ubuntuforums.org/showpost.php?p=2792971&postcount=16]("http://ubuntuforums.org/showpost.php?p=2792971&postcount=16") but i get the error ev_calibration cannot be found

how did you manage to calibration it???

---

### Post by gborzi on 2008-07-05
@creatureofthedark
Look at this [post]("http://ubuntuforums.org/showpost.php?p=4784444&postcount=869") of mine, it explains the procedure step by step.

---

### Post by creatureofthedark on 2008-07-06
ok i followed the links and all i have now is the the mouse just moves about randomly when i touch the screen! any ideas what im doing wrong?

---

### Post by crazyness003 on 2008-07-06
I have a quick question.

Through the readings here, i noticed two separate approaches to getting touchscreen to work.
1. Evtouch
2. Touchkit

Now, i did try the evtouch approach and couldnt get it to work (all it did was click in the cursor's current location, no matter where i touched the screen)

With touchkit, it actually works but has come bizzare effects (when touch the screen it immediately clicks and created a selection box but dosnt let go, it double clicks on single click, etc)

My question is: Which is better?
Since i have Touchkit working, im gonna stick with it for now, but im thinking of reinstalling Hardy (due to some errors i got from over-experimentation :D ). When I reinstall, should I go with touchkit or evtouch? Which is "better" or "easier". Im sure everyone has different opinions. Thats what i wanna hear tho.
Thanks

PS: If anyone can explain to me how i can tame touchkit so it does what i want it to do, that would be nice. The GUI is a little...limited.

---

### Post by gborzi on 2008-07-06
@creaturefromthedark
Post your xorg.conf Section for the touchscreen, it's difficult to say what went wrong without any clue.
@crazyness003
Sorry, I can't help here, I've not used Touchkit.

---

### Post by ccw127 on 2008-07-07
Does anyone know the how I can hot swap my cd/dvd drive? I have never tried to do this under linux as this tx1320us is my first laptop with such a device.

Chris

p.s. I hope I never have to reinstall my os as my touchscreen is working great and I really do not remember how I got it going...

---

### Post by Cuppa-Chino on 2008-07-07
> **crazyness003 said:**
> I have a quick question.

Through the readings here, i noticed two separate approaches to getting touchscreen to work.
1. Evtouch
2. Touchkit

Now, i did try the evtouch approach and couldnt get it to work (all it did was click in the cursor's current location, no matter where i touched the screen)

With touchkit, it actually works but has come bizzare effects (when touch the screen it immediately clicks and created a selection box but dosnt let go, it double clicks on single click, etc)

My question is: Which is better?
Since i have Touchkit working, im gonna stick with it for now, but im thinking of reinstalling Hardy (due to some errors i got from over-experimentation :D ). When I reinstall, should I go with touchkit or evtouch? Which is "better" or "easier". Im sure everyone has different opinions. Thats what i wanna hear tho.
Thanks

PS: If anyone can explain to me how i can tame touchkit so it does what i want it to do, that would be nice. The GUI is a little...limited.

well the gui is all you got, the key are tabs with the tapings, I am also personally struggling with its click behavior but find the accuracy and reaction speed LEAGUES better than evtouch

> **ccw127 said:**
> Chris
p.s. I hope I never have to reinstall my os as my touchscreen is working great and I really do not remember how I got it going...

to get touchscreen working with evtouch you need this post:[http://ubuntuforums.org/showpost.php?p=5051175&postcount=1057]("http://ubuntuforums.org/showpost.php?p=5051175&postcount=1057")


and to remember stuff get the **SCRAPBOOK** extension and locally save the pages you need - then backup on cd/usb/separate partition and restore when reinstalling, has been a life saver for me...

---

### Post by crazyness003 on 2008-07-07
> **Cuppa-Chino said:**
> well the gui is all you got, the key are tabs with the tapings, I am also personally struggling with its click behavior but find the accuracy and reaction speed LEAGUES better than evtouch

So the xorg.conf file dosnt play much of a a role with it. I use Touchkit for my winXP partition and i like it ( first thing i did was remove Vista when i got this thing). It worked as good, if not better than the vista driver. Oh well.

Let us know if you make a breakthrough.

Thanx

---

### Post by DalleP on 2008-07-13
Touchscreen problem with Nvidia 173.14.05 driver (?)
I am using Hardy 8.04 on a tx1040ea. Before I used the standard nvidia (169.12) driver and got the Touchscreen to work flawlessly after Edmondt's instructions ( [http://ubuntuforums.org/showpost.php?p=5051175&postcount=1057](http://ubuntuforums.org/showpost.php?p=5051175&postcount=1057) ). But I had problems with the graphics being messed up after a black screen. After a clean installation I upgraded to the 173.14.05 driver and the graphics are working fine, but now the Touchscreen is not working. I tried to blacklist usbtouchscreen and tkusb without success.
Any ideas?

Ps. Thanks for all the hard work!

---

### Post by gabesword on 2008-07-13
I'm running Hardy and have a problem.  Every time the laptop goes into sleep mode, or whatever it is called when you don't input anything for a few minutes, when it wakes up the display is all screwed up.  Restarting X fixes it, but the problem is annoying.

Does anyone know the solution?

---

### Post by RaZoR1394 on 2008-07-13
> **gabesword said:**
> I'm running Hardy and have a problem.  Every time the laptop goes into sleep mode, or whatever it is called when you don't input anything for a few minutes, when it wakes up the display is all screwed up.  Restarting X fixes it, but the problem is annoying.

Does anyone know the solution?

Upgrade your nVidia driver to the latest one. I think you may have to use Envy to get the correct one.

This problem has surfaced before in this thread.

---

### Post by DalleP on 2008-07-13
Gabesword
You can use the Synaptic installer and chose the nvidia-glx-new-dev-envy package. This gives you the 173.14.05 driver which solves the problem. Please tell me if you run into problems with the touchscreen when updating the driver, see above post.

---

### Post by gabesword on 2008-07-13
Thanks for the tips.  That solved the problem.

I haven't gotten the touchscreen going yet on this Hardy install.  I had it working previously, but I haven't had the time yet on this install.

---

### Post by manu456 on 2008-07-14
My wireless stopped working suddenly one morning. (I am using ndiswrapper with hardy)

The problem is that my network device has vanished! **lspci does not show the wireless card** :shock:

Does that mean that there is a hardware problem with my card?

I dond't have windows anymore to check if it works there and also my hardware warranty just expired 2 days ago ](*,)

Any suggestions?

---

### Post by TSS on 2008-07-14
I'm on a tx1220 /w Hardy and I'm tryin go get the microphone to work.  It's recognized in Alsa mixer, and I can even switch between Front and ATAPI mics, but Sound Record is not picking up anything.  I searched this thread with no luck.  No other sound problems of note either.

Thoughts?

And as for the wireless card disappearing, I have a thought that is in no way technical.  I've got a switch on the front right of my comptuer that can turn the wireless on and off.  If you have the same switch, make sure it's set so the wireless is on :-p.

---

### Post by manu456 on 2008-07-14
> **TSS said:**
> I'm on a tx1220 /w Hardy and I'm tryin go get the microphone to work.  It's recognized in Alsa mixer, and I can even switch between Front and ATAPI mics, but Sound Record is not picking up anything.  I searched this thread with no luck.  No other sound problems of note either.

Thoughts?

What software are you using for recording? Both my mics seem to work fine with audacity.

> **TSS said:**
> And as for the wireless card disappearing, I have a thought that is in no way technical.  I've got a switch on the front right of my comptuer that can turn the wireless on and off.  If you have the same switch, make sure it's set so the wireless is on :-p.

I've already gone through this once before when I spent at least 2 days trying to figure out why my wireless wasn't working. :-P

But unfortunately that's not the case this time. The switch is on and bluetooth is working fine (since that switch also shuts down bluetooth). I think I've lost my wireless card :sad: I can't think of any other explanation. 

I have a gentoo install that I haven't used for a while and grub doesn't recognize it right now. I will configure it back and see if the card shows up in gentoo as it runs an older kernel...

---

### Post by DalleP on 2008-07-14
TSS
About the mic problem. I had it too, but playing around with the settings in volume control for a while I got it to work. i can't remember exactly what I did. I am only using an external mic, and for that I use "capture" for recording and in options I use "Front mic". And make sure to set up the volume of the mic so that it is not muted. I hope my rambling is of any help...

manu456
In Hardy you can use the b43 driver. All I did to get wireless to work was:
sudo apt-get install b43-fwcutter
and then reboot. Since this is more simple than using the ndiswrapper it might be a good idea to try it.

---

### Post by TSS on 2008-07-14
> **manu456 said:**
> What software are you using for recording? Both my mics seem to work fine with audacity.


I'm just using Sound Recorder that comes with Gnome.  I also gave it a try in Skype with no luck.

---

### Post by waspbr on 2008-07-18
dallep, what is your wireless card, do a lspci for us...

I am asking that cos as far as I know my card is not (yet) supported, bcm 4328 rev 03

---

### Post by DalleP on 2008-07-18
Here's my lspci:
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

---

### Post by crazyness003 on 2008-07-18
> **DalleP said:**
> Here's my lspci:
...
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

Shouldnt the new kernel supported hardy kernel (2.6.24-19) automatically detect and enable that card. I have the BCM4311 and only by kernel upgrade did I manage to get wi-fi. Check to see what kernel you have by typing this in the terminal
```
uname -r
```

---

### Post by DalleP on 2008-07-20
Again regarding my touchscreen problem. I tried to use a different graphicsdriver and installed the glx-new driver (161.14) via the Synaptic manager. This resulted in the computer not recognizing the hardware. So I went back to the glx-new-dev-envy (173.14.05) driver and the graphics are fine again. Furthermore I got a response from the touchscreen! When I tap the screen the trashcan opens, due to the calibration being of and only responds in the lower right corner where the trash can is in my system.

I am now using the evtouch driver, so I exited x and went to tty-1 and ran the calibration sucessfully. My values where [MinX,MinY,MaxX,MaxY]=[77,148,3994,3978], and I copied them to xorg as described in [http://gentoo-wiki.com/HARDWARE_HP_tx1000#Touchscreen](http://gentoo-wiki.com/HARDWARE_HP_tx1000#Touchscreen) . But when I restart x and try it out I get totally random response to the taps, or when drawing in e.g. gimp.

I have since tried the egalax driver again, but there I get no response at all from the touchscreen.

Can anyone help me?

[System details: Computer TX1040ea, Ubuntu 8.04, Kernel 2.6.24-19-generic]

---

### Post by hojthojt on 2008-07-21
@TSS
I got both the built in microphone and a headset microphone to work, but when I first recorded something with the sound recorder, the volume I got in the recording was very low. With my previous experience with Gutsy, I immediately suspected wrong settings in alsamixer, and with some trial-and-error I got it to work fine. 

First you should start the alsamixer GUI (by double click on the volume control icon) and make sure no devices are muted and that the levels are high enough. 

Unfortunately, there is an important setting that for some reason cannot be accessed through this GUI interface. Instead you need to use alsamixer from a command line terminal:

```
alsamixer -V all
```

Now use the right arrow key to select the setting column called "Capture", when selected use the up/down arrow keys to set an appropriate level (the default was set very low for me). Also note that the built-in microphone is called "ATAPI Mic" and any externally connected microphone is called "Front mic" in alsamixer.

---

### Post by phattyacid on 2008-07-22
> **DalleP said:**
> 



I have since tried the egalax driver again, but there I get no response at all from the touchscreen.

Can anyone help me?

[System details: Computer TX1040ea, Ubuntu 8.04, Kernel 2.6.24-19-generic]

make sure your xorg.conf has these lines

### Touch Configuration Begin ###
Section "InputDevice"
	Identifier "EETI"
	Driver "egalax"
        **Option "Device" "/dev/usb/hiddev0"**
        Option "Parameters" "/var/lib/eeti.param"
	Option "ScreenNo" "0"
EndSection
### Touch Configuration End ###

if what is in bold says usbauto it likely will not work as egalax will select some weird non-existant device.

the calibrate with TouchKit started from terminal prompt.

---


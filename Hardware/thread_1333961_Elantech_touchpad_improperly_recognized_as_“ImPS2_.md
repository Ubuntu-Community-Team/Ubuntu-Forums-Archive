---
title: "Elantech touchpad improperly recognized as “ImPS/2 Logitech Wheel Mouse”"
date: 2009-11-21
forum: Hardware
---

### Post by dozy on 2009-11-21
Hello everyone!
This is my first post. I hope I have posted it in the appropriate section.

Here is the problem I'm having:
I just purchased the Asus K61IC-A1 laptop and installed Ubuntu 9.10 on it.
Everything is now working properly with the exception of the Touchpad, which is made by Elantech.
To clarify, the Touchpad does function correctly, but I cannot configure some of its properties.
I want to disable 'click' on the pad, but when I go to System->Preferences->Mouse, there is no 'Touchpad' tab; which is where the 'Enable mouse clicks with touchpad' option is located.

I assume this is a driver/detection issue but I don't really know how to proceed.

I did find some information about Elantech touchpads in Ubuntu on eeepc's but it did not help, it just kept breaking X.

Here is the relevant section of my /proc/bus/input/devices (which shows the improper detection - i think!?) and my whole xorg.conf:

-------start /proc/bus/input/devices-------
I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input9
U: Uniq=
H: Handlers=mouse1 event9
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103
-------end /proc/bus/input/devices-------


-------start xorg.conf-------
Section "Screen"
          Identifier "Default Screen"
          DefaultDepth 24
EndSection
Section "Module"
          Load "glx"
EndSection
Section "Device"
          Identifier "Default Device"
          Driver "nvidia"
          Option "NoLogo" "True"
EndSection
-------end xorg.conf-------


Thanks in advance for any help you can provide!

---

### Post by Kerin on 2009-11-30
Affects me on my Dell Mini 10 (1010.)

---

### Post by lalada on 2009-12-13
Any solution found yet?

---

### Post by sg3524 on 2009-12-23
Solution found for me in Karmic.

I have an Asus U81 (Best Buy version of the U80) which has the Elantech mousepad.

A friend shared this solution.

9.10 includes an X configuration utility called xinput.  It is a command line tool.  To see the many things you can do with this simply type xinput at a shell prompt.

Start by typing in:
> xinput list

This will show you all the input devices attached to your computer.  You will need to know your mousepad's id to continue.  On My Asus laptop the internal pointer was found as a "ImPS/2 Logitech Wheel Mouse".  The Id I get after booting my system with my external mouse attached is 10.

Next you need to know how to disable the mousepad.  So you need to know what properties it supports. the command is "xinput list-props" followed by your mousepad's id number, which for me was: 
> xinput list-props 10

The "Device Enabled" was what I needed to be able to use to switch it off.  On my laptop this line was "Device Enabled (97):   1".  The parenthesized number is the properties id number, the 1 that follows it is the value (0 will turn it off).

So now I need to set it such that the mousepad is disabled.  My mousepad id is 10, property id I want to set is 97 and I need to set the property value to be 0.  The option for xinput is set-int-prop which needs deviceid, propertyid, format of the value (8, 16, or 32 bit), and the value itself.  For me this is:
> xinput set-int-prop 10 97 8 0

To turn it back on:
> xinput set-int-prop 10 97 8 1

Since this does its work on the X in memory it is not persistent.  If you log out and back in the mousepad will be active again.  This is desired behavior for me as I occasionally need to be able to use the laptop without my external mouse.

When I get a little time, I will write a small shell script that can toggle it on or off based on a grep of the output of "xinput list" and bind it to a key combination so I can do this without having to drop out to a script. (EDIT NOTE:  See post #15 in this thread if you want the scripts)

One last note, xinput interacts with X.  It will not be able to function at a normal terminal screen not running under your X.  It will work just fine in an xterminal (the one under accessories menu).

Gram

---

### Post by c901906 on 2009-12-25
sg3524,

Thank you. Works great. I made a slight modification that I believe is a little more robust. Instead of using the id, use the actual string:

xinput set-int-prop "ImPS/2 Logitech Wheel Mouse" 97 8 0

---

### Post by sg3524 on 2009-12-26
> **c901906 said:**
> sg3524,

Thank you. Works great. I made a slight modification that I believe is a little more robust. Instead of using the id, use the actual string:

xinput set-int-prop "ImPS/2 Logitech Wheel Mouse" 97 8 0

That's actually a lot better solution.  I should have tried that, since the id can change depending on the number of devices attached at boot time.

Thanks for posting it!

---

### Post by QuanTime on 2009-12-26
ive been wrestling with this for a while.  Asus laptop, touchpad is identified as a PS2 mouse.  All i want to do is enable the "disable touchpad while typing" function as im ALWAYS lightly brushing it and end up typing somewhere other than what i want.

Its a elantech and any help on this matter would be HUGELY appreciated.

karmic 9.10 x86_64 - 2.6.31-16

---

### Post by abandonedthe_mulletator on 2009-12-27
I am in the same situation as QuanTime.  I have a new ASUS K60 laptop with Karmic Koala.  I just want to disable the touchpad while typing.

---

### Post by QuanTime on 2009-12-27
[http://ubuntuforums.org/showthread.php?p=8505087#post8505087](http://ubuntuforums.org/showthread.php?p=8505087#post8505087)

Thats as far as i got.. Im on a K70 Asus laptop..  So it seems to be some sort of common problem with the Asus.

What does the Asus EEEpc use ?  I read somewhere it uses elantech.. but i could be wrong.. Is this some way it might help us ?

Incidently, you tried the webcam with skype ? i got that sorted.  The video from my cam was inverted.  But submitted a bug and the dev fixed it.. Freakin my hero !!

Now just get this sorted, and im set.

---

### Post by abandonedthe_mulletator on 2009-12-28
Yeah my webcam is flipped.  How can I fix that?  If you submitted a bug it should cover mine too, right?

---

### Post by QuanTime on 2009-12-28
[http://people.fedoraproject.org/~jwrdegoede/libv4l-0.6.4-test.tar.gz](http://people.fedoraproject.org/~jwrdegoede/libv4l-0.6.4-test.tar.gz)
from [email]hdegoede@redhat.com[/email]
> 
1. Install 
=========== 

Howto install and test libv4l depends on your system. There are 
different instructions for if you have a 32 bit system or a 64 bit system. 
which is using multilib. A 64 bit system without multilib is the same as 
a 32 bit system. 

To find out what you have do: 
ls -d /usr/lib64 

If this command gives a "No such file or directory" error, use the 
Non multilib instructions, if the second command is successfull, you have multilib, 
to find out which version (dubbed Fedora and Ubuntu multilib, because those are 
the most well known examples, do): 

ls -d /usr/lib32 
If this command gives a "No such file or directory" error, use the Fedora multilib 
instructions. If this command succeeds use the Ubuntu multilib instructions 

Non multilib instructions: 
------------------------------- 
tar xvfz libv4l-<version>.tar.gz 
cd libv4l-<version> 
make PREFIX=/usr 
sudo make install PREFIX=/usr 

Fedora Multilib instructions: 
----------------------------------- 
Basic 64 bit install: 
tar xvfz libv4l-<version>.tar.gz 
cd libv4l-<version> 
make PREFIX=/usr LIBDIR=/usr/lib64 
sudo make install PREFIX=/usr LIBDIR=/usr/lib64 

If you also want to use 32 bit apps (such as skype), you 
will need to have the 32 bit libc headers installed, on Fedora 
this can be done like this: 
Fedora 10-: "sudo yum install glibc-devel.i386" 
Fedora 11:  "sudo yum install glibc-devel.i586" 
Fedora 12+: "sudo yum install glibc-devel.i686" 
Then do: 
make clean 
make PREFIX=/usr CFLAGS=-m32 LDFLAGS=-m32 
sudo make install PREFIX=/usr 

Ubuntu Multilib instructions: 
----------------------------------- 
tar xvfz libv4l-<version>.tar.gz 
cd libv4l-<version> 
make PREFIX=/usr 
sudo make install PREFIX=/usr 

If you also want to use 32 bit apps (such as skype), you 
will need to have the 32 bit libc headers installed, on Ubuntu 
this can be done like this: 
sudo apt-get install libc6-dev-i386 
Then do: 
make clean 
make PREFIX=/usr CFLAGS=-m32 LDFLAGS=-m32 LIBDIR=/usr/lib32 
sudo make install PREFIX=/usr LIBDIR=/usr/lib32 


2. Testing 
======== 
You have a chance that your webcam app use libv4l or have an appropriate 
script starting it. In that case you don't have to do anything. Just run 
the application. This is the most common situation with Ubuntu and Fedora 
packages. If your problem remains unsolved, then your app might not use libv4l. 
In that case start the application from a terminal like this: 

Non multilib: 
---------------- 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so <your favorite webcam app> 

Note on Ubuntu sometimes skype is using a wrapper script, so if skype 
does not work try: 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real 

Fedora multilib: 
-------------------- 
For 64 bit applications (allmost all apps): 
LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so <your favorite webcam app> 

For 32 bit applications (you only need it for proprietary softwares, which 
don't have a 64 bit version, like skype): 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 

Ubuntu multilib: 
-------------------- 
For 64 bit applications (allmost all apps): 
LD_PRELOAD=/usr/lib64/libv4l/v4l1compat.so skype 

For 32 bit applications (you only need it for proprietary softwares, which 
don't have a 64 bit version, like skype): 
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype 

Note on Ubuntu sometimes skype is using a wrapper script, so if skype 
does not work try: 
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real 


Please let me know if this version of libv4l turns the image the 
right way up for you. 

If not, please do: 
cat /sys/devices/virtual/dmi/id/board_name > name.txt 
cat /sys/devices/virtual/dmi/id/board_vendor > vendor.txt 

And mail the 2 created files to me. It is important to use the 
">" operator here, as I need any whitespace inside this files 
exactly as is. 


---

### Post by abandonedthe_mulletator on 2009-12-28
Thanks QuanTime but that did not work. In fact now when I run the webcam in skype or vlc the program crashes.  gstreamer-properties displays the webcam fine but it is still flipped.  How do I undo those steps?

---

### Post by QuanTime on 2009-12-28
not sure on how to roll-back.. BUT do what is explained in this post:
[http://ubuntuforums.org/showpost.php?p=8535381&postcount=197](http://ubuntuforums.org/showpost.php?p=8535381&postcount=197)
And you might wanna read that thread.. But either way, its how i got my result.. He is the dev for the libv4l (library Video for linux).  
Hope that helps you some..

---

### Post by abandonedthe_mulletator on 2009-12-29
Ok I got the webcam sorted out.  Thanks to Hans on this thread [http://ubuntuforums.org/showthread.php?p=8579914#post8579914]("http://ubuntuforums.org/showthread.php?p=8579914#post8579914")

The touchpad is driving me nuts though.

---

### Post by sg3524 on 2010-01-10
I wrote a couple of shell scripts to turn the touch pad off and back on using the methodology I posted in a previous post.  The only change was to use the device name rather than device id as c901906 suggested in the post following mine.

If you want to use these scripts you will need run "xinput list" and make sure your touch pad is identified (as mine is) as a "ImPS/2 Logitech Wheel Mouse".  If it is not, you can modify these two scripts to use the device name your touch pad is recognized as.

Download the tar file I attached to this post.

Untar the files to a location somewhere in your home directory (mine are in ~/applications/mouse directory).  Make sure both files are executable (chmod 775 filename).

Then go into keyboard shortcuts under System->Preferences and add two shortcuts.  I called mine EnableTouchPad and DisableTouchPad.  For each put in the paths to the appropriate script for each command.

So in mine, I created EnableTouchPad shortcut with the command /home/username/applications/mouse/enable-tp.sh, and DisableTouchPad with the command /home/username/applications/mouse/disable-tp.sh .

Then in the list of shortcuts, got to your new shortcuts and click on the right column where it says "disabled".  Then press the key combination you want to user for that shortcut.  In my case I use control-alt-0 to disable the touchpad and control-alt-1 to enable it.

Now I can disable the touch pad at any time by using the key combination control-alt-0 .  If I need to enable it I use the key combination control-alt-1 .

Works like a champ.

---

### Post by QuanTime on 2010-01-11
thats not a bad solution.. But i would still prefer it to disable only while i was typing.  Would make like much easier.

Such is life i guess.  Thanks heaps for your app, ive not tried it yet, but ill give it a whirl at some point..

---

### Post by abandonedthe_mulletator on 2010-01-11
The script does not work on my machine.  Even if I just run the command "xinput set-int-prop "ImPS/2 Logitech Wheel Mouse" 97 8 0" It does not work.  I tried it as sudo and I tried using the id number instead of the string and no luck.  

xinput list gives me this:

```
"ImPS/2 Logitech Wheel Mouse"	id=2	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 7
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```

Weird.  Its not the solution I need though anyway but it would be helpful.  Why does syndaemon not work with the Elantech touchpad?      This touchpad is driving me crazy!!!  It screws up everything I type, it is happening right now.

---

### Post by abandonedthe_mulletator on 2010-01-15
I've had some unnatural things happening with my touchpad.  It was moving all around the screen and clicking randomly.  It opened programs and stuff.  The madness continued even after I put the laptop down and was not touching it.


This happened today and yesterday.  Yesterday it stopped on its own and today I had to reboot.

Not only is my touchpad not recognized properly it is apparently cursed too.

WTF?

---

### Post by metrofun on 2010-02-03
> **sg3524 said:**
> Solution found for me in Karmic.

I have an Asus U81 (Best Buy version of the U80) which has the Elantech mousepad.

A friend shared this solution.

9.10 includes an X configuration utility called xinput.  It is a command line tool.  To see the many things you can do with this simply type xinput at a shell prompt.

Start by typing in:


This will show you all the input devices attached to your computer.  You will need to know your mousepad's id to continue.  On My Asus laptop the internal pointer was found as a "ImPS/2 Logitech Wheel Mouse".  The Id I get after booting my system with my external mouse attached is 10.

Next you need to know how to disable the mousepad.  So you need to know what properties it supports. the command is "xinput list-props" followed by your mousepad's id number, which for me was: 


The "Device Enabled" was what I needed to be able to use to switch it off.  On my laptop this line was "Device Enabled (97):   1".  The parenthesized number is the properties id number, the 1 that follows it is the value (0 will turn it off).

So now I need to set it such that the mousepad is disabled.  My mousepad id is 10, property id I want to set is 97 and I need to set the property value to be 0.  The option for xinput is set-int-prop which needs deviceid, propertyid, format of the value (8, 16, or 32 bit), and the value itself.  For me this is:


To turn it back on:


Since this does its work on the X in memory it is not persistent.  If you log out and back in the mousepad will be active again.  This is desired behavior for me as I occasionally need to be able to use the laptop without my external mouse.

When I get a little time, I will write a small shell script that can toggle it on or off based on a grep of the output of "xinput list" and bind it to a key combination so I can do this without having to drop out to a script. (EDIT NOTE:  See post #15 in this thread if you want the scripts)

One last note, xinput interacts with X.  It will not be able to function at a normal terminal screen not running under your X.  It will work just fine in an xterminal (the one under accessories menu).

Gram

Thanks a lot.It helped me on my ASUS k40AB

---

### Post by yaddoshi on 2010-02-08
> **QuanTime said:**
> thats not a bad solution.. But i would still prefer it to disable only while i was typing.  Would make like much easier.

Such is life i guess.  Thanks heaps for your app, ive not tried it yet, but ill give it a whirl at some point..

I installed and ran touchfreeze from the Canonical repositories and that seemed to work fine for my MSI Wind U123 after everything else I tried failed.  It defaults to 0.5 second delay - I increased to 2 seconds (which is the max setting) and added an entry for it in my startup programs.

---

### Post by QuanTime on 2010-02-08
unfortunately, touchfreeze wont work for me :(

I still get an error when i try to load up the touchpad GUI, about "SHMconfig must be 'true' in your xorg.conf", and i cant get gynaptics to load.. Whats your xorg.conf look like ? might have a clue for me.

---

### Post by abandonedthe_mulletator on 2010-02-13
Touchfreeze does not work for me either.  The GUI does not load When I run it from the command line I get this,
```
SynDaemon::SynDaemon 

set daemon true 
set pad true 
using typing delay of 500 ms 
"/usr/bin/synclient" 
initial state is TouchpadOff= 0 
Segmentation fault

```

---

### Post by udutronik on 2010-02-14
To all that have an elantech touchpad... 

This is a bug that has been reported here : [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/512192](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/512192)

Add your input and maybe next update will bring usability for our touchpads...

---

### Post by QuanTime on 2010-02-14
cheers heaps for the news.  If you need any information on my device (asus K7 series) ill help where i can.

---

### Post by pi/roman on 2010-02-17
I don't have one of these so I'm unable to test on it myself, but I am curious what would happen if you tried to load the synaptics driver through hal  by creating a policy file
```
gksudo gedit /etc/hal/fdi/policy/11-x11-synaptics.fdi
```And placing the following into it
> <?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="ImPS/2 Logitech Wheel Mouse">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
<merge key="input.x11_driver" type="string">synaptics</merge>
    </match>
  </device>
</deviceinfo>Then you would have to remove references to the input device from xorg.conf if they exist.

---

### Post by QuanTime on 2010-02-17
i only have
```

~$ sudo gedit /etc/hal/fdi/policy/
preferences.fdi  shmconfig.fdi    shmconfig.fdi~   

```

My preferences.fdi is prolly the correct one.. it contains
```

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="evdev">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
    </match>
  </device>
</deviceinfo>

```

And just for interest sake, my xorg.conf contains
```

Section "InputDevice"
    Identifier     "Configured Mouse"
    #Driver         "mouse"
    #Option         "CorePointer"
    #Option         "Device" "/dev/input/mice"
    #Option         "Protocol" "ExplorerPS/2"
    #Option         "ZAxisMapping" "4 5"
    #Option         "Emulate3Buttons" "false"

    Driver      "synaptics"
   Option    "SHMConfig" "true"
   Option       "CorePointer"
   Option       "Device"        "/dev/evdev"
   #Option       "Device"        "/dev/psaux"   
   Option       "Protocol"      "auto-dev"
   Option       "LeftEdge"      "1700"
   Option       "RightEdge"     "5300"
   Option       "TopEdge"       "1700"
   Option       "BottomEdge"    "4200"
   Option       "FingerLow"     "25"
   Option       "FingerHigh"    "30"
   Option       "MaxTapTime"    "180"
   Option       "MaxTapMove"    "220"
   Option       "VertScrollDelta" "100"
   Option       "MinSpeed"      "0.06"
   Option       "MaxSpeed"      "0.12"
   Option       "AccelFactor" "0.0010"
   Option       "SHMConfig"     "on"
EndSection

```

So what direction do you think i should head in ?  Just wanna make sure that the right file gets edited in the correct way... ideas ?  And cheers heaps for the assistance, its VERY appreciated.

---

### Post by pi/roman on 2010-02-18
You could search lshal and make sure "ImPS/2 Logitech Wheel Mouse" is the device that is being recognized as the touchpad:
```
lshal -s | grep AUX | xargs -n1 lshal -u
```or if that doesn't show it try:
```
lshal -s | grep i8042 | xargs -n1 lshal -u
```so you know you can use "ImPS/2 Logitech Wheel Mouse" in your hal configuration.

Then do a:
```
gksudo gedit /etc/hal/fdi/policy/11-x11-synaptics.fdi
```and make a new fdi using the info.product that you found in the lshal command as the match key and turn on shmconfig  and apply the synaptics driver:
> <?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="ImPS/2 Logitech Wheel Mouse">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
<merge key="input.x11_driver" type="string">synaptics</merge>
<append key="info.capabilities" type="strlist">input.touchpad</append>
    </match>
  </device>
</deviceinfo>                      I included an append in this to ensure it has touchpad capability but if you see this in your lshal output then it would not be necessary to include it.
You could look for it in your lshal by:
```
lshal | grep touchpad
```and if this returns a device with input.touchpad then that would be the one to use.

About your xorg.conf input device section, I tested it out on my computer removing all the setting options and it was still causing my settings to be changed so it would probably either need to be commented out or deleted. Also if you have a reference to this device in your server layout section that should be commented out and if you have a synaptics driver loaded in the modules section that should probably be commented out also.  Since it is on file here already it should not be to difficult to put it back the way it was.

---

### Post by QuanTime on 2010-02-18
ok, lshal shows up a bunch of stuff, so im guessing thats what i need. I can post the results result of AUX
```

~$ lshal -s | grep AUX | xargs -n1 lshal -u
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'
  info.linux.driver = 'psmouse'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX3 port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio4'  (string)
  serio.description = 'i8042 AUX3 port'  (string)
  serio.id = 'serio4'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  info.product = 'ImPS/2 Logitech Wheel Mouse'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'  (string)
  input.device = '/dev/input/event9'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  input.product = 'ImPS/2 Logitech Wheel Mouse'  (string)
  input.x11_driver = 'evdev'  (string)
  input.x11_options.SHMConfig = 'on'  (string)
  linux.device_file = '/dev/input/event9'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio4/input/input9/event9'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX2_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX2 port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX2_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio3'  (string)
  serio.description = 'i8042 AUX2 port'  (string)
  serio.id = 'serio3'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX1 port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX1_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio2'  (string)
  serio.description = 'i8042 AUX1 port'  (string)
  serio.id = 'serio2'  (string)

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX0_port'
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042'  (string)
  info.product = 'i8042 AUX0 port'  (string)
  info.subsystem = 'serio'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX0_port'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'serio'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1'  (string)
  serio.description = 'i8042 AUX0 port'  (string)
  serio.id = 'serio1'  (string)

```

you can see that the i8042 output would be identical.

```

~$ lshal | grep touchpad
udi = '/org/freedesktop/Hal/devices/leds_asus_touchpad'
  info.udi = '/org/freedesktop/Hal/devices/leds_asus_touchpad'  (string)
  leds.function = 'touchpad'  (string)
  linux.sysfs_path = '/sys/devices/platform/asus_laptop/leds/asus::touchpad'  (string)

```Made the synaptics.fdi file, with the code you pasted, and my touchpad dies.  Looses all input.  My USB mouse still works a charm..  
I tried commenting out a few things in my xorg.conf file to no avail.  So ive commented out every line in the synaptics.fdi until i can get a grasp on whats going on.

Any more direction would result in free cookies for you.

---

### Post by pi/roman on 2010-02-18
This is very interesting:
> ~$ lshal | grep touchpad
udi = '/org/freedesktop/Hal/devices/leds_asus_touchpad'
  info.udi = '/org/freedesktop/Hal/devices/leds_asus_touchpad'  (string)
  leds.function = 'touchpad'  (string)
  linux.sysfs_path = '/sys/devices/platform/asus_laptop/leds/asus::touchpad'  (string)It would probably be a good idea to look at the rest of this:
```
lshal -u '/org/freedesktop/Hal/devices/leds_asus_touchpad'
lshal -u '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
```and the second one is the ImPS/2 but maybe that isn't the one that should be used for the touchpad because the leds_asus_touchpad looks like a better candidate.

---

### Post by QuanTime on 2010-02-18
```

~$ lshal -u '/org/freedesktop/Hal/devices/leds_asus_touchpad'
udi = '/org/freedesktop/Hal/devices/leds_asus_touchpad'
  info.addons.singleton = {'hald-addon-leds'} (string list)
  info.capabilities = {'leds'} (string list)
  info.category = 'leds'  (string)
  info.interfaces = {'org.freedesktop.Hal.Device.Leds'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/platform_asus_laptop'  (string)
  info.subsystem = 'leds'  (string)
  info.udi = '/org/freedesktop/Hal/devices/leds_asus_touchpad'  (string)
  leds.device_name = 'asus'  (string)
  leds.function = 'touchpad'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'leds'  (string)
  linux.sysfs_path = '/sys/devices/platform/asus_laptop/leds/asus::touchpad'  (string)

```

and

```

~$ lshal -u '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  info.product = 'ImPS/2 Logitech Wheel Mouse'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'  (string)
  input.device = '/dev/input/event9'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  input.product = 'ImPS/2 Logitech Wheel Mouse'  (string)
  input.x11_driver = 'evdev'  (string)
  input.x11_options.SHMConfig = 'on'  (string)
  linux.device_file = '/dev/input/event9'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio4/input/input9/event9'  (string)

```

Hows that ?

---

### Post by pi/roman on 2010-02-18
Good thanx, but I'm still not sure what the leds_asus_touchpad device is exactly. Maybe it's not the main device but some sort of ghost helper device.
It may be better to keep trying to configure the ImPS/2.  If you do try that again you could check "synclient -l" and ```
xinput list-props 'ImPS/2 Logitech Wheel Mouse'
```and make sure the touchpadoff=0 and the xinput deviceenabled=1
```
synclient touchpadoff=0
xinput set-int-prop 'ImPS/2 Logitech Wheel Mouse' 'Device Enabled' 8 1
```and if those don't work then try modprobe using the verbose option so you can see what's happening:
```
sudo modprobe -v psmouse
```and if you could lshal the device while it was loaded by hal you could see if hal was doing its job.

---

### Post by QuanTime on 2010-02-18
```

~$ xinput list-props 'ImPS/2 Logitech Wheel Mouse'
Device 'ImPS/2 Logitech Wheel Mouse':
    Device Enabled (93):    1
    Evdev Reopen Attempts (229):    10
    Evdev Axis Inversion (230):    0, 0
    Evdev Axis Calibration (231):    
    Evdev Axes Swap (232):    0
    Evdev Middle Button Emulation (233):    1
    Evdev Middle Button Timeout (234):    255
    Evdev Wheel Emulation (235):    1
    Evdev Wheel Emulation Axes (236):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (237):    10
    Evdev Wheel Emulation Timeout (238):    200
    Evdev Wheel Emulation Button (239):    4
    Evdev Drag Lock Buttons (240):    0

```

ive NEVER had synclient working or installed properly..

```

~$ synclient touchpadoff=0
Couldn't find synaptics properties. No synaptics driver loaded?

```

modprobe -v psmouse doesnt list anything..

---

### Post by pi/roman on 2010-02-18
> modprobe -v psmouse doesnt list anything..Thats good it means it's already loaded.
Can you run:
```
lshal -u '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
```while the touchpad is loaded through hal fdi?  You could try unloading psmouse then loading it again.
```
modprobe -rv psmouse
modprobe -v psmouse
```

---

### Post by QuanTime on 2010-02-18
```

~$ lshal -u '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  info.product = 'ImPS/2 Logitech Wheel Mouse'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'  (string)
  input.device = '/dev/input/event9'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port'  (string)
  input.product = 'ImPS/2 Logitech Wheel Mouse'  (string)
  input.x11_driver = 'evdev'  (string)
  input.x11_options.SHMConfig = 'on'  (string)
  linux.device_file = '/dev/input/event9'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio4/input/input9/event9'  (string)

```

How can i ensure its loaded via hal ?

and to make this easier on you, i can pass you my ICQ or MSN.. or im on #ubuntu @ irc.freenode.org (user name Quan-Time) if you wanna jump on irc..  But im more than happy with this forum thread, might help others later in the future with the same problem.

---

### Post by pi/roman on 2010-02-18
If the hal configuration was working correctly the following lines of the output would be changed as such:
```
info.capabilities = {'input', 'input.mouse', [COLOR=Red]'input.touchpad'[/COLOR]} (string list)
input.x11_driver = [COLOR=Red]synaptics[/COLOR]
```So there is probably something interfering with the hal policy being able to make the changes.
I would go on ICQ but I'm not set up for it right now and I have to go to bed soon anyway.
> How can i ensure its loaded via hal ?The best way would probably be to save the whole xorg.conf as a backup:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```then delete all the references to synaptics or ImPS/2 and then reboot to load the hal policy and then check lshal and if the changes are still not there then maybe it's not possible. Then the xorg.backup could be renamed again to xorg.conf.

---

### Post by QuanTime on 2010-02-19
ah ok.. so what options do i have ? and i guess ill hear from you tomorrow (i hope). Not quite sure where to go from here.  This is all new to me. (touchpad config)

---

### Post by pi/roman on 2010-02-19
I would try this and make sure to have this fdi policy uncommented
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="ImPS/2 Logitech Wheel Mouse">
      <merge key="input.x11_options.SHMConfig" type="string">on</merge>
<merge key="input.x11_driver" type="string">synaptics</merge>
    </match>
  </device>
</deviceinfo>                      
``` and save the whole xorg.conf as a backup:
     ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup 
```then delete all the references to synaptics or ImPS/2 in xorg.conf and then reboot to load the hal policy and then check lshal 
```
lshal -u '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX3_port_logicaldev_input'
```and if the changes input.touchpad capability and synatpics drvier are still not there then maybe it's not possible. Then the xorg.backup could be renamed again to xorg.conf.

---

### Post by QuanTime on 2010-02-19
kk ill try that and post results tomorrow.. i gotta step out shortly.  Cheers again !

---

### Post by pi/roman on 2010-02-22
I just came across this link:
[[COLOR=Blue]http://wiki.debian.org/DebianEeePC/HowTo/ElantechTouchpad[/COLOR]]("http://wiki.debian.org/DebianEeePC/HowTo/ElantechTouchpad")
It looks like It's necessary to patch the kernel to make it work.  That sounds like an adventure.  Other than that it looks like the only thing that will work is changing a few xinput settings.
The middle button could be disabled by:
```
xinput set-int-prop 'ImPS/2 Logitech Wheel Mouse' 'Evdev Middle Button Emulation' 8 0
```

---

### Post by orengolan on 2010-04-11
I just upgraded to 10.4 and it was not fixed.
here are the 2 bug reports, please go there and add a comment with your machine etc.

[https://bugs.launchpad.net/ubuntu/ha...ev/+bug/123775](https://bugs.launchpad.net/ubuntu/ha...ev/+bug/123775)

[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/512192](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/512192)

I also post it on kernel-team mailing list:
[https://lists.ubuntu.com/archives/ke...il/009826.html](https://lists.ubuntu.com/archives/ke...il/009826.html)

go there and reply, tell the developers it's a real issue.

Also go to #ubuntu-kernel on irc and ask about it.

---

### Post by QuanTime on 2010-04-11
tried pi/roman's suggestion, couldnt get it to work the way i wanted..  Forgot to post.. Sorry about that.

@orengolan
All those links dont work for me..  And im not surprised 10.04 doesnt have any fixes for this issue.  Theres lots of other "important" stuff which goes on.  Wish they fully supported some of the common hardware tho, would be nice.

Guess ill keep waiting and complaining.

---

### Post by ALLurGroceries on 2010-04-25
See comment 24 for a patchset: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192")

I also submitted a quick and dirty patch for this in comment 25, but it's not as nice as the patchset in comment 24.

This should fix the issue. Good luck.

P.S. I also posted about this here: [http://forum.notebookreview.com/showthread.php?t=478755]("http://forum.notebookreview.com/showthread.php?t=478755")

Edit:

> **pi/roman said:**
> I'm still not sure what the leds_asus_touchpad device is exactly.

It's for the ASUS G50 and others(?) that have electroluminescent lighting around the touchpad. It gets false positives on a lot of machines that don't have this feature like my G51J. Note that this is NOT the same as the touchpad lights on some U series notebooks. It's for a single light that is on the border of the touchpad, not lights that are actually on the touchpad itself.

---

### Post by QuanTime on 2010-04-25
id love to install it and give it a go, if only i knew how.

Point me in the direction of a guide / tutorial ?  Not much experience on this sort of patching.  Cheers for the work tho !! hugely appreciated !

---

### Post by ALLurGroceries on 2010-04-26
[COLOR="Red"]**UPDATE:[/COLOR] This patch set (3/4 of it at least) has been included in 2.6.34-rc7**
To find out your kernel version, run: **uname -r**
If you are running 2.6.34-rc7 or later, create **/etc/modprobe.d/psmouse.conf** and add the line: **options psmouse force_elantech=1**
DO NOT do the above if you are running an older kernel than 2.6.34! Proceed directly below to Step 1.

**_Step 1_**
**[COLOR="Red"]IMPORTANT:[/COLOR] BACK UP THE EXISTING MODULE FIRST!** You can revert to the .backup copy if things go wrong.
```
sudo cp /lib/modules/`uname -r`/kernel/drivers/input/mouse/psmouse.ko /lib/modules/`uname -r`/kernel/drivers/input/mouse/psmouse.ko.backup
```
DO NOT run the above command twice. You may lose your good backup copy of the module; to restore the backup see 'IF SOMETHING GOES WRONG' at the bottom of this post.

Note: I modified this post to work for stock kernels. If you're running a custom kernel that you built from source, you don't need to go through all of this. Instead, cd to your source directory, make sure the elantech option is on in your .config (step 4), apply the patches (step 5) and **make drivers/input/mouse/psmouse.ko** then insmod it (step 7) to see if it works. You can continue to step 8 if you want to make the change permanent.

**_Step 2_**
Get the kernel source and headers for your installed kernel along with some prerequisites:
```
sudo apt-get install linux-source linux-headers-`uname -r` build-essential libncurses5 libncurses5-dev kernel-package fakeroot
```

(Note: You don't need kernel-package or fakeroot for this, but if you want to build your entire kernel after this for a separate reason, you will have everything you need.)

If you get a warning saying linux-source is a virtual package, install the specific source package for your installed kernel, such as linux-source-2.6.31, linux-source-2.6.32, linux-source-2.6.33, etc. To find out what kernel version you are running, run **uname -r**.

**_Step 3_**
Now extract the kernel sources to a folder named src in your home directory, where VERSION is the version of your kernel sources. If you aren't sure, just do a **ls /usr/src/linux-source*.bz2** to find it:
```
mkdir ~/src
cd ~/src
tar jxvf /usr/src/linux-source-VERSION.tar.bz2
cd linux-source-VERSION
```

Then copy your config file in and make oldconfig:
```
cp /boot/config-`uname -r` .config
make oldconfig
```

**_Step 4_**
Make sure that the elantech option is on:
```
grep -i elantech .config
```

It should return this if it is set:
**CONFIG_MOUSE_PS2_ELANTECH=y**

If it is not set it will return:
**# CONFIG_MOUSE_PS2_ELANTECH is not set**

If the elantech option is not set, run **make menuconfig** and navigate to **Device Drivers->Input device support->Mice** and press space on the **Elantech PS/2 protocol extension** so that it has an asterisk like this: [*]. Then press the right arrow and enter repeatedly to back out of the menus, and then answer YES to save your config.

**_Step 5_**
Get and apply the patches:
```

wget -O elantechpatch1 https://patchwork.kernel.org/patch/94862/raw/
wget -O elantechpatch2 https://patchwork.kernel.org/patch/94863/raw/
wget -O elantechpatch3 https://patchwork.kernel.org/patch/94861/raw/
wget -O elantechpatch4 https://patchwork.kernel.org/patch/94864/raw/
patch -p1 < elantechpatch1
patch -p1 < elantechpatch2
patch -p1 < elantechpatch3
patch -p1 < elantechpatch4

```

_**Step 5.5 - DELL MINI ONLY**_
For the Dell Mini (not sure about others), you will need to force version 2 by editing **drivers/input/mouse/elantech.c** after applying the original 4 patches, go to line 675 and remove these two lines:
```
if ((etd->fw_version_maj == 0x02 && etd->fw_version_min >= 0x30) ||
                                           etd->fw_version_maj > 0x02) {
```
...and replace them with with this line:
```
if (1) {
```

Reference: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192/comments/43]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192/comments/43")

**_Step 6_**
Next, build the module:
```
make -C /usr/src/linux-headers-`uname -r` SUBDIRS=`pwd` drivers/input/mouse/psmouse.ko
```

**_Step 7_**
Try the new module to see if it works:
```
sudo modprobe -r psmouse
sudo insmod drivers/input/mouse/psmouse.ko

```

If it doesn't work, DO NOT continue to step 8. You can reload the psmouse module and your touchpad will function again:
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

There are no permanent changes to your system until step 8 below.

**_Step 8_**
Note: This step will make a persistent change to your system.

If the patched module worked, you can move it into its place in /lib/modules/ if you want to keep using it:
```
sudo cp drivers/input/mouse/psmouse.ko /lib/modules/`uname -r`/kernel/drivers/input/mouse/psmouse.ko
```

It'd be a good idea to try this copy of the module to make sure it works:
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

**_IF SOMETHING GOES WRONG_**
If for some reason your touchpad will not work after following these directions, move the backup back into place and you should be fine:
```
sudo cp /lib/modules/`uname -r`/kernel/drivers/input/mouse/psmouse.ko.backup /lib/modules/`uname -r`/kernel/drivers/input/mouse/psmouse.ko
sudo modprobe -r psmouse
sudo modprobe psmouse
```

**_IF IT WORKED_**
For ASUS machines, [see page 8]("http://ubuntuforums.org/showthread.php?t=1333961&page=8") for details on switching the tap buttons and a tweak to get Fn+F9 to work to toggle the touchpad on/off.

For the Dell Mini 10, or machines which have integrated buttons (if you press down on the touchpad surface to click), you may want to set **AreaBottomEdge** to 600 via xorg.conf, a udev rule, or synclient (see below). This will prevent the problem [described here]("http://ubuntuforums.org/showthread.php?p=9451995#post9451995") by disabling a lower border of the touchpad area. The value can be adjusted up or down to find the optimal setting. If this breaks things just set it back to 0.
```
synclient AreaBottomEdge=600
```

Similarly, **AreaLeftEdge** or **AreaRightEdge** (depending on orientation) can be set to disable the left or right hand border, if desired. A suggested starting value is 50:
```
synclient AreaLeftEdge=50
```

**_References_**

Bug reports:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192")
[https://bugs.launchpad.net/ubuntu/+bug/418282]("https://bugs.launchpad.net/ubuntu/+bug/418282")

Original patches (only apply to 2.6.34-rc6 or earlier):
[https://patchwork.kernel.org/patch/94862/]("https://patchwork.kernel.org/patch/94862/")
[https://patchwork.kernel.org/patch/94863/]("https://patchwork.kernel.org/patch/94863/")
[https://patchwork.kernel.org/patch/94861/]("https://patchwork.kernel.org/patch/94861/")
[https://patchwork.kernel.org/patch/94864/]("https://patchwork.kernel.org/patch/94864/")

Linus' 2.6.34-rc7 LKML post with the accepted patches:
[http://lkml.org/lkml/2010/5/9/179]("http://lkml.org/lkml/2010/5/9/179")

---

### Post by Bender2k14 on 2010-04-26
These instructions didn't work for me and now my touchpad doesn't work at all.

When executing the last instruction, I get:
```
tyson@tyson-netbook:~/src/linux-source-2.6.31$ sudo modprobe psmouse
FATAL: Error inserting psmouse (/lib/modules/2.6.31-20-generic/kernel/drivers/input/mouse/psmouse.ko): Invalid module format

```

Why didn't it work?

(It case this information is important, I have a custom wifi driver that I installed from [here]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") via the "Karmic (9.10) - New Method".)

---

### Post by ALLurGroceries on 2010-04-26
> **Bender2k14 said:**
> These instructions didn't work for me and now my touchpad doesn't work at all.

When executing the last instruction, I get:
```
tyson@tyson-netbook:~/src/linux-source-2.6.31$ sudo modprobe psmouse
FATAL: Error inserting psmouse (/lib/modules/2.6.31-20-generic/kernel/drivers/input/mouse/psmouse.ko): Invalid module format

```

Why didn't it work?

(It case this information is important, I have a custom wifi driver that I installed from [here]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") via the "Karmic (9.10) - New Method".)

Just use the last part I posted to restore the backup module to its place... then your touchpad will work like it did. Here again:

[COLOR="Red"]**_Undo information_**[/COLOR]
```
sudo cp /lib/modules/`uname -r`/kernel/drivers/input/mouse/psmouse.ko.backup /lib/modules/`uname -r`/kernel/drivers/input/mouse/psmouse.ko
sudo modprobe -r psmouse
sudo modprobe psmouse
```

Edit: I broke up step 4 into more steps so that you test the module before installing it, etc...

---

### Post by Bender2k14 on 2010-04-26
Crap...

When your commands didn't work for me the first time, I tried them again without thinking what I was executing...so I lost my backup :(

---

### Post by ALLurGroceries on 2010-04-26
> **Bender2k14 said:**
> Crap...

When your commands didn't work for me the first time, I tried them again without thinking what I was executing...so I lost my backup :(

Uhg. In that case I'm going to heavily modify my previous post to prevent that.

To get the original module back on your system you're going to have to do:
```
wget http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-20-generic_2.6.31-20.58_amd64.deb
dpkg --fsys-tarfile linux-image-2.6.31-20-generic_2.6.31-20.58_amd64.deb | tar -xf - ./lib/modules/2.6.31-20-generic/kernel/drivers/input/mouse/psmouse.ko
sudo install -m755 lib/modules/2.6.31-20-generic/kernel/drivers/input/mouse/psmouse.ko /lib/modules/2.6.31-20-generic/kernel/drivers/input/mouse/psmouse.ko
sudo modprobe -r psmouse
sudo modprobe psmouse

```

Edit: I'm assuming you're runing 64 bit, if not, download this deb instead: [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-20-generic_2.6.31-20.58_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-20-generic_2.6.31-20.58_i386.deb")

In a nutshell that's download the deb, extract the module from it, move it back, and reload the module.

---

### Post by Bender2k14 on 2010-04-26
I tried your newest commands (with i386 replacing amd64 since I have a 32 bit system) and I still get the same module format error when executing the last command.

---

### Post by ALLurGroceries on 2010-04-26
> **Bender2k14 said:**
> I tried your newest commands (with i386 replacing amd64 since I have a 32 bit system) and I still get the same module format error when executing the last command.

Are you sure you're replacing it in both places?

```
wget http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-20-generic_2.6.31-20.58_i386.deb
dpkg --fsys-tarfile linux-image-2.6.31-20-generic_2.6.31-20.58_i386.deb| tar -xf - ./lib/modules/2.6.31-20-generic/kernel/drivers/input/mouse/psmouse.ko
sudo install -m755 lib/modules/2.6.31-20-generic/kernel/drivers/input/mouse/psmouse.ko /lib/modules/2.6.31-20-generic/kernel/drivers/input/mouse/psmouse.ko
sudo modprobe -r psmouse
sudo modprobe psmouse

```

---

### Post by Bender2k14 on 2010-04-26
I replaced amd64 with i386 in two places, once in each of the first two commands.

---

### Post by ALLurGroceries on 2010-04-26
Not sure why that wouldn't work, unless 2.6.31-20 isn't the kernel you are running... it's a fresh copy of the module... from the directory you extracted from try: ```
sudo insmod lib/modules/2.6.31-20-generic/kernel/drivers/input/mouse/psmouse.ko
```

If that doesn't work you can reinstall your kernel package, but it will break any stuff you've done to it like wireless etc. That's a worst-case thing to do though.

---

### Post by Bender2k14 on 2010-04-26
Yes :)

That last command get my touchpad working again.

For the record, my touchpad is still being recognized as a wheel mouse.

Also, I would recommend structuring your tutorial similar to [this one]("http://ubuntuforums.org/showthread.php?t=221174"), where the backup instructions are at the beginning and given special attention.

Thanks for your help in getting my touchpad working again.  We will have to continue working together to see if we can get my touchpad recognized correctly.

---

### Post by ALLurGroceries on 2010-04-26
You should be able to do this then:
```
sudo cp lib/modules/2.6.31-20-generic/kernel/drivers/input/mouse/psmouse.ko /lib/modules/2.6.31-20-generic/kernel/drivers/input/mouse/psmouse.ko
sudo modprobe -r psmouse
sudo modprobe psmouse

```

That will fix it permanently, if you rebooted now it wouldn't work until you ran the insmod.

Edit: In terms of recognizing the touchpad, the patch set works fine for me.

---

### Post by Bender2k14 on 2010-04-26
Yea, I noticed that it didn't persist across a reboot.

I followed your instructions, and now it does persist across a reboot.

I am going to try and apply the patches again.

---

### Post by ALLurGroceries on 2010-04-27
Sorry, it was my fault. I tried it from a clean source tree and it did the same thing for me. I wrote the guide using the commands for my source tree that had already been built in since I always build my own kernel. If the source tree is clean, building the module won't produce any errors but trying to insmod it will result in an error in the system log: "no symbol version for module_layout". So we need the kernel headers and to change the command line for make. Generically:
```
make -C /path/to/linux-headers/ SUBDIRS=/path/to/linux-source/ path/to/module.ko
```

[I updated my post]("http://ubuntuforums.org/showthread.php?p=9175201#post9175201"), give it another try, and if I need to make any changes let me know. This time I took your advice and put the backup instructions at the top. :)

Cheers.

---

### Post by Bender2k14 on 2010-04-27
Great work...thanks for your continued help.

As I just said on the bug report, I think your instructions worked, but it does not seem like the patch worked for me.

I am very excited get this bug fixed because it greatly affect my ability to use my system.  Thank you very much for helping so much :)

---

### Post by ALLurGroceries on 2010-04-27
OK, glad it worked. Or my directions worked... sorry that the patches didn't.

First, look at /var/log/syslog, do a:
```
grep -i elantech /var/log/syslog
```

The important lines are like this:
```
elantech.c: Synaptics capabilities query result 0x79, 0x13, 0x0d.
elantech.c: Elantech version query result 0x04, 0x04, 0x11.
elantech.c: assuming hardware version 2, firmware version 4.17
```

Paste the output on the bug report, I'll see it there.

If it says assuming hardware version 1, that is the problem.

---

### Post by timuckun on 2010-04-28
> **ALLurGroceries said:**
> OK, glad it worked. Or my directions worked... sorry that the patches didn't.



What is the probability of these patches being applied to the official kernel?

---

### Post by Bender2k14 on 2010-04-28
According to this
[http://www.spinics.net/lists/linux-input/msg08298.html](http://www.spinics.net/lists/linux-input/msg08298.html)

...Good :)

---

### Post by ALLurGroceries on 2010-04-29
I [updated my post with the instructions]("http://ubuntuforums.org/showthread.php?p=9175201#post9175201") again to add the detail about forcing version 2 for the Dell Mini.

---

### Post by Bender2k14 on 2010-04-29
As I said in my reply to Florian about forcing Dell Mini 10 to hardware version 2, his patch needs to

Remove:
if ((etd->fw_version_maj == 0x02 && etd->fw_version_min >= 0x30) ||
            etd->fw_version_maj > 0x02) {

and Add:
if(1) {

I dont think that the code will compile after his patch.

---

### Post by ALLurGroceries on 2010-04-29
Oh. Heh. That patch must be in the wrong order.. I'll make a note of that extra line. Thanks for pointing that out :)

---

### Post by Bender2k14 on 2010-04-29
I figured out how to modify his patch to be correct:
```
diff --git a/drivers/input/mouse/elantech.c b/drivers/input/mouse/elantech.c
index a138b5d..07f6b17 100644
--- a/drivers/input/mouse/elantech.c
+++ b/drivers/input/mouse/elantech.c
@@ -666,7 +666,7 @@ int elantech_init(struct psmouse *psmouse)
 	 * Assume every version greater than this is new EeePC style
 	 * hardware with 6 byte packets
 	 */
-	if (etd->fw_version_maj >= 0x02 && etd->fw_version_min >= 0x30) {
+	if (1) {
 		etd->hw_version = 2;
 		/* For now show extra debug information */
 		etd->debug = 1;
```

I am sure he will figure it out, so I won't bother posting to the bug report.

If someone wants a downloadable copy of this patch, I am hosting one at the following url:
[http://dl.dropbox.com/u/123623/Ubuntu/elantechpatch_force_hwv2.patch](http://dl.dropbox.com/u/123623/Ubuntu/elantechpatch_force_hwv2.patch)

---

### Post by dinhtrung on 2010-05-01
Great! The original patch work for me. I'm on ASUS K40IN, with Elantech touchpad. :D

---

### Post by jsevi83 on 2010-05-02
It worked perfect for me, on Asus A52F. The only thing is that now, two fingers tap is right click, and three fingers tap is middle click. Before I had the opposite, which I think made more sense:

- One finger tap, mouse button 1 (left click)
- Two fingers tap, mouse button 2 (middle click)
- Three fingers tap, mouse button 3 (right click)

Was this change done on purpose, or it happens accidentally on my model?

---

### Post by ALLurGroceries on 2010-05-02
You can change that in your xorg.conf in your InputDevice section for the touchpad:
```
	Option		"TapButton2"	"3"
	Option		"TapButton3"	"2"
```

---

### Post by jsevi83 on 2010-05-02
I dont have a xorg.conf file. Is there another way to do that? Or any way to automatically create a new xorg.conf on ubuntu lucid 64bit?

---

### Post by ALLurGroceries on 2010-05-02
Sure, see:
[http://wiki.debian.org/DebianEeePC/HowTo/ElantechTouchpad#Configuration]("http://wiki.debian.org/DebianEeePC/HowTo/ElantechTouchpad#Configuration")

If that doesn't work as-is add this to the inputdevice section:
```
Option "AutoServerLayout" "true"
```

---

### Post by jsevi83 on 2010-05-02
ok, I don't need a xorg.conf. I just found out with "synclient -l" that TapButton2 was set to 3, and TapButton3 was set to 2. So I did:

synclient TapButton2=2
synclient TapButton3=3

That fixed it. Now I realized I could set PalmDetect to 1 (it was disabled), but after that and also setting PalmMinWidth and PalmMinZ very low, I can still move my touchpad easily with my palm, and even make clicks.

Is this an expected behaviour?

---

### Post by benbeel on 2010-05-05
the patch "worked" on my asus UL30A running ubunut 10.04. However, after applying the patch, tapping the touchpad with two fingers changed to button 3 (prior to patching, it was button 2). Do you know how to switch that back, or alternatively (and this could be another work-around), a useful script that would disable a mouse (ps/2 mouse prior to patching) while typing?

---

### Post by ALLurGroceries on 2010-05-06
Yes, see the last page for the reversed buttons. You can do it with your xorg.conf or synclient:
```
synclient TapButton2=2
synclient TapButton3=3
```

To disable the touchpad while typing, you can either do it from your mouse preferences, or with:
```
syndaemon -i 1 -d
```

---

### Post by ALLurGroceries on 2010-05-10
Sorry to double post.

To get the touchpad hotkey to work (Fn+F9), edit /etc/acpi/asus-touchpad.sh:
```
sudo gedit /etc/acpi/asus-touchpad.sh
```

On (or around) line 16 where it says Synaptics change it to this:
```
XINPUTNUM=`xinput list | grep 'ETPS/2 Elantech Touchpad' | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`
```

Edit: Also make sure to xinput is installed:
```
sudo apt-get install xinput
```

Here's the full script with [a tweak added from Felixoid]("http://ubuntuforums.org/showthread.php?p=9490605#post9490605") so that using syndaemon doesn't re-enable the touchpad if you have disabled it with Fn+F9. If you don't use syndaemon, just the change above is enough, and the script below will enable syndaemon if you disable and re-enable the touchpad. However, if you do use syndaemon, you can replace the entire script with this so that everything works smoothly:
```
#!/bin/sh
[ -f /usr/share/acpi-support/state-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs

if (! test -x /usr/bin/xinput)
then
logger "Error: Please install package xinput to enable toggling of touchpad devices."
exit 0
fi

# if this is the right behavior, then this should be moved out of acpi-support
# to hal (or whatever is replacing hal for such events)
getXconsole

XINPUTNUM=`xinput list | grep 'ETPS/2 Elantech Touchpad' | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`

[ -f /usr/share/acpi-support/state-funcs ] || exit 0

# get the current state of the touchpad
TPSTATUS=`xinput list-props $XINPUTNUM | awk '/Synaptics Off/ { print $NF }'`

# if getting the status failed, exit
test -z $TPSTATUS && exit 1

if [ $TPSTATUS = 0 ]; then
   sinp=`ps -A|grep syndaemon| awk '{print$1}'`
   xinput set-int-prop $XINPUTNUM "Synaptics Off" 8 1
   kill $sinp
   if [ -e /sys/class/leds/asus::touchpad/brightness ]; then
        echo 0 > /sys/class/leds/asus::touchpad/brightness
   fi
else
   xinput set-int-prop $XINPUTNUM "Synaptics Off" 8 0
   syndaemon -i 1 -d
   if [ -e /sys/class/leds/asus::touchpad/brightness ]; then
        echo 1 > /sys/class/leds/asus::touchpad/brightness
   fi
fi

```

---

### Post by Orcie on 2010-05-12
> **benbeel said:**
> the patch "worked" on my asus UL30A running ubunut 10.04. However, after applying the patch, tapping the touchpad with two fingers changed to button 3 (prior to patching, it was button 2). Do you know how to switch that back, or alternatively (and this could be another work-around), a useful script that would disable a mouse (ps/2 mouse prior to patching) while typing?

Patch also worked on my ul30a. However my twofingerscroll is not working any more. If I modify this with synclient it gets re-enabled but this method is not persistent after a reboot. I tried to modify this in xorg.conf but i got the feeling I am doing something wrong. This option I indicate is right but it does not affect the touchpad. Below I posted my xorg.conf. Any1 can tell me what is going wrong. Just to be clear I previously used an usb mouse in ubuntu maybe this is the cause of the interference with the touchpad settings in xorg.conf. Ubuntu lucid btw...


```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dbe"
    Load  "glx"
    Load  "dri2"
    Load  "extmod"
    Load  "dri"
    Load  "record"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
    Option        "PalmDetect" "1"
    Option        "VertTwoFingerScroll" "1"
    Option        "HorizTwoFingerScroll" "1"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 4 Series Chipset Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by ALLurGroceries on 2010-05-12
Your mouse section should have synaptics instead of mouse for the driver.

Don't you have Mouse (or touchpad) Preferences under System->Preferences? In Debian I have a Touchpad tab with an option for Two Finger Scrolling. That's by far the easiest way.

---

### Post by Orcie on 2010-05-12
> **ALLurGroceries said:**
> Your mouse section should have synaptics instead of mouse for the driver.

Don't you have Mouse (or touchpad) Preferences under System->Preferences? In Debian I have a Touchpad tab with an option for Two Finger Scrolling. That's by far the easiest way.

I have the menu but the scrolling does not work option does not work (on or off makes no difference). It work with synclient therefore I think I am not pointing my settings in xorg.conf to the right direction however I do not know how to verify this. Changing the driver to synaptics in xorg.conf does not work (tried a reboot aswell). Is the     Option        "Device" "/dev/input/mice" correct?

Next to that grep -i elantech /var/log/syslog gives:

May 12 09:39:50 maarten-laptop kernel: [    2.829415] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input7

---

### Post by ALLurGroceries on 2010-05-12
Mine is /dev/input/mouse0 but /dev/psaux should also work. Look at your **/var/log/Xorg.0.log** for error messages. For starters look for lines with EE:
```
grep EE /var/log/Xorg.0.log
```

As long as it works with synclient, the patches have worked, and that's all this thread is really about. Depending on your setup you will need to tweak one thing or another to get synaptics settings to persist. Good luck.

Edit: You could try commenting out your entire mouse's inputdevice section (add a # at the beginning of each line) since it should autodetect anyway . You don't need to reboot to test if the setting will persist - just hit Ctrl+Alt+F1, log in and run **sudo /etc/init.d/gdm restart**

---

### Post by Orcie on 2010-05-12
[ALLurGroceries]("http://ubuntuforums.org/member.php?u=694978") many thanks for the patches aswell as the explanation to enable disable touchpad fn button. Both work excellent!

---

### Post by QuanTime on 2010-05-12
Id also like to say this also works for me now too !  Its been quite a while, but you came thru with the gold on this.

A few things i will add and query, my "2 finger scrolling" doesnt work anymore.  2-finger-tap has the on-screen scroll icon and you move the mouse up and down to "autoscroll" but id really like to be able to move 2 fingers up and down for autoscroll..  Anyone know a setting for that ?

If i do:
```

synclient TapButton2=2
synclient TapButton3=3

```My tapping works, but no scrolling the way i want it, BUT if i go to system -> preferences -> Touchpad
Theres no option for it, and it INSTANTLY removes / undoes my TapButton fix.  Ideas for this ?
Is it something i need to put into my xorg.conf file to make the settings last ? 

Im sure im just needed to fix a setting somewhere for my 2 finger auto scroll, and some way to stop it changing settings.  Least i can now:

```

syndaemon -i 1 -d

```Again. Cheers heaps, and can you help this last part of my problem ?  
If i ever meet you, ill buy you a beer !

---

### Post by ALLurGroceries on 2010-05-12
I think you are talking about
```
synclient VertTwoFingerScroll=1
```
and maybe
```
synclient HorizTwoFingerScroll=1
```

The massively annoying part is no matter if you are using xorg.conf or udev rules, the mouse preferences in Gnome overrides it. So for example if you want tapping for three fingers but not one, you have to make a shell script. With my udev rules, I have to have tapping enabled under preferences and then I disable the first mouse button tap with a script that has synclient TapButton1=0 in it.

---

### Post by Orcie on 2010-05-12
> **QuanTime said:**
>  
If i ever meet you, ill buy you a beer !


1.Use post #73 of this topic to reenable the touchpad fn key.
2. About the two-finger scroll. I have been messing with this all morning. I managed to put this into xorg.conf  a few posts up I posted mine. Make sure you match the identifier label with the same string that you get from xinput list (ETPS/2 Elantech Touchpad). With synclient -l you can get a list with all available options.

---

### Post by QuanTime on 2010-05-12
Those are the exact thing i wanted fixed, now my touchpad is working 100% the way i want.

Will these synclient options persist, or do i have to re-do them every time ?  Reboot / etc..  Can i just have a script on startup to change them and somehow "lock" them ?  Just adding the appropriate switches in Input Devices in my xorg.conf, is that enough for em to stick ?

---

### Post by Orcie on 2010-05-12
> **QuanTime said:**
> Those are the exact thing i wanted fixed, now my touchpad is working 100% the way i want.

Will these synclient options persist, or do i have to re-do them every time ?  Reboot / etc..  Can i just have a script on startup to change them and somehow "lock" them ?  Just adding the appropriate switches in Input Devices in my xorg.conf, is that enough for em to stick ?

I have them in xorg.conf but that was a mess to get working.

---

### Post by eidex on 2010-05-17
Thank you very much ALLurGroceries for your step-by-step how-to and making the hotkeys on my UL30a work!

---

### Post by Cierreics on 2010-05-27
Thank you VERY much ALLurGroceries!! :guitar:
I've added your guide to [this post]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110"), it's a tips collection for Asus UL30A, but most of the tips are valid for every notebook with > 2GB ram.


> **QuanTime said:**
> Those are the exact thing i wanted fixed, now my touchpad is working 100% the way i want.

Will these synclient options persist, or do i have to re-do them every time ?  Reboot / etc..  Can i just have a script on startup to change them and somehow "lock" them ?  Just adding the appropriate switches in Input Devices in my xorg.conf, is that enough for em to stick ?

You can add synclient commands in a new entry in System -> Preferences -> Startup Applications, I use this:

```
synclient MinSpeed=1 MaxSpeed=1 AccelFactor=0 TapButton2=2 TapButton3=3
```

Look at "TOUCHPAD" section of the post I've linked on top.

---

### Post by ALLurGroceries on 2010-05-27
force_elantech works with the latest Ubuntu kernel then? The patches must've been backported? If that's true let me know and I'll update my post. I can't test it cause I run Debian with a custom kernel. Cheers.

---

### Post by Cierreics on 2010-05-27
> **ALLurGroceries said:**
> force_elantech works with the latest Ubuntu kernel then? The patches must've been backported? If that's true let me know and I'll update my post. I can't test it cause I run Debian with a custom kernel. Cheers.

No, I run Lucid with 2.6.34 kernel through a repository (look at [my post]("http://ubuntuforums.org/showpost.php?p=9328344&postcount=110")). I don't tink they've backported them...
Regards! ):P

---

### Post by Cierreics on 2010-05-28
If you have problems to make tap button fix permanent, look here:

[http://ubuntuforums.org/showpost.php?p=9373226&postcount=129]("http://ubuntuforums.org/showpost.php?p=9373226&postcount=129")

:wink:

---

### Post by abandonedthe_mulletator on 2010-06-07
Is it possible to do this fix on Ubuntu 9.10?  Can I just upgrade the kernel to 2.6.34?

---

### Post by ALLurGroceries on 2010-06-07
You can try it, there's no harm done to your system as long as you don't copy the module if it doesn't work. You can also upgrade the kernel to 2.6.34.

---

### Post by vesayth on 2010-06-12
I just want to say thank you very much for this post! This was a problem that started bugging me the second I got my dell mini 10 netbook and put lucid on it.

There is one major annoyance that I'm having though. I can't decide whether it's more annoying than the old problem. I can at least type without the touchpad being as sensitive as a baby's skin, but my new problem occurs when i'm using both hands on the touchpad.

If I am using my right hand to move the mouse, and then my left hand to click at the same time, the cursor jumps to the bottom left corner of the screen. This does not happen vice-versa (move with left and click with right). Is there any known solution for this? If I can't used to it I may have to go back to the old driver which will make me sad =[.

---

### Post by ALLurGroceries on 2010-06-12
I was not aware of this problem, so I have no solution. Are you using tap-to-click? If you have two fingers on the pad at the same time you might try toggling two finger scrolling to stop the cursor from moving. That's just a wild guess.

---

### Post by vesayth on 2010-06-12
I tried turning off tap to click, and also turned of tapbutton2 and tapbutton3. Neither of those fixed it. Playing with the JumpyCursorThreshold or turning off TapAndDragGesture doesn't seem to do anything either.

---

### Post by ALLurGroceries on 2010-06-14
What kind of machine are you on? Does it have integrated mouse buttons (like a macbook pro) where you push down on the touchpad surface? You might want to read **man synaptics** and tweak HorizResolution or VertResolution to compensate.

---

### Post by vesayth on 2010-06-14
it's a dell mini 10 and yes it has integrated buttons. however it doesn't happen on the click itself, it happens on the touch. if i were moving the mouse with one finger, and then touch anywhere left of that on the touchpad it happens.

---

### Post by vesayth on 2010-06-14
thanks, setting the areabottomedge seems to be a very acceptable workaround.

---

### Post by ALLurGroceries on 2010-06-14
Cool, if you post the value(s) that worked for you I'll update my post with the directions. :)

Edit: Oh wait, you just set AreaBottomEdge... nvm. Gotcha ;)

Edit 2: Updated the [post with the tweak]("http://ubuntuforums.org/showthread.php?p=9175201#post9175201") (at the bottom).

---

### Post by vesayth on 2010-06-15
I will say that from time to time it still does the jump but it is is much less often and certainly manageable. All in all I would still prefer a proper fix if one eventually comes around. I also tweaked the AreaLeftEdge a little bit too and that seemed to make it a little better.

---

### Post by sokekoke on 2010-06-15
> **Bender2k14 said:**
> According to this
[http://www.spinics.net/lists/linux-input/msg08298.html](http://www.spinics.net/lists/linux-input/msg08298.html)

...Good :)

Sorry i'm not very techy, just installed linux for the first time aswell.

So there is a good chance if i just wait patiently ubuntu will one day tell me to update stuff and touch pad will magically be detected?
hehe... :p

---

### Post by vesayth on 2010-06-15
Yes, pretty much. Also those fixes generally come pretty quickly. That post was talking about using the .34 kernel which is going to be used in the Ubuntu 10.10 so we may see it as soon as that (October).

---

### Post by cakoji on 2010-06-18
Thank you very much ALLurGroceries.
I succeeded applying the patch to my asus U30Jc on Ubuntu 10.04.
Touchpad is properly recognized as Elantech touchpad and I can turn off the tapping.

However, one problem remains.
The problem is that the cursor moves when I touch the pad.
For example, when I touch the right side of the pad, the cursor moves to the right side.
The situations of top, bottom, and left are also similar.
And I can not scroll with the touchpad.
I think scrolling may be correct when the solution for the cursor is found.

Are there the solution for this problem?

---

### Post by ALLurGroceries on 2010-06-18
I'm not sure what you mean. Are you saying that the cursor jumps if you put your finger on a different side of the touchpad from where it was last?

Make sure you are using two finger scrolling. Edge scrolling will not work on most of these elantech touchpads as far as I know.

---

### Post by cakoji on 2010-06-19
Thank you for your reply, ALLurGroceries.

Sorry for my poor English.
Maybe, I could not tell you what I want to say. 

It is right that the cursor jumps if I put my finger on the touchpad.
But I mean that coordinates on the touchpad where I put my finger seem to synchronize with the position of the cursor on the display.
If I put my finger on the right part on the touchpad, the cursor jumps to the right side on the display.

I think that the touchpad has the information of the absolute coordinates.
But I want the touchpad to have only relative positions. 
I hope the same operation regardless of the position where I put my  finger.

Unfortunately, I can not use both two finger scrolling and edge scrolling under the present situation.

---

### Post by ALLurGroceries on 2010-06-19
Hm, the elantech driver is designed to work in absolute mode, so I think your touchpad must have a different protocol or one of the registers acts differently. You can try fuzzing reg_10 with different values (from 00 to ff -- hexidecimal), it should be 0x54 by default. For example:

```
sudo sh -c "echo 0x54 > /sys/devices/platform/i8042/serio5/reg_10"
```

Your touchpad may be on a different port than serio5, you can find out by looking at the output of:
```
grep -i elantech /var/log/dmesg
```

If you post the output from the last command it may help. Especially the part about capabilities query result and the firmware version.

---

### Post by cakoji on 2010-06-21
I'm sorry for my late reply.

The result of the command is following:
```

$ grep -i elantech /var/log/dmesg
[   14.899976] elantech.c: assuming hardware version 2, firmware version 4.1
[   14.929576] elantech.c: Synaptics capabilities query result 0x7e, 0x13, 0x0d.
[   15.009599] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input8

```My touchpad uses serio4 instead of serio5.
The directoty (serio5) does not exist and I did not try to write the value into reg_10.

---

### Post by Felixoid on 2010-06-21
Sorry, if my english is not very well =)> **ALLurGroceries said:**
> ```
...
if [ $TPSTATUS = 0 ]; then
   xinput set-int-prop $XINPUTNUM "Synaptics Off" 8 1
   if [ -e /sys/class/leds/asus::touchpad/brightness ]; then
        echo 0 > /sys/class/leds/asus::touchpad/brightness
   fi
else
   xinput set-int-prop $XINPUTNUM "Synaptics Off" 8 0
   if [ -e /sys/class/leds/asus::touchpad/brightness ]; then
        echo 1 > /sys/class/leds/asus::touchpad/brightness
   fi
fi

```
**ALLurGroceries**, thank you very much for your work, it's work almost perfect =)
This part of script doesn't work, if ```
syndaemon -i 1 -d
``` launched. Touchpad goes off, but if I typing anything, it's on...
I replaced this part of script: ```
if [ $TPSTATUS = 0 ]; then
   sinp=`ps -A|grep syndaemon| awk '{print$1}'`
   xinput set-int-prop $XINPUTNUM "Synaptics Off" 8 1
   kill $sinp
   if [ -e /sys/class/leds/asus::touchpad/brightness ]; then
        echo 0 > /sys/class/leds/asus::touchpad/brightness
   fi
else
   xinput set-int-prop $XINPUTNUM "Synaptics Off" 8 0
   syndaemon -i 1 -d
   if [ -e /sys/class/leds/asus::touchpad/brightness ]; then
        echo 1 > /sys/class/leds/asus::touchpad/brightness
   fi
fi
``` and all worked perfectly ):P

---

### Post by ALLurGroceries on 2010-06-21
That's interesting, and it makes sense. I hadn't noticed because I don't actually use syndaemon... Thanks for that, I updated my post with your tweak.

---

### Post by Wanchu on 2010-06-24
First of all, thanks ALLurGroceries for your help :)

My laptop is an ASUS N61JQ and I am using Ubuntu 10.4. I have followed the steps in posts #44 and #73. I have found some problems:

- After disabling the touchpad with Fn+F9, it is automatically reenabled if I type and the option "Disable touchpad while typing" is checked in System > Preferences > Mouse > Touchpad. It kind of works the opposite way as what the option says. The problem disappears if you uncheck that option, so I think this should be added to your tutorial, ALLurGroceries.

- The touchpad is reenabled at startup even if I disabled it before rebooting with Fn+F9. Is there any way to make the change permanent? This also happens with the keys for screen brightness, so I would appreciate if someone told me how to make the changes to the brightness permanent too.

Thanks again for your help, it really makes a difference and makes it possible for me to enjoy Linux in the laptop :)  It was very annoying to accidentally touch the enabled touchpad before.

---

### Post by ALLurGroceries on 2010-06-24
Wanchu, this problem was addressed by Felixoid a couple of posts up. You can replace the entire script with the one listed in my post here: [http://ubuntuforums.org/showthread.php?p=9271851#post9271851]("http://ubuntuforums.org/showthread.php?p=9271851#post9271851") or you can just make the modifications in the post above, either way the end result is exactly the same.

There is no way to make the touchpad disabled on startup from keeping the last setting, at least without a custom script. This is not part of the acpid scripts' functionality.

If you always want it disabled at every startup, just add a startup item under System->Preferences->Startup Applications and click Add, then enter the command:
```
synclient TouchpadOff=1
```

You can still re-enable the touchpad with Fn+F9 normally.

---

### Post by Wanchu on 2010-06-24
Thanks for your quick and complete answer.

> **ALLurGroceries said:**
> Wanchu, this problem was addressed by Felixoid a couple of posts up. You can replace the entire script with the one listed in my post here: [http://ubuntuforums.org/showthread.php?p=9271851#post9271851](http://ubuntuforums.org/showthread.php?p=9271851#post9271851) or you can just make the modifications in the post above, either way the end result is exactly the same.


What I mean is that Felixoid's solution doesn't work if the "Disable touchpad while typing" option is checked in System > Preferences  > Mouse > Touchpad. That is why I suggested adding that note to the tutorial.

---

### Post by ALLurGroceries on 2010-06-24
I think there is a misunderstanding. If you disable the touchpad with Fn+F9, and you type something, the mouse starts working after you are done typing? That is not the way it works for me with Felixoid's modifications to the asus-touchpad.sh script. Are you sure you copied the script correctly? Please read through the posts carefully.

---

### Post by Wanchu on 2010-06-25
> **ALLurGroceries said:**
> If you disable the touchpad with Fn+F9, and you type something, the mouse starts working after you are done typing?

Yes, that is what happens, when the "Disable touchpad while typing" option is checked in System >  Preferences  > Mouse > Touchpad. I know it is working in the opposite way.

Anyway, everything works OK if I uncheck that option, so never mind. Thanks a lot for your help :)

---

### Post by ALLurGroceries on 2010-06-25
> **Wanchu said:**
> Yes, that is what happens, when the "Disable touchpad while typing" option is checked in System >  Preferences  > Mouse > Touchpad. I know it is working in the opposite way.

Anyway, everything works OK if I uncheck that option, so never mind. Thanks a lot for your help :)

Weird. That doesn't happen for me. Can someone else confirm this?

What happens if you run **syndaemon -i 1 -d** instead of using disable touchpad while typing in mouse preferences?

---

### Post by Worp8d on 2010-06-26
Thankyou!!!!!!!!!!

---

### Post by Wanchu on 2010-06-26
> **ALLurGroceries said:**
> What happens if you run **syndaemon -i 1 -d** instead of using disable touchpad while typing in mouse preferences?

It happens the same, the touchpad is automatically reenabled when I type.

---

### Post by ALLurGroceries on 2010-06-26
> **Wanchu said:**
> It happens the same, the touchpad is automatically reenabled when I type.

OK something is definitely different with your system. Until somebody else confirms this I'll assume it's a quirk for your system or setup. Thanks.

---

### Post by Snippa on 2010-07-09
Thank you for this. I'm running on an Asus K50ij.
Disabling the touchpad while typing works now.

I have 2 problems though. I cannot disable the touchpad using fn + f9, and I can no longer 2 finger tap to get the effect of a wheel click. I liked that 2 finger tap for wheel click, is there a way I can get that back while keeping the current settings?

2 finger scroll works fine, click works fine, disable while typing works fine, just cannot manually disable and instead of 2 finger tap for wheel click it's 2 finger tap for right click.

---

### Post by ALLurGroceries on 2010-07-09
> **Snippa said:**
> I cannot disable the touchpad using fn + f9

See [http://ubuntuforums.org/showthread.php?p=9271851#post9271851]("http://ubuntuforums.org/showthread.php?p=9271851#post9271851")

> **Snippa said:**
> and I can no longer 2 finger tap to get the effect of a wheel click.

```
synclient TapButton2=3
```

---

### Post by Snippa on 2010-07-09
> **ALLurGroceries said:**
> See [http://ubuntuforums.org/showthread.php?p=9271851#post9271851](http://ubuntuforums.org/showthread.php?p=9271851#post9271851)
Did this before posting in this thread, doesn't help with fn + f9.

> **ALLurGroceries said:**
> ```
synclient TapButton2=3
```
This had no effect, still right clicks instead of a wheel click.

---

### Post by ALLurGroceries on 2010-07-09
> **Snippa said:**
> Did this before posting in this thread, doesn't help with fn + f9.
Hm, that is curious, maybe you can try fiddling with the script if your system has some quirk.

**Edit:** maybe you have the same problem as above with the 'disable touchpad while typing' option. Try disabling that and see if Fn+F9 works.

> **Snippa said:**
> This had no effect, still right clicks instead of a wheel click.

Sorry, for 3rd button it's:
```
synclient TapButton2=2
```

---

### Post by Snippa on 2010-07-09
Alright, that worked for tapping w/ 2 fingers to act like the wheel click, but the fn + f9 still didn't work for me after unchecking that in mouse preferences.

---

### Post by ALLurGroceries on 2010-07-09
You should debug the script for your setup. Since you haven't provided any details of your problem, I can give you some generic advice. Start with this:

```
xinput list | grep 'ETPS/2 Elantech Touchpad' | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'
```

It should output the id=xx line from:
```
xinput list
```

After comparing that, you can move on to trying to disable it manually with the commands from the script. Replace xx with the number returned from the xinput list.

To disable:
```
xinput set-int-prop xx "Synaptics Off" 8 1
```

To enable:
```
xinput set-int-prop xx "Synaptics Off" 8 0
```

This should get you started. There is probably a small difference somewhere in the way your system is reporting things that must be changed in the script.

---

### Post by Snippa on 2010-07-10
Still no change. Did it exactly as you explained. I'm not too worried about that function working, but if you want to keep searching for why it isn't working like it should, I will help out however I can.

---

### Post by ALLurGroceries on 2010-07-10
Yeah I didn't mean that to be a fix, it was just a way of seeing if part of the script is working as it should. If you want to paste the output of the first two commands it'll show if it's working as expected. If you can't disable and enable it manually that's an entirely different story... you didn't say whether that worked or not.

---

### Post by lupus78 on 2010-07-16
I've create a small shell script to turn on/off the touchpad in my Asus K72F, based on the suggestion of the first pages of this thread.

My script is a toggle script, once you execute it, it switches the Device Enable state between 0 and 1.

```

#!/bin/bash

devicename="ImPS/2 Logitech Wheel Mouse"
propname="Device Enabled"
# get property sting
enableprop=$( xinput list-props "$devicename" | grep -i "$propname" )
# extract last charater, this is the value
enablestate=${enableprop: -1} 

# switch state
if [ $enablestate -eq 0 ]; then
	setstate=1
else
	setstate=0
fi

#set state
xinput set-int-prop "$devicename" "$propname" 8 $setstate

```

Don't forget to set it executable. 

I've attached this script to a hotkey in my Ubuntu, so now it's works as I want.

---

### Post by ALLurGroceries on 2010-07-16
It looks like you haven't patched your psmouse module, your script is for the incorrectly recognized logitech wheel mouse. There are patches available that should make your elantech touchpad recognized. I posted instructions here:
[http://ubuntuforums.org/showthread.php?p=9175201#post9175201]("http://ubuntuforums.org/showthread.php?p=9175201#post9175201")

Good luck! :)

---

### Post by lupus78 on 2010-07-17
Yes, I've seen that, but wanted to omit the patching. I've seen it already available in 2.6.34-rc7 kernel, so i was thinking that this workaround is enough for me, while your patch reaches a stable kernel and my ubuntu get's updated automatically. Am I right? Will it be available in the stable kernels later on?

---

### Post by ALLurGroceries on 2010-07-19
Yep if you install 2.6.34 (or later) all you need is to create **/etc/modprobe.d/psmouse.conf** and add the line: **options psmouse force_elantech=1**

That will fix it upon reboot. To avoid rebooting, after doing the above:
```
sudo modprobe -r psmouse
sudo modprobe psmouse force_elantech=1
```

I mentioned that in my post with the patching instructions, but I repeated it here anyway. :) Good luck!

---

### Post by oregonbob on 2010-08-08
Wow, I just read through this entire thread and near panicked. But instead of doing the patches I just did Lupus78's touchpadonoff.sh script and bound it to Alt-T and it works great for disabling the touchpad while I type. That is the only problem I have with my ASUS K50ij. I'll stick with that until the kernel is fixed in updates.

I have to thank those who spend hours making all this work, like Allurgroceries.

---

### Post by rajmkothari on 2010-08-10
ASUS X5DIJ

Just tried the fix posted by ALLurGroceries on my ASUS X5DIJ which was driving me mad. Sanity restored. Even "Mines" is possible ! Thanks.

---

### Post by Mazzhe on 2010-08-24
Thanks a lot ALLurGroceries !

You solve my problem.
I linked and translated your post #44 in french to help french users, [here]("http://forum.ubuntu-fr.org/viewtopic.php?pid=3683689")...

---

### Post by ALLurGroceries on 2010-08-24
Nice job, thanks for linking back. :)

---

### Post by ajithvisu on 2010-08-28
Thanks I had a Lenovo B460 and this thread helped me fix this and make my trackpad working

Cheers

---

### Post by crownedzero on 2010-09-05
OMG what a pain in the .... after upgrading I lost my wireless driver and had a heck of a time working through that but at long last working wireless and a mouse that doesn't have a mind of it's own! Great work!

---

### Post by houndi on 2010-09-05
Since this does its work on the X in memory it is not persistent. If you log out and back in the mousepad will be active again. This is desired behavior for me as I occasionally need to be able to use the laptop without my external mouse.

---

### Post by mikewhatever on 2010-09-13
> sudo apt-get install linux-source linux-headers-`uname -r` build-essential libncurses5 libncurses5-dev make-kpkg fakeroot

What's **make-kpkg**? I wasn't able to locate the package.

---

### Post by ALLurGroceries on 2010-09-13
> **mikewhatever said:**
> What's **make-kpkg**? I wasn't able to locate the package.

Brutal. That's a brainfart, sorry. It's **kernel-package** which has make-kpkg in it. I'm surprised nobody called me out on it! ;)

[http://packages.ubuntu.com/lucid/kernel-package]("http://packages.ubuntu.com/lucid/kernel-package")

I updated my post with the instructions here...

[http://ubuntuforums.org/showpost.php?p=9175201&postcount=44]("http://ubuntuforums.org/showpost.php?p=9175201&postcount=44")

---

### Post by mikewhatever on 2010-09-14
Thanks for the quick reply. I've applied the patch on Dell mini 10 running Karmic 2.6.31, and the touchpad now works as before, but when I run 'synclient AreaBottomEdge=600', the output is:
> synclient AreaBottomEdge=600
Couldn't find synaptics properties. No synaptics driver loaded?


same for 'syndaemon -i 1 -d'
> syndaemon -i 1 -d
Unable to find a synaptics device.


---

### Post by ALLurGroceries on 2010-09-14
You're on a dell mini, did you force the version by manually editing the patch as in [step 5.5]("http://ubuntuforums.org/showpost.php?p=9175201&postcount=44")?

In the output from
```
grep -i elantech /var/log/messages
```

You should see lines like 'elantech: assuming hardware version...' and 'synaptics capabilities query result'.

---

### Post by absolutezero1287 on 2010-09-14
I have the same touchpad on my Lenovo Ideapad Z560. What worked for me was the following:
```

sudo rmmod psmouse
sudo modprobe psmouse proto=imps

```

In order to make the change permanent you must add a file to /etc/modprobe.d/. The file must have .conf at the end. I named my file touchpad.conf. The file must have the following line: 
options psmouse proto=imps

Hope this helps.

---

### Post by ALLurGroceries on 2010-09-14
> **absolutezero1287 said:**
> I have the same touchpad on my Lenovo Ideapad Z560. What worked for me was the following:
```

sudo rmmod psmouse
sudo modprobe psmouse proto=imps

```

In order to make the change permanent you must add a file to /etc/modprobe.d/. The file must have .conf at the end. I named my file touchpad.conf. The file must have the following line: 
options psmouse proto=imps

Hope this helps.

The idea of this thread is to get away from ImPS/2 Logitech Wheel mouse because it's the wrong protocol for elantech... Are you sure it's an elantech touchpad in your thinkpad? I thought they used true Synaptics or Alps.

---

### Post by absolutezero1287 on 2010-09-14
> **ALLurGroceries said:**
> The idea of this thread is to get away from ImPS/2 Logitech Wheel mouse because it's the wrong protocol for elantech... Are you sure it's an elantech touchpad in your thinkpad? I thought they used true Synaptics or Alps.

I'm positive that my touchpad is elantech. I never said that my solution was a permanent one but it works. Either way, I don't really care because my touchpad works fine. I can scroll up and down, double click with the touchpad, and everything. It works the way a touchpad should. Why not test it? What's the worse that could happen from loading and unloading a module with different arguments?

Edit: 

```

root@satori:/etc/modprobe.d# grep -i elantech /var/log/messages 
Sep 12 06:45:26 satori kernel: [    7.065055] elantech.c: assuming hardware version 1, firmware version 20.0
Sep 12 06:45:26 satori kernel: [    7.144405] elantech.c: Synaptics capabilities query result 0x68, 0x18, 0x0c.
Sep 12 06:45:26 satori kernel: [    7.610458] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input8
Sep 12 08:01:10 satori kernel: [    9.420876] elantech.c: assuming hardware version 1, firmware version 20.0
Sep 12 08:01:10 satori kernel: [    9.480618] elantech.c: Synaptics capabilities query result 0x68, 0x18, 0x0c.
Sep 12 08:01:10 satori kernel: [    9.926175] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input8

```

---

### Post by ALLurGroceries on 2010-09-14
LOL I didn't mean to get you all flustered, I see you have an elantech touchpad, I didn't know lenovo was using them. Anyway, there are patches for this, so the issue has been resolved for some time, the thread really should be [SOLVED].

I'll post the link again, since it tends to get lost in all these replies: [http://ubuntuforums.org/showpost.php?p=9175201&postcount=44]("http://ubuntuforums.org/showpost.php?p=9175201&postcount=44")

---

### Post by mikewhatever on 2010-09-14
> **ALLurGroceries said:**
> You're on a dell mini, did you force the version by manually editing the patch as in [step 5.5]("http://ubuntuforums.org/showpost.php?p=9175201&postcount=44")?

In the output from
```
grep -i elantech /var/log/messages
```

You should see lines like 'elantech: assuming hardware version...' and 'synaptics capabilities query result'.

I did force the version as instructed, but there is no mention of 'elantec in messages'. In fact, 'grep -i elantech /var/log/*' returns nothing.

---

### Post by ALLurGroceries on 2010-09-14
> **mikewhatever said:**
> I did force the version as instructed, but there is no mention of 'elantec in messages'. In fact, 'grep -i elantech /var/log/*' returns nothing.

Hm, try tailing messages when you insmod.. in one window:
```
tail -f /var/log/messages
```

In another, cd to your linux source directory and:
```
sudo modprobe -r psmouse
sudo insmod drivers/input/mouse/psmouse.ko
```

If it gives an error, you'll have a clue, or if it says ImPS/2 there's a problem somewhere, double check your patched file (or start from scratch).

Bender2k14 posted a [patch here]("http://ubuntuforums.org/showpost.php?p=9198109&postcount=64") that you could use after the other patches. But it's the same thing as editing it manually.

If your mouse stops working:
```
sudo modprobe -r psmouse;sudo modprobe psmouse
```

---

### Post by mikewhatever on 2010-09-14
Did this:
sudo modprobe -r psmouse
sudo insmod drivers/input/mouse/psmouse.ko

and the only output in 'messages' is as follows:

> [36014.316381] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input10


I'll try the whole thing again.

---

### Post by mikewhatever on 2010-09-14
Redone, yet the result is as described earlier.

---

### Post by ALLurGroceries on 2010-09-14
> **mikewhatever said:**
> Redone, yet the result is as described earlier.

Ah, patchwork.kernel.org is down. That's probably why -- your patch files are probably empty, yeah?

I uploaded a copy of the patched file, from your kernel source directory:
```
wget -O drivers/input/mouse/elantech.c http://pastebin.com/download.php?i=i6uPx1vb
```

This replaces step 5. You'll still need to edit it to force version 2 as in step 5.5.

To be absolutely sure that step 6 works, you should first delete the old object files from the previous build:
```
rm drivers/input/mouse/*.o
```

---

### Post by mikewhatever on 2010-09-14
Hm..., no, the patch files are not empty. All four have stuff in them.

---

### Post by psifertex on 2010-09-20
Thanks so much! Worked great on my dell mini 10. Much appreciated.

---

### Post by elcalamar on 2010-09-29
Sorry if this has been posted elsewhere, but I could not find it: Every time I 'upgrade' my kernel I have to re-install the patch. Is there a way to avoid that? Sorry I am new to Linux so a step-by-step explanation will be much appreciated. Thank you!

---

### Post by ALLurGroceries on 2010-09-29
The patch is for the psmouse kernel module, and kernel modules are specific to kernel versions, so there is no way around that, unless you were on a kernel 2.6.34 or newer that has the patch rolled in.

---

### Post by Felixoid on 2010-11-10
Hello, [ALLurGroceries]("http://ubuntuforums.org/member.php?u=694978")
I don't' know, why, but after update on 10.10 script for switching touchpad by Fn+F9 doesn't work.
I didn't change anything, new kernel is 2.6.35-22-generic, amd64 version
Commands ```
xinput set-int-prop 13 "Synaptics Off" 8 0
and
xinput set-int-prop 13 "Synaptics Off" 8 1
``` is switch on and switch off TP...
What I do wrong? =)

---

### Post by ALLurGroceries on 2010-11-10
Hi Felixoid,

It looks like they've stripped out most of the script in the acpi-support package for 10.10. If you change line 10 of /etc/acpi/asus-touchpad.sh to this it works for me (on Debian Sid, no guarantees it'll work for you :)):

```

XINPUTNUM=`xinput list | grep 'ETPS/2 Elantech Touchpad' | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`
```

Basically just change **'SynPS/2 Synaptics TouchPad'** to **'ETPS/2 Elantech Touchpad'**.

---

### Post by Felixoid on 2010-11-11
I tried do this. My asus-toushpad.sh looked like this:```
#!/bin/sh
[ -f /usr/share/acpi-support/state-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs

if (! test -x /usr/bin/xinput)
then
logger "Error: Please install package xinput to enable toggling of touchpad devices."
exit 0
fi

# if this is the right behavior, then this should be moved out of acpi-support
# to hal (or whatever is replacing hal for such events)
getXconsole

XINPUTNUM=`xinput list | grep 'ETPS/2 Elantech Touchpad' | sed -n -e's/.*id=\([0-9]\+\).*/\1/p'`

[ -f /usr/share/acpi-support/state-funcs ] || exit 0

# get the current state of the touchpad
TPSTATUS=`xinput list-props $XINPUTNUM | awk '/Synaptics Off/ { print $NF }'`

# if getting the status failed, exit
test -z $TPSTATUS && exit 1

if [ $TPSTATUS = 0 ]; then
   sinp=`ps -A|grep syndaemon| awk '{print$1}'`
   xinput set-int-prop $XINPUTNUM "Synaptics Off" 8 1
   kill $sinp
   if [ -e /sys/class/leds/asus::touchpad/brightness ]; then
        echo 0 > /sys/class/leds/asus::touchpad/brightness
   fi
else
   xinput set-int-prop $XINPUTNUM "Synaptics Off" 8 0
   syndaemon -i 1 -d
   if [ -e /sys/class/leds/asus::touchpad/brightness ]; then
        echo 1 > /sys/class/leds/asus::touchpad/brightness
   fi
fi
``` and now i changed it to original with replace line 10.
Nothing chanched. By Fn+F9 is no reaction. :(

add
Thanks for help =)
on forum.ubuntu.ru found fix
in gconf-editor change /apps/gnome_settings_daemon/keybindings/touchpad on XF86Tools

---

### Post by eidex on 2010-11-11
Easy fix and working, thank you!

> **Felixoid said:**
> 
add
Thanks for help =)
on forum.ubuntu.ru found fix
in gconf-editor change /apps/gnome_settings_daemon/keybindings/touchpad on XF86Tools

---

### Post by GoogleyEyes on 2010-11-13
ALLurGroceries,

I just bought a Samsung QX410, and I have been unable to get the trackpad working. I was told that your patch had already been applied to the kernel, but I'm not sure if that is true or not. I tried applying it myself, but I kept getting a hunk error, or something like that.

Any info on the situation would be appreciated. I do not have a tab in Mouse Preferences for configuring my touchpad, and I would really like to enable scrolling.

Thanks.

---

### Post by ALLurGroceries on 2010-11-13
@ GoogleyEyes: I've seen the newer Samsungs mentioned in bug reports. On a kernel since 2.6.34 the patches will fail to apply. Assuming you've set force_elantech=1, try the steps I outlined in [this post]("http://ubuntuforums.org/showpost.php?p=9182727&postcount=58") and post the text from your syslog that should show up. My guess is that the version "magic" for these is again different, which was one of the problems that these patches fixed. Since there is no public documentation for these touchpads, each new revision seems to be broken until enough info is found by poking at it.

---

### Post by GoogleyEyes on 2010-11-14
ALLurGroceries,

Sorry, but I don't know what I'm doing wrong. I created  /etc/modprobe.d/psmouse.conf and added the line to it. I also ran the command sudo modprobe -v psmouse force_elantech=1, but when I ran grep -i elantech /var/log/syslog, nothing showed up. Elantech is not anywhere is the log file. Is there something that I missed? I've read through the thread, but it's pretty long and I may have missed something.

If you could walk me through what I'm doing wrong, I would really appreciate it. This is the only place I've found that anyone has any sort of idea of how to fix this problem.

Thanks again.

---

### Post by ALLurGroceries on 2010-11-14
Ur not doing anything wrong but the touchpad is not identifying itself as elan. Are you positive u have an elan touchpad? In the other os you would have an elan branded mouse control panel.

---

### Post by GoogleyEyes on 2010-11-14
Yes, I'm certain it's Elan. Any other ideas?

---

### Post by ALLurGroceries on 2010-11-14
Look in dmesg instead maybe
```
grep -i elantech /var/log/dmesg
```

---

### Post by GoogleyEyes on 2010-11-14
Nothing found there either...

---

### Post by ALLurGroceries on 2010-11-14
Gonna have to hack at the driver then, it must be a new protocol, or at least a new magic knock if the driver isn't giving you ANY output. There haven't been any elantech patches on linux-input for a while, so if there's someone working on it now, they're probably on their own. If you're interested in working on this send me a PM and I can try to help.

---

### Post by oregonbob on 2010-11-20
Ubuntu 10.04 kernel: 2.6.32-25-generic
I have an ASUS K50ij with the elantech touchpad and it is way too sensitive. I have a hot-key to disable/enable it while I am typing, but that is not that handy when a lousy typist like me needs to mouse to make corrections.

So, I am wondering if anyone has a clean, fairly easy-to-follow fix for this yet? I would just like it to be less sensitive. The fix may be buried in this thread but my aimless wondering cannot locate the best solution. Anyone got a link to a recommended solution?

---

### Post by ALLurGroceries on 2010-11-21
@oregonbob - Try the directions I've posted here: [http://ubuntuforums.org/showthread.php?p=9175201]("http://ubuntuforums.org/showthread.php?p=9175201")

---

### Post by Roadmaster on 2010-12-19
Hi All,

I'm on a Samsung QX-410 and having the same problem with the touchpad, which is recognized as "PS/2 Logitech Wheel Mouse". The pad "works" but is annoying, particularly because it's very easy to rub against the pad while typing, thus sending the mouse pointer flying all over the screen. Multitouch would be nice to have, but for now I'd settle for Ubuntu recognizing this as a touchpad and allowing users to set desirable touchpad behaviors.

I did a bit of poking with the elantech stuff on the psmouse kernel driver. This leads me to believe that the issue should be reported against kernel, since this is where the problem starts.

When queried, this pad reports a different set of numbers than other Elantech pads, this happens BEFORE the part where the force_elantech parameter comes in action, thus it is useless in this case.

I managed to get the driver to recognize the pad as an Elantech by changing the expected reply; indeed it reports back as "ETPS/2 Elantech Touchpad". However, the data the pad sends is apparently encoded differently, and there's basically no coordinate information. Only thing that works are the buttons, and even then, sporadically; the driver goes out of sync (reported in dmesg). So getting it to work will probably be a bit more involved.

There's already an Ubuntu bug reported for the QX410 [https://bugs.launchpad.net/bugs/681904](https://bugs.launchpad.net/bugs/681904). It's reported against xserver-xorg-video-intel, which I believe is not correct. I'll submit my findings and hopefully this will help get things sorted out.

---

### Post by ALLurGroceries on 2010-12-22
@Roadmaster, It may be stuck in relative mode, or the protocol may be different again, try fuzzing the register values to get it into absolute mode. If you go to the original bug for this thread [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/512192") check out comments 23, 24 and 25 for some possibly helpful clues. Feel free to PM me if you want, I was trying to get somewhere with the Samsung, but since I don't have a machine with this touchpad I can't really help much.

---

### Post by benbeel on 2010-12-22
> **oregonbob said:**
> Ubuntu 10.04 kernel: 2.6.32-25-generic
I have an ASUS K50ij with the elantech touchpad and it is way too sensitive. I have a hot-key to disable/enable it while I am typing, but that is not that handy when a lousy typist like me needs to mouse to make corrections.

So, I am wondering if anyone has a clean, fairly easy-to-follow fix for this yet? I would just like it to be less sensitive. The fix may be buried in this thread but my aimless wondering cannot locate the best solution. Anyone got a link to a recommended solution?

I use synclient to adjust my touchpad settings on my asus UL30A. You can enter into a terminal ```
synclient -l
```
This will provide a list of current settings for the touchpad. For instance, you may see TapButton2=3, which means a three-finger strike will trigger mouse button 2. You can change that to two-finger strike triggers button 2 by entering the following code:
```
synclient TapButton2=2
```
You can extrapolate this to any of the options present there. Check the man synclient for more info.
If your touchpad is truly being recognized as a touchpad, then you should have options in system>preferences>mouse>touchpad to disable clicks while typing. If not there, check gconf-editor apps/gnome/peripherals/touchpad as well.
Hope this helps.

---

### Post by Roadmaster on 2010-12-23
Thanks for the pointers on the QX410's touchpad. I have been poking around the reg_10 register but have been unable to get anything from the pad; the elantech.txt doc states that in v2 hardware, bit 1 of reg_1 controls drag & drop, but nothing changes if I touch this bit. if I do tap-hold-drag, the pad still reports button 1 is pressed during the drag.

    I modified the driver so that it reports to syslog the decoded absolute coordinates, number of fingers, and status of the buttons. What I see is packets being read from the pad, but coordinates get decoded as 0,0, and fingers is always 0. If I use two fingers, the pad doesn't even generate packets. Only the buttons work as expected, with a tap on the pad doubling as the left button.

    I'm also getting a lot of these loss-of-sync events, every time this happens the driver gets reinitialized:

```

    Dec 23 20:30:17 snowflake kernel: [ 6406.333118] psmouse.c: Touchpad at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
    Dec 23 20:30:18 snowflake kernel: [ 6406.839460] psmouse.c: resync failed, issuing reconnect request
    Dec 23 20:30:18 snowflake kernel: [ 6407.155017] elantech: retrying ps2 command 0xe6 (2).
    Dec 23 20:30:19 snowflake kernel: [ 6407.670745] elantech: retrying ps2 command 0xf8 (2).
    Dec 23 20:30:19 snowflake kernel: [ 6408.375595] elantech: retrying ps2 command 0xf8 (1).
```    Is there a way to see how the Windows driver initializes and configures the pad? that might help go in the right direction.

    I'll keep exploring and report back.

---

### Post by mikewhatever on 2011-01-04
As promised by ALLurGroceries, the Dell mini 10 touchpad is indeed recognized in Maveric. I had to add 
**synclient AreaBottomEdge=700  AreaLeftEdge=25 AreaRightEdge=1125 MinSpeed=0.3 AccelFactor=0.58** to startup commands to make the buttons usable. I've also tried adding the following to xorg.conf, but the settings are ignored. Anyone knows why?
```
Section "InputDevice"
        Identifier      "Elantech Touchpad"
        Driver          "synaptics"
        Option          "Device"                "/dev/input/mouse0"
        Option          "Protocol"              "auto-dev"
        Option          "AreaBottomEdge"        "700"
        Option          "AreaLeftEdge"          "25"
        Option          "AreaRightEdge"         "1125"
EndSection

```

I've not the slightest idea how to add it as a udev rule.:confused:

Syndaemon can now be used to disable touchpad when typing. The default timeout is 0.5 seconds, and there seems to be no straight forward way to change it, or at least I couldn't find it. You have to kill the daemon and then relaunch with your own timeout, 'syndaemon -i 1 -k' in my case.

---

### Post by ALLurGroceries on 2011-01-04
@mikewhatever try throwing the option lines in **/usr/lib/X11/xorg.conf.d/10-synaptics.conf**

---

### Post by mikewhatever on 2011-01-05
ALLurGroceries, thanks for input, but those settings are ignored too. I also had to create the highlighted part because it didn't exist.
/usr/lib/X11/**xorg.conf.d/10-synaptics.conf**

---

### Post by oregonbob on 2011-01-06
After reading the last few posts I took a hint and in-place upgraded my ASUS K50ij from 10.04 to latest 10.10. Wow I can't believe it. That alone fixed my touchpad problems without making any adjustments to settings!

Even though touchpad problems seem like a small issue, I didn't realize how critically important it was until I finally got it fixed! It is fabulous to not have cursor bouncing everywhere when typing.

Thanks Groceries, you can have mine.

---

### Post by ALLurGroceries on 2011-01-06
@mikewhatever sorry that was bad info, I don't use Ubuntu, I'm on Debian.. it looks like it may have been changed to **/usr/share/X11/xorg.conf.d** now since 10.10. Give that a shot, if it still doesn't work, I'll dig into the documentation for 10.10.

@oregonbob glad you're happy, but I can't take the credit for the final patches... I just made an initial patch and wrote a guide. :)

---

### Post by oregonbob on 2011-01-06
That was a nasty bug that took a long time to get resolved. I have become spoiled from previous versions when bugs were often fixed within days or a week at most. But finally 10.10 fixed it. It also fixed my upside video cam. I'm on a roll. In both of those bugs I tried almost all of the fixes without success, to the point I gave up.

---

### Post by mikewhatever on 2011-01-06
> **ALLurGroceries said:**
> @mikewhatever sorry that was bad info, I don't use Ubuntu, I'm on Debian.. it looks like it may have been changed to **/usr/share/X11/xorg.conf.d** now since 10.10. Give that a shot, if it still doesn't work, I'll dig into the documentation for 10.10.


You are quite right, that's probably the right place, but when I've added 10-synaptics.conf and rebooted, the keyboard didn't work so that I couldn't check if the settings were applied.:p Promptly used the recovery mode to delete it. This was the content:
```
Section "InputClass"
        Identifier      "Elantech Touchpad"
        Driver          "synaptics"
        Option          "Device"                "/dev/input/mouse0"
        Option          "Protocol"              "auto-dev"
        Option          "AreaBottomEdge"        "700"
        Option          "AreaLeftEdge"          "25"
        Option          "AreaRightEdge"         "1125"
EndSection
```

I've also noticed that the Min/Max Speed and AccelFactor I've set with GpointingDeviceSettings are being ignored as well.

---

### Post by ALLurGroceries on 2011-01-06
Oh yeah, you'd need only the option lines, specifically the last 3, nothing else, not even the section markers. That's crazy that the keyboard died, lol! Not sure why... Also, make sure your settings between gnome-mouse-properties and gpointing-device-settings agree, mouse-properties will take precedence.

---

### Post by mikewhatever on 2011-01-06
So, I created /usr/shar/X11/xorg.conf.d/10-synaptics.conf with the following content and rebooted ...
```

      Option          "AreaBottomEdge"        "700"
      Option          "AreaLeftEdge"          "25"
      Option          "AreaRightEdge"         "1125"

```

... and it gets stuck at the splash screen. The recovery mode saved the day again. ;)

---

### Post by cichy69 on 2011-03-25
Hello!

Are there any progress with this Elantech driver here? The above described methods do not work for me, my touchpad is always detected as PS/2 Logitech Mouse. 
 
I use a Samsung QX310 laptop with Elantech touchpad. Ubuntu 10.10, kerr 2.6.35-28-generic.

---

### Post by shmup on 2011-03-25
> **cichy69 said:**
> Hello!

Are there any progress with this Elantech driver here? The above described methods do not work for me, my touchpad is always detected as PS/2 Logitech Mouse. 
 
I use a Samsung QX310 laptop with Elantech touchpad. Ubuntu 10.10, kerr 2.6.35-28-generic.

Glad to see you tried it. I was just about to, on my Samsung RF510. I'm really hoping there is a solution for you and I.

Can't believe one hasn't been posted at:

[http://askubuntu.com/questions/29200/elantech-trackpad-being-identified-as-a-logitech-wheel-mouse/](http://askubuntu.com/questions/29200/elantech-trackpad-being-identified-as-a-logitech-wheel-mouse/)

---

### Post by cichy69 on 2011-03-25
I do some research on my own, correct me if i'm wrong:
1. there is a kernel module responsible for detecting a mouse/touchpad and loading a proper driver
2. there is a driver which is responsible for working of the elantech hardware in file `elantech.c`
3. this driver used some data called `magic knock` to find elantech touchpads. In fact i found this function in the source code: 

```

/*
 * Use magic knock to detect Elantech touchpad
 */
int elantech_detect(struct psmouse *psmouse, bool set_properties)
{
    ....
}

```

i'm not fluent in c code but there is an interesting comment from the author: 

```
  
  /*
   * Query touchpad's firmware version and see if it reports known
   * value to avoid mis-detection. Logitech mice are known to respond
   * to Elantech magic knock and there might be more.
   */

```

but real detection is carried out in this function (i think):

```
 
if (param[0] != 0x3c || param[1] != 0x03 || param[2] != 0xc8) 
{
                pr_debug("unexpected magic knock result 0x%02x, 0x%02x, 0x%02x.\n",
                         param[0], param[1], param[2]);
              return -1;
}

```

i tried the 'brute force' approach and just commented above `return -1;` and got touchpad detected correctly as `Elantech Touchpad`, but that `patch` didn't solve the original problem. despite the fact that the touchpad was detected correctly, still the functionality was impaired (inability to move the pointer). the only things that worked were: left and right mouse clicks. 


any1, any thoughts?

---

### Post by ALLurGroceries on 2011-03-28
There are a few bugs for the samsungs, I've tried brute forcing it also and that didn't work (but I don't have access to one of those machines now):
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904)

---

### Post by cichy69 on 2011-03-31
Errors are reported, and we can only waiting for a solution from Kernel team :| 

Is there a way to disable the touchpad while typing on the keyboard?  I found couple tutorials but all these methods assume that the synaptics driver is loaded ...

---

### Post by AureiAnimus on 2011-05-13
I'm having the same problem. The touchpad works, but it's terribly sensitive while typing and multitouch doesn't work. (My laptop is an Asus K53sv) 

aEditing /etc/modprobe.d/psmouse.conf didn't work.
Anything further i could try?

---

### Post by frigginacky on 2011-05-15
I too have the same issue on an Asus K53SV (Natty, kernel 2.6.38-8).  It's the one thing on this laptop I haven't been able to get working. :(

---

### Post by AureiAnimus on 2011-05-16
> **frigginacky said:**
> I too have the same issue on an Asus K53SV (Natty, kernel 2.6.38-8).  It's the one thing on this laptop I haven't been able to get working. :(

Then you might be interested to know, I managed to switch it on/off with a shortcut linked to a script. 
I followed this: [http://ubuntuforums.org/showthread.php?t=1629433](http://ubuntuforums.org/showthread.php?t=1629433) 
until "Making the magic happen automatically:" and then linked the script to a shortcut.

Make sure you set the touchPadID this way and use "Wheel" as touchpadString
```
touchpadID=$(xinput list | grep $touchpadString | awk -F " " '{print $7}' | awk -F "=" '{print $2}')
```

---

### Post by shadowninty on 2011-06-02
Cant get my elantech touchpad recognised properly here either
Really need multitouch :(

---

### Post by mkquist on 2011-06-05
make -C /usr/src/linux-headers-`uname -r` SUBDIRS=`pwd` drivers/input/mouse/psmouse.ko  ok not to sound too noob, whats the pwd stand for... really would like to get this working...

---

### Post by shadowninty on 2011-06-17
> **benbeel said:**
> I use synclient to adjust my touchpad settings on my asus UL30A. You can enter into a terminal ```
synclient -l
```
This will provide a list of current settings for the touchpad. For instance, you may see TapButton2=3, which means a three-finger strike will trigger mouse button 2. You can change that to two-finger strike triggers button 2 by entering the following code:
```
synclient TapButton2=2
```
You can extrapolate this to any of the options present there. Check the man synclient for more info.

Hope this helps.
I love you. Thank You so much

---

### Post by ALLurGroceries on 2011-06-18
@mkquist pwd stands for print working directory, it returns the full path of your current working directory

I haven't subscribed to this thread in ages, I'll try reading backwards when I have more time... oops. :p

---

### Post by mikewhatever on 2011-07-15
The new 2.6.32-33 kernel adds Elantech support in Lucid, but completely breaks the previously decent touchpad functionality. Have to use the following in the startup apps:
```
synclient TapButton1=1 TapButton2=2 TapButton3=3 AreaBottomEdge=700 AreaLeftEdge=25 AreaRightEdge=1125
```

---

### Post by sridel on 2011-07-25
> **Bender2k14 said:**
> These instructions didn't work for me and now my touchpad doesn't work at all.

When executing the last instruction, I get:
```
tyson@tyson-netbook:~/src/linux-source-2.6.31$ sudo modprobe psmouse
FATAL: Error inserting psmouse (/lib/modules/2.6.31-20-generic/kernel/drivers/input/mouse/psmouse.ko): Invalid module format

```Why didn't it work?



I received a similar error when doing sudo modprobe psmouse in step 8. However, I could regain control by issuing the sudo insmod psmouse.ko command from within the directory ~/src/linux-source-2.6.38/drivers/input/mouse.

For me the fix was to 
[CODE] sudo gedit /etc/modprobe.d/psmouse.conf
[CODE/]
and comment out the line 'options psmouse force_elantech=1' like so....
[CODE]#options psmouse force_elantech=1
[CODE/]

This was a remnant from an earlier attempt to get my Elantech touchpad recognized correction on my Samsung QX410. With the current patch I now have two finger scrolling (hor/vert), palm recognition, two finger tap which simulates right click, and click and drag. I am missing edge scrolling in both directions (prolly something in the config), and of course pinch to expand (which is not yet available to my knowledge)...

FYI, I am a very enthusiastic noob, and this is my first ever post, so be gentle.

Thanks ALLurGroceries for an excellent tutorial!

---

### Post by nymusicman on 2011-07-30
The solution on page 5 works for the Samsung RF711 with Ubuntu 11.04 if you use the patches found [here]("https://bugzilla.kernel.org/show_bug.cgi?id=27442") inside posts 49 and 50. Both batches must be applied.

---

### Post by Chromos on 2011-08-13
the how to on page 5 dont worked for me. Im using kernel 2.6.38-10-generic and the elan-tocuhpad is recogniced as PS/2 Generic Mouse. Just adding the line "options psmouse force_elantech=1" to /etc/modprobe.d/psmouse.conf changed nothing.
Should I do the howto?

---

### Post by LifeBringer on 2011-08-20
Same problem here chromos, someone made a gdeb package too, but I have yet to find it, it's x86-64.

---

### Post by Mr.BS on 2011-09-13
Elantech problems and most other ones are solved by cucisan....check out [http://ubuntuforums.org/showthread.php?t=1791081](http://ubuntuforums.org/showthread.php?t=1791081)

---

### Post by Lamko on 2011-09-13
There is a dkms which ads support to the natty kernel
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904)
Install it, know it gets recognized as Elantech mousepad.

There is another bug in Ubuntu natty which swaps the right and middleclick buttons also scroll isn't working.
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/563276](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/563276)

Therefore you need this PPA for natty
[https://launchpad.net/~o.shybystyi/+archive/gnome-settings-daemon-natty](https://launchpad.net/~o.shybystyi/+archive/gnome-settings-daemon-natty)

Now I can enable scroll and configure the touchpad buttons in the mouse configuration menu at the tab : touchpad.

All working fine, now :)

---

### Post by kmas on 2012-03-16
I'm having similar issues. Mousepad was finally detected but I can't get synclient or the touchpad tab to work. 
[http://ubuntuforums.org/showthread.php?p=11770109](http://ubuntuforums.org/showthread.php?p=11770109)

---

### Post by Digger109 on 2012-05-10
> **absolutezero1287 said:**
> I have the same touchpad on my Lenovo Ideapad Z560. What worked for me was the following:
```

sudo rmmod psmouse
sudo modprobe psmouse proto=imps

```In order to make the change permanent you must add a file to /etc/modprobe.d/. The file must have .conf at the end. I named my file touchpad.conf. The file must have the following line: 
options psmouse proto=imps

Hope this helps.

FYI, if the above file has ever been added to "/etc/modprobe.d", it will, in my case anyway (eee PC 901 with Debian Squeeze loaded), prevent the touchpad from being recognized as an Elantech touchpad.  If you're having this problem, I'd check for this file, first.

IHTHS!

---

### Post by NormanFLinux on 2013-02-23
[QUOTE=Digger109;11922375]FYI, if the above file has ever been added to "/etc/modprobe.d", it will, in my case anyway (eee PC 901 with Debian Squeeze loaded), prevent the touchpad from being recognized as an Elantech touchpad.  If you're having this problem, I'd check for this file, first. QUOTE]

I have a Dell Mini 10 with an Elantech touchpad. I could press the left and right buttons but the touchpad cursor was frozen solid in Ubuntu 12.10. Adding the psmouse file to /etc/modprobe.d sets up the touchpad as a generic mouse. Finally cursor movement works on the desktop. Its not recognized an Elantech touchpad but the main thing is the touchpad cursor now works! In gpointing-device-settings the Elantech touchpad shows up as a generic mouse - which is a good fix to this particular problem with the synaptics touchpad driver not loading from the kernel.

---


---
title: "ALPS touchpad not recognized (hp mini 311)"
date: 2009-11-05
forum: Hardware
---

### Post by patsissons on 2009-11-05
fresh install of 9.10, the touchpad works, but i cannot use gsynaptics to configure it.  The touchpad will move the mouse, tap to click, and scroll.  It may do other things but this is all i have tried, basically it does do more than just move the mouse.

i have xserver-xorg-input-all installed, and running 2.6.31-14-generic kernel.  I added output from the usual indicators below.  you can disregard the microsoft mouse, its just the usb mouse i have plugged in right now (didn't want the device numbers to be confusing so i included it).  It appears that the touchpad is just being recognized as a basic mouse, instead of an alps touchpad.  I really don't know how to even start working at this because i don't understand why the touchpad works (scroll and tap to click) but isn't recognized.  strange indeed, any thoughts are appreciated.  Oh, one last thing, tpconfig appears to see the device as a valid touchpad, but 

relevant output from devices:
```

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input4
U: Uniq=
H: Handlers=mouse0 event4
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=045e Product=0040 Version=0110
N: Name="Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)"
P: Phys=usb-0000:00:04.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/input/input7
U: Uniq=
H: Handlers=mouse1 event7
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

I: Bus=0011 Vendor=0002 Product=0005 Version=0000
N: Name="ImPS/2 Generic Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input9
U: Uniq=
H: Handlers=mouse2 event9
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

hal-device output:
```

udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  info.capabilities = { 'input', 'input.mouse' } (string list)
  input.device = '/dev/input/event9'  (string)
  input.product = 'ImPS/2 Generic Wheel Mouse'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  input.x11_driver = 'evdev'  (string)
  info.subsystem = 'input'  (string)
  info.product = 'ImPS/2 Generic Wheel Mouse'  (string)
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input9/event9'  (string)
  info.parent = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port_logicaldev_input'  (string)
  info.callouts.add = { 'hal-probe-vmmouse' } (string list)
  info.category = 'input'  (string)
  linux.device_file = '/dev/input/event9'  (string)

```

relevant output from xinput list:
```

"Virtual core pointer"  id=0    [XPointer]                                                                                                           
        Num_buttons is 32                                                                                                                            
        Num_axes is 2                                                                                                                                
        Mode is Relative                                                                                                                             
        Motion_buffer is 256                                                                                                                         
        Axis 0 :                                                                                                                                     
                Min_value is -1                                                                                                                      
                Max_value is -1                                                                                                                      
                Resolution is 0                                                                                                                      
        Axis 1 :                                                                                                                                     
                Min_value is -1                                                                                                                      
                Max_value is -1                                                                                                                      
                Resolution is 0                                                                                                                      
"ImPS/2 Generic Wheel Mouse"    id=8    [XExtensionPointer]                                                                                          
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
"Macintosh mouse button emulation"      id=9    [XExtensionPointer]
        Type is MOUSE
        Num_buttons is 5
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
"Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)"        id=10   [XExtensionPointer]
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

relevant output from dmesg:
```

[    1.309645] input: Macintosh mouse button emulation as /devices/virtual/input/input4
...
[    1.450492] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.465323] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.465339] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.465503] mice: PS/2 mouse device common for all mice
...
[   11.142661] psmouse serio1: ID: 73 02 64
...
[   11.841028] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input9

```

tpconfig -i output:
```

Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;           no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.

```

---

### Post by patsissons on 2009-11-06
just an update, i don't think tpconfig is of any use, it appears to have the same output for both the touchpad and the usb wheel mouse.

---

### Post by madbbb on 2009-11-09
i have same problem on my mini 311

dmesg:
```

[    1.446499] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.466036] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.466050] serio: i8042 AUX port at 0x60,0x64 irq 12

```
```

udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'
  linux.sysfs_path = '/sys/devices/platform/i8042/serio1/input/input8/event8'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.category = 'input'  (string)
  info.capabilities = { 'input', 'input.mouse' } (string list)
  input.device = '/dev/input/event8'  (string)
  input.product = 'ImPS/2 Generic Wheel Mouse'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.device_file = '/dev/input/event8'  (string)
  input.x11_driver = 'evdev'  (string)
  info.subsystem = 'input'  (string)
  info.product = 'ImPS/2 Generic Wheel Mouse'  (string)
  info.udi = '/org/freedesktop/Hal/devices/computer_logicaldev_input'  (string)

```

---

### Post by Setheus on 2009-11-09
Im having the same problem with my ASUS X5DIJ. Its annoying as I cant turn the touchpad off while typing! *grrr*

---

### Post by lflindsey on 2009-11-11
I've got the same problem on my hp mini 311.  I have Xorg configured to use the touchpad with the synaptics driver.  It recognizes it and it works just fine, but as with y'all, gsynaptics et al won't turn off the tap-to-click "feature".

---

### Post by madbbb on 2009-11-13
> **lflindsey said:**
> I've got the same problem on my hp mini 311.  I have Xorg configured to use the touchpad with the synaptics driver.  It recognizes it and it works just fine, but as with y'all, gsynaptics et al won't turn off the tap-to-click "feature".

how did you configured xorg.conf to use synaptics driver?

---

### Post by Glimps on 2009-11-14
Same problem here. HP mini 311. I can scroll on the right side, tap to click but it is not recognised as a touchpad.

---

### Post by lflindsey on 2009-11-16
> **madbbb said:**
> how did you configured xorg.conf to use synaptics driver?

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "Device"                "/dev/input/mouse1"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
    Option        "TapButton1"        "0"
    Option        "TapButton2"        "0"
    Option        "TapButton3"        "0"
EndSection
```

Looking at this, I can't remember what auto-dev does.  I should look that up...

---

### Post by kruzztee on 2009-11-17
So basically, no improvement on Alps Touchpad detection in 9.10... it so frustrating at 9.04 and why is it not fixed yet?

---

### Post by madbbb on 2009-11-18
its possible to disable touchpad with:

```

sudo rmmod psmouse

```

:D

---

### Post by psuter on 2009-11-18
Hi all 

two days ago i bought a HP Pavilion dm1 which looks exactly like the mini 311 but it has a faster dual core cpu, 2gig's of ram and 320 gigs of harddisk space. however, it seems to have the same crappy touchpad. 

allthough i am not really a c programmer nor a kernel hacker i saw a wiki (german) which described some way to modify the alps driver to enable the use of newer models.. (here's the link for those speaking german amongst you: [http://wiki.ubuntuusers.de/Touchpad#Touchpad-wird-nicht-erkannt](http://wiki.ubuntuusers.de/Touchpad#Touchpad-wird-nicht-erkannt) ) 

however, the proposed line didn't work but once i was in that file i started to fiddle around.. 

in the german wiki they add one line that looks like this: 
```
 { { 0x73, 0x02, 0x50 }, 0x4f, 0x4f, ALPS_FW_BK_1 },
```

to the array definig the different known alps touchpad models (this line probably contains the model description for one type i think) 

i then found in the sources, that the first three numbers must match some kind of a hardware fingerprint which they call "E7 report". in order to find out the numbers for my notebook i changed to debug mode by defining DEBUG at the beginning. i then recompiled and loaded the new module. and voilà, my E7 report contained: 73 02 64. so i put them in a new line like this one: 

```
{ { 0x73, 0x02, 0x64 }, 0xf8, 0xf8, ALPS_FW_BK_2 },
```

and recompiled and loaded the whole thing.. and tataaaaa.. my ubuntu recognized an ALPS touchpad and when i checked the mouse settings in gnome i even saw the touchpad tab where i could choose all these options and disable the pad while typing etc.. but don't jump around yet.. because sadly it had no effect on the behaviour of the touchpad.. no matter what i set, it didn't change anything.. 

since i had no clue what the rest of the line was for (except for the last parameter which seems to be something defining special types of touchpads which obviousley need special attention) i tried to go deeper into the sources to find out what the rest stands for... 

while i did't find out what the rest is used for (and changin it had no effect on it not changin anything in gnome) i found the place where the actual events from the touchpad are being received by the driver and then processed to pass them on to the system.. its inside the function called 
alps_process_packet()

i started to put some printk statements in there which basically print some output to the dmesg pipe or whatever that thing is called and i then found out that as it seems the touchpad itself is sending pure ps2 commands to the OS.. 

and i also found out that from the data packet, that the driver seems to receive from the bios or whatever sends them, there was no way to distinguish between a tap-click and a real mouse button click! 

while googling around the web i also found out that other notebooks with similar touchpads have a "hardware tap feature" which can be enabled or disabled.. if it is enabled the touchpad's firmware does the interpretation of the tap and converts it into a click and i suspect that exactly this is what's happening here... sadly HP's bios sucks so badly that they don't allow us customers to change anything at all and they also don't allow to change how the pad works.. 

i am  now about to restore my notebook to windows 7 again, hoping to find a driver option which disables this crappy hardware touch stuff and finally makes the touchpad work as a real touchpad.. 

if anyone of you knows what the rest of the lines stand for or how the whole mouse stuff really works i'd be happy to know more about it.. 

another thing that worried me a bit was: allthough x seemed to recognize my mous as a touchpad it didn't seem to receive the mouse movement from the touchpad driver.. when i checked with 
```
xinput test "AlpsPS/2
``` 
..." i never saw any movements.. i only saw them on the PS/2 Mouse device.. whereas on my old vaio it is exactly the opposite way, i see the movements from the alps but not form the regular ps2 mouse driver.. 


any help on this is appreciated.. this stupid tap feature really renders my notebook more or less useless because it is soooo annoying when typing something.. 

my last solution to "solve" the problem would be to find a way how to script X to not accept any mouse input while typing.. so also with a normal mouse it would not be able to move it or click while typing ... maybe that's available somewhere.. the problem of accidentially clicking on something while moving the cursor around would still exist though.. 

regards
Pascal

---

### Post by psuter on 2009-11-19
unfortunately changing any of the settings under windows doesn't change anything for linux. so if these settings like the tapping are to be changed in the firmware at least they don't stay permanently. 

one thing i've noticed.. i was playing around with those i8042 parameters and it seemed that i disabled the vertical scrolling somehow using these kernel parameters (like i8042.reset and such) ... so maybe fiddling with the i8042 driver could help to get real touchpad stuff from the touchpad and not just mouse commands.

---

### Post by psuter on 2009-11-21
and another self-reply :) (maybe someone will find this interesting one day :) )

i experimented alot with the alps.c driver source but i couldn't find the right solution yet. however, i succeeded in getting rid of the biggest annoyance: my ubuntu 9.10 now turns off the mousepad when i'm typing.. i therefore had to giveup the scrolling for now.. 

so here is the current status: 
as described before i found out that the touchpad is a new type with a new E7 signature. I added the signature to the driver which with most other new types of alps touchpads usually leads to the touchpad being recognized as a touchpad and then the cursor jumps around your screen like crazy until you set the last three arguments in that line i discussed before to the right values. unfortunately in our case this doesn't happen. the mousepad is recognized as an alps pad now and gnome shows the desired third pannel in the mouse settings but they have no effect. that is, because the touchpad is still working in some kind of pass through mode, meaning, it still transmits relative movements and not absolute coordinates of the finger posiion on the tablet and therefore it still is the firmware of the touchpad who decides weather it should click on tab and these things and because the ps2 output is then sent through a virtual ps2 mouse device rather than through the alps device even disabling the mousepad won't work. 

i then commented out some lines in the driver part where it obviously creates this second virtual mouse and made it not do this anymore. however i don't understand what i've really done in detail, i just imagine i did about this :) .. the consequence is, that now the ps2 commands are sent through the driver and then through the alps device and therefore gnome is now able to turn off the touchpad while i am writing.. 

at least it can do so as long as you don't stop and think .. :) 

below you can find my modified alps.c file and a compiled version of psmouse.ko

if you use the exact same version of ubuntu 9.10 with the same kernel as i am (i am using the regular desktop install, up to date as of now and with the folowing kernel: 

```
$ uname -a
Linux pshp 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

```

so if this is the same for you you can give it a try and copy these two compiled files to /liob/modules/2.6.31-14-generic/kernel/drivers/input/mouse/ **AFTER MAKING A BACKUP COPY OF THE ORIGINAL!**
and then do 
```
sudo rmmod psmouse
sudo modprobe psmouse
```

now you should see the "touchpad" tab under System->Preferences->Mouse

you have to disable and then enable the "disable touchpad while typing" option to activate it the first time. from then on it should work.. 

i hope i'll get some help from someone who knows how the driver really works and how i can find out how to do this the right way and get the touchpad to work as a real touchpad. 

regards
pascal

---

### Post by madbbb on 2009-11-22
thank you psuter!!! now my mini311 touchpad turns off while typing, but without scroll.

---

### Post by patsissons on 2009-12-07
I don't know much about kernel compiling, so how do you compile just the psmouse kernel module? like i know enough to compile the entire kernel, but is there an easy way to just rebuild psmouse.ko?

---

### Post by patsissons on 2009-12-07
i will self reply too... here is the answer to my question.

once you have the kernel source and the build requirements, (see [here]("https://help.ubuntu.com/community/Kernel/Compile") for more info) the source will likely reside in /usr/src/linux-source-`uname -r`.  so copy the mouse module source files to somewhere like /tmp/mouse (i.e. cp /usr/src/linux-source-`uname -r`/drivers/input/mouse /tmp/mouse), or if you don't care about modifying your /usr/src then just edit the files in place.

once your source files are modified to your liking, from within your mouse directory (either /tmp/mouse or /usr/src/...) run the following command:

```
make -C /lib/modules/`uname -r`/build M=`pwd` psmouse.ko
```

finally, you'll need to copy your psmouse.ko module back to the modules directory like psuter said.  remember to rmmod psmouse first, copy (backup first) the module over, then modprobe psmouse.

---

### Post by indelible on 2009-12-08
Used your binary successfully on 2.6.31-16-generic #52-Ubuntu SMP, thanks for the hack.  Can't disable the tap to click "feature" still using either the Trackpad tab in mouse settings or gpointing-device-settings, and stuck with no scrolling, but it's still better than constantly clicking the damn thing accidentally while typing  ;) This is definitely an annoying bug, hopefully it will get squashed soon.  Not having a properly functioning trackpad on a netbook/laptop is a major pain.  

The 311 is awesome in 9.10 though, aside from this one thing.. compiz runs perfect thanks to the ION, wifi and sound work great out of the box. If I had the cash lying around I'd buy some kernel hacker a 311 just to get it done yesterday. :P

---

### Post by patsissons on 2009-12-11
i have been using synaptiks so far which seems to work well for avoiding the accidental touchpad bumps while typing.  i also wrote a quick script for rebuilding the psmouse module.

```
#!/bin/bash                                                                                                                                          
                                                                                                                                                     
BUILD_DIR=/tmp/mouse                                                                                                                                 
SRC_DIR=/usr/src/linux-source-2.6.31/drivers/input/mouse                                                                                             
MOD_DIR=/lib/modules/`uname -r`/kernel/drivers/input/mouse                                                                                           
MOD_BUILD_DIR=/lib/modules/`uname -r`/build                                                                                                          

if [ "`whoami`" != "root" ]; then
    echo "Please Run as root"
    exit
fi

echo "Unloading old psmouse module"
rmmod psmouse

echo "Removing old module build directory"
rm -rf $BUILD_DIR

echo "Copy source files to new build directory"
cp -R $SRC_DIR $BUILD_DIR
cd $BUILD_DIR

echo "Building psmouse module"
make -C $MOD_BUILD_DIR M=$BUILD_DIR psmouse.ko
if [ -z $BUILD_DIR/psmouse.ko ]; then
    echo "Module failed to build, aborting"
    exit
fi

if [ -z $MOD_DIR/psmouse.ko.orig ]; then
    echo "Backing up original psmouse module"
    cp $MOD_DIR/psmouse.ko $MOD_DIR/psmouse.ko.orig
fi

echo "Installing new psmouse module"
cp $BUILD_DIR/psmouse.ko $MOD_DIR/psmouse.ko

echo "Loading new psmouse module"
modprobe psmouse
```

i just left it in the kernel source path where the mouse driver files are located.

---

### Post by farbird on 2009-12-14
could this thread be of any help??

[http://www.uluga.ubuntuforums.org/showthread.php?p=8459653](http://www.uluga.ubuntuforums.org/showthread.php?p=8459653)

---

### Post by wysiwyg31 on 2009-12-20
Hello patsissons,

I try to use your script but face some issues.


It seems that the makefile is missing or something (the make step does not work).

do you have some suggestions ?

I think we should prepare a kind of howto at the end. many users would be interested. 

ps: I use jolicloud prebeta. It is based on ubuntu netbook remix 9.04 but with some modification.

---

### Post by wysiwyg31 on 2009-12-22
Hello,

finally, I get back to UNR 9.10.
It work and I have the tab with the touchpad in the mouse properties.

On the other hand, it seems that the scroll function on the right on the touchpad does not work any more...

any idea?

---

### Post by farbird on 2009-12-27
any new updates on this issue?

Am on 9.10 and the touchpad is driving me nuts

---

### Post by genosensor on 2009-12-30
I, too, got very frustrated with the HP 311 touchpad.

In desperation, I hacked the AT keyboard and the psmouse drivers
in the 2.6.32 kernel to cooperate so that standard PS/2 mouse events
could be ignored for a preset amount of time after any key is pressed
and/or require that a specified key remained pressed for mouse input
to be accepted.

500ms seems to work reasonably well for me.

I also experimented with forcing one to hold down the caps lock key
while using the touch pad.  This completely eliminates touch pad
artifacts, but it takes a bit of getting used to.

If anyone's interested (and willing to build and test a custom patched kernel),
I'll post a patch file here after I've tested it a bit more myself.

Hey, I managed to type this whole message without screaming ;-)

- brent

---

### Post by farbird on 2010-01-01
awaiting your patch and instructions

---

### Post by FireNoodle on 2010-01-02
Same problem with the missing touchpad tab here, I would love a solution that didn't require disabling scrolling. Once the touchpad stuff is working will two-finger scrolling work?

---

### Post by beefstu on 2010-01-04
Maybe someone who has got the touchpad tab back could try this? [http://blog.twinapex.fi/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/](http://blog.twinapex.fi/2009/10/11/setting-up-multi-touch-scrolling-for-ubuntu-9-10-karmic-koala-linux-on-asus-eee-1005ha-netbook/)

I'm really missing two-finger scrolling but would rather at least keep the side scrolling that (sort of) works than loose that just to get the option to disable whilst typing back at the moment.

---

### Post by nrune on 2010-01-07
Any Movement on this the touch poad not turning off is driving me nuts.

---

### Post by genosensor on 2010-01-09
Attached is a patch to the generic 2.6.32.2 kernel sources from kernel.org

It patches the ps/2 mouse driver and the at keyboard driver such that mouse input will be ignored for a preset time delay after the last key pressed or released.

It can also be configured to require that a key remain pressed to enable mouse input.
Typical choices are the caps lock or the windows key.
If you go this route, you have to use two hands to operate the touch pad.

I find the keyboard delay is good enough for me.  It eliminates random touchpad noise as long as you keep typing quickly.  You just have to remember to take your palm off the pad whenever you stop typing.

Note that this assumes your touch pad is not recognized as such.
If your touchpad emulates a PS/2 mouse (as that in the HP311 Mini does), it should work with this patch.  If it emulates a scroll wheel, that should continue to work.
If it is recognized as a touchpad, however, these patches won't work for you.
Look, instead, into fixes in the synaptics X windows driver to ignore palm noise.

I'm assuming also that whoever tries this is already familiar with the process of building 2.6 series kernels from source code:

1)  Download the 2.6.32.2 kernel from kernel.org
     Other recent versions probably will work, but they are untested.

2)  untar the contents of the attached archive into the top level linux source directory

3)  after changing to that directory, apply the patch with:

$  cd linux*
$  patch -p1  < ignoreMouseWhileTyping.diff

4)  configure, build and install your patched kernel
     Note that the hp311-config.tar archive contains the kernel
     configuration I use for my HP311 Mini.  If you'd like to use it as a starting point
     untar it and rename  hp311.config to .config, then run:   $ make oldconfig

If all goes well, you'll have a kernel that works just as before.
You'll need to reload the psmouse module with one or both of these new parameters to enable the new palm noise filtering features:

int enable_key:  Keycode of key that must remain pressed to enable mouse
int enable_delay:  msecs after last keystroke before mouse re-enabled

You can most quickly do that as follows:

# modprobe -r psmouse && modprobe psmouse enable_delay=1000

After you've found an enable_delay (and/or enable_key) that work well for you,
create a psmouse.conf file in /etc/modprobe.d similar to the example provided in the attached tarball.

I hope at least someone (else) finds this helpful.

---

### Post by firefeather on 2010-03-12
I've filed a bug on this issue at [LP:527890]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/527890") following the instructions at the Ubuntu Wiki [page on debugging touchpad detection]("https://wiki.ubuntu.com/DebuggingTouchpadDetection"), if any of you would like to mark this bug as affecting you or subscribe to the bug e-mail.

---

### Post by pmcelwee on 2010-04-03
Thanks genosensor for this patch. I just installed it on UNR using kernel 2.6.32.11. I haven't tried the enable-key option, but the enable-delay solves the problem for now. Mouseemu did something similar, but I did not seem to be able to change the delay time to make it longer on mouseemu. I currently have it set to 1500, though that might start to bother me when I'm doing things other than typing. (I *really* hope there will be an official fix soon that simply allows disabling tapping, though since this bug goes back at least 5 years, I'm not holding my breath.) 

I am completely new to Linux, but this ALPS touchpad bug (I'm using an Acer AspireOne 532h) was driving me crazy enough to tackle patching and configuring a kernel for the first time.

Thanks again genosensor!

---

### Post by captainhorseboy on 2010-04-05
> **madbbb said:**
> thank you psuter!!! now my mini311 touchpad turns off while typing, but without scroll.

this is my exact issue at this time.  everything is functional after installing NBR10 except for touchscrolling on the right side.

---

### Post by farbird on 2010-05-14
any new updates?

---

### Post by FireNoodle on 2010-05-14
Nothing that works that I've found. Lucid included an update that didn't work, I think its been marked regression already. It got the touchpad tab in mouse properties back, but the functions there don't work. It also broke vertical scrolling which had to be put back using a workaround from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/78:](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/78:)

"
Add the following to /etc/modprobe.d/psmouse.conf:
 options psmouse proto=imps
The psmouse.conf file doesn't exist by default, just create a text file  with that name in /etc/modprobe.d/
"

It works to restore the scrolling and the tab is still present but disabling tapping during typing or other options don't function.

I use Alt-F2 (Run) with "gksudo modprobe -r psmouse" to turn the touchpad off and "gksudo modprobe psmouse" to turn it back on. Awful work around but with an extra mouse it does the job when I need it to.

---

### Post by farbird on 2010-05-18
sucky aint it?

why cant HP use common parts such as the actual synaptics touchpad and intel wifi mini-pci cards?


sigh...

---

### Post by pmcelwee on 2010-05-26
**UPDATE: This does not actually work. See next two comments.**

There is one silver lining. If you want to disable the touchpad while typing, you can now (meaning, using Lucid) use mouseemu to do that (rather than having to patch the kernel, as before). This is probably because the touchpad is recognized as a touchpad rather than a mouse. Once you have the mouseemu package installed, just remove the comment marker on the relevant line in /etc/default/mouseemuThere don't seem to be any immediately apparent side effects of doing this.

---

### Post by FireNoodle on 2010-05-26
pmcelwee: Does that actually  work for you? I have deleted the comment in the mouseemu config file but it doesn't actually stop accidental taps when typing.

Did you have to do something additional to get this working?

---

### Post by pmcelwee on 2010-05-26
FireNoodle:
Your comment made me go back and check - and you're right, it doesn't actually stop taps. :confused:

It **does** stop the touchpad from being able to move the cursor around while typing - that's why I assumed that tapping was barred as well, but sadly no. I can still tap on the touchpad and click using the button while typing ... I just can't move the cursor around.

Sorry for the confusion.

---

### Post by mike909 on 2010-07-26
> **FireNoodle said:**
> 
"
Add the following to /etc/modprobe.d/psmouse.conf:
 options psmouse proto=imps
The psmouse.conf file doesn't exist by default, just create a text file  with that name in /etc/modprobe.d/
"

That fixed the non-scrolling issue for me.

---

### Post by psuter on 2010-09-18
hey everyone.. since i posted the first solution on how to disable the mousepad while typing i really got used to just lift my thumbs up in the air while typing which also solved that problem for me :) BUT.. my touchpad often gets overly active when touching it.. meaning, i almost can't use the touchpad as a mouse anymore.. when i move my finger across it jumps around on the screen and soometimes even if i get close enough with a finger without even touching it it just clicks! 

do any of you experience this behaviour too or is my mousepad just broken? 

regards
Pascal

---

### Post by elrasho on 2011-03-23
I've installed Linux Mint but it recognises the touchpad as a mouse and so changing the sensitivity does nothing. Can I increase the sensitivity through terminal? I don't know what the commands would be, if anyone can help I'd be very greatfull :)

---

### Post by dangerousnerd on 2011-10-24
A Possible Solution!!... for part of the problem. :)

I know that this is a super old thread, but this has been bugging the heck out of me for so long! I hate having to bring my USB mouse with me everywhere and every time my thumb grazes the trackpad while typing, I want to throw my HP 311 through the nearest window. But, randomly, I think I solved it!!

Well, some of it.  The worst part for me was the whole clicking-while-typing thing. I installed 11.10 hoping that the issue was solved, but to no avail. Today I randomly did a search for "trackpad" in the Ubuntu Software Center and found mouseemu.

Apparently designed for those one button Mac notebooks, I noticed that it had an option for delaying the trackpad while typing. I installed it just an hour or so ago, and so far it is running like a dream - no more clicking while I'm typing!

So, to install:

```
sudo apt-get install mouseemu

```
then run

```
sudo mouseemu -typing-block DELAY

```
you can set your own DELAY to whatever your preference is in milliseconds.

Here's the manpage: [http://manpages.ubuntu.com/manpages/oneiric/man8/mouseemu.8.html](http://manpages.ubuntu.com/manpages/oneiric/man8/mouseemu.8.html)

Hope this works for others. Good luck!!

---

### Post by pmcelwee on 2011-10-24
Actually, there is now a nearly official fix for this. You can download the latest version of the psmouse-alps-dkms package here: [http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb](http://people.canonical.com/~sforshee/alps-touchpad/psmouse-alps-0.10/psmouse-alps-dkms_0.10_all.deb)

See comments by Seth Forshee, who did this great work, on the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/492](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/492)

Thanks to Seth I can use Linux again!

---

### Post by johnh44 on 2011-10-30
Has this ever been resolved? 

The thread goes back to 2006. I have the same symptoms on a Toshiba Satellite C655.

---


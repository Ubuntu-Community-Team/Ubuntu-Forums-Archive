---
title: "Howto: Configuring Touchpad"
date: 2010-02-08
forum: Hardware
---

### Post by pi/roman on 2010-02-08
This guide will not be updated after Maverick Meerkat 10.10 unless this message is removed.

If you have an Elantech touchpad which is being detected as "ImPS/2 Logitech Wheel Mouse" then ALLurGroceries has created a fix for it here:
[http://ubuntuforums.org/showthread.php?p=9175201](http://ubuntuforums.org/showthread.php?p=9175201)

I have not seen a simple howto guide on adjusting touchpad settings so I am making one.
 For Lucid there are special instructions since it does not use HAL configuration.  Lucid users should get the synclient values from step 3 then go straight to step 4b. Now for Maverick it seems we are reverting back to xorg.conf so Maverick users can check out section 4c. Purple syntax is used as a placeholder which should be replaced with proper syntax.

[SIZE=5][COLOR=Sienna]_step 1: research_[/COLOR][/SIZE]
Open a terminal and read or scan through the manuals that may pertain to your problem.
```
man synaptics #synaptics touchpad input driver manual.
man synclient #command line utility to query and modify Synaptics driver options.
man xinput #configures all input devices including touchpad
man syndaemon #a program that monitors keyboard activity and disables the touchpad when the keyboard is being used.
```[SIZE=5][COLOR=Sienna][U]
Step 2: update synaptics driver[/U][/COLOR][/SIZE]
This step is probably unnecessary but is only to ensure you have the latest driver.

```
sudo apt-get update
sudo apt-get install xserver-xorg-input-synaptics
```[SIZE=5][COLOR=Sienna][U]
Step 3: testing touchpad options[/U][/COLOR][/SIZE]
Open a terminal and type:
```
synclient -l
```You should see some values assigned to your touchpad options here. You should not have an 'SHMconfig error' with the latest synaptics driver but if so then please let me know about it.
You can adjust settings temporarily through synclient by typing in terminal ```
synclient [COLOR=DarkOrchid]OPTION[/COLOR]=[COLOR=DarkOrchid]VALUE[/COLOR]
``` Open the synaptics manual 'man synaptics' to see what the different options do. There are a range of possible values for any given option but you will need to play with it to determine what they are.
In order to adjust these values permanently you must enter them into your permanent configuration files.

[SIZE=5][COLOR=Sienna]_Step 4: permanent configuration_[/COLOR][/SIZE]
[SIZE=4][COLOR=SeaGreen]_a: HAL configuration for Karmic 9.10 and earlier_[/COLOR][/SIZE]
All references to your input device should be removed from xorg.conf in order to continue.
Use the the following command to bring up the location of the hal configuration file
```
sudo find /usr/share/hal /etc/hal -name *synaptics.fdi
```The first line of output will list the path to your HAL configuration file if it exists and it should look similar to one of these:
> /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
/usr/share/hal/fdi/policy/10osvendor/11-x11-synaptics.fdi
/etc/hal/fdi/policy/11-x11-synaptics.fdiOpen a program launcher by pressing Alt/F2 and type the following, substituting in the actual path to your configuration file.
```
sudo gedit [COLOR=DarkOrchid]"path to configuration file"[/COLOR]
```Enter the options and values you found to work from step 3 in the following form same as above outside the <!--example section--> and within the <match key> section recreating the line as many times as necessary to cover all your desired options and values:
```
<merge key="input.x11_options.[COLOR=DarkOrchid]OPTION[/COLOR]" type="string">[COLOR=DarkOrchid]VALUE[/COLOR]</merge>
```Save and you are done. The configuration will be implemented the next time you reboot or restart your touchpad driver with modprobe. Then you can check the values by "synclient -l".[COLOR=SeaGreen]

[/COLOR] [SIZE=4][COLOR=SeaGreen]_b: udev configuration for Lucid 10.04_[/COLOR][/SIZE]
This is the only way I have found to configure the touchpad in Lucid but it may not work with ealier releases.
You will need to create a file to include udev rules so use Alt/F2:
```
gksudo gedit /etc/udev/rules.d/touchpad.rules
```Now you should have a blank slate here to configure udev. If you already have code in touchpad.rules then you should be able to append the following code below it:
```
ACTION!="add|change", GOTO="touchpad_end"
KERNEL!="event*", GOTO="touchpad_end"
ENV{ID_INPUT_TOUCHPAD}!="1", GOTO="touchpad_end"
ENV{x11_options.[COLOR=DarkOrchid]OPTION[/COLOR]}="[COLOR=DarkOrchid]VALUE[/COLOR]"
ENV{x11_options.[COLOR=DarkOrchid]OPTION[/COLOR]}="[COLOR=DarkOrchid]VALUE[/COLOR]"
ENV{x11_options.[COLOR=DarkOrchid]OPTION[/COLOR]}="[COLOR=DarkOrchid]VALUE[/COLOR]"
LABEL="touchpad_end"
```In this line: "ENV{x11_options.[COLOR=DarkOrchid]OPTION[/COLOR]}="[COLOR=DarkOrchid]VALUE[/COLOR]" you want to change the [COLOR=DarkOrchid]option[/COLOR] and [COLOR=DarkOrchid]value[/COLOR] to the ones you found to work in step 3 and make only one or recreate as many more of these lines as you need to cover all of the settings you want.

[SIZE=4][COLOR=SeaGreen]_c: xorg.conf for Maverick 10.10_[/COLOR][/SIZE]
You will need to edit xorg.conf in the folder /etc/X11.
```
sudo gedit /etc/X11/xorg.conf
```and add an "InputClass" section using any identifier you want and matching it to the touchpad then insert your configuration options.
```
Section "InputClass"
    Identifier "Touchpad"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Option "[COLOR=Purple]Option[/COLOR]" "[COLOR=Purple]Value[/COLOR]"
EndSection
```Here are some examples of configuration options which can be inserted in the "InputClass" section which I copied from the user documentation for Xserver.
> Option    "LeftEdge"      "1700"
Option    "RightEdge"     "5300"
Option    "TopEdge"       "1700"
Option    "BottomEdge"    "4200"
Option    "FingerLow"    "25"
Option    "FingerHigh"    "30"
Option    "MaxTapTime"    "180"
Option    "MaxTapMove"    "220"
Option    "VertScrollDelta" "100"
Option    "MinSpeed"    "0.06"
Option    "MaxSpeed"    "0.12"
Option    "AccelFactor" "0.0010"
Option    "Repeater"    "/dev/ps2mouse"[SIZE=5][COLOR=Sienna][U]
Step 5: failsafe[/U][/COLOR][/SIZE]
[SIZE=4]_[COLOR=SeaGreen]a: synclient on startup[/COLOR]_[/SIZE]
You have followed this guide to the end and your settings are still not being held after reboot, there is still hope.  Using the synclient commands from step 3, you can place run them in a script and place it in /usr/bin so you can run it anytime or place a shortcut to it in startup applications.  If the script works normally but not at statrtup you will need to add a delay at the beginning, such as "sleep 10;" so it will be executed after the boot up process is complete.
Go to System / Preferences / StartupApplications, click the "Add" button, for "Name" enter whatever you want, and for "Command" enter the name of your script
[SIZE=4]_[COLOR=SeaGreen]b: xinput on startup[/COLOR]_[/SIZE]
You can change settings through xinput also. First look at your touchpad properties:
```
xinput list --short | grep -i 'touchpad' | grep -o '=[0-9]*' | cut -d'=' -f2 | xargs -t xinput list-props
```For a more interactive approach you can use the first part of that command:
```
xinput list --short
```followed by ```
xinput list-props [COLOR=DarkOrchid]'id of touchpad'[/COLOR]
```Each property has a bit size of [COLOR=DarkOrchid]8,16 or 32[/COLOR] so you will have to try each bit size when setting the value. Values are seperated by a space so to set them use the following example:
```
xinput set-int-prop  '[COLOR=DarkOrchid]name of touchpad in single quotes[/COLOR]' '[COLOR=DarkOrchid]name of property in single quotes[/COLOR]' [COLOR=DarkOrchid]bitsize valueA valueB ........[/COLOR]
```and of course substitute the proper syntax for  "'name of touchpad in single quotes' 'name of property in single quotes' bitsize valueA valueB ......."
Then place the setting in an executable file in /usr/bin and create a startup command for it.  If the script works normally but not at statrtup you will need to add a  delay at the beginning, such as "sleep 10;" so it will be executed  after the boot up process is complete.

[SIZE=5][COLOR=Sienna]_Addendum_[/COLOR][/SIZE]
[U][SIZE=2][COLOR=SeaGreen][SIZE=4]a: toggle while typing[/SIZE]
[/COLOR][/SIZE][/U]This option should be available under the system's menu mouse preferences on the touchpad tab.
You can also use the syndaemon command to disable the touchpad while typing from startup applications:
```
syndaemon -i 1 -d -K
```as a startup command will cause the touchpad to be disabled while typing except when using modifier keys.
Another way to disable the touchpad while typing on gnome desktop is in the configuration editor.  Use the gconfig gui from the menu or use this command to see the touchpad settings:
```
gconftool -R /desktop/gnome/peripherals/touchpad
```Use this to set disable_while_typing to true:
```
gconftool -s -t bool /desktop/gnome/peripherals/touchpad/disable_while_typing true
```[SIZE=4]_[COLOR=SeaGreen]b: toggle shortcut[/COLOR]_[/SIZE]
from [[COLOR=Blue]CommunityDocs[/COLOR]]("https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey#Bash%20Script")
Place this script in a file, make it executable and place it in /usr/bin/ so you can start it from the 'run application' dialog box.
```
# toggle synaptic touchpad on/off

# get current state
SYNSTATE=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')

# change to other state
if [ $SYNSTATE = 0 ]; then
    synclient touchpadoff=1
elif [ $SYNSTATE = 1 ]; then
    synclient touchpadoff=0
else
    echo "Couldn't get touchpad status from synclient"
    exit 1
fi
exit 0
```This script will accomplish the same goal except it is designed to toggle the touchpad through xinput:
```
# toggle synaptic touchpad on/off
SYNSTATE=$(xinput list-props "SynPS/2 Synaptics TouchPad" | grep Enabled | grep -Eo '.$')
if [ $SYNSTATE = 0 ]; then xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
else xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0; fi
```[U][SIZE=2][COLOR=SeaGreen][SIZE=4]
[/SIZE][/COLOR][/SIZE][/U]You can also toggle this script through a keypress using keyboard shortcuts.  For instance, press alt/F2 and type "gnome-keybinding-properties" then click add and for name enter whatever you want and for command enter the path to the script which for me would be "/usr/bin/syntoggle.sh". So then click apply and you can set whatever key combination you wish.

_[SIZE=2][COLOR=SeaGreen][SIZE=4]c: toggle when using usbmouse[/SIZE][/COLOR][/SIZE]_
Make a script to disable the touchpad and one to enable it called "synkill.sh" and "synwake.sh". For convenience these can also be run from the command line.
```
DISPLAY=:0 xinput list --short | grep -i 'touchpad' | grep -o '=[0-9]*' | cut -d'=' -f2 | DISPLAY=:0 xargs -I nero xinput set-int-prop nero 'Device Enabled' 8 0
``````
DISPLAY=:0 xinput list --short | grep -i 'touchpad' | grep -o '=[0-9]*' | cut -d'=' -f2 | DISPLAY=:0 xargs -I nero xinput set-int-prop nero 'Device Enabled' 8 1
```Now create a udev rule to enact the script when the mouse is changed and place it in /etc/udev/rules.d/:
[HTML]ACTION=="add", SUBSYSTEMS=="usb", ID_CLASS="mouse", RUN+="/bin/sh -c /usr/bin/synkill.sh"
ACTION=="remove", SUBSYSTEMS=="usb", ID_CLASS="mouse",  RUN+="/bin/sh -c /usr/bin/synwake.sh"[/HTML]That concludes this guide. I will update it if I find there is more to add. Good luck.

---

### Post by radtek on 2010-02-10
Thanks for doing this. I'm running 9.04 64bit on a 2 y.o. Toshiba laptop. Always had issues with the touchpad and typing.

Fairly sure I'm configured through HAL.

```
radtek@radtek-laptop:~$ sudo find /usr/share/hal /etc/hal -name *synaptics.fdi -print0 | xargs -0 -t cat
[sudo] password for radtek: 
cat /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi 
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        [COLOR="Red"]<merge key="input.x11_driver" type="string">synaptics</merge>[/COLOR]
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        [COLOR="Red"]<merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->[/COLOR]
    </match>
  </device>
</deviceinfo>

```

Then for fun I tried this:

```
radtek@radtek-laptop:~$ [COLOR="Red"]synclient -l[/COLOR]
Can't access shared memory area. SHMConfig disabled?
radtek@radtek-laptop:~$ [COLOR="Red"]syndaemon -d -t -i 1[/COLOR]
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  141 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  12
  Current serial number in output stream:  12
radtek@radtek-laptop:~$ [COLOR="Red"]synclient TouchPadOff=1[/COLOR]
Can't access shared memory area. SHMConfig disabled?

```

Any Ideas?

---

### Post by pi/roman on 2010-02-10
This line needs to be included in the HAL configuration:

<merge key="input.x11_options.SHMConfig" type="string">true</merge>

hope that helps

---

### Post by Dackandy on 2010-02-12
Hi,

I have 9.04, had 9.10, and I needed to disable the touch pad, since every time I tried to write something, the cursor jumped where was left by the touch pad. I tried in 9.10 to make some changes, with limited success, and when I had to reinstall the whole Ubuntu, I put it back the 9.04. Surprise! There was Disable touch pad. Cannot this be inserted in the new versions, or a configuration possibility like it is in Windows: Disable touch pad if external mouse detected. Have someone some bright ideas, since I'm not a programmer, I may actually mess something. Thank for help.

---

### Post by pi/roman on 2010-02-13
> **Dackandy said:**
> 
  Disable touch pad if external mouse detected.

I have not found how to disable the touchpad when a mouse is attached but there is a script here to toggle it:
[[COLOR=Blue]SynaticsShortcut[/COLOR]]("https://help.ubuntu.com/community/SynapticsTouchpad/ShortcutKey#Bash%20Script")
I will summarize how to use it. Copy and paste this into an empty file called syntoggle.sh on your desktop: 
```
# toggle synaptic touchpad on/off

# get current state
SYNSTATE=$(synclient -l | grep TouchpadOff | awk '{ print $3 }')

# change to other state
if [ $SYNSTATE = 0 ]; then
    synclient touchpadoff=1
elif [ $SYNSTATE = 1 ]; then
    synclient touchpadoff=0
else
    echo "Couldn't get touchpad status from synclient"
    exit 1
fi
exit 0
```Then right click, go to properties / permissions and check to "allow executing as program", then move it to /usr/bin/
```
sudo mv ~/Desktop/syntoggle.sh /usr/bin/
```and you will be able to run it by alt/f2. You could also create a link to it from the desktop:
```
sudo ln -s /usr/bin/syntoggle.sh ~/Desktop/syntoggle
```

---

### Post by pi/roman on 2010-02-13
Here is way to disable the touchpad when hotplugging a usb mouse which shows success in test mode for me but does not work when it is actually called.

I gathered information on my mice by plugging them in then copying the lshal to file:
```
lshal > ~/Desktop/device-data
```Then search through it for "usbhid" and if you have 2 usb mice plugged in there should be 2 sections for this. You can get different values out of this section to identify your mouse like:
> usb.interface.class = 3
usb.interface.protocol = 2
info.subsystem = 'usb'So then you can take these values and make a udev configuration in the /etc/udev/rules.d/ folder to run a command whenever this device is plugged in. Here is mine:
```
SUBSYSTEMS=="usb", ATTRS{bInterfaceProtocol}=="02", ACTION=="add", RUN+="xinput set-int-prop 'SynPS/2 Synaptics TouchPad' 'Synaptics Off' 8 1"
SUBSYSTEMS=="usb", ATTRS{bInterfaceClass}=="03", ACTION=="remove", RUN+="xinput set-int-prop 'SynPS/2 Synaptics TouchPad' 'Synaptics Off' 8 0"
```I use different values for testing but they all work in test mode. You could also run the "synclient touchpadoff=1" command. 
You can find the path to your device by running:
```
udevadm monitor
```and then plugging your usb mouse.
To test the udev config with the mouse plugged in I run:
```
udevadm test /devices/pci0000:00/0000:00:10.2/usb4/4-1/4-1:1.0
```with the path I found from udevadm monitor and it shows that my command is being run in test mode:
> udev_rules_apply_to_event: RUN 'xinput set-int-prop 'SynPS/2 Synaptics TouchPad' 'Synaptics Off' 8 1'and the command works to disable the touchpad in terminal but it does not seem to work when hotplugging.

---

### Post by pi/roman on 2010-02-13
Ok, I have the touchpad switch upon hotplugging a mouse working now.  It seems the problem is that udev is unable to communicate with Xserver directly and it's very difficult to make X listen to it.
So you need to make scripts to do the work and then run them from udev commands. The scripts are simple, here is a touchpad disabler:
```
DISPLAY=:0 xinput set-int-prop 'SynPS/2 Synaptics TouchPad' 'Device Enabled' 8 0
```and this is wakes it up:
```
DISPLAY=:0 xinput set-int-prop 'SynPS/2 Synaptics TouchPad' 'Device Enabled' 8 1
```I named mine 'synkill.sh' and 'synwake.sh'. Save each one in a file and make it executable then place them in /usr/bin/.
So now you only need to call them from udev when hotplugging a mouse so here is the udev script to place in /etc/udev/rules.d/
> ACTION=="add", SUBSYSTEMS=="usb", DRIVER=="usbhid", ATTRS{product}=="*Mouse", RUN+="/bin/sh -c /usr/bin/synkill.sh"
ACTION=="remove", ATTRS{product}=="UHCI Host Controller", RUN+="/bin/sh -c /usr/bin/synwake.sh"You can use any identifier that fits as long it is fairly unique to the type of device you are using. "UHCI Host Controller" was one that fit both my mice.

I've created a more specific rule to ensure the device being attached is a usb mouse although it doesn't work when re-enabling the touchpad so I will update the scripts.

---

### Post by mykrob on 2010-02-13
Hey-

I am still having a problem just getting the synaptics driver loaded on my Asus K50I. I have made the edit to the .fdi files Follwed your directions to the best of my ability, but I must be missing something..

Please take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1404850](http://ubuntuforums.org/showthread.php?t=1404850)

Any advice? What further information do you need from me to be able to help me? My touchpad is not being detected as a touchpad. It works, but requires two fingers to scroll, and I do not have a touchpad option under System-->Preferences-->Mouse

thanks,
-myk

---

### Post by Rhubarb on 2010-02-13
Looks like I'll have to try out Lucid, and update / create another simple guide to allow left + right mouse buttons to be pressed simultaneously without registering as middle mouse button (good for using in games).
For reference, the old old way was to use xorg.conf, the old way was to use hal, and now I'll have to figure out (with the help of this guide) how to use it with udev :)

My old (and now mostly irrelevant thread):
[HOWTO: Emulate2Buttons = false in Intrepid the proper way]("http://ubuntuforums.org/showthread.php?t=972534")

My new (and relevant thread):
[HOWTO: Emulate3Buttons = false in Lucid with udev]("http://ubuntuforums.org/showthread.php?t=1426012")

---

### Post by pi/roman on 2010-02-14
mykrob, your problem goes beyond the scope of my ability. It seems you would have two options which would be to either try to make your laptop recognize your touchpad properly or try to configure whatever controls you can on the device that is recognized.
To make it recognize your touchpad you would probably need to create a udev rule which you can learn about [[COLOR=Blue]here[/COLOR]]("http://www.reactivated.net/writing_udev_rules.html") or typing "man udev" and "man udevadm" into a terminal. Another thing you might want to do is see if anyone with the same model of computer has the touchpad working properly and get a copy of their udev and hal configuration files so you could compare them againt your own. They should probably match up though so it would have to be the id attached to the device that is in error.
To try to configure your touchpad as it is using my guide you could use the  hal configuration from section 4b. You may also need to use an xinput startup configuration from section 5b. You can reference your device by number for easier testing but the device number will change upon rebooting so you will need to use the name in startup commands.

---

### Post by mykrob on 2010-02-15
had a friend buy the same model today. Apparently its just the way this touchpad is "wired", as it performs the same in Windows 7. Even in Windows Almighty, there is no way to take it to a single finger operation.

still a great laptop, just something I'll have to get used to

---

### Post by pi/roman on 2010-02-19
I've adjusted my touchpad toggle script to work with any touchpad as long as it is recognized as a touchpad but I'm not going to place this in the guide so it doesn't get too big.

[PHP]# toggle any touchpad on/off
SYNSTATE=$(xinput list | grep -i touchpad | grep -o '"[^"]*"' | xargs xinput list-props | grep Enabled | grep -Eo '.$')
if [ $SYNSTATE = 0 ]; then xinput list | grep -i touchpad | grep -o '"[^"]*"' | xargs -I nero xinput set-int-prop nero "Device Enabled" 8 1
else xinput list | grep -i touchpad | grep -o '"[^"]*"' | xargs -I nero xinput set-int-prop nero "Device Enabled" 8 0; fi[/PHP]You can replace the 3 "touchpad" 's with anything that you want to toggle from your xinput list then just place it in /usr/bin and make a shortcut key for it if you want or just run it from the run application prompt.

---

### Post by arkmundi on 2010-06-14
See my reply at [http://ubuntuforums.org/showthread.php?t=1509049]("http://ubuntuforums.org/showthread.php?t=1509049").  GSynaptics is the answer!

---

### Post by ahmed abd elkader on 2011-01-23
Hello everyone :D
i`m have a strange problem , my Alps touchpad is detected as PS2 generic mouse but it works fine for me except that the up scroll works as the down scroll , they both scroll the page down , how can i fix that ?

---

### Post by ahmed abd elkader on 2011-01-24
bump

---

### Post by ReproMan on 2011-05-11
As of

Ubuntu 10.04.2 LTS 

2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:25:51 UTC 2011 x86_64 GNU/Linux

the xinput disable trick posted here no longer works for my IBM Ultranav Keyboard.  Touchpad can longer be disabled.

What happened at 10.04.2 that changed how the touchpad is loaded?

Does it work in 10.10, 11.04?  Is either of 10.10 or 11.04 back to the HAL xml tables?

---


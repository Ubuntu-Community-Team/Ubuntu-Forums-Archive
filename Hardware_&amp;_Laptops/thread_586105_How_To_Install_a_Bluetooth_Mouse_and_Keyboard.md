---
title: "How To: Install a Bluetooth Mouse and Keyboard"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by steveneddy on 2007-10-22
**I have edited this thread because I have found a piece of software that seems to work better than the stock bluetooth software. It's called blueman and [can be found here]("http://blueman.tuxfamily.org/"). I have this installed since 11-17-2007 and it works better for me with my bluetooth mouse. You do have to uninstall the old gnome-bloothtooth, bluez stuff and bluetooth from the repos. Just install the .deb from the blueman website and away you go.**

************************************

_**Here is the original thread.**_

I found this helpful info at [this site]("https://help.ubuntu.com/community/BluetoothSetup").

It is a useful site to get basically all of your Bluetooth peripherals set up and hooking up the first time, at boot up.

There is this disclaimer from the web site about Gutsy Gibbon 7.10:

 > 
**For Gutsy Gibbon (7.10)** most of the instructions below are obsolete. For 7.10, just plug in your supported adapter and an icon appears in the top right. Right click to setup your preferences. Devices will auto connect to your PC and you can setup security as you connect each device, eg your phone.

To send files to your phone, in synaptic, install gnome-bluetooth. It will be in the accessories menu, click it to run it. Now sending a file is as easy as right clicking the file and select Send-to. To make this run every time you re-boot, select System-->Preferences--Sessions. Add a Startup program. Call it, lets say, "Bluetooth File Transfer" and in the Command box, enter "gnome-obex-server". Click on OK. 


On my Gutsy install, I never got automatic detection until I followed the following instructions. This works on my system and your may be a little different, but so far everything here seems to work well.

You have to install some software for Bluetooth to work on your machine:

```

sudo apt-get install bluez-utils

```

Then, connect your Bluetooth device if you are using one. Restart the Bluetooth services by doing:

```

sudo /etc/init.d/bluez-utils restart

```

On some machines - 7.04 feisty at least - it may be 

```
sudo /etc/init.d/bluetooth restart
```

On my Gutsy laptop, I use the last command to restart bluetooth and it seems to work.

Verify that your Bluetooth device has been detected, and the appropriate modules loaded by viewing the output of

```
lsusb
```

Here's my bluetooth module listing in **lsusb**

```

Device 004: ID 0a5c:2101 Broadcom Corp.

```

Also, view the output of the command **hcitool dev** which will give you a listing of Bluetooth devices on your computer.

Here's the output of hcitool dev on my machine:

```

Devices:
        hci0    00:16:CE:E1:99:F4

```

***Your Bluetooth device will have a different id.***

If you get all zeros, then try restarting the bluez-utils service and try again.

**Now we have the hardware setup to find your new mouse or keyboard, lets find the mouse/keyboard.**

To connect to a Bluetooth device, you will need to find the address of the device. Make the device discoverable (look for a "Connect" button on many keyboards and mice or look in the device's manual) and then search for the device with this command:

```

  sudo hidd --search

(If that command doesn't work, try this one:) 

  hcitool scan

```

Each device should have its own address in a aa:bb:cc:dd:ee:ff format.

[B]
If no devices are being shown and you are using Edgy Eft (6.10), you may try
[/B]

```

sudo hciconfig hci0 inqmode 0

```

[B]
Connect Devices for Current Session Only
[/B]

To temporarily connect to a device, use this command where 'aa:bb:cc:dd:ee:ff' is the address of the device you want to connect to:

```

sudo hidd --connect aa:bb:cc:dd:ee:ff

```

Your device should now be connected for the current session.

[B]
Connect Devices at Startup
[/B]

To connect the device at startup every time, use the following commands to edit the configuration file:

```

sudo cp /etc/default/bluetooth /etc/default/bluetooth_backup
 sudo gedit /etc/default/bluetooth

```

**We always want to backup the files we alter so we can save the system if this doesn't work.**

Look for the following line:

```

HIDD_ENABLED=0

```

And change it to:

```

HIDD_ENABLED=1

```

Next, look in the same file for a line similar to:

```

HIDD_OPTIONS="--master --server"

```

[B][I]You can leave the "--master" command or remove it, depending on the device. If you have problems with "--master", try removing it or vice versa.
[/I][/B]

Add additional "--connect" arguments for each device that you want connected at startup so that it looks like this:

```

HIDD_OPTIONS="--connect aa:bb:cc:dd:ee:ff --connect aa:bb:cc:dd:ee:ff --connect aa:bb:cc:dd:ee:ff --server"

```
[B]
Save the file.[/B]

Finally, add HIDP to /etc/modules:

```

echo hidp | sudo tee -a /etc/modules

```

Your Bluetooth devices should now be connected at startup.

************************************************************

Some folks will say that **I cut and pasted this whole thing from the web site**, *which I did*, but there wasn't a guide on the forums for some people to find, so I hope it becomes easy for some of you to get your bluetooth mouse and keyboard up and running.

I hope you have fun with your new devices. I know I do. This works for me and I use the same laptop every day at work and home. I use a Logitech V270 mouse. It is a basic mouse with two buttons and a scroll wheel. I don't game and only work with files and web surf, so nothing fancy.

This should work for every bluetooth enabled mouse and keyboard on the market today.

[COLOR="Red"]The website has more info for those with bluetooth enabled cell phones, PDA's and other devices that need to communicate with their bluetooth enabled laptop or desktop.
[/COLOR]

---

### Post by steveneddy on 2007-10-24
I have found that once the laptop/desktop is powered up and fully started (ie.-wireless connected, etc.) that I can turn on the mouse and it hooks up immediately with this set up, and stays hooked up all day long.

So far this has been a fool proof set up.

:popcorn:

After a few weeks of trying to determine when is the best time to turn on the Bluetooth mouse, I have found that if I turn on the mouse before i boot the machine and then log in normally, the mouse is connected as soon as I log on. I typically plug in the laptop and turn it on and then walk away to go get coffee or other morning chores in my office, so the machine is on for a few minutes at the log on prompt before I actually log on. 

Using this technique delivers the best results on my laptop.

---

### Post by popophobia on 2007-12-23
Sorry to get this thread up again. I've got my mouse working just the way I wanted it to. But then I installed Blueman 0.3 for browsing the phone, then, everytime I turn the mouse off and on again, I have to reconnect it manually, either through Blueman or through command line (turn the mouse to discovery mode, then hidd --connect).

I tried to remove Blueman but the problem persist. The file /etc/default/bluetooth does not seem to matter any more. Any idea how to get Blueman working peacefully with my mouse?

---

### Post by steveneddy on 2007-12-23
I had to uninstall the gnome-bluetooth stuff, uninstall blueman and then reinstall blueman.

Blueman will then install the gnome-bluetooth software that it needs.

I believe that is what worked for me.

---

### Post by steveneddy on 2008-02-28
I just found a thread with a hack that really helped my Bluetooth mouse issue.

With this fix, the mouse is connected at GDK, and I don't have to wait for a total log on.

[Here's the thread]("http://ubuntuforums.org/showthread.php?t=542776&page=3"), and start at post #25.

> 
Side buttons work perfectly fine over here with 10mins effort
Try the following and enjoy.. (I guess you guys only need the stuff in /etc/X11/xorg.conf, added the rest for sake of completeness)

1.[B] load modules
use modprobe and add to your /etc/modules[/B]

[COLOR="Red"]    * evdev
    * ushid[/COLOR]


2. [B]identify mouse
cat /proc/bus/input/devices[/B]
Code:

...
I: Bus=0005 Vendor=046d Product=b008 Version=0314
N: Name="Bluetooth Laser Travel Mouse"
P: Phys=<<your phys id>>
S: Sysfs=/class/input/input9
U: Uniq=<<your uniq id>>
H: Handlers=mouse3 event9
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=143
...

3. **modify touchpad to be a corepointer in /etc/X11/xorg.conf**
Code:

[COLOR="Red"]Section "InputDevice"
    Identifier "Synaptics Touchpad"
    Driver "synaptics"
    option "SendCoreEvents" "true"
    option "Device" "/dev/psaux
    option "Protocol" "auto-dev"
    option "HorizScrollDelta" "0"
    Option "CorePointer"
EndSection[/COLOR]

4. [B]enable HHID for bluetooth
In /etc/default/bluetooth set[/B]
Code:

HIDD_ENABLED=1
HIDD_OPTIONS="-i <<your uniq id>> --server"
[B]
add to /etc/bluetooth/hcid.conf:[/B]
Code:

[B][COLOR="Red"]    device <<your uniq id>> {
    name "Bluetooth Laser Travel Mouse";  <<-- **or the name of[COLOR="Blue"] your[/COLOR] mouse**
    }[/COLOR][/B]

5. Connect mouse
I'm on kde, thus as outlined before:

    * Right-click bluetooth applet
    * Properties
    * click input service
    * Add...
    * select your device (turn on and click connect-button underneath)
    * click connect


6. [B]add mouse to xorg.conf
Add new Input Device section[/B]
Code:

[B][COLOR="Red"]Section "InputDevice"
    Identifier "v470"  <<-- **or the name of[COLOR="Blue"] your[/COLOR] mouse**
    Driver "evdev"
    Option "Name" "Bluetooth Laser Travel Mouse"  <<-- **or the name of[COLOR="Blue"] your[/COLOR] mouse**
    Option "Dev Phys" "<<your phys id>>"
    Option "HWHEELRelativeAxisButtons" "7 6"
    Option "SendCoreEvents" "true"
EndSection
[/COLOR][/B]
**then add it to the Server Layout**
Code:

[B][COLOR="Red"]Section "ServerLayout"
    Identifier "Default Layout"
    screen 0 "Default Screen" 0 0
    InputDevice "Generic Keyboard"
    InputDevice "v470"  <<-- **or the name of[COLOR="Blue"] your[/COLOR] mouse**
    InputDevice "Synaptics Touchpad"
EndSection[/COLOR][/B]

7.** restart X**
Ctrl+Alt+Del

8. **verify buttons**
open konsole, then launch xev
In the window you should see button 6 for left scroll and button 7 events for right scrolls
It should work in Firefox and all other apps from here on


I use Gnome, but all worked great for me.

Firefox will go forward and back with the Logitech V470 mouse scroll wheel side buttons.

Mainly I added the modules and edited the xorg.conf with the red highlighted sections.

This is a great hack that works well with the addition of Blueman.

---

### Post by bhuthogg on 2008-05-20
[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)


works great for my keysonic kb with touchpad


thanks

---

### Post by steveneddy on 2008-06-01
> **bhuthogg said:**
> [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)


works great for my keysonic kb with touchpad


thanks

You are welcome.

---


---
title: "Karmic 9.10 Disable Touchpad Hotkey not working"
date: 2009-11-02
forum: Hardware
---

### Post by proxess on 2009-11-02
In Jaunty there used to be Hotkeys package, but there's non in Karmic. Ever since I upgraded, my Disable Touchpad Hotkey doesn't work, which makes typing very annoying because I can't disable the touchpad. Anyone have a solution?

Running 64bit on an Asus Z53Jr (F3Jr motherboard).

Edit: Bump!

---

### Post by kumoshk on 2009-11-02
I didn't know about the hotkey in Jaunty for this. Anyway, all I had to do in jaunty to toggle the touchpad was make a script like this:

```

#!/bin/bash

if [ $(gconftool-2 --get "/desktop/gnome/peripherals/mouse/touchpad_enabled") = true ]; then
	gconftool-2 --set "/desktop/gnome/peripherals/mouse/touchpad_enabled" --type boolean false
else
	gconftool-2 --set "/desktop/gnome/peripherals/mouse/touchpad_enabled" --type boolean true
fi

```

However, the touchpad_enabled variable no longer exists in Karmic. So, I just made a new variable with the same name (with gconf-editor)&#8212;this in and of itself won't do anything, by the way. Then, I made a script that looked like this:

```

#!/bin/bash

if [ $(gconftool-2 --get "/desktop/gnome/peripherals/mouse/touchpad_enabled") = true ]; then
	gconftool-2 --set "/desktop/gnome/peripherals/mouse/touchpad_enabled" --type boolean false
        xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0
else
	gconftool-2 --set "/desktop/gnome/peripherals/mouse/touchpad_enabled" --type boolean true
        xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
fi

```

So, you need xinput.

Also, you might need a different configuration on your computer. Here's how to find out what you need:
Type this:
```
xinput list | grep 'id='
```

Find your touchpad in the resulting list (its name, and its id number). The line with mine is at the end, and it looks like this:
```
"SynPS/2 Synaptics TouchPad"	id=8	[XExtensionPointer]
```

Then, edit the following line of code accordingly:
```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0
```

Replace "SynPS/2 Synaptics TouchPad" with the name of your device (if different). Replace 8 with your device's ID. The zero just means you're disabling it (change it to 1 to enable it).

Then create a shortcut to your script.

Anyway, I prefer this method to those that require me to download extra stuff and edit fdi files or xorg.conf, and then do synclient TouchpadOff=1 or such (none of those methods worked for me more than once per session anyway).

If you just want to disable buttons, rather than the ability to move the pointer around, try this:
```
xinput get-button-map "SynPS/2 Synaptics TouchPad"
```
That will get the mapping of your device.
My mapping is this:
```
1 2 3 4 5 6 7 8 9 10 11 12
```

Anyway, I believe the positions for 1 2 3 are the most important (for mouse button 1, 2, and 3). If you change a field to 0, it will disable it. So, if you just want to get rid of the middle-click so you don't accidentally paste data to the screen (I'm not sure how to do that on purpose on a touchpad, but I've done it a lot on accident) then do such as this:
```
xinput set-button-map "SynPS/2 Synaptics TouchPad" 1 0 3 4 5 6 7 8 9 10 11 12
```
I have a script that does this start with my laptop.

You can turn them all to 0 if you want to turn them all off:
```
xinput set-button-map "SynPS/2 Synaptics TouchPad" 0 0 0 0 0 0 0 0 0 0 0 0
```

---

### Post by proxess on 2009-11-03
Is all that much necessary? It makes no sense to be, seeing that it worked fine on Jaunty.

---

### Post by kumoshk on 2009-11-03
> **proxess said:**
> Is all that much necessary? It makes no sense to be, seeing that it worked fine on Jaunty.

Well, I'm guessing there are tons of solutions to this problem. However, the solution you had in Jaunty is one that I haven't heard of elsewhere. How did you do it, now?

I'm guessing they'll fix it one of these days&#8212;but you might end up waiting until the next release or so (I would file a bug report or something, if you're really concerned).

Anyway, with the solution I provided, you don't really need to make a variable in the gconf-editor (I just haven't worked with scripts much, yet&#8212;so I'm not sure how variables normally work through scripts like this). It's probably a lot simpler in that regard.

If you compare this method to the traditional alternatives, though, I personally think this one is a lot easier, as you just make a script and a keyboard shortcut (and it does actually work). If you want to try it and need help getting it working, let me know. I'd love to answer any questions&#8212;but then, you might just be seeking a more elegant situation regardless of how this works for you.

Anyway, let me know exactly how you did it in Jaunty. Maybe that will spark some ideas.

---

### Post by Dave_gb on 2009-11-03
I would be interested in an answer to this as well.

I am a newcomer to Ubuntu (9.10) and only converted from windows a week or so ago with Linux Mint. In Mint there is an option in the hardware preferences to disable the touchpad but I can not find one in 9.10.

Cheers

Dave

---

### Post by proxess on 2009-11-04
In Jaunty there was the Laptop-Hotkeys package, and adding into xorg.conf the following made the Synaptics touchpad work and switch off fine.

```
Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents"            "True"
        Option      "Device"                    "/dev/psaux"
        Option      "Protocol"                  "auto-dev"
        Option      "HorizEdgeScroll"           "0"
**[COLOR="Red"]        Option      "SHMConfig"                 "Yes"[/COLOR]**
EndSection

```

---

### Post by proxess on 2009-11-05
It seems that, being HAL replaced by devicekit, hotkey handling is now done on devicekit. Now there must be someone with this working, without a workaround, but right now devicekit seems more like a regression to HAL.

---

### Post by WilliamCampbellJr on 2009-11-06
[http://ubuntuforums.org/showthread.php?t=1313224&highlight=disable+touchpad](http://ubuntuforums.org/showthread.php?t=1313224&highlight=disable+touchpad)

Try this. (Scroll down to the #4 entry). It's simple, quick, and works perfectly as a toggle system. And, best of all, keeps its settings even after reboot.

Cheers.

---

### Post by proxess on 2009-11-08
Not exactly a solution, but a workaround. I guess it'll have to do for now.

---

### Post by XProflmfao on 2009-11-08
Thanks so much!!! You know what's weird? In 9.10, they removed the option of disabling the touchpad by going into System>Preferences>Mouse>Touchpad. In 9.04, there would be a checkbox as to whether or not you wanted the touchpad to be enabled or not. This seems to have been removed for 9.10. But anyways, thanks a lot!!!! :)

---

### Post by gsanders99 on 2009-11-15
I have an ASUS U80A laptop running Kubuntu 9.10.
I created my own hotkeys to disable the touchpad when I want to.

I was able to use the "xinput set-int-prop 9 'Device Enabled' 8 1" command as an argument in the "Input Actions" section of "System Settings".

Here's how:

I selected "System Settings", then clicked "Input Actions".

I don't think it matters where you put your new hotkey shortcuts, but I chose to add mine to the Examples group.  So, I activated the Examples group by checking the box beside it.

Then I highlighted Examples, and clicked the "Edit" button at the bottom.

Then I selected "New Group" and backspaced to clear the name field for the new group.

Next I named my group "Tpad_off", selected the "Trigger" tab to the right, and clicked on the button to the right of the "Shortcut" label.

I chose to use my Windows key plus F9.  This reads "Meta+F9" in the button now.  

Next I selected the "Action" tab and pasted in this line of text:

xinput set-int-prop 9 'Device Enabled' 8 0

NOTE: The number 9 in the line above is the device number I found by typing "xinput list" in a terminal window.  I was able to figure out which device was the touchpad and saw that its ID was 9.  Obviously, if I had used the wrong ID number, I'd be turning the wrong thing off.  So, don't blindly use my command line without checking the device number for your touchpad.

Next I clicked the "Apply" button, and was immediately able to turn the touchpad off using the new hotkey combination.

I then followed the same procedure to create another hotkey shortcut named "Tpad_on" using Windows key plus F10 (Meta+F10) and the "Action" command: 

xinput set-int-prop 9 'Device Enabled' 8 1

Now I can turn the touchpad on and off at will.  Finally!

---

### Post by WilliamCampbellJr on 2009-11-15
A couple of questions: where, exactly, do you find your System Settings dialogue? Also, do the changes you make in creating your hotkeys remain in effect after a reboot, or do you have to go through this routine every time you start your machine?

Thanks,
Bill Campbell

---

### Post by patrick49 on 2009-12-01
I found an easier solution (Asus A6/Karmic): I just unticked the box "disable touchpad when typing" in the mouse preferences (thumbnail touchpad) and my hotkey works!

---

### Post by hkphooey on 2009-12-03
I must say I'm getting a bit fed up of having to find a new solution to this problem every time I upgrade. Anyway, based on the previous postings I came up with this script.
```
if xinput list-props "SynPS/2 Synaptics TouchPad" | grep "Device Enabled" | grep 1
then 
	xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 0
else
	xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 8 1
fi
```

I saved this to a file called toggle-touchpad.sh and then assigned it to a key (in my case F6) using System > Preferences > Keyboard Shortcuts. All seems to work again ... until the next upgrade.

---

### Post by ww2 on 2009-12-17
That didn't work for me. I did it the following way:

Create a script that looks like this:
```
#!/bin/sh
if xinput list-props "SynPS/2 Synaptics TouchPad" | grep "Device Enabled" | grep 1
then 
	modprobe -r psmouse
else
	modprobe psmouse
fi
```

Save it in your home folder. Next, open a terminal and make the script executable with the following command (replace <user> with your username):
```
sudo chmod +x /home/<user>/.toogletouchpad.sh
```

Finally, create a launcher with the command below (replace <user> with your username):
```
gksudo /home/<user>/.toogletouchpad.sh
```

Running the launcher will enable or disable the touchpad. If you prefer you can associate the command above with a keyboard shortcut.

---

### Post by pjvaanan on 2009-12-30
It's just easier to use xinput to enable/disable touchpad. Works without sudoing.

```
#!/bin/sh
if xinput list-props "AlpsPS/2 ALPS DualPoint TouchPad" | grep "Device Enabled" | grep 1
then 
	xinput set-int-prop "AlpsPS/2 ALPS DualPoint TouchPad" "Device Enabled" 8 0	
else
	xinput set-int-prop "AlpsPS/2 ALPS DualPoint TouchPad" "Device Enabled" 8 1
fi
```

---

### Post by NightBlue on 2010-01-04
This is great! I now have a green and red button in my top panel to switch.
Too bad that the "Touchpad disable"-button on my keyboard doesn't work...

---

### Post by veko on 2010-01-06
Thanks [hkphooey]("http://ubuntuforums.org/member.php?u=462027") & others! You've saved me from so much trouble and discomfort!

I took liberty to tweak your script a bit: I added automatic touchpad id look up and simple sanity check to see whether an usb mouse is connected. If not, touchpad is not disabled.

These are both rather heuristic (read: kludges), but should work if there's only one touchpad device and external mouse is sensibly labelled as "usb mouse".

```

#!/bin/sh

DEVICE_ID=`xinput -list | grep -i touchpad | grep id= | sed 's/.*id=\([0-9]*\).*/\1/' `

if xinput -list-props $DEVICE_ID | grep "Device Enabled" | grep "1$" > /dev/null
then 
    if xinput -list | grep -i mouse | grep -i usb > /dev/null
    then
        xinput set-int-prop $DEVICE_ID "Device Enabled" 8 0
    fi
else
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 1
fi

```I did a keyboard shortcut for this script and also added a launcher to the panel (with tooltip to remind me about the shortcut).

As touchpad is now turned off only if the usb mouse is connected, you should be able to add this script to your startup applications too.

---

### Post by vintermann on 2010-04-24
> **ww2 said:**
> That didn't work for me. I did it the following way:

Create a script that looks like this:
```
#!/bin/sh
if xinput list-props "SynPS/2 Synaptics TouchPad" | grep "Device Enabled" | grep 1
then 
	modprobe -r psmouse
else
	modprobe psmouse
fi
```


Big thanks!! I was a bit surprised to see this work, as I thought my USB mouse would go to if I unloaded the driver. But it didn't. The easier way of using xinput to disable it just doesn't work for me (a bit of a mystery, really. "Device Enabled" is set to 0, and it says so plainly in xinput list-properties, yet the device continues to work. I can't disable the USB mouse this way either, so it's not just that I got a crappy touchpad, although I do)

---

### Post by Brandano on 2010-05-12
I did alter the script a little further, to work with bluetooth mice as well. Not a biggie, but I thought I'd share:
```

#!/bin/sh

DEVICE_ID=`xinput -list | grep -i touchpad | grep id= | sed 's/.*id=\([0-9]*\).*/\1/' `

if xinput -list-props $DEVICE_ID | grep "Device Enabled" | grep "1$" > /dev/null
then 
    if xinput -list | grep -i mouse | egrep -i 'usb|bluetooth' > /dev/null
    then
        xinput set-int-prop $DEVICE_ID "Device Enabled" 8 0
    fi
else
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 1
fi

```I called it toggle-touchpad, and placed it in /usr/local/sbin so that it would be available to all user profiles

---

### Post by RetiredAtLast on 2010-05-24
I went to Synaptic Package Manager and installed gsynaptics.  Then went to System>Preferences>Touchpad and I can check or uncheck to use the touchpad or not.  It has worked perfectly for me for several months.

I am using a Dell Vostro 1500 laptop.

---

### Post by adbask on 2010-10-13
sorry mistake

---


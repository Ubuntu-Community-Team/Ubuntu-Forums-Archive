---
title: "Asus UX32LN screen brightness keys not working"
date: 2014-07-22
forum: Hardware
---

### Post by akos.maroy on 2014-07-22
Hi,

I've just installed 14.04 unto an Asus UX32LN: [http://www.asus.com/Notebooks_Ultrabooks/UX32LN/specifications/](http://www.asus.com/Notebooks_Ultrabooks/UX32LN/specifications/)  , and went through this page: [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

all seems to work fine, but the screen brightness function keys don't work. everything else does, like even the keyboard backlight keys. I can set the screen brightness from the preferences window, but that is kind of awkward

I wonder if anyone else has experienced this, and if at least one can have a work-around with some custom scripts & key bindings?


Akos

---

### Post by jeremy31 on 2014-07-22
> **akos.maroy said:**
> Hi,

I've just installed 14.04 unto an Asus UX32LN: [http://www.asus.com/Notebooks_Ultrabooks/UX32LN/specifications/](http://www.asus.com/Notebooks_Ultrabooks/UX32LN/specifications/)  , and went through this page: [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

all seems to work fine, but the screen brightness function keys don't work. everything else does, like even the keyboard backlight keys. I can set the screen brightness from the preferences window, but that is kind of awkward

I wonder if anyone else has experienced this, and if at least one can have a work-around with some custom scripts & key bindings?


Akos

Lets try this in terminal, please paste the results back using the code tags, the "#" above the reply area
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/brightness; done
```

Then we can see if another command will change the brightness

---

### Post by akos.maroy on 2014-07-22
> **jeremy31 said:**
> Lets try this in terminal, please paste the results back using the code tags, the "#" above the reply area
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/brightness; done
```

Then we can see if another command will change the brightness

here is the output:


```
# for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/brightness; done
/sys/class/backlight/acpi_video0
10
10
/sys/class/backlight/acpi_video1
10
8
/sys/class/backlight/intel_backlight
825
495

```

---

### Post by jeremy31 on 2014-07-22
> **akos.maroy said:**
> here is the output:


```
# for interface in /sys/class/backlight/*; do echo $interface; cat $interface/max_brightness; cat $interface/brightness; done
/sys/class/backlight/acpi_video0
10
10
/sys/class/backlight/acpi_video1
10
8
/sys/class/backlight/intel_backlight
825
495

```
Try ```
xev
``` and try the backlight keys, any response?  Or even ```
acpi_listen
``` and try the same keys again..anything?

And if those don't work, we can check for a work around
```
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
Did the brightness change? If not try the next one
```
echo 4 | sudo tee /sys/class/backlight/acpi_video1/brightness
```
If the brightness didn't change, then this is the last try
```
echo 300 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

---

### Post by akos.maroy on 2014-07-23
> **jeremy31 said:**
> Try ```
xev
``` and try the backlight keys, any response?  Or even ```
acpi_listen
``` and try the same keys again..anything?

no response for these, although both respond to the keyboard backlight setting keys

> **jeremy31 said:**
> And if those don't work, we can check for a work around
```
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
Did the brightness change? If not try the next one
```
echo 4 | sudo tee /sys/class/backlight/acpi_video1/brightness
```

these work

> **jeremy31 said:**
> If the brightness didn't change, then this is the last try
```
echo 300 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

this works as well

so it seems the key events are lost somewhere :(

---

### Post by jeremy31 on 2014-07-23
Please post the result of ```
cat /proc/cmdline
```

---

### Post by akos.maroy on 2014-07-23
> **jeremy31 said:**
> Please post the result of ```
cat /proc/cmdline
```

```
$ cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=86be9a9c-56ef-4c51-8f0c-87925477e1fc ro quiet splash "acpi_osi=!Windows 2012" pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1 vt.handoff=7

```

---

### Post by jeremy31 on 2014-07-23
> **akos.maroy said:**
> ```
$ cat /proc/cmdline 
BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic.efi.signed root=UUID=86be9a9c-56ef-4c51-8f0c-87925477e1fc ro quiet splash "acpi_osi=!Windows 2012" pcie_aspm=force drm.vblankoffdelay=1 i915.semaphores=1 vt.handoff=7

```
The quotes are wrong in your /etc/default/grub it should look like acpi_osi="!Windows 2012" from cat /proc/cmdline

There is a workaround using scripts and custom keybindings

I will post the scripts when I get home

---

### Post by miguel-carcamo on 2014-07-23
I have the same problem but with the ASUS x450LN, if you get something let me know :), and I do if I can get something too.

---

### Post by varunendra on 2014-07-23
> **akos.maroy said:**
> no response for these, although both respond to the keyboard backlight setting keys
....<snip>....
so it seems the key events are lost somewhere :(

As far as I have experienced, no "Fn+" key combination can be recorded using 'xev' or 'acpi_listen' or any other tool I have ever heard of. At least not on my Asus X54C, or an HP Pavillion Dv6 or a Lenovo I experimented on. Even though the brightness keys (or any other 'Fn+' key combos for that matter) work perfectly with Ubuntu on all those models.

So unless someone can confirm that they DO get responses when pressing 'Fn+' key combos, I believe the 'xev' or 'acpi_listen' or any other similar tests are completely useless when we are talking about "Fn+" key combos, and not regular keys that can be found on a generic keyboard.

I don't know how these special key combos are handled (I'm not even sure whether they are handled by the kernel or directly via hardware), but I do know by experience that no response on tools like 'acpi_listen' doesn't mean the event was not generated or sensed.

However, since manually defining the brightness value is working, the script+hot-key assignment formula would work equally good as with "Fn+" key combos, only you can't make use of the "Fn" key, it simply can't be captured by any hot-key assignment program I know of, just like it can't be detected by the key event detection tools.


**@ jeremy31, akos.maroy**

I had written a script for the same purpose once, and successfully used it with 'xbindkeys' on my laptop here. Hope it may be able to save you some time. Here's the script -
```
#!/bin/bash

# Script to control brightness

INCR=1
MIN=0
MAX=10
CURR=`cat /sys/class/backlight/acpi_video0/brightness`

if [ "$1" = "BrUP" ]; then
	if [ $CURR -lt $MAX ]; then
		let CURR=CURR+INCR
		echo $CURR | sudo tee /sys/class/backlight/acpi_video0/brightness
	fi

elif [ "$1" = "BrDN" ]; then
	if [ $CURR -gt $MIN ]; then
		let CURR=CURR-INCR
		echo $CURR | sudo tee /sys/class/backlight/acpi_video0/brightness
	fi
fi
```

Suppose this script is saved in /usr/bin with the name "**brightness_ctrl.sh**" and made executable, then using "xbindkeys", two hotkeys (or hot key combinations) can be assigned to issue commands "**brightness_ctrl.sh BrUP**" and "**brightness_ctrl.sh BrDN**" to increase or decrease the brightness just like the 'Fn+' key combo would have done.

Here's the detailed steps to install and use xbindkeys for the purpose (adapted from [this post]("http://ubuntuforums.org/showthread.php?t=2181558&p=12819607#post12819607")) :

[indent]**1)** Install ***xbindkeys-config*** (a GUI frontend to xbindkeys - the program that captures and binds hotkeys with commands) -
```
sudo apt-get install xbindkeys-config
```

**2)** Create a default config file for it (else it would crash on key capture step) -
```
xbindkeys --defaults > ~/.xbindkeysrc
```

**3)** Run the program from terminal or "Alt+F2" (because it does not create a launcher in Unity dash) -
```
xbindkeys-config
```
let the terminal running in the background..
In the GUI box that opens, 3 example shortcuts are already present. You may leave them.

**4)** Click on "**[COLOR="#0000CD"]New[/COLOR]**" button at the bottom of the GUI.

**5)** In the right hand pane of the GUI, fill in a suitable name in the "**[COLOR="#0000CD"]Name[/COLOR]**" field, e.g. "**Brightness Up**"

**6)** Click on "**[COLOR="#0000CD"]Get Key[/COLOR]**" button. This will open a tiny blank box doing nothing but waiting for your input.

**7)** Press the desired key (or key combination) that you want for increasing brightness. For example, "F3" key (as it remains mostly unused). The tiny box will disappear and the key will be recorded.

**8)** In the "**[COLOR="#0000CD"]Action[/COLOR]**" field, type this -
```
/bin/bash /usr/bin/brightness_ctrl BrUP
```

**9)** Click on "**[COLOR="#0000CD"]Apply[/COLOR]**" button and test the hotkey to see if it works as expected.

**10)** Click on "**[COLOR="#0000CD"]Save & Apply & Exit[/COLOR]**" to save the new hotkey to the default file and exit.

**11)** Repeat steps 4 to 10 to assign another hot key to decrease the brightness, changing the name to "Brightness Down" in step 5, a different key (to decrease brightness) in step 7 and command to "/bin/bash /usr/bin/brightness_ctrl **BrDN**" in step 8.[/indent]

If I remember correctly, the 'xbindkeys' process runs in the background with root privileges, so the user doesn't need to provide sudo password to let the script run. But even if it is required, there are ways to bypass that as well (by adding a "NOPASSWD" rule for the script in "/etc/sudoers" file).


**PS:**
@jeremy31,
A bit shorter command to capture the brightness values is -
```
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```
same command you used, just a bit shorter, taking advantage of bash expansion. :)

---

### Post by jeremy31 on 2014-07-23
> **varunendra said:**
> 


**PS:**
@jeremy31,
A bit shorter command to capture the brightness values is -
```
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```
same command you used, just a bit shorter, taking advantage of bash expansion. :)

I can remember the other command for brightness values.;)

---

### Post by varunendra on 2014-07-24
Yup, it is always a matter of personal choice. Thought a scripting guy will find it easier and more interesting to grab something new from bash fundamentals, and start using it. :)

But then I have another tip for you - one shouldn't quote entire post (especially if it is a huge one) if they are responding to only some small part of it.
(now this one you must take.. :p)

---

### Post by akos.maroy on 2014-07-31
thanks for the input. I created the script above, and did the key bindings, but maybe xbindkeys is running with my user, so I guess this is why it doesn't do anything. after installing xbindkeys, would it always run as root in the background?

---

### Post by varunendra on 2014-08-01
> **akos.maroy said:**
> after installing xbindkeys, would it always run as root in the background?

Just checked on my system, appears to be running with user 'varun', so maybe not. But does the script work if you run it directly? That is, in a terminal -
```
brightness_ctrl.sh BrUP
```(or BrDN. It should ask for sudo password for the 'tee' command)

If yes, we can add a NOPASSWD rule in the /etc/sudoers file for the script, which should work then.

---


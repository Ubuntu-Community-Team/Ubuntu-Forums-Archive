---
title: "Brightness fn keys not working on an Acer Aspire One"
date: 2012-08-14
forum: Hardware
---

### Post by Dea ex Machina on 2012-08-14
Newbie ubuntu user here, just installed 12.04 on my new netbook a week ago. Been troubleshooting the wifi all week, and now that that's finally working it's time to move to the next most pressing issue; namely, I can't adjust the screen brightness. It's at maximum all the time, and the function keys (fn left and right arrows) do nothing. 

I've googled the problem, and tried the fix where you go into grub and replace the lines 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

with

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```

but so far, that hasn't worked. Can anyone tell me a fix or a workaround? This netbook's battery life is going to be next to zilch if I can't convince it to stop blazing like the sun! 

It's a Japanese Acer Aspire One D270-F61C/KF, any help appreciated.

---

### Post by Marric on 2012-08-14
Just to make sure, did you use this command in Terminal?
```
sudo update-grub
```

Found this on kubuntu wiki
[https://wiki.kubuntu.org/Kernel/Debugging/Backlight](https://wiki.kubuntu.org/Kernel/Debugging/Backlight)

---

### Post by Toz on 2012-08-14
Looks like someone has already reported this as a bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1005495]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1005495"). Feel free to add your name to the affected list.

As a temporary workaround to lower the  brightness on the laptop, try the following command:
```
sudo setpci -s "00:02.0" F4.B=XX
```
...where XX is a percentage value between 0 and 99. So, for example:
```
sudo setpci -s "00:02.0" F4.B=35
```
...should set brightness to 35%.

---

### Post by Dea ex Machina on 2012-08-15
I did update the grub, but it hasn't helped.

Doing the terminal command worked (Thank you!), and I've pasted the command into a txt on the desktop so I can find and copy it easily, but it would be nice if I had a better method of doing it on the fly than opening terminal every time...

---

### Post by Toz on 2012-08-15
> **Dea ex Machina said:**
> Doing the terminal command worked (Thank you!), and I've pasted the command into a txt on the desktop so I can find and copy it easily, but it would be nice if I had a better method of doing it on the fly than opening terminal every time...

Have a look at this post ([http://ubuntuforums.org/showpost.php?p=12161155&postcount=16]("http://ubuntuforums.org/showpost.php?p=12161155&postcount=16")) for setting up a script to manage brightness using setpci. As per this post, you can map the script to the brightness keys (or any other key combination) to give you some quick-access control to managing brightness.

---

### Post by Dea ex Machina on 2012-08-15
The script seems to be working, but terminal keeps asking for my password in order to run it. I assume that means I must have done something wrong in visudo. Can I get more detailed instructions about that step?

---

### Post by Toz on 2012-08-15
> **Dea ex Machina said:**
> The script seems to be working, but terminal keeps asking for my password in order to run it. I assume that means I must have done something wrong in visudo. Can I get more detailed instructions about that step?

Can you copy/paste back the line you added via sudo visudo and the results of:
```
whoami
```

The first word in the sudoers entry should be exactly the same as your userid.

---

### Post by ramsharan065 on 2012-08-15
> **Dea ex Machina said:**
> The script seems to be working, but terminal keeps asking for my password in order to run it. I assume that means I must have done something wrong in visudo. Can I get more detailed instructions about that step?

[LIST=1]
[*]You can use "**xbacklight**" command which **does not need sudo **i.e. any user can use it to **change brightness**.
[*]First install "**xbacklight**" using **ubuntu software centre** or using command sudo apt-get install xbacklight (prefer ubuntu software centre)
[*]Then you can use command: **xbacklight -set (0 to 100)** to set brightness.
[*]Use command: **info xbacklight**     to know more about xbacklight 
[/LIST]

---

### Post by Dea ex Machina on 2012-08-16
Ah! After looking at whoami, I realized I capitalized my username when I shouldn't have. All right, br up and br down are now working without the su password. (though br down never seems to go below a certain brightness level?)

Okay, how do I keybind them? Fn left arrow for brighter and Fn right arrow for dimmer is how the system is supposed to work, I'd like to use that, if I can? Never keybound anything before, so if you could take me through step by step, I'd appreciate it.

---

### Post by Toz on 2012-08-16
> **Dea ex Machina said:**
> Ah! After looking at whoami, I realized I capitalized my username when I shouldn't have. All right, br up and br down are now working without the su password. (though br down never seems to go below a certain brightness level?)
Have a look at the following part of the script:
```
case $NEW in
	0) VAL=45 ;;
	1) VAL=60 ;;
	2) VAL=75 ;;
	3) VAL=90 ;;
	4) VAL=99 ;;
esac
```
These are the brightness values. The lowest value is 45. You might want to change these values to something like:
```
case $NEW in
	0) VAL=20 ;;
	1) VAL=40 ;;
	2) VAL=60 ;;
	3) VAL=80 ;;
	4) VAL=99 ;;
esac
```
...to get more of a range. I can also adjust the script if you want more steps of brightness (right now there are only 5), just let me know.

> Okay, how do I keybind them? Fn left arrow for brighter and Fn right arrow for dimmer is how the system is supposed to work, I'd like to use that, if I can? Never keybound anything before, so if you could take me through step by step, I'd appreciate it.
I fired up ubuntu in a VM to check (I use Xubuntu) and it looks like you can go to Settings -> Keyboard -> Shortcuts tab to create shortcuts. Click on the +, and add a name and the command. This will create the shortcut entry. Now click on the word "Disabled" and press the keyboard shortcut you want to use. 

The only issue you might run into is that your keyboard combination may not be recognized by Ubuntu. In a terminal window, enter the following command:
```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
```
...a box will popup on the screen. Press the keyboard combination, and if something displays in the terminal that you entered the command in, then the keyboard shortcut is being recognized and you can use it. If not, you'll have to select another combination that is recognized.

---

### Post by Dea ex Machina on 2012-08-16
All right, I tested it out. It looks like Fn won't work for keybinding, so I bound it to Ctrl Left and Ctrl Right instead for now, and that seems to work all right for the moment. And the second set of brightness values, going down to twenty, should do me just fine. Thank you so much!

---


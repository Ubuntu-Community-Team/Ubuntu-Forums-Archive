---
title: "Unable to change brightness in Lenovo B570 laptop"
date: 2011-08-18
forum: Hardware
---

### Post by BlaXpirit on 2011-08-18
Brightness adjustment keys [Fn] + [&#8657;]/[&#8659;] have no effect (although they are recognized by the environment), and I can't change the brightness using GUI tools as well. This seems like a problem in Linux itself, not the desktop environment.

I can change the brightness in Windows OS, so it's not some kind of hardware fault.

Details:
[INDENT]Lenovo B570 (Model Name: 20093)
Integrated Intel HD graphics card
Kubuntu 11.04 (Linux 2.6.38-10-generic, KDE 4.7.0), everything up to date
No proprietary graphics drivers (only Wi-Fi one)[/INDENT]

What I've tried:

[LIST][*] Edit [FONT="Courier New"][COLOR="Navy"]/etc/default/grub[/COLOR][/FONT]&#8614;[FONT="Courier New"][COLOR="Navy"]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][/FONT]: [FONT="Courier New"][COLOR="Navy"]acpi_osi=Linux[/COLOR][/FONT], [FONT="Courier New"][COLOR="Navy"]acpi_backlight=vendor[/COLOR][/FONT], [FONT="Courier New"][COLOR="Navy"]nomodeset[/COLOR][/FONT]. And yes, I did [FONT="Courier New"][COLOR="Navy"]update-grub[/COLOR][/FONT]
[*] Edit [FONT="Courier New"][COLOR="Navy"]/etc/X11/xorg.conf[/COLOR][/FONT] (no such file, even after [FONT="Courier New"][COLOR="Navy"]sudo dpkg-reconfigure xserver-xorg[/COLOR][/FONT])
[*] Edit [FONT="Courier New"][COLOR="Navy"]/proc/acpi/video/VGA/LCD/brightness[/COLOR][/FONT] (no such file)
[*] [FONT="Courier New"][COLOR="Navy"]sudo setpci -s 00:02.0 F4.B=##[/COLOR][/FONT] (no effect)
[*] [FONT="Courier New"][COLOR="Navy"]xbacklight -set ##[/COLOR][/FONT] ("[FONT="Courier New"][COLOR="Navy"]No outputs have backlight property[/COLOR][/FONT]")
[*] [/LIST]
How can I fix this issue?
_________________________________________________

[SIZE="3"]This has been fixed in Ubuntu 11.10![/SIZE]
[[COLOR="Blue"]Solution for older distributions[/COLOR]](http://askubuntu.com/questions/57236/unable-to-change-brightness-in-a-lenovo-laptop/58088#58088)

---

### Post by Toz on 2011-08-19
I notice you've posted on a couple of other forums and unfortunately none of the usual solutions work. I would add one more possible thing you could try since you have an integrated intel video card - Kamal's custom kernel. (See: [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight")). I believe he is a kernel developer working on, among other things, improving support for intel-based video chips.

---

### Post by BlaXpirit on 2011-08-19
[QUOTE=Kamal]```
lsmod | grep ^i915
```If no "i915" line appears, then this PPA will not be useful on your system.[/QUOTE]
No line appeared :(

---

### Post by Toz on 2011-08-19
Then it looks like it won't work. Too bad. Out of curiosity, can you post back the full listing of 
```
lsmod
``` and
```
lspci -vnn | grep VGA -A 10
```
and 
```
ls /sys/class/backlight
```

Also, are you currently booting with any kernel parameters?
```
dmesg | grep "Kernel command line"
```

---

### Post by BlaXpirit on 2011-08-19
WAIT A MINUTE!!!

Talk about stupidity.
I tried that line on the desktop PC, not the laptop.

On laptop there actually was some output!

---

### Post by Toz on 2011-08-19
Here's something else to try. 

If
```
xrandr --prop | grep BACKLIGHT
```
returns something, try:
```
xrandr --output LVDS --set BACKLIGHT <value>
```
where <value> is one of the numbers in the range.

---

### Post by BlaXpirit on 2011-08-19
So I've installed the custom kernel. Brightness still doesn't work.

[**Here**](http://pastebin.com/fRPRu9wY) are the listings you asked for. (After installing the kernel)

[COLOR="Navy"][FONT="Courier New"]xrandr --prop | grep BACKLIGHT[/FONT][/COLOR] yields no output.

---

### Post by Toz on 2011-08-19
Did you try the new kernel with the **acpi_backlight=vendor** kernel parameter? Note: don't replace the work "vendor" with your vendor name - it should just say vendor.

---

### Post by Toz on 2011-08-19
And what does the following show:
```
cat /sys/class/backlight/intel_backlight/brightness
```
```
cat /sys/class/backlight/intel_backlight/max_brightness
```
```
cat /sys/class/backlight/intel_backlight/actual_brightness
```

Then try something like:
```
echo 5 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

If still nothing, change back to the original kernel and what does the following show:
```
ls /sys/class/backlight
```

---

### Post by BlaXpirit on 2011-08-20
> **Toz said:**
> Did you try the new kernel with the **acpi_backlight=vendor** kernel parameter?

The kernel's page says the parameter isn't needed.

> **Toz said:**
> [FONT="Courier New"][COLOR="Navy"]echo 5 | sudo tee /sys/class/backlight/intel_backlight/brightness[/COLOR][/FONT]

[SIZE="3"]THIS WORKED![/SIZE] The screen became entirely black, because, as I later found out, [FONT="Courier New"][COLOR="Navy"]max_brightness[/COLOR][/FONT] is **976**! A reboot saved me from the black screen, so, unfortunately, the brightness setting is reset after reboots.

By the way, without the kernel, there's nothing in [FONT="Courier New"][COLOR="Navy"]/sys/class/backlight[/COLOR][/FONT], even with [FONT="Courier New"][COLOR="Navy"]acpi_backlight=vendor[/COLOR][/FONT]

Now, how can I make some integration with the system? Particularly, KDE desktop.
[FONT="Courier New"][COLOR="Navy"]xbacklight[/COLOR][/FONT] probably tries to use the same thing (is it called *interface*?) as the system, so it doesn't work.
If nothing can be done, I could make some scripts to read and write that [FONT="Courier New"][COLOR="Navy"]brightness[/COLOR][/FONT] file, but it would need [FONT="Courier New"][COLOR="Navy"]sudo[/COLOR][/FONT] all the time :?

---

### Post by Toz on 2011-08-20
Good news! Not a solution, but a potential workaround. 

I came across a report where someone with a lenovo system still needed to specify acpi_backlight=vendor. It might be worth a shot just to see.

Otherwise, according to that website, KDE integration hasn't been developed yet, so you may have to write your own scripts for now. I would suggest adding to **/etc/rc.local** (before the last "exit 0" statement) the following:
```
chmod 777 /sys/class/backlight/intel_backlight/brightness
echo some_value > /sys/class/backlight/intel_backlight/brightness
exit 0
```

This would set the rights to this file so that everyone can write to it (meaning no need for sudo) and the second command would set a default brightness value that you would be comfortable with.

You can then use a script like this:
```
#!/bin/bash
# /usr/local/bin/brightness
# wrapper script to change brightness values
# make script executable

# constants - edit as required
UPPER=100
LOWER=0
INCREMENT=10
DECREMENT=10

# current value
CURRENT=`cat /sys/class/backlight/intel_backlight/brightness`
NEW=$CURRENT

case $1 in
	up)
		if [ $(($CURRENT+$INCREMENT)) -le $UPPER ]; then
			NEW=$(($CURRENT+$INCREMENT))
		fi
	;;
	down)
		if [ $(($CURRENT-$DECREMENT)) -ge $LOWER ]; then
			NEW=$(($CURRENT-$DECREMENT))
		fi
	;;
	*)
	;;
esac

# set the new brightness value 
echo $NEW > /sys/class/backlight/intel_backlight/brightness

exit 0
```
...to change the brightness (make sure you adjust the values of UPPER, LOWER, INCREMENT, DECREMENT so they work for you) and run **brightness up** or **brightness down** when you want to change the brightness. You can also try to map your current FN function keys to this script.

---

### Post by BlaXpirit on 2011-08-20
Thank you very much! This [FONT="Courier New"][COLOR="navy"]chmod[/COLOR][/FONT] in [FONT="Courier New"][COLOR="Navy"]/etc/rc.local[/COLOR][/FONT] is just what I need! (isn't [FONT="Courier New"][COLOR="navy"]chmod 666[/color][/font] better?)

But I think I'll write a bit different script - to save the brightness value between sessions, not make a default one. Now that it's possible to write to the brightness file, I'm free to use Python for this.

Thanks again!

---

### Post by Toz on 2011-08-20
> **BlaXpirit said:**
> Thank you very much! This [FONT="Courier New"][COLOR="navy"]chmod[/COLOR][/FONT] in [FONT="Courier New"][COLOR="Navy"]/etc/rc.local[/COLOR][/FONT] is just what I need! (isn't [FONT="Courier New"][COLOR="navy"]chmod 666[/color][/font] better?)
Ah yes, no need to make it executable.

> But I think I'll write a bit different script - to save the brightness value between sessions, not make a default one. Now that it's possible to write to the brightness file, I'm free to use Python for this.
If you don't mind sharing, I'd like to have a look at your completed script. Maybe make use of it elsewhere.

> Thanks again!
No worries.

---

### Post by BlaXpirit on 2011-08-20
So, [**[COLOR="Blue"]here[/COLOR]**](http://ideone.com/yPlo5) is the script.

[LIST]
[*]Put `[FONT="Courier New"][COLOR="Navy"]brightness restore[/COLOR][/FONT]` to [COLOR="DimGray"]**/etc/rc.local**[/COLOR]
[*]Map `[FONT="Courier New"][COLOR="Navy"]brightness inc[/COLOR][/FONT]` and `[FONT="Courier New"][COLOR="Navy"]brightness dec[/COLOR][/FONT]` to some hotkeys.
[/LIST]

---

### Post by Toz on 2011-08-20
Thats a nice bit of coding there.
Thanks.

---

### Post by jhenkins on 2011-10-08
> **BlaXpirit said:**
> So, [**[COLOR="Blue"]here[/COLOR]**](http://ideone.com/yPlo5) is the script.

[LIST]
[*]Put `[FONT="Courier New"][COLOR="Navy"]brightness restore[/COLOR][/FONT]` to [COLOR="DimGray"]**/etc/rc.local**[/COLOR]
[*]Map `[FONT="Courier New"][COLOR="Navy"]brightness inc[/COLOR][/FONT]` and `[FONT="Courier New"][COLOR="Navy"]brightness dec[/COLOR][/FONT]` to some hotkeys.
[/LIST]

Awesome, thanks! This works a treat! I really enjoy the restore function, very thoughtful to put that in.

Where do I vote??? :-)

PS: For in case somebody else stumbles across this thread, I have noticed that the official bug in the KDE4 tracker has been updated with a preliminary patch on the 30th of September 2011, so now it's only a matter of time before KDE4 has full support for this new backlight device. If it interest you, the bug URL is here:

[http://bugs.kde.org/show_bug.cgi?id=271467](http://bugs.kde.org/show_bug.cgi?id=271467)


Regards,
jhenkins

---

### Post by BlaXpirit on 2011-10-08
> **jhenkins said:**
> Where do I vote??? :-)Well, you could vote [[COLOR="Blue"]here[/COLOR]](http://askubuntu.com/questions/57236/unable-to-change-brightness-in-a-lenovo-laptop/58088#58088).

> **jhenkins said:**
> ...it's only a matter of time before KDE4 has full support for this new backlight device.Good to hear!

---

### Post by piccobello on 2011-10-08
Hi,

I have used a similar workaround, however in my case (Panasonic CF-T5) the hotkeys used to work out of the box in Kubuntu Lucid. Brightness keys stopped working in Kubuntu Natty, while other hotkeys (volume, sleep/hybernate,..) still work.
I filed a bug report here:
[https://bugs.kde.org/show_bug.cgi?id=283471](https://bugs.kde.org/show_bug.cgi?id=283471)

---

### Post by BlaXpirit on 2011-10-13
This has been fixed in Ubuntu 11.10!

---


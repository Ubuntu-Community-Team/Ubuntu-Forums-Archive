---
title: "How do I change screen brightness from a terminal?"
date: 2011-05-21
forum: Hardware
---

### Post by belltown on 2011-05-21
I'm running Ubuntu 11.04 with the Gnome Classic (No effects) display manager. My laptop's brightness keys work. However, when I boot or resume from suspend when using the integrated Intel graphics card the display brightness is turned all the way down, and I have to turn up the brightness using the brightness function keys so I that can see the display. I'd like to automate this by putting a terminal command in a script so I can automatically turn up the screen brightness when the system boots.

I've tried the following commands with no success:

```
echo 9>/sys/class/backlight/acpi_video0/brightness
```What ever I echo in the brightness file has no effect on the screen brightness, and nothing changes in the /sys/class/backlight/acpi_video0/brightness or actual_brightness files. The contents of these files do change, however, if I change the brightness using the keyboard function keys.

```
setpci -s 00:02.0 F4.B=10
```Some posts have suggested this command might work, but in my case it has no effect. The contents of the F4 register remain at 00, even if I change the screen brightness with the function keys.

```
xbacklight -set 90
```Using this command I can change the value of xbacklight (i.e. xbacklight -get shows the new value), but the screen brightness does not change. However, if I change the screen brightness using the keyboard function keys then the value of xbacklight -get shows the new value.

```
acpi_backlight=vendor
```I've tried putting this command on the linux command line when I boot. Even with this parameter I'm still unable to change the screen brightness from the terminal. This parameter also disables the keyboard brightness function keys.

Any suggestions of anything else I could try to change the screen brightness from a terminal?

---

### Post by Bazookan on 2012-04-19
Hey,

I had a similar problem and did some googling. What I am going to suggest is not a totally automatic setting but I hope it may help u....
Open the terminal and type the following:
$sudo apt-get install acpi
    Install acpi in ur comp first. 

$find /proc/acpi/video -name 'brightness'
    This will tell u what all drivers control the brightness.
When I did on my comp, it gave me 5 options which went like this

/proc/acpi/video/GFX0/DD05/brightness
/proc/acpi/video/GFX0/DD04/brightness
/proc/acpi/video/GFX0/DD03/brightness
/proc/acpi/video/GFX0/DD02/brightness
/proc/acpi/video/GFX0/DD01/brightness

After this, I had to do some trial and error and found out that the driver actually involved was DD02.

What I did was..
1.$sudo -s
     This took me root status.

2.$ cat /proc/acpi/video/GFX0/DD02/brightness 
It gave this as output:
levels:  0 10 20 30 40 50 60 70 80 90 100
current: 50
     The above command gave the allowed levels and current level.

3.$echo 70 > /proc/acpi/video/GFX0/DD02/brightness
Basically, we set our brightness level as 70.

You may have to play around to figure out which one controls ur brightness levels. I am unable to give u a single command to do all this coz just typing
$sudo echo 70 > /proc/acpi/video/GFX0/DD02/brightness
doesn't seem to work. :(

Anyways, the above gives u a "terminal" way of handling the brightness issue...:)

---


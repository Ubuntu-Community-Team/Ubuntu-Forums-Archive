---
title: "Backlight brightness control not working in notebook LG R590"
date: 2010-07-08
forum: Hardware
---

### Post by andfer on 2010-07-08
[COLOR=#000000][FONT=Sans Serif]Hello,

I am using ubuntu 10.04 LTS with the last updates (July-08-2010), but the buttons that control the brightness are not working. I tested with the proprietary nvidia drivers and without.
When I use the 'FN' key + arrow up (or down) it appears an image of the brightness control but the brightness don't change. It stays at the maximum.
The notebook is an LG R590, the graphic card is an Nvidia GT 335M.
Probably is a software problem as the control works in Windows.
I also tried to control the brightness in Ubuntu using the Power Management Preferences -> Set display brightness to.

Another tip that not work:
echo -n 10 > /proc/acpi/video/VGA/LCD/brightness
I tried other values than 10 but no success.

I also make a search in this forum and with Google and don't found any solution.

If someone needs more information or want that I try another command please tell me.[/FONT][/COLOR]

---

### Post by hayalci on 2010-08-03
Hi,

I have a LG R580 notebook, with Nvidia GT 130M graphics card.

I also cannot change the brightness. Here are the things I tried, they may help you.

In [this thread]("http://ubuntuforums.org/showthread.php?t=1408321&page=3"), I found a suggestion for adding the following in the device section of Xorg file
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
This was not a solution, neither Fn+brightness keys work, nor the KDE power management interface.

In [this thread]("http://forums.gentoo.org/viewtopic-t-818740-highlight-brightness.html") and some other places, addin the following boot option to grub was suggested.This did not solve the problem either.
```
acpi_osi="Linux" 
```

Finally, [This thread]("http://ubuntuforums.org/showthread.php?p=7810590") suggested another grub option.
```
acpi_backlight=vendor
```
But after this change the brightness file stopped showing anything 
```
cat /proc/acpi/video/VGA/LCD/brightness
<not supported>
```
Previously, it showed available brightness levels and current level. But setting the level through the file was not working. Also the nvidia driver began complaining.
```
(WW) Aug 03 23:56:56 NVIDIA(0): ACPI: Error: Unable to find the brightness file path under
(WW) Aug 03 23:56:56 NVIDIA(0):     /proc/acpi/video. The NVIDIA X driver will not be able to
(WW) Aug 03 23:56:56 NVIDIA(0):     respond to ACPI brightness change hotkey events.
```

I'm still looking for possible solutions.

---

### Post by andfer on 2010-08-06
Hi,

Thanks Hayalci for all these suggestions, I have the same results as you: still not working.
I am contacting Nvidia and LG about the brightness issues (without any useful answer until now). If I get any news I put here.

---

### Post by utilitytrack on 2010-08-06
to **andfer** and **hayalci**

try change brightness over [FONT="Courier New"]/sys[/FONT] interface:

```
# echo 0 > /sys/class/backlight/acpi_video0/brightness
```

---

### Post by andfer on 2010-08-06
> **utilitytrack said:**
> to **andfer** and **hayalci**

try change brightness over [FONT=Courier New]/sys[/FONT] interface:

```
# echo 0 > /sys/class/backlight/acpi_video0/brightness
```

It don't work. It not returns any error code but don't change the backlight brightness either.

---

### Post by utilitytrack on 2010-08-06
[FONT="Courier New"]/sys/class/backlight/acpi_video0/brightness 
[/FONT]
Did you check that this file exist on your system? Please put its contents on forum.

---

### Post by andfer on 2010-08-06
> **utilitytrack said:**
> [FONT=Courier New]/sys/class/backlight/acpi_video0/brightness 
[/FONT]
Did you check that this file exist on your system? Please put its contents on forum.

It exist. The output ```
# cat /sys/class/backlight/acpi_video0/brightness
``` is 0 (zero). The value is also zero after an reboot.

There are other files that look relevant in the same directory too, like actual_brightness that stays with value 8 and max_brightness that is also 8.

If I use the FN+up arrow or FN+down arrow, the value of brightness change to 8, don't matter how many times I press one way or the other. I can change it back to 0 using your suggestion. I also tried other values, between 0 and 8, no change.

---

### Post by utilitytrack on 2010-08-06
to **andfer**

please post here [FONT="Courier New"]uname -r[/FONT]

---

### Post by andfer on 2010-08-06
The output of uname -r is: 2.6.32-24-generic

---

### Post by weijie90 on 2010-09-01
bump. Having the same problem: [http://ubuntuforums.org/showthread.php?t=1510159](http://ubuntuforums.org/showthread.php?t=1510159)

---

### Post by suid0 on 2011-04-12
Hello all.. 

I was googling about this problem and after I gave up I found a solution while resting.. lol

BTW I did that in a Slackware box but I'm pretty sure Ubuntu will work the same.

Install the NVIDIA driver.. the orginal one I mean.. After that, go to  NVIDIA X Server Settings that should be available on your WM menu.

After it's open, navigate to X Server Color Correction and there you go!! brightness control.. and it works!!!! :grin:

Suggestion.. reduce both brightness and gamma to have a better result.

I posted on my blog with the same thing so google can have more results so more people can learn that thing
[http://suid0.unitednerds.org/wpress/...5700-notebook/]("http://suid0.unitednerds.org/wpress/2011/04/12/how-to-configure-brightness-on-linux-with-lg-r590-5700-notebook/")


[ ]'s

suid0 a.k.a Sergio
[EMAIL="suid0@unitednerds.org"]suid0@unitednerds.org[/EMAIL]

---

### Post by hayalci on 2011-04-15
Those settings actually do not reduce the actual brightness of the lamp, but they will make things seem darker. (which is fine)

I am also using my system with a reduced gamma.

BTW, I have read that LED backlights cannot be "reduced" in intensity, and the driver just decreases gamma when it's told to decrease brigtness. This may be true, because I experimented in with windows, and while reducing brightness makes the screen easy on my eyes, the backlight does seem to keep its intensity. 

You can check this by looking at the screen in a very inclined angle, look at the light that comes out of it and not the image it displays. FYI, on windows installing the nvidia drivers from nvidia's site disabled the brightness setting, I had to use the LG display driver for the brightness to work.

---

### Post by Gabrys on 2011-05-10
I had a similar problem. GRUB configuration change didn't work. Adding stuff to xorg.conf neither. But I managed to "fix" it using a Python program that binds to D-Bus signal BrightnessChanged and sets the proper brightness using nvclock command. Check this out at my blog: [http://piotr.gabryjeluk.pl/dev:ubuntu-11-04-natty-on-sony-vaio-sz640](http://piotr.gabryjeluk.pl/dev:ubuntu-11-04-natty-on-sony-vaio-sz640)

---

### Post by dedalu on 2011-06-28
Gabrys's workaround does not work for me (nvclock complains about "Unable to shadow the video bios"), so I filed a bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/803051](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/803051) .

---


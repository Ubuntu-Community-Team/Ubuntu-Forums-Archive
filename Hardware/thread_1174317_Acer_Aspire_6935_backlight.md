---
title: "Acer Aspire 6935 backlight"
date: 2009-05-30
forum: Hardware
---

### Post by K. Hendrik on 2009-05-30
Hi,
I've got a problem with my backlight, if I use FN + Brightness up or down the popup showing the increasing decreasing shows up but the Brightness stays the same. But if I use FN + F6 to turn off the backlight an turn it on again the light will have the before selected brightness.
The Brightness applet for the panel doesn't work at all.

---

### Post by K. Hendrik on 2009-05-31
No one any idea how to fix this?

---

### Post by rojakcoder on 2009-05-31
I have a suggestion - it is a command for the terminal/console. You might not like it but it might work.

Open a terminal and go to the directory /proc/acpi/video/

```
cd /proc/acpi/video/
```Type "ls" to see if you get a directory like "LCD" or "OVGA". Type "cd <directory_name>" where <directory_name> is the name of the directory that you see.

Inside the directory you should be able to see a file named "brightness". It might in some sub-directory.

In my case, the file is located at /proc/acpi/video/OVGA/DD03/brightness. Try the following:

```
echo 70 > /proc/acpi/video/OVGA/DD03/brightness
```I've read from many people that this should work - unfortunately, it didn't work for me. So I hope you have better luck!

My post is located [here]("http://ubuntuforums.org/showthread.php?t=1173732"). You can use the "cat" command to see the values available.

---

### Post by K. Hendrik on 2009-05-31
Hi,
/proc/acpi/video/ is an empty directory on my notebook.
but i have found
/sys/devices/platform/acer-wmi/backlight/acer-wmi/
there's a file brightness but it already gets changed by the use of the fn+brightness controll.

---


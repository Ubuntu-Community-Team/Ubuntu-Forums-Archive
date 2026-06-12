---
title: "echo &gt; /proc/.../brightness changes the file but not the brightness"
date: 2010-11-08
forum: Hardware
---

### Post by A.Go on 2010-11-08
Hi!
Could someone help me, please?
I'm trying to adjust power saving settings with a script.
Echoing into the /proc/.../brightness does change the content of the file, but the actual brightness remains the same. The command, however, has a peculiar effect. It changes the value where the brightness would change from with a keyboard.

Let's say, normally, if I have a bright monitor at 80 and 
~$ cat /proc/acpi/video/GFX0/DD02/brightness
levels:  10 20 30 40 50 60 70 80 90 100
current: 80

Pressing Fn+"brighter" would make the monitor brighter (and change the value of "current:" to 100)
If instead I'd press Fn+"dimmer" it would become 60 both in the file and on the screen


Now, if I have it at 80 and
echo 30 > /proc/acpi/video/GFX0/DD02/brightness     

the monitor would remain the same bright (=80), but the file changes
~$ cat /proc/acpi/video/GFX0/DD02/brightness
levels:  10 20 30 40 50 60 70 80 90 100
current: 30

and if I press Fn+"brighter" it would start from 30, not 80 and make the monitor dimmer from 80 to 50
If instead I press Fn+"dimmer" it would become 10

Can someone explain why the content of the file in /proc is respected so little or so late? Is it hardware, Ubuntu, Gnome, kernel bug? Maybe this is the reason Ubuntu Power Management does not work properly on my netbook (at least the screen brightness is not adjusted automatically on a power supply change)?
 
I also suspect that other commands, like:
echo 90 > /proc/sys/vm/dirty_ratio
echo 25 > /proc/sys/vm/dirty_background_ratio
echo 60000 > /proc/sys/vm/dirty_expire_centisecs
echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

neither have any effect on the same reason. Just was not able to test it the same obvious way as with the monitor brightness.

I've got Acer TimelineX 1830TZ, Ubuntu 10.04

---

### Post by JustinR on 2010-11-08
Hi,

the '/proc' directory isn't a system/hardware configuration folder - all it does it hold values for other programs to access information about your system.

You can't actually set anything in '/proc' because all /proc is is for system information - not configuration.

---

### Post by A.Go on 2010-11-08
Thank you for the reply, Justin!

People say kernel is live and one can change values there. At least, I've googled out only this approach to change the monitor brightness with a script. Would you agree, it would be unfair if my keyboard could handle both the /proc file and the actual brightness of the monitor and my script could not?
Do you think there's a better approach?

Andrey

---

### Post by JustinR on 2010-11-08
> **A.Go said:**
> Thank you for the reply, Justin!

People say kernel is live and one can change values there. At least, I've googled out only this approach to change the monitor brightness with a script. Would you agree, it would be unfair if my keyboard could handle both the /proc file and the actual brightness of the monitor and my script could not?
Do you think there's a better approach?

Andrey

Hi,

/proc is changed when a value is changed - i.e. there should be a brightness file somewhere in the '/sys/' directory you can change - which will then change the actual brightness of your monitor and update the '/proc' file at the same time.

---

### Post by A.Go on 2010-11-08
Right, I understand. I kind of also felt that way, that it is a kernel value stored in the memory gets reflected in /proc, not necessary the other way around. But that's just a speculation comparing to an observable fact that, on luckier machines, it is adjustable via echoing to /proc.

Got checked every file in /sys. One by one, in a honest way. They are not so many :-) Nothing hinting on the monitor brightness, no file containing value "50" -- current actual brightness level. Googled once again. Now know a little bit more about "/sys" :-)

---

### Post by A.Go on 2010-11-09
Sorry, it was my mistake. You were right. /sys/ contains, indeed, the brightness handles in /sys/class/backlight/acpi_video0/ There are:
actual_brightness  bl_power  brightness  max_brightness  uevent
But echoing to /sys/.../brightness had exactly the same effect as to /proc/.../brightness
it changes files
/sys/.../brightness
/sys/.../actual_brightness
/proc/.../brightness
unfortunately, it does not change the actual brightness of the screen.
How can I see what is the command performed when I press Fn-Left, which can do an effective change?

---

### Post by JustinR on 2010-11-09
You could check for specific function keys in '/sys' or maybe brightness control is handled by the BIOS - which you wouldn't be able to do much with.

---


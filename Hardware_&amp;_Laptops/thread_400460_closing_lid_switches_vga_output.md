---
title: "closing lid switches vga output"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by jgubes on 2007-04-03
At least, I think this is what is happening.

I have a Dell Latitude c610.  When I close the lid and re-open it, the screen is blank.  To reactivate it I have to push <Fn+F8(crt/lcd)>.  This is the same button I push to switch from the laptop's built-in screen to the vga port on the back.

I don't have an external monitor, so I can't test to see what that vga port is doing.  Is there another way to test which port is active?  Maybe terminal commands over ssh?  And if this really is the problem, is there a way to tell the machine not to switch the output when the lid is closed?

I've tried this, [http://ubuntuforums.org/showthread.php?t=358432](http://ubuntuforums.org/showthread.php?t=358432), but it didn't help.

---

### Post by jjordan on 2007-04-04
OK, stay with me on this.  Frequently laptops do not turn the backlight back on when they un-suspend.  You can try this: 

Open your laptop 
shine a bright flashlight at an angle near the center of the screen 
if you can see anything that might be your login dialog (or anything else) then the screen is on, the backlight is the problem.

If it is the backlight then:
create the file: **/etc/acpi/resume.d/99-undim.sh** use your favorite editor
with the following contents: **echo 8 > /proc/acpi/video/GFX0/LCD/brightness**

oh, don't forget to make it executable:
**sudo chmod +x /etc/acpi/resume.d/99-undim.sh**

This will turn the backlight on at full brightness if your laptop supports acpi.

( I originally got this script from this website: [http://www.xmission.com/~bmidgley/p1510/](http://www.xmission.com/~bmidgley/p1510/) which fixed my similar problem)

-j

---

### Post by jgubes on 2007-04-06
no luck.
```
josh@josh-laptop:~$ sudo ./test.sh
./test.sh: line 1: /proc/acpi/video/GFX0/LCD/brightness: No such file or directory
```
I do have a /proc/acpi/video/VID/LCD/brightness.  Tried that modification to the script, but nothing happened.

Besides, if I close the lid and then open it and run
```
josh@josh-laptop:~$ sudo radeontool light on
```
The backlight comes on, but nothing on screen.

I thought maybe I could figure out which script Fn+F8 calls, but xev doesn't even receive those keystrokes.  The Fn key must shortcut straight into the bios.  So does that mean this is really a Dell problem?

---

### Post by jgubes on 2007-04-06
Finally solved this problem by updating my bios from version a5 to version a16.  If Dell owners are having similar problems I suggest getting the latest bios from dell customer support.

---


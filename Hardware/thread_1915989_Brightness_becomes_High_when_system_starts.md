---
title: "Brightness becomes High when system starts"
date: 2012-01-27
forum: Hardware
---

### Post by ashishpatel on 2012-01-27
I am having Dell Inspiron 1564 Laptop. 
My systems problem is that when I start my PC the brightness always becomes High & I have to reduce it each the i Start my system.
Please help..!:KS

---

### Post by Toz on 2012-02-02
Hello and welcome to the forums.

Lets see what backlight interface you have, and we can setup a process whereby we control the brightness level at startup.

Open a terminal window, type in the following command, and post back the results:
```
ls /sys/class/backlight
```

---

### Post by ashishpatel on 2012-02-03
it returns with..

acpi_video0  intel_backlight

---

### Post by Toz on 2012-02-03
Each of those directories (**acpi_video0** & **intel_backlight**) will have some files in it:
- max_brightness = the maximum brightness level that you can set for that interface
- actual_brightness = the current brightness value
- brightness = the file that you can use to change the brightness

Some examples:
1. To see the current brightness value:
```
cat /sys/class/backlight/intel_backlight/actual_brightness
```
2. To see what maximum brightness level the interface can take:
```
cat /sys/class/backlight/intel_backlight/max_brightness
```
3. To change the brightness:
```
echo VALUE | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...where VALUE is a number between 0 and the contents of the max_brightness file.

Try changing the brightness in both the **intel_backlight** and **acpi_video0** interfaces until it works. Make note of the interface and value that works best for you.

Then, edit /etc/rc.local:
```
gksudo gedit /etc/rc.local
```
...and above the ***exit 0*** line, add the following:
```

echo VALUE > /sys/class/backlight/INTERFACE/brightness
```
...where VALUE is the number and INTERFACE is the interface that works.

Save the file and reboot to test.

---

### Post by acron1 on 2013-03-25
This worked great... Thank you.

---


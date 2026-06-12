---
title: "cannnot adjust brightness ...no matter what"
date: 2010-08-08
forum: Hardware
---

### Post by dinsaurabh on 2010-08-08
Hi guys, I recently installed xubuntu lucid on my toshiba tecra m1 laptop....i had a few problems making it work but i eventually figured them out but the thing that i am stuck in is that i am not able to adjust brightness of the screen no matter what i try....i have googled around and found some workarounds and solutions but none of them worked for me. Moreover the fn keys  are also not working for adjusting brightness but for the rest of the things they started working when i installed **fnfxd**  The brightness of my screen is just stuck and its pretty annoying. Please help!!!

---

### Post by arasbm on 2010-08-08
Is there a bios option to set the default brightness level? Also, is the screen dim even when the laptop is plugged in? If not, maybe you can play with the power management setting to get the screen to stay bright.

I dont have the same laptop, but I remember something about being able to set brightness level in the bios settings.

---

### Post by utilitytrack on 2010-08-08
to **dinsaurabh**

Look in here: [http://ubuntuforums.org/showthread.php?p=9677094#post9677094]("http://ubuntuforums.org/showthread.php?p=9677094#post9677094")

PS
Don't forget that only root can do this

---

### Post by dinsaurabh on 2010-08-08
> **utilitytrack said:**
> to **dinsaurabh**

Look in here: [http://ubuntuforums.org/showthread.php?p=9677094#post9677094]("http://ubuntuforums.org/showthread.php?p=9677094#post9677094")

PS
Don't forget that only root can do this

Yes i have already tried but that doesnt help. Moreover i had two generic backlight devices , so i thought that this might be the reason that they are clashing with each other so what i did was , i added acpi_backight=vendor in the /etc/default/grub file , which i found as a solution on some threads and updated the grub. So the outcome was that now i have only one backlight device but it still doesnt work. I have already tried the method u suggested on the following files but there is still no change in the brightness.

```
root@saurabh-laptop:~# echo 0 > /sys/class/backlight/toshiba/brightness
root@saurabh-laptop:~# echo 2 > /sys/class/backlight/toshiba/brightness
root@saurabh-laptop:~# echo 3 > /sys/class/backlight/toshiba/brightness
root@saurabh-laptop:~# echo "brightness:3" > /proc/acpi/toshiba/lcd
root@saurabh-laptop:~# echo "brightness:2" > /proc/acpi/toshiba/lcd
root@saurabh-laptop:~# echo "brightness:2" > /proc/acpi/toshiba/lcd
```

---

### Post by dinsaurabh on 2010-08-08
> **arasbm said:**
> Is there a bios option to set the default brightness level? Also, is the screen dim even when the laptop is plugged in? If not, maybe you can play with the power management setting to get the screen to stay bright.

I dont have the same laptop, but I remember something about being able to set brightness level in the bios settings.

I tried looking for the brightness level in the bios. It was set to automatic. So i changed it to user-adjustable and it worked. Now i am able to change my lcd brightness using the panel applet as well as the fn keys.Thanks a lot. The only thing now is that it doesnt show any kind of notification(Notify OSD) when i change it, the way it does when i adjust the volume.Can you help me with that??

---


---
title: "Temperature issues"
date: 2006-12-05
forum: Hardware &amp; Laptops
---

### Post by alek66 on 2006-12-05
I wanted to know the way to lower my temp in my acer laptop.
I have acpi running, cpu thotelling works also. but I noticed that the fan never stops... I recall that when using WinXp the fan used to stop...meaning the computer runned cooler (when it was on powersave and entered in screensaver) now in linux it doesnt anymore.

apart from that I would like to unload services or things that I dont use, so it runs cooler but I dont much about that. Besides i thing that the most heating thing is the nvidia device, but I am not using beryl or things like that to make it work in effort. So I dont know what to do... if you could tell me what to post, i post so that you can help me.

I had previous problems using beryl and aiglx...the computer heated up... and shutdowns automatically.

---

### Post by kevinlyfellow on 2006-12-05
To prevent loading services that you don't use, install sysv-rc-conf... don't forget to write down the changes you make!

I used to have that fan issue with my desktop.  Check to see if there is a file in /proc/acpi/fan/  On my desktop I sent the file the value 0 to give control to the bios... so
echo 0 > /proc/acpi/fan/FAN0
but be very careful with this and make sure that it doesn't shut the fan off completly.

---

### Post by alek66 on 2006-12-05
> **kevinlyfellow said:**
> To prevent loading services that you don't use, install sysv-rc-conf... don't forget to write down the changes you make!

I used to have that fan issue with my desktop.  Check to see if there is a file in /proc/acpi/fan/  On my desktop I sent the file the value 0 to give control to the bios... so
echo 0 > /proc/acpi/fan/FAN0
but be very careful with this and make sure that it doesn't shut the fan off completly.

```
alek@Darkstar:/proc/acpi$ ls
ac_adapter  dsdt                 fan             processor     video
alarm       embedded_controller  hotkey          sleep         wakeup
battery     event                info            sony          wmi
button      fadt                 power_resource  thermal_zone
alek@Darkstar:/proc/acpi$ cd fan
alek@Darkstar:/proc/acpi/fan$
alek@Darkstar:/proc/acpi/fan$ ls
alek@Darkstar:/proc/acpi/fan$ 

```

theres nothing there....
But the thing is that the fan is running cause it is hot... i want to run a little bit cooler and i dont know how

---


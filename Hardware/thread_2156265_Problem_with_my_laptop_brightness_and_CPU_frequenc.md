---
title: "Problem with my laptop brightness and CPU frequency"
date: 2013-06-21
forum: Hardware
---

### Post by th27 on 2013-06-21
Hi everone,
I have two questions.

1.
The first problem is that the maximum of the brightness setting is still too dim, according to*** /sys/class/backlight/acpi_video0/max_brightness***.
I tried to rewrite the file max_brightness, but failed of permission denied. 


Then I checked***/sys/class/backlight/intel_backlight/brightness***, and I found the actual brightness is only 1100 out of 4437.


I rewrote*** /sys/class/backlight/******intel_backlight******/brightness*** to 4400, and it worked. But every time I restart or close and open the lid, it gets back to the dim scene.


And I can't use my fn key either, for it can only adjust* **/sys/class/backlight/acpi_video0/brightness*** in a dim range.

Is there a way to bind the ***/sys/class/backlight/acpi_video0/brightness*** with  ***/sys/class/backlight/******intel_backlight******/brightness*** ?

2.
My cpu is i7 3517u. When I use windows it can get 2.8GHz, but in ubuntu it can only get as high as 2.4GHz.


How to adjust the max frequency of CPU?


Thanks

---

### Post by Toz on 2013-06-21
Hello and welcome to the forums.

What is the make and model of your laptop?

1. Brightness:
> Is there a way to bind the /sys/class/backlight/acpi_video0/brightness with /sys/class/backlight/acpi_video0/brightness ?
This is somewhat confusing. Is one of those actually acpi_video**[COLOR="#FF0000"]1[/COLOR]**? If so, can you try using the **acpi_backlight=vendor** kernel parameter? Have a look at the "Kernel Boot Parameters" link in my signature for more information on how to use these parameters.

2. CPU Frequency:
By default, Ubuntu uses the ondemand frequency governor, meaning it will increase the CPU speed as required. You can view specific info about your cpu (including maximum frequencies, available governors, etc by catting the files in /sys/devices/system/cpu/[COLOR="#FF0000"]**<CPU>**[/COLOR]/cpufreq where [COLOR="#FF0000"]**<CPU>**[/COLOR] is either cpu0, cpu1, cpu2....up to the number of cpu/cores you have. For example:
```
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq
```
```
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

Does the first command report that your maximum frequency as 2800000 or 24000000?

---

### Post by th27 on 2013-06-21
Sorry Toz, it is actually ***intel_backlight. ***[COLOR=#000000]I copied it wrong.
[/COLOR]
My laptop is Lenovo K29. HM77, HD4000, no Discrete graphics.

1.
[COLOR=#000000]In my folder [/COLOR][COLOR=#000000]*/sys/class/backlight/, there are *[/COLOR][COLOR=#000000]*acpi_video0 and *[/COLOR]*intel_backlight.*[COLOR=#000000]
The [/COLOR]**acpi_backlight=vendor **[COLOR=#000000] parameter works and I entered the system with the max brightness.
 BUT when I press FN hotkey to adjust down the brightness and then brighten the backlight again, it can't get as bright as before (brightness=4437=max_brightness). 
It seems it can just get to as much as "brightness=1740" with my fn key.
My question is: Can I use fn key to reach t[/COLOR][COLOR=#000000]h[/COLOR][COLOR=#000000]e max brightness (without command input)? or Can I make [/COLOR][COLOR=#000000]*acpi_video0/max_brightness(15) *[/COLOR][COLOR=#000000]bind to [/COLOR]*intel_backlight/max_brightness(4437) *[COLOR=#000000]when it actually reaches no more than 1740?

2.
I checked:
[/COLOR][SIZE=3][COLOR=#00ff00]
[/COLOR][COLOR=#006400][FONT=georgia]cat cpuinfo_max_freq 
2401000


cat scaling_governor 
ondemand

cat scaling_available_frequencies 
2401000 2400000 2300000 2200000 2000000 1900000 1800000 1700000 1500000 1400000 1300000 1200000 1100000 900000 800000 799000 
[/FONT][/COLOR][/SIZE]


But I know it can reach 2800000. Why is that?


Thanks a lot!

---

### Post by Doug S on 2013-06-21
> **th27 said:**
> [SIZE=3][COLOR=#006400][FONT=georgia]cat cpuinfo_max_freq 
2401000

cat scaling_available_frequencies 
2401000 ... [/FONT][/COLOR][/SIZE]The "01" on the 2400 means "turbo" and does not actually indicate the frequency that your system will get to. When using the acpi-cpufreq frequency scaling driver the only way to know the actual frequency of your cpu is to use turbostat, particularly when it is in turbo mode (there are issues under some conditions with reported frequencies when not in turbo mode also).

---

### Post by Toz on 2013-06-21
> **th27 said:**
> 1.
[COLOR=#000000]In my folder [/COLOR][COLOR=#000000]*/sys/class/backlight/, there are *[/COLOR][COLOR=#000000]*acpi_video0 and *[/COLOR]*intel_backlight.*[COLOR=#000000]
The [/COLOR]**acpi_backlight=vendor **[COLOR=#000000] parameter works and I entered the system with the max brightness.
 BUT when I press FN hotkey to adjust down the brightness and then brighten the backlight again, it can't get as bright as before (brightness=4437=max_brightness). 
It seems it can just get to as much as "brightness=1740" with my fn key.
My question is: Can I use fn key to reach t[/COLOR][COLOR=#000000]h[/COLOR][COLOR=#000000]e max brightness (without command input)? or Can I make [/COLOR][COLOR=#000000]*acpi_video0/max_brightness(15) *[/COLOR][COLOR=#000000]bind to [/COLOR]*intel_backlight/max_brightness(4437) *[COLOR=#000000]when it actually reaches no more than 1740?

Can you try the following kernel parameters as well (one at a time) and remember to run "sudo update-grub" after each set?
```
acpi_osi=
```
```
acpi_osi=Linux acpi_backlight=vendor
```

---

### Post by th27 on 2013-06-22
Thank you, the turbo seems working.

---

### Post by th27 on 2013-06-22
The  [COLOR=#000000][FONT=Ubuntu Mono]acpi_osi=[/FONT][/COLOR]  [FONT=Ubuntu Mono][SIZE=2][COLOR=#000000]didn't work, and [/COLOR][/SIZE][/FONT][COLOR=#000000][FONT=Ubuntu Mono]acpi_osi=Linux acpi_backlight=vendor [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] acts the same as [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]acpi_backlight=vendor[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]...
And I can use **Settings -- Brightness and Lock** to adjust the brightness well, the only problem now is the fn key.[/FONT][/COLOR]

---

### Post by Toz on 2013-06-22
With acpi_osi=Linux and acpi_backlight=vendor enabled, can you post back the following:

```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

And finally, open a terminal window and type in:
```
acpi_listen
```
...then press the brightness up function key once and then the brightness down function key once. Post back the codes that are displayed in the terminal window.

---

### Post by th27 on 2013-06-23
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=7cd4cfb5-bc5e-448e-a704-da1f56a16666 ro quiet splash acpi_osi=Linux acpi_backlight=vendor vt.handoff=7


for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/intel_backlight
3771
4437

In the  [COLOR=#000000][FONT=Ubuntu Mono]acpi_listen[/FONT][/COLOR] terminal, I pressed fn key up and down but it displayed nothing.

---

### Post by Toz on 2013-06-23
> **th27 said:**
> 
In the  [COLOR=#000000][FONT=Ubuntu Mono]acpi_listen[/FONT][/COLOR] terminal, I pressed fn key up and down but it displayed nothing.

This I believe is your problem. The O/S is not recognizing the function keys. Trying those kernel paramters above instructed the bios to offer up differing acpi tables to the O/S, but it did not work. Can you look directly into your bios settings to see if there are any options that affect the operations of function keys? 

Do any of the other function keys work?

Can you post back your dmesg log file:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

As a workaround for your original problem:
> 
I rewrote /sys/class/backlight/intel_backlight/brightness to 4400, and it worked. But every time I restart or close and open the lid, it gets back to the dim scene
...you could:
1. For restarts, add:
```
echo 4400 > /sys/class/backlight/intel_backlight/brightness
```
...to **/etc/rc.local** before the *exit 0* command. And:
2. Create a resume script to reset the brightness on resume:
```
gksu gedit /etc/pm/sleep.d/99_fixbrightness
```
...copy/paste this content:
```

#!/bin/bash
case $1 in
     suspend|suspend_hybrid|hibernate)
	# do nothing
        ;;
     resume|thaw)
	echo 4400 > /sys/class/backlight/intel_backlight/brightness
        ;;
esac
```
...save the file and make it executable:
```
sudo chmod +x /etc/pm/sleep.d/99_fixbrightness
```

---

### Post by th27 on 2013-06-23
Sorry, I am afraid I didn't express correctly.

Now with [COLOR=#000000]acpi_osi=Linux acpi_backlight=vendor [/COLOR]I can boot with the maximum brightness. And I can adjust brightness well in the system settings (GUI approach).
[COLOR=#000000]In the [/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]acpi_listen[/FONT][/COLOR][/COLOR][COLOR=#000000] terminal, I pressed fn key up and down ,the brightness may go to 1600/1700,  but the terminal displayed nothing.[/COLOR]

My fn key is able to adjust the screen brightness, but only in a small range (0 to 1700 while the max is 4400). 
So if I give up using fn key to adjust brightness, I can say my brightness problem is solved...

And other function keys works well.

[COLOR=#000000][FONT=Ubuntu Mono]pastebinit /var/log/dmesg :
[/FONT][/COLOR][http://paste.ubuntu.com/5794252/](http://paste.ubuntu.com/5794252/)

---

### Post by Toz on 2013-06-23
Can you try the acpi_osi='!Windows 2012'" kernel parameter instead of the other two? The line in your /etc/default/grub file should look like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi='!Windows 2012'"
```

If that doesn't work, return back to the previous two parameters (acpi_osi=Linux acpi_backlight=vendor) and create the file (/usr/share/X11/xorg.conf.d/20-intel.conf) with the following contents:
```

Section     "Device"
   Identifier  "Card0"
   Driver      "intel"
   Option     "Backlight"          "intel_backlight"
EndSection
```

Reboot and test again.

---

### Post by th27 on 2013-06-24
I think the '!Windows 2012' parameter doesn't work...

And after using [FONT=Verdana]20-intel.conf, I can't even load into the desktop...(all blackout after the grub2 menu)[/FONT]

---

### Post by Toz on 2013-06-24
I'm sorry but I'm out of ideas. Perhaps it is best to create a bug report for this problem. Keep in mind, that as a workaround, you can echo values directly into the interface brightness file to fine-tune the laptop brightness:
```
echo xxxx | sudo tee /sys/class/backlight/intel_backlight/brightness
```
...where xxxx is a number between 0 and 4437.

---

### Post by th27 on 2013-06-25
OK got it, thank you so much for your help.

---


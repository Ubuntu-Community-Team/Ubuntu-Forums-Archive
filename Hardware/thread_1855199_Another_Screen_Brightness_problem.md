---
title: "Another Screen Brightness problem"
date: 2011-10-05
forum: Hardware
---

### Post by Kyledoo on 2011-10-05
I have a gateway nv59 laptop, and i have recently decided to try using ubuntu as my only OS. so far it is going very well, I have been able to find all of the applications I need native except for a few that run perfectly in wine. Right now my biggest two issues are not being able to adjust screen brightness and no two finger scrolling on my trackpad. I tried downloading the synaptiks control panel and for some reason it won't let me change the number of fingers my track pad will recognize from 1 to 2, even though I know it supports 2 because in windows 7, 2 finger scrolling worked. 
The first issue is much more important, however, and I have not been able to find a way to solve it. I tried editing the grub file, got an error when attempting to save, but did the update-grub anyway. it seems to hold the values i changed after system reboot so I am presuming that it was changed correctly, yet I still cannot change screen brightness.
Any help is greatly appreciated, I really want to make Ubuntu my only OS if possible (it currently is the only one installed on this hard drive)
P.s. I am running 64 bit 11.04

---

### Post by Redblade20XX on 2011-10-05
Can you tell us the graphics card you have and whether you installed any proprietary drivers pertaining to the card?:p

-Red

---

### Post by Toz on 2011-10-05
Have a look at this post: [http://ubuntuforums.org/showpost.php?p=10481512&postcount=19]("http://ubuntuforums.org/showpost.php?p=10481512&postcount=19")

---

### Post by Kyledoo on 2011-10-06
> **Toz said:**
> Have a look at this post: [http://ubuntuforums.org/showpost.php?p=10481512&postcount=19](http://ubuntuforums.org/showpost.php?p=10481512&postcount=19)

How do I apply this to my system? I don't really see any instructions and I'm not familiar enough with the terminal to do something without having a little guidance

---

### Post by Toz on 2011-10-06
From the terminal.....

1. First check that you have the right graphics processor. 
```
lsmod | grep ^i915
```
If it returns something like:
>   i915 331519 3 
...then you're good to go.

2. Add the repository:
```
sudo add-apt-repository ppa:kamalmostafa/linux-kamal-mjgbacklight
```

3. Update your system:
```
sudo apt-get update
```

4. Install the modified kernel:
```
sudo apt-get dist-upgrade
```

If it still doesn't work, you can also try adding the **acpi_backlight=vendor** kernel parameter.

---

### Post by Kyledoo on 2011-10-06
> **Toz said:**
> From the terminal.....

1. First check that you have the right graphics processor. 
```
lsmod | grep ^i915
```
If it returns something like:

...then you're good to go.

2. Add the repository:
```
sudo add-apt-repository ppa:kamalmostafa/linux-kamal-mjgbacklight
```

3. Update your system:
```
sudo apt-get update
```

4. Install the modified kernel:
```
sudo apt-get dist-upgrade
```

If it still doesn't work, you can also try adding the **acpi_backlight=vendor** kernel parameter.

I did this and now my system wont boot :( it gets to the loading screen then goes to a blank black screen

---

### Post by Toz on 2011-10-06
Hold down the shift key while the computer is booting and you should get to the grub screen. From there you can boot a previous kernel.

Are you using a nomodeset parameter? Post back the contents of **/etc/default/grub**

---

### Post by Kyledoo on 2011-10-06
> **Toz said:**
> Hold down the shift key while the computer is booting and you should get to the grub screen. From there you can boot a previous kernel.

Are you using a nomodeset parameter? Post back the contents of **/etc/default/grub**
I didn't change anything beyond the instructions you posted. However, it is now working properly, however whenver I shut down or reboot the system I have to put it into sleep mode then wake it back up in order to get the screen to come on. The screen brightness controls DO work now though!

---

### Post by Toz on 2011-10-06
What does the following return when the screen is at the desired brightness?
```
cat /sys/class/backlight/intel_backlight
```

---

### Post by Kyledoo on 2011-10-06
> **Toz said:**
> What does the following return when the screen is at the desired brightness?
```
cat /sys/class/backlight/intel_backlight
```

```
kyle@kyle-laptop:~$ cat /sys/class/backlight/intel_backlight
cat: /sys/class/backlight/intel_backlight: Is a directory
```

---

### Post by Toz on 2011-10-06
How about:
```
ls /sys/class/backlight/intel_backlight
```

If there is an acpi_video0 directory there, then:
```
cat /sys/class/backlight/intel_backlight/acpi_video0/brightness
```

---

### Post by Kyledoo on 2011-10-06
> **Toz said:**
> How about:
```
ls /sys/class/backlight/intel_backlight
```If there is an acpi_video0 directory there, then:
```
cat /sys/class/backlight/intel_backlight/acpi_video0/brightness
```

I went ahead and ran the cat command for all of the items in that directory, as well as listed the items in the one subdirectory for you.
```
kyle@kyle-laptop:~$ ls /sys/class/backlight/intel_backlight
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type
kyle@kyle-laptop:~$ cat /sys/class/backlight/intel_backlight/actual_brightness
640
kyle@kyle-laptop:~$ cat /sys/class/backlight/intel_backlight/brightness
640
kyle@kyle-laptop:~$ cat /sys/class/backlight/intel_backlight/max_brightness
976
kyle@kyle-laptop:~$ cat /sys/class/backlight/intel_backlight/bl_power
-2119831232
kyle@kyle-laptop:~$ cat /sys/class/backlight/intel_backlight/uevent
kyle@kyle-laptop:~$ cat /sys/class/backlight/intel_backlight/type
raw
kyle@kyle-laptop:~$ ls /sys/class/backlight/intel_backlight/power
autosuspend_delay_ms    wakeup               wakeup_last_time_ms
control                 wakeup_active        wakeup_max_time_ms
runtime_active_time     wakeup_active_count  wakeup_total_time_ms
runtime_status          wakeup_count
runtime_suspended_time  wakeup_hit_count
kyle@kyle-laptop:~$ 
```

---

### Post by Toz on 2011-10-06
> kyle@kyle-laptop:~$ cat /sys/class/backlight/intel_backlight/brightness
640

That's the one. 

Add to the file **/etc/rc.local** (before the command "exit 0"), the following:
```
echo 640 > /sys/class/backlight/intel_backlight/brightness
```

This will set the current brightness value on startup so hopefully, you won't have to sleep/resume to get the brightness working.

---

### Post by Kyledoo on 2011-10-06
> **Toz said:**
> That's the one. 

Add to the file **/etc/rc.local** (before the command "exit 0"), the following:
```
echo 640 > /sys/class/backlight/intel_backlight/brightness
```This will set the current brightness value on startup so hopefully, you won't have to sleep/resume to get the brightness working.
Thank you so much! It works now! I'm loving ubuntu!

---

### Post by Toz on 2011-10-06
Glad to hear it works. According to kamal's launchpad site, all of these changes are included in the new version of ubuntu (oneiric), so you won't have to go through these steps again to get brightness working properly on the newer versions of ubuntu.

If you don't mind, can you please mark the thread as SOLVED using the "Thread Tools" link above?

---

### Post by Kyledoo on 2011-11-05
Problem solved!

---

### Post by Kyledoo on 2011-11-07
So, I upgraded to 11.10, and it is working beautifully! I got the screen brightness working by modifying the kernel boot parameter. Anyway, the only problem I am having is that when the laptop sleeps, when I wake it up and it goes to the login scren, the backlight is all the way down. I can usually type my passord, hit enter, then once it is logged in I am able to use the keyboard hotkeys to adjust the light to the desired layer. I like being able to turn the backlight off when downloading or doing something that doesn't require the screen for a long amount of time, but if I am not in direct sunlight or bright indoor lighting, it is impossible to see the screen upon resume. Any ideas how to correct this?

---

### Post by Toz on 2011-11-08
> **Kyledoo said:**
> Anyway, the only problem I am having is that when the laptop sleeps, when I wake it up and it goes to the login scren, the backlight is all the way down. I can usually type my passord, hit enter, then once it is logged in I am able to use the keyboard hotkeys to adjust the light to the desired layer. I like being able to turn the backlight off when downloading or doing something that doesn't require the screen for a long amount of time, but if I am not in direct sunlight or bright indoor lighting, it is impossible to see the screen upon resume. Any ideas how to correct this?

We can try rerunning the original command at the time the system resumes. You will need root access to do this. Create the file **/etc/pm/sleep.d/restore_brightness** with the following contents:
```
#!/bin/bash
case "$1" in
   suspend|hibernate)
      #do nothing
   ;;
   resume|thaw)
      echo 640 > /sys/class/backlight/intel_backlight/brightness   
   ;;
   *)
      exit 1
   ;;
esac
exit 0

```
...and make the file executable.

On next resume, that command should be run again and should reset the screen brightness.

---


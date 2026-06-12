---
title: "Fan doesn't Stop!"
date: 2008-07-07
forum: Hardware
---

### Post by moved on 2008-07-07
Hi everybody,
I installed Ubuntu a few days ago with Wubi.
Normally,
When I hit power button,fan starts to turning.Later when I see Windows Splash Screen,it stops.Which **fan** stops I don't know but in Ubuntu(Hardy Heron) it **never** **stops**!It sounds loudly.I thought that the problem may be with drivers.Here's the My Pc:

[COLOR="SeaGreen"]CPU[/COLOR]:Intel E7200 Core2Duo
[COLOR="SeaGreen"]MotherBoard[/COLOR]:**GIGABYTE P35-DS3R**
[COLOR="SeaGreen"]Graphic Card[/COLOR]:Palit GeForce 9600 GT.
(Also I have an power supply,but I don't think problem is with it)
Please Help me to solve this problem.I want to use Ubuntu!Thanks. :(

---

### Post by AlesUbu123 on 2008-07-07
What is the output of commands:
```
acpi -V
```
and
```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
```
and
```
cat /proc/acpi/thermal_zone/TZ*/temperature
```

---

### Post by moved on 2008-07-07
Can you wait for a day?Because I deleted Ubuntu.Then maybe I can pm you.Thanks for helping. :)

---

### Post by AlesUbu123 on 2008-07-07
No problem.
Regards

---

### Post by sagararora on 2008-07-08
hello friends...
i seem to have same problem as one of my friend stated above...plz help me..
i too installed ubuntu using wubi but it always run quite heavily..even if only mozilla and terminal are running in foreground.
i give u result of my laptop ..plz see thru it...
[B]
sagar@sagar-laptop:~$ acpi -V
     Battery 1: charged, 100%
     Thermal 1: ok, 60.0 degrees C
     Thermal 2: ok, 27.0 degrees C
  AC Adapter 1: on-line
sagar@sagar-laptop:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
1733000 1333000 1067000 800000 
1733000 1333000 1067000 800000 
sagar@sagar-laptop:~$ cat /proc/acpi/thermal_zone/TZ*/temperature
temperature:             60 C
temperature:             27 C[/B]

plz reply if there is any problem

---

### Post by moved on 2008-07-09
Here's the result.
```
akif@akif-desktop:~$ acpi -V
No support for device type: thermal
akif@akif-desktop:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
2400000 1600000 
2400000 1600000 
akif@akif-desktop:~$ cat /proc/acpi/thermal_zone/TZ*/temperature
cat: /proc/acpi/thermal_zone/TZ*/temperature: No such file or directory
akif@akif-desktop:~$ 
akif@akif-desktop:~$ 



```

---

### Post by AlesUbu123 on 2008-07-20
Sorry for the late reply. I am on the vacation 8)
It seems scaling of CPU frequencies in your cases are supported fine for both of you, so that isn't the cause of this problem.

Maybe the next step would be to use 
```
top
```
and check if any particular process is consuming a considerable percentage of CPU cycles.

Is your fan speed changing during use or is always the same?
And also, what does 
```
cat /proc/acpi/fan/*/*
``` 
say?

---

### Post by jay019 on 2008-07-29
I dont really want to hijack this thread, but as I have the same problem thought it best to just post here...

Everything was fine with 7.04 these problems started since upgrading (on a new drive) to 8.04 so if anything on my old drive can give some clues then please ask as its still intact. Computer is a Toshiba Satellite M110/L00 and everything (except the function and multimedia keys) works perfectly.

Once my fan starts it doesnt stop UNLESS i run acpi -t then it will stop and tell me...

> 
Battery 1: charged, 100%
Thermal 1: active[0], 24.0 degrees C
Thermal 2: ok, 33.0 degrees C


Why the fan is still running when the temps are so low is what I would like to find out and fix.

For completeness here is the results (although taken after fan turned off with acpi -t...

acpi -V
> 
Battery 1: charged, 100%
Thermal 1: active[0], 35.0 degrees C
Thermal 2: ok, 43.0 degrees C
AC Adapter 1: on-line


cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
> 
1600000 1333000 1067000 800000 
1600000 1333000 1067000 800000 


cat /proc/acpi/thermal_zone/TZ*/temperature
> 
temperature:             52 C
temperature:             57 C

(Fan also just started slowly when this was done, which sounds about right judging by the temps. Will keep testing the temp and post the temp the fan stops by itself if it ever does.

Edit, got sick of the sound of the fan so ran cat /proc/acpi/thermal_zone/TZ*/temperature which turned of the fan and returned...
> 
temperature:             26 C
temperature:             36 C


Hmmm. Somethings definately not right!

---

### Post by AlesUbu123 on 2008-07-30
Hello!

I am not a linux guru and I don't own a Toshiba laptop to test my advice, so I'll try to help you with what I can until someone more insightful comes around.

So, could you check wheter toshiba_acpi module is loaded on your laptop by writing with this command:
```
lsmod | grep toshiba
```

---

### Post by jay019 on 2008-07-30
OK. I dont seem to have that module loaded. I dont even know where to look to see if I even have it on my system.

---

### Post by AlesUbu123 on 2008-07-31
Umm, what happens if you try to insert module by

```
sudo modprobe toshiba_acpi
```

---

### Post by jay019 on 2008-07-31
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.24-19-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device


It also appears in modules.dep so I take it I have to add something to /dev ???

---

### Post by AlesUbu123 on 2008-07-31
Ok.
What is the output of: 
```
dmesg | grep acpi
```

Checkout acpi's logfile for error messages:
```
gedit /var/log/acpid
```

Are you using any special grub boot parameters?

---

### Post by callum_G on 2008-07-31
Also in my new computer with a Gigabyte ep35-ds3l I cannot get the system fan speeds to a reasonable level, they are always at 100%. 

The output of acpi -V is:

callum@******:~$ acpi -V
No support for device type: thermal

then for the other command cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies i get

callum@******:~$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies
cat: /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_frequencies: No such file or directory

and for thermal zone 

callum@******:~$ cat /proc/acpi/thermal_zone/TZ*/temperature
cat: /proc/acpi/thermal_zone/TZ*/temperature: No such file or directory

Are there any modules for my Motherboard that I can load?

Thanks in advance any help is greatly appreciated:)

---

### Post by AlesUbu123 on 2008-07-31
callum_G: What CPU you have?

---

### Post by jay019 on 2008-07-31
> **AlesUbu123 said:**
> Ok.
What is the output of: 
```
dmesg | grep acpi
```

Checkout acpi's logfile for error messages:
```
gedit /var/log/acpid
```

Are you using any special grub boot parameters?

dmesg | grep acpi...
```

... (nothing)

```

gedit /var/log/acpid
```

Couldn't see any error messages, just some notifications about it executing power.sh, lid.sh, videobtn.sh

```

Grub...
```

splashimage=(hd0,0)/boot/grub/splashimages/splash1.xpm.gz

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=dffa5e92-dc47-44c6-8450-6e330fc8e21f ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

And thanks for stepping through this with me. I am lost when it comes to hardware problems not solved by googling.

---

### Post by callum_G on 2008-08-03
I have a Q6600:)

---

### Post by jay019 on 2008-08-06
Oh well, looks like its back to 7.04 before my laptop melts and dies. Nice!

---


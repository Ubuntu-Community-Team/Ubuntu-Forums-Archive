---
title: "HP Pavilion g6-1155ee brightness problem"
date: 2011-07-21
forum: Hardware
---

### Post by 3Dman on 2011-07-21
Hello, 
I have HP Pavilion g6-1155ee and I can't change the brightness at all and it's stuck at max.

I tried changing it using the keys and gnome-power-preferences and none of them did work.

Laptop specifications:
Intel Core i5 2.3 GHz
4GB RAM
Intel HD 3000

Any help would be appreciated.

EDIT: Solved using this kernel [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-i915bri](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-i915bri)

---

### Post by Toz on 2011-07-21
Can you open a terminal window, type in the following commands, and post back the results?
```
lspci | grep VGA
```
```
cat /sys/class/backlight/acpi_video0/brightness
```
If you get an error message with this last command, then run:
```
ls /sys/class/backlight
```

---

### Post by 3Dman on 2011-07-21
```
ubuntu@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```
```
ubuntu@ubuntu:~$ cat /sys/class/backlight/acpi_video0/brightness 
5

```

Thanks for helping me fixing this :)

---

### Post by Toz on 2011-07-22
Does the following command make your screen dimmer?
```
sudo setpci -s 00:02.0 F4.B=96
```

If so, does the following make it fully bright again?
```
sudo setpci -s 00:02.0 F4.B=ff
```

---

### Post by 3Dman on 2011-07-22
I tried the setpci command, it never worked with me.

---

### Post by Toz on 2011-07-22
1. Does anything happen if you echo a value lower than 5 to /sys/class/backlight/acpi_video0/brightness ?
```
sudo echo 4 > /sys/class/backlight/acpi_video0/brightness 
```

2. Do you have an **/etc/X11/xorg.conf** file? If so, post contents.

3. Can you try the following kernel parameters to see if it makes a difference?
```
acpi_osi=Linux
``` 
```
acpi_osi=\"Linux\"
``` 
```
acpi_backlight=vendor
```

4. Try the xbacklight program:
```
sudo apt-get install xbacklight
```
then:
```
xbacklight -set 50
```

---

### Post by 3Dman on 2011-07-23
1. Nothing happens when echoing values at all even with the kernel parameters are set.

2. There's no xorg.conf file, I think xorg-server does the configuration on the fly?

3. Tried every parameter of them with with the first two it's the same, I can't change the brightness, xbacklight doesn't change anything as well as the keys and gnome-power-preferences

With the third one:
```
acpi_backlight=vendor
```

I don't get the backlight device detected and xbacklight throws this:
```
No outputs have backlight property
```

I wonder what causes this problem so I could file a bug, but at the moment I'm not sure if it's a BIOS problem or kernel or acpi...

Thanks for helping :)

---

### Post by Toz on 2011-07-23
Hmmm. Only 3 more suggestions left:

1. I've seen in a few posts that the X parameter EnableBrightnessControl may fix this problem (though most of the posts focus on the nvidia driver) - but it may be worth a try. Create an /etc/X11/xorg file with the following contents:
```
Section "Device"
        Identifier "Default Device"
        Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```

2. Try the xorg-edgers X version. See: [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa") and [http://ubuntuforums.org/showthread.php?t=1728526]("http://ubuntuforums.org/showthread.php?t=1728526")

3. Possibly try a newer kernerl. See: [https://wiki.ubuntu.com/Kernel/MainlineBuilds]("https://wiki.ubuntu.com/Kernel/MainlineBuilds")

---

### Post by 3Dman on 2011-07-28
Thanks Toz for bearing with me I've fixed my issue by using this kernel [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-i915bri](https://launchpad.net/~kamalmostafa/+archive/linux-kamal-i915bri)

So the problem is from the i915 driver, I hope it will get fixed in upstream soon.

Thanks a lot.

---


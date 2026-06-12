---
title: "fn+brightness does not work 14.04 Trusty 64 bit"
date: 2014-06-08
forum: Hardware
---

### Post by Ashwij on 2014-06-08
Hi All,

the Fn+brightness up or down button do not work on my AMD A4 5000 based laptop from Asus. I tried using xorg driver and updated to fglrx latest, updated to kernel 3.14.

All otherfn buttons including screen off,mute, wifi, touchpad etc work fine. I even tried disabling varibright from catalyst.


Please assist

---

### Post by mikeyinid on 2014-06-08
Not sure if this will help, its all I got. Might point you in the right direction.
[http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)

---

### Post by jeremy31 on 2014-06-08
use ```
acpi_listen
``` in terminal and press the brightness hotkeys and post results

---

### Post by Ashwij on 2014-06-09
ashwij@ashwij-X550EA:~$ acpi_listen
video/brightnessup BRTUP 00000086 00000000
video/brightnessup BRTUP 00000086 00000000
video/brightnessup BRTUP 00000086 00000000
video/brightnessdown BRTDN 00000087 00000000
video/brightnessdown BRTDN 00000087 00000000
video/brightnessdown BRTDN 00000087 00000000


Thanks for helping Jeremy

---

### Post by Ashwij on 2014-06-09
Hey,

I tried almost all that google had, has not worked.

I would also like to inform that updating to kernel 3.14.5 has not changed anything. If I get the Xorg driver, I get the slider but it doesnt change anything, also a brighness controller app changes numbers but no change in brightness.

Also with fglrx, it does show varibright changing brightness effectively but its still too bright

---

### Post by jeremy31 on 2014-06-09
Have you tried ```
video.use_native_backlight=1
``` or ```
acpi_backlight=vendor
``` in grub?

---

### Post by Ashwij on 2014-06-09
Hi Jeremy,

I believe I tried the second option and also replaced vendor with output from another command. But neither worked. Can you pleasedetail out the steps for me or just guide me to a link?

Heres what grub looks like

GRUB_CMDLINE_LINUX="quiet splash acpi_osi=Linux acpi_backlight=asus-nb-wmi"

---

### Post by jeremy31 on 2014-06-09
[https://wiki.ubuntu.com/Kernel/Debugging/Backlight](https://wiki.ubuntu.com/Kernel/Debugging/Backlight)

You might want to search for asus-nb-wmi bug also

And post the results from this ```
[COLOR=#000000][FONT=verdana]for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```[/FONT][/COLOR]

---

### Post by TonyPursell on 2014-06-09
Might be the same as my bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1311297](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1311297)

---

### Post by jeremy31 on 2014-06-10
> **TonyPursell said:**
> Might be the same as my bug

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1311297](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1311297)

What happens when you press you brightness hotkeys when using ```
acpi_listen
``` with the original kernel?

And what do you see from this using the 3.15 rc2 ```
lsmod | grep wmi
```

Have you tried ```
acpi_osi=Linux video.use_native_backlight=1
``` in grub

---

### Post by Ashwij on 2014-06-11
Hi Jeremy,


ashwij@ashwij-X550EA:~$ lsmod | grep wmi
asus_nb_wmi            16990  0 
asus_wmi               24697  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
snd_rawmidi            30465  1 snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd                    73979  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
wmi                    19363  1 asus_wmi
video                  19914  1 asus_wmi



I added 
acpi_osi=Linux video.use_native_backlight=1

no change

---

### Post by jeremy31 on 2014-06-11
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
I will need the results from this

---

### Post by jeremy31 on 2014-06-11
And also look at this
[http://forums.linuxmint.com/viewtopic.php?f=49&t=165132](http://forums.linuxmint.com/viewtopic.php?f=49&t=165132)

---

### Post by Ashwij on 2014-06-23
ashwij@ashwij-X550EA:~$ for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done

 /sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory


hi Jeremy31,

Please assist

---

### Post by jeremy31 on 2014-06-23
```
ls /sys/class/backlight
```
and nothing is there, wow
So how about ```
lspci
``` and see what video card is there

---

### Post by jeremy31 on 2014-06-23
```
ls /sys/class/backlight
```
and nothing is there, wow
```
sudo apt-get install xbacklight
```

After it installs try ```
xbacklight -dec 10
```  if it gives error or doesn't work, I have no way to help you as I don't have anything with the same graphics card

---


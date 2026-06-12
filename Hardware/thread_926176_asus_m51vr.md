---
title: "asus m51vr"
date: 2008-09-21
forum: Hardware
---

### Post by DakoCwerf on 2008-09-21
Hello i have 2 problems with my laptop.

**Brightness.**
*solution found in 2nd post.*
display looks very dim. because of specific keyboard my control shortcuts for brightness are moved to fn+F5/F6. still they dont work =)

the main problem is when i try to manually change the brightness level of my display i can enter values only between 1 and 15.

so my proc/acpi/video/VGA/LCDD/brightness file looks like 

> levels:  15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 0
current: 13


that means i cant go more then 15% of my brightness. and thats bad.

some weird thing i've noticed - when i go to sleep mode and come back, my brightness seems to be like 30-40%. somehow it is changed but the current level didnt change.

also, when i load my hardy at the first 5-10% of the loading bar my brightness is ok (really nice and working) but then kernel loads some module and my brightness goes down to 10%...

would appreciate any help with that.

**Sound**
*solution found in 3nd post.*
was not been able to make my sound work. installed latest alsa driver, upgraded backports and changed alsa-base file to use device=lenovo or device=asus. none of them works. my sound device is listed as ICH9 (rev 03). seems like alsa doesnt support it yet? anyone founf solution to make it work?

thanks.

---

### Post by DakoCwerf on 2008-09-21
ok brightness is fixed now, ambient light sensor was a problem, it blocked the brightness control.

so to turn it off - > echo -n 0 > /sys/devices/platform/asus-laptop/ls_switch

to make it works on startup - make a simple script and put in in init.d

A) Open Terminal (Menu->Accessories), and type the following:
```
sudo gedit brightness
```

B) Now paste the following in the Terminal window:
```
#!/bin/sh
echo -n 0 > /sys/devices/platform/asus-laptop/ls_switch
```

C) Save your file. 

D) Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:
```
sudo mv brightness /etc/init.d
sudo chmod 755 /etc/init.d/brightness
sudo update-rc.d brightness defaults 90
```

E) Reboot, and you will have regained control of your brightness level.

---

### Post by DakoCwerf on 2008-09-21
fixed the sound now too.

for simpleness - use script from this topic [http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)
and add at the end of alsa-base
> options snd-hda-intel model=m51va

---

### Post by Jonno_FTW on 2008-10-19
Thanks for the tip, i tried them but wireless still doesn't work, neither does sounds.

---

### Post by ricaxe on 2009-12-03
KARMIC user

A) Open Terminal (Menu->Accessories), and type the following:
```
sudo gedit brightness
```B) Now paste the following in the Terminal window:
```
#!/bin/sh
echo -n 0 > /sys/devices/platform/asus_laptop/ls_switch
```C) Save your file. 

D) Now we will copy our new shell script to the appropriate directory, make it executable and add the following links by typing the following in Terminal:
```
sudo mv brightness /etc/init.d
sudo chmod 755 /etc/init.d/brightness
sudo update-rc.d brightness defaults 90
```E) Reboot, and you will have regained control of your brightness level.

---

### Post by rachael4u on 2009-12-03
thnxxx for the info...

---

### Post by ricaxe on 2009-12-03
> **rachael4u said:**
> thnxxx for the info...


you welcome thats Ubuntu is... :D

i learn from here. when i install karmic these script didn't work and then i realized that the folder as changed on these new realest.

---

### Post by Nailox on 2009-12-08
i fixed the sound by going in system>administration>hardware drivers and i removed the driver for the software modem. thus the internal audio is visible again from the sound preferences menu. in the "hardware" tab i choose the pofile: analog stereo duplex. i don't find any trouble after removing the software modem driver. and thanks for the brightness thing - it really helped me.

---

### Post by djhorry on 2010-10-31
> **DakoCwerf said:**
> Hello i have 2 problems with my laptop.

**Brightness.**
*solution found in 2nd post.*
display looks very dim. because of specific keyboard my control shortcuts for brightness are moved to fn+F5/F6. still they dont work =)

the main problem is when i try to manually change the brightness level of my display i can enter values only between 1 and 15.

so my proc/acpi/video/VGA/LCDD/brightness file looks like 



that means i cant go more then 15% of my brightness. and thats bad.

some weird thing i've noticed - when i go to sleep mode and come back, my brightness seems to be like 30-40%. somehow it is changed but the current level didnt change.

also, when i load my hardy at the first 5-10% of the loading bar my brightness is ok (really nice and working) but then kernel loads some module and my brightness goes down to 10%...

would appreciate any help with that.

**Sound**
*solution found in 3nd post.*
was not been able to make my sound work. installed latest alsa driver, upgraded backports and changed alsa-base file to use device=lenovo or device=asus. none of them works. my sound device is listed as ICH9 (rev 03). seems like alsa doesnt support it yet? anyone founf solution to make it work?

thanks.

Hello! Sorry for being a noob but, is your ASUS m51vr getting really hot while running Ubuntu?

---


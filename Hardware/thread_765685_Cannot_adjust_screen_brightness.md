---
title: "Cannot adjust screen brightness"
date: 2008-04-24
forum: Hardware
---

### Post by jwwadk on 2008-04-24
Hello all, apologies if this sounds like a noob-ish question. I upgraded to Hardy today from Gutsy, and my screen seems very dim. My computer is an Asus M50sv-a1 laptop dual-booting with Vista, and it has shortcut keys for adjusting the brightness. Using Gutsy, these shortcut keys worked just fine (they're Fn+F5 and Fn+F6) and adjusted my brightness accordingly. However, they do nothing using Hardy. I looked at Power Management and the options for adjusting screen brightness seems to have disappeared, and the /proc/acpi/video/VGA/LCDD/brightness trick refuses to work for me. As it is, I'm straining to see my screen, so any help would be greatly appreciated.
Thanks

---

### Post by apu95 on 2008-04-24
I also have this problem, but I haven't upgraded from Gutsy. I just did a fresh install on the same laptop (it's brand new, I got it on Monday).
I did a little digging and found out that in /sys/class/backlight there's two symbolic links, one named acpi_video0 and another one called asus-laptop. 

Under acpi_video0, there's a few files, which when viewed in a text editor shows this:

File: actual_brightness
Contents: 1

File: brightness
Contents: 0

File: max_brightness
Contents: 13

File: bl_power
Contents: 0

Now, in the asus-laptop folder, the same files are present, but the values are these:

File: actual_brightness
Contents: 12

File: brightness
Contents: 12

File: max_brightness
Contents: 15

File: bl_power
Contents: 0

It seems that the one being used is acpi_video0, since it has the lower values for the LCD brightness. I'm not sure how to go about making the system use the other values... Like jwwadk, I can't use the Fn + F5/F6 keys to increase/decrease brightness either.

A quick view of my dmesg log shows this:
[   27.140807] asus-laptop: Asus Laptop Support version 0.42
[   27.141437] asus-laptop:   M50SV model detected

So it's detecting my laptop correctly and using the ACPI module for ASUS laptops... not sure if that has anything to do with it.

Hopefully someone can shed light on this... it's a pain in the butt working with the low brightness of the LCD...

---

### Post by ]Nbx*cmD[ on 2008-04-25
ok found a solution for u guys using ASUS M50sv laptop.

The problem seems to be with the lihght sensor, which doesn't work properly.

First of all, take a torchlight and point it to the sensor (right to the right of the "ALTEC LANSING" writing on the top of your keyboard) and... voila! lights up!

Ok, here's the fix:

> 
$sudo su
#echo 0 > /sys/devices/platform/asus_laptop/ls_switch


This will put a 0 in the ls_switch file, telling your laptop to NOT use the light sensor, which will give you the control of your brightness back.

Hope it helps!

Taken from: [http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us)

---

### Post by ]Nbx*cmD[ on 2008-04-25
ok found a solution for u guys using ASUS M50sv laptop.

The problem seems to be with the lihght sensor, which doesn't work properly.

First of all, take a torchlight and point it to the sensor (right to the right of the "ALTEC LANSING" writing on the top of your keyboard) and... voila! lights up!

Ok, here's the fix:

> 
$sudo su
#echo 0 > /sys/devices/platform/asus_laptop/ls_switch


This will put a 0 in the ls_switch file, telling your laptop to NOT use the light sensor, which will give you the control of your brightness back.

Hope it helps!

Taken from: [http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us)

---

### Post by neonflx on 2008-04-25
greeeeeaaaatttttttt  :lolflag: i can see my screen

---

### Post by yadayada2 on 2008-04-25
I don't have such a file in my sony_laptop directory. What should I do?

---

### Post by haseeb on 2008-04-25
Yet another "Temporary solution"

Right click on the task bar. And select **Brightness Applet** and drag it to the task bar.

Click the brightness applet icon. And set your brightness.

The problem of this solution is, change of brightness is not permanent.Every time you start your laptop you have to set the brightness from the bar.

Thanks.

[IMG]http://farm3.static.flickr.com/2137/2441995210_0518169eed_o.png[/IMG]

---

### Post by apu95 on 2008-04-26
> **']Nbx*cmD[ said:**
> ok found a solution for u guys using ASUS M50sv laptop.

The problem seems to be with the lihght sensor, which doesn't work properly.

First of all, take a torchlight and point it to the sensor (right to the right of the "ALTEC LANSING" writing on the top of your keyboard) and... voila! lights up!

Ok, here's the fix:



This will put a 0 in the ls_switch file, telling your laptop to NOT use the light sensor, which will give you the control of your brightness back.

Hope it helps!

Taken from: [http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us)

Aw man, that was fantastic, thanks so much!!! =D
It was so funny, I turned on my cell phone's light and put it close to the sensor, and the screen started lighting up xD... Thanks for the fix again ^_^

---

### Post by ]Nbx*cmD[ on 2008-04-27
lol
glad it helped :)

---

### Post by hotweiss on 2008-05-19
> **']Nbx*cmD[ said:**
> ok found a solution for u guys using ASUS M50sv laptop.

The problem seems to be with the lihght sensor, which doesn't work properly.

First of all, take a torchlight and point it to the sensor (right to the right of the "ALTEC LANSING" writing on the top of your keyboard) and... voila! lights up!

Ok, here's the fix:



This will put a 0 in the ls_switch file, telling your laptop to NOT use the light sensor, which will give you the control of your brightness back.

Hope it helps!

Taken from: [http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us)

I keep on getting this error when following your instructions:

bash: /sys/devices/platform/asus_laptop/ls_switch: No such file or directory

---

### Post by gganitis on 2008-05-19
> **']Nbx*cmD[ said:**
> ok found a solution for u guys using ASUS M50sv laptop.

The problem seems to be with the lihght sensor, which doesn't work properly.

First of all, take a torchlight and point it to the sensor (right to the right of the "ALTEC LANSING" writing on the top of your keyboard) and... voila! lights up!

Ok, here's the fix:



This will put a 0 in the ls_switch file, telling your laptop to NOT use the light sensor, which will give you the control of your brightness back.

Hope it helps!

Taken from: [http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us)




In my case this didn't work. (HP notebook with nvidia card):
bash: /sys/devices/platform/asus_laptop/ls_switch: No such file or directory

But reinstalled the nvidia restricted driver and everything worked right! It was really dark for days, and I've seen the light! I don't know yet if I can adjust the brightness. The brightness applet in my panel doesn't work.

---

### Post by redcathy on 2008-06-09
Thanks a lot for this, for me ```
echo 0 >/sys/devices/platform/asus-laptop/ls_switch
``` worked (note the dash, rather than underscore in asus-laptop).  You can check the file path by navigating along it.

Now all I need to do is make this happen automatically!!

---

### Post by Waffle07 on 2008-10-25
> **']Nbx*cmD[ said:**
> ok found a solution for u guys using ASUS M50sv laptop.

The problem seems to be with the lihght sensor, which doesn't work properly.

First of all, take a torchlight and point it to the sensor (right to the right of the "ALTEC LANSING" writing on the top of your keyboard) and... voila! lights up!

Ok, here's the fix:



This will put a 0 in the ls_switch file, telling your laptop to NOT use the light sensor, which will give you the control of your brightness back.

Hope it helps!

Taken from: [http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us)

Hi guys!

Sorry for resurrecting this thread but this seams to be my problem (I just installed Ubuntu). But I'm a total noob at this stuff. My question is, where do I type in this code to fix my problem?

Thanks, Dave

---

### Post by jwwadk on 2008-10-25
You type it into the Terminal, which you can get to by Applications > Accessories menu in the top-left of your screen.

Hope it works.

---

### Post by Waffle07 on 2008-10-25
Ok I copied the code in but it keeps asking me for a password, the terminal looks like this. I tried entering my login password but nothing happens when i type.

dave@dave-laptop:~$ $sudo su
Password: (I type stuff but it doesnt show anything here)

---

### Post by jwwadk on 2008-10-25
Right, it won't show anything there. That's just how it is. The password you should type is the password that you use to log in to the computer. Even though you might not see anything showing up after the password prompt, text is being entered.

---

### Post by Waffle07 on 2008-10-25
Whoa, OK i got it!!!! i just needed to type the sudu su (with no$ sign) entered my password like you said and it worked. Then I got the bash error, but I changed the underscore to a dash like the guy said above and bam my screen is bright as hell now!!

Thanks for your help!!!

---

### Post by Waffle07 on 2008-10-25
One more question. I restarted my computer and it went back to its original state(I cant adjust the brightness again). Anyway to fix this?

---

### Post by jwwadk on 2008-10-25
This site:

[http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/](http://seethisnowreadthis.com/2008/05/19/how-to-install-ubuntu-804-hardy-heron-on-the-asus-m50sv-a1/)

shows how to fix the problem nicely.

Good luck!

---

### Post by neorg on 2008-10-25
On my Asus M51 V-series laptop I installed Intrepid. It works great, including the auto adjuster for the screen brightness. Most of the time this works great but sometimes, particularity in the evening, it still to bright. I create the following solution.

I made a simple script that can switches the sensor ON and OFF and controle it by de main menu.

```

#!/bin/bash

INPUT=$1

if [ $INPUT = "--on" ]
then
        echo 1 > /sys/devices/platform/asus-laptop/ls_switch
fi

if [ $INPUT = "--off" ]
then
        echo 0 > /sys/devices/platform/asus-laptop/ls_switch
fi


```

Save the scrip wherever you want, lets say in ~/bin/ and name it brightness-switch.sh

so the script is now on /home/YOUR-LOG-IN/bin/brightness-switch.sh

make the scrip executable (chmod u+x ~/bin/brightness-switch.sh)

run the scrip to switch off the sensor
```
gksudo "sh ~/bin/brightness-switch.sh --off"
```
(Notice that you have to be root to switch the sensor on anf off)
 
run the scrip to switch on the sensor
```
gksudo "sh ~/bin/brightness-switch.sh --on"
```

If this works fine you make a menu entry System -> Preferences -> Main Menu and to create two entrys. One for sensor ON and one for Sensor Off (see screenshot)

I also made 2 brightness icons On and OFF that you can use free for your menu. Save them in ~/.icons

Good luck!!

---


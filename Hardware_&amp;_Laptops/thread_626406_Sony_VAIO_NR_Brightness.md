---
title: "Sony VAIO NR Brightness"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by amdma2003 on 2007-11-29
I just recently got a Sony VAIO VGN-NR110E, and I formatted the hard drive in hopes of installing WinXP. However, I can't, so now I'm using Ubuntu 7.10 for the first time, and I'm liking it so far.

One of the problems I'm having is the brightness of the screen. I can't change it, even in the control panel.

When I looked at the hardware information, I didn't see a "sony_acpi" and I think that might be the problem. Does anyone know how and where I can install sony_acpi?

---

### Post by elantris on 2007-11-29
I also just got an NR180E and i am having the same issue with brightness and only my FN key for mute works.  I wiped Vista for Kubuntu 7.10, i am a newbie to Kubuntu/linux in general.  So far i like this better then XP and am seriously thinking about installing it on my other Vaio SZ230P, if i can get the issues resolved with this Vaio.  So any and all help will be much appreciated.

---

### Post by ktru on 2007-12-03
Did anyone get this problem solved? I'm having the same issues right now too :|

---

### Post by sebo123 on 2008-02-11
I have also NR serie - sony vaio nr21

for me 
xbacklight -set 40 work :) (try it)

but I can't set brightness with spicctrl too :
spicctrl --setbrightness=50 didn't works


```

lsmod | grep sony
sony_laptop            32088  0
sonypi                 23960  0

```

rmmod sonypi gives me :
```

dmesg
 5713.172000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
[ 5713.216000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
[ 5713.240000] sonypi: removed.

```

```

modprobe sonypi
dmseg
[ 5892.816000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[ 5892.816000] sonypi: please try the sony-laptop module instead and report failures, see also http://www.linux.it/~malattia/wiki/index.php/Sony_drivers
[ 5892.816000] sonypi: detected type2 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[ 5892.816000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[ 5892.816000] sonypi: device allocated minor is 63
[ 5892.816000] input: Sony Vaio Jogdial as /class/input/input16
[ 5892.816000] input: Sony Vaio Keys as /class/input/input17
[ 5892.864000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
[ 5892.908000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
[ 5892.952000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
[ 5892.992000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)

```

```

uname -a
Linux desire 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686 GNU/Linux

```

```

spicctrl -B
0
spicctrl -a
0

```

---

### Post by pwn on 2008-02-14
Neither of them worked on my Vaio (AR series)


death@pwned:~$ xbacklight -get
No outputs have backlight property

death@pwned:~$ spicctrl -B
0

---

### Post by L815 on 2008-02-25
Excellent thank you. spicctrl didn't work but xbacklight did.

I'm on a Vaio VGN-FZ240E

Now is there a way to have this execute when the battery is activated? Of if someone knows where the batter configuration (detect if it's plugged or not) is, I might be able to figure out how to set it automatically.

---

### Post by diegosouza on 2008-03-06
Hello people,
I have a Sony NR180E and xbacklight works fine!

Thanks sebo123
:)

---

### Post by sebo123 on 2008-03-09
L815:
>  Now is there a way to have this execute when the battery is activated? Of if someone knows where the batter configuration (detect if it's plugged or not) is, I might be able to figure out how to set it automatically.

I have looked to acpi init scripts and I found  "/etc/acpi/battery.d/" directory ...
create file here, e.g name should be "16-set_brightness.sh", it depend on the names of the other script in this direcory, so create file:
touch /etc/acpi/battery.d/16-set_brightness.sh

set execute permissons to it :
chmod +x  /etc/acpi/battery.d/16-set_brightness.sh

and put this code to this file (dont forget replace "sebo" with your username!!!):
```

#! /bin/sh

export HOME=/home/sebo
export DISPLAY=:0

/usr/bin/xbacklight -set 20

```

for me this solution works, but I am not well in acpi scripts, maybe you will find better solution

---

### Post by wieman01 on 2008-04-01
I have file a bug report here:

[https://bugs.launchpad.net/ubuntu/+bug/210103]("https://bugs.launchpad.net/ubuntu/+bug/210103")

Apparently other Sony Vaio users are faced with the same issue as outlined.

---

### Post by rockmanac on 2008-04-10
No dice with my VGN-NR110E on Hardy.

---

### Post by Paco758 on 2008-04-18
I have the same problem with a Vaio VGN-NR290E. I can alter the backlight setting with xbacklight only. I have attempted to alter the keymap to include the specific model. This was not successful. 

Also, as of this date, running 8.04 Hardy Beta, I need to run "xrandr --output LVDS --set BACKLIGHT_CONTROL native" in order to control the brightness using xbacklight in a terminal. Otherwise there is no response.

---

### Post by drlisacuddy on 2008-05-08
I have a NR110E and I had to use "xrandr --output LVDS --set BACKLIGHT_CONTROL native" in order for xbacklight to actually work for me; currently i have a panel item to set the brightness to a certain level with one click (set at 70) although i would like for the slider in the brightness applet to actually work. Using Hardy 8.04.

---

### Post by wieman01 on 2008-05-08
An upgrade to Hardy solved it for me.

---

### Post by jabali on 2008-05-16
I have the same problem with my vaio nr21s, NVIDIA GeForce 8400M GT
Ubuntu 8.04 
xbacklight doesn't work for me: "No outputs have backlight property"
spicctrl -B
0

does anybody solve this problem?
thanks a lot

---

### Post by diegosouza on 2008-05-18
> **Paco758 said:**
> I have the same problem with a Vaio VGN-NR290E. I can alter the backlight setting with xbacklight only. I have attempted to alter the keymap to include the specific model. This was not successful. 

Also, as of this date, running 8.04 Hardy Beta, I need to run "xrandr --output LVDS --set BACKLIGHT_CONTROL native" in order to control the brightness using xbacklight in a terminal. Otherwise there is no response.

Thank you Paco758, you solved my problem with the Ubuntu 8.04!

---

### Post by fabrix on 2008-05-28
Same problem with vaio nr21z, can't change backlight,so before spend more money to buy a new sunglasses i have a question for you.......
Have someone tried to recompile dsdt table?
Because in my log I found this message:
“ACPI: Looking for DSDT in initramfs… file /DSDT.aml not found, using machine DSDT.”

Sorry for my bad english & tanks for any answer

---

### Post by barlas on 2008-06-01
After using ```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
``` xbacklight work for me now.

I am using VGN-NR220E

---

### Post by panzet on 2008-06-21
Hello everybody,

wieman01, which is your VAIO model, and what you did to solve it before/after ubuntu's upgrade?

I have a VAIO VGN-NR10M with Ubuntu 8.04 and I have to run the command

```
xrandr --output LVDS --set BACKLIGHT_CONTROL native
```

every time after Ubuntu starts, to use the xbacklight commands.

I have tested the method from

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/173652]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/173652")

to run a script that do it automatically at ubuntu's start, but none happens, and I have to run the "xrandr..." command to use xbacklight too. There is another methods proposed in the web, but none of them works for me. For example, the method that propose to run:

```
sudo locate -u && for i in $(locate lcd-???-brightness); do sudo cp $i $i.bak; sudo sed -i '1 s|#!/bin/sh|#!/bin/bash|g' $i; done
```

do not work for me, because it says that -u is a invalid option for the command "locate".

@ sebo123, I think that I need to have first the xbacklight running to use your batterie's-mode script... but I've not tried yet. Is possible to use your script without running the "xrandr"?

Anyway, at least I can modify the brightness of my vaio. Any other solution for Vaio VGN-NR users?

Thanks a lot for everybody, this is a very helpful forum!!

Panzet

PD: sorry about my english.:)

---

### Post by fetchinson on 2008-06-21
This won't solve the problem of those of you who can't use xbacklight, but thought that maybe you'll find this helpful: I've written a gtk based GUI called gbacklight that can be used to control screen brightness. It's pure C and the only dependencies are X and GTK:

[http://code.google.com/p/gbacklight/](http://code.google.com/p/gbacklight/)

---

### Post by leandromartinez98 on 2008-06-22
> **fetchinson said:**
> This won't solve the problem of those of you who can't use xbacklight, but thought that maybe you'll find this helpful: I've written a gtk based GUI called gbacklight that can be used to control screen brightness. It's pure C and the only dependencies are X and GTK:

[http://code.google.com/p/gbacklight/](http://code.google.com/p/gbacklight/)

I found your package nice. I had, however, to create a calling
script that runs the xrand command before. Thanks for sharing.

By the way, I'm using Hardy, and the brightness only works with
the xrand+xblacklight combination. I have had problems before
in my X while using xrand, and then I have stoped using it, I'm
not sure it was the cause of the problems though. The Fn/F5/F6 do
not work anyway, so I think the problem persits.

(Vaio VGN-NR11Z/S)

---

### Post by pihhan on 2008-06-24
Hello,

i made some instructions to get sony hotkeys working. I believe it might help you when configuring FN+F5 and such keys. If you are lucky and have powermanager backlight control working, you should get nice backlight control.

see [http://www.pihhan.info/sony/sony-hotkeys.html](http://www.pihhan.info/sony/sony-hotkeys.html)

If you have working xbacklight and want to map it to hotkeys, it should work also if you try scripts from my archive [http://www.pihhan.info/sony/sony-fz-fnkeys-2008-05-21.tar.gz](http://www.pihhan.info/sony/sony-fz-fnkeys-2008-05-21.tar.gz)
I dont have detailed instructions for its installation, but you should be able to install it, if you understand scripting in linux a little. It should be working after extracting to root, but i suggest you backup original files and replace them by hand.

---

### Post by chetan.89 on 2008-07-10
Thank you so much sebo123 !! You really made my day :)

I'm using a Sony VAIO NR-385E laptop with Ubuntu 7.10 Gutsy Gibbon.

---


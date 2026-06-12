---
title: "Asus G50/G71v OLED daemon"
date: 2008-11-03
forum: Hardware
---

### Post by essexboyracer on 2008-11-03
Are there any Asus Laptop G50 or G71v owners out there that have managed to get the OLED Daemon working on heron 8.04? 

I tried it following instructions from [http://asusg50oled.sourceforge.net/](http://asusg50oled.sourceforge.net/) but all I get is:

oliver@G71V:~/Desktop/asusg50oled$ ./start.sh
oliver@G71V:~/Desktop/asusg50oled$ Sorry, cannot write to the asus_oled device. Please check if asus_oled driver is loaded.


Any Ideas Asus Gaming Laptop Owners?

---

### Post by costing on 2008-11-09
Make sure you have loaded the asus_oled module _before_ usbhid. A safe sequence is:
$ sudo su -
# rmmod usbhid
# modprobe asus_oled
# modprobe usbhid

You can check with dmesg to see if the device is properly detected:
dmesg | grep asus
[   22.565218] asus-laptop: Asus Laptop Support version 0.42
[   22.569052] asus-laptop:   G50V model detected
[   22.574139] Registered led device: asus::touchpad
[   23.216917] asus-oled 4-4:1.0: Attached Asus OLED device: G50 [width 256, pack_mode 1]
[   23.216933] usbcore: registered new interface driver asus-oled

If you don't see the "G50V model detected" it usually means that you didn't get the SVN version of asus_oled (0.03 release doesn't have support for G50/G70). If this is the case, do this:

$ sudo su -
# cd /usr/src/
# svn co svn://svn.berlios.de/lapsus/asus_oled/trunk asus_oled
# cd asus_oled
# make install

---

### Post by essexboyracer on 2008-11-14
Did dmesg first, got this...

[   48.336981] asus-laptop: Asus Laptop Support version 0.42
[   48.337198] asus-laptop:   G71V model detected
[   48.342099] Registered led device: asus:mail
[   48.342110] Registered led device: asus:touchpad

then did the module loading safe sequence and got this

[   48.336981] asus-laptop: Asus Laptop Support version 0.42
[   48.337198] asus-laptop:   G71V model detected
[   48.342099] Registered led device: asus:mail
[   48.342110] Registered led device: asus:touchpad
[ 2051.475797] usbcore: registered new interface driver asus-oled

ran ./start.sh - still no joy so
then downloaded the SVN but got errors on make...

root@G71V:/usr/src/asus_oled# make
make -C /lib/modules/2.6.24-21-generic/build SUBDIRS=/usr/src/asus_oled modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /usr/src/asus_oled/asus_oled.o
/usr/src/asus_oled/asus_oled.c: In function &#8216;asus_oled_probe&#8217;:
/usr/src/asus_oled/asus_oled.c:626: error: implicit declaration of function &#8216;device_create_drvdata&#8217;
/usr/src/asus_oled/asus_oled.c:627: warning: assignment makes pointer from integer without a cast
make[2]: *** [/usr/src/asus_oled/asus_oled.o] Error 1
make[1]: *** [_module_/usr/src/asus_oled] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: *** [default] Error 2

root@G71V:/usr/src/asus_oled# make install
install -d /lib/modules/2.6.24-21-generic/extra/
install -m 644 -c asus_oled.ko /lib/modules/2.6.24-21-generic/extra/
install: cannot stat `asus_oled.ko': No such file or directory
make: *** [install] Error 1
root@G71V:/usr/src/asus_oled# 


ps: did you have any problems with sound on your asus?

---

### Post by costing on 2008-11-14
So you are still using the original kernel that comes with 8.04... To have sound, wireless and have asus_oled compile you need a newer one (2.6.27.6 for example). So you either upgrade to ubuntu 8.10 that has it by default or have a look here to see how you can compile the latest kernel on 8.04: [http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/](http://monalisa.cern.ch/blog/2008/09/16/ubuntu-on-asus-g50v/)

---

### Post by essexboyracer on 2008-11-16
weird, upgraded to 8.10 but amstill using 2.6.24-21-generic...?

Leave it with me costin and thank you for all your help

---

### Post by essexboyracer on 2008-11-16
Sorted, I fell foul of the upgrade bug where you dont update menu.1st, the update-grub doesn't recognize the new kernel.

The OLED is working great! Going to have a look at the cool stuff I can put in there

---

### Post by costing on 2008-11-16
Nice :) Let me know if you have any feature requests from the daemon.

---

### Post by essexboyracer on 2008-11-16
Yeh, rebooted and nothing again with the OLED. Will need to take a proper look. Unfortunately after getting my sound working I cant stop listening to the Snowblower by B. Baker Chocolate Co. - Damn jazz-funk

ps - sound on linux has never come close to Windows in terms of media players like Winamp, WMP et al. How come?

pps - OLED FEATURE REQUEST(S):

[LIST]
[*]Proximity Alert for when the wife is around...
[*]TV Programme Warning
[/LIST]

---

### Post by costing on 2008-11-16
You have to do again the trick with "rmmod usbhid; modprobe asus_oled; modprobe usbhid" before starting the app ... I hacked the usbhid module to get rid of this problem, but I guess an option is to either modify start.sh to execute this sequence before starting the application or putting it in /etc/rc.local. But since /etc/rc.local is executed last at boot, it might be too late if you start the daemon before it. Or maybe just adding asus_oled to /etc/modules makes it load before usbhid ... Let me know which of these (or other solution) works for you to update the page with this final touch :)

You can try Amarok for sound, it's pretty neat ... I wouldn't know how it compares to Windows apps, but for me it's complicated more than enough :)

---

### Post by costing on 2008-11-16
Now about the wife-sensing module... It's hard to implement a proper mind-reading module :( . But you might try to configure KBlueMon or a similar app to notify you when a certain BT device is nearby :D

But an alarm system would indeed be a nice addition to the OLED daemon. One could use it to schedule arbitrary events, like TV shows ... Thanks, I'll think about it ;)

---

### Post by seuaniu on 2008-11-29
Would just like to chime in and say I got this working on my G50V this morning, on 8.10.  Awesome software, and the guide on sf.net worked great.

---

### Post by Ev1L on 2009-04-25
Hi, I have a G1 and so far it just removed the blue ASUS message.
leds.log tells:
> ASUS G1 forced in the configuration file
Found an ASUS OLED device under '/sys/class/asus_oled/oled_1/picture'
dcop: found in /usr/bin
Getting the battery info from /sys/class/power_supply/BAT0/{energy_full,energy_now}
Reading CPU temperature from /sys/class/thermal/thermal_zone0/temp


---

### Post by abeowitz on 2009-08-06
This works for me, and is a great tool!

But I've got a G71G, which has quad core...

The last line with the 4 cpu freqs are overwriting the time/uptime text.

How can I move it over 4 or 5 characters to the right?

---

### Post by abeowitz on 2009-08-06
Nevermind, I got this to work... :)

 c.drawString(s, this.x+this.width + 55, this.y+this.height, Canvas.ALIGN_RIGHT);

---

### Post by costing on 2009-08-06
It's probably better to use the configuration file to change the position of this module:

leds.modules.CPUFreq.x=120 (?)

If you use config.properties to change the position it's easier to upgrade at a later time, otherwise you will have to hack it again :)

---

### Post by chalkos on 2010-09-13
Anyone got this to work on ubuntu 10.04?

I have configured according to instructions. I have a G1.
```
# lsusb | grep 0b05:1726
Bus 001 Device 003: ID 0b05:1726 ASUSTek Computer, Inc. Laptop OLED Display
```

When I try start.sh this is what I get
```
ASUS G1 forced in the configuration file
Found an ASUS OLED device under '/sys/class/asus_oled/oled_3/picture'
dcop: couldn't find anywhere on the system. If you have it, please set 'Utils.dcop_path' in the configuration file to point to it
Getting the battery info from /sys/class/power_supply/BAT0/{energy_full,energy_now}
Reading CPU temperature from /sys/class/thermal/thermal_zone0/temp
```
And it hangs there. The led does not change.

When I try notify.sh (in utils folder) providing a string as argument I get no output on the console and the led changes from the "ASUS" message to fully lit.

Any help would be appreciated

---

### Post by chalkos on 2010-09-14
I just turned on my laptop and the OLED is working. Just had to reboot :popcorn:

---

### Post by yax51 on 2011-03-11
Anyone else having difficulty in getting the GPU temperatureto work? I can get the HDD temp, and CPU temp, but not the GPU. I have nvclock installed, and when I use: nvclock -T -f in the terminal I get the GPU temp output, like I should, and the module leds.module.GPUTemperature says thats what its supposed to do, but I get nothing on my oled...any ideas?

---


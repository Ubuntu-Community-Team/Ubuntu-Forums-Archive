---
title: "Not getting optimal 2560x1440 60Hz resolution"
date: 2018-08-26
forum: Hardware
---

### Post by maventulep on 2018-08-26
I am running Ubuntu 18.04 LTS on a Gigabyte GB-BXi5H-4200 (Intel Core i5-4200H and 4400 graphics) and I am not getting the optimal resolution of 2560x1440 @60Hz on a 25" Philips monitor through HDMI. Instead I'm getting 1920x1080.
The only thing I found about the Brix system is: HDMI Resolution (Max.) 4096 x 2160 @24Hz. That doesn't help much.

The 2560x1440 @60Hz resolution and refresh rate is quoted by Philips as the resolution for the best results for their monitor.

I tried the steps laid out here: [http://ubuntuhandbook.org/index.php/...buntu-desktop/]("http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/"),  but to no avail, the resolution didn't take :sad:

***However***, it may be interesting to mention that the screen resolution got picked  up automatically and correctly (2,560x1,440) by Ubuntu 14.04 LTS on  exactly the same hardware. [I]What gives?


[/I]How do I go about fixing this? Any help greatly appreciated!

---

### Post by Autodave on 2018-08-26
Did you upgrade or do a clean install?

---

### Post by maventulep on 2018-08-26
Clean install. 

However, the install was on a 1920x1080 monitor connected through HDMI.

The 14.04 install was initially also on a 1920x1080 monitor. 2560x1440 worked plug and play, though. No settings to tweak.

---

### Post by jetpeach on 2018-08-27
I have basically the same issue - I got 2560x1440 working with xrand though- but the cvt command gave the wrong output (apparently it isn't always right.)

i found my correct modeline inside a log -- i ran

cat /var/log/Xorg.0.log 

and saw this line
  7640.135] (II) modeset(0): Printing DDC gathered Modelines:
  7640.135] (II) modeset(0): Modeline "2560x1440"x0.0  241.50  2560 2608 2640 2720  1440 1442 1447 1481 +hsync +vsync (88.8 kHz eP)

that gave away that while the resolution wasn't showing up, the line was detected somewhere at least!

so i then ran 
sudo xrandr --newmode "2560x1440_60"  241.50  2560 2608 2640 2720  1440 1442 1447 1481 +hsync +vsync
sudo xrandr --addmode HDMI-1 2560x1440_60

and inside display preferences (in system settings, but i'm on Kubuntu) I then could successfully change to 2560x1440.

for refernces, this was my wrong cvt out
cvt 2560 1440 60
# 2560x1440 59.96 Hz (CVT 3.69M9) hsync: 89.52 kHz; pclk: 312.25 MHz
Modeline "2560x1440_60.00"  312.25  2560 2752 3024 3488  1440 1443 1448 1493 -hsync +vsync

which when i tried, would not switch...

now i'm searching the forums to see the best way to get this added (properly) to a config file

---

### Post by maventulep on 2018-08-27
Thanks for the input! Will look into it when I get home.

---

### Post by maventulep on 2018-08-27
Hmm, it would help if there were Xorg logs under /var/log...

I assume that has something to do with the whole Xorg-Wayland dynamic going on in 18.04? Any suggestions as to where to dig for this kind of output instead?

---

### Post by Yellow Pasque on 2018-08-29
Ubuntu 18.04 does not use Wayland by default. They tried it in 17.10 and decided it wasn't yet stable enough for an LTS release. Have you manually selected Wayland?

---

### Post by jesstv on 2018-10-29
> **maventulep said:**
> Hmm, it would help if there were Xorg logs under /var/log...

I assume that has something to do with the whole Xorg-Wayland dynamic going on in 18.04? Any suggestions as to where to dig for this kind of output instead?

I found the log (and the correct line) under [COLOR=#008000] [FONT=monospace]~/.local/share/xorg/Xorg.0.log[/FONT] [/COLOR] -- try there.

Once I found the right file, I got the exact line by running [COLOR=#008000] [FONT=monospace]grep 2560 ~/.local/share/xorg/Xorg.0.log[/FONT] [/COLOR] (since 2560x1440 was the resolution I was looking for). It gave me:
```
"2560x1440"x0.0  241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
```
vs the following from [COLOR=#008000] [FONT=monospace]cvt[/FONT] [/COLOR] that most unhelpfully gave me a blank screen:
```
"2560x1440_60.00"  312.25  2560 2752 3024 3488  1440 1443 1448 1493 -hsync +vsync
```

Note the radically different clock and inversion of the sync polarity! I should be thankful my monitor's smart enough to shrug that off and go blank... I know some older CRTs would go ***pop* **if you drove them wrong!

Thanks @jetpeach for the tip!

---

### Post by ilyuha21st on 2018-11-30
Hi maventulep,
I'm going to buy a new monitor and have some doubts about the resolution. I consider two option right now: 2560x1440 and 4K(3840x2160). Did you expect the issues while using your setup with  2560x1440? Looks like this is not x2 number to 1920x1080 which potentially could lead to some problems. Any advice or suggestion is welcome.

---

### Post by comperem on 2018-12-30
jetpeach,

Thanks. This worked like a champ on Ubuntu 18.04.1 LTS with Mate desktop and Samsung LC27H711QENXZA C27H711 27-Inch WQHD QLED Curved Monitor.

My display parameters were just slightly different in [FONT=Courier New]/var/log/Xorg.0.log[/FONT] but the two commands executed without error. My monitor happened to be plugged into HDMI port 2:
[FONT=Courier New]
[INDENT]xrandr --newmode "2560x1440" 241.50  2560 2608 2640 2720  1440 1443 1448 1481 +hsync -vsync
xrandr --addmode HDMI-2 2560x1440[/INDENT]
[/FONT]

This immediately provided the 2560x1140 resolution through the Mate Display dialogue.

---

### Post by kalnitz on 2019-07-12
Did you ever figure out how to add this to a config file and have it work all the time? I was having the same problem and this fixes it but is not permanent. Thanks!

> **jetpeach said:**
> I have basically the same issue - I got 2560x1440 working with xrand though- but the cvt command gave the wrong output (apparently it isn't always right.)

i found my correct modeline inside a log -- i ran

cat /var/log/Xorg.0.log 

and saw this line
  7640.135] (II) modeset(0): Printing DDC gathered Modelines:
  7640.135] (II) modeset(0): Modeline "2560x1440"x0.0  241.50  2560 2608 2640 2720  1440 1442 1447 1481 +hsync +vsync (88.8 kHz eP)

that gave away that while the resolution wasn't showing up, the line was detected somewhere at least!

so i then ran 
sudo xrandr --newmode "2560x1440_60"  241.50  2560 2608 2640 2720  1440 1442 1447 1481 +hsync +vsync
sudo xrandr --addmode HDMI-1 2560x1440_60

and inside display preferences (in system settings, but i'm on Kubuntu) I then could successfully change to 2560x1440.

for refernces, this was my wrong cvt out
cvt 2560 1440 60
# 2560x1440 59.96 Hz (CVT 3.69M9) hsync: 89.52 kHz; pclk: 312.25 MHz
Modeline "2560x1440_60.00"  312.25  2560 2752 3024 3488  1440 1443 1448 1493 -hsync +vsync

which when i tried, would not switch...

now i'm searching the forums to see the best way to get this added (properly) to a config file

---


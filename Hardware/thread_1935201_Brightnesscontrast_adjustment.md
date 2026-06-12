---
title: "Brightness/contrast adjustment"
date: 2012-03-03
forum: Hardware
---

### Post by Spae on 2012-03-03
Hi, i have a aspire as5750 which is running the intel hd 3000 graphics. Ubuntu 11.10.

I have tried using the function keys and the screen settings in ubuntu. When i use the function keys a little dial shows up and it seems to be adjusting on the dial but it isn't changing my screen brightness. Same with the dial in ubuntu settings.

I have tried searching this forum and elsewhere but it's hard to know what to do still. Because i'm not sure what posts were only relevant to the specific laptop/ubuntu version/graphics they were using.

But really the screen is too bright even for general use at normal angles. if i tilt the screen back far the colours look much better. But also i want this so i can save power as well.

Also in the colour settings i can't change anything because it is un-calibrated. "The measuring instrument is not detected please check it is turned on and properly detected."

---

### Post by gordintoronto on 2012-03-04
Have you run System Settings/Displays? I think there is a slider for brightness. However, it has no effect on some computers.

---

### Post by Spae on 2012-03-04
Yes, it does nothing.

In colour options it says un-calibrated because none of the default profiles work. I am wondering if i could set up one some how whether i would then be able to adjust the brightness.

---

### Post by NickoHall on 2012-03-04
Hi,

I'm having the exact same problem on my HP dv6. I press the brightness hotkeys and a box does pop up moving the slider up and down but it makes no effect on the actual brightness. I'd really love to be able to lower the brightness a tad as I dont need it all the way up and i'd like to be able to save some battery.

cheers :)

---

### Post by utnubuuser on 2012-03-04
There is undoubtedly a proper solution for your respective laptops, and in the meantime you might be able to use xgamma to tone your screen down a little

I believe the command is something like this:> 'xgamma -rgamma 1 -ggamma 1 -bgamma 1'
and you adjust the brightness in increments of .1  ie:> 'xgamma -rgamma .9 -ggamma .9 -bgamma .9'
 

or simplified > xgamma -gamma .5
or > xgamma -gamma .25

xgamma is adjutable to 3 decimal places.

man xgamma 
[http://linuxcommand.org/man_pages/xgamma1.html]("http://linuxcommand.org/man_pages/xgamma1.html")
As I stated, it's not a real solution, though it might help until you find said solution

---

### Post by Spae on 2012-03-04
Mmm yeah that works somewhat. Having on .9 is definitely an improvement. Thanks.

I hope maybe there will be a fix for this is an update.

---

### Post by siepo on 2012-03-04
I use xbacklight and dim the display with a command

xbacklight -set 40

(or 20 or 60 or whatever). Works great.

---

### Post by Spae on 2012-03-04
^that didn't work. Probably the same reason everything else didn't.

---

### Post by NickoHall on 2012-03-05
That didn't work for me either :( I'd really love to fix this since I need to maximize my battery life for school.

---

### Post by hannah187 on 2012-03-05
Hi, Not planning to hijack this thread.. but am having similar problem..my issue is well documented here:
[http://www.backtrack-linux.org/forums/showthread.php?t=48392](http://www.backtrack-linux.org/forums/showthread.php?t=48392)

xbacklight returns No outputs have backlight property


any solution please..

---

### Post by NickoHall on 2012-03-06
Bump.

---

### Post by Spae on 2012-03-09
^that.

---

### Post by NickoHall on 2012-03-10
Bumpity.

---

### Post by Spae on 2012-03-13
Too many people are having this problem on different laptops. How is there not a fix for this? If ubuntu should gain popularity, compatibility should be of high priority.

---

### Post by NickoHall on 2012-03-13
Yeah this is a common problem and yet there are no fixes, only temporary work arounds which hardly work anyway :( I needs moar battery lyf!

---

### Post by Spae on 2012-03-14
For me battery isn't the big problem. It's just too bright. Hard to look at, especially at night time.

---

### Post by Toz on 2012-03-14
Have you tried the following kernel parameters:
- **acpi_backlight=vendor**
- **acpi_osi=**
- **acpi_osi=Linux**
- **acpi_osi=Linux acpi_backlight=vendor**
- **acpi_osi="Linux"**
- **acpi_osi="Linux" acpi_backlight=vendor**
- **acpi_osi=\"Linux\"**
- **acpi_osi=\"Linux\" acpi_backlight=vendor**

Information here ([https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot")) on how to test these parameters during boot.

If no luck, open a terminal window and type in the following command and post back the results:
```
ls /sys/class/backlight
```

---

### Post by prarobo on 2012-11-01
I have a hp-dv6 laptop
This worked for me

[http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html](http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html)

:guitar:

---

### Post by skiss on 2013-01-20
> **Spae said:**
> For me battery isn't the big problem. It's just too bright. Hard to look at, especially at night time.

Try: redshift
I noticed, that it is easier on the eyes at night time.

---

### Post by amjjawad on 2013-02-12
> **prarobo said:**
> I have a hp-dv6 laptop
This worked for me

[http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html](http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html)

:guitar:

+1
Same machine, worked for me too - thanks!

---


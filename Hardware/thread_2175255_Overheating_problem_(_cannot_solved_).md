---
title: "Overheating problem ( cannot solved )"
date: 2013-09-18
forum: Hardware
---

### Post by LEE_ZHI_JIANG on 2013-09-18
My laptop overheated very frequently after I installed Ubuntu based Operating System. My laptop started to cool down when I switch the proprietary drivers. Once I restarted everything went hairwire. I only able to see my desktop wallpaper ! I right clicked and select change wallpaper. The dialog box pop up and I noticed that the close, minimize and maximize buttons are missing ! This goes for all OS. The problem just improved slightly after I install another kernal. My laptop is warm for normal use, but it is extreamly hot when I watch videos. 

Is there any other solutions. I already tried everything. Changing the driver solved overheating issue but it makes everything went hairwire !

---

### Post by ranger1021994 on 2013-09-18
The problem may be with your graphics drivers.
Can you please specify your video card make ?

To better define power consumption and battery usage you can use 'tlp'
Its a console-based application that does a pretty neat job in managing power.
See if it helps you

---

### Post by LEE_ZHI_JIANG on 2013-09-18
Please refer to the screenshot below. I select the second one and the heating problem solved, but once I restarted I only able to view my wallpaper. My laptop stil warm. 
[IMG]http://lifeisabedofroses.tk/wp-content/uploads/2013/09/Screenshot-from-2013-09-18-231640.png[/IMG]

[FONT=arial][SIZE=5] [SIZE=2]So, I actually installed Jupuiter and cfkg ( sth like that ) to lower down my CPU by setting it in Power Saving Mode. I notice my laptop doesn't get as hot as I just installed Ubuntu but it still get hot as time passes by unlike I select the proprietary driver. 
 
 I cannot figured out why I switched off my laptop, placed in a air conditioned room, 26 degree celcius. I switched it on back and the temperature reading is 50 ++ . 
 
 I actually installed kernal but it didn't help much. The option that can greatly reduce the temperature ruin the whole system as I can see the wallpaper when I logged in once I started it up. [/SIZE]
[/SIZE][/FONT]

---

### Post by ranger1021994 on 2013-09-18
Do you use Compiz ?
Maybe Compiz is causing problem

---

### Post by whitesmith on 2013-09-18
One thing you might try is installing Gnome 3 (download from USC) and then logout. On the Login screen, click on the Ubuntu logo and select Gnome Without Special Effects (this may not be the exact wording). My PC 's performance went up and temperature went down after doing this. On the other hand, maybe a pretty screen is more important to you than performance. That's why *nix offers choices.

---

### Post by Yellow Pasque on 2013-09-18
Showing a screenshot may be leaving out important information (like if you also have an Intel GPU in a hybrid setup).
```
lspci | grep VGA
```

---

### Post by LEE_ZHI_JIANG on 2013-09-18
lspci | grep VGA

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M/7400M Series]

I cannot downl

---

### Post by jonnyboysmithy on 2013-09-18
So it looks like you have hybrid graphics chips in your computer like  me. The problem for me was solved by turning off the ATI graphics card  and only using the intel integrated. The ATI graphics card is much  faster and always on (making it very hot). If you're going to be doing  intensive graphics work you might need to use the ATI gpu.
For me the intel integrated graphics is more than enough so I only use that.

There is the proprietary catalyst driver avaliable from AMD. Using that  you can switch between the two cards to give you best performance or  battery life. Personally I've had no success with it. I've tried  everything, spent days on it. I have heard some success stories and last  I tried them was more than a year ago so things might have changed.  Personally I wouldn't bother with Catalyst and found it easier to just  turn off the ATI card and be done with it. 

I suggest you completely remove the graphics drivers you installed before you go on  and that you reboot after removing them. If you're not sure how to ask for help, I'm not to  sure how to go about completely removing the ATI drivers but it  shouldn't be that difficult.

To check which graphics card is on and which is in use run:
```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch

```
You should see something like this:
```
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0

```
IGD is the Intel chip, the + means it's the one in use, and Pwr means it's on.
 DIS is the ATI card and if it says Off, you're laptop is going to be a LOT cooler. Plus your battery life should go up heaps.

Now if the ATI card is On you can turn it off.
First become root:
```
sudo -i

```
Then in the same terminal run:```

echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```
then: ```
exit
```
You can check if it worked by running:
```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch

```
If it worked it will say:
```
0:DIS: :Off:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0
```

To make it permanent and last across reboots, add these to /etc/rc.local above the 'exit 0' line (e.g. sudo gedit /etc/rc.local from the terminal):
```
modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

And then add this to /etc/modprobe.d/blacklist-local.conf, also as sudo:
```
blacklist fglrx
```


Big post phew [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG] hope that helps!

---

### Post by LEE_ZHI_JIANG on 2013-09-18
Going to try it later

---

### Post by LEE_ZHI_JIANG on 2013-09-18
> **jonnyboysmithy said:**
> So it looks like you have hybrid graphics chips in your computer like  me. The problem for me was solved by turning off the ATI graphics card  and only using the intel integrated. The ATI graphics card is much  faster and always on (making it very hot). If you're going to be doing  intensive graphics work you might need to use the ATI gpu.
For me the intel integrated graphics is more than enough so I only use that.

There is the proprietary catalyst driver avaliable from AMD. Using that  you can switch between the two cards to give you best performance or  battery life. Personally I've had no success with it. I've tried  everything, spent days on it. I have heard some success stories and last  I tried them was more than a year ago so things might have changed.  Personally I wouldn't bother with Catalyst and found it easier to just  turn off the ATI card and be done with it. 

I suggest you completely remove the graphics drivers you installed before you go on  and that you reboot after removing them. If you're not sure how to ask for help, I'm not to  sure how to go about completely removing the ATI drivers but it  shouldn't be that difficult.

To check which graphics card is on and which is in use run:
```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch

```
You should see something like this:
```
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :Off:0000:01:00.0

```
IGD is the Intel chip, the + means it's the one in use, and Pwr means it's on.
 DIS is the ATI card and if it says Off, you're laptop is going to be a LOT cooler. Plus your battery life should go up heaps.

Now if the ATI card is On you can turn it off.
First become root:
```
sudo -i

```
Then in the same terminal run:```

echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```
then: ```
exit
```
You can check if it worked by running:
```
sudo cat /sys/kernel/debug/vgaswitcheroo/switch

```
If it worked it will say:
```
0:DIS: :Off:0000:01:00.0
1:IGD:+:Pwr:0000:00:02.0
```

To make it permanent and last across reboots, add these to /etc/rc.local above the 'exit 0' line (e.g. sudo gedit /etc/rc.local from the terminal):
```
modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

And then add this to /etc/modprobe.d/blacklist-local.conf, also as sudo:
```
blacklist fglrx
```


Big post phew :smile: hope that helps!
[SIZE=3]
[SIZE=4][FONT=century gothic]How to do the last two steps ? It says no file [SIZE=4]or directory and command not found (blacklist) [/SIZE] , R[SIZE=4]eally worry I have to make the words bigger because of some .... 
[/SIZE][/FONT][/SIZE]

[/SIZE]

---

### Post by jonnyboysmithy on 2013-09-19
So run:
```
sudo gedit /etc/rc.local
```
and put into the file:
```
modprobe radeon
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```
into the file above the line that says exit 0 
Click save, and close.


Sorry my mistake, the second command is actually supposed to be like this:
```
sudo gedit /etc/modprobe.d/blacklist.conf

``` 
Add this line at the bottom of the file and remember to click save.
```
blacklist fglrx
``` 

How's those temperatures? Cooling down?


You really worry you have to make the letters bigger? I can read this text size fine... sorry if I misunderstand..

---

### Post by LEE_ZHI_JIANG on 2013-09-21
[SIZE=3][FONT=century gothic]This problem is back again. I do the same steps back again and I get this error when I type the command "[/FONT][/SIZE][COLOR=#000000][FONT=Ubuntu Mono]sudo cat /sys/kernel/debug/vgaswitcheroo/switch"

Error msg : [/FONT][/COLOR]cat: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory

---

### Post by jonnyboysmithy on 2013-09-21
Ok, I've never had that problem, but after a bit of googling it appears you need to run:
[COLOR=#000000]```
sudo mount debugfs none /sys/kernel/debug
```
Before you can switch it off.


Here, follow these instructions: [/COLOR][http://planetoss.com/articles/how-to-disable-the-discrete-amd-graphics-card-in-linux/](http://planetoss.com/articles/how-to-disable-the-discrete-amd-graphics-card-in-linux/)

---

### Post by Jonathan Precise on 2013-09-21
Please use "gksudo gedit" (no quotes) instead of "sudo gedit". [See here why.]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by LEE_ZHI_JIANG on 2013-09-23
It's kinda weird. The problem occurs when I did a base update. Software updates are fine. It's OK now

---

### Post by Jonathan Precise on 2013-09-23
Please mark as solved by going to thread tools.

---


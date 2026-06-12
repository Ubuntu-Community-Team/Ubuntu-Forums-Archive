---
title: "Toshiba NB205 Overheating / Fan Constantly Running with Ubuntu Netbook Remix"
date: 2010-09-29
forum: Hardware
---

### Post by MadCity on 2010-09-29
I just noticed after about a week of really digging Ubuntu Netbook Remix on my Toshiba NB205 that the fan is almost constantly running! And the bottom of the netbook feels warmer than it used to when running windows. That is not a good sign. I'm a noob here. Can anyone help!!!??

---

### Post by msakms on 2010-09-29
I guess may be the processor is set at maximum speed
Try adding to the main panel the CPU Frequency Scaling Monitor and see if your CPU is set to maximum frequency 
-right click on the main panel
-select "Add to panel"
-choose from the menu "CPU Frequency Scaling Monitor" and hit add
-left click on the CPU tiny icon and choose "on demand" or simply choose the slowest speed 
Tell me if this doesn't work

---

### Post by MadCity on 2010-09-29
Thanks for the speedy response. I tried your procedure, and I couldn't even add the CPU frequency monitor. I right clicked on the "main panel" (the panel which defaults at the top, with the ubuntu logo on the upper left side, and with wireless card icons, and time and date, and shutdown button--right?): the only option was "preferences" or "about". 

I tried running "System Monitor" and it shows that CPU1 runs between 77-90% and CPU2 is running 94-98%. But there's no option to adjust this. :(

---

### Post by msakms on 2010-09-29
Follow the tutorial on how to setup your CPU frequency on [http://www.go2linux.org/how-to-configure-cpufreqd]("http://www.go2linux.org/how-to-configure-cpufreqd")
Use the "on-demand" profile to unleash your CPU cores powers only when needed.

---

### Post by MadCity on 2010-09-30
So, I entered in TERMINAL the first line: 

sudo aptitude install cpufreqd

And it appeared to install. Then, I entered the next line as per the tutorial: 

sudo lsmod | grep cpufreq

And got nothing, just like I would have hit "enter," it simply skips to the next line. 

It also seems that I can't really configure my "main panel" by adding programs or moving it around--why is that? Is that because I'm using netbook remix? I'm a Noo-b here, and this the first time I've ever run Linux on one of my machines. thanks for your patience and any help!

---

### Post by Porkchop62882 on 2010-10-13
Toshiba's just don't support linux.  I've been running Ubuntu since 8.04 on my Toshiba laptop, and have always had problems with with the fan not kicking on until it hits an extremely high temp. I've tried every trick on the forum. Just can't seem to find a fix.  I love Ubuntu, and that's why I stick with it. The way I see it is my CPU doesn't freak out until it hits 90c, and the fan always comes on at 70c.  Looks like you and I will just have to deal.  
[http://ubuntuforums.org/showthread.php?t=1420247&page=5](http://ubuntuforums.org/showthread.php?t=1420247&page=5)
There's a thread in case you felt like giving it a try.

---


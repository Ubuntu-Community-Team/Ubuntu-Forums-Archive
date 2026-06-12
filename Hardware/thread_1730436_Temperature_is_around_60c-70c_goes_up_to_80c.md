---
title: "Temperature is around 60c-70c goes up to 80c"
date: 2011-04-16
forum: Hardware
---

### Post by ihavenoname on 2011-04-16
Using almost any linux distro, my temperature goes up to 85c (when playing a game)usually hands around 65c-73c. I'm not sure if that is safe or not. On windows it is lower, usually around 58-60c and only goes up to 74c playing the same game on windows. 

  There seems to be an "extra level" on the fan that kicks in on windows and not on Linux. My Laptop is a Toshiba Satellite L305D-S5928 (Model#: PSLC8U-03G01U)

AMD Athlon X2 64bit QL-62. 3gb of ram. 

Is this normal? A sensor problem? 

  That "extra level" of fan speed kicks-in during the bios as well. I have tried installing gkrellm and lm-sensors. I have been unable to find a "fan sensor".  

 The bios is InsydeH2O BIOS version 1.8.

---

### Post by ihavenoname on 2011-04-16
Does anyone know where I could maybe ask this question that would be more appropriate?

---

### Post by varunendra on 2011-04-18
I guess the section is okay for this type of question.

I've recently tried (for the first time) an AMD Phenom processor, and while studying those processors to make a choice, I found at many forums/reviews that upto 70 degree Celsius is somehow normal for AMD processors. (Mine is Phenom II X2 555 BE, and hangs around 45-55 during normal usage)

I don't have experience with fan speed controllers in linux. Do gkrellm or lm-sensors provide options for controlling the speed? Did you try these:
[http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu](http://ubuntumanual.org/posts/127/how-to-control-fan-speed-lm-sensors-in-ubuntu)
[http://www.thinkwiki.org/wiki/ACPI_fan_control_script](http://www.thinkwiki.org/wiki/ACPI_fan_control_script)
[http://ubuntuforums.org/showthread.php?t=846480](http://ubuntuforums.org/showthread.php?t=846480)
[http://ubuntuforums.org/showthread.php?t=1320309](http://ubuntuforums.org/showthread.php?t=1320309)
(sorry for such a pile of links without any specific recommendation, but as I said, I've no personal experience with fan speed controlling in linux, so that's all I could suggest, try them yourself)

And above all, you didn't mention the name of the game you are trying. If it originally belongs to Windows and you have to use some kind of emulation to run it on ubuntu, then the emulation itself might be causing a processor overhead resulting in more heat than windows.

Lastly, you may try **top** command to see live resource usage (CPU, memory etc.) by different processes.

---

### Post by ihavenoname on 2011-04-18
I don't have a thinkpad and none of the thinkpad tutorials have been any help.
I don't have any "fan" sections or folders under acpi  in /proc/. In fact it seems linux cannot really even detect my fan speed let alone change it. Though my fan speed does indeed seem to vary slightly based on heat. Interestingly enough, after testing gnome-shell I got rid of both it an unity (it occurred to me that I am on natty, which is unreleased so I tested it on 10.10 and the same issue occurred) and installed kde. Then I deleted all the gnome and gdm stuff switched to all kde. And turned off compositing in kde (I suspect this is the most important) and now I am hanging around ~54c. Even with flash running (which used to be really bad)I also remembered that I had compositing off in Windows so it wasn't a fair comparison. 

 The game was the linux version of Trine. Thanks for your time! :D

---


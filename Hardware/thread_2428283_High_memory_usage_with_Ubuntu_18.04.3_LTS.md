---
title: "High memory usage with Ubuntu 18.04.3 LTS"
date: 2019-10-02
forum: Hardware
---

### Post by jtcarlos on 2019-10-02
[LIST]
[*][#1]("https://forums.tomshardware.com/threads/high-memory-usage-with-ubuntu-18-04-3-lts.3530846/post-21330979")
[/LIST]
[COLOR=#191E1E][FONT=Lato]Hi! Let me get straight to the question, is it this normal for ubuntu to have such a high memory usage? After a fresh restart my, my ubuntu already have 2.1gb usage and after I open 3 apps (Robo3t, Eclipse and LibreOffice Calc) memory usage goes to 90% on system monitor. Right now as I type all apps are closed yet the memory usage stay at 64%. What could be the cause of this problem? How do I fix it?

Specs:
Ryzen 5 3550h
8GB 2666mhz single channel
1TB Hdd (200GB partitioned for Ubuntu)
GTX 1650



[/FONT][/COLOR]

---

### Post by uRock on 2019-10-02
Hello and welcome to the forums. 

From the image you posted on Tom's Hardware, Chrome is eating your RAM.

Open a terminal, then install htop with **sudo apt install htop**. Htop is a terminal version of the system monitor that tends to be a bit more accurate. Something tells me Google Chrome is still running in the background, which I used to see happening regularly back when I used Chrome. You can highlight Chrome in htop or system monitor, then hit F9, then Enter to kill Chrome in htop or right-click Chrome in System Monitor and select to Kill it.

---

### Post by cruzer001 on 2019-10-02
also

[https://superuser.com/questions/269385/why-does-google-chrome-leave-running-processes-behind-even-after-closing-the-bro](https://superuser.com/questions/269385/why-does-google-chrome-leave-running-processes-behind-even-after-closing-the-bro)

---

### Post by Yellow Pasque on 2019-10-02
> Right now as I type all apps are closed yet the memory usage stay at 64%

That's because a lot of data remains cached. That memory could be freed if really needed. The bottom line is that you shouldn't trust how system monitor reports RAM numbers because it doesn't give you the full story. Use the 'free' command to see detailed stats:
```
free -m
```
[https://www.linuxatemyram.com/](https://www.linuxatemyram.com/)

---

### Post by dagmann on 2019-10-04
I just checked my system, i7-4790, all cores @ 4.4, and cpu is usages is between zero and three percent.
firefox 1%, xorg 1%, once there is an update check and uses about 2%, web 1%.
I am running clamscan and it is using 12%.

[**[COLOR=#000000]jtcarlos[/COLOR]**]("https://ubuntuforums.org/member.php?u=2133191"), have you checked for a virus?

---

### Post by Yellow Pasque on 2019-10-04
> **dagmann said:**
> I just checked my system, i7-4790, all cores @ 4.4, and cpu is usages is between zero and three percent.
firefox 1%, xorg 1%, once there is an update check and uses about 2%, web 1%.

[**[COLOR=#000000]jtcarlos[/COLOR]**]("https://ubuntuforums.org/member.php?u=2133191"), have you checked for a virus?

You are confusing CPU usage with memory usage. I see no reason to suspect a virus from the info the OP gave. In fact, I don't think the OP has any problems, other than being misled by the way system monitor reports memory usage.

---


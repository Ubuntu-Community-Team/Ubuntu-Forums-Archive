---
title: "Powerful PC to run demanding apps to be used remotely?"
date: 2015-10-30
forum: Hardware
---

### Post by marco furio ferrario on 2015-10-30
Problem: portable devices are not powerful enough to handle demanding task & powerful enough devices are not portable.
My intuitive solution: can I buy a powerful workstation and access it remotely with a combo of good 13" tablet & keyboard and mouse?
Example: 
Lenovo P300 [COLOR=#555555][FONT=Helvetica]Intel® Xeon® E3-1200 V3 processor + [/FONT][/COLOR][COLOR=#555555][FONT=Helvetica]NVIDIA® Quadro® K4000 + 32gb ram TO RUN PROGRAMS
[/FONT][/COLOR]Lenovo Yoga tab pro 3 + asus mb169 portable monitor to remotely access it and work from everywhere.

Isn't this better than an expensive workstation laptop that won't be neither portable as the pad neither powerful as the pc?
Please challenge my idea.

Best
m

---

### Post by francescopasa on 2015-10-30
Yes you can do that, but you always need a internet connection and it may not be that comfortable. Let's say you need to transfer big files to elaborate-view them... To be more specific I would need to know what you mean for demanding tasks. Do you need a GUI or not?

---

### Post by marco furio ferrario on 2015-10-30
Internet connection is not a problem as I have LTE mobile and almost always fast connections. 
I would'nt transfer anything from the tablet/very light laptop I would use to remote, and the only thing would be transfer to it should be the render of what's happening on the workstation and commands. It should work as if I was at the desk on the workstation but I actually remote the imputs and render the outputs on my ipad/tablet or very light laptop. 
Can it work? Examples of "heavy duties": rendering, cad, database searching and statistics programs. stuff like that.

The only thing that makes me think there must be a bottleneck somewhere is that it looks so simple that I wonder why nobody is offering as a service... Or maybe I am just not aware of it? Any hints?
thanks

---

### Post by francescopasa on 2015-10-31
Yes I think it works. All webservers are managed like that, with ssh. Basically you get a console on another computer and you can run any command. If you need a graphical user interface, there are different ways. The best one is using the xserver. Since it is a server you can run it on the desktop and connect to it from the client machine. It feels like using your desktop and is very good because only commands and data is transferred from one computer to the other. This should not work with a tablet.

Another way is using VNC, but this only transfers the image so it is slower. There are VNC clients for andoid, so a tablet should work (but it would be difficult without mouse and keyboard...).

You can try with any machine and your tablet/phone to get a feel of how it works.

---

### Post by marco furio ferrario on 2015-11-03
Thanks Francesco, 
do you think that splashtop ([http://www.splashtop.com/business](http://www.splashtop.com/business)) could work well? (should work both on laptop and tablets)
Thanks!

---

### Post by francescopasa on 2015-11-06
I have no idea, never used it. I think it should work, but there is also free software available to do what you want. I have scanned the link you sent, but from what I understand It does not work in Linux. Moreover I'd also look for a way to start the remote computer with wake on lan.

---

### Post by marco furio ferrario on 2015-11-06
It's actually patched "ubuntu" so it should work. Anyhow can you suggest a good freeware alternative?
thanks!

---


---
title: "fan speed"
date: 2013-05-27
forum: Hardware
---

### Post by bbroad1 on 2013-05-27
Hi there,

I am absolutely new to linux and am just trying it on my desktop, from windows 7. If you have any instructions then please give basic commands.

I am running linux mint 14 nadia on an intel mobo with a quad core chip. When I was running windows I could barely hear my fans, now with the computer doing almost nothing - I just have firefox running the fans are going full speed and I can't make them quieter (or slower) I can't find a program for this. I have googled and seen various programs? thinkfan and sensors applet. I 'think' I have installed them, but am not sure as there seems to be no way to tell. Either way I can't find them on the desktop and I can't make the fans any slower. Could someone help please? I have blindly followed various instructions for the terminal, I'm not sure what I've done, the commands complete without failure, but nothing 'seems' to happen?

tried this: [http://www.muylinux.com/2011/06/16/controlar-el-uso-del-ventilador-en-ubuntu/](http://www.muylinux.com/2011/06/16/controlar-el-uso-del-ventilador-en-ubuntu/)
and various other things that I don't have the info for to hand btw I don't speak spanish I found that link on the forums.

Please help a n00b,

Thanks

Ben

---

### Post by tgalati4 on 2013-05-27
If you are running in a virtual environment under Windows7, then it's possible that the fans are running due to higher CPU load of the virtual environment.  Perhaps a better way to experiment is to run from a Live USB and see if your fans behave the same way.

To run *thinkfan*, open a terminal and type *thinkfan*.  Thinkfan is quite sophisticated in that you can set different fan speeds at differerent temperature thresholds.  It generally works with IBM/Lenovo Thinkpads with Intel motherboards.  I don't know if it will work with a desktop, but tell us what you see on the screen.

Also, monitor your CPU temperatures from Win7 and see if the temperatures go up when running linux in a VM.

---

### Post by bbroad1 on 2013-05-27
This used to be a windows 7 machine, but I wiped it. It is only running linux now. When it was running windws it only sounded like a jet taking off when under heavy 3d high fps games. Under linux it always sounds like this even under very very light load.

If I type 'thinkfan' nothing happens.

[ATTACH=CONFIG]243126[/ATTACH]

---

### Post by Yellow Pasque on 2013-05-27
Is this a laptop or desktop?

---

### Post by bbroad1 on 2013-05-27
desktop

---

### Post by geocool on 2013-05-27
I have almost the same problem, I made a post here : [http://ubuntuforums.org/showthread.php?t=2149105&p=12666136#post12666136](http://ubuntuforums.org/showthread.php?t=2149105&p=12666136#post12666136)
My Cpu Temperature is around 40[COLOR=#000000]°C right now but Fun speed is high.  :(  
I tried this : [/COLOR][http://askubuntu.com/questions/22108/how-to-control-fan-speed](http://askubuntu.com/questions/22108/how-to-control-fan-speed)
but unfortunately I don't have compatible motherboard maybe you have a better luck.

---


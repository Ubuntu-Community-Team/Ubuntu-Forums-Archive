---
title: "Laggy mouse under Ubuntu 18.04"
date: 2019-12-05
forum: Hardware
---

### Post by bakilaszlo on 2019-12-05
Hey everyone!

I'm kind of new in Ubuntu, but very intent. My desktop is a Lenovo Y520. I have a few problems with my Ubuntu 18.04. One of them is my bluetooth mouse, which is a Microsoft Z5000. My OS can connect and disconnect very easily, even after suspend, but sometimes the mouse starts to be very laggy. I've been looking for a solution on several topics in connection with this theme, without success. Under Windows it was perfect, so with my phone. So, I reckon that the source of the problem is with my OS. 

I've figured out that the /sys/module/usbhid/parameters/mousepoll path doesn't exist at the system start. So, when I hit the cat /sys/module/usbhid/parameters/mousepoll command, I get "No such file or directory". 
After these commands the situation is a little bit better, but apparently not the best:
[COLOR=teal][FONT=&amp]modprobe[/FONT][/COLOR][COLOR=#333333][FONT=&amp] -r usbhid
[/FONT][/COLOR][COLOR=#333333][FONT=&amp]modprobe usbhid mousepoll=[/FONT][/COLOR][FONT=&amp][COLOR=#009999]8
[/COLOR][/FONT]I found these here: [https://forum.manjaro.org/t/wireless-mouse-periodically-inoperable/99702/16](https://forum.manjaro.org/t/wireless-mouse-periodically-inoperable/99702/16)
I've added this command too: [COLOR=#333333][FONT=&amp]echo [/FONT][/COLOR][COLOR=#DD1144][FONT=&amp]"options usbhid mousepoll=8"[/FONT][/COLOR][COLOR=#333333][FONT=&amp]>> [/FONT][/COLOR][COLOR=#333333][FONT=&amp]/etc/modprobe.d/blacklist.conf[/FONT][/COLOR]
However after I hit these commands, the mentioned path exist! So, I get an exact number for my mousepoll question, which would be the usual way of its working, I suppose. This state maintains until I reboot my laptop. 
Would somebody help me in this?

---


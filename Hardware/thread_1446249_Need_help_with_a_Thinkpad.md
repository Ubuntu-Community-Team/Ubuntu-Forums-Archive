---
title: "Need help with a Thinkpad"
date: 2010-04-03
forum: Hardware
---

### Post by dave2001 on 2010-04-03
I have just installed Ubuntu 9.10 KK on my Thinkpad A20m (yes I know it's old). The install went fine, but I have a two major issues.

1. I cannot seem to connect to the repositories. They are all checked in software sources.
I have tried using 
~sudo apt-get install (package) 
instead of the Software Center and Synaptics, but no luck, can't find any packages that way either.  I should mention my desktop was setup with 9.10 not long ago, it shares the same IC and everything is running smoothly on it, repositories included. That seems to rule out problems with my IC

2. My trackpoint middle button does not enable scolling when pressed. I have tried the various solutions on the forums. Eg. I could not get the gpointing-device-settings pkg because of problem #1. I didn't want to edit the Xorg.conf file, because it's not in the location described in the tutorials.  The responsiveness of the trackpoint is also very slow, even with mouse sensitivity and acceleration cranked all the way up.

Any suggestions greatly appreciated. Keep in mind I am pretty new to Ubuntu, so pretty please don't tell me to go get some source code and compile something myself.

---

### Post by curtisjwong on 2010-04-03
** Scrolling with Trackpoint**

 Create a new file called /etc/hal/fdi/policy/mouse-wheel.fdi typing: 
 sudo gedit /etc/hal/fdi/policy/mouse-wheel.fdi
And fill it with this code: 
 <?xml version="1.0" encoding="UTF-8"?> 

<match key="info.product" string="TPPS/2 IBM TrackPoint">
 <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
 <merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
 <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
 <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.ZAxsisMapping" type="string">4 5</merge>
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>

[http://www.thinkwiki.org/wiki/Install_Ubuntu_9.10_%28Karmic_Koala%29_on_a_ThinkPad_T400#Scrolling_with_Trackpoint](http://www.thinkwiki.org/wiki/Install_Ubuntu_9.10_%28Karmic_Koala%29_on_a_ThinkPad_T400#Scrolling_with_Trackpoint)

---

### Post by dave2001 on 2010-04-06
CurtisJWong! your the man! A simple and elegant solution.  I followed your suggestion and it worked like a charm. On a side note, Ubuntu 9.1 was a bit unstable on my thinkpad, so I gave Xubuntu 9.1 a try. It runs faster and is very stable. 
 I now have one another question for laptop users. I have an old belkin wireless fd56020 pcmcia card, which ubuntu refuses to work with. If anyone has a recommendation for a cheap pcmcia wireless card to replace it, I would love to hear it.

---


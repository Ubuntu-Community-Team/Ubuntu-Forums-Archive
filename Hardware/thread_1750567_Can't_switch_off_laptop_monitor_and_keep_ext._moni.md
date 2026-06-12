---
title: "Can't switch off laptop monitor and keep ext. monitor"
date: 2011-05-05
forum: Hardware
---

### Post by akazia on 2011-05-05
Hello, 

I have a lenovo Laptop L512 and an external Monitor 22"- I like to close the laptop and only use the external monitor. According to an other thread in this forum I just have to switch off the laptop monitor in an config file.
When I use the monitor tool (ubuntu 11.4/ unity) I can switch of the labtop but then also the external monitor gets dark... this way I can not save the change. 
where is the config file? I may can change this file direktly

Best regards and thanks a lot
Michael

---

### Post by archkidd on 2011-05-05
With 10.10 I used to be able to use different configurations of my laptop and external screen using Fn- F7.  This does not work with 11.04 which gives all sorts of odd screens.  I really dislike this Unity workspace!

---

### Post by akazia on 2011-05-06
Hello 

I can convirm that with 10.10 I could close my laptop, remove the laptop screen in the display settings and use the external screen as single screen.
With 11.04 I still can remove the laptop screen but now all screen went black and never come back. 
Also the behavior of FN F7 is somewhat different - I cound not excatly figgure out what all is different but at least it is no longer possible to send the laptop screen to an external monitor with its own resolution. 

does any one know where the setting file is stored - I like to compare it with the 10.10 version. Some times it just helps to ecit the files directly - it is still the X-server underneath..

Michael

---

### Post by akazia on 2011-05-06
Hi all,

well I am quit sure now that this is more an gnome issue - since the effect comes also up when I use the ubuntu classic desktop.
How ever does any know if there is a config file which I may manually change?

Thanks a lot 
Michael

---

### Post by teachop on 2011-05-06
My laptop is acting the same way.  Have tried everything, and ended up with some big messes to fix, but never can get it to work.  Interestingly, I have Xubuntu also, and if I choose Xubuntu at the login screen, it works fine.  With Unity, nope.  Sorry I have found no solution.

EDIT:  One thing you can do, is with gconf-editor, go to apps | gnome-power-manager | buttons, and change the setting for lid_ac to "nothing".  This allows me to close the laptop, however, the screen is still in use, so the mouse can fly off into nowhere, and sometimes windows too.

---

### Post by akazia on 2011-05-09
Hello 

sorry it took me some days to get my system back to shape..

> One thing you can do, is with gconf-editor, go to apps | gnome-power-manager | buttons, and change the setting for lid_ac to "nothing". This allows me to close the laptop, however, the screen is still in use, so the mouse can fly off into nowhere, and sometimes windows too.

Well even if you would be able to get used to this, the panel is still spread over two screens. Incase to want to make an ext. Monotior to your prim. screen the uniti dash(board) - still not user to the wording- will stay "on" the laptop.


I am faily sure that this is not unity issue but a x11 issue with 11.04 there where some changes..I am not an expert but willing to provide all needed info to fill a bug request. Where would be the place to do so?

Meanwhile I have set up a new system with 10.10 The above mentioned isseus are not existing in 10.10.

Michael



I workaround

---

### Post by flyingAnt on 2011-05-09
:KSI am just right also encountered this kind of problem, I think I can understand this solution

---

### Post by akazia on 2011-05-09
Hi,

I'd like to get the problem fixed - guess it is good that here are more that one who has this problem but where is the correct place to address this? 
Would this also go to the lanchpad? Though this seems to be more a X11/gnome than ubuntu/unity issue? 

Or let the experts descide (I'd prefer this) but again - how to address this to an expert???

Thanks for any hint
Michael

---

### Post by akazia on 2011-05-11
Hi

I found the following bug report in launchpad 
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/766490]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/766490")
can all of you who have the same problem please add a comment and indicate that more users are effected?

Thanks a lot
Michael

---

### Post by Krazedmaz on 2011-06-17
I have Ubuntu 10.04 i was able to switch screens on my Dell Vostro 1000, but since i have changed to an Acer Aspire i havent been able to switch the screens. it only comes up when i have the ext. monitor attached already....

---


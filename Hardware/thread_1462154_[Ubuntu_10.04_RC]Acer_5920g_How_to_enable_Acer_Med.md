---
title: "[Ubuntu 10.04 RC]Acer 5920g How to enable Acer Media Touch?"
date: 2010-04-25
forum: Hardware
---

### Post by saffolino on 2010-04-25
Since ubuntu 10.04 doesn't have HAL anymore, is there a way to enable Acer media touch (buttons on the right, play,pause,etc)?

---

### Post by saffolino on 2010-04-27
up

---

### Post by saffolino on 2010-04-28
bump

---

### Post by saffolino on 2010-04-30
up

(installed the final version but still no touch)

---

### Post by saffolino on 2010-05-01
bump

---

### Post by Pott on 2010-05-02
Have you tried the Karmic methods?

You need xbindkeys to map the buttons to their functions, and there's a script to rename the buttons on a previous thread if you do a search.

Then again without HAL it may not work but I wouldn't know about this... :/

Let us 5920G owners know please!

---

### Post by saffolino on 2010-05-03
Yes, I tried and failed ;_;. There must be another way with 10.04 :/

---

### Post by saffolino on 2010-05-04
up

---

### Post by fantakk on 2010-05-04
Up :!:

---

### Post by saffolino on 2010-05-05
> **fantakk said:**
> Up :!:

up

---

### Post by dino99 on 2010-05-05
maybe you need to install with synaptic: acerhk-source

---

### Post by Gatemaze on 2010-05-16
saf

i have the same problem here...

posted the same question a while ago describing what i did in previous versions to make them work.
[http://ubuntuforums.org/showthread.php?t=1478269](http://ubuntuforums.org/showthread.php?t=1478269)

basically if you notice the multimedia-keys are mapped to the scroll-cross (between left-click and right-click buttons)

have you found a solution?

cheers

---

### Post by Gatemaze on 2010-05-16
> **dino99 said:**
> maybe you need to install with synaptic: acerhk-source

installed it through synaptic, but i see no difference... is there something extra i need to do??

---

### Post by oleg89 on 2010-05-17
Gatemaze I didn't have to mess with xorg.conf to make the Media Keys work.

The first thing you got to do is finding whether you have to use head or tail in the script below. To do so type the following command in the shell:

```
xinput list --long
```There are to entries with the name "SynPS/2 Synaptics TouchPad". You need to find out which of these entries has a resolution of 1000 units/m (this corresponds to the Media Keys, at least on my machine). If this entry is the first of the those SynPS/2 Synaptics TouchPads when you must use head, otherwise tail.

The actual script is:
```
xinput set-button-map "`xinput list | grep Synaptics | head -1 | grep -o id=.. | tr -d id=`" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
```or
```
xinput set-button-map "`xinput list | grep Synaptics | tail -1 | grep -o id=.. | tr -d id=`" 1 2 3 17 18 19 20 8 9 10 11 12 13 14 15 16
```according to the mentioned fact above. The original script can be found [here]("http://swiss.ubuntuforums.org/showthread.php?t=997860").

The last thing to do is to save this script, make it executable, add it to the startup apps and reboot.
Now you should be able to use the buttons with xbindkeys.

oleg

---

### Post by Gatemaze on 2010-05-17
Many thanks Oleg. It works like a charm. For the record my mapping is also the one with resolution of 1000 units/m.

---

### Post by Habib Chemist on 2010-06-30
I am using Acer 4920 with Ubuntu 10.04 LTS Operating System and Windows Vista HP (double OS). There is Acer media touch key here. But it doesn't work corectly. malfunction. As we know that the Acer Media touch key in some application is used to scroll up or scroll down in a page. When I opened openoffice or Document viewer application, Acer media touch key sometime turn on randomly, so the page I opened is scrolled up and scrolled down randomly too. 

Is there anybody can help me to correct this? Or, how to disable acer media touch key In My Acer Aspire 4920? I do not need to Acer Media Touch key too much. 

Thanks for your attention.. 
Habiburrahman

---

### Post by Gatemaze on 2010-06-30
have you tried the solutions written above?

---

### Post by Akioshi on 2012-05-04
so, first of all - thanks for solution ^_^ and excuse me for my english....
the solution posted above was great on 10.04LTS, but on 11.04 it doesn't worked... so is on 11.10 and on 12.04LTS. This is how to enable acer mediakeys.
1) do the same things as oleg89 did.
2) install xbindkeys and xvkbd - this packet is important. 
The thing is that xvkbd was installed out-of-box in 11.04, but is not in 11.10 and 12.04. So, xbindkeys can't work propertly. 
The config file of xbindkeys (/home/your-user-name/.xbindkeysrc):

```
#Remark
"xvkbd -text "\[XF86AudioPlay]""
   b:17

#Remark
"xvkbd -text "\[XF86AudioStop]""
   b:18

#Remark
"xvkbd -text "\[XF86AudioPrev]""
   b:19

#Remark
"xvkbd -text "\[XF86AudioNext]""
   b:20

#Remark
"audacious"
    m:0x0 + c:157
    XF86Launch2 

#
# End of xbindkeys configuration
```
please notice that i've changed the action of button situated above the multimediakeys to launch audacious instead of banshee (by default). Yes, i hate banshee player ;)

also, it is necessary to notice that it's necessary to add into autostart applications not only the script from oleg88, but also xbindkeys.

good luck

---

### Post by nothingspecial on 2012-05-04
Thanks for the information but this thread is old.

Closed.

---


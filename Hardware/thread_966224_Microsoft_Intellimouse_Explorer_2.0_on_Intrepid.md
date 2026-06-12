---
title: "Microsoft Intellimouse Explorer 2.0 on Intrepid"
date: 2008-11-01
forum: Hardware
---

### Post by bgenc on 2008-11-01
Hi all,

I installed Intrepid yesterday (clean install). Everything is amazing, runs out of the box. Ubuntu is getting only better by each release. However, here is a small annoyance:

My MS imouse, although works fine as a simple mouse, doesn't have any configuration options for the wheel speed or side buttons. As a result, my wheel speed is way too slow to be of real assistance and the side buttons do things that I don't prefer.

The wheel works as a middle button in my mouse. However, great MS designers made it so difficult to press that I could never manage to use it. Therefore, I was remapping the side buttons to act as the middle button. Now, in Intrepid, there is not even a mouse section in the Xorg configuration. Being the noob, I googled for a clue but all existing tutorials are for old versions and "existing" mouse sections in Xorg.conf.

Is there a working tool/documentation/page for setting up mouse in intrepid?

---

### Post by ronnielsen1 on 2008-11-01
You could ask Microsoft if they have linux drivers.

Did this work right in your previous version? I found this page on making the mouse work in Dapper. Intrepid is too new for there to be a howto

[http://ketsugi.com/panegyrist/howto-intellimouse-explorer-with-ubuntu-dapper/](http://ketsugi.com/panegyrist/howto-intellimouse-explorer-with-ubuntu-dapper/)

---

### Post by bgenc on 2008-11-01
> **ronnielsen1 said:**
> You could ask Microsoft if they have linux drivers.


they actually do, but you need an msdn subscription to download it.

there are many howto's indeed for hardy-, the problem is the mouse section is not in the xorg.conf file anymore. And I am not sure whether it is a good idea to create one or not. I know that the keyboard and mouse handling "sorta" changed in intrepid, well in Xorg 7.4, but I am not a developer and don't know exactly what the change is and how it effects this and that. So what I am basically asking is, is it an acceptable thing to fix intrepid xorg with pre-intrepid xorg patches such as this one. Or is the xorg.conf intentionally left blank to avoid overlapping settings already done/hardcoded somewhere else?

---

### Post by bgenc on 2008-11-02
here is an update: I tried to create my own input device section in xorg.conf similar to the examples on the net, and boom, X totally crashed. So, apparently I can not remap the buttons inside xorg.conf. 

But that really is quite annoying. Ubuntu gave us a flashy compiz desktop with elastic window borders, rotating cubes, flaming texts, raining desktops etc. but there is not a simple gui for remapping mouse buttons? Heck, there is not a way to fix it from the console. I found that there was a program called btnx which worked before and doesn't work with intrepid any more.

---

### Post by K1200S on 2008-11-02
Well, I can't contribute much to help you but I agree that mouse handling / config in general seems to be quite different in Intrepid (compared to earlier versions). This is not necessarily less good than before as almost all buttons on my Logitech MX1000 are working as I'd expect them to out of the box. The only thing that I'd like to tweak is to have one button dedicated to a double click. In Hardy, I accomplished this with imwheel but this doesn't seem to work in the same way anymore.

So, to cut a long story short, are there any ressources that describe in more detail what is actually different in Intrepid and how adding customised functions for extra mouse buttons is still possible? That would already help a lot.

Thanks,

K1200S

---

### Post by bgenc on 2008-11-02
Considering that the problem is more X related than Ubuntu related, I am willing to read some X documentation about the 7.4 release. However, I can't seem to find some detailed document about the release. Does anybody have a pointer?

---

### Post by Falcorian on 2008-11-02
> **bgenc said:**
> Considering that the problem is more X related than Ubuntu related, I am willing to read some X documentation about the 7.4 release. However, I can't seem to find some detailed document about the release. Does anybody have a pointer?
8.10 doesn't handle the mousein xorg anymore. It's in HAL now.

---

### Post by grajea on 2008-12-04
I used the xorg.conf hack to switch the funcionality of my buttons in previous versions of ubuntu.
Since Intrepid Ibex, it is no possible (because of HAL), but I have found another way using xmodmap.

In my case, I want to use the side button of my mouse (microsoft intellimouse explorer) as the middle button.

Step 1:
With the xev command, see what number have each button.

Example: launch xev, click on left button and see ...
```
    ButtonPress event, serial 31, synthetic NO, window 0x4e00001,
    root 0x13b, subw 0x0, time 89113837, (138,82), root:(145,133),
    state 0x10, **button 1**, same_screen YES
```

Step 2:
Create a .xmodmap file with the following line (to suit my preferences)

```
 pointer = 1 8 3 4 5 6 7 2 9
```

I switched the "2" and "8" buttons, to give middle button function to the side button.

Step 3:
execute 
 ```
xmodmap .xmodmap
```
and test the results.

Step 4:
Create a job at session startup (System > Preferences > Sessions) to launch the command every session of my user.

I hope this help you.

---

### Post by kristoff on 2009-01-12
Have just upgraded from Ubuntu 4.10 to 8.10 running on a HiGrade Asus Ultinote AS8400 with a Microsoft serial mouse on ttyS0 and a Symantics Trackpad touch-pad.
Re-partitioning and installation uneventful but I just cannot configure the Serial Mouse which I really want to have available.
Usual alterations to /etc/X11/xorg.conf don't seem appropriate given the new layout of the file and they don't work anyway. 
I haven't been able to write an 'inputattach'line into /etc/rc.local and sudo dpkg-reconfigure xserver-xorg only calls up the monitor.
The two pointing devices worked happily together on all earlier installations of Ubuntu (and SuSe from what I recall)
Any suggestions will be very much appreciated.

---

### Post by monos98 on 2009-02-12
> **grajea said:**
> I used the xorg.conf hack to switch the funcionality of my buttons in previous versions of ubuntu.
Since Intrepid Ibex, it is no possible (because of HAL), but I have found another way using xmodmap.

In my case, I want to use the side button of my mouse (microsoft intellimouse explorer) as the middle button.

Step 1:
With the xev command, see what number have each button.

Example: launch xev, click on left button and see ...
```
    ButtonPress event, serial 31, synthetic NO, window 0x4e00001,
    root 0x13b, subw 0x0, time 89113837, (138,82), root:(145,133),
    state 0x10, **button 1**, same_screen YES
```

Step 2:
Create a .xmodmap file with the following line (to suit my preferences)

```
 pointer = 1 8 3 4 5 6 7 2 9
```

I switched the "2" and "8" buttons, to give middle button function to the side button.

Step 3:
execute 
 ```
xmodmap .xmodmap
```
and test the results.

Step 4:
Create a job at session startup (System > Preferences > Sessions) to launch the command every session of my user.

I hope this help you.

Thats great! I have been trying find help on this for a while now. That worked perfectly!  But seriously, there really needs to be a GUI for this.

---


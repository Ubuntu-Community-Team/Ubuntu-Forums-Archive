---
title: "Toshiba P755-S5196"
date: 2012-02-10
forum: Hardware
---

### Post by okaar on 2012-02-10
First of all, awesome computer, awesome price, awesome hardware and awesome ubunutu (Linux) compatibility

I installed ubuntu 11.04 and then upgraded to 11.10, it was the only LiveCD that I had at that time. Everything worked out of the box, everything except the Optimus system which works good with Ironhide. The only thing that annoys me a little is the webcam which, for some reason, doesn't look so good. Oh, the backlight in the softkeys didn't worked either, but it's ok for me although I will try to make them work.

**_[COLOR="Red"]Installing Ironhide[/COLOR]_**

This was quite annoying at the beginning since I though at the beginning that it was working alright but... it didn't, it was just the intel chipset, sandybridge btw, doing it's work.

So, you need to run
```

sudo add-apt-repository ppa:mj-casalogic/ironhide
sudo apt-get update && upgrade
sudo apt-get install ironhide ironhide-ui

```

then you have to configure your system:

```
sudo ironhide-configuration
```

When it asks for Image Transport, you can play with the settings but the one that worked for me was PROXY. That is not all, the program ironhide-indicator is broken but there is a fix, you can see it here:

[https://github.com/MrMEEE/ironhide/issues/77]("https://github.com/MrMEEE/ironhide/issues/77")

If you are having a hard time looking for the ironhide-indicator excutable, I know I did, it is here:
```
/usr/share/ironhide-ui
```

This is the test that I did to check if the discrete card was being used.

```

oscar@neurona:~$ optirun glxgears
 * Starting Ironhide X server ironhide                                     .                                                                   [ OK ]
2549 frames in 5.0 seconds = 509.712 FPS
2470 frames in 5.0 seconds = 493.878 FPS
 * Stopping Ironhide X server ironhide                              [ OK ] 
oscar@neurona:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
300 frames in 5.0 seconds = 59.948 FPS
300 frames in 5.0 seconds = 59.857 FPS
300 frames in 5.0 seconds = 59.853 FPS
300 frames in 5.0 seconds = 59.857 FPS
300 frames in 5.0 seconds = 59.857 FPS


```

Optirun makes your apps run over the discrete card or you can use the indicator to run them.
Also try the command ironhide-settings, it has a lot of fun stuff.


**_[COLOR="Red"]Installing Touchegg[/COLOR]_**

Do you remember that I told you that this laptop have an awesome hardware? Well it has a multitouch touchpad, cool isn't it?, actually it only has 3 point detection but it's pretty awesome nonetheless.

You don't need any new repository just run:
```
sudo apt-get install touchegg
```

Don't forget to add it to you startup applications.

Since I didn't like the configuration that came by default, I had to modify the following conf file:

```
gedit /home/oscar/.config/touchegg/touchegg.conf
```

With this code:
```

<touchégg>
    
    <settings>
        <property name="composed_gestures_time">0</property>
    </settings>
    

    <application name="All">
        
        <gesture type="TAP" fingers="2" direction="">
            <action type="MOUSE_CLICK">BUTTON=3</action>
        </gesture>
    
        <gesture type="TAP" fingers="3" direction="">
            <action type="SEND_KEYS">Super</action>
        </gesture>

        <gesture type="DRAG" fingers="2" direction="ALL">
            <action type="SCROLL">SPEED=7:INVERTED=true</action>
        </gesture>
        
        <gesture type="DRAG" fingers="3" direction="ALL">
            <action type="SEND_KEYS">Super</action>
        </gesture>

    </application>


    <application name="Okular, Gwenview">

        <gesture type="PINCH" fingers="2" direction="IN">
            <action type="SEND_KEYS">Control+KP_Add</action>
        </gesture>

        <gesture type="PINCH" fingers="2" direction="OUT">
            <action type="SEND_KEYS">Control+KP_Subtract</action>
        </gesture>

        <gesture type="ROTATE" fingers="2" direction="LEFT">
            <action type="SEND_KEYS">Control+L</action>
        </gesture>

        <gesture type="ROTATE" fingers="2" direction="RIGHT">
            <action type="SEND_KEYS">Control+R</action>
        </gesture>

    </application>


    <application name="Chromium-browser, Dolphin, Nautilus">

        <gesture type="DRAG" fingers="2" direction="LEFT">
            <action type="SEND_KEYS">Alt+Left</action>
        </gesture>

        <gesture type="DRAG" fingers="2" direction="RIGHT">
            <action type="SEND_KEYS">Alt+Right</action>
        </gesture>
        
    </application>


</touchégg>

```

Since I'm using the gnome-shell, I love that thing, I used the 3 finger DRAG and TAP to bring up the overview.
**Update:** touchegg made my trackpad very sensitive so I made a script to handle this problem

```

#!/bin/bash

exec xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Finger" 50 60 255 & touchegg


```



Basically that's it.
Enjoy.


If you have suggestion, let me know... I'm actually quite curious about if I'm using ironhide correctly.

---


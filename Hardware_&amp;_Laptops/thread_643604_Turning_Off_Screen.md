---
title: "Turning Off Screen"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by lavapunk on 2007-12-18
I have an IBM Thinkpad and would like to turn off the screen using the Thinkpad/Thinkvantage button.  In other words, when I hit the button, I would like the screen to turn off.  Then, when I hit a key or move the mouse, I'd like the screen to turn back on.  

However, I am uncertain how to turn the screen off.  I realize that one can blank the screen, but this is not the same thing as the backlight does not turn off and, consequently, it defeats the purpose of saving battery life.  When I use vbetools to turn off the monitor "sudo vbetool dpms off" the screen does not turn back on when I move the mouse or hit a key.  Only when I enter "sudo vbetool dpms on."

Any suggestions?

---

### Post by gary4gar on 2007-12-18
its simple, put the following in terminal:)
> xset dpms force off
also you can make a shortcut for it on the panel( application launcher)
also you can make it to key shortcuts
[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

---

### Post by erginemr on 2007-12-18
You can also follow one of the several tips on this web page to achieve the same effect:
[http://www.shallowsky.com/linux/x-screen-blanking.html](http://www.shallowsky.com/linux/x-screen-blanking.html)

Editing "/etc/X11/xorg.conf" there is an interesting call.

---

### Post by lavapunk on 2007-12-18
For some reason xset does not work for me.  That was my original idea. 

Also, erginemr, thank you for the link.  That was the website I read through initially--with the failure of xset I was uncertain how to proceed.  And, especially, uncertain why it isn't working.

---

### Post by erginemr on 2007-12-18
Strange... If I were in your boots, I would not give up on "xset", because the suggestion by gary4gar above (and also your initial plan) is the exact, straightforward solution you are looking for.

Perhaps some tidbits of info on my system will help. When I use 
```
xset dpms force off
```
I don't quite get the effect, as the screen turns off, but initiates itself momentarily. But the command below, which instructs the computer to wait for one second before the action does the trick:
```
sleep 1; xset dpms force off
```
and my screen goes into the suspend mode.

On a side note, the "Monitor" section of my "/etc/X11/xorg.conf" file has an option to activate the "DPMS" mode:
```
Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection
```

Hope this helps.

---

### Post by lavapunk on 2007-12-18
I should have been a little more specific.  Setting a certain time for the screen to sleep doesn't work either.  It doesn't matter if I set the value to 1, 5, or higher; all that occurs is the cursor in the terminal blinks once each second without the screen blanking.  DPMS is enabled in my xorg.conf.  It seems as though xset either doesn't have the permissions or is being circumvented by another process.I should have been a little more specific.

---

### Post by erginemr on 2007-12-18
Please read the following posts:
[http://www.shallowsky.com/linux/x-screen-blanking.html](http://www.shallowsky.com/linux/x-screen-blanking.html)
[http://www.linuxquestions.org/questions/linux-general-1/xset-dpms-force-off-doesnt-turn-off-screen-531977/](http://www.linuxquestions.org/questions/linux-general-1/xset-dpms-force-off-doesnt-turn-off-screen-531977/)

There, as a second alternative the use of "vbetool" has been proposed. But its man page (man vbetool) warns the user that it may be dangerous for the X server. So, please investigate further this tool's capabilities before using it regularly.

EDIT: Sorry, forget about it: In your initial post, you have already stated that you resorted to vbetool.

---

### Post by lavapunk on 2007-12-18
The second post was helpful thank you.  It seems that the only way to turn the screen back on using using vbetool.  I suppose I will use vbetool and will have to link it to two keys in order to turn the screen off and then turn it on when I return.

What I was trying to do was only use the ThinkVantage button.  Is there any way to run a script that would keep track of each time I hit the key and alternate between turning the screen on and off.

---


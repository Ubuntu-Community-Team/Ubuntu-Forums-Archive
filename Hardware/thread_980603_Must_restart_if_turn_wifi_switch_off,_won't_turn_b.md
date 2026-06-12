---
title: "Must restart if turn wifi switch off, won't turn back on (Acer 5920G)"
date: 2008-11-13
forum: Hardware
---

### Post by chubby127 on 2008-11-13
Hi, I have an Acer 5920G and am runing 8.10. Everything works out of the box for me on the laptop... except one thing i noticed a few days ago. When I boot up Ubuntu Wifi works and the LED blinks like it should. If i decide to turn Wifi off and connect an ethernet cord then that also works fine too.The problem occurs when i want to start using my Wifi again, when i press the Wifi button nothing happens. The light just never comes back on and Ubuntu still claims that wireless is disabled even though i pressed the button. The only way I can get Wifi to work again and the LED to come back on is when i restart my computer. It's not really a big problem just something little that has been annnoying me lately. Thanks in advance!

---

### Post by blackened on 2008-11-13
Instead of restarting your machine, you can likely just restart your wireless adapter. Use ```
ifconfig
``` to find the name of your wireless adapter (mine is wlan0, yours might be as well depending on manufacturer) and then use (if it is wlan0, otherwise substitute your adapter name in place of wlan0 in the following command)
```
sudo ifconfig wlan0 up
```

That should get your connection going again. Make sure you have the wireless switch turned on.

---

### Post by chubby127 on 2008-11-13
Thanks a lot Blackened, the second command got the wireless working again. :)

---

### Post by teaker1s on 2008-11-13
could be caused by key code for powering on not registered- does it seem like a physical hardware switch or software switch ```
xev
``` should allow you to tell

---

### Post by blackened on 2008-11-13
> **teaker1s said:**
> could be caused by key code for powering on not registered- does it seem like a physical hardware switch or software switch ```
xev
``` should allow you to tell

My wireless switch does the same thing. If I turn it off and then back on I have to use ifconfig to bring the wireless adapter back up.

xev doesn't report anything when wireless switch is turned off/on, which I assume it's supposed to do.

---

### Post by teaker1s on 2008-11-13
some wireless switches generate keycodes  and if so can be made to reload wireless. In this case it appears that yours is a hardware power switch.

---

### Post by blackened on 2008-11-14
> **teaker1s said:**
> some wireless switches generate keycodes  and if so can be made to reload wireless. In this case it appears that yours is a hardware power switch.

So in this case I can't trap it and write an event handler in /etc/acpi/events then. That's kindof annoying. Guess I'll have to deal with manually switching it on and off with ifconfig.

---

### Post by chubby127 on 2008-11-14
yeah i'm just entering the ifconfig every time i need wlan back... annoying but ill guess ill have to deal with it

---

### Post by luxiter on 2008-11-25
i've the same problem but the xev utility report this event when i press the button:

KeyPress event, serial 34, synthetic NO, window 0x4400001,
    root 0x13b, subw 0x0, time 2659731, (-127,487), root:(965,540),
    state 0x0, keycode 246 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


i can do anything for work this button or is an hardware button ?

---

### Post by chubby127 on 2008-12-01
So ever since I entered "sudo ifconfig wlan0 up" my wireless works again but now every single wireless network within range has a 100% signal strength. Is there any way I can get the signals to report their actual strength again? This hadn't been a problem for me until I entered "sudo ifconfig wlan0 up." Thanks

---

### Post by jalirious on 2009-09-05
Kids

AA1 - the hardware switch disables wifi, but no renabling. 9.04

xev [hardware switch for wifi]

*************************

KeyPress event, serial 32, synthetic NO, window 0x3c00001,
    root 0xa5, subw 0x0, time 5584629, (675,86), root:(682,451),
    state 0x0, keycode 246 (keysym 0x1008ff95, XF86WLAN), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x3c00001,
    root 0xa5, subw 0x0, time 5584635, (675,86), root:(682,451),
    state 0x0, keycode 246 (keysym 0x1008ff95, XF86WLAN), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

*********************

Any ideas (other than installing linpus) to get wifi happiness?

cheers

---

### Post by blackened on 2009-09-06
This thread is 9 months old. Please start a new one with a clear subject line describing your problem. Provide a reference to this thread if you think it will be helpful.

---


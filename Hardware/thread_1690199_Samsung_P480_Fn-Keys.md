---
title: "Samsung P480 Fn-Keys"
date: 2011-02-18
forum: Hardware
---

### Post by Cullin1989 on 2011-02-18
Hello everyone.

After doing some research on the topic, I'm still stuck with my brand new Samsung P480 Fn-Key issues.

Here's the problem:

The only Fn-Keys working correctly are those for muting und volume changes and the NumLock.
The others are either not functional (CapsLock I think that is, Standby, and whatever those with the euro sign, the toolbox and the running man are for;)
When I hit one of the others, they look like they're doing their job, but they keep sending signals somehow.
So for example, when I hit Fn+up for an increase in brightness it fires the brightness up and up again until max is reached and it still tries to keep going - plus it messes up my desktop (no typing, no moving of windows, no menus, etc.) until I go Alt-F2 -> Alt-F7. And then it still keeps sending those signals.
This is especially bad on my battery since I can only run the laptop with full brightness (which btw kills my eyes;)

I so far tried out this ppa [https://launchpad.net/~voria/+archive/ppa](https://launchpad.net/~voria/+archive/ppa) which at least activates some more of the Fn-Keys, but they all keep sending signals ;(

I read that it is somewhat a standard issue with Samsung notebooks, so maybe someone has a conveniant answer in terms of what I can do to fix this already. But everything I keep finding on google is stuff related to other models. Seems like no one but me uses linux on a P480.

Regards,
Cullin

---

### Post by Cullin1989 on 2011-02-19
From The Ubuntu Keyboard Settings I gathered some information on the keys.  

Fn+Esc= XF86Sleep 
Fn+F2 = XF86Battery 
FN+F3 = Alt+NB_Einf (the strange thing with a euro sign on it)
Fn+F4 = XF86Display 
Fn+F5 = XF86Launch1 (which is supposed to turn on/off the backlight) 
Fn+F6 = XF86AudioMute 
Fn+F7 = XFLaunch2 
Fn+F8 = XFLaunch3 
FN+F9 = XF86WLAN 
Fn+F10 = XF86TouchpadToggle 
Fn+F11 = NumLock 
Fn+F12 = ScrollLock 
Fn+Up = XF86MonBrightnessUp 
Fn+Down = XF86MonBrightnessDown
Fn+Left = XF86AudioLowerVolume 
Fn+Right = XF86AudioRaiseVolume  
So it slooks like they're recognized, by the system. All I need now is a fix for that repeated signal that the keys are sending. Maybe there is a way to force a release of the key after being pressed or something like that. 
And than of course if someone could hint me some commands for controlling the brightness in a script, so I can map it to those keys. And possibly also for switching on/off Wifi.  I also tried xbacklight, wich doesn't work. 

Also when I change /proc/acpi/video/NVID/LCD/brightness nothing happens.

---

### Post by Cullin1989 on 2011-02-20
After adding the P480 like so [http://linuxtweaking.blogspot.com/2011/01/fedora-14-how-to-make-samsung-fn.html](http://linuxtweaking.blogspot.com/2011/01/fedora-14-how-to-make-samsung-fn.html) in "/lib/udev/rules.d/95-keyboard-force-release.rules" I'm almost happy now. The keys do a release as expected, BUT I still can't adjust the brightness. The change that is indicated in the notification area is not applied.

When I go into standy and back again someow the brightness gets applied...

All the other Fn combinations suddenly also work as expected.

That leaves me with only the brightness problem. Any ideas on how to aplly a brightness change on a samsung notebook?

---

### Post by Cullin1989 on 2011-02-20
Adding this line in the Device Section of xorg.conf

Option "RegistryDwords" "EnableBrightnessControl=1"

I was able to solve the mystery.
Now everything runs smoothly.

Hope this helps other people, too. I'm pretty sure it will help myself in the future ;)

---

### Post by poibs on 2011-06-02
Hello,

I want to configure the FN-keys for my Samsung R522 on Ubuntu 11.04. The brightness, volume and some other keys are working, but I want to use all the FN-keys and configure some in that way I want to use them.

I don't understand what you did.

Thank you

---


---
title: "Lefthanded mouse+touchpad configuration help"
date: 2008-07-16
forum: Hardware
---

### Post by slyn4ice on 2008-07-16
Hello all,

I have to apologize in advance if this has been answered somewhere but all threads about left-handed problems were either kindly disregarded or provided no solution whatsoever.

Anyways, the problem is simple - if you use an external mouse on a laptop, switch it to left-handed mode, then unplug the mouse and use the touchpad instead, the settings are screwed up - the touchpad recognizes both double-click and single-click (on the touchpad itself, not the buttons) as context menu (or right-clicks - on a lefty mouse that would be a left-click) instead of a normal click. This means that anytime you move the pointer via the touchpad, if you lift your finger a little too soon the system recognizes it as a right-click ... which is very annoying.

I found this bug on Launchpad with the exact same problem:
[https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/231736](https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/231736)

I have had the same problem in much earlier versions of Ubuntu though (even though the above bug report is relatively recent) so i guess it is a recurring problem.

So, all you lefties out there - what did you do to make this problem go away?

Thanks

---

### Post by slyn4ice on 2008-07-16
And while we are on this topic, is it possible to have 2 different configurations - for the mouse and the touchpad? The problem is that i have a 17" LCD and it takes forever to scroll from one end to the other with the touchpad. I have to change the acceleration from the Preferences->Mouse section so i can scroll faster. But then i decide to use the mouse and i have to change those preferences again ... what gives?

Thanks

---

### Post by phantomjoker on 2008-07-16
So have you gone into System/Preferances/Mouse ?

That has most settings - as neither a lefty nore a computer user i may be of no help but if you havent... also chage the double click sensitivity if that is causing problems. and you may have got the box ticked which reads 

> trigger secondary click by holding down primary button

or the option to
> initiate pointer click when stopping pointer movement 

unclick them if they are clicked.

post what the results are.

---

### Post by slyn4ice on 2008-07-16
> **phantomjoker said:**
> So have you gone into System/Preferances/Mouse ?

That has most settings - as neither a lefty nore a computer user i may be of no help but if you havent... also chage the double click sensitivity if that is causing problems. and you may have got the box ticked which reads 



or the option to


unclick them if they are clicked.

post what the results are.

Of course i have ;) Those settings were disabled in the first place. So, no result to post :) I also don't want to mess with double click sensitivity since it works fine with my usb mouse ;)
I think it's not much of a development problem, but a conception issue. The idea that the mouse and the touchpad are the same type of device but may require different settings simultaneously because they function differently is not really present here... maybe it's just my problem. I don't know.

---

### Post by phantomjoker on 2008-07-16
yer - I cant say that sounds right.

is there any software you can download or drivers to enable you to switch your touchpad settings to left handed - or is that already done too? :)

---

### Post by slyn4ice on 2008-07-16
> **phantomjoker said:**
> yer - I cant say that sounds right.

is there any software you can download or drivers to enable you to switch your touchpad settings to left handed - or is that already done too? :)

Well, i guess that's what i am trying to find out :) There is no left/right hand setting in the gsynaptics package. I guess it is controlled globally by the Preferences->Mouse settings.

As long as i can have the touchpad be left-handed without the single tap bringing the context menu but instead always being a click - than i am fine. 

Even though without changing the acceleration to max in the mouse settings i have to scroll like crazy to get from one end to the other (1920x1200 on a 17" LCD :)). Of course when i plug in the usb mouse back with the acceleration on max its too sensitive so i have to change it back...

Wait, actually if i can keep everything on right-handed settings but somehow inverting primary/secondary buttons on the mouse (without changing to left-hand) would work.

So, is there a way to switch primary/secondary button roles without using the left-hand/right-hand setting in Preferences->Mouse?

I don't mind messing with some configuration files...

---

### Post by R2D2! on 2008-10-08
Well, there's a way to left(r&#305;ght?)-cl&#305;ck w&#305;th a left&#305;e touchpad:

```
&#9484;&#9472;&#9516;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9516;&#9472;&#9488;
&#9474;?&#9474;        &#9474;M&#9474;
&#9500;&#9472;&#9496;        &#9492;&#9472;&#9508;
&#9500;&#9472;&#9488;        &#9484;&#9472;&#9508;
&#9474;?&#9474;        &#9474;R&#9474;
&#9492;&#9472;&#9524;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9524;&#9472;&#9496;
```

Where R is r&#305;ght cl&#305;ck for r&#305;ght-handed, and M &#305;s m&#305;ddle cl&#305;ck. I'm not sure, but I th&#305;nk &#8220;?&#8221; are buttons 4 and 5.

I th&#305;nk th&#305;s funct&#305;on &#305;s from gsynapt&#305;cs; &#305;f not, let me know.

&#8212;Ilhu&#305;temoc &#948;

---

### Post by Orra on 2008-11-16
Hello there,

> **slyn4ice said:**
> Hello all,
So, all you lefties out there - what did you do to make this problem go away?


I've got a solution. I don't love it, because it involves changing the xorg configuration file, but it works for me.

Put the following in your /etc/xorg.conf file:
```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Option	"TapButton1"	"3"
	Option	"TapButton3"	"1"
EndSection
```

You may already have the Synaptics section, in which case you just add the "Option" lines to that.

You'll need to restart X to get this to work (reboot the computer or Ctrl+Alt+Backspace).

---


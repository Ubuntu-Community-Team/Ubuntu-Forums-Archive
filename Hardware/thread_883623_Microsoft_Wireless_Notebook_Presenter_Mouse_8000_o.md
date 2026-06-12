---
title: "Microsoft Wireless Notebook Presenter Mouse 8000 on 8.04"
date: 2008-08-08
forum: Hardware
---

### Post by Xinef on 2008-08-08
Hello,
I have been browsing some old threads that have been archived looking for a solution to a problem it seems I am not the only one to face:
I have a bluetooth mouse model Microsoft Wireless Notebook Presenter Mouse 8000 which can connect, but then some of its buttons do not work (particularly the forward and backward arrows for presentation mode).
Xorg doesn't receive any event, so I figured this had to do with some bluez configuration, but I have tried various settings based on what I could find on forums, yet without any luck.
If someone have this mouse and got it to work with all of its buttons, I would be very thankful for some help.

---

### Post by Xinef on 2008-08-08
[-o< Bump [-o<

edit: I have checked the associated devices, by doing a brute cat /dev/mouse1 or cat /dev/event9, I could see when events were sent and when they were not.
It turns out that the non functional buttons just don't send anything.
So I doubt this is an xorg.conf problem at all, it is definitely a problem with bluez...
I have no idea what kind of parameters can be used to influence the way bluetooth input peripherals are handled. Anybody with such experience ?

---

### Post by Xinef on 2008-08-10
I guess not so many people are interested by that, but I'll post my progress anyways...
So I have tried hcidump, which showed some activity when buttons were pressed, any button. So the problem doesn't seem so much about bluez anymore. I think that somehow the mouse driver here is to blame, I would say evdev... But then again, I have tried to force xorg to use mouse instead, without any difference.
I don't know if we can expect an upgrade of xorg to 7.4 on hardy, but I am a bit disappointed about not being able to use my mouse fully for this time.
Some people have mentioned some other modules... I might give it a shot.

---

### Post by rfsalomon on 2008-09-22
Please continue posting. I just got myself the same mouse and so far, after battling the bluez stack, I was able to get it working (at least in regular mouse mode). Besides the wheel and movement, all 5 buttons on the top (counting the wheel click as one) work fine.

When placed in presenter mode, however, only the volume controls work. As with your observations, I was unable to find any event thrown when the forward, back or play keys are pressed.

---

### Post by pafnow on 2008-09-24
Hello,

I'm also very interested about this topic. I'm just going on using kubuntu but I don't find how to make my mouse work properly.

For example, does someone succeed in using the Microsoft dongle (given with the mouse) for other things like data transfering ?
I've installed kbluetooth but it doesn't work and all the hci* commands also.

I hope to read you soon and that we would find a solution together. :)

---

### Post by whatsvictory on 2008-09-24
Could someone please post some links? I have managed to get the two side buttons to work for scrolling back & forth by editing the xorg.conf file but that is as far as I've gotten. Has anyone figured out how to get the side to side tilt action of the mouse wheel to work or set the sensitivity of the wheel movements yet? How did you get the volime controls to work? If I find something I'll post but like I said some links would be good....PEACE....

---

### Post by Xinef on 2008-09-28
Well, the thing is, I have tried this mouse on Fedora 9 which features the new (and still not yet finalized) Xorg 7.4
And under such circumstances, it turns out all buttons are detected under xev. The only thing I had to do is associate the buttons codes to something meaningful.
Anyways, Ubuntu 8.10 Intrepid will ship the latest version of Xorg, so hopefully, the latest evdev which should help us getting all of our mouse buttons to work.
I'll keep on posting as I make progress but I am afraid it won't be before October 30th (the release date of intrepid).

---

### Post by rfsalomon on 2008-09-29
Fedora 9 already ships with kernel 2.6.25 that has the correct mappings for the Presenter 8000. Found the info on the changelog for 2.6.25 in [http://lwn.net/Articles/268667/](http://lwn.net/Articles/268667/)

Unfortunately it seems that Hardy won't receive 2.6.25 anytime soon...

---

### Post by aytalp on 2008-10-24
Hello guys,
Is there anyone who uses the Presenter Mouse with full functionality in Ubuntu?

---

### Post by Xinef on 2008-10-24
No, not yet.
Unless one tried the beta version of 8.10, I don't think the proper button mapping can be taken into account in 8.04
We are waiting for Intrepid to be released.
Then, the best case scenario would be the mouse works out of the box, and at worst the X events should be available and we should be able to configure a proper action for such event.
Anyways, it is now just a matter of days...

---

### Post by cordel on 2008-10-26
@Xinef

You didn't happen to try it on FC9 using a built in bluetooth did ya? :grin:
Or did you use the dongle?

I'm looking for a mouse that I can either use the built in BT in my laptop or that I can use or comes with one of those ultra small USB BT dongles.

The MS notebook mice seem to be the one product I still like by them. :biggrin:
Subject to change at any time of coarse :lol:

---

### Post by Xinef on 2008-10-26
> **cordel said:**
> You didn't happen to try it on FC9 using a built in bluetooth did ya? :grin:
Or did you use the dongle?
I used the built-in BT of my laptop with FC9.
All buttons were sending events, but the presentation mode ones had to be associated with the right action before it could be fully functional so I cannot say it worked out of the box.
Yet, it eventually worked as it was supposed to, and I never even plugged the MS dongle.
Looking forward to how it will do with 8.10
Cheers

---

### Post by cordel on 2008-10-28
> **Xinef said:**
> I used the built-in BT of my laptop with FC9.
All buttons were sending events, but the presentation mode ones had to be associated with the right action before it could be fully functional so I cannot say it worked out of the box.
Yet, it eventually worked as it was supposed to, and I never even plugged the MS dongle.
Looking forward to how it will do with 8.10
Cheers

Absolutely Awesome and what I wanted to hear. I just didn't want to have to muck in the BT stack. Anything beyond that isn't very trivial. That makes two of us as I'd love to seen it in conjunction with my eee-1000 ;)

Thank you for that :D

---

### Post by vouzico on 2008-10-31
There is no sign of improvement after my upgrade to Intrepid :/

Using the native Bluetooth adapter of my laptop, xev still shows nothing when I click on the presentations buttons.

How does it look like for you guys ?

---

### Post by aytalp on 2008-10-31
Same here. Nothing is changed after 8.04 in 8.10.

Waiting for the improvements from you guys.

Thx :)

---

### Post by pafnow on 2008-11-05
Hi all !

I just upgrade my kubuntu to the 8.10 version and i succeed with my Microsoft Wireless Presenter 8000.
Now I can control my amarok from my bed with my mouse in presenter mode !

To do that, i use *xev* to detect the keycode associated to each button (before the upgrade, this didn't work) and i assign an action to each.
I create a ~/.Xmodmap as following
```
keycode 215 = XF86Close
keycode 214 = XF86Close

keycode 172 = XF86AudioPause
keycode 166 = XF86AudioPrev
keycode 167 = XF86AudioNext
```
and I activate it with *$ xmodmap ~/.Xmodmap*

If you want to activate it automatically when you open your session, go to *~/.kde/Autostart* and create a text-file named *clavier* :
[HTML]#!/bin/sh
xmodmap ~/.Xmodmap[/HTML]
and chmod it : *$ chmod +x clavier*

Now I'm trying to make it work with OpenOffice Impress because it doesn't change to the next diapo neither with *XF86AudioNext* nor *XF86Next*...
If someone find something, tell us !

Hope you will all succeed.
Sorry for my english ;)

---

### Post by Xinef on 2008-11-05
> **vouzico said:**
> xev still shows nothing when I click on the presentations buttons.> **pafnow said:**
> i use xev to detect the keycode associated to each button (before the upgrade, this didn't work)mmm seems you guys get varying results...
I haven't tried it myself as I am still working with 8.04...
Anyone using a home brewed kernel ?

---

### Post by Xinef on 2008-11-07
Hi, so I installed 8.10 on my eee 901, along with the modified kernel by Adam, but this shouldn't have any impact on the BT stack or mouse button mapping.
> **pafnow said:**
> i use *xev* to detect the keycode associated to each buttonYes, I get to do the same thing, and using Xmodmap it works now perfectly.
I just used Prior and Next for my arrow buttons keysyms in order to have things working in slideshows (which is really what I need from my mouse).

If some of you guys really don't get any input under xev **while being in presentation mode**, then post again to let us know.
But now it looks like it is working just like it should be.

---

### Post by rfsalomon on 2008-11-07
Installed 8.10 on my work machine (T61p) and the presenter buttons still didn't work. Checking the forums once more, I found this kernel related entry ([https://lists.linux-foundation.org/pipermail/bugme-new/2007-October/016869.html](https://lists.linux-foundation.org/pipermail/bugme-new/2007-October/016869.html)) and recompiled my box's kernel with the suggested changes. Works like a charm with no other changes!

---

### Post by Xinef on 2008-11-07
> **rfsalomon said:**
> Installed 8.10 on my work machine (T61p) and the presenter buttons still didn't work. Checking the forums once more, I found this kernel related entry ([https://lists.linux-foundation.org/pipermail/bugme-new/2007-October/016869.html](https://lists.linux-foundation.org/pipermail/bugme-new/2007-October/016869.html)) and recompiled my box's kernel with the suggested changes. Works like a charm with no other changes!This link shows how the buttons map are hardcoded.
I believe that using recent kernel, the buttons are mapped to no particular key symbols, but they DO have code. Hence the use of Xmodmap for pafnow and myself.
I guess either way is fine, but it sounds a bit excessive to recompile your kernel just for a couple of keysyms.
Anyways, as long as you got it working.

EDIT: there is a bug in Intrepid that unsets Xmodmap modifications after a suspend:
[https://bugs.launchpad.net/ubuntu/+bug/289781](https://bugs.launchpad.net/ubuntu/+bug/289781)
There is no clean workaround so far, so maybe I will start looking for another way... On Fedora I don't really remember what I used but it only involved associating key codes to other key codes. Will keep you guys up to date.

---

### Post by Ben___ on 2008-11-11
> **Xinef said:**
> If some of you guys really don't get any input under xev **while being in presentation mode**, then post again to let us know.
But now it looks like it is working just like it should be.

I still get no input in xev. The normal mode (all buttons) and the volume control in presentation mode works. The other buttons don't give anything...

I am using this kernel, not patched:
> uname -rvm
2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64

Have you done any special setting other than just pairing?

Ben

---

### Post by Xinef on 2008-11-11
> **Ben___ said:**
> I still get no input in xev. The normal mode (all buttons) and the volume control in presentation mode works. The other buttons don't give anything...

I am using this kernel, not patched:
> uname -rvm
2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64

Have you done any special setting other than just pairing?

Ben> uname -rvm
2.6.27-7-eeepc #1 SMP Fri Oct 31 11:36:36 MDT 2008 i686

I would be surprised if the kernel for eee is patched for this mouse in particular.
Anyone got it working on a generic kernel?
On your side, have you tried checking your xorg.conf to see if it is forcing the mouse driver to anything else than evdev?

---

### Post by Ben___ on 2008-11-11
> **Xinef said:**
> >On your side, have you tried checking your xorg.conf to see if it is forcing the mouse driver to anything else than evdev?

Do I have to force it to evdev manually? Since the update to intrepid the section about InputDevices are commented out. I have only Sections about Files, Device, Monitor, Screen and ServerLayout…

Ben

---

### Post by Xinef on 2008-11-11
> **Ben___ said:**
> Do I have to force it to evdev manually? Since the update to intrepid the section about InputDevices are commented out. I have only Sections about Files, Device, Monitor, Screen and ServerLayout…

BenNo you should not have to... One more detail: are you using your own BT adapter (or one built-in your computer), or are you using the dongle which comes with the mouse (and which is not a standard BT adapter as far as I know)
In my case, I use a built-in BT module and never really tried the original dongle...

---

### Post by Ben___ on 2008-11-11
> **Xinef said:**
> are you using your own BT adapter (or one built-in your computer), or are you using the dongle which comes with the mouse (and which is not a standard BT adapter as far as I know)

I'm using the built-in one of my Thinkpad X61.

---

### Post by Ben___ on 2008-11-11
I found out, that the mouse is added as a Keyboard. So I tried to use the most generic one and ran dpkg-reconfigure console-setup until I got us/pc105. Unfortunatly it made no impact to the problem. What do your /var/log/Xorg.0.log says, when you turn on the mouse?

Mine says:
```

(II) config/hal: Adding input device Microsoft Wireless Notebook Presenter Mouse 8000
(**) Microsoft Wireless Notebook Presenter Mouse 8000: always reports core events
(**) Microsoft Wireless Notebook Presenter Mouse 8000: Device: "/dev/input/event10"
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Found x and y relative axes
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Found 6 mouse buttons
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Found keys
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Configuring as mouse
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Wireless Notebook Presenter Mouse 8000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Wireless Notebook Presenter Mouse 8000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Wireless Notebook Presenter Mouse 8000: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Microsoft Wireless Notebook Presenter Mouse 8000: xkb_layout: "us"
(**) Microsoft Wireless Notebook Presenter Mouse 8000: YAxisMapping: buttons 4 and 5
(**) Microsoft Wireless Notebook Presenter Mouse 8000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

```

---

### Post by Xinef on 2008-11-11
```
(II) config/hal: Adding input device Microsoft Wireless Notebook Presenter Mouse 8000
(**) Microsoft Wireless Notebook Presenter Mouse 8000: always reports core events
(**) Microsoft Wireless Notebook Presenter Mouse 8000: Device: "/dev/input/event11"
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Found x and y relative axes
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Found 6 mouse buttons
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Found keys
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Configuring as mouse
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Wireless Notebook Presenter Mouse 8000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Wireless Notebook Presenter Mouse 8000: xkb_rules: "evdev"
(**) Option "xkb_model" "jp106"
(**) Microsoft Wireless Notebook Presenter Mouse 8000: xkb_model: "jp106"
(**) Option "xkb_layout" "jp,jp"
(**) Microsoft Wireless Notebook Presenter Mouse 8000: xkb_layout: "jp,jp"
(**) Option "xkb_variant" "106,"
(**) Microsoft Wireless Notebook Presenter Mouse 8000: xkb_variant: "106,"
(**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
(**) Microsoft Wireless Notebook Presenter Mouse 8000: xkb_options: "grp:alt_shift_toggle,grp_led:scroll"
(**) Microsoft Wireless Notebook Presenter Mouse 8000: YAxisMapping: buttons 4 and 5
(**) Microsoft Wireless Notebook Presenter Mouse 8000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
```this is what I get on my side with my Japanese eee PC 901.
I doubt the Japanese layout has any effect on this, but I notice Xorg seems to detect an extra "keyboard" or option with a line:
xkb_variant: "106,"
which does not appear in your case.
Now to find the why...?

---

### Post by threepwood960 on 2009-02-20
Hi, did you get configurate the presentation buttons? I have this mouse with Ubuntu 8.10 but these buttons don't work.

---

### Post by Xinef on 2009-02-20
> **threepwood960 said:**
> Hi, did you get configurate the presentation buttons? I have this mouse with Ubuntu 8.10 but these buttons don't work.
Do you get any activity with these buttons on xev ?

---

### Post by threepwood960 on 2009-02-21
No. Do you get any activity? I only get with volume buttons, but I don't the most important for me: the next and previous slide.

---

### Post by Xinef on 2009-02-21
> **threepwood960 said:**
> Do you get any activity?
Yes, normally you should get activity. (in "presentation" mode, that is)
This is how you can retrieve the codes to configure what you want these buttons to do. You can write a script which will, for instance, associate these buttons to page up/down. But if you get no activity, then the buttons are just not configured at all...
You can show us the relevant portion of your /var/log/Xorg.0.log , but the default scenario usually is xev activity out of the box.

---

### Post by threepwood960 on 2009-02-22
At presentation mode I get the following, with volume buttons:

```
MappingNotify event, serial 63, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

MappingNotify event, serial 63, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 247

FocusIn event, serial 63, synthetic NO, window 0x4800001,
    mode NotifyGrab, detail NotifyPointer

KeymapNotify event, serial 63, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   4   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 65, synthetic NO, window 0x4800001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 65, synthetic NO, window 0x4800001,
    mode NotifyGrab, detail NotifyPointer

KeymapNotify event, serial 65, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   8   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 65, synthetic NO, window 0x4800001,
    mode NotifyUngrab, detail NotifyPointer

MappingNotify event, serial 65, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

```

But I don't get nothing with the arrow buttons. And the Xorg log give this:

```
(II) config/hal: Adding input device Microsoft Wireless Notebook Presenter Mouse 8000
(**) Microsoft Wireless Notebook Presenter Mouse 8000: always reports core events
(**) Microsoft Wireless Notebook Presenter Mouse 8000: Device: "/dev/input/event11"
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Found x and y relative axes
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Found 6 mouse buttons
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Found keys
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Configuring as mouse
(II) Microsoft Wireless Notebook Presenter Mouse 8000: Configuring as keyboard
(II) XINPUT: Adding extended input device "Microsoft Wireless Notebook Presenter Mouse 8000" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Microsoft Wireless Notebook Presenter Mouse 8000: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Microsoft Wireless Notebook Presenter Mouse 8000: xkb_model: "pc105"
(**) Option "xkb_layout" "es"
(**) Microsoft Wireless Notebook Presenter Mouse 8000: xkb_layout: "es"
(**) Microsoft Wireless Notebook Presenter Mouse 8000: YAxisMapping: buttons 4 and 5
(**) Microsoft Wireless Notebook Presenter Mouse 8000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

```

---

### Post by Xinef on 2009-02-23
You seem to have the same symptoms and Xorg.log as Ben___
He never reported back so it is hard to know if he got his problem fixed or not eventually, but I will make the same remark:
Xorg seems to detect an extra "keyboard" or option with a line: xkb_variant in my log.
There has to be something to it, so we know it is most likely related to the way the mouse is detected by Xorg. What must be found is what element influences that: Xorg version? kernel? For starters, have you tried with a different bluetooth adapter? Or tried to associate the mouse in bluetooth while in presentation mode?

---

### Post by threepwood960 on 2009-02-24
Thanks Xinef, I have associated the mouse in presentation mode, but it's the same: it works the default mode but not the presentation mode. The xorg version is 1:7.4~5ubuntu3 and the kernel is 2.6.27-11-generic.

I will try this evening with the microsoft adapter. Thanks,

Iam.

---

### Post by KSeeSharp on 2009-02-25
I am riding on the same boat. Did anyone of you have your mouse's (8000 model) scroll button working? It does not work for me (8.10, not using the dongle). Although the left, middle and right buttons work. xev does not see anything when I scroll so I did not think editing xorg.conf would have helped. Please help!

---


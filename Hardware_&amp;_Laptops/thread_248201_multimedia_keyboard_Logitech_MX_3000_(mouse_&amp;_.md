---
title: "multimedia keyboard Logitech MX 3000 (mouse &amp; keyboard)"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by Psykotik on 2006-08-31
Hi everybody,

I've been looking in many ubuntu boards to resolve my problem : many of my multimedia keys from my Logitech MX 3000 keyboard don't work. I've been through many receipts, with no luck. However, don't be rude with me, I'm pretty new in the linux world.

I own a LX 700 keyboard and a MX 600 mouse; if I don't mind getting all mouse buttons to work, I would enjoy using multimedia buttons. Some of them work, some don't. The ones that don't, are not detected at all by Ubuntu.

I've tried to set them using "keys shortcuts" (translated from french), which works nice for a few keys. Same applies to Keytouch software; but it seems like it is normal, since...

When I run the "xev" command, my undetected keys don't show any code. Thus, the warping is useless, IMHO. Getting them detected would give a meaning both to keytouch configurator and to "keys shortcuts" 

Here is a part of my xorg.conf:

```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "ch"
    Option        "XkbVariant"    "fr"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
        Option          "Emulate3Buttons"   "false"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"       "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection
```

I've tried to fill

"XkbModel"    "pc105"

with other values, with no luck. My only success has been to get with every boot a question about if I "prefer to keep the xorg or gnome keyboard configuration". BTW, if someone could help me to get rid of this (using a clean way)...

However, the most annoying stays my multimedias keys which are dead. One could start a webcam software, another one my /home, and so on. Has ever someone set this kind of keyboard ?

Thanks.

---

### Post by Psykotik on 2006-10-10
no one ? I can't believe no advanced logitech keyboard users read this forum...

---

### Post by polly1 on 2006-10-12
Hi Psykotik

I have done some research and possible solutions are :-

You could try to alter System>Preferences>Keyboard>Layouts dropdown menu,so that one of the Logitech entries possibly matches the description your model MX3000 model. It may be a case of trying them all, but I should try Logitech Cordless Desktop Optical entry first.
 
Then close the Preferences, without "resetting the defaults" button because
the layout will revert back to the generic model if you do, which you dont want. Go to :-

System>Preferences>Keyboard Shortcuts to check the the multimedia buttons etc now operate OK with the first entry mentioned above. If they do, problem over. Close the shortcuts down and enjoy your keyboard and perhaps mouse. You will need to repeat this procedure for each Logitech keyboard entry entry, until you find one that works.
 
If you have no luck the other solution involves a lot of hacking and does need reading up from the book UBUNTU HACKS, published by O`REIllY  
Media Inc. which is very useful for generally hacking Ubuntu. The information is set out between pages 176 to 184.

There is an on-line edition at [http://safari.oreilly.com/0596527209](http://safari.oreilly.com/0596527209), which is fee based, unfortunately.

Im sorry I am unable to give details of the hacks on this post, but they are complex, and would be very difficult to detail here. 

Finally, your particular keyboard drivers may be included on the up-grade Ubuntu due on 01 December.

Cheers

---

### Post by polly1 on 2006-10-13
Hi Psykotic

Re. my reply of 1 day ago, I am going to try to set up my Microsoft Multimedia Keyboard by following the hacks outlined in "UBUNTU HACKS" and I
hope to get back to you, with the instructions, within the next week.

Cheers

---

### Post by Psykotik on 2006-10-27
> **polly1 said:**
> Hi Psykotic

Re. my reply of 1 day ago, I am going to try to set up my Microsoft Multimedia Keyboard by following the hacks outlined in "UBUNTU HACKS" and I
hope to get back to you, with the instructions, within the next week.

Cheers

Hi Polly,

Sorry about the delay, and thank you for your answer. I was quite desperate about my keyboard...

Do you have more information ? What about you "Ubuntu hacks" ? You are my best hope :)

---

### Post by marc_th on 2006-11-02
I am using a Logtech MX 3000 (Mouse & keyboard) and am also trying to configure it. Following polly1 advice, I was able to configure around 50% of the keyboard buttons using any one of the Logitech Cordless keyboard layouts under System>Preferences>Keyboard.  Most of the multimedia buttons work if you re-assign via Keyboard Shortcuts as suggested.  This is good enough for me--most of the other buttons are redundant and silly anyway.

One minor yet nasty issue arises when you press the Hibernate button.  When pressed the computer hibernates ok, but I've found no way to waking the computer up, so I have yank the power cord and cold boot back in.  There appears to be no way of disabling the button.

---

### Post by polly1 on 2006-11-06
Hi

There is software called "KeyTouch" available, which can be downloaded from
[http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/). Version 2.2 can be installed, using Deb 
installer. The later 2.3 needs to be installed from source, as it is a tarball file. You will probably need "Keytouch Editor" as the MX 3000 does not appear on "KeyTouch" list of models.

This program appears on System>Administration>Menu, when installed and works OK for my pretty basic keyboard model.

There are "How To`s" in the Ubuntu and Linux forums to configure multi button mice and install tar.gz files.

Hope this helps

---

### Post by polly1 on 2006-11-07
Hi 

Re my post of 1 day ago, the links you require are

[http://www.ubuntuforums.org/showthread.php?t=246770&highlight=Multi+Button+mouse](http://www.ubuntuforums.org/showthread.php?t=246770&highlight=Multi+Button+mouse)   

for configuring your mouse and

 [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

for installing from source.

I should have mentioned that the software "KeyTouch" and "KeyTouch Editor" are in Synaptic, but the download software from the link given in my previous post are later versions.

Finally, "KeyTouch" is a package for configuring shortcuts on keyboards and probably replicates the "hacks" as shown in the book "Ubuntu Hacks"

best of luck

Cheers

---

### Post by Psykotik on 2006-12-07
Well, I opened a bug on launchpad : [https://bugs.launchpad.net/distros/ubuntu/+source/control-center/+bug/73619](https://bugs.launchpad.net/distros/ubuntu/+source/control-center/+bug/73619)

That's sound weird... Is there really so few people using this keyboard ?

---

### Post by Psykotik on 2006-12-28
I hope many many people received that keyboard as a christmas present. Maybe it will help me ](*,)

---

### Post by Psykotik on 2007-01-09
I finally found a workaround.

One has to install keytouch AND plug BOTH mouse and keyboard in PS/2 ports.

In consequence, this bug is related to the keyboard USB port management.

---

### Post by HardCoder on 2007-01-11
Hi there! I have the very same keyboard. When i used Gentoo i had it all working by following the directions in this thread.
[http://forums.gentoo.org/viewtopic-t-246605.html](http://forums.gentoo.org/viewtopic-t-246605.html)

---

### Post by dtarase on 2008-05-10
New software available for Logitech MX 3000. I got my Logitech 3000 keyboard working using hidpoint software. All my multimedia and office keys are working like a treat.  software is availble for free download . visit [www.hidpoint.com](www.hidpoint.com)

---

### Post by Princey on 2008-05-10
I'd really like to know what version you tried it and it worked as it just quites on Hardy. Their list did state that it supports 6.06 which I think is Dapper.

---

### Post by dtarase on 2008-05-14
Hi Princey,
   I use ubuntu 6.0.6 and the software works fine. I think u have tried on ubuntu 8.04 (hardy). I checked there forums and came to know that shortly they will support 8.04 also. Plz subscribe to their mailing list.

thanks

---

### Post by Princey on 2008-05-14
Thanks for your answer. I have already subscribed to their mailing list and registered on their forums as well. I figure the more requests, the more attention is given to getting it to work with Hardy.

---


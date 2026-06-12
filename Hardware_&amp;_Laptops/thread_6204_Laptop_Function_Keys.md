---
title: "Laptop Function Keys"
date: 2004-11-26
forum: Hardware &amp; Laptops
---

### Post by Jerrac on 2004-11-26
Is there a way to get my laptops function keys working? You know the ones to mute the sound or change the volume or brightness. That would be really cool! Especially since they are currently broken in my Windows XP installation... lol

---

### Post by paulproteus on 2004-11-26
Tell us more details about your laptop: What make, what model?  Mine are working great on my Apple iBook G4 because of the program pbbuttons that Ubuntu bundles.  Maybe there's something like that already on your Ubuntu system for your laptop - so help us help you! (-:

---

### Post by knappen on 2004-11-27
Update your bios and see if that works.

Dont think it is an Ubuntu issue.

---

### Post by Jerrac on 2004-11-27
[QUOTE=knappen]Update your bios and see if that works.

Dont think it is an Ubuntu issue.[/QUOTE]
 Eh, I doubt it is the bios. Windows has to have a program installed for them to work, so....

My laptop is a Sony Vaio PCG-FRV37 Notebook. The only program I know of for sony notebooks is sonypi, and when I have installed that, it doesn't do anything.

---

### Post by knappen on 2004-11-27
I am not using a Sony but it works fine for me. Dont think I have a special program for those Fn buttons.

If they dont work in Windows either it sounds like it is a BIOS issue.

---

### Post by Jerrac on 2004-11-27
[QUOTE=knappen]I am not using a Sony but it works fine for me. Dont think I have a special program for those Fn buttons.

If they dont work in Windows either it sounds like it is a BIOS issue.[/QUOTE]
 Eh? Then why does sony tell me to reinstall HotKeys program when I ask how to fix my function keys? Which did work when I first got my laptop.

---

### Post by knappen on 2004-11-27
You do mean the buttons where you have to press the Fn key first?

Or is it the shortcut keys to the browser, email etc.?

---

### Post by Jerrac on 2004-11-27
[QUOTE=knappen]You do mean the buttons where you have to press the Fn key first?[/QUOTE]
That, I don't have the other kind of buttons.

I just checked my bios and there isn't anything in there for the function keys. So....

---

### Post by knappen on 2004-11-27
I have just been using the keys to change the brightness off the screen and that works fine. The other keys for stop and play etc. dont do a thing.

---

### Post by muzzy on 2004-12-26
First, you have to know the keycodes. In term start **xev** , move mouse to black square and press thise buttons. Keycodes will appear in term. The install **hotkeys**. You have to edit the keyboard file (xml) like this
```

<?xml version="1.0"?>

<definition>

  <config model="HP nx9020">

    <VolUp        keycode="176" adj="2"/>
    <VolDown      keycode="174" adj="2"/>
    <Mute         keycode="160"/>

  </config>

  <contributor>
    <name>to be added</name>
    <email>to be added</email>
  </contributor>

</definition>

``` 
It's stored in /usr/share/hotkeys/*.def, eg.  /usr/share/hotkeys/muzzy.def
Than, run **hotkeys -t muzzy**
And thats all

---

### Post by iltofa on 2004-12-26
hi all.

Tested on HP NX9105. 

First I installed hotkeys with synaptic, then, as I tested the itouch logitech driver
under windows for the laptop integrated hotkeys, I use the itouch scheme:

hotkeys -t itouch

I think testing the keys with xev as suggested by muzzy is a good idea!

Bye

---

### Post by jisakiel on 2005-01-06
What if xev doesn't show any events for the Fn keys when pressed? My "hardware" Fn combinations still work, such as Fn-F1 (wireless switch, light turns on/off) or Fn-F6/7 (brightness) and Fn-F11 (turns off the screen). Only that the volume keys don't, and it's quite disgusting :D


PS: My laptop is a Fujitsu-Siemens Amilo M1420... centrino, all the usual. I'm in some hoary-stable mixed distro right now.

---

### Post by telmo on 2005-01-09
I got an HP Pavilion ZX5051EA and this is how it goes... in this model, as well as others, not all of the keys work. Even the fn ones. I've seen Toshiba's (for ex.) that can't even do that without the respective drivers (for Windows of course!)

But since i don't have (nor like) a toshiba laptop, i can only say that i'm going quite desperate to get all the keys to work. The basic functions do work, but not all the shortcuts... :(

Let's just hope that in a very near future they all work.

---

### Post by smtanner on 2005-02-23
[QUOTE=jisakiel]What if xev doesn't show any events for the Fn keys when pressed? My "hardware" Fn combinations still work, such as Fn-F1 (wireless switch, light turns on/off) or Fn-F6/7 (brightness) and Fn-F11 (turns off the screen). Only that the volume keys don't, and it's quite disgusting :D


PS: My laptop is a Fujitsu-Siemens Amilo M1420... centrino, all the usual. I'm in some hoary-stable mixed distro right now.[/QUOTE]

On my laptop, some the keys are hardwired to their function.  These keys work without any software and do not show any codes with xev.  My screen brightness is hardwired.  Other keys are software controlled and require hotkeys to work.  These keys show codes with xev.  My volume button is this way.  So I have to use hotkeys to get my volume to work but do not need it for screen brightness.  Your laptop is probably the same

---

### Post by knappen on 2005-02-24
Same for me.

---

### Post by TheAngryPenguin on 2005-02-28
Quick Q:  How does one go about disabling the hotkeys splash screen?

---

### Post by aquarichy on 2005-03-08
[QUOTE=smtanner]On my laptop, some the keys are hardwired to their function.  These keys work without any software and do not show any codes with xev.  My screen brightness is hardwired.  Other keys are software controlled and require hotkeys to work.  These keys show codes with xev.  My volume button is this way.  So I have to use hotkeys to get my volume to work but do not need it for screen brightness.  Your laptop is probably the same[/QUOTE]
 And what about when Fn keys are not wired to the hardware and do not produce anything in Xev, like my volume keys?  I am afraid my case is hopeless.

---

### Post by jsgotangco on 2005-03-08
In my laptop, an ECS G551, some of the function keys work (sound and numlock) but you have to map it out  as a Gnome keyboard shortcut. The function key to toggle display (ie, projector, monitor) freezes the whole system forcing me to hard reboot.

---

### Post by Scirious on 2005-03-15
Well, I'm new to this forum, but I have one question abou these hotkeys. How can I make hotkeys to start with system boot?

Thaks,
Scirious.

---

### Post by TheAngryPenguin on 2005-03-15
[QUOTE=Scirious]Well, I'm new to this forum, but I have one question abou these hotkeys. How can I make hotkeys to start with system boot?[/QUOTE]
Not sure about how to start [FONT=Lucida Console]xev[/FONT] at boot, but you can make it start when you log into Gnome by following the directions [here](http://ubuntuguide.org/#runprogramsstartupgnome).

Still waiting on any info about disabling [FONT=Lucida Console]xev[/FONT]'s splash screen...

---

### Post by smtanner on 2005-03-16
[QUOTE=aquarichy]And what about when Fn keys are not wired to the hardware and do not produce anything in Xev, like my volume keys?  I am afraid my case is hopeless.[/QUOTE]

Hmm, messing around with my keyboard it appears I have some keys like this too.  My standby key doesn't produce anything in Xev and doesn't appear to do anything.  Perhaps these keys require special windows drivers.  If that is the case, you are pretty much screwed as far as those keys are concerned.  It's a minor annoyance.

---

### Post by Slalomsk8er on 2005-03-17
[http://www.ubuntuforums.org/showpost.php?p=96599&postcount=10](http://www.ubuntuforums.org/showpost.php?p=96599&postcount=10)
Maybe this helps (omke) but I have not tryed yet.

---

### Post by dave9191 on 2005-04-27
Hey knappen, 

I dont know if you are still interested, been a while. But I came accross this thread when i was trying to get my FN keys working on my vaio, and Ive managed it now. Ive explained it in my thread [here](http://www.ubuntuforums.org/showthread.php?p=149734#post149734) . Hope this helps you :)

Dave

---

### Post by knappen on 2005-04-27
Thanks Dave!

I will check out that thread.

---

### Post by gcranston on 2005-05-10
[QUOTE=jsgotangco]In my laptop, an ECS G551, some of the function keys work (sound and numlock) but you have to map it out  as a Gnome keyboard shortcut. The function key to toggle display (ie, projector, monitor) freezes the whole system forcing me to hard reboot.[/QUOTE]

I have this exact problem as well, but on a Dell Inspiron 2650.  Any help would be nice.  More with the other function keys than the display switching, but that would also be pretty sweet.  Hot swapping in and out of simul mode would probably reduce my reboots from 1/week to 1/2months making me much happier.

-Graham

---

### Post by Bartholomaeus on 2005-05-11
[QUOTE=gcranston]I have this exact problem as well, but on a Dell Inspiron 2650.  Any help would be nice.  More with the other function keys than the display switching, but that would also be pretty sweet.  Hot swapping in and out of simul mode would probably reduce my reboots from 1/week to 1/2months making me much happier.
-Graham[/QUOTE]

Hi. I have a Fujitsu Siemens Amilo K7600 and some function keys like brightness are working. But the sound-functionkeys are doing nothing. I have tested some of the solution, which were postet here and their is no difference. 
I would be very happy about an other solution for this little problem. Thanks.

---

### Post by anders.ostling on 2005-05-16
System -> Preferences -> Keyboard shortcuts. 

Thats all. I cant bealive that a simple question like this (no offense, we are all newbies at some point in time) can generate such a wild diversity of replies :-), but no one that pointed out the obvious and simple answer. 

Anders

---

### Post by gcranston on 2005-05-23
[QUOTE=anders.ostling]System -> Preferences -> Keyboard shortcuts. 

Thats all. I cant bealive that a simple question like this (no offense, we are all newbies at some point in time) can generate such a wild diversity of replies :-), but no one that pointed out the obvious and simple answer. 

Anders[/QUOTE]


Thanks, great.  But what is this _cough_ obvious and simple answer 'cause it's far from both to me...

-Graham

---

### Post by gcranston on 2005-05-23
[QUOTE=anders.ostling]System -> Preferences -> Keyboard shortcuts. 

Thats all. I cant bealive that a simple question like this (no offense, we are all newbies at some point in time) can generate such a wild diversity of replies :-), but no one that pointed out the obvious and simple answer. 

Anders[/QUOTE]

Except that does not work.  There is no value for screen brightness, or presentation mode to assign under shortcuts and many posts above cite that solution as not working sometimes for eject and some volume/mute functions.  Clearly there is a deeper problem with a less "obvious and simple answer"

---

### Post by knappen on 2005-05-24
[QUOTE=anders.ostling]System -> Preferences -> Keyboard shortcuts. 

Thats all. I cant bealive that a simple question like this (no offense, we are all newbies at some point in time) can generate such a wild diversity of replies :-), but no one that pointed out the obvious and simple answer. 

Anders[/QUOTE]


Did you read this thread? I dont think so!

---

### Post by gcranston on 2005-06-05
SUCCESS!!
(for me at least)

I was running Warty 4.10 using Hoary sources in /etc/apt/sources.list (just changed all instances of "warty" to "hoary", apt-get update/upgrade) when I originally posted in this forum.  Since then I have run apt-get dist-upgrade to get the new kernel and other packages that come with it (some x-system-core and other stuff) and my Laptop function keys now work!  Given my across the board performance increase since the upgrade without losing any of the customised stuff I'd done under Warty, I recommend dist-upgrade to anyone out there still on warty.  Godd luck to you all!!

-Graham

*Fokker... Out!*

---

### Post by andrewsawyer on 2005-06-14
[QUOTE=TheAngryPenguin]Quick Q:  How does one go about disabling the hotkeys splash screen?[/QUOTE]

hotkeys -Z should load hotkeys without the splash screen.

I am having the same problem with my Acer C110 in that the brightness (Fn Left/Right) works, as does Fn F11 (for NumLk), however items that aren't hardwired for example Fn F7 to turn off the pointing device or Fn F8 to mute etc don't work.

Having a look at hotkeys help reveals that it is supposed to work with the following:
```
Supported keyboards: (with corresponding options to --kbd-list or -l)
    aceraspire1300      - Acer Aspire 1300 Series Keyboard
    acer430     - Acer TravelMate 430
    applepro    - Apple Pro Keyboard
    acerwl      - Acer Wireless Keyboard
    inspiron8100        - Dell Inspiron 8100 Notebook
    btc8190     - BTC Smart Office (8190)
    btc9000     - BTC 9000
    hp5181      - HP 5181 Internet Keyboard
    ibook       - iBook Internal Keyboard
    logitech-cfo        - Logitech Cordless Freedom Optical Keyboard
    ipanel      - Asus IPanel
    itouch      - Logitech Cordless iTouch/Internet/Cordless Desktop
    kb9930      - IBM Rapid Access II Keyboard
    kb9963      - Compaq KB-9963 keyboard
    kbp8993     - Chicony KBP-8993 keyboard
    logitech-nav-usb    - Logitech Internet Navigator USB
    mck800      - Process MCK-800
    msnatpro    - Microsoft Natural Keyboard Pro
    msnet       - Microsoft Internet Keyboard
    msnetpro    - Microsoft Internet Pro Keyboard
    mx1998      - Memorex MX1998 Keyboard
    mx2500      - Memorex MX2500 Keyboard
    mx3000      - Memorex MX3000 Keyboard
    orktekusb   - ORKTEK USB Hub/keyboard
    pb5140w     - Packerd Bell Model 5140W
    polypix     - Polypix Keyboard
    sk2500      - Fujitsu/Logitech/Trust SK2500 Keyboard / Liteon-ak2500
    sk2501a     - Silitek SK5210A Keyboard
    sk2505      - SK-2505 Keyboard
    sk2800c     - SK-2800C
    sk7100      - Silitek SK7100 Keyboard
    sk9925      - Silitek SK-9925 USB Keyboard
    uniwilln243s1       - Uniwill N243S1

```

As the acer430 doesn't work (the only other TravelMate in the option), I guess I will just keep trying the other options and see if any of the others will work!

Another way (which I'm currently using) would be System>>Preferences>>Keyboard Shortcuts and put them in using CTRL instead of Fn.  So if Fn F4 is supposed to make the laptop sleep, use CTRL F4 instead.

---

### Post by liviococcia on 2007-04-02
Hello members, i recon you could really help me out....

I'm using Windows XP sp2

I've got a Fujitsu-Siemens Amilo Pro v2060, some of the funtion keys work but the ones that i want to use don't, these are F6 (volume up) and F7 (volume down), F8 (mute) does work, i see a little red 'x' over the volume icon in the quicklaunch bar.

I have looked at the BIO's, and there was nothing obvious, no settings to try and change.

My question to the forum, is you been posting about turning on and turning off the 'Hotkeys', and about a peice of software that is used for these 'Fn' keys, and asigning other 'Hotkeys ' to do these functions, but there is no clear instructions on how i do this, where do i go in the Windows XP settings, and where can i get any related software for the Amilo Pro v2060 'Hotkey' use.

Any guidence in simpleton terms would save my brain from exploding

Kind regards
Livio

---

### Post by dave9191 on 2007-04-02
Hey, 

I don't mean to be rude or unhelpful, but wouldn't it make more sense to ask a windows xp question on windows xp forums somewhere rather then on a Linux forum? Not many people round here use windows and you could get help quicker elsewhere. 

All the talk about hotkeys on this forums is for Ubuntu linux and not windows xp.

You could try the Fujitsu-Siemens website for any useful software or just send them an emial directly with your issue. 

--
Dave

---


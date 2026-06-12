---
title: "Mouse Freezes(Saitek Cyborg MMO7)"
date: 2012-07-12
forum: Hardware
---

### Post by Rukiri on 2012-07-12
I'm sure it's a common problem but it's driving me nuts.. I have tried just about all the "fixes" for linux for this mouse and it'll freeze now sometimes it'll come back right away(5 seconds) sometimes it freezes indefinitely.

I'm thinking it's a xorg problem, might try wayland and see how that goes or could be a Nvidia issue which kinda makes linux unusable for me unless I'm using Xnomad or Awesome but most of the time I'm just using photoshop, programming, and watching youtube so I'm kinda use to the mouse.

Anyone have any ideas?

---

### Post by Rukiri on 2012-08-06
Just a bump, I'm also using alpha 3 of 12.10 beta.  CTRL+ALT+F1 than F7 seems to fix it but I really want/need a permanent fix. 

I've tried the xorg.conf suggestions however when I add anything to xorg.conf.d in /usr/share/X11/ it freezes on bootup until I go into the terminal directly and remove it. 

I could always buy another mouse, but I spent $120, I like this mouse a lot.  (I got it when it was fresh of the presses)

---

### Post by MrGrey1 on 2012-12-09
I've sort of resolved my issues with the MMO7 on xubuntu. It should also work for you on Ubuntu. The mouse still freezes on first boot and from what I have read it's a bug that effects all rat mice and I gather there's not much chance of it being fixed anytime soon.
See here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/615892](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/615892)
On the up side restarting the x server does seem to fix this issue. We used to be able to just Ctrl-Alt-Backspace to restart x but the geniuses running the show decided this was bad mkay and disabled this option. 
To turn this option back on the command is

```
setxkbmap -option terminate:ctrl_alt_bksp
```

To make it permanent just add it to your autostart list. For me on xubuntu this is in SettingsManager > Session and Startup > Application Autostart.
This makes it 'relatively' less painful to get it working although having to login twice is still a bit of a PITA. I'm going to try suspending my system instead of shutting down and see if that stops me having to login twice but I haven't tested this yet.

To get all the buttons working correctly including the side scroll

```
sudo nano /etc/X11/xorg.conf.d/910-rat.conf
```

and enter 

```
Section "InputClass"
        Identifier "Mouse Remap"
        MatchProduct "Saitek Cyborg M.M.O.7 Gaming Mouse"
        MatchDevicePath "/dev/input/event*"
        Option "Buttons"        "19"
        Option "ButtonMapping" "1 2 3 4 5 0 0 8 9 10 11 12 13 14 15 16 17 7 6"
        Option "ZAxisMapping" "4 5 6 7"
EndSection
```

Just a little warning.
My MMO7 was originally setup on windows 7. I used the MMO7 application that disables the mode buttons in windows. ie the two small orange sub buttons on the left/right buttons and the button on the right hand side. I believe by doing this it sets and stores the disabled setting onboard the mouse thereby disabling those buttons in ubuntu as well. As a result I haven't had any problems with the mode buttons. If you haven't also done this you may get issues with the mode buttons.
I'm taking a guess but the mode buttons are likely button 20 21 & 22. I may try re-enabling the buttons in windows and seeing if they show up in xev as at the moment there is no input from any of them. I will post back if I have anything else to add.
Hope it helps. :)

EDIT: My final configuration below. NO MORE FREEZES w00t!

```
Section "InputClass"
        Identifier "Mouse Remap"
        MatchProduct "Saitek Cyborg M.M.O.7 Gaming Mouse"
        MatchDevicePath "/dev/input/event*"
        Option "Buttons"        "24"
        Option "ButtonMapping" "1 2 3 4 5 0 0 8 9 10 11 12 13 14 15 16 17 7 6 0$
        Option "ZAxisMapping" "4 5 6 7"
        Option "AutoReleaseButtons" "20 21 22 23 24"
EndSection
```

---

### Post by MrGrey1 on 2012-12-25
Reinstalled recently and realised I made a mistake in the previous post...
Place conf file here...

```
/usr/share/X11/xorg.conf.d/910-rat.conf
```

---

### Post by Barsoianu Radu on 2013-02-25
Nicely done m8. Can you please help me with a issue i have with the same mouse ? I'm trying to bind the buttons to key events, i'm using it mostly to play wow, and wow by default only recognizes 5 mouse buttons. BTNX does not work, EasyStroke has a 1-2 secconds delay. I heard that u can can bind mouse click to keys directly in xorg.conf ? Any ideea would be apreciated.

---

### Post by Narcas on 2013-02-26
I did everything that you said but it's still not working. For example I can just click in the toolbar nowhere else.. Help?
Thanks!

---

### Post by Barsoianu Radu on 2013-02-27
a thread about the same issue has also been opened here : 

[http://ubuntuforums.org/showthread.php?t=2096812&page=2](http://ubuntuforums.org/showthread.php?t=2096812&page=2)

but without any results so far.

---

### Post by MrGrey1 on 2013-03-12
> **Barsoianu Radu said:**
> Nicely done m8. Can you please help me with a issue i have with the same mouse ? I'm trying to bind the buttons to key events, i'm using it mostly to play wow, and wow by default only recognizes 5 mouse buttons. BTNX does not work, EasyStroke has a 1-2 secconds delay. I heard that u can can bind mouse click to keys directly in xorg.conf ? Any ideea would be apreciated.

Sorry about the delayed response. Only just got the email notification... anyways.

I use xbindkeys for macros on the mouse. There's a GUI xbindkeys-config. Install it and it's dependancies...
Have a look here under 'Text Entry Shortcuts' for installation guide
[https://help.ubuntu.com/community/KeyboardShortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)

Format for the keys in the GUI is a little tricky and took me a while to get susesd.
left is button 1
middle : 3
right : 2
wheel up : 4
wheel down : 5
backward button : 8   forward button : 9  (the two upper thumb buttons)
alternate lower button : 10 ( the button on the horizontal lower thumb rest)
forward1 : 11  backward1 : 12  (the two lower larger back forward buttons)
snipe : 17
wheel right : 18 left : 19
thumbstick up : 13  
thumbstick down : 14  
thumbstick forward : 15 
thumbstick backward : 16

Now say you want the sniper button in xbindkeys to hit the enter key when pushed, the format is;

name;     sniper
Key;       m:0x10 + b:17          
Action;    xte 'key Return'

if you want a macro in then

name;    sniper
Key;       m:0x10 + b:17 
Action;    xvkbd -xsendevent -text "macro here"

The 'm:0x10' bit is constant no matter, I believe it's got something to do with it being a mouse event, the 'b:17' is the button on the mouse you want to use, see the list above. The 'macro' format is probably what you are looking for in WOW. I have a game that doesn't recognise the extra buttons if I use the 1st method above. It does however recognise the 'text' input from the extra buttons if I use the second format.

More help here
[http://www.butlerpc.net/blog/2011/01/using-xbindkeys-on-ubuntu-linux-to-remap-key-commands/](http://www.butlerpc.net/blog/2011/01/using-xbindkeys-on-ubuntu-linux-to-remap-key-commands/)

Hope this gets you going in the right direction. ;

---

### Post by MrGrey1 on 2013-03-12
> **Narcas said:**
> I did everything that you said but it's still not working. For example I can just click in the toolbar nowhere else.. Help?
Thanks!

Sounds like the buttons are still not releasing window focus for you. Did you try the 'Ctrl Alt Backspace' method I mentioned to reload your desktop? That's worked for me with that issue.

---

### Post by Narcas on 2013-03-21
> **MrGrey1 said:**
> Sounds like the buttons are still not releasing window focus for you. Did you try the 'Ctrl Alt Backspace' method I mentioned to reload your desktop? That's worked for me with that issue.

Thanks! It helped.

---


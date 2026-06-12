---
title: "DELL + suspend + function keys"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by markr on 2005-12-13
I'm running KUbuntu at the moment and it rocks!!

I do have a couple of problems however that I'm hoping the community can help to resolve.

Firstly,  I have suspend (But not hibernate, that's next) fully working when I issue the sleep.sh script as sudo.  However,  if I close my lid (or press Fn + esc) nothing happens.  I suspect that the close lid and function key combo are getting ignored by the system.  Anyone any idea on how to get them working?

Secondly, a similar sort of problem.  I can't use my Fn+Vol Up/Down keys in KUbuntu, they also seem to be ignored.

Anybody have a dell and had any look with these?

Thanks

Mark.

---

### Post by ranf on 2005-12-13
In a terminal run this:
```
sudo tail -f -c0 /var/log/acpid
```

then close the lid and look if there are some new lines in the terminal.

---

### Post by anil_robo on 2005-12-17
I'm running Ubuntu 5.10 on Dell Inspiron 6000 and the system hibernates when I close the lid, or press Fn+F2. In order to wake it up again, I have to open the lid, but there's no key shortcut to wait it up I guess.

Upon waking up, the display is garbled for a moment, and then I'm taken to a shining desktop! :)

---

### Post by Vorian on 2005-12-18
[QUOTE=anil_robo]I'm running Ubuntu 5.10 on Dell Inspiron 6000 and the system hibernates when I close the lid, or press Fn+F2.[/QUOTE]

Doesn't using Fn F2 turn off your wifi?  I have the 6000, the only problem I have is the graphics display when booting.....    

I have installed KDE in Ubuntu, but that hasn't created a hybernation problem.

---

### Post by anil_robo on 2005-12-19
[quote=Vorian]Doesn't using Fn F2 turn off your wifi?[/quote]
Yes it does turn my wifi off indeed!
>  I have the 6000, the only problem I have is the graphics display when booting.....    
But my system displays the boot graphics well! :)
> I have installed KDE in Ubuntu, but that hasn't created a hybernation problem.
I am running Breezy with GNOME (metacity)

---

### Post by .t. on 2005-12-19
[QUOTE=markr]I'm running KUbuntu at the moment and it rocks!![/QUOTE]
I surely agree with you there and Dapper seems to be working well.
[QUOTE=markr]
Secondly, a similar sort of problem.  I can't use my Fn+Vol Up/Down keys in KUbuntu, they also seem to be ignored.
[/QUOTE]
They are ignored because the kernel/Xserver knows not what to do with them.
If you do an "apt-get install xbindkeys-config; apt-get install aumix", you can set up xbindkeys so that when it receives that keypress, it runs "mute", say.

Here is my /etc/xbindkeys.rc:

```
###########################
# xbindkeys configuration #
###########################
#
# Version: 0.1.3
#
# If you edit this, do not forget to uncomment any lines that you change.
# The pound(#) symbol may be used anywhere for comments.
#
# A list of keys is in /usr/include/X11/keysym.h and in
# /usr/include/X11/keysymdef.h 
# The XK_ is not needed. 
#
# List of modifier (on my keyboard): 
#   Control, Shift, Mod1 (Alt), Mod2 (NumLock), 
#   Mod3 (CapsLock), Mod4, Mod5 (Scroll). 
#
# Another way to specifie a key is to use 'xev' and set the 
# keycode with c:nnn or the modifier with m:nnn where nnn is 
# the keycode or the state returned by xev 
#
# This file is created by xbindkey_config 
# The structure is : 
# # Remark 
# "command" 
# m:xxx + c:xxx 
# Shift+... 




#keystate_numlock = enable
#keystate_scrolllock = enable
#keystate_capslock = enable



"xbindkeys_show"
   control+shift + q

#Mute
"mute"
    m:0x0 + c:160
    NoSymbol 

#Vol Up
"aumix -v +1"
    m:0x0 + c:176
    NoSymbol

#Vol Down
"aumix -v -1"
    m:0x0 + c:174
    NoSymbol 

#
# End of xbindkeys configuration

```

and my startup script (/etc/init.d/xbindkeys) - it's ultra-basic!:
```

#!/bin/sh
xbindkeys -f /etc/xbindkeys.rc

```

I chmodded that to executable, and linked to it from /etc/rc*.d/S99xbindkeys (except from rc0.d and rc6.d - that would be pointless). Then I rebooted to check that all works, and it does! I also have (on my Inspiron 6000) the play|pause/stop/forward/back keys, and will set them up to control XMMS playback (using xmms from the console is possible, I believe).

I hope this helps. 

NB: I haven't bothered with suspend yet.

EDIT: MPlayer seems to natively support my multimedia "playback" keys, but I am surprised that others do not, as it is a surprisingly useful feature!

---

### Post by Vorian on 2005-12-19
[QUOTE=anil_robo]But my system displays the boot graphics well! :)[/QUOTE]
What does your xorg.conf look like?  Do you have the ati x300 card?

I have tried to fix this a few times, broke the system, reinstalled:mad: 
I gave up, didn't seem worth the trouble...:smile:

---

### Post by s_g_robertson on 2006-01-12
[QUOTE=.t.]I surely agree with you there and Dapper seems to be working well.

They are ignored because the kernel/Xserver knows not what to do with them.
If you do an "apt-get install xbindkeys-config; apt-get install aumix", you can set up xbindkeys so that when it receives that keypress, it runs "mute", say.

Here is my /etc/xbindkeys.rc:

```
###########################
# xbindkeys configuration #
###########################
#
# Version: 0.1.3
#
# If you edit this, do not forget to uncomment any lines that you change.
# The pound(#) symbol may be used anywhere for comments.
#
# A list of keys is in /usr/include/X11/keysym.h and in
# /usr/include/X11/keysymdef.h 
# The XK_ is not needed. 
#
# List of modifier (on my keyboard): 
#   Control, Shift, Mod1 (Alt), Mod2 (NumLock), 
#   Mod3 (CapsLock), Mod4, Mod5 (Scroll). 
#
# Another way to specifie a key is to use 'xev' and set the 
# keycode with c:nnn or the modifier with m:nnn where nnn is 
# the keycode or the state returned by xev 
#
# This file is created by xbindkey_config 
# The structure is : 
# # Remark 
# "command" 
# m:xxx + c:xxx 
# Shift+... 




#keystate_numlock = enable
#keystate_scrolllock = enable
#keystate_capslock = enable



"xbindkeys_show"
   control+shift + q

#Mute
"mute"
    m:0x0 + c:160
    NoSymbol 

#Vol Up
"aumix -v +1"
    m:0x0 + c:176
    NoSymbol

#Vol Down
"aumix -v -1"
    m:0x0 + c:174
    NoSymbol 

#
# End of xbindkeys configuration

```

and my startup script (/etc/init.d/xbindkeys) - it's ultra-basic!:
```

#!/bin/sh
xbindkeys -f /etc/xbindkeys.rc

```

I chmodded that to executable, and linked to it from /etc/rc*.d/S99xbindkeys (except from rc0.d and rc6.d - that would be pointless). Then I rebooted to check that all works, and it does! I also have (on my Inspiron 6000) the play|pause/stop/forward/back keys, and will set them up to control XMMS playback (using xmms from the console is possible, I believe).

I hope this helps. 

NB: I haven't bothered with suspend yet.

EDIT: MPlayer seems to natively support my multimedia "playback" keys, but I am surprised that others do not, as it is a surprisingly useful feature![/QUOTE]
Would this type of solution also be applicable to the volume control keys on the front edge.  These work perfectly when using Gnome(I installed ubuntu then added KDE) but seem to have no effect in KDE.

Thanks
Stephen.

---


---
title: "Acer, Hotkeys with Kubuntu. How-to?"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by zba78 on 2006-07-03
Any Acer users using Kubuntu that would like me to write a mini how-to on getting those special keys (volume up, volume down, play, pause etc.) working let me know.

---

### Post by kudanil on 2006-07-03
hi... I'm using ubuntu dapper drake with acer aspire 5502, the hot keys for volume up (FN+up), down (FN+down), and brightness(FN+left/right) work perfectly without need to setup anything. 
But the special keys for launching applications (in WindowsXP for launching email client,etc) don't work at all.

---

### Post by zba78 on 2006-07-03
Yes Ubuntu works straight off the bat but in Kubuntu it has to be configured manually.

---

### Post by rev_1318 on 2006-07-06
one way to do this in kubuntu:
[LIST]
[*]in system Settings, go to Regional & Accessibility -> System Actions
[*]create actions for volume up/down and mute on/off:
[/LIST]
[INDENT][LIST][*]volume up: 
keyboard shortcut: XF86AudioRaiseVolume (=Fn+arrow up)
command: dcop kmix Mixer0 increaseVolume 0
[*]volume down: 
keyboard shortcut: XF86AudioLowerVolume (=Fn+arrow down)
command: dcop kmix Mixer0 decreaseVolume 0
[*]mute on/off
keyboard shortcut: XFAudioMute (=Fn+F8 )
command: dcop kmix Mixer0 toggleMute 0
[/LIST][/INDENT]

HTH,
Paul

---

### Post by obi-nine on 2006-07-13
Hi,

I'm trying to get these keys mapped according to your directions (thanks, BTW) but I haven't done this before.

Can you spell out your directions for inputting these strings in a little more detail?

I've managed to input the dcop calls and test them (and they work) but it doesn't seem to want to accept my keyboard shortcuts.

thanks,

obi9

---

### Post by zba78 on 2006-07-14
In order for the system to translate the fn+action keypresses into a meaningful key you first have to map the special keys using the **xmodmap** command.

I'm not at a linux box now so I'll write how I did it when I'm back at my laptop.

---

### Post by rev_1318 on 2006-07-14
First, make sure that the acerhk-module is loaded:
lsmod | grep acerhk

If it's not, add it to /etc/modules so it will be loaded at system startup.

Next, check if /etc/init.d/hotkey-setup is enabled for your runlevel.

Then, check if the key-definitions are OK:
xmodmap -pk | grep XF86Audio
this should give you something like:
    160         0x1008ff12 (XF86AudioMute)
    174         0x1008ff11 (XF86AudioLowerVolume)
    176         0x1008ff13 (XF86AudioRaiseVolume)

If not, create or edit ~/.Xmodmap and add the correct mappings. For my system (Acer TM800) they are:
keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume

but you may need other keycodes (use eg xev to get the correct keycodes).

Good luck,
Paul

---

### Post by zba78 on 2006-07-14
OK the basic principle is that you need to map the hotkeys to some keys on the keyboard. As most keyboards will have function keys only up till F12 it's safe to map your hotkeys to anything from F13 onwards.

I map all my keys from F20 onwards.

So here's how:

- Open a terminal and run **xev**#
- press a hotkey. you should get some output. When I do volume up (Fn + Up arrow) I get this ```
KeyRelease event, serial 28, synthetic NO, window 0x3200001,
    root 0x76, subw 0x0, time 1845970944, (12,466), root:(1110,488),
    state 0x0, keycode 176 (keysym 0xffd1, F20), same_screen YES,
    XLookupString gives 0 bytes:
```
The bit we are looking for is where it says **keycode**. in my case the volume up hotkey is keycode 176. So we need to map 176 to a key. 

I'll map keycode 176 (volume up) to F20. simply run the command ```
xmodmap -e "keycode 176 = F20"
```

Thats it. F20 is now mapped to kecode 170. Now open Kmix, go to Settings menu, seleck Configue Global Shortcuts and map Increase volume to F20.

Do the same for all other hotkeys (map them to F21, F22, F23 etc.).

I've placed all the commands in a file called keymaps and placed the file in /usr/bin (I made it executable). I then set the file to autorun each time I log into KDE

The keymaps file looks like this```
xmodmap -e "keycode 176 = F20"   #volume up
xmodmap -e "keycode 174 = F21"   #volume down
xmodmap -e "keycode 160 = F22"   #mute volume
xmodmap -e "keycode 178 = F23"   #web browser hotkey
xmodmap -e "keycode 236 = F24"   #email client hotkey
xmodmap -e "keycode 162 = F25"   #Play / Pause
xmodmap -e "keycode 164 = F26"   #Stop
xmodmap -e "keycode 144 = F27"   #Previous Track
xmodmap -e "keycode 153 = F28"   #Next Track
xmodmap -e "keycode 115 = F29"   #Win
```

---

### Post by fugit10 on 2006-07-15
I have an asus z63a and I noticed that most of the hotkeys work but some aren't even recognized at all. I tried the command xev with them but nothing happens. What would I need to do to make ubuntu know that those keys are actually there?

---

### Post by zba78 on 2006-07-17
I could be wrong but if xev does not recognise a key press I don't believe there is anything you can do.

---

### Post by munckfish on 2006-10-20
Hi

I think I may have found the ultimate guide on setting up all the hotkeys (recognised by X and also not) here:

[http://studenti.ing.unipi.it/~s242578/hotkeys_howto.html](http://studenti.ing.unipi.it/~s242578/hotkeys_howto.html)

About to work my way through the instructions.

---

### Post by munckfish on 2006-10-20
Ok I ran through that guide (noted in my last post). I certainly found some keys working that I hadn't noticed before, however, none of the Arcade keys nor the 'e', 'P', 'www', and 'email' buttons. Most of the keys on my small remote control are recognised already (didn't try the big controller).

However, it seems that loading the acerhk module is of no use to Aspire 9504 users. I noticed the following in dmesg:

$ dmesg | grep acer
[17179590.660000] acerhk: Could not find model string, will assume type 200 series

After checking the acerhk source code I discovered this basically sets no extra features at all. :(

---

### Post by grinias on 2006-10-21
I think that the best how-to for hotkeys is found in

[http://ubuntuforums.org/showthread.php?t=27039]("http://ubuntuforums.org/showthread.php?t=27039")

Using this guide I managed to set up the hotkeys for Acer TM 4101 WLmi,
by using this file
[http://www.csd.uoc.gr/~grinias/Ubuntu/acer.hk]("http://www.csd.uoc.gr/~grinias/Ubuntu/acer.hk")
as 
```
/usr/share/hotkey-setup/acer.hk
```

and putting this file
[http://www.csd.uoc.gr/~grinias/Ubuntu/xmodmap.conf]("http://www.csd.uoc.gr/~grinias/Ubuntu/xmodmap.conf")
in 
```
~/.kde/Autostart
```
directory.

That way, the kernel stops to complain about uknown keycodes (because of acer.hk) 
and xserver recognizes the key-mapping using xmodmap.conf. 

Hope it helps...

---


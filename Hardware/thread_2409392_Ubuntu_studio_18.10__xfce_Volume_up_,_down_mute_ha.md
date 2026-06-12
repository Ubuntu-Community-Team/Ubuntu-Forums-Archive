---
title: "Ubuntu studio 18.10  xfce Volume up , down mute hardware keys"
date: 2019-01-01
forum: Hardware
---

### Post by gh0zt362 on 2019-01-01
So I've been toying with the OS trying to get the volume up and down and mute keys to work .  I've researched forum posts dealing with this issue and have seen various instructions and commands none of which I can get to work . 

I tried several manual keyboard short cut entries programming the buttons such as ```
[COLOR=#242729][FONT=Consolas]amixer -D pulse sset Master toggle[/FONT][/COLOR]
```

And the keys are not responding . Could something as simple as pulse audio and alsa running in the tray cause a conflict and restrict volume key operation ?

---

### Post by gh0zt362 on 2019-01-01
also , using xfce .

Also tried to open alsa gui as I read there is supposed to be an option to tick Use keyboard controls . Couldn't find this option and where in pulse audio or alsa mixer

---

### Post by clementc on 2019-01-01
Hi [**gh0zt362**]("https://ubuntuforums.org/member.php?u=1989081"),

Can you please confirm if "Enable keyboard shortcuts for volume control" is enabled when right-clicking the PulseAudio plugin icon in the tray (you might have to install the PulseAudio Plugin first)?

Also, can you please try a shortcut command like: amixer set Master toggle

---

### Post by gh0zt362 on 2019-01-01
I right click and get a "launcher" prompt where when I hit properties it brings me to a whitelist of launchers included which at this time is pulse audio by itself on the list
 [https://i.imgur.com/RZOuDka.png](https://i.imgur.com/RZOuDka.png)

and when I hit edit it just gives me a launch command window and offers to run in terminal and I think startup . 

[https://i.imgur.com/g1g8tbK.png](https://i.imgur.com/g1g8tbK.png)

And as I said when I right click the pusle audio icon on the tray it just gives me your standard launcher menu  as there is no Show in tray proprietary icon that would actually have a pulse audio menu when right clicked . 

And as you can see in the OP I attempted a custom keyboard shortcut from settings manager > keyboard > shortcuts 

And I even just tried your command syntax and nothing happens when I hit the volume mute button . Do I have to reboot for it to take effect ?

---

### Post by gh0zt362 on 2019-01-01
[IMG]https://upload.wikimedia.org/wikipedia/commons/thumb/3/3b/Paris_Tuileries_Garden_Facepalm_statue.jpg/300px-Paris_Tuileries_Garden_Facepalm_statue.jpg[/IMG] I rebooted and all volume keys work lol  Sorry to bother you guys ^.^

---

### Post by wildmanne39 on 2019-01-01
Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

Glad you resolved the issue.

---

### Post by gh0zt362 on 2019-01-01
no worries brother , sorry about that.

---

### Post by clementc on 2019-01-01
Hi [**[COLOR=#000000]gh0zt362[/COLOR]**]("https://ubuntuforums.org/member.php?u=1989081"),

No worries, I am glad to hear that your issue is now resolved.

Sometimes the simplest fixes are the best ;-)

---

### Post by gh0zt362 on 2019-03-26
Mmmmkay , keys are gone again . Restarted  didnt work . Reset pavucontrol service didnt work . Attempted to make custom keyboard shortcut using [COLOR=#242729][FONT=Consolas]pactl -- set-sink-volume 0 +10%   didnt work . killed pavucontrol configs didnt work . 


[/FONT][/COLOR]Funny thing though when the terminal is open when I hit those keys the cursor blinks inverting color scheme  from white to black with white outline indicating the keypress is registering with the system . They just dont do anything . 

All other keys work include multimedia control , brightness , airplane mode .

---

### Post by gh0zt362 on 2019-03-26
OS: Ubuntu Studio 18.10 x86_64 
 Host: HP Laptop 17-by0xxx 
 Kernel: 4.18.0-16-lowlatency 
 
 Shell: bash 4.4.19 
Resolution: 1600x900 
 DE: Xfce 
 WM: Xfwm4 
 WM Theme: NumixBlue 
Theme: NumixBlue [GTK2/3] 
Terminal: xfce4-terminal 

CPU: Intel i5-8250U (8) @ 3.400GHz 
GPU: Intel UHD Graphics 620 
Memory: 1411MiB / 7857MiB

---

### Post by gh0zt362 on 2019-03-26
it is in the plugin .

---

### Post by gh0zt362 on 2019-04-16
Ok . tried fiddling with it some more .  Set the default sink to 3 as per  sink-list  . Result should have been setting analog as default directing all hardware keybindings away from hdmi as default  and still no volume control . 

default.pa ; 
" ### Make some devices default
set-default-sink 3
set-default-source 3 "


When I hit the volume up down and mute button in terminal the cursor colors invert for a moment confirming keybindings but they do not manipulate the volume as they should. 

All other keys function including multimedia playback control .  Just the volume control keybindings appear to not manipulate volume.

---

### Post by gh0zt362 on 2019-04-16
again all brightness , display , backlight volume , multimedia playback keys are primary on this laptop  . Actual F keys you need to fn + fkey to operate . ex; Page refresh  = fn + blacklit (f5 key)    Bcklit toggle on/off : backlit (f5 key) alone

---

### Post by gh0zt362 on 2019-04-16
its like some app perhaps is grabbing the key command before  pulseaudio

---

### Post by gh0zt362 on 2019-04-16
Keyboard layout pic . Again all toggles are primary and F functions secondary on this keyboard . All toggles work except volume control  .

---

### Post by gh0zt362 on 2019-04-16
Audio Device sink 3 : Intel Corporation Sunrise Point-LP HD Audio (rev 21)

---


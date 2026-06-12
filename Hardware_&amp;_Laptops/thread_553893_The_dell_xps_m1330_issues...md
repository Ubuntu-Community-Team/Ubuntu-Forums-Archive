---
title: "The dell xps m1330 issues.."
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by Secher on 2007-09-18
I have the DELL XPS m1330 - 1.8ghz, with the intel graphics.

Ok after hours and hours of googling the subject i have concluded that it is basicly impossible to install 7.04 on this laptop if you have the intel graphic x3100.. And by the way not 6.06 either..

I accepted that and tried the gutsy version of ubuntu.. (7.10) It worked reasonably well for a while, actually, pretty much everything ended up working except sound. But today i saw that there was a major update package ready.. (about 150 updates i think it was) So i hurried to download and install the updates. But then hell started.. My touch pad can now only move the curser around, i cant "click" on the pad itself anymore. I cant use the scroll function by touching it on the right side anymore. 
The sound still doesnt work. But the worst thing is that my terminal is messed up. If i open a new terminal, all i get is a very small empty window, with a curser about 2x2 pixels flashing about a quarter in on what i think is the first line.

Can anyone help.. Cant really do much without a command line.. 

Or maybe someone even has a better way of getting ubuntu on a m1330?

-Secher

---

### Post by MaLk0 on 2007-09-18
Same problem here!

Have Dell XPS m1330 with Geforce GFX card. After I installed the update today my terminal is messed up and click on mousepad doesnt work. Also still no sound.

EDIT: Just saw this can be fixed by opening terminal and writing: $ gconftool --type float --set /desktop/gnome/font_rendering/dpi 96
          Even though you cant see what you are writing it should work :D

---

### Post by Secher on 2007-09-18
> **MaLk0 said:**
> Same problem here!

Have Dell XPS m1330 with Geforce GFX card. After I installed the update today my terminal is messed up and click on mousepad doesnt work. Also still no sound.

EDIT: Just saw this can be fixed by opening terminal and writing: $ gconftool --type float --set /desktop/gnome/font_rendering/dpi 96
          Even though you cant see what you are writing it should work :D

Ye i just got that fixed too..

But my mouse pad is still messed up..

-Secher

---

### Post by MaLk0 on 2007-09-18
Also have sound if I add "options snd-hda-intel model=3stack" to /etc/modprobe.d/alsa-base - Yay!

Problem is mousepad and also I can only lower brightness with hotkey - I cant make it brighter :(

---

### Post by crisby on 2007-09-21
I had the mousepad problem too, but after an update I could find a "Touchpad"-tab in the mouse dialog (systemsettings). There you should be able to set "tab on click" and scrolling (vertical, horizontal).

Brightness problem is the same here. It worked until one of the lasts updates. Until this is fixed, you can make it brighter by opening the energyproperties.

Greetings,
crisby

--
PS: I apologize for my English.

---

### Post by paxmaniac on 2007-09-25
> **crisby said:**
> 
Brightness problem is the same here. It worked until one of the lasts updates. Until this is fixed, you can make it brighter by opening the energyproperties.

Thanks for the tip.  Mine also worked until an update a couple of days ago.

Has anyone figured out how to link the volume and mute touch buttons to the main system volume (e.g PCM)?  By default it seems to move the 'digital recording' volume, which isn't a lot of use.

I have also noticed that while my sound works, I cannot get any system sounds in Gutsy working.  I can test the sounds in the sound preferences window, but they don't work in the window manager.

Anyone having any luck with suspend?

---

### Post by crisby on 2007-09-26
Brightness: There is also a panel applet available (which is at least a little bit more comfortable that to use the energy properties every time)

Media Keys: hmm... that's strange. For me it works perfectly out-of-the box. 

System-Sounds: Oh... you are right. I didn't miss them, so I actually didn't even notice that they don't work in the windows manager, but in the end I have the same problem here.

Suspend: No, black screen after trying to wake up again.

---

### Post by GeoMX on 2007-09-30
I've just downloaded the beta version, the live CD seems to work (Ubuntu starts), I'm using gparted right now. The problem I noticed with the brigthness controls, can't increase brightness but lowering it works fine (just as you mentioned).

---

### Post by crisby on 2007-10-02
\\:D/ The brightness-problem got fixed with yesterday's update.

---

### Post by paxmaniac on 2007-10-10
The latest round of updates (including kernel 2.6.22-14) seems to have fixed the suspend problem.  System sounds are also now working properly.  Kudos to the dev teams!  I now have a completely functional computer devoid of Windows.  Hooray!

---

### Post by mani99 on 2007-10-11
As I use KDE I don't know how gnome handles special keys. When I installed Kubuntu 7.10 beta all the media keys worked right away. I wanted to be able to use all of the Fn-keys, and this is how I did it:

In KDE I can put their keycodes and keysyms (desired function) for them in ~/.Xmodmap, which loads on kde login, using this syntax:

```

keycode ### = Keysym

```
Example:
```

keycode 214 = F13

```


I found it easiest to just map the keys I wanted to use/change to F-keys; F13-F35 are unused, and I use them as shortcut keys in the various KDE applications. You can also use modifiers (ctrl/alt/shift/win) with F-keys, so you could have multiple actions for the same button. For example: I use the Mediadirect-key to show/hide amarok and show/hide amarokFS when using the alt-key

It's also possible to use them as browser (back/forward/stop/reload/home/bookmarks etc), audio (volume/play/pause/ff/rw etc) shortcuts, and a lot of other things.

The complete list of possible Keysyms can be found in /usr/share/X11/XkeysymDB. This file contains a lot of useless commands, so search for XF86* to see the relevant keysyms (144!), or copy them to a new document for reference using this command:
```

cat /usr/share/X11/XKeysymDB | grep XF86 > ~/Keysyms

```

Here are the keycodes for all Fn/multimedia keys on the m1330:

Fn-keys:
165 Sleep (Fn+F1)
241 Battery (Fn+F3)
214 CRT/LCD (Fn+F8 )
212 Brightness up (Fn+Up)
101 Brightness down (Fn+Down)


Buttons above keyboard:
237 mediadirect
222 power button (yes, you can use it for anything :))

144 Previous
164 Stop
162 Play/Pause
153 Next
160 Mute

174 Volume up
176 Volume down

Xmodmap can be called with a custom file as an argument, so it's also VERY useful for temporarily remapping the keys found on the remote bundled with the m1330. This could be useful for more advanced control of media players (subtitles, aspect ratio, dvd menus etc), presentations or just about anything. It's not practical however, to remap some of these keys in the .Xmodmap file, as they are required for normal usage.

The keysyms for the volume and media control keys are the same as above (except for rewind/fast forward, which are not on the keyboard), here is the rest of them:

```

\   1      |
 \  2  3   |
  \  4 5 6 |
   | 7 8   |
   | 9   0 |
   |       |

```

Number:, Keycode, Keysym, (Description)
1: 99 Prior (PageUp)
2: 105 Next (PageDown)
3: 98 Up
4: 100 Left
5: 108 KP_Enter (Keypad Enter)
6: 102 Right
7: 22 BackSpace
8: 104 Down
9: (Ctrl+Shift+B)
0: (Ctrl+Shift+F)

If you have any questions regarding this, feel free to ask :)
/Máni

---


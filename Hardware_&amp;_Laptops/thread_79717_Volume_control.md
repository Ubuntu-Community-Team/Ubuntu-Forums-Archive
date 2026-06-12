---
title: "Volume control"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by Coutsos on 2005-10-20
On my laptop, if I hold down the Fn key and press up or down I can turn the volume up or down respectively (in windows, at least). It appears to work just fine in Ubuntu as well, except that it controls the Master volume which does nothing as opposed to the PCM volume. Any way I can switch this up?

The laptop is an Acer Aspire 3003WLCi if that matters at all :p

---

### Post by rsankuratri on 2005-10-21
Roght click on the sound icon in the system tray and from the context menu choose Preference.  From the window that opens choose PCM and click OK

---

### Post by russelld on 2005-10-23
I have noticed this with my Acer Inspire 3002WLC.
Even after doing as suggested, the Fn + up/down button still doesn't change the volume.

so far what I have found:
The keyboard shortcuts for sound and media doesn't do anything to volume or play media.  This occurs in both asla and OSS drivers. 
While using the keyboard volume control a graphic on screen will be displayed showing volume or mute been changed, however volume remains the same.
The media and sound key combinations are:
mute: Fn + F8
vol up: Fn + up arrow
vol down: Fn + down arrow
Media keyboard combinations:
Play/Pause: Fn + home
stop: Fn + PgUp
previous: Fn+ PgDn
next: Fn + End
This remained the same after checking "keyboard preferences" via System -> Preferences -> Keyboard Shortcuts.
Using xmms volume plugin and alsa, the keyboard volume control changes "Master" which has no effect on volume.  While in alsa, when playing media with xmms, the actual overall volume control is controlled via "headphone", not "master".
Using OSS, the actual overall volume contol is via "pcm2", and not "master". Both OSS and ALSA work, though its not clear on how to map the keyboard to the volume controls.

I also changed to several different types of keyboards, and still the same result.

BTW The help file which comes with the keyboard shortcuts does not reflect the actual application.
The help file states that the keyboard shortcuts ap has a choice of "text editing" and "desktop shortcuts".  These options are not available when the keyboard shortcuts ap is started.  

TIA

---

### Post by jobezone on 2005-12-14
Hi, I managed to fix this (was having the same problem as you) by following a tip on installing **xbindkeys** from an HOWTO in this forum [http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560).
But, to be more exact, this is what I did:

1 - Deleted gnome's keybindings for the mute, increase volume and decrease volume. Did this by clicking in the Shortcut column of the gnome-keybinding-properties window respective to these three actions, then pressing backspace.

2 - Installed xbindkeys and its gui configuration utility:
```
sudo apt-get install xbindkeys xbindkeys-config

```
3 - Executed this:
```
xbindkeys --defaults > /home/eduardo/.xbindkeysrc
```
Don't know if this is strictly necessary.

4 - Ran xbindkeys and xbindkeys-config
```
xbindkeys
xbindkeys-config
```

5 - In the configuration window of xbindkeys-config delete the pre-existent keybindings (unless you want to keep any, like the Ctrl+Shift+q , which looks handy, since it shows the configured keybindings at any time) .

6 - Press the button "New" to create a new keybinding, and on the right, you can name it, choose what key to use (use the Get Key button then press the combination of keys you want, and it will capture it for you), and choose the command to run. 

These are the ones I created:

Name: Mute                                        
Action: amixer sset PCM toggle

Name: Increase volume
Action: amixer sset PCM 1+ unmute

Name: Decrease volume
Action: amixer sset PCM 1- unmute

7 - File -> Save to default File

8 - You can already test it!

9 - Add "xbindkeys" to Gnome-session Startup applications so it always runs when you enter Gnome.

---

### Post by nandasunu on 2006-01-02
jobezone: thanks for the walkthrough, this is very helpful to me.

---

### Post by Coutsos on 2006-01-27
Sorry, old topic I know, but I'm not having any luck with this method. Using xbindkeys-config, Fn+(function key) doesn't register as an input. Fn+(regular key) works except that it doesn't register the Fn key either. Anybody happen to know how I can figure out what the keycode is?

---

### Post by Brian McConnell on 2006-02-08
[QUOTE=russelld]
The keyboard shortcuts for sound and media doesn't do anything to volume or play media.  This occurs in both asla and OSS drivers. 
While using the keyboard volume control a graphic on screen will be displayed showing volume or mute been changed, however volume remains the same.[/QUOTE]
I have this problem as well. How do I change it so as to affect the other soundcard (the one I use).

---

### Post by russelld on 2006-02-12
Fantastic!

It just worked!:D 

If not running a window manager other than gnome ie windowmaker, enlightenment, blackbox and you want to start xbindkeys, place the command in the ~/.Xsession file:

```

#make sure keymapping is on; not required with bbkeys
xbindkeys &

#call window manager
exec /usr/bin/wmaker
```

---

### Post by sup on 2006-02-12
I have got similar problem - multimedia keys would work with gnome-keybinding-properties only when manually set up and would stop working after reboot. So I use xkeybindings to overcome that and commands above to un/mute sound and raise and lower volume. It works but with no gui as if it were assigned throu gnome-keybinding-properties. I kind of liked that, any ideas about commands that are called by gnome-keybinding-properties so that I could use those? Master/PCM etc is not an issue here.

---

### Post by russelld on 2006-02-13
well after yesturday's success, I have just reprogramed the fn + home, etc, to control xmms and volume.

use man xmms to get command for xmms to play-pause, stop, go forward, go back,   eg to play/pause xmms, its xmms -t
Do exaclty as above to locate appropriate keys to control sound, then insert xmms command.  Apply, save and quit.  Enjoy fingertip control! \\:D/ 

Wahlah! its tooo easy!  Now all the buttons work! 

ohh this is soo cool, many thankyous.......

---

### Post by ktiedt on 2006-02-26
Very handy thread! I just thought it might be handy to offer a bit more insight into this :)

The problem with ubuntu and media keyboards (or laptop volume controls) is that it only ties the control to the MASTER volume which as ubuntu sees it, is your laptops internal speakers.

When you are using earphones or line out, thats a seperately controllable volume level (like CD audio versus MIDI in windows). At home my laptop is plugged into my stereo 24/7... so for me to fix this I had to tie xbindkeys into both controls... really quite simple.

instead of just using
"amixer sset PCM toggle" for mute control I did this
"amixer sset Master toggle;amixer sset Headphone toggle" notice I dont use PCM, that is because PCM is a volume control much like MIDI or CDaudio was for windows. It doesnt control the output level, but the source of the sound (Rythmbox or XMMS for example)

The same can be done for volume up/down just add the semicolon and string commands together ;)

Hope this helps more people!

---

### Post by snowboard975 on 2006-03-30
xbindkeys-config accept "Fn+right arrow" keys and "amixer sset Master 1+" command well. But after saving & exiting it, the key doesn't work. I tried to input obvious keys like Alt+3 to do the same job. But even it didn't work. I think xbindkeys doesn't work in my system at all. Why is that??

---

### Post by pinolero1984 on 2006-07-06
Very helpful thread!! Keys work great aside from the fact that I cant get them to automatically run at startup. I am using Kubuntu 5.10. Breezy. I saved the xbindkeys line as rc.local in /etc/init.d but when I run "sysv-rc-conf -p", rc.local does not show up. I went to the folder and the icon on rc.local is not a script icon, just a regular text file icon, is that the problem? If so, how do I make it a script?

---

### Post by pinolero1984 on 2006-07-06
Nevermind, I got the rc.local file to show up on the sysv-rc-conf -p by making it a script, but it still doesnt work automatically when I boot up. Any suggestions?

---

### Post by Aarohi on 2006-07-20
Thanks a lot guys. Its worked quite successfully. Very useful thread indeed.
I set up the rc.local file and its configuration as was instructed but it didn't seem to work for some reason.. it doesn't start automatically at startup. Any ideas why?

I added the command to gnome session startup though.

---

### Post by russelld on 2006-07-23
The rc.local method doesn't work for me either! ](*,) 
xbindkeys seems to only work with an running X server so starting it from a rc.local file will not work

Sorry for leading you astray.

The better way is to load into to gnome session like Aarohi said.

If not using gnome then place it in the ~/.Xsession file as
(assuming window manager is windowmaker) 
```

#make sure keymapping is on
xbindkeys &

#start window manager
exec /usr/bin/wmaker

```

Then at login screen click "sessions" and select "default"
and xbindkeys will start with the window manager executed in .Xsessions

---

### Post by keinhaar on 2006-12-30
Hi,

on my system, kubuntu 6.10, there is no master volume mixer. the keyboard did always change the volume of the headphone, but i wanted it to control the laptop speakers (amilo 1538).
after reading lots of threads with no success, i found a simple solution for KDE. maybe this could be done in gnome as well.

- open the kde control center by calling kcontrol from a terminal.
- open "regional & accessebility" -> "Input Actions"
- create a new group. i called my one "martin" :-)
- create a new action.
- change the action type to "keyboard shortcut -> command/url"
- on the "keyboard shortcut" tab define the shortcut by simply using your keyboards volume key.
- on the "command/url" tab enter the command needed to change the volume. on my system i needed this one to increase the volume: "amixer set Front 1+" and this to decrease the volume: "amixer set Front 1-" (thanks to some forum users for this information).

be aware, that this is case sensitive (Front NOT front).
feel free to control the channel you want, by simply replacing "Front" with your channels name.
after applying input actions to increase and decrease the volume, there is no longer a nice window popping up, that shows the volume increasing an decreasing, but if you have opened "kmix", you will see, that your selected channel is controlled by the volume keys.

hopefully this is useful to someone.
maddin

---

### Post by BFris on 2008-01-19
> **keinhaar said:**
> Hi,
- open the kde control center by calling kcontrol from a terminal.
- open "regional & accessebility" -> "Input Actions"
- create a new group. i called my one "martin" :-)
- create a new action.
- change the action type to "keyboard shortcut -> command/url"
- on the "keyboard shortcut" tab define the shortcut by simply using your keyboards volume key.
- on the "command/url" tab enter the command needed to change the volume. on my system i needed this one to increase the volume: "amixer set Front 1+" and this to decrease the volume: "amixer set Front 1-" (thanks to some forum users for this information).

maddin

keinhaar, this rocks. Works very nicely in Kubuntu 7.1. Two things:
1.  on the keyboard shortcut tab, you have to press the "None" button first. This is very counterintuitive. Then a small window pops up. You can then press any key on the keyboard and the window will recognize it.
2. to mute, use "amixer set Front toggle"  the toggle tells amixer to turn sound on or off.

I love Linux.

---


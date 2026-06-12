---
title: "multimedia keys not working"
date: 2011-05-24
forum: Hardware
---

### Post by NERDMAN! on 2011-05-24
i seem to be having alot of issues dont i? XD anyway the latest issue with this laptop is the capacitive touch media controls, volume works just fine but the media player controls wont work at all, i tried enabling the gnome mmkeys plugin for gmusicbrowser but i got this in return: Error :
no signal with name 'MediaPlayerKeyPressed' is exported in object '/org/gnome/SettingsDaemon/MediaKeys'

i did some checking and such a directory does not exist, i'm guessing thats where the key bindings are stored but i have no idea how to fix this issue. i'm running xubuntu 11.04 natty on a dell inspiron 1525 notebook. 
my first guess would be to mock up a file with the key bindings but i have no idea when it comes to finding out the required information or coding up a suitable file. can anyone help me out here?

---

### Post by Toz on 2011-05-24
Try going to the Keyboard applet in the settings manager and changing your keyboard layout to one of the Dell-specific layouts. Perhaps the Dell USB Multimedia keyboard?

---

### Post by NERDMAN! on 2011-05-24
ive just attempted those layout options, and i'm afraid they didnt have any effect on the media controls.
perhaps this screenshot may be of use?
 [IMG]http://i290.photobucket.com/albums/ll256/technomancer21/gmusicbrowserpluginfail.png[/IMG]

---

### Post by Toz on 2011-05-24
Sorry, but I won't be able to help with that error message - I get it here as well. However, gmusicbrowser has a fifo channel that you can use to control it. Basically, you can send commands to the fifo file and gmusicbrowser will process them. To test, from a command line, type in the following while a song is playing in gmusicbrowser:```
echo PlayPause > ~/.config/gmusicbrowser/gmusicbrowser.fifo
```Enter it in again to make the song play again. The list of commands can be found in the man file. Using the built-in key shortcuts functionality, we can assign these codes to execute when you press a key on your keyboard.

It's easy to setup and you should be able to assign your multimedia keys to control it. Here's how:

First, create a file called gm in your home directory with these contents:```
#!/bin/bash

case $1 in
	1) echo PlayPause > ~/.config/gmusicbrowser/gmusicbrowser.fifo
	;;
	2) echo PrevSong > ~/.config/gmusicbrowser/gmusicbrowser.fifo
	;;
	3) echo NextSong > ~/.config/gmusicbrowser/gmusicbrowser.fifo
	;;
	4) echo DecVolume > ~/.config/gmusicbrowser/gmusicbrowser.fifo
	;;
	5) echo IncVolume > ~/.config/gmusicbrowser/gmusicbrowser.fifo
	;;
	*)
	;;
esac
```


Second, Make the file executable:```
chmod +x gm
```

Third, goto Settings Manager -> Keyboard -> Application Shortcuts tab and add a new shortcut. For the command, set it to: **~/gm 1** and when it asks for the shortcut, press the Play multimedia key. Do the same for the others so that:```
~/gm 1 -> Play/pause multimedia key
~/gm 2 -> Previous song multimedia key
~/gm 3 -> Next song multimedia key
~/gm 4 -> Volume decrease multimedia key
~/gm 5 -> Volume increase multimedia key
```

Now, as gmusicbrowser is playing, press the multimedia key to send the proper code to the fifo control file.

---

### Post by NERDMAN! on 2011-05-25
i followed your instructions, but for some reason all the keys seem to do is refresh the screen if that makes any sense, media is not being controlled by the keys.
which doesnt make any sense to me as the fifo commands when typed in terminal work perfectly.

---

### Post by NERDMAN! on 2011-05-25
well, i feel somewhat stupid now, there as a shortcut key system built into gmusicbrowser the entire time, i added the keys to it and it works while gmusicbrowser is displayed as the active window, but as soon as i minimise it they cease to work. i'm thinking perhaps the fifo method is the way to go as it did work when i typed it into terminal.

---

### Post by Toz on 2011-05-25
> **NERDMAN! said:**
> i followed your instructions, but for some reason all the keys seem to do is refresh the screen if that makes any sense, media is not being controlled by the keys.
which doesnt make any sense to me as the fifo commands when typed in terminal work perfectly.

That's interesting. What happens when you enter ```
~/gm 1
```at the command prompt when music is playing? Does the music pause?

Can you also post back the contents of your ~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml file.

---

### Post by Toz on 2011-05-25
> **NERDMAN! said:**
> well, i feel somewhat stupid now, there as a shortcut key system built into gmusicbrowser the entire time, i added the keys to it and it works while gmusicbrowser is displayed as the active window, but as soon as i minimise it they cease to work. i'm thinking perhaps the fifo method is the way to go as it did work when i typed it into terminal.

The fifo method is what I use and it works perfectly for me. However, I don't have multimedia keys, so I've mapped to other shortcuts (pause = Ctrl+P, Next = Ctrl+., etc). And the keys work regardless whether gmusicbrowser is in focus or minimized.

---

### Post by NERDMAN! on 2011-05-25
in terminal ~/gm 1 runs perfectly, infact all of the multimedia commands work. just not when i press the keys
i saved a txt copy of the xml file to upload, i wasnt sure if it would let me upload an xml directly.

---

### Post by Toz on 2011-05-26
Can you try this? Post back the results of:

```
xmodmap -pke | grep XF86AudioPlay
```

Then, in the terminal window, run:```
xev
```
A box will pop-up. Press the Play key and in the terminal window a bunch of text will display. Post back the section starting with "Keypress event".

Lets see if your key codes match up.

---

### Post by NERDMAN! on 2011-05-26
```
rawr@corruption:~$ xmodmap -pke | grep XF86AudioPlay
keycode 172 = XF86AudioPlay XF86AudioPause XF86AudioPlay XF86AudioPause
keycode 208 = XF86AudioPlay NoSymbol XF86AudioPlay
keycode 215 = XF86AudioPlay NoSymbol XF86AudioPlay
 
``````
KeyPress event, serial 31, synthetic NO, window 0x1800001,
    root 0xad, subw 0x0, time 19704111, (-206,-318), root:(345,17),
    state 0x0, keycode 172 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x1800001,
    root 0xad, subw 0x0, time 19704415, (-206,-318), root:(345,17),
    state 0x0, keycode 172 (keysym 0x1008ff14, XF86AudioPlay), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

### Post by Toz on 2011-05-26
Hmph. This should work. Can you try to assign **~/gm 1** to another keystroke combination, like Ctrl+p? Lets see if that works.

EDIT: Do any of your other shortcut keys work (ie. does Ctrl+Esc bring up the menu)? Is xfce4-settings-helper running```
ps -ef | grep xfce4-settings-helper | grep -v grep
```

---

### Post by sdlion on 2011-06-14
I had the same problems ( the gm script didn't work ), but recently I'd found two details.

When I was trying to put this settings using the Configuration Editor, it told me "/ must be the first character" when I was entering the command string.
This could be the reason why the xfce key-shortcut manager would hang up.
So, instead of 
~/gm 1

the command string changed to
/home/MyUsername/gm 1

(No more hangups)

Also, the reason why the command didn't work at all, was most likely the permissions.
In a terminal:

cd ~/ 
(To enter your personal folder where the gm file is)

chmod 777 gm
(to change the gm's permissions, now is available to every user (or program) )

Know in the same terminal you can type
ls -l
and look how the permission were changed (10 first characters) to
-rwxrwxrwx
Owner Permissions | Group Permissions | Others Permissions
being rwx = Read-Write-Execute

I hope this also would work for you.

---

### Post by IrrationlArtist on 2011-10-09
Hey everyone, I know this is a pretty old thread but I found a solution, thought I might share for future people who have this problem. This is the first thing I clicked on when trying to research a solution, anyways, so maybe some people will see it.

Open up the main menu and go to Settings > Settings Manager.

Once in the Settings menu, click the "Startup and Session" icon.
Go over to the "Advanced" tab and check the box that says "Launch GNOME services on Startup". Log out, log back in, and then enable the GNOME mmkey plugin in gmusicbrowser.

This worked for the multimedia keys built into my laptop's keyboard, so I'm guessing it will work for other keyboards?

---


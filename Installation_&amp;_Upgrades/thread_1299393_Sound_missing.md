---
title: "Sound missing"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by Gordonisnz on 2009-10-23
Hi,

I'm on 8.10 now (Ive got a seperate thread about upgrading to 9.xx )

Basically, I have SYSTEM >> PREFERENCES >> SOUND

& do tests - the tests work fine, (no errors) - But no sound.

Question :-

:- How do I find out (without opening up the box) - if I have a sound card installed

:- Is there a way to test / configure the sound card (maybe its on the board, but disconnected ?)


Ps I don't even get system siounds (beeps)

i've also got sound volume to 68%


Ps - Is there a 'MUTE' setting ?  It doesn't look as if I have it set on mute.

---

### Post by OrangeVixen on 2009-10-24
Check the mixer:

Applications -> Sound & Video -> Volume Control

If you don't see Volume Control, go to System -> Preferences -> Main Menu and look to see if Volume Control is enabled in the Applications -> Sound & Video menu.

Once you are in Volume Control, check the Preferences, and make sure ALL the playback channels are not muted and are at a high enough volume.

---

### Post by Gordonisnz on 2009-10-24
Thanks

I've activated Volume control - but still no sound...


I guess I need to re-boot... (doing that now).....


all options are active - not muted

---

### Post by oboedad55 on 2009-10-24
What sounds are not playing, just the system sounds? BTW, those need to be enabled in your sound settings, by default they're off. I'm curious what it is you're trying to play.

---

### Post by Gordonisnz on 2009-10-24
any / all sounds are not playing....

Right now, 

I'm testing on Youtube,  and SYSTEM >> PREFERENCES >> SOUND >> TEST

no sound...


Ive checked
- NOT going to 'headphones' (I have none)
- Not muted (on the screens ive seen here)

- I didn't have 'vulume control' option, but ive enamed that (& rebooted) - still no sound...

Is there a way to detect I have a sound card installed ?

---

### Post by Gordonisnz on 2009-10-24
I WAS on 8.04  Ununtu  earlier today, Now on 8.10

---

### Post by motsteve on 2009-10-24
The first thing I always do is to go to a command line and enter:

"alsamixer"

This brings up a control panel in the x window where you can see what the settings are for mixer.  There's a man page for alsamixer, but basically you can move left and right with your arrow keys and if the sound is muted you'll see a "mm" and not a "00".  Use the "M" key on the keyboard to toggle the setting on and off.  Volume settings can be changed with up and down arrows.  Use "esc" to exit alsamixer.

I hope it is this simple because sound can be a real pain fixing.

---

### Post by Gordonisnz on 2009-10-24
Card: PulseAudio                                                             &#9474;
&#9474; Chip: PulseAudio                                                             &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master      


It has volume on high (with "master"...)

above the word "master" it has  100<>100

and above that is "00"


THOUGH I can't press left / right - Nothing hapens, it always remains as 'master'....


I did try "M" & it did mute it (changed it back to 00 )


more testing.....

---

### Post by Gordonisnz on 2009-10-24
NEW DEVELOPMENT


How do I test if ive got a 32 bit or 64 bit system...  ??  (I found it a few days ago, But can't remember...)

my Linux box is running 64 bit (from a few days ago)

BUT I found this :-

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

Its running WIN32   

i'm not 32 bit, or running windows... on that box...

will that matter ?


Is there a way I can see if i have anything OTHER than "pulseAudio" on the Box - & how to select / use it for sound ??

---

### Post by Gordonisnz on 2009-10-24
Ive found out my audio device


[COLOR=#CC0000]** **[/COLOR]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

---


---
title: "Audio problems"
date: 2005-01-14
forum: Hardware &amp; Laptops
---

### Post by marikka on 2005-01-14
When I istalled Ubuntu, the sound worked well. 

Then, I installed tvtime to use my tv-card.
Now my tv-card works just fine, I get the sound and all, but all the Gnome sounds have died.

Starting esd with "esd -d /dev/dsp1" works,  so I presume the sound device of my tv-card is somehow set up at /dev/dsp, and my soundcard at /dev/dsp1

Also, I can get XMMS and MPlayer to work if I tell them to use /dev/dsp1

Now the question is: How can I set my soundcard at /dev/dsp and my tv-card at /dev/dsp1?

Thanks in advance!

---

### Post by tom on 2005-01-14
Add two lines to your

/etc/modules

```
*Driver of your Soundcard*
bt878 (Driver of your TV-card)
```

Mine looks like:

```
sd_mod
psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp
[COLOR=DarkOrange]ES1938
bt878[/COLOR]
```


You may test your cards before:
```
koni@ubuntu:~ $ cat /proc/asound/cards

```

... stems from German ubuntu-forum, where I had nearly the same problem today as well

---

### Post by iverylm on 2005-01-15
The below worked for me for DVD playback

From the KDE desktop......
Open terminal or from command line run:  **alsamixer** 
Check the "master" control, last column on left.  If its colorless...use left/right arrows to hightlight menu at the bottom of the status column, then use up arrow to raise the volume range. Once completed, use esc to close mixer.
Then go the multimedia section...open   **kmixer** ....look for your sound card in lower right, if the radio button is bright green, click to enable. You can make other  adjustments here.

As far as "muting" the external amp" from the  gnome....I did not do it.

hOPE THIS HELPS!!

IVERY

---

### Post by marikka on 2005-01-16
[QUOTE=iverylm]
Open terminal or from command line run:  **alsamixer** 
Check the "master" control, last column on left.  If its colorless...use left/right arrows to hightlight menu at the bottom of the status column, then use up arrow to raise the volume range. Once completed, use esc to close mixer.[/QUOTE]

If I start 'alsamixer', it says:
Card: Brooktree Bt878 
Chip: Bt87x
Item: TV Tuner

If I start 'alsamixer -c 1', it says:
Card:  VIA 823x rev60
Chip: Realtek ALC655 rev 0
Item: Master

Now, clearly my problem is that the TV-tuner gets set up first (at /dev/dsp ) and only then my sound-chip (at /dev/dsp1 )

Now how to reverse this is my problem. I don't see why I should add anything to my /etc/modules, since my both devices work already, they just get set up in the wrong order.

---

### Post by tom on 2005-01-16
> Now how to reverse this is my problem. I don't see why I should add anything to my /etc/modules, since my both devices work already, they just get set up in the wrong order.

 :confused: In doing this you get them in the right order I suppose. It worked for me like this at least.

---

### Post by marikka on 2005-01-17
Well.. I tried it, but it didn't work. Too bad. :(

---

### Post by marikka on 2005-01-19
Alright. I think I solved this. Thanks for the help!

What needed to be done was to add these lines to /etc/modules:

snd_via82xx
snd_ac97_codec

It didn't work before, since I didn't know where to look for the module names.
Now I know I should have looked them up from lsmod

---


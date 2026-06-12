---
title: "Tv-out problem: ati Mobility U1"
date: 2005-05-03
forum: Hardware &amp; Laptops
---

### Post by XanonimX on 2005-05-03
I want to use the TV-out of my laptop (hp compaq nx9005)

I have a ATI Radeon Mobility U1

I've been reading posts to intall the fglr drivers, in orther to use the ati panel to use the tv-out, but as Mobility U1 is not accepted by fglr this solution doesn't work.

How can I use it instead? there is another software? I have to recognize some hardware?

Thanks

---

### Post by Xerampelinae on 2005-05-03
Perhaps this will work

```

sudo apt-get install atitvout
sudo atitvout auto

```

---

### Post by enderson on 2005-11-26
atitvout is not on any of my repositories, could you tell what's yout config ?


Edit: Ok, I found it.

---

### Post by meth on 2006-01-18
I have a hp compaq nx9010 with ati radeon mobility and i installed atitvout but i get this error:

> sudo atitvout auto
Failed to detect adapter type.
Use either -f or -r for forcing either Rage Mobility/Rage 3D Pro LT or Radeon/Rage 128 mode.
> sudo atitvout -f auto
Forcing Rage Mobility/Rage 3D Pro LT mode

But i dont have any image in the TV, some help please

---

### Post by maxdevis on 2006-02-09
did you find a solution?

---

### Post by jomar1i1 on 2008-04-29
This does work on the compaq nx9010

you must first install atitvout in terminal:

    [COLOR="Blue"] # sudo apt-get install atitvout[/COLOR]

then modify the xorg.conf to recognise all video out ports (please perform backups when modifying files!):

     [COLOR="Blue"]# sudo gedit /etc/X11/xorg.conf
[/COLOR]
Under Section "Device", add this option entry:

     [COLOR="Blue"]Option    "BIOSHotkeys"      "true"[/COLOR]

Save xorg.conf.

Now powerdown laptop and plug in S-video cable to S-video port plug into tv, and turn on television.
[COLOR="Red"]
***Note, television must be on and cables pluged into both TV and Laptop, in order for atitvout to recognize it[/COLOR]!

Boot up ubuntu normally and in terminal run atitvout:

      [COLOR="Blue"]# sudo atitvout -f detect
[/COLOR]
this detects the available monitors/tv/LCDs etc, you should get something like this:

     [COLOR="Blue"] Forcing Rage Mobility/Rage 3D Pro LT mode
      LCD is attached.
      TV is attached via S-Video.[/COLOR]

As the maker of atitvout says, most video card are not automatically detected, if not, then force to recognize the card. I find using -f instead of -r more stable.

to switch to television, use this command:

     [COLOR="Blue"] # sudo atitvout -f t
[/COLOR]

to switch back to LCD, use this command:

      [COLOR="Blue"]# sudo atitvout -f l[/COLOR]

---


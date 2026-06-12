---
title: "Synaptics Tap Zone size"
date: 2011-08-14
forum: Hardware
---

### Post by adk on 2011-08-14
Is there any way to adjust tap zone corner size in Synaptics touchpad, just like in Windows driver? My default tap zones are too small for me and difficult to use.

---

### Post by Enterpart on 2011-10-14
To chnage the area of Tap zones have a look at this

[ATTACH]204253[/ATTACH]

taken from synaptics manpage

```
man synaptics
```

as you can see we need to change the parameters of LeftEdge RightEdge TopEdge and BottomEdge.

These can be changed with the commands

```
synclient LeftEdge=2196
```

and you need to change all edges i.e. synclient RightEdge=....

You can guess the numbers or use this command

```
synclient -m 100
```

but first you would need to enable SHMConfig

do this by the following method

Enter this command, it will give you access to change files on nautilus

```
sudo nautilus
```

Enter Password -> go to "File System" -> "USR" -> "share" -> "X11" -> "xorg.conf.d" -> "50-synaptics.conf"

now you should see this

Section "InputClass"
        [INDENT]Identifier "touchpad catchall"
        Driver "synaptics"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"[/INDENT]
EndSection

you want to add **Option "SHMConfig"  "true"** so it looks like this 

[ATTACH]204254[/ATTACH]

save and exit

now enter "synclient -m 100" in terminal 

```
synclient -m 100
```

and you should see this

    time     x    y   z f  w  l r u d m     multi  gl gm gr gdx gdy
   0.000     1 5855   0 0  0  0 0 0 0 0  00000000   0  0  0   0   0

were interested in the x and y numbers
touch your finger on the touchpad were you want the corner of the area 3 you want (see first picture were the TopEdge meets the RightEdge)
you should see the terminal output numbers with a big number around 5000 on x and a number around 2500 in y
the x cordinate is the RightEdge and the y is the TopEdge
record on a piece of paper
then again tap the touchpad at the bottom left at were you want The Leftedge meet the BottomEdge (see again first picture)

the numbers I get are x=2254 y=3654 (each touchpad has different dimensions and you might want a bigger area for the taps)
now here the x=LeftEdge and y=BottomEdge
again record these down

thats all we need so in the terminal you can use this to change the location of the Edges

```
synclient RightEdge=4905
```
```
synclient TopEdge=2431
```
```
synclient LeftEdge=2196
```
```
synclient BottomEdge=3689
```

(these are my own that Ive calibrated with my touchpad and preference so enter the ones you jotted down)

now thats all and you can use this command to see if you changed them

```
synclient -l
```

lastly you can add these to xorg.conf.d (see above to recap) and you should have them permantley saved

and the way you type them in as follows

Option "RightEdge"  "4905"

dont forget its one space between Option and "RightEdge" and two spaces between "RightEdge" and "4905"

and the same with the other 3 save and reboot and then its complete!

---

### Post by Enterpart on 2011-10-14
to set the tap zones with key strokes or commands check this

[COLOR="Red"][http://ubuntuforums.org/showthread.php?p=11342077#post11342077]("http://ubuntuforums.org/showthread.php?p=11342077#post11342077")[/COLOR]

---


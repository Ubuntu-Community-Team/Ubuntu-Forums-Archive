---
title: "Restore the xorg.conf"
date: 2007-05-08
forum: Hardware &amp; Laptops
---

### Post by ruibuntu on 2007-05-08
I had a Nvidia Geforce Mx 440 card which worked greaat with the latest nvidia legacy driver.


But after two weeks, the card which wasn't in a very good shape burned (i'm working on the reason for the burn). So I took the nvidia out and search mycupboard for any agp card, the best one was a matrox g200 with 8mb of sdram. I place it and turn on the pc.

No need to mention that a error happened and I had to change to the "terminal mode".

After 10 minutes(:lolflag: ) I was very angry and desperate so i made a backup of my old xorg.conf and deleted the one being used (I deleted it because the device section was for the nvidia card and I know it was stupid but i didn't care for that, after all if I had to reinstall ubuntu it wouldn't matter).

But it worked, the gdm started working without the xorg.conf!!

Now i wonder to regenerate the xorg.conf file with my currents graphics specs.


And by the way where can find decent 3d drivers for this board??

Thx in advance!!
:)

---

### Post by Wim Sturkenboom on 2007-05-08
G200 is a 2D card (afaik), so I would not waste my time on that part. No answer to the rest of the question(s).

---

### Post by jjordan on 2007-05-08
If you look in /etc/X11/ I think you will find that a new xorg.conf file has been generated when none was found.  I like to keep several backups of my xorg.conf when I am playing with video cards.  I usually copy the old on to something like xorg.conf-5-8-07-1 or something like that.

the command is:
**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-5-8-07-1**

- j

---

### Post by ruibuntu on 2007-05-08
> **jjordan said:**
> If you look in /etc/X11/ I think you will find that a new xorg.conf file has been generated when none was found.  I like to keep several backups of my xorg.conf when I am playing with video cards.  I usually copy the old on to something like xorg.conf-5-8-07-1 or something like that.

the command is:
**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-5-8-07-1**

- j

There wasn't any but i reconfigured xorg and everything went fine.
About the backups, i know the command but the one i had was for my burned nvidia so..

And Wim g200 is a 3d card. i'm sure of that.
About the drivers, i did found one with an .o extension.

How can use it ?????

---


---
title: "Live CD Installation woes"
date: 2006-01-20
forum: Installation &amp; Upgrades
---

### Post by dtrexel on 2006-01-20
Help. I put in the Live CD and it goes through the boot process. Once it is done, I get a screen that that has colored lines all throgh it and I can't see anything. Does anyone know why this happens and what I can do to correct it?

Thank you,
Derik

---

### Post by Kapre on 2006-01-20
[QUOTE=dtrexel]Help. I put in the Live CD and it goes through the boot process. Once it is done, I get a screen that that has colored lines all throgh it and I can't see anything. Does anyone know why this happens and what I can do to correct it?

Thank you,
Derik[/QUOTE]

derik - When you say "once it is done", do you mean the whole process went through and no GUI screen showing? or it is during the install (set-up process) that you experience this. What video card do you have?

K

---

### Post by dtrexel on 2006-01-20
I belive it is going through the setup process. I am not sure. I get the part that asks what language and what not, the video questionnaire screen and then I het the screen that shows all the colored lines. I have a (2) NVIDIA GEForce 660GT cards running in SLI mode, At least in Win XP. Any suggestions on what I am doing wrong?

Derik

---

### Post by dueY on 2006-01-20
[QUOTE=dtrexel]I belive it is going through the setup process. I am not sure. I get the part that asks what language and what not, the video questionnaire screen and then I het the screen that shows all the colored lines. I have a (2) NVIDIA GEForce 660GT cards running in SLI mode, At least in Win XP. Any suggestions on what I am doing wrong?

Derik[/QUOTE]

It's the video card.  Not really sure how to fix this on a LIVE CD.  If there's a way to configure X then you can fix it by switching your drive to "vesa".  Hmmm...

When you get to the colored messed up screen try pressing CTRL+ALT+F1.  It should bring you to a console.  Now type ```
sudo dpkg-reconfigure xserver-xorg
``` and see if that works.  If it takes you to the X configuration then as your display driver choose "vesa".  The rest of the options should be default/common sense.  Try that.  Once you get out of the configuration you might have to type ```
sudo /etc/init.d/gdm start
``` Try that and see if it works.

---

### Post by dtrexel on 2006-01-21
[QUOTE=dueY]It's the video card.  Not really sure how to fix this on a LIVE CD.  If there's a way to configure X then you can fix it by switching your drive to "vesa".  Hmmm...

When you get to the colored messed up screen try pressing CTRL+ALT+F1.  It should bring you to a console.  Now type ```
sudo dpkg-reconfigure xserver-xorg
``` and see if that works.  If it takes you to the X configuration then as your display driver choose "vesa".  The rest of the options should be default/common sense.  Try that.  Once you get out of the configuration you might have to type ```
sudo /etc/init.d/gdm start
``` Try that and see if it works.[/QUOTE]


Okay, I tried that and it did not work. At the console, I typed what you said to and it said that xserver-xorgand is not installed and that there is no information availbale. Any more suggestions.

Thank you,
Derik

---


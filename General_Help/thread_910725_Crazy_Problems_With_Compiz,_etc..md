---
title: "Crazy Problems With Compiz, etc."
date: 2008-09-04
forum: General Help
---

### Post by Thecoolguru on 2008-09-04
Ok, so I installed Emerald and Compiz-Fusion, and Compiz Icon  (though I don't know if that does anything), and I went to Appearance thing to change the setting from none to special. I got an error saying that I needed to install my graphics card, so I say sure, enter in my sudo password, and let 'er rip. A moment later, I was prompted to restart my computer, so I did. Ubuntu started to open up, everything was looking good until I needed to log in. Instead of my bright and cheery login screen, I got a strange flickering dark blue screen- obviously the nvidia driver didn't work. So I shutdown my computer, start back up again, and after a few minutes in recovery mode, I've managed to get everything back where it needs to be. So I go back and try to enable special in Appearance, and it just tells me that it can't enable it. I can't figure out how to get any of this to work, lest it be Emerald themes or purty 3D box type thingies. I need your help! Thanks in advance.

---

### Post by Kinetic_lord on 2008-09-05
You can install envy. It can install the latest drivers for nvidia or ati.
Open up Accessories>Terminal
paste this
Code:

sudo apt-get install envyng-gtk

when its done installing, to run it, in terminal type
Code:

envyng-gtk

or Applications>System Tools

it will install you're graphics card (the right way). After that... enjoy compiz :guitar:

---

### Post by Crafty Kisses on 2008-09-05
Post the results of this command: ```
glxinfo

```

---

### Post by revanb on 2008-09-05
I am running Hardy on a LG LM50a notebook with a ATI radeon mobility graphics card. I have a similar issue when using the default opensource driver, however the screen doesnt flicker everytime. Restarting x with Ctrl-Alt-Backspace or rebooting clears up the problem. When I use the fglrx driver it doesnt happen, but then x hangs often when I switch between virtual text consoles and back to graphical (ie Ctrl-Alt-[F1/F2 etc]

By the by, I am happy to hear about envy. I am going to try it, because I have been using compiz and it is really awesome, but unfortunately my system ends up lock up too frequently. I think it is due to the graphics card not being set up perfectly.

Also, I am starting to think about purchasing a new notebook as mine is already almost 4 years old. Are there any quality graphics card the are officially supported for linux by the manufacturers? For instance does ATI/nVidia provide the same quality drivers for linux as it does for windows for one/some/any of their cards?

---


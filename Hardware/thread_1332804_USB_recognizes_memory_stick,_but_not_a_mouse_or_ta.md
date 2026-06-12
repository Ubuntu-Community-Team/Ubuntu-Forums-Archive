---
title: "USB recognizes memory stick, but not a mouse or tablet?"
date: 2009-11-20
forum: Hardware
---

### Post by Naphrys on 2009-11-20
I am having some issues with my wacom bamboo tablet, because Ubuntu fails to recognize it, or my USB mouse. I know it's not a hardware issue because my memory stick loads just fine. I looked up drivers for it on the "Wacom Linux Project" but I am pretty lost.

Is there and easy way to do this? I'm much better at troubleshooting Windows as I have only been using Ubuntu for a few hours. So please feel free to dumb down any explanations as much as possible.

The computer is a Toshiba Satellite L45 series laptop. and I am pretty sure Windows vista is still available from the boot menu.

---

### Post by Naphrys on 2009-11-20
Ok I seem to have halfway solved this problem. 
now I can use the tablet, but I have not pressure sensitivity whatsoever.

I have downloaded the "linuxwacom-0.8.4-4" driver, extracted it to the desktop, and I kinda understand how to install it, but I keep getting a "file not found" type of error.

---

### Post by Favux on 2009-11-21
Hi Naphrys,

Welcome to Ubuntu Forums!

What version of Ubuntu are you using?  Karmic or Jaunty, etc.?  And what is your Bamboo model?  What application are you lacking pressure in?  Did you successfully compile and install linuxwacom-0.8.4-4?

---

### Post by Naphrys on 2009-11-21
Hello Favux! 
I'm using Karmic, and my tablet is a bamboo fun CTE-450/K.
I'm using Gimp 2.6 and as of the last post I could draw, but without sensitivity.

A few moments ago I managed to compile and install the "linuxwacom 0.8.4-4" pack, but since then I only have navigation, and it's very jumpy and feels broken. It is treating my tablet like a mouse, but I cant click on anything, or do much besides point at things.

---

### Post by Favux on 2009-11-21
Hi Naphrys,

OK, you need to install a linuxwacom.fdi.  The purge line if you followed my [HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949") deleted it.  Since the default .fdi doesn't work right I suggest you install the wacom.fdi in post #176 [here]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").  Just follow the instructions.

To get pressure in Gimp you need to configure the extended input devices.  See near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

Good luck!

---

### Post by Naphrys on 2009-11-21
That all seems really informative and I appreciate the help I have no idea where I'm trying to go with any of this.
I am pretty sure I used the Ubuntu wiki to do the "broken" compiling, but besides that I am lost. Meh I will work on it in the morning, maybe that will help.

---

### Post by Naphrys on 2009-11-21
OK, I tried the two options you gave me but I cant even get past the first step, keeps saying the .fdi file does not exist. 
It seems so straightforward but I keep missing something. What am I doing wrong!?

---

### Post by Favux on 2009-11-21
Hi Naphrys,

Well because you compiled the linuxwacom drivers the .fdi file isn't there.  So the cp (copy) command is just saying that.  The .fdi file is in the source code but you have to manually hunt it down and copy it into place yourself.  The Ubuntu linuxwacom packages automatically install the .fdi file.

So just go onto the next step, the "gksudo gedit etc." for Karmic.  It will automatically created the file for you.  Of course you have to enter the contents of the modified .fdi into it.

---

### Post by Naphrys on 2009-11-21
After a good bit of frustration I just ended up reinstalling the entire OS with the tablet plugged in and now everything works wonderfully.

Way easier then try to fix code I don't even understand how I messed up in the first place lol

But thank you so much for your help, it was very much appreciated ^__^

---


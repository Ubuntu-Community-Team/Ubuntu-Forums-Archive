---
title: "Restricting Wacom Tablet to a single screen with twinview"
date: 2011-05-24
forum: Hardware
---

### Post by BertieRooster on 2011-05-24
After googling around, I gather that the correct way to restrict my wacom (Intuos 3 A4) to a single screen is with the following xsetwacom commands:

```
xsetwacom --set "dev_name" "Twinview" "horizontal"
xsetwacom --set "dev_name"  "ScreenNo" "1"
```

However when I do this xsetwacom does not seem to recognise this as a valid parameter. I get the following:

```
~$ xsetwacom --set "Wacom Intuos3 9x12 stylus" "Twinview" "horizontal"
Unknown parameter name 'Twinview'.

```

I have tried twinview, TwinView etc too. And running xsetwacom --get "dev_name" all does not list TwinView" or the accompanying "ScreenNo" as parameters at all. Is this an issue with the version of xserver-xorg-input-wacom (0.10.11) I have installed or perhaps my display setup?

I'm running Ubuntu 11.04 with the regular gnome desktop (no unity).

Once I work out what the issue is I plan to add the correct options to my 50-wacom.conf

---

### Post by Favux on 2011-05-24
Hi BertieRooster,

Since you are using TwinView I gather you are using the Nvidia proprietary drivers?  TwinView stuff was dropped from xf86-input-wacom a while ago.  You would either use MapToOutput, or if you have the Nvidia proprietary driver the CTM method.  See:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Dual_and_Multi-Monitor_Set_Up)

---

### Post by BertieRooster on 2011-05-24
Edit: Thanks Favux. Yeah this is the method I arrived at.

Aha. So I discovered thanks to twitter that the twin view option is gone and [replaced by using a coordinate transform matrix. ]("http://ubuntuforums.org/showthread.php?t=1656089")

I've currently got the relevant commands for switching my tablet between screens as launchers on my desktop. I'm looking to map them to my tablet buttons now.

---

### Post by cartoonmonkey on 2011-07-30
OMG. This thread is a prime example of why Ubuntu isn't widely adopted by many artists.

Hand calculate a transform matrix to restrict wacom placement to one monitor?
It's mind blowing to me that the old GUI wacom control panel that used to exist for Linux has been "depreciated" to.. to this.

It's totally and completely insane to take something that worked, and throw out the easy setup for this option.. very frustrating!
:(

---

### Post by Favux on 2011-07-30
Hi cartoonmonkey,

Welcome to Ubuntu forums!

Well everything was rewritten and they are adding functions back.  MaptoOutput now supports Nvidia/TwinView so with the latest xf86-input-wacom you no longer need to do a CTM calculation.

The developement of configuration gui's is going slower than planned but they're getting there:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=External_applications#Graphical_Configuration_Tools](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=External_applications#Graphical_Configuration_Tools)  I should probably add the KDE one too I suppose:  [https://projects.kde.org/projects/extragear/base/wacomtablet](https://projects.kde.org/projects/extragear/base/wacomtablet)

---

### Post by merrak on 2011-07-31
I teach Linear Algebra from time to time, and I -told- my students there are uses for matrix multiplication! :P

This is a little nuts. I can see how the flexibility could be useful from a programmer's perspective, though...

---


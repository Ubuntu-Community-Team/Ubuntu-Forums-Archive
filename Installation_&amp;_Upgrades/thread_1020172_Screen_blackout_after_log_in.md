---
title: "Screen blackout after log in"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2008-12-23
I have installed 8.10 yesterday for a friend. Everything was perfect, we updated and installed compiz fusion. Today, when she turned on her computer, it booted all right, then the loading screen and log in, she put her user name and password and logged in and after it finished loading, a tiny black square appeared, then another and another when she clicked with the mouse and so on till the whole screen is black. I have told her to check for proprietary drivers but she can't see anything, she says that her video is an Intel 945GC Express Chipset.

P.S.: I'm posting for her because she doesn't speak english.

---

### Post by arashiko28 on 2008-12-23
Bump! Please help! she can boot perfectly on windows and doesn't have that problem...

---

### Post by abn91c on 2008-12-23
sudo apt-get remove compiz
sudo apt-get remove compiz-core
sorry dude no eye candy for her :-) Compiz no funciona con unas tarjetas de video intel, ve al recovery i saca compiz

---

### Post by arashiko28 on 2008-12-23
she can't run terminal, she can't see a thing.

I have been twitching a bit with the xorg.conf and found that she only has one line at the device section:
> :  Identifier    "Configured Video Device"

No driver, no option.

I know there is a bug since 8.04 that only allows to configure keyboard when typing 
> sudo dpkg-reconfigure xserver-xorg
So, how do I fix this?

P.S: No dude, I'm a girl.

---

### Post by Coder543 on 2008-12-23
Look

CTRL + ALT + F1
type username
type password (won't appear)

voila, you are now logged into the terminal!

type away...

---

### Post by arashiko28 on 2008-12-23
We are on recovery mode about an hour ago. I'm trying to find out how to get xorg.conf configure the video section and not just the keyboard.

---

### Post by arashiko28 on 2008-12-23
after removing compiz the black boxes went away. Now the big shot is to install video drivers for her card, as I said before is an Intel 945GC Express Chipset. So... any ideas?

---

### Post by abn91c on 2008-12-23
> **arashiko28 said:**
> after removing compiz the black boxes went away. Now the big shot is to install video drivers for her card, as I said before is an Intel 945GC Express Chipset. So... any ideas?

in the terminal sudo aptitude reinstall xserver-xorg-video-intel
 then reboot

---

### Post by arashiko28 on 2008-12-23
> **abn91c said:**
> in the terminal sudo aptitude reinstall xserver-xorg-video-intel
 then reboot

Still getting one line at the device section, no driver, no option:confused:

---

### Post by arashiko28 on 2008-12-24
We already ran out of ideas, I found this on another post
> sudo apt-get remove nvidia-glx
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-dri libgl1-mesa-glx

We tried it and it's the same. No driver output...

I'd like to thank to all of you who are trying to help.:)

---

### Post by abn91c on 2008-12-24
did you try the hardware drivers from the toolbar:  system>administration>hardware drivers
if anything is listed there you can enable it, if the box is blank you have the latest driver, if you screen resolution is Ok then the intel drier is installed properly

---

### Post by arashiko28 on 2008-12-24
The box is emtpy.

We still haven't found the solution.

---


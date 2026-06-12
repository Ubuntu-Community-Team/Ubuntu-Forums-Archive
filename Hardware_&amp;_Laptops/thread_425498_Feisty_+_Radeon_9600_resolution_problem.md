---
title: "Feisty + Radeon 9600 resolution problem"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by Karri on 2007-04-27
I can't seem to find any guides how to set my resolution in Feisty. The guides for previous Ubuntus seemed to go nowhere in Feisty.

The problem is I can't set my screen resolution to be bigger than 1024x768 @ 60Hz.

I could get it up to 1280x1024 @ 75 Hz on XP. What should I do to get there?

My monitor is some old crap Nokia Valuegraph 447W.

---

### Post by rjfioravanti on 2007-04-27
same problem here, even if I put the resolution 1280x1024 in the modes line, i restart x server and its still not in the list

using radeon driver

---

### Post by kelvin spratt on 2007-04-27
hi guys i use that 9600 and it defaults to 1600x1200 75 for me witch is ideal on a 19in screen i can't help to solve the problem except i did try ati drivers and just got a black screen i use an old uni dell monitor and i get good 3d

---

### Post by Karri on 2007-04-28
So basically I should just try and add "1280x1024" in every "mode" line in xorg.conf file?

---

### Post by rjfioravanti on 2007-04-28
I tried that but it doesnt work for me! I am using the open source radeon driver

Beryl works using AIGLX but can't get this resoultion past 1024x786

---

### Post by Karri on 2007-04-28
I found a complete solution at the Finnish Ubuntu board! Here's how it goes:

Go to the Terminal and type:

```
sudo gedit /etc/X11/xorg.conf
```

The xorg configuration file opens. Go to the part where it reads **Section "Device"**

See what it says in the **Driver** part (for example, **Driver ATI**)

Memorize it or write it down somewhere. Now back to the terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Now choose the name of the driver you just wrote down. It might differentiate a little, like my xorg.conf said "ATI andalongblablabla" and here it just said "ati".

Then press TAB and then ENTER to get to the next screen.

Now put a star in front of every resolution (using BACKSPACE) you want to use.

Use TAB and ENTER again to proceed.

Now restart your computer or restart X. The biggest resolution should now be in use. If not, you can now choose it from the Screen Resolution menu.

For some reason your keyboard layout probably changed to US settings. To fix this, open xorg.conf again:

```
sudo gedit /etc/X11/xorg.conf
```

and find the line called **Section "InputDevice**, and under it it says
**Option "XkbLayout" "us"**. Change the "us" to your country.

If your restricted driver says it's out of use, just click it back to on use and restart the computer.

This worked for me anyway.

---


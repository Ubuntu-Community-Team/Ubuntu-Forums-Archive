---
title: "Quake-style gnome-terminal with wmctrl"
date: 2008-10-18
forum: General Help
---

### Post by gfxfreak on 2008-10-18
First of all forget about my bad English and let me introduce myself since this is my first post, I'm from Bolivia and I've been an Ubuntu user since a few months ago (windows disapointment). I consider myself a computer geek and that's why I love Linux and open source software, it gives me the freedom to learn almost everything about my system.

So let's move to the point, since in Linux world you need to get used to the command line I've been searching for a comfortable way to access the terminal from any window, and that's quake-style! so I've tried Tilda, which is pretty good but it doesn't give me true transparency as gnome-terminal does (along with XGL and Compiz-Fusion) and I found wmctrl, a command to control windows position and all of that stuff, I managed to get it working with a script along with the ~ key but ran in a trouble when I changed the directory and the terminal windows changed it name (since wmctrl was using the window title to control it) and then I figured out that wmctrl can use hexadecimal ID's from windows to control them, but since the hex ID from a window can change from a session to another, my question is:

¿Can I write a startup script where wmctrl (or another tool) can output the hex ID to a file (or a buffer) and with it overwrite my existing script which controls gnome-terminal?

here is my script:

#!/bin/bash

if [ -f ~/bin/temp/quake ] ; then
wmctrl -i -r 0x03000020 -b remove,below
wmctrl -i -r 0x03000020 -b remove,shaded
rm -r ~/bin/temp/quake
else
wmctrl -i -r 0x03000020 -b add,below
wmctrl -i -r 0x03000020 -b add,shaded
touch ~/bin/temp/quake
fi

and here's the tutorial I used:

[http://wazem.blogspot.com/2008/03/quick-and-simple-quake-terminal.html](http://wazem.blogspot.com/2008/03/quick-and-simple-quake-terminal.html)

Thanks in advance! and oh yeah, thank you all of you ubuntu devs and all ubuntu users for making ubuntu my favorite distro and also for making my life easier and funnier. :lolflag:

---

### Post by shawnrgr on 2008-10-19
**sudo apt-get install yakuake**

YaKuake is inspired from the terminal in the Quake game: when you press a key
(by default F12, but that can be changed) a terminal window slides down from
the top of the screen. Press the key again, and the terminal slides back.

It is faster than a keyboard shortcut because it is already loaded into memory
and as such is very useful to anyone who frequently finds themselves switching
in and out of terminal sessions.

---

### Post by gfxfreak on 2008-10-19
Thank you for replying.
I appreciate your suggestion for using yakuake but there are some issues for me preventing it use.

First: It NEEDS to support true transparency as gnome-terminal does (I use it for copying long commands, to download certain data or to modify scripts).

Second: For simplicity I don't like the fact that it needs most of KDE's dependencies since I'm in a GNOME environment, also because my hard disk's space is limited.

I've thought of using some of this apps but I truly prefer making a script for this.

---

### Post by shawnrgr on 2008-10-19
well you could install its gnome equivalent, yeahconsole. but i don't know if it can be made transparent

---

### Post by gfxfreak on 2008-10-19
Thanks, I've successfully installed yeahconsole and I like it, BUT it does only support urxvt, urxvtc and xterm as terminal emulators which none of these support true transparency through compositing.

PS: Transparency is the most critical feature that I'm looking in a quake-style console, that's why I'm trying to write the script.

---

### Post by gfxfreak on 2008-10-19
Oh yeah and don't forget the tabbing feature of gnome-terminal that I use a lot. (I suppose many of you also do :shock:)

---

### Post by zhocchao on 2008-11-15
Hi 
You could use 


trm=$(wmctrl -l |grep "NAME@COMPUTER"|awk '{print $1}')


and put it in
wmctrl -i -r trm -b remove,below
wmctrl -i -r trm -b remove,shaded

I allways forget how to put it in.try it with ($trm),$(trm)

greetings
z

---


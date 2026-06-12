---
title: "Dvorak on Log in Screen"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by lexen on 2007-06-13
I use the dvorak keyboard, as do most of the people that I live with, but when someone comes to visit they like to change the keyboard to qwerty.  One of my friends did this and made it so it changed the keyboard layout for the login screen.  I don't know how he did it, but I can't change it back.  I have tried switching every user to dvorak and removing qwerty completely, but it still didn't help.  From what I can tell, he didn't change the system keyboard layout, because I have run a terminal while the OS is starting up and it is in Dvorak.

     Any help would be greatly appreciated.




Thanks,
Lexen

---

### Post by imog on 2007-07-04
I'm also a dvorak user.

Please refer to the post by nautilus [here](http://ubuntuforums.org/archive/index.php/t-24763.html%5B/t-14636.html).
[quote]tada, here i am to save your days!

for terminal, copy the dv keymap to your default, like so:

cp /usr/share/keymaps/i386/dvorak/dvorak.kmap.gz /etc/console/boottime.kmap.gz

there are a few dvorak variants in there, too.

for X, edit /etc/X11R6/xorg.conf and find the keyboard section ("Generic Keyboard") and add/edit the XkbLayout to be "dvorak"

all done, if it worked; enjoy :D

although, i think mine worked from installation, so, hmm weird :/

i hate getting stuck in "',.pyf" too ;)[/url]

---

### Post by E.T.Expatriate on 2007-07-28
I also have recently made the jump to Dvorak, and have been unable to change my login screen. Unfortunately, the process above is a bit too technical for a casual user (ie, strickly GUI) like myself. Would someone mind explicating a bit?

---

### Post by E.T.Expatriate on 2007-08-01
*cough*

Anyone?

---

### Post by PsyWolf on 2007-08-11
unfortunately there isn't a GUI way to do this yet but I will try to make it very simple for you.

1) Open up a terminal (i'm sorry) Its in the menu **Applications>Accessories>Terminal**

2) copy and paste the following line into the terminal and press enter```
sudo gedit /etc/X11/xorg.conf
```

3) hold down **Ctrl** and press the **F** key to open the "find" window

4) type "XkbLayout" into the "Search for:" bar and press enter
the text editor should jump to the line that reads: Option               "XkbLayout"               "us"

5) copy and paste this new line directly underneath that one```
	Option		"XkbVariant"	"dvorak"
```

6) Save and close the file

7) restart the X server by holding down **Ctrl** + **Alt** and pressing [B]Backspace
[/B]
Let me know if you have any problems.

---


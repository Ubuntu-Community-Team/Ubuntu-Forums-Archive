---
title: "updated kernal, now can't edit Grub menu.lst"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by deleyd on 2009-02-07
Kind of a moderate newbie to Linux. Ubuntu 8.04, I did an update of the kernel and now I can't edit Grub file menu.lst

I tried: **gksu gedit /boot/grub/menu.lst**

and nothing happens for 3 minutes, then the edit window comes up, but it's frozen.

I check SYSTEM -> ADMINISTRATION -> SYSTEM MONITOR,
I see a process named 'gedit', editing file:///boot/grub/menu.lst,
right-click select 'Open Files', among other things it lists:

[INDENT]/home/david.Xauthority
/tmp/libgksu-VspXRx/.Xauthority
/dev/null[/INDENT]


I *can* edit by going to File Browser, select menu.lst, right-click, select 'Open with "Text Editor"', text editor comes up fine with the file, but it won't let me save (I assume since I didn't invoke it in a privileged way).

Had a look at SYSTEM -> ADMINISTRATION -> USERS AND GROUPS,
that lists 2 items:

[INDENT]root
David Deley[/INDENT]

I noticed the Properties on root User Privileges all the boxes were unchecked. Tried checking them all (I have no idea what I'm doing. _Tell me if I should uncheck all those boxes again._)


Tried installing nautilus-gksu, then right-click on the file and select "Open as Administrator". Nothing happens, 3 minutes later the edit window comes up frozen just like before.

Also tried:
[INDENT]sudo apt-get purge grub
sudo apt-get install grub
sudo update-grub
cat /boot/grub/menu.lst[/INDENT]

seemed to uninstall/reinstall Grub OK, but didn't help.


Tried uninstalling Grub via Synaptic Package Manager. The box is now clear, but Grub still does its thing when I boot so I can select what operating system to boot (Ubuntu or Windows Vista).

[FONT="Arial Narrow"]"I know just enough to get myself into trouble, and not enough to get myself out of trouble."[/FONT]

---

### Post by taurus on 2009-02-07
```
sudo nano -Bw /boot/grub/menu.lst
```
When you are done editing, you can save and exit with <Ctrl>x and Y.

---

### Post by MarblePanther on 2009-02-07
Or:

sudo gedit /boot/grub/menu.lst

(gedit is easier than nano--though nano is easy also)

---

### Post by taurus on 2009-02-07
> **MarblePanther said:**
> Or:

sudo gedit /boot/grub/menu.lst

(gedit is easier than nano--though nano is easy also)

He/She said gedit froze on him/her after taking 3 minutes to start.

And by the way, it's probably a better idea to use gksu/gksudo with gedit than just sudo gedit.

---

### Post by MarblePanther on 2009-02-07
> **taurus said:**
> He/She said gedit froze on him/her after taking 3 minutes to start.

And by the way, it's probably a better idea to use gksu/gksudo with gedit than just sudo gedit.

Oh, I just assumed it was gksu that was taking a long time
You're right, my bad habits of sudo :)

oh, and I've had this problem with gedit taking forever to load up, it happened after an update-manager upgrade from hardy to intrepid.  It was some plugin that was stalling it.

Nano is a better idea... or you could install leafpad or mousepad,etc...

---

### Post by deleyd on 2009-02-07
> **taurus said:**
> ```
sudo nano -Bw /boot/grub/menu.lst
```
When you are done editing, you can save and exit with <Ctrl>x and Y.
Wow that actually worked no problem. So, nano is a different editor. Something wrong with gedit. Some sort of add-on? All I did was upgrade, but it was quite an upgrade, over 200 things installed. Wonder how I can review what those 200+ things were. Maybe one of them broke gedit.

---

### Post by caljohnsmith on 2009-02-07
Just to see if maybe the problem was with gedit, how about trying:
```
sudo apt-get purge gedit
sudo apt-get install gedit
```
And then try again:
```
gksudo gedit /boot/grub/menu.lst 
```
And see if that makes any difference.

---

### Post by deleyd on 2009-02-07
> **caljohnsmith said:**
> Just to see if maybe the problem was with gedit, how about trying:
```
sudo apt-get purge gedit
sudo apt-get install gedit
```
And then try again:
```
gksudo gedit /boot/grub/menu.lst 
```
And see if that makes any difference.

Tried that several times, didn't help. Also opened gedit and went to EDIT -> PREFERENCES -> PLUGINS, and unchecked everything (not many checked). Rebooted. Still get same thing editing any file with gksu gedit. Tried:```
gksu gedit /home/david/DAVID/x.s
```still no go.

Gedit works fine if I don't launch it using gksu.

---

### Post by MarblePanther on 2009-02-08
> **deleyd said:**
> Tried that several times, didn't help. Also opened gedit and went to EDIT -> PREFERENCES -> PLUGINS, and unchecked everything (not many checked). Rebooted. Still get same thing editing any file with gksu gedit. Tried:```
gksu gedit /home/david/DAVID/x.s
```still no go.

Gedit works fine if I don't launch it using gksu.

That's why I wanted you to try sudo instead of gksu.
Does sudo work?

If you like gedit better than nano, than mousepad or leafpad are great alternatives.

---

### Post by deleyd on 2009-02-09
Oh yes, I tried sudo, gksudo, gksu, made no difference.

---


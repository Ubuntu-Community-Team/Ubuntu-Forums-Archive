---
title: "xorg issue?"
date: 2008-08-20
forum: General Help
---

### Post by skydiver|goose on 2008-08-20
When I boot ubuntu, I get to what I assume is my logon screen, but my display is all sorts of screwed up, I can't see anything. From what I can see, the OS still works fine. I can just type in my username and password and hit enter and I see all the strewn lines on the screen do what I assume is log on, then I press the power button and I have my settings so that just pressing it initiates a shutdown, and it shuts down just fine, I just can't see anything.

---

### Post by tuxxy on 2008-08-20
Did you recently edit any video settings, you could try and reconfigure the xorg with this command

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by qstraza on 2008-08-20
Is it possible that your resolution is wrong?
Usualy screen moves when this is the case,

ctrl + alt + "Minus Key"

The numeric minus '-', on right side of the keyboard

---

### Post by skydiver|goose on 2008-08-20
Tuxxy, I can't even see the screen to pull up terminal

qstraza, I'll give that a try

---

### Post by qstraza on 2008-08-20
I had simular problem once (not the resolution related). I was trying to install drivers for nvidia from repos, and that thing happened, so i installed them using Envy

---

### Post by skydiver|goose on 2008-08-20
no luck.. took a picture with my mobile, here's what my screen looks like:

[Picture]("http://s20.photobucket.com/albums/b245/PearlExport5Pc/?action=view&current=PIC-0341.jpg")

---

### Post by qstraza on 2008-08-20
does it move/fuzzle? If it does than its the resolution, if not, then try that evny thing.

I hope it helps, if not, im out of the ideas

---

### Post by tuxxy on 2008-08-20
> **skydiver|goose said:**
> Tuxxy, I can't even see the screen to pull up terminal

qstraza, I'll give that a try

skydiver, can you not pull up a terminal by pressing, CTRL + ALT + F1 ?

---

### Post by skydiver|goose on 2008-08-20
qstraza, when I move the mouse, it does. I got no response from your key combination, though.

tuxxy, I probably could, but keep in mind I'm doing all of this blind, I wouldn't be able to read the terminal prompts :/

---

### Post by qstraza on 2008-08-20
I did not know that u r unable to get even in the text mode.
Pop in some livecd and boot it up, mount the root partition change config from init 5 to init 3 and reboot, so your linux should stay in text mode. 
Than play with xorg.conf or envy or whatever...

for changing init 5 to init 3 use search, i bet u could find how to do that and which conf u need to change;>

glhf ;)

---


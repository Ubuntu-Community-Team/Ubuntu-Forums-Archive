---
title: "Help! Keyboard problem"
date: 2008-10-28
forum: General Help
---

### Post by zerq on 2008-10-28
while trying to get resolutions above 640x480 in ubuntu in the x config file i must have messed up the keyboard...

can someone tell me how i fix it?
(swedish keyboard btw)


i'm a new linux user but i'm learning quite quickly... i'm just not sure what i do to fix this.. i'm guessing there is some way of booting up in bash console mode or such.. and then editing the x config file but i am not sure exactly how and what to change.

(its not my main computer is one i'm setting up for my sister and i've got it really neatly set up so i dont wanna have to start over...)

---

### Post by Portmanteaufu on 2008-10-28
I'm not the most knowledgeable person in the world when it comes to editing xorg.conf, but we can probably get you shell access so you can tweak it. Do you have either: 

1.) An SSH daemon installed and running on your Ubuntu box?
or
2.) A "Recovery Mode" (or something like it) in your grub menu at boot time?

If you don't recall installing an SSH daemon, you probably don't have one as I'm pretty sure it's not installed by default on Ubuntu. If you do have one, though, then you can go to your main computer and use putty (if you're in windows) or 'ssh username@[dead box's IP address]' to log in.

If you don't have #1, you should still (theoretically, at least) have #2, which as I understand it will let you boot to a command prompt so you can go edit the necessary files with vi(m) / nano / whatever. Typically I'd try it out myself first to make sure that I'm not giving you bogus advice, but unfortunately I'm not at home right now.

Good luck!

---


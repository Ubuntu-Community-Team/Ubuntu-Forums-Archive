---
title: "can't recet to default monitor on login"
date: 2009-11-13
forum: Hardware
---

### Post by Boulemans on 2009-11-13
I was just playing with hardware on Ubuntu the other day, just by adding a second monitor (acer) to my laptop (dell vostro 1000). All went fine, some display settings worked out, other didn't (laptop could only handle the 1280x720 60hz setting, the acer screen could handle other screen resolutions and refreshrates).

Now I must have changed some settings, because when need to login with the loginscreen, it does the following:

- displaying the loginscreen on the new acer display (although it is not always plugged in)
- using a screen setting that my laptopscreen can not handle (fuzzy grey/black/strange picture screen on the laptopscreen, although everything looks normal on the acer screen) 

I can still login when I plug the external acer monitor. Also, I can go into the terminal by ctrl-alt-f_: it's odd, but the terminal does displays on my laptop screen (and not the acer display).

I've tried changing my settings by the command:
```
sudo dpkg-reconfigure xserver-xorg
```
but just couldn't find "it" . I don't know which setting would change the monitor problem / don't know if i can solve the problem by this command.

I just want to get away the acer screen - using only my laptop screen.

greetings,

EDIT: By using a backup-file of xorg, the problem was solved.

---

### Post by Boulemans on 2009-11-16
No, not any idea? to bad ...

---


---
title: "Keyboard problems!!!"
date: 2008-10-09
forum: General Help
---

### Post by Dorian17xD on 2008-10-09
Hi, greetings from Costa Rica.

I've been having problems with my keyboard and Ubuntu.

Everything else is working perfect!! I love Ubuntu!! But my keyboard is the one that is not working properly.

The issue appeared when I tried to play Frets on Fire, I installed the game from Add/Remove Programs on the Gnome Menu, I changed some settings and the Frets on Fire crashed, my desktop looked very bad so I opened the terminal and I typed ```
sudo dpkg-reconfigure xserver-xorg
``` and I don't know what I did that my keyboard stopped responding (my mouse too).

I rebooted the pc and I entered to recovery mode, I typed ```
sudo dpkg-reconfigure xserver-xorg
``` again and I followed the steps but my keyboard was not responding as I wanted.

Later, when I reopened Ubuntu in normal mode and I enabled my Nvidia driver I saw that my keyboard layout was not checked on System->Preferences->Keyboard, I checked and from this point I got an error message explaining me that XKB crashed and may be a bug.

I tried again with ```
sudo dpkg-reconfigure xserver-xorg
``` twice and still the problem appears.

So I ran ```
xprop -root | grep XKB
``` and ```
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
``` as I was advised to do by the error message and I got this:

**xprop -root | grep XKB:**

```
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "latam", "\303\241latamlatams", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "latam", "\303\241latamlatams", ""
```

**gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd**

```
 layouts = []
 model = pc102
 options = []
 overrideSettings = true

```

Somebody can help me?? I cannot use "at" and also the "super" key. :(

---

### Post by Dorian17xD on 2008-10-09
Here I attach the error message, hope this will help me to solve this issue, even Print Screen key is not working, this is going bad...

---

### Post by Dorian17xD on 2008-10-09
Plz somebody delete this thread, I solved the issue with: sudo aptitude reinstall xkb-data

Thx to the people that saw the thread, I'm sorry I have not been in a long time on a forum and I was frustrated...

---

### Post by Kurou-san on 2008-10-09
Then you should mark this thread as solved.
(It is at the bottom of this page.)

---


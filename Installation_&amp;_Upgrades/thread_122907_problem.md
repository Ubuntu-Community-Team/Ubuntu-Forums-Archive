---
title: "problem"
date: 2006-01-28
forum: Installation &amp; Upgrades
---

### Post by wEEtoZ on 2006-01-28
After installation you log on to your account, after i've logged in i dont know what to do.. i tried to write "help" and a list of commands shows up.. but i dunno how to get INTO linux..:( plz help someone

---

### Post by wEEtoZ on 2006-01-28
plz dont ignore this.. i really need help here..:(

---

### Post by DiscoKiller on 2006-01-28
are you in the console/terminal perchance and are looking for the GUI?

if so try typing:
 
sudo startx
enter your password and the x server should start up giving you a shiny little GUI to play on

---

### Post by wEEtoZ on 2006-01-28
is the problem that i chose to only install "base system" or?

---

### Post by DiscoKiller on 2006-01-28
to me it just sounds like your xserver isnt running. what happened when u typed sudo startx?

---

### Post by wEEtoZ on 2006-01-28
first it asked for password.. i typed it in and then it comes "Command not found" and if i try to write sudo startx more it just says command not found:(

---

### Post by DiscoKiller on 2006-01-28
i cant think why that command wouldnt work. it has worked for me in the past even if it has only thrown an error up for a misconfigured xserver.

try this 

sudo /etc/init.d/gdm restart

thats another command i`ve geard of for restarting the GUI

---

### Post by wEEtoZ on 2006-01-28
damn.. it still doesnt work..:( im new to linux so i need a bit help to get started.. thanks for trying to help me dude! If u have any more advises just come with them=) Can i restart the computer now that its installed?

---

### Post by DiscoKiller on 2006-01-28
reboot is a mans best friend, i`m no expert but i kinda felt i had to try by you`re desperate tone,

if you end up back in the terminal again you can try installing the xserver package. i guess the command would be something along the lines of 

sudo apt-get install xserver-xorg-core

once that is installed do another reboot and hopefully you should be in the gui

keep posting i`ll try my best :D

DK

---

### Post by wEEtoZ on 2006-01-28
ok;D thanks:D im installing the xserver or what u call it now=)

---

### Post by hen3rz on 2006-01-28
> is the problem that i chose to only install "base system" or?

Yes. This is the problem. The base system is pure console with no GUI. To get the GUI you can either install it manually by using the following commands:

```
sudo apt-get install x-window-system-core gnome-session gnome-applets nautilus metacity xscreensaver gdm gedit gnome-terminal synaptic
```

Or you could reinstall ubuntu doing a full installation not a "server" installation **(Recommended)**.

I would recommend you reinstall ubuntu doing a full installation just so you get all the apps and everything else that comes with it.

---

### Post by DiscoKiller on 2006-01-28
hehe, kinda sorts the men from the boys, good luck weetoz, sorry i wasnt quite as sharp as el duderino there 

Peace 

DK

---

### Post by wEEtoZ on 2006-01-28
THANKS ALOT BOTH OF YOU:D It works perfect now..;) good to see people who wants to help beginners;)

---

### Post by DiscoKiller on 2006-01-28
surely the whole reason i come here. well saying that u can probably tell i`m no expert, but i do like to help those in the position i was in once. hope you get as much out of ubuntu as i have, 

DK

---


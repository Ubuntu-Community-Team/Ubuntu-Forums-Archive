---
title: "problems after installing with server option"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by spyke01 on 2006-02-05
ok, this is the 4th time ive written this message, i accidentally hit the left arrow inlynx and lost the preios three. This is also the 8th time ive installed ubuntu with the server otpion, i ust killed off a good copy of a normal ubuntu install.

each time i try installing either fluxbox, ubunmtu, or xfce afterr the server iunstall all i get is a blank screen and my monitor cuts on and off continuosly.

heres my latest set of commands:
```
install using server option
login
edit sources.list
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install fluxbox x-window-system-core xdm dillo synaptic
startx
"blank screen and blinking monitor"
sudo apt-get install  xfce4 mozilla-firefox
startx
"blank screen and blinking monitor"
sudo apt-get install  xterm icewm menu abiword
startx
"blank screen and blinking monitor"
sudo apt-get install  xubuntu-desktop
startx
"blank screen and blinking monitor"
sudo apt-get install  ubuntu-desktop
startx
"blank screen and blinking monitor"
sudo /etc/init.d/xdm
"blank screen then back to console"
sudo /etc/init.d/gdm start
"blank screen and blinking monitor ctrl+alt+bksp starts a constant loop between console and screen"
```

ive got no idea what is going wrong, a regular install works perfect, but anything above does the blinking screen effect

i really need a low resource using desktop that will be used for web, printer, file, and databse servers

does anyone know what might help me?

---


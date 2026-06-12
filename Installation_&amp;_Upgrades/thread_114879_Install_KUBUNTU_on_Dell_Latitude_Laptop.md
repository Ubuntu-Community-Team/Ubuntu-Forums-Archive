---
title: "Install KUBUNTU on Dell Latitude Laptop"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by jongooni on 2006-01-09
I installed kubuntu breezy on a dell laptop
but when I get to the kubuntu initializing screen
and get to the initializing pcmcia part it 
sends me directly to the tty1 login screen.
I login but it wont let me do 
sudo startx because the command not found
or
sudo kdm because the command not found
i did 
dpkg-reconfigure xerver-xorg but it says that it is 
not installed.

Any help is appreciated.

---

### Post by welsh_spud on 2006-01-09
Hmmm...it doesn't sound like very much was installed on your computer. When you get dumped into a command line type

sudo apt-get install kubuntu-desktop

But I suggest you give reinstalling Kubuntu all together a go. If that fails, the odds are it's faulty media (scratched CD, bad burning process etc)

---


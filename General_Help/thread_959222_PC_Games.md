---
title: "PC Games"
date: 2008-10-26
forum: General Help
---

### Post by rmcellig on 2008-10-26
My young nephew (10), wants to buy a computer. It would be so cool if I can install Ubuntu on it. He runs many PC games on his dad's PC. Would he be able to run these games under Ubuntu? What are his options.

---

### Post by Nepherte on 2008-10-26
All in all, Ubuntu or linux for that matter isn't suited for playing games. 

There are very few games that have linux versions of their games (Unreal Tournament, Neverwinter Nights, Enemy Territory, America's Army, ...

When there is no linux version available, some but certainly not all of the games can be run under wine, a windows emulator. Sometimes it can be difficult to set up as well.

If he's mainly going to game on his computer, I'd leave him be with windows.

---

### Post by CatKiller on 2008-10-26
It depends entirely on the games that he wants to run. There are some Linux-native games that he might like, and there are a handful of commercial games that have been ported to Linux. If these are the games that he plays, then there's no problem.

The more likely scenario is that these are games that are written for a different OS, in which case some kind of interpreter will be necessary - DOSBox for DOS games, ScummVM for point-and-click adventure games, or WINE for more general Windows games. Some games work better in WINE than in Windows, others don't work at all. There is a list of games and how well they work in WINE at appdb.winehq.com. There is also particular information there on how people have made specific games work in WINE.

Otherwise, you can dual-boot Windows and Ubuntu, so that when he wants to play games he boots into Windows, and he boots into Ubuntu for everything else. You can try virualisation, which will allow you to install a pretend version of Windows in Ubuntu, but the thing that is least likely to work in a virtual environment is graphical acceleration, which makes it a pretty sub-optimal solution for most types of game. Obviously you'll need to buy another Windows licence if you're going to install another copy of Windows.

EDIT: If there's already a copy of Windows installed on the new computer, then you can easily set up a dual-boot without removing the existing Windows installation. It used to be the case that the Vista EULA prohibited running Windows in a virtual environment. I have no idea whether Microsoft have decided to change these terms.

---


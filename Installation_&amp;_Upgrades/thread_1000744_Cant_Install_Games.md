---
title: "Cant Install Games"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by snipe76 on 2008-12-03
How can i install games on ubuntu 8.10?
i have some file with .sh and .tbz
can some 1 help me please?

---

### Post by Diabolis on 2008-12-03
Probably your game has a readme file where it tells you how to do it. If the .sh file its called "install", then run it like this in a terminal:
```

chmod +x install.sh
sudo ./install.sh
```

Before running anything with the sudo command, verify that it come from a trustworthy source.

A very quick guide: [http://martin.ankerl.com/2007/04/19/how-to-install-anything-in-ubuntu-condensed/](http://martin.ankerl.com/2007/04/19/how-to-install-anything-in-ubuntu-condensed/)

---

### Post by snipe76 on 2008-12-03
but which folder i put the "install" to install it?

---

### Post by snipe76 on 2008-12-03
after i installed it how can i play?

---

### Post by Diabolis on 2008-12-03
Don't you have a menu option now???
If not try typing the name of the game, example:
```
pacman -h
```

*next time give more info about what you are doing, like the name of the game or any error messages, so you'll get quicker responses.

---

### Post by snipe76 on 2008-12-03
ok, the name of the game is darwinia.
error:
Verifying archive integrity... All good.
Uncompressing Darwinia full 1.4.0b9......................................................................
/home/snipe76/.setup8599: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by Diabolis on 2008-12-03
I googled the error and I'm guessing that you are on a 64 bit computer, right?

---

### Post by snipe76 on 2008-12-03
how can i check it?

---

### Post by Diabolis on 2008-12-03
Execute:
```
uname -m
```
and paste the output here.

---

### Post by snipe76 on 2008-12-03
i686

---

### Post by binbash on 2008-12-03
sudo apt-get install libgtk1.2

---

### Post by Diabolis on 2008-12-03
nvm, you are not on a 64 bit machine. Yep, I was just about to tell you to install that library.

---

### Post by snipe76 on 2008-12-03
> **binbash said:**
> sudo apt-get install libgtk1.2

what it installed?

---

### Post by Diabolis on 2008-12-03
A library called **libgtk1.2**.

---

### Post by snipe76 on 2008-12-03
> **binbash said:**
> sudo apt-get install libgtk1.2

woohoo thanks man!
its worked

---

### Post by snipe76 on 2008-12-03
> **Diabolis said:**
> A library called **libgtk1.2**.

but why the installation ask for CD?

---

### Post by Diabolis on 2008-12-03
I don't know, I haven't installed it.

---

### Post by snipe76 on 2008-12-03
ok i installed it now how i run it?

---

### Post by Diabolis on 2008-12-03
Just run the game.

---

### Post by snipe76 on 2008-12-03
i click on the launcher in the games but nothing happan

---

### Post by Diabolis on 2008-12-03
Run it in a terminal, just as before, so you can see the error message.

---

### Post by snipe76 on 2008-12-03
error:
/usr/local/games/darwinia/lib/darwinia.bin.x86: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by Diabolis on 2008-12-03
You need another library:
```
sudo apt-get install libstdc++5
```

---

### Post by Diabolis on 2008-12-03
You need another library:
```
sudo apt-get install libstdc++5
```

---

### Post by snipe76 on 2008-12-04
thnks! i downloaded other game and its work!
i thing the problem is in darwinia!
thnks very much people!

---


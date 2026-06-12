---
title: "run exe files"
date: 2008-11-15
forum: General Help
---

### Post by maxx123 on 2008-11-15
i searched for this problem first but i only found topics where people are getting errors

My problem is that when i double click an exe file it opens it and shows loads of other files within it, it doesnt actually install the game..

Any ideas?

Thanks

---

### Post by SunnyRabbiera on 2008-11-15
windows .exe files do not really work by default in Ubuntu, to get them working you need wine.
But what game are you trying to install?
because Wine doesnt work on all games, wine is sort of the imperfect solution to running windows applications in linux, it works for some things but doesnt in others.

---

### Post by maxx123 on 2008-11-15
Worms armageddon..
What is this wine?

thanks for your help

---

### Post by RequinB4 on 2008-11-15
What are you trying to install?

An exe is a windows-only executable binary.  It may be possible to use Wine to run the exe, but there is no guarentee (see [http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine) and appdb.winehq.org)

You're might be better off finding a linux replacement or installing the game on a windows partition.

As for worms, try going to applications - add/remove and installing wormux

---

### Post by SunnyRabbiera on 2008-11-15
> **maxx123 said:**
> Worms armageddon..
What is this wine?

thanks for your help

Wine is a way to use windows applications in Ubuntu, it basically offers a way to use a good percent of your favorite windows applications.
Ubuntu and Windows are entirely different operating systems, they use different means to do the same basic thing.
Anyhow give wine a shot, its in your repository.
You can try it out by going up to your menu and click the add/ remove software option and search for wine.
Now the wine in the repositories isnt the latest version but since you are new I wont bog you down with command lines or nonsense like that.
Just give it a try, I am unsure if your game will work but its always worth a shot :D

---

### Post by ezkde4 on 2008-11-15
Use Windows for .exe files, or use an emulator. The first one is obvious--WINE. It's not really an emulator as defined by the programmers, but it works like an emulator from the user's view.
WINE does run some things correctly, and some not. It just depends.

There's also Wine-Doors, which is a GUI version of wine. Wikipedia has an entry on it over [here]("http://en.wikipedia.org/wiki/Wine-Doors")

Another application which I just found out about a couple of weeks ago is called PlayonLinux, which is [http://www.playonlinux.com/]("http://www.playonlinux.com/") here.
Try those out.
Also, if you have powerful enough hardware, you can run virtualbox, which allows you to run multiple OSes on top of one OS at a time. So, you could run an almost real time Windows XP or Vista session on top of linux. But you have to have good hardware specs for it to work.

---

### Post by maxx123 on 2008-11-15
Thanks for all your help guys =D really helped..

---


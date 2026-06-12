---
title: "no gui, need help"
date: 2009-02-01
forum: Installation &amp; Upgrades
---

### Post by Zom-b on 2009-02-01
I just upgraded to kubuntu 8.10 and decided I didn't like the KDE layout so I did all the stuff to get to the gnome gui, after that I did an update and install a few things, when I restarted my computer the GUI was completely gone and it doesn't let me leave the command line, I need help please, and thanks in advance

---

### Post by Zom-b on 2009-02-01
also I am wondering how often other people have problems quite like this? I'm sure it's just some simple fix, but I am fresh to ubuntu and still trying to beat that learning curve

---

### Post by Zom-b on 2009-02-02
alright I have been searching around and trying different things so far nothing has worked, I have tried typing gdm in the command line, startx, I tried sudo /etc/init.d/gdm start  so far nothing I have tried has worked, I am still stuck in this command line which I have very limited experience with, I seriously need help to resolve this

---

### Post by Neural oD on 2009-02-02
are you sure you downloaded all the right files for gnome? One the command line type: sudo apt-get install .....
whatever you were wanting - this should check to see if in fact all the necessary components are installed.

---

### Post by dominiquec on 2009-02-02
Tried

```
sudo apt-get install ubuntu-desktop
``` ?

This should get all the necessary packages in.

---

### Post by Neural oD on 2009-02-02
that should get everything in - so u saying that u have run that command?

---

### Post by Neural oD on 2009-02-02
have u tried typing: sudo gdm from the command line

---

### Post by Zom-b on 2009-02-02
> **dominiquec said:**
> Tried

```
sudo apt-get install ubuntu-desktop
``` ?

This should get all the necessary packages in.

I have tried this and I have also tried sudo gdm  and starx, but nothing seems to work, when I sudo gdm it says it's loading the gnome interface, then says ok then that's all that happens it just drops me back into command line, I have tried sudo apt-get install ubuntu-desktop again to no avial, I have tried going into aptitude and making sure I have all the updates fully installed and all the dependencies met, still nothing

---

### Post by Neural oD on 2009-02-02
maybe you're not in the correct tty - have u tried alt-F7 after running that command?

---

### Post by Zom-b on 2009-02-02
no I haven't tried that, I am at work right now and didn't think about bringing in my laptop. so I will have to check that when I get home, I hope that works, because I refuse to head back to windows lol

---

### Post by Neural oD on 2009-02-02
well good for u :) - I too have left windows in the scrap heap!

---

### Post by Zom-b on 2009-02-02
alright, I tried the alt-F7 and it changed from being root to being a blank screen with a blinky curser in the top left corner, the accessing hdd light blights every so often, how long does this usually take?

---

### Post by Zom-b on 2009-02-02
it was in tty1 when I was looking at it let me see if I can't get a screen shot in here maybe that will help out

---

### Post by Zom-b on 2009-02-02
This is what it looks like after everything is done and loaded

[ATTACH]101934[/ATTACH]

---

### Post by Neural oD on 2009-02-03
That is weird - have you tried going into the recovery mode when booting up - it should be on the grub menu

---

### Post by Partyboi2 on 2009-02-03
deleted[[COLOR=Blue][/COLOR]]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation")

---

### Post by jimbren on 2009-02-03
have you tried 
```
sudo apt-get install -f
```
or
```
sudo aptitude install gnome-desktop
```

I would reboot after each and see what happens.


kisses,

jimbo

---

### Post by Neural oD on 2009-02-03
Partyboi2 - ?? what is deleted

---

### Post by Partyboi2 on 2009-02-03
> **Neural oD said:**
> Partyboi2 - ?? what is deleted
It means I posted something then changed my mind, as I slightly misread the post.

---

### Post by Neural oD on 2009-02-03
kk - I see :)

---

### Post by Zom-b on 2009-02-03
> **jimbren said:**
> have you tried 
```
sudo apt-get install -f
```
or
```
sudo aptitude install gnome-desktop
```

I would reboot after each and see what happens.


kisses,

jimbo

I have tried sudo aptitude also, I also tried just typin aptitude and heading into it and updateing everything to make it current and it didn't help anything.

---

### Post by Zom-b on 2009-02-03
I only started getting this problem after I installed kubuntu and then tried to switch to ubuntu, I did a sudo apt-get install ubunut-desktop, after it was done I restarted and it worked fine, then I installed compiz and wine, went and restarted my laptop and then I got this problem.

---

### Post by Neural oD on 2009-02-03
maybe try: sudo dpkg-reconfigure ubuntu-desktop gdm

---

### Post by Partyboi2 on 2009-02-03
> **Zom-b said:**
> I only started getting this problem after I installed kubuntu and then tried to switch to ubuntu, I did a sudo apt-get install ubunut-desktop, after it was done I restarted and it worked fine, then I installed compiz and wine, went and restarted my laptop and then I got this problem.
Maybe compiz is causing the problem. Boot into recovery mode and remove compiz[FONT=monospace]
[/FONT]```
sudo apt-get remove compiz compiz-core
```

---


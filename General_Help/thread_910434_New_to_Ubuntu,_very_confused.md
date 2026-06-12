---
title: "New to Ubuntu, very confused"
date: 2008-09-04
forum: General Help
---

### Post by takkuso on 2008-09-04
I've been messing with it for a while, but there's one thing I'm having a really hard time getting used to: I can't find how to open things I've downloaded! For instance, I downloaded Secret Maryo Chronicles, and it's installed in my /usr/share/games/smc folder. But I can't for the life of me find which file I'm supposed to run to play the game.
Is there not a certain file type? Like windows has .exe which means "Run this"?

Thanks for the help.

---

### Post by tuxxy on 2008-09-04
What extension is the file

---

### Post by kostkon on 2008-09-04
> **takkuso said:**
> I've been messing with it for a while, but there's one thing I'm having a really hard time getting used to: I can't find how to open things I've downloaded! For instance, I downloaded Secret Maryo Chronicles, and it's installed in my /usr/share/games/smc folder. But I can't for the life of me find which file I'm supposed to run to play the game.
Is there not a certain file type? Like windows has .exe which means "Run this"?

Thanks for the help.
How did you install it?

---

### Post by bodhi.zazen on 2008-09-04
you run an application by calling it from the command line or making a launcher.

The problem is /usr/share/games/smc is not on your path.

As with windows, your path is where your shell looks for applications. You can see your path in a terminal by :

```
echo $PATH
```

you can all a launcher. The launcher will ask for the path to the application.

put in /usr/share/games/smc/application

Or you can add a link :

```
sudo ln -s /usr/share/games/smc/applicaion /usr/local/bin/application
``` or any other directory on your path.

Or you can add your directory to your path.

Open ~/.bashrc and add this line :

[quote]export PATH=$PATH:/usr/share/games/smc[/code]

then log out and back in (you can . ~/.bashrc if you wish not to log off :twisted:)

---

### Post by bingoUV on 2008-09-04
How to install anything in ubuntu, (and find it): [http://web.archive.org/web/20080202162909/http://monkeyblog.org/ubuntu/installing.html](http://web.archive.org/web/20080202162909/http://monkeyblog.org/ubuntu/installing.html)

---

### Post by ronnielsen1 on 2008-09-04
I assume it didn't put in a menu entry. Did you install with synaptic? If you're not sure where a program is you can open a terminal 
Accessories > Terminal

Type in whereis to find all instances of a package like ***whereis smc*** which returns 
smc: /usr/games/smc
(games are usually installed in /usr/games)

If it turns in more than one result which is usually the case type in ***which smc*** which will display the executable file

---


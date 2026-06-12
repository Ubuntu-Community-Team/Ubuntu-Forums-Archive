---
title: "Skype doesn't work"
date: 2005-12-01
forum: General Help
---

### Post by Nitro on 2005-12-01
I've installed all depenancies for skype, and just went through the guide on the ubuntu page. It seems to install fine and adds it's menu link. After I click the Skype icon in Applications -> Internet it just makes a "bloop" noise and does nothing. Am I missing something to get this running?

---

### Post by Nitro on 2005-12-01
bump

---

### Post by n8dagr8 on 2005-12-01
[QUOTE=Nitro]bump[/QUOTE]

same here...got it, click on it, nada. 

Thanks!

---

### Post by FLeiXiuS on 2005-12-02
Have you tried running it from the command line to possibly see any debug output.

---

### Post by mikeymouse on 2005-12-02
Hi. I had the same problem with skype,as they say kinda complicated to install.
Do a search here for 'skype and Automatix'  the Automatix will install it for you just fine actually it does a lot more but i have only installed skype with it . 
As they say try it it wont hurt.. 
good luck mikeymouse

---

### Post by Nitro on 2005-12-02
ryan@nitro:~$ skype
skype: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory


Er uh um huh? Halp!

---

### Post by FLeiXiuS on 2005-12-02
Try installing the libraties.

```
$ sudo apt-get install libqt3-mt
```

---

### Post by Nitro on 2005-12-02
Automatix doesn't work on .10

Installing now. Let's see if this fixes it. I thought I did this already though, hm, must have been uninstalled somewhere.

---

### Post by Nitro on 2005-12-02
That worked. Thanks. I could have sworn everything was spot on though, damn skype. This was the only thing that I had problems with.

---

### Post by n8dagr8 on 2005-12-02
[QUOTE=FLeiXiuS]Try installing the libraties.

```
$ sudo apt-get install libqt3-mt
```[/QUOTE]


You da man...seems to have fixed what was ailing me. Man, it takes for ever to load...oh, well. Thanks!

---

### Post by mikeymouse on 2005-12-02
[QUOTE=Nitro]Automatix doesn't work on .10.[/QUOTE]

Do you mean 5.10?
 I am using 5.10  Breezy  and it works and installs just fine.
 Using Automatix to install skype was a breezey hehehhe
 thanks

---


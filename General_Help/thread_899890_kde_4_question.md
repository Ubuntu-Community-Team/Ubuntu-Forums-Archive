---
title: "kde 4 question"
date: 2008-08-24
forum: General Help
---

### Post by evilnone on 2008-08-24
ok well basically i have ubuntu installed and i wanted to try out kde4 for myself and i installed it through rep. and did not like it... is there a way i can uninstall it and everything it installed (ie kopete, etc) or do i have to do that manually? also it changed the boot screen to kubuntu instead of ubuntu anyway i can change that back?

---

### Post by tuxxy on 2008-08-24
The boot screen will change back to the original Ubuntu screen once you remove KDE, open syanptic and search for KDE, remove anything you have installed

---

### Post by evilnone on 2008-08-24
> **tuxxy said:**
> The boot screen will change back to the original Ubuntu screen once you remove KDE, open syanptic and search for KDE, remove anything you have installed

kde removed kubuntu screen still there and yes i removed everything with kde (except whats needed for amarok)

---

### Post by evilnone on 2008-08-24
ok i guess ill reinstall ubuntu

---

### Post by tuxxy on 2008-08-24
> **evilnone said:**
> ok i guess ill reinstall ubuntu

lol theres no need to reinstall Ubuntu, open a terminal and try this and select your desired usplash

```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by evilnone on 2008-08-24
> **tuxxy said:**
> lol theres no need to reinstall Ubuntu, open a terminal and try this and select your desired usplash

```
sudo update-alternatives --config usplash-artwork.so
```



thanks fixed it... thanks given!

---

### Post by tuxxy on 2008-08-24
No problem, glad it worked, now you can mark the thread as solved :)

---

### Post by evilnone on 2008-08-24
ok when it shuts down it says ubuntu and when it boots up it says kubuntu what do i do to change that

---

### Post by evilnone on 2008-08-24
is a reinstall the only way to fix this? why does installing kde change the splash screen to kubuntu its not kubuntu it has gnome primary so why would it change?

---

### Post by evilnone on 2008-08-24
ok i guess its not fixable so i guess i have to reinstall... fyi never install kde4 on ubuntu it make pointless and irreversible changes to your system

---

### Post by evilnone on 2008-08-24
can someone please just tell me if a reinstall is needed before i waste time doing it?

---

### Post by txcrackers on 2008-08-25
Why does it matter? There's functionally no difference - or at least there *shouldn't* be any functional difference. If there is, you've got other problems to worry about...

---

### Post by evilnone on 2008-08-25
> **txcrackers said:**
> Why does it matter? There's functionally no difference - or at least there *shouldn't* be any functional difference. If there is, you've got other problems to worry about...


It matters to me, I don't run kubuntu I run ubuntu

---

### Post by txcrackers on 2008-08-25
That's just the splash/startup screen - there's *no* difference underneath it all. The distinction comes in which display manager gets installed by default. If you install Ubuntu and then install the KDE desktop, you get "Kubuntu." If you install Kubuntu and install Gnome, then you have "Ubuntu."

---

### Post by evilnone on 2008-08-25
> **txcrackers said:**
> That's just the splash/startup screen - there's *no* difference underneath it all. The distinction comes in which display manager gets installed by default. If you install Ubuntu and then install the KDE desktop, you get "Kubuntu." If you install Kubuntu and install Gnome, then you have "Ubuntu."


its just annoying to see since i no longer have kde installed, does anyone know of a way to change it? is it something in a script somewhere i can change?

---

### Post by fooman on 2008-08-25
have you tried using "startupmanager" to change the usplash screen? ...there is an option in there for that. 

don't know if it will work, but worth a shot.  it is in the repos so you can use synaptic, or in a terminal:

```
sudo apt-get install startupmanager
```

---


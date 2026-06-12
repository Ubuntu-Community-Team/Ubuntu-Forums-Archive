---
title: "Ubuntu isn't loading in Hardy"
date: 2008-10-19
forum: General Help
---

### Post by JH.Kael on 2008-10-19
EDIT: SOrry for the error at the title, I think I was distracted...

after a disk fsck during startup Firefox 3.0 isn't loading anymore, I click on the shortcuts and only shows "Loading Mozilla Firefox..." and then nothing, then I type "firefox" on commmand and doesn't gave me any input, it's just:
```
kael@kinich:~$ firefox
kael@kinich:~$ 

```
And nothing else happens... I installed Ephipany in order to browse the forums... any ideas, I'm worried since it seems like a lot of stuff depends of firefox.

---

### Post by Hangwire on 2008-10-19
erm... reinstall firefox? 

```
sudo apt-get remove firefox
sudo apt-get install firefox
```

---

### Post by JH.Kael on 2008-10-19
> **Hangwire said:**
> erm... reinstall firefox? 

```
sudo apt-get remove firefox
sudo apt-get install firefox
```

Isn't working, I unisntalled, restarted, then reinstalled and still the same problem

---

### Post by Hangwire on 2008-10-19
Did you try running it in safe mode?

```
firefox -safe-mode
```

---

### Post by JH.Kael on 2008-10-19
> **Hangwire said:**
> Did you try running it in safe mode?

```
firefox -safe-mode
```

Thanks, that worked, sorry for the newb question, i was really lost, I wonder why doesnt started normally until trying safe mode...

---

### Post by jimv on 2008-10-19
Could be something messed up in your profile.  /home/you/.mozilla

---


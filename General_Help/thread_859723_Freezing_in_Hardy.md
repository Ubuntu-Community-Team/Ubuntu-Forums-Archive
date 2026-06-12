---
title: "Freezing in Hardy"
date: 2008-07-14
forum: General Help
---

### Post by theelk801 on 2008-07-14
I have a problem in Hardy where an app will freeze for no reason and then not open again. I'll have Banshee open and something will cause it to freeze, forcing me to force quit it. Then when I go to open it again it won't open. After that other apps will freeze and die until I reboot. It has afflicted Banshee, Firefox, Pidgin, XChat, Nautilus, and Terminal. It is very annoying to have to continually reboot and I'd like a solution besides reinstalling Ubuntu. Upgrading to Hardy first day was a huge mistake and I regret it heavily now. Please help.

Now I'm off to reboot yet again.

---

### Post by tramir on 2008-07-14
Never mind, I mis-understood you problem. Sorry...

---

### Post by Jim! on 2008-07-14
Compiz sure seems to get the blame for a lot of things these days, its never caused me any problems (fortunately). A lot of people seem to be experiencing this problem lately so try doing a search of the problems;) 

Is your system up to date? I'm pretty sure there has been a recent kernel release so it could help your system with stability.

---

### Post by theelk801 on 2008-07-14
It should be up to date.

Also I have Compiz disabled due to errors. I think I should just reinstall...

---

### Post by ghost_ryder35 on 2008-07-14
> **theelk801 said:**
> I have a problem in Hardy where an app will freeze for no reason and then not open again. I'll have Banshee open and something will cause it to freeze, forcing me to force quit it. Then when I go to open it again it won't open. After that other apps will freeze and die until I reboot. It has afflicted Banshee, Firefox, Pidgin, XChat, Nautilus, and Terminal. It is very annoying to have to continually reboot and I'd like a solution besides reinstalling Ubuntu. Upgrading to Hardy first day was a huge mistake and I regret it heavily now. Please help.

Now I'm off to reboot yet again.
is there anything interesting in
```

/var/log/messages

```
```

dmesg

```
? 
One thing you can do is run the programs from the terminal and the next time they freeze copy the text from the terminal to this thread

```

xchat

```
```

nautilus

```
etc...

---

### Post by theelk801 on 2008-07-14
Well what exactly am I looking for in it?

---

### Post by ghost_ryder35 on 2008-07-14
> **theelk801 said:**
> Well what exactly am I looking for in it?
when a program that is running in the terminal crashes the terminal will spit error messages out... thats what you will want to look for.

---


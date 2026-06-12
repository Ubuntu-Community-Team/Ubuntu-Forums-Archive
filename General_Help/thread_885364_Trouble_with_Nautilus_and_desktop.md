---
title: "Trouble with Nautilus and desktop"
date: 2008-08-10
forum: General Help
---

### Post by Linux&gt;All on 2008-08-10
Hello, I'm new around these parts but always come here to look for help. Before now, I could find the answer to most of my problems here, but I haven't been able to fix this one on my own.

First off I'm running the Hardy 2.6.24-19 kernel. My problem is that when I first log in Nautilus starts and brings up my home directory (for reasons unknown to me), then crashes repeatably starting the chain over again. I have to open a terminal and "killall nautilus" to regain control of my computer. I have no icons on my desktop and can not right-click it either. Nautilus also closes when I try to open my desktop folder.

I have tried reinstalling nautilus and ubuntu-desktop to no avail. When I start nautilus from the terminal I get this:

```
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:9677): WARNING **: Unable to add monitor: Not supported
Segmentation fault
```

I can however start it from Places > Home etc. I am trying to be as specific as possible to help you guys out. Thanks for a great community that hasn't let me down let!

~Sean

---

### Post by Linux&gt;All on 2008-08-11
Bump.

Anyone? :(

---

### Post by Tom--d on 2008-08-11
Try this:

```
mv ~/.nautilus ~/.nautilus-backup
```

Then log out. and log in again. 
Did it fix it? 
If not, reverse the command.

```
 mv ~/.nautilus-backup ~/.nautilus
```

---

### Post by Linux&gt;All on 2008-08-11
[QUOTE="Tom--D"]Try this:...[/QUOTE]

I tried the first line of code and logged out and then back and it didn't fix it, same with the second line. I then restarted and still nothing. I never realized how much I used my desktop until I couldn't.. :confused: Thanks for your reply!

---

### Post by Linux&gt;All on 2008-08-12
Is anyone able to help? Pwease? :)

EDIT: I found [this]("http://ubuntuforums.org/showthread.php?t=794220&highlight=nautilus%3A13474+segmentation+fault") thread with a similar problem where nautilus opens up to home folder with desktop icons and then crashes and starts over again and again and then eventually stops, ending up with no desktop icons and no right-click. I have tried removing the .nautilus folder and removing most config files in my home directory to no avail.

I still can't even open my Desktop folder, not even through gksu nautilus which returns no errors. Just "nautilus" however still comes up with an "Unable to add monitor" and "Segmentation fault" error. Help is appreciated! I want my desktop back. :(

---

### Post by Linux&gt;All on 2008-08-13
Ka-bump.

---


---
title: "Several Commans in Main Menu Entry"
date: 2008-08-12
forum: General Help
---

### Post by Unanimated on 2008-08-12
Hi, I was just wondering how I can get a main menu entry to run multiple commands, and also what I need to put in to get something to get put in and entered into the terminal. The entry I'm trying to get is Tremulous. I'm trying to get it to run in x.game. Here's what I've tried so far:

gnome-terminal wait 40 cd ~/.Games/tremulous wait 40 x.game start tremulous.x86 [X]

gnome-terminal input x.game start ~/.Games/tremulous/tremulous.x86 [X]

I noticed that x.game will only start something if it is run from a terminal window. [X] means that it didn't work, [R] means that it did.

---

### Post by Ahadiel on 2008-08-12
For executing commands inside a new terminal, try this:
```
gnome-terminal -e "code to execute inside here"
```

And for having multiple commands in one line, either seperate the commands with either && or ;
```
echo "hello" && echo "hello again"
or
echo "hello"; echo "hello again"
```

---

### Post by Unanimated on 2008-08-12
I tried the first option, but when it starts x.game, it goes back to my current X server instead of staying on the one that's running Tremulous. I Ctrl+Alt+F12 to the other X server where it should be, and it shows a blank screen.

EDIT: To be more specific, here's what I put:

```
gnome-terminal -e "x.game start ~/.Games/tremulous/tremulous.x86"
```

That didn't work. However, when I open a normal terminal window and put x.game start ~/.Games/tremulous/tremulous.x86, it opens just fine.

---

### Post by Unanimated on 2008-08-12
bump

---

### Post by Unanimated on 2008-08-12
bump

---

### Post by Unanimated on 2008-08-13
bump

---

### Post by Unanimated on 2008-08-13
bump

---

### Post by Unanimated on 2008-08-13
bump

---

### Post by rossjman1 on 2008-08-13
Just make a script to do what you want. Create a script called "tremulous" in your home folder. Put this in there:
```
#!/bin/sh
cd ~/.Games/tremulous
./tremulous.x86

```
I ommited the wait commands, because I don't know the exact bash command to wait, you may need to look it up. Then you need to make the script executable (you may need to use sudo for this, I'm not 100% sure.
```
chmod +x tremulous
```
Then just point the launcher in the menu to this script.

---

### Post by Unanimated on 2008-08-13
That worked. Here's what I put:
```
#!/bin/sh
x.game start ~/.Games/tremulous/tremulous.x86
```
Thanks a lot!

---


---
title: "Spring Engine mods."
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Kale the Quick on 2009-10-31
The Spring Engine, which we can download from the Software center, and a single mod for it (Kernel Panic) is cool, BUT, i cannot install any other mods for it! I can download them from the project [website]("http://springrts.com/"), but i cannot copy/paste into my usr/share/games/spring directory to allow it to play the mod.

Any ideas? 

Also why can i not write to a directory on MY computer? I should be able to write all over the place!

---

### Post by bulldog on 2009-10-31
Can't help you with the game,BUT if you want to write to any of your system files,you need super-user rights.
This can be obtained by using sudo as the first word in your terminal.
Like ```
sudo aptitude update
```
It will ask for your password.
Be very careful when changing system files,be sure you know what you're doing!

Also you can open applications as super-user```
gksu gedit /etc/apt/sources.list
```this will open your sources.list and you can edit this.
Make sure to make a back-up before changing anything.

---

### Post by Kale the Quick on 2009-10-31
Yes, i know of sudo and his innumerable prowess... 

What would i type if i wanted to move something from say, /home/downloads/ultragame.game to usr/share/games/spring

i have been having trouble with this, as using a terminal is new to me. i tried what the little ubuntu help thing said, but now i need the help of real people.

---

### Post by bulldog on 2009-11-01
It would be something like this ```
sudo cp /home/downloads/ultragame.game /usr/share/games/spring 
```

Or you can use nautilus with root permission to drag and drop.

---


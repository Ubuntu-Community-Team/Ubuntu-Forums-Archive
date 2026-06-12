---
title: "[SOLVED] Help Firefox 3.0.3 CPU problem"
date: 2008-10-28
forum: General Help
---

### Post by alienprdkt on 2008-10-28
First off I have an Intel core-duo 3.0 with 2048mb ram.

I have installed  Firefox 3.0.3 on Ubuntu Hardy, and have it opened and minimized. Then opened system manager and watching as Firefox goes up to 78% of CPU, then goes to sleep (25%) then runs again starts at 45% back up to just bout 80% and keeps repeating.

I can not open more then 4 tabs without Firefox locking my system up, why is this, please help?

---

### Post by drelyn86 on 2008-10-28
Check if your addons might be the culprit. Disable them one-by-one and see what happens.

---

### Post by forger on 2008-10-28
also try:
```

killall -9 -r firefox
firefox -safe-mode

```

---

### Post by alienprdkt on 2008-10-28
nope didnt work, the only Addon extention I had was the Ubuntu Firefox Modifications 0.5. 

Disabled it didn't change the problem.

Thanks for your input..
Any other solutions?

---

### Post by alienprdkt on 2008-10-28
> **forger said:**
> also try:
```

killall -9 -r firefox
firefox -safe-mode

```

seems to run a lot better now... am I going to have to use firefox -safe-mode all the time?

---

### Post by forger on 2008-10-28
- Did you upgrade your Ubuntu Hardy Heron, or did you do a format and clean installed it?
- Did you use the wubi installer?

- Try this (close all your firefox windows first):
```
firefox -ProfileManager
```

Create a new profile, then use the newly created profile

If new profile works well, one of the following is problematic:
a) your extensions / add-ons
b) your themes
c) something in the configuration folder: /home/yourusername/.mozilla

You could backup your bookmarks and passwords (see this post for more info on those: [http://ubuntuforums.org/showthread.php?p=6041787#post6041787](http://ubuntuforums.org/showthread.php?p=6041787#post6041787))

Then you could move the .mozilla folder temporarily (**Close all firefox windows!**):
```
mv $HOME/.mozilla $HOME/mozilla-backup
```

And restore everything back inside :)

---

### Post by alienprdkt on 2008-10-28
> **forger said:**
> also try:
```

killall -9 -r firefox
firefox -safe-mode

```

just wondering what was the 

killall -9 -r firefox ?

what ever it was (don't know if it is related to the fix) seems to have fixed my problem with 

"Firefox goes up to 78% of CPU, then goes to sleep (25%) then runs again starts at 45% back up to just bout 80% and keeps repeating"

it only goes to the running state whenever I do anything, its not constant anymore thanks.

---

### Post by forger on 2008-10-28
ah, great then!
it killed all processes that contained the word "firefox" in their name :)

---

### Post by alienprdkt on 2008-10-28
yeah 
didn't think it was anything too serious, i dont have any addons, Ubuntu clean install LAMP only been up for bout 2 weeks. 

Guess I had multiple instances running somehow? 
but system monitor only showed 1?
anyways works great now, goes to sleep as soon as I stop using it.
So thanx agian.

---

### Post by forger on 2008-10-28
Weird, maybe it wasn't firefox exactly.. A sort of equivalent to the command above (to find the processes in a similar way) would be:
```
ps aux | grep firefox
```
..and it would kill all the processes you had access to.

Maybe some child process borked it, no idea! It wasn't supposed to be a solution :lolflag:

---


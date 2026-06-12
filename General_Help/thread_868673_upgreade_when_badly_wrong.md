---
title: "upgreade when badly wrong"
date: 2008-07-24
forum: General Help
---

### Post by dellboy on 2008-07-24
i updated my verion of ubuntu via the update manger to ubuntu 8.04.  it stop when it got to  cleaning and restart part so i turned of my computer but now i can not login to uubntu. as soon as i put my username and password in it neaver finds the desktop.

is there away i can find this i can still get in to repir mode.

any help would be Great 

i done this update like this before i just i have an old verion of ubuntu on a disk so i used that to instill 

thank you 

hope i made my self clear

---

### Post by iaculallad on 2008-07-24
> **dellboy said:**
> i updated my verion of ubuntu via the update manger to ubuntu 8.04.  it stop when it got to  cleaning and restart part so i turned of my computer but now i can not login to uubntu. as soon as i put my username and password in it neaver finds the desktop.

is there away i can find this i can still get in to repir mode.

any help would be Great 

i done this update like this before i just i have an old verion of ubuntu on a disk so i used that to instill 

thank you 

hope i made my self clear

Try to boot using recovery mode:

```
sudo apt-get install -f
sudo dpkg --configure -a
sudo xfix
startx
```

One-command-at-a-time

---

### Post by dellboy on 2008-07-24
no luck still not working :(

---


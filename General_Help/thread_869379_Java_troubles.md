---
title: "Java troubles"
date: 2008-07-24
forum: General Help
---

### Post by TheRedStarProject on 2008-07-24
I was trying to install Java last night and i finally managed to get it to start installing and i go this

E: dpkg was interrupted you must manually run 'dpkg--configure-a' to correct the problem
E: _cache-7 open () failed, please report

i tried again today from a plug-in link on a website and it did the same thing.  how do i correct this ?

thanks!

---

### Post by TheRedStarProject on 2008-07-24
anyone?

---

### Post by Tim Sharitt on 2008-07-24
In a terminal:
```
sudo dpkg--configure -a
```

---

### Post by TheRedStarProject on 2008-07-24
sudo: dpkg--configure: command not found


i got this in terminal

ive been looking around the net for a good while and tried all the terminal commands and added the deb.. to the repository and tried that method

ive downloaded jdk-6u7-linux-i586-rpm.bin to my desktop and it wont let me install it, i get sudo: ./jdk-6u7-linux-i586-rpm.bin: command not found


i tried ./<file name>.bin , chmod 755 <file name>.bin, and sudo ./name.bin
all three failed.  

thanks again for the help, ill get the hang of it soon

---

### Post by Tim Sharitt on 2008-07-24
Sorry, I left a space out:
```
sudo dpkg --configure -a
```

---


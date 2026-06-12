---
title: "theme problem intrepid"
date: 2008-11-14
forum: General Help
---

### Post by fireoptic on 2008-11-14
I did a fresh install of intrepid and reinstalled my theme however now the temem is not applied to synaptic. the title bar is right but the rest of the window is in the default theme..This was not an issue in hardy have tried re downloading and reinstalling theme with no difference. any ideas where to start looking to fix this? thanks in advance.

---

### Post by binbash on 2008-11-14
did you link your .icons .themes .fonts to /root ? or if they are small @ size you can copy them to /root , it will fix that

---

### Post by loomsen on 2008-11-14
Aye, I wouldn't do that, but rather store icons either in 
/usr/share/icons or ~/.icons

Where they actually belong. Otherwise you could experience some very ugly glitches. My /root/.icons as well as /root/.themes are there, but nothing in them.

---

### Post by mssever on 2008-11-15
Making symlinks like binbash suggested will ensure that programs that run as root will always match your current theme. However, I think it's preferable to use a different theme for root (such as the default) to remind you when you're running as root. The uglier the better.

---

### Post by blackened on 2008-11-15
They are referring to
```
sudo ln -s /home/**yourusername**/.themes /root/.themes
sudo ln -s /home/**yourusername**/.icons /root/.icons
sudo ln -s /home/**yourusername**/.fonts /root/.fonts
```

---

### Post by fireoptic on 2008-11-15
thanks guys ill give that a try and post results

---

### Post by fireoptic on 2008-11-15
yes that solved my issue thanks much guys.

---

### Post by MyKal on 2008-11-16
i have the same problem i want my root apps to match the rest 

i tryed this once and i must have done something wrong because it didnt work but now when i try the directions here i get the error too many link levels or something like that


edit* ok i figured it out on my own i had to go in and manually delete the old links that i made and start over

---


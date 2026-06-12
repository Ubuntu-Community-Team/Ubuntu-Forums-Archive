---
title: "How to install Ubuntu Studio Audio files on Hardy."
date: 2008-07-11
forum: General Help
---

### Post by Avinash.Rao on 2008-07-11
Hello all,

I am running Ubuntu Hardy 8.0 on Acer 3620 Laptop and i am trying to install Ubuntu Studio audio files. I don't require the complete theme, i just want to be able to select the Studio Login/Logout sound files and the wallpaper. Is this possible? 

the result of apt-get install ubuntustudio-audio is

0 upgraded, 169 newly installed, 0 to remove and 0 not upgraded.
Need to get 346MB of archives.
After this operation, 738MB of additional disk space will be used.

I don't want the whole thing? Is is possible to just get the studio login/logout files? 

:) :)

---

### Post by sayakb on 2008-07-11
Try:
```
sudo apt-get install ubuntustudio-sounds
```
This would remove ubuntu-desktop and ubuntu-sounds
It's okay to remove ubuntu-desktop since its a metapackage and removing it wont actually harm your system. But Im not sure if ubuntustudio sounds will work (I mean, it should, but since I haven't tried this before, I cannot assure you).

---

### Post by Avinash.Rao on 2008-07-12
Okay, i don't mind this, but how do i get Ubuntu sounds back?



> **LinuxIsInnovation said:**
> Try:
```
sudo apt-get install ubuntustudio-sounds
```
This would remove ubuntu-desktop and ubuntu-sounds
It's okay to remove ubuntu-desktop since its a metapackage and removing it wont actually harm your system. But Im not sure if ubuntustudio sounds will work (I mean, it should, but since I haven't tried this before, I cannot assure you).

---


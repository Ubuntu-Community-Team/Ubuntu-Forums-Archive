---
title: "Cant login ubuntu :("
date: 2005-11-19
forum: General Help
---

### Post by SkillZero on 2005-11-19
i try login my ubuntu and it says "cannot open your authoration file" something.. with a long messege , and says to contact my adminstator blabla..
dont know what to do

p.s
i dont know how to spell authoration..

---

### Post by Bachstelze on 2005-11-19
is by any chance your /home directory mounted to a FAT partition ?

---

### Post by SkillZero on 2005-11-20
i beg your partten? =\

i forgot to mention that im using linux for 2 days..
andits "authorization file", sry for my mistakes.

---

### Post by Karahana on 2005-11-20
Is it maybe the .IDEauthority file in your home directory? Had the same problem a while back. It's caused by some KDE apps running under non-KDE desktops.

Just delete the file manually from console (hit Ctrl + Alt + F1 for console,  Alt + F7 to return back to GUI, then Ctrl + Alt + Backspace to reset X and login again).

---

### Post by SkillZero on 2005-11-20
[QUOTE=Karahana]Is it maybe the .IDEauthority file in your home directory? Had the same problem a while back. It's caused by some KDE apps running under non-KDE desktops.

Just delete the file manually from console (hit Ctrl + Alt + F1 for console,  Alt + F7 to return back to GUI, then Ctrl + Alt + Backspace to reset X and login again).[/QUOTE]

am i supposed to do it when im already inside the ubuntu? because i cant login at all. when i click Enter it opens the ubuntu for 1 sec that i can only see my background and then error , when i click ok im back to the login window

---

### Post by Karahana on 2005-11-20
You can hit Ctrl + Alt + F1 at any time (even when the error window is on screen) and it will ask you your username and password. When logged in go to your home directory, erase the file, return to GUI (Alt + F7) and restart it (Ctrl + Alt + Backspace). Now enter your login details again and keep your fingers crossed. :)

---

### Post by SkillZero on 2005-11-20
HEY! I GET IT NOW!
yesterday , before i had the error..i was downloading few things.
the download was stuck at the middle, so i quit it and started again , it also stuck again.
i couldn't figure why, but now, when i tried to use the wine command to open a game from that console u told me , it said that memory is full!
now i get it! why the download stuck and probably why i cant login!
now , how do i enlarge the space for my linux? (im running 2 OS)

---

### Post by Karahana on 2005-11-20
Just a small correction... The file is ".ICEauthority" nod "IDE". :)

Even though "out of memory" doesn't sound like a HD-space error to me, under linux you can use QTparted (free) ,under windoze you can use PQMagic or Acronis (not free :P) to resize your partitions.

---

### Post by SkillZero on 2005-11-20
i already have Partition Magic, im in it right now.
it shows that i have 2 linux partitions , 1 of them is using almost the whole space.
i dont know how to add more =\

---

### Post by SkillZero on 2005-11-20
hmm help..i think im gonna delete the current linux partition and add new one and reinstall linux..

---


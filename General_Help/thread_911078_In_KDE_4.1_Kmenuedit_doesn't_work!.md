---
title: "In KDE 4.1 Kmenuedit doesn't work!"
date: 2008-09-05
forum: General Help
---

### Post by bad_boy_87 on 2008-09-05
Good morning,
my name's Leo, and I've a problem with Kubuntu 8.1, powered by KDE 4.1 . I can't modify my menu entries with the KDE Menu Editor (downloaded by Adept Manager). So I can't erase a broken Google link, or add Catalyst Control Center in Applications for example! The application (so appear) work, but when I save all, and close it, the Menu is the same! Maybe my version is wrong for KDE 4? It's the 0.7 but based on KDE 3.5.9, because I didn't find any versions for KDE4. Thank you very much to all, help me please! Bye!:confused:

---

### Post by Crafty Kisses on 2008-09-05
Try running it Terminal do you get any errors?

---

### Post by bad_boy_87 on 2008-09-05
Yep, I have to start it on terminal, by command: "sudo kmenuedit", it go, work, update the system configuration, but doesn't apply any "reals" changes! :mad:

---

### Post by bad_boy_87 on 2008-09-05
> **bad_boy_87 said:**
> Yep, I have to start it on terminal, by command: "sudo kmenuedit", it go, work, update the system configuration, but doesn't apply any "reals" changes! :mad:
Ops excuse me, it's true I remember that when I start it from terminal, and after working, I close it, it shows this:

Error: "/var/tmp/kdecache-badboy" is owned by uid 1000 instead of uid 0.
QImage::smoothScale: Image is a null image
ERROR: Communication problem with kmenuedit, it probably crashed.
badboy@badboy-laptop:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3600436

But the program, doesn't give any alarms or problems and Kwin doesn't appears!

---

### Post by bad_boy_87 on 2008-09-10
Nobody can help me? Exist a patch, a trick, something that fix this bug? :confused:

---

### Post by Ayuthia on 2008-09-10
> **bad_boy_87 said:**
> Nobody can help me? Exist a patch, a trick, something that fix this bug? :confused:

Did you try right-clicking on the K button (The application button or the start button as it is commonly known in Windows) and selecting Menu Editor?  That is how I have been editing the menu.

---

### Post by bad_boy_87 on 2008-09-11
Yes but if I click with right button on K Menu, I read this options:

Applications Launch Settings
Panel Settings
Add gadgets
Remove Application Launch

I'm using KDE 4.1! I knew too that in KDE 3 it's so! Thank you however...!

---

### Post by genericcitizen on 2008-09-12
Hi I seem to have I think the same problem with KDE4.1.1.

If I launch kmenuedit via terminal it launches kmenuedit 0.8 (the kwin version for kde4.1), however it does not actually allow me to edit or add icons.

If I launch kmenuedit with kdesudo or sudo seems to launch kmenuedit 0.7, for kde 3.5.x, which as reported by bad_boy87 does not effect the kickoff menu in 4.1.1.  This appears to be working correctly from what I've read on the kde forums.

The funny thing is I've not got kde 3.5.x installed, only 4.1.1 and gnome.

Given the little coverage of this I'm wondering if this ubuntu/kubuntu specific?

---

### Post by bad_boy_87 on 2008-09-12
Hi everybody,according to you could be possible install a program similar to "Alacarte" in Gnome for replace kmenuedit? Do exist one?

---

### Post by bad_boy_87 on 2008-09-12
Hi everybody,according to you could be possible install a program similar to "Alacarte" in Gnome for replace kmenuedit? Do exist one? If it could be ok, it's a possible (and partial) solution to the problem!:)

---

### Post by vussvillem on 2008-10-15
I can't change the K menu in KDE 3.5. I make the changes with kmenuedit and they just do not take effect.

---


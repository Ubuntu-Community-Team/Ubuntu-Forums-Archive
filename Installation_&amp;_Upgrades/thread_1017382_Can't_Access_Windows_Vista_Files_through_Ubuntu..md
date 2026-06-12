---
title: "Can't Access Windows Vista Files through Ubuntu."
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by running_with_scissors on 2008-12-21
Hi, I'm a relatively new user to Ubuntu.

I've installed Ubuntu 8.10 inside windows through the option on the CD.

However, I can't seem to be able to access my windows files. It just doesn't show up?

There is only one drive on the computer and around 60 GB is free.

Any ideas?

---

### Post by taurus on 2008-12-21
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```
Use it to configure your windows partition.

---

### Post by running_with_scissors on 2008-12-21
Thanks for responding so quickly.

I ran all those commands at the terminal.
And I saw the updates getting installed.

I still see Toshima System volume but when I open it, it has some system files, but none of my windows files (like videos, music etc)

---

### Post by running_with_scissors on 2008-12-21
Thanks for responding so quickly.

I ran all those commands at the terminal.
And I saw the updates getting installed.

I still see Toshima System volume but when I open it, it has some system files, but none of my windows files (like videos, music etc)

---

### Post by psycho5 on 2008-12-21
Are you sure you don't have your vidoes and music etc in a seperate partition? 

On another note, my friend did install ubuntu inside windows xp and he also couldn't access his xp files. I've personally never done that but I can tell you if you do the normal installation, you can access your entire disk no problems.

---

### Post by running_with_scissors on 2008-12-21
"Are you sure you don't have your vidoes and music etc in a seperate partition?" 

Yeah, that bit I'm sure about. This laptop came with a single C: DRIVE.

Interesting thing to note is that when I installed the demo version (again an option in the cd), I could access my hard drive. I could go to the drive->users and select the user and access data.

When I go to it again, I don't find users. Alternatively, there are lot fewer files and they seem to be system files.

I can access data through windows as usual though.

---

### Post by running_with_scissors on 2008-12-21
Okay, it's working now. Thanks a lot for your help.

---


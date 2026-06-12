---
title: "[SOLVED] Change terminal defualt directory from command line"
date: 2008-10-15
forum: General Help
---

### Post by chez17 on 2008-10-15
I want to assign different keyboard short cuts and while I want the terminal to open to my home folder, which it does now, I would like to have a command to open a terminal already in a specific folder. So I don't want to edit any user setting, I just want to do it by command line. I have played around with -e and -x and couldn't get them to work and the --help isn't much help. Can someone show me how to do this?

---

### Post by Sam on 2008-10-15
```
gnome-terminal --working-directory=[PATH]
```
Change [PATH] with the directory of your choice.

---


---
title: "Error when trying to update"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by jedchase on 2008-12-31
This past month, whenever I try to update, I receive an error saying something like use dpkg -a in the terminal because it cannot do it in the update program.  Then there is a line that says cache please report.


Sorry, I do not have the exact error, but it would not let me copy and paste.  I tried typing that in the terminal, then after several attempts to get in superuser mode, and it hangs everytime on ubuntu docs.

Help greatly appreciated.  Not as much concerned about help docs, but would like to make sure my security updates are current.  Thanks!!!

---

### Post by donkyhotay on 2008-12-31
> **jedchase said:**
> This past month, whenever I try to update, I receive an error saying something like use dpkg -a in the terminal because it cannot do it in the update program.  Then there is a line that says cache please report.


Sorry, I do not have the exact error, but it would not let me copy and paste.  I tried typing that in the terminal, then after several attempts to get in superuser mode, and it hangs everytime on ubuntu docs.

Help greatly appreciated.  Not as much concerned about help docs, but would like to make sure my security updates are current.  Thanks!!!

We really need the terminal output to know whats going on. Ctrl-c & ctrl-v usually doesn't work in some terminal programs. Try highlighting the text and then right-clicking to copy it into your clipboard then use right-click to paste into your web browser here so we can take a look at it for you.

---

### Post by ajgreeny on 2008-12-31
It may well be that all you need to do is open a terminal and run ```
sudo dpkg --configure -a
```Give it a try, it will not cause any problems even if it does not solve the difficulty you have at the moment.

---


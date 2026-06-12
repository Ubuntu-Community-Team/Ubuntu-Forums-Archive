---
title: "Modify a command from the bash shell history before using it again?"
date: 2008-08-16
forum: General Help
---

### Post by caljohnsmith on 2008-08-16
I suppose this is almost sort of a trivia question, but is there a way to pull up a previous command from the bash shell history and modify it before using it? Other than doing a copy and paste I mean. For instance, if I do:
```
history
```
And I see that command number 423 is:
```
423  cat /boot/grub/menu.lst 
```
So if I want to re-execute that command I could simply do:
```
!423
```
But what if I want to modify that command slightly before executing it? Is there an easy way of doing that? Just curious.

---

### Post by y-lee on 2008-08-16
May not be what you are looking for but I edit the history file in a word processor. Open nautilus and hit ctrl-H to show hidden files and look for .bash_history. Open it in gedit or whatever editor you like to use and edit. You will probably have to restart the terminal for the changes to take effect, tho i might be wrong.

---

### Post by olejorgen on 2008-08-16
Uh. press up (the arrow keys) of ctrl+p revious / ctrl+n ext if you use standard (emacs) bindings. or esc k/j if you use vi bindings

EDIT: Ah, I think I missunderstood what you wanted
EDIT2: If you use vi bindings you could do "esc 432k" maybe emacs have something similar

---

### Post by olejorgen on 2008-08-16
Or you could use zsh and do !423<tab>

---

### Post by y-lee on 2008-08-16
see also [Bash History]("http://www.gnu.org/software/bash/manual/html_node/Bash-History-Builtins.html"). The fc command mentioned there may help.

---


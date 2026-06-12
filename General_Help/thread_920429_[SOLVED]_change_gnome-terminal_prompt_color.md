---
title: "[SOLVED] change gnome-terminal prompt color"
date: 2008-09-15
forum: General Help
---

### Post by Promixa on 2008-09-15
I want gnome-terminal to display the prompt in green color. I looked in .bashrc and inserted the colored part in my .bashrc:

```
# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
xterm-color)
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
    ;;
*)
    PS1='${debian_chroot:+($debian_chroot)}**[COLOR="Red"]\e[32m[/COLOR]**\u@\h:\w\$**[COLOR="Red"]\e[0m[/COLOR]** '
    ;;
esac
```

OK, I was happy with that until i realized that when i enter a command that is longer than the terminal window, the command doesn't continue in the next line but stays on the same line (see picture below)

[IMG]http://img81.imageshack.us/img81/8361/term1dd9.png[/IMG]

Can anybody help me to fix this?

---

### Post by hwttdz on 2008-09-15
Yeah you're going to at least want \[ before you start your color codes and \] after you're done.  I believe this is interpreted as make this non printing, and it is one of your problems.  So try:

PS1='${debian_chroot:+($debian_chroot)}\[\e[32m\]\u@\h:\w\$\[\e[0m\] '

---

### Post by Promixa on 2008-09-15
thanks, that really solved my problem :-)

---


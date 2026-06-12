---
title: "bashrc vs. bash_profile"
date: 2008-10-08
forum: General Help
---

### Post by sulekha on 2008-10-08
hi all,

can any one explain the subtle difference between bashrc and .bash_profile files ?

---

### Post by bogdan.veringioiu on 2008-10-08
Hi.

I got these lines from bash manual.
~/.bash_profile
The personal initialization file, executed for login shells
~/.bashrc
The individual per-interactive-shell startup file

To be more clear: 
.bashrc will be executed everytime you open the terminal from within Gnome, as you are not making a login.

.bash_profile is executed after login to a terminal. In the case of desktop systems, if I am not mistaking, this file is executed after the graphical login, just once. If you were to boot without graphical mode, after you were presented with bash login prompt, this file would be executed after successful login.

Regards.

Bogdan

---

### Post by geirha on 2008-10-08
No, opening a terminal in gnome will also give you a login shell. .bash_profile is read when you open a terminal, log in at the console or specifically start a loginshell with ```
bash --login
```

.bashrc is read for non-login shells. Typically that means when you run bash-scripts; it spawns a new bash process to run the script, but it only reads .bashrc.

The .bash_profile provided to you with ubuntu, will run .bashrc too, so .bashrc is "always" read.

---

### Post by bogdan.veringioiu on 2008-10-08
> **geirha said:**
> No, opening a terminal in gnome will also give you a login shell. .bash_profile is read when you open a terminal, log in at the console or specifically start a loginshell with ```
bash --login
```

.bashrc is read for non-login shells. Typically that means when you run bash-scripts; it spawns a new bash process to run the script, but it only reads .bashrc.

The .bash_profile provided to you with ubuntu, will run .bashrc too, so .bashrc is "always" read.

I am not so sure about this.
You can make a simple test, add an echo in .bash_profile, and .bashrc.

While the echo in .bashrc will always be displayed when you open gnome-terminal, the one in .bash_profile will not appear, because opening gnome-terminal is not a login shell...

Bogdan

---

### Post by kpkeerthi on 2008-10-08
The commands in .bash_profile will be run every time the user logs in. 
The commands in .bashrc will be run everytime you open bash shell (the terminal). .bash_profile will not be run in this case.

* Usually .bash_profile internally invokes .bashrc. So .bashrc will also be run once upon login.

---

### Post by geirha on 2008-10-08
> **bogdan.veringioiu said:**
> I am not so sure about this.
You can make a simple test, add an echo in .bash_profile, and .bashrc.

While the echo in .bashrc will always be displayed when you open gnome-terminal, the one in .bash_profile will not appear, because opening gnome-terminal is not a login shell...

Bogdan

That's odd, I just did the same test, and it prints both from _profile and rc for me. Perhaps it's an option in gnome-terminal.

---


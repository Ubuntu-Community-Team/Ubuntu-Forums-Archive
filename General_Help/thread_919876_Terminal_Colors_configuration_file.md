---
title: "Terminal Colors configuration file?"
date: 2008-09-14
forum: General Help
---

### Post by syko21 on 2008-09-14
I installed linux mint originally for the artwork and I later disable their repos and switched to 8.04.1. In linux mint the terminal has a color scheme where the prompt is green and switches to red when root. Also the ls command colorizes directories and other things. Does anyone know where the configuration file is for this is stored?

---

### Post by FuturePilot on 2008-09-15
It's probably set in the .bashrc file. It's hidden so if you open your Home directory and press Ctrl+H you can see your hidden files.

---

### Post by syko21 on 2008-09-15
I found the file, it was /etc/bash.bashrc or something along those lines (I'm at work and away from my linux box). I tried that file before but I didnt know a restart was required for the changes to take affect which is why it slipped under the radar. Thanks anyway though.

---

### Post by Promixa on 2008-09-15
You do not have to restart! Either you start a new instance of gnome-terminal, xterm,... or you source the configuration file (force the program to reread its configuration file) with source .bashrc

---

### Post by syko21 on 2008-09-15
> **Promixa said:**
> You do not have to restart! Either you start a new instance of gnome-terminal, xterm,... or you source the configuration file (force the program to reread its configuration file) with source .bashrc

Thanks for the heads up. But starting a new xterm or gnome-terminal session kept the old configuration so I thought I should do a restart to be thorough and that's what did the trick.

---

### Post by billgoldberg on 2008-09-15
I recently made an article about customizing the terminal prompt.

This is mine now (on the laptop):
[IMG]http://linuxowns.files.wordpress.com/2008/09/bash.png?w=500&h=154[/IMG]

The guide is here:
[http://linuxowns.wordpress.com/2008/09/05/custom-terminal-prompt/](http://linuxowns.wordpress.com/2008/09/05/custom-terminal-prompt/)

---

### Post by syko21 on 2008-09-15
> **billgoldberg said:**
> I recently made an article about customizing the terminal prompt.

This is mine now (on the laptop):
[IMG]http://linuxowns.files.wordpress.com/2008/09/bash.png?w=500&h=154[/IMG]

The guide is here:
[http://linuxowns.wordpress.com/2008/09/05/custom-terminal-prompt/](http://linuxowns.wordpress.com/2008/09/05/custom-terminal-prompt/)


A rather useful article, thanks!

---


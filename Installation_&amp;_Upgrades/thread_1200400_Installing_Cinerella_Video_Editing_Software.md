---
title: "Installing Cinerella Video Editing Software"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by ZombiesNTea on 2009-06-30
Hi... I went to download Cinerella here: [http://www.heroinewarrior.com/cinelerra.php#download](http://www.heroinewarrior.com/cinelerra.php#download)

But all of the downloads are tar.bz2 files... and I have absolutely no idea how to install it.

---

### Post by Arup on 2009-06-30
Open terminal and paste echo deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-jaunty main | sudo tee /etc/apt/sources.list.d/akirad.list && wget -q [http://akirad.cinelerra.org/dists/akirad.key](http://akirad.cinelerra.org/dists/akirad.key) -O- | sudo apt-key add - && sudo apt-get update

Type your password when asked. Then go to Synaptic and install Cinelerra of your choice, for multi core use the SMP version.

[http://cinelerra.org/getting_cinelerra.php](http://cinelerra.org/getting_cinelerra.php)

---

### Post by ZombiesNTea on 2009-07-24
I did that stuff in the terminal, and now this message pops up when I go to the "Add/Remove Programs":

[I]
**Failed to check for installed and available applications**

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.[/I]



I did the "sudo apt..." stuff in the terminal, it didn't work.

How do I fix this?

---

### Post by ZombiesNTea on 2009-07-24
I got it.  S'all good.

---

### Post by ZombiesNTea on 2009-07-24
So I do this... it isn't in synaptic, neither is "akirad".  It read all the "package lists" and whatnot.

Did I do something wrong?

---

### Post by Gormanilius on 2009-09-23
I am having issues at this point to. I can find it in synaptic, but it states something about other packages having unresolvable dependancies, at which point my knowledge fails me.

I am by no means that great with linux(im a newb), but how am I to resolve this?

---


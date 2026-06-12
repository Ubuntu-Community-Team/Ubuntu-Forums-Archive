---
title: "Installation Problem - Gnome does not load"
date: 2005-01-09
forum: Installation &amp; Upgrades
---

### Post by mikemuffels@hotmail.com on 2005-01-09
Hey, I'm completely new to Linux. I installed Ubuntu 4.10 seemingly without problems on my old i-series Thinkpad. From the websites it says I am supposed to end up with a graphical Gnome Login Screen. I get a text Login screen which lets me login in just fine but I can't figure out how to start Gnome. I thought Gnome was supposed to load automatically, am I wrong?

At the moment I have Win98 on the first partition and Ubuntu on the second and third. I don't know if this would create any problems. I have tried installing it twice now.

Thanks in advance.

---

### Post by Dissonance on 2005-01-09
[QUOTE=mikemuffels@hotmail.com]Hey, I'm completely new to Linux. I installed Ubuntu 4.10 seemingly without problems on my old i-series Thinkpad. From the websites it says I am supposed to end up with a graphical Gnome Login Screen. I get a text Login screen which lets me login in just fine but I can't figure out how to start Gnome. I thought Gnome was supposed to load automatically, am I wrong?

At the moment I have Win98 on the first partition and Ubuntu on the second and third. I don't know if this would create any problems. I have tried installing it twice now.

Thanks in advance.[/QUOTE]
 IIRC, I think you'll need to type a command to start it.

type: "startx" 

...without the quotes...

---

### Post by mikemuffels@hotmail.com on 2005-01-09
great!
I have been up and down the ubuntu website and this forum but haven't been able to find that useful bit of info. where did you find it? I know you have been at this less time then me from your other post.

---

### Post by Dissonance on 2005-01-09
[QUOTE=mikemuffels@hotmail.com]great!
I have been up and down the ubuntu website and this forum but haven't been able to find that useful bit of info. where did you find it? I know you have been at this less time then me from your other post.[/QUOTE]

I've used a few other Linux distro's before this one.  I gained that little bit of info from mandrake's board ([www.mandrakeusers.org](www.mandrakeusers.org))  Glad to have been of help.   :smile:

---

### Post by mikemuffels@hotmail.com on 2005-01-09
thanks for the help. startx wasn't the complete solution but it was a good lead. startx didn't work, which made me have to look up what startx was and what it was supposed to do. after a bit of searching on the site you recommended and google and then back here i found the solution under the following thread.

hoary 2005-01-09 incomplete install

it seems that Ubuntu didn't completely install from the CD. I think X was missing. So i used the following two commands in turn

sudo apt-get dist-upgrade

sudo apt-get install ubuntu-desktop

after a promising looking install I was brought back to the command prompt.
I then typed "startx" et voila!

Well I learned something new today. Time for bed!
Cheers

---


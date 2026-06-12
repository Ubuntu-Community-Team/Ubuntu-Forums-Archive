---
title: "vi colours unreadable"
date: 2005-11-18
forum: General Help
---

### Post by pickarooney on 2005-11-18
Is there a way of tweaking the colours used by vi(m)? At the moment they're all navy-blue on black and dark-green on black and are barely readable.

---

### Post by Bjørn on 2005-11-18
You're probably looking for adapting vim for use on a dark background, which you can do as follows "*set background=dark*". Something you probably want to put in your ~/.vimrc if your terminal is black by default. To get back to light background settings, use "*set background=light*".

---

### Post by suRoot on 2005-11-18
These colors are generated through dircolors in your .bashrc file.  You can tweak them to your liking - here's a pretty good how-to:

[http://ubuntuforums.org/showthread.php?t=41538&highlight=bashrc+directory+colors]("http://ubuntuforums.org/showthread.php?t=41538&highlight=bashrc+directory+colors")

---

### Post by pickarooney on 2005-11-18
Great, it looks much better now :)

---


---
title: "Change repo mirros via command line"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by plr4ever on 2009-10-06
I recently installed 9.10-server on a laptop i have lying around, and i noticed that the default repository server was still set to ubuntu.org. 
Since i am a student at Georgia Tech, i wanted to switch the mirrors to the gtlib.gatech.edu site. However, without having a gui, the only way i can think to change all of the mirrors is to go through the sources.list file and edit it by hand. Is anyone aware of a script/cli tool that allows you to change ALL of the mirrors at once?

Thanks!

---

### Post by kanikilu on 2009-10-06
I don't know of something already out there, but could you not just use sed to replace the current mirror with something else? Similar to how this page explains how to uncomment lines with sed:

[https://help.ubuntu.com/community/Repositories/CommandLine#Enabling%20Repositories%20with%20a%20%28non-interactive%29%20Script](https://help.ubuntu.com/community/Repositories/CommandLine#Enabling%20Repositories%20with%20a%20%28non-interactive%29%20Script)

Here's a similar thread with some other suggestions:

[http://ubuntuforums.org/showthread.php?t=226299](http://ubuntuforums.org/showthread.php?t=226299)

---


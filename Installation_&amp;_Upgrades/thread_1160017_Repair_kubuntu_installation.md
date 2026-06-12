---
title: "Repair kubuntu installation"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by thewhat on 2009-05-15
I mistakenly deleted some required files/dependencies in kubuntu while trying to uninstall a program. I had also run system sweeper to clear out what I mistakenly thought were un-needed files. As a result my system will not load the gui. I had previously setup the pc to dual boot intrepid ibex and xp. It seems that the actual base installation is still present but some key files are missing because the system will only boot to root. I have tried to repair the installation from my ubuntu disk, I have tried running a live ubuntu session to see if I could figure out the problem. One of the online suggestions was to run the command "sudo apt-get install ubuntu-desktop" but that doesn't work: it says something about unmet dependencies (I think). I think the system tries to download files from the online repositories but can't connect as I use a password protected wireless network. I would rather not delete the previous installation and would appreciate some help .

Thanks

---

### Post by Lampi on 2009-05-15
I'd backup your data first - this could get messy and sure you don't want to risk anything.

Then I'd suggest you have a look at

/var/log/dpkg
/var/log/aptitude
/var/log/apt/term.log

These logs should cover the changes you made - you better open them in your Ibex installation and use an editor.

Another approach could be checking the syslog what it is complaining about.

from terminal you can login and try 'startx' - it will probably hang as well but then again: it might give you a hint what is missing.

Honestly I wouldn't invest to much time and consider a fresh install anyway.

---

### Post by thewhat on 2009-05-15
I fortunately have almost every important file backed up. There were some emusic and amazon mp3 purchases from earlier this week which are located in the default ubuntu music folder. How can I get to said folder from root and copy them to an external drive? I'm not familiar withperforming basic  file operations such as copy from the terminal/root.

---

### Post by Lampi on 2009-05-15
@thewhat: if it's just about a few files you can copy them from terminal using midnight commander ('sudo apt-get install mc') - tool is easy to understand, you'll get the trick how it works fast.

I really recommend reinstallation instead of trying to fix a possible mess with your current installation all on your own.

---


---
title: "Unable to locate programs"
date: 2008-08-17
forum: General Help
---

### Post by davethewave83 on 2008-08-17
Many times I will install a program, but it does not show up in the Applications/Places or System menu, and it does not tell me how to start it. So I was wondering if there is a universal way to start programs or find the ones that do this? For example, I installed emifreq-applet but when I type emifreq-applet in the command prompt it says bash: emifreq-applet: command not found
and I type gnome-applets and I get bash: gnome-applets: command not found
so I have no way to run these programs after installation.. the best I can do is uninstall them and forget about it :confused:

a similar thing happens with cpufreqd - I install it, type cpufreqd and nothing happens, no errors or anything. There is no GUI anywhere in the menus to configure it so I have to just uninstall it and try to find one that actually works. IF anyone can give me pointers on how to work with ambiguous programs like these please let me know. 

Thanks! :guitar:

---

### Post by tiggsy on 2008-08-17
Yes, im having the same the same problem with freemind. I installed it, but cant find it. Why doesn't synaptic tell you where it is, so you can use it?

---

### Post by mb_webguy on 2008-08-17
All programs in a Linux system are installed to either the /usr directory or the /usr/local directory.  Executables are in the bin subdirectory (or sbin for programs intended to be run as root), and data files are in the share subdirectory.  So if you install a program but it doesn't show up in the Gnome menu and you don't know what the command is to start it in the terminal, you can open the terminal and type "ls /usr/bin" and "ls /usr/local/bin" and look for a command that looks like your program.  

Also, if you installed the application from the repositories, you can find out the name of the executable by opening Symantic, finding the package, right-clicking it, selecting Properties->Installed Files, and looking for a file installed to /usr/bin or /usr/local/bin.

---

### Post by rossjman1 on 2008-08-17
Applets wont be in the application menu. To add an applet right click on the gnome-panel and add applet. The newly installed applet should be in that list.

---

### Post by davethewave83 on 2008-08-17
Thanks for the info :)

---

### Post by tiggsy on 2008-08-18
Thanks! I found what I was looking for. It wouldn't work, but that's ok. At least I found it!

---


---
title: "How to use Synaptic Package Manager?"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by KinaU on 2009-08-07
I've been trying to get rid of several applications I don't need anymore (internet browsers, for example) and it tells me to use the synaptic package manager. I see all the things on the left side, but I have no idea where to find the browsers?

How do I use the Synaptic Package Manager to remove apps? :(

---

### Post by wojox on 2009-08-07
Click the Status button on the left bottom and pick installed. That will narrow your search down. You could also use the search bar.

---

### Post by drs305 on 2009-08-07
It may be easier for you to find them from the Main Menu, then "Add Remove", Internet. They are probably listed there by the name you are familiar with.

For Synaptic, you need to know the package name. First, click on Status in the left pane and make sure you have Installed selected. On the right, find the application by it's package name, highlight and right click, and mark for removal or complete removal, then Apply.

The problem may come in knowing what the application is called by the system. If you aren't sure and the application is running, you can type "ps -u *yourusername*" and it will show you all the apps currently running *under your username*. "ps aux" shows all running processes but it can be a bit much. For a GUI, you can go to System, Administration, System Monitor and look at the Processes tab to see what is running. Get the application process name and go back to Synaptic.

---

### Post by running_rabbit07 on 2009-08-07
If you want more precise help you can post the names of the programs you want uninstalled. There is a risk that if you were to uninstall Firefox it would also uninstall xulrunner which you need to keep. Basically some of the program files are used by other programs and can cause issues. 

I once uninstalled Bluetooth and it really gave me hell.

---

### Post by snowpine on 2009-08-07
If it's a program you installed, usually no problem to remove it, you may find Add/Remove Programs is easiest.

If it's a program that came with ubuntu, be very careful... removing one thing might remove other things. Better to keep it and just not use it. :)

---

### Post by KinaU on 2009-08-09
> **drs305 said:**
> It may be easier for you to find them from the Main Menu, then "Add Remove", Internet. They are probably listed there by the name you are familiar with.

For Synaptic, you need to know the package name. First, click on Status in the left pane and make sure you have Installed selected. On the right, find the application by it's package name, highlight and right click, and mark for removal or complete removal, then Apply.

The problem may come in knowing what the application is called by the system. If you aren't sure and the application is running, you can type "ps -u *yourusername*" and it will show you all the apps currently running *under your username*. "ps aux" shows all running processes but it can be a bit much. For a GUI, you can go to System, Administration, System Monitor and look at the Processes tab to see what is running. Get the application process name and go back to Synaptic.

Thanks a lot. It turned out to be so easy. :D

---


---
title: "Gnome, xfce, and kde"
date: 2005-11-08
forum: General Help
---

### Post by eyebrowman92 on 2005-11-08
after i upgraded to breezy i found gnome wasnt to well..me. i decided to install the xfce4 desktop and after that decided to try the kde desktop.  after installing these my computer started to slow down trmendously.  i couldnt find out how to get rid of kde and xfce so i was forced to reinstall and upgrade back to breezy allll over again. does anyone know an easier way?

---

### Post by KingBahamut on 2005-11-08
sudo apt-get remove xubuntu-desktop 
sudo apt-get remove kubuntu-desktop 

=)

---

### Post by Miguel on 2005-11-08
Will that remove xubuntu-desktop and kubuntu-desktop's dependencies? I would suppose those commands would only remove those dummy packages.

---

### Post by lerrup on 2005-11-08
Wouldn't it be better to find out what the problem is?  Does is happen in Gnome?  The installation of these 2 shouldn't slow down the computer like that unless you have visual effects running with no 3D accleration.  

Why not run ksysguard (or equivalent) and see if there is anything slowing it down?

---

### Post by kalin on 2005-11-08
Synaptic keeps a history of what you did with it. If you used the "Add Application" tool or Synaptic itself you will find the list of newly installed packages logged under the date/time you installed KDE/Xfce.

---

### Post by SickTwist on 2005-11-08
[QUOTE=Miguel]Will that remove xubuntu-desktop and kubuntu-desktop's dependencies? I would suppose those commands would only remove those dummy packages.[/QUOTE]

You're absolutely right-- it would only remove the meta-packages. However, you could look at what xubuntu-desktop and kubuntu-desktop depend on to remove the package by hand if you really want to do that.

Although, like lerrup said, just having the packages installed should not effect performance (unless it is a service that automatically starts when the computer boots like ssh, cups, etc.)

In situations like these you can use a GUI tool (like gnome-system-monitor) or a command line tool (like top) to see what processes are running and how much memory/CPU usage each is consuming.

---

### Post by eyebrowman92 on 2005-11-08
i tried removing them using sudo and it didnt do anything. it didnt even remove the packages.  and yes it slows down when its in gnome or any othr of the desktops.

---


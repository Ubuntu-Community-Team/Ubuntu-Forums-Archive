---
title: "Help please."
date: 2008-08-14
forum: Hardware
---

### Post by mirchichamu on 2008-08-14
I installed Xubuntu with usb mouse attached in my laptop. Now when I remove usb mouse laptop freezes both in Gnome and Xfce. Please help how to resolve this. I shall be thankful.

---

### Post by mirchichamu on 2008-08-15
Hi! Nobody there to help solve my problem?

---

### Post by mirchichamu on 2008-08-15
i am waiting for help

---

### Post by tamoneya on 2008-08-15
first of all, please do not bump a thread for 24 hours.  It spams the forums.  Also I find that you typically get a better response to your thread if you include a more descriptive title like: "unplugging mouse freezes gnome/XFCE".

Now on to your problem.  When you unplug your mouse is it possible to do a restart of X (hit ctrl-alt-backspace).  Also is it possible for you to get to tty1.  Hit (ctrl-alt-F1).  Then login and run the following command: ```
dmesg | tail > ~/dmesg.txt
```.

Then restart the computer and post the file ~/dmesg.txt to the forum.

---

### Post by fiddler616 on 2008-08-15
> **tamoneya said:**
> first of all, please do not bump a thread for 24 hours.  It spams the forums.  Also I find that you typically get a better response to your thread if you include a more descriptive title like: "unplugging mouse freezes gnome/XFCE".

Amen.

---

### Post by mirchichamu on 2008-08-15
> **tamoneya said:**
> first of all, please do not bump a thread for 24 hours.  It spams the forums.  Also I find that you typically get a better response to your thread if you include a more descriptive title like: "unplugging mouse freezes gnome/XFCE".

Now on to your problem.  When you unplug your mouse is it possible to do a restart of X (hit ctrl-alt-backspace).  Also is it possible for you to get to tty1.  Hit (ctrl-alt-F1).  Then login and run the following command: ```
dmesg | tail > ~/dmesg.txt
```.

Then restart the computer and post the file ~/dmesg.txt to the forum.

Thanks tamoneya for your support.
Once I succeded by hitting alt+ctrl+F1. I got a screen to log in to tty1. When I try to log in by my name, it says you last logged in.........
Alt+Ctrl+Backspace not working.
When I disconnect my usb mouse, It freezes completely.

---

### Post by tamoneya on 2008-08-15
okay so disconnect the mouse then go to tty1 and run the command in the first post.  It may help to write the command down since you wont be able to view this thread when you are in tty1.

---

### Post by mirchichamu on 2008-08-15
> **tamoneya said:**
> okay so disconnect the mouse then go to tty1 and run the command in the first post.  It may help to write the command down since you wont be able to view this thread when you are in tty1.

Thanks tamoneya once again.
I tried with mouse disconnected but as I told that my laptop completely stop working with mouse disconnected. With mouse connected when I hit alt+ ctrl+F1, I typed the above command and I got a command like the one in this terminal window. A screenshot is attached.

---

### Post by tamoneya on 2008-08-15
okay now please boot ubuntu and post ~/dmesg.txt 

The idea of writting to dmesg.txt was that if things locked up we could still get the data.

---

### Post by mirchichamu on 2008-08-16
Thanks once again.
When in terminal, I put the above command, I get a reply that permission is denied.

---

### Post by adieb on 2008-08-16
Are you sure you are typing "~" in front of /mesg.txt? That means /home/$USERNAME.
In your home-folder you should have write access.

---

### Post by mirchichamu on 2008-08-16
Thanks adieb for your concern.
Yes. I am writing ~/dmesg.txt

---

### Post by mirchichamu on 2008-08-16
I am having one dmesg file in my home folder which is as follows. I don't know if it is the same what you want?
"[  137.133162] [drm] Setting GART location based on new memory map
[  137.133181] [drm] Loading R300 Microcode
[  137.133237] [drm] writeback test succeeded in 1 usecs
[  164.516549] NET: Registered protocol family 10
[  164.517510] lo: Disabled Privacy Extensions
[  164.518825] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  182.556304] eth1: no IPv6 routers present
[   67.274611] NET: Registered protocol family 17
[   67.731873] ieee80211_crypt: registered algorithm 'WEP'
[  216.362642] eth1: no IPv6 routers present"

---

### Post by linux_tech on 2008-08-16
If you receive message "permission denied" you can use sudo before command
ie.  sudo modprobe psmouse

---

### Post by mirchichamu on 2008-08-16
> **linux_tech said:**
> If you receive message "permission denied" you can use sudo before command
ie. sudo dmesg

Thanks linux_tech for your support.
When I put sudo, then I get "command not found"

---


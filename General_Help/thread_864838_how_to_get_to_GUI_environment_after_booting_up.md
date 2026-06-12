---
title: "how to get to GUI environment after booting up?"
date: 2008-07-20
forum: General Help
---

### Post by serendipity1276 on 2008-07-20
Hi,

I just installed ubuntu 8.04, the server version for 64 bits.  I downloaded the software online, and burned the ISO file onto a CD.

After installing the OS, my PC reboots.  Then, I see a shell.

What do I need to do so that after booting up, it goes into a graphical user interface?  (For example, on Solaris 10, after booting up, I would get a log-in screen.  Then, after logging in, then, I would go into a CDE graphical environment.)

How do I do something like this on ubuntu?  Thanks.

---

### Post by cdtech on 2008-07-20
> I just installed ubuntu 8.04, the server version for 64 bits. I downloaded the software online, and burned the ISO file onto a CD.

You installed the server version which has no GUI......

You would have to install a graphical desktop manager for your server.

---

### Post by bogdanbiv on 2008-07-20
Install a package manager: 
sudo apt-get install aptitude

It has ncurses interface (GUI made in ASCII painting), it'll have to do for now.
Now "sudo aptitude"
In aptitude you access the menu using CTRL + T and then use the arrows.
Navigate through the menu until you find an option to search for packages. 

Then install any GUI environment you want - I suppose you know how to do that, I'll leave it here.
UPDATE: I have Ubuntu JeOS which is a Server edition, I hope I can help further should you run into problems

---

### Post by serendipity1276 on 2008-07-20
OK, that makes sense.  So I installed ubuntu server without a GUI interface.

This is where I downloaded mine:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)


Can someone post the link to where I can download the one WITH a GUI interface?

---

### Post by bogdanbiv on 2008-07-20
There is some misunderstanding here:
I don't think there is *any* server variant with GUI. That is by design.
All server variants I have seen are 32bit and 64bit (I have both) .

I presume that the Ubuntu team assumes that if you need a server you are able enough to install a GUI yourself.

Not including the GUI on the default install *does* have some logic: installing GUI introduces some overhead on the server that could otherwise be used to provide useful services (like serve more HTTP requests). Also GUIs need security updates more often, which is something most people want to do as seldom as possible.

> **serendipity1276 said:**
> OK, that makes sense.  So I installed ubuntu server without a GUI interface.

This is where I downloaded mine:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)


Can someone post the link to where I can download the one WITH a GUI interface?


On the other hand, you needn't be afraid of the CLI.
If you take it one step at a time and post back the results you'll get your GUI pretty quickly. Remember all the members of the forum are trying to help.

UPDATE:
At your prompt, after you type in your name and password and you are logged in, you should see something similar to this:
```
yourUserName@computerName:~$
```

type this:
```
sudo apt-get install kubuntu-desktop
```
Expect your computer to start downloading a lot. (the whole KDE environment). Oh and your server does have a working internet connection, right?

If you don't have a second computer where you can browse the forum while installing/using the Ubuntu server then write it down on a piece of paper.

---

### Post by hyper_ch on 2008-07-20
why do you want a gui on a server?

---

### Post by p_quarles on 2008-07-20
If you want to alter your installation to the standard Ubuntu setup, you can run this from the shell:
```
sudo apt-get install ubuntu-desktop
```
This will download quite a bit of stuff, but not nearly as much as a fresh installation.

Also, bogdanbiv: aptitude is a standard part of any Ubuntu edition.

---

### Post by JagDragon on 2008-07-20
To get a GUI (restart needed)
```

sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo reboot

```

ubuntu-desktop is a collection of packages (gnome, nautilus, firefox) that is Ubuntu's desktop environment.

EDIT: Whoops, someone beat me to it. :mrgreen:

---

### Post by p_quarles on 2008-07-20
> **JagDragon said:**
> To get a GUI (restart needed)
No, no it's not. 
```
sudo /etc/init.d/gdm start
```
will load the display manager. It will start automatically on future boots.

---

### Post by zipperback on 2008-07-20
The server version doesn't have a GUI interface by default.

However, don't let that bother you, all you need to do is install the required desktop manager package and you'll have a standard Ubuntu Linux system.

To install the Gnome desktop use:
sudo apt-get install ubuntu-desktop

To install the KDE desktop use:
sudo apt-get kubuntu-desktop

To install the XFCE desktop use:
sudo apt-get install xubuntu-desktop

Once you install that, you will have a gui desktop.

- zipperback
:popcorn:

---


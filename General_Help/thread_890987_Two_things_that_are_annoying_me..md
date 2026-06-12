---
title: "Two things that are annoying me."
date: 2008-08-15
forum: General Help
---

### Post by Mashy on 2008-08-15
Ok, so I'm loving Ubuntu (hardy), but so far there are only two things that are annoying me slightly. There are probably things similar to these, and if there are, or any downloads that can do something like this, then please say.

First off is the lack of ctrl+alt+del task manager from windows. I used to use it alot, and it's not in ubuntu.

Second are the icons next to the clock, in the bottom right hand corner of windows. These are invaluable to me to keep track of what programs are still running, and for some programs instead of closing they just minimise to this tray.

So are there ways in Ubuntu to make things similar/the same as these?

Thanks.

---

### Post by Too Late on 2008-08-15
The application, which you would like to start with Ctrl+Alt+Del, is called gnome-system-monitor. (You can also find that from System -> Administration -> System Monitor.) There are several ways to do a global keyboard shorcut:
[http://ubuntuforums.org/showthread.php?t=79560](http://ubuntuforums.org/showthread.php?t=79560)

I always put that same Ctrl+Alt+Del shortcut after a new installation. I think it should be there by default.

---

### Post by Morty007 on 2008-08-15
Ubuntu has everything windows has (except the crashes) and more. 

To your 1st annoyance, simply add to panel the task manager (ubuntu calls it something else, I forget). Then just click it once to see all of your proccesses. 

As for your icons, I'm not sure what you are saying. You might also want to do a forum search before asking. Welcome to Ubuntu.

---

### Post by mb_webguy on 2008-08-15
> **Mashy said:**
> First off is the lack of ctrl+alt+del task manager from windows. I used to use it alot, and it's not in ubuntu.
As others have said, you're referring to the System Monitor applet.  You can add it to a panel (i.e. menu bar) by right-clicking on the panel and selecting "Add to panel", and then picking System Monitor.  Follow the link Too Late posted to see how to set up a global shortcut to open it with Ctrl-Alt-Delete.
> **Mashy said:**
> Second are the icons next to the clock, in the bottom right hand corner of windows. These are invaluable to me to keep track of what programs are still running, and for some programs instead of closing they just minimise to this tray.
That would be the System Tray, which in Ubuntu would be the Notification Area applet, which should already be in the upper-right corner if you're using Ubuntu (rather than Kubuntu, in which most of the information in this thread will be wrong).  Some programs, such as Amarok and Deluge, will minimize to the Notification Area, while others won't.  You can, however, install a program called AllTray that allows you to minimize any application to the Notification Area. To install AllTray, follow this instructions on [this page]("http://asher256-repository.tuxfamily.org/index.php?page=faq&lang=en") to add a repository to your sources, then type "sudo apt-get install alltray" in the terminal.

---

### Post by Mashy on 2008-08-16
> **mb_webguy said:**
> As others have said, you're referring to the System Monitor applet.  You can add it to a panel (i.e. menu bar) by right-clicking on the panel and selecting "Add to panel", and then picking System Monitor.  Follow the link Too Late posted to see how to set up a global shortcut to open it with Ctrl-Alt-Delete.

That would be the System Tray, which in Ubuntu would be the Notification Area applet, which should already be in the upper-right corner if you're using Ubuntu (rather than Kubuntu, in which most of the information in this thread will be wrong).  Some programs, such as Amarok and Deluge, will minimize to the Notification Area, while others won't.  You can, however, install a program called AllTray that allows you to minimize any application to the Notification Area. To install AllTray, follow this instructions on [this page]("http://asher256-repository.tuxfamily.org/index.php?page=faq&lang=en") to add a repository to your sources, then type "sudo apt-get install alltray" in the terminal.

Hmm, yeah, I had a feeling that was where they should be going, but wasn't sure. 
When I minimise things that should go to the tray, such as amarok or emesene, they don't and just disappear off of my desktop.

---

### Post by bingoUV on 2008-08-16
Have you added "Notification Area" applet to your panel?

Right click on panel, Add to panel, Notification Area, Add.

---

### Post by Mashy on 2008-08-16
> **bingoUV said:**
> Have you added "Notification Area" applet to your panel?

Right click on panel, Add to panel, Notification Area, Add.

Ah, thank you very much. 
I think that was there when I first installed ubuntu, but for some reason it's been missing for a while. *hits self*.

Yeah, many thanks everyone!

---


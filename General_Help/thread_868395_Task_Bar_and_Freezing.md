---
title: "Task Bar and Freezing"
date: 2008-07-23
forum: General Help
---

### Post by pelicanghost on 2008-07-23
Computer has worked since the last time I restarted five days ago, for a kernel update.  

I restarted again, just so I could play games on my Windows Partition, got bored, and rebooted back into Linux.  

I logged in. my desktop came up.  I tried clicking on the Firefox icon on the taskbar (I have one on the top for applications, one on the bottom for window management.  The standard setup), and it didn't respond.  The only thing that does work is CTRL-ALT-Backspace, which takes me back to login, I can login again.  Same thing happens, even when I reboot.

Nothing responds, the only action I can complete is to make translucent boxes by clicking and dragging the mouse.  Right-clicking results in freezing the computer.  Cant access the terminal.  Mouse works so I don't think it's an X server problem.

I believe its a GNOME problem, but I cant imagine what could affect it since the last time I have rebooted.  The only thing I can think of is libgtk1.2, which I installed for Enemy Territory.

It's Hardy Heron, not sure on the kernel, but I updated it recently.  Its on AMD 64, but I'm running the 32-bit.  Nvidia GEforce 8800, not sure on the driver.  Is there a way to repair from the login window, as its is the only time I can use the computer and what is causing the problem.

---

### Post by pelicanghost on 2008-07-23
bump

---

### Post by daniel3ub on 2008-10-13
> **pelicanghost said:**
>  I tried clicking on the Firefox icon on the taskbar (I have one on the top for applications, one on the bottom for window management.  The standard setup), and it didn't respond.  The only thing that does work is CTRL-ALT-Backspace, which takes me back to login, I can login again.  Same thing happens, even when I reboot.

Nothing responds, the only action I can complete is to make translucent boxes by clicking and dragging the mouse.  Right-clicking results in freezing the computer.  Cant access the terminal.  Mouse works so I don't think it's an X server problem.



I am having an issue like this, and I've seen this in the forums a while ago, without solution.
My problem is that the taskbars freeze randomly. I can use alt+tab to switch open apps, but cannot use anything on the taskbars. The clock freezes, too. Anyway, the right-click issue is not happening here.

I've noted that some java programs can cause this, and Grsync seems to cause it sometimes too.

Is there a way to restart the taskbars without ctrl+alt+backspace? It's annoying, because ctrl+alt+backspace closes firefox and all other graphical apps...

Anyone?

---

### Post by blath on 2008-10-13
Salutations,
Recently I had been experiencing similar problems. And about 2 hours ago it got really bad, and while searching for a solution I found this thread.

Anyway.. I found my solution, so hopefully it will at the very least help both or one of you.

From the top menu.. 
**System > Administration > System Monitor**

I discovered that a program called gtk-gnash was hogging a LOT of memory. Hundred plus meg in one instance. I forgot the total qty but it was pretty high. When I did a search to see what this program was.. I found  this thread and learned it was my system's flash movie player that I installed awhile back.
[http://ubuntuforums.org/showthread.php?t=676870](http://ubuntuforums.org/showthread.php?t=676870)

and followed the suggestion of removing it by going into Terminal 

From top menu..
**Applications > Accessories > Terminal**

And typing.. 

**sudo aptitude purge gnash**

and it solved my slow down issues. :) Huzzah! I'll no doubt replace it with adobe or whatever later on. But happily my system is working fine. 

If the purge gnash seems to wholesale for you, another thread 
[http://www.uluga.ubuntuforums.org/showthread.php?t=588831](http://www.uluga.ubuntuforums.org/showthread.php?t=588831)
shows more specific discussions about the gtk-gnash situation.

Anyway if your problems are not with gtk-gnash . Ouch and best wishes on finding out what is slowing down your system. 
- blath

---

### Post by daniel3ub on 2008-10-13
Well, my computer is not slowing down, it is just the taskbars that are hanging and freezing.

Anyway, I'll take a look at this app you told about. Thanks.

---


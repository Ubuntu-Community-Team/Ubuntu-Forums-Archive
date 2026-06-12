---
title: "Ubuntu 9.10 Boots Up To Command Line And Not Gui"
date: 2010-03-11
forum: Hardware
---

### Post by VeGeTa-X on 2010-03-11
I have a small problem with my ubuntu 9.10 on my laptop when I tried to plug my tv to my vga port on my laptop and changed the display settings on my laptop to the my too on.  I can only boot to the command line.  I have tried the startx command and I get the error in the pic below.  Also I have folllwed one solution that I found in the link below and edited the xorg.conf file and added  Driver "radeon" or Driver "ati" ## I even tried using intel instead of radeon or ati because my laptop is a dell d505 and it has a intel video graphics chip.  If anyone has any suggestions please let me know. Thx

[http://superuser.com/questions/63759/no-gui-after-upgrade-to-ubuntu-9-10-boots-to-command-line](http://superuser.com/questions/63759/no-gui-after-upgrade-to-ubuntu-9-10-boots-to-command-line)

[IMG]http://i68.photobucket.com/albums/i39/VeGeTa-X/IMAG0046.jpg[/IMG]

---

### Post by coffeecat on 2010-03-11
First thing: a default install of 9.10 doesn't have an xorg.conf file, so you must have created one. Is this correct?

Second - have a look at your screenshot, about halfway down. "Parse error..... xorg.conf". There's a syntax error in the xorg.conf which is a very efficient way of bringing the xserver to its knees.

Third - adding Driver radeon or Driver ati lines to an xorg.conf for a machine with Intel graphics is inappropriate, so you were correct to try "intel", but something is still wrong.

The simplest solution is probably to rename /etc/X11/xorg.conf (to something like xorg.conf.backup). Then, when you boot up it should be able to autodetect the Intel graphics and set itself up. (Which is what the live CD does.) 

But before you try this, it would be useful to see the contents of the current xorg.conf. Try booting up with the live CD, mount your hard disc Ubuntu root partition from the Places menu, and post the contents of xorg.conf. (Make sure you navigate to /etc/X11 on the hard drive. If you look in /etc/X11 of the live filesystem there won't be an xorg.conf.)

---

### Post by VeGeTa-X on 2010-03-11
> **coffeecat said:**
> First thing: a default install of 9.10 doesn't have an xorg.conf file, so you must have created one. Is this correct?

Second - have a look at your screenshot, about halfway down. "Parse error..... xorg.conf". There's a syntax error in the xorg.conf which is a very efficient way of bringing the xserver to its knees.

Third - adding Driver radeon or Driver ati lines to an xorg.conf for a machine with Intel graphics is inappropriate, so you were correct to try "intel", but something is still wrong.

The simplest solution is probably to rename /etc/X11/xorg.conf (to something like xorg.conf.backup). Then, when you boot up it should be able to autodetect the Intel graphics and set itself up. (Which is what the live CD does.) 

But before you try this, it would be useful to see the contents of the current xorg.conf. Try booting up with the live CD, mount your hard disc Ubuntu root partition from the Places menu, and post the contents of xorg.conf. (Make sure you navigate to /etc/X11 on the hard drive. If you look in /etc/X11 of the live filesystem there won't be an xorg.conf.)



I did not create the xorg.conf file I just went into the /etc/X11 directory and just edited it.  Yeah I just noticed the error I left an I their by mistake; I just moved the both of the xorg.conf file to a directory called called tmps and rebooted the computer and issue was solved thx for your help.  I guess this how you learn linux break and learn to fix and I like linux and this flavor ubuntu =)



[IMG]http://i68.photobucket.com/albums/i39/VeGeTa-X/IMAG0049.jpg[/IMG]

---

### Post by coffeecat on 2010-03-12
> **VeGeTa-X said:**
> I did not create the xorg.conf file I just went into the /etc/X11 directory and just edited it.  

Perhaps the system created the xorg.conf when you changed the display settings for the TV, although I wouldn't have thought it would - it didn't when I hooked my Karmic laptop up to a TV. Whatever - the trick was to remove the xorg.conf which is what you did when you moved it to another directory. I'm glad it's working now.

---


---
title: "Ubuntu 9.04 &quot;Hangs&quot; Whilst Installing In Virtual Machine 2007"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by Godbrother on 2009-10-04
Hi, I'm having a slight problem. It's my first time trying to use Ubuntu, my friend had it and I was really impressed.

When I'm trying to install it, it asks for the languge, then how I want to install it. I've tried selecting full install, or just booting from the ISO. But it "hangs" at the following screen. It happens straight after you select how you want it to be installed. Any adivce? 

Virtual System is set to: Pentium 4 3.0Ghz - 1GB Ram - 20GB HDD. 

[IMG]http://i33.tinypic.com/2whdp2x.jpg[/IMG]

---

### Post by mikewhatever on 2009-10-05
Forgive my ignorance, but what is Virtual Machine 2007? Why not use VirtualBox or VMplayer, both free tools know to work?

---

### Post by danfango on 2009-10-19
Hi Godbrother,

I had this issue also. You need to do the following (the command line appears just about the function options):

Boot Ubuntu 9.04 up. On the first screen, choose [English]. 
Then press [F4] and select [Safe Graphics].
Then press [F6], but do not select any option. Instead press [Escape] and it will allow you to change the command line. Remove the option "quiet splash --" and replace it with "vga=791 noreplace-paravirt" instead.
Press [Enter] to start the installation.

Thanks to NemesisV for this info:

[http://nemesisv.blogspot.com/2009/04/installing-ubuntu-904-on-microsoft.html](http://nemesisv.blogspot.com/2009/04/installing-ubuntu-904-on-microsoft.html)

Hope this helps!

---


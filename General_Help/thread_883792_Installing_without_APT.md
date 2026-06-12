---
title: "Installing without APT"
date: 2008-08-08
forum: General Help
---

### Post by A2JC4life on 2008-08-08
Is there any (relatively easy) way to install programs without using the APT repository system?  That only works if you can set up a good internet connection, and setting up a good internet connection seems to be pretty nigh on impossible when making the switch to Linux.  (I've been trying off and on for seven years now, and have yet to connect to the internet for so much as two seconds.)  I have downloaded packages I could install from my disk drive, but Ubuntu doesn't seem to be set up to do this. :confused:

---

### Post by tuxxy on 2008-08-08
What internet connection are you using, have you tried the internet guide?

[https://help.ubuntu.com/8.04/internet/C/index.html](https://help.ubuntu.com/8.04/internet/C/index.html)

---

### Post by A2JC4life on 2008-08-08
I'm still working on it.  I have PeoplePC.  (I think that's about half the problem.  They seem to be downright hostile to Linux.)  But hubby handles the bills, etc., and I don't want to ask him to change ISP's until I'm sure that everything is working properly on my end and ONLY PeoplePC is causing a problem.

---

### Post by y@w on 2008-08-08
If you have the .deb packages downloaded, you can use dpkg to install them. You just have to run 'sudo dpkg -i <package>.deb'.

---

### Post by Mgiacchetti on 2008-08-08
Internet worked out of the box for me, dunno what the problem is with your setup.   (now i see its people pc, they don't seem to like windows 98 either. they say "you NEED to be running windows XP or later to use "the internet". when I have been online with 3.1)

Maybe you should go live cd and try to diagnose the problem there before you set up your system.

I've had many problems with ubuntu, only to find that it was Me causing the problems with my thinking.

I thought I had to install envy to install my nvidia video card, went through hell and did a clean reinstall to find that it was all enabled through proprietary drivers.

Maybe you need to step back and reassess your method of installing the network card.  also the link in the above post may help you.

Have you tried using wine to install the software that nobody pc requires?

---

### Post by dannyboy79 on 2008-08-08
> **A2JC4life said:**
> I'm still working on it.  I have PeoplePC.  (I think that's about half the problem.  They seem to be downright hostile to Linux.)  But hubby handles the bills, etc., and I don't want to ask him to change ISP's until I'm sure that everything is working properly on my end and ONLY PeoplePC is causing a problem.

a little goggle resulted in a possible solution if you have access to a windows machine.

[http://www.linuxforums.org/forum/linux-newbie/100801-how-connect-peoplepc-linux-yay.html](http://www.linuxforums.org/forum/linux-newbie/100801-how-connect-peoplepc-linux-yay.html)

---

### Post by Elfy on 2008-08-08
It alos might help us to help you if you tell us what youa re trying to connect with, tbh ubuntu is a lot easier when you're connected. But there are waysof getting around the problem I think...

welll I was thinking of nonetdebs - but it appears to have problems of it's own - others might have an idea

---

### Post by tuxxy on 2008-08-08
You could try downloading the packages with your DVD ISO, to prevent you needing internet to download them

---

### Post by A2JC4life on 2008-08-08
I never thought of using WINE and trying to run PeoplePC's program.  I don't run the program on Windows; I just make a dialup connection that uses their dialup numbers and our username/password. lol 

This is a different computer than the one I was using before, though, so I have to go do all the modem detection stuff again.

---


---
title: "Canon Pixma iP1300 driver?"
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by ethernal on 2007-06-22
Hi there, I tried installing the driver that was on the openprinting.org website, it said that iP2200 driver would work but it does not. I can "print" something, and cups will say that it printed ok. Whereas nothing will actually happen, not even printing the test page works. But the status is ok and it says that it "prints" it too. But as I said, nothing actually happens. I also tried with several drivers from the canon website and I'm almost bashing my head against the wall soon because I can't get this to work. Any ideas what to do? Thank you

---

### Post by liam.casimir on 2007-07-26
Hey, I have the same printer as yours and me too is having problem.  Will somebody help us out,  ? I am using 64-bit Feisty. Thanks.  :(

---

### Post by guatelinux on 2007-07-30
I have the same printer and have tried pretty much everything suggested by folks here at the Ubuntu forums.  Nothing has worked.  At one point, the info over at openprinting.org had given "paperweight" status to this printer under Linux, but I see that they now are indicating once again that the printer works "perfectly" using the iP2200 driver (which it doesn't).

What I have found is something called Turboprint for Linux: [http://www.turboprint.de/english.html]("http://www.turboprint.de/english.html")

This costs money (30€/$39) for the real version, but the free version I downloaded has been the only thing that makes my iP1300 print at all.  I still haven't shelled out the money for the real version yet, mostly because I don't have a lot of printing needs right now and also because I'm holding out hope that someone comes up with a free driver.

I hope this helps,
Guatelinux

---

### Post by strangequarks on 2007-11-27
I have the same printer, also on feisty, tried the canon ip 2200 and it didn't work, exactly the same problem as ethernal...and I've just installed turboprint and now it works. Thanks for the advice!

---

### Post by strangequarks on 2007-11-27
Well, the printer works, but prints a turboprint logo in the middle of every page. This is a big nuisance as I need to print notes, but I'm not paying for it. Any more suggestions?

---

### Post by tj.c on 2007-11-27
I have an Epson (USB port) that does the same thing. Do a file/print, everything goes through the motion but nothing comes out of the printer. (short version)...turn off printer, log out od desktop (gnome), log in to desktop, turn on printer, it now works.
It seems that booting up and logging in with the printer already powered up is the issue. 
Hope it helps
TJ

---

### Post by Tavathlon on 2007-12-26
Hi all!

I'm trying to set up Ubuntu on my sister's new computer. However, she is completely new to Ubuntu, and she has some prerequisites of what she wants to have working on her machine - her camera and her printer is the two most important hardwares for her. The camera works fine, but I'm experiencing some problems with the printer, which of course is a Canon Pixma iP1300.

I installed the driver using the guide provided in this thread: [http://ubuntuforums.org/showthread.php?t=563627](http://ubuntuforums.org/showthread.php?t=563627)  (although I never saw the setting options shown in the 6th post of that thread, have no idea why - perhaps because that user was using KDE and I'm using Gnome?).

Anyway, printing as such is not really a problem, that works fine after following the guide. However, my sister wants to be able to use the printing software that was delivered with the printer (Easy PhotoPrint), since she think that software is handy to use for printing. Installing that software in Wine was no problem, as long as I chose not to install the windows driver for the printer (the installation stopped when I tried to do that). However, once installed, I tried to start the program - it starts neatly, but as soon as it got started, a box popped up telling me that there is no driver for the printer installed, and then the program shuts down immediately. So apparently, this program is not able to use the cups driver...  (which Adobe Photoshop, also installed through Wine, manages to do nicely)

So, anyone got any ideas on how I can manage to get this program to understand that there is a driver, just not where the windows drivers usually are located...  =P
(or have a suggestion for a good program that can do the same thing, i.e. make photo printing easier with putting up several photos on the same paper and providing a nice preview and stuff like that. I'm pretty sure she will think that is sufficient, as long as she will be able to achieve the function of printing the way she wants it.)

[Oh, btw - one feature my sister misses from printing in windows is to be able to see the ink levels in the cartridges..  perhaps that is included in the software that I'm trying to get working through wine, but it feels a little bit like something that is usually in the driver, right?]  Edit 2: The problem about ink status is now fixed, thanks to Turboprint! However, I have no idea about whether it is possible to get rid of the logo without purchasing the license, being a private user and not a company and that stuff..  ([http://www.turboprint.de/english.html](http://www.turboprint.de/english.html)) The other problem still existing. Anyone who know a good program for the task?

Best regards
Patrik

Edit 1: I just realized that the free version of turboprint is for testing _or private_ use only..  that means that it's okay to use it as long as you're not using it for company computers, right? Can't really get how that's supposed to work though..
Going to try that now, anyway...

---


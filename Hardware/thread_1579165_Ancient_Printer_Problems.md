---
title: "Ancient Printer Problems"
date: 2010-09-21
forum: Hardware
---

### Post by minigilani on 2010-09-21
Hey, i'm running **Ubuntu 10.04 LTS**, and i have an [[COLOR="Red"]HP Laserjet 6L printer[/COLOR]]("http://h20000.www2.hp.com/bizsupport/TechSupport/ProductList.jsp?lang=en&cc=us&prodTypeId=18972&prodSeriesId=25476&taskId=135"). This old, stupid piece of hardware is the only thing tying me to my Windows XP install!

The problem is this, it plugs into the big wide serial-port type thing at the back of my computer, i've never ever seen anything being plugged in that port before, and it's automatically detected and installed in my Windows XP OS, it shows the port at LP1, no idea what that means, though =s
In Ubuntu, it doesn't show ANYTHING about that printer =/
.
What's ironic is, that i'm printing out William Shotts' book, [[COLOR="Red"]The Linux Command Line[/COLOR]]("http://linuxcommand.org/tlcl.php") through this printer, and i can't get it to run on Linux =/

Please help me out =s
or tell me if it's hopeless =(

---

### Post by BobvanderPoel on 2010-09-21
The serial port thingie you have is a "Parallel Port". Sometimes it's called a Centronics port. It most likely shows up in linux as LPT #1.

From system->admistration->printing select <add> and the lpt#1 ... should work.

Can't confirm ... haven't had a parallel printer for many years.

Hope this helps.

---

### Post by minigilani on 2010-09-22
Wahaha! Thank you! Dude, it works!! All those pages i read, all those drivers i tried, all those drivers i compiled!! and all i had to do was go into settings!! Kill me!
.
Btw, i forgot, i use Kubuntu, not Ubuntu =p
I used to use Gnome, i think i like KDE more now =D
anyways, thanks! =D

---


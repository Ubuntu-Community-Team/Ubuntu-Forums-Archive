---
title: "Printer Problems"
date: 2010-05-14
forum: Hardware
---

### Post by chzuck on 2010-05-14
I am begining to think Linux is only for computer pros.  First I could not install and run any of the programs from my hard drive.  Now I cannot get Xubuntu to recognize my Epson printer.  Why can't Linux make things simple!!!!!!!!!
 
I have tried several of the methods listed in the manuals for Xubuntu and Ubuntu and have not had any success.

---

### Post by mamies on 2010-05-14
What type of Epson Printer is it? It may only need a little tweak to get it to work. Most things on Linux these days are rather easy and with the creation of Ubuntu it has just evolved into a fairly easy to use OS.

---

### Post by chzuck on 2010-05-14
Epson Stylus Color 640

---

### Post by IcarusR on 2010-05-14
Plug printer in, switch on then goto 

System > Administration > Printing > New 

Your printer should be found & setup for you.

If this fails then you can use the cups web interface

[http://localhost:631/]("http://localhost:631/")

Click 'Add Printer' & fill in the info. There are drivers for Epson Stylus 640.

---

### Post by chzuck on 2010-05-15
No can do, Xubuntu does not have that progression.  I was able to get the printer installed, but when I want to print it says the printer is not connected.  
 
I cannot believe how difficult this is.  Why do people put themselves through this? :confused:

---

### Post by cjazz on 2010-05-15
How is the printer connected? By USB? Network? Is gutenprint installed?

---

### Post by chzuck on 2010-05-15
Printer is connected via parallel port.  I am not sure gutenprint is installed.  How do I check.  I am beginning to think this Linux stuff is over my head. :(

---

### Post by cjazz on 2010-05-15
Sorry. Sometimes the more familiar you become with a system, the easy it gets to start slinging jargon. Gutenprint is a cups driver. According to [this site]("http://www.openprinting.org/printer/Epson/Epson-Stylus_Color_640"), your printer model works perfectly with it. You can check to make sure it's installed by navigating to Applications > System > Synaptic Package Manager and typing gutenprint into the search box.

I doubt that's the problem, however, since both Ubuntu and Xubuntu install gutenprint by default in my experience. I wonder if your problem is associated with the parallel port. I seem to remember some related bug in some versions of Ubuntu. Which version are you using?

It might be helpful to post the output of

```
dmesg | grep par
```

```
lsmod | grep lp
```

and

```
lsmod | grep parport
```

---

### Post by chzuck on 2010-05-18
Gutenprint appears to be installed and I am running Xubuntu 9.10.  I don't know how to get the info you are asking for.  Sorry, I am not very familiar with this Linux stuff and how it works.  I am trying to learn.  I do have a cable to connect the printer via USB, if you think that may be the problem.

---

### Post by chzuck on 2010-05-19
cjazz,
I changed my printer cable from a straight parallel cable to a parallel/USB and now the printer works. I removed the printer and reinstalled it after changing the cable. When I went through the configuration, it even identified it automatically, where before it did not. 
Thanks much for everyones help!

---


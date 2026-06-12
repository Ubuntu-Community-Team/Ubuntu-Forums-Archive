---
title: "install file that can read exe."
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by sanozuke02 on 2009-03-17
i dont know how to make my desktop read a exe. file!! 

i am using ubuntu and it doesnt read those exe. file.. 

please!! help me!! or e-mail me,


[email]redbuenaventura18@yahoo.com[/email]

thanks ,,,,,,.....:KS:KS:P

---

### Post by sansa dude on 2009-03-17
Use Wine it is a windows emulator so it will install windows applications like Microsoft office and other things. it may not work too well but for most programs it will do what it is supposed to. and its not a good idea to use your personal email on forums you may get a lot of spam

---

### Post by lisati on 2009-03-17
EXE files are designed for Windows (and occasionally MS-DOS). They don't usually work without help.

Your options depend on what you were trying to do: the main ones are look for a Linux-friendly alternative, or use an emulator such as WINE

---

### Post by iaculallad on 2009-03-17
Ubuntu can't read Win32 application (*.exe) files, you have to use a third party software to do that for you (i.e:[WinE]("www.winehq.org")).

To be specific, what EXE file application are you trying to read/execute?

---

### Post by pbpersson on 2009-03-17
A file with a .exe extension is a Windows executable file.  That is why the last poster suggested you use Wine - that is a Windows emulator that runs on Ubuntu.  You can install it from the Synaptic Package Manager.

---

### Post by sahabcse on 2009-03-17
Hi

Running .exe file in ubuntu we have to install wine packages. Installation steps is given below.

Add the following entry in sudo vim /etc/apt/sources.list

    deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 “Intrepid Ibex”

The run sudo apt-get update

Then install wine using

sudo apt-get install wine

---

### Post by lisati on 2009-03-17
> **pbpersson said:**
> A file with a .exe extension is a Windows executable file.  
Not necessarily. MS-DOS uses (used?) the EXE extension too, but with different/less information contained in the .EXE header.

---

### Post by sanozuke02 on 2009-03-17
thanks for the respone!! im just new here in ubuntu,, and i like it!! but my computer doesnt read exe.file!!

i want to run my yahoo messenger ,,

where can i find the wine??

please help!! me!!





from philippines..

---

### Post by sansa dude on 2009-03-17
> **sanozuke02 said:**
> thanks for the respone!! im just new here in ubuntu,, and i like it!! but my computer doesnt read exe.file!!

i want to run my yahoo messenger ,,

where can i find the wine??

please help!! me!!





from philippines..go to applications -> add/remove -> then in the search box search wine then from there just follow the instructions its pretty simple to install software that way

---

### Post by sanozuke02 on 2009-03-17
i search it andthe is no result about the wine...


help me please..

---

### Post by pbpersson on 2009-03-17
There are other applications in Ubuntu that will do the same function as Yahoo Messenger if you just want to instant message people.

I use Pidgin

---

### Post by pbpersson on 2009-03-17
> **sanozuke02 said:**
> i search it andthe is no result about the wine...


help me please..

You did not get a result for wine because there is a drop-down box at the very top of the window where you specify the types of packages you are looking for.  You need to make sure the drop-down is set to "all packages"

---

### Post by iaculallad on 2009-03-17
> **sanozuke02 said:**
> 
i want to run my yahoo messenger ,,


The beauty of using an Open Source OS, you have a couple of choices to choose from. You can either choose to use Pidgin or Kopete, both having the ability to support multiple messenger protocols.

---

### Post by sanozuke02 on 2009-03-17
most of my friends are using ymessenger thats why i need to install it..

can i ask???

is the wine??? really can help my computer to read exe. file?? such as yahoo messenger???

thanks!!!!!
thanks for those persons who will help me..and give there help...

---

### Post by iaculallad on 2009-03-17
> **sanozuke02 said:**
> most of my friends are using ymessenger thats why i need to install it..


No worry even if you're friends are using YM. As I've stated on my previous post, Pidgin or Kopete supports multiple protocols. Whether that be AIM, Bonjor, Gadu-Gadu,MSN,Google Talk, Yahoo Messnger, ICQ, ... and others. 
Using either of the two mentioned would also give you the edge of signing in as yourself simultaneously on different protocols not just Yahoo.

---

### Post by LiamWilson on 2009-03-17
To use Pidgin, Go to Applications > Internet > Pidgin. When it opens, the accounts window should open. Click add, and another window will appear. Then in the Top box which says Protocol, select Yahoo!. Then type in your username and password, then click ok! Then your all set to go!

---

### Post by hello_from_russia! on 2009-03-17
Really, try to use wine. I think it's the best of emulators windows software. I use it sometimes and it's always working well.

---

### Post by sanozuke02 on 2009-03-17
oh thanks!! but yahoo messenger in pidgin doesnt have a call conversation!! 
:(:(

i really need an installer that can read an exe. files!!:(:(:(:(:(

---

### Post by jespdj on 2009-03-17
Lots of people in this thread have already told you to install Wine, but you just keep on repeating your question... why?

Install Wine: Go to System / Administration / Synaptic Package Manager and search for "wine", and install it. Or, use a terminal window (Applications / Accessories / Terminal) and type:
```
sudo apt-get install wine
```
After that, do:
```
wine ymessenger.exe
```

---

### Post by sanozuke02 on 2009-03-17
weeh!! thanks!!

to all!! my yahoo is now working!!!


gud day to all!




salamat!<thank you>

---


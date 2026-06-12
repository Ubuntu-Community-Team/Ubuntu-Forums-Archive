---
title: "Hp Printer ink level?"
date: 2008-08-25
forum: General Help
---

### Post by Camilia on 2008-08-25
I was wondering, where do you view the ink levels of the printer?
I don't see in the printer preferences. My printer is an hp deskjet-3930.

---

### Post by kaibob on 2008-08-25
> **Camilia said:**
> I was wondering, where do you view the ink levels of the printer? I don't see in the printer preferences. My printer is an hp deskjet-3930.

I'm not familiar with your printer but with my HP I can view the ink levels in the HPLIP Toolbox. Just click on:

*System > Preferences > HPLIP Toolbox*

---

### Post by Camilia on 2008-08-25
> **kaibob said:**
> I'm not familiar with your printer but with my HP I can view the ink levels in the HPLIP Toolbox. Just click on:

*System > Preferences > HPLIP Toolbox*

I don't have HPLIP toolbox. Every program for the printer in the add programs has been added.

---

### Post by Bablefish on 2008-08-25
When I downloaded my HP Linux driver from the HP site, that program istalled with the drivers. How did you install yours?

---

### Post by coffeecat on 2008-08-25
> **Camilia said:**
> I don't have HPLIP toolbox. Every program for the printer in the add programs has been added.

You need the graphical frontend. It's in the Ubuntu repositories. Open Synaptic (System > Administration > Synaptic Package Manager) and select 'hplip-gui'. Once installed you'll find it under System > Preferences as an earlier poster has pointed out.

---

### Post by Camilia on 2008-08-25
> **Bablefish said:**
> When I downloaded my HP Linux driver from the HP site, that program istalled with the drivers. How did you install yours?

I just turned in on. I have the disk for the printer but inserting it just gave me folder, which I don't understand. 

'hplip-gui not found in the Synaptic Package Manager. HPLIP is marked installed.

---

### Post by coffeecat on 2008-08-25
> **Camilia said:**
> 'hplip-gui not found in the Synaptic Package Manager.

Ho hum. Look at my attachment. Which version of Ubuntu are you running and which repositories have you got installed?

---

### Post by Camilia on 2008-08-25
> **coffeecat said:**
> Ho hum. Look at my attachment. Which version of Ubuntu are you running and which repositories have you got installed?

I have ubuntu 8, hard heron.  What is a repository. Probably have them just don't where.

---

### Post by coffeecat on 2008-08-25
> **Camilia said:**
> What is a repository.

A repository is a software source held on a server. Ubuntu has categorised them. Open Synaptic and go to Settings > Repositories. Make sure you are on the 'Ubuntu Software' tab. Compare what you have with my screenie attachment. I should imagine that hplip-gui is in the 'Software restricted by copyright..' repository but I can't be sure. Enable whichever repositories you need. (Don't change the 'Download from' server - yours will be different. That doesn't matter.) Now click on the 'Reload' button and once the package database has been upated, hopefully, hplip-gui will appear in your package list.

---

### Post by Camilia on 2008-08-25
Coffeecat I did as you suggested and did upgrades. I still don't see anything in the menu under system for hp. I see printer prior and have made all of the changes I can in it.

Have ubuntu 8 Hardy Heron

---

### Post by mssever on 2008-08-25
From the terminal, type ```
hp-toolbox
```If you don't have the proper package, you'll be told what to install.

---

### Post by Camilia on 2008-08-25
> **mssever said:**
> From the terminal, type ```
hp-toolbox
```If you don't have the proper package, you'll be told what to install.

Did that and this the result- 
error: hp-toolbox requires GUI support. Exiting.

Googled GUI support and found aria. Downloaded it and in terminal pasted hp-toolbox. Result-
error: PyQt not installed. GUI not available. Exiting.
warning: Qt/PyQt initialization failed.
error: hp-toolbox requires GUI support. Exiting.

---

### Post by mssever on 2008-08-25
> **Camilia said:**
> Did that and this the result- 
error: hp-toolbox requires GUI support. Exiting.
Are you running on the console? hp-toolbox is a GUI app, so if you're not running x, it won't work. hp-info is a CLI app. (If you hit hp<tab><tab>, you'll see a list of options.)

---

### Post by Camilia on 2008-08-25
> **mssever said:**
> Are you running on the console? hp-toolbox is a GUI app, so if you're not running x, it won't work. hp-info is a CLI app. (If you hit hp<tab><tab>, you'll see a list of options.)

I don't what you are talking about.

Just downloaded djtool tools for hp printer and libinklevel4. Nothing has changed 

In terminal typed hp and hit tab 2x =:
hp-align       hpijs          hp-probe       hp-testpage
hp-check       hp-info        hp-scan        hp-timedate
hp-clean       hp-levels      hp-sendfax     hp-toolbox
hp-colorcal    hp-makecopies  hpset          hp-unload
hp-fab         hp-makeuri     hp-setup       
hp-firmware    hp-print       hpssd

---

### Post by kaibob on 2008-08-25
Perhaps you should try the "automatic installer" from the HP website:

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

You download the file and then follow the website's very detailed instructions which include lots of illustrations. Just follow them step by step and you should be fine.

---

### Post by Camilia on 2008-08-25
> **kaibob said:**
> Perhaps you should try the "automatic installer" from the HP website:

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

You download the file and then follow the website's very detailed instructions which include lots of illustrations. Just follow them step by step and you should be fine.

I already tried that!! Saved it to documents. Clicked 
and got - Could not open file. Pasted sh hplip-2.8.7.run
in terminal, instructions and got Can't open hplip-2.8.7.run.

---

### Post by mssever on 2008-08-25
> **kaibob said:**
> Perhaps you should try the "automatic installer" from the HP website:
It's much better to use the packages from the repos. If you installed from the repos, then it should work.

Have you tried hp-info? Uninstall all the HP stuff that you installed using some method other than the repos, then install hplip from the repos. You should then get all the dependencies.

---

### Post by Camilia on 2008-08-25
> **mssever said:**
> It's much better to use the packages from the repos. If you installed from the repos, then it should work.

Have you tried hp-info? Uninstall all the HP stuff that you installed using some method other than the repos, then install hplip from the repos. You should then get all the dependencies.

I don't that will make a difference for I had installed the download before I added these items.

What does this mean: Are you running on the console? hp-toolbox is a GUI app, so if you're not running x, it won't work. hp-info is a CLI app

If you are going to give advise explain. I might as well be reading chinese

---

### Post by mssever on 2008-08-25
> **Camilia said:**
> I don't that will make a difference for I had installed the download before I added these items.What download?

> What does this mean: Are you running on the console? hp-toolbox is a GUI app, so if you're not running x, it won't work. hp-info is a CLI app

If you are going to give advise explain. I might as well be reading chinese
But I don't know Chinese. How about ancient Greek? :) The console is a text only interface that has no graphical interface. It's the default in, e.g., Ubuntu Server. X is the program that powers the GUI. CLI == command-line interface. Since you don't understand this, my question doesn't apply to you.

---

### Post by kaibob on 2008-08-25
> **Camilia said:**
> I already tried that!! Saved it to documents. Clicked and got - Could not open file. Pasted sh hplip-2.8.7.run in terminal, instructions and got Can't open hplip-2.8.7.run.
After opening a terminal window, you have to change to the directory that contains the downloaded hplip file. You can then run the command, sh hplip-2.8.7.run. If this doesn't work, then you are either in the wrong directory or have typed the command incorrectly. Try again and it will work.

If you are new to the terminal and don't know how to change directories, see the following page:

[http://linuxcommand.org/lts0020.php](http://linuxcommand.org/lts0020.php)

---

### Post by Camilia on 2008-08-26
> **kaibob said:**
> After opening a terminal window, you have to change to the directory that contains the downloaded hplip file. You can then run the command, sh hplip-2.8.7.run. If this doesn't work, then you are either in the wrong directory or have typed the command incorrectly. Try again and it will work.

If you are new to the terminal and don't know how to change directories, see the following page:

[http://linuxcommand.org/lts0020.php](http://linuxcommand.org/lts0020.php)

I am new to ubuntu. I only know about pasting commands. Thus I don't know anything about the directory. Pasted  hplip-2.8.7.run and got Can't open hplip-2.8.7.run  

I went to that link confused from the beginning. The directory you are standing in is called the working directory. To find the name of the working directory, use the pwd command. 

[me@linuxbox me]$ pwd
/home/me

Tried and got this.
dawn@dawn-desktop:~$ [me@linuxbox me]$ pwd
bash: [me@linuxbox: command not found

dawn@dawn-desktop:~$ /home/me
bash: /home/me: No such file or directory

dawn@dawn-desktop:~$ pwd
/home/dawn

---

### Post by Camilia on 2008-08-27
I removed ubuntu do do a dual bootup with windows. Have reinstalled it. Have hplip installed. Now have the toolbox in systems preference. 

Thank you everyone for your suggestions and for putting up with my confusion.

---

### Post by Camilia on 2008-08-28
Got HPLIP tool box now but don't see the ink levels. Check out every area in the tool box. 

Where are the ink levels?

---

### Post by mssever on 2008-08-28
> **Camilia said:**
> Got HPLIP tool box now but don't see the ink levels. Check out every area in the tool box. 

Where are the ink levels?On the Supplies tab.

---

### Post by Camilia on 2008-08-28
The supplies is empty.

---

### Post by rbmorse on 2008-08-29
Does your printer connect to the computer via a USB cable, or does it have the wireless interface adapter?

---

### Post by Camilia on 2008-08-29
> **rbmorse said:**
> Does your printer connect to the computer via a USB cable, or does it have the wireless interface adapter?

I am connected via a usb cable.

---

### Post by mssever on 2008-08-29
In system-config-printer, does the device URI begin with hp:? For example, here's my device URI:
```
hp:/usb/deskjet_5100?serial=MY3BF4R1C77A
```

---

### Post by Camilia on 2008-08-29
> **mssever said:**
> In system-config-printer, does the device URI begin with hp:? For example, here's my device URI:
```
hp:/usb/deskjet_5100?serial=MY3BF4R1C77A
```

Pasted hp:/usb/deskjet_3905? in the terminal result No such file or directory.

Uncertain if the URI begins with hp?

---

### Post by mssever on 2008-08-29
> **Camilia said:**
> Pasted hp:/usb/deskjet_3905? in the terminal result No such file or directory.

Uncertain if the URI begins with hp?
Right. I said to look in system-config-printer, not paste into the terminal.

---

### Post by Camilia on 2008-08-29
msservr
system-config-printer I don't understand. Do mean in the tool box? There is a tab to configure. In advanced area, which I don't understand there are areas to paste url. Print extenal command is hp-print -p%PRINTER%

---

### Post by mssever on 2008-08-29
> **Camilia said:**
> msservr
system-config-printer I don't understand. Do mean in the tool box? There is a tab to configure. In advanced area, which I don't understand there are areas to paste url. Print extenal command is hp-print -p%PRINTER%
system-config-printer is the name of a program. Type that in a terminal, or in the run dialog.

---

### Post by Camilia on 2008-08-29
This is in the url hp:/usb/Deskjet_3900?serial=CN5CM1M2WY04DF

---

### Post by jpangamarca on 2008-08-29
My printer is an HP Deskjet 845c. It always prints in High Quality, therefore it uses WAY too much ink. How can I control the level of ink used? I have HPLIP Toolbox installed but there's not any ink level settings. Can anyone help me out?

---

### Post by mssever on 2008-08-29
> **jpangamarca said:**
> My printer is an HP Deskjet 845c. It always prints in High Quality, therefore it uses WAY too much ink. How can I control the level of ink used? I have HPLIP Toolbox installed but there's not any ink level settings. Can anyone help me out?
Set that in system-config-printer, or in the print dialog.

---

### Post by jpangamarca on 2008-08-29
> **mssever said:**
> Set that in system-config-printer, or in the print dialog.
Hmmm, I still can't find that setting, not in any of those dialogs. There's only DPIs, type of paper, media size, color/grayscale, but there's not anything for the ink. With Window$ there's a setting for the quantity of ink, it's something like Draft, Normal, and Extra, I don't remember exactly. Is there something like that in Ubuntu?

---

### Post by jpangamarca on 2008-08-29
> **mssever said:**
> Set that in system-config-printer, or in the print dialog.
Hmm, I still can't find that setting, there's only DPIs, media type, color/grayscale, and others. What I'm looking for is a setting like the one there's on Window$, it's something like print quality: draft, normal and high. Is something like that for Ubuntu?

---

### Post by mssever on 2008-08-29
> **jpangamarca said:**
> Hmm, I still can't find that setting, there's only DPIs, media type, color/grayscale, and others. What I'm looking for is a setting like the one there's on Window$, it's something like print quality: draft, normal and high. Is something like that for Ubuntu?
It's right here:

---

### Post by Camilia on 2008-08-29
My print out mode is not the same as yours. I just get diferent types or printing like for pictures.

Nothing in that program shows ink levels

---

### Post by mssever on 2008-08-29
> **Camilia said:**
> My print out mode is not the same as yours. I just get diferent types or printing like for pictures.

Nothing in that program shows ink levels
I guess I don't know how to help you then. :(

---

### Post by stinger30au on 2008-08-29
> **jpangamarca said:**
> My printer is an HP Deskjet 845c. It always prints in High Quality, therefore it uses WAY too much ink. How can I control the level of ink used? I have HPLIP Toolbox installed but there's not any ink level settings. Can anyone help me out?

Turbo print 2 is what you want

[http://www.turboprint.info/](http://www.turboprint.info/)


you need to purchase this program. it has a free 30 day trial. magic s/w

it will allow you to controll how much ink your printer lays down when printing in a smiliar fashion that inksaver does for windows

[http://www.inksaver.com/](http://www.inksaver.com/)


but turbo print does a TON of handy stuff

---

### Post by jpangamarca on 2008-08-30
Thanks a lot, msssever and stinger30au. The setting didn't appear there, but I downloaded the PPD file for my HP Deskjet 845c printer from [http://www.linuxprinting.org/ppd-o-matic.cgi?driver=hpijs&printer=HP-DeskJet_845C&show=0](http://www.linuxprinting.org/ppd-o-matic.cgi?driver=hpijs&printer=HP-DeskJet_845C&show=0) , and the printout mode is configurable now and the printer works fine. So, I didn't have to download TurboPrint or perform any ugly fix. I hope this can help anyone else out.

[IMG]http://jpangamarca.wordpress.com/files/2008/08/printer_options1.png[/IMG]

:guitar:

---

### Post by Camilia on 2008-08-30
jpangamarca I have the program you posted. Is via this you view your print level?

I tried what you did [http://www.linuxprinting.org/ppd-o-m...et_3095&show=0](http://www.linuxprinting.org/ppd-o-m...et_3095&show=0) and got no url. Went to linuxprinting.org and didn't find anything.

---

### Post by jpangamarca on 2008-08-30
@Camilia: Actually, I can't see the cartridge ink levels, but I can configure the print quality (draft, normal, high). EDIT: The URL ofr my printer is -- [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_845C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_845C) -- , Don't know why it didn't show properly. Maybe you can find the driver for your printer in that site.

---

### Post by Butthead on 2008-08-30
There is a small program in the software repositories for (supposedly?) checking the ink levels in HP printers, search for & install one called **"ink."**

---

### Post by Sef on 2008-08-30
> There is a small program in the software repositories for (supposedly?) checking the ink levels in HP printers, search for & install one called "ink."

It's called Qink; however, it is alpha ware, so it may be unstable or the features may not all work or both.  Applications > Add/Remove > Show: All Available Applications or All Open Source Applications > Search: Qink > click on the box next to Qink > Apply Changes > Apply > Close

HPLIP is available from Add/Remove too.  Just search for it instead of Qink.

---

### Post by jonian_g on 2008-08-30
To see inklevels from hp toolbox application you have to install the python-qt3 bindings. To install them open a terminal and type:

```
sudo apt-get install python-qt3
```

Once they are installed run hp toolbox either by typing:

```
hp-toolbox
```

or navigating to System>Administration. On the window that appears go to the Supplies tab.

---

### Post by Camilia on 2008-08-31
> **Sef said:**
> It's called Qink; however, it is alpha ware, so it may be unstable or the features may not all work or both.  Applications > Add/Remove > Show: All Available Applications or All Open Source Applications > Search: Qink > click on the box next to Qink > Apply Changes > Apply > Close

HPLIP is available from Add/Remove too.  Just search for it instead of Qink.

I found Qink in the synapse. Downloaded. It won't work. Says no printer dectected. May not have permission to access printer devise file. Add yourself to the lp user group using sytems administrator utility.

---

### Post by Camilia on 2008-08-31
> **jonian_g said:**
> To see inklevels from hp toolbox application you have to install the python-qt3 bindings. To install them open a terminal and type:

```
sudo apt-get install python-qt3
```

Once they are installed run hp toolbox either by typing:

```
hp-toolbox
```

or navigating to System>Administration. On the window that appears go to the Supplies tab.

Still not seeing an area to see ink levels. I guess when I get low I will notice it when I print.

---

### Post by Camilia on 2008-08-31
> **jonian_g said:**
> To see inklevels from hp toolbox application you have to install the python-qt3 bindings. To install them open a terminal and type:

```
sudo apt-get install python-qt3
```

Once they are installed run hp toolbox either by typing:

```
hp-toolbox
```

or navigating to System>Administration. On the window that appears go to the Supplies tab.

Well, now the printer is printing properly. There is nothing in the supplies tab, though.

---


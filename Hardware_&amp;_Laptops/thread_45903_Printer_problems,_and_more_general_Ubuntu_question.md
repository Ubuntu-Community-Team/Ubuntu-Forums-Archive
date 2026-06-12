---
title: "Printer problems, and more general Ubuntu questions"
date: 2005-07-02
forum: Hardware &amp; Laptops
---

### Post by zoqaeski on 2005-07-02
G'day All
I decided to give Ubuntu Linux a go, and so far I'm impressed... but I've got a few questions:
- Where do I download drivers for the HP Deskjet 710c printer? It says in the printer properties dialog that the pnm2ppa driver is required, but I have no idea where to find it  :-? ... does anyone know?

- What about firewalls and antivirus stuff? Where should I go to find these, what versions are recommended? Having migrated from a windoze environment, I know all too well that those particular items of software are ESSENTIAL for computer security issues... what is the status quo with Ubuntu?

- Last, but very important nonetheless, how do I get programmes to install? What sort of different procedures do you do as compared with windoze?

If you can help me out, it would be greatly appreciated - I'm a total newbie with Linux systems (up until a couple of hours ago, I had never tried it), so I s'pose I need all the advice I can get.

cheers
Robbie

---

### Post by Juergen on 2005-07-02
For printer drivers look here:
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_710C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_710C)
Or, maybe the Gimp-print drivers work with your printer - you can install these with synaptic.

> I know all too well that those particular items of software are ESSENTIAL for computer security issuesReplace 'computer' with 'Windows' here.

There are about 10 Linux viruses, none of them 'in the wild', so the antivirus-stuff you can install usually only scans your mailserver to avoid sending MS-viruses to MS-users.
If you follow the common advice to use the root account only for administrative work (in Ubuntu with 'sudo' only for single commands) a virus would have to ask you to consciously install it. 
So use trusted software (from the Ubuntu servers) only and you should be OK.

A firewall is built-in the kernel. You can configure it with tools like 'shorewall'
But remember: a firewall can only protect the boxes behind it. 
So take care if you modify the config of a 'server'-app you install on your firewall-box.
Freshly after installation they should all be configured to only listen to localhost.

And for installing apps:
In the Gnome-menu look at System/Administration/Synaptic package manager.
If you enable all repositories, you have >16000 packages to install.
This should be enough to get you started... ;-)

---

### Post by angkor on 2005-07-02
For more info on printing in Linux:

[http://www.linuxprinting.org/](http://www.linuxprinting.org/)

No need for anti-virus or firewall, unless you have to protect windows-boxes that connect through your Ubuntu-box. This stuff is only ESSENTIAL on Windows-machines :smile: 

To install programs, use synaptic, which is a graphical front-end to the apt package system.

You really need to read this site:

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

It has _lots_ of info on Ubuntu.

---

### Post by David Haas on 2005-07-02
zoqaeski--The driver (the PPD file) for the HP Deskjet 710c comes with the Ubuntu Hoary distribution. It's located in the HP directory at /usr/share/cups/model/foomatic-ppds/HP and the file is labelled HP-DeskJet_710C-pnm2ppa.ppd.gz. So, after selecting your printer in the Gnome printer manager GUI (System>Administration>Printing) click on select driver and click through the directories to the HP directory where you will find this PPD file. Then select it. Once selected, an unzipped copy will automatically be placed in /etc/cups/ppd. Then your printer should work.
David

---

### Post by zoqaeski on 2005-07-03
[QUOTE=David Haas]zoqaeski--The driver (the PPD file) for the HP Deskjet 710c comes with the Ubuntu Hoary distribution. It's located in the HP directory at /usr/share/cups/model/foomatic-ppds/HP and the file is labelled HP-DeskJet_710C-pnm2ppa.ppd.gz. So, after selecting your printer in the Gnome printer manager GUI (System>Administration>Printing) click on select driver and click through the directories to the HP directory where you will find this PPD file. Then select it. Once selected, an unzipped copy will automatically be placed in /etc/cups/ppd. Then your printer should work.
David[/QUOTE]

Thanks for that, I found the driver. But now it comes up with an error to do with something called samba  :-? ....
Now what??

Robbie

---

### Post by David Haas on 2005-07-03
zoqaeski--I've not run into this error message when selecting a PPD file, but others may have, and may undestand it. Samba is a filesharing software suite for Unix (and Linux). Among other things, it permits Windows computers to share a printer(s) with a Linux server. Exactly what did the error message say? from what i now know, I'd ignore it and select the PPD file. Then check to make sure that an unzipped copy has been placed in /etc/cups/ppd.
David

---

### Post by zoqaeski on 2005-07-04
I've checked all of that, but the printer and computer are not talking. I forgot to mention, but the printer is setup as a network printer on the windows network (which, I can't access either - my Linux box knows there's a network there, but it won't connect or talk to them)... could the netowrking issues be the cause of the printer problem?

Robbie

---

### Post by David Haas on 2005-07-05
Robbie--Ah, it's a networked printer. You'll need to get help from those who do networking in this forum. But look at Networking in the Unofficial 5.04 guide at [http://ubuntuguide.org/](http://ubuntuguide.org/).
David

---

### Post by Aardark on 2005-07-24
I have the same problem, so I figured it's not worth making a new thread.

[QUOTE=David Haas]zoqaeski--The driver (the PPD file) for the HP Deskjet 710c comes with the Ubuntu Hoary distribution. It's located in the HP directory at /usr/share/cups/model/foomatic-ppds/HP and the file is labelled HP-DeskJet_710C-pnm2ppa.ppd.gz. So, after selecting your printer in the Gnome printer manager GUI (System>Administration>Printing) click on select driver and click through the directories to the HP directory where you will find this PPD file. Then select it. Once selected, an unzipped copy will automatically be placed in /etc/cups/ppd. Then your printer should work.
David[/QUOTE]
I'm trying to do this, but when I choose the driver, I get this error: *Missing asterisk in column 1 at 1:'/usr/share/cups/model/foomatic-ppds/HP/HP-DeskJet_656C-hpijs.ppd.gz'*. Any idea about what's causing it?

---

### Post by badboyz107 on 2005-08-02
I have the same astricks error when I'm trying to select the drivers for my HP 610cl.....GRRRRR

---


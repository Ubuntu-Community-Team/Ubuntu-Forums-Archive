---
title: "HP 3740 and hplip"
date: 2005-04-15
forum: Hardware &amp; Laptops
---

### Post by valmar on 2005-04-15
Hello everyone!

I am trying to make my HP DeskJet 3740 work under Kubuntu 5.04 (or Ubuntu, it would be the same for me). However, I run into two problems:

1) The instructions on this page: 

[http://hpinkjet.sourceforge.net/install.php](http://hpinkjet.sourceforge.net/install.php)

Ask me to install the printer (I use the printing manager for this) using the foomatic/hpijs
driver. The problem, of course, is that when I apt-get install hplip, the hpijs package is removed, so the driver does not appear in drivers list.

To work around this, I kept hpijs installed and compiled hplip from source.

2) However, when I try to launch the HP toolbox, apparently everything goes fine (the "Launching Toolbox..." message is shown, etc.) but the toolbox application never starts!

I have to say that this happens also when I install hplip from the ubuntu repositories (of course in that case the printer driver is not foomatic/hpijs)

Anyone has any advice?


       Thank you in advance for your help

Valerio

---

### Post by joeh on 2005-04-15
I had the same problem getting hplip_toolbox working.
 
 This is what I did. 
 
$sudo gedit /usr/lib/hplip/ui/devmgr4_base.py
 
 Edit line 30 - replace both 5's with QSizePolicy.Preferred so it looks like this (should be no spaces in this line):
 
self.DeviceList.setSizePolicy(QSizePolicy(QSizePolicy.Preferred,QSizePolicy.Preferred,0,0,self.DeviceList.sizePolicy().hasHeightForWidth()))
 
 Edit line 113 - replace the first two 0's with QSizePolicy.Minimum so it looks like this (should be no spaces in this line):
 
self.StatusIcon.setSizePolicy(QSizePolicy(QSizePolicy.Minimum,QSizePolicy.Minimum,0,0,self.StatusIcon.sizePolicy().hasHeightForWidth()))
 
 Now hplip_toolbox should work.

Let me know if this works for you,
Joe

---

### Post by valmar on 2005-04-16
Thank you for your help

No, I'm sorry I tried but it didn't work. I must say that when I use the command line tools to print test page. clean noozles, etc. they work very well. So I think the problem lies with the graphical user interface

    Valerio

But do I really need to keep hpijs installed and install hplip from source?

---

### Post by joeh on 2005-04-16
These are the hoary packages I have installed:

[font=Courier New]hpijs          2.0.1+0.8.7-4  HP Linux Printing and Imaging - gs IJS drive
hplip          0.8.7-4        HP Linux Printing and Imaging System (hplip)
hplip-data     0.8.7-4        HP Linux Printing and Imaging - data files
[/font]
Joe

---

### Post by valmar on 2005-04-17
Well, I have installed exactly the same packages, but in this way I do not have a driver for the 3740 printer in the driver list! Am I missing something?

Thank you

---

### Post by joeh on 2005-04-17
I looked on HP's hplip website [hpinkjet.sourceforge.net/]("http://hpinkjet.sourceforge.net/")

Do you have a DJ3600 or DJ3320 listed? 

You might try each of those.

Joe

---

### Post by finster on 2005-04-17
[QUOTE=joeh]These are the hoary packages I have installed:

[font=Courier New]hpijs          2.0.1+0.8.7-4  HP Linux Printing and Imaging - gs IJS drive
hplip          0.8.7-4        HP Linux Printing and Imaging System (hplip)
hplip-data     0.8.7-4        HP Linux Printing and Imaging - data files
[/font]
Joe[/QUOTE]

How did you manage to get hplip and hpijs installed together?

When I try to install hplip (for my HP PSC 1215), I get a message that it conflicts with hpijs which would have to be removed along with ubuntu-desktop.

---

### Post by joeh on 2005-04-17
hplip does conflict with ubuntu-desktop, but according to the description listed for ubuntu-desktop it is safe to remove it.

 > The Ubuntu desktop system
This package depends on all of the packages in the Ubuntu desktop system

It is safe to remove this package if some of the desktop system
packages are not desired.  However, it is recommended that you keep
it installed, because it is used to carry out certain upgrade
transitions (such as adding new packages to the system). 

hplip conflicts with hpijs versions less than 2. hpijs will need to be upgraded if you have a version less than 2 installed.

Joe

---

### Post by finster on 2005-04-17
Thanks, I will try that when I get chance.

---

### Post by valmar on 2005-04-17
Ok I think we are almost there. This is what I did. I installed hplip from the ubuntu repositories. This removed the following packages:

foomatic-db-hpij
foomatic-filters-ppds

I downloaded the source code for them with apt-get source <package names>.
I changed in the directories and compiled them (That was easy: ./configure/make/sudo make install for one, and simply ./install for the other).
Now I have hplip and all the drivers present on the system at the same time.

Then I modified the hplip code like joeh suggested. If I do this on the source code of a version of hplip that I donwload and compile myself, it doesn't work. But if I do it on the version from the ubuntu repository, it works and the panel opens.

However, there are still some problems. The buttons in the "Manteinance" tag ("print test page", for example) do not work. 

I think that it's just some problem with the front-end again, however. If I print the page using hplip_testpage, it works like a charm . So we only have some problems with the GUI!

Maybe Joeh or anyone else can help again? 

Also, do you all think that I should file a bug report somewhere about this? I know that hplip is not officially supported, but this might help other people who have the same problem

Thank you everybody! We are slowly making things work!

          Valerio

---

### Post by finster on 2005-04-18
Thanks... I went along with removing kubuntu-desktop, with no major problems - I  seem to have now got the following installed: -

hplip          0.8.7-4        HP Linux Printing and Imaging System (hplip)
hplip-data     0.8.7-4        HP Linux Printing and Imaging - data files

All seems to have installed OK - I have various hplip* executables available to me.

I tried running hp_toolbox, but I just get the message "Launching toolbox localhost:32789)..." and then nothing.

Is there something else I should be doing?

---

### Post by valmar on 2005-04-19
Anyone had any success in making the buttons work or in general the panel work?

Thank you

      Valerio

---


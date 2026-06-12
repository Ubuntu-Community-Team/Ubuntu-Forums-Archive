---
title: "Install Canon driver install.sh"
date: 2013-01-13
forum: Hardware
---

### Post by Catbells on 2013-01-13
The Canon instructions for Ubuntu are: -

For Ubuntu 10.10
(1)    Expanding the archived file and switching to the expanded directory

[user@zzz /yyy]$ tar zxvf cnijfilter-mg3100series-3.60-x-deb.tar.gz
[user@zzz /yyy]$ cd cnijfilter-mg3100series-3.60-x-deb

(2)    Installing the printer driver

[user@zzz /yyy]$ sudo ./install.sh

When I tried this in the Dolphin Terminal pane, I got an error message, "Command not found."  I've tried to attach a snapshot of the Dolphin window.  I also tried running the two commands from the next folder up, but that didn't work.  What makes me want to cry is that it worked first time in Ubuntu 10.10.

---

### Post by offgridguy on 2013-01-13
Have you tried this site ?

[http://www.linux-drivers.org/](http://www.linux-drivers.org/)

---

### Post by pdc on 2013-01-14
so Rosemary I am guessing you want to install a Canon MG3100 series printer
inside that directory or folder that is called packages ...

...........are four .deb files:

2 for a 32bit system and 2 for a 64bit system;

for the 32bit there will be a common package and a specific one; same for 64bit;

so to install; if you use the GUI to open the package directory/folder

....... you will know if you have 32bit or 64bit;

and then right-click on the common package that is for you;

select install with gdebi installer; enter your sudo password ...

.....then right-click on the MG3100 package ..32 or 64 whichever is right for you .......again select to install with gdebi installer......

.......that should get you all set up ......

.....I give you this way, as the install.sh script just does what I have suggested you do .............

........if you really, really want to unleash the install.sh script, I can give you the commands ....... but the final do it instruction is "./install.sh"

---

### Post by Catbells on 2013-01-14
pdc, thank you so much for your help I had been confused at having a -deb folder rather than a .deb file.  I found the files and am now printing.  Thank you so much for your help.

Can I trouble you a little further?  I installed the Scangear drive with Qapt (right click offered me that rather than gdebi, probably because I'm in Kubuntu rather than Ubuntu).  It seems that scangearmp-common_1.80-1_i386.deb isn't working properly.  I think I'd like to uninstall it before trying scangearmp-mg3100series_1.80-1_i386.deb.  The only thing is that the only way I know of uninstalling something is to look in Muon Package Installer and it's not there.  It's also not in Additional Drivers.  How do you uninstall a package installed by Qapt?

---

### Post by pdc on 2013-01-14
pleased to try to help: 

I am not clear why you want to remove the scangear common package:

if I say that each printer/scanner needs 2 packages related to [COLOR="Blue"]scangear[/COLOR] installed:

1) a scangear [COLOR="Blue"]COMMON[/COLOR] package

.........[COLOR="Magenta"]AND[/COLOR]..............

2) the scangear [COLOR="Blue"]SPECIFIC[/COLOR] package for that printer

...........and they need to be installed as ***common first*** and then **specific** .. so that's how you seem to be set up..

.....so you would install the common package ..[COLOR="SeaGreen"]scangearmp-common_1.80-1_i386.deb[/COLOR]..first: (you already have it installed?).....and then to use scangear, you would install the specific MG3100 series ..[COLOR="Green"]scangearmp-mg3100series_1.80-1_i386.deb[/COLOR]

and you could drill down into the scangear package as you did for the printer driver to find what you need......

when you have done that if you copy and paste the command below

> [COLOR="Red"]sudo dpkg -l | grep scangear[/COLOR]

it checks to see all is installed: the 2 packages should be there: (I enclose a thumbnail of my install, as I too have an MG3100 series printer)

to run scangear you type

> [COLOR="Red"]scangearmp[/COLOR]

in a terminal, and to make a launcher ..you may well know how ..

but the command must be [COLOR="Red"]scangearmp[/COLOR]

here is a link for launcher in kubuntu

[http://askubuntu.com/questions/187300/how-to-enable-arrow-keys-in-kubuntu-application-launcher-12-04](http://askubuntu.com/questions/187300/how-to-enable-arrow-keys-in-kubuntu-application-launcher-12-04)

---

### Post by Catbells on 2013-01-15
Hooray! Hooray!  I don't need the Gimp!  the Canon User Guide said that the driver only worked in GIMP and you've shown me that that's not true.  It's much easier.

Everything is working better than ever.

PDC, your instructions are easy to understand and, I like your use of colour.  Thank you for your help particularly as you found some time for me in the late evening.  I feel quite privileged to have such responsive support.

Just in case anyone else finds this page when they are in need of help, I'll explain how to add to the KDE Menu: -

.  Right click on the KickOff button and choose, "Edit Applications..." at the top of the list.
.  The KDE Menu Editor opens.  You'll see two panes.  Above them are a toolbar and the menus.  Click "New Item" on the toolbar and in the right hand pane, add scangearmp in the box marked "Command".  Click save on the toolbar.  
.  Your new item is shown at the top of the tree in the left hand pane and you can drag it wherever you like.  Drop it on top of an item and it will be placed following that item.

---

### Post by pdc on 2013-01-15
oh that is very kind of you catbells..Rosemary?

delighted that all is working well for you: enjoy

thanks for adding the KDE how-to: I just use gnome

my long-suffering wife when I tell her of your thanks may feel there is some benefit from my time on the computer!!

all the best

....oh if you mark the title as SOLVED the ubuntu forum administrators seem to like that ...as you created the thread, only you can do this: that's power for you, isn't it ??  !!

---

### Post by nicraz on 2013-05-11
I know this is already marked as solved but thank you so much for your post. I helped me get my MP495 scanner up and running.

---


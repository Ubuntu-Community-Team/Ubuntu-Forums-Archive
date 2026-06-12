---
title: "Canon Pixma mp280 scanner driver issue"
date: 2013-02-12
forum: Hardware
---

### Post by grubbles444 on 2013-02-12
Hi,

I've been using ubuntu for a while but I can't perform any type of trouble shooting without the aid of google. According to some of the folks on the #ubuntu channel I'm some what ubuntu illiterate, which is ok, I like the resources ubuntu offers and I am trying.

My problem is that I recently found a Canon Pixma mp280 scanner/printer, and upon setup I was able to get the printer working with relative ease by going to system admin, printer, and I guess finding the driver in the kernal (?). So printing is in no way the issue, but the scanner is giving me a lot of problems.

I have downloaded the package _scangearmp-mp280series-1.60-1-deb_ from Canon's site, and after alot of googling I tried playing around with the dpkg -i command. a few of the .deb files in the folder installed but some refused to due to the presents of the others that did. I assume that there is a particular order that I have to install them, but IDk.

I did search this forum for the answer, but even when the problem is specified as a scanner issue, most of the responses always have to do with the printer. It seams as though the scanner issue is actively avoided which makes me wonder what I've got myself into. I did find a site off of this forum which is here:

[U][http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

[/U]It tells me to do the following commands:

Sudo add-apt-repository ppa:michael-gruz/canon
Sudo apt-get update

Both of which worked, but then it tells me to use this command:

Sudo apt-get install _cnijfilter-ip100series_

But to replace the underlined portion with the driver specific to my printer/scanner. all of the listed drivers are printer drivers, but the forum user that posted the link to the site gave the name of the drivers for my printer/scanner: 

scangearmp-mp280series

and the output is this:
sudo apt-get install scangearmp-mp280series
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package scangearmp-mp280series:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'scangearmp-mp280series:i386' has no installation candidate


So I am quite lost. Sorry this is so long but I wanted to be as descriptive as I know how to be as I am determined to fix this. Any help would be greatly appreciated.

Also I have gimp, simplescan, and xzane installed, none of which will recognize the scanner.

---

### Post by pdc on 2013-02-13
hi grubbles;

I suggest you need scangearmp installed;

if you go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100302702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100302702.html)

you will download [COLOR="SeaGreen"]scangearmp-mp280series-1.60-1-deb.tar.gz[/COLOR]

....I suggest you click on your Downloads directory; where this .tar.gz file should arrive into;

if you right-click on the package, and open with archive manager; 

you will see a packages folder: if you open that you will see it contains 32bit and 64bit packages;

as you say you have 32bit???

you need to install [COLOR="SeaGreen"]scangearmp-common_1.60-1_i386.deb[/COLOR] first

so right-click on it, and select "install with gdebi installer";

then right-click on [COLOR="SeaGreen"]scangearmp-mp280series_1.60-1_i386.deb[/COLOR] and do the same:

......you can check it is installed by copying and pasting this command

> [COLOR="Red"]sudo dpkg -l | grep scangear[/COLOR]

and to run scangear, if you type

> [COLOR="Red"]scangearmp[/COLOR] in your terminal, it should open the programme.....and really.......it should do all you need..........you can save the images and manipulate them in GIMP etc if you want to..........

...it helps to have a launcher to run it, 

[http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/](http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/)

this tells you how to do it .........let us know how you get along

---

### Post by grubbles444 on 2013-02-13
Sorry I took so long to reply.

I wasn't aware that i386 meant 32bit. and I thought that amd64 had something to do with an amd processor. I also did not take into consideration this being my issue. But I think it is.

I followed your first few steps, installing the common amd64 .deb instead of the other. do do this I had to figure out what gdebi installer was, but that was easy and after I installed and used it gdebi said that the common file install wsa successful. did the next setep which was to install this "[COLOR=SeaGreen]scangearmp-mp280series_1.60-1_i386.deb" [COLOR=Black]only I tried to install [/COLOR][/COLOR][COLOR=SeaGreen][COLOR=Black][COLOR=SeaGreen]scangearmp-mp280series_1.60-AMD64.deb  [COLOR=Black]instead. This was what gdebi gave me:

Error: Dependency is not satisfiable: scangearmp-common (>= 1.60)

So I skipped forward and used [/COLOR][/COLOR][/COLOR][/COLOR]
[COLOR=Red]sudo dpkg -l | grep scangear

[COLOR=Black]and received: 

jcopacetic@ubuntu:~$ sudo dpkg -l | grep scangear
[sudo] password for jcopacetic: 
ii  scangearmp-common:i386                 1.60-1                                  ScanGear MP for Linux.
ii  scangearmp-mp280series:i386            1.60-1                                  ScanGear MP for Linux.

I assumed that the issue was then that I had somehow installed the 32bit versions of the package and so I should remove them to enable the 64bit packages to install correctly.

This hapened:

jcopacetic@ubuntu:~$ sudo dpkg -r scangearmp-common:i386 
dpkg: dependency problems prevent removal of scangearmp-common:i386:
 scangearmp-mp280series:i386 depends on scangearmp-common (>= 1.60).
dpkg: error processing scangearmp-common:i386 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 scangearmp-common:i386
jcopacetic@ubuntu:~$ sudo dpkg -r scangearmp-common:i386                 1.60-1
dpkg: warning: there's no installed package matching 1.60-1
dpkg: dependency problems prevent removal of scangearmp-common:i386:
 scangearmp-mp280series:i386 depends on scangearmp-common (>= 1.60).
dpkg: error processing scangearmp-common:i386 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 scangearmp-common:i386


So I guess I don't know the names of the files I need to remove (if I do need to remove them)  because even though I copied and pasted from the output of [/COLOR][/COLOR][COLOR=Red]sudo dpkg -l | grep scangear [COLOR=Black], from what I can tell it's telling me that the name of the file is incorrect. Now my head hurts...[/COLOR]
[/COLOR]

---

### Post by grubbles444 on 2013-02-13
I attempted to reinstall scangearmp-common_1.60-1_amd64.deb and I actually paid attention to the terminal output this time and it was this:

dpkg: error processing /home/jcopacetic/.cache/.fr-S8o4GW/scangearmp-mp280series-1.60-1-deb/packages/scangearmp-common_1.60-1_amd64.deb (--install):
 scangearmp-common: 1.60-1 (Multi-Arch: no) is not co-installable with scangearmp-common:i386 1.60-1 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 /home/jcopacetic/.cache/.fr-S8o4GW/scangearmp-mp280series-1.60-1-deb/packages/scangearmp-common_1.60-1_amd64.deb


 So I do have to remove the 32bit packages if I can figure out how.

---

### Post by grubbles444 on 2013-02-13
I used sudo apt-get remove scangearmp_common-i386 and it removed both the common and the mpseries-i386 packages, I then installed both of the 64bit packages with no problems, so I attempted to run scangearmp in the terminal but received an error stating that no scanners could be detected. Here's this:

sudo dpkg -l | grep scangear
[sudo] password for jcopacetic: 
ii  scangearmp-common                      1.60-1                                  ScanGear MP for Linux.
ii  scangearmp-mp280series                 1.60-1                                  ScanGear MP for Linux.

so they did install, but the scanner isn't registering....

---

### Post by pdc on 2013-02-13
so the printer is turned on........and connected via a USB cable directly to the computer.......

..........and it is NOT going through a USB hub..........

......and you have it connected to a USB port that you know works......

and if you type

> [COLOR="Red"]lsusb[/COLOR]........does it show your printer

(the command lsusb asks the system to list ([COLOR="Red"]ls[/COLOR]) the usb connections......)

(my MG3160 shows as Bus 001 Device 007: ID [COLOR="SeaGreen"]04a9:1752[/COLOR] Canon, Inc.)

where 04a9 is the Canon identifier, and the 1752 is the specifics for the MF device

---

### Post by grubbles444 on 2013-02-15
Yeah... my printer works.

Weird thing though. I did some kind of terminal voodoo that involved building a program and installing it called "make" that had something to do with sane, and then after what ever that was finished I typed scangearmp into the terminal, and it didn't detect a scanner again, so I tried sudo scangearmp, and it opened scangear.

I scanned a test page with it. saved the png to my desktop, and did a celebration dance.

I then attempted to open the png in my image viewer, but I don't have permission. So I attempted to import it into gimp, but I don't have permission for that either. So I went to the files properties to try and change the permissions, but I do not own said file therefore cannot change the permissions.

I can only guess that it is because root owns the program, so and products of the program, i.e. scanned images, belong to root also, and cannot not be seen by the likes of me. grrr...

But alas tis a problem for another forum...

---

### Post by pdc on 2013-02-15
some distros have the scanner as part of the [COLOR="Magenta"]lp[/COLOR] group; and with ubuntu, it seems to be part of the [COLOR="Magenta"]scanner[/COLOR] group

[http://askubuntu.com/questions/211447/12-04-scanner-works-fine-as-super-user-but-is-not-recognised-as-a-normal-user](http://askubuntu.com/questions/211447/12-04-scanner-works-fine-as-super-user-but-is-not-recognised-as-a-normal-user)

so you need to be a part of that group

I suggest you try the command

> [COLOR="Red"]sudo adduser[/COLOR] [COLOR="Magenta"]<yourusernamehere>[/COLOR] [COLOR="Red"]scanner[/COLOR]

where <yourusernamehere> is likely to be grubbles444 ?

this thread

[http://www.tuxradar.com/answers/412](http://www.tuxradar.com/answers/412)

talks more about it, if you want to work through it

the command

> [COLOR="Red"]ls -l /dev/{par,lp}*[/COLOR]

will show you all relevant devices and their permissions. 

You can see this post also suggests adding some specifics to the file
[COLOR="SeaGreen"]/etc/udev/rules.d/10/local.rules[/COLOR]

You would do that with the command

> [COLOR="Red"]gksudo gedit /etc/udev/rules.d/10/local.rules[/COLOR]

and then paste what is below into the file that emerges: (it is likely to be a blank file so you are creating this specific entry: it can easily be deleted if you don't like it): I would suggest a reboot after doing all this, 


> [COLOR="Blue"]KERNEL=="parport0", GROUP:="scanner",
MODE:="660", SYMLINK:="scanner"[/COLOR]

---

### Post by BicyclerBoy on 2013-02-16
When this stops being fun & becomes a pain..
The ppa you tried is out-of-date w.r.t multi-arch etc..

The current canon printer/scanner is:
[https://launchpad.net/~michael-gruz/+archive/canon-trunk](https://launchpad.net/~michael-gruz/+archive/canon-trunk)

---

### Post by xruno on 2013-06-05
The driver is officially released by cannon


Printer driver : [http://www.all-driver.com/printer-driver/canon-mp280-printer-driver.html](http://www.all-driver.com/printer-driver/canon-mp280-printer-driver.html)
extract the archive and find the dep packages in the extracted folder... install the deb file that has "common" word in the name first, then the mp280 deb file


the same concept


Download the scanner instructions from here: [http://support-in.canon-asia.com/contents/IN/EN/0300410501.html](http://support-in.canon-asia.com/contents/IN/EN/0300410501.html)

---


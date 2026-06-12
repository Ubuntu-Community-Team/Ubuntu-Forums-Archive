---
title: "Canon MX892 Printer Drivers"
date: 2012-08-16
forum: Hardware
---

### Post by jbartosh on 2012-08-16
Hello, I am trying to get a Canon MX892 all-in-one printer to do simple b&w print functions from my ubuntu 10.04 machine.  I have installed cnijfilter-common & cnijfilter-mx890series packages seemingly successfully from Canon Europe web-site (USA says linux support is unavailable).  When I go through the GUI printer install sequence via system>administration>printing - it recognizes a driver now as a Canon MX890 seemingly with no problems.  Yet, when I go to print, the print job flashes by in the queue super fast and nothing at all happens with the printer - ubuntu gives no indication that anything went wrong.  Any ideas?  Anybody get this printer working on Linux?

---

### Post by jbartosh on 2012-08-19
Would it be easier or possible to get connectivity out of a wired ethernet connection via router instead of using this direct connect USB?  Or would the needed drivers be the same?

---

### Post by unevenflow on 2012-08-19
Hey, from gui remove printer and press add new printer then choose select ppd file and navigate to    [FONT=Ubuntu]usr/share/ppd/ from there choose your printers model .ppd
[/FONT]

---

### Post by jbartosh on 2012-08-19
Thanks for the idea.  I found the .ppd buried in Canon's .rpm.  I extracted that out just to the desktop for testing purposes.  I went through and pointed to the file via the printer setup gui.  It acts like everything should work but still nothing...  Any tips on finding maybe a better .ppd or something?  Maybe download the Windows driver package from Canon and see if there is a .ppd buried within it?

---

### Post by unevenflow on 2012-08-19
Hey, do it the way  i,ve described from **[FONT=Ubuntu]usr/share/ppd/ [/FONT]**[FONT=Ubuntu]and it should work[/FONT][B][FONT=Ubuntu]
[/FONT][/B]

---

### Post by jbartosh on 2012-08-21
Unfortunately that didn't work either.  May be that the driver / ppd doesn't work - like I say Canon USA doesn't supply one - thought I could get by with what seemed to be a Euro equivalent.  It would be great to hear if anybody has gotten this printer going on a Linux machine?  Maybe some generic .ppd I could try?

---

### Post by pdc on 2012-09-05
I am not sure if you have subscribed to this thread;

...........so you may not see this 2 weeks later ..........

I wonder if you have a 64bit system;

many canon drivers are 32bit so they assume to look in /lib for what they want, instead of /lib64 so a symbolic link is needed 

as here 

[http://ubuntuforums.org/showthread.php?t=2021854](http://ubuntuforums.org/showthread.php?t=2021854)

> sudo ln -s /usr/lib /usr/lib64
sudo ln -s /usr/local/lib /usr/local/lib64



---

### Post by aikishugyo on 2012-09-06
You might also try the gutenprint driver that is included with your OS. When you try to add a new printer in CUPS, you can select Canon as the vendor and then the MX890 family driver (it should say something about the gutenprint version as well in the selection---don't choose a foomatic one, for example).

For B/W I think you should have no trouble with the gutenprint driver.

---

### Post by tolbunt5 on 2012-11-30
None of this worked for me. I have Ubuntu 10.04 and my printer is a  Canon Pixma MX892. Brand new and I can't even use it. So  frustrated!!!!!!!  :(

---

### Post by aikishugyo on 2012-11-30
I'm deeply interested only in the gutenprint support for the MX890 family.
So for those of you who want to try the gutenprint driver for printing, please let me know what happens when you try to use it.
Make sure you set CUPS debug on and supply the relevant parts of the debug file output, including of coure the gutenprint part.
You might need to read up on how to set debug in CUPS.
Regards,
Gernot

---

### Post by pdc on 2012-11-30
so tolbunt: welcome to the Ubuntu forums; and welcome to Ubuntu as an operating system; 

Canon make drivers for your printer; so you can install those; or install the open source drivers that aikishugyo and his other hard working colleagues do such an excellent job maintaining and improving continually;

if you want to install the Canon drivers, go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100412202.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100412202.html)

and you can see Canon supply a package for you in debian format, as ubuntu uses debian type packages ............ [COLOR="SeaGreen"]cnijfilter-mx890series-3.70-1-deb.tar.gz[/COLOR]

**LEAVE THE PRINTER TURNED OFF AT THIS STAGE** ..

as you click to download, you will be asked if you want to open with archive manager or save file ...if you select open with archive manager ..when it has downloaded, and opened archive manager, you will see the directory [COLOR="SeaGreen"]cnijfilter-mx890series-3.70-1-deb[/COLOR] and go to the menu bar and EXTRACT to your [COLOR="DarkOrchid"]desktop[/COLOR]; when you click enter to do that, it will show what I enclose as a thumbnail: click on "[COLOR="Blue"]Show the Files[/COLOR]" and now left click on the [COLOR="Magenta"]install.sh[/COLOR] file 

......it will open up the second "*what do you want to do*" box that I have called [COLOR="Plum"]**run_in_terminal**[/COLOR] ............. so select the left option of "[COLOR="Blue"]run in terminal[/COLOR]" ............and that should ............open a terminal.......that will run and .............install the driver .......

and you should then able to print .......

Canon also provide a scanner programme ScanGearMP that installs in a similar way ..........

.......let us know how it goes............

---

### Post by ECE NY on 2013-01-09
So In searching for a driver for my new MX892 I found this site and your post... Hopefully you got your printer working by now.  However for those that have not.  I found that the Canon site in asia does have a linux version of a driver for the MX890 series printers.
link:  [http://support-sg.canon-asia.com/P/search?model=PIXMA+MX897&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-sg.canon-asia.com/P/search?model=PIXMA+MX897&menu=download&filter=0&tagname=g_os&g_os=Linux)

I may not be the most graceful when it comes to Linux terminology yet, but this is what I did.
1-- saved all the support files from the asia Canon support site.
2-- from the downloads directory (where i saved to) I double clicked on the one file that was for the print driver "cnijfilter-mx890series-3.70-1-deb.tar.gz"
this opened up the archive manager
3-- I proceeded by double clicking on the only directory shown "cnijfilter-mx890series-3.70-1-deb"
4--Double clicked on the "packages" folder
5--Double clicked on the "cnijfilter-common-3.70-1_i386.deb" file which opened it up in Ubuntu Software Center where I selected "install"
6--Once installed I went back to the archive manager and double clicked on the "cnijfilter-mx890series-3.70-1_i386.deb" file and again selected install in the Ubuntu Software Center
7-- follow normal Ubuntu printer install.
So  then you have to go through the System Settings and select the printer icon to install the printer... this time I saw two MX890 series printer under network printers. before I saw the MX890 and then the IP address, not there was "MX890 'and the MAC address'" 
I selected the new one and proceeded on.  after that it did a search for drivers and then it brought up a window for the printer name and long name and location, I just left them as it and clicked next or finish.  
Then I printed a test page and got a Ubuntu printer test page in color it told me the PPD file name which is CNMX890.PPD

well this is more then long... also my first post on this forum... hope it helps some others out!;)

if for some reason that link doesn't work just chop off all the stuff after ".com" and then navigate to the driver support section to download the RPMs or Deb archive files.  When I was navigating I didn't see a MX892 device only a MX897 device... They are the same series so long story short it still works... for ubuntu you want to download the deb.tar.gz files. 

I am running Ubuntu 12.04LTS on a dell inspiron mini (netbook) 32 bit... 64bit drivers are available in the same link however.
I downloaded the all the files that they supply just to make sure i will have them for future use.

---

### Post by pdc on 2013-01-10
well done; great that it is all working; 

.........as you say..one can have an MX892 or MX894 or 897 or whatever..the driver for all is the 890 series driver.............

.....and life is much simpler for you with a 32bit driver!! well done

---

### Post by emagin on 2013-01-14
This did the trick for me as well using peppermint os 3. 
Thank you, helped me out a lot!

Don't forget that the MX892 series is Google Cloud Print ready, so you can always set up the printer in your GApps account and then print to it from anywhere in the world.

QUOTE=ECE NY;12447504]
5--Double clicked on the "cnijfilter-common-3.70-1_i386.deb" file which opened it up in Ubuntu Software Center where I selected "install"
6--Once installed I went back to the archive manager and double clicked on the "cnijfilter-mx890series-3.70-1_i386.deb" file and again selected install in the Ubuntu Software Center[/QUOTE]

---

### Post by pdc on 2013-01-14
thanks:

> Don't forget that the MX892 series is Google Cloud Print ready, so you can always set up the printer in your GApps account and then print to it from anywhere in the world.

........yet another thing for me to read up and learn about !!

---


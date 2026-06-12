---
title: "Brother all-in-one printer MFC J430W"
date: 2014-03-24
forum: Hardware
---

### Post by BrandonE on 2014-03-24
I have completed a barebones build and installed the current Xubuntu LTS, the goal being to migrate away from XP for the main household computer. An important part of that goal is to be able to accomplish the complete process without using terminal for any step, everything went well until I went to hook up my Brother all-in-one printer (MFC J430W) which is not shown in the list of available drivers. My question to the group is do some of the Ubuntu distros have more driver support than others? Has anyone tried any of the listed drivers to see if they work on other models, and if I install drivers that don't work is there any way to remove them in order to try another set?

Remember the goal is to avoid terminal, this may ruffle some feathers but as a fan of Linux I want to be able to demonstrate to others interested in a new OS that the conversion is doable. 

Thanks in advance for any help

---

### Post by gifford on 2014-03-24
I can appreciate what you are trying to do but am not sure if you can do it.
Here is a link for the Brother installer, which indicates your printer is compatible. I have never used it so hope it will work for you. [http://support.brother.com/g/b/downloadend.aspx?c=eu_ot&lang=en&prod=dcp7055_all&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=eu_ot&lang=en&prod=dcp7055_all&os=128&dlid=dlf006893_000&flang=4&type3=625)

For your information, Brother supports Linux and Ubuntu very well. But, all of the installation of drivers and set up I have always done by the command line following the instructions on the Brother site.

---

### Post by ajgreeny on 2014-03-24
Why are you so fearful of the terminal?

I can understand perhaps, you wanting to avoid all your family having to learn how to use terminal, though I am not at all sure it is a valid fear for any of you, and surely there must be a way that one of your number can take up the cudgel and become familiar with using the terminal.

If I remember correctly from when I had a Brother machine, it was necessary to install two .deb driver packages, one for printer, the second for scanner, and the only way that was possible, as each was deperndent on the other, was to use the terminal and command ```
sudo dpkg -i file1.deb file2.deb
```It was not possible to do the job one at a time by double clicking on the packages one by one.

There! Not too difficult was it?  And you will quickly learn how incredibly useful the terminal can be to get information about your hardware and software, and to carry out many other activities.

---

### Post by BrandonE on 2014-03-25
Thank you for understanding my point of view. I will continue to poke around and see if I can come up with a solution but I'm afraid my hopes for a total Linux household have faded for now and the XP machine will stay put.

---

### Post by Mark Phelps on 2014-03-25
> An important part of that goal is to be able to accomplish the complete process without using terminal for any step

You combining two very different aspects of Linux usage: casual usage and system administration.  The former can be done regularly without having to resort to terminal usage; the latter can not.

When you convert a household to Linux, YOU become the system administrator; you are the one faced with configuring and maintaining the systems.

I can assure you from personal and professional experience that being the system administrator for Windows systems ALSO involves the use of command lines; not everything can be done using a GUI.

---

### Post by pqwoerituytrueiwoq on 2014-03-25
if you want to impress someone with linux and printing plug a hp printer into the usb port when you are using it and watch it magically just start working without you clicking a single thing (works with most models depending on when the model was made and when that version of ubuntu was released)

there is a guide for your printer and 12.04 LTS
[http://ithinkthereforeiforget.blogspot.com/2012/11/installing-brother-mfc-j430w-on-ubuntu.html](http://ithinkthereforeiforget.blogspot.com/2012/11/installing-brother-mfc-j430w-on-ubuntu.html)

---

### Post by mastablasta on 2014-03-26
oh yes, my HP go t recognised and working while it was off (only USB cabel was plugged it and it had power but it was turned off ). ubutnu just found it, instaleld it and told me it's ready for printing. i didn't even ask to do that.

as for the drivers they don't have much to do with linux. it's the way your printer company packaged them. they could have probably made just one package that could be opened in software center with no terminal use. anyway who cares you do it once and then probably never again (well at least until next upgrade). an option is to put command into a script make it executable put an icon and then you only double click the icon to trigger the install. why brother didn't make it like that ? well who knows. actually they know and they might answer this question.

---

### Post by pdc on 2014-03-26
Hi Brandon: the brother printer asks for two debian packages to be installed:

[COLOR="#0000FF"]lpr[/COLOR] first and then the [COLOR="#0000FF"]cupswrapper[/COLOR]; 

from here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J430W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J430W)

the[COLOR="#0000FF"] lpr[/COLOR] link is [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj430wlpr-3.0.1-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj430wlpr-3.0.1-1.i386.deb&lang=English_lpr)

and the [COLOR="#0000FF"]cupswrapper[/COLOR] link is [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj430wcupswrapper-3.0.0-1.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfcj430wcupswrapper-3.0.0-1.i386.deb&lang=English_gpl)

download them to your Downloads folder; open that from your desktop; right-click on the [COLOR="#0000FF"]lpr[/COLOR] icon first and select *[COLOR="#008000"]install with gdebi installer[/COLOR]*; enter your sudo password when asked; then the [COLOR="#0000FF"]cupswrapper[/COLOR] and that should have the printer working;

_____________

try that; let us know how it goes

---

### Post by BrandonE on 2014-03-27
Thank you "pdc" the printer did work after doing what you suggested, tried doing the same thing with the scanner downloads with no luck. Once again thanks to those who have tried to get this going without command line. Fifteen years I have been following Linux looking forward to the day it would overtake you know who but unfortunately it will NEVER happen. Don't bother with a reply I am signing off...

---

### Post by pdc on 2014-03-28
I thought to enter a note here that for anyone following after this: looking for the instructions to install the scanner driver for the MFC: 

**step 1)** it needs the br4 driver and you need to know if you have 32bit or 64bit system; and so get the right driver from here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html) 

it comes down as a .deb package so when you click to download the system may offer you the option of "install with gdebi installer": if you do that, it will be installed and you will be asked for your sudo password;

__________________________________________

**_There is a step 2_**, as described here

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u13.04](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_scn1c.html#u13.04)

the commands to do it, that you copy and paste into a terminal are:

> [COLOR="#FF0000"]gksudo gedit /lib/udev/rules.d/40-libsane.rules[/COLOR]

........those commands use the text editor gedit to open the file quoted above; and opens gedit with sudo powers to edit the file: you could safely read the file only by pasting > gedit /lib/udev/rules.d/40-libsane.rules into a terminal instead ..............

2. ..........*so having opened the file with gedit* .......... [COLOR="#008000"]**Add the following two lines to the end of the device list**[/COLOR]. (Before the line "# The following rule will disable ..."):
If there is "LABEL="libsane_rules_end"", add the following 2 lines before "LABEL="libsane_rules_end"".

The lines to be added .............are ..............

> [COLOR="#0000FF"]# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/COLOR]

Save; Close; reboot .............hopefully the scanner will do its work

---


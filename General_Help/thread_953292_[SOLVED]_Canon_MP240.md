---
title: "[SOLVED] Canon MP240"
date: 2008-10-20
forum: General Help
---

### Post by icore-skippy on 2008-10-20
Does anyone have any clues on getting a Canon MP240 multifunction printer to work with Hardy 8.04?

I can't get the unit to print or scan. The printer appears to be receiving data via the USB cable, but there is no printout. I have tried using a number of different drivers (as there isn't one specially for the MP240).

XSane tells me no devices are available.

The printer is working fine with (spit) Windows XP.

The setup was working perfectly with Canon MP150 until that printer died over the weekend.

Any help greatly appreciated.

---

### Post by BriFranJoy on 2008-10-20
My first posting.  How about sympathy?  I'm here because I have a Canon Pixma MP 160 and XSane gives me and an error message.  Have you tried downloading Kooka from the "Add Applications" menu?

---

### Post by icore-skippy on 2008-10-20
I downloaded Kooka 0.44 but 'Settings => Select scan device' doesn't see the MP240, which makes me believe there is something unusual about the USB protocols Canon is using on this printer/scanner.

---

### Post by bsv on 2008-11-07
Hi,

I was wondering if you've had any luck getting the MP240 to work since your last post? I'm in the same boat and outta ideas!

Cheers,
Ben.

---

### Post by icore-skippy on 2008-11-07
No joy as yet. :(

---

### Post by bsv on 2008-11-07
hmmmmmmmm that's a shame :(

Luckily I have a dual boot machine so I can use windoze to print/scan but this is hardly a long-term solution. I rang Canon Australia today to inquire if they're going to release any Linux drivers and was told that if it's not on the website then they can't talk about it, very helpful!

Another possibility that crossed my mind was to install the windows drivers under crossover/wine. But I'm not sure if when I use a Linux program, ie. OpenOffice to print whether it will know anything about the windows based drivers, probably not. Didn't get to that point though because the crossover installation of the drivers failed :(

Anyway post here if you have any luck and I'll do the same.

Cheers,
Ben.

---

### Post by sirwilliamthenice on 2008-12-05
[http://software.canon-europe.com/products/0010645.asp](http://software.canon-europe.com/products/0010645.asp)

is the link for the drivers released on the cannon site in the last day or so.

---

### Post by icore-skippy on 2008-12-05
Thanks sirwilliamthenice, I'll grab that now.

Ooherr, it's a TAR file. How do I install that?

---

### Post by sirwilliamthenice on 2008-12-05
Yeah
 I'm a n00b. 
I extracted it and there were two more tars
scanner and printer
so i untarred printer
and there were two deb files
i ran them. 

not working for me... but. im using #!crunchbang linux, (ubuntu based) not debian.

---

### Post by sirwilliamthenice on 2008-12-05
Gone! Deleted!:shock::shock:
I wasn't insane.. Those drivers arn't there anymore. 
I have them on my Desktop.. 
Not working.. but there in a tar all the same. 

Argghhhhh

---

### Post by icore-skippy on 2008-12-05
Yahoo! I have a functioning printer (although not the scanner as yet).

Here is what I did:

As root user, download the file MP240_debian_drivers.tar from here:

[http://software.canon-europe.com/products/0010645.asp](http://software.canon-europe.com/products/0010645.asp)

the site found by sirwilliamthenice.

Expanded that archive to get the archives

- MP240_debian_printer.tar
- MP240_debian_scangear.tar

The archive - MP240_debian_printer.tar expands to give the archives/directories

- cnijfilter-common-3.00-1.tar.gz
- cnijfilter-common-3.00-1._i386.deb
- cnijfilter-mp240series_3.00-1_i386.deb

The archive - cnijfilter-common-3.00-1.tar.gz expands to give the directory

- cnijfilter-common-3.00

This directory contains a directory ppd

which contains the file

- canonmp240.ppd


I ran:

- cnijfilter-common-3.00-1._i386.deb
- cnijfilter-mp240series_3.00-1_i386.deb

simply by double-clicking on them. 

Powered up the printer, went to

System 
      - Administration 
                      - Printing

- New printer

- Select CanonMP240 from the list

- Forward

- Provide ppd

- Browse to the file - canonmp240.ppd

Then follow the prompts.


Anyone who can get the scanner functioning properly will be a hero. Beyond my meager Ubuntu abilities, but I'll keep plugging at it.

---

### Post by icore-skippy on 2008-12-05
I now have the scanner working.

The archive 

- scangearmp-common_1.20-1.tar.gz

contains the folders

- scangearmp-common_1.20-1_i386.deb
- scangearmp-mp240series_1.20-1_i386.deb
- scangearmp-common-1.20

I ran the files 

- scangearmp-common_1.20-1_i386.deb
- scangearmp-mp240series_1.20-1_i386.deb

and the scanner is now seen and functions through GIMP, but is still not seen by Xsane.

To use, load GIMP.

File
____ Acquire

____________ Scangear MP

Works a treat!

I hope this information is of use to others with this MP printer, and a tip of the hat to Canon for supporting Linux and releasing these drivers.

---

### Post by bsv on 2008-12-06
Hey sirwilliamthenice,

Can you post that tar file somewhere other people could grab it? Or I could pm to get a copy. I have this printer and would LOVE to get it working in Ubuntu.

Cheers!

---

### Post by icore-skippy on 2008-12-06
Check to see if you can access the tar here:

[http://software.canon-europe.com/products/0010645.asp](http://software.canon-europe.com/products/0010645.asp)

You need to select this link:

	1.   Debian Linux Printer & Scanner Drivers (3.0) 

Scroll to the bottom of the page and select this link:

MP240_debian_drivers.tar  	 	12301 Kb.

Accept the license agreement and it should download for you.

PM me if you can't grab it from Canon's site.

---

### Post by bsv on 2008-12-06
hmmmmm either I'm going blind or Canon is doing something weird! I would swear on my first born that link wasn't there an hour ago!!! 

I feel the need to make up some devious and complicated conspiracy theory to cover for me not being able to read ;P

Thanks icore-skippy got the file and will now try to get it up and running.

Cheers,
Ben.

---

### Post by bsv on 2008-12-07
It worked for me too! Thanks guys for working this out, very chuffed :)

---

### Post by icore-skippy on 2008-12-07
Excellent news bsv! Great printer, and the scanner interface via GIMP is neat too.

---

### Post by pompeyjohn on 2008-12-12
Somebody please help

Unless I am blind - the file is no longer there.

If anyone has it would they PLEASE PLEASE PLEASE email it me. Pretty please :)

[email]john@mulhollandonline.com[/email]

---

### Post by icore-skippy on 2008-12-12
Hi pompeyjohn, the file is still there when I go to the link.:confused: IIRC bsv had the same problem when looking for it. What do you see when you go to that link? You could try selecting the 'OS' and 'language' and see if that discloses the download link for you. My ISP will choke if I try to email a 12mb tar to you.

---

### Post by RomanIvanov on 2008-12-12
It might be irrelevant but read [https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900), I hope similar steps will help you

---

### Post by pompeyjohn on 2008-12-12
thanks for the replies

at that link I see two drop down boxes

Operating system  	   	
Language

There is a linux option in the Operating system drop down. No matter what combination of drop downs I select I can not get the file to display in the box below. If I select XP and English - I can see the XP driver. But for me selecting Linux and either english or any language, returns nothing.

AARGH

edit - just tied internet explorer to see if it was a browser issue - still nothing.

---

### Post by pompeyjohn on 2008-12-12
Aaargh WTF is going on?!

perhaps they are limiting access via IP address? It is a European site [presumably] and I am in North America.

---

### Post by pompeyjohn on 2008-12-12
WOO HOO!

It *WAS* the IP location. I installed foyproxy and set up a British proxy; and now I have the file :)

WOO HOO!

If anyone else has the same issues I suggest trying that. 

Interested to hear from anyone who is using this driver with CUPS for a printer attached to a vista machine.

Happy printing and Happy Linux everyone :)

---

### Post by reloadtek on 2009-01-07
Is there a way to install these drivers under amd64?

---

### Post by elliott.montana on 2009-01-17
Nice one sirwilliamthenice on finding those drivers.
Micro$oft pay to make that hard.

To install the 32-bit printer drivers on an amd64 system

Follow icore-skippys post on page 2 for the printer but when he asks you to install the .deb packages do this instead:

Extract "cnijfilter-common-3.00.tar.gz"
Open a terminal
$ sudo apt-get install libtool
In terminal, go to your extracted "cnijfilter-common-3.00" folder
$ sudo dpkg-buildpackage
The installation will most likely stop with the error "there are dependent packages to install": if it does stop and calls for dependencies start "symaptic package manager" from "System" "Administration" to search and install the required packages. After doing this repeat the last terminal command.

Nuts eh. Just glad to give back to the community.
[live without dead time]

---

### Post by elliott.montana on 2009-01-17
A scanner would be nice though.

---

### Post by the_eternal_dark on 2009-01-24
> **elliott.montana said:**
> A scanner would be nice though.

Got you covered.

To install and get a properly working pixma mp240 scanner in 64bit Ubuntu, have sane and xsane already installed from the repo (for some reason, I couldnt get xsane to act right if I installed it after compiling sane).

Go [[COLOR="Blue"]here[/COLOR]]("http://alioth.debian.org/scm/?group_id=30186") and pick up the Nightly CVS Snapshot, then get libusb-dev from synaptic if you don't already have it.

The easiest way, save it to your desktop and extract all contents, I have a folder called sane-scm-2009-01-24. Within this folder are multiple other folders, our focus is on "sane-backends".

Open terminal:

```
$ cd sane-backends
```

Then type:
```
$ ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
```

Now you will have to wait a few moments. Once the wait is through, proceed with:

```
$ make
```

Wait again, this time for a bit longer, and when its done, run:

```
$ sudo make install
```

And you should be done, and when you run ```
$ scanimage -L
``` you should see your scanner listed and then you should be able to use xsane to scan all you could ever want in Ubuntu 8.10 64-bit. Now all we need is a .deb and this will be a walk in the park.




Now the printer was as simple extracting the 2 .deb files from MP240_debian_printer.tar (inside MP240_debian_drivers.tar) to the desktop and running:

```
$ dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb
```

followed by

```
$ dpkg -i --force-architecture cnijfilter-mp240series_3.00-1_i386.deb
```

and then printing a test page, which looks beautiful, btw.


**Let me know if I left anything out, it is very late here and I am very VERY tired..**

---

### Post by ender353 on 2009-02-09
Hey thanks a lot for the instructions! I got the printer working fine but the scanner is still not working i ran the 2 .deb files you mentioned but it still does not work. I can see scangear mp in gimp but when i click on it nothing happens. Help! :)

---

### Post by waxyfresh on 2009-02-13
> **ender353 said:**
> Hey thanks a lot for the instructions! I got the printer working fine but the scanner is still not working i ran the 2 .deb files you mentioned but it still does not work. I can see scangear mp in gimp but when i click on it nothing happens. Help! :)

Im having the same problems with the 32bit drivers!

---

### Post by murataht on 2009-03-06
Thanks, this worked for me, too.

but for those who have problems with scanner, try to run the scanner program form the command line.

```

scangearmp
```

this should give you more information about why the scanner is not working.

Please note that if the scanner is not connected, the program will not work. so, please connect and turn on the scanner before try this.

---

### Post by Jdizzel on 2009-03-15
I sucsesfully provided the canon mp240 ppd file under "change driver" in printer coniguration.
But then it says that it requires the "pstocanonji" program wich is not installed.

I am new to linux and i know how to accsess the terminal but i am unformilular with the language and have very limited programing expearinace. 

Any help would be much appreshiated

---

### Post by irok84 on 2009-03-17
Hi. 

Do You know how to check ink state in Canon MP240 on linux?


Drivers from canon site are packed with four commands:
cngpijmonmp240
cifmp240
printuimp240
lgmonmp240

but i dont know how to check ink status. 
This commands don't put errors on console.

Please help.

---

### Post by ArduinoFun on 2009-04-25
I am new to Linux also, and have this same printer which I can not get to print. I unpacked all the files, clicked on them. It went through some sort of set up. Then I added my printer and told the system where the PPD file was. Tried a test print. Says it was sent to the printer, but nothing. Opened up a doc, typed some text, hit print. says it went to the printer and was complete, etc. still nothing.

This is a bummer. I need to get the printer and scanner working. I have too many papers due, etc. to not have this. I will have to go back to using Windows, and I really dont want that. I like Ubuntu.

Any help is appreciated. Thank you in advance for your time.

---

### Post by ArduinoFun on 2009-04-25
I got it working. I used Computer janitor to remove my prior attempts and then went through the steps all over again and its working!

---

### Post by linkhouse on 2009-04-25
.

---

### Post by billybag on 2009-06-25
I still cant get scanner to work at all.

$ scangearmp
Cannot find Canon MFP scanner device.

$ scanimage -L
device `v4l:/dev/video0' is a Noname Laptop Integrated Webcam virtual device

---

### Post by jmort253 on 2009-07-05
Hi BillyBop,

I got that same error message, so I just tried running it using sudo:

```

sudo scangearmp

```This worked, I was able to scan a document as a PDF successfully!  Although I have to run with sudo, it works, and that's good enough for now!

James

---

### Post by mcbride_62 on 2009-07-23
I had a similar problem with an MP810.  You need to alter the permissions of the USB device so that it is not only accessible by root.  As always, it is best to make a backup of the file that you are altering prior to edit...

In /etc/udev/rules.d/40-basic-permissions.rules:

change:
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"

to:
# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"

You must reboot Ubuntu after making this change.

---

### Post by rwbest on 2009-08-02
It took me a long time to find HOW this problem was SOLVED but finally the MP240 works, both printing and scanning, on Ubuntu 8.10 and also 9.04.

I was guided by post #11 and 12, not working as root, being prompted for password, unpacked all deb files using Extract Here option, didn't use PPD dirs, installed with GDebi Package Installer option.

I start the scanner on the command line, see post #30, don't know how to use GIMP for this. Scangearmp works very good!

Robert

---

### Post by cmu on 2009-08-08
> **elliott.montana said:**
> 
To install the 32-bit printer drivers on an amd64 system

Follow icore-skippys post on page 2 for the printer but when he asks you to install the .deb packages do this instead:

Extract "cnijfilter-common-3.00.tar.gz"
Open a terminal
$ sudo apt-get install libtool
In terminal, go to your extracted "cnijfilter-common-3.00" folder
$ sudo dpkg-buildpackage
The installation will most likely stop with the error "there are dependent packages to install": if it does stop and calls for dependencies start "symaptic package manager" from "System" "Administration" to search and install the required packages. After doing this repeat the last terminal command.


Thanks for posting, elliott.montana, but it didn't work for me.
Anybody got an idea ?

I tried 
sudo apt-get install libtool (was already latest version)
cd cnijfilter-common-3.00
sudo dpkg-buildpackage
[ ... lots of configure and make output ... ]
First error I hit is:
make[1]: Entering directory `cnijfilter-common-3.00/cnijfilter'
make  all-recursive
make[2]: Entering directory `cnijfilter-common-3.00/cnijfilter'
Making all in src
make[3]: Entering directory `cnijfilter-common-3.00/cnijfilter/src'
gcc  -O2 -L../../333/libs_bin -Wl,-Bsymbolic-functions -o cif bjferror.o bjfilter.o bjfimage.o bjfoption.o bjfpos.o bjfrcaccess.o getipc.o bjflist.o -lcnbpcmcm333 -lcnbpess333 -lm -ldl -ltiff -lpng -lcnbpcnclapi333 -lcnbpcnclbjcmd333 -lcnbpcnclui333 -lpopt 
/usr/bin/ld: skipping incompatible ../../333/libs_bin/libcnbpcmcm333.so when searching for -lcnbpcmcm333
/usr/bin/ld: cannot find -lcnbpcmcm333

Now I know that is because of the 32-bit library libcnbpcmcm333.so:
333/libs_bin/libcnbpcmcm333.so: symbolic link to `libcnbpcmcm333.so.7.03.1'
333/libs_bin/libcnbpcmcm333.so.7.03.1: ELF 32-bit LSB shared object ...

What am I missing here ?

---

### Post by energy_One on 2009-08-28
Post 27 was the most helpful for me (Ubuntu 9.04 64-bit is my current OS). The test page printed perfectly, but unfortunately xsane doesn't seem to have permission to access the scanner without being run sudo.

Also, when I tested via 'sudo xsane' and pressing the 'Scan' button, the device immediately began scanning, and the picture came out grainy. Doesn't the lamp need to warm up first?

I won't be testing scanning further until I can figure out proper permissions and wrap my head around xsane (maybe -I'm- doing something wrong).

---

### Post by wactuary on 2009-09-03
I was setting up this printer for a friend in Jaunty.  It seems the package on the Canon website has a dependency on libcupsys2, but Jaunty now uses libcups2.  By installing using the --force-depends switch with dpkg for both .debs, I was able to get the printer working.

Thanks for the help from this thread!  Extremely useful!

---

### Post by elri07 on 2009-09-24
Hello,
I'm unable to install printer driver on ubuntu 64 bits. I've tried all solutiions in this post!
Any new Idea please? Help !

Sorry for bad english :s.

Thanks for help!

Elie

---

### Post by Chainy on 2009-09-26
> **Jdizzel said:**
> I sucsesfully provided the canon mp240 ppd file under "change driver" in printer coniguration.
But then it says that it requires the "pstocanonji" program wich is not installed.

I am new to linux and i know how to accsess the terminal but i am unformilular with the language and have very limited programing expearinace. 

Any help would be much appreshiated

I also got the message that  "pstocanonji" is required, but then I found out that it was simply because I had not done the installation properly. This was mainly due to the fact that I'm also rather new to linux and so I missed an obvious step! 

Here's a full explanation of how I installed everything correctly (the same as what icore-skippy explains in post number 11 on this thread, but with a couple extra details!)

**Downloading the driver from the Canon website:**

I downloaded the file "MP240_debian_drivers.tar" from the Canon website ([http://software.canon-europe.com/products/0010645.asp](http://software.canon-europe.com/products/0010645.asp)). On this page, you have to select "Linux" and then your language in the drop down menus at the top. Press submit. Then click on the link "Debian Linux Printer & Scanner Drivers (3.0)", which takes you to a screen with a lot of writing on it, something to do with an agreement for using the driver. Scroll down to the bottom of this page to the part titled 'Downloads'. Click on the link "MP240_debian_drivers.tar". This then takes you to a page titled "Software License Agreement". At the bottom, click on the little box 'I accept' and then click on the box "Download Software"!! It will start downloading (at last!). In my case a box popped up asking me where I want to save the file. You can either open it immediately with the archive manager, or save it somewhere. I saved mine to the desktop, just so I knew where it was. 

**Installation of Driver:**

I then double clicked on the "MP240_debian_drivers.tar", which was now on my desktop. This causes the archive manager to open (or expand) it. A screen pops up where you will see the following listed:
- MP240_debian_printer.tar
- MP240_debian_scangear.tar

Focussing just on the printer for now, I selected (highlighted) the "MP240_debian_printer.tar" and then clicked the button "Extract", which is on top panel of the Archive Manager. A box pops up and you should see that it says "Extraction completed successfully". Just click "close". Also close the archive manager for now. Then go back to same place as "MP240_debian_printer.tar" and you will now see a new file called "MP240_debian_printer.tar" (this is the result of the extraction!). Double click on this file, which again opens the archive manager. This time you will see three things listed:
- cnijfilter-common-3.00-1.tar.gz
- cnijfilter-common-3.00-1._i386.deb
- cnijfilter-mp240series_3.00-1_i386.deb

Don't click or highlight any of them (Make sure none of them is highlighted, otherwise you will end up just extracting one of them!). Then click "Extract" and then you will have the above three files on your desktop (again, located in the same place as the "MP240_debian_printer.tar" - in my case, this was the desktop.) 

Double click on "cnijfilter-common-3.00-1._i386.deb" to run the installation process. But be careful here, as this is where I made my silly mistake! :-). A package Installer pops up and it kind of looked like it was already installing quite happily, but it wasn't! The initial activity is just the Package Installer checking the dependencies... The blue line shows the progress of this check. Then when it's finished you'll see in the Package Installer window "Status: All dependencies are satisfied". **Don't close the Package Installer yet!!** (that's what I did the first time!) Now, you have to click on the box at the top right hand side of the Package Installer window, where it says "Install Package"!! You'll be asked for you password, put it in. A box pops up showing the progress of the installation. On one occasion this didn't work too well for some reason and the installation failed, but the system told me what to do. It asked me to do something in the Terminal. I just did as it said and then it worked fine. But, hopefully you won't see this extra complication. I think it's just got something to do with having to run as root... I just had to write a line in the terminal beginning with "sudo install..." Something like that. Sorry, I've forgotten the exact thing now. Once I had written it in the terminal, I just hit enter and then it all worked out fine.

Then do the same with "cnijfilter-mp240series_3.00-1_i386.deb". Double click it to run the installation process. **After the dependencies have been checked don't forget to click install!** :-)

**Important note:** I think it's important to install "cnijfilter-common-3.00-1._i386.deb" **BEFORE** "cnijfilter-mp240series_3.00-1_i386.deb". This is because the latter depends on some things in the first one.

Then I plugged in the printer, attached it to the computer via the USB. And as Icore-skippy says, go to 
System 
- Administration 
- Printing

- New printer

- Select CanonMP240 from the list

- Forward

- Provide ppd

- Browse to the file - canonmp240.ppd.

Follow the prompts...

(icore-skippy explains in post 11 of this thread how to find the canonmp240.ppd file).

---

### Post by Chainy on 2009-09-26
> **icore-skippy said:**
> 

and the scanner is now seen and functions through GIMP, but is still not seen by Xsane.

To use, load GIMP.

File
____ Acquire

____________ Scangear MP

Works a treat!


Just a little note about using the scanner with GIMP. It seems GIMP has changed its menus a bit as I couldn't find 'Acquire' in the 'File' section. You have to click on "File" and then click on "Create". You will then see the MP240 scanner listed there. And yes, it does, indeed, work a treat! :-)

Thank you, icore-skippy, for your help with all of this. It's much appreciated!

---

### Post by elri07 on 2009-09-26
But what about 64 bits...? :confused:

---

### Post by synaptic.flaws on 2009-09-27
HI

I am getting this error
/usr/lib/cups/filter/pstocanonij failed
I followed the instructions for the printer only from post 27 in this thread

the printer seems to be detected correctly now but I am unable to print from any application I have tried.

Any help would be appreciated

---

### Post by sumpm1 on 2009-11-03
Hey guys. I was previously using Ubuntu 8.10 and had the MP240 working fine. I now have installed Ubuntu 9.10 and get errors when trying to install. Instead of sit here and describe all of my errors, I made a video of the install process. I could really use some help on this, cause I can't really live without the use of my printer!

Here is the link to the video: [http://www.youtube.com/watch?v=WX2CqHLfnDQ](http://www.youtube.com/watch?v=WX2CqHLfnDQ)

Thanks

---

### Post by Chainy on 2009-11-03
> **sumpm1 said:**
> Hey guys. I was previously using Ubuntu 8.10 and had the MP240 working fine. I now have installed Ubuntu 9.10 and get errors when trying to install. Instead of sit here and describe all of my errors, I made a video of the install process. I could really use some help on this, cause I can't really live without the use of my printer!

Here is the link to the video: [http://www.youtube.com/watch?v=WX2CqHLfnDQ](http://www.youtube.com/watch?v=WX2CqHLfnDQ)

Thanks


Hello! I don't think this is a big problem. I got the same thing when I installed the driver. Look at my posts in this thread. Make sure you do things in the correct order.

You seemed to be doing things correctly, though. Just one thing - when the installer hits a problem on the way and the box pops up with the message about running "sudo apt-get install -f" in the terminal, I did this whilst leaving the installer open. So leave the installer open - don't close it. Open the terminal and do what it says and it will probably run just fine. It did with me. If you still get a problem about dependencies, then double check that you are installing things in the correct order - see my previous posts!

I think the reason why the installer encounters such a problem is that you are not logged in as root (which is a good thing!). That's why it asks you to run that command in the terminal, which then asks you for your password so that things work ok. The 'sudo' bit enables just this command to be executed with root permissions.

---

### Post by nloewen on 2009-11-04
It's more that just a problem with privileges or installing the packages in the right order. The package from canon depends on libcupsys2, however it cannot be installed because installing libcupsys2 selects libcups2 (I'm guessing it replaced the other package?). The driver probably needs to be recompiled.

If someone could post instructions on how to do that in karmic that would be great as I'm having this problem as well.

---

### Post by Chainy on 2009-11-05
> **nloewen said:**
> It's more that just a problem with privileges or installing the packages in the right order. The package from canon depends on libcupsys2, however it cannot be installed because installing libcupsys2 selects libcups2 (I'm guessing it replaced the other package?). The driver probably needs to be recompiled.

If someone could post instructions on how to do that in karmic that would be great as I'm having this problem as well.

Are you sure that you are not just over-complicating things here?! Everything works just fine on a 32-bit PC installation. Are you perhaps using a 64-bit installation? I have no idea what you mean by libcupsys2 or libcups2 - I don't remember seeing either of these during my installation of the Canon driver. If the Ubuntu 9.04 system is installed properly on the machine, then the Canon drivers work just fine. Just click on them (as in my instructions earlier) and away you go. Forget about recompiling etc! (I don't even know what you mean by that!) I like to keep things simple! 

I wonder how sumpm1 is getting on?

---

### Post by nloewen on 2009-11-05
sorry, I should have been more specific. It 9.04 it works fine and the problem the person is having is probably just installation order or permissions.

In 9.10, it shows that all dependencies are satisfied, but when you install it you get this message
"dpkg: dependency problems prevent configuration of cnijfilter-common:
  cnijfilter-common depends on libcupsys2 (>= 1.2.1); however:
   Package libcupsys2 is not installed.
 dpkg: error processing cnijfilter-common (--install):
  dependency problems - leaving unconfigured"
running "sudo apt-get install -f" removes the cnijfilter-common package and running "sudo apt-get install libcupsys2" gives the message
"Note, selecting libcups2 instead of libcupsys2
 libcups2 is already the newest version."

I may have incorrectly diagnosed the problem/solution as I am not incredibly advanced yet.

---

### Post by nloewen on 2009-11-05
After some more googling I discovered installing [this]("http://packages.ubuntu.com/jaunty/all/libcupsys2/download") transitional package from jaunty in karmic, the driver will install fine.

---

### Post by Chainy on 2009-11-06
> **nloewen said:**
> After some more googling I discovered installing [this]("http://packages.ubuntu.com/jaunty/all/libcupsys2/download") transitional package from jaunty in karmic, the driver will install fine.

Thank you, nloewen, for posting your solution to this. I'll keep this in mind if I decide to give Ubuntu 9.10 Karmic a go. Glad to hear it's all working! :)

---

### Post by Phis on 2009-11-13
yes, thank you !

---

### Post by ElevenWarrior on 2009-11-21
> **nloewen said:**
> After some more googling I discovered installing [this]("http://packages.ubuntu.com/jaunty/all/libcupsys2/download") transitional package from jaunty in karmic, the driver will install fine.

THIS WORKS!!!!
thank you so much!

---

### Post by butter100fly on 2009-11-29
I've tried everything in these posts and others, several times, in correct order. I still cannot get this to work in my newly installed 64bit Karmic Kernel 2.6.31-15-generic

The printer is contactable, and obviously working in windows. I can install the 32 bit .deb packages by forcing them. The PPD appears to install without issue. The printer state in printer properties is: idle - /usr/lib/cups/filter/pstocanonij failed. But that file is where it should be

I've made an attempt to rebuild the package from cnijfilter-common-3.00. I think the dependency on libcupsys2-dev really isn't helping (haven't found a dummy -dev package yet, just the dummy libcupsys - though I can also install the 32-bit .debs by ignoring the dependency), but basically using dpkg --build on the cnijfilter-common directory produces parsing errors.

End-user experience once again proving extremely poor from needing to install a very common peripheral!

My process:
1) Make sure libcup2 is installed and libcupsys2 dummy driver from above posts is installed. Turn printer off
2) Delete Canon-MP240-series printer from system/administration/printing/printer configuration
3) Stop/restart cups service (have tried both)
4) sudo dpkg -i --force-architecture cnijfilter-common_3.00-1_i386.deb

```
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 140198 files and directories currently installed.)
Preparing to replace cnijfilter-common 3.00-1 (using cnijfilter-common_3.00-1_i386.deb) ...
Unpacking replacement cnijfilter-common ...
Setting up cnijfilter-common (3.00-1) ...
```5) sudo dpkg -i --force-architecture cnijfilter-mp240series_3.00-1_i386.deb

```
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 140198 files and directories currently installed.)
Preparing to replace cnijfilter-mp240series 3.00-1 (using cnijfilter-mp240series_3.00-1_i386.deb) ...
Unpacking replacement cnijfilter-mp240series ...
Setting up cnijfilter-mp240series (3.00-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```both appear to work
6) Start/restart cups service (have tried without stopping too)
7) Turn on printer - it finds Canon-MP240-series
8 ) Go into printer configuration and re-find the PPD and tell it to remake with new settings
9)  The printer state in printer properties is: idle - /usr/lib/cups/filter/pstocanonij failed. Printing fails when I try


please help

---

### Post by madurey on 2009-11-30
thank you for the package it works great!

cheers

---

### Post by neil33 on 2010-03-15
> **nloewen said:**
> After some more googling I discovered installing [this]("http://packages.ubuntu.com/jaunty/all/libcupsys2/download") transitional package from jaunty in karmic, the driver will install fine.
 
 
Thank you so much for this excellent link. After 2 days of troubleshooting, the MP 240 finally works on Ubuntu 9.10. Yeaaaaaaa!
 
This is great! I can print no problem. 
 
regards and thanks again.

---

### Post by thedomed on 2010-04-05
Thanks for all this - i found posts 44 and 53 did the trick for me. I now have printing and scanning thanks to post 12. I can Sleep again at night

---

### Post by teejay17 on 2010-05-11
Has anyone been able to get this printer working in 32-bit Lucid Lynx? I am getting errors when I try to install the packages downloaded from the link here and they won't install.

---

### Post by Chainy on 2010-05-11
> **teejay17 said:**
> Has anyone been able to get this printer working in 32-bit Lucid Lynx? I am getting errors when I try to install the packages downloaded from the link here and they won't install.

Yes, I got it working. I just had a little scare when I went to the Canon site and the driver wasn't there - but it was when I selected another language (German)... But maybe this was just a temporary problem at the Canon site. Just follow the instructions on this thread, and you will be fine.

---

### Post by Chainy on 2010-05-11
just make sure you install the transitional package as mentioned in post 53 on this thread and then everything will work....

---

### Post by teejay17 on 2010-05-11
> **Chainy said:**
> just make sure you install the transitional package as mentioned in post 53 on this thread and then everything will work....
Alright, thanks...I appreciate it. 
Now, forgive me for being so daft, but how do I install that package on Lucid Lynx? What command do I type in the terminal? 
Thanks in advance...

---

### Post by Chainy on 2010-05-11
> **teejay17 said:**
> Alright, thanks...I appreciate it. 
Now, forgive me for being so daft, but how do I install that package on Lucid Lynx? What command do I type in the terminal? 
Thanks in advance...
Forget the terminal. Just click on this link and then a screen will pop up for you to install it: 

[http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.6_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.6_all.deb)

The above link was taken from the page that post 53 mentions. On that page it is listed as "security.ubuntu.com/ubuntu"

---

### Post by teejay17 on 2010-05-11
> **Chainy said:**
> Forget the terminal. Just click on this link and then a screen will pop up for you to install it: 

[http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.6_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.6_all.deb)

The above link was taken from the page that post 53 mentions. On that page it is listed as "security.ubuntu.com/ubuntu"
Oh wow, it worked like a charm. Thank you, your help is very much appreciated.

---

### Post by teejay17 on 2010-05-15
I also have a 64-bit system that I have not attempted to install the driver on yet. Does this printer driver install the same, or are extra steps needed?

---

### Post by Chainy on 2010-05-15
> **teejay17 said:**
> I also have a 64-bit system that I have not attempted to install the driver on yet. Does this printer driver install the same, or are extra steps needed?

Sorry, I don't have any experience on how it all works with a 64-bit system, but posts 25 and 27 in this thread give some instructions. There might be some other posts, too - just read through this thread from page 1!

---

### Post by AlexDS on 2010-07-11
> **elliott.montana said:**
> Nice one sirwilliamthenice on finding those drivers.
Micro$oft pay to make that hard.

To install the 32-bit printer drivers on an amd64 system

Follow icore-skippys post on page 2 for the printer but when he asks you to install the .deb packages do this instead:

Extract "cnijfilter-common-3.00.tar.gz"
Open a terminal
$ sudo apt-get install libtool
In terminal, go to your extracted "cnijfilter-common-3.00" folder
$ sudo dpkg-buildpackage
The installation will most likely stop with the error "there are dependent packages to install": if it does stop and calls for dependencies start "symaptic package manager" from "System" "Administration" to search and install the required packages. After doing this repeat the last terminal command.

Nuts eh. Just glad to give back to the community.
[live without dead time]

when i type this : [COLOR=Blue]alexds@alexds-desktop:~/Desktop/cnijfilter-common-3.00$ sudo dpkg-buildpackage[/COLOR]

this is what i get :  [COLOR=Blue]sudo: dpkg-buildpackage: command not found[/COLOR]

please help!!! I wanna install canon mp240 on Ubuntu 10.04 amd64

---

### Post by AlexDS on 2010-07-11
> **elri07 said:**
> But what about 64 bits...? :confused:
Yeah. how to install this file cnijfilter-common-3.00-1._i386.deb, because it doesn't work by just click on it. How to install if I have Ubuntu on 64 bits?

---

### Post by tudor117 on 2010-07-11
```

$ dpkg-buildpackage
The program 'dpkg-buildpackage' is currently not installed.  You can install it by typing:
sudo apt-get install dpkg-dev
$ sudo apt-get install dpkg-dev
......

```
[S]For amd64 you *DON'T* install the *_i386.deb files, but you build your own.
Alright, alright. I built it as I found it's not as easy as I first expected. However, it's not tested, so no guarantees. [/S]

[S]Force install the i368 packages. Apparently this works best.[/S]
Apparently forcing it to install does not work for most users.
I'll keep my builds up for educational purposes.

---

### Post by kitty griffin on 2010-07-19
where on my desktop will i find the canon solution menu icon ? what does it look like?

---

### Post by AlexDS on 2010-07-19
yeah, good question :)
I want to know that too :D

---

### Post by Chainy on 2010-10-17
I downloaded some images as pdf's and I would like to print them in black and white, but there doesn't seem to be any way of selecting 'black and white'. I can print text documents made in OpenOffice in black and white without any problem, the black ink cartridge is new. But when it comes to printing the pdf, it just doesn't work at all, the printer seems determined to print it out in colour (which won't work as the colour cartridge is nearly empty).

In the preferences section of the Ubuntu default pdf viewer (Evince) there's no way of selecting 'black and white' only. And the Adobe pdf viewer doesn't offer this either. Very strange, because the OpenOffice suite certainly does offer this option. In fact, OpenOffice offers either 'black' or 'grayscale'... not sure what the difference is there...

Does anyone know how to fix this? Thank you for your help!

---

### Post by Chainy on 2010-10-17
> **kitty griffin said:**
> where on my desktop will i find the canon solution menu icon ? what does it look like?

Not sure what you mean by the 'Cannon Solution menu'. I've never had anything like that on my system. If you want to access the preferences and settings of the printer, then go to System>Administration>Printing. Double click on your printer and you will see the 'printer properties' (settings/preferences).

The weird thing that I've noticed is that there is no option there to print only in black and white, though. Seems that Cannon is determined that we should always print in colour. Or does anyone else know a way of getting round this?

Ok, so I can make sure that my documents are already in black and white on the computer first, but I don't know how to convert a colour pdf into black and white, or even if this is possible!

---

### Post by Baeckman on 2010-10-18
Hi Chainy, I have the same problem as you have. There are no option in the driver setting to force black and white printing. I have the MP630 with two black ink tanks and both are full while the color tanks are almost empty. :( This is really sad. I am almost tempted to replace my Canon printer.

Apperantly there is supposed to be a solution. It is called TurboPrint and of course cost money... I have not yet tested but there is a free test version for 30 days.

---

### Post by Chainy on 2010-10-18
> **Baeckman said:**
> Hi Chainy, I have the same problem as you have. There are no option in the driver setting to force black and white printing. I have the MP630 with two black ink tanks and both are full while the color tanks are almost empty. :( This is really sad. I am almost tempted to replace my Canon printer.

Apperantly there is supposed to be a solution. It is called TurboPrint and of course cost money... I have not yet tested but there is a free test version for 30 days.

Hello, thank you for the tip about TurboPrint. I've just installed the trial version and it works very well. It does indeed give you the option of selecting 'grayscale' - I just used it to print out a colour pdf, but in black and white. Very nice - simple task, but seemingly impossible with the driver that Canon provides! 

I'm not sure yet if I'll buy TurboPrint. It's certainly a nice thing, lots of additional options - but I only really need the 'grayscale' part, so it seems a bit odd to pay 30EUR for this! The only other option that I would probably use with  TurboPrint is the ability to lower the saturation, which saves ink (I don't mind having a slightly paler print...). But if you print a lot in colour, then the other features of TurboPrint would come in very handy (ways to save on ink etc, alter the amount of each colour used etc - very useful for the cartridges that contain all the colours together, as is the case with this Canon mp240 printer). But, I don't print in colour so often...

We'll see, I've got 30 days of the TurboPrint trial to go - maybe another way of getting 'grayscale' to work will crop up?!

---

### Post by Chainy on 2010-10-20
> **Baeckman said:**
> Hi Chainy, I have the same problem as you have. There are no option in the driver setting to force black and white printing. I have the MP630 with two black ink tanks and both are full while the color tanks are almost empty. :( This is really sad. I am almost tempted to replace my Canon printer.

Apperantly there is supposed to be a solution. It is called TurboPrint and of course cost money... I have not yet tested but there is a free test version for 30 days.

Hi Baeckman, I've found a way of setting grayscale as the default. And this is using the free driver from Canon. Just do the following steps:

1. Click System &#8211;> Administration &#8211;> Printing.
 2. Now right click on your printer and select properties.
 3. Now select Job Options.
 4 Now scroll down to the bottom.
 5. At the bottom you will see a text box. In that text box add &#8220;CNGrayscale&#8221; (without quotes) and click on Add button.
 6. Once you click add there will appear another text box right above the first text box. So in the second text box add &#8220;TRUE&#8221; and click on apply.

Note: The above instructions are taken from [http://harbhag.wordpress.com/2010/07/03/enable-grayscale-printing-in-canon-pixma-mp250-series-on-ubuntu/](http://harbhag.wordpress.com/2010/07/03/enable-grayscale-printing-in-canon-pixma-mp250-series-on-ubuntu/)

I did the above and it worked perfectly - I now have the option for grayscale, and it has a drop down box, where I can just click it on or off. I've just tried it out and it works fine.

---

### Post by Chainy on 2010-10-20
In the properties of the Canon PIXMA MP240, there is an option to change the saturation - also located in the 'Job Options' section. However, it doesn't seem to work. I've tried setting the saturation at 70% and even 50%, but the resulting print-out is the same as when it was at 100%. Strange, I wonder why it has no effect?

So, I've got the grayscale working, just need to figure out how to change the saturation! (handy for saving ink, especially when there are images)

---

### Post by Ptero-4 on 2010-10-27
I installed it on Ubuntu 10.04 64bits and it worked. I managed to print a 20 pages text document. But now the printer can only print 1 document at a time. After that the power button starts blinking and the alarm LED turns on, it only works if it is unplugged and pluged back in, which makes it repeat the same pattern.

---

### Post by teejay17 on 2010-11-10
> **Chainy said:**
> Forget the terminal. Just click on this link and then a screen will pop up for you to install it: 

[http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.6_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.6_all.deb)

The above link was taken from the page that post 53 mentions. On that page it is listed as "security.ubuntu.com/ubuntu"

It seems the above link no longer works. I've reinstalled 10.04, 64-bit, and it would be great to be able start from the beginning and go through the process of getting the Canon MP240 working. 
I appreciate everyone's feedback. 
Thanks in advance.

---

### Post by Chainy on 2010-11-10
> **teejay17 said:**
> It seems the above link no longer works. I've reinstalled 10.04, 64-bit, and it would be great to be able start from the beginning and go through the process of getting the Canon MP240 working. 
I appreciate everyone's feedback. 
Thanks in advance.

Have you tried installing the Canon driver without the above security patch? Maybe it's not necessary anymore?

---

### Post by Chainy on 2010-11-10
> **teejay17 said:**
> It seems the above link no longer works. I've reinstalled 10.04, 64-bit, and it would be great to be able start from the beginning and go through the process of getting the Canon MP240 working. 
I appreciate everyone's feedback. 
Thanks in advance.

If you do indeed need what was in that link, then you can find it here: [https://launchpad.net/ubuntu/jaunty/i386/libcupsys2/1.3.9-17ubuntu3.6](https://launchpad.net/ubuntu/jaunty/i386/libcupsys2/1.3.9-17ubuntu3.6) - you can download the file on the right hand side where it says "produced these files: libcupsys2_1.3.9-17ubuntu3.6_all.deb. 

As it says there on that page, "this is a dummy package to ease transition to new package name", so you will probably need it due to the fact that the Canon drivers for the MP240 were created a while back and haven't been updated as far as I'm aware. The problem is that the Canon drivers use the old name 'libcupsys2' rather than the new name 'libcups2' and so a dependency problem arises due to the mismatching names. The dummy package sorts this out.

---

### Post by teejay17 on 2010-11-11
> **Chainy said:**
> If you do indeed need what was in that link, then you can find it here: [https://launchpad.net/ubuntu/jaunty/i386/libcupsys2/1.3.9-17ubuntu3.6](https://launchpad.net/ubuntu/jaunty/i386/libcupsys2/1.3.9-17ubuntu3.6) - you can download the file on the right hand side where it says "produced these files: libcupsys2_1.3.9-17ubuntu3.6_all.deb. 

As it says there on that page, "this is a dummy package to ease transition to new package name", so you will probably need it due to the fact that the Canon drivers for the MP240 were created a while back and haven't been updated as far as I'm aware. The problem is that the Canon drivers use the old name 'libcupsys2' rather than the new name 'libcups2' and so a dependency problem arises due to the mismatching names. The dummy package sorts this out.
Thanks for the help. I have it installed, and now have the first part of this little chore done. 
Now how do I force the x86 .debs to install on 64-bit?

---

### Post by chatmoa on 2010-11-11
teejay17: 
  This could help you:

[http://ubuntuforums.org/showthread.php?t=953292&page=9](http://ubuntuforums.org/showthread.php?t=953292&page=9)

---

### Post by zexelon on 2010-11-30
I am dead in the water on this one. I have a Canon MP240 that I simply can not get to work with Ubuntu 10.10 x64.

There do not seem to be any drivers anywhere for this printer! I have tried a bunch of old hacks and have come to the painful reminder of why I always gave up printing with Linux and went paperless. 

At this point I am simply going to connect the printer to a windows virtual machine... unless someone can tell me a way to make this thing work.

---

### Post by AlexDS on 2010-12-01
> **zexelon said:**
> I am dead in the water on this one. I have a Canon MP240 that I simply can not get to work with Ubuntu 10.10 x64.

There do not seem to be any drivers anywhere for this printer! I have tried a bunch of old hacks and have come to the painful reminder of why I always gave up printing with Linux and went paperless. 

At this point I am simply going to connect the printer to a windows virtual machine... unless someone can tell me a way to make this thing work.

i will try this myself since we have the same machine and the same printer. But i cannot right now, only after a couple of months.

but good luck, i think that i should be a way to be victorious ;)

---

### Post by Chainy on 2010-12-01
zexelon, sorry I don't have a 64-bit computer, so I can't really advise you on this. But, this thread contains info on how to do it. Seems like it is possible! There are definitely drivers for this printer. Hope you manage to work it out.

---

### Post by crf112 on 2010-12-01
You can find a copy of libcupsys2_1.3.9-17ubuntu3.9_all.deb [here.]("http://security.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-17ubuntu3.9_all.deb")

I've downloaded it but haven't used it yet.  I also have a copy of an older version named libcupsys2_1.3.9-17ubuntu3.6_all.deb that I HAVE used to get an MP240 running on a network shared by a 10.10 64-bit desktop and a 10.10 32-bit netbook.

---

### Post by amac777 on 2010-12-30
You can download and install a dummy libcupsys2 package that will allow the MP240 to keep printing with the original canon drivers. This web site has instructions and they worked for me for both 64 and 32-bit Ubuntu 10.01:

[http://r3dux.org/2010/05/how-to-get-a-canon-mp240-printer-working-in-ubuntu-10-04-3264-bit/](http://r3dux.org/2010/05/how-to-get-a-canon-mp240-printer-working-in-ubuntu-10-04-3264-bit/)

---

### Post by syb0rz on 2011-01-10
> **amac777 said:**
> You can download and install a dummy libcupsys2 package that will allow the MP240 to keep printing with the original canon drivers. This web site has instructions and they worked for me for both 64 and 32-bit Ubuntu 10.01:

[http://r3dux.org/2010/05/how-to-get-a-canon-mp240-printer-working-in-ubuntu-10-04-3264-bit/](http://r3dux.org/2010/05/how-to-get-a-canon-mp240-printer-working-in-ubuntu-10-04-3264-bit/)

Just ignore the package:

```
sudo dpkg -i --ignore-depends=libcupsys2 --force-architecture cnijfilter-common_3.00-1_i386.deb

```

```
sudo dpkg -i --ignore-depends=libcupsys2 --force-architecture cnijfilter-mp240series_3.00-1_i386.deb

```

---

### Post by syb0rz on 2011-01-10
**Working MP240 printer and scanner on Ubuntu 10.04 x64 easy method:**

**1. **Download Linux Debian drivers from [http://software.canon-europe.com/products/0010645.asp]("http://software.canon-europe.com/products/0010645.asp")

**2. **Extract the MP240_debian_drivers.tar/MP240_debian_printer.tar file and run the following:
```
sudo dpkg -i --ignore-depends=libcupsys2 --force-architecture cnijfilter-common_3.00-1_i386.deb

```
```
sudo dpkg -i --ignore-depends=libcupsys2 --force-architecture cnijfilter-mp240series_3.00-1_i386.deb

```

**3. **Now, connect the printer, go to Administration > Printing and click 'Add'. You should see the Canon MP240 Series printer listed.

---

### Post by teejay17 on 2011-01-23
> **syb0rz said:**
> **Working MP240 printer and scanner on Ubuntu 10.04 x64 easy method:**

**1. **Download Linux Debian drivers from [http://software.canon-europe.com/products/0010645.asp]("http://software.canon-europe.com/products/0010645.asp")

**2. **Extract the MP240_debian_drivers.tar/MP240_debian_printer.tar file and run the following:
```
sudo dpkg -i --ignore-depends=libcupsys2 --force-architecture cnijfilter-common_3.00-1_i386.deb

```
```
sudo dpkg -i --ignore-depends=libcupsys2 --force-architecture cnijfilter-mp240series_3.00-1_i386.deb

```

**3. **Now, connect the printer, go to Administration > Printing and click 'Add'. You should see the Canon MP240 Series printer listed.

Are we to extract this to the desktop, or to another folder? When I try to follow the directions, this is the error I receive: 

> dpkg: error processing cnijfilter-common_3.00-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 cnijfilter-common_3.00-1_i386.deb

---

### Post by rlanders on 2011-01-25
Made a dummy package:
[ftp://install.withinboredom.info/libcupsys2_1.3.7-6_all.deb](ftp://install.withinboredom.info/libcupsys2_1.3.7-6_all.deb)

I'd recommend someone mirroring it ASAP as the vps will expire in a couple of weeks.

Probably will save everyone the hassle.  To create your own:
In a console:
```
sudo apt-get install equivs
mkdir dummy-libcupsys2
cd dummy-libcupsys2
equivs-control dummy-libcupsys2
gedit dummy-libcupsys2

```

Make it say this below:

```

Edit it to show these values
### Commented entries have reasonable defaults.
### Uncomment to edit them.
Section: misc
Priority: optional
# Homepage: <enter URL here; no default>
Standards-Version: 3.6.2

Package: libcupsys2
#Put the current version of CUPS here
Version: 1.3.7-6
Maintainer: Your Name <your.email@gmail.com>
Pre-Depends:
Depends:
Recommends:
Suggests:
Provides:
Replaces:
# Architecture: all
# Copyright: <copyright file; defaults to GPL2>
# Changelog: <changelog file; defaults to a generic changelog>
# Readme: <README.Debian file; defaults to a generic one>
# Extra-Files: <comma-separated list of additional files for the doc directory>
# Files: <pair of space-separated paths; First is file to include, second is destination>
#  <more pairs, if there's more than one file to include. Notice the starting space>
Description: stupid defaults
 long description and info
 .
 second paragraph

```

Save and exit.  In a console type:

```
equivs-build dummy-libcupsys2

```

This will put a .deb file in the directory that you can install to satisfy the dependencies.

I'm not responsible for any damage this may cause.  You may need to do this with every CUPS update. It works for me.

Feels good to give back :)

---

### Post by rlanders on 2011-01-25
If the downloaded version doesn't work, the directions will.

---

### Post by vkunkel on 2011-03-06
Thanks syb0rz, worked perfectly. (I only wish i had scrolled to the end of this thread first, and saved an hour of going through other's suggestions)

---

### Post by Quantux on 2011-03-22
> **syb0rz said:**
> **Working MP240 printer and scanner on Ubuntu 10.04 x64 easy method:**

**1. **Download Linux Debian drivers from [http://software.canon-europe.com/products/0010645.asp]("http://software.canon-europe.com/products/0010645.asp")

**2. **Extract the MP240_debian_drivers.tar/MP240_debian_printer.tar file and run the following:
```
sudo dpkg -i --ignore-depends=libcupsys2 --force-architecture cnijfilter-common_3.00-1_i386.deb

```
```
sudo dpkg -i --ignore-depends=libcupsys2 --force-architecture cnijfilter-mp240series_3.00-1_i386.deb

```

**3. **Now, connect the printer, go to Administration > Printing and click 'Add'. You should see the Canon MP240 Series printer listed.

Perfect! Ran those two packages (can't imagine why I didn't think of the ignore switch before), turned on the printer, ubuntu (10.10 x64) did the rest. Now I just need the command to refill the ink...

---

### Post by syb0rz on 2011-05-21
I have a problem know with Natty (amd64). dpkg keeps giving me dependency errors even with --force-all... Here's my output from dpkg without --force-all:

```
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 146966 files and directories currently installed.)
Preparing to replace cnijfilter-common:i386 3.00-1 (using cnijfilter-common_3.00-1_i386.deb) ...
Unpacking replacement cnijfilter-common:i386 ...
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1).
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cnijfilter-common:i386
```


Any help would be appreciated...

---

### Post by syb0rz on 2011-05-27
ALL CANON PIXMA MP240 USERS READ THIS!

A saint has a PPA setup with everything you need for both i386 and amd64 for all PIXMA printers. Check out Michael Gruz's PPA here:
[https://launchpad.net/~michael-gruz/+archive/canon](https://launchpad.net/~michael-gruz/+archive/canon)

**Installing an MP240 on Natty amd64:**
```

sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-common cnijfilter-mp240series

```

---

### Post by teejay17 on 2011-05-31
> **syb0rz said:**
> ALL CANON PIXMA MP240 USERS READ THIS!

A saint has a PPA setup with everything you need for both i386 and amd64 for all PIXMA printers. Check out Michael Gruz's PPA here:
[https://launchpad.net/~michael-gruz/+archive/canon]("https://launchpad.net/%7Emichael-gruz/+archive/canon")

**Installing an MP240 on Natty amd64:**
```

sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-common cnijfilter-mp240series

```
Thank you Saint Michael Gruz! This works amazing! This is the only time I have been able to print successfully using on a 64-bit Ubuntu machine with a Pixma 240.
This is amazing!

---

### Post by pezunite on 2011-06-20
Hi GUys,

I have posted a thread and no one has responded so i thought i would try here..

I have installed canon mp240 on 11.04 and only the scanner works but it does not print anything.

Any one can help me please??

---

### Post by teejay17 on 2011-06-20
> **pezunite said:**
> Hi GUys,

I have posted a thread and no one has responded so i thought i would try here..

I have installed canon mp240 on 11.04 and only the scanner works but it does not print anything.

Any one can help me please??

Did you install the PPAs?

---

### Post by pezunite on 2011-06-28
whats that?

---

### Post by teejay17 on 2011-06-28
> **pezunite said:**
> whats that?
Seriously? Look it up, then come back and read this thread...the answer to all your dilemmas is like two posts above yours. The trick is to read the thread...

---

### Post by Ningbojoe on 2011-07-16
Just like to thank the contributor of entry number 90. It worked perfectly for my Pixma MP 190. All the -force suggestions did not work on my Linux Mint Debian Edition. I would also like to thank the chap who just saved a the dummy package required to complete the installation of my printer. Thanks to r3dux.org.

---

### Post by gippeswyc on 2011-08-09
> **syb0rz said:**
> ALL CANON PIXMA MP240 USERS READ THIS!

A saint has a PPA setup with everything you need for both i386 and amd64 for all PIXMA printers. Check out Michael Gruz's PPA here:
[https://launchpad.net/~michael-gruz/+archive/canon]("https://launchpad.net/%7Emichael-gruz/+archive/canon")

**Installing an MP240 on Natty amd64:**
```

sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-common cnijfilter-mp240series

```

Thanks for this, the only 64-bit various attempt that's worked for me :D

---

### Post by Jolicoeur on 2011-09-23
> **gippeswyc said:**
> Thanks for this, the only 64-bit various attempt that's worked for me :D

Thanks for this! After running these three lines do I just plug in the printer it will start working?

Thanks):P

---

### Post by lobo621 on 2011-12-19
:popcorn:Many thanks to those above.  Just wanted to let you know that the procedures work on the new Linux Mint 12!  Have a great day!:)

---

### Post by volodiak on 2012-01-27
> **syb0rz said:**
> ALL CANON PIXMA MP240 USERS READ THIS!

A saint has a PPA setup with everything you need for both i386 and amd64 for all PIXMA printers. Check out Michael Gruz's PPA here:
[https://launchpad.net/~michael-gruz/+archive/canon](https://launchpad.net/~michael-gruz/+archive/canon)

**Installing an MP240 on Natty amd64:**
```

sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-common cnijfilter-mp240series

```

Thanks syb0rz for these 3 magic lines and great respect to Michael Gruz!!! Finally I can print form my 64bit 11.10 lubuntu!  My printer is mx320 and I changed 3rd line respectively to sudo apt-get install cnijfilter-common cnijfilter-mx320series

---

### Post by teejay17 on 2012-05-09
This PPA stopped working for 12.04. Does anyone know how to get it working? 
> sudo add-apt-repository ppa:michael-gruz/canon 
sudo apt-get update 
sudo apt-get install cnijfilter-common cnijfilter-mp240series

---

### Post by Chainy on 2012-05-10
> **teejay17 said:**
> This PPA stopped working for 12.04. Does anyone know how to get it working?

This might not be necessary. I've recently installed Ubuntu 12.04 (changed to the KDE desktop), and the default printer installer now includes a Gutenberg driver that seems to work perfectly well with the Canon MP240 printer. I've done a few test prints, and everything's gone smoothly so far. This alternative driver also gives access to far more preferences, too.

EDIT: in the preferences of this Gutenberg driver, you should select CMYK, rather than RGB in the preferences. This makes the colour printouts look much better.

---

### Post by teejay17 on 2012-05-10
> **Chainy said:**
> This might not be necessary. I've recently installed Ubuntu 12.04 (changed to the KDE desktop), and the default printer installer now includes a Gutenberg driver that seems to work perfectly well with the Canon MP240 printer. I've done a few test prints, and everything's gone smoothly so far. This alternative driver also gives access to far more preferences, too.

EDIT: in the preferences of this Gutenberg driver, you should select CMYK, rather than RGB in the preferences. This makes the colour printouts look much better.
Is the Gutenberg something I have to download and install, or is it already in Ubuntu?

---

### Post by Chainy on 2012-05-10
> **teejay17 said:**
> Is the Gutenberg something I have to download and install, or is it already in Ubuntu?

Just try out the printer installer and see what happens. Follow the prompts. 

Sorry, I don't have my Ubuntu computer with me right now, so I can't give you more detailed instructions. But, when I set up the printer yesterday, the driver seemed to be already included (unless it appeared there due to one of my previous attempts to install the official Canon driver - but, I'm pretty sure I ended up deleting this as when I ran 'sudo apt-get update', I was warned that there was a dependency problem. After running 'sudo apt-get autoremove', the official Canon driver files got removed from the system due to this.

Let me know how you get on!

EDIT: I'll check my actual Ubuntu installation tomorrow to see exactly how I've got it set up. Either way, it's certainly possible to get the printer working!

---

### Post by teejay17 on 2012-05-14
> **Chainy said:**
> Just try out the printer installer and see what happens. Follow the prompts. 

Sorry, I don't have my Ubuntu computer with me right now, so I can't give you more detailed instructions. But, when I set up the printer yesterday, the driver seemed to be already included (unless it appeared there due to one of my previous attempts to install the official Canon driver - but, I'm pretty sure I ended up deleting this as when I ran 'sudo apt-get update', I was warned that there was a dependency problem. After running 'sudo apt-get autoremove', the official Canon driver files got removed from the system due to this.

Let me know how you get on!

EDIT: I'll check my actual Ubuntu installation tomorrow to see exactly how I've got it set up. Either way, it's certainly possible to get the printer working!
I've been messing around with Gutenprint, but nothing seems to work. My printer seems to be detected, but when I try to print something, nothing happens. After a while of "processing" in the print queue, it then says print job was "completed" even though that is not the case. 
Too bad the PPA doesn't work anymore. It was awesome.

---

### Post by Chainy on 2012-05-15
> **teejay17 said:**
> I've been messing around with Gutenprint, but nothing seems to work. My printer seems to be detected, but when I try to print something, nothing happens. After a while of "processing" in the print queue, it then says print job was "completed" even though that is not the case. 
Too bad the PPA doesn't work anymore. It was awesome.

I've just had a look at my printer settings. It does indeed say that I'm using the Gutenprint driver (Canon PIXMA MP240-CUPS+Gutenprint v5.2.8-pre1).

I just made a couple of changes in the printer settings:

1. As mentioned before, I changed the Color Model to CMYK (as far as I remember, in Gnome this is listed as CYMK). I'm using KDE. The default setting was RGB, which doesn't give very good colours in the printout.

2. I changed the Resolution to 600x600 DPI. The Gutenprint driver gives many other possibilities for the resolution. The default setting didn't work well with the printer, it just started making a strange chugging sound and was very slow at printing. I don't remember what it was set at, but perhaps it was on one of the very high resolution settings?! Anyhow, once I changed it to 600x600 DPI, it started to print as normal.

The only other change I made was concerning the page size (I set it at A4, rather than the default Letter size). There were two locations where I could make this change.

EDIT: I'm using the 32-bit version of Ubuntu, so perhaps any problems could be connected with using the 64-bit version? By the way, why even bother using the 64-bit version? - for day-to-day usage, it doesn't really improve performance much, as far as I'm aware. And you can always install the 32-bit version onto a 64-bit machine.

---

### Post by teejay17 on 2012-05-15
> **Chainy said:**
> I've just had a look at my printer settings. It does indeed say that I'm using the Gutenprint driver (Canon PIXMA MP240-CUPS+Gutenprint v5.2.8-pre1).

I just made a couple of changes in the printer settings:

1. As mentioned before, I changed the Color Model to CMYK (as far as I remember, in Gnome this is listed as CYMK). I'm using KDE. The default setting was RGB, which doesn't give very good colours in the printout.

2. I changed the Resolution to 600x600 DPI. The Gutenprint driver gives many other possibilities for the resolution. The default setting didn't work well with the printer, it just started making a strange chugging sound and was very slow at printing. I don't remember what it was set at, but perhaps it was on one of the very high resolution settings?! Anyhow, once I changed it to 600x600 DPI, it started to print as normal.

The only other change I made was concerning the page size (I set it at A4, rather than the default Letter size). There were two locations where I could make this change.

EDIT: I'm using the 32-bit version of Ubuntu, so perhaps any problems could be connected with using the 64-bit version? By the way, why even bother using the 64-bit version? - for day-to-day usage, it doesn't really improve performance much, as far as I'm aware. And you can always install the 32-bit version onto a 64-bit machine.
I will try to make the changes that you did, to see if that makes a difference and enables printing. If not, perhaps you are correct and it is a 64 bit issue. I may end up having to install 32 bit just to see if that changes things, however, I am hesitant to do that due to time restraints for the next week-and-a-half or so.

---


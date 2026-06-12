---
title: "Printer Drivers...we need help from Kodak"
date: 2010-03-22
forum: Hardware
---

### Post by deadringerinc on 2010-03-22
I am unaware of any (really, any?) LINUX print drivers for Kodaks printers.  I hope this is just an oversight on my behalf, but I requested a response from Kodak regarding this issue.  Please help in getting their attention focused on resolving this issue by emailing them as well.  See my original msg below, feel free to C&P it at their site ( [http://www.kodak.com/global/en/service/contactKodak/email/consumerDigital_contact.jhtml?pq-path=13452](http://www.kodak.com/global/en/service/contactKodak/email/consumerDigital_contact.jhtml?pq-path=13452) ).  

"I'd like to work with you on developing drivers for your printers so that all of the people that utilize the LINUX operating system can buy your products.  Please advise me on how you want to approach a  possible beneficial mutual relationship between Kodak and the ever growing LINUX Community as well as the Open Source Software world.  Thanks for your time and I look forward to discussing this with you further.  Be well.  
-A concerned supporter of your relationship with LINUX  "

With the utmost sincerity,  
the staff @ DeadRingerInc.com
"been dedicated to using LINUX solid ever since we discovered it"

---

### Post by deadringerinc on 2010-03-22
please show your support through the Facebook CAUSE:
[http://www.causes.com/causes/463261](http://www.causes.com/causes/463261)

---

### Post by cariboo on 2010-03-22
Please don't bump your thread more than once every 24 hours

---

### Post by paulnewall on 2010-04-23
I have written a driver for ESP 5250 (it may work with other ESP printers.
search for kodak on sourceforge to find it.

---

### Post by pctek on 2010-05-01
> **paulnewall said:**
> I have written a driver for ESP 5250 (it may work with other ESP printers.
search for kodak on sourceforge to find it.


I want to thank you for your driver. I just purchased a 5250 and it is working very well.:KS

---

### Post by Aurora@FleetBuzz on 2010-05-05
**paulnewall**, I want to thank you as well.  I got my ESP 7250 working out of Lucid with your driver!

---

### Post by Jim_in_Omaha on 2010-05-10
> **paulnewall said:**
> I have written a driver for ESP 5250 (it may work with other ESP printers.
search for kodak on sourceforge to find it.

Is that available in 64 bit?

---

### Post by Jim_in_Omaha on 2010-05-11
> **paulnewall said:**
> I have written a driver for ESP 5250 (it may work with other ESP printers.
search for kodak on sourceforge to find it.

To answer my own question, I compiled it based on your help information at Sourceforge in 64-bit 10.04. I have a Kodak 5500 Aio. 

I had to select the driver for the esp unit when installing the printer. I also had to install from Synaptic libcupsimage2-dev.

I does print in Color and B&W. 1000 thank you's. Amazing...

---

### Post by Max Uglee on 2010-05-17
> **Jim_in_Omaha said:**
> To answer my own question, I compiled it based on your help information at Sourceforge in 64-bit 10.04. I have a Kodak 5500 Aio. 

I had to select the driver for the esp unit when installing the printer. I also had to install from Synaptic libcupsimage2-dev.

I does print in Color and B&W. 1000 thank you's. Amazing...

Jim, could you post a link to where you found that info?  I need a 64 bit version of the driver.  I am trying to get an ESP 5250 working in Lucid.  Thank you!

---

### Post by Jim_in_Omaha on 2010-05-17
> **Max Uglee said:**
> Jim, could you post a link to where you found that info?  I need a 64 bit version of the driver.  I am trying to get an ESP 5250 working in Lucid.  Thank you!

Sure,

Here are the files. I downloaded the .tar.gz to compile.

[https://sourceforge.net/projects/cupsdriverkodak/files/]("https://sourceforge.net/projects/cupsdriverkodak/files/")

Here is the instructions to compile.
[URL="https://sourceforge.net/projects/cupsdriverkodak/forums/forum/1107085/topic/3656491"]
https://sourceforge.net/projects/cupsdriverkodak/forums/forum/1107085/topic/3656491[/URL]

And here are those instructions from SourceForge on the CUPS Kodak driver

> INSTALLATION The general procedure will be like this (see below for details for different distros):

Download:
You download the compressed archive file

Unpack:
You uncompress the archive to get several files required to install the driver.
(This is one of those files, so you have probably done that already)

(Optional) Install packages needed for this driver to work:
You may need to install some packages before you can install the driver.
Most distros have some package manager that you use to do this.

(Optional) Uninstall:
If you have already installed a previous version of this driver, it might be helpful to uninstall it.
If not, ignore this step.

Compile:
You need to convert the program, written in c, into something your computer can run.
Compiling will be done by a command like "make"

Install driver, PPD files, and extra files:
Various files need to be copied to folders where the system can find them.
This will be done with a command like "make install"

Restart cups:
cups is the printing system, having installed the files of this driver, you restart cups so that it knows about the new driver.
This will be done with a command like "make cups"

Create printers:
This is where you tell cups about the new printer.

Then it should be possible to print.


Detailed versions follow for different distros:

UBUNTU NOTES (in the following NN in the filename c2espNN means the 2 digits of the release no)
(so for release 0.4, you would type c2esp04 )

Download:
You download the compressed archive file from [http://sourceforge.net/projects/cupsdriverkodak/](http://sourceforge.net/projects/cupsdriverkodak/)
It is usually convenient to store the dowloaded file on the desktop.

Unpack:
You uncompress the archive to get several files required to install the driver.
If you double click on the dowloaded .tar.gz file, the archive manager should open.
Use the extract button to extract files from the archive.
The goal is to get a folder called something like c2esp04 (the last 2 digits depend on the version of the driver)in some place you specify, for example in your home folder.
This folder should contain the files in the archive.

(Optional) Install packages needed for this driver to work:
You may need to install some packages if you do not already have them, before you can install the driver.
I'm assuming you know how to do that (with synaptic package manager, in Menu: System/Administration).
You will need the following:
[COLOR="Red"]build-essential
cups
libcups2-dev[/COLOR]

You need to open a terminal for the following steps:
Menu: Applications/Accessories/Terminal
When the terminal starts you will be in your home folder. You need to navigate to the folder where you unpacked the driver.
(in the following NN in the filename c2espNN means the 2 digits of the release no)
(so for release 0.4, you would type c2esp04 )
For example (in this example "$" represents the prompt, you type what follows the $:
$ cd c2espNN

(Optional) Uninstall:
If you have already installed a previous version of this driver, it might be helpful to uninstall it.
If not, ignore this step.
To uninstall, you type:
$ sudo make uninstall
The sudo indicates that you want to do some kind of system modification that you would normally be prevented from doing.
So you get asked for the password the first time you use sudo.

Compile:
You need to convert the program, written in c, into something your computer can run.
To compile, you type:
$ make
You may get messages suggesting you need to install some package (see the (Optional) Install packages section above)
You may get some warnings, you can probably ignore those.
You may get some error messages, if so it's unlikely you can continue.

Install driver, PPD files, and extra files:
Various files need to be copied to folders where the system can find them.
To install, you type:
$ sudo make install
The sudo indicates that you want to do some kind of system modification that you would normally be prevented from doing.
So you get asked for the password the first time you use sudo.

Restart cups:
cups is the printing system, having installed the files of this driver, you restart cups so that it knows about the new driver.
To restart cups, you type:
$ sudo make cups

Create printers:
This is where you tell cups about the new printer.
Turn the printer on.
Menu: System/Administration/Printing
A printer configuration window should open.
Click the "new" button, and wait while the system searches for printers, you should get a "Select device" window.
Navigate to the printer (network printer or USB printer).
I find I have to wait for several seconds after clicking on a network printer for it to be highlighted.
Click "Forward" and wait again for the "Describe printer" window.
Change the names if you wish, and click the "Apply" button.
Print test page if you wish, but you might do this first:
If you right click the newly created printer in the printer configuration window, you can set up some properties like:
Colour or b/w, resolution, paper size etc. (under printer options)
I generally make 2 printers, one colour and one b/w.

Then it should be possible for you to print

---

### Post by Max Uglee on 2010-05-18
Thanks alot Jim.  I am up and printing with no problems!  The directions in the install file worked perfectly except for one part.
 
I got this error when running the "make" command:
 
#
# Dependencies...
#
***
*** Error: /usr/include/cups/raster.h is not installed!
***
*** Install cups raster library package
*** for Ubuntu: sudo apt-get install libcupsimage2
***
make: *** [all-test] Error 1

So I tried "sudo apt-get install libcupsimage2" and I got a message that it was already the latest version.  
 
I googled and found this thread:
 
[http://ubuntuforums.org/showthread.php?p=9300604](http://ubuntuforums.org/showthread.php?p=9300604)
 
where someone had said:
 
"You need to install libcupsimage2-dev then it'll work"
 
and they were right, it worked.
 
I made a mistake in my first post, the computer I was working on had Karmic, not Lucid, if that matters.
 
Thanks everyone!

---

### Post by Jim_in_Omaha on 2010-05-18
Great to see yours is working too. I had the same issue with libcupsimage2-dev and mentioned it in post #8. Then it worked without issue..

---

### Post by Spoom on 2010-07-26
Thank you very much, you prevented me from having to return this printer.  We should get this driver into the repositories.

---

### Post by Trent T on 2010-08-22
Hi all -- 
I found a printer driver for my Kodak ESP 7250 printer at Sourceforge;

The name of the driver is

c2esp_08-1_i386.deb.

More info on this is on page 6 of another thread:

[http://ubuntuforums.org/showthread.php?p=9749680#post9749680](http://ubuntuforums.org/showthread.php?p=9749680#post9749680).

It's working very well for me!

---


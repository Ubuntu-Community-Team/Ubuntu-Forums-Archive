---
title: "Canon iP2600....anyone?"
date: 2008-04-30
forum: Hardware
---

### Post by theZoid on 2008-04-30
Has anyone got this work?  Please advise as to how.  Yes, Turboprint works great with the ip2500 driver, I don't mind ponying up for a good job for linux, but you know....:)

How-you-did-it appreciated!!

---

### Post by WendyWeber on 2008-05-10
same here :-)
I found canon drivers for various pixma printers, not for the ip2600. I guess I'll give the canon to one of my kids and buy a printer of a more linux-friendly manuf myself.

X10

---

### Post by iheartubuntu on 2008-06-07
My dad just bought a new monitor at Fry's and got this Canon PIXMA iP2600 for free. He gave it to me since I need a home printer, but I cant get it to work in Ubuntu yet. I do have Ubuntu 8.04 and when I plugged in the printer and turned it on, Ubuntu immediately found the printer and installed the drivers. I was so excited (since Canon SUCKS with linux support). Ive tried printing a few things, and the printer light will flash, but nothing prints. Any ideas? Thanks!

---

### Post by Mexico Man on 2008-06-16
Hi,

It seems that the drivers are now available.
[http://ubuntuforums.org/showthread.php?t=282096&page=6&highlight=ip2600]("http://ubuntuforums.org/showthread.php?t=282096&page=6&highlight=ip2600")

However , my problem is that I am trying to use the Canon IP2600 on an AMD64 PC. 

The instructions here 
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900")
mention a work around for AMD64 PC's and this may work with the IP2600 drivers from the Canon web site [http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100119102.html")  

Has anyone had any success with Canon's Pixma IP2600 ( or IP2000 , IP2400, IP2500 or IP2600 for that matter ) on an AMD64 PC ?

Thank You

---

### Post by liviubero on 2008-07-04
I have a Canon IP2500 and it seems to work, I mean I don't get any error messages.
I am on Ubuntu.
The only problem is that IT DOESN'T PRINT.
It doesn't do anything.
Any suggestions?

---

### Post by naildeca on 2008-07-06
In my search to get my Canon iP2600 working I found a forum thread with this address [http://support-asia.canon-asia.com/](http://support-asia.canon-asia.com/) (thanks to whoever it was, I cannot remember where I found it)

There I found drivers for _many_ Canon printers. For the iP2600 you can start here [http://support-asia.canon-asia.com/EN/search?v%3aproject=AZZ-EN&binning-state=model%3d%3dPIXMA%20iP2680%0amenu%3d%3dDownload%0aos%3d%3dLinux&](http://support-asia.canon-asia.com/EN/search?v%3aproject=AZZ-EN&binning-state=model%3d%3dPIXMA%20iP2680%0amenu%3d%3dDownload%0aos%3d%3dLinux&) 

You need two files,
IJ Printer Driver Ver. 2.90 for Linux (debian Common package) (the filename is cnijfilter-common_2.90-1_i386.deb)
and
IJ Printer Driver Ver. 2.90 for Linux (debian Package for iP2600 series) (the filename is cnijfilter-ip2600series_2.90-1_i386.deb)

I downloaded both files and saved them to the desktop.

Somewhere someone gave a step-by-step (again I forgot who, thanks anyway). He mentioned that the printer should be on and then the common package should be installed first (double click in the icon and the installer, gdebi, begins)

Then do the same for the ip2600 file.

Then you can go to System -> Administration -> Printng and add your printer.

Sorry for so much detail, it is probably more than the original poster needed. I am new to participating in forums and this may have been better placed elsewhere.

---

### Post by Mexico Man on 2008-07-07
These drivers for the IP2600 also work on AMD64 if the debs files are converted with alien to rpms in a 32 bit environment :-

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900#amd64%20Steps:](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/Canon_LBP_2900#amd64%20Steps:)

---

### Post by liviubero on 2008-07-07
I got my IP2500 working following the instructions on the German Ubuntu forum:
[http://www.ubuntu-forum.de/artikel/28303/canon-ip-2500-druckt-nicht.html](http://www.ubuntu-forum.de/artikel/28303/canon-ip-2500-druckt-nicht.html)
An English approach is here:
[http://ubuntuforums.org/showthread.php?t=592685](http://ubuntuforums.org/showthread.php?t=592685)

---

### Post by lubeck on 2008-08-15
DRIVERS for the CANON Pixma iP2600 are indeed located at:
[http://support-asia.canon-asia.com/](http://support-asia.canon-asia.com/)           as "naildeca" says.

**Couple Notes, FYI:**
This install took about 5 minutes... easy for a noob like me.

In addition to the two .deb files (the drivers) mentioned by "naildeca" above at this site (the drivers appear when you select the Injet, Pixma, iP2680 printer, Downloads), are the **VERY USEFUL Linux install instructions (Ubuntu included)** listed if you then select "Manuals":

"IJ Printer Driver Ver. 2.90 for Linux (Operation guide [Explanation of the iP2600series operation (html file)]"

With this wonderful documentation the installation went a bit easier... since there is one install step one must take before installing the .debs.

Noteworthy in these instructions, CANON recommends the following command at the Terminal before installing the .debs, to ready the system to "receive" them.  I found this necessary and fundamental:

sudo aa-complain cupsd   

Final Notes:
The install instructions include a step called "Register the Printer to the Spooler."  A sample command is shown, so this is easy to do.  However, part of the command needs two things that are peculiar to your computer after you install the .debs.  
[printer_name] 
[PPD_filename] 
[device_URI]
Printer name and the URI may be easily found at System, Administration, Printing ... and your iP2600 PPD can be found using "locate *.ppd" at the command line.

If it helps, mine was located in /usr/share/ppd/canonip2600.ppd, and after the Registration command, in /etc/cups/ppd/canonip2600.ppd

Some applications need to be told the Printer "PPD" to allow them to understand how to talk to the iP2600, so you may want to save this location in a text file--for later recall or copy & paste.
Thanks to those who forged the path and helped me find the drivers.
Best wishes.

---

### Post by Syntaxeus on 2008-09-29
> **lubeck said:**
> DRIVERS for the CANON Pixma iP2600 are indeed located at:
[http://support-asia.canon-asia.com/](http://support-asia.canon-asia.com/)           as "naildeca" says.

**Couple Notes, FYI:**
This install took about 5 minutes... easy for a noob like me.

In addition to the two .deb files (the drivers) mentioned by "naildeca" above at this site (the drivers appear when you select the Injet, Pixma, iP2680 printer, Downloads), are the **VERY USEFUL Linux install instructions (Ubuntu included)** listed if you then select "Manuals":

"IJ Printer Driver Ver. 2.90 for Linux (Operation guide [Explanation of the iP2600series operation (html file)]"

With this wonderful documentation the installation went a bit easier... since there is one install step one must take before installing the .debs.

Noteworthy in these instructions, CANON recommends the following command at the Terminal before installing the .debs, to ready the system to "receive" them.  I found this necessary and fundamental:

sudo aa-complain cupsd   

Final Notes:
The install instructions include a step called "Register the Printer to the Spooler."  A sample command is shown, so this is easy to do.  However, part of the command needs two things that are peculiar to your computer after you install the .debs.  
[printer_name] 
[PPD_filename] 
[device_URI]
Printer name and the URI may be easily found at System, Administration, Printing ... and your iP2600 PPD can be found using "locate *.ppd" at the command line.

If it helps, mine was located in /usr/share/ppd/canonip2600.ppd, and after the Registration command, in /etc/cups/ppd/canonip2600.ppd

Some applications need to be told the Printer "PPD" to allow them to understand how to talk to the iP2600, so you may want to save this location in a text file--for later recall or copy & paste.
Thanks to those who forged the path and helped me find the drivers.
Best wishes.

Thanks, this worked like a charm. After installing the two .deb's and restarting the CUPS daemon. I was abled to choose IP2600 in the list of drivers in CUPS web interface, and just add it to the system.

I bought this printer, after reading this thread, at lunch and I'm already up and running. It did only take 5 min to configure... sweet!

---

### Post by Leadbelly on 2008-11-16
Thank for your advice, naildeca. It was very helpful.

---

### Post by randall375 on 2009-06-09
Hi - I am really new newbie.  I installed the packages from the Asian site - both debs and they seemed to install properly in 9.04 - but when I go to add the printer I get the error that says "CUPS sever error - "client-error-not-possible"  then it fails and I can do nothing... does anyone have an idea of what is wrong??? 

BTW - I do have an AMD 64 processor - but what does this have to do with a printer??? 

Thanks to any and all that can help.

---

### Post by dukebytes on 2009-07-23
Just bought one of these printers and it did not have the right driver.  All I had to do extra was the following from a terminal 'sudo apt-get install -f' and then both packages worked great!

Just wanted to say thanks!!!

---

### Post by SeePU on 2009-07-24
Did you have to do the steps in posts #6 and #9?

I was considering buying this printer.   It appears to be a relatively Linux-friendly printer that is cheap yet decent.  I find that HP inkjet printers are way overrated.  The functioning of them, not the Linux part. 

I was going to go by this guide before I came across this thread.  I guess  they are both more or less the same:

[http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP2600](http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_iP2600)

---

### Post by almikul on 2009-10-29
For those who cannot install packages [list][*]cnijfilter-common_2.90-1_i386.deb
[*]cnijfilter-ip2600series_2.90-1_i386.deb[/list] due to missing libcupsys2 in Karmic Koala (9.10), you can modify these packages as described in this _[tutorial](http://forums.linuxmint.com/viewtopic.php?f=42&t=35136)_.

Alternatively, you can download the following packages that I have modified myself :) Of course, the order of installation remains the same: common -> IP2600. 

[u][rebuilt_common.deb](http://almikul.home.comcast.net/debs/rebuilt_common.deb)
[rebuilt_ip2600.deb](http://almikul.home.comcast.net/debs/rebuilt_ip2600.deb)[/u]

---

### Post by booksnmore4you on 2009-10-31
@[almikul]("http://ubuntuforums.org/member.php?u=731104")

Thank you, that was extremely helpful. :-)

---

### Post by gpmanrpi on 2009-11-03
Thank god you modified those.  I was looking at the source for the common library and could not make heads or tails of it.

---

### Post by almikul on 2009-11-15
**Some minor update:** when I installed IP2600 with my own modified packages, the file /usr/lib/cups/filter/pstocanonij was owned by me and not root. It is supposed to be owned by root, so if it is not, then you should manually set the ownership to root by doing 

```
sudo chown root:root /usr/lib/cups/filter/pstocanonij
```

Hope it helps.

---

### Post by saatu on 2009-11-21
Thanks for the modified packages for Karmic. I was able to install them using --force-architecture but when I try to print, it gives a 'cups-insecure-filter' error and it won't print. Any idea how to overcome this?

Also, one of the posts above says to 'Register printer to the spooler'. How do I do this?

---

### Post by saatu on 2009-11-22
I solved this and my canon ip2600 is printing back again.

Ran the following commands:

sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend

Thanks all for your help

---

### Post by JasonT76 on 2009-11-30
almikul and saatu.... 

Thank you both very much !!!  I've been searching the forums for hours, and now happily printing once again.

---

### Post by Chrisco66 on 2009-12-19
Thanks to aimikul and saatu.  If you are still having problems, get the debs from entry #15 above, and install. Common first, then ip2600.  Go to printing under administration menu, and click add printer.  When it finds it, follow the instructions for adding the printer, and tell it to print a test page.  It offered to print on my machine.  It may give you a fault about insecure filter.  If it does, run the 4 commands in terminal that are listed in entry #20 above.  You may have to delete the printer and reinstall after you do the commands.  Try another test print.  Mine is working fine now.  Thanks again to the folks who figured this out.  I now have my printer back, not a paperweight.  My next printer may be an HP because they seem to offer much better support for Linux..

---

### Post by stmcc on 2010-01-01
> **almikul said:**
> **Some minor update:** when I installed IP2600 with my own modified packages, the file /usr/lib/cups/filter/pstocanonij was owned by me and not root. It is supposed to be owned by root, so if it is not, then you should manually set the ownership to root by doing 

```
sudo chown root:root /usr/lib/cups/filter/pstocanonij
```

Hope it helps.
Thanks. I have been fighting this since October.Your rebuilt debs and change to root fixed my problems.

---

### Post by jam3s_ on 2010-01-22
thank you, my ip2600 works flawlessly now.
had the "insecure filter" error but after changing the permissions to root it now works!

:popcorn::popcorn::popcorn::popcorn:

---

### Post by jblaven on 2010-02-18
> **almikul said:**
> For those who cannot install packages
[LIST]
[*]cnijfilter-common_2.90-1_i386.deb
[*]cnijfilter-ip2600series_2.90-1_i386.deb
[/LIST]
due to missing libcupsys2 in Karmic Koala (9.10), you can modify these packages as described in this _[tutorial]("http://forums.linuxmint.com/viewtopic.php?f=42&t=35136")_.

Alternatively, you can download the following packages that I have modified myself :) Of course, the order of installation remains the same: common -> IP2600. 

[U][rebuilt_common.deb]("http://almikul.home.comcast.net/debs/rebuilt_common.deb")
[rebuilt_ip2600.deb]("http://almikul.home.comcast.net/debs/rebuilt_ip2600.deb")[/U]

THEN DO THIS...

```
sudo chown root:root /usr/lib/cups/filter/pstocanonij
```

This was awesome,

Worked like a charm!  Cheers to [B]almikul :guitar:                   
[/B]

---

### Post by kurotsuno on 2010-03-02
I'm complete newbie so please understand I don't know all the commands or how to really use the terminal. 

I'm using ubuntu 9.10 amd64bit reading up it seems you can force the installation of these drivers but I don't have a clue how to do that. I've tried reading all the guides but its practically French to me

I have a canon pixma ip2600 and it wont print at all. So if someone can give a complete step by step on this I would be in your debt.

---

### Post by Cowboybebop79 on 2010-03-06
> **kurotsuno said:**
> I'm complete newbie so please understand I don't know all the commands or how to really use the terminal. 

I'm using ubuntu 9.10 amd64bit reading up it seems you can force the installation of these drivers but I don't have a clue how to do that. I've tried reading all the guides but its practically French to me

I have a canon pixma ip2600 and it wont print at all. So if someone can give a complete step by step on this I would be in your debt.

I have just gone through installing a pixma ip2500 and the process is basically the same as with the ip2600. So I will go through it step by step because it drives me nuts when some one posts that they have solved a particular problem but doesn't give a full explanation of how they did it. Taking in to account that inexperienced users and experienced users might need tot do the same thing.

Step 1. Download the packages posted by almikul in post #15
and move them to your home folder (makes it easier with terminal)

Step 2. Open terminal from Applications/Accessories menu

the packages are 32bit so if you double click the file to install deb package manager will give you lots of red writing and won't install them
but you can force install it through terminal (if you read this [page]("http://www.unixtutorial.org/2008/03/install-32-bit-deb-packages-on-64-bit/") and the command to do it)

Step 3. OK so you have terminal open it will be looking at your home folder by default cut and paste (ctrl+shift+v in terminal) this > ```
sudo dpkg -i --force-architecture rebuilt_common.deb
```
when terminal has completed this cut and paste this > 
```
sudo dpkg -i --force-architecture rebuilt_ip2600.deb
```

In both cases remember to scroll to the end of the line and press enter to start the process you will be asked for a password which is the password you login with.

step 4. in the same terminal run ```
ldd cifip2600
```
the output will tell you which files the driver can't find if you post the result of this command I can make a list of commands to run to solve that issue.

I will check back soon for your reply.

good luck!

---

### Post by kurotsuno on 2010-03-06
After I ran those codes I ran the code above to sort the filter error and it is now printing. Just trying to figure out how to network it to all the other computers now.

---

### Post by Cowboybebop79 on 2010-03-06
there's a how to in the Ubuntu documentation

[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu")

and there are probably plenty of forum threads about the subject.

and sometimes things just work without any fiddling about got a canon scanner plugged it in and it worked after not working on vista :p

---

### Post by nuchdog on 2010-03-08
> **saatu said:**
> I solved this and my canon ip2600 is printing back again.

Ran the following commands:

sudo chown -hR root /usr/lib/cups/filter
sudo chown -hR root /usr/lib/cups/backend
sudo chgrp -hR root /usr/lib/cups/filter
sudo chgrp -hR root /usr/lib/cups/backend

Thanks all for your help

I also had to:

sudo chmod 700 /usr/lib/cups/backend/cups-pdf
sudo chmod 700 /usr/lib/cups/backend

also for those trying to get cups-pdf to work, you might have to manually create the folder ~/PDF

mkdir ~/PDF

---

### Post by MButterman on 2010-04-26
I tried the and this was the output:

merrill@merrill-desktop:~/Downloads$ sudo dpkg -i --force-architecture rebuilt_common.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 153829 files and directories currently installed.)
Preparing to replace cnijfilter-common 2.90-1 (using rebuilt_common.deb) ...
Unpacking replacement cnijfilter-common ...
Setting up cnijfilter-common (2.90-1) ...
merrill@merrill-desktop:~/Downloads$ sudo dpkg -i --force-architecture rebuilt_ip2600.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 153829 files and directories currently installed.)
Preparing to replace cnijfilter-ip2600series 2.90-1 (using rebuilt_ip2600.deb) ...
Unpacking replacement cnijfilter-ip2600series ...
Setting up cnijfilter-ip2600series (2.90-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
merrill@merrill-desktop:~/Downloads$ ldd cifip2600
ldd: ./cifip2600: No such file or directory
merrill@merrill-desktop:~/Downloads$ ldd cifip2600
ldd: ./cifip2600: No such file or directory
merrill@merrill-desktop:~/Downloads$ 

Thanks the info and any help you can provide

---

### Post by almikul on 2010-04-26
Sorry, I cannot help you with this one. I took the 32-bit packages and just modified dependencies in them. 

What you could try is to find 64-bit packages from the same Asian Canon site and follow this [tutorial](http://forums.linuxmint.com/viewtopic.php?f=42&t=35136) to change the dependencies.

---

### Post by inverse-ion on 2010-07-13
> ldd: ./cifip2600: No such file or directory
&

> The printer's state message is: '/usr/lib/cups/filter/pstocanonij failed'.in the printer troubleshooter.

I'm running AMD64, Ubuntu 10.04, the ldd command is the only one that failed, and then the pstocanonij failing. No printer activity.
(total newbie to Linux, Windows user since 3.11 when I was 8 and really wanted to expand my horizons.)

any help or suggestions would be greatly appreciated!

---

### Post by pdc on 2010-07-14
try this

> sudo ln /usr/lib/cups/filter/pstocanonij /usr/lib64/cups/filter/pstocanonij

with the 64bit system, the lib files are in lib64 and the canon drivers are 32 bit drivers, so they look in /usr/lib so you create a symbolic link as above to tell the system to look in lib64

we hope that works

---

### Post by inverse-ion on 2010-07-17
same errors as before after running that, any additional suggestions would be great!

---

### Post by pdc on 2010-07-17
open a terminal

> cd /usr/lib/cups/filter

> ls

> cd

> cd /usr/lib64/cups/filter

> ls

please copy and paste the results od the two ls commands

---

### Post by inverse-ion on 2010-07-18
n.1
> bannertops      hpcac          pdftops       rastertoepson
commandtocanon  hpgltops       pdftoraster   rastertoescpx
commandtoepson  hplipjs        pstocanonij   rastertogutenprint.5.2
commandtoescpx  imagetopdf     pstopdf       rastertohp
commandtopclx   imagetops      pstops        rastertolabel
commandtops     imagetoraster  pstopxl       rastertopclx
cpdftocps       oopstops       pstoqpdl      rastertoqpdl
**cupsomatic**      pdftoijs       pstoraster    textonly
**foomatic-rip**    pdftoopvp      pstotiff      texttopdf
gziptoany       pdftopdf       **rastertodymo**  texttops
n.2
> bannertops      hpcac          pdftops       rastertoepson
commandtocanon  hpgltops       pdftoraster   rastertoescpx
commandtoepson  hplipjs        pstocanonij   rastertogutenprint.5.2
commandtoescpx  imagetopdf     pstopdf       rastertohp
commandtopclx   imagetops      pstops        rastertolabel
commandtops     imagetoraster  pstopxl       rastertopclx
cpdftocps       oopstops       pstoqpdl      rastertoqpdl
**cupsomatic**      pdftoijs       pstoraster    textonly
**foomatic-rip**    pdftoopvp      pstotiff      texttopdf
gziptoany       pdftopdf       **rastertodymo**  texttops

the bolded is in blue, while the rest of the text is green

---

### Post by pdc on 2010-07-19
so pstocanonij is in /usr/lib/cups/filter

whereas your 64 bit system is looking in /usr/lib64/cups/filter

if you copied and pasted this

> cd /usr/lib/cups/filter and pressed ENTER

and then copied and pasted this

> sudo cp /usr/lib/cups/filter/pstocanonij /usr/lib64/cups/filter  

that is aiming to copy the file pstocanonij into the comparable directory in lib64

linux is for adults so I am suggesting and it is your system; it should be fine and you can delete the file if it does not help

---

### Post by inverse-ion on 2010-07-21
ah, you fixed my newb-ish issues! thank you very much.
As I said though, Windows user since Windows 3.11 (circa 1994) which makes me 24 now. I learned how to type on a monochrome Apple II, so I'm no stranger to the "other" guys, there is just quite a bit more to Linux than anticipated. Perhaps I should join the local LUG.

---

### Post by pdc on 2010-07-21
delighted to hear your printer is now working; my comments about linux were just to mean: I suggest; you carry them out; if any problems, I hope not to attract too much blame! 

enjoy your printer: great to hear it is now working; do look out for a local LUG: usually a friendly, and mixed bunch of users of many ages!

best wishes

---

### Post by stovie87 on 2010-07-25
> **lubeck said:**
> DRIVERS for the CANON Pixma iP2600 are indeed located at:
[http://support-asia.canon-asia.com/](http://support-asia.canon-asia.com/)           as "naildeca" says.

**Couple Notes, FYI:**
This install took about 5 minutes... easy for a noob like me.

In addition to the two .deb files (the drivers) mentioned by "naildeca" above at this site (the drivers appear when you select the Injet, Pixma, iP2680 printer, Downloads), are the **VERY USEFUL Linux install instructions (Ubuntu included)** listed if you then select "Manuals":

"IJ Printer Driver Ver. 2.90 for Linux (Operation guide [Explanation of the iP2600series operation (html file)]"

With this wonderful documentation the installation went a bit easier... since there is one install step one must take before installing the .debs.

Noteworthy in these instructions, CANON recommends the following command at the Terminal before installing the .debs, to ready the system to "receive" them.  I found this necessary and fundamental:

sudo aa-complain cupsd   

Final Notes:
The install instructions include a step called "Register the Printer to the Spooler."  A sample command is shown, so this is easy to do.  However, part of the command needs two things that are peculiar to your computer after you install the .debs.  
[printer_name] 
[PPD_filename] 
[device_URI]
Printer name and the URI may be easily found at System, Administration, Printing ... and your iP2600 PPD can be found using "locate *.ppd" at the command line.

If it helps, mine was located in /usr/share/ppd/canonip2600.ppd, and after the Registration command, in /etc/cups/ppd/canonip2600.ppd

Some applications need to be told the Printer "PPD" to allow them to understand how to talk to the iP2600, so you may want to save this location in a text file--for later recall or copy & paste.
Thanks to those who forged the path and helped me find the drivers.
Best wishes.
I finally got it to work thanks!!


i found that i needed to remove and  reinstall the cnijfilter-common2 package before i got it to work.

---

### Post by jiggzson on 2010-10-19
If you tried installing the Asian drivers but you're getting a dependencies error [try these. ]("http://rapidshare.com/files/426070260/Rebuilt_drivers_IP2600.tar.gz")The dependencies were changed using a tutorial on the web. Worked for me.

---

### Post by murpter on 2012-05-18
Okay after a ridiculous amount of hassle, I have found a method to make an iP2600 work in Ubuntu 12.04
First download the two customized drivers from this [thread]("http://ubuntuforums.org/showthread.php?p=9355680#poststop")
These are drivers that have been altered to enable the driver to play nicely with the new libcups2 package.

Next, open the terminal.
**type**: sudo aa-complain cupsd
This prepares the system for the driver, also move your downloaded files to your Home folder out of downloads.

Next, in the terminal, **type**: sudo dpkg -i cnijfilter-common_2.90-1_i386_1004customized.deb

**Then follow that up with**: sudo dpkg -i cnijfilter-ip2600series_2.90-1_i386_1004customized.deb

These should now be installed but there will be a filter issue. You resolve this with **two commands**:
sudo chown root /usr/lib/cups/filter/pstocanonij
sudo chmod 755 /usr/lib/cups/filter/pstocanonij

Now the printer should be able to be added through the control menu at the top right -printers... and if needed, Add...

Hope it helps!

Acknowledgements: Thank you to MillDaKill, China_Jobs, and TechnoStripe.com for the info and files, since this is but an application and compilation of your work.
Tested on: Ubuntu 12.04 LTS Precise Pangolin 32-bit

---

### Post by ppssupport on 2012-12-10
I know, I'm very late, but...

Please view this tutorial, it contains very easy instruction for terminal user and shell script user.

[http://www.ppsolution.net/en/articles/linux/ubuntu_driver_printer_canon_ip2600.pdf](http://www.ppsolution.net/en/articles/linux/ubuntu_driver_printer_canon_ip2600.pdf)

---

### Post by Davey_Burgess on 2013-08-27
An even later response, but those who are running 12.04 LTS and above 64bit will like this one!  
[http://askubuntu.com/questions/230039/installing-canon-ip2600-printer-drivers-on-ubuntu-12-10](http://askubuntu.com/questions/230039/installing-canon-ip2600-printer-drivers-on-ubuntu-12-10)
The second answer worked perfectly for me on an AMD dual core running 64bit.  In case the link above should stop working, here's the meat of it:
> After updating to Ubuntu 13.04 (64-bit), I got my Canon ip2600 printer to work with the canon-trunk repository:
  ```
sudo add-apt-repository ppa:michael-gruz/canon-trunk
sudo apt-get update
sudo apt-get install cnijfilter-ip2600series

```
Hope that helps someone else :)

---


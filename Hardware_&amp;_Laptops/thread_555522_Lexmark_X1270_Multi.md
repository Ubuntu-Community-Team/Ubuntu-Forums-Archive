---
title: "Lexmark X1270 Multi"
date: 2007-09-20
forum: Hardware &amp; Laptops
---

### Post by Chief_Darkcloud on 2007-09-20
I am having problems getting my Lexmark X1270 which is Printer/Scanner combo. Ubuntu will recognize it but when I go thru the config it does not work. I have seen a few threads with few responses on how to get this to work. Has anyone gotten the printer/scanner X1270 to work in Ubuntiu? Any help would be appreciated.

---

### Post by archolman on 2007-09-20
I've been having trouble with the same thing, but my PC won't even see the printer. Help needed , or advice on/reccomendations for, an all-in-one that runs 'Plug&Play' with ubuntu 6.0.* LTS.
Thanks,
Dick

---

### Post by Chief_Darkcloud on 2007-09-20
I take it by the lack of response that a Lexmark X1270 will not work in Linux? Seems like all the previous threads asking for help with this printer/scanner did not get responses. Please help as I dont want to buy another machine or have to also run Windows on my HD just to print.

---

### Post by preacher2B on 2007-09-20
I also have a Lexmark x1270. I am running Ubuntu 7.04 AMD64. The problem with the drivers from what I have found is that they are for a 32 bit OS. I have not been able to find out how to use the drivers in a 64 bit OS. The only people I have found that can run the Lexmark x1270 have done so by using a chroot or reinstalling using a 32 bit OS. 

I hope you find a solution, I am still needing my printer to work using the 64 bit OS.

---

### Post by timothy632 on 2007-09-23
MUST INSTALL BOTH OF THESE 


 [http://leighm.dgtlmoon.com/misc/binaries/z600cups_1.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/binaries/z600cups_1.0-2_i386.deb)

[http://leighm.dgtlmoon.com/misc/binaries/z600llpddk_2.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/binaries/z600llpddk_2.0-2_i386.deb)

USE THE GDEBIAN PACKAGE INSTALLER 

GO TO PRINTERS AND U SHOULD FIND THE Z600 UNDER DRIVERS USE THIS FOR THE X1270 

FOR MORE HELP GO HERE [http://dgtlmoon.com/dell_720_printer_lexmark_z600_printer_on_debian_sarge](http://dgtlmoon.com/dell_720_printer_lexmark_z600_printer_on_debian_sarge)

---

### Post by archolman on 2007-10-04
OK, I swapped the X1270 for a X1180:-) as its an all-in-one. Any pointers? I'll try anything once:-)
Please, has anyone got a clue as to what printers I can buy will run with ubuntu/Linux.

---

### Post by QB89Dragon on 2007-10-06
I'm unable to make it work on an amd64 computer. Is there any windows printer-driver converter, like ndiswrapper is for wireless card drivers?

---

### Post by coffeecat on 2007-10-06
> **archolman said:**
> Please, has anyone got a clue as to what printers I can buy will run with ubuntu/Linux.

If you buy a Hewlett-Packard printer you'll be almost (but not quite 100%) sure of getting one that works ootb with Linux. HP is probably the most Linux-friendly of the main printer manufacturers. Have a look in Synaptic, and you'll find the HPLIP toolbox.

[This link is worth bookmarking]("http://www.linux-foundation.org/en/OpenPrinting"). It's what used to be LinuxPrinting dot org. Have a hunt around. Lots of useful advice and databases on compatible printers. Just make sure the make and model you are thinking of buying is listed as supported and you should be fine.

Oh, and did I mention that HP is the brand to go for? :wink:

---

### Post by daverave999 on 2007-10-07
> **timothy632 said:**
> MUST INSTALL BOTH OF THESE 


 [http://leighm.dgtlmoon.com/misc/binaries/z600cups_1.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/binaries/z600cups_1.0-2_i386.deb)

[http://leighm.dgtlmoon.com/misc/binaries/z600llpddk_2.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/binaries/z600llpddk_2.0-2_i386.deb)

USE THE GDEBIAN PACKAGE INSTALLER 

GO TO PRINTERS AND U SHOULD FIND THE Z600 UNDER DRIVERS USE THIS FOR THE X1270 

FOR MORE HELP GO HERE [http://dgtlmoon.com/dell_720_printer_lexmark_z600_printer_on_debian_sarge](http://dgtlmoon.com/dell_720_printer_lexmark_z600_printer_on_debian_sarge)

Thank you so much! This has worked perfectly for me.

---

### Post by sambucuself on 2007-10-08
it works, but it also has a scanner built in that is not working ? what to do?

I know my way around linux, but not with scanning in linux, so your reply would be very mych appreciated.

---

### Post by sambucuself on 2007-11-23
it works under my amd64 machine, but only the printer function, it won't scan...

help!

---

### Post by sebman2112 on 2008-01-08
OK, for those using the X1270 Scanner/printer from Lexmark in Windows XP 64 bit environments I might have a solution for you.

Go to Lexmarks website. The fallowing page should work: [http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:537:0:0](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:537:0:0)

Then download the "Windows Vista (x64)" drivers. You might be thinking I'm incorrect here, but this driver pack also includes 64 bit drivers for Windows XP. Here's the deal. I tried installing the printer drivers first, but I either couldn't get it to install, or work correctly. What I found worked for me was installing the scanner drivers first, then installing the printer drives. Now both the scanner and printer are working fine, and I'm running Windows XP Pro 64 bit with service pack two and all updates. Don't think I'm wrong about the scanner working if you're "scan" button on the top of the unit doesn't work, as you can scan without using that button (by using the scanner software installed on your PC).

Hopefully this works for other people, as it is truly working for me. Oh, and I just printed out a receipt and scanned photos last night. Everything looked fine. 

I don't know if this will help those here, but I know there are plenty of people who can't install this printer using their Windows XP 64 bit system, so it will be good to have to info on the net.

---

### Post by t3cat5 on 2008-02-20
Hey thanks dude it worked out great for me, my x1270  printer is working fine now in ubuntu gutsy 7.10

---

### Post by SuporteTecnicoID on 2008-03-15
Hi,,,,

I've this drivers for printer and scanners for X1270 Lexmark working fine in Linux by my distro ResuLinux, but this work fine in your distro too,,,,,

[http://www.resulinux.forumdebian.com.br/web/forum/viewtopic.php?p=18152#18152](http://www.resulinux.forumdebian.com.br/web/forum/viewtopic.php?p=18152#18152)

You want help, pleasy contact-me in my messenger :

[email]suporte@indexdata.com.br[/email]  

:):):)

---

### Post by lilnovina on 2008-05-03
> **timothy632 said:**
> MUST INSTALL BOTH OF THESE 


 [http://leighm.dgtlmoon.com/misc/binaries/z600cups_1.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/binaries/z600cups_1.0-2_i386.deb)

[http://leighm.dgtlmoon.com/misc/binaries/z600llpddk_2.0-2_i386.deb](http://leighm.dgtlmoon.com/misc/binaries/z600llpddk_2.0-2_i386.deb)

USE THE GDEBIAN PACKAGE INSTALLER 

GO TO PRINTERS AND U SHOULD FIND THE Z600 UNDER DRIVERS USE THIS FOR THE X1270 

FOR MORE HELP GO HERE [http://dgtlmoon.com/dell_720_printer_lexmark_z600_printer_on_debian_sarge](http://dgtlmoon.com/dell_720_printer_lexmark_z600_printer_on_debian_sarge)



That definitely worked for me!! Thanks a million!!:guitar: 

And for any other Linux newbies like myself, just download those files to your hard drive and double-click them (ubuntu desktop) and it will start the install. If you download them to a server on your LAN, you have to copy them to your home folder (or another local folder) first. For some reason when I tried to run them from the network drive they would just open in archive manager.:confused: Wierd.

---

### Post by durableapostle on 2008-05-15
> [http://leighm.dgtlmoon.com/misc/bina...1.0-2_i386.deb]("http://leighm.dgtlmoon.com/misc/bina...1.0-2_i386.deb")

[http://leighm.dgtlmoon.com/misc/bina...2.0-2_i386.deb]("hhttp://leighm.dgtlmoon.com/misc/bina...2.0-2_i386.debttp://")

USE THE GDEBIAN PACKAGE INSTALLER

GO TO PRINTERS AND U SHOULD FIND THE Z600 UNDER DRIVERS USE THIS FOR THE X1270

FOR MORE HELP GO HERE [http://dgtlmoon.com/dell_720_printer...n_debian_sarge](http://dgtlmoon.com/dell_720_printer...n_debian_sarge)

Works! Finally! Thanks a million!

---

### Post by Programmer210 on 2008-06-26
> **preacher2B said:**
> I also have a Lexmark x1270. I am running Ubuntu 7.04 AMD64. The problem with the drivers from what I have found is that they are for a 32 bit OS. I have not been able to find out how to use the drivers in a 64 bit OS. The only people I have found that can run the Lexmark x1270 have done so by using a chroot or reinstalling using a 32 bit OS. 

I hope you find a solution, I am still needing my printer to work using the 64 bit OS.

See the post from Timothy for the stuff you will need. Don't install
directly, however. Under Ubuntu 64 bit, 32 bit stuff needs to go into the
/lib32 directory. I used "alien -t" to convert the two deb's into tar
files that I could deal with easier. I extracted them in /tmp. Then I
copied the parts I wanted to the real locations. You need all of the
printer-specific stuff. I didn't copy in the header (.h) files. When you
have the libraries (.a, .so, etc.) in /lib32, you will need to make the
normal "XXX.so.0" symbolic links to them.

After all that is done, check that you can load the rastertoz600 and
z600 binaries without loader errors. If all is well, then use the
printer admin tool to create a new printer, and select z600 as the driver.
Then restart the CUPS service. Printing should now work. For me, under
8.04 LTS, the scanning worked without me doing anything, so I was
surprised when printing didn't.

---


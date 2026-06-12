---
title: "Help with lexmark x5470 printer drivers!"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by FPU4eva on 2006-12-25
well reinstalled ubuntu after vista gave me the fits anyways how can i get this printer to install correctly the printer doesent respond to the printer setup in ubuntu anyone have the drivers?

---

### Post by cilynx on 2006-12-25
Does it show up at all in the printer setup and then just not work or does your computer claim that there are no printers attached?

---

### Post by FPU4eva on 2006-12-25
well it says printing but on the printer it says failed only printer avalible is the 5400 hundrard

---

### Post by cilynx on 2006-12-25
Using the 5400 driver should work.  Generally, all printers in a series use the same driver.

Were there multiple driver options when you setup the printer?  You may want to try another.

---

### Post by FPU4eva on 2006-12-25
edit its the 5000 driver but anyways it says its the recommended one but then when i print a test page it says failled to get application data on my printer ugh

---

### Post by FPU4eva on 2006-12-25
anyone please?

---

### Post by cilynx on 2006-12-25
I'm not sure that the 5000 series and the 5400 series use the same driver.  I'm not really a Lexmark guy.  You're beyond my scope here.  Anyone else?

---

### Post by FPU4eva on 2006-12-25
i want this printer to work so bad so i can ditch windows completly! ugh

---

### Post by FPU4eva on 2006-12-26
well comeon someone help!

---

### Post by FPU4eva on 2006-12-26
well no  one will help....

---

### Post by cilynx on 2006-12-27
Much more likely, no one can help.  Do a google search.  You have a rare printer.  If no one else has it working, you can't really expect anyone to be able to tell you how to do it.  Maybe you can fight with it a bit more and figure it out for the next person.

---

### Post by brundlelfy76 on 2007-03-28
Much like yourself, I own a Lexmark x5470 and am viciously trying to ditch Win-doze.  Also, having the EXACT same issue as you.

I'm sure you already know this, but the Lexmark website has ZERO support for us Linux folks as far as drivers.  They just provide a silly flowchart so that we "Linux enthusiasts" can write our own code.  When will people understand that just because we choose to use it as an operating system DOESN'T automatically mean we can program in it?

Anyhow...on another forum, I followed a thread and found that we own one of the magical paperweight printers that is NOT supported by CUPS or SANE, the two big Linux standards for scanning and printing devices..... which means that we are probably either going to end up buying new printers or running dual boot Win/Linux computers.

But, in the off chance you find something.... LET ME KNOW!  Thanks.

---

### Post by ramjet_1953 on 2007-03-30
If you follow this link: [http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-x5470](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-x5470)

You will see why there has not been a plethora of replies.

Basically as it says, under Linux, it is a paperweight.

Sorry!

Regards,
Roger :cool:

---

### Post by Austin_KW on 2007-03-30
For my lexmark and dell paperweights, I leave them connected to an old windows pc with ghostscript and redmon. I can then print to them as networked postscript printers using samba. Not perfect but at least I can use them from my linux laptops.

---

### Post by ashesoffire on 2007-04-11
i have an X5270 and i am encountering more or less the same problem, i can only get the machine to 'begin' a test page, the it just stops once the sheet has fed into the printer uhh track and no ink comes out, the cartriges just slide over to the left again, i have tried using various drivers both the 5000 and the 5700 as well as several others, please help (us) - lengthy post =(

---

### Post by mattyp1 on 2007-05-13
I just picked one of these devices up for a gift, the card reader works, haven't tried the fax or copier but I would hope they work. Unfortunately printing does not and the 5000 driver appears to be the closest option to 5400 (5470). I have done quite a bit of google searching and found a lot of posts with people complaining that the device is now a paperweight. Since there is a demand I would hope someone can figure this out. I will certainly try, there is a Linux driver development kit on Lexmark's site ([http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668523_676599624_en,00.html)](http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668523_676599624_en,00.html)). I'm no programmer but have a friend who wrote drivers for Lexmark a long time ago. I will beg him for his help. Otherwise, I will be returning this device or switching my parents back to Windows :( .

---

### Post by mattyp1 on 2007-05-16
It turns out that the development kit does not cover this All in One series. So, knowing I was SOL, I returned the printer and bought an HP Officejet for $30 more.

Good luck, sorry I couldn't help.

---

### Post by JSThePatriot on 2007-05-22
Unfortunately, the printer came with the new PC that I purchased so I am unable to return it to the store. This is a very nice printer (as far as Lexmarks go), and it would be nice to get it working. I thought I had seen some where a few days ago that someone had it working with a 5000 driver (as that's what is recommended), but I am now unable to find that post.

My problem is slightly different. Linux thinks it printed. The job never errors out, but it eventually "prints". Not sure why that is.

If there is anyone that figures this out please post this here so we know what you did!

Thanks,
JS

---

### Post by Mike Denman on 2007-05-26
I resently bought an X5470 Lexmark printer and after instalation found it to fax, print, scan, and copy as advertised. However after shutting down and attempting a reboot, my computer would freeze after going through a couple lines of bootup instructions. I then shutoff power and rebooted and after several attempts got it through the boot cycle. Again after shutdown had the same problems booting. Since this problem occurred as a result of adding this new printer, I disconnected the USB cable from the printer and walla, the problem went away - system booted normally. I have since added a USB 2.0 4-port hub placing it to the left of my PC and have my USB cable from the printer hanging over it. I now boot up my PC first and then plug in the printer. This has solved my problem and all for $7 as the hub was on sale at MicroCenter. I am now waiting word from Lexmark as to their answer to this problem. I do think the X5470 is a great all-in-one printer for the price.

 I hope this information will be of some help to those who have had booting problems with this printer.

---

### Post by Austin_KW on 2007-05-27
> **Mike Denman said:**
> I resently bought an X5470 Lexmark printer and after instalation found it to fax, print, scan, and copy as advertised. However after shutting down and attempting a reboot, my computer would freeze after going through a couple lines of bootup instructions. I then shutoff power and rebooted and after several attempts got it through the boot cycle. Again after shutdown had the same problems booting. Since this problem occurred as a result of adding this new printer, I disconnected the USB cable from the printer and walla, the problem went away - system booted normally. I have since added a USB 2.0 4-port hub placing it to the left of my PC and have my USB cable from the printer hanging over it. I now boot up my PC first and then plug in the printer. This has solved my problem and all for $7 as the hub was on sale at MicroCenter. I am now waiting word from Lexmark as to their answer to this problem. I do think the X5470 is a great all-in-one printer for the price.

 I hope this information will be of some help to those who have had booting problems with this printer.


Disable booting from USB in the BIOS or check your BIOS for an update. Some PCs attempt to boot from the card reader in the lexmark printer causing the problem.

---

### Post by mattyp1 on 2007-05-27
> **Mike Denman said:**
> I resently bought an X5470 Lexmark printer and after instalation found it to fax, print, scan, and copy as advertised. However after shutting down and attempting a reboot, my computer would freeze after going through a couple lines of bootup instructions. I then shutoff power and rebooted and after several attempts got it through the boot cycle. Again after shutdown had the same problems booting. Since this problem occurred as a result of adding this new printer, I disconnected the USB cable from the printer and walla, the problem went away - system booted normally. I have since added a USB 2.0 4-port hub placing it to the left of my PC and have my USB cable from the printer hanging over it. I now boot up my PC first and then plug in the printer. This has solved my problem and all for $7 as the hub was on sale at MicroCenter. I am now waiting word from Lexmark as to their answer to this problem. I do think the X5470 is a great all-in-one printer for the price.

 I hope this information will be of some help to those who have had booting problems with this printer.

Austin_KW - Are you saying that this printer works for you using Ubuntu? Or, are you using it under Windows or MAC?

---

### Post by Austin_KW on 2007-05-27
The hang on boot is a bios/configuration problem where some PCs attempt to boot from the printer storage devices and so will hang whether you are trying to boot linux/windows.

My lexmark is connected to a windows xp PC. I use ghostscript and redmon to share the printer as a  postscript printer. 
I can then print from my ubuntu PCs using a postscript driver. Not a perfect solution but at least I can use the printer.

I never managed to get my lexmark/dell printers to work under linux but as I have a windows PC that is always on, I gave up trying and use the ghostscript & port redirection method.

---

### Post by mattyp1 on 2007-05-27
> **Austin_KW said:**
> The hang on boot is a bios/configuration problem where some PCs attempt to boot from the printer storage devices and so will hang whether you are trying to boot linux/windows.

My lexmark is connected to a windows xp PC. I use ghostscript and redmon to share the printer as a  postscript printer. 
I can then print from my ubuntu PCs using a postscript driver. Not a perfect solution but at least I can use the printer.

I never managed to get my lexmark/dell printers to work under linux but as I have a windows PC that is always on, I gave up trying and use the ghostscript & port redirection method.

Thank you for the clarification Austin_KW. Not a bad solution if you're running multiple machines, unfortunately (or fortunately for me), my parents only run one machine so this wasn't an option. I'm sure support will improve as linux becomes more popular. Until then I'll stick with HPs.

Take care,

Matt

---

### Post by ramjet_1953 on 2007-05-28
If you follow this link, you will see that there is little that can be done:

[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-x5470](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-x5470)

Lexmark are the least Linux-friendly printers on the market. They refuse to release information on hardware and firmware, making it almost impossible for coders to write Linux drivers for their printers.

It is not a problem with Linux, it is a problem with Lexmark's attitude towards open source.

If you have an old Windows box lying around, you could always use it as a print server.

Much better to just buy a HP printer, which work fine under Linux.

Regards,
Roger :cool:

---

### Post by Mike Denman on 2007-05-29
My OS is Windows

---

### Post by woland on 2007-06-02
Actually, Lexmark has decided [to release a SDK]("http://www.lexmark.com/lexmark/sequentialem/home/0,6959,204816596_659668505_0_en,00.html") for it's printers, so the Linux community developers would develop the Linux printer drivers for themselves. 

It would be great that all the hardware manufacturers do at least that much. If they would bother to release an open source drivers for themselves it would be even greater.

---

### Post by Prisma on 2007-06-02
wow, they finally did? that is really good. Bad thing they loosed many customer like me for not supporting Linux earlier. ;)

---

### Post by tzileon on 2007-06-27
Dear all,

I had the same problem with a Lexmark X5400 series (x5450 all in one). It was impossible to find drivers for Linux (I use Linux mint & ubuntu), so I installed vmware workstation under linux. I made a Windows 2000 virtual machine and I installed the printer in the VM. So, every time I need Lexmark printer I run the vmware player and the win2000 virtual machine, without leaving the Linux environment!

So, until Lexmark give the Linux community drivers, I think that the vmware is a solution.

---

### Post by TasKiNG on 2007-07-12
I sent an email to lexmark about this issue. Below is my email and their reply for anyone interested :-

I have just upgraded from windows to Linux Ubuntu.
 
 I cannot find any lexmark drivers for this printer that will work under
 Linux. Looking around the forums it seems there are a loads of other
 people with the same problem.
 From what I can tell it seems that Lexmark
 Linux support is non-existent. If this is the case then it is very
 disappointing as you are missing out on a huge amount of custom and it
 also means that I now have a big , nice looking paperweight on my desk.
 Any
 help resolving this issue will be appreciated.
 If you cannot help then
 please forward this to whoever it may concern.
 
 Cheers

--------------------------------------------------------------------------------------------------------------------

>From Lexmark UK Technical Support Team
Phone no.  (UK) 02073652496, (IRE) 012421090
Monday to Friday 9 am to 5.30 pm.
Fax no. (UK) 02073653021 (IRE) 012421091

Dear Dave,

Thank you for contacting Lexmark International.

Currently our only inkjet printers that have Linux support are the Lexmark
3000, the 1020 Business Edition (model 4078-001), the 4079 Plus and the
Optra Color 40/45 with Postscript Level 2 or PCL 5 emulation. As of
November 1st we now have support and drivers available for the LINUX OS on
the Z32 (Z22 if you have both cartridges installed) and the Z52.

Supported Linux versions:

Red Hat 6.1+
SuSe 6.3+
Mandrake 7.0+


Minimum system requirements:

200 MHz
32 MB RAM
20 MB HD


Z32 (Z22) Parallel support only
Z52 Parallel and USB support


All of our other inkjet printers are host based printers that were
developed for Windows 3.1 and Windows 95/98, NT/2000, and MacIntosh in some
cases. We appreciate your comments and customer feedback helps in
determining the interest level of our Lexmark customers with the various
operating systems. Although we do not have a solution for you at this time,
we will pass your comments on to our marketing department. They are
constantly evaluating our product line and input such as yours is extremely
valuable.

----------------------------------------------------------------------------------------

---

### Post by grokwik on 2007-09-12
I send the same (more or less) now, maybe insisting a lot will help, for the worst, it doesn't cost anything...

---

### Post by pianomany2k on 2007-09-12
It looks like someone could use the information about the "sample Z55 driver" to construct the driver for the x5470.

No, I'm not going to even attempt it.

---

### Post by grokwik on 2007-09-13
It has never been attempted by anyone ?

---

### Post by Shingo [fw] on 2007-09-14
I have lexmark x5250 printer and I was trying to install my printer with LLDDPK.

> shingo@magi:~/Desktop/print$ sudo alien --scripts x5250llpddk-2.0-3.i386.rpm
Password:
x5250llpddk_2.0-4_i386.deb generated

I installed this deb package with no errors, but I don't know what to do with this:

> shingo@magi:~/Desktop/print/Z55SampleCUPS-1.0-1$ make
(cd ./source/backend; make -f Makefile)
make[1]: Wej&#347;cie do katalogu `/home/shingo/Desktop/print/Z55SampleCUPS-1.0-1/source/backend'
make[1]: `../../bin/z55' jest aktualne.
make[1]: Opuszczenie katalogu `/home/shingo/Desktop/print/Z55SampleCUPS-1.0-1/source/backend'
(cd ./source/filter; make -f Makefile)
make[1]: Wej&#347;cie do katalogu `/home/shingo/Desktop/print/Z55SampleCUPS-1.0-1/source/filter'
[ -d Objects ] || mkdir Objects
g++  -I./ -c -g -Wall -O2 -funsigned-char main.cpp -o Objects/main.o
In file included from z55filter.h:30,
                 from main.cpp:33:
cupsraster.h:24:25: error: cups/raster.h: No such file or directory
cupsraster.h:117: error: ISO C++ forbids declaration of ‘cups_raster_t’ with no type
cupsraster.h:117: error: expected ‘;’ before ‘*’ token
cupsraster.h:118: error: ‘cups_page_header_t’ does not name a type
z55filter.h:69: error: extra qualification ‘Z55Filter::’ on member ‘UpdateInkLevels’
make[1]: *** [Objects/main.o] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/home/shingo/Desktop/print/Z55SampleCUPS-1.0-1/source/filter'
make: *** [all] B&#322;&#261;d 2

---

### Post by grokwik on 2007-09-14
It seems that the building of the cpp files at the end failed...
If I'm not wrong :
You have a library (cups/raster.h) missing :
>> cupsraster.h:24:25: error: cups/raster.h: No such file or directory
And that's what gives you all the other errors.
I checked the last cups source code (1.4svn-r6926) and raster.h is not in the cups directory but in the filter directory...
There's not a problem of version in your dependencies ?

---

### Post by Shingo [fw] on 2007-09-17
After installing "gcc-3.4" I have something like this:

> shingo@magi:~/Desktop/print/Z55SampleCUPS-1.0-1$ CC="gcc-3.4" make(cd ./source/backend; make -f Makefile)
make[1]: Wej&#347;cie do katalogu `/home/shingo/Desktop/print/Z55SampleCUPS-1.0-1/source/backend'
make[1]: `../../bin/z55' jest aktualne.
make[1]: Opuszczenie katalogu `/home/shingo/Desktop/print/Z55SampleCUPS-1.0-1/source/backend'
(cd ./source/filter; make -f Makefile)
make[1]: Wej&#347;cie do katalogu `/home/shingo/Desktop/print/Z55SampleCUPS-1.0-1/source/filter'
[ -d Objects ] || mkdir Objects
g++  -I./ -c -g -Wall -O2 -funsigned-char main.cpp -o Objects/main.o
z55filter.h:69: error: extra qualification ‘Z55Filter::’ on member ‘UpdateInkLevels’
make[1]: *** [Objects/main.o] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/home/shingo/Desktop/print/Z55SampleCUPS-1.0-1/source/filter'
make: *** [all] B&#322;&#261;d 2

---

### Post by grokwik on 2007-09-17
Hum... Sorry but I have problems with polish :D
Anyway, (my colleague is polish) it seems the build has problem accessing a directory (maybe a question of rights ?).
Maybe you can check at line 69 of the z55filter.h file, it seems there's a bad function call...
Sorry, I can't tell anything more.

---

### Post by Shingo [fw] on 2007-09-18
I've deleted &#8216;Z55Filter::&#8217; from that file and it seems to be ok now but I have another error ;p

> shingo@magi:~/Desktop/print/Z55SampleCUPS-1.0-1$ make
(cd ./source/backend; make -f Makefile)
make[1]: Wej&#347;cie do katalogu `/home/shingo/Desktop/print/Z55SampleCUPS-1.0-1/source/backend'
make[1]: `../../bin/z55' jest aktualne.
make[1]: Opuszczenie katalogu `/home/shingo/Desktop/print/Z55SampleCUPS-1.0-1/source/backend'
(cd ./source/filter; make -f Makefile)
make[1]: Wej&#347;cie do katalogu `/home/shingo/Desktop/print/Z55SampleCUPS-1.0-1/source/filter'
[ -d Objects ] || mkdir Objects
g++  -I./ -c -g -Wall -O2 -funsigned-char z55filter.cpp -o Objects/z55filter.o
[ -d Objects ] || mkdir Objects
g++  -I./ -c -g -Wall -O2 -funsigned-char cupsraster.cpp -o Objects/cupsraster.o
cupsraster.cpp: In member function &#8216;void CupsRaster::MirrorImage(unsigned char*, long int)&#8217;:
cupsraster.cpp:165: warning: comparison between signed and unsigned integer expressions
[ -d ../../bin ] || mkdir ../../bin
g++ -llexprintjob -llexz55core -lcups -lcupsimage -o ../../bin/rastertoz55 Objects/main.o Objects/z55filter.o Objects/cupsraster.o
/usr/bin/ld: cannot find -llexz55core
collect2: ld returned 1 exit status
make[1]: *** [../../bin/rastertoz55] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/home/shingo/Desktop/print/Z55SampleCUPS-1.0-1/source/filter'
make: *** [all] B&#322;&#261;d 2


> /usr/bin/ld: cannot find -llexz55core

I have this file there but I can't edit it. Maybe I should just give up and accept using win98 for printing...

---

### Post by grokwik on 2007-09-18
the warning is not really important : "warning: comparison between signed and unsigned integer expressions"

The error : "/usr/bin/ld: cannot find -llexz55core"
Means the compiler (g++) doesn't find the library "lexz55core". I guess it's installed, if so, the problem comes from the include paths, i.e. the locations (on the hd) where the g++ looks for libraries.

---

### Post by John Bennett on 2007-10-07
I have a Lexmark x5470 hooked to a Windows XP box in my living room.

Ubuntu Feisty allows me to set up the printer like this..

[IMG]http://img.photobucket.com/albums/v227/jbennett1966/misc/lexmarkprint.jpg[/IMG]

When I try to print, I get the following error...

> Printing: Error writing spool: ERRSRV - ERRerror 
(Non-specific error code.)

---

### Post by Maxh on 2007-11-01
I can't help. I need help. I had a perfectly operational Lexmark X5470 operating with my Imac on system 10.4.9. I upgraded to System 10.5 (Leopard). The system works well but attempts to print have crashed the program (whatever) I am printing from. I re-installed OS 10.5. Still didn't work. I downloaded the latest Lexmark drivers (twice) and installed. They don't work!

I think Lexmark has not got an appropriate driver for Mac OS 10.5, apparently.

Any suggestions.

---

### Post by winhamwr on 2007-11-25
I'm another ubuntu user suffering a lack of linux driver support. I'll send in something to lexmark so that they can "forward it to their marketing department."

---

### Post by pianomany2k on 2007-11-26
well, you're closer to printing with your x5470 than I am.

---

### Post by scrooge_74 on 2007-11-26
Hope it works, I send them an email also a few weeks ago in the hope that they see the light one day.  But the response was some sort of script, in other words we are #$%&!

---

### Post by tiberius_k on 2008-01-31
Hi, 
I assume the rest of you can write to a memory card inserted into the printer as I can. If so (and I'm at work, so I haven't had a chance to try this), you could make a jpg (jpeg) image of the doc, save it on the memory card, and print from that using the functions built into the printer. You could leave a card in the printer full-time (I have a 4MB Memstick that came with my camcorder) and use it as a default print directory. Granted, this would be a pain in the... neck for anything more than a couple of pages, but I'm catching... heck because my wife can't even print a recipe! Is there a setting in CUPS or another app that will print a doc to a jpeg file? 

Cheers,

Kirk.

---

### Post by grokwik on 2008-02-01
...******* good idea...
I'm burning to try that out (I'm at work too:s) ! At last I'll have all my recipies cooked ;)

---

### Post by brucerealtor on 2008-03-31
You know Lexmark does support the X5270 in 2 versions of Red Hat Linux.

Anyone know if you can use a Red Hat driver in Ubuntu?

---

### Post by ashvee on 2008-04-01
has anyone tried x5270 is it working 
can we use the same for x5470

---

### Post by ashvee on 2008-04-01
where can we download the driver x5270 for linux

---


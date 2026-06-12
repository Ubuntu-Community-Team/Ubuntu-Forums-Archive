---
title: "HP Deskjet 690c wont print!!!!"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by seiflotfy on 2005-09-12
I have an HP Deskjet 690c, however i cannot print anything!!!
I installed cups and hpij!!!
when i try printing anything from openoffice (even with lpr) it stops at Queue!!!
Please help me i dont want to buy a new Printer!!! :)

---

### Post by seiflotfy on 2005-09-12
any1 there?

---

### Post by David Haas on 2005-09-12
seiflotfy--The HP Deskjet 690C appears to be supported by Ubuntu 5.04, for I see the PPD file installed in the HP directory at /usr/share/cups/model/foomatic-ppds/HP. The file is HP-DeskJet_690C-cdj670.ppd.gz. How did you try to install the printer? You didn't need to install either CUPS or the driver, since Ubuntu has them both in its distribution. You might want to look in the Synaptic Package Manager to see what CUPSYS packages came with Ubuntu. It's at System>Administration>Synaptic Package Manager. I have five packages, from cupsys to cupsys-driver-gimprint-data, and am running the HP Deskjet 5740. I installed it with the Gnome Printer Manager at System>Administration>Printing. First, select the printer model (yours should be listed). Then select the driver/PPD file by clicking through the directories I listed above. You will see your PPD file there. Once you select this file, Linux puts an unzipped copy of it in /etc/cups/ppd. I hope this helps. If you need further help, either I or someone more knowledgeable should be able to give instructions to install the printer successfully. 
David

---

### Post by cychem1 on 2005-09-12
I am having simialr problems with an HP 970 Cse. I am using KDE destop with hoary 5.04 installed (not Kubuntu but "Regular" + KDE using X86_64 CD). I have tried all foomaatic printer drivers and did search the forum with no joy. My printer simply keeps ejecting paper until I kill most to the CUPS processes when I try a test print

Not a total newbie to Linux, but I still  have much yet to learn I  just switched to Ubuntu from SuSe ( my printer was auto detected and worked fine) and I've managed to ge all my other hardware to work.

I have also searched the Starter guide. BTW cheers on the guide an excellent work.

System specs

Asus K8N
Athlon 64 3200 +
Nvidia FX5700 ( driver installed )
3 WD 250's IDE
Sound Blaster Live

Any hint or help is much appreciated.

---

### Post by seiflotfy on 2005-09-13
well i will write down the packages i snstalled as soon as i get home!!!

---

### Post by seiflotfy on 2005-09-14
Problem report
=========

When I try to print (using openoffice print menu, or lpr), this happens:

The process cupsd has 2 child processes, lp0 and perl (script foomatic-rip), both of them sleeping. Nothing happens. Inbetween, other processes are started (e.g. pdf2ps when printing a pdf file using lpr).

I cannot print anything. Once I got a page with only half of the content because all letters were double as high as they should be, but I can't remember the constellation.

Printer Configuration
=============

I installed my printer as described. I also see the file DeskJet-690C.ppd in /etc/cups/ppd. Seems to be ok. Detailed printer dialog information: My driver is hpijs (which is recommended), printer connection local, printer port "parallel port #1(canon)" (whatever canon means, there is also the option of epson and just parallel).

/etc/cups/printers.conf shows:

<DefaultPrinter DeskJet-690C>
Info DeskJet-690C
DeviceURI canon:/dev/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

The printer cable is ok, it works from another operating system, and also it worked on SuSe (with cups as well).

I suspected access right problems on /dev/lp0, but as I see it, it should work. /dev/lp0 has group 'lp' with read/write access, and the user cupsys (which is used by cupsd) is member of group 'lp'.

Installed Packages
===========

I installed

cupsys
cupsys-bsd
cupsys-client
cupsys-driver-gimpprint
cupsys-driver-gimpprint-data
gnome-cups-manager
libcupsimage2
libcupsys2-gnutls10
libgnomecups-1.0-1
libgnomecupsui-1.0-1

all coming with the ubuntu distribution.

I applied all updates, my system should be up to date (ubuntu 5.04).

---

### Post by seiflotfy on 2005-09-15
help????

---

### Post by David Haas on 2005-09-15
seiflotfy--I don't know enough about Linux printing--which is exceedingly complex--to diagnose your problem, but can suggest some things to be corrected. First, according to the author Brian Ward of "How Linux Works," CUPS uses the lp client for sending data to the print server. It has only limited lpr capability. 

"Canon" must be referring to the printer model.  Since your printer is an HP, I would think that you should choose just /dev/lp0, which is the parallel port designation for Linux.

David

---

### Post by Liakoni on 2005-09-18
I have the same problem with HP 710 Deskjet. I tried with live CD x86 and it's works fine. With Live CD x86_64 doesn't. With my x86_64 instalation doesn't work either.
Does anyone has any idea?

---

### Post by Simon-au on 2005-09-19
I had problems with a Minolta 2300 dl printer that was helped by getting the latest 
driver from printer database at [http://www.linuxprinting.org](http://www.linuxprinting.org).

So for your printer down load the PPD file from
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_690C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_690C)

When you add the printer from gnome or kde printer admin tool just choose to 
load your own driver option.

May not help, but worth a try.


Simon

---

### Post by Liakoni on 2005-09-19
I did load the latest driver but i didn't see any difference.
The problem is with ubuntu amd64 version.
I hadn't try with other distribution so far, so i don't know if it is a ubuntu amd64 problem or amd64 general...

---

### Post by Liakoni on 2005-09-20
I tried Ubuntu 5.10 Preview LiveCD amd64 but I didn't have any luck.
Printer doesn't print...

---

### Post by seiflotfy on 2005-09-22
i hope it works with breezy

---

### Post by Liakoni on 2005-09-22
[QUOTE=seiflotfy]i hope it works with breezy[/QUOTE]

Unfortunately i tried Ubuntu Breezy amd64 Preview LiveCD but my printer didn't work 
(HP Deskjet 710c).

---

### Post by openmind on 2005-09-26
I'm having the same problem with my 712c in Breezy, is this a known bug? I have no idea how to report it other than coming here.

---

### Post by openmind on 2005-09-27
Ok, I got it working finally. This might be really basic stuff for most of you guys, but I'm gonna post what worked for me so it can hopefully help a noob like me find a solution.

> sudo gedit /etc/pnm2ppa.conf

Then change the version section to look like this:

> #version  
#version  720	
version 710, 712, 722 also acceptable
#version  820
#version 1000

save file and try printing.

Hope it helps somebody.

---

### Post by ThomasW on 2005-10-02
Thanks for your answer.

This can only work if ppa is used at all (search for PPA in the CUPS trouble shooting guide [http://http://www.linuxprinting.org/kpfeifle/LinuxKongress2002/Tutorial/VII.cups-help/VII.cups-help.html#L715 ]("http://http://www.linuxprinting.org/kpfeifle/LinuxKongress2002/Tutorial/VII.cups-help/VII.cups-help.html#L715")
to get more information).

My printer is a HP 690C, and I don't think ppa is used (no PPA output in the cups error_log file (/var/log/cups/error_log) when setting LogLevel to debug2 in /etc/cups/cupsd.conf) and after trying to print something.

Printing still does not work for me though it worked without problems in SuSe. I wouldn't like to reinstall SuSe because their desktop is much slower than the Gnome desktop on my old PC (550 MHz Pentium III).

Any other ideas?

---

### Post by blair on 2005-10-11
I am having problems printing with my HP855C. I received a tip:

[http://ubuntuforums.org/showthread.php?t=65833](http://ubuntuforums.org/showthread.php?t=65833)

that helped  bit but not much. I believe there is fundamentally a bug in the Mozilla engine causing my problem. Perhaps the same thing is affecting you.

---

### Post by seanj on 2005-10-12
I've tried numerous times to get my HP DeskJet 600c working with Ubuntu, to no avail. Hitting up the docs and Wiki, well... there is no material on printing. I've made at least 1 visit per 2 months to the IRC channel on FreeNode, asking for help, getting confused answers and a bit flamed to boot. I attempted to use the CUPS web interface, which I'm more accustomed to and find more effective than the GNOME printing manager, just to find that the CUPS web interface is deliberately disabled to prevent configuration using it. What gives with that? Anyway, after over half a year of no help and no luck working with Hoary's broken printing system, I dropped it and went back to slackware. Why don't Ubuntu devs attempt to leave printing a little more purist instead of fixing what isn't broken? Thanks.

---

### Post by 504harry on 2005-10-12
Just to add to this discussion I loaded Ubuntu504 onto a 120G blank HDD - it needed the printer installed (under system. something)...and it _prints fine _from OpenOffice (text) - also with some odd banding, maps from Multimap.com = but curiously **nothing **from Gimp = indeed on looking to install the Lexmark z51 under Gimp it doesn't list it - the're other Lexmarks there, but not mine. Also there is a reference to PostScript. The system installation **does** list z51 - so I had assumed once installed (eg for OpenOffice) it would be there for all applications - but it seems Gimp is a "special case" - is this true? 
Consequently I'm still using Paint-Shop Pro and Windows to play with photos, even though I think Gimp has some nice touches.
/

**Camera**:  (( I download my Digital camera images using the USB (it works - great) It is recognised as a removable storage device and I need no camera-specific driver (just as well as I don't recall there being one on the CD that came with the camera just 2 months ago).....it loads the images into "C/.../My Photos" file )) ...and I can access them from Gimp - but on trying to download the camera to my Windows 98SE-computer those that have been downloaded using Linux - are NOT there.  (they can be viewed on the camera LCD, so they are not "missing") - I found a workaround by importing them into PaintShopPro - seems a long-winded scheme - so why does Linux do something to the camera memory? It worries me that some code is being sent to the memory card.
Perhaps I'll try the SD card at a photo store but until then, can anyone suggest a fix  for these two problems:

1) not being able to use Lexmark z51 with Gimp, at all
2) long-winded workaround for previously Linux-selected pictures.

REGARDS All.

PS I notice (here) there is an option to download "ieSpell" ( a spell checker for Internet Explorer - Is it any good for UK-English (eg Colour) - does it have strings?.
[Sorry to ask about one of the "Other Program Issues", but clearly many on this site must be using IE (otherwise the link wouldn't be there) - and until I'm at peace with Ubuntu I leave it for Weekend-work only.]

---

### Post by grj on 2005-10-12
When I looked at my /etc/pnm2ppa.conf file there was a line:

version

I changed it to 

version 722

and my HP 722C started printing.

I did this in response to an earlier posting. I am also going to modify my bug report as this information may help the developers.

---

### Post by buildid on 2005-10-26
this also works for me with an hp deskjet 720c

---

### Post by ThomasW on 2005-12-17
Solution!

I hoped printing would work on breezy, but to no avail. Finally I found it out, probably my hardware is a bit old.

It works with the following settings:[LIST]
[*]BIOS Setting: Configure parallel interface as **Printer** or **EPP**. **Bidirectional** or **ECP** (the other possible values in my BIOS setup) don't work.
[*]CUPS Setting: Set connection parameter to **Parallel** instead of **Canon**. For this to work (setting this with the GUI interface does not work), I stopped CUPS with ```
sudo /etc/init.d/cupsys stop
```, then edited /etc/cups/printers.conf with ```
sudo gedit /etc/cups/printers.conf
``` and replaced **canon** by **parallel**. Finally, I restarted CUPS with ```
sudo /etc/init.d/cupsys start
```[/LIST]

---

### Post by jso on 2005-12-18
I am running Ubuntu for amd64.  I have a Deskjet 692c, which is essentially the same as the 690c.  It printed with cups in suse, but now I'm having problems.  Nothing prints correctly.
[LIST]
[*]When I click "print test page", under properties, the printer seems to get stuck in a loop where it feeds the paper and prints one line of nonsense.
[*]When I try to print from Firefox or OpenOffice, the printer doesn't even seem to register the data, but the printer info in Ubuntu suggests no error, saying only that "parallel port is busy, retrying in 30 seconds".
[/LIST]

What do I do?

/etc/cups/printers.conf:
```
<DefaultPrinter DeskJet-692C>
Info DeskJet-692C
DeviceURI parallel:/dev/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>
```

Would any other info be helpful?

Thanks for your assistance.

---

### Post by ThomasW on 2005-12-22
jso, did you experiment with your BIOS settings as suggested in my previous post?

---

### Post by jso on 2005-12-23
[QUOTE=ThomasW]jso, did you experiment with your BIOS settings as suggested in my previous post?[/QUOTE]
No, I had not; I can't recall why.  Now that I have, my printer works like a charm (albeit a slow one -- but that's the printer's fault, not the computer's).  Thank you very much for your simple solution.

---

### Post by www.rzr.online.fr on 2006-05-06
[QUOTE=jso]No, I had not; I can't recall why.[/QUOTE]

At least Did you recall if you needed to hack the config files or not ?

---

### Post by patrick295767 on 2006-06-04
Hi, 
I change the canon to parallel in /etc/cups/printers.conf :
```
# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Sun 04 Jun 2006 04:25:02 PM CEST
<DefaultPrinter DeskJet-710C>
Info DeskJet-710C
DeviceURI parallel:/dev/lp0
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

```
  
And it's still not printing.
 
I tried to give also the  :
```
chmod 777 /dev/lp0
```
  
I also change the /etc/pnm2ppa

To give permissions to users.
  
Dotn knwo what to do ... 
:-(
  
When I print from gedit, the job is like getting printed, 
says READY after sending ... 
but nthg happens to the printer : no movemnents :-(
  
my /var/log/cups/error_log:
> I [04/Jun/2006:16:34:55 +0200] Started filter /usr/lib/cups/filter/pstops (PID 10505) for job 8.
I [04/Jun/2006:16:34:55 +0200] Started filter /usr/lib/cups/filter/foomatic-rip (PID 10506) for job 8.
I [04/Jun/2006:16:34:55 +0200] Started backend /usr/lib/cups/backend/parallel (PID 10507) for job 8.
E [04/Jun/2006:16:34:55 +0200] PID 10506 stopped with status 22!
I [04/Jun/2006:16:34:55 +0200] Hint: Try setting the LogLevel to "debug" to find out more.
I [04/Jun/2006:16:35:17 +0200] Adding start banner page "none" to job 9.
I [04/Jun/2006:16:35:17 +0200] Adding end banner page "none" to job 9.
I [04/Jun/2006:16:35:17 +0200] Job 9 queued on 'DeskJet-710C' by 'celina'.
I [04/Jun/2006:16:35:17 +0200] Started filter /usr/lib/cups/filter/pstops (PID 10532) for job 9.
I [04/Jun/2006:16:35:17 +0200] Started filter /usr/lib/cups/filter/foomatic-rip (PID 10533) for job 9.
I [04/Jun/2006:16:35:17 +0200] Started backend /usr/lib/cups/backend/parallel (PID 10534) for job 9.
E [04/Jun/2006:16:35:17 +0200] PID 10533 stopped with status 22!
I [04/Jun/2006:16:35:17 +0200] Hint: Try setting the LogLevel to "debug" to find out more.

  
Linux is getting like windows ??
> kernel-2.4 or kernel-2.6 
I had a vary nice experience with my printer when I installed Sarge using kernel-2.4. Everything worked fine. After, I installed kernel-2.6 package, I rebooted and the printer worked fine.
I made an experimental installation. I made a clear installation using kernel-2.6 ( linux26 at the prompt of debian installer ). I could not make my printer to work. Everything configured fine but the prinnter was idle. Even when I installed the package kernel-2.4 and reboot the system with it.
It's an old printer ( HP 710C ).
This is my experience.
from : [http://www.linuxquestions.org/questions/showthread.php?t=342924](http://www.linuxquestions.org/questions/showthread.php?t=342924)
  
HP tutorial : [http://www.hanklambert.com/Tutorial%20Pages/printer.html](http://www.hanklambert.com/Tutorial%20Pages/printer.html)
where its recommanded to install : 
> #apt-get install cupsys cupsys-bsd
#apt-get install python-dev
#apt-get install libsnmp5-dev
#apt-get install libcupsys2-dev
#apt-get install python-qt3
#apt-get install lsb
#apt-get install hp-ppd
#apt-get install hpijs
#apt-get install hplip
#apt-get install hplip-base
#apt-get install hplip-data

---

### Post by culmore on 2006-07-14
I have had similiar problems with a deskjet 520. I have tried varios BIOS setting for my parallel port EPP ECP Normel bi-directional  with no success. I tried downloading the packages from

HP Linux Imaging and Printing (HPLIP) i.e.
[http://hplip.sourceforge.net/install/step4/setup/index.html](http://hplip.sourceforge.net/install/step4/setup/index.html)

made no difference. 


Here is the contents /etc/cups/printers.conf
# Printer configuration file for CUPS v1.2.1
# Written by cupsd on 2006-07-14 21:53
<Printer DeskJet-520>
Info
Location
DeviceURI parallel:/dev/lp0
State Idle
StateTime 1152910394
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy stop-printer
</Printer>

Note my printer is NOT automatically recognised when I try and install it using System->Admin->Printing. So I manually select the driver HP driver for the deskjet 520, (I have also tried some generic drivers). I also manually select lp1, as ubuntu does not detect any printer.

Here is the contents of

/etc/pnm2ppa.conf 

# Sample configuration file
#
# This file will be automatically read upon startup if it is placed in
# /etc/pnm2ppa.conf
#
# uncomment entries by removing "#" to activate them.
#
#-----------set the printer model---------------------------
# The printer model will normally  be set by a -v <model> command
# line argument.   Otherwise, if not set in the configuration file
# it defaults to the 710/720 series.   Remove/comment out the line
# "version 0" below to get the default choice.
#
# If there is more than one "version" entry activated, the last one
# will be used.   The printer version can also be set with the command line
# option e.g., "-v 720".

version  710
#version  720   # 710, 712, 722 also acceptable
#version  820
#version 1000


Can I set the version here to something other than the values shown??? I tried 520 but no luck.

Is my printer now to old to be supported? Surely not.

Many thanks for any help you can be.

---

### Post by culmore on 2006-07-14
ups wrong forum. I am on 6.06 ekkk I'll post there.

---


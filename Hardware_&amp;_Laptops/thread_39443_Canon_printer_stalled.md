---
title: "Canon printer stalled"
date: 2005-06-05
forum: Hardware &amp; Laptops
---

### Post by C.B. on 2005-06-05
There are (at least) 3 of us with the same problem.

sweetnjguy29 posted on May 30:
	
"Unhappy Canon BJC-4300 - parallel port busy - I have been trying to print out documents from Firefox and Open Office with a Canon BJC-4300 ink jet printer. I usually get one line printed and then it stalls. Then if I check the status, it says "parallel port busy". I did some web research, with no real luck, except for setting icq to 7 or something like that, which ubuntu does by default (?). Now what?"

And dominik posted the same day: "i have the same problem here, with my lexmark optra r+..."

I have the same problem too. System/Admin/Printers shows "Status: Ready" or "Printing" but nothing happens. If I go into Properties it shows "Ready: Parallel port busy; will retry in 30 seconds..." but nothing happens.

Removing and reinstalling the printer thru System/Admin doesn't help.

---

### Post by David Haas on 2005-06-08
After selecting the Canon BJC-4300 in the printer manger GUI, what PPD file did you select? The one I see listed is Canon-BJC-4300-bjc600.ppd.gz. It's located at /usr/share/cups/model/foomatic-ppds/Canon. Once selected, an unzipped copy of the file should be listed at /etc/cups/ppd. Do you now have a copy here?
David

---

### Post by C.B. on 2005-06-08
David,

Thanks for your reply.

I find the expanded file, BJC-4550.ppd, located in etc/cups/ppd as you suggested.

If I click on it I get alot of info like:

*PCFileName:	"BJC600.PPD"
*Manufacturer:	"Canon"
*Product:	"(BJC-4300)"
*cupsVersion:	1.0
*cupsManualCopies: True
*cupsModelNumber:  2
*cupsFilter:	"application/vnd.cups-postscript 0 foomatic-rip"
*%pprRIP:        foomatic-rip other
*ModelName:     "Canon BJC-4300"

---

### Post by dominik on 2005-06-09
thanks for reposting that C.B. 
The problem is realy annoying. But what i noticed, some time ago my printer worked. And the only different was, that WindowsXP was installed on another partition. 

Perhaps thats the reason. Also it seems like the problem only exists under Ubuntu (because you cant find the problem in google). 

Hope we'll find a solution :/

---

### Post by David Haas on 2005-06-09
C.B.--Well, you seem to have installed the correct PPD file, and the correct printer model is listed, but I don't know why BJC-4550.ppd is listed in /etc/cups/ppd instead of Canon BJC-4300. Could there be a bug here, I wonder? since the PPD file for the Canon-BJC-4200 looks to be the same as for the 4300, Why not select this file instead of the one for the 4300? I'd begin again with "New Printer". Another way to get some information on your current set up is to do the terminal command "lpinfo -v". This will list all the URI options for USB and parallel ports, but should list your printer in the row "direct parallel". At least this will tell you that Ubuntu connects to your printer via the correct port. Well, I hope these suggestions move you closer to solving the prblem. I hope that other forum members jump in with suggestions.
David

---

### Post by C.B. on 2005-06-12
David,

My internet service has been mostly off for past 2 days. I only just got back online now.

Tried BJC-4200 as suggested. Same problem.

I enetered the "pinfo" at the command prompt as follows:
"cb@ubuntu:~$ |pinfo -v"
The line returned:
network socket
network http
network ipp
network lpd
direct canon:/dev/lp0
direct epson:/dev/lp0
direct parallel:/dev/lp0
direct usb:/dev/usb/lp0
direct usb:/dev/usb/lp1
direct usb:/dev/usb/lp2
...etc

I also noticed in printer preferences that I cannot select "Use a detected printer" because "No printer is detected." Instead I must select "Use another printer by specifying a port." So the currently selected printer, at the top of the list, is "Parallel Port #1 "(CANON)." 

Thank you for your assistance.

---

### Post by David Haas on 2005-06-12
C.B. -- I see that no printer is listed in your parallel port when you do the lpinfo -v command. So, your printer hasn't been detected, it seems. I'm not clear about what happens when you start with "New Printer. Don't you get a list of printers (and of course Canon printers) to choose from? Regarding the choice of PPD file, I found that besides one being listed in foomatic, as I wrote before, one is also listed in gimp-print. It's at /usr/share/cups/model/gimp-print/4.2 and it's bjc-4300.ppd.gz. So, after selecting whatever Canon printer you can, try clicking through the file system to select the PPD file in gimp-print. By the way, sometimes turning the printer off and then on when Ubuntu is running may help detection, I think. 
David Haas

---

### Post by C.B. on 2005-06-13
R what happens when I choose New Printer:
Yes, I get a choice of manufacturers and a list of printers to choose from.
I have tried powering printer off and on. Still no printer auto deteted.
Would it help if the printer is on at boot-up? Will try this next time just in case.

Re selecting ppd thru alternate route, I get one of the follwoing error messages:
     "Line longer than the maximum allowed (255 characters) at     
     1:'/usr/share/cups/model/gimp-print/4.2/bjc-4300.ppd.gz' "
or
     "Missing asterisk in column 1 at 
     1:'/usr/share/cups/model/foomatic-ppds/Canon/Canon-BJC-4300-bjc600.ppd.gz' "

However, if I deliberately try to install the ppd thru /etc/cups/ppd, then it tells me it has already been installed, which seems to be confirmed if I look there for the expanded ppd file using the file browser.

Further possible clues to problem:

  BJC-4550 PROPERTIES
Name:             BJC-4550
Description:    BJC-4550
Location:                                                            ](*,) 
Resolution:     360 DPI
Status:           Ready

Location, above, is suspisciously blank (except for the bonking head).

Also, System/Administration/Printers indicates BJC-4550 in Ready state even when the printer itself is off.


Pretty much ready to give up . . . at least for now. Not into trying to recompile printer drivers. Also sound doesn't work (old ISA card) and that looks like a job and a half, scanner is garbled, etc. So for time being I'll be running a dual system, mostly using windows which I have working okay these days. Bit disappointed in Ubuntu. It's been a short but rather steep learning curve. Now I know what's meant by "limited hardware support."

P.S. Wanda the Fish says: "Just to have it is enough." Words to live by.

---

### Post by David Haas on 2005-06-14
C.B. -- Perhaps the problem is with the Gnome printer manager; a recent posting stated that printer set up was unsuccessful with Gnome, but successful with the KDE printer manager. Another option would be to configure the printer with the command line. I've not done this, but the command (from the book "How Linux works" by Brian Ward) is as follows: lpadmin -p printer name -v device name -m model. The printer name would be, I think, just "Canon" (without the quotes). The device name would be "parallel:/dev/lp0". The model would be the PPD file name. The one in gimp-print is "bjc-4300.ppd.gz". 

I would have the printer on before you turn on the computer, but it shouldn't make a difference, I believe. 

David

---

### Post by Typhoon on 2005-06-17
I had this problem with a Canon BJC-265SP. It would choke, the the Printer Property indicated that the parallel port was busy.

I found that the problem was fixed by adding myself to group lp, the reboot.

In a terminal:

sudo addusr <your user name> lp

The system will reply that you have been added to group lp, but it does not take effect until you log in again - I rebooted just to be on the safe side.

It seems to me that it is a bug in a desktop system to not add the principal user to the group necessary for printing through a parallel printer.

Typhoon

---

### Post by C.B. on 2005-06-17
David & 'Ty',

Have temp. "solved" problem by downgrading to an older monochrome printer, BJ-200, which was immediately recognized and works fine. Chances are I'll want colour in near future so will try either/both suggestions.

Thanks muchly for help.

Charles.

---

### Post by pierre_s_rosen on 2005-11-30
In case any of you need to use the BJC-4300 printer still, it is fully operational and auto-detected in Ubuntu 5.10 (Breezy).  How excited am I?  W00t! :cool: :razz: :D :o :eek:

---

### Post by www.rzr.online.fr on 2006-05-06
FYI I had the same with Canon BJC 3000
it  does not works on [Ubuntu] , It wont print more that 5 lines and stuck on "Parallel port busy; will retry in 30 seconds..."


Will put some additionnal info at [http://rzr.online.fr/q/Print](http://rzr.online.fr/q/Print)

---


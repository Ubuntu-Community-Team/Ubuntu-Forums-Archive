---
title: "Brother DCP-7060D laser printer/copier"
date: 2014-11-12
forum: Hardware
---

### Post by harelb on 2014-11-12
Hi,
I am wanting to connect up a Brother DCP-7060D laser printer/copier to my desktop. 

In case it's relevant, it's an old desktop from around 2005 or 2006 (actually came with Xandros linux pre-installed which was an option consumers were given way back then from walmartcom, not today...I put ubuntu on top of it) Where things are:

*1* I've completed all the steps in the Set Up guide for this, my first laserprinter, except for the software set up part, where the instructions diverge into Windows and Apple (and entirely opposite, "make sure the USB interface cable is NOT connected to the machine.." for Windows versus "Connect the USB cable..." for the Mac) which led me to look for online instructions

*2* I cannot remember how I got the current printer (HP JetPrinter) to work, I just know, first, that it was simple, *not* something long or complicated.(and also, maybe I got the HP JetPrinter to work just by using the CD? can't recall that far back..either that or something else quick)

*3* Question: would anything bad happen if I tried to use the CD? Or is "nothing bad happens, it just doesn't work" the worst case scenario? If "nothing good or bad happens" is worst case, I should maybe try that (but which? Apple directions? Windows directions)? Otherwise, I guess I'll plow forward and hope not to mess up shell level driver installs (hides under bed.. (-;

*4* Assuming the answer to previous is "no, don't try to use the CD that came with the laserprinter!" I did some research, found a thread on ubuntuforums whose details of back and forth I was not able to follow but it did lead me to a Brother web page from which I downloaded a file "linux-brprinter-installer-2.0.0-1"
which is 92056 in size and which, using gedit, and skipping the commented top, starts with:

[INDENT]ENABLE_FAX_INSTALL=No           # change to Yes if FAX is required 
 
DEBUG_MSG=0
MSG=1

COLOR='\033[1;31m'
COLOR2='\033[1;35m'
COLOR3='\033[1;32m'
COLOR4='\033[1;34m'
MONO='\033[1;0m'[/INDENT]

Do I just run that? After a disaster or two in the past I now want to make extra sure all is well before I do anything on linux (-: I have 	Ubuntu 12.04.5 LTS (and I'm trying to remember what this machine has, what it's called, since I used a laptop for a year before it died forcing me to return to this one..I think I "removed" a "unity" and put it back into "gnome" style Ubuntu? something like that..)

..and am using an old machine (see top, before item *1*, above) as noted which may or may not be relevant but mentioning just in case, so if there's something I should check that might not be there that should be there (files, etc) that "everyone has" but not to assume I have it...or anything else before I run script above, please let me know so I don't blow things up by mistake (o:

Thanks,

Harel

---

### Post by weatherman2 on 2014-11-12
Have you simply tried plugging the printer into the computer and trying to print?  Ubuntu has built-in driver support for many old printers.

Otherwise, go to the printer setup in Ubuntu and (with USB cable plugged in, printer turned on) try to add the printer, if it doesn't get added automatically.

Don't try to use any CD with a Windows driver - it will be useless in Linux.  If you can't get the printer to work automatically, try looking for a Linux driver on Brother's website.

---

### Post by harelb on 2014-11-14
Thanks for response weatherman2, sorry took 2 days to get back here (other "life" stuff kept me away)...I assumed it would not work by just plugging it in, given that linux usually takes "more work" and manual said to take steps even for a windows...But I'll try anything...unfortunately it did not work when I tried. Even though I unpluggede the OfficeJet and plugged in, instead, the Laserprinter, the message from ubuntu in a dialog box was something like "printing...officejet-4300-series"..." followed by "printing error" and naming that same, no longer plugged in, jet printer, that it can't find of course...

So I guess I need to Add Printer...I tried: *System Tools --> System Settings and then under Hardware section, "Printers" *

There, it seemed like the only thing to do  that is relevant is to click on a plus symbol **"+" button**

Then a new dialog box on top of the old one has a "Local" and "Network" section, and both say:

> [B]"FirewallD is not running. Network printer detection needs services
mdns, ipp, ipp-client and samba-client enabled on firewall."[/B]

though even while displaying this message it still says "**getting devices**" while some cursor/icon is animating...before it gives up saying, "**No local printers found**". (The "Network" one --which should ignore anyway since I just have my one home desktop and one printer and do not have any network set up, a far as I know-- also had the same "FirewallD...." message and then instead of "No local printers found" instead it has a "search by address" box to check if I want and a text-box for "Address:..." I assume ignore these if I don't have a Network)

So....knowing minimal about ubnut, what do I do? Some "sudo apt-get...." followed by the list of all the above? Something else? The exact text that I could copy and paste from here would be wonderful..

---

### Post by plucky on 2014-11-14
Brother have a tool on their website which should help to install the drivers for your printer.

[Driver Install Tool](http://support.brother.com/g/b/downloadhowto.aspx?c=gb&lang=en&prod=dcp7060d_all&os=128&dlid=dlf006893_000&flang=4&type3=625)

Follow the instructions but make sure you specify your printer in the "bash" command line.

Good Luck

---

### Post by harelb on 2014-11-16
[B][EDIT ADDED LATER: You can ignore the rest of my post...I just ran the shell script and now the test page printed out fine! I typed the whole thing thinking that "add printer" works, must mean that "printer driver is there"...not the same thing after all! Thanks for everyone's help :-)]

[Anther update: the test page worked, but printing from OpenOffice did not..but I just figured that out, sort of: the print options now list two lines with a "DCP...one from the earlier (before I added ran the script) and one added just now by running the shell script...one of them can be used to print, the other is bogus..I just made the working one the default..deleted the other...printig from OpenOffice and Notepage worked, I think I'm out of the woods..thanks again![/B] ]

[Update 3: now what I'd really love to know is how to make _"toner saver" be ON as the default_ so I don't have to select that every single time I print under "options"...anyone know? When I go to system tools-->system settings-->printers that doesn't seem to let me choose "options" for the selected printer..I thought I saw that there yesterday before I installed the printer driver..
but now when I'm in System Tools-->System Settings-->Printers, and then select the DCP and finally click "options" button there, it just takes me to blank listing of "Allowed Users"?]

(Please everyone I_GNORE the nonsense below_, unless it helps a future lost/sloppy soul not to repeat same confusion/mistakes!)


Well there's good news and bad..

The "good news" is I did a sloppy job of connecting the USB cable when changing from the OfficeJet to the LaserPrinter (facepalm)  that was the reason it couldn't find a printer! After connecting properly I did not need to do anything but try clicking on the + symbol button again and it found and was able to successfully "add new printer" for the DCP-7060D...sorry about that silly error..

(It still says *"FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall."* as a message in the Printers dialog, but I assume I can ignore that since I'm using local not network printer, given that now I've gotten the DCP added at last..)

**The Bad News?** Unfortunately it still doesn't print! I've waited to see if I can catch another silly error before posting here again but so far no luck :-(

Whether it's through "Print Test Page" from the "Printers" dialog you get from "System Settings", or whether from OpenOffice, it just lets me select/keep the DCP chosen, and then says it is sending to the printer..and then it is happy, but nothing comes out!

Clues:

A.* I am able to use the DCP as a Copier _without_ problems*...so the drum etc of this laserprinter are working clearly.

B. Instructions for "Printing a document (page 25) " say: "1. Instal the Brother printer driver on the Installation CD-ROM 2) From your application choose the Print command 3) Choose the name of your machine in the Print dialog and click properties 4) Choose the settings [paper size etc] 5) click ok"

so if I call Brother they will point out that at the advice of Unbutuforums I skipped item 1..? :-(

Clue C: The Troubleshooting Guide for "no printout" 9page 59)  says:
> 
* "Check that the machine is plugged in and the power switch is turned on" (checked, it's fine, according to both my eyes/hand, and the simple fact that I can successfully use it as a Copier!)

*"check that the toner cartridge and drum unit are installed..." (again, used Copier without any problems..)

* "Check the interface cable connection on both the machine and your computer" (well that's the part that I initially did not have right, but after making sure both ends are plugged in fully, that's when the "Add New Printer" finally worked...so this part must be ok it seems..)

* "Check that the correct printer drive has been installed and chosen" - well that's the fact that OpenOffice lets me choose "DCP" now before I print...right? so that must be done..

*"check to see if the LCD is showing an error message" - no error message, just in Deep Sleep mode, but "Troubleshooting guide" does not say that's a problem, I think that's just where it's at when it hasn't been used for a while..

* Last item under Troubleshooting Guide for "no printout" is the longest, and says: "check that the machine is online"
and has four different possible sets of actions (all starting with Start Menu) depending on whether one has Windows 7, Vista, XP, or 2000...none of which apply here (no instructions for Apple/Mac, let alone for linux..)

That's the entirety fo the Trouble-shooting section for no printout...Now maybe I should call and bug Brother toll free or something, not you kind hearted folks at ubuntu forums, but I have a deep feeling in my gut they will 

1. possibly say "what?? linux? we don't give help to linux, sorry!"

and even more likely, they'll say:

2. They'll say: "you skipped the very first step, 'use the CD-ROM to install...' so you have to do that before we can help you!" which as I noted in B, earlier in this thread I was told to forget trying to use the CD-ROM for a linux machine...plus,  it's to "install brother printer driver"

Wait,  unless one can still have the printer be detected, and listed as an option,  and NOT have the driver after all? 

**I assumed that seeing that printer as an option means the printer driver is there....are the two entirely separate? **

If so I need to go to brother.com after all? Before I do that can I check in Ubuntu whether or not I have the driver?
[B]
When I go to System Tools --> System Settings -->Printers does that display show drivers I have or not? If not, what is the ubuntu command or menu steps to ask ubuntu to list my drivers to check if I have the right driver?[/B]
Many thanks,
Harel

---

### Post by plucky on 2014-11-16
> now what I'd really love to know is how to make "toner saver" be ON as the default so I don't have to select that every single time I print under "options"...anyone know?

Have a look at the CUPS interface to see if that option is in there.

In your internet browser address bar type ```
localhost:631
``` which should open the CUPS interface.

Good Luck

---

### Post by harelb on 2014-11-17
Wow plucky, thanks, a whole world out there about "CUPS", here's what seems to have worked, in case this helps others:

1. I went to [http://localhost:631/](http://localhost:631/) in firefox

2. Initially I was overwhelmed: there are 5 linked under "for users", another 8 under "for admins" and another 8 under "for developers"

3. I clicked eventually on the first link under "CUPS for Administrators" that first link is: "Adding printers and classes" (I did not initially think to look under "adding" a pritner but...see below..)

4. This takes you to [http://localhost:631/admin](http://localhost:631/admin)

5. Click on the button, "Manage printers" (the third button after "Add pritner" and "Find new printer" buttons)

6. That took me to [http://localhost:631/printers/](http://localhost:631/printers/)  which I am guessing is a url others can copy and paste from my post here and just use directly to skip earlier steps so far...

and from there I clicked on the name of the laserprinter, taking me to [http://localhost:631/printers/DCP7060D](http://localhost:631/printers/DCP7060D)
(which is *not* something others can copy and paste since your printer may have a different name)

7. Here there is a "Maintenance" pull-down menu (things like "clean print heads" and "print test page" etc) and then a pulldown menu called "Administration"...from there I chose "Set default options"

8. I am now about to change "Toner save" from "Off" to "On" and then to click "Set Default Options"

I'll post again if it does not work but hopefully that will "remember" it and do it right...again hope the above summary helps others in a similar situation :-)

P.S. Strange! I noticed my "media type" had been with an "A4" default, so I'm changing that to "letter" at the same time as I'm changing "toner save" to be "on" by default to save me money and toner. Will let you know how it works out.

---

### Post by harelb on 2014-11-18
So far, steps -8 above seem to work (from Firefox, OpenOffice Writer, and Notepad at least) meaning toner save ON and only 600dpi insted of higher resolution, are the DEFAULTS to save resources ...defaults I'll chance only for special print jobs...so hope above is useful to others (I'm almost always less expert on things so happy to have a rare chance to 'give back' with a summary that others might find helpful)

 Thanks again for ubuntuforums and all who posted especially plucky!   (-:

---


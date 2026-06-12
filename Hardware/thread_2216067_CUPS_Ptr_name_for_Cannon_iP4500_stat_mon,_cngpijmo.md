---
title: "CUPS Ptr name? for Cannon iP4500 stat mon, cngpijmon"
date: 2014-04-09
forum: Hardware
---

### Post by marksmarks on 2014-04-09
I have a Canon iP4500 printer working correctly via USB on my Ubuntu 12.04 (.03?) LTS box.  I'd like to use the status monitor;  "cngpijmoniP4500".  

    However everytime I run it from the terminal it says "Unknown Printer".

    I know it requires the CUPS printer name;   "cngpijmoniP4500  <CUPS ptr name here>".

   Is that the CUPS Queue name I see using 127.0.0.1:631 and selecting printers? 

   I've tried using that queue name, "Canon-iP4500-series" and it still says unknown printer. 

   I tried the printer name in Ubuntus printer configure area "Canon-iP4500-series"  Still unknown printer. 

  I changed the printer name in Ubuntus printer config area to "iP4500", used that.  Still unknown printer.

   I tried the usb printer name (lsusb I think) "Canon-iP4500-Series Canon, Inc. Pixma ip4500 Printer" and still unknown printer.


  -->> So which of the various names Ubuntu has for the printer is the CUPS printer name?  Once I know that, I can move forward.

---

### Post by pdc on 2014-04-10
Canon supply a user guide for your printer [http://support-asia.canon-asia.com/contents/ASIA/EN/0300055101.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0300055101.html)

if you download it; open with archive manager; then click the extract button; ............. maybe extract to your Desktop; click the button that says *view files* ..........and then drill down a couple of directories; looking for [COLOR="#008000"]guide_index.htm[/COLOR] and if you right-click on that and open in Firefox, you see a Canon guide:

if your device is usb they would suggest the command might be > cngpijmonip4500 IP4500

---

### Post by marksmarks on 2014-04-11
I've tried all the variations of the printer name 'IP4500' in the command, 'cngpijmonip4500 IP4500',  I can think of.   Including using sudo.

And, always the Canon Status Monitor window opens and displays 'Unknown Printer'.


I will look more closely at the help file you referenced, the section titled, 'Register the printer to the spooler'.

I had assumed that since CUPS listed the printer with a Queue it was already 'registered'


I guess I could purge the canon drivers and start over.

( ppa.launchpad.net/michael-gruz/canon-stable/ubuntu precise )

Thanks

/mark

---

### Post by pdc on 2014-04-11
can you give us a screenshot of your CUPS page please Mark [http://localhost:631/printers/](http://localhost:631/printers/)

eg I enclose what I see here

---

### Post by marksmarks on 2014-04-12
I got ink & libinklevel5 to work. 

However, still have not gotten cngpijmoniP4500 to work.  

I'm thinking that since cngpijmoniP4500 is made to work with this Canon printer, it my tell me more than ink & libinklevel5  ?


  Usage: cngpijmon****** [cups entry name]

   ex) cngpijmonip3500 IP3500

Canon, Inc. Pixma iP4500 Printer

----------------------------

[ATTACH=CONFIG]252002[/ATTACH][ATTACH=CONFIG]252003[/ATTACH][ATTACH=CONFIG]252004[/ATTACH]

---

### Post by marksmarks on 2014-04-12
I started trying to check the ink levels before I confirmed that ink level monitoring is still enabled on the printer.

It should, stop printing when out of ink. [-o<

I don't want to burn out the printhead and do plan on refilling and using a chip reseter.  ([www.precisioncolors.com](www.precisioncolors.com))

---

### Post by pdc on 2014-04-13
from what I can see of your helpful CUPS screenshot (thanks for that) ............. you **only** have the gutenprint driver installed:

my understanding of [COLOR="#0000FF"]cngpijmon[/COLOR] was that it was part of the Canon ip4500 driver 

so ..........to me ........... you need the two Canon packages: common and ip4500 specific

common from here .............[http://support-asia.canon-asia.com/contents/ASIA/EN/0100083401.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100083401.html) and it comes down as [COLOR="#008000"]cnijfilter-common_2.80-1_i386.deb[/COLOR] (so it is just a 386 package)

and the specific from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100083601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100083601.html) and it is [COLOR="#008000"]cnijfilter-ip4500series_2.80-1_i386.deb[/COLOR] 

and the list of files Canon details in the above includes > [COLOR="#008000"]cngpijmon*.mo[/COLOR]  

(when you click to download, you may well be offered an option to "open with gdebi installer" ..........which would install for you)

..............so my take is ..........do you just have a gutenprint driver installed? You could install the Canon drivers as above: and choose which driver to print with; as suits you; I don't see that gutenprint and Canon ip4500 would clash .............

---

### Post by marksmarks on 2014-04-13
When I first installed the printer I used the Michael Gruz, Ubuntu-Canon, PPA and installed ver 3.9 of the cnijfilter* files.



So,.. the way to see the CUPS printer names is by viewing the CUPS printer queues, right?

 Then I'd think that name is what 'cngpijmonip4500' would be expecting.


Could there be a permission problem when accessing a USB device? 

 'cngpijmonip4500' runs, yet it can't seem to see/recognize the USB printer?

I found out that the command, 'ink' alone would not work.  I had to use 'sudo ink'


Hummm,... or could the Gutenprint addition to the CUPS driver be the issue....

I may also try asking Michael Gruz about these issues in an email...


[ATTACH=CONFIG]252031[/ATTACH]

---

### Post by marksmarks on 2014-04-13
In my CUPS screen shots, there was only one queue listed for the ip4500.  I noticed that in your CUPS screen there is more than one queue for a given printer.

I just wanted to mention that because in my screen shot the terminal window covered the other printers Queue names.

---

### Post by pdc on 2014-04-13
thanks;

so what does 

> [COLOR="#FF0000"]dpkg -l | grep cnijfilter[/COLOR] give if you copy and paste into a terminal: there is a pipe command in the middle

---

### Post by marksmarks on 2014-04-13
$ dpkg -l | grep cnijfilter
ii  cnijfilter-common                           3.90-63~precise1                        IJ Printer Driver for Linux.
ii  cnijfilter-ip4500series                     3.90-63~precise1                        IJ Printer Driver for Linux.

---

### Post by marksmarks on 2014-04-13
Solved!   … I think. 

I decided to try installing a 2nd instance of the Canon ip4500. In order to test different drivers.

However, when it installed it read; … – > with status readback for Canon IJ < –

Than sounded positive. I noticed it was automatically given the name 'Canon-ip4500'

When I used that name, 'Canon-ip4500', the status monitor and the maintenance utility recognized the printer. (See screen shots).

That first instance of the ip4500, was apparently what Ubuntu 12.04 installed on its own BEFORE I installed theCanon InkJet drivers, cnijfilter-* (via the Michael Gruz PPA).  It was using the CUPS+GutenPrint driver.


I may have been able to change it by, in the printer properties screen, clicking on the 'make and model' - 'change' button.  Then, in the list of drivers, selecting 'iP4500 Ver x.xx' instead' of 'PIXMA iP4500'.


PS: In the printer settings I now have 600 - 2,400 DPI output resolution.


[ATTACH=CONFIG]252036[/ATTACH][ATTACH=CONFIG]252037[/ATTACH][ATTACH=CONFIG]252038[/ATTACH]

---

### Post by pdc on 2014-04-14
well done;

enjoy

(oh, by the way you can edit the title as SOLVED)

---

### Post by mörgæs on 2014-04-14
No, not the title. Please use 'thread tools'.

---


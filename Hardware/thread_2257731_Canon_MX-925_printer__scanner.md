---
title: "Canon MX-925 printer / scanner"
date: 2014-12-22
forum: Hardware
---

### Post by crazybear on 2014-12-22
I followed the two basic methods  given in the downloaded package for installing the Ubuntu drivers for this model series - for both the printer and scanner. One method is shown here [http://www.seleads.com/how-to-install-setup-canon-mx925-on-debian-7-linux/](http://www.seleads.com/how-to-install-setup-canon-mx925-on-debian-7-linux/) Tried one [it failed to print]; then tried the other [also failed to print]....tried both several times. Am confused because many things seem to indicate that it installed correctly and is partly recognized, but will not print nor scan - with one exception: it will print correctly a test page when the command is issued from the printer program in system settings. It shows correctly after running lsusb in terminal and the installations and registering of the printer all went as they are supposed to and without error messages. No program [pdf, word processor, others] however can print and none of the scanner programs will scan. Any ideas? The debugging page on printers [https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems) is HUGE and covers more things than I think I need to try. I have tried a few and the few seem to show no problems...but obviously there is one. I also tested the printer on Windoz and it works fine...but I don't use Windoz but once in a blue moon. Help please with suggestions of what to do and what to test. This is a somewhat new printer and I don't see any internet posts on this problem with this printer in Ubuntu 12.04 or 14.04. I use both of those. Thanks

One test: cngpijmonmx920 MX920USB delivers a strange error message:Xlib:  extension "RANDR" missing on display ":0.0". This makes no sense to me - as the displays [3] seem to be working fine and shouldn't have anything to do with the printer [?!]

---

### Post by pdc on 2014-12-22
if you can open a terminal; can you copy this command

```
dpkg -l | grep cnijfilter
``` and paste it into the terminal; hit the ENTER key and if you get any results; can you copy them; and paste them back here please; often easiest to use the mouse and the top line of the terminal to copy and paste;

............the command is looking to see if the Pixma drivers were installed 

______________________

[http://localhost:631/printers/](http://localhost:631/printers/)

can you click on the above link; it should open CUPS, printer admin; on your system; can you look in column 4: Make & Model; is anything listed for Canon MX920series Ver 3.6 or similar?

---

### Post by crazybear on 2014-12-22
It looks good to me.... [and there was also installed a scanner driver from another package]...as I said, it prints a proper test page from the control center, but prints nothing else and won't scan.
[COLOR=#0000cd]:~$ dpkg -l | grep cnijfilter[/COLOR]
ii  cnijfilter-common                                           3.90-1                                              IJ Printer Driver for Linux.
ii  cnijfilter-mx920series                                      3.90-1                                              IJ Printer Driver for Linux.

---

### Post by pdc on 2014-12-22
can you also answer part 2 please

---

### Post by crazybear on 2014-12-22
[TABLE="class: list"]
[TR]
[TD][Canon-MP540-series]("http://localhost:631/printers/Canon-MP540-series")[/TD]
[TD]Canon MP540 series[/TD]
[TD]GA-X58A-UD7[/TD]
[TD]     Canon PIXMA MP540 - CUPS+Gutenprint v5.2.8-pre1[/TD]
[TD]Idle[/TD]
[/TR]
[TR]
[TD][MX920-series]("http://localhost:631/printers/MX920-series")[/TD]
[TD]Canon MX920 series[/TD]
[TD]GA-X58A-UD7[/TD]
[TD]     Canon MX920 series Ver.3.90[/TD]
[TD]Idle[/TD]
[/TR]
[TR]
[TD][MX920-series-FAX]("http://localhost:631/printers/MX920-series-FAX")[/TD]
[TD]MX920-series-FAX[/TD]
[TD][/TD]
[TD]     Generic text-only printer[/TD]
[TD]Paused - "Unplugged or turned off"[/TD]
[/TR]
[TR]
[TD][MX920USB]("http://localhost:631/printers/MX920USB")[/TD]
[TD]MX920USB[/TD]
[TD][/TD]
[TD]     Canon MX920 series Ver.3.90[/TD]
[TD]Idle[/TD]
[/TR]
[/TABLE]

Note: the MP540 was my old printer [I assume that driver is still present], but it is currently not connected. The current printer is connected via USB.

---

### Post by pdc on 2014-12-22
thanks; so it would seem the printer drivers are installed; and an entry has been made in CUPS ........presumably from you running the Canon install script .......that creates the 2 MX920 entries; 

Canon say you can print from a terminal with the structure ```
lpr -P [printer_name] [filename]
```

so ```
lpr -P MX920USB [filename]
``` and you nominate a file to print: seems to me you need the full path so if you know a filename that you want to print, from the terminal the command ```
locate [filename]
``` will tell you where it is; you can copy that and paste it into the Canon command

---

### Post by crazybear on 2014-12-22
Not sure I understand. I know one can print using the command line, BUT I do NOT want to do that more than once to test. I want to be able [as before] to print from all the various programs I have and use that have a print function. I assume the CUPS was installed when the first printer was. I didn't do anything related to CUPS this time. I don't understand what [above] you are suggesting...as a test? [I hope not as a 'solution'! - it would be a complete hassle and would not give me the print options screen I need at every printing.

....anyway, it doesn't work from command line. I get a message on screen that it is being sent to the printer...but NOTHING happens [same from LibraOffice or any other program]. Again, only the test page from control center works. Nothing else does.

What next?!

---

### Post by pdc on 2014-12-22
I just wondered if it would work from the command line; ......direct communication ......................and any errors may well get spelt out in the command line ..............

______________________________


I wondered if your system was otherwise stable; any other issues going on; ..................recently installed..............tweaked in some way .........

the Canon shows up reliably on the command ```
lsusb
``` does it? Are you using a usb hub? Is it a USB3 point?

____________

one could easily delete the two MX920 entries and create a new entry: ```
system-config-printer
``` opens the printer GUI; delete existing entries; click on the "Add a new printer" and it should find your MX920 with drivers already installed; and see if that works;

---

### Post by crazybear on 2014-12-23
Yes, I think I mentioned at the beginning it shows up correctly on command lsusb. Your suggestion to open the printer GUI solved one of the problems {i think}....as what was listed_ as available_ was named slightly differently [MX920-series-2]. I just added it and it printed when made the default. I just need to test the other functions..... Thanks. Will report back if the other functions are working as well....hmmm....just opened my scanner program [simple scan] and it said no scanners available.....will try other programs for scanning as well as printing and report as I can already tell all is not yet right. I haven't deleted any of the printers shown...but some [not the one that just printed and is set as default at moment] has a location indicated - as the same location as the old printer; however, the newer other printers, including the one that just printed a page, have NO location listed, which is very strange. I'm confused at this point...close, but obviously not 'there' yet. Also, likely not [?] connected but on the terminal after giving the command [COLOR=#000000][FONT=Ubuntu Mono]system-config-printer[/FONT][/COLOR] I get the very strange reply: Xlib:  extension "RANDR" missing on display ":0". [but I'm not having any problems with the displays of which I have 3]!?!?...... Strangest of all, now the only thing that did work before [printing a test page] does NOT work.

*The computer is very robust [built it myself] and am not using a usb hub and not using a usb3 port for the printer.*

---

### Post by pdc on 2014-12-23
sounds like it is coming together

_________

scanning: Canon provide [COLOR="#0000FF"]ScanGearMP[/COLOR] from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100518302.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100518302.html) and if you download and save, it comes down as [COLOR="#008000"]scangearmp-mx920series-2.10-1-deb.tar.gz
[/COLOR]
assuming downloads are saved to [COLOR="#0000CD"]Downloads[/COLOR], the commands to install would be:

```
cd Downloads
```

```
tar -zxvf scangearmp-mx920series-2.10-1-deb.tar.gz
```

```
cd scangearmp-mx920series-2.10-1-deb
```

```
./install.sh
```

____________________________

to run it, the command is ```
scangearmp
``` and if all is good, one sets up a launcher to ......... launch it ......... ask if you haven't set up a launcher

______________

Simple Scan runs on Sane [http://www.sane-project.org/](http://www.sane-project.org/) and your MX920 is listed as [COLOR="#A52A2A"]UNTESTED[/COLOR] !! [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) and they would like help !!

_________________

[http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html) this is the link page for the good folks that do this work: there should be contact details; they would be very grateful for your help I am sure

---

### Post by crazybear on 2014-12-23
I'm getting very weird results now. It will print, but also always prints a partial test page [the black and white part - not the color part] as the first page even though NOT asked to...then prints the page I asked it to. Also, I had left the terminal open when I selected a 'new' printer [many were listed and to my untrained eye several represented the same printer [only one now connected]...but the terminal wrote the following even though I got a print [and an unwanted partial test page]: No ID match for device usb://Canon/MX920%20series?serial=11156D&interface=1:MFG:Canon;MDL:MX920 series;CMD:BJL,BJRaster3,BSCCe,NCCe,IVEC,IVECPLI;DES:Canon MX920 series;

Also getting messages such as _Idle - Sending data to printer_ listed for the printer state of printers not listed as the default. Is that indicating a print job was once sent there and is now stalled? I don't know if it is safe to delete all the extra listed printers, as I don't know which one really is listed as connected properly - none seem to be working fully at this time. Telling it to print a 'self-test' or to print a 'test page' gives only a B&W, off-center, too light test page...not centered, not very dark and no color as before. Pfft.

Still no scanner. Ill try reinstalling that driver. I had done so before using the same manner as you describe.

---

### Post by pdc on 2014-12-23
I don't know Sooty ..............for those old enough to remember Harry Corbett ............

you seem to be fighting demons and monsters ............ 

________________

it all depends on how much time you have; 

[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

________________

in this, there is a section called > Sending a file to the printer unfiltered [https://wiki.ubuntu.com/DebuggingPrintingProblems#Sending_a_file_to_the_printer_unfiltered](https://wiki.ubuntu.com/DebuggingPrintingProblems#Sending_a_file_to_the_printer_unfiltered)

```
lp -d <printer> -oraw <file> 
```

so yours might be 

```
lp -d MX925USB -oraw <file> 
```

_____________

you could use CUPS [http://localhost:631/printers/](http://localhost:631/printers/) or ```
system-config-printer
```to delete all existing entries; and start them anew

---

### Post by crazybear on 2014-12-24
I will try a few things in the next 24 hours and report back.....things still not working properly on a new and good printer that is supposed to work well in Ubuntu.....

---

### Post by crazybear on 2014-12-25
see post below.

---

### Post by crazybear on 2014-12-25
Pffft. I deleted all the odd printers, re-installed the one offered. Strange that now my old printer is NOT offered...as I'd like the option to use it too - especially if this one has to be returned as not compatible. 
Every print requested gets, now, two improperly printed test pages [not requested] and the item to be printed is much lighter than it should be by the settings. Haven't tried color much, as don't want to waste ink if things are still problematic.
Re-installed scanner for this series [not the common] and ran scanner update...but all programs report there are no scanners [there should be two as I plugged in the old printer too]. 
However, from command line it scans - seemingly well. 
But prints and scans are not working properly  and not coordinated with software - nor with what I ask to be done.
Still getting terminal messages like: GA-X58A-UD7:~/Desktop/scangearmp-mx920series-2.10-1-deb$ scangearmpXlib:  extension "RANDR" missing on display ":0.0".
[when I'm not aware of any display problems]

---

### Post by crazybear on 2014-12-26
It iS ALL  much worse now....only prints parts of test prints; no longer will print what I want it to print...just gives error message and freezes up. I can print nothing now and can't even get the terminal to really respond properly on the [COLOR=#000000][FONT=Ubuntu Mono]system-config-printer command. Very frustrated!

[/FONT][/COLOR]"Unable to send data to printer."

---

### Post by crazybear on 2014-12-28
OK, now after reinstalling the drivers and doing several other things, it is getting better...almost to the point I can say it is 'working' properly. Do you know how I can get the same choices [many] when I hit 'print' in a program, as when I enter [COLOR=#000000][FONT=Ubuntu Mono]system-config-printer via the command line?....then I'll have all the functionality of the printer.[/FONT][/COLOR]

---

### Post by crazybear on 2014-12-30
No, I spoke too soon.....it often prints well, then all of a sudden it will do something strange like print the top half of a page twice on the printed page......I don't understand where the problem is. At the moment none of the  prints are correct; for the last few days they were OK - with no change of settings.

---


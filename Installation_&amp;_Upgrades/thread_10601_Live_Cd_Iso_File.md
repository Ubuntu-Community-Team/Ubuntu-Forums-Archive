---
title: "Live Cd Iso File"
date: 2005-01-09
forum: Installation &amp; Upgrades
---

### Post by Alik on 2005-01-09
OK I am very frustrated right now. It took me 16 hours to download a shitty ISO file and then I burned it on a Cd as it said. Now I reboot my Pc, I press enter and nothing happens. I am completly new to linux and never installed a OS myself. Could anyone please gove me some tips on how to deal with this ISO file and and how to make it work. 
 
    Thank You in advance!

---

### Post by nemin on 2005-01-09
[QUOTE=Alik]OK I am very frustrated right now. It took me 16 hours to download a shitty ISO file and then I burned it on a Cd as it said. Now I reboot my Pc, I press enter and nothing happens.[/QUOTE]
I think you have to tell a bit more about what does and doesn't work. Does the CD boot in fact? What do you see on your screen? What do you mean with "nothing"? Your computer just hangs?

---

### Post by Alik on 2005-01-09
no by nothing i mean that the computer just reboots normally in windows without taking into consideration the Cd or the fact that i press enter. It just reboots normally in Windows mode.

---

### Post by nemin on 2005-01-09
[QUOTE=Alik]no by nothing i mean that the computer just reboots normally in windows without taking into consideration the Cd or the fact that i press enter. It just reboots normally in Windows mode.[/QUOTE]
Check your BIOS setup if your computer boots from CD by default. Try another bootable CD, does that work? Then you know if the CD is the problem or not..

---

### Post by #Greg on 2005-01-09
Make sure your CD is bootable in the BIOS BEFORE the hard drive.
Did you definately burn the CD as an IMAGE and not just a data CD?

---

### Post by Alik on 2005-01-09
> Check your BIOS setup if your computer boots from CD by default. Try another bootable CD, does that work? Then you know if the CD is the problem or not..

Greg:
Make sure your CD is bootable in the BIOS BEFORE the hard drive.
Did you definately burn the CD as an IMAGE and not just a data CD?  


I burned my Cd as a Data Cd using the Ahead Nero Program. I don't really know what the BIOS is because I have never used it before but how could I access this from Windows and what should I change in it?

---

### Post by nemin on 2005-01-09
[QUOTE=Alik]I burned my Cd as a Data Cd using the Ahead Nero Program.[/QUOTE]
Then you can be sure it'll never work..  You have to look for a "Write image" option or so within Nero. Search for something like "nero iso burning"  on google for more information about that...
[QUOTE=Alik]
 I don't really know what the BIOS is because I have never used it before but how could I access this from Windows and what should I change in it?[/QUOTE]
You can't acces it within windows, you have to press a key, usually del or esc or so, directly after you start up your computer. You have to look for something like "First boot device" or so..  Read your motherborth manual for more info about that. 
But maybe isn't that nessecary at all and is your BIOS already setup correctly and will a correctly burned CD fix your problem...

---

### Post by Alik on 2005-01-09
OK i did burn it as an Image file. Also I was able to enter in the Bios by pressing the ESC key during startup. However I didn't change anything in it because of my narrow knowledge and didn't want to screw things up. But I am still not able to make the Cd load by pressing enter. It just boots in Windows. Any further help would be very appreciated.

---

### Post by #Greg on 2005-01-09
It's hard to give advice on your BIOS because all are slightly different. Look for a CMOS menu or boot menu, you should see 3 or 4 different entries such as your hard drive, floppy & cdrom. Select the first entry and press enter, choose your cdrom drive. Then on your second entry select floppy, then on your third select your hard drive.

Press F10 and then enter to save changes, or go back to the main menu and select/enter "Exit saving changes".

Reboot and put your cd in, it should boot up from the CD.

---

### Post by wallijonn on 2005-01-09
Alik,

Exactly what computer do you have or what motherboard do you have?

---

### Post by Alik on 2005-01-09
I have 500 MHZ, 191 Ram Intel Celeron Computer running under Windows 98. Its an old computer I bought 5 years ago.

---

### Post by Alik on 2005-01-09
When I am given the choice to what kind of a disk I want to burn for the ISO file I chosse (CD-Rom Boot). But then it askes for an image with either a .IMA or .Bin extension. Is this the correct path and if yes then what is the image file? And tnx for the BINOS part... I understand how it works now. However, the problem I believe is with the way I burn the ISO file onto the CD. Anyone that could give me some advice on what I should do?

---

### Post by nemin on 2005-01-10
[QUOTE=Alik]I understand how it works now. However, the problem I believe is with the way I burn the ISO file onto the CD. Anyone that could give me some advice on what I should do?[/QUOTE]
As far as I know, you don't have to care about .bin and .ima image, correct me if I'm wrong..
I think that by following the description on this page your CD will be perfect :)
[http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)

---

### Post by Alik on 2005-01-10
Thanks alots  Nemin for the website. It helped me alot. I am actually typing this from the Ubuntu operating system and not from Windows. Thanks to all of you who tried to help.

---


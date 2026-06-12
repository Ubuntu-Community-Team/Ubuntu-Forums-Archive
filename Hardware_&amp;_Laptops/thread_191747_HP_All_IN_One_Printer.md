---
title: "HP All IN One Printer"
date: 2006-06-07
forum: Hardware &amp; Laptops
---

### Post by mzracer360 on 2006-06-07
I need a how-to on installing a HP all-in-one.
I found:
[https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters](https://wiki.ubuntu.com/HpPscHpPhotosmartSeriesAllInOnePrinters)
but when i went to:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
I became confused, i think the repositories how to needs to be updated, since half the options arent where they say they are or not even there at all.

---

### Post by sggray on 2006-06-22
I have an HP K80 all-in-one.  I am completely new to anything other than Windows so bear with me and I will tell you what I finally had to do to get my printer to work.  Note that I have not tried scanning or faxing - only printing at this point.

1) Remove your existing version of hplip using the Synaptic Package Manager.

2) Acquire and install hplip-1.6.6 and its patch from [http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)
The installation instructions aren't easy, but I am literally on my second day as a Linux and Ubuntu user and I was able to do it, so follow them closely and you can do it.  If you don't have a c-compiler on your system you will have to acquire and install one as part of this process.

3) I used the Synaptic Package Manager to reinstall everything that appeared even remotely related to USB (I'm not sure this had any effect but I saw where someone suggested it so I tried it).  If you want to do this, search on USB in the title and description then sort the list on the install status flag in the first column - that way you only have to look at the ones that are installed (the green ones).

4) Go to [http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi) and get the hpijs driver and save it somewhere on your hard drive.  Remember where you put it because you will need it in the next step.

5) Go to System | Administration | Printing and click on the new printer icon.  If everything has worked so far, you will see your printer named in the printer port box at the bottom of the screen.  Select "use another printer by specifying a port" and make sure you printer is highlighted in the box below it, then click forward. Select your manufacturer and model, then click on the install driver button.  When the window opens locate the file you saved in step 4, highlight it and click open.  The driver should show up in the box next to the load driver box.  Click on forward.

6) Give the printer a name, etc. on the next screen and click Apply.  your printer should show up.

I know these instructions are high level and a little more remedial than you probably needed but hopefully they will help you.  Good luck - I was about two tries away from going straight back to Windows ](*,)  before I finally got it to work :D .

---


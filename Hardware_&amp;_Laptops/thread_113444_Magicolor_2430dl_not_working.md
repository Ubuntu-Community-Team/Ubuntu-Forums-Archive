---
title: "Magicolor 2430dl not working"
date: 2006-01-06
forum: Hardware &amp; Laptops
---

### Post by peterthebike on 2006-01-06
I have copied the linux driver from the install CD and then:
```
sudo alien magicolor2430DL-1.5.0-1.i386.rmp
sudo dpkg -i magicolor2430dl_1.5.0-2_i386.deb
```
Then System>Administration>Printing to install the new printer where it shows as ready.

Nothing produces output though, Test Page or output from Firefox and OpenOffice.

You can see the job in the Job Queue, but as soon as it appears it is gone??

Any suggestions please.

---

### Post by peterthebike on 2006-01-07
After seeing this thread [minoltaqms magicolor laser printer]("http://www.ubuntuforums.org/showthread.php?t=112192") I tried setting my printer to a generic post script printer, but it didn't make any difference.

I reset it to a KONICA MINOLTA magicolor 2430 DL but I am sure the driver was different this time, I was only offered Standard, which I do not remember from when I first set it up. Probably my memory is going (old age), but the end result is the printer is now working!!

---

### Post by theGerbil on 2006-01-07
Hi PetertheBikie

Just wanted to let you know I had exactly the same problem as you. I guess the new driver off the CD doesn't appear in the driver list until after a re-boot or something.

Hey-ho .. gr8 printer tho.

Good luck!!

---

### Post by Amon_Re on 2006-01-08
Actually, restarting cupsys should be sufficiant.

sudo /etc/init.d/cupsys stop
sudo /etc/init.d/cupsys start

---

### Post by peterthebike on 2006-01-08
[QUOTE=theGerbil]Just wanted to let you know I had exactly the same problem as you. I guess the new driver off the CD doesn't appear in the driver list until after a re-boot or something.[/QUOTE]
Thanks for that, sometime wonder if I am going mad and just did not see it properly first time!
> Hey-ho .. gr8 printer tho.Tad slow in going through the raster bit, but I am very pleased with the quality for a reasonably priced color laser.

---

### Post by peterthebike on 2006-01-08
[QUOTE=Amon_Re]Actually, restarting cupsys should be sufficiant.

sudo /etc/init.d/cupsys stop
sudo /etc/init.d/cupsys start[/QUOTE]
There was a valid driver it showed on initial install so nothing appeared to be wrong. It was only by luck that I found what the problem was, otherwise I would probably still be moaning about it next Christmas!!

---

### Post by mojavelinux on 2006-01-24
Sure enough, it appears that even though Breezy ships with drivers for the magicolor2430dl printer, those drivers don't seem to be enough to get the printer to actually do anything.  The solution, however, is ultra simple and has been explained in this thread.  However, to help out fresh eyes, I am going to summarize EXACTLY what I did to make it work.

1. Go to: [http://printer.konicaminolta.com/support/current_printers/mc2430dl_sup.htm#Drivers](http://printer.konicaminolta.com/support/current_printers/mc2430dl_sup.htm#Drivers)

2. Get:  Printer Driver for Linux Version: 1.5.0

3. Unpack it

4. sudo apt-get install alien fakeroot

5. fakeroot alien magicolor*rpm

6. sudo dpkg -i magicolor*deb

7. sudo /etc/init.d/cupsd restart

8. setup printer as normal, but use the driver from the all caps KONICA_MINOLTA category (and not the Minolta category).

9. Print a test page, be happy and go back to praising Ubuntu

---

### Post by peterthebike on 2006-01-24
[QUOTE=mojavelinux]Sure enough, it appears that even though Breezy ships with drivers for the magicolor2430dl printer, those drivers don't seem to be enough to get the printer to actually do anything.  The solution, however, is ultra simple and has been explained in this thread.  However, to help out fresh eyes, I am going to summarize EXACTLY what I did to make it work.

1. Go to: [http://printer.konicaminolta.com/support/current_printers/mc2430dl_sup.htm#Drivers](http://printer.konicaminolta.com/support/current_printers/mc2430dl_sup.htm#Drivers)

2. Get:  Printer Driver for Linux Version: 1.5.0

3. Unpack it

4. sudo apt-get install alien fakeroot

5. fakeroot alien magicolor*rpm

6. sudo dpkg -i magicolor*deb

7. sudo /etc/init.d/cupsd restart

8. setup printer as normal, but use the driver from the all caps KONICA_MINOLTA category (and not the Minolta category).

9. Print a test page, be happy and go back to praising Ubuntu[/QUOTE]mojavelinux

Thanks for your instructions, I had the chance to check them as I have just had to re-install Ubuntu. :) 

Only comment is I needed to change step 7 to```
sudo /etc/init.d/cupsys restart
```If anyone finds the wait before printing is a little too long, try changing the Resolution under the printer's properties from the default 
1200x600 DPI to 600x600 DPI. For general usage I found this perfectly acceptable quality.

---

### Post by goneskiing on 2006-03-31
Guys,
Thanks so much for the tips - especially mojavelinux.  I spent 3 hrs trying to get the printer to work using google searches - then I tried this forum and bingo, now my printer is working fine.  

ps: whoever mentioned that 600x600 is plenty good for most work - you're right, saves ink, saves time.

---

### Post by gobuntu on 2007-10-06
> **mojavelinux said:**
> Sure enough, it appears that even though Breezy ships with drivers for the magicolor2430dl printer, those drivers don't seem to be enough to get the printer to actually do anything.  The solution, however, is ultra simple and has been explained in this thread.  However, to help out fresh eyes, I am going to summarize EXACTLY what I did to make it work.

1. Go to: [http://printer.konicaminolta.com/support/current_printers/mc2430dl_sup.htm#Drivers](http://printer.konicaminolta.com/support/current_printers/mc2430dl_sup.htm#Drivers)

2. Get:  Printer Driver for Linux Version: 1.5.0

3. Unpack it

4. sudo apt-get install alien fakeroot

5. fakeroot alien magicolor*rpm

6. sudo dpkg -i magicolor*deb

7. sudo /etc/init.d/cupsd restart

8. setup printer as normal, but use the driver from the all caps KONICA_MINOLTA category (and not the Minolta category).

9. Print a test page, be happy and go back to praising Ubuntu

Dear friends,

Thanks for this good thread.

However, on my feisty Ubuntu*[I][I] the magicolor 2430 DL actually showed-up under the minolta brand*[/I][/I], not under the KONICA-MINOLTA as said above. 

At "minolta" brand, I chose the 2430 DL and the printer worked first time. Only the colors are somewhat off, and will start now to investigate the settings, for which there are some options that are not yet meaningful to me.

---

### Post by gobuntu on 2007-10-07
A MISTERY FOR ME, please help ...

Dear friends, 

Yesterday when I posted the above concedrning magicolor 2430 DL, I was able to print and even use the Printer/Properties/Advanced options "ICM Color Profile", and I left the printer option for ICM Color Profile: "File km2430_2 .icm", which gave me closer colors to my screen's. I also had chosen other files for that option and they did vary color print noticeably. I still have the prints.

Today, however, the printer would not print from anywhere, except a test page.

After not being able to fix the problem, was ready to re-install Feisty, and re-do my setups. However, I tried "use no ICM" and the printer worked.

So, I did not reinstall Ubuntu, although am mysified why this functioning was there yesterday, and not today.

I did remove the printer, and re-installed it, and am still where only "use no ICM" shows. I figure that when the several ICM files show in the option, it's because they are there.

Howver, Places/Search for file does not find them in the File System.

Can someone, please, clarify on WHERE these files are supposed to come from, and WHERE are they supposed to be, or assist with whatever might let me have again ICM capability?

Thanks for any help.

-gobuntu

---

### Post by gobuntu on 2007-10-08
Dear friends,

On Feisty Ubuntu 386 installation, would like to say:

1. [I]None of the rpm download, nor alien conversion is required as stated above.
[/I]
2. The 2430 printer works on a Feisty installation right-out of the box. 

3. It works with the ICM color management options perfectly.

4. The BIG problem is that whle the installation detects a KONICA-MINOLTA printer, for that's probably how the PRINTER reports itself at the USB port. All one has to change is the MANUFACTURER to "minolta" and THERE the magicolor 2430 DL shows up, and choosing it and continue (don't choose install any drivers), just proceed, and it will install perfectly. 

5. Then just right-click on its icon to make it default. 

(On Opera and Firefox, would suggest to set the page-layout to 80% rather than "shrink to fit".)

I believe this solves my "mystery" and clears me out of a lot of confussion that had me go through this issue for 3 or 4 days.

I hope this helps others avoid much time wasting as I ran into.

To work with ICM definition files, remove the printer directly via System/Administration/Printing and re-install it without the rpm method. Install it via System/Administration/Printing and click on the "new printer" icon.

SummarY: *After KONICA-MINOLTA 2430 DL is detected and accepted, change the brand to "minolta" and all will be just great.*

-gobuntu

---

### Post by gobuntu on 2007-10-09
Friends,

Have put up a post under compatibility that clears-up the issue a little more, and it is, I believe, simpler and hopefully quite clear:

[http://ubuntuforums.org/showthread.php?p=3506399&posted=1#post3506399](http://ubuntuforums.org/showthread.php?p=3506399&posted=1#post3506399)

---

### Post by dbodner on 2007-10-12
> **mojavelinux said:**
> Sure enough, it appears that even though Breezy ships with drivers for the magicolor2430dl printer, those drivers don't seem to be enough to get the printer to actually do anything.  The solution, however, is ultra simple and has been explained in this thread.  However, to help out fresh eyes, I am going to summarize EXACTLY what I did to make it work.

1. Go to: [http://printer.konicaminolta.com/support/current_printers/mc2430dl_sup.htm#Drivers](http://printer.konicaminolta.com/support/current_printers/mc2430dl_sup.htm#Drivers)

2. Get:  Printer Driver for Linux Version: 1.5.0

3. Unpack it

4. sudo apt-get install alien fakeroot

5. fakeroot alien magicolor*rpm

6. sudo dpkg -i magicolor*deb

7. sudo /etc/init.d/cupsd restart

8. setup printer as normal, but use the driver from the all caps KONICA_MINOLTA category (and not the Minolta category).

9. Print a test page, be happy and go back to praising Ubuntu


Anybody have any luck with this on 7.04?  I followed through the steps, but I get teh error:
"Database Error"
The 'rastertokmXXXXdl' driver cannot be used with printer 'KONICA MINOLTA magicolor 2430 DL'.

Nothing showing up in the cups error log or /var/log/messages.

---

### Post by PaulHuffman on 2007-10-12
Hoorah- finally got a printer running.  All I had to do was choose the Minolta driver in the listed printers, not the Konica-minolta.

---


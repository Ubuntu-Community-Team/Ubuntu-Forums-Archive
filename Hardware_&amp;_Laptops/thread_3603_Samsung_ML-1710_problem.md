---
title: "Samsung ML-1710 problem"
date: 2004-11-07
forum: Hardware &amp; Laptops
---

### Post by claymore on 2004-11-07
Well, it seems I am narrowing down the problems I am having with Ubuntu.  I still love the distro, but I am having a potentially serious problem with my printer.

It works fine and the quality is good, but it's printing about an inch lower than it's supposed to.  I have checked the paper size everywhere in the configuration file, and nothing seems to solve the problem.  I have tried using the CUPS driver that I downloaded from Samsung.com. but the configuration program won't let me choose it.

Is there some setting that I'm missing?

---

### Post by trico on 2004-11-07
I've found that after downloading and installing a new printer driver, you have to reboot before it shows up in the printer dialog.  Try reboot and see if it shows up.

trico

---

### Post by claymore on 2004-11-08
Sorry, I should have been more specific.  It lets me choose the CUPS driver, but as soon as I leave the page, it reverts to a different driver.

---

### Post by claymore on 2004-11-08
Okay, I need to do a little clarification.  After reading more how the whole linux printing system works, it's not a CUPS driver that I was trying to install.  It's just the driver that you can download from Samsung, rather than the one included in the distro that seems to be printing off-centre.  

I will try a reboot again with that driver selected, otherwise I am going to have to find something else to try.

It's really a pain to boot into my other OS when I want to print something off...

---

### Post by claymore on 2004-11-09
Okay, been working on this a little more.  In Open Office, when I go into printer settings, it always returns to A4.  It seems to stay in letter in other parts of the printing thing, but I think it might still be set to A4 somewhere as default.  I have no idea where to even look since it seems that the regular CUPS configuration is broken in ubuntu.

---

### Post by mark on 2004-11-11
[QUOTE=claymore]Okay, been working on this a little more.  In Open Office, when I go into printer settings, it always returns to A4.  It seems to stay in letter in other parts of the printing thing, but I think it might still be set to A4 somewhere as default.  I have no idea where to even look since it seems that the regular CUPS configuration is broken in ubuntu.[/QUOTE] 
*Computer>System Configuration>Printing*, select your printer, bring up Properties and check the paper size in *Paper* and PageRegion in *Advanced* .  That did it for me with an Epson Stylus C82.

Hope this helps!

---

### Post by claymore on 2004-11-11
Thanks for voicing in, Mark.  Unfortunately, that's exactly what I've been doing, and it doesn't seem to be working.

I've sort of relegated myself to booting into my other partition until the next version of either ubuntu or cups comes out... kind of frustrating, but I like ubuntu enough not to give up on it altogether.

---

### Post by tog on 2004-11-13
Been struggling with the papersize issue myself, having tried it on three different printers. Apparently, there is a default paper size that cups uses in /etc/papersize. Try changing the value in that file to letter. I was also messing with the ppd in /etc/cups for the printers that I have, but I still can't fix the problem completely. Sending a job over lpd always prints in A4, rather than letter. If you try the papersize option, and it works, let me know. Thanks.

Murali

---

### Post by claymore on 2004-11-14
[QUOTE=tog]Been struggling with the papersize issue myself, having tried it on three different printers. Apparently, there is a default paper size that cups uses in /etc/papersize. Try changing the value in that file to letter. I was also messing with the ppd in /etc/cups for the printers that I have, but I still can't fix the problem completely. Sending a job over lpd always prints in A4, rather than letter. If you try the papersize option, and it works, let me know. Thanks.

Murali[/QUOTE]

That did it for me, at least in Open Office.  You're my hero.  Thanks so much.

---

### Post by kalinga on 2006-02-12
Hi!
Well, you folks are doing better than me with the old ML-1710.

How did you get the driver installation script (and its nice GUI) to work? I've used this before on various SuSE installations.

Any help or hints greatfully recieved.

PS

I've tried three approaches and none of them work for me.
1 "authentication failure"
./setp.sh -> 
2 does nothing
 sudo ./setup.sh 
3 does nothing
sudo -i
./setup.sh 

I'm running and AMD64 with kubunt 5.10 breezy

---

### Post by xreekinghavocx on 2006-07-19
i can't get past the part where the correct driver doesn't stay selected... it keeps defaulting to the alphabetical first driver. rebooting right after selecting my printer model and the driver doesn't seem to cut it. help?

---

### Post by Chris11 on 2006-11-14
I'v got also a problme with my ML-1710.

no problmes with printing letter from OpenOffice, but when I print a custom formated page it prints the text is shifted 2 inch to the right...

I use the drivers tha came with the ubunto 6.06 disc. any ideas? 

Chris

EDIT: I just installed the new Samsung drivers but I have still the same problem...

---

### Post by bgeek on 2006-12-20
I have the same problem - everything prints fine except in Open Office, which prints 2 or 3 inches or so to the right of the page.  I'm using the Samsung drivers, which work on FC, but not Ubuntu so i'm guessing it's something in Ubuntu. 

Would be grateful for any ideas/solutions.

---

### Post by Inyoni on 2007-01-05
I had a Samsung ML-2552W with the same problem.  My fix was to:

Change /etc/papersize to contain "letter", instead of "a4"

Change the following lines from "A4" to "Letter" in your printers .ppd file 
    (mine was /etc/cups/ppd/Samsung ML-2552W)
    *DefaultPageSize: Letter
    *DefaultPageRegion: Letter
    *DefaultImageableArea: Letter
    *DefaultPaperDimension: Letter

Reboot... just for luck...

---

### Post by Chris11 on 2007-01-08
Thanks for your suggestion - nut it dint resolv the problme with the ML-1710

Chris

---

### Post by Robsteranium on 2007-11-19
I can't print to C5 paper size from OpenOffice.

I've got an HP2605dn.  I've rebuilt the HPLIP drivers twice.  Abiword prints fine.  The HP drivers recognise C5 as does Xubuntu but OO only lets me print to A4, letter and a couple of other categories rather than the dozens that appear under the other (non-OO) dialogs.

Any ideas?

---

### Post by academiphiliac on 2007-11-20
My ML-1710 shoots blanks. Everything seems to be fine except for the absence of ink on the paper.

It's not a printer problem. It works fine with the Macs.

Based on what I've been reading on this thread, setting-up an ML-1710 on Ubuntu requires two steps:
[LIST=1]
[*]Download the driver from the web, as the one that ubuntu automatically installs does not always function correctly
[*]Make sure all settings are adjusted so that the printer knows it is working with 8.5" x 11" letter-size paper
[/LIST]

In regards to the first step, I'm having a little trouble finding the right driver through Google. Would someone kindly post a link?

In regards to the second step, I have the problem that most are having; the print-size is, by default, set to A4. I've changed it to Letter, but both settings have the same result. I still get empty pages.

Faith, brothers and sisters. We will get things up and running eventually.

---

### Post by Robsteranium on 2008-01-09
I reinstalled the HP device manager from synaptic which seems to have done the trick.

Have you tried splix?

---


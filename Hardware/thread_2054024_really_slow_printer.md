---
title: "really slow printer"
date: 2012-09-06
forum: Hardware
---

### Post by lintlicker on 2012-09-06
Hi,

I am running the latest lubuntu on a machine with unknown specs.  My old (fast) computer was stolen over the summer (I'm a teacher) and I was given a replacement that does not boot windows.  I know this is not much to go on.  Sorry. I am slightly experienced with linux (I run dual boot Vista/Linux Mint on my laptop).  If this information is obtainable through lubuntu, I will get it if you tell me how.

I'm trying to run a hp Lazerjet 1200 series printer using one of the old serial port (the big plug with like 56 pins).  I tried to follow other instructions to use CUPS and hplip-2.8.9 but I ran into problems with the installation.  I was unable to find anything about CUPS, and hplip said it was missing required dependencies.  

I was able to use the gui "printing" tool under "system tools" to configure the printer.  The issue is that it takes a LONG time for the printer to process a job before it prints.  It took probably 20 minutes to process a 4 page webpage print job, and even then, it printed at about a page every 3-5 minutes.  When I was using this printer on my XP machine last year, it worked much much faster.

Is there anything I can do to fix this issue?

Thank you in advance.

Lintlicker

---

### Post by joparksc on 2012-09-06
That printer has some speed issues using the Konqueror browser and some other applications.

There is an article on openprinting.org ([http://www.openprinting.org/printer/hp/hp-laserjet_1200](http://www.openprinting.org/printer/hp/hp-laserjet_1200)) that may help you.

Try using the pxlmono driver (instead of the HP one) when you set up the printer and remember to set the printing type to greyscale instead of color.

Hope this helps.

---

### Post by lintlicker on 2012-09-06
Hey!  It works WAY better now!  Thank you!  

I needed to wrestle with CUPS and I used the driver you recommended.  Now it works like it used to.

Should I bother trying to remove hplip?

---

### Post by lintlicker on 2012-09-11
Since my last post, my printer has stopped functioning altogether.  I figured since I was using a different driver, I wouldn't need hplip, so I used synaptec to remove it.  Today, I tried to use the printer and it would not print from ABIWord.  I used the CUPS web interface, and discovered it no longer had the driver selected.  Re-selecting the driver prompted the printer to spit out a page with an error message.  (Happened twice, different errors)

PCL XL error
     Subsystem: KERNEL
     Error:     IllegalTag
     Operator:  0x40
     Position:  55

PCL XL error
     Subsystem: KERNEL
     Error:     IllegalOperatorSequence
     Operator:  SetClipRectangle
     Position:  43

I am unable to get the printer to respond to anything except the occasional test page command.  I've re installed hplip-3.12.9.run and it hasn't changed anything.

I think I've done screwed something up.  I've looked at openprinting.org and haven't found anything helpful.  I don't know what else to try.

Thank you in advance for your help and advice.

---

### Post by lintlicker on 2012-09-19
Bump.  

Still having problems.  Was able to get the printer working again using the printing gui interface, but it is still very very slow.  I'm using the pxlmono driver, but the problem persists.  I'm willing to wrestle with my machine, but I do not know where to start.  Does a resource exist that discusses the manipulation of printer settings? 

I'm a windows native, but I'm trying to understand linux/ubuntu.  To me, ubuntu is this magic OS that mysteriously just works 99% of the time.  It's that 1% when it doesn't work that I have absolutely no idea how to proceed.

Even a nudge in the right direction would be greatly appreciated.

---

### Post by lintlicker on 2012-10-03
Last ditch bump.

Does anyone have a suggestion how to proceed?  I'm still experiencing long delays between sending print jobs and having them actually print.  I'd like to take advantage of this opportunity to learn about linux/ubuntu and how to fix issues.

I won't bump this again if it remains ignored.

---


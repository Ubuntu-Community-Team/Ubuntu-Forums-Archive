---
title: "Latest CUPS update broke printing"
date: 2010-06-23
forum: Hardware
---

### Post by konradpiskorz on 2010-06-23
The latest upgrade of the CUPS system has broken access to my printer, a HP Laserjet 1300.  Printing no longer works at all.  The repository was [lucid-updates].  Trying to force the original lucid packages (from lucid repository) in package menager makes packagemanager uninstall them. :mad:

files updated:
cups_1.4.3-1ubuntu1.2_i386.deb
cups-bsd_1.4.3-1ubuntu1.2_i386.deb
cups-client_1.4.3-1ubuntu1.2_i386.deb
cups-common_1.4.3-1ubuntu1.2_all.deb
libcups2_1.4.3-1ubuntu1.2_i386.deb
libcupscgi1_1.4.3-1ubuntu1.2_i386.deb
libcupsdriver1_1.4.3-1ubuntu1.2_i386.deb
libcupsimage2_1.4.3-1ubuntu1.2_i386.deb
libcupsmime1_1.4.3-1ubuntu1.2_i386.deb
libcupsppdc1_1.4.3-1ubuntu1.2_i386.deb

I should also note, trying to downgrade cups-client_1.4.3-1ubuntu1.2_i386.deb to the alternative version in the [lucid] repository as opposed to the [lucid-updates] repository makes aptitude want to remove ubuntu-desktop... WTF.

---

### Post by EngineerStu on 2010-06-23
I appear to be having the same problem with a Samsung 315 networked printer and 64-bit Karmic. I can ping the printer, but the status message in the printer selection dialog says something about it being "unavailable" or "unrecognized."

---

### Post by konradpiskorz on 2010-06-23
Just an addendum,

I have managed to revert the files to their older counterparts with great duress.  However, the issue remains.

@EngineerStu, The problem is similar with me, except my printer is connected via USB.  When I plug in the printer it is recognized as a HP Laserjet 1300.  However as soon as I try to print, an error pops up saying the printer may not be connected.  However the printer status remains 'processing' until the job it cancelled.

---

### Post by EngineerStu on 2010-06-23
I was able to get printing to work again.

After verifying that I could still print to my Samsung from a different computer I opened the "Printer Configuration" tool on my Ubuntu box and found that the "Enabled" box was no longer checked. Re-enabling the printer got things working again.

The "Enabled" check box is in the "Printer" menu, not in the printer's properties. You can also get to that menu by right clicking on the printer's icon.

---

### Post by konradpiskorz on 2010-06-24
@EngineerStu, This is not the case with my printing services.  My printers are enabled.

I have tested this on a few printers now.

Not working:
HP Laserjet 1300
HP PSC 950

Working
HP PSC 1310

This is very inconvenient.  I wonder if anyone else is having these issues.

---

### Post by oldrocker99 on 2010-06-24
Using Synaptic, I've been able to reinstall CUPS and have my Epson CX6600 printer  recognized, but I've had to do it repeatedly.

I agree, this is a real pain, and not what I expect from Ubuntu.

:guitar:

---

### Post by konradpiskorz on 2010-06-24
@oldrocker99, Does reinstalling cups fix your system?  It does not for mine.

---

### Post by oldsoundguy on 2010-06-24
This happens a lot. (especially if you just add the updates and do not re-boot!)

Re boot.  Works for me! (cups then sees all 5 printers in 3 locations on my network.)

---

### Post by samedirection on 2010-06-25
> **konradpiskorz said:**
> as soon as I try to print, an error pops up saying the printer may not be connected.  However the printer status remains 'processing' until the job it cancelled.

I had just this problem (with a HP LaserJet 1320 and a DeskJet 920).  But I guess I hadn't rebooted.  

Anyway, rebooting solved it for me.

---

### Post by konradpiskorz on 2010-06-28
I have tried an additional printer which works.

Not working:
HP Laserjet 1300
HP PSC 950

Working
HP PSC 1310
HP Deskjet 5650

Now, my problem is not a reboot and it magically works type of situation.  When on June 21st, I allowed ubuntu to automatically update the cups files located at the beginning of this thread, printing no longer worked for a variety of printers.  Unfortunately of which are our lab printers which is where I do 95% of all my printing.

Now, not all printers are broken, however the ones I use for work are.  The printers are recognized when plugged in just fine.  When a print job is sent to them, ubuntu will pop up a message saying that 'The printer may not be connected?'  Note the question mark in the error message.  If I go and check if the printer is connected through system-config-printer it says it is.  It is only on sending a job that an error occurs.  When looking at the status of a printer it will say processing until I cancel the job.

---

### Post by parktownprawn on 2010-06-30
Something that worked for me:

[http://ubuntuforums.org/showthread.php?t=1503268](http://ubuntuforums.org/showthread.php?t=1503268)

---

### Post by konradpiskorz on 2010-07-05
The following bug report indicates the problem as libusb.  Downgrading from libusb-0.1-4=2:0.1.12-14ubuntu0 to 2:0.1.12-14 fixed the problem.

[https://bugs.launchpad.net/hplip/+bug/595650](https://bugs.launchpad.net/hplip/+bug/595650)

---

### Post by Mat11 on 2010-07-13
Hi i recently updated Cups for printing using Ubuntu 9.10 on an i386 laptop and low and behold no more printing ever after using another printer.So i deleted both the printers and reconnected my usb connection back into my first printer which is recognised being a HP 1300 series (hsp1355) and once again attempted to print a doc and nothing happened.So i clicked into the default printer and where it says HP...serial/usb...(no's and letters) below that there is a box named OTHER i took a gamble pressed that and a previous deleted doc printed out.I went back and printed another doc and all is now back as it was nice and fast !
P.S don't pay any more than a tenner for a black ink _refill._;)

---

### Post by threedee on 2010-07-14
I think my machine has this same problem. 

I just fixed it by deleting the printer, and then added a new one, selecting USB rather than HPLIP as the printer type.
[B]
This is not an acceptable remedy for a someone who uses a computer but who doesn't work in IT or is technically minded.

[/B]Any word on when this is going to be fixed? This is a bit of a disaster really. Think about how long from when the patch was pushed out that caused this problem, up to when a patch is released to fix it. Is it days? Luckily I don't use my printer a lot, but if I used it every day, and Ubuntu was making the demand of me to go without printing for several days, that would be unacceptable. I don't think many people would stick it out for that long if they can't print.

I have read the solutions but most people would not take the time to implement them, even if they could find them, buried in bug reports and forum posts. Instead reinstalling Windows. Remember, if they can install Ubuntu, they can install Windows!

So aside from fixing this problem, the lessons to be learnt are:

(A) When something like this happens, the fault is admitted and put up somewhere, with an easy to follow remedy that is clearly documented. Do not expect people to look for it.

(B) What is to be done to stop this from happening again? Aren't these things tested for? I don't want to know why this one was missed, whether it's HPs fault or libusb or whoever. That's not the point.

Sorry for a bitchy and whiney first post! I humbly introduce myself to the forums. I reserve the right to bitch and whine about Ubuntu, but please believe me when I say, I've been using Ubuntu for a few years, and I will **not give up on it**. So don't tell me to :)

---


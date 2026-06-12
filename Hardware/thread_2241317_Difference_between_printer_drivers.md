---
title: "Difference between printer drivers"
date: 2014-08-25
forum: Hardware
---

### Post by lou_parker on 2014-08-25
Recently, I tried an experiment.  I compared printer drivers from my Win 7 machine, my macbook pro laptop and my ubuntu 14.04 machine.  the printer is a Canon MG7120.  I downloaded the scangear driver from Canon Europe.  I could not beleive the difference between machines.  I guess that it is the driver.  The Win7 and the Linux driver printed my picture very dark and muddied colors.  The Mac was vibrant.  Is there that big a difference between drivers or is there another setting in Linux that I am missing?

---

### Post by pdc on 2014-08-27
Hi Lou; I am not entirely clear if we are comparing "oranges" with "oranges":

if you click on this link [http://localhost:631/printers/](http://localhost:631/printers/) for ubuntu?? and look at the right-hand column: entitled Make & Model ....................does it say [COLOR="#EE82EE"]gutenprint[/COLOR] for the Canon?

_________________________

You say you downloaded the scangear driver from Canon Europe: that drives the scanner side of the device ......................... you are talking of the printer function, is that right?

______________________

for the Canon debian driver; for the **printer**; I would go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100551202.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100551202.html) and download and SAVE the file which is [COLOR="#008000"]cnijfilter-mg7100series-4.00-1-deb.tar.gz
[/COLOR]
the commands in a terminal to install it are pasted line by line; hitting the ENTER key after each paste ........

[COLOR="#FF0000"]cd Downloads
tar -zxvf cnijfilter-mg7100series-4.00-1-deb.tar.gz
cd cnijfilter-mg7100series-4.00-1-deb
./install.sh[/COLOR]

.................is that what you did?

---

### Post by lou_parker on 2014-09-01
Thanks for the advice.  Pardon me for not being clearer.  I was wondering if anyone was able to comment on the quality of drivers for the apples, oranges and I guess lemons I was comparing.  I realize they are different, but I was surprised to see the different outcomes on the same printer.  I did not use the canon asia driver, but I will try that.  I used the canon Europe driver using the same terminal entries you suggested. I did try the gutenprint and saw no difference.  The MAC print looked much better.  I did download and install both the scangear portion and the print driver portion of the tarball.  I am a huge Linux convert and taking the EDx class online this month to learn some more about Linux.  Thanks so much for the suggestions.  I'll see if the photo outcomes are different.  :razz:

---


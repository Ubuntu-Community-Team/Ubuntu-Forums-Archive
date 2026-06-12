---
title: "Printer problem: Brother DCP-130C prints content shifted upwards by 1 inch"
date: 2011-10-25
forum: Hardware
---

### Post by kwanylongy on 2011-10-25
Hi all,

    I am a Ubuntu newbie on 11.10. I installed the driver for my Brother DCP-130C printer following the steps described [[COLOR="Blue"]_here_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1166868") (steps performed are detailed below). After the installation, the printer worked, yet the content printed is shifted upwards by an inch. I tried re-installing the printer driver, but the outcome was the same, and I have no idea how I could fix that. :(

    Could someone please help me on this? Any suggestion or comment would be much appreciated! Many thanks! :)

Steps performed
===============
[LIST=1] 
[*] Install [COLOR="Blue"]brother-cups-wrapper-bh7[/COLOR] and [COLOR="blue"]brother-lpr-drivers-bh7[/COLOR] using Synaptic
[*] In System Settings/Printing, I first deleted the printer added automatically by Ubuntu (as recommended in the post),  I then added the printer using the wizard. I selected driver specifically for 'Brother DCP-130C' in the wizard, as it was available.
[/LIST]

---

### Post by kwanylongy on 2011-10-26
anyone? :confused:

---

### Post by KiwiExpat on 2011-10-27
Since 11.04 all my prints on DCP-130C have been missing the top half or so of the first line, regardless of where I was printing from (LibreOffice, pdf, image, etc).

I upgraded to 11.10 (on a 32-bit machine) and hoped this would fix it - no luck.

By the way, after the 11.04 upgrade, both DCP-130C printing and scanning failed so I had to reinstall drivers from Brother and make a number of other changes...

Finally today, I seem to fixed this (for me), so hope this helps:

1. have a look at this file
       /usr/Brother/Printer/dcp130c/inf/brdcp130crc

2. there is a line in there that defines the paper type - in my file, it read PaperType=Letter (even though I had assiduously ensured that paper size was set to A4 whenever I was printing from Libre etc)

3. open Terminal and move to the /usr/bin folder

4. run this command:
       sudo brprintconf_dcp130c -pt A4
       (enter your password when prompted)

5. check the brdcp130crc file again
   paper type should now be set to A4

Caveat - I don't know anything about the other options or different paper types that can be set using brprintconf. Have a look at this link [https://bbs.archlinux.org/viewtopic.php?pid=430970](https://bbs.archlinux.org/viewtopic.php?pid=430970) which pointed me in this direction.

Looking around at other Brother files in the Brother/inf and Brother/Printer folders, I noticed what appears to be a discrepancy in A4 paper sizes in the paperinf and paperinfij2 files with different widths and heights for A4 - so if the above doesn't work for you, you might want to check that out as well.

---

### Post by kwanylongy on 2011-10-27
> **KiwiExpat said:**
> Since 11.04 all my prints on DCP-130C have been missing the top half or so of the first line, regardless of where I was printing from (LibreOffice, pdf, image, etc).

I upgraded to 11.10 (on a 32-bit machine) and hoped this would fix it - no luck.

By the way, after the 11.04 upgrade, both DCP-130C printing and scanning failed so I had to reinstall drivers from Brother and make a number of other changes...

Finally today, I seem to fixed this (for me), so hope this helps:

1. have a look at this file
       /usr/Brother/Printer/dcp130c/inf/brdcp130crc

2. there is a line in there that defines the paper type - in my file, it read PaperType=Letter (even though I had assiduously ensured that paper size was set to A4 whenever I was printing from Libre etc)

3. open Terminal and move to the /usr/bin folder

4. run this command:
       sudo brprintconf_dcp130c -pt A4
       (enter your password when prompted)

5. check the brdcp130crc file again
   paper type should now be set to A4

Caveat - I don't know anything about the other options or different paper types that can be set using brprintconf. Have a look at this link [https://bbs.archlinux.org/viewtopic.php?pid=430970](https://bbs.archlinux.org/viewtopic.php?pid=430970) which pointed me in this direction.

Looking around at other Brother files in the Brother/inf and Brother/Printer folders, I noticed what appears to be a discrepancy in A4 paper sizes in the paperinf and paperinfij2 files with different widths and heights for A4 - so if the above doesn't work for you, you might want to check that out as well.

Thank you so much for your reply, KiwiExpat.

I did follow your suggestion to see if it fixes my problem - turns out that the printed content is shifted down by 1 inch this time! But your suggestion provides a direction towards solving the problem, I will fiddle with the other 'paper size' options and other related settings to see if it leads me some where.

Thanks again for your help! :D

---

### Post by roger_1960 on 2012-03-11
Hi

Have you set te printer default paper size to A4 in the cups settings?

Go to localhost:631 in a browser, go to printer tab, select your printer, go to the administration drop down and select "set default options" and there the paper size.  This solved a similar problem for me.

Good luck

---

### Post by kurt18947 on 2012-03-11
I believe you're using the drivers from the repositories.  If you're still having problems, you might try installing the software provided by Brother.  It's found here and must be installed via the command line on 64 bit systems.  32 bit systems can use Ubuntu Software Center or Gdebi:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)

If you're using a 64 bit system, you also need to look through this:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html#004)

Which steps apply depend on distro version.  There are also scanner issues with 11.10 and 12.04 (so far).  They can be made to work but require a bit of tinkering.

---

### Post by kwanylongy on 2012-03-23
Thanks for your reply Roger and Kurt. :p

My problem was solved after following KiwiExpat's instructions for the 2nd or 3th time (god knows why...). Sorry I forgot to update here that I had already solved the problem!

Many many many thanks! :p


Carlos

---

### Post by Cal55 on 2012-05-01
Further to this.  I've had the same problem with my Brother DCP-350C since upgrading to 11.10 and now 12.04, which I had hoped might fix it.

KiwiExpat's fix worked for me.  I didn't do any other editing or file moving (as I couldn't find the file in the location specified), just simply ran an amended version of his script :-

> **KiwiExpat said:**
> 
4. run this command:
       sudo brprintconf_dcp**350**c -pt A4
       (enter your password when prompted)

This seems to have done the trick.

Thanks KiwiExpat!

---

### Post by norbertomoritz on 2012-12-05
Thank's to kwanylongy for showing the path to dcp130c configuration files. I'm running Mageia and i use midnight commander to edit both files brdcp130cfunc and brdcp130crc, i changed it from Letter to A4 and it started  to print correctly. On Mageia the path is /usr/local/Brother/Printer/dcp130c/inf. Thank you all.

---

### Post by offgridguy on 2012-12-05
Lot's of useful stuff in this thread.:D

---


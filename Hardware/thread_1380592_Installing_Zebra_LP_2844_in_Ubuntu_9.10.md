---
title: "Installing Zebra LP 2844 in Ubuntu 9.10"
date: 2010-01-13
forum: Hardware
---

### Post by jhadhar65 on 2010-01-13
Hello all...

Ubuntu 9.10
Foomatic 0.7.9.2ubuntu2
Gnome CUPS config tool 1.1.12
Pentium 4
USB 2.0
Zebra LP 2844 (EPL II)

I'm in the process of helping my church convert some of their computers from MSWIN to Ubuntu 9.10.  These machines are used for checking kids into the Children's Center and use locally attached Zebra label printers that they already have and have been using.

When installing, it finds no drivers for Zebra at all under 'Makes' and the generic make doesn't appear to offer a label printer.

My background work on this suggested that there may have been Zebra EPL II drivers in previous editions of Ubuntu and/or CUPS, but they seem to be missing now.

Any/all suggestions greatly appreciated...

---

### Post by zandebar on 2010-01-15
I am having the same problem, except that our printer was working perfectly, until we updated to 9.10.  We went to a laptop that had 8.04 on it, and it worked again.  After updating the laptop, the zebra no longer works.  Obviously it has something to do with the update, and am hoping someone can fix this soon, otherwise we'll just have revert back to 8.04.

---

### Post by jhadhar65 on 2010-01-15
[FONT=monospace][FONT=Verdana]I think the absence of instruction here possibly has to do with someone's copyright, but I can't be sure.

I have learned that it might work out best for you if you created and installed your own ppd file.  That's simply a text file with a ".ppd" extension instead of a ".txt" extension and you can make one yourself easily with gedit or any plain text editor.  You'll need the ppd instructions to go into the file to make it a real ppd file, however.  I'm guessing if you happened to search for "zebra.ppd", you might find a sample file that you can learn from to arrive at driver instruction needed to finish your new ppd file.  Get rid of text lines that don't start with "*".  The first text line should start with "*(something or other)" and the last line should consist of "*%".  It will make sense if you look at the sample as you read this.

Somewhere about a third down or so you'll find references to cupsModelNumber.  The lines that start with "*%" are instructional and not read by the system.  16, 17, and 18 are model numbers that correspond with your printer's language type, basically EPL or ZPL.  If yours is EPL like mine, change the line:

"*cupsModelNumber:  18"

...to something like:

[/FONT][/FONT][FONT=monospace][FONT=Verdana]"*cupsModelNumber:  16"[/FONT][/FONT] or [FONT=monospace][FONT=Verdana]"*cupsModelNumber:  17"

I used 17 and that at least made mine do something after I changed the printer driver to this file in the CUPS GUI.  I'll try 16 as soon as I can and report back.  I'm sure more tweaking will be required.

To be clear, I'm not encouraging any copyright violations - just showing you how to learn to do simple things yourself as I am myself learning to do.  Hopefully I haven't violated any terms of service here.  I apologize and will eagerly rectify it if so.
[/FONT][/FONT]

---

### Post by jhadhar65 on 2010-01-16
Well, I'm no further ahead than I was at last post and I have no more time to devote to it.  I really thought I was close to an answer.  The printer is still "doing something", but it's not the something I want it to do.  The page (label) alignment isn't right, letters are too big, and none of it fits on the selected label size.

I'm attaching the latest two ppd files I've been working with... for what it's worth.  I have tested them at the CUPS website and they check out okay, but they don't work for me.  Maybe someone else will get farther than I have.

I've been down every road I can think of:  Modding the ppd, changing printer settings in CUPS, changing page settings per job - nothing seems to help.  It's a shame, too, as I'm an ardent Linux follower and I've been running my mouth about how the church I'm doing the work for should convert to Linux - safer, cheaper, more secure, more robust, etc.  Now I can't even get the easiest Linux OS to work for them.  I've had their machine for two weeks now and I just can't keep it any longer.

As much as it pains me, it looks like it's back to Windows for them... and I'll keep my mouth shut now.

---

### Post by jhadhar65 on 2010-01-18
Here is a great resource of ppd's for study - Zebras at the bottom:

[http://opensource.apple.com/source/cups/cups-136.11/cups/ppd/](http://opensource.apple.com/source/cups/cups-136.11/cups/ppd/)

As I mentioned before, it's back to WIN for these machines, but I did experiment a little farther and I think the Zebra ppd's would have worked out fine with some more tweaking.  I think there are still issues to be solved, including printing labels from web apps that ASSume all/most users are on Redmond machines.  A project for another day...

---

### Post by motion_design on 2010-05-18
Hey,

I was having the same problem as above, I have a zebra LP2844 printer and originally used EPL to print but since updating to lucid, lost the print settings.

I solved this those by following the above thread, I copied the zebraep1.ppd file into gedit, changed the cups model number to 17 in the script and saved as a .ppd file, then plugged in the printer and instead of search for a driver I directed to the ppd file and the printer worked!

I had to print a few times and make a label template to get it printing in the right place.

but thanks and i hope this works for jhadhar65 so he can get his church back on ubuntu!!!!

---

### Post by isotherm on 2010-07-05
Thanks for these tips. I used the zebra.ppd at the slightly newer link:
[http://opensource.apple.com/source/cups/cups-136.18/cups/ppd/](http://opensource.apple.com/source/cups/cups-136.18/cups/ppd/)

The Zebra DA402 now works successfully. And it works with PayPal shipping. It also works with FedEx Ship Manager, but you must edit /etc/cups/raw.types and add the following line:

application/vnd.cups-raw        priority(1000) string(0,"^XA^CF,0,0,0^PR12^MD30^PW800")

The above line is for ZPL printers. If your printer is EPL, instead you need:

application/vnd.cups-raw        priority(1000) string(0,"*PB USB001")

Note that I determined these strings based on the FedEx Ship Manager. They may not be generic enough to detect all ZPL/EPL output.

---

### Post by jacob019 on 2010-09-10
isotherm, thank you so much.  The addition to raw.types made all the difference with my Zebra LP2844.

---

### Post by telseth on 2010-09-22
Thank you all of you!  Here are the full steps for the LP2844 to get it to work.

1. Download [http://opensource.apple.com/source/cups/cups-136.11/cups/ppd/zebraep2.ppd](http://opensource.apple.com/source/cups/cups-136.11/cups/ppd/zebraep2.ppd)
2. Add the printer, specify the PPD file when it asks what driver.  Choose the one above.
3. Add the line "application/vnd.cups-raw priority(1000) string(0,"*PB USB001")" to the end of /etc/cups/raw.types
4. sudo dpkg-reconfigure cups, "Do you want CUPS to print unknown jobs as raw jobs?" :: choose "Yes"
5. Print test page.
6. ???
7. PROFIT!

(Written out somewhat for my own benefit).

---

### Post by djhellbent on 2010-10-05
My Zebra LP2844 printer works now...However I can't seem to get the configuration correct.  It's squishing letters together, and the margins are not quite exact (about 1/4"-1/2" off).  I've gone threw and setup the printer to accept the paper size (4"x6"), still nothing.  Changing the DPI from 203 to 300 fixes it, but then the label is printed too large and gets cut off (as well as printing on two concurrent pages).

Any ideas?

---


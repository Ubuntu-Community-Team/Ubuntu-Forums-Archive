---
title: "End of my wits -- CAN NOT INSTALL Brother MFC J410W"
date: 2012-04-17
forum: Hardware
---

### Post by WinRiddance on 2012-04-17
I thought I had this problem licked 3 weeks ago but last week it came back to haunt me once again, this time worse than ever before !!!

I have a Brother MFC-J410W multi function printer that I used to have working on Xubuntu 11.04 just fine. But ever since I upgraded to Xubuntu 11.10 about 1 month ago, this printer has been refusing to work correctly. Now it won't work at all anymore, at least not from my relatively new machine with or without USB (if I try to set up a network printer).

I've installed this printer according to older directios that I had on my computer and it won't work. I've installed it from scratch (every time) following the step by step instructions from the Brother website. I've double, triple, and quadruple checked the required libraries to see if I'm missing something. All told I must have installed this printer a good dozen times in the past 2 weeks alone. Followed instructions from here too:
[http://ubuntuforums.org/showthread.php?p=10428811#post10428811](http://ubuntuforums.org/showthread.php?p=10428811#post10428811)

**The printer appears to be installable** ... message pops up informing me that printer is installed ... check of properties to confirm shared, ownership, and idle status ... attempt to print and printer icon appears in the tray ... AND THAT'S ALL SHE WROTE every single time. If I check the printer properties again, the idle status has changed either from idle to "waiting for printer to become available" or from idle to "printer is not connected" or from idle to "processing" which will remain in that state indefinitely if I don't cancel the pending print job. USB or network, it doesn't seem to make a difference at all.

I think part of the problem may have to do with the fact that Brother also updated their lpr and cups drivers for this printer which is why their instructions don't jive with the ones that I used a few months ago. Now I'm afraid that all of the different installations may have convoluted parts of the printing system to where I'll never get this printer working again.

Any ideas? I really don't know what else to try at this point ... :cry:
I don't know enough about Linux to safely remove anything that might be conflicting either. :cry:

.

---

### Post by ahallubuntu on 2012-04-17
OK, let's back up:  did you get the PPD file from here?  (You're using the PPD method?)

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J410W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J410W)

Stick to USB for now - it's less complicated than network printing.  Once you get it working reliably for USB, try it again as a network printer...

---

### Post by WinRiddance on 2012-04-17
Well ... that's all part of the problem ...
Yes, I got the lpr and cups drivers from the Brother site for my printer model. Those downloaded deb files contained the PPD file too.. Initially those downloadable deb files were version 1.1.1-1 and that version worked on my Xubuntu 11.04 setup. Network printing worked as well back then.

Later, when I began having printer problems after my upgrade to 11.10 the new installation of those drivers wouldn't work for me any more, but it might have been an error on my part though. Didn't receive any terminal errors either but during an earlier installation attempt this morning a command with an error in it actually processed through without any error in the screen.

So I went back to the Brother site and downloaded the updated deb files that are there now, version 1.1.3-1 debs. The printer is a primary printer that's attached to my fairly new laptop via USB port. However, since we have Roadrunner Lightning I also tried to install the printer as a network printer. But for that, the info. in the directions from the Brother site doesn't jive with the URI/PPD description of my old (working) installation, nor with the info. that I get when I ping my printer via terminal. Since I used Windows for 18 years before switching to Linux, I'm now beginning to enter the realm of madness & despair ... :o
(just kidding)

PS: At this point I'm not even certain any more which method is for network printing and which is for USB printing ...

.

---

### Post by ahallubuntu on 2012-04-17
I understand your desire to want to use your printer over the network.  I'm just saying that UNTIL you get it working reliably with USB, stick to USB, because it's simpler to get that working than a network printer.

Since I can't see exactly what you're doing or be clear on what you've done, it's hard for me to offer you much more specific help.    I have installed a Brother laser printer in Ubuntu a few times, but that was in 11.04 which you too were able to get working.  11.10 is a big change in a lot of things, namely the kernel being upgraded to the 3.0 kernel.

You might consider moving on to the upcoming 12.04 LTS release that is due out very soon; let's hope that fixes whatever problem you ave having!  Otherwise, I'd google around for more help.  Other Brother printers that are similar may have similar issues in 11.10 like what you are experiencing, so looking for tips beyond just for your exact model may be helpful to you.

---

### Post by kurt18947 on 2012-04-17
I'm not sure how much help I can be.  I installed an MFC-J430W on both 11.10 and 12.04.  The last time I tried 12.04 it was having first page issues -- took about 45 seconds from clicking 'print' to the printer waking up.  11.10 was and is perfect.  I installed as documented on Brother's site.  Do be sure to look at the 'pre-install' instructions or whatever they call it.  This was on 32 bit 11.10 but I've installed on 64 bit via the command line with no issues.  To change from USB to wireless was trivial for me.  I did assign a static I.P. address to the printer.  When I got to the printer property window, I noted the device URI.  For a USB connection it will be something like usb://Brother/MFC-6490CW?serial=xxxxxxxxxx.  I just changed that line to
```
socket://xxx.xxx.xxx.xxx:9100
```where xxx=I.P. address

Apparently this is an old-timey method of connecting a networked printer but it works well.  Here's another tip for Gnome-shell.  To get the old fashioned printer configuration app back, in a terminal type 
```
system-config-printer
```It's also pretty easy to create desktop launchers.  Setting up the scanner function is more involved but that would be way OT.

---

### Post by WinRiddance on 2012-04-17
Oh, believe me ... before I seek help in the forum I'm always googling and looking for solutions in other areas too. Sometimes I use as many as 4 different search engines before eventually getting "back" to the Ubuntu forum since I prefer to start/end posts with actual answers which will help more [SOLVED] threads to appear here ... :KS

So which method is the non-usb method?
Brother has lpr as well as cups based installation, which would you recommend? Thanks.

.

---

### Post by WinRiddance on 2012-04-17
**@kurt18947**

Thanks a bunch. I'll be using that info. tomorrow and I'll post back to let everyone know how it turned out. Maybe we'll get that "solved" in here after all ... ;)

.

---

### Post by kurt18947 on 2012-04-18
> **WinRiddance said:**
> Oh, believe me ... before I seek help in the forum I'm always googling and looking for solutions in other areas too. Sometimes I use as many as 4 different search engines before eventually getting "back" to the Ubuntu forum since I prefer to start/end posts with actual answers which will help more [SOLVED] threads to appear here ... :KS

So which method is the non-usb method?
Brother has lpr as well as cups based installation, which would you recommend? Thanks.

.

No matter whether you use a USB or network connection you must install both lpr and CUPS.  lpr first, then CUPS.  Brother's instructions are a little confusing in that they recommend CUPS if it's available.  That could lead someone to believe they don't have to install lpr.

---

### Post by roger_1960 on 2012-04-18
Hi, if you havn't already done this but have done everything else, this could be the solution - it evaded my notice for many weeks...

I believe you have to do this:

Ubuntu 9.10, 10.04, 10.10, 11.4, 11.10
1. Open "/lib/udev/rules.d/40-libsane.rules" file.
2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):


The lines to be added---------------------------


# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"


3. Restart the OS.

Suggest you use
Quote:
sudo gedit /lib/udev/rules.d/40-libsane.rules
to open file for editing.

This is taken from the Brother website - scanner settings for normal user. I could not get my device (printer or scanner) recognised without this. 

Hope it helps.

Roger

---

### Post by kurt18947 on 2012-04-18
Roger_1960 is correct for the scanner function.  Additionally in 12.04, at least the development releases, I had to add scanner users to the 'lp' group in order for the scanner to be recognized.  I don't know if that will be the case with the final release or not.

---

### Post by WinRiddance on 2012-04-18
> **kurt18947 said:**
> No matter whether you use a USB or network connection you must install both lpr and CUPS.  lpr first, then CUPS.  **Brother's instructions are a little confusing** in that they recommend CUPS if it's available.  That could lead someone to believe they don't have to install lpr.

ABSOLUTELY .... :D

That was part of the problem that I ran into as well. I never even knew that the drivers & instructions were different because they removed any older info. with their older drivers which makes it confusing for anyone who has older info. on their machine ... from back when those instructions or files worked ... just a few months ago.

And you're right, it's not clear at all that LPR **and** cupswrapper are both required, no matter what.

I just submitted a step by step tutorial for this specific printer, the MFC-J410W. It has everything step by step as I went through the process of getting my printer going again. Don't have a link for it here since it's pending approval but I'm going to mark this thread as solved. I don't have any scanner instructions though. Those who need to scan might want to subscribe to this thread for that reason. Thanks for the assist and pointing me in the right direction(s). ;)

[COLOR=DarkRed]**EDIT:**[/COLOR] The tutorial for this printer finally made it Online, it's available here: [http://ubuntuforums.org/showthread.php?t=1961148](http://ubuntuforums.org/showthread.php?t=1961148)

.

---


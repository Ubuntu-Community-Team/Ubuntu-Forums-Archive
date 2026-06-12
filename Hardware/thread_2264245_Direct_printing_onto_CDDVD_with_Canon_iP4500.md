---
title: "Direct printing onto CD/DVD with Canon iP4500"
date: 2015-02-06
forum: Hardware
---

### Post by MZ250Supa5 on 2015-02-06
Seemingly simple task, but also seemingly impossible to achieve.  Despite several How-to articles on the web, (most of them quite superannuated) there seems to be no way of printing directly onto printable CD/DVD.  The few articles I've found don't seem to work, and though I've tried using Gutenprint and followed the instructions there, I still have no success.  My system (Ubuntu 12.04) offers the option of printing to the CD tray, as I have installed Gutenprint, and the printer initially responds, but then hangs and does nothing.  I don't particularly want to use Turboprint as I would eventually have to pay for that, and anyway, such a seemingly trivial issue must surely have been solved by now with free and opensource drivers.

If anyone has any ideas, I'd be happy to hear them.

PS.

I note that some who have posted similar questions in Linux forums have been misinterpreted as wanting to print labels - I DO NOT want to print labels, I want to print DIRECTLY on to the media surface.

---

### Post by Mark Phelps on 2015-02-06
I have been able to print directly to CDs and DVDs -- but my case is slightly different from yours.

While I also used Gutenprint with their drivers, I was printing to Epson printers, first, an R200 and later, an R220.

The drivers are really important because they allow you to configure printing to the disks and to align the output to fit exactly on the disk.

IF there are no such drivers for Canon printers, then you are out of luck.

---

### Post by pdc on 2015-02-06
> such a seemingly trivial issue must surely have been solved by now with free and opensource drivers.

......................such things are done by volunteers............ in their own free time .............. they show great commitment; dedication; selflessness; your values would resonate greatly with them; join their community

---

### Post by aikishugyo on 2015-02-17
Hello,
I'm the current maintainer of the Canon backend in the gutenprint project, and I have an iP4500, so this is my testbed too.
First of all, I agree with you that these "problems" should be solved, and I made some efforts, partially successful, but still not entirely grokked as to what parameters need to be set, and their interaction.
I have an entire rewrite of the CD printjob creation which is not committed to the code because of the uncertainty still.
What we have currently is some very hacked code based I believe on an iP4200 for which CD printing should work. Not breaking this while expanding the printing to other printers and tray types is a challenge.
What I have done so far is isolate one printer per tray type (as you might know there are tray types from A to at least L by now, which have mostly different parameters of printjob sizes and centering).
For the iP4500 with tray type F, I can I believe print with the currently committed gutenprint code. Since I have not touched it since 5.2.10, that or any later version (5.2.11 pre-release or compiled directly from CVS) should work for you also.
You need to be careful: since this is CUPS, there is no message from the printer via the driver on the screen telling you when to insert the CD and what button to press once that is done.
Also, you absolutely must select the correct parameters in CUPS: CD tray, CD media, 5" CD, and one of the 3 CD resolutions. If any of these is not chosen correctly, the printer firmware will throw up its hands and refuse to print. Actually, the situation is not quite so dire, as since 5.2.9, the driver does have some convoluted logic to try and guess what the user intended, so if CD media is chosen, then the resolution at least will default to one of the CD resolution modes (based on quality of the currently chosen but inapplicable mode) even if the user chose incorrectly. I don't think there are heuristics to handle the tray selection though, IIRC, so that must be correct.
So, assuming your printjob in CUPS is correctly set to output a proper CD printjob, prepare the printer first! Open the front door and power it on. Don't open the CD tray section (it folds down and out).
Then print under CUPS. Now CUPS sends the data to gutenprint, and gutenprint sends it off to the iP4500.
The firmware then looks at this incoming printjob, and decides to activate the CD printing mode, quite complicated and under Windows interactive with the user. However, with linux and CUPS we are on our own.
The orange light under the power button blinks. At this point you should fold down the CD tray section, and insert the CD tray with a CD, up until the arrows on either side of the tray are level with the front of the CD tray section of the printer.
Once that is done, press the upper printer button, the one that is for formfeed (with the inverted triangle mark also next to it).
This indicates to the printer to start the calibration and printing of the CD. After a few pull-ins and push-outs the calibration is done, the CD is pulled all the way in, and is slowly printed on the way out. Voila!

My problem is currently that the offsets are not correct, so your printing may not be centered---please experiment to see if you can work around this with pre-offcentered images. When I try to fix the offsets, other things tend to go wrong still, with the parameters interacting with one another in unfortunate ways.

I hope the above helps, and you can follow the steps to print CDs on your iP4500 under linux. If you really get lost, try printing on a Windows machine to understand better when to do what on the printer in relation to sending the printjob.

Best regards,
Gernot Hassenpflug

---


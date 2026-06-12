---
title: "Printing problem in FireFox &amp; Brother MFC-J430W"
date: 2012-05-16
forum: Hardware
---

### Post by kurt18947 on 2012-05-16
[FONT=Ubuntu]I've run into what appears to be a pretty narrow problem that I suspect is going to be very difficult to diagnose.  I'll be pleased to be proven wrong on this.[/FONT]
 

 
[LIST]
[*][FONT=Ubuntu]Text printed     from FireFox looks like it's been printed on a 9 pin dot matrix     printer with a couple pins misfiring.  It's most noticeable on small     type and in draft/fast  mode as expected[/FONT]
[*][FONT=Ubuntu]The problem is     with text only, graphics print as expected.[/FONT]
[*][FONT=Ubuntu]It only occurs     with the Brother MFC-J430W.  I have two other Brother printers, an     MFC-6490CW and MFC-7820N.  Neither of those exhibit this problem     when printing with 12.04 and FireFox12 or 13.[/FONT]
[*][FONT=Ubuntu]The problem     occurs in Firefox only.  I installed Opera and the page prints as I     would expect.  It isn't just one web page or site; any pages with  quite a lot of small text is pretty much unreadable.[/FONT]
[*][FONT=Ubuntu]Ubuntu 11.10     and FireFox 11 print as expected.[/FONT]
[*][FONT=Ubuntu]I reset     FireFox 12.  It made no difference.[/FONT]
[*][FONT=Ubuntu]It appears to  be related to HTML text.  I created a simple text document in     LibreOffice, saved it as .html and opened it in FireFox.  The     printed text was crude.  The same filed saved as .odt and printed was smooth as expected.[/FONT]
[/LIST]
 

 [FONT=Ubuntu]So the problem occurs only on 12.04 and only on the Brother MFC-J430W.   I wondered If there was something to do with Gnome, Compiz, Unity or Gnome-shell.  I installed Lubuntu12.04 and did the updates.  The problem is still present with Lubuntu 12.04 with only updates and FireFox installed.[/FONT]
 

 [FONT=Ubuntu]The machine belongs to SWMBO and I think she would have a difficult time with another browser, she's been using FireFox since Netscape.  I have a fix in place using the screenshooter  add-on  then printing the screen capture which works okay but it's extra steps.[/FONT]
 

 [FONT=Ubuntu]It would be easy to say it's a FireFox problem but pages rendered on Firefox 12 & 13 print fine on two other Brother printers.  To say it's a Brother printer driver problem ignores that pages printed from Opera appear as expected.  And the same drivers print correctly on FireFox 11.[/FONT]   I wonder if this has shown up with any other printers.
 

 [FONT=Ubuntu]Thoughts?  Report a bug to Mozilla?
[/FONT]

---

### Post by kurt18947 on 2012-05-18
Hmmmm, well it's looking like an Ubuntu/Brother problem.  I've installed - temporarily - Xubuntu 12.04 64bit and Lubuntu 12.04.  The same problem occurs every install.  Ubuntu 11.10 and FireFox 11 don't exhibit this problem.  I then downloaded FireFox 11 and FireFox 10 from Mozilla's archives.  I checked help -> about and the versions did indeed check.  I launched 10 & 11 via the executable in Xubuntu 12.04.  The same printing problem occurs running FireFox 11 & 10.  This leads me to believe there's some interaction between *buntu 12.04, Firefox and certain Brother print drivers that causes poor print quality. 

I guess it's time to file a bug report and not expect too much, this being such a narrow problem unless others chip in with "me too" or other printers.

Edit:  It's not just FireFox.  I installed Chromium in Xubuntu 12.04.  Chromium exhibits the same symptoms as FireFox.  I did not expect this seeing as Chromium is, I believe, a WebKit based browser unlike FireFox.

---

### Post by markiangooley on 2012-05-20
I am getting very slow print processing with my USB-connected Brother HL-5250DN since going to 12.04 .  Usually a file will print out okay but whether it's a test page printed from CUPS, a PDF from Adobe Reader, or a webpage from Chrome, the printer flashes the light to indicate data is being received... for some minutes per page instead of a few seconds the way it did before the upgrade.

---

### Post by kurt18947 on 2012-05-20
> **markiangooley said:**
> I am getting very slow print processing with my USB-connected Brother HL-5250DN since going to 12.04 .  Usually a file will print out okay but whether it's a test page printed from CUPS, a PDF from Adobe Reader, or a webpage from Chrome, the printer flashes the light to indicate data is being received... for some minutes per page instead of a few seconds the way it did before the upgrade.

I had a similar problem during 12.04's gestation.  There was always a 45-50 second delay before printing started.  My problem was fixed during one of the last updates before 12.04 became 'official'.

I'm still trying to narrow down the problem with printing htlm text from FireFox & Chromium.  Opera works okay.  As far as I know both Opera and Chromium are webkit based browsers which makes FireFox no longer the prime suspect.  I would like to be able to narrow the problem before filing a bug with either Ubuntu or Mozilla.

---

### Post by kurt18947 on 2012-05-31
Fixt.  Some update, I'm guessing a CUPS-filter update has the little fella working as expected in 12.04.

---

### Post by lkub on 2012-06-01
> **kurt18947 said:**
> Fixt.  Some update, I'm guessing a CUPS-filter update has the little fella working as expected in 12.04.

Kurt,

Glad to hear your problem is solved.  Does your printer prints correctly from all applications?  Here is why I'm asking: Brother's own web site ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00107](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00107)) indicates that their printers don't print correctly from Ubuntu 12 from the following applications:

CUPS testprint
Document Viewer
GIMP

So, does your printer prints correctly from these three apps?

---

### Post by kurt18947 on 2012-06-01
> **lkub said:**
> Kurt,

Glad to hear your problem is solved.  Does your printer prints correctly from all applications?  Here is why I'm asking: Brother's own web site ([http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00107](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00107)) indicates that their printers don't print correctly from Ubuntu 12 from the following applications:

CUPS testprint
Document Viewer
GIMP

So, does your printer prints correctly from these three apps?

It appears that all the above print correctly.  I did not perform thorough tests but 

CUPS testprint did print correctly and has never been an issue for me.

1 page from a Brother .pdf file printed correctly in Document Viewer

A .jpg file imported into GIMP printed correctly.

My issue seems to have been with printing .html text which now appears to be printing cleanly.

---

### Post by lkub on 2012-06-01
> **kurt18947 said:**
> It appears that all the above print correctly.  I did not perform thorough tests but 

CUPS testprint did print correctly and has never been an issue for me.

1 page from a Brother .pdf file printed correctly in Document Viewer

A .jpg file imported into GIMP printed correctly.

My issue seems to have been with printing .html text which now appears to be printing cleanly.

Glad to hear that - congratulations and thanks. Did you use Brother's tool (linux-brprinter-installer-1.0.4-1) to install the drivers?  Or, if not, how did you do that?

---

### Post by kurt18947 on 2012-06-02
> **lkub said:**
> Glad to hear that - congratulations and thanks. Did you use Brother's tool (linux-brprinter-installer-1.0.4-1) to install the drivers?  Or, if not, how did you do that?

I have used the installer recently.  The thing I find useful about the installer is that it takes care of the 64 bit tweaks associated with Brother printer drivers.  I'm not sure why Brother has 64 bit scanner drivers but only 32 bit printer drivers.  Before discovering the installer script  I was just following the directions on the driver download page.  I have found the installer complains about no folder /var/spool/something.  I just checked and the folder /var/spool/lpd does exist and I didn't create it manually so I guess it's a false error message, not sure.

---

### Post by lkub on 2012-06-12
> **kurt18947 said:**
> I have used the installer recently.  The thing I find useful about the installer is that it takes care of the 64 bit tweaks associated with Brother printer drivers.  I'm not sure why Brother has 64 bit scanner drivers but only 32 bit printer drivers.  Before discovering the installer script  I was just following the directions on the driver download page.  I have found the installer complains about no folder /var/spool/something.  I just checked and the folder /var/spool/lpd does exist and I didn't create it manually so I guess it's a false error message, not sure.

That's great - thank you.  I'll use the installer, then (when my printer arrives - it's still on its way).  Did you have to do any " pre-required procedures" Brother mentions or you just run the installer?  And does the printer needs to be connected before you run the installer, or you connect the printer after running the installer?

Many thanks!

---

### Post by lkub on 2012-06-16
Here is some info that might be useful to Brother users:
My MFC has arrived and I installed it (both printing and scanning functions) with no particular problems with one important exception (that took me some 10 hours to debug!): While printing works through both USB2 and USB3 ports, scanning works through USB2 ports only (at least, on my PC).

---


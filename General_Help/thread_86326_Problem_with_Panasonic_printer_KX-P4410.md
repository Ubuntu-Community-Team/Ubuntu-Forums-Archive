---
title: "Problem with Panasonic printer KX-P4410"
date: 2005-11-04
forum: General Help
---

### Post by ValhallaSystems on 2005-11-04
Yes its an old printer, but it works fine under windows (Where have I heard that before?) Actually its a Raven LP510 - Thats how panasonic branded their printers many moons ago in Canada. The manual says it is Laserjet II compatible.

I'm using Ubuntu 5.10. It appears to install the printer correctly using the Gnome printer install wizard. It uses ljet2p which is (after research on the web - Linuxprinting - I think) apparently the correct driver. However, when I attempt to print a test page, I get one line of miscellaneous ASCII characters, and then a form feed, then another page the same, then another page the same .... The printer jobs window says the file is 150K, so I abort printing by taking the printer off line - waste of paper otherwise. Switching off the printer cleans out any print stream left in the printer. But as soon as I switch the printer on again, the stream of garbage continues. Did I say that by then I've also deleted the print job from the printer jobs window, so the print spooler must still be full and raring to go.

Have I missed something. How can I get the test page to print correctly. I haven't been able to test it on another printer - its the only one I have. And since Ubuntu is the only distro I've found so far that can make sound, recognize my laptop widescreen display, and my wheeled mouse. I've also had problems getting them to find my printer at all. So I'd kind of like to be able to go with it.

Also, if anyone can tel me how to clean out the print spooler without rebooting I'd sure like to know.

So after all this rambling...

1. How can I make my printer print something I can recognize?

2. How can I cleanout the print spooler?

Thanks to anyone who can help.

---

### Post by Joe_lurker on 2005-11-04
I am willing to be that the first 3 characters of the printed page are %ps.  You are using a postscript driver for a non-postscript printer.  Try the "LaserJet II Series" of the "LaserJet III Series" drivers.

To clear out the spool go to System | Administration | Printing.  Double-click on the printer in question.  In the printer dialog choose Edit | Cancel Jobs.

-Joe

---

### Post by ValhallaSystems on 2005-11-05
Thanks for the idea BUT.

I did it again, and installing it as a laserjet 2 did not work. Got similar results.

So tried the ljet2p driver again.

This time I looked at the output.

The first line was"2 /MT52 put Encoding 53 /MT53 Encoding 54 /MT54 put Encoding 545/MT55 put Enc" and the printer ran out of space.
The next page was blank, and the next, and the next ....

Presumably this is not Postscript.

Any suggestions?

---

### Post by Joe_lurker on 2005-11-05
Try this:
Download the ppd file to your home folder from 
[http://www.linuxprinting.org/ppd-o-matic.cgi?driver=ljet2p&printer=Panasonic-KX-P4410&show=0](http://www.linuxprinting.org/ppd-o-matic.cgi?driver=ljet2p&printer=Panasonic-KX-P4410&show=0)
Open a terminal window and enter the command:
```
sudo lpadmin -p Panasonic -E -v parallel:/dev/lp1 -m Panasonic-KX-P4410-ljet2p.ppd
```
This assumes your printer is connected the the LP port on your computer.
Now go to the printer dialog, you should see the new printer named "Panasonic",  and try and print a test page.

Since I don't have a similar printer to fiddle with this is about all I can suggest.  I have had problems (in the old days) with non-postscript printers but this looks like it should work fine.

-Joe

---

### Post by ValhallaSystems on 2005-11-07
Thanks for your help Joe, however, this did not work either.

option -E is not recognized by lpadmin, option -m should be -P

With those changed, the command script installed a network printer that could not find the printer installed on my parallel port. We tried.

Thanks again - not sure where to go now. Am going to try Kubuntu when it finishes downloading on my other machine. I hate to say this but Knoppix can install the printer correctly using CUPS.

---

### Post by ValhallaSystems on 2005-11-07
Well, Kubuntu did successfully install my printer. The KDE printing manager offers more driver options. The one that I chose and which worked was "foomatic plus ljet2p". Don't ask me!

I like the KDE desktop, but there are some features about GNOME that are really slick. Now if the two could get together!

This still does not offer an answer as to why GNOME could not do the trick ... but I've run out of time to try figure out why.

---


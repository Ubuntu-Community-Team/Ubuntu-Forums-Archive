---
title: "(resolved) Printing from Ubuntu to Windows Printer Samba Share"
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by lottes70 on 2007-01-27
Ok, this is a printing issue that I've closed but I want to share what I learned because it is useful for printing from Ubuntu to any Windows printer share without needing linux printer drivers. For example, I have a Canon Pixma which does have linux drivers, but they are laborious to install (though there are very good step by step guides to do this).

Those drivers are not necessary if you are printing to a Windows printer share using Ghostscript and a redirected printer port. That is because you can set up Linux printer with any of the included postscript printer drivers and print generic PostScript documents to a "ghostscript share" on the Windows box, and then the "ghostscript printer" on the Windows box converts the postscript file and prints it on the windows machine using the windows machines printer driver for the printer. No linux driver for the printer necessary.

The first thing you have to do is set up the Windows printer. Obviously, install the printer on windows. I have a Pixma installed on Windows 2000 Pro SP4. Next, you have to follow [these instructions]("http://iharder.sourceforge.net/current/macosx/winmacprinter/") to install a redirected printer port on windows. They are great instructions, but their goal is a little different than ours, so you'll have to deviate a bit from the instructions on that page. You will only do steps 1 to 3 on the linked page, and at the end of 3, there are some changes...

[LIST]
[*]You might want to pick the LaserWriter 12/640 PS for your printer (I actually have the 660 set up on the windows box, but there isn't a 660 driver on Ubuntu, but I think it'll work just fine either way).
[*]At the point where you are told NOT to share the printer, DO share the printer.
[*]After following another few steps you are told to set up the redirected printer port. On Win2k, I had to set it up differently to get it to work. The settings I used are (and these may not be "optimized settings" in the sense that some of these settings may be not necessary): 1) my path to gsprint was not the same as the example 2) my "arguments" were '-color -' (without apostrophies but with space and extra seemingly useless hyphen) 3) then (on Win2k at least) I set output to "copy pipe to printer" 4) on Printer I selected the printer that I wanted to print on (my Pixma) 5) and I checked "Run as User"
[*]Make sure you can print a test page. I couldn't at first, and then I just jacked around with settings and finally I got it to work.
[/LIST]

Now you are done with the Windows part of the exercise. Now, you might want to make sure you can print in some way from Ubuntu over Samba. I can't walk you through all that, but I think the least you should be able to do is set up on Ubuntu a generic type printer for printing text files. Then, if you have samba set up right on Ubuntu and Windows, you should be able to print from gedit, I think, because it just does generic character printing which doesn't require a driver, I don't think (a bit out of my depth here).
Anyway, once you've got your Samba set up properly, you'll need to add a PostScript printer into Ubuntu. I recommend going to System->Administration->Printers and then double clicking "Add New Printer" and using the wizard. You can probably add any postscript printer you want, I added a LaserWriter 12/640 PS because it matches what I set up on the Windows box. After it is installed, open the printers properties and:
[LIST]
[*]make sure all the paper is set to Letter (if appropriate for you)
[*]On the Advanced tab, make sure the "Ghostscript Prefiltering" setting is on "Convert to PS Level 2"
[*]of course on the "Connections" tab make sure you have correctly typed your share host and printer share name.
[/LIST]

Now it should work. Good luck. Sorry these instructions are somewhat lame, but I hope someone finds it useful. It fixed a problem I was having with printing from dapper to windows Canon Pixma (great printer, BTW). I found that I could print from gedit and evince but not from Firefox or anything else. (Interestingly, I have the release before dapper installed on a different computer, and it can print fine to my windows Share with the same setup that wouldn't work with dapper.) For what it's worth, I saw another thread that suggesting replacing all of Ubuntu's CUPS setup with the CUPS directories from MEPIS.

Anyway, as I said, if you have a printer shared on a windows box and don't have linux drivers for it, you can use this set up to print to that printer from Linux without having that printers drivers for Linux.

---

### Post by FunkSoulStrange on 2008-03-29
I know this is a really old post but maybe someone will stumble on this problem, I modified the GhostScript printer as you suggested and it works fine but I get an additionally error page plus blank page on every print job.  (This happens on the windows print test page as well as from Ubuntu)

The error message page is as follows:

ERROR: typecheck
OFFENDING COMMAND: get

STACK:

/Policies
/ClusterHalftone
-dictionary-
-dictionary-
-dictionary-
-mark-


Any thoughts/suggestions would be appreciated.  Thanks!

EDIT:  I was able to go into the advanced options of the printer and turn off "Send PostScript Error Handler" which removed the error page but I still get the blank page.  I'm sure its something silly, but its not jumping out at me.

---


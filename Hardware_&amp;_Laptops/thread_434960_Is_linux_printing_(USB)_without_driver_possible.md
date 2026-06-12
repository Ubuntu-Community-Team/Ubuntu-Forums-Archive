---
title: "Is linux printing (USB) without driver possible?"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by gwatts on 2007-05-06
I have 3 wired XP computers and a Linux Ubuntu 7.04 computer. I have a Canon D320 printer/copier. The printer is USB  attached to one of the XP devices. I use a D-Link-604 router and all 4 ports are in use. My goal is to migrate from XP to Linix  for most of my work.

I can find no driver in several Linux driver banks for the printer. Crossover on the Linux did not help.

What is the best and most realistic way to use this printer or do I need new hardware?

I will probably want to use a wireless "n" router at some time in the near future if a print server is required although if Ubuntu will work on the USB, I could keep one of the XP devices temporarily unplugged since my print needs are not great.

Currently I transfer the files to be printed to a USB key or over the network to print from the USB XP device.

Thank you.

---

### Post by Pigsflew on 2007-05-07
It might be pretty hard to "just try" drivers to see if something works, so here's probably your best bet:

There are a lot of postscript printer drivers for Linux (and other operating systems), so if you can make Windows pretend that it *is* a postscript printer, and then just convert on the fly to raw to be printed, you can make windows into a printserver for your unsupported hardware.

This can be done through GhostScript and GSPrint. I haven't personally tried it (i have an HP printer that has linux drivers), but there seems to be a decent tutorial [here]("http://mywebpages.comcast.net/heretrythis/hp3100/psemuxp.html").

Good luck!

---

### Post by gwatts on 2007-05-07
I don't expect you to solve my problem but have you any suggestion as to where or how  I can pursue this error?

I am following the Postscript Emulation for Network Printing that you suggested. It worked perfectly down to the point where  I can go no further).

C:\gs>cd ..

C:\>cd program files\ghostgum\

C:\Program Files\Ghostgum>gsprint waterfal.ps
'gsprint' is not recognized as an internal or external command,
operable program or batch file.

C:\Program Files\Ghostgum>cd gsview

C:\Program Files\Ghostgum\gsview>gsprint waterfal.ps
Copyright (C) 2003, Ghostgum Software Pty Ltd.  All Rights Reserved.
2003-09-03 gsprint 1.6
AFPL Ghostscript 8.14 (2004-02-20)
Copyright (C) 2004 artofcode LLC, Benicia, CA.  All rights reserved.
This software comes with NO WARRANTY: see the file PUBLIC for details.
Error: /undefinedfilename in (waterfal.ps)
Operand stack:

Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval-
-   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   fa
lse   1   %stopped_push
Dictionary stack:
   --dict:1115/1686(ro)(G)--   --dict:0/20(G)--   --dict:70/200(L)--
Current allocation mode is local
Last OS error: No such file or directory
AFPL Ghostscript 8.14: Unrecoverable error, exit code 1


C:\>cd program files\ghostgum

C:\Program Files\Ghostgum>gsp
'gsprint' is not recognized a
operable program or batch fil

C:\Program Files\Ghostgum>

Thank you.

---

### Post by Pigsflew on 2007-05-07
sounds like it just isn't finding the program when you're in one folder, and isn't finding the file when you're in the other. Try adding GSPrint's folder to the PATH variable:

1.  From the desktop, right click My Computer and click properties.
2. In the System Properties window, click on the Advanced tab.
3. In the Advanced section, click the Environment Variables button. 
4. Finally, in the Environment Variables window, highlight the path variable in the Systems Variable section and click edit. Add or modify the path lines with the paths you wish the computer to access. Each different directory is separated with a semicolon.

Just add a semicolon and the path to GSPrint into that path, hit OK and try again. I'm not sure if you have to restart after doing this.

---

### Post by Pigsflew on 2007-05-07
Oh, and make sure you were spelling "waterfall.ps" correctly, looks like you missed an "L" :)

---

### Post by gwatts on 2007-05-09
Thank you. I appreciate your efforts.

I followed your directions but no printing.

In the example command path in the help file you would see:

“C:\gs\gsview\gsview&gtgsprint waterfal.ps”

The help file has "&gt" that is not in any of my installation files. (So I searched for &gtgsprint and came up with no results on C:).

I don’t know where the “&gt” part is coming from. Could this be significant?

 I.e. my installation does not seem to include something the troubleshoot file suggests is part of the package.

I Googled “gsview&gtgsprint” but it only refers back to the help file from which it came.

---

### Post by Pigsflew on 2007-05-09
It looks like &gt is supposed to resolve to the "Greater than" symbol... you were correct to navigate to the "gsview" directory. Did you change the command so that you were entering "waterfall.ps"? The directions say to enter "waterfal.ps" with one 'l', you may want to check the files in the directory to see if such a file exists. If not, you can download an example postscript file to use [here]("http://atrey.karlin.mff.cuni.cz/~milanek/PostScript/Examples/images/").

---

### Post by gwatts on 2007-05-10
Thank you

The waterfal has only the single " l " and at an earlier point in the protocol I printed waterfal.ps as well as snowflak.ps. 

I guess they like to shorten the command.

Assuming I have made no typos, should I cut my losses here and get a network printer or can you think of any other possibilities.

---

### Post by Pigsflew on 2007-06-06
hm... unfortunately you might have to bite the bullet on this one... I'd go with almost anything Hewlett-Packard, because their driver support for linux is pretty phenomenal.

Sorry I couldn't help further

---


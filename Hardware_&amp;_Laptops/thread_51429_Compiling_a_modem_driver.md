---
title: "Compiling a modem driver????"
date: 2005-07-23
forum: Hardware &amp; Laptops
---

### Post by rebalde on 2005-07-23
At last I think this newnewnewbe can ask an intelligent (though be it very basic) question. 

I instaled a "Diamond Supra Max LE" (very cheap)  analog modem.  On the install disk there are two (2) linux drivers.  #1 is "slmdm-2.7.14.tar.gz" and #2 is slmodem-2.9.7.tar.gz.  After decompressing them I read the appropriate readme files, but when I got to the "DriverCompiling.txt" I found myself in a delema
 .
First I need to quote from the text, and this is verbatum:
"Within the workshop there is an instruction set, the Makefile, and a few tools.  You command: ""make clean"" An elf named "make clean" reads Makefile and then cleans up any debris of previous efforts."   O:)  I love it! whoever wrote that knows how to communicate.  OK back to the quote:  "The major work of compiling drivers and any associated tools is commanded with: "make" or perhaps "made DriverName" then finally "There only remains to command installation of the modem driver(s) and tools with: "make install"....  the author then proceeds with some over simplified but amusing dialog.

But NOW: my question:  
Where is my workshop??  or: is there an existing folder for this "workshop", or should I make a subfolder for it, and if so: under what higher folder????? last part of the question, can anyone tell me which driver might be best for ubuntu 5.04.  

I created a subfolder for the drivers and their associated files here:  /home/Desktop/Modem/linuxdrvrs/.  I would be happy to send more info if you need it.

I know there will be more questions, but answering this will get me started.

rebel

---

### Post by ubuntp on 2005-07-24
Simply start those commands from the directory of the drivers (where you extracted them). I have no idea what a workshop is, and it's also interesting that there's gonna be an elf making all this :D

---


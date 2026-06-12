---
title: "Printer: Canon Pixma iP4820 - can't get to work"
date: 2011-02-03
forum: Hardware
---

### Post by angelsneverdie on 2011-02-03
Hello boys and girls.

I recently purchased a Canon Pixma ip4820 printer and I can't get it to, you know, print.  I followed some instructions from this thread:
[http://ubuntuforums.org/showthread.php?t=850298&highlight=pixma+ip4820](http://ubuntuforums.org/showthread.php?t=850298&highlight=pixma+ip4820)
and now when i got to system>administration>printing  it shows Canon-iP4800-series.  when i tell it to print a test page, it sends it as a job, and then says complete, but the printer never actually does anything.  when i try to print an open office document, nothing.

has anyone else managed to get this printer to work with ubuntu?  if so, how?  

otherwise does anyone have any ideas of what i can try?  is there anymore information i can provide that would be useful?  let me know.

by the by,i'm using Ubuntu 10.10 64 bit.

Gracias!

---

### Post by angelsneverdie on 2011-02-04
update:  i got it to work using drivers from the canon europe site:
[http://software.canon-europe.com/index.asp](http://software.canon-europe.com/index.asp)

---

### Post by ewg on 2011-02-05
What driver did you use? I don't see for for the 4820. I did see 4840 & 4850 drivers.

Thanks,

---

### Post by gunit888 on 2011-03-04
I had the same problem, and I got it working pretty easily.  Here's the steps I took:

1. Go to: [http://software.canon-europe.com/index.asp](http://software.canon-europe.com/index.asp) to get the drivers
-From the Printers drop down, I chose "PIXMA iP4840".  I have a PIXMA iP4820, but that option wasn't listed, so I took a gamble on this one and it works for me.
2. Select "Linux" and your language from the two drop down menus.
3. Click on "Linux IJ Printer Driver".  The version number when I tried this was 3.40
4. Download the .tar file.
5. Extract the .tar file, and then extract the file: cnijfilter-ip4800series-3.40-1-deb.tar.gz
6. Within the newly created directory resulting from the second extraction, make sure the 'install.sh' script has executable permissions.
7. In a Terminal window, execute the 'install.sh' script.  It automatically ran it for me using sudo, so I had to provide the appropriate password to proceed.
8. It automatically searched for printers, and gave me a list of detected printers.  I should point out that before I started, the printer was plugged into a power source, the USB port on my Ubuntu machine, and the power was on.  It detected my computer as "Canon iP4800 series".
9. I chose the detected printer when prompted, and took the default for the printer name.
10. I chose 'y' when asked to set it as my default printer.
11. I opened up the Printing menu from System->Administration->Printing, and right clicked on the new printer to open up it's Properties menu.  From there, I chose Print Test Page to make sure it was working.

It took about 2 or 3 minutes for me of listening to various strange printer self check and diagnostic noises, but I let it go and it printed a perfect test print page out for me.  I'm running Ubuntu 10.10.

I hope that helps someone out!

---


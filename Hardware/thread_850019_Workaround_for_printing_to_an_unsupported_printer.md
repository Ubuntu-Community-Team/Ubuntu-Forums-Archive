---
title: "Workaround for printing to an unsupported printer"
date: 2008-07-05
forum: Hardware
---

### Post by boazarad on 2008-07-05
I have a Xerox Phaser 6125N (absolutely unsupported in linux) connected to a windows machine.
Is there any way I can set up the windows machine to receive print jobs from the linux machines on my network - and send them to the printer using the correct drivers?

SMB Printer sharing is not an option - as it requires the correct drivers on the client side.

---

### Post by lswb on 2008-07-05
Have you tried drivers for similar, maybe older model Xerox printers? Anyway, I don't know enough about Windows to give an exact solution, but, if you print to a .pdf or postscript file on the linux box, it should be possible to configure some type of service to run on the windows machine that will handle this. Perhaps even just copy the ,pdf files to a shared directory on the Windows machine, and have the windows equivalent of cron periodically check for any files there. If they are found, print and delete them. Also, I'm not sure about the Phaser, but many recent printers can print a .pdf directly.

---

### Post by boazarad on 2008-07-05
After trying several similar drivers (Xerox 6130, 6110 etc) - to no avail,
I tried setting up [pdfcreator]("http://www.pdfforge.org") as a shared printer on windows machine, and set to auto printing.
That did not go very well either.

Eventually I managed to set up a virtual postscript printer on the windows pc, and routed the output to the windows Xerox 6125N printer driver.

I've detailed the process in [my blog]("http://www.boazarad.com/sharing-the-xerox-6125-n-with-linux-clients")

---

### Post by jaxån on 2011-01-16
Just if someone comes here when searching:
There are no support for this from Xerox, but there are some from Fuju Xerox on another printer that works on x86 and AMD64 cups.

Search here in Ubuntu Forums for 6125N and DocuPrint C525A. The DocuPrint C525A can be made to work.

---


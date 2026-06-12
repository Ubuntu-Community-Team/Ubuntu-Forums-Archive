---
title: "Fuji Xerox M205B printer / scanner"
date: 2011-07-19
forum: Hardware
---

### Post by jasonjob on 2011-07-19
Any clues as to how I can use this with Ubuntu?  Fuji Xerox provides no linux drivers (although oddly enough they do provide Mac OS X drivers), and various attempts to use generic options have failed.

Is this something where I wait a couple of months and Ubuntu will just know how to use it, or is it another thing that will never be addressed?

Thanks.

---

### Post by nomko on 2011-07-19
Did you try to install the printer using the CUPS administration tool (in a webbrowser go to localhost:631)?
 
*edit*
I just see here: [http://www.fujixeroxprinters.com.au/en/support/Downloads.aspx?product=9934&category=5726&dl=1](http://www.fujixeroxprinters.com.au/en/support/Downloads.aspx?product=9934&category=5726&dl=1) that you can do only a firmware update using Linux software. Have you tried that? It migth bring the solution to get your printer working under Ubuntu.
 
**edit**
Had a quick look on the CUPS website. Seems to me that your device is not supported.

---

### Post by drpjkurian on 2011-07-19
Try this thread. This may help you
[http://ubuntuforums.org/showthread.php?t=273489](http://ubuntuforums.org/showthread.php?t=273489)

---

### Post by jasonjob on 2011-07-19
Cups admin is new to me - trying now...

...and that's just the same as the printing options under System-Administration, except via browser interface.  Nothing new to try there.

The firmware upgrade is, despite what their page says, Windows only (an exe in a zip with some data files), and is only minor bug fixes.

That idea in the other thread of using a driver for a similar printer... hmm... will try that, I think.  Haven't seen any PPD files for this printer yet.

---

### Post by jasonjob on 2011-07-19
Okay, finding a similar printer isn't as simple as I thought - anyone got a better idea than running "multifunction printer" through google images? :)

---

### Post by MyR on 2011-07-20
> **jasonjob said:**
> Okay, finding a similar printer isn't as simple as I thought - anyone got a better idea than running "multifunction printer" through google images? :)

Does this help: [Linux-compatible printers]("http://linuxdeal.com/printers.php") ??

---

### Post by jasonjob on 2011-07-20
> **MyR said:**
> Does this help: [Linux-compatible printers]("http://linuxdeal.com/printers.php") ??

Yes, thanks :)

Unfortunately there don't seem to be any printers physically similar to mine, and I've no idea how you would make hardware comparisons other than that...

Oh well, guess I just wait for it to be covered by someone (if it is...), or simply pass print jobs through SHMBO's windows box.

---

### Post by nomko on 2011-07-20
[FONT=Calibri][SIZE=2]Why aren’t some printer/scan devices properly supported under Linux is basically due to the fact that some hardware manufacturers don’t put any effort in making device drivers for Linux since they reckon that the market is not profitable enough or that the investment they have to make to create drivers for Linux is higher for Linux systems then for Windows or MacOS systems. Also they lack the knowledge of Linux and how Linux operates and to write proper drivers for Linux, they don’t have the qualified developers. Some hardware manufacturers are aiming on a particular market in which Windows systems are more commonly then Linux operated systems. Basically it comes down to availability, investment and unfamiliarity. In such cases, the Linux users at the mercy of the community who develope  usable drivers.[/SIZE][/FONT]

---


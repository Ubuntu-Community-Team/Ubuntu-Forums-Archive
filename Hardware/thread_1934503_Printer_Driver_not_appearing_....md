---
title: "Printer Driver not appearing ..."
date: 2012-03-02
forum: Hardware
---

### Post by asearle on 2012-03-02
Hi Everyone,

I am trying to install a Canon MP540 for a friend and have found that it is turning out to be quite a complicated affair ...

First I found that the drivers supplied by Canon have a dependence on libcups2 rather than libcupsys2 and so, after trawling through the forums, I found instructions on how to change the dependencies.  I then went on to install and found that I could install (apparently successfully) but then, when I tried to connect the printer the driver was not available in the driver list ... despite being visibly available/installed in Synaptic.

So my questions are the following ...

- Can anyone give me further help with the installation of the MP540:  Maybe there are other drivers available somewhere that don't need adapting?
- When we tried to install the printer, the newly installed driver did not appear in the driver list.  Can this happen?  And is there a way around it?  Maybe I need to declare the driver in some other way?  Or does not non-appearance in the list indicate that the driver is corrupt?

Any tips here would be a great help.

Regards and many thanks,

Alan Searle
Cologne, Germany

---

### Post by asearle on 2012-03-06
Hi Everyone,

I found this link ...

[http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html](http://www.ubuntubuzz.com/2011/06/download-install-canon-printer-driver.html)

Which sorted out my problem perfectly.

Indeed, they have a whole list of other drivers which will certainly come in useful for others.

But one word of warning:  Be sure to de-install all other Canon tests (e.g. cnijfilter etc.) and drivers that you have been experimenting with.  Otherwise that will block/mess up the new driver.

Bravo to the guys who compiled these drivers.

Regards,
Alan Searle

---


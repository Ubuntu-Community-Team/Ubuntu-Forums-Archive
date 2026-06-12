---
title: "Keytec ProE Serial touch screen drivers"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by John_T on 2007-11-01
I thought I'd post this as I now have my touch screen working with Feisty, and was banging my head against a wall for a while with it.

After having no luck with any of the documentation I could dig up here, or anywhere else, I contacted  the manufacturer with the text below: (Summarised from a web form I submitted)

> Attempting to use a magictouch addon touchscreen with the Keytec ProE serial interface module on Ubuntu Linux 7.04.
Followed instructions on driver package downloaded from web site.  Directory names not compatible with Ubuntu 7.04.  Converted as best as possible, but the X windows system crashes, and I cannot boot into the graphical environment. Restoring the xorg.conf file recovers the system.

I didn't expect much, but Alex from MagicTouch got back to me the next day with a package full of shiny new drivers which did the trick nicely.  I mentioned that they should update their web page with the new package, do date (1st Nov 2007) that hasn't been done.

There were a couple of minor deviations I had to use from the supplied instructions, which I'll quote below.  Feel free to contact me if you want a copy of the drivers, although I'm sure macictouch would help you out as well.

> Perfect, it's all going now.  The only notes/comments that I would add are:

1. I had to run "Configuration" as root, that is, "sudo ./Calibration", but otherwise the documentation was helpful and accurate.

2. The install script did not create desktop shortcuts to the tools as advertised, although this is not a problem for me personally.

3. Would it be possible to update your web page  [here ]("http://www.magictouch.com/support_proe.html"): with a link to that file? If so,  I'll post something to the community forums to that effect so that others can solve their problems more easily in the future.

Thank you for the prompt reply. Timely and useful technical support is far too rare a thing! It's much appreciated.


I hope this can help anyone someone else out. Most of the help I could find was only applicable to the later, USB hardware models. This applied to the old fashioned serial ones, on a DB9 connector.

---

### Post by John_T on 2008-03-15
It seems that MagicTouch haven't yet updated their drivers page.

Here's a [link]("http://www.megaupload.com/?d=5IPHD1UR") to anyone that wants the driver in the meantime.

---


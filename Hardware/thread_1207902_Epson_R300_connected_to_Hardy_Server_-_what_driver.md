---
title: "Epson R300 connected to Hardy Server - what driver for CUPS use?"
date: 2009-07-08
forum: Hardware
---

### Post by Rebajas on 2009-07-08
Subject pretty much says it all but I'm tired of getting irrelevant results in the various searches I've done so I am turning to the community to hopefully get an answer.

Basically I had this all working on CUPS from my 2 clients, then one day I just couldn't print; even from the CUPS control panel.

I decided to delete the printer and simply reinstall but there are about 50 or so driver options and none of them are R300 printer :( it is defaulting to Foomatic variants.

Any idea which one I should use? Can't live without printer...


Thanks in advance.

---

### Post by shatterblast on 2009-07-09
Installing the Karmic test version of CUPS may help.  The following is the link for it:

[http://packages.ubuntu.com/karmic/cups](http://packages.ubuntu.com/karmic/cups)

If you see something in red color to the effect of "dependencies not met," then you may need to add the Universe portion of Karmic to your Software Sources and then install through Synaptic.  Just take care so that you don't accidentally try a full upgrade to the Karmic test version.  It would be good to remove entries about Karmic away from Software Sources after finishing.

---


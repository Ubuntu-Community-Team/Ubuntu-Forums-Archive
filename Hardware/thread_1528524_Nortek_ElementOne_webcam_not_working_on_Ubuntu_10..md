---
title: "Nortek ElementOne webcam not working on Ubuntu 10.04 (Lucid)"
date: 2010-07-10
forum: Hardware
---

### Post by ^andrea^ on 2010-07-10
Hello everyone,

I have a webcam (Nortek ElementOne) that doesn't seem to be working on Ubuntu Lucid.
I run a test with "gstreamer-properties" and, as you can see from the imagine attached, ubuntu is receiving a "kind of signal" by the camera but it does not work as it's supposed to.

In the imagine you see a Map of the world hanged on the wall... and NO, I didn't hang it oblique!!! ;-)

So, after some (maybe even lots) googleing I've decided to ask for help to see if somebody can figure out what the problem is.
Many tutorials/guides suggest to enable the module gspca but something changed with Ubuntu Lucid (somebody said that Ubuntu Lucid comes with gspcaV2 but I haven't found much info about it).

There is a module related to gspca:

lsmod | grep -i gspca
gspca_sonixb            9272  0 
gspca_main             21199  1 gspca_sonixb
videodev               34361  1 gspca_main


What can I do?

Any suggestion would be really appreciated.

Thanks in advance,
Andrea

PS: I have a laptop HP dv4000 in case it helps...

---


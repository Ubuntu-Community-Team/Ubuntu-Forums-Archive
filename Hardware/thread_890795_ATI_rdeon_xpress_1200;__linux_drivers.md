---
title: "ATI rdeon xpress 1200;  linux drivers?"
date: 2008-08-15
forum: Hardware
---

### Post by dado prso on 2008-08-15
Are there linux drivers for this?

---

### Post by rogorido on 2008-08-15
> **dado prso said:**
> Are there linux drivers for this?
yes, they are.

the best thing is to install the last driver by ati.com:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by dado prso on 2008-08-15
When I goto ati.com I don't see my driver listed.  There is an x1250. Will this work?

---

### Post by swisscow on 2008-08-15
All I did for this was go to hardware drivers in the system...admin menu, and enabled it (must wait for a few moments for it to do it's stuff). Rebboted, job done.

No problems (a lot easier than in the past)

---

### Post by dado prso on 2008-08-15
isn't that just the general ati driver though?

---

### Post by dado prso on 2008-08-15
Ok, Ati has a 32-bit driver for this card, but not a 64-bit.  Is this a problem?

---

### Post by swisscow on 2008-08-16
It's working fine so I'm not worrying about it. Compiz, googleearth all work (though together it's a bit flickery).

Try it, if you're not happy you can always disable it by removing the tick in the hardware drivers box

---

### Post by lavikl on 2008-09-21
As I'm trying to run Ubuntu 8.04 Live from CD or trying to install it from the LiveCD, I get an error "Fatal error : No screens found" and I get thrown out to command line.
It happens early in the installation process (just after I choose the keyboard layout).
Do you have any suggestions how to get over this so I could finaly install Ubuntu ?
My card is ATI Radeon Xpress 1200
and it's on a laptop LG R405

Adi

---

### Post by timothywcrane on 2011-03-04
adding the fglrx package in addition to the regular Radeon drivers will help you with 3d support.

the fglrx-dev info states :

Video driver for the ATI Radeon and FireGL graphics accelerators.

This package provides definitions for the GL and GLX extensions
and the FGLRXGAMMA extension interface library.

Canonical provides critical updates supplied by the developers of fglrx-dev until April 2012.

---


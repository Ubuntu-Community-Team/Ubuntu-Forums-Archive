---
title: "Video driver help"
date: 2009-12-25
forum: Hardware
---

### Post by 6dof on 2009-12-25
All,

I recently tried to change my video driver from the default to one for my specific card.  My hope was that some of the games would run better as they are all fairly slow.  My card is an old ATI FireGL Z1.  I downloaded the driver from ATI's site, and double-clicked on the *.run file and ran it in a terminal window.  It started, but failed.  However now I can no longer run my games - otherwise the system seems fine.

The error message I'm getting states:

Error: ./default_policy.sh does not support version
default:v2.i686:lib::none:2.6.31-16-generic; make sure that the version is being correctly set by --iscurrentdistro

Then it removes the temp directory it created and stops.  

I'm not very knowledgeable with Ubuntu or Linux for that matter.  Is there an easy way to set the system bakc to the previous state?  Or is there a way to finish installing the ATI driver (fglrx-8.583)?  

I tried sudo and gksudo, but couldn't get the installation to start.  Again, I'm not that knowledgeable here and probably typed in something wrong.

Thanks!

---

### Post by 6dof on 2009-12-26
I've found out that there are support issue with older cards and karmic (9.10).  The existing Catalyst driver doesn't work in karmic either.  There are some beta versions available, but these don't support older cards.

I was able to revert back to the default Ubuntu graphics driver by removing "xorg-driver-fglrx" using synaptic.

---


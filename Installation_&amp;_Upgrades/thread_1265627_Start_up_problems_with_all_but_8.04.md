---
title: "Start up problems with all but 8.04"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by hotmeloncoolin on 2009-09-13
ubuntu 8.04 32 bit is the only linux that starts up on my presario f700 amd x2nvidia computer without having to hold a button. I would really love to install ubuntu 9.04 for the newer software or maybe even a 64 bit version for increased speed but every time i try one of these i have to hold a keyboard button upon start up for the computer to start up. if Any body could shed some light as to why this is happening , i will be forever in debt to your wisdom. it just drives me nuts that nothing will work but 8.04, i even tried open suse and it does the same thing. Any help? any body?

---

### Post by hotmeloncoolin on 2009-09-13
sereusly no one knows?

---

### Post by drs305 on 2009-09-13
Is it a specific button you have to hold down?

Can you boot to the LiveCD Desktop without holding down a key?

Have you tried installing from the Alternate CD?

---

### Post by hotmeloncoolin on 2009-09-14
It is not a specific button i have to press. anybutton on the keyboard will work. and the live cd also must have a button to press. It might be worth noting that i bought the 8.04 dvd with a book and the other distros i burned except for open suze that came with linux magazine, i havnt tried the alternate cd is that in the download page?

---

### Post by drs305 on 2009-09-14
> **hotmeloncoolin said:**
> i havnt tried the alternate cd is that in the download page?

It is. The alternate CD sometimes works when other methods don't. In this case, since the problem persists with even other linux distributions lessens the chance that this option will be successful. Nevertheless, it may be worth a try.

---

### Post by hotmeloncoolin on 2009-09-14
yup that appears to have solved the problem. im amazed for mounths i had to hold a button everytime i started up this is great thanks.

---

### Post by hotmeloncoolin on 2009-09-14
Problem has reawakened. i suspect it may have something to due with a nvidia graphic's driver. It did not occur until after two proprietary drivers were installed, one being nvidia  something and a broadcom wireless driver, also updates to ubuntu 9.04 as well. This has happened to other people i know because someone gave me the advice to hold a button down at start up in a irc chat. Still lovin the new jaunty though.

---

### Post by drs305 on 2009-09-14
Your analysis is probably correct. The alternate CD takes a more conservative approach and I would agree that since it worked initially it was probably the driver upgrade or some other upgrade that caused the return of this problem.

If you really wanted to isolate the problem you could reinstall with the Alternate CD then take an image so restoring a working system wouldn't be so painful as you slowly add drivers and update other packages.

---


---
title: "Blacklisted graphics card?"
date: 2009-02-25
forum: Hardware
---

### Post by redb on 2009-02-25
I ran Compiz because I was having problems with visual effects.  Is there anyway to fix this issue?




Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc M24 1P [Radeon Mobility X600]
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 1002:3150 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 


Thanks,

redb

---

### Post by ScarySquirrel on 2009-05-16
The same thing has happened to me, and I do not fully understand the implications.

I found the source code for the script which runs the check, but it tells me little.

[the source code for the script]("http://209.85.173.132/custom?q=cache:VgB8ykubhiUJ:blogage.de/files/3583/download%3Fcompiz-check_2-0+Your+particular+graphics+chip+may+be+blacklisted+on+certain+distributions.&cd=3&hl=en&ct=clnk&gl=us&client=pub-5386907765195439")

---


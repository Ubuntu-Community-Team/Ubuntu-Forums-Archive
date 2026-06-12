---
title: "Ubuntu crashes after loading screen"
date: 2007-08-18
forum: Hardware &amp; Laptops
---

### Post by StandardsDT on 2007-08-18
My friends laptop has been having problems for a while now with Windows not loading and it crashing when trying to reinstall it. So I figured I would pick up the task of trying to solve the problem. My plan was to install Ubuntu to wipe out anything that might have gotten corrupted in Windows that would prevent it from installing. Unfortunately I'm running into an issue with Ubuntu as well. It gets to the loading screen and then it crashes to a black screen with what it appears to be a bunch of error codes. I even tried running it from my USB installation and that didn't work either. At the moment it's just hanging on the loading screen. The model is a Toshiba Satellite  A105-S4254.  Any help greatly appreciated.

---

### Post by merlinus on 2007-08-18
Post system specs.

-merlin

---

### Post by StandardsDT on 2007-08-18
> **merlinus said:**
> Post system specs.

-merlin

Well I'm getting a bit further. Ever since I turned off the 2nd core. This time I'm told the UI won't load and asked me if I would like to see the error  message or something like that so I can diagnose the problem. The error reads.

```

Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting
(++) from command line, (!!) notice, (II) informational, 
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.log", Time Sat Aug 18 11:37:20 2007
(EE) Unable to locate/open config file
```

I'm running off a Ubuntu Live CD that I had shipped to me. So shouldn't the config file not be missing? I did use the disk  to create the USB Live Disk. Maybe that damaged something?

And I'd like to note that after hitting ok I viewed the other output and it was the same error message. However following that I'm taking to a black screen with what it was trying to load and two things failed. They are:

Could not receive return value from daemon process and Starting HP Linux Printing and Imagaing System.

Oh and the specs are

Intel Core Duo Processor, 1024MB DDR2 SDRAM 80GB HDD, DVD Super/Multi (+/-R double layer) drive, 802.11 a/g wireless LAN and a 15.4" TrubRITE (WXGA) display.

---

### Post by StandardsDT on 2007-08-18
Porblem solved. I decided to do some hardware troubleshooting. Took out the hard drive to see if it was bad everything was ok there. Then decided to test the memory. Took out the one loaded Ubuntu and it went straight into a kernel panic. So I shut off the machine reinserted the memory and took out the other one. Turned on the system and Ubuntu Live loaded. Turns out it was a bad memory chip.

---


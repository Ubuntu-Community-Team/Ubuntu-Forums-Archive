---
title: "HP LaserJet 5, PPD"
date: 2013-12-02
forum: Hardware
---

### Post by pwabrahams on 2013-12-02
I'm running Kubuntu 13.10 and recently I've been having a constellation of new printer-related problems.  My printer is an HP LaserJet 5 -- old but reliable, and augmented with a network interface.  The furnished drivers, whether Foomatic or Gutenprint, don't understand the duplexing features, so I had been using an older PPD.  But now when I attempt to set up the printer with that PPD, the printer configuration section of System Settings changes it to "Current - HP LaserJet 5M Foomatic / Postscript".  I go into the printer configuration and use "Manually Provide a PPD Driver".  I can navigate to the PPD I want and select it, but when I press OK or Accept, it gets changed back to Foomatic/Postscript.

I've specified the connection as "socket://192.168.0.11:9100", but I've also tried variations such as "http://192.168.0.11:9100" with no success.  What's even worse, the printer is sitting in a ready state but the driver thinks it's busy.    Throughout all of this, I've consistently been able to ping the printer, so I know it's not a networking issue.

All that nasty behavior started within the last few weeks.  Before that, everything worked fine.  I assume that some update is responsible.

Postscript:  I've finally gotten my printer working correctly, but there are some very odd things about the behavior of the printer configuration module in System Settings. I'm posting a new thread on that subject.

---


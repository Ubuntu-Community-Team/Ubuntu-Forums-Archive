---
title: "Canon MP620 printer issue in 13.10"
date: 2014-02-23
forum: Hardware
---

### Post by dad2 on 2014-02-23
I have the above printer and only use it connected via the usb cable.  I tried to print something today and nothing happens.

The printer is shown as the only printer in the menu and is selected as default printer.  The print queue shows that the print is pending and for how long it has been pending for.  

It's been a while since I printed something and all was fine then (perhaps even pre-upgrade?).

Where do I start in diagnosing and resolving the issue?

---

### Post by mörgæs on 2014-02-23
[http://ubuntuforums.org/showthread.php?t=361236&page=88&p=12909495&viewfull=1#post12909495](http://ubuntuforums.org/showthread.php?t=361236&page=88&p=12909495&viewfull=1#post12909495)

---

### Post by aikishugyo on 2014-02-23
I would suggest for your own enlightenment, to do things in two stages, if this is for the gutenprint driver:
1a. enable debug in the CUPS web interface and then examine the CUPS error log, also accessible from the interface (file is at /var/log/cups/error.log). If the job is shown as pending, it could be as simple as checking that the printer is not paused, for example, in which case no errors would be in the logs.
1b. If there is anything there of note, post it here and maybe keep it as a file for later reference. Also post the driver, which should be shown in the interface, and will also be in the logs.
2. Reinstall the driver ("modify printer" in the CUPS interface), making sure to note whether the same driver is available or a different one. This should only be necessary if an error such as incompatible PPD is in the logs, which would be the case if you installed a new driver and PPD version, while the installed printer is trying to use older ones with different version number.

For the Canon driver, out of my league, use the link given by the moderator....
Regards,
Gernot Hassenpflug

---

### Post by dad2 on 2014-02-24
W: Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon-stable/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/michael-gruz/canon-stable/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


After following the moderators link I have the above error message in Terminal.

I don't know how or where to access CUPS files?

---

### Post by mörgæs on 2014-02-26
It's normal for a PPA to be offline once in a while. 
Do you get access now?

---

### Post by dad2 on 2014-03-02
Thanks to the link provided I have managed to re install the printer on my laptop and the main home pc (all my pc and laptops use Ubuntu 13.10) but the remaining laptop won't seem to communicate with the printer.

I followed the instructions to the letter.  The printer shows as active and default in the printer menu.  When i try to print it just says waiting for the printer to become available.

I've run the update command numerous times in terminal but we can't get past this step.

---


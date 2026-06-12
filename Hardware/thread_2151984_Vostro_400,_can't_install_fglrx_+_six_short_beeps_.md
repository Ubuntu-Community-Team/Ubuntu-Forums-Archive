---
title: "Vostro 400, can't install fglrx + six short beeps on shutdown"
date: 2013-06-06
forum: Hardware
---

### Post by malenkylizards on 2013-06-06
Hello all,

I just installed Ubuntu 12.04 on my workstation at work.  It's a Dell Vostro 400, seen here [http://ps3-www1.us.dell.com/us/en/gen/desktops/vostrodt_400mt/pd.aspx?refid=vostrodt_400mt&s=gen](http://ps3-www1.us.dell.com/us/en/gen/desktops/vostrodt_400mt/pd.aspx?refid=vostrodt_400mt&s=gen), with 8 GB of memory and an AMD ATI RV610 (Radeon HD 2400 PRO).

The install was painless, but now I've got a few problems.  It seems to like the default open-source graphics drivers for the most part, but the one thing that isn't working is Google Earth, which I need to use fairly regularly.  It freezes after a minute of use, and research suggests that what I need to do is install fglrx.

So first I tried installing fglrx through System Tools->System Settings->Additional Drivers, but something's not working there.  All I get is "No proprietary drivers are in use on this system."  The enable button is grayed, and there are no other options.  Next, I tried installing fglrx manually using these instructions: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI), following the "Installing via the command line" set of instructions.  No apparent problems up until I reboot.  When it turns back on, the resolution seems to be about 600x800 or so, and fglrxinfo yields an error message which I will post momentarily (I've got to redo it).  The Catalyst control center is there, but when I click on it I get another error message (again, I'll post it in a minute), saying fglrx isn't installed.  To get back to the working open-source drivers, I have to `sudo apt-get remove --purge fglrx fglrx-amdcccle` and then reboot.

So there's another weird symptom.  I don't *think* this happened every time yesterday when I was installing the OS, but it happened once.  Now, it happens every time.  When I reboot, it gets stuck and starts making a sequence of six short beeps (i.e., BEEP BEEP BEEP BEEP BEEP BEEP PAUSE BEEP BEEP BEEP BEEP BEEP BEEP PAUSE etc.). This sequence keeps going and I have to do a hard shutdown.  I looked online and found this site: [http://www.manualslib.com/manual/371334/Dell-Vostro-400.html?page=82](http://www.manualslib.com/manual/371334/Dell-Vostro-400.html?page=82) which says that six short beeps is indicative of a "Video BIOS Test Failure", if those beeps show up on startup.  I couldn't find any info about what it means if these beeps show up on shutdown.

Not sure what other information I can offer.  Maybe I need to replace the video card?  Hard to tell.  Again, with the exception of Google Earth, the card appears to work great with the open-source drivers.

---


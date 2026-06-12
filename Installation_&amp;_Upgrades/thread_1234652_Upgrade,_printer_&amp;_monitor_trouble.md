---
title: "Upgrade, printer &amp; monitor trouble"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by Alabamian on 2009-08-08
Okay, there's a computer guy I'm in charge of who's having trouble printing.  I check it out, and sure enough, his Brother HL-5250 will not print.  I rebuilt things (it is plugged in directly USB to the CPU.  One of the peculiar things about the printing is that I couldn't get the new print driver to just say, a USB (or paralle) port.  It kept acting like it was a network printer.  I couldn't select lpt1: or usb or anything direct, only various IP address choices, as if for a networked queue.  I tried downloading drivers and everytime I tried to install a 64-bit version, it said I was running a 32-bit OS system.  u-name -a  clearly shws the box to be 64-bit.

So I decide, shoot, I myself had all kinds of printing troubles with Ubuntu 8.04, why don't I upgrade him?  Well, I tried to bring him up to date, but got a message that it couldn't, and it failed, so no upgrades over the Internet.

Then I make the Alternate 8.10 CD, figuring I should be able to get to 9.04 if I make it to 8.10  It autolaunches and tries to install, but I get a "Failed to add the CD" error.  Eventually, I also get "Not all updates can be installed" message, and a partial update option, which I've done.  The installer script said I wouldn't be able to use a proprietary Dell driver (the nVidia, stuff), and we're off.

Now the system defaults to 800x600 (this is a 22" widescreen, so 1920x1080 is what it should handle (and did before I set hands on it).

So what now?  I sure don't want to have to reformat his drive to 9.04  He's been warned to back up his data, but invariably, this is a rough, at best, solution fraught with problems, in its middle of the upgrade jam.

Any advice welcome,

CDS

---

### Post by running_rabbit07 on 2009-08-08
> **Alabamian said:**
> Okay, there's a computer guy I'm in charge of who's having trouble printing.  I check it out, and sure enough, his Brother HL-5250 will not print.  I rebuilt things (it is plugged in directly USB to the CPU.  One of the peculiar things about the printing is that I couldn't get the new print driver to just say, a USB (or paralle) port.  It kept acting like it was a network printer.  I couldn't select lpt1: or usb or anything direct, only various IP address choices, as if for a networked queue.  I tried downloading drivers and everytime I tried to install a 64-bit version, it said I was running a 32-bit OS system.  u-name -a  clearly shws the box to be 64-bit.

So I decide, shoot, I myself had all kinds of printing troubles with Ubuntu 8.04, why don't I upgrade him?  Well, I tried to bring him up to date, but got a message that it couldn't, and it failed, so no upgrades over the Internet.

Then I make the Alternate 8.10 CD, figuring I should be able to get to 9.04 if I make it to 8.10  It autolaunches and tries to install, but I get a "Failed to add the CD" error.  Eventually, I also get "Not all updates can be installed" message, and a partial update option, which I've done.  The installer script said I wouldn't be able to use a proprietary Dell driver (the nVidia, stuff), and we're off.

Now the system defaults to 800x600 (this is a 22" widescreen, so 1920x1080 is what it should handle (and did before I set hands on it).

So what now?  I sure don't want to have to reformat his drive to 9.04  He's been warned to back up his data, but invariably, this is a rough, at best, solution fraught with problems, in its middle of the upgrade jam.

Any advice welcome,

CDS

To get the nvidia driver going, Got to the system menu and under prefereances I believe there is a selection for Display Drivers. Click on it and then activate one of the drivers listed. After it installs you will have to restart and then you will have your highquality graphics back.

If you want, you can back up files using the LiveCD and an external HDD or flash drive. Just copy and paste.

---

### Post by Alabamian on 2009-08-09
I fixed things, kind of.  I found that by following mayfer's advice ...

[http://ubuntuforums.org/showthread.php?t=488419](http://ubuntuforums.org/showthread.php?t=488419) 

... I was eventually able to get rid of enough bad stuff that the video worked and the upgrade proceeded.  Great.

Now I'm stuck in Brother HL-5250 hell.  I've read Brother's pages, but I still don't know how to get Ubuntu to restart cups.  I'm getting ready to restart my box now (I've tried sudo /etc/init.d/cupsys restart about 50 times)

Any advice on these horrible printers is appreciated.

---

### Post by Alabamian on 2009-08-11
Believe it or not, when I plugged the Brother laser printer into the network, I simply used the Ubuntu-supplied driver and it worked like a champ.  Yeah!

Now the final 2 bits of weirdness and I will consider this situation completely resolved.  On my own 9.04 install, when I check System -> Administration -> Services I find Printing Service (cups).  On my client's, I don't see it.  In fact, his printing situation requires he go to the terminal and type "sudo cupsd -l" to call up the cups daemon manually.  Why does mine seem to recognize it should be done automatically, yet my client's computer does not?  How can I make that option appear in the Services options?

Second, I upgraded him to Firefox 3.5.2  Great.  When at the command line, he'd type firefox and Firefox 3.02 would be launched.  When we went to the Synaptic Package Manager and removed firefox 3.0.2, typing firefox results in nothing.  If he types firefox-3.5, firefox 3.5.2 opens.  How can I make it so Ubuntu 9.04 will call Firefox 3.5.x and work when he types "firefox" at the command line?

Thanks ahead of time,

Alabamian

---


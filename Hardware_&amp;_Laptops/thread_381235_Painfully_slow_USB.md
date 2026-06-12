---
title: "Painfully slow USB"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by skip27 on 2007-03-10
Hi everyone,

I've been using Ubuntu for the past two weeks and love it... except for one problem--a big one, mind you. My iPod is transferring at painfully slow speeds. For as much as I hate Windows, this is the one thing where it has my current Linux setup beat and I'm stumped. 'usbtree' and catting out /proc/bus/usb/devices indicates that my iPod is running at 480M. I've mounted the thing using 'mount' and 'pmount' using every imaginable option but to no avail. Yes, I am using 'async' and that has not solved the issue. I have used Amarok and Gtkpod, both of which give me slow transfers. I've tried adding a user policy under hal (the one that's been suggested for SUSE in Google to force an asynchronous USB mount) but that did not work.

I'm getting really frustrated since this is something so basic. Re-inserting the EHCI module doesn't appear to help.

Why are USB transfers so slow in Ubuntu? I have to be doing something wrong... it can't possibly be Linux. Or can it? Please, I *really* could use some help here. Thanks!

---

### Post by skip27 on 2007-03-10
It is also worth noting that my transfers, when I *start* them, are incredibly fast as they should be. However, the speed decreases as the transfer continues. So, I know that my computer is capable of transferring at high speeds, but the question is whether or not there is a way to sustain the high speeds. Any help would be appreciated.

---

### Post by skip27 on 2007-03-10
I plugged in an old mp3 player that merely uses drag-and-drop for music transfers and I run into no problems. Is there anyone else who is disappointed with the transfer speeds between their PC and iPod? Is it just me? Is anyone having problems with USB transfers in general? I'm getting so many conflicting findings that it's hard to know where to find the problem. It *seems* to be this iPod, which makes me regret purchasing it to begin with... if only I hadn't been so willing to acquiesce to Apple's proprietary format...

---

### Post by martinquested on 2007-03-12
I am having problems too.  Not with an ipod, just an ordinary old mp3 player.  Transferring *from* the device takes hours, literally.  It's a breeze in XP.  I can't work out why, and I too have tried the things you already mention.

---

### Post by truant on 2007-04-08
I'm getting this too, with my 4G/20GB iPod under Amarok in Gnome (Feisty).  Can't, yet, figure out what's going wrong.  I regularly transfer hundreds of MB from my camera through the same USB hole with no problems.

The only thing that seems a bit awry so far is this, in the syslog:

```
Apr  8 20:42:10 lumiere kernel: [95656.937860] Info fld=0x0
Apr  8 20:42:23 lumiere kernel: [95663.844302] sdb: Current: sense key: No Sense
Apr  8 20:42:23 lumiere kernel: [95663.844309]     Additional sense: No additional sense information
Apr  8 20:42:23 lumiere kernel: [95663.844314] Info fld=0x0

```

No sense!  uh-oh!  Although a bit of Google Searching(TM) suggests this means [all is well](http://www.seagate.com/support/kb/disc/scsi_sense_keys.html) in the world of scsi..

Occasionally amarok's window will dim, as if it's busy, but it's cpu/memory load doesn't change.  The syslog messages appear sporadically, and don't appear to coincide with anything happening - like a track transfer ending, or one of the (very rare) flurries of transfer when four or five tracks will be transferred in a few seconds.

When I get the chance, I'm going to dig out my Firewire cable, see if that's any better.

[edit, a bit later on]  Dammit.  Now the iPod is no longer mounted (although it still thinks it is) and the syslog is full of:

```
Apr  8 21:07:04 lumiere kernel: [96423.106834] sd 12:0:0:0: rejecting I/O to offline device
Apr  8 21:07:04 lumiere kernel: [96423.106841] sd 12:0:0:0: rejecting I/O to offline device

```

This isn't cool.

---

### Post by intel352 on 2007-04-08
i'm having similar issues. i have a 4g/20gb Ipod, browsing the ipod directly so that i can transfer large backup files to Ubuntu (Feisty). these files transfer to/from the ipod in XP lightning fast, yet in Ubuntu, the "estimated time" for around 1.5gb went from 30 minutes to 4+ hours, and is still rising...

This is ridiculous. Help?

---

### Post by truant on 2007-04-08
First, good news - found the firewire cable, all is well - blistering transfer speeds.  At least there is a workaround, if you've got the ports.

Bad news - appears to be some pretty low-level instability using iPod+USB cable, it's not just Amarok.  Writing files using nautilus or even a shell is unreliably and may cause iPod failure.  After a bad unmounting, mine wouldn't even reboot and show the "broken - got to apple.com/support/ipod" message.  Partition table was utterly trashed, somehow.  I had to mkfs.vfat it and reinstall the firmware through iTunes (the ONLY time I've had to boot into windows in years - dammit).  

Then, I tried (and failed) to install ipodlinux and/or rockbox, both from Windows and Ubuntu - both of which require the use of USB rather than FW.  Both failed due to I/O problems.  iPod looking very bad, still not booting, or even capable of Disk Mode.  Formatted again, restored using firewire cable.  Back in Ubuntu, Amarok seems happy.

---

### Post by martinquested on 2007-04-09
Oh dear, that sounds bad.  Hope you manage to fix it completely...

---

### Post by truant on 2007-04-09
oh, it's fine now, thanks.  it's pretty hard to totally paperweight an iPod short of hardware failure - iTunes will restore it from a completely blanked disc (which is easy enough to do under linux, Windows seems less happy about formatting).

---

### Post by martinquested on 2007-04-09
Good.

My own solution to the problem has been with a different mp3 player.  I bought the new player for different reasons than the USB, but by happy coincidence I've just discovered that it works super-fast under ubuntu.

Incidentally, it is doing this using the cable which was supplied with the other, problematic mp3 player.  When I used the new player's own cable on Saturday it wouldn't work at all unless I removed the usb 2.0 module from the kernel, by typing sudo rmmod ehci_hcd  ... I don't have the proper cable with me today so I can't test whether it works now as well.

Anyway, so I'm happy.

---


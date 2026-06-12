---
title: "Installation problems on netbook."
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by dtkiyoshi on 2009-07-25
Hey guys.  Complete noob here.  I've been trying to install ubuntu on my netbook - after not being able to mount a disk image in unetbootin or win diskimager32, I got an ISO of Jaunty Jackalope (instead of the netbook remix which I was trying to use), mounted it, and copied the files to my external drive.  That seemed to work, as the drive now acted as a cd would.  So I rebooted the computer, and I went to select to boot from that drive.

Then, I got an "NTLDR is missing, press ctr-alt-delete" error.  So I googled a bit, read that I should try to activate the drive, went into the windows command line, activated the drive, and rebooted.  Again, I chose to boot from the external drive, and again, I got the NTLDR error.

What is going on here?

---

### Post by blazemore on 2009-07-25
You need to
1) Burn the ISO to a CD, and boot from an external CD-rom drive
2) Make a bootable USB flash drive using unetbootin

What netbook is it?
If it's an eeePC, try [http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)
It it's an Aspire One, try [www.kuki.me](www.kuki.me)

Oh, and don't post it on Digg, that's just lame.

---

### Post by nobaloney on 2009-07-26
> **blazemore said:**
> What netbook is it?
If it's an eeePC, try [http://www.geteasypeasy.com/](http://www.geteasypeasy.com/)
I'd like to use the official 9.04 netbook remix but my eeePC 1000 won't boot from the USB stick, it just ignores it (yes, I've tried settings in the BIOS, etc.). There's nothing wrong with it, a friend's eeePC 901 can boot from it.

Sure I should try to figure out the reason why, but I'd rather boot from a CD (tested with old Knoppix boot cd; that works).  How can i get an ISO of the 9.04 netbook remix?

Thanks.

Jeff

---

### Post by nobaloney on 2009-07-26
Ive tried easypeasy. I downloaded an ISO, put it on a DVD, and plugged in my DVD player to the USB port.  It worked; I was able to run it on the live CD.

But it always pops up that Network-Manager has failed, and I can't find any other programs with the name "network" in them to try starting (# find / -name *network*).

So how do I get an ubuntu varient (preferably the official one) started on my eeePC 1000?  Anyone?

Jeff

---

### Post by 00b00nt00 on 2009-07-30
Have you tried making an image of the netbook remix following the steps on this page?

[https://wiki.ubuntu.com/UNR/Installation/Easy](https://wiki.ubuntu.com/UNR/Installation/Easy)

I couldn't get regular Ubuntu to install on my netbook, but UNR works like a charm, even though the Atom is even more feeble than I had imagined.

---

### Post by Katalog on 2009-07-30
> **00b00nt00 said:**
> Have you tried making an image of the netbook remix following the steps on this page?

[https://wiki.ubuntu.com/UNR/Installation/Easy](https://wiki.ubuntu.com/UNR/Installation/Easy)

I couldn't get regular Ubuntu to install on my netbook, but UNR works like a charm, even though the Atom is even more feeble than I had imagined.

Using that method worked fine for me as well, and I have two Eee PC (901 and 1000HA). After making the bootable USB drive, I pressed the ESC key at the boot up screen, selected the flash drive as the boot device and away I went. Couldn't have been easier.

---


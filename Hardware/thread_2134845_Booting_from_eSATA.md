---
title: "Booting from eSATA?"
date: 2013-04-12
forum: Hardware
---

### Post by qyot27 on 2013-04-12
When my parents decided to get rid of their old iMac, I took the hard drive out with the hope that I can use it as a dedicated hard drive for my Ubuntu install.  I first wanted to put the drive directly into the case, but unfortunately I don't think that's an option due to the internal configuration - the response I got from one of the local computer shops when I showed them a picture of the inside of the case was that I'd have to get creative to fit another drive in it (read: making custom brackets to either mount it behind the existing drive or mount it to the floor of the case, or taking out one of the optical drives and using a 5.25-to-3.5 bay converter).

So I'm reluctantly looking at enclosing it.  USB2.0's bandwidth is unsatisfactory because I want to boot and use Ubuntu from the drive, and because of my computer's age, there is no native ability to boot from USB.  plop is too flaky to be reliable here, and while I've looked at using grub2 to boot it directly, I'd still have to deal with that bandwidth issue.

To that end, I'm contemplating the idea of taking the ethernet card out of one of the PCI ports, and replacing it with a USB2.0 wireless network adapter I can plug into my USB hub.  This would leave me with room for a PCI SATA card with eSATA port that I could use to connect the hard drive in an external enclosure.  From what I've read, there's very little difference in speed between internal SATA and eSATA, and since it's a 7200rpm drive, the disk transfer rate is just about equal to the bandwidth of the conventional PCI bus, so I shouldn't have to worry about the PCI bus causing a bottleneck.  Even if it does, it should still be better than the IDE/PATA speeds I get with my main drive, and definitely better than USB.


So, my actual question is: if I do this (assuming I get a wireless adapter Ubuntu is happy with), should I have to worry about my BIOS not seeing the eSATA enclosed drive, or is the presence of the card enough to let the drive be seen correctly?  Will grub2 have issues seeing it by default like USB, or will it see it as a regular hard drive and 'just work'?  If I don't have the enclosure turned on at boot time, will grub2 complain about not finding it?  It's not set to boot into Ubuntu by default, but if it has to see all partitions to continue booting into any OS, that would be a problem.

---

### Post by pfeiffep on 2013-04-12
> [COLOR=#000000] If I don't have the enclosure turned on at boot time, will grub2 complain about not finding it?[/COLOR]
While not exactly an answer my experience is that when I don't have my usb hard drive connected to laptop grub2 just presents all the options.

Good luck with booting to a device not supported by bios!

---

### Post by dabl on 2013-04-12
If that computer can't boot USB devices, the chance that it can boot e-SATA is about nil out of a million.  Custom brackets on the case floor is your path forward, IMHO.  If you can find a standard drive bracket for your 3.5" drive, just epoxy the bracket it in position, to avoid drilling holes and driving screws.  Use alcohol to clean the area where you're gluing it down, and it should work.

---

### Post by qyot27 on 2013-04-12
It would seem as though *some* expansion cards can get around this, because they ship their own BIOS which simply comes up as part of the normal startup sequence.  This was one that's reputed to have that capability that I found through searching on Google (it uses the L-shaped connector instead of eSATA, though; I guess that'd need an adapter cable):
[http://www.newegg.com/Product/Product.aspx?Item=16-132-009](http://www.newegg.com/Product/Product.aspx?Item=16-132-009)

This is untested waters for me, though, so I'm still trying to weigh the options.

---

### Post by efflandt on 2013-04-12
If you decide to find a place to attach it in the computer case in a non-standard location, I would use double stick foam tape instead of epoxy. We used something like that (servo tape) to mount servos in RC vehicles. But big box stores like Home Depot have assorted double stick foam tape that can hold anywhere from 5 lbs to maybe 20 lbs(?).

I looked at this thread initially because I was curious if it is normally possible to boot from eSata on a computer that came with an eSata port.  I got an eSata 2-drive caddy, but have not tried it yet.

---


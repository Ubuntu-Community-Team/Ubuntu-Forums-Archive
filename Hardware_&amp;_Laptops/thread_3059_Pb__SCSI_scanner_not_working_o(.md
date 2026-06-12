---
title: "Pb : SCSI scanner not working :o("
date: 2004-11-03
forum: Hardware &amp; Laptops
---

### Post by troutrou on 2004-11-03
Well, my SCSI scanner is not recognized by Sane it seems. When I launch XSane, all it sees is the TV card, but no scanner... :-/

I come from one year of trouble free Mandrake 9.2 where hardware detection was flawless and hassle free to say the least. Plus there is a tool with a GUI to detect  and configure scanners, in case it doesn't see it first time. So basically I really don't know what to do to get it working with Ubuntu.... no dedicated tool for scanners ! :o(

It's a SCSI AGFA Snapscan 1236

I searched this formum for "scsi" and "scanner" and the best I could find was this topic: [http://www.ubuntuforums.org/showthread.php?t=1966&highlight=scanner](http://www.ubuntuforums.org/showthread.php?t=1966&highlight=scanner)

I did everything that it says. Made sure that my user is a member of "scanner", then installed sane-util, did a "sane-find-scanner" but it returns that no SCSI scanner were found... :o(

However, I had a look at the "device manager" (see first screenshot) and it shows that the SCSI card/controller (Adaptec 2940) is detected, and uses the driver 'AIC-7861' which I think is what Mandrake also used so should work (?).
Then I can also see that there is a "device" detected on the SCSI bus, albeit with no proper name. So this means the scanner has been detected too, I guess.
Looking at the "advanced tab" for the scanner, it says it is "mounted" (forgive my ignorance) in '/sys/devices/pci...blah blah... /host 0... '
So I had a look in that directory and saw the following (see second screenshot). Basically a few tiny text files that contain the scanner brand (AGFA) then model (Snapscan 1236) and even the scanner position on the SCSI bus (position #3)

So, if Ubuntu managed to find all the relevant info about the scanner, how come Sane (or whatever is relevant here) doesn't catch this  ?? :o(

I had a look in Synaptic, and found a package that extends Sane's support to a few more scanners, but mine is not listed in the description of that package.

If a SCSI/scanner Guru understands something and can give me a hand, I would be soooo very grateful.  I just installed Ubuntu after 24 hours downloading it on dial-up, and love it, so I would rather make the effort to get everything working so as to move to Ubunto for good and forget Mandrake, which is hardly Gnome friendly to say the least ! :-/

Sorry for the long post, tried to be exhaustive so as to expose the situation clearly (I hope).

Regards,

Vince

[IMG]http://www.007.org.uk/~vtrouilliez/scanner.jpg[/IMG] 

[IMG]http://www.007.org.uk/~vtrouilliez/scanner_2.jpg[/IMG]

---

### Post by tjm on 2005-11-16
I have exactly the same problem with a beige Apple G3 333 MhZ Minitower connnected to the AGFA 1236s.

I have a TEAC external SCSI CD-Writer that works fine with K3B and is on the same bus than the AGFA scanner. So it cannot be a problem related to bus detection.

It's really ugly because if the Scanner would work in Ubuntu 5.10 PPC I could get rid of the slowmo Mac OS 9 that I have to use for scanning still.

Who knows a solution?

---

### Post by tjm on 2005-11-16
Let's give this a try:
[URL="http://snapscan.sourceforge.net/"]
http://snapscan.sourceforge.net/[/URL]

---


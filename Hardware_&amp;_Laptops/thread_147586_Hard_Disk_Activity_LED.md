---
title: "Hard Disk Activity LED"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by j-a-p on 2006-03-20
I have two hard IDE disks connected as master and slave on the primary IDE channel.  I also have 2 optical IDE drives connected as master and slave on the secondary IDE channel.

My problem is that the LED for the hard disks (primary channel) indicates no activity, but for the optical drives (secondary channel) it does.  Everthing works fine apart from this, the drives perform as expected etc.

Please assist.

---

### Post by mjwood0 on 2006-03-20
This is really dependent on the Motherboard as that's where the output for the LEDs comes from.

My Motherboard just has a HD activity led output.  It's lit whenever ANY drive activity is present (Pri IDE, Sec IDE and even SATA).

---

### Post by aggiechemist on 2006-03-20
If you are comfortable with this sort of thing, open up the case. I can't tell if you are a total noob or ultra leet, so sorry if that sounds basic.

I would just trace the leads. I've seen this thing before, and for me it was always a bent pin or a loose connection or I once switched the LED connectors for the power light and hard drive light. If you have a motherboard manual, that is a huge help to make sure you're plugged in the right spot.

---

### Post by PowerWCRulez on 2006-03-20
If you use a tower case, you could get other HD faceplate with a brackets with a LED, I have old HD faceplate brackets with a LED good for secondary drives (Drive E or F), you can find at surplus junk computer stores and look for the HD faceplate bracket with a LED. Or you can do get a wire with a LED, you can do modding the tower case for make a 2nd hole for secondary drive HD LED or even modding faceplate make new hole for HD LED. I still have old HD LED wires in my storage for modding a PC case.

:)

---

### Post by j-a-p on 2006-03-20
I'm not a linux expert, but I'm not a complete muppet either.

Thanks for all the input folks.  The case only has one LED for all drives.  There is only one connection on the M/B for the LED.  The polarity is correct for the diode (checked with multimeter).  As I said it works for the secondary IDE channel drives.  It worked when I used Fedora Core 4 and my hardware config (physical) has not been changed for the change over to Ubuntu (Breezy).

---

### Post by mjwood0 on 2006-03-20
From my understanding, the wires coming off the case LED going to the MB connect to the two terminals in the block of front panel connectors.

I don't believe this could be a wiring problem if the secondary IDE works.  And I really don't think this could be a Ubuntu problem as those pins which go to the light are physical traces in the Motherboard to the activity lines in the IDE connectors.  If the light doesn't blink, it seems like a Motherboard issue.  The other option is that the cables used to attach the primary devices is defective and not transmitting the signal to the Motherboard.

Try swapping cables for the primary and secondary IDE.  Perhaps that will clear things up?

Just my $0.02

---

### Post by j-a-p on 2006-03-20
Thanks, but I have tried that.  It is surely an Ubuntu issue since all was well during Fedora Core 4 use.  It is definately not a wiring or hardware physical config issue.

---


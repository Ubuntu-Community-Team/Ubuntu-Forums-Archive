---
title: "How can I get eSATA hotplugging &amp; S.M.A.R.T. to work?"
date: 2010-09-15
forum: Hardware
---

### Post by Objekt on 2010-09-15
My motherboard (listed in sig) has two eSATA ports, but I can't get them to support either plugging in or disconnecting an external drive while the system is powered on, which is what I would call "hotplugging."  What gives?

I do have the SATA controller set to AHCI mode in the system BIOS.  Ubuntu 9.10 has no problem booting with the controller in either AHCI or Legacy (IDE-like) mode.  But my external HDD still does not show up when I plug it in via eSATA.  The drive also has a USB connection, or I wouldn't be able to use it at all.

Is there a big secret for getting eSATA to support hotplugging, as it's supposed to?  Or does my SATA controller have a crappy chipset that is not actually capable of supporting all the eSATA features?

I also noticed that I can't get SMART monitoring information on my internal hard drives through Ubuntu's "Disk Utility" application.  Shouldn't AHCI mode enable SMART monitoring features?  All my hard drives are either SATA 1.5 Gb/s or SATA 2 (3.0 Gb/s), so I would assume they support SMART features.  I know I have had them report info before.

---

### Post by cascade9 on 2010-09-16
> **Objekt said:**
> My motherboard (listed in sig) has two eSATA ports, but I can't get them to support either plugging in or disconnecting an external drive while the system is powered on, which is what I would call "hotplugging."  What gives?

I do have the SATA controller set to AHCI mode in the system BIOS.  Ubuntu 9.10 has no problem booting with the controller in either AHCI or Legacy (IDE-like) mode.  But my external HDD still does not show up when I plug it in via eSATA.  The drive also has a USB connection, or I wouldn't be able to use it at all.

Is there a big secret for getting eSATA to support hotplugging, as it's supposed to?  Or does my SATA controller have a crappy chipset that is not actually capable of supporting all the eSATA features?

That5 board uses a %&^#&%# Marvell 88SE61xx for the eSATA ports. From what I can see here, it needs a driver for eSATA hotpluging to work-

[http://www.evga.com/forums/tm.aspx?m=466734](http://www.evga.com/forums/tm.aspx?m=466734)

Being marvel, there is sod-all chance of there being drivers you can install to get eSATA hotpluging.  

Ironicly, you would probably have better luck with the onboard intel SATA controller. I cant be 100% sure that is will work, but the chances are much, much better than for any marvel SATA controller. 

ACHI wont automatically turn on SMART. You normal have to do that for  the individual drives....er....somehwere in the BIOS. Sorry I cant be  more exact on that, but exactly where SMART gets turned on can vary.

---

### Post by Objekt on 2010-09-16
I see, once again Marvell is synonymous with "crap."  I freaking HATE hardware that requires Windows-only drivers to work.  Winprinters are bad enough, but Win-disk controllers are even worse.

You're on to something, regarding the Intel SATA controller.  I had an adapter which turns a SATA connector into an eSATA port.  I connected this adapter to the Intel controller to give an eSATA port not tied to the Marvell controller.  No surprise - it works!  I can hotplug the external drive through that eSATA port, because the Intel SATA controller actually meets the SATA specs without a damned Windows driver.

I still can't figure out what the deal is with S.M.A.R.T. monitoring.  I know I've gotten it to work before, but I have no idea how.  SMART is definitely enabled in BIOS, it's just not working once Ubuntu boots.

---

### Post by cascade9 on 2010-09-16
> **Objekt said:**
> I see, once again Marvell is synonymous with "crap."  I freaking HATE hardware that requires Windows-only drivers to work.  Winprinters are bad enough, but Win-disk controllers are even worse.

+1. 

I think what annoys my more than marvel (et al) making those useless controllers, its hardware manufacturers putting them on motherboards. For them, I spose, its an easy and very cheap way of 'making the numbers look better', and when lots of consumers buy 'on specifications' thats a win-win for them. I'd just much prefer it is they put good controllers on the motherboards, or not bother at all. 

I guessed that the intel controller would work, while I'm not intels biggest fan, they tend to follow specifications. 

Sorry that I cant help with SMART, but you win some, and you...er......wait till somebody who actually knows whats wrong comes along. :)

---

### Post by Objekt on 2010-09-17
I still haven't a clue what's blocking the S.M.A.R.T. monitoring.  It's specifically turned *on* in BIOS, so I don't see what else I can do to make it work.  

Windows-dependent hardware caused me big sound headaches under Ubuntu for almost a year.  The crappy onboard sound device (Analog Devices something-or-other) not only wasn't properly supported under Ubuntu, it actually interfered with use of my SoundBlaster Audigy card (which does work properly under Ubuntu, thanks to Creative Labs not being total douches about it).  I had latency, echoing, garbling, and sound not-working-at-all problems which I simply couldn't solve, even though I was telling PulseAudio to use the SoundBlaster instead of the motherboard device.

The solution was, it turned out, to disable the onboard piece of junk in BIOS.  Ever since I did that, I have had zero sound problems.

Unfortunately, there are a lot of PC owners who have only the built-in sound devices.  I suspect that the continued use of crippled, Windows-driver-dependent, onboard sound devices causes at least 75% of the reported problems with sound under Linux.

Manufacturers who even think about using a half-assed, Windows-dependent device on a motherboard need a beating.  Especially on a motherboard like mine.  It was quite expensive at the time (nearly $300) and supposedly "workstation" grade - it's in the name, even.  Turned out it was only the former.

---

### Post by dougalkerr on 2010-09-17
Don't know if this helps but, I spent over a day and after a few posts and replies I was no further ahead.
My laptop would not activate the eSata disk when I plugged it in. The system could see it but, I couldn't use it nor do anything with GParted...

As a last resort I plugged it into my wife's Windows Vista system which picked it up straight away just as Linux did but, again I couldn't do anything with. Panic set in for just a few milliseconds till I noticed the option to Initialize the disk - I did. I formatted it to Fat32 and took it to my Linux box.

Hey presto everything works. I reformatted to Fat32 again as I am using the disk for storing fotos and will be sharing between different operating systems.

Anyway - have you initialized the disk/s???

I don't know how to do it in Linux but, I am sure going to find out before my next disk purchase.

Good luck.

---

### Post by Objekt on 2010-09-19
It appears that the lack of SMART info in Palimpsest is a commonly-encountered error.  It is a problem with Palimpsest (labeled just "Disk Utility" under System menu->Administration), rather than with anyone's hardware.  Somehow, an update earlier this year broke Palimpsest for a lot of folks, with respect to SMART monitoring.  So Palimpsest erroneously reports that SMART monitoring is "not available," even though people have it turned on in BIOS.

That agreess with what I remember, which is that Palimpsest had no problems when I began using Ubuntu heavily late last year, but now doesn't show SMART information.

Here's a thread on the topic, where a few solutions were found:

[http://ubuntuforums.org/showthread.php?t=1439140&page=3]("http://ubuntuforums.org/showthread.php?t=1439140&page=3")

I installed the GSmart utility, and, as suggested in that thread, it works.  There's oodles of information available for every drive.  I've had an uneasy feeling about one of my 1 TB drives lately, so it's nice to have the extra info SMART monitoring provides.

I also tried the code fix explained in the thread.  That caused Palimpsest to start displaying SMART info again.

---


---
title: "How to power up machine automatically when power supply is present."
date: 2011-09-22
forum: Hardware
---

### Post by cobraun85 on 2011-09-22
I have Lubuntu 10.04 installed on a WalkAbout Hammerhead XRT.  It will be mounted onto an ATV with an attached GPS.  The power supply for both the computer and the GPS are attached to the ATVs battery and controlled by a simple toggle switch.  I won't be the one using this equipment in the field; there are about 20 other considerably less tech savvy grunts who will be using it, so I'm trying to make this as user friendly as possible.

As it is now, the computer must be turned on by a difficult to reach power button.  I wrote a daemon to monitor the presence of a power supply and to shut the machine down when one is not detected.  That works perfectly and virtually eliminates the possibility of sudden power loss, but this causes the machine to shut down properly.  And that means the BIOS setting that would turn the machine back on after a power failure won't work.

Is there a way to fool the computer into thinking it experienced a power failure so that the BIOS would start the computer automatically when power is reapplied?

---

### Post by SteveDee on 2011-09-23
> **cobraun85 said:**
> ...is there a way to fool the computer into thinking it experienced a power failure so that the BIOS would start the computer automatically when power is reapplied?

I don't know anything about the equipment you describe, so my comments may not be useful in your case......but, if your computer is essentially atx (with a push button to provide a pulse to start) and you are able to get access to the switch contacts, you could solder a 10uF capacitor across it. When power is applied this looks like a short duration short circuit, thereby simulating the button being pressed.

You sound like a teckie however, DO NOT do this if you have no experience of electronics or soldering....and don't bug me if you break something!

---

### Post by cobraun85 on 2011-10-05
SteveDee,

I am a bit of a techie, but I don't have the steadiest hands so soldering isn't my strongest skill.  I'll soon have a whole pallet full of these Hammerheads, though, so I might give this a shot on one of them.  I'll let you know how it goes if I do.

---

### Post by SteveDee on 2011-10-05
> **cobraun85 said:**
> SteveDee,

I am a bit of a techie, but I don't have the steadiest hands...

The degree of difficulty will rise as the component size falls (i.e. more difficult to do this on a laptop than a desktop).

Having just Googled "hammerhead pc" I can see its going to be tricky, especially with a nicely sealed IP67 enclosure.

But if you do have a go, remember to check polarity while the pc is running by clipping a voltmeter across the power switch. This will determine where to attach the "+" lead of the capacitor.

You may also be able to use a smaller value capacitor (and consequently smaller in size) if space is a problem, but you will need to experiment. Good luck!

---


---
title: "High pitch sound from onboard VIA sound card"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by berlinbrown on 2008-02-02
I have my sound working...sort of.  I am getting a high pitch sound whenever there is sound output.  It is a cheap onboard card, I wouldn't use it, except I am running out of PCI slots.

HDA VIA VT82xx.

I have kind of a higher end bass speakers.  Maybe that is effecting it?

---

### Post by berlinbrown on 2008-02-02
Oh yea...ASUS!!!! QUIT PUSHING THESE stupid VIA onboard graphics, tcp-ip, audio devices on us.  They always suck, they never work on linux.  They are complete waste of time.

And then you give us 2-3 PCI slots.

It drives me nuts.

---

### Post by oldsoundguy on 2008-02-02
then why buy the board?  There ARE other choices! (such as MSI or even Intel)

On your sound ... it is feeding back (microphone hooked up or plugged into the wrong jack?) or you are overdriving the crud out of that on board chip.

---

### Post by berlinbrown on 2008-02-02
RIght jack and I am just running the test sounds in ubuntu.

On asus, I am not partial to them, but I thought they were good?

---

### Post by oldsoundguy on 2008-02-02
Ubuntu has a master volume control ... upper right on the desktop next to the date.  turn it down.  And check to MAKE SURE your speakers are plugged into the correct jack on the rear.

---

### Post by Rui Pais on 2008-02-04
Hi,
same happen to me (and i read thats quite common and even happen sometimes under Windows...)

I just needed to add correct options from my sound card at file
/etc/modprobe.d/alsa-base

(In my case i need to add "options snd-hda-intel model=3stack position_fix=2" to get ridden of the high pitch...)

---


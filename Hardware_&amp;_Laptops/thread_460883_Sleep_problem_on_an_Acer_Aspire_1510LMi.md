---
title: "Sleep problem on an Acer Aspire 1510LMi"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by masterthor on 2007-06-01
While trying to test every feature of my machine for the LaptopTestTeam and also personal use, i've noticed that sleep and hibernate won't work on my laptop.

The symptoms are: 

-sleep : shows some messages in console mode about going to sleep, then the display shows all sorts of colors and  lines, and after a second or two it enters the sleep state. When pressing any key, i again get some sleep messages in console mode (no errors though), and then the screen blanks with the backlight still on, and the hard drive led blinking from time to time. In this state nothing short of a hard shutdown seems to work: mouse, keyboard, closing the lid does nothing.

-hibernate : it seems to shutdown and save the data correctly (i can't tell because i don't know where to look) but when resuming i again get a blank screen, and a flashing power led. 

Linux thor-laptop 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux

dmesg and "lspci -vvnn" output attached. 

I'm sure i've seen similar symptoms but i can't seem to find them again, and any help would be very apreciated, as i don't want to post this as a bug, because i'm sure there is a solution somewhere somehow.

Thanks!

---

### Post by michael.conner on 2007-06-01
This might sound bizarre, but when it comes back up with the blank screen, hit the "Esc" (escape) key.  I have an Acer Aspire 5100, that's how I get mine to come back from sleep and hibernate.

---

### Post by masterthor on 2007-06-02
Unfortunately pressing the Esc key has no effect, nor do other keys, (even Caps lock does not turn on the led on the panel). It just sits with the black screen, eating up CPU cycles ( i know this by the sound of my noisy CPU cooler) with hard drive led blinking from time to time.

One thing is strange though: if I am to play some media file while putting it to sleep, like an mp3 or something, on waking up, while on that blank screen, the media seems to continue playing, although with pauses, like 4-5 seconds playing, 2-3 seconds pause, and so on.

I guess the system isn't completely frozen, it just waits for some piece of hardware to recover and fails at it but still tries. Any ideea how can i find out witch part of the system is the problem? (a log or something)

Thanks

---


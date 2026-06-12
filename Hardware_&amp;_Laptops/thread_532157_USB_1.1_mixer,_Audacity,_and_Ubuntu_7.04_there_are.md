---
title: "USB 1.1 mixer, Audacity, and Ubuntu 7.04: there are clicks all over my recordings"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by Brendo613 on 2007-08-22
I'm using a Compaq N1015v, with an Alesis multi mix 16.  There are random clicks all over the recordings I make, at different intervals.  The mixer only allows for a stereo USB out (boo), but I'm glad I didn't opt for the 16 track firewire mixer straight up, seeing how much trouble I'm running into with the stereo mix ...

Today I tried some new tweaks.  I do have DMA enabled, and am recording straight to the hard drive. I get fewer clicks recording mono, but they still exist and sound bad.  I've done recordings with 8 mics plugged in at once during a jam and received clicks, but for testing purposes I'm plugging a guitar straight in to a channel with a built-in preamp.  My sample rate is at 44.1khz, and I'm using 16 bit depth.  I disabled auto-scroll while playing, and I disabled software playthrough.  I even gave highest priority to Audacity through "sudo nice -n -20 audacity".

I'm now looking into speeding up the latency of the USB drive ... I stumbled across a forum page yesterday discussing this, and I recall someone talking about how they changed the latency of their USB drive to >20ms.  I could use something like that ... does anyone know how to do this, or have any other suggestions?

Thank you very much in advance.

=Brendan

---

### Post by Brendo613 on 2007-08-22
If I use a lower kilohertz rating, like 16k, it doesn't have clicks ... so how do I make it okay at higher khz ratings?

=Brendan

---

### Post by fredj on 2007-08-23
Ubuntu is a general purpose operating system so in its basic form it may not be good for sound
recording. The clicks you hear are caused by overruns i.e. the sound recording input failing to
supply sound at a fast enough rate.

However a tweaked Ubuntu can make a great sound recording system. Here is what you need
to do 
1. Install jackd and qjackctl
Jack is a sound server and is needed for all professional sound applications.
2. Configure Audacity so that it runs through Jack.
3. Run qjackctl and enter setup. Configure Jack so that it is using your usb mixers inputs
and so that it doesn't have any xruns (this will get rid of the glitches in the sound).
Start Jack first through qjackctl and then audacity

4. To carry this a stage further
5. Read the Multimedia Production forum
6. Install the Realtime kernel
7. Apply the realtime tweaks to the limits.conf file
8. Run Jackd in Realtime mode to get a low latency.

---

### Post by Brendo613 on 2007-08-25
Well, I've  been messing around with Jack, but am having no luck figuring out how to use it, really.  It's not exactly as self-explanatory as I was hoping, so I went online to try and find some sort of manual or tutorial ... no luck :-\ any help on how to set this up with Audacity?  Where is that multimedia production forum, and how do I go about getting the realtime kernel / realtime in Jack setup?
  I really don't know anything about it other than what's on this page.

Thanks again.

=Brendan

---


---
title: "Shutdown Ubuntu via USB/RS232 Connection"
date: 2013-09-30
forum: Hardware
---

### Post by i4-rs-t3 on 2013-09-30
Hi all,

I have an ubuntu server that is connected with other computers to the same mains. All systems are connected via USB with the main powersuplly. When the main system shuts down all system get the signal to shut down as well.
That works well on the one windows7 system also connected but my ubuntu server asks me "Do want to shutdown...." screen on the X window.
The problem is that I want my server to be headless. When I try it headless nothing happens, no logs nothing.

I tried to find out what kind of information is transmitted to make the systems shutdown, but I did not succeed so far.
I was playing around with APCUPSD, but no success.

When I press the power button, the system shuts down, can that be triggered via Serial/USB connection?
Any ideas where I should search? Why does it work (at least asking me) on X but not headless?

Any help appreaciated!

Thanks

raise

---

### Post by tgalati4 on 2013-10-01
I have an APC SMARTUPS on one of my servers and dumb or non-apc ups on my other machines.  I set the server with the smart ups to send out a signal to the other machines to shut down via ethernet.  It seems to work.  It requires setting the server apcupsd configuration to act as a "shutdown server" (also known as "master") and set the apcupsd on the other machines to "slave" mode.  These slave machines listen to a specific TCP port for the shutdown signal from the master.  This then turns off all machines on the network when the power goes out.  You can fiddle with the shutdown times and on-battery times to stagger the shutdowns so that the master stays up long enough to keep sending the shutdown signal to all slaves.  If the master shuts down too quickly, then the slaves don't get the signal. That is the tricky part of this configuration.

If you allow the master to stay on battery for 5 minutes (make sure your battery is up to the task), then all of the slaves should receive several shutdown signals.

The fact that you are running an X server on your headless server may interfere with this process.  Especially if a pop-up dialog requires a confirmation.  That's hard to get around on a headless system.  Perhaps there is a desktop preferences setting to turn off the shutdown confirmation.

I'm running 9.04 on this laptop at the moment and there is a setting on the Power Management Preferences (General Tab).  "When Power Button is Pressed"  Ask me or Shutdown.

---

### Post by i4-rs-t3 on 2013-10-02
thanks for your answer, I solved my problem using NUT [http://www.networkupstools.org/](http://www.networkupstools.org/)

Thanks

---


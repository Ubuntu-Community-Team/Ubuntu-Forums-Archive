---
title: "Ubuntu/gnome compatible UPS shutdown software with GUI"
date: 2008-06-23
forum: Hardware
---

### Post by wpshooter on 2008-06-23
Has anyone yet written a Ubuntu compatible UPS shutdown software with a GUI (that is on par with the features/functions that can be performed in their counterpart M/S versions of this same software) ?   And I am looking for something much better than the rudimentary APCUPSD program !!!

Thanks.

---

### Post by andrewbrown22 on 2008-07-12
I, too, am looking for something similar.  I'm having a hard time understanding and getting apcupsd working...

---

### Post by wpshooter on 2008-07-13
> **andrewbrown22 said:**
> I, too, am looking for something similar.  I'm having a hard time understanding and getting apcupsd working...

Andrew:

If your experience is like mine, then you are probably just wasting your time trying to get any meaningful performance out of that APCUPSD program.

I have recently acquired a UPS from Tripplite.  The manufacturer has been telling me that it is capable of having a GUI for doing a timed graceful system shutdown after an AC power loss.

The current model that they have that is supposed to do this is utilizing a serial interface for the communications between the UPS and the computer.  They say that they are working on a USB model which is supposed to come to market in 3 to 6 months.

So far, I have not been able to get the PowerAlert software on the model that I have to install because a certain version of JAVA has to be installed prior to the PowerAlert software being installed and I am having some difficulties, in that, the version of JAVA that is being offer by Ubuntu Synaptic and the version that is being offer by the SUN-JAVA website neither seem to satisfy the installation requirement needs of the PowerAlert software.  I am currently trying to get some answers from both Tripplite and SUN-JAVA to see if I can resolve this problem.  As you might guess, it is like pulling teeth to get any meaning discourse going with these companies, and like always, especially so when it has anything related to a non-M/S operating system.

Somebody really needs to come up with some solutions to the fact that you have to reinvent the wheel almost to get a UPS with a useable GUI shutdown software to work on a Ubuntu machine.

Good luck.

---

### Post by andrewbrown22 on 2008-07-13
I have an APC ES 750 with USB interface. I just wish that there was a UPS program with a decent GUI so that I could easily set up this scenario:
I have two computers on this unit, my desktop and my server, both of which I leave powered on at most times.  If, in the event of a power failure, after 5 minutes running on battery, I'd like it to shut down both computers. That's basically all that I need, but I can't seem to get it working with APCUPSD although I am sure it is possible, it is difficult for me to understand...

---

### Post by wpshooter on 2008-07-13
> **andrewbrown22 said:**
> I have an APC ES 750 with USB interface. I just wish that there was a UPS program with a decent GUI so that I could easily set up this scenario:
I have two computers on this unit, my desktop and my server, both of which I leave powered on at most times.  If, in the event of a power failure, after 5 minutes running on battery, I'd like it to shut down both computers. That's basically all that I need, but I can't seem to get it working with APCUPSD although I am sure it is possible, it is difficult for me to understand...

Andrew:

I am not sure that what you are trying to do is possible with APCUPSD.

I have 1 APC also and when I tried to do what you are doing and then when I performed the test via unplugging the UPS from the wall socket, the computer just shutdown immediately instead of waiting the time period for which I had attempted to setup in APCUPSD.  I think APC or some other UPS company really needs to write some shutdown software for use on Ubuntu.  If and when they do they are going to sell a ton of UPS units.

---

### Post by andrewbrown22 on 2008-07-13
Yes they will. I'll buy more. I'd like to have one in my entertainment center for my TV, XBOX and Wii. The power goes out for short periods of time in this city (recently moved here) and the UPS on my computers works good at keeping them up for a bit, but after 5 minutes I'd really like for it to shut them both down. I understand that I probably won't get quite that functionality, but if I could just get it to shut down the one with the USB cable plugged in I'd be happy. I could get an additional small UPS to keep the other computer powered.

---


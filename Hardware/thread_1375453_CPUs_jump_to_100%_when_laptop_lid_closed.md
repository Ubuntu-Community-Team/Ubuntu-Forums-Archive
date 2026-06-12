---
title: "CPUs jump to 100% when laptop lid closed"
date: 2010-01-07
forum: Hardware
---

### Post by Thomar on 2010-01-07
How's this for crazy?

I'm using an Aspire One AOD250, current version of non-remixed Ubuntu.  I'm using an external monitor (because it's a netbook.)

When I close my laptop's lid, both of my CPUs jump from 50-70% to 100%, thanks to two processes named "kapcid" and "kacpi_notify" and If I leave it like that for an extended period of time, the system will get more and more laggy and eventually do a slow freeze/crash.  Opening the lid puts the CPUs back to normal, but I haven't tested if it will keep the system from crashing yet.

I have Power Management set to blank the screen for both battery and AC power.

I originally thought it was overheating, but now I've realized it's directly tied to this lid thing, which is pathetic and anticlimactic.

I've heard that kapci is a laptop power management process that is unstable, but I've also heard that disabling it would turn off one of my CPUs.  Any good solutions that will let me close my laptop's lid?

Also, is this a problem I should submit to Canonical?  Or does it have to do with the kapci processes?

---

### Post by Thomar on 2010-01-08
Ugh, I just found out that the same thing happens in Windows.  I guess I'll have to look for an answer somewhere else.

---

### Post by Thomar on 2010-01-08
Ah, found a fix!

Apparently it's a BIOS issue common to Acer Aspire netbooks.  The internal lid switch keeps repeatedly sending a "closed" message to the OS, which bogs down the processor.  A simple BIOS update will fix the problem.

I'll explain it here for anyone who has a similar problem. (I did this dual-booting on Windows, I don't know if there's a good solution if you've wiped your Windows partition.)

1) Go to [http://support.acer.com/drivers_download.aspx](http://support.acer.com/drivers_download.aspx) and select your computer's model from the lists.
2) Click the BIOS tab on the table below.
3) Click the topmost orange download icon for the update (I was on 1.03, the current rev as of posting this is 1.25.).
4) Unzip the downloaded file to your hard drive, a folder on the desktop or in your C: drive will do.
5) Run the executable, THIS WILL REBOOT YOUR COMPUTER.  Don't turn off your computer while it's running the update, it'll probably brick it.  One reboot later, and it works just fine now!

---


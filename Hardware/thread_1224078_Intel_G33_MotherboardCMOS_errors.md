---
title: "Intel G33 Motherboard/CMOS errors"
date: 2009-07-27
forum: Hardware
---

### Post by Taylor13 on 2009-07-27
Hello Ubuntu World!  I would go on about how great Ubuntu is, but this is going to be a long post and I want people to actually read it.  I'll just say thanks for the hard work ; 

This isn't a specific linux question but my google-fu has failed me and I'm hoping some people here may shed some light on my issue.

I have a Gateway GT5628 that is running Ubuntu Jaunty 64bit.  Well it's mostly a GT5628, but I've replaced some things. 

Anyway, while adding the last few upgrades to the system I noticed that the system would power on for a second or so then off again when the power was plugged into the power supply.  I didn't think this was normal.  Booting after that was rewarded with checksum errors and Ubuntu forcing an fsck.

It seemed to work normally at first, subsequent reboots didn't get errors unless I unplugged it, but last time I transferred everything to a new case and replaced the power supply with a new one.  When I plugged everything in all the fans and lights came on for just a second when I plugged in the power supply but then went dead again.

Booting the system got me the same checksum errors but also an addition error message which I didn't write down. It did have to do with Intel's HECI interface, which manages the temperature and voltage sensors.  When I tried to view the hardware monitoring in the BIOS setup after that it wouldn't show at all.  

Other features were also missing.  Including my sound!  The on board sound card seemed to have just fallen off into nothing.  lspci showed it as a device but the alsa drivers couldn't find the codec to use in order to actually use it.

By it self, losing the on board sound isn't a huge deal, it prompted me to get my Creative X-Fi card working which sounds better anyway.  But my concern is that this issue could get worse, and I would like to know what's caused it.

I actually took the CMOS battery out and checked it to see if it was going bad.  It read 2.5V or so instead of 3V.  I suppose that could be some of the problem.

I've tried re-flashing the BIOS using Gateway's provided BIOS updates.  This failed at the same HECI related part and didn't seem to completely flash.  I had flashed it previously with a vanilla Intel bios for the board, and I now get undefined AA errors when it boots.

I'm really at a loss as to anything that could be done to fix it.  Should I be looking for a new board now?  Any ideas at all?

Thanks Much!

---


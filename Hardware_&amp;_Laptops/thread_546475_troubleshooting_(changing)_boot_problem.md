---
title: "troubleshooting (changing) boot problem"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by TravMan63 on 2007-09-08
My computer is having various boot/halt problems...

1st symptom - pc just halted - video was still up, no response to mouse or keyboard.
I was just typing and accessing dvd drive.

Since then - I have been able to boot - rarely - to the desktop...
Usually - the machine halts - in the cmos/bios startup - it does NOT pass post.
HOWEVER...sometimes it does -!  sometimes not - but it never runs on the desktop for over a minute or two)  Also -my keyboard does not allow me to chose an os...(dual boot) it works fine navigating cmos, and works if the machine boots, but not at the os choice screen.

There are no beep error codes (other than 'cmos settings are wrong' - this happened both before and after I removed the cmos battery (it is good)... and after I reset the cmos with the motherboard jumper.  (I have had issues - if I changed a HD -  without disabling it in the bios, that it would not boot).  The DVD drive light flashes 2x... and the HD busy light usually stays on. (pointing to a controller again?)  DVD will open and close.(I have previously had issues with the DVD drive - not wanting to read a CD's DVD's (that were or were not burned on it - changed cable etc -- but wondering - if I have a controller problem - which would be on the mobo... maybe this was an indication of a future complete failure?)  The cmos errors went away once they were set. (it lost all settings - time, HD configs, misc boot order etc...)

I have reinserted all cables and cards/memory.

The machine is clean (no dust) - and the temps and voltages when running seem fine
(about 20c for case, 30-40 for cpu (Athlon XP 1800+) - Soyo Dragon Kt-600 v2.0).
I monitor voltages, fan speeds, temps - and there was no problem at the time of the 1st failure)

I can always power down by holding in the power button... doesn't this indicate that the processor is running?  Interesting - on one halt - I had a dialog box open in the bios - the cursor was flashing - but the machine had halted...

I'm guessing - with these boot failures/lockups - and occurring at various points in the boot process... point to a failing device on the motherboard... perhaps a capacitor? (I don't see any bulging or leaking signs)...

but.... I'd like other opinions .... what do you think?

Thanks,
TM

---

### Post by TravMan63 on 2007-09-10
It was indeed a faulty motherboard.

I installed another (with same chipset - ViA KT-600 - from Chaintec (SKT-600) - replaced a SOYO KT-600 Dragon Plus v2.0.  The SOYO board had failed before - under warranty.

So - if you have any of these symptoms - it could vary well point to a faulty motherboard.


--
Comments:
I have XP Pro installed on this system, running Elive presently (live cd) - Microsoft does not support this method (artlicles also written by Intel) - state that problems may occur when replacing a motherboard - even if the chipset is the same.  Posts I have seen in this forum state that with Ubuntu - there may be problems with X.  I got lucky - no problems other than my ps-2 mouse and HD activity light (will recheck hookup)  not working, and finding 'new hardware' (that already existed --- but this can happen if you just change the (pci) slot the card is in.

--
Links:
[http://arstechnica.com/journals/hardware.ars/2007/09/04/how-to-install-a-new-motherboard-without-reinstalling-windows](http://arstechnica.com/journals/hardware.ars/2007/09/04/how-to-install-a-new-motherboard-without-reinstalling-windows)
[http://support.microsoft.com/default.aspx?scid=kb;en-us;824125](http://support.microsoft.com/default.aspx?scid=kb;en-us;824125)

---


---
title: "Wont Boot"
date: 2014-04-05
forum: Hardware
---

### Post by mayagrafix on 2014-04-05
PC will do POST, no beep codes, after OEM splash screen appears I can go into setup, and see that processor, RAM and HD all show up healthy in diagnostics, but after continuing with startup all I get is dark screen with a blinking cursor.

Tried to boot with a LiveCD, but after selecting Boot from CD in start up menu and initial CD splash screen shows, again the blank screen with blinking cursor appears and PC will not boot any further.

Is Mobo screwed up? maybe lost the BIOS? I took out the GPU card (instead using built in graphics on processor) and tried another HDD but no joy. CPU and Memory seem to be all right.

Thanks for any help.

---

### Post by Bashing-om on 2014-04-05
mayagrafix; Hummm,

You did verify the md5sum of the .iso file ? And did you also verify the integrity of the liveDVD ? - Don't think any of the mainstream editions of the 'buntu desktops will fit on a CD any longer -. We are not talking UEFI or secure boot are we ?

OK, we know now that the .iso file was good, and that the burn to DVD was good, ->
Boot the liveDVD, soon as bios screen clears depress and hold the right shift key -> language screen, escape key to accept the default -> boot options screen -> F6 key for boot parameters .. many times with several chip sets, the boot parameter "nomodeset" will prove effective. - space or enter to accept and then the escape key to exit - enter key to continue the boot process ..

What now results ?

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by mayagrafix on 2014-04-06
Thanks for ur responce. The CD, er, excuse me, the DVD is in perfect working order, I used it a couple of days ago (Ubuntu 13.10 with GNOME) so I know it works. No UEFI or secure boot either, just plain vanilla 2 year old Dell 620s desktop. Let me give this right shift key thing a try and Ill get back to you.

---

### Post by mayagrafix on 2014-04-10
Turns out the PSU is not good enough... somehow, even though it works, it is the cause of aformentioned problems. After switching to another PSU, no more problems. Thanks for all help.

---

### Post by Bashing-om on 2014-04-10
mayagrafix; Hey !

Appreciate ya posting what the resolution is.
Under powered power supply ! Who would have thunk it ! -> when you are good, you are good.

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

### Post by mayagrafix on 2014-04-11
Great to be appreciated. However, I'm not the hero you make me out to be. Here is the link where I got the answer:
[http://www.tomshardware.com/forum/354159-28-power-supplies-lose-wattage-years](http://www.tomshardware.com/forum/354159-28-power-supplies-lose-wattage-years)
and here is the summary:
> A power supply will drop its ability to supply power over time due to the capacitors aging and drying up. There is little difference in this regard between a expensive power supply and a cheap power supply
and here:
[http://www.pcadvisor.co.uk/how-to/pc-components/3503892/pc-shuts-down-unexpectedly/](http://www.pcadvisor.co.uk/how-to/pc-components/3503892/pc-shuts-down-unexpectedly/)
> Your power supply should be delivering 3.3-, 5- and 12V inputs to your motherboard, but these can fall outside acceptable ranges if the PSU is under-powered or has developed a fault. Check to make sure the power supply is operating as it should. If not, you may have to replace it
I had diagnosed the MoBo but cooler heads prevailed and pointed me to PSU. Low and behold, after jerry-rigging another PSU all problems were solved!
[[IMG]http://i16.photobucket.com/albums/b1/mayagrafix/binaryes/DSC04964_zpsb754aba4.jpg[/IMG]](http://s16.photobucket.com/user/mayagrafix/media/binaryes/DSC04964_zpsb754aba4.jpg.html)

Hope this helps someone else with similar problem :>)

---

### Post by Bashing-om on 2014-04-11
mayagrafix; Hey,

Your last Starts my day out with a chuckle . Ya still done good work.

Fault isolation to resolution ->
[INDENT][INDENT]nothing else like it
[/INDENT][/INDENT]

---


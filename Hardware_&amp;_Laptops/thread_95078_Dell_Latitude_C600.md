---
title: "Dell Latitude C600"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by migueljacq on 2005-11-25
Hi,

I've recently been using a C600 Dell Latitude running Breezy for about 2 months. I've had no problems except for the cpufreq problem which was easy fixed.
However, last night, all of a sudden the touchpad has gone crazy. The cursur is constantly sliding down the screen without stopping. Can't seem to stop it. I plugged in a normal mouse but it seems the touchpad overrules it, the drag is too strong for the normal mouse to overcome.
Can anyone tell me if this is the touchpad itself, ie a laptop problem, or is it some sort of sudden incompatibility with Ubuntu? Can it be fixed?
I guess what I'm asking is, should I install a different distro on it, or throw the laptop out :-) twas only second hand anyway.

Thanks

Miguel

---

### Post by utcamperj on 2005-11-25
On older laptops I've seen this be caused by dirty/loose connectors on the touchpad (i.e. open the case, pull the cable that connects it to the motherboard, blow it out with compressed air, reseat the cable (carefully!) and reassemble the case).  Also seen a couple that just freaked out for good.  To be able to use the laptop at all I disabled the touchpad in the BIOS and just used an external USB mouse.

---

### Post by teaker1s on 2005-11-25
it may be chance but my ubuntu bid the same on a new wireless mouse so i took it back

---

### Post by migueljacq on 2005-11-26
Thanks for the responses.
To be honest, the touchpad annoyed me even when it was working. It hadn't occured to me about disabling it in the BIOS, which I did. 
Thanks again

Miguel

---

### Post by inigopete on 2005-12-19
I've got a Latitude C600 that started doing that (in my previous install of Gentoo).  The mouse cursor would start drifting, sometimes slowly and sometimes rapidly, towards one corner or edge of the screen.  Cleaning the trackpad and moving a finger over it made no difference.

I noticed that it happened most when I was sitting with the laptop actually on my lap.  It very rarely did it on a flat tabletop.  Then I realised that it had nothing to do with the trackpad, it was the little nipple thing in between the G and H keys which was causing the problem.  Once the cursor started drifting I'd wiggle the nipple thing and it would stop.

I haven't actually found a cure for it - I plan to take the keyboard off and do a full Contact Cleaner de-gunk of it at some point over Christmas - but I have found, in my case, that that's the problem and a regular remedy.

HTH.

---

### Post by noco37 on 2005-12-19
The Dell "crazy cursor".  That is a hardware issue.  The problem is that the track point (the eraser tip by the g and h keys) is losing its calibration.  In a former life I did alot of support on the C6XX series, this is a universal dell issue for machines of that ilk.  There are a few solutions for this:

1) Disable the touch pad and track pad in the BIOS and use an external device.
2) Replace the keyboard
3) In the Windows world, get the newest dell BIOS and synaptics driver. (eventually the hardware will degrade so much that this will no longer work.)
4) Live with it.  When the cursor starts floating, let go of your pointing device.  Fighting it will only make the issue worse.
5) (My favorite) Cut the ribbon cable to the track point. This will disable the track point but leave the touch pad active.
    a) Remove all power from the unit (AC and battery)
    b) Remove the HDD
    c) Remove the 5 screws on the bottom of the computer labled with a 'k'
    d) Remove the keyboard.  The blank key above the right arrow key can    be used to pry the the keyboard up.  Slip a small screwdriver or knife between that and the edge of the computer.
    f) Under the keyboard there are 2 ribbon cables.  Cut the cable that has 4 wires in it.
    g) put it back togeather.

Look arround on the net before you just trust me and cut your computer up, but I have done this with many Latitude CXX's and have never had a problem.

---


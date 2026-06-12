---
title: "Why won't my computer boot?"
date: 2010-12-09
forum: Hardware
---

### Post by Xamith on 2010-12-09
I recently tried to install another HDD in my computer. I discovered I would not be able to fit it past my nvidia geforce 9600 GT graphics card, so I removed the card. Because I would not be able to fit the extra HDD with the graphics card I decided to not use the HDD. I put everything back together in the computer and plugged the power cable, DVI cable, etc. into the computer again. When I pressed the power button the computer turned on for roughly a second with nothing showing up on the monitor, then shut down. 5 seconds later it did the same thing automatically. I tried removing and reinstalling the graphics card and I played around with the BIOS jumper on the motherboard. Can anyone help me, or do I need to take it in? Thanks in advance.

Intel E7400 @ 2.8GHz
Nvidia GEForce 9600 GT 
Antec NSK4480B Chassis
Ubuntu 10.10 and Windows Vista

---

### Post by paulisdead on 2010-12-09
If the video card has one, did you remember to plug the power cable back into it?  I've done the same thing.  Take the card out and put it back in, and forgot to plug the power back into it.  Look closely at the way the card's sitting in the slot, too, to make sure it's in straight and even.

If that fails, you can try unplugging everything from the mobo, ram, power cables, etc, reseat them, and see if that makes any difference.  Not typically worth it to remove the cpu itself, but everything else should be re-seated, since it's easy.  Sometimes things get jiggled out of place while working, and you've got to unplug/plug everything back in to find what it was.

---

### Post by Xamith on 2010-12-09
Thanks, I'll try it

---

### Post by Xamith on 2010-12-09
So now it will look like it turns on(doesn't do the reboot cycle), but the monitor doesn't work. Is this now just a driver issue, or will drivers affect the BIOS and everything? I also tried using the onboard VGA with my monitor, with no luck.

---

### Post by paulisdead on 2010-12-09
Drivers won't affect the POST, since none of that loads yet.  In order to use the onboard video, you'll likely need to completely remove the add in graphics card from the system to get it to POST on the onboard.

I assume you checked the connections for your monitor are tight, and made sure it's configured to listen on the correct input, ie analog/digital.

---

### Post by Xamith on 2010-12-10
Yeah, I did... last night I left it unplugged with the CMOS battery out, so I'm going to plug everything back in and try it today.

---

### Post by Xamith on 2010-12-10
Still nothing. It's still "booting" but I think the GPU is fried

---

### Post by Xamith on 2010-12-10
So, to recap, my current situation is this: [LIST=1]
[*]Computer boots up
[*]There is nothing on the monitor when I use the graphics card, and same with the onboard (even with card out)
[*]Card is getting power, because fan is spinning.
[*]The manufacturer of my card (BFG Tech) is out of business.
[*]I'm freaking out right now.
[/LIST]

---

### Post by drs305 on 2010-12-10
Is there even a flashing cursor on the monitor, or truly 'nothing'. If there is a cursor, you could try booting with the 'nomodeset' option.

---

### Post by conradin on 2010-12-10
Sometimes the default BIOS setting don't actually work correctly for booting specific hardware configurations.  Can you tell us more about your bios?
is this an AGP or PCI video card?
how much buffer is assigned to the video card in the bios? is the video card assigned to be the default used when its available? (auto detect video setting is typically ok too.) (did you work on your computer grounded? (eliminating risk of ESD?)) 

Can you set quiet boot & the quick boot to disabled & look for any inform there when booting?

Whats the power rating of your new hard drive?

---

### Post by Xamith on 2010-12-10
The monitor goes into "Power Saving Mode", so it's like the card isn't sending any information at all to the monitor. I'm pretty sure it's a hardware issue.

---

### Post by Xamith on 2010-12-10
The card is PCI, I reset the BIOS with the jumper, and I decided not to install the second hard drive (no room)

---

### Post by Xamith on 2010-12-10
So, do I need to just scrap this computer, or is there any hope for it?

---

### Post by Xamith on 2010-12-10
I managed to get it to boot using the onboard video and taking out both the GPU and a stick of RAM.

---

### Post by Xamith on 2010-12-10
I put the GPU back in and now it works, it might just be the RAM.

Computers... gotta love 'em.

---


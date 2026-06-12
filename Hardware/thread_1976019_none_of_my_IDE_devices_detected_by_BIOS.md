---
title: "none of my IDE devices detected by BIOS"
date: 2012-05-08
forum: Hardware
---

### Post by s1wood on 2012-05-08
I recently unplugged my HDDs to check out another one, which didn't load; when I reconnected the original disks the computer would not start and going into the BIOS I found it was not detecting any of the IDE devices including the CD drive. The CD drive will open and close but that's it.
I removed and reconnected all the cables and tried different cables, I removed the BIOS battery briefly: no change.
This is (or rather was) the self-assembled computer so the motherboard has been around a bit - it looks as if the IDE controllers are defunct. 
Any other suggestions before it goes to landfill?

Susan

(Luckily the purpose of the manoeuvres was to set up another P4 in case of something like this happening and I have been able to transfer my HDD to the other computer)

---

### Post by mips on 2012-05-08
Maybe try the MB with a different PSU.
Alternatively try and reflash the BIOS.

If this does not help I suspect it's bye bye MB.

---

### Post by prshah on 2012-05-08
> **s1wood said:**
>  found it was not detecting any of the IDE devices including the CD drive. The CD drive will open and close but that's it.

Please check and ensure that IDE channels are enabled in the BIOS, typically settings like ("Primary IDE", "Secondary IDE") etc.

Some motherboards that have BOTH IDE and SATA ports are very confused in handling them.

Please check your BIOS options for options on how to handle IDE devices. Since the exact term varies from BIOS to BIOS, I cannot be more specific. You need to look for something like "IDE SATA MODE: p0-Master,p1-Slave" etc. You will need to toggle and play with the options. You NEED to save and exit after every change, before checking if your IDE devices are detected.

Please post your motherboard BIOS screen (photo) for more specific details.

I have such a motherboard and it's a right pain to get working; I will post some screenshots of the BIOS settings later.

Of course, it may just be dead IDE ports as you suggest, so this is just something to check.

---

### Post by s1wood on 2012-05-08
It only had IDE and both controllers were enabled, I hadn't interfered with the settings.
However, I reconnected it all to take a picture of the BIOS screen and it is now completely dead - no fan, lights or anything. Have tried another cable but no go, so - computer by-bye!

Thanks for assistance.

Susan

will now have to change my signature.

---

### Post by mips on 2012-05-08
> **s1wood said:**
> It only had IDE and both controllers were enabled, I hadn't interfered with the settings.
However, I reconnected it all to take a picture of the BIOS screen and it is now completely dead - no fan, lights or anything. Have tried another cable but no go, so - computer by-bye!

Thanks for assistance.

Susan

will now have to change my signature.

Try a different PSU, if it still does not work you can bin the motherboard and keep the rest of the stuff.

---

### Post by s1wood on 2012-05-08
Haven't got a spare PSU for P4 and don't really think it's worth getting one just to find out if the mb is dead - this computer doesn't owe me anything.  I shall of course scavenge anything potentially usable - given that I've got the original P3 mb & PSU in the loft I might just reinstall that!

regards,

Susan

---

### Post by mips on 2012-05-08
> **s1wood said:**
> Haven't got a spare PSU for P4 and don't really think it's worth getting one just to find out if the mb is dead - this computer doesn't owe me anything.  I shall of course scavenge anything potentially usable - given that I've got the original P3 mb & PSU in the loft I might just reinstall that!

regards,

Susan

If you have a newer PSU with more pins (I think it is 4) then with the notch in from of you let the 4 additional pins fall over the right hand side. This works as I have tried it before and the electrical specification matches.

---

### Post by s1wood on 2012-05-08
The only spare PSU I've got is the one from the P3 and it doesn't have the separate lead for the mb as I remember - I found this out after I fitted the P4 mb. I'm NOT taking the PSU out of my working computer!

Susan

---

### Post by jmore9 on 2012-05-14
Did you try disconnecting all drives including the cd/dvd and only connecting one hard drive to either ide or sata ?  Using ide make the hard drive master and see what happens.  If your bios sees the hard drive like that then you have to configure all your drives.

Say if you had a 80 gig and a 250 gig hard drive both ide and also had a 250 gig sata.

And you wish to boot from 80 gig and use the others for storage I would do the following :

On the rear of the ide drives there is a connector which allows you to select either Master, Slave or Cable Select , Make the 80 gig drive a master using the selector connector , and make the 250 gig a slave.

The sata does not need any connector connections.  Your bios should now see each drive with the proper storage space.

Hope this helps a little.

---


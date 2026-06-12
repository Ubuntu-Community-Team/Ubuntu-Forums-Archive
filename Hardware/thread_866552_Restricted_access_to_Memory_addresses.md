---
title: "Restricted access to Memory addresses"
date: 2008-07-21
forum: Hardware
---

### Post by wizardfait on 2008-07-21
I'm on a Compaq Armada M700, and I recently went back to Ubuntu because of some Windows XP deficiencies...  One main one being I've heard of this to cause many stability issues with other users, however I didn't find any, and didn't want to wait for them anyways, however in Windows XP BY DESIGN they chose to implement some restrictions on this laptop's ACPI techniques, where-in they made it so that certain reads and writes to certain CMOS addresses were restricted to make the environment "more stable" however, as I previously stated, this was quite counter-intuitive to many computers.

I'm wondering if Ubuntu has any of these restrictions, if I recall correctly Windows XP declared the memory address 0x70 and 0x71.

Also, kind of a random question... I know in Windows if I use a HDD in one computer, as long as there aren't too many differences between the machines, and a few other *things* that I can swap it into another machine, and it'll load the drivers for the devices, require a reboot, then work... Can ubuntu do the same thing?

Btw: I am a new user to these forums, however, to ubuntu I am not too new. Granted, when it comes to the deep tech stuff, I'm not so good at it yet, but I plan on it. (And actually I've used these forums for quite a while, just never registered. :D)

---

### Post by Dark_Stang on 2008-07-21
Not sure where you're getting your information on memory. The operating system usually doesn't even know where a certain memory location even is and it just relies on the MMU (memory management unit) to do all the work for it. Windows may declare certain logical addresses for itself, but I don't think it would take control of certain physical addresses. If it did this would have the potential to slow things down considerably.

And as far as your HDD question. Just do the default install to the hard drive, do not setup any extra drivers on the mule machine. Then put the hard drive in the target machine and setup your extras from there.

---

### Post by wizardfait on 2008-07-21
I'm referencing this issue that would pop up in the system logs, and I did a little research on it, only to find the only solution would be turn of ACPI (No thank you) or use a different os... Probably 2k wouldn't do it, but W/e, UBUNTU ALL THE WAY! :D, or bios update. Being as I just got the most recient bios, just in order to get ACPI fully functional (Which in Ubuntu it works SO much better now) that's not an option to go newer.

The message:
AMLI: ACPI BIOS is attempting to write to an
illegal IO port address (0x70), which lies in the 0x70 - 0x71 protected
address range. This could lead to system instability.

That is what I'm referencing, however, in one of the websites I read up about this issue, they said that 0x70 was a cmos memory address, so that's where I got that "idea" from, however, if I"m wrong, I'm sorry for the misinformation, however, I still would like to know if Ubuntu has any "protections" involving this, like XP does.

---

### Post by Dark_Stang on 2008-07-21
That appears to be a driver issue between windows' acpi and your mobo's bios acpi. If I had seen that error I would have probably just shrugged it off and disabled acpi, but I'm pretty laid back when it comes to things like that. If I don't need it, it's off/isn't installed.

---

### Post by wizardfait on 2008-07-22
Thanks, but that still doesn't answer my question. :P

---

### Post by Dark_Stang on 2008-07-22
I don't know of any restrictions ubuntu has on acpi, however there definately are issues between ubuntu and certain motherboards. The best advice is to try it out and see how it goes.

---

### Post by wizardfait on 2008-07-22
well, so far no issues, I just didn't know if I should be concerned about my ACPI causing instabilities.

---


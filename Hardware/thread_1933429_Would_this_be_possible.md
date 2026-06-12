---
title: "Would this be possible?"
date: 2012-02-29
forum: Hardware
---

### Post by segamaster222 on 2012-02-29
Okay, so my idea is to have 2 hard drives and 2 video cards in one case (It's a big case don't worry) and have the hard drive with windows on it use the ATI card only and have the Ubuntu hard drive use the Nvidia card only. 

Is there any way at all that this is possible?

---

### Post by wyliecoyoteuk on 2012-02-29
Only if you run them both as virtual machines on a hypervisor.
Otherwise you would need 2 motherboards and processors, and 2 lots of memory.

---

### Post by segamaster222 on 2012-02-29
> **wyliecoyoteuk said:**
> Only if you run them both as virtual machines on a hypervisor.
Otherwise you would need 2 motherboards and processors, and 2 lots of memory.

Sorry for not explaining well enough, I plan to have it as a dual boot hard disk setup where I'm either in one or the other.

---

### Post by wyliecoyoteuk on 2012-02-29
Well that's far simpler.
Just set up a dual boot, or do 2 totally seperate installs, and use the bios boot control to switch between them.

---

### Post by heroofhyrule on 2012-02-29
@wyliecoyoteuk: Couldn't he just install the drivers for the ATI card on his HDD with Windows and the drivers for the Nvidia card on his HDD with Ubuntu?  That way the OS points to the correct card because the drivers for the other card are missing.  

Now that I think of it, this might work on Windows, but I think Ubuntu will recognize the ATI card automatically?

---

### Post by wyliecoyoteuk on 2012-02-29
Both OSes would probably recognise both cards, but you could disable them in the relevant ones.

---

### Post by Mark Phelps on 2012-03-01
This will be problematic in MS Windows because, even if you uninstall the video drivers you don't want, it will see the hardware on every boot and try to reinstall them.  The typical "solution" to this is, after you've removed the drivers, then disable the other video card in the BIOS -- but this will disable it for ALL of the OSs.

Don't even know if this is possible in Ubuntu. 

So, wyliecoyoteuk, HOW would the OP go about disabling the video card he doesn't want do use, in Ubuntu, without disabling it in the BIOS?

---

### Post by wyliecoyoteuk on 2012-03-01
To be honest, I don't understand why you would want to do this anyway.
It is probably possible in Linux just by editing the Xorg.conf file.
In windows, less so.

---


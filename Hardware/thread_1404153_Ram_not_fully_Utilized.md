---
title: "Ram not fully Utilized"
date: 2010-02-11
forum: Hardware
---

### Post by BionicGear83 on 2010-02-11
I have recently upgraded my Ram to 6GB, but Ubuntu 9.10 can only detect and use up to 4GB.

What settings do I have to edit in Karmic to use all 6GB of the Ram?

---

### Post by mcduck on 2010-02-11
> **BionicGear83 said:**
> I have recently upgraded my Ram to 6GB, but Ubuntu 9.10 can only detect and use up to 4GB.

What settings do I have to edit in Karmic to use all 6GB of the Ram?

I suppose you are running the 32-bit version of Ubuntu?

32-bit operating systems are only able to addrss up to 4GB of memory (which includes all meory on your system, not just RAM, so if your graphics cards has 1GB that leaves only 3GB of memory addresses for RAM).

The best option would be to install 64-bit version of Ubuntu (Assuming you have a 64-bit CPU), or alternativelty install the PAE kernel from repositories.

---

### Post by BionicGear83 on 2010-02-11
I am using 64-bit Ubuntu 9.10.
I installed from ubuntu-9.10-desktop-amd64.iso

That's why I find it strange that Ubuntu cannot fully utilize the RAM that I put in.

---

### Post by mcduck on 2010-02-11
> **BionicGear83 said:**
> I am using 64-bit Ubuntu 9.10.
I installed from ubuntu-9.10-desktop-amd64.iso

That's why I find it strange that Ubuntu cannot fully utilize the RAM that I put in.

In that case it should work without any problems.

Make sure the RAM stick is correctly in it's place, and then check from your BIOS that it's detected. Or run the memtest from Grub menu or Ubuntu's live-CD.

---

### Post by BionicGear83 on 2010-02-11
I checked out the BIOS and confirmed that all 6GB of the RAM has been detected. I find it quite strange that Karmic can only use 4GB.

---

### Post by mcduck on 2010-02-11
There is something defnitely wrong on your system, the 64-bit version of Ubuntu shouldn't have any troubles addressing 6GB of RAM.

Cold you run "uname -a" and "free -m" & post the outputs here?

---

### Post by BionicGear83 on 2010-02-13
Finally managed to detect all the RAM after reformatting my HDD and reinstalling Ubuntu.

Must be something I did to the previous OS.

---


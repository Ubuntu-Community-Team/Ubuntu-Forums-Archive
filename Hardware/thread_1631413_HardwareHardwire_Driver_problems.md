---
title: "Hardware/Hardwire Driver problems"
date: 2010-11-26
forum: Hardware
---

### Post by deanom on 2010-11-26
Hi All
Firstly, I am a newbie, and could have posted this in a number of the forums.
I have been unable to install a stable version of 10.04, 10.10, or Mint 10. I have confirmed that the DVDs are working by successfully installing each of them onto an old laptop.
At no pointcould I install 10.10, or Mint 10. At each attempt the installation froze during disk partition. 
Attempting to install 10.04 has allowed me to get an unstable OS working. Of about 30 attempts, most froze at the same point, as the other versions. Two attempts failed during hardware configuration. One attempt succeeded, but continues to freeze, particularly during software updating.
The first question is what is the difference in the installation processes that allow 10.04 to install, but not the others? Perhaps there is a clue there.
Writing to disk seems to be one of the main triggerss. My **motherboard is an Abit AB9, **which uses an **Intel P965/ICH8 Chipset**. It has it's own windows drivers, including a floppy disk for a **JMicron SATA RAID driver**, which has some relationship to the connector for my Hard Drive, which is a **Samsung Spinpoint HD401LJ**.
The only other possible clue is that the motherboard battery ran out in the Summer. When I replaced it there was an XP Sevice pack update, which crashed the computer, so there may be some bios settings that have altered when the CMOS was cleared.
I hope that this is enough information to go on, and would just remind you that as a newbie, I may need more detailed descriptions of solutions.

Thanks

Deano

---

### Post by Fafler on 2010-11-26
Have you confirmed the system to be stable with other operating systems?

P965 boards are really wellsupported and stable under Linux. All drivers are included on the installation CD. Speaking of CD, try burning on another burner. Also, theres an option to check the CD for defects. Last, there a program included in the menu that will test you memory. Try letting it run for a while and see if something comes up.

What graphics card do you have? Any other hardware?

---

### Post by deanom on 2010-11-26
Hi Fafler
The system was stable running XP.
The CDs worked fully on an old laptop.
Graphics card is Nvidia 7950
No other hardware connected at the moment.
Have not tried the memtest yet, but will look at it tomorrow.
Thanks

Deano

---

### Post by Fafler on 2010-11-27
Still, some drives might work fine with CD-R's discs that wil fail on other drives. Try burning it at 8x speed. Or try using a USB flash drive instead of a CD.

Also, reset the BIOS and try some of the special boot options from the CD, like noapic and acpi=off. Theres a help menu that explains it. Unless the board is defective, it's going to run Ubuntu.

---

### Post by deanom on 2010-11-27
Thanks Fafler
I've got most of the day to play around with the bios settings. If that fails, I'm going to get a new hard drive, and give that a go.
All of the best

Deano

---

### Post by deanom on 2010-11-30
Hi all
I still haven't solved this. 
My suspicions lie with the Hard Disk, or the SATA drivers for it.
My MOBO  (Abit AB9) uses drivers installed from a Floppy disk, to run 1 x IDE socket, and 2 x SATA sockets.
This is where my hard drive is connected. There is also a Floppy disk drive, connector, and 4 x SATA sockets which do not need additional drivers. Whilst the socket and cable for this look identical to the one for the Hard drive, there seems to be a slightly different pin/socket layout. The handbook says that the FDD has a 34 pin cable, but then says that each of the IDE ports can connect up to two IDE drives using a 40 pin cable, and 3-connector Ultra ATA cable.
**Question ONE.**
To me this suggests that I can connect the Hard drive directly to the Floppy Disk socket,using the cables that are currently connected to the other socket (which needs the additional drivers). Is this correct?
**Question TWO**
How do I check whether the drivers have been installed during the UBUNTU installation?
**Question THREE**
How do I find and then install any alternative drivers to get this system up and running for the first time?

Please feel free to answer any of the questions, even if you cannot answer them all.
Thanks

Deano

---

### Post by deanom on 2010-11-30
Hi I've found linux drivers for the SATA controller
[HERE.]("ftp://driver.jmicron.com.tw/SATA_Controller/Linux/")  
but I cannot tell which I should use. The options are Fedora, Redhat9, Red Hat Linux3, Red hat Linux4, and SUSE.
Suggestions would be helpful, and I'll post a question to the manufacturer.
Thanks
Deano

---

### Post by Fafler on 2010-11-30
Try setting the SATA controller to AHCI mode in the BIOS and have your harddrive on the first of the four SATA ports. The kernel Ubuntu uses already has 100% support for that.

You have two controllers:

The one inside your south bridge, which provides the 4 SATA connectors. It can run in two modes, AHCI and one i can't remember. AHCI has better Linux compatibility.

The other it probably a JMicron chip, providing one 40 pin PATA/IDE/ATAPI... connector and 2 SATA connectors. It has good Linux compatibility, but i haven't tried to boot SATA  drives from it.

---

### Post by deanom on 2010-12-01
Thanks fafler
I'll give it a try.

Deano

---


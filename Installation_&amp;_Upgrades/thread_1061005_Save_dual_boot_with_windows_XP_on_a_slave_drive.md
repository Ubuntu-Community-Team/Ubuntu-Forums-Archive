---
title: "Save dual boot with windows XP on a slave drive"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by Niksu on 2009-02-05
Hello world!

 I've been planning to install Ubuntu on my desktop for ages and now I've come to the final stage. My PC has two disk drives with Windows XP installed on the first and the second used as a storage (NTFS formatted, used under 50% of capacity).
 I wish to keep the XP, to give the several other persons using it a chance to gradually switch to Ubuntu.

 With all the dual boot info gathered from posts and articles I intend to make the second disk master and the Windows' one slave and install Ubuntu on the second.

What troubles me is this: 

- should I disconnect the Windows (slave) disk drive before installing Ubuntu on the second (master)? Or should it stay connected in order for Ubuntu to recognize there's another OS?

 - also at the moment there's no option in my BIOS menu to make the second drive bootable. Would that be a problem or it's just because the drive's current position is slave?

 - can I keep the stored files as a separate partition, and istall Ubuntu on its own partition or should it take the whole disk?

- and one side question: can I create one more partition and have Ubuntu and BSD installed at the master (and keep the stored files), with XP on the slave. I'm just curious to try BSD..is this a good idea...!?

I apologize for so many questions, I guess I'm playing it too safe ;)

 Thanks in advance, I can't wait to join the Ubuntu Tribe!

---

### Post by drew2222 on 2009-02-05
Niksu,

Interested in your post as I too am about to install ubuntu as a dual boot install over Windows xp pro. I have 2 existing hdd's on my setup and plan to install ubuntu on a third dedicated drive. I downloaded the ubuntu iso file and burned it to a cd.

There are several install options available from the cd. I intend to leave all drives connected so that ubuntu will recognise windows and install the neccessary dual boot config?

Can't blame you for being cautious, I have done alot of research and backed everything up twice!
My system is a home built AMD 64 CPU on an ASUS A8N SLI mainboard.
I'll post results and any errors here.
Good luck with yours!

---

### Post by caljohnsmith on 2009-02-05
> **Niksu said:**
> Hello world!
- should I disconnect the Windows (slave) disk drive before installing Ubuntu on the second (master)? Or should it stay connected in order for Ubuntu to recognize there's another OS?

You can leave the Windows slave drive connected when you install Ubuntu to your master drive, and most likely Ubuntu will detect Windows just fine and add it to your Grub menu as a boot option. Hence I would leave the Windows drive connected since it should be to your advantage.
> **Niksu said:**
> 
 - also at the moment there's no option in my BIOS menu to make the second drive bootable. Would that be a problem or it's just because the drive's current position is slave?

Most likely Grub will have no problem booting your Windows slave drive, so it's OK if your BIOS does not support booting the slave drive directly.
> **Niksu said:**
> 
 - can I keep the stored files as a separate partition, and istall Ubuntu on its own partition or should it take the whole disk?

Sure, in fact it is recommended that you keep your personal files separate from your Ubuntu install. When you go through the installation process, I would suggest clicking the "manual" partitioning option, and there you can set up partitions for Ubuntu while keeping your stored files partition untouched. 
> **Niksu said:**
> 
- and one side question: can I create one more partition and have Ubuntu and BSD installed at the master (and keep the stored files), with XP on the slave. I'm just curious to try BSD..is this a good idea...!?

Sure, you can have BSD and Ubuntu on the same drive but on different partitions. If I remember correctly, there is special syntax necessary in Grub's menu.lst to boot BSD from Grub, so you might have to look that up. Anyway, good luck and let us know how it goes.

---

### Post by Niksu on 2009-02-09
Operation "Red Pill" was successfully completed!
I'm writing these lines from my brand new Intrepid Ibex.

Caljohnsmith - thanks for your help and tips!
Drew2222 - hope you will too succeed without problems.

I'd like to share a few things I bumped into, that might be useful to other Neos like me :)

First, I've missed a section in my BIOS Boot Order menu, s.th. called "disk drives". There one is able to change which drive is primary. Since I haven't checked it, the XP drive (C:\) was primary and present in booting order menu, while my second drive (H:\) wasn't even listed.
I switched them so the PC could see H: as primary.

Then I found out my both disk are SATA, and that there's no Master or Slave amongst them. Still I found the XP disk was connected at SATA 1, and the Ubuntu-would-be disk - at SATA 2. Again, I switched them and this made it possible for the Ubuntu installer to see the XP disk as /hdb, and the other one - as /hda.

Third, I had some difficulties understanding the Ubuntu partitioner, so I just used another one and created 1 GB swap area and 150 GB place for Ubuntu.

I ran the Ubuntu installer for the last time, and followed the instructions without more troubles. 
Everything seems to work fine now: I have a choice of OS at start up, the two OS are on different disk drives, the Windows MBR is intact, the Ubuntu disk is separated to a ntfs part (my XP storage), swap area and Ubuntu ext3 partition.

Now I'm off to discover this new world (starting with experiments to install Cinelerra... :)

Thanks a lot, again.

As for the BSD... it will wait for now...

nick

---


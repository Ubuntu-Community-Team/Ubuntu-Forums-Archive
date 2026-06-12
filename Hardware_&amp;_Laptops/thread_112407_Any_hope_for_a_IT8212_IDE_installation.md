---
title: "Any hope for a IT8212 IDE installation?"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by boomducky on 2006-01-04
Hi,

I've been using ubuntu for about a month now and I love it.

Unfortunately, last Sunday, my built in IDE controller started acting flaky and ate my hard-drives. Being a pov uni student, I went for the cheapest repair option - a cheapo IDE card (the IT8212) and new hard drive.

I'm booting off this device now. I managed to install windows (with a little pain and misery), but I can't get the ubuntu intaller to see my hard drive, let alone the nice little free space on my disk. I've had a quick glance on google, and the forums, but all the work arounds for the IT8212 cards seem to be for AFTER you get the thing to install.

Does anyone have any ideas on how to get the ubuntu installer to SEE my hard disk? It doesn't have to work great, or be easy.

Heck, it doesn't even have to be ubuntu. I just really need a linux distro to complete my work experience....

Thanks a lot,
Em

---

### Post by Menuta on 2006-01-25
Hi boomducky

 
I have successfuly been able to see the drive by compiling the kernel as shown in the following thread. [Http://ubuntuforums.org/showthread.php?t=106285](Http://ubuntuforums.org/showthread.php?t=106285)
( but you probably already know this)

I can then boot from another ide controller that will see and partition the drives on the IT8212.
I have copied my Ubuntu install over to the new drive on the RAID controller.
The only trouble is I cannot boot properly from it. The boot process begins to work then drops back to a shell complaining that it can't find /dev/hde2.
I hope someone has ideas on how to boot from an it8212, I have been trying to figure it out for about two weeks.

Good luck I hope you find a solution.

---


---
title: "External HDD"
date: 2010-08-20
forum: Hardware
---

### Post by libssd on 2010-08-20
I have little expectation of a solution in a Linux forum, but thought I would raise this issue because it might happen to others.

I have an Acer D150 netbook, which came with a 160gb HDD, installed with Windows XP, of course. Installing Ubuntu in a 35gb partition was no problem, and I boot in Windows once a month or so to spend 2-3 hours apply security updates, then go back to Windows.

Two months ago, I found a deal on a solid state drive, and installed Ubuntu 10.04 on it. Since it's somewhat inconvenient to open the netbook and remove the SSD every time I want to run Windows, today I acquired an external 2.5" SATA case, with the thought of booting Windows through it, and avoiding the drive swap hassle.

Ubuntu boots just fine from the 160gb HDD mounted in the external enclosure. However, if I select Windows, the Windows boot sequence starts, then aborts, and I end up booting into Ubuntu anyway. Suggestions? (Other than trash Windows entirely.) 

Startin

---

### Post by efflandt on 2010-08-20
Have you run sudo update-grub with the USB drive attached (or from the Ubuntu booted from the USB drive)?  Grub can boot Linux anywhere based on UUID, but even if you somehow boot to Windows, its boot.ini might be pointing at the wrong drive/partition.

I am not sure how Windows sees drives, but if grub does not switch drive positions in BIOS maybe you need to modify Windows boot.ini to change **disk(0)** to 1 instead of 0 (or whatever it is).  Not sure what **rdisk(0)** is.  Someone who has done that could probably help with details.

---

### Post by libssd on 2010-08-20
> **efflandt said:**
> Have you run sudo update-grub with the USB drive attached (or from the Ubuntu booted from the USB drive)?  Grub can boot Linux anywhere based on UUID, but even if you somehow boot to Windows, its boot.ini might be pointing at the wrong drive/partition.

I am not sure how Windows sees drives, but if grub does not switch drive positions in BIOS maybe you need to modify Windows boot.ini to change **disk(0)** to 1 instead of 0 (or whatever it is).  Not sure what **rdisk(0)** is.  Someone who has done that could probably help with details.
Good idea, but no cigar. After removing the SSD to be safe (I have grub legacy on the HDD, grub2 on the HDD), I booted Ubuntu from the now external drive, ran update-grub, then restarted. Windows did exactly the same thing -- about 15 seconds into the Windows boot routine, a few messages flash by faster than they can be read, the screen goes black, and it restarts the boot sequence in Ubuntu. 

Just to be sure everything was copacetic, I removed the HDD from the case, and put it back in the netbook; Windows boots just fine (and is now starting the usual endless round of downloads and updates). After all the updates finish (probably in a couple of hours), I'll go back to the old configuration, and change the boot sequence, so that the USB drive is first. I don't think this is going to make any difference (it didn't when the HDD was internal), but it's worth crossing off another variable. I think the problem is that Windows is inherently too stupid to recognize that it's OK, even though it's connected via USB, rather than directly to the internal SATA connector.

---

### Post by libssd on 2010-08-20
Only 90 minutes to apply Windows updates -- a new speed record.

As expected, with the SSD back inside, and the HDD connected via USB, Windows still refuses to start, even though the USB is now the first device on the BIOS boot list. This is not a big deal for me, as I'm hardly less well off than before. It's a little more effort to extract the HDD from the external case, but since I hardly ever use Windows, it really doesn't matter. Plus, I now have a handy case to protect the HDD. Eventually, I'll probably just reformat the HDD, and have an external drive for storage, at a cost of $10.

---

### Post by child on 2010-09-03
I found this: [http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)
I've never tried to do this but according to that article it may will be useful for you.

---

### Post by libssd on 2010-09-03
Thanks for the pointer. Somebody went to a great deal of trouble to write that up.

---


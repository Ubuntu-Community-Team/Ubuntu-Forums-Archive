---
title: "recommended boot manager for dual boot ?"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by HarryMangurian on 2005-12-31
I dual boot Ubuntu and Win XP.

Grub is ok, but I would like to know if there are any reliable freeware boot managers.   I found some, but do not know if they will screw up my system.

At least one is OS independent in that it runs from an unused section of the harddrive.  It also should still work even if Linux is corrupted or unavailable.  GRUB will not.

Please let me know your experience.

---

### Post by raghav_p on 2005-12-31
I believe the one with partition magic works ok; they might have it in freeware.

---

### Post by peanut butter on 2005-12-31
you could try grubfor windows but i believe it is still very beta

---

### Post by opensourcerocks on 2005-12-31
In my Opinion, when something works just fine leave it.
Whenever I try to do something different in the computer it always 
ends up to be a disaster.

---

### Post by Herman on 2005-12-31
[http://gag.sourceforge.net/]("http://gag.sourceforge.net/")

I use GRUB, I love GRUB, but for those who do not share the same beliefs as me, or have reasons why they don't want to use GRUB, then I highly recommend GAG, which is free, open source software and is only a small download from the link given (above). GAG is also on the 'System Rescue CD'.
If you download your own copy of GAG from the GAG site, you can make your own GAG CD, install GAG to your MBR, or make your own GAG floppy disk.
The GAG floppy disk is my favourite. The CD is okay, but with the floppy disk you can configure GAG and 'save the changes' to the floppy disk. You can't do that with a CD. 
GAG has its own instructions in the 'install.txt' that comes with it, and also more when you run your GAG floppy or CD.
I liked GAG so much I wrote some extra instructions for it as well, on my own Ubuntu install website , about how to use it with Ubuntu, just to make sure.
Here: [http://users.bigpond.net.au/hermanzone/p12.htm]("http://users.bigpond.net.au/hermanzone/p12.htm")
You will need either GRUB installaled on a seperate /boot partition, or Lilo installed on your Ubuntu partition for GAG to boot Ubuntu. On most computers you can do that easily without re-installing. One of my computers has both Lilo and Grub installed together on both Kubuntu and Ubuntu. My older computer used to be able to do that, but now for some reason won't do it. For that one I would need to know about GAG before the install and install Lilo from the start.
Try GAG, I have tested it quite a lot (actually when I first heard of it I was critical of it), and it hasn't done any harm to any of my computers yet. I have used it from CD or floppy, but have never had the need to install it to MBR, since I have GRUB, and the main advantage of GAG for me is that it can run from the floppy. :D (Herman)

---

### Post by HarryMangurian on 2005-12-31
> In my Opinion, when something works just fine leave it.
Whenever I try to do something different in the computer it always 
ends up to be a disaster.

 Dr Wang or the CEO of Digital Equipment Corporation ??:razz:

---

### Post by cetol on 2005-12-31
I use osloader2000. Works great with multiple copies of windows and linux on the same machine. Current configuration has 4 separate copies of windows plus Fedora core 4 and now Ubuntu. All work seamlessly. Free to try. I did pay for this, but at $24.00 it has been worth it.

---


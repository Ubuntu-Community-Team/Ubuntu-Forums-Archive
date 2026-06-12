---
title: "MBR, can it become corrupted ?"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by randiroo76073 on 2009-01-15
I did a forum search on this & didn't find any threads/post to help. I regularly am multi-booted and chain load all distros but 8.10 Intrepid which is my main/swing partition(hd0,0)(sda1). Lately I've had to re-install grub 2-3 times because on boot/reboot I get the error: No operating system found, etc. Once I re-install grub I'm good to go for about 2-3 wks, then it happens again. It seems like it's taking longer for boot menu to come up too. 

Could it be that I've somehow corrupted/overwritten grub to many times previous to setting up chain loader(aprox 6 mos) ? Is there any way to reformat the mbr section only & then re-install grub w/o screwing up the whole system ? HDD is 320gb eide(pata), less than a year old, but as always there's Murphy:confused: 

Thanks for any help

---

### Post by Pumalite on 2009-01-15
Take a look. It might help:
[http://users.bigpond.net.au/hermanzone/p18.htm](http://users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by Archmage on 2009-01-15
To answer one of your questions:

Yes, the MBR can become coruppted. There are Viruses that are famous for this. When you boot from an infected medium it will spread itself on the harddrive and from any other medium that you insert.

Is it possible that you are using floppy discs from time to time? In this case I would change the boot-order to hdd-only and don't try other medias.

---

### Post by randiroo76073 on 2009-01-15
Thanks to both for answers :)
@Pumalite: I had forgotten about Hermanzone site, I visited there alot when I first moved to linux :) and his excellent tuts helped me over some rough spots. I didn't see anything imparticular that tripped my light-bulb to come on.

@Archmage: I haven't used floppies since I moved from win about 3-4 yrs ago(still have 2 shoe boxes full tho) I only, for the most part, download distro iso's that I want to try and then only from reliable sites, but now days thats no garauntee, once again Murphy is always hiding in the wings :( Is there any special to linux rootkit programs I should acquire & run ? I ran the stand-alone ones(updated) I had for win & nothing poped up.

---

### Post by caljohnsmith on 2009-01-15
Actually, it is ironic to note that some Windows anti-virus programs will also "corrupt" the MBR, or not really the MBR per se, but more specifically, they store information in the first track of the drive. Grub also uses about 20 sectors in the first track of the drive to embed its stage1.5 file, so sometimes Windows anti-virus programs will overwrite Grub's stage1.5 file. Do you happen to have Windows and any Windows anti-virus programs on that HDD too? If not, then at least you don't have to worry about that. :)

---

### Post by randiroo76073 on 2009-01-15
@caljohnsmith: Nope, this is a pure tux machine :D I do have a older 32bit machine set up with win XP(so I can help friends that I haven't been able to convert, yet) It is not connected to the outside world :)

---


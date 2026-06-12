---
title: "Hard Drive failure coming soon i feel..."
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by cmmike1 on 2007-07-17
Recently one of my hard drive with my ubuntu install has been clicking as if it was shutting down. It freezes my computer  for a few minutes when this happens. Basically i feel that the drive is going to fail at any minute now and i'm looking for the best way to back up my install. What i want to do is do a complete backup if i can and erase my windows hard drive and install my ubuntu image over that one. I will be removing the failing hard drive so i will be back to 1 hard drive. here is how my hard drives are linked.
My ubuntu Hard drive is the first drive
My windows xp drive is second.
What would be the best way to save all my ubuntu stuff? Should i backup my home folders and just do a clean install and then restore my home folder?

---

### Post by w4ett on 2007-07-17
You are correct, backup the home folder and then restore it on your new install....plus if you have spent a lot of time 'tweaking' your install, check out Apt on CD:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Highly recommended!

---

### Post by milton1 on 2007-07-17
You could use the GParted Live CD to wipe your windows drive, copy your Ubuntu partitions to the previously-windows drive, then simply yank the current ubuntu drive. Assuming there is no corruption on the current, possibly failing drive, you will not need to do a reinstall.

---

### Post by doog519 on 2007-07-17
As stated....I would back up the home folder and any other files of importance.
If you are on a network you could move them to another computer on the network.

Also if your going to get another hard drive get a 7200rpm. They cost a little more.But the extra speed is nice.

---

### Post by cmmike1 on 2007-07-18
I have one more quick question. If i do a back up of my /home will i have to re install any of my programs that i have already or will they be there when i restore it to the new install. also does anyone know if my rythmbox play counts willl be the same after the restore?

---

### Post by starfry on 2007-07-18
Is your drive an IBM Deskstar by any chance?

I had three of these fail with the annoying click click death noise.

---

### Post by tgalati4 on 2007-07-18
Those would be called Hitachi "Deathstars".  At least you have a warning.  If you get a new disk, spend the time to do a zero-write to the drive to break it in and ensure that the entire drive is writeable.  Quality control is poor these days.

---

### Post by cmmike1 on 2007-07-18
The drive is a Western Digital. does anyone know if restoring my /home folder will restore my play count in rhythmbox. it's not a big deal to me but it would just be cool if it was possible.

Also, i have an external hard drive that stand vertically. Is it better for it to lay horizontally or stand vertically?

---

### Post by w4ett on 2007-07-18
WELL, you can make a bootable clone of your dying drive.  Try clonezilla

[http://clonezilla.sourceforge.net/gparted-clonezilla/](http://clonezilla.sourceforge.net/gparted-clonezilla/)

---

### Post by tgalati4 on 2007-07-18
I'm not sure where the rhythmbox playcounts are stored, but you could look in /home/yourusername/.gnome2/rhythmbox.

Assuming you get your /home backed up properly, your playcounts should be OK.

---

### Post by vegetable on 2007-07-18
> **tgalati4 said:**
> Those would be called Hitachi "Deathstars".  At least you have a warning.  If you get a new disk, spend the time to do a zero-write to the drive to break it in and ensure that the entire drive is writeable.  Quality control is poor these days.

yup, i've had this happen to me with the same drive. laptop HD's are too fragile IMO, i just can't wait untill solid state drives come out. seriously.

---

### Post by cmmike1 on 2007-07-18
Alright guys. I installed the "Simple Backup Config/Restore" tool available in the Add/Remove Applications. I've used it to backup my /home  to my external hard drive. Now after i do a clean install all i should have to do is install this application and restore from my external and my comp should go back to it's past state correct? I really appreciate what everyone has said to me and i would do the live cd option but my computer won't run live cds unless i remove my video card because i have an onboard intel card. Luckyily Ubuntu Studio helped me around that because it was a text install. Thanks for all the help.

---

### Post by w4ett on 2007-07-18
Why not download the alternate install cd and use it? then restore your /home

---

### Post by cmmike1 on 2007-07-18
i could do that too. but after i did the install all i have to do is install the restore app and it should restore my old /home right?

---

### Post by w4ett on 2007-07-18
That is correct.

---

### Post by cmmike1 on 2007-07-18
> **w4ett said:**
> That is correct.

thank you so much for all your help. you saved me all the trouble of configuring my comp all over again. thanks again.

---

### Post by w4ett on 2007-07-18
No Problem....If you have any other questions, just ask... :)

Good Luck

---

### Post by cmmike1 on 2007-07-21
Well i did a clean install of Ubuntu Studio because the other alt install cd wouldn't work. Thne i installed the back up software and went ahead and backed everything up. Now i have a new problem. I have all these new programs and none of my old ones show up. I think all of the data is backed up and restored to my /home folder but it says the programs are not installed. So i went to synaptic to install them again but they are all checked off. Now what i'm doing is just going to reinstall all the packages from synaptic and hopefully this will work. If not I will just start from scratch. :-|

---


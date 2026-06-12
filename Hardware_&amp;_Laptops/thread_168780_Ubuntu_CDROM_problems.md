---
title: "Ubuntu CDROM problems"
date: 2006-05-01
forum: Hardware &amp; Laptops
---

### Post by quincyjones on 2006-05-01
Hey, 
I'm having some really strange CDROM problems. My CD/DVD RW drive in my new Dell Inspiron 1300 laptop only reads maybe 1 out of 5 data CDs or DVDs. It reads audio CDs or video DVDs no problem. Many CDs it'll read but not recognise any of the files, it puts "????" for filenames. If I put these same files onto my memory stick, they work fine. Some CDs it'll sometimes read and sometimes not. **I don't think it's the drive itself because in windows it reads everything.** Most of these CDs were writen on my old PC with Nero in windows XP, a few writen with windows XP itself. They all read fine in windows and on other computers. ***Origional pressed data CDs give the same problems.***

PLEASE HELP:confused:

---

### Post by Sef on 2006-05-01
I would say that the way the data was written to the cd is the reason ubuntu can't read them.

---

### Post by barisurum on 2006-05-06
> I'm having some really strange CDROM problems. My CD/DVD RW drive in my new Dell Inspiron 1300 laptop only reads maybe 1 out of 5 data CDs or DVDs. It reads audio CDs or video DVDs no problem. Many CDs it'll read but not recognise any of the files, it puts "????" for filenames.

I have the same strange problem. but the cd's that ubuntu cannot read include the cd's I created with K3B.. I think it is a different problem. a bug or something. or do we need to upgrade somethin. Please help because its a serious problem thanx.:confused:

---

### Post by barisurum on 2006-05-09
> I'm having some really strange CDROM problems. My CD/DVD RW drive in my new Dell Inspiron 1300 laptop only reads maybe 1 out of 5 data CDs or DVDs. It reads audio CDs or video DVDs no problem. Many CDs it'll read but not recognise any of the files, it puts "????" for filenames.

Any solutions please?

---

### Post by quincyjones on 2006-05-09
I've since installed windows on a spare partition on the same Inspiron 1300 and I can report that all my CDs work on it (windows). I can open the CDs in windows and then move the data over to Ubuntu!
What's up with this? Quite annoying... :-|

---

### Post by quincyjones on 2006-05-28
I figured out the problem, when I push the eject button on my laptop, the tray opens and the icon for the cd/dvd disappears from my desktop but I think Ubuntu does not actually unmount it, so then it doesn't read the new disk! If I instead right click on the desktop icon and eject the disk that way, then insert a new disk, it works perfectly (mounting & ejecting from terminal also works every time). I got the functionality of my laptop eject button from automatix, I guess this may be a bug with Automatix.

If you have a similar problem and the above doesn't help, I'd read up about mounting/unmounting from terminal and about your *fstab* file.
;)

edit:
I've done some research and I'd suggest not using the hack for getting the eject button to work. Check it out for yourself but apparently it can't make the drive unmout and your system can thus get unstable etc.

---


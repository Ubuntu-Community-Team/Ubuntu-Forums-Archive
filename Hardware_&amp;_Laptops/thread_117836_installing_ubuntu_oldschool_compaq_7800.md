---
title: "*installing ubuntu oldschool compaq 7800*"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by kruz on 2006-01-15
this is an old compaq and im wondering
i cant get into the bios
ive tried EVERY possible combination
i read somewhere that compaq's have their bios on the hardrive
maybe its gone? 
im not sure

but my plan is to use a USB drive to install ubuntu, but it obviously isnt hitting the USB cdrom before windows, therefore not booting


any help would be greatly appreciated
thanx
kruz~

---

### Post by mips on 2006-01-15
As far as i can recall there was a small non-dos partition at the beginning of the HD that held the bios files. The info was still on the motherboard but the software to access it was on the hd.

You should be able to get it of the compaq website and reinstall it.
[http://h20180.www2.hp.com/apps/Lookup?h_lang=en&h_cc=us&cc=us&h_page=hpcom&lang=en&h_client=S-A-R163-1&h_query=7800&submit.x=11&submit.y=8](http://h20180.www2.hp.com/apps/Lookup?h_lang=en&h_cc=us&cc=us&h_page=hpcom&lang=en&h_client=S-A-R163-1&h_query=7800&submit.x=11&submit.y=8)

---

### Post by kruz on 2006-01-16
thanks man ill try it
i hope its under 1.44 megs so i can fit it on a floppy
or im screwed

---

### Post by mips on 2006-01-17
They usually made it so you could fit it on one or more 1.44mb stiffies.

---

### Post by Brian Smith on 2006-01-17
I sucessfully installed Breezy on one of these yesterday.
If you don't have a cd or dvd drive for the machine, you may be in trouble.
Even when you get into the special Bios partition, there is no way to select USB boot devices.  

You can get the floppies that will let you access the bios in two flavours:

one that will allow you to create the partition and programs on the partition
- or -
one that will access the bios using hte same programs straight from the floppy

you will have to be careful not to delete that funny bios setup partition if you choose to install it.

I did, but haven't had to access that partition since installing Ubuntu (and about 3 other distros on the way here....)


You may have problems with the display once you do get it installed, let me know if you do, I can help you work around them, they are minor.

---


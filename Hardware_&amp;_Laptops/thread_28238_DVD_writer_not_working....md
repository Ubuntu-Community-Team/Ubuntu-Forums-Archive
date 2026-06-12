---
title: "DVD writer not working..."
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by robza on 2005-04-19
hi
my dvd-ram drive (LG GSA-4082B) is not working. it's attached as ide secondary master, with a cd-rw as secondary slave and two hard disks on the primary channel.

i can't see /dev/hdc, but have /dev/hda*x*, /dev/hdb*x*  and /dev/hdd...

can anyone make any suggestions? why would hdc just not show up?

the drive works fine under windows, so it's not broken...

thanks
rob

---

### Post by jennhi on 2005-10-04
Hi everyone! I've got a Hammer DVD-RAM and am also having trouble getting this drive detected and mounted. Does anyone have any suggestions as to how to get it to show up?

Thanks!
jennHi

---

### Post by robza on 2005-10-05
Hi jennHI
After a lot of asking around on other forums, I got very little useful information. I ended up just messing with the jumpers a bit, and all was good - I set both my DVDRAM and my CDRW (on the same IDE channel..) to cable-select, and it magically started working - I just had to put a disc in and it popped up on my desktop, as expected.
Hope this is helpful :)
rob

---

### Post by jennhi on 2005-10-05
Hi Rob! Can you tell me how you set them to cable-select? Is it that switch in the back of the drives themselves or something I can do in system administration?

Thanks!
Jenn

---

### Post by codejunkie on 2005-10-05
[QUOTE=jennhi]Hi Rob! Can you tell me how you set them to cable-select? Is it that switch in the back of the drives themselves or something I can do in system administration?

Thanks!
Jenn[/QUOTE]
to set it to cable select you have to change the jumpers on the back of the drive.

---

### Post by robza on 2005-10-05
codejunkie beat me to it ;) 

Yup, back of the drive - the manual for the dvd burner should have more info if you need it. I don't guarantee this will work for you, but it did for me, so it's worth a shot :)

rob

---


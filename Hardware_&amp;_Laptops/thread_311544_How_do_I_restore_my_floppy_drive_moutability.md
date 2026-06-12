---
title: "How do I restore my floppy drive moutability?"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by lukon on 2006-12-03
My floppy drive no longer shows up in Dapper Drake nautalis file browser. And it used to.

Since I'm a newbie, I don't know how to fix this.

Here's an interesting thing I discovered, a clue:

When I examine my drive array using the "Disks" GIU at "System>Adminitration>Disks" I see the floppy there with a big icon on the left side. If I click the icon, the information window shows information about one of my hard drives instead of about a floppy drive. This is messed up. 

Also, my /dev/fd0 file is empty.

I suspect this got all fouled up because I installed an additional IDE drive on my sound card IDE controller, a controller that Windows98SE recognizes (on this dual boot system), but which ubuntu does not.

I'm ok with ubuntu failing to recognize these other drives. But I'm not ok with ubuntu getting confused about the drives it CAN recognize when I add more drives that it CAN'T recognize.

Whatever. So does anyone know how I can fix this?

---

### Post by lukon on 2006-12-03
The thing with the "Disks" GUI showing a hard drive description for my floppy appears to be simply a failure of the GUI to refresh part of the information when I switch among drives to display. When I click on floppy, it just continues to show at least the main information about whatever drive I had just been looking at before the floppy.

---

### Post by lukon on 2006-12-03
Ok.

Problem solved by looking at other threads.

---


---
title: "Cd is not detected automatically by Thunar file manager"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by jis on 2006-07-19
I have got a CD-ROM drive and a CD-RW drive (Samsung CD-R/RW SW-252S) in my computer. When I put in a disc in the former one, there comes an item of that  disc to the left column of Thunar file manager and I can click the item to (mount automatically) and browse the contents of the disc. But, the latter drive does not have the similar desired effect on Thunar, if I insert a disc to that drive; instead I have to mount the drive in command line. On the other hand, when the plain CD-ROM drive has a disc in, the drive keeps making noise even if it is not used, which is not desired. Is it possible to get the other drive detected and the other quiet when it is not used.

---

### Post by zxee on 2006-07-19
I don't know why the cd drive continues to spin but to the mounting issue I would compare or post the fstab entries for those two drives. I have both a reader and rw optical drives on the 2nd IDE channel of my computer's mainboard and both automount when media is inserted.

Note: I was aware that you were using XFCE because of the reference to thundar, but you did post this in ubuntu rather than xubuntu. I don't know if this problem is related to XFCE since I'm not using that WM.

---

### Post by jis on 2006-07-20
Well today the CD-RW-drive did not even open by pressing the drive's button even if there was no media inserted. Soon after I tried several times pressing the drive's button, the computer stopped responding to keyboard and mouse. The same computer has stopped responding several times before, but I am not sure, if it is related to the CD-RW drive. Very confusing. Maybe this Pentium III computer is getting old (although I have had it only for about a month). But the CD-RW drive is about two years old and has been working perfectly with my older Windows PC.

After reboot, Thunar started autodetecting media in the CD-RW drive. Yesterday it did not autodetect, with same fstab settings, although it did autodetect media in the other drive. Now also media in CD-RW is autodetected even if I remove/comment the row corresponding the CD-RW in fstab.

Sorry, is there separate forum for xubuntu?

---

### Post by K.Mandla on 2006-07-21
I would suspect the drive before anything else (and that's not a cop-out, I swear). 

The drive shouldn't eject with the button. As I understand it, Linux locks that shut. There are ways to turn it back on; Automatix has (had?) that as an option a while back. 

Any chance it's the CD?

---

### Post by jis on 2006-07-21
In my experience I can now eject with drive's button, if the device is not mounted. And I can not mount cdrom if the drive is empty.

I don't think it is the CD. If I remember right I used same CD with different results before.

---

### Post by jis on 2006-07-21
The cd-rw drive (and my computer altogether) works after cold boot. But after some time I can not open the 
drive by the button anymore.. and eventually the whole computer stops responding. Computer "warns" me before by stopping responding for short time. Then I tried "quit restart" immediately, but computer could not restart further than checking memory. Led indicating drive activity is constantly on. I can restart only by swiching power off and on. This reminds me of bad old Windows.

---

### Post by jis on 2006-07-21
Last time the drive activity led of the computer was not on after my computer stopped responding. 

This time the cr-rw drive's button works, but if I put a media in, xubuntu does not autodetect the media. Media in the other drive is autodetected. So it is again like in the original posting. At least computer continues to respond to keyboard and mouse this time.

---

### Post by jis on 2006-07-21
> **zxee said:**
> I have both a reader and rw optical drives on the 2nd IDE channel of my computer's mainboard and both automount when media is inserted.


My reader and rw are also on the 2nd IDE channel, but does it matter which is master and which is slave? I suppose the master should be connected to the end of the cable..

---


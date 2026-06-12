---
title: "GParted and now my comp wont boot GRUB Error 17"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by omkarwagh on 2007-04-30
Im a new user of linux and ubuntu and i fell totally in love with it. So I wanted to convert an ntfs data drive into extending the root partition of ubuntu.

on reading up in the archives of this forum i saw that i could use gparted to resize my root partition without having to do a clean reinstall. this did not work out as expected however and now grub gives me an error message number 17 and doesn say anything else at all.

most of my important data is backed up but there is still some that i forgot to back up. can anyone help me out here?

---

### Post by omkarwagh on 2007-04-30
forgot to give my drive specs...
i have a lappy with a 40GB hdd. i had windows and ubuntu on 10GB partitions and a 20GB ntfs data partition.
i tried to resize the ubuntu partition into 30GB keeping 10GB for xp but i guess ive more or less screwed up my comp.
help a noob please. thanks in advance.
omkar

---

### Post by koshari on 2007-04-30
just run grub again off a live disk and it will update the conf file, 

see here.

[http://johnny.chadda.se/2007/02/17/restore-grub-in-ubuntu-after-installing-windows/](http://johnny.chadda.se/2007/02/17/restore-grub-in-ubuntu-after-installing-windows/)

---

### Post by omkarwagh on 2007-04-30
Thanks. Now at least the brub selector screen loads up. however i am still not able to run ubuntu.
it now says Error 17. Unidentified file system

but at least now i can run windows. can someone help me out here???

---

### Post by DJiNN on 2007-04-30
> **omkarwagh said:**
> Thanks. Now at least the brub selector screen loads up. however i am still not able to run ubuntu.
it now says Error 17. Unidentified file system

but at least now i can run windows. can someone help me out here???

If you have (had) a separate /home partition, then why not just re-install Ubuntu? All you have to do is tell it what partition you want to use as the /root (Signified by just a / )  partition, and then tell it which one is /home partition, and remember DON'T check the box that tell's it to format the /home partition, only the /root, and you should be good to go......

Once it's installed, it should redo the Grub file on your MBR for you, pick up whatever other OS's that you have, & all your data & settings that you had before will still be the same (You'll have to obviously re-install whatever extra progs that you were using also)

This is assuming that you were of course running a separate /home partition..... if you were NOT doing it that way & it was all on the same partition, then you'd have to do it a different way. :)

DJiNN

---

### Post by omkarwagh on 2007-04-30
unfortunately i din have a seperate /home partition.

but anyways i got the problem fixed now. what had happened was that after deleting the ntfs partition either GParted changed the name of the linux root partition to hda5 or it changed the grub menu.lst file and made it point to hda6. hda6 being the swap partition.

thus after installing grub again, i also had to make this change in the menu.lst file using the ubuntu live CD. now both os's are working perfectly. :)

hope this helps someone else and thanks for the help guys.
omkar

---

### Post by DJiNN on 2007-04-30
> **omkarwagh said:**
> 
thus after installing grub again, i also had to make this change in the menu.lst file using the ubuntu live CD. now both os's are working perfectly. :)


Hey, that's great news..... nice one. I've had that happen before & it's good to hear that you've got it sorted.  :)

DJiNN

---

### Post by EXCiD3 on 2007-05-03
I had Error 17 come up whenever i had my external usb hd turned on before booting. Grub would load and then display the error. I finally realized it after .5 hour trying to figure out the problem and deciding i didn't need that drive on...lol

---


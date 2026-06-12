---
title: "Win10 went bad came back to Ubuntu. Need help"
date: 2017-05-08
forum: Hardware
---

### Post by John_C_Brady on 2017-05-08
Ok so Im sure this is post a million times. My apologizes. So I was running a legit copy of Windows 10 professional. It went south so I installed Ubuntu 17.04. I am using an external hdd enclosure with 2 drives in it. I HAVE to be able to access them. They are showing up in the "disk" app but the mount option is greyed out. I do NOT have another way to pull the info off the drives to format for linux. Is there a work around? Please help.

---

### Post by oldos2er on 2017-05-08
What file system(s) are used in these hard disks? If they are NTFS you may need Windows to repair them.

---

### Post by mastablasta on 2017-05-09
if they are NTFS you can download or create Windows repair disk on another pc put chkdsk on it and then run it: chkdsk /r

to repair the drives.

anothe rotpion would be to use Windows 10 safe boot mode or repair mode and use that to repair the drives.

---

### Post by sp40140 on 2017-05-09
Are you trying to fix windows install or just want to mount the drives on ubuntu?
Do you have two drives in one enclosure?
If so, have you tried removing one? Just to try it out? 
Have you tried to manually mount them (using elevated privileges : "sudo")?

---

### Post by John_C_Brady on 2017-05-09
It is a dual hdd enclosure. I have NOT tried to remove one to see yet. And Ive also not tried the sudo command. I am going to try to repair the drives in windows (on my laptop) and then see if they will mount on Ubuntu (PC).

---

### Post by John_C_Brady on 2017-05-09
ok so Im not sure how it works now but it does. I think it MIGHT be the fact that I was using the USB3.0 slot on the back of my PC instead of the 2.0. After I inserted it into the 2.0 it cam right up with no issues. Thanks guys for the help. I love Ubuntu and I'm glad to be back on it.

---


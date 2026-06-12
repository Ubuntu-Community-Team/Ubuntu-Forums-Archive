---
title: "Problems mounting HDDs"
date: 2008-03-06
forum: Hardware &amp; Laptops
---

### Post by darien42 on 2008-03-06
Hey everyone,

I seem to be having a problem with mounting some of my HDDs.

I have 5 HDD in my computer and only two of them are mounting into Ubuntu. I am running Ubuntu Ultimate 1.7 with all the latest updates, but something seems to be amiss here. 

I have the NTFS Config application and I have run it. The only problem is that the drives wont seem to mount. When I click on the drives, I get the following message...

Cannot mount volume
You are not privilaged to mount the volume *drive name*

I find this odd due to the fact that I am the only user of the system and I have full administrative access to the computer. 

Does anybody know what I can due to mount my drives so that I can use them

Thanks,
Andy

---

### Post by ryanhaigh on 2008-03-06
Try mounting the drives from the terminal, that will probably give you a better error decription. From my experience it is likely caused by the ntfs drives not being cleanly unmounted in windows/ubuntu, ntfs3g suggests doing a checkdisk on the drive under windows and then it should mount. You can also force the drive to mount. Have a look at the manual page for ntfs-3g for some more info. Just go to System>Help and search for ntfs 3g or use man ntfs-3g from a terminal.

The best/easiest thing to do is to boot into window, check the drives for errors and reboot into ubuntu.

---


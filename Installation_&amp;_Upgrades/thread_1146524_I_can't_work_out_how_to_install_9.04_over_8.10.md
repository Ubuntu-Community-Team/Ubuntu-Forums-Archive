---
title: "I can't work out how to install 9.04 over 8.10"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by Macr237 on 2009-05-02
Sorry guys for sounding like a numpty, but I can't work out how to install 9.04 over 8.10. I tried running the disk and it wants to run wubi.exe, which I know it can't and then I tried rebooting the computer from the CD-Rom and still no luck. Is there a way to do it, without having to download it a third time?
The first time died half way through, using the upgrade manager.

---

### Post by ajgreeny on 2009-05-02
I think you just go through the normal install, but at the partitioning page choose **NOT TO FORMAT** the partition(s) by unchecking the boxes.  That way all the system files will be overwritten instead of formatted and then installed.  I have no idea how successful it would be if you have added a lot of apps that are not on the install CD, so would think it easier to start fresh and just backup all your data and do a clean install of 9.04.  I've always done clean installs and never had a glimmer of a problem at that stage.

---

### Post by Macr237 on 2009-05-02
Ah, I don't think we understand each other. I can't get it to start at all, there is no instal.exe like I am used to with M$ winblows. So how do I get it to work?

---

### Post by ajgreeny on 2009-05-03
You need to boot from the CD not run the CD from an existing ubuntu install.  It will look just like the first install you did, but when you get to the partitioning stage follow my suggestions above, and do not format the partition, simply overwrite it.

---

### Post by Macr237 on 2009-05-04
And how do I do that? Every thing I've tried has failed and I am only new to *nix.
TIA

---

### Post by astr365 on 2009-05-04
> **Macr237 said:**
> And how do I do that? Every thing I tried has failed and I am only new to *nix.
TIA

You should be able to boot from the Ubuntu CD (put it into your drive and restart your computer). When the system is started it should now show you the new Ubuntu desktop. There you should find an icon labelled INSTALL. Double-click this and the install will start. Then, as mentioned before, it may be a good idea not to your partitions to keep your data.

---

### Post by raananb on 2009-05-04
If you have a fast internet link, then just upgrade your 8.10, it worked faultlessly for me.

See link below for instructions

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Macr237 on 2009-05-04
> **raananb said:**
> If you have a fast internet link, then just upgrade your 8.10, it worked faultlessly for me.

See link below for instructions

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
If you re-read my first post, you may discern that I have already been down this route!

---

### Post by Macr237 on 2009-05-04
> **astr365 said:**
> You should be able to boot from the Ubuntu CD (put it into your drive and restart your computer). When the system is started it should now show you the new Ubuntu desktop. There you should find an icon labelled INSTALL. Double-click this and the install will start. Then, as mentioned before, it may be a good idea not to your partitions to keep your data.
Thanx, I didn't notice it on boot up, as it looked like 8.10 except for the boot screens. I will take another look.

---


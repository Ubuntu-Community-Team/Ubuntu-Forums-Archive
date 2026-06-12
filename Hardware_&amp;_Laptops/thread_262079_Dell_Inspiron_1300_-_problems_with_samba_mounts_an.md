---
title: "Dell Inspiron 1300 - problems with samba mounts and suspend"
date: 2006-09-21
forum: Hardware &amp; Laptops
---

### Post by GlennB on 2006-09-21
Hi all,

I have a new Dell Inspiron 1300, which is working really well with Dapper, apart from one thing - it is usually connected to a LAN, with some samba shares mounted. Whenever the Dell goes into suspend or hibernate, the samba shares get 'lost'. When I wake the machine up again, it seems that Ubuntu believes the shares are still available, but doing an 'ls /mnt/point' will lead to a long delay followed by an i/o error.

Is there some way to unmount the shares in one of the suspend/hibernate scripts, then remount them at resume time?

At the moment, i have to resume the machine, then manually umount the shares and remount them again - if possible, I'd like to automate the process.

Thanks for any suggestions.

Regards,

Glenn.

---

### Post by xyz on 2006-09-21
Hi GennB,
I have a Toshiba Satellite A 40 and I followed the following guide to make Suspend Hibernate work the way it should:
[http://www.linux.com/article.pl?sid=06/05/24/1716222](http://www.linux.com/article.pl?sid=06/05/24/1716222)
Also:
[http://packages.ubuntu.com/dapper/utils/hibernate](http://packages.ubuntu.com/dapper/utils/hibernate)
Hope it helps. It did do the trick for me. Good luck.

---

### Post by GlennB on 2006-09-26
Hi,

Sorry for the delay, and thanks for the information. Unfortunately, while I now have Suspend and Hibernate working, the samba mounts still get broken when the notebook goes into Suspend.

I think what I need to do is find out where in the suspend scripts I can safely put a 'umount' command, and where in the resume scripts I can place the corresponding 'mount' command to remount the shares.

Ironically, I was expecting wireless networking to give me problems with suspend/hibernate, but this seems to work perfectly. 

Regards,

Glenn.

---


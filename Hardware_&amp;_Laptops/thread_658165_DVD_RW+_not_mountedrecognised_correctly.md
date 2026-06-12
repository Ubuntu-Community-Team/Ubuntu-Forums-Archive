---
title: "DVD RW+ not mounted/recognised correctly"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by elope on 2008-01-04
Dear All,

After a lifetime of Windows I have finally made the step to Ubuntu. I'm mighty impressed about the performance, running on an old HP Compaq nx9105. 

Must say that it has been quite tricky to get started fixing to mount partitions etc, getting the Nvida to run etc. but now finally getting there!

:popcorn:

**THE PROBLEM....**

I tried to surf the forum but I could not find anything that would actually help me.

I have one annoying problem which still exists. My DVD-RW plus is not running properly.
CD burning ok, reading DVD's ok. But the RW+ is not working.

I have checked the hardware info and rw plus is set to false.
Drive is recognized as SD-R6252.

Fstab mount looks as following...

# /dev/hda6
UUID=81833956-7291-4525-b8cb-99ae7d4788aa none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


A question I have as well, to understand the process. Is the RW+ set through a command in the Fstab, or is this set elsewhere? 

Thanks in advance!

Sincerely,
Johan

---

### Post by logos34 on 2008-01-04
You can't burn DVD_+_RW?  Is that the problem? What about dvd-r or dvd+r, can you burn those?

fstab entry for optical drive looks exactly as it should.  

What does 

ls -l /dev | grep dvd

show?

---


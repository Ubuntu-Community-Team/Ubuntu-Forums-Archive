---
title: "Recover win7 raid0 with ubuntu"
date: 2013-09-02
forum: Hardware
---

### Post by scotty018 on 2013-09-02
Hi everyone, I am a ubuntu newbie so i hope here is someone to help me.

My mainbord is broken. I had a 2disk raid 0 configuration so now i have a big problem.
After googling if ound several topics about recover raid 0 data with ubuntu.

But how?

I installed a new mainbord and installed on a new disk ubuntu 12.04.
installed the disk utility.
connected my 2 raid disks.
In the disk utility i can see the 2 disk. they are stated healthy. i see the partitions on the disks but i can't access the disk or save any data.

what are the next steps to take?

---

### Post by lukeiamyourfather on 2013-09-02
I've never tried it but there's a guide here.

[https://help.ubuntu.com/community/Mount%20Windows%20Raid%200%20Volumes%20Howto](https://help.ubuntu.com/community/Mount%20Windows%20Raid%200%20Volumes%20Howto)

---

### Post by scotty018 on 2013-09-02
i managed to fix it!!

i downloaded dmraid.

after that i went to the terminal and executed the commandline: sodu dmraid -ay

after that i could access all partitions

---


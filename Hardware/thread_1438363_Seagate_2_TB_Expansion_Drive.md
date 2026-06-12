---
title: "Seagate 2 TB Expansion Drive"
date: 2010-03-24
forum: Hardware
---

### Post by kurtisnathan on 2010-03-24
I bought a Seagate Expansion Drive, 2 TB. One of its features is that after a certain amount of time, it goes into some kind of energy save mode, where it's essentially unreadable, but still detectable. The problem is that I can't get it back online. I also can't unmount it then mount it, because after unmounting it, I can't see it anywhere. The only way I can use it again is if I unplug its power suply, and reconnect it. 

I'm assuming that I wouldn't have problems with it if I were using Windows, since it's apparently made for Windows.

Does anybody know any way, through terminal or other means, to get the thing back online from energy save mode without having to unplug it?

Thank you very much.

---

### Post by garvinrick4 on 2010-03-24
> **kurtisnathan said:**
> I bought a Seagate Expansion Drive, 2 TB. One of its features is that after a certain amount of time, it goes into some kind of energy save mode, where it's essentially unreadable, but still detectable. The problem is that I can't get it back online. I also can't unmount it then mount it, because after unmounting it, I can't see it anywhere. The only way I can use it again is if I unplug its power suply, and reconnect it. 

I'm assuming that I wouldn't have problems with it if I were using Windows, since it's apparently made for Windows.

Does anybody know any way, through terminal or other means, to get the thing back online from energy save mode without having to unplug it?

Thank you very much.What if you label it in gparted say to "seagate"
Then when you want to mount it.
To Make a Directory a one time thing for your OS.
sudo mkdir /media/seagate

To mount drive: Use your own sdb1 (what ever it is in your machine) fdisk -l (small L)
will tell you.
sudo mount /dev/sdb1 /media/seagate

To unmount:
sudo umount /media/seagate    (that is not a typo it is umount)

---

### Post by kurtisnathan on 2010-03-25
Thanks a bunch! Worked.

---


---
title: "partition problems"
date: 2008-07-29
forum: General Help
---

### Post by xaocan on 2008-07-29
I've formated one of my partitions with Gparted partition editor. I couldn't access this partition so I deleted it and made a new 1 but i ran out on this problem:
[[IMG]http://img525.imageshack.us/img525/1934/erormv9.th.jpg[/IMG]](http://img525.imageshack.us/my.php?image=erormv9.jpg)

I can't unmount cause i have only 1 hdd. What is partition tables and how do i fix it? :P

---

### Post by falcon61102 on 2008-07-29
Are you running gparted from a LiveCD or from your Ubuntu intallation?

If you are running Ubuntu from your hard drive, you can't delete the partition that you are running from.  Use a LiveCD and boot up from that and gparted, then you can edit the entire drive if necessary.

---

### Post by forger on 2008-07-29
Were you trying to format one of your linux system partitions while you were running that system on that hard drive? (root "/", home "/home" or swap?)

Try an Ubuntu release as a live cd, use System > Administration > Partition editor from there

---

### Post by xaocan on 2008-07-29
I'm not trying to format the partition with my linux, this partition is just empty. And I'm not trying to do from a LiveCD.

---

### Post by vanadium on 2008-07-29
You will need to do it from a live CD (be very careful). The reason you could not access it as a normal user is because by default, normal users have no permissions. They must be given permissions by the root.

---

### Post by xaocan on 2008-07-29
OK, so what should I do after I log into LiveCD to make a this partition accessible for my Ubuntu user?

---

### Post by xaocan on 2008-07-29
Thx alot... I figured it out, :P

---


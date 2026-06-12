---
title: "HP Pavilion zv5000 installation problems. Please help me!!!"
date: 2008-07-26
forum: General Help
---

### Post by Jakeklausmeier on 2008-07-26
ok, so i have an hp pavilion zv5000, and i am having a problem installing ubuntu 8.04. it goes through the installation setup just fine, but when it begins partitioning the hard drive it freezes at 5% every single time. At that point it is attempting to create ext #3 in / hda5 or something like that. Does anyone have any ideas, or anything i can do? I would greatly appreciate any help you guys can give me.

Thanks in advance, 
Jake

---

### Post by 0x29a on 2008-07-28
A couple of questions: Are you setting up this machine to dual-boot? Are you using the partitioning scheme suggested by the installation?

Also, one thing you can do to rule out problems with the hard drive itself is run badblocks from the "live" session when you boot from the DVD. badblocks tests for bad sectors, which can cause the behaviour you've described. Open a terminal and type ```
badblocks -svn /dev/hda
```This will run a NON-destrutive test of your hard drive surface, so it's safe.

You may have to type ```
sudo badblocks -svn /dev/hda
```If you do, just press enter at the password prompt. badblocks takes a couple hours or more to run depending on the size of your hard drive, but very much worth the wait if it's going to prevent headaches down the road.

For what it's worth, I have a zv5000 and the only problems I've had so far was not using ndiswrapper to get the wireless working, and flashplayer seemingly causing trouble with my preferred browser, but I haven't had time to completely delve in to that issue yet.

Hope this helps.

Andrew

---


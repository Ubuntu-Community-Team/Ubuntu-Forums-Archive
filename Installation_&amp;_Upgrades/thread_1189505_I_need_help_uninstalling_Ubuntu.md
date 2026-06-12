---
title: "I need help uninstalling Ubuntu"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by vladislavua on 2009-06-16
I use Windows XP and I downloaded Ubuntu a while back. Every time I started the computer a menu would come up asking me which OS to start up. Now I want to uninstall Ubuntu and don't want that menu to come up.

Can I use add/remove programs on Ubuntu?

Thanks,

Vladislav

---

### Post by merlinus on 2009-06-16
You will need to delete the ubuntu partitions, and then use your xp install disk.  Select restore or repair, and then fixmbr (or fix boot record).

If you do not have the cd, then supergrub will help.

---

### Post by dewboi on 2009-06-16
If you installed Ubuntu using Wubi inside windows, you can uninstall Ubuntu via windows just like any other program. But why? Not satisfied with Ubuntu?

---

### Post by raymondh on 2009-06-16
And if you change your mind and decide to keep ubuntu ... download (from synaptic or thru terminal) **startup manager**.  From there, you can set which OS to default to as well as the time it takes to boot.  By keeping Ubuntu... if ever your windows install crashes, you still have ubuntu to back you up :)

To follow up on merlin's post.... should you decide to get rid of ubuntu... after you delete the ubuntu partitions (/ and swap) and fix the mbr/boot, don't forget to extend the windows partition to take up the space vacated by Ubuntu.

Good luck.

---

### Post by vladislavua on 2009-07-11
> If you installed Ubuntu using Wubi inside windows, you can uninstall Ubuntu via windows just like any other program.

I installed Ubuntu when I was running windows. I didn't do it in the boot menu and from the disk. Ubuntu is a program in windows list. So I can use add/remove program?

So can I do it that way?

---

### Post by raymondh on 2009-07-11
> **vladislavua said:**
> I installed Ubuntu when I was running windows. I didn't do it in the boot menu and from the disk. Ubuntu is a program in windows list. So I can use add/remove program?

So can I do it that way?

Yes.  See the wiki and browse to UNISTALL:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Be careful when you edit the boot.ini file.  Only delete the ubuntu/wubi line.

Good luck.

---


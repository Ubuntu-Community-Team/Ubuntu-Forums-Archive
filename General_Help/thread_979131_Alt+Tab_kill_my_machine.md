---
title: "Alt+Tab kill my machine"
date: 2008-11-11
forum: General Help
---

### Post by jyuan86 on 2008-11-11
I've upgraded to the latest version 8.10 of Ubuntu. But I've a quite strange problem that is when you press alt+tab combination key to switch between different applications, the computer is dead. You can't ever redo this alt+tab because the computer is totally dead no matter what keys or buttons you press. The only way of getting out of this is taking out the battery and rebooting the system.This makes me crazy!

Does anybody have a situation like me? I'm already missing the 8.04.

Anyway, I'll appreciate your help if there's any. I'm almost desperate:(

---

### Post by phantomgunex on 2008-11-11
i not having this problem though are you sure it was a clean upgrade???

---

### Post by jyuan86 on 2008-11-11
> **phantomgunex said:**
> i not having this problem though are you sure it was a clean upgrade???

What do you mean by a clean upgrade? I'm a new user of linux.

---

### Post by phantomgunex on 2008-11-11
Sorry for the late reply... Was there any errors when upgrading though those should prevent you from upgrading. The new released is just new maybe there are still bugs like my com always hangs sometimes for no reason. Lets just wait for a new release.

---

### Post by jyuan86 on 2008-11-11
> **phantomgunex said:**
> Sorry for the late reply... Was there any errors when upgrading though those should prevent you from upgrading. The new released is just new maybe there are still bugs like my com always hangs sometimes for no reason. Lets just wait for a new release.

After the upgrade, I've checked out the version using System>About Ubuntu>Version and release number. But it doesn't display any version at all. 
Is there any methods to reupgrade or even downgrade the ubuntu? Just out of curiosity!:)

---

### Post by 5ulo on 2009-08-20
Sorry, that i had open this thread again.. i have the same problem in 9.04 with compiz and kernel 2.6.29 and earlier... but when i disable compiz, all works fine. Can i find the problem somewhere in the log files? Thanks

Sorry for my bad englis :P

---

### Post by XCan on 2009-08-20
Have you checked your drivers, System -> Admin. > Hardware Drivers? I bet you're sitting on an AMD or Intel chip.

---

### Post by 5ulo on 2009-08-21
This is my configuration

```
http://www.cdfreaks.com/hardware/product/82682-Toshiba-Satellite-L300-1EF.html
```

No proprietary drivers are in use on this system... hmm... Compiz is fast... but the combination alt-tab is bad

---

### Post by P4man on 2009-08-21
> **XCan said:**
> Have you checked your drivers, System -> Admin. > Hardware Drivers? I bet you're sitting on an AMD or Intel chip.

His problem is due to the intel 4500 integrated graphics. AFAIK, that driver was borked for jaunty and they had to disable desktop effects. Im not sure how well its fixed by now. Perhaps try updating ubuntu or try some newer drivers. Or disable compiz until its fixed.

---

### Post by 5ulo on 2009-08-21
I had updated kernel from official ubuntu 2.6.28-15 (from repo autoupdate)... all works fine but compiz was sometimes slow (e.g. alt-tab, expo...). Then i found somewhere here, that i need to upgrade to newer kernel 2.6.30 from this site

```
http://kernel.ubuntu.com/~kernel-ppa/mainline/
```

When i found this "bug" in 2.6.30, i try to boot at 2.6.29... there was the same bug... The newes intel graphic adapter is build in the kernel... or not?
Now i have disabled compiz and active metacity window manager.

---

### Post by P4man on 2009-08-21
I suppose you've already seen this ?
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Either way, there is only 2 things I can recommend: first, file a bug report. If no one does, things dont get fixed :) Secondly, unless you want to try out the bleeding edge route described in the link above, either wait for karmic, or ironically, go back to intrepid.

---

### Post by 5ulo on 2009-08-21
Thanks.. i'll try it and let you know.

---


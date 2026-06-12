---
title: "uninstalling ubuntu 7.04"
date: 2008-07-14
forum: General Help
---

### Post by m4k4v3l1 on 2008-07-14
I had some connection problems to internet with ubuntu , so I want to uninstall it , I installed it from CD and now I want to delete it , I have windows XP and ubuntu installed in the same partition.

---

### Post by Jim! on 2008-07-14
What? Is it even possible to have both OS's installed on the same partition? Can you please double check that?

---

### Post by CatKiller on 2008-07-14
If you used Wubi to install it from within Windows then you can use the Windows Add/Remove Programs tool to uninstall it.

---

### Post by mcduck on 2008-07-14
Did you install with Wubi? Apart from that it's impossible to have them on same partition. On the same disk, certainly, but not on the same partition.

Anyway, there is no "uninstaller" for operating systems (unless, again, you used Wubi). To get rid of Ubuntu go to Disk Mamanement (or whatever it was called) in Windows, select the Ubuntu's partition and format it into something you can use from Windows. Or use some more advanced partition manager to merge the Ubuntu's partition(s) back to the windows partition.

Then you'll need to use the Windows install CD to boot into recovery console and run "fixmbr" to get rid of the Grub bootloader.

---

### Post by m4k4v3l1 on 2008-07-14
oh my bad I meant in the same disk , ok I'll format it. I didn't install with wubi.

---

### Post by CatKiller on 2008-07-14
Of course, you could just fix the Internet connection problem...

---

### Post by coffeecat on 2008-07-14
> **m4k4v3l1 said:**
> I had some connection problems to internet with ubuntu , so I want to uninstall it , I installed it from CD and now I want to delete it , I have windows XP and ubuntu installed in the same partition.

You posted a week ago about your internet problem and no one bothered to respond. I'm sorry about that. A couple of thoughts. Have you decided to get rid of Ubuntu 7.04 because of the problem or because you're disappointed that you didn't get a response. I've got a couple of ideas for you about your internet problem but there's no point in my posting them if you are going to abandon Ubuntu.

Also, that's a year-old version of Ubuntu so here's an idea for you. Download the latest 8.04 version of Ubuntu and install it to the partition that 7.04 is on. That will effectively uninstall 7.04. Now try 8.04 out. Maybe your internet will work; maybe it won't. If it doesn't, start a new thread and if no one responds at first, bump the thread every day or so. Be clear in your first post, give hardware details about your computer, the type of internet connection you have and whatever modem/router you might be using and I am sure someone will be able to help you.

Good luck!

---

### Post by coffeecat on 2008-07-14
> **CatKiller said:**
> Of course, you could just fix the Internet connection problem...

Or someone could have answered his first thread. I fear we have rather let him down.

Sunny Southend, eh? I was born there! :(

:wink:

**Edit:** Yikes! I've just noticed your nick. :shock: I'm off.....

---

### Post by CatKiller on 2008-07-14
> **coffeecat said:**
> Or someone could have answered his first thread. I fear we have rather let him down.

I think you're right. I'd have investigated further myself, but I had to go out. I think your suggestion to try 8.04 was a good one though. There were quite a few upgrades to the way networks are handled in the intervening time.

> Sunny Southend, eh? I was born there! :(

:wink:

**Edit:** Yikes! I've just noticed your nick. :shock: I'm off.....

I think you're safe. You're a local! :)

---


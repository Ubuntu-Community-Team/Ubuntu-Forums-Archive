---
title: "Reinstalling Ubuntu"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by mazonamt on 2009-03-09
Hi,

I recently installed Ubuntu next to XP. After having problems with Gnome not loading I decided to reinstall Ubuntu. I foolishly unallocated the Ubuntu partition using XP (thinking that GRUB uses another partition). Then running the live CD I noticed that Ubuntu didn't want to use the unallocated partition. So I reformated the it using the live CD. Following that I can't boot into XP either (receive GRUB error). Also the live CD doesn't want to install. Instead it gives me an Ubuntu console (ubuntu@ubuntu). 

Can I install Ubuntu from the console or do I need to obtain an XP cd? My goal is to keep XP and have a fresh installation of Ubuntu.

Appreciate all help I can get!
M

---

### Post by Nxion on 2009-03-10
So if I understand you correctly you are unable to boot into either Ubuntu or XP? When you say you are at a prompt, is this after the Live CD boots? or is it when you try to boot the PC w/o a Live CD?

---

### Post by upchucky on 2009-03-10
hmm a day old post, hope we caught it in time.

at the time of your post the xp install was still there, grub needed to be edited to get it to boot again, 5 minute fix. ubuntu console could have gotten ubuntu booting in safe mode then rebooting normal.

assuming you have not given up, if the above is still the case, it is a matter of editing a couple of files to get things right but need more specific details, grub error? symptoms, machine specs. ubuntu version?

---

### Post by mazonamt on 2009-04-29
Problem fixed (the brute force newbie way). Reapaired xp mbr and reinstalled ubuntu...

Thanks to both of you anyway!

---


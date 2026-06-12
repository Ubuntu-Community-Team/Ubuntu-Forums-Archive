---
title: "Ubuntu installed in Hidden Location?"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by Pauld2 on 2009-08-31
After attempting to install ubuntu drive on my flash drive, it installled all the files somewhere within my machine. Every time i boot it takes me to linux unless i select windows, when I try to download something for linux it says insufficient space. it says something about being in hd0 or something, but all devices, discs or anything that can hold data are not in my computer. Is there some way to locate the files and remove them? Ive been digging through and searching but I cant find anything.

---

### Post by presence1960 on 2009-08-31
Let's get a better look at your setup. Boot into Ubuntu with that flash drive plugged in. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by tgeer43 on 2009-08-31
> After attempting to install ubuntu drive on my flash drive, it installled all the files somewhere within my machine. Every time i boot it takes me to linux unless i select windows, when I try to download something for linux it says insufficient space. it says something about being in hd0You didn't install it to your flash drive, you installed it to your hard drive. In doing so you've apparently filled up your hard drive to the point that you can't fit anything else on it. Hd0 is your first hard drive, the one that Windows would normally be installed on.
> all devices, discs or anything that can hold data are not in my computer.That sentence makes no sense to me whatsoever.
> Is there some way to locate the files and remove them? Ive been digging through and searching but I cant find anything.Yes, there is a way but it involves more than just deleting some files if you want to reclaim the disk space for Windows.
It might be a little involved for an inexperienced user and doing it incorrectly could render your Windows installation unusable so I'm hesitant to proceed. I don't want to start something that I can't finish successfully.

tgeer

---

### Post by presence1960 on 2009-08-31
> **tgeer43 said:**
> all devices, discs or anything that can hold data are not in my computer. 

That sentence makes no sense to me whatsoever.


tgeer

+1

That's why I asked OP to run Boot Info Script. I am waiting to see the results. :P

---

### Post by tgeer43 on 2009-08-31
You're a better man than me. I'm not getting involved any further with this one. Looks like a recipe for disaster to me.

I will be monitoring, though. :wink:

Good luck,

tgeer

---

### Post by presence1960 on 2009-08-31
> **tgeer43 said:**
> You're a better man than me. I'm not getting involved any further with this one. Looks like a recipe for disaster to me.

I will be monitoring, though. :wink:

Good luck,

tgeer
That's where the Boot Info Script is great. A lot of times new users state the nature of their problem incorrectly or relay incorrect info about their setup either through ignorance or not understanding terminology. Sometimes language itself is a barrier. Boot info script eliminates all that and can show us the exact setup, even where GRUB is installed and where it points to. So we will see what the OP actually has if he/she ever runs the script & posts back.

---

### Post by tgeer43 on 2009-08-31
I believe I'll start using that when the occassion calls for it.
I can't tell you how much time I have spent troubleshooting the wrong problems due to incorrect info or lack of it altogether.

Thanks!

tgeer

---

### Post by Pauld2 on 2009-09-01
Ill check it tomorrow i'm sorta of busy and its really late. I didn't think this thread would take off so quick, when a said no data devices i meant portable, I'm running a laptop so i leave hard drive in, sorry i didnt specify earlier. My flash drive doesn't contain anything ubuntu because when i removed it it still goes into ubuntu and works properly(besides lack of space problem) My current OS is windows vista ultimate 64bit if it makes a difference.

I asumed hd0 was my flash drive because its labeled H.

I will make sure to check ubuntu settings tomorrow as early as I can.

---

### Post by steveneddy on 2009-09-01
I'm interested in this.

I will monitor this problem also.

I wasn't aware of that application.

Good call.

---


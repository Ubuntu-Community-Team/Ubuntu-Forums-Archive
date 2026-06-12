---
title: "Enabling swap after partition resize"
date: 2008-10-03
forum: General Help
---

### Post by BigAl-SA on 2008-10-03
From this thread,
[http://ph.ubuntuforums.com/showthread.php?t=691986](http://ph.ubuntuforums.com/showthread.php?t=691986)
and to some extent this help file:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
I figured out a way to re-enable the swap partition after resizing with gparted. 

(Using a console for these instructions)
1. The uuid of the swap partition was incorrect in /etc/fstab (**swapon -a** complains)
2. **cd /dev/disk/by-uuid**
3. Find the link associated with the swap partition by using **ls** and note starting sequence of numbers (4ce in my case).
4. Change back to your home directory by entering **cd**
5. **ls /dev/disk/by-uuid/4c* > swapid.txt**
6. **kate swapid.txt**
7. copy the uuid 
8. **sudo kate /etc/fstab**
9. Replace the uuid associated with the swap partition with the one copied from swapid.txt (you can first copy and paste the incorrect one, the precede it with a #)
10. Save fstab
11. **sudo swapon -a**

I hope this helps someone.

---


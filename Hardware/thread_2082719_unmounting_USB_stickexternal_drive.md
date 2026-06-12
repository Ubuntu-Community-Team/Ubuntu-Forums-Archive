---
title: "unmounting USB stick/external drive"
date: 2012-11-10
forum: Hardware
---

### Post by engine on 2012-11-10
When I was very new to linux, it took me a while to get my head round using [FONT="Courier New"]mount[/FONT] and [FONT="Courier New"]umount[/FONT]; I was relieved when right-click > Unmount came along.

Now I've installed lubuntu on a netbook, and I can't find any option at all for unmounting. Is it no longer necessary, or just well hidden? After years of carefully unmounting (on various o/s), I'd feel more comfortable if I still did it myself <g>

Thanks in advance!

---

### Post by 2F4U on 2012-11-10
If I am not mistaken, the file manager has an option to unmount removable media.

---

### Post by engine on 2012-11-28
No sign of a right-click option, nor any command in the menu bar. Where (else) should I be looking?

---

### Post by Sunon on 2012-11-28
if you just run mount in the terminal it will show you all disks that are mounted, from there sudo umount device is all you need.

---

### Post by efflandt on 2012-11-29
If you write to USB memory or other device it is important to make sure that it is finished writing before physically disconnecting it.  If it is something that has automounted it will typically have a little up arrow with line under it to the right of the partition name in file manager.  Clicking on that up arrow will umount that partition and usually other partitions on that device.  But if you clicked on that device name, it is best to click on something else first (like your home directory) before clicking on the arrow to umount a device.

Hopefully, it will tell you if it is not yet finished writing when you umount it, or if the device has an activity light wait until that stops flickering or goes off and that partition is no longer listed in file manager (or in Unity bar or desktop depending which gui you are using).

If you want to do something like repartition the device, you can use the umount command in a terminal which will umount the partition without actually disabling the device.

---

### Post by engine on 2012-12-31
> **Sunon said:**
> if you just run mount in the terminal it will show you all disks that are mounted, from there sudo umount device is all you need.

Quite correct, and thanks for the reminder. This is really not the technique I expect to have to use at the end of 2012, though!

---

### Post by engine on 2012-12-31
> **efflandt said:**
> ... If it is something that has automounted it will typically have a little up arrow with line under it to the right of the partition name in file manager.

That's what I would have expected … but there's no sign of anything like that in my file manager window.

---

### Post by vanadium on 2012-12-31
[http://ubuntuforums.org/showthread.php?t=1901625](http://ubuntuforums.org/showthread.php?t=1901625)

---

### Post by engine on 2012-12-31
No, that thread doesn't give all the information either &#8230; what I've just this minute discovered is that it seems to depend on the side pane view. If I set side pane view to Places, then there is an eject option next to the USB drive icon. If I set side pane view to Directory tree, which is the way I usually work, no eject option. Perhaps not a genuine bug, but it certainly feels like a shortcoming.

---

### Post by sudodus on 2012-12-31
Are you running Lubuntu as the tag indicates?

The default browser is pcmanfm. At least in my Lubuntu 12.04, there is an eject symbol in the left pane for each unmountable partition. For internal drives, it defaults to unmount, and for external drives it defaults to unmount and switch off (prepare for pulling out), which is the usual reason to unmount.

If you want to unmount an external partition without switching off, you can use the terminal command umount. Then it will be possible to run tasks that need the partition to be switched on but not mounted.

---

### Post by sudodus on 2012-12-31
You can check if you get better options with the more powerful file browsers Thunar and Nautilus. Install them from the repositories (sudo apt-get install ...)

---


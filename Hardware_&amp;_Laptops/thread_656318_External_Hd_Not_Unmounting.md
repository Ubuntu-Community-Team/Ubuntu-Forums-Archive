---
title: "External Hd Not Unmounting"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by chr1831 on 2008-01-02
Ive been looking through the forums and i have yet to find a working solution to unmount my external harddrive :(, everything i have is on it (its a nice 120gb one ^_^ but i don't want to just pull the power on it while its running witch is what i have had to do a few times now :(

When i tell it to unmount i get an error saying it cant unmount and it remounts it :(
-Chris

---

### Post by dje on 2008-01-02
in a terminal try:
```
sudo eject <mount point>
```
Obviously insert the mount point where it says so eg. /media/disk. hope that helps

EDIT: What is the exact error that you get when you attempt to unmount it?

---

### Post by ARhere on 2008-01-02
External hard drives will not unmount if they are being used.  You need to make sure and close all programs that *could* be using the memory and then try again.  Try going to your list of running programs and you might see a shadow copy of a program you were using that you thought you closed.  It might still be accessing the drive.  *For example, if you close Banshee it will still run in the background so you can play music*

If you are certain nothing is using the HDD and you need to unplug it, then goto your terminal and 
```
sudo umount -f /media/<your_device>
```

This [thread ]("http://ubuntuforums.org/showthread.php?t=334704")talks about your problem a little.

-AR

---

### Post by chr1831 on 2008-01-02
The drive is still spinning when i run either of the 2 commands above..., if i unmount it in windows the drive stops spinning.... :-\

-Chris

---

### Post by ARhere on 2008-01-02
> **chr1831 said:**
> The drive is still spinning when i run either of the 2 commands above..., if i unmount it in windows the drive stops spinning.... :-\

-Chris

That does not mean it is not unmounted.  Its a USB drive so even though you unmount it, the USB will still provide power.  If the drive icon disappears, then it is unmounted.

-AR

---

### Post by dje on 2008-01-02
The hard drive should stop spinning, when i use:
```
sudo eject <mount point>
```
If i switched it off without it spinning down it made a funny noise

EDIT: Have a look [here]("http://ubuntuforums.org/showpost.php?p=2761781&postcount=15")

---

### Post by chr1831 on 2008-01-02
That Worked, is there any way to make it when i right click eject to auto do that stuff?, or run the shutdown-exhd.sh when i press eject
 
-Chris

---

### Post by dje on 2008-01-02
Have a look at /home/YOUR_USERNAME/.gnome2/nautilus-scripts . Note that folder is hidden so you will have to type it in or press Crtl + H to view hidden files. Copy and paste the script into that folder and it should appear on your right click menu (under Scripts i think). Hope that helps ;)

---


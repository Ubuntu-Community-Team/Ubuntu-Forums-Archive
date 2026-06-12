---
title: "HP Mini 1000 with Ubuntu NBR and HP Mobile Drive"
date: 2009-03-02
forum: Hardware
---

### Post by petey305 on 2009-03-02
Hi Folks,

I did a search for this but didn't find an answer. Hopefully I'm not the only one.

I have a Mini 1030NR, originally purchased with windows XP, but I blew that away and installed ubuntu netbook remix on it (which i LOVE...the machine is so much faster now, making it much more usable for my purposes).

Anyway, I've got the whole thing running smoothly, only 1 issue...and this is very minor, but annoying none-the-less.

My problem is with the Mini Mobile Drive (basically a Transcend 2gb usb-type flash card that slide in a dedicated slot). 

This drive always mounts just fine automatically, but when I come back from Suspend, after the drive mounts, it launches a file folder for that drive. It's a little annoying as it something that I always have to close on return from Suspend...especially since this stick stays in the mini.

This doesn't happen at initial startup...at initial start-up the drive also mounts fine, but does not open a file folder for the drive.  That is the behavior I'm looking for, mount, but force me to open the stick if I want to view it.  I'm even fine if this is the default behavior all inserted usb flash drives...as long as they mount...I don't care if it opens a file manager automatically.

I did try going to:

    Systems -> Preferences -> Removable Drives and Media

In there, on the 'Storage' tab I have these options set/not-set:

[checked] Mount removable drives when hot-plugged
[checked] Mount removable media when inserted
[unchecked] Browse removable media when inserted
[unchecked] Auto-run programs on new drives and media
[unchecked] auto-open files on new drives and media

Did a reboot, and the behavior is unchanged.

I'm guessing maybe there is a mount option that I can set that could possibly prevent this folder from automatically opening?

Has anyone else encountered this/solved this? If not, I may just remove the drive, but I'd prefer not to (I'd rather leave it in since I have it).

By the way, I'm pretty new to linux.  I have no problem editing config files as root etc, etc, etc...but pretty much, assume I know nothing about file location, specific config files functions etc etc etc... :)

Thanks in advance!  

petey305

---

### Post by petey305 on 2009-03-03
This is solved.  A gentleman in another forum pointed me to the correct solution.  He pointed me to this post:

[http://ubuntuforums.org/showthread.php?t=974087](http://ubuntuforums.org/showthread.php?t=974087)

For completeness, here is what I did (edited instructions from the other post)

* Hit Alt-F2 and enter gconf-editor. 
* When the Configuration editor comes up, expand apps and scroll down to nautilus. 
* Expand nautilus and click on preferences. 
* On the list to the right, uncheck the box beside media_automount_open. 
* Reboot

This caused mounted flash media to not open in nautilus...including my internal flash drive upon wake from suspend...happy days! :)

Petey

---


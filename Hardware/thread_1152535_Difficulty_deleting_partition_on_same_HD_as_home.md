---
title: "Difficulty deleting partition on same HD as /home"
date: 2009-05-07
forum: Hardware
---

### Post by tsdemented on 2009-05-07
I need to delete my partition at mount point /windows (sda5), but it is on an HD with another partition at mount point /home (sda7). I tried using fuser by typing "fuser -km /home", but it killed Gnome and brought me back to the login. When I logged back in, processes were still running on /home (sda7), disallowing me from deleting my /windows (sda5) partition.

So how would I go about deleting my /windows (sda5) partition?

Thank you,

Tom

---

### Post by sgosnell on 2009-05-07
I would use gparted.  You can run it from System/Administration/Partition Editor.  If it's not installed for some reason, you can install it from Synaptic or "sudo apt-get install gparted" in a terminal.

---

### Post by tsdemented on 2009-05-07
That is what I am using. That's actually how I came upon fuser, because it recommended using it to see which processes were using my /home partition.

Thanks, though; any other suggestions?

---

### Post by sgosnell on 2009-05-08
Do a cold reboot, then try.  If you can't delete the partition, post a screenshot of the gparted window.  It's possible to have logical partitions within extended or primary partitions, and you have to delete them in the correct order.

---

### Post by tsdemented on 2009-05-08
First I unmount sda5, which works without a problem. Then I try to delete sda5, and screenshot.png pops up. Then I follow its directions and try to unmount sda7, and screenshot-1.png pops up.

Thank you for your time,

Tom

---

### Post by tsdemented on 2009-05-08
And for reference, this is what my drive setup looks like (screenshot-2.png).

I was thinking maybe that I could load Linux up without Gnome or all the bells and whistles (I think there is a "root user command prompt only" boot option when you choose the "recovery" option in GRUB). I would not know which commands to input, though. =(

---

### Post by caljohnsmith on 2009-05-08
The reason gparted is asking you to unmount all logical partitions with numbers higher than 5 is because when you delete sda5, gparted will have to renumber the other logical partitions so your logical partitions always start with 5. Thus sda6 will become sda5, and sda7 will become sda6. About the only way you can do that is if you run gparted from the Live CD (or you could download the gparted boot CD), so then your home partition won't be mounted. Also, you may have to right-click the sda6 swap partition and select "swapoff" to make sure it is unmounted too. Good luck and let us know how is goes.

John

---

### Post by sgosnell on 2009-05-08
You have sda5, sda6, and sda7 inside the extended partition sda2.  You'll need to boot from a live CD or USB drive in order to get things changed, as caljohnsmith said.

---

### Post by tsdemented on 2009-05-09
Thanks, that worked!

Hmmm...how do I mark this issue as solved?

---


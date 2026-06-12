---
title: "Ubuntu won't Restart/Reboot"
date: 2011-08-29
forum: Hardware
---

### Post by Joshua on 2011-08-29
I'm seeing a bug, but I don't know how to diagnose or report it.  Can someone help.

I have an [Intel DH57JG Mainboard]("http://www.intel.com/content/www/us/en/motherboards/desktop-motherboards/desktop-board-dh57jg.html") and the [Core i5-650 Processor]("http://ark.intel.com/products/43546?wapkw=i5%20650").

From within Ubuntu 11.04, I can click the shutdown button and chose "Shut down..." and the computer will shut down.

However, if I chose "Restart..." the computer will hang.

If I use the command line to execute either
```
sudo shutdown -h now
```
or
```
sudo shutdown -r now
```
I see the same behavior, respectively.

If I try to restart from tty1 I can see some of the restart activities, but eventually, the Ubuntu shutdown graphic appears, and the progress bar stops changing.

Does anyone know how I can go about reporting this or diagnosing where the problem is?

---

### Post by ktmom on 2011-08-29
My help will be limited, but I think I can get you started.  Can you boot to a LiveCD?  

I'm thinking that you can get the dmesg log for the last attempt from your HD after booting to CD.  The dmesg should give some insight as to where the hang is coming.  You'll need to mount the hard drive after booting to CD and the log is in /var/log/  there will be several dmesg files, the one that is not compressed is the newest.

I have a post elsewhere looking for help with something similar, but I can force a boot by hitting the reset button after the hang occurs.  My system hangs about 50% of the time and boots normally the other.

---

### Post by Joshua on 2011-08-29
ktmom, you reminded me that this same behavior occurs when I run the LiveCD, but it looks like it's not happening on my desktop now.  After my last post, I noticed that there were quite a few updates waiting for installation.  I ran the update manager, and now things are working normally.  This must have been a problem with the initial release.  I know there were a number of bugs related to my mainboard, but I couldn't find any that were limited to what I saw.  Perhaps a fix for one of them, fixed this as well.

I'll go ahead a mark this thread as solved.

---


---
title: "Ubuntu installs and drops to a crippled bash"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by Democritus on 2006-07-26
I downloaded Ubuntu [server?] for install and ran it. Then I ran it again. And again.  Every time I get the same results regardless of the partition I chose.  it works, and after reboot, I get dropped to a shell that doesn't even know what "find" is.

Or "Startx" or "grep" or "gdm."  The list is longer than this but I'm not going to type it all out.  Essentially I have a crippled shell from which I can do very little.  The DVD is not in the drive on reboot, thanks for asking.

Specs:
Acer Aspire 1360, split partition to HDA1 and HDA3 with two swap partitions, 2 and 4.  I have knoppix running [pretty] well on hda1 and Ubuntu not doing much on hda3. These are all recent downloads about 3 days old in total.

I have NO idea how to even begin to fix this.

Is the shell not installed right?  I got no "dmesg" to tail.  :)

No Xwindows, no ethernet, and repeated installs fix nothing.  Once I do a USB backup, I'm going to completely wipe the drive and try again unless someone has a fix.

Knoppix has its own install problems but I can run it off the DVD for now so I can listen to tunes on the train ride home.

//Hello, Earth?  It's me.

---

### Post by cracker on 2006-07-27
If you chose the advanced/server CD, you NEED to manually choose all those packages. The advanced/server CD installs stripped by default on purpose. This is to keep security risks on a server to a minimum--packages can't be exploited if they're not installed. It is also for people who have specific needs and do not want the 'usual' packages that are installed by default on the desktop CD. If you want a useful desktop/notebook setup without much work, use the desktop CD.

---


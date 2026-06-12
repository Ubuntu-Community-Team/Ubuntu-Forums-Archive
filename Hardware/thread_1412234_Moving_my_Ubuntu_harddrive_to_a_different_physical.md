---
title: "Moving my Ubuntu harddrive to a different physical drive"
date: 2010-02-20
forum: Hardware
---

### Post by Amablue on 2010-02-20
I might be mixing up the acronyms here, if I've got it wrong let me know and I'll fix it. I'm not sure if this is the right forum for this, it's the closest I could find. 

So I have two computers. One is an older one that just has the old style harddrive connector (IDE I think?). The other is a newer one that has both SATA and IDE. I've removed the old harddrive from the older computer since it was just 80 gigs and my current two are 500 gigs. This is how I currently have the drives set up:

```

Computer 1       Computer 2
(Newer one)      (Older one)
+-------------+  +-------------+
| SATA:       |  | IDE:        |
| +---------+ |  | +---------+ |
| | Windows | |  | |(nothing)| |
| +---------+ |  | +---------+ |
| IDE:        |  |             |
| +---------+ |  |             |
| | Linux   | |  |             |
| +---------+ |  |             |
|             |  |             |
+-------------+  +-------------+

```

I would like to have each computer dedicated to a single OS though
This is how I would like it set up:

```

Computer 1       Computer 2
(Newer one)      (Older one)
+-------------+  +-------------+
| SATA:       |  | IDE:        |
| +---------+ |  | +---------+ |
| | Linux   | |  | | Windows | |
| +---------+ |  | +---------+ |
| IDE:        |  |             |
| +---------+ |  |             |
| |(nothing)| |  |             |
| +---------+ |  |             |
|             |  |             |
+-------------+  +-------------+

```

Basically, I want to move my IDE harddrive into the other computer, but I want to keep linux on the newer machine and put Windows on the older machine, so I need to swap the entire contents of the HDs. I have an 500 gig external drive I can use, but I don't know the best way to go about doing this.

---

### Post by 2hot6ft2 on 2010-02-20
You explained it very well. The only problem I see is windows typically doesn't like hardware changes like that. It can be moved from one drive to another as long as it's still in the same machine.

For example if the drive is failing and you clone it to another drive to take the failing drives place it will require 1 or 2 reboots when it's first booted up afterwards but is fine after that.

The linux is no problem just moving it from a IDE to a SATA drive and I can tell you how to do that using the dd command.

---

### Post by 2hot6ft2 on 2010-02-20
You could clone the windows to the IDE drive for the other computer and try it BEFORE cloning the ubuntu over the windows that is on the SATA.

That way you could make sure windows will work on the other computer first, and if not you would still have it intact on the SATA.

Here's a great guide for cloning drives:
[Using a Linux Live CD to clone XP and/or Vista]("http://www.justlinux.com/forum/showthread.php?threadid=134457")

---


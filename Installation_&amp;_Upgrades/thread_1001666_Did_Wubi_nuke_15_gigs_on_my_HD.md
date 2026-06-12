---
title: "Did Wubi nuke 15 gigs on my HD?"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by altiod on 2008-12-04
Hi everyone,

I recently tried to install wubi (kubuntu) on my lenovo x61.  During installation (I believe it was while it was formatting the loopback partition exactly), the machine froze and forced me to reboot.  It was stuck on a progress bar that was stuck at 66% and said it would be done in less than a minute.  After about 20 minutes and a nonresponsive mouse it seemed pretty obvious it wasn't going to recover.

Scary enough, but I was able to boot back into windows no problem (cool), so I went to control panel and removed the installation in Add/Remove programs.

I rebooted the computer again and windows wanted to run checkdisk, so I let it do that - everything came through fine.  Great.  I finally get back into Windows, and everything seems to be working normally, aside from the fact that the 15 gigs I allocated to the installation are now gone.  It seems like that should have been fixed when I uninstalled Wubi?

Anyway, is that 15 gig file sitting somewhere on my machine?  Can I just delete it safely?  I don't want to do anything to make this machine inoperable.

I don't think it makes a difference but I'm running windows server 2008.

Thanks a bunch!  Also, if any of you know why it froze like that I would like to know.  I'd be willing to try wubi again (maybe on a different machine) if i knew why the install went bad.

---

### Post by zika on 2008-12-04
schedule chkdsk in Windows and reboot (to get it done). probably are those 15G (which is default for Wubi) somewhere as lost file or whatever.

---

### Post by altiod on 2008-12-04
Thanks, but as I mentioned in the post, I already ran chkdisk - nothing turned up.  Any other ideas?

---

### Post by altiod on 2008-12-21
bump??

---

### Post by zika on 2008-12-21
I've never worked with win 2008 but there might be Search tool. Go to Advanced (something of that kind) menu and choose to search for files of that size. I do not know what directory You gave Wubi to store Your 15GB file. This is only a wild guess. I have a very short experience with Wubi on Vista that led to 'proper' installation of Ubuntu on several machines so I forgot about details of Wubi. My son put it, for example, on D:\Ubuntu\ ... :)

---


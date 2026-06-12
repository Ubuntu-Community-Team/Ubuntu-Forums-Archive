---
title: "Burn network files to CD or DVD"
date: 2008-08-04
forum: General Help
---

### Post by airjrdn on 2008-08-04
Ubuntu 8.04 comes with Brasero for burning disks, but can't seem to burn files from SMB (samba) shares.

How can I burn them without first copying them to my Ubuntu box?

---

### Post by coffeecat on 2008-08-04
I don't have an answer but have you tried burning from a share using another app - say Nautilus or K3b? Is this something that only affects Brasero?

If it's not just Brasero I have a theory. Perhaps this is deliberate, a safety feature. If you were able to burn directly from a smb share, you might have unpredictable network congestion which would cause the data stream to hiccup - leading to a bad burn. Or maybe the data stream might be simply too slow to allow a reliable burn.

Can you burn directly to a CD in Windows from a share on another machine? Have you ever tried it? I haven't It might be interesting to find out whether it's possible. It's too late for me now - I'm going to bed in a minute - but tomorrow, if there's been no further developments on this thread, I'll try this on my MacMini. I'll connect to my fileserver using smb from the Mac, and see if I can burn the files to a CD without transferring them to my HD first.

Thanks for raising an intriguing question.

---

### Post by airjrdn on 2008-08-04
Thanks for replying.

I tried w/GnomeBaker and it wouldn't do it either.  I think the problem is the applications not having access to the keyring.

Burning across the network (same network share, and same burning pc - Ubuntu PC) works fine in Windows.

---

### Post by eftifz on 2008-09-27
Hi, locate your network share in /home/yourusername/.gvfs/ and drag files to any burning app ^_^

---

### Post by linuxgeoff on 2012-04-09
I thought this post might be onto something, but no luck.

I've tried Brasero, k3b and i've tried makking an ISO file instead of going straight to CD.  Brasero creates a 67KB file with no burnable content; k3b is at least good enough to tell you that it doesn't support remote drives.  I've read that Gnomebaker will not do it either.

Is thhre any way in Ubuntu of burning files from a non-local drive? Seems like a bit of a major shortcoming.

---

### Post by nothingspecial on 2012-04-09
Please start a new thread.

This one is old and moldy.

Closed.

---


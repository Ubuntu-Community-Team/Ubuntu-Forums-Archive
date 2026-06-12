---
title: "Alternate ISO always uses the network!"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Toadinator on 2009-10-29
I'm trying to upgrade to Ubuntu 9.10, but since the network servers are so slow I tried downloading the Alternate (i386) ISO. Now I'm trying to upgrade from it, but even though it technically works, it always uses the network even when I tell it not to! The pop-up comes up asking me whether or not I want to to a network upgrade as well, but if I select "Yes" or "No" it still downloads packages! I have a LOT of packages which would take forever to upgrade on these slow servers and I would prefer to wait until they're not so bogged-down. Any advice? Can someone else confirm this?

---

### Post by lovinglinux on 2009-10-29
> **Toadinator said:**
> I'm trying to upgrade to Ubuntu 9.10, but since the network servers are so slow I tried downloading the Alternate (i386) ISO. Now I'm trying to upgrade from it, but even though it technically works, it always uses the network even when I tell it not to! The pop-up comes up asking me whether or not I want to to a network upgrade as well, but if I select "Yes" or "No" it still downloads packages! I have a LOT of packages which would take forever to upgrade on these slow servers and I would prefer to wait until they're not so bogged-down. Any advice? Can someone else confirm this?

Disconnect your network cable before starting the upgrade. It worked for me on a clean install.

---

### Post by theSuperman on 2009-10-29
Same problem with me. I disconnected my network cable, and then the "Getting New Packages" process gets to package 1040, then restarts back to 1.  This goes on and on until I cancel.  However, if I have my network cable plugged in, it downloads (starting at package 1040) and on.  It seems like something is broken in the alternate ISO.

---

### Post by bswilson on 2009-10-29
Very weird, I downloaded the i386 Alternate Installation torrent, burned the ISO, and my installation went fine.  I opted not to use the network install, and my network cable was plugged in.

It worked as I expected, pulling data only from the CD-ROM drive.

---

### Post by mikeljnola on 2009-10-29
I have this same problem.  I downloaded the AMD64 9.10 alternate CD, mounted it (the ISO, not a burned CD), and ran "sudo ./cdromupgrade".  It asked me if I wanted to use the network, I said no, and it started to download a bunch of packages.  Like was said above, I'd rather not spend two days downloading on bogged down servers when I can just bittorrent the ISO.

In full disclosure I had an unsuccessful beta upgrade, but I didn't follow up, I just waited for the actual release.  Is there a way to purge old packages and start from just the CD?  A revert or something?

Thanks,
Michael

---

### Post by theSuperman on 2009-10-29
Alright I figured out what was going on.  Eventually a window pops up saying that it cannot download the following packages, and lists a few hundred.  Well those are programs that I had installed (like emacs and such) which I am guessing need to be updated and not on the CD.  Hence the need for an Internet connection for those packages.  But do they really need to be updated in order to get to 9.10??

---


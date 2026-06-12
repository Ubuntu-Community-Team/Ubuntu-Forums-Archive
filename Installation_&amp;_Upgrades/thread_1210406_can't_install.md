---
title: "can't install"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by thedlw on 2009-07-11
I have 9.04 burned to a dvd that i burned from my ubuntu server.  

I am trying to install ubuntu on my emachine t3522 it has 2 gigs of ram and a celeron 3.33 ghz processor.

Everytime i've tried to do this i keep getting this.

rc-default main process terminated with status 127

From what i've seen this looks like a memory error either in capacity or otherwise.

I've already ran the ubuntu check for defects and a memory scan both came back clean.

So i'm kind of at a loss now..

Thanks

---

### Post by merlinus on 2009-07-11
Did you checksum the .iso?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by thedlw on 2009-07-11
dlw@dlw:~$ md5sum ubuntu-9.04-desktop-i386.iso
66fa77789c7b8ff63130e5d5a272d67b  ubuntu-9.04-desktop-i386.iso

which is the same as is listed here.

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by merlinus on 2009-07-11
Have you tried the live cd, and running ubuntu from that?  This will usuually show any problems you might have after installing.

Also, you can try the text-based alternate install cd.  And perhaps burn the .iso to a cd rather than dvd.

---

### Post by thedlw on 2009-07-11
live cd fails on same install.  currently trying a usb install if that fails will try to burn to a cd.

---

### Post by thedlw on 2009-07-11
Well still no luck.  still same error.  i did try with the alternate cd and it did install.  then it was screaming about /bin/getty crashing and some other things.

I've come to the determination it may be the board :(

But the baffling thing is windows installs perfectly which makes me think its not hardware related.  

But why would ubuntu not install where windows would?

I have 2 machines that ubuntu installed on without any issues at all.  literallly popped it in and poof was up in under 30 minutes.  I'm now vested 50 hours on this and no luck.  I think i'm goiing to try a new burner to see if that possibly can be it but i doubt that will fix it as windows can use the old cdrom.

---


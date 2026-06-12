---
title: "Getting just a few squiggly lines ONLY on boot  after installing ati drivers"
date: 2009-05-28
forum: Hardware
---

### Post by BooDaddy on 2009-05-28
Hello all. 
I attempted to install the proprietary driver from ATI but it wouldnt finish stating it couldnt find a compatible adapter. I have a Radeon x1200 card in my laptop.

Now, when I rebooted the computer, all I get is just a few (maybe 20) lines of mutli-colored lines and thats it. I cant see anything.  The ubuntu logo will display for about 20 seconds then the lines come up, and thats it.

I tried going to recovery mode, and dropping to root and doing the following:

first I tried doing: aticonfig --initial -f     in order to uninstall, but it came back with the error " could not find compatible adapter"

Then I attempted to restore my xorg.conf to a copy that I had made as a backup before I ran the ATI installer.  

None of these options worked on a subsequent reboot, so I then tried the "attempt to repair graphics problems" in the recovery console, and that didnt work either.

I am now dualbooting into XP, and I am missing my ubuntu desktop.. LOL

Any suggestions as what to try?

---

### Post by BooDaddy on 2009-05-28
found my solution!  Check this thread:

[http://ubuntuforums.org/showthread.php?p=7362450#post7362450](http://ubuntuforums.org/showthread.php?p=7362450#post7362450)

I summarized what I did to get it fixed.

---


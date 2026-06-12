---
title: "help compiling with patch"
date: 2008-09-30
forum: Hardware
---

### Post by robcalewar on 2008-09-30
I am having some problems with my Toshiba A215 audio so I turned to google to find a solution and came up with this.

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Method E is the confirmed method for the toshiba series so I am trying to use that one however, the .deb package link is dead. I am completely clueless as to how to rebuild linux modules and applying patches. If someone could write a step by step on how to do this "Rebuild the linux-ubuntu-modules-2.6.22 packages after applying this patch" I'd be extremely grateful.

---

### Post by pytheas22 on 2008-09-30
According to this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/116326) , the sound issue should be resolved in Ubuntu 8.04; the patch was only required on Ubuntu 7.10 and earlier.  The microphone may not work, but everything else should.  Are you using an older version of Ubuntu?  If so, we can try to figure out a way to apply that patch, but I don't want to spend time doing that if it's not necessary.

If you're using Ubuntu 8.04 (Hardy) but the sound doesn't work at all, please post the output of this command:

```
lspci -nn
```

so that we can lookup your audio chipset and try to figure out how to make it work.

Also, if you haven't already, you may want to take a look at the sound troubleshooting guide: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by robcalewar on 2008-09-30
well, the issue is whenever I plug in my headphones, and then remove them, I get no sound, it also happens when I close the lid to my laptop and then reopen it.

---

### Post by pytheas22 on 2008-09-30
If you look through that bug report, there are a few other users who mention what sounds like the same issue--unplugging external speakers seems to break the sound.  Unfortunately, none that I saw offered a solution (but I didn't read the report exhaustively).

I don't think that that patch that you found will help, because it was written for Ubuntu 7.10 and the problems that it fixed (no sound at all) seem to have been resolved in 8.04.

It might help to upgrade to a more recent version of ALSA.  Or try burning a CD of Intrepid alpha, which will have updated ALSA.  Does the problem still exist there?

---


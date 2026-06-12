---
title: "startup problem - read-only filesystem"
date: 2009-12-13
forum: Hardware
---

### Post by LordIshamael on 2009-12-13
Hey, I am running Kubuntu 64 bit on a Dell XPS Studio 13. I just installed a bunch of packages, including git and ssh, and then rebooted. Upon restarting, I got through Grub but then got the error message shown in the picture. This happens in recovery mode and in other kernel versions as well.

It appears on runlevel 8. Runlevel 1 has 3-4 messages on bootsplash. The others (2-7) are all blank.

Any idea how to rectify this? Thanks!

Edit: BTW, the last few lines are the error received when I press Ctrl-Alt-Delete

---

### Post by IcarusR on 2009-12-13
I would suggest booting from live cd & running fsck on the hdd in question.
Usual caveats apply... don't blame me if you loose more data, do this at your own risk. 
But is what I'd be doing.

---

### Post by LordIshamael on 2009-12-13
All right, will try that. Will also try reinstalling initscripts, and report back if that helps.

---

### Post by LordIshamael on 2009-12-13
Yeah, no luck with either one. fsck comes up clean, and reinstalling initscript just gives me a bunch of errors, which I will post in a little while.

I saw another thread like this, trying to track down that link, but that person ended up reinstalling. I'd really rather not do that.

Edit: This is basically the error I get: [http://ubuntuforums.org/showpost.php?p=5228506&postcount=19](http://ubuntuforums.org/showpost.php?p=5228506&postcount=19)

---

### Post by LordIshamael on 2009-12-13
Ended up reinstalling...

---


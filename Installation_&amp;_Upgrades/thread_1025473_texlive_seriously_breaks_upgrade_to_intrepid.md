---
title: "texlive seriously breaks upgrade to intrepid"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by fraktalek on 2008-12-30
Hi, I want to report my experience upgrading from Hardy to Intrepid, it was quite painful...

First all went fine up to the point of texlive upgrade - I don't know exactly why but I got a series of configuration errors from the upgrade manager complaining about texlive and related packages. Then the upgrade stopped due to too many errors and went down to reboot.

It wasn't possible to boot using the new kernel thanks to a kernel panic:

```

Kernel Panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)

```

Googling for that error didn't help much except for the recommendation to try to boot into another kernel and try to finish the upgrade.

So, I tried
```
dpkg --configure -a 
```
which didn't help because dpkg complained that there were too many errors to continue. (*"Processing was halted because there were too many errors"*)

All, or most of the errors dpkg wrote out were related to the texlive package. So I figured I could try to remove the package, but *"apt-get remove texlive"* only recommended to run *"dpkg --configure -a"*.
So, having not much to lose in that state..., I decided to try to remove all the problematic texlive packages using *"dpkg -r"*. And there were many of them, so I actually did something like
```

aptitude search texlive | sed "s/  */ /" | cut -d\  -f2 | xargs dpkg -r

```
... to get me started and did the rest manually.

Maybe I should mention that I had to do all this in the text console / terminal because X couldn't start because of a problem with nvidia driver.

After removing some of the texlive packages this way, I tried *"dpkg --configure -a"* again. This time it probably complained again about some packages so I kept removing them as long as they seemed to be TeX-related. After a while some of the *"dpkg --configure -a"* started to work as it should have had. Only, after a while it stopped again, again due to too many errors, but this time they were DBUS and HAL related, something like *"/var/run/dbus does not exist"*. It took me a minute or two to figure out that I should probably start DBus...:
```
/etc/init.d/dbus start
```

After this, another *"dpkg --configure -a"* which finally succeeded.

I'm writing all this mostly from what I remember from yesterday and a couple of messy notes... I did more things on the way, like trying to run apt-get install -f, etc. but I succeeded in the end... and was able to boot the new kernel, X and the nvidia module work fine too, I only had to upgrade my BIOS because the fan of my Dell Latitude D630 went mad, see [http://ubuntuforums.org/showthread.php?t=965029](http://ubuntuforums.org/showthread.php?t=965029)

I hope this report helps someone and if you read it and notice that I did something wrong on the way (it was rather wild guesses than really really knowing what I'm doing, many of the times) then, please, share a comment.

So, one more thing left - to try to install TeX again... Man, I don't like computers...

---

### Post by fraktalek on 2009-01-12
Now I got to installing TeX again and found the source of the errors. I once needed MnSymbol to compile one of my TeX files so I followed this thread: [http://ubuntuforums.org/showthread.php?t=722871](http://ubuntuforums.org/showthread.php?t=722871) and installed it manually. Now when I tried to install texlive-full I again got a number of errors and dpkg refusing to work, one of the first errors was about a missing MnSymbol.map file, so I tried to install MnSymbol again - using the script from the above thread. It didn't help so I uninstalled MnSymbol, again using the provided script and then dpkg started working and I was able to finish the texlive-full installation.

---


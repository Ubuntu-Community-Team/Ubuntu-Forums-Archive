---
title: "Flickering Line on Radeon after sleep"
date: 2014-12-28
forum: Hardware
---

### Post by Brandon_MacEachern on 2014-12-28
This isn't desktop environment like I originally thought, but it is definitely something with the Radeon open source driver.

After waking my laptop from sleep, I find that at the bottom of the screen, is a flickering black line that is about 3 pixels high.  The only way to stop it, is to log out and log back in.  It does this on Ubuntu, Xubuntu, etc, anything buntu. I tried Linux Mint, and found it did NOT do this (but had very poor visual performance that made it unusable).

I don't want to use FGLRX, I would like to keep using the open source drivers.

This only happens waking from sleep like I said.  A work around is alt+f2, and doing unity --replace.  That actually clears the black line, but causes other issues, like in Xchat, links no longer open up with the browser.

Ubuntu 14.04 did not have this issue.

I know the driver between the two changed, because on 14.04, Google maps in Chrome always loaded black, and on 14.10 it loads now, and Chrome works faster when scrolling.

ATI Radeon 6400M, Ubuntu 14.04.  As of right now, it's completely up to date and has no other updates for me to run, not even from apt-get upgrade.

---

### Post by Brandon_MacEachern on 2015-01-04
bump.

[https://www.youtube.com/watch?v=V-t3K95g898](https://www.youtube.com/watch?v=V-t3K95g898)

---

### Post by Brandon_MacEachern on 2015-01-05
Here's my findings.

Ubuntu 14.10:  Flickering Line, fixed by running unity --replace
Ubuntu GMOME:  Flickering Line
XUbuntu:  Flickering line, sometimes fixed by reloading Compton.  If using XRender, it doesn't seem to happen.  With NO compositing it does it also.
KUbuntu:  Just works, no flickering line at all, all is good here.

---

### Post by Brandon_MacEachern on 2015-01-15
Ok so this CAN actually happen on Kubuntu, but only if it's set to not lock on resume.  So if it goes straight to the desktop when unlocking, the flickering line is there.

I'm guessing no one else can help though from the lack of comments, or anything.  I refuse to use FGLRX, it doesn't work with WebGL in Chrome, and it's slower than the open source driver on this computer believe it or not.

I don't know what 14.10 did to the open source radeon driver, but it's way faster than 14.04, but it doesn't like resuming from sleep, that's for sure.

---


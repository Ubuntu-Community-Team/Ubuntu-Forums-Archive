---
title: "Ubuntu 9.10 Install disk doesn't boot"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by Benn on 2009-10-29
Hi, I downloaded 9.10 beta AMD64 (not RC). I have a Gateway ID58, Intel Core 2 Duo T6500 centrino, 4GB Ram.

When I select "Try ubuntu without installing..." or "Install Ubuntu..." the screen goes black and nothing happens, I've burned the ISO 3 times and checked integrity twice.

Any Ideas ?

---

### Post by tommcd on 2009-10-29
Your laptop has intel graphics, which *should* be ok with the live CD.
When you say you checked the integrity, did you run the option on the CD that says "check disc for defects"?
If the check for defects passes, then the CD should be ok.
Things to try:
Try the release candidate CD. There may be some bug fixes for the xserver-xorg-video-intel driver (the Ubuntu intel graphics driver) on the release candidate that may fix the problems you are having with the beta CD.
Try the option on the live CD that says "boot into safe graphics mode" or something like that. It has been a while since I used the live CD, but there should be an option for safe graphics mode.
You could try installing Ubuntu from the alternate install CD. This is a text based install CD that will avoid any problems with graphics drivers during installation. You will not be able to try Ubuntu first without installing it with the alternate CD though.
If you are burning the CD from Windows, try using Iso Recorder or Infra Recorder, and be sure to burn the CD at the slowest possible speed:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
If the "check disc for defects" option passes ok though, then I would assume the CD is good.

---


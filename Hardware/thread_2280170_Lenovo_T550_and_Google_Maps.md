---
title: "Lenovo T550 and Google Maps"
date: 2015-05-28
forum: Hardware
---

### Post by stefan_bahrens on 2015-05-28
I'm using a new Lenovo T550 laptop with 8MB Ram. If I do "lspci | grep" I get VGA 00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09). If I do "sudo lshw -C video" I get *-display - description: VGA compatible controller, product: Broadwell-U Integrated Graphics, vendor: Intel Corporation. I have Ubuntu 14.04 LTS 64bit installed. If I attempt to use Google Maps the text in the search box is corrupted - letters are omitted and replace with odd symbols. The maps themselves do not respond correctly and I cannot zoom in. Sometimes large areas go black. Is there anything I can do about this? Is this a known problem with this graphics adapter. Thanks for any help.

---

### Post by weatherman2 on 2015-05-28
You are doing this in Firefox?  If so, try Google Chrome and see if things work any better.

---

### Post by stefan_bahrens on 2015-05-28
Thanks weatherman2. I am indeed using Firefox 38.0. I followed your suggestion and installed Google Chrome. This browser had no problem displaying images and text on the Google Maps pages. This is a workaround and thank you for it. Any idea why this is happening? Have Google deliberately made "Maps" difficult to display to try to drive users into the arms of their browser? Or am I being too conspiratorial. Will Firefox address this issue or is affecting too few users?

---

### Post by weatherman2 on 2015-05-28
Seems you aren't the only one with this problem:

[http://ubuntuforums.org/showthread.php?t=2274372](http://ubuntuforums.org/showthread.php?t=2274372)

The only "solution" found by the OP there was to use the latest version of Ubuntu 15.04, which is not an LTS release, so not a real solution for me.  (But because I already use Chrome, not an issue for me at all.)

---

### Post by stefan_bahrens on 2015-05-29
Blimey. I'm now inclined to think it might be some issue connected with Flash. Ahh well.

---


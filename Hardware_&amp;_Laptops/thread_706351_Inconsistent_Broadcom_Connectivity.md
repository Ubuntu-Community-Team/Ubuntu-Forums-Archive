---
title: "Inconsistent Broadcom Connectivity"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by burgerearl on 2008-02-24
I'm having troubles with my Broadcom card, similar to this post, except I'm using the firmware and not ndiswrapper: [http://ubuntuforums.org/showthread.php?t=129425](http://ubuntuforums.org/showthread.php?t=129425)

lspci|grep Broadcom tells me I have the BCM94311MCG wlan min-PCI

I installed the 43xx firmware with darkn00b's scripts ([http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)). This worked fine right after I installed it, but I found I needed to rerun the scripts to keep connectivity. I don't recall specifics (this was ~2 months ago), but it may have been as often as every reboot.

Now I'm getting totally unpredictable connectivity. Sometimes I connect as soon as I log in, other times not at all. It is detecting the network (and several others) without problem and even asks for a password (although when it connects successfully, it does *not* ask, it uses the one I stored when I first set up the connection) - entering the password causes it to try again, subsequenty asking for the password again after 20-30 seconds.

The process I last used to successfully connect WAS: I disabled the broadcom firmware in the restricted drivers manager, rebooted, and got a connection instantly (although the firmware was reenabled on reboot). Repeating this process does not give me connectivity.

Any help would be greatly appreciated.

---


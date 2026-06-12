---
title: "Fujitsu LifeBook N3500 Notebook - error message loops on install and liveCDs"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by lotusleaf on 2005-11-25
Hello,

I'd like to install Ubuntu Breezy on a friend's brand new Fujitsu LifeBook N3510 Notebook ([Technical Specifications](http://support.fujitsupc.com/CS/Portal/supportsearch.do?srch=TECHSPECS)). However, when I boot from a Breezy install CD or a LiveCD, I get several messages which repeat and begin an endless, certainly infinite loop, forcing me to reboot to get out of it, it doesn't even let me get to the language selection (or any other selection screens) before throwing me into this loop. The loop contains the following information:

```
hub 4-0:1.0: connect-debounce failed, port 1 disabled over-current charge on port 1
```

The above message repeats with the numerical values going from 1 - 6 for "port # disabled" "on port #".

The error message above follows the ```
hotplug/usb.rc
``````
dev/scsi/host0/bus0/target0/lun0:p1
``````
scsi device sda
``` and ```
scsi 0
``` messages.

I tried booting both the install CDs and the LiveCDs with the acpi=off, noapic, and no lapic options but none of them alone or in combination bypassed this issue. In addition to the Breezy install/LiveCDs I tried the Hoary install/LiveCDs and received the same error loop on boot.

I decided, for comparison, to try the SUSE 9.3 install DVD and it booted up without any of the above error messages and loaded up the installation screen/language selection. That's great and all, but I want to install Ubuntu Breezy on the laptop, as I'm moving as many people as I can to Ubuntu.

Thanks for reading, I appreciate any help. :)

---

### Post by lotusleaf on 2005-11-27
bump - any help appreciated so I can install Ubuntu Breezy on a friend's laptop. :)

---

### Post by lotusleaf on 2005-12-01
one final bump - anyone have any info?

I Googled and discovered someone else had a similar problem with this laptop using Knoppix and from what I read they ended up having to install another distro because  Knoppix kept crapping out on boot. I'd much rather install Ubuntu on my friend's laptop but if this error loop on install/liveCD boot can't be resolved I guess I'll have to toss SUSE on it. I appreciate any help!

Edit: I ended up installing SUSE v.10 on my friend's laptop (due to a limited time frame for install) since I couldn't solve the error loop at boot when I tried installing Ubuntu Breezy. This error loop problem with this particular laptop doesn't seem to be limited to Ubuntu, I've seen others using Knoppix and other Debian based distros expressing the same frustration with the issue.

So, **the reader(s) of this thread may now disregard my request(s) for help** as I'm done with my limited troubleshooting with the error loop on this laptop. Were it my laptop I would've continued to find a possible solution to this problem but since it's not, fsck it. :) Anyone considering buying this model laptop from Fujitsu, please be aware of this issue before buying.

---


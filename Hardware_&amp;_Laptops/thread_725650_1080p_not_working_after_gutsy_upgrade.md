---
title: "1080p not working after gutsy upgrade"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by TgBoat on 2008-03-15
Hello All,
I just upgraded my computer to gutsy, and am having problems setting the resolution.  In feisty, I was able to set my resolution via a modeline in my xorg.conf, but it appears to be ignored in gutsy.  My setup is as follows:
Intel GMA950 graphics connected to my Sony STR-DG910 AV receiver via DVI-HDMI Cable.  The receiver is connected to my Westinghouse LVM42-W2 1080p panel via HDMI.  This setup worked well in feisty.

Since the upgrade, I can only get 1920x1080 when the pc is connected directly to the panel.  Anytime I connect through the receiver, I drop to 1280x720.  I think this may be an EDID problem between the receiver and the pc.  I used get-edid to pull the EDID info from the monitor, and tried to force the use of it by putting the following in my xorg.conf:

Option "UseDisplayDevice" "TMDS-1"
Option "CustomEDID" "TMDS-1:/home/bill/edid"

where /home/bill/edid is the data captured by get-edid.
I am lost here.  Am I using get-edid correctly?  The receiver will pass 1920x1080, but for whatever reason, xorg won't do it.  Any help would be greatly appreciated.

Thanks,
Bill

---


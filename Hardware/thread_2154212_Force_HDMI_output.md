---
title: "Force HDMI output"
date: 2013-06-13
forum: Hardware
---

### Post by innominate227 on 2013-06-13
I have a mythbuntu box hooked up to an LG TV via HDMI.  Its a motherboard with intel onboard video.  Here is the exact motherboard ([http://us.shuttle.com/barebone/Models/SH67H3.html](http://us.shuttle.com/barebone/Models/SH67H3.html)).  The HDMI works when I first boot the machine.  But if I turn the TV off and then turn it back on I see only an all black screen.  It is a black screen not "no signal" because the TV does not display its "no signal" box.  This appears to be an issue only with this TV I tried a smaller TV and things worked as expected.  However this TV has not had the same issue with any of the other devices hooked up to it via HDMI.  One way to fix the issue is to unplug the HDMI cable and then plug it back in, but I dont want to have to do that every time.

Is there anyway to:  force ubuntu to always output to the HDMI port, or perhaps some cron job I could run every 5 second to attempt to reconnect the HDMI if its not currently connected?  Or any other ideas?

Thanks
-Nate

---

### Post by innominate227 on 2013-06-13
I tried a fresh install of the latest normal ubuntu (13.04) instead of mythbuntu (which I think uses 12.04) and it seems to be working as expected now.

---


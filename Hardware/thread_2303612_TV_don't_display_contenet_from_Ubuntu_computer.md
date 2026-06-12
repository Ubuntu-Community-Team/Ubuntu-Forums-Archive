---
title: "TV don't display contenet from Ubuntu computer"
date: 2015-11-20
forum: Hardware
---

### Post by mark253 on 2015-11-20
Hi,
I have computer running Xubuntu 14.04, with all updates. I also have new Panasonic TV. I have connected them with new HDMi cable, and in TV I have enable HDMI. TV is showing that it is in AV mode taking content from HDMI. Unfortunately I don't know how to force Xubuntu to send the content of a screen to the TV set.
I have watch some youtube tutorials but I haven't found the solutions in them.
Kind Regards
Mark

---

### Post by cmcanulty on 2015-11-20
I believe you go to displays and set it to mirror display

---

### Post by efflandt on 2015-11-21
It is not clear if you are trying to use more than one display (are both the same native resolution?). In order for a TV to display HDMI, its Input would need to set to HDMI not AV (AV usually refers to Composite with yellow RCA jack/plug or possibly S-Video). If you are trying to use more than one display, how to do that might also depend upon what graphics hardware and driver you are using. If you have both integrated (built-in) graphics and a graphics card, it also may depend whether HDMI is connected to a port on the motherboard or graphics card and which graphics is being used at the time (even if just one display).

If you are trying to hot plug a second display (while X is running), X will not necessarily see it because X determines what graphics is connected when it starts. So if Settings > Displays > Detect Displays button does not detect a second display, see if it shows up logging out of X and back in, or booting with everything on and proper inputs set on the display(s).

If you mirror (duplicate) your desktop display to another display, they both may need to be "capable" of a common resolution (even if not their native resolution), but not necessarily for extending the desktop (different things on each screen).

---

### Post by Bucky Ball on 2016-02-06
*Thread moved to **Hardware**.*

Reason: Nothing to do with ***Gaming & Leisure***.

---


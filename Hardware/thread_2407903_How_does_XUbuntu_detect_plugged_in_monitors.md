---
title: "How does XUbuntu detect plugged in monitors?"
date: 2018-12-11
forum: Hardware
---

### Post by agrowcott on 2018-12-11
For background info on the problem I am having, please see [https://askubuntu.com/questions/1099527/monitor-detection-is-failing](https://askubuntu.com/questions/1099527/monitor-detection-is-failing)

How does XUbuntu detect monitors? Which service is responsible? Does it use cached data at all?

I ask the last because despite disabling my on-board graphics card in hardware, plugging the monitor into it causes XUbuntu to detect the monitor and restore my signal.

I am also curious why xrandr on my main PC (which has 3 display ports, 1 HDMI and 1 DVI-D) reports 6 display ports, 1 HDMI and 1 DVI-D while my boy's PC (which has 1 VGA, 1 S-video, and 1 DVI-I on the PCI graphics card) reports 1 VGA, 1 TV and 2 DVI-I. It is almost as if the port type that has a monitor plugged in is doubled up in the list.


Anyway, if I am to fix this issue, and no-one else seems to know or care what the problem might be, I need to know where to start, so this post is a request for general information regarding monitor detection so I at least know which bits of code to dig into and try to debug.

I will be very grateful for any information and help that anyone might give me.

---

### Post by CatKiller on 2018-12-11
Your problem sounds like it's caused by a bad cable.

---

### Post by agrowcott on 2018-12-11
Wow, great idea. I'll borrow a spare from work and test it.

Thanks.

Still interested to know how Ubuntu detects monitors though.

---

### Post by CatKiller on 2018-12-11
> **agrowcott said:**
> Still interested to know how Ubuntu detects monitors though.

[Display Data Channel](https://en.wikipedia.org/wiki/Display_Data_Channel)
[Extended Display Identification Data](https://en.wikipedia.org/wiki/Extended_Display_Identification_Data)

---

### Post by oldfred on 2018-12-11
Monitor EDID
sudo get-edid | parse-edid
[http://askubuntu.com/questions/81370/how-to-create-extract-the-edid-for-from-a-monitor](http://askubuntu.com/questions/81370/how-to-create-extract-the-edid-for-from-a-monitor)

---

### Post by Autodave on 2018-12-11
Simply, the monitor info is sent to the PC through the cable.  Early and/or cheap VGA cables don't always have the extra wire needed to transmit that info.  HDMI cables have gone through quite a lot of changes since first introduced. Some older ones / cheaper ones may not work as expected.

---

### Post by agrowcott on 2018-12-27
Thanks, CatKiller.

I swapped the cable with one attached to a Windows PC. Since then neither computer has shown any issues. I guess Linux graphics drivers are more sensitive to cable issues.

Thanks also for the links.

---

### Post by Yellow Pasque on 2018-12-29
Note that xfce stores monitor config in:
~/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml

IIRC, I've had to delete this file and let xfce generate a fresh one a couple times over the years.

---


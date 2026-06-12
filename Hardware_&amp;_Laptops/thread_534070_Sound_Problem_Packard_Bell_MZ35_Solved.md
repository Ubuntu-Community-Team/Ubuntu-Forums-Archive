---
title: "Sound Problem Packard Bell MZ35 Solved"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by MartijnWeterings on 2007-08-24
I've found several threads about problems with the snd-hda-intel module but none of them fixed my problem. Realtek has updated the hda-intel driver and it solved the problem for me.

My problem was:
 I've installed ubuntu on my Packard Bell MZ35-001. It has a SB450 HDA Audio soundcard using the snd-hda-intel driver. The speakers work fine but the headphones don't. The volume couldn't be changed. There was only a mute button in the mixer panel but no volume control. As a result it was as if the headphones where muted even though the button on the mixer panel was selected. The speakers worked fine.

How my problem can be solved:
Regularly searching the internet for new drivers I found this new driver alsa-driver-rt-20070820 at the realtek website. [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs)
Download the driver. Install it. Add the line "option snd-hda-intel mode=hp" to the file /etc/modprobe.d/alsa-base. Reboot and the headphone jack now works.

This new driver might also be able to solve problems of other people using the hda-intel driver and the ALC861VD/660VD soundcard.

---

### Post by nesk1 on 2008-02-12
when i install the realtek driver and try to start alsamixer it says that there are missing modules i cant understand that where is the error

---


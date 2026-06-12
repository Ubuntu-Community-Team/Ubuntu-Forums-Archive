---
title: "Need help with undoing sound driver modification."
date: 2010-05-16
forum: Hardware
---

### Post by darkodin14 on 2010-05-16
When I installed ubuntu 10.04, my sound was working perfectly but my microphone was not. I have a HP DV6871US laptop. So i found a solution which i attempted to get my mic to work. I entered this command into terminal.
This is the command: 

/configure --with-cards=hda-intel
make
sudo make install

and when i restarted ubuntu does not detect any audio devices and my sound does not work.

Can you please tell me how to restore to the original driver? Thanks in advance.

---

### Post by lidex on 2010-05-16
Yeah. Click on the alsa-upgrade-script link in my sig and follow directions there.

---


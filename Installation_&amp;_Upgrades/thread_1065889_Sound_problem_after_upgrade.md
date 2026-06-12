---
title: "Sound problem after upgrade"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by Dale Gerdemann on 2009-02-10
After upgrading to 8.10 I didn't have sound at all. I followed the instuctions at: help.ubuntu.com/community/SoundTroubleshooting and now I have the drumbeat sound and other system sounds. But I don't have sound in other applications such as the browser (Firefox) or games. Any ideas?

A few details: this is for a new Dell laptop. It came with 8.04 and I immediately updated to 8.10. So I'm not actually sure that I had sound before the upgrade. But I think I probably did. The one point on the SoundTroubleshooting page that helped was to reinstall alsa with:

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2.

---


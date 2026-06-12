---
title: "My laptop's webcam doesn't work with Skype."
date: 2009-03-30
forum: Hardware
---

### Post by oblador on 2009-03-30
Hi, folks!

My webcam doesn't work with Skype, why? and most of times I start Skype I have to reconfigure the audio settings or else it doesn't work. What can I do?

Thanks!

PS: running Ubuntu 8.10, my laptop is a Dell Inspiron 1525.

---

### Post by emergingtechnologies on 2010-01-24
> **oblador said:**
> Hi, folks!

My webcam doesn't work with Skype, why? and most of times I start Skype I have to reconfigure the audio settings or else it doesn't work. What can I do?

Thanks!

PS: running Ubuntu 8.10, my laptop is a Dell Inspiron 1525.


This got my Inspiron 1525's webcam to work with Skype:



Code:

sudo rmmod uvcvideo
sudo modprobe uvcvideo

---


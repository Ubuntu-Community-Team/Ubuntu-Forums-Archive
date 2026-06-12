---
title: "Sound loops over and over after login"
date: 2005-07-10
forum: Hardware &amp; Laptops
---

### Post by JMFontaine on 2005-07-10
Hello,

I installed Ubuntu Hoary on a Samsung VM 8000 series laptop. Everything went right. After I log in, Ubuntu is supposed to play a drum roll and then load Gnome but instead the drum roll loops over and over and Gnome never loads.

I think this problem is related to the sound driver but as I am quite newbie to Linux and even more to Ubuntu, I can not fix this by myself.

Can anyone help ?
Thanks.

---

### Post by JMFontaine on 2005-07-11
The audio chipset is a Sis 7018.

---

### Post by taddy_porter on 2005-07-11
I had a similar problem. The sound would work for a time, then get stuck like yours. I changed the gstreamer-properties to OSS and it works fine now.

---

### Post by JMFontaine on 2005-07-11
Thanks for your answer. :)

But since Gnome is not loading, how can I change the gstreamer-properties via command line ?

---


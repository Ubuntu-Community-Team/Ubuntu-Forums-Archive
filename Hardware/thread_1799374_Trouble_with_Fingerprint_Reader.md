---
title: "Trouble with Fingerprint Reader"
date: 2011-07-07
forum: Hardware
---

### Post by striker07 on 2011-07-07
Hello!

I'm trying to use the Digital Persona u.are.u 4000B in Ubuntu 11.04. I've installed the libfprint, that installed well, but when I try to use the reader, I received the following message:

uru4000:error [dev_init] interface claim failed
async:error [fp_async_dev_open] device initialisation failed, driver=uru4000

Well, I searched the internet to found a solution, but all forums and blog posts refeer to this solution:

"You have to add yourself to the plugdev group and then change the permissions of the usb folder to allow access to the plugdev group. You can verify you are in the plugdev group by using groups:

sudo usermod -a -G plugdev $USER
groups | grep plugdev # Make sure there is output from this
sudo chgrp -R plugdev /dev/bus/usb/"

But after that, the error remais the same. Someone can help me?

---


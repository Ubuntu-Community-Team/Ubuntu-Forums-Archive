---
title: "problem with graphics driver and wireless"
date: 2008-10-11
forum: General Help
---

### Post by a_weasel on 2008-10-11
Just installed ubuntu. 2 problems so far:

1. No drivers for nvidia cards. supposedly mine is supported (i saw it in a list of supported cards) and i should be able to install it by going to my hardware drivers thing, but when I try to update it says download begun and then gives me this error:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb)
  404 Not Found


2. no wireless: internet works fine if i'm plugged in, but no support for wireless. I haven't really looked into this at all really, but since i'm here i thought i'd ask.

---

### Post by JangMunho on 2008-10-11
If you installed 8.04, use this command to open /etc/apt/sources.list:
```
sudo gedit /etc/apt/sources.list
```
Then replace all the text in the file within this one:
```

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse 
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

```
then run "sudo apt-get update" to update the software list.
And rerun the driver manager to install the driver.

And the second question, if nothing appears in the driver manager that mentions wireless card, I think you need to get a driver for your card from the official website of the manufacturer of your card, and compile and install the driver yourself.

---

### Post by caleb12 on 2008-10-11
What kind of wireless card is it? 

You can always check this link as well:

[http://linuxwireless.org/](http://linuxwireless.org/)

---

### Post by a_weasel on 2008-10-11
success! it works.

how do you learn all this stuff? it all seems pretty daunting right now...

---


---
title: "Ubuntu requires login?"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by Gwynplaine on 2009-11-02
I have made an ubuntu installation on my USB flash-disc which have worked smoothly for some days. Since everything seemed to work fine, I decided to install xbmc. I installed it, set it as start automaticly during startup and unactivated some unneccesary startup programs meanwhile (like bluetooth). When all was finished, I decided to reboot just to check that the program started as configured. But instead Ubuntu starts with a brown/gray background, and a "login" buttom. I haven't configured any login, and I haven't got any password! I've tried to login without giving any username or password, I've tried ubuntu/ubuntu and username/password, without any results, except by the usual "autenciation failure". When I try to log in as "ubuntu" without a password it loads for a few seconds, but then the login-button appear again.

What have happened? Have I disabled something that I shouldn't have dissabled, or is Ubuntu pure evil?

---

### Post by sisco311 on 2009-11-02
[http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

---

### Post by corncob on 2009-11-02
> **Gwynplaine said:**
>  is Ubuntu pure evil?

[http://ubuntusatanic.org/installation.php](http://ubuntusatanic.org/installation.php)

---

### Post by Gwynplaine on 2009-11-02
> **sisco311 said:**
> [http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

That guide doesn't work for me. When installing on an usb-flash, ubuntu acts like a boot on a liveCD, with the exception that changes can be saved. Therefor, no screen saying grub loading is appearing. First comes a screen where I can choose to boot linux, install it on disk or boot from first hdd. Thereafter a quick text comes telling ie casper loaded, and then there's just an blinking black and white ubuntu logo. Then the brown/black backgrounds appear, along with the ubuntu logo and a yellow square going back and forth. Thereafter the login button appears.

Everything up to the brown/black background appeared before as well, but earlier did I see the desktop after the black/white logo.

---

### Post by sisco311 on 2009-11-02
the default user on the LiveCD is ubuntu and the password is blank.

so try:

username: ubuntu
password: <just hit Enter>

---

### Post by Gwynplaine on 2009-11-02
> **sisco311 said:**
> the default user on the LiveCD is ubuntu and the password is blank.

so try:

username: ubuntu
password: <just hit Enter>

I've tried that. Then the login screen disappears and the system appears to be booting. But then suddenly the screen turns black and thereafter the login screen appears again.

---

### Post by Gwynplaine on 2009-11-02
I managed to start ubuntu once by choosing "help" during the initial boot (where I choose how to start the system), and thereafter doing nothing. But the problem reappeared again during the next reboot (which had to be done by switching off the power, due to software problems with xbmc), and now that method doesn't work either... Seems like there has been some error in the system, which makes the login malfunction.

---

### Post by Gwynplaine on 2009-11-02
Am I really the first to experience this problem?

---

### Post by Gwynplaine on 2009-11-02
Hmmm, signing in with ubuntu as username and no password works if I choose failsafe GNOME. Seems like it's some program that's causing all this trouble, and it wouldn't surprise me if it's xbmc. Anyway, thanks for the help!

---


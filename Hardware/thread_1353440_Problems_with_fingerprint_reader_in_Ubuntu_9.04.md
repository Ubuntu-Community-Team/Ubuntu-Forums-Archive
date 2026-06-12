---
title: "Problems with fingerprint reader in Ubuntu 9.04"
date: 2009-12-12
forum: Hardware
---

### Post by Pazau on 2009-12-12
Hello everyone.

After reading a guide on my laptop built-in fingerprint reader and how to get it to work, I am having troubles.

[http://www.aldeby.org/blog/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/9#fingerprint](http://www.aldeby.org/blog/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/9#fingerprint)

In '/etc/pam.d/common-auth' you must insert the top 'auth sufficient pam_fprint.so' if you want to use either fingerprint or password for administrative tasks.

The problem is that Ubuntu requires both, before I can do anything. Fingerprint reader accepts my fingerprint, so for now I can still do what I want, but how do I get Ubuntu to understand that I will not use both, each time I have to confirm?

---

### Post by paulisdead on 2009-12-12
I think this is the guide I followed for my latitude d430 [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Ubuntu](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Ubuntu)
I can login in, sudo, gksu, su, etc fine with a fingerprint.  However gnome-keyring is kinda bitchy about needing a password still.  The main thing it bugs about it for, is using the wifi connection, so I made the connection available to all users, to get it to stop bugging me for the wifi.

---

### Post by Pazau on 2009-12-17
It does not work, unfortunately. I did not install the ThinkVantage Fingerprint since Fprint demo has worked on previous versions of Ubuntu. Furthermore, FingerThink is only of fingerprint readers built into Dell, Lenovo and Toshiba laptops.

My laptop is from HP.

---


---
title: "problem about login with Fingerprint of ThinkPad X61"
date: 2010-07-20
forum: Hardware
---

### Post by colinyao on 2010-07-20
ubuntu 10.04 LTS /i386

I have installed all finger components for thinkpad via apt,
and I can use
tf-tool --acquire
system can read my fingerprint, and I can use 
tf-tool --verify
to veirty my fingerprint.

someone said that I need to use tf-tool --add-user, but tf-tool has not the option.
and I have not modified the /etc/pam.d/common-auth file, it looks like modified automaticly.

I have enabled the fingerprint login.

when I login with gdm , it shows me 'please type password or swipe finger'.

I can't swipe finger, only password can be accepted.

---


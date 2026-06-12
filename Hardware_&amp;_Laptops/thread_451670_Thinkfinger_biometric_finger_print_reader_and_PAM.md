---
title: "Thinkfinger biometric finger print reader and PAM"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by u-blunt-2 on 2007-05-22
I am trying to configure Thinkfinger to work with my Toshiba tecra S4 laptop. I compiled and installed the latest Thinkfinger software (0.3) with success.  I used this command to compile
```
./configure --with-securedir=/lib/security --enable-pam --with-birdir=/etc/pam_thinkfinger --prefix=/usr
```

I believe my problem is with my PAM authentication settings. I followed the recommendations in the README file that came in the tarball. My   contained the following line :
```
auth	required	pam_unix.so nullok_secure 
```

I changed it to :
```

auth	required	pam_unix.so nullok_secure
auth    sufficient   	pam_thinkfinger.so
auth     required     pam_unix.so try_first_pass
auth     required     pam_unix.so debug 
```
as recommended in README. I loged out and noticed that the login screen asked me for my password once, then asked me for password or swipe finger, which worked. I then changed /etc/pam.d/common-auth to the following :
```
auth    sufficient   	pam_thinkfinger.so
auth     required     pam_unix.so try_first_pass
auth     required     pam_unix.so debug 
```
I then rebooted and found that I was no longer prompted to swipe my finger. I tried multiple combinations in /etc/pam.d/common-auth , tried installing pam_unix2, all to no avail. I even recompiled Thinkfinger and had the same conclusion. 

Can anyone please help me ?

---


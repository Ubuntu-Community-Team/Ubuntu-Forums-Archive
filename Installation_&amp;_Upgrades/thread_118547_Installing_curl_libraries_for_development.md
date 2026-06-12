---
title: "Installing curl libraries for development"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by w2vy on 2006-01-17
I have 5.10 and so far all is going well.
(well partition issues but *everyone* hits that)

I have GCC installed and am trying to complie a program that uses libcurl

I installed libcurl3 (apt-get) but it did not seem to bring curl.h with it.

All i see is:

tom@w2vy:~/$ find /usr -name "*curl*" -print
/usr/share/doc/libcurl3
/usr/share/curl
/usr/share/curl/curl-ca-bundle.crt
/usr/lib/python2.4/macurl2path.py
/usr/lib/python2.4/macurl2path.pyc
/usr/lib/python2.4/macurl2path.pyo
/usr/lib/libcurl.so.3.0.0
/usr/lib/libcurl.so.3

Am I forgetting a step?

I did apt-get install libcurl3

Thanks, Tom

---

### Post by 23meg on 2006-01-17
Try installing "libcurl3-dev".

---

### Post by w2vy on 2006-01-17
Ah ha that makes too much sense :)

My problem is I have not learned how to search the available packages yet.

A friend just told me about "dpkg --get-selections"

Tom
ps. I only installed server edition since it's a small machine

---

### Post by w2vy on 2006-01-17
Yup that did the trick... libcurl, libcurl-dev and curl

But I see version 7.14.0 I was using version 7.15.1 in cygwin :(

And leads on a newer version?

If I need to build it, is it hard to convert to a apt package?

tom

---

### Post by 23meg on 2006-01-18
You can search the apt cache with ```
 apt-cache search
```

---

### Post by w2vy on 2006-01-20
Well I finally got it all set up right... a few re-installs later...
(I'll explain that later)

23meg suggested I try loading the curl libraries from dapper,
to do this I added the following to /etc/apt/sources.list after the breezy entries

# Uncomment to grab things from dapper ***BUT THEN RE-COMMENT ***
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

Uncomment them to load the newer curl and then recomment...
This is real important becuase if you forget you end up pulling anything
else you install from dapper which is bad, very bad :)

I had no idea how to un-do it, so I just reinstalled from scratch...

Oh Yes! When you change sources.list you should do an apt-get update
so the database is in sync with what you can access.

Also I did get some link warnings because of mismatching library versions,
they looked like this:

```
/usr/bin/ld: warning: libssl.so.0.9.8, needed by /usr/lib/libcurl.so, may conflict with libssl.so.0.9.7
/usr/bin/ld: warning: libssl.so.0.9.8, needed by /usr/lib/libcurl.so, may conflict with libssl.so.0.9.7
/usr/bin/ld: warning: libcrypto.so.0.9.8, needed by /usr/lib/libcurl.so, may conflict with libcrypto.so.0.9.7
/usr/bin/ld: warning: libcrypto.so.0.9.8, needed by /usr/lib/libcurl.so, may conflict with libcrypto.so.0.9.7

```

Now it looks bad, but it does not seem to be effecting anything
(yet - call me an optimist)

This *could* cause issues with other things, so be careful if you try
this on other libraries

Tom

---


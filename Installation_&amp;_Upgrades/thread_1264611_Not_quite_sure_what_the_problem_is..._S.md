---
title: "Not quite sure what the problem is... :S"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by PolloE on 2009-09-12
OK, so here is the thing:

Whenever I tried to check if there is any updates with the Update Manager by clicking check.

Then a window pops up and it says "Downloading Package Information" it says it is downloading the file "1 out of 15" and it just stays there for about a minute without downloading anything and then shows this error message:

```
W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty/Release.gpg  Could not connect to ftp.corbina.net:21 (195.14.50.21), connection timed out

W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2  Unable to connect to ftp.corbina.net ftp:

W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2  Unable to connect to ftp.corbina.net ftp:

W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2  Unable to connect to ftp.corbina.net ftp:

W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2  Unable to connect to ftp.corbina.net ftp:

W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty-updates/Release.gpg  Unable to connect to ftp.corbina.net ftp:

W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2  Unable to connect to ftp.corbina.net ftp:

W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2  Unable to connect to ftp.corbina.net ftp:

W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2  Unable to connect to ftp.corbina.net ftp:

W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2  Unable to connect to ftp.corbina.net ftp:

W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty-security/Release.gpg  Unable to connect to ftp.corbina.net ftp:

W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2  Unable to connect to ftp.corbina.net ftp:

W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2  Unable to connect to ftp.corbina.net ftp:

W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2  Unable to connect to ftp.corbina.net ftp:

W: Failed to fetch ftp://ftp.corbina.net/pub/Linux/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2  Unable to connect to ftp.corbina.net ftp:

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

thus I havent being able to update for like 32 days...

I share internet with my office, and everything goes through a proxy, which requires authentication. 

I went to PREFERENCES>NETWORK PROXY and filled in the details... im not sure if that helps but i thought i'd let you know. And I can't use pidgin either (which I could before i got this new job) but I CAN use things like mozzila... but i cant use the ADD and REMOVE thing which i really need.

I have Ubuntu 9.04

Please help!

---

### Post by wojox on 2009-09-12
Open System > Admin > Software Sources Ubuntu Software and try downloading from a different server.

---

### Post by Findarato on 2009-09-12
I might be completely wrong, but "ping ftp.corbina.net" returns nothing to me, this would mean the servers are simply down, right ?

---

### Post by Bucky Ball on 2009-09-12
Could be right as this:

Unable to connect to ftp.corbina.net ftp:

... is obviously your problem.

---

### Post by PolloE on 2009-09-12
OK...

i tried another two servers (the US one and the "MAIN" one) and when I hit relod i get (this time) i different message:

```
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-amd64/Packages  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-amd64/Packages  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-amd64/Packages  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-amd64/Packages  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-amd64/Packages  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-amd64/Packages  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-amd64/Packages  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-amd64/Packages  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-amd64/Packages  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-amd64/Packages  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-amd64/Packages  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-amd64/Packages  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Some index files failed to download, they have been ignored, or old ones used instead.
```

and i noticed that at the end of each sentecne it says:

```
"Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )"
```

any idea whats wrong?

---

### Post by Bucky Ball on 2009-09-12
That looks like it is generating from your office set up and is not letting you out of the LAN.

---


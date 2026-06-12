---
title: "update help"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by MikeyLinux on 2009-04-21
i get the following while going to update mgr. i know the repositories need to be changed but what do i change them to? I appreciate it.

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.6+nobinonly-0ubuntu0.8.04.1_i386.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.6+nobinonly-0ubuntu0.8.04.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.6+nobinonly-0ubuntu0.8.04.1_all.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.6+nobinonly-0ubuntu0.8.04.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.6+nobinonly-0ubuntu0.8.04.1_all.deb)
  404 Not Found [IP: 91.189.88.31 80]


W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ubuntu/pool/main/u/ubuntu-tweak/ubuntu-tweak_0.4.5-1~hardy1_all.deb](http://ppa.launchpad.net/tualatrix/ubuntu/pool/main/u/ubuntu-tweak/ubuntu-tweak_0.4.5-1~hardy1_all.deb)
  404 Not Found

---

### Post by vigyani on 2009-04-21
Is you internet connection working?

what is the result of running the following command in a terminal;

ping us.archive.ubuntu.com

You can stop the above command using Ctl+c

---

### Post by MikeyLinux on 2009-04-21
connection is working. i goto update mgr and get those errors.

this is the results

PING us.archive.ubuntu.com (91.189.88.40) 56(84) bytes of data.
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=1 ttl=44 time=155 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=2 ttl=44 time=163 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=3 ttl=44 time=142 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=4 ttl=44 time=167 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=5 ttl=44 time=154 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=6 ttl=44 time=162 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=7 ttl=44 time=160 ms

--- us.archive.ubuntu.com ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 5997ms
rtt min/avg/max/mdev = 142.719/158.114/167.084/7.413 ms

---

### Post by MikeyLinux on 2009-04-21
when i goto terminal to update i get this at the end.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: You may want to run apt-get update to correct these problems

---

### Post by MikeyLinux on 2009-04-21
ok i got the updates working except the last error message error message about the key/ any idea on what i need to do to fix that.

---

### Post by Partyboi2 on 2009-04-22
Hi, to add the key open a terminal and type or paste
```
gpg --keyserver keyserver.ubuntu.com --recv 6AF0E1940624A220
gpg --export --armor  6AF0E1940624A220 | sudo apt-key add -
```
then
```
sudo apt-get update
```

---


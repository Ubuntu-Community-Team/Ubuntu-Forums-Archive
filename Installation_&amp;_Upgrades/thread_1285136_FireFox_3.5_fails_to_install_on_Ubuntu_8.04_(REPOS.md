---
title: "FireFox 3.5 fails to install on Ubuntu 8.04 (REPOSTING)"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by mamboknave on 2009-10-07
I'm in Ubuntu 8.04. and I'm trying to install *properly* Mozilla FireFox 3.5.

I followed several suggestions and ALL failed!

The [**_last link_**]("http://www.ubuntusolutions.org/2009/07/ubuntu-firefox-3-5-install-use-ubuntu-mozilla-security.html") I tried, reported the following errors, exactly like [**_the one before_**]("http://www.ubuntusolutions.org/2009/07/installing-firefox-3-5-the-right-way-on-ubuntu-jaunty.html"):

> sudo apt-get install firefox-3.5 firefox-3.5-gnome-support
...
The following packages have unmet dependencies:
  firefox-3.5: Depends: xulrunner-1.9.1 (>= 1.9.1) but it is not going to be installed
               Depends: libasound2 (> 1.0.18 ) but 1.0.15-3ubuntu4 is to be installed
               Depends: libgtk2.0-0 (>= 2.16.0) but 2.12.9-3ubuntu5 is to be installed
  firefox-3.5-gnome-support: Depends: libasound2 (> 1.0.18 ) but 1.0.15-3ubuntu4 is to be installed
                             Depends: xulrunner-1.9.1-gnome-support but it is not going to be installed
E: Broken packages

But, again, I tried few others with no success!

Can someone please help?
Thanks

---

### Post by aysiu on 2009-10-07
I don't think Firefox 3.5 is available for Ubuntu 8.04:
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=firefox-3.5](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=firefox-3.5)

Can you paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
cat /etc/apt/sources.list
```

---


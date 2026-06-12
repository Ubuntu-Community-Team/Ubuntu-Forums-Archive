---
title: "Update ubuntu 7.10 Gutsy server upgrade"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by Slancher on 2009-04-28
I'm wondering how to update my 7.10 Gutsy server.  The sources.list file is out of date. The sources seem to have been removed from archive.ubuntu.com

The only access I have to this server is via ssh since it lives in a different city.

Any ideas would be appreciated.

---

### Post by tahnok on 2009-04-28
You can run a system update with the following two commands from the terminal once you've logged in via ssh.

The first is to update your sources.list

```
 sudo apt-get update 
```

and the second is to actually upgrade all the out of date packages

```
 sudo apt-get upgrade 
```

---

### Post by snowpine on 2009-04-28
There will be no new updates for 7.10, as support ended earlier this month. I recommend 8.04, the current long-term-support version (supported through April 2011).

---

### Post by Slancher on 2009-04-28
apt-get update and apt-get upgrade both fail:

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/ntp/ntpdate_4.2.4p0+dfsg-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/ntp/ntpdate_4.2.4p0+dfsg-1ubuntu2.1_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

apt-get update --fix-missing doesn't do anything.

---

### Post by Slancher on 2009-04-28
I'd like to upgrade to 8.04 but I'm not sure how to acomplish this.  apt-get dist-upgrade fails.  I believe this is all due to the out of date sources.list file.

---

### Post by snowpine on 2009-04-28
Try editing sources.list and changing all instances of 'gutsy' to 'hardy'. This is the Debian method, but I think it will also work in Ubuntu when all else fails.

---

### Post by Slancher on 2009-04-28
> **snowpine said:**
> Try editing sources.list and changing all instances of 'gutsy' to 'hardy'. This is the Debian method, but I think it will also work in Ubuntu when all else fails.

Thanks, so far this is working like a charm.

---


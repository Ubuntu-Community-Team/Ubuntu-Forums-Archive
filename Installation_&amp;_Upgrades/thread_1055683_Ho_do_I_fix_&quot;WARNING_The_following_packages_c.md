---
title: "Ho do I fix &quot;WARNING: The following packages cannot be authenticated&quot;"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by snake_eyes on 2009-01-31
Hello,

I ran this command to install apache and php5:
```
sudo apt-get install apache2 php5 libapache2-mod-php5 php5-common php5-ldap php5-odbc
```
Bu I got this error message, how do I fix it?
```
Err http://sa.archive.ubuntu.com hardy Release.gpg
  Could not resolve 'sa.archive.ubuntu.com'
Err http://sa.archive.ubuntu.com hardy/main Translation-en_US
  Could not resolve 'sa.archive.ubuntu.com'
Err http://sa.archive.ubuntu.com hardy/restricted Translation-en_US
  Could not resolve 'sa.archive.ubuntu.com'
Err http://sa.archive.ubuntu.com hardy/universe Translation-en_US
  Could not resolve 'sa.archive.ubuntu.com'
Err http://sa.archive.ubuntu.com hardy/multiverse Translation-en_US
  Could not resolve 'sa.archive.ubuntu.com'
Err http://security.ubuntu.com hardy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://sa.archive.ubuntu.com hardy-updates Release.gpg
  Could not resolve 'sa.archive.ubuntu.com'
Err http://sa.archive.ubuntu.com hardy-updates/main Translation-en_US
  Could not resolve 'sa.archive.ubuntu.com'
Err http://sa.archive.ubuntu.com hardy-updates/restricted Translation-en_US
  Could not resolve 'sa.archive.ubuntu.com'
Err http://sa.archive.ubuntu.com hardy-updates/universe Translation-en_US
  Could not resolve 'sa.archive.ubuntu.com'
Err http://sa.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
  Could not resolve 'sa.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://sa.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not resolve 'sa.archive.ubuntu.com'

W: Failed to fetch http://sa.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not resolve 'sa.archive.ubuntu.com'

W: Failed to fetch http://sa.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Could not resolve 'sa.archive.ubuntu.com'

W: Failed to fetch http://sa.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Could not resolve 'sa.archive.ubuntu.com'

W: Failed to fetch http://sa.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'sa.archive.ubuntu.com'

W: Failed to fetch http://sa.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not resolve 'sa.archive.ubuntu.com'

W: Failed to fetch http://sa.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'sa.archive.ubuntu.com'

W: Failed to fetch http://sa.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'sa.archive.ubuntu.com'

W: Failed to fetch http://sa.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'sa.archive.ubuntu.com'

W: Failed to fetch http://sa.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'sa.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```
and this is my sources.list
```
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://sa.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://sa.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://sa.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://sa.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://sa.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://sa.archive.ubuntu.com/ubuntu/ hardy universe
deb http://sa.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://sa.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://sa.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://sa.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://sa.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://sa.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://sa.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://sa.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://sa.security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://sa.security.ubuntu.com/ubuntu hardy-security main restricted
deb http://sa.security.ubuntu.com/ubuntu hardy-security universe
deb-src http://sa.security.ubuntu.com/ubuntu hardy-security universe
deb http://sa.security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://sa.security.ubuntu.com/ubuntu hardy-security multiverse
```

Cheers,

---

### Post by lykwydchykyn on 2009-01-31
If you are downloading them from the main repositories (rather than some ppa or third-party repository), then there's nothing you can do.  Not every package has been digitally signed, as far as I know.

Can you post the exact output from that command?

---

### Post by snake_eyes on 2009-01-31
Sorry I updated my previous post above, I included the exact error.

Please help!

---

### Post by lykwydchykyn on 2009-01-31
It says it cannot resolve the addresses, which means either the network is down on the machine or DNS is not working for it. 

Can you browse the web on the machine getting these errors?

---

### Post by snake_eyes on 2009-01-31
> **lykwydchykyn said:**
> It says it cannot resolve the addresses, which means either the network is down on the machine or DNS is not working for it. 

Can you browse the web on the machine getting these errors?

Thank my dear for you advice, actually I tried 2 simulate this before I post my issue and there I can browse sites through FF.

but now I ran cat /etc/resolv.conf it noticed that there is no DNS, how do I refresh my DNS through shell?

---

### Post by lykwydchykyn on 2009-01-31
If you're on DHCP, just renew the address, like so:
```

dhclient eth0

```

If you're on static IP, first remove the "resolvconf" package, and then put a line in /etc/resolv.conf for your DNS server.

```

sudo aptitude purge resolvconf
echo "nameserver 192.168.1.254" >> /etc/resolv.conf

```
Of course, replace 192.168.1.254 with the IP of your DNS server.  If you're not sure, see what your workstation is using.

---

### Post by snake_eyes on 2009-01-31
> **lykwydchykyn said:**
> If you're on DHCP, just renew the address, like so:
```

dhclient eth0

```

If you're on static IP, first remove the "resolvconf" package, and then put a line in /etc/resolv.conf for your DNS server.

```

sudo aptitude purge resolvconf
echo "nameserver 192.168.1.254" >> /etc/resolv.conf

```
Of course, replace 192.168.1.254 with the IP of your DNS server.  If you're not sure, see what your workstation is using.

Thank you my dear..... Solved!!!

---


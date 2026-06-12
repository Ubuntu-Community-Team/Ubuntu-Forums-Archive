---
title: "Update Manager cannot resolve some hosts?"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by sblunix on 2009-10-25
When using Update Manager on Ubuntu Karmic Koala, I get the following error every time:

```

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://apt.wakoopa.com/dists/all/Release.gpg  Could not resolve 'apt.wakoopa.com'

W: Failed to fetch http://apt.wakoopa.com/dists/all/main/i18n/Translation-en_US.bz2  Could not resolve 'apt.wakoopa.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

```Is there anything I should do?

---

### Post by lemming465 on 2009-10-27
Check that DNS resolution works, e.g. try ```
host archive.canonical.com
``` from a terminal prompt.  If it doesn't, that's your problem.

Next, see if /etc/resolv.conf makes sense.  If it doesn't contain any lines of the form
"nameserver xxx.yyy.zzz.www" where xxxx, yyy, zzz, and www are all digits, you have a problem with your DHCP setup.  Try power cycling your modem and/or router and/or computer as a quick possible fix.

If /etc/resolv.conf has IP addresses in it, like 12.34.56.78, try ```
ping -c4 12.34.56.78
``` substituting one of the nameserver "dotted quad" IP addresses from /etc/resolv.conf.  Good output looks something like:
> PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=1 ttl=55 time=47.7 ms
64 bytes from 208.67.222.222: icmp_seq=2 ttl=55 time=34.4 ms
64 bytes from 208.67.222.222: icmp_seq=3 ttl=55 time=32.5 ms
64 bytes from 208.67.222.222: icmp_seq=4 ttl=55 time=32.7 ms


If the ping doesn't work, you have no network connectivity.  Try power cycling your modem and/or router and/or computer as a quick possible fix.

If the ping works, try something like```
host archive.canonical.com. 12.34.56.78 
``` to see if DNS lookups work.  Use the same IP address from your nameserver line.  Be sure to include the trailing "." (period) at the end of the name you are looking up.  A successful DNS lookup includes a line of output like:> archive.canonical.com has address 91.189.90.142 and does not include any failure lines like> Host flubber.canonical.com not found: 3(NXDOMAIN)

If /etc/resolve.conf is empty, or contains no nameserver lines, then try```
sudo nano /etc/resolv.conf
```and edit it to have one of the public OpenDNS servers, say> nameserver 208.67.222.222

Now retry the *host archive.canonical.com* lookup.

---


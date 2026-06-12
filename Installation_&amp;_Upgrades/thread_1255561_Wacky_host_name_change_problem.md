---
title: "Wacky host name change problem"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by HaroldCo on 2009-09-01
On Xbuntu 9.04
Used hostname to change system name
Change populated to hosts and hostname files
For good measure I used sysctl kernel.hostname= successfully.
Everybody is happy except SYSLOG
Event headers have old name in message
uname and hostname return good name
released dhcp and it sees new name
Where is syslog picking up old name?

---

### Post by HaroldCo on 2009-09-02
After trouble shooting syslog discovered that syslogd service on target machine was caching old name.

---


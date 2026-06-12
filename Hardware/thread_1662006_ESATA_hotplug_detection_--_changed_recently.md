---
title: "ESATA hotplug detection -- changed recently?"
date: 2011-01-07
forum: Hardware
---

### Post by jtappin on 2011-01-07
Has there been a recent change in the handling of hotplugging detection?

Up to late last year (some time after I'd upgraded to 10.10) if I plugged in an ESATA external hard drive, I got a prompt for password and then the disk was mounted. Now I get nothing (no messages in /var/log/syslog, no device nodes created).

If however I plug the drive in before booting, the device nodes are present and can be mounted.

I have tried this with both Ext4 and VFAT formatted drives -- same result.

The last confirmable date of a "proper" mount was 17 Dec 2010.

I have the KDE device notifier configured to show all devices -- but  think any change is occurring before things get to userspace.

---


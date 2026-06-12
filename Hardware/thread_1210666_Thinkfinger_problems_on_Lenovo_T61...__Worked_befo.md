---
title: "Thinkfinger problems on Lenovo T61...  Worked before reinstall."
date: 2009-07-11
forum: Hardware
---

### Post by raintheory on 2009-07-11
So I reinstalled Jaunty, and followed the jaunty instructions here to enable the fingerprint reader: [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Jaunty](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Jaunty)

While this had worked fine previously, it seems that now the only time it works is when typing "su" @ terminal (but sudo doesn't work).  Previously, the login screen (and sudo @ terminal, amongst other password requests) would ask for "Password or Swipe Finger".  ...Not the case now, and I'm not sure why or where to look/what to tweak.

My /etc/pam.d/common-auth as is follows:

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth	sufficient	pam_thinkfinger.so
auth	[success=1 default=ignore]	pam_unix.so try_first_pass nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```

Any help would be greatly appreciated, it's a vanilla install currently, so if a reinstall would make things easier that would be fine.  I've done this already 3 times with same results.

Thanks!

---


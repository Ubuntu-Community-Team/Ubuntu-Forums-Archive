---
title: "Got fingerprint reader working ...kinda. HP Compaq 6910p"
date: 2009-12-19
forum: Hardware
---

### Post by raintheory on 2009-12-19
Running Ubuntu 9.10

So I installed libpam-fprint, fprint-demo, libfprint-dev, etc..

Enrolled fingerprint..

Added the following 2 lines to /etc/pam.d/common-auth

```

auth sufficient pam_fprint.so
auth required pam_unix.so nullok_secure

```

Fingerprint reader does work, however I am being asked for a password *first* on login and sudo, and *then* a fingerprint (both).

I'd like this to be reversed, where I am asked for a fingerprint, and *failing that*, a password.

Where did I go wrong?

Thanks!

---

### Post by Whoopie on 2009-12-19
You could try adding "try_first_pass" at the end of the pam_unix line.

---

### Post by raintheory on 2009-12-20
added try_first_pass.  

moved the entries up before the primary block.

i'm asked for a fingerprint first now, but then also for a password, twice.

here are the contents of /etc/pam.d/common-auth

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
# added myself
auth	sufficient			pam_fprint.so
auth	required 			pam_unix.so nullok_secure try_first_pass
# here are the per-package modules (the "Primary" block)
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so

# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```

---


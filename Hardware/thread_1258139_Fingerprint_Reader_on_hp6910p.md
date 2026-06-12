---
title: "Fingerprint Reader on hp6910p"
date: 2009-09-04
forum: Hardware
---

### Post by mathgeek2000 on 2009-09-04
I'm trying to get my fingerprint reader working with Ubuntu 9.04 (Jaunty) and having some trouble with PAM. -- well, that's the half of it.
  -- I seem to be having trouble with PAM altogether.

What I'd like is to be able to use my fingerprint to log in, *RATHER* than the password.
the problem is the 'sufficient' keyword doesn't seem to work correctly.

for example it seems to pass the result (fail or succeed) on to the next line, which calls for a typed password:
    
  ```
auth sufficient pam_fprint.so
  auth [success=1 ... ] pam_unix.so
   ... 
```

if I comment out the '@include common-auth' from the '/etc/pam.d/login' I'll log in without any prompt for password.

Any help would be appreciated.

---


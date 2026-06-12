---
title: "fglrx/Catalyst not working in Quantal"
date: 2012-10-22
forum: Hardware
---

### Post by alexThunderr on 2012-10-22
Hi,

I just upgraded to quantal and installed the Catalyst 12.8. fglrxinfo now gives me this:

```
BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```

Same with Catalyst 12.9 Beta and 12.10

I have a Radeon 5870 and I'm on quantal with 3.5 64 bit

---

### Post by alexThunderr on 2012-10-23
Ok, I didn't know, that the current XOrg isn't supported by the drivers from the AMD site, but the version from the repos works.

---

### Post by novafluxx on 2012-10-23
Please check out this thread and let me know if that helps you out. If you still need help :)

[http://ubuntuforums.org/showthread.php?p=12309529#post12309529](http://ubuntuforums.org/showthread.php?p=12309529#post12309529)

---


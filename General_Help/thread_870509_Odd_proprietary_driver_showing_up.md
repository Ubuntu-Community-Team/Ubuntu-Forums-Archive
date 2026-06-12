---
title: "Odd proprietary driver showing up"
date: 2008-07-25
forum: General Help
---

### Post by lzydba on 2008-07-25
Just after I rebooted after applying the latest kernel update on 07/25 (hardy) I now have this new proprietary driver showing up. It is listed in the proprietary drivers window as "w|" and the description just says:

"This driver is necessary to support the hardware, there is no free/open alternative.

If this driver is not enabled, the hardware will not function"

Now I have to admit to being lazy and not having read the changelog or release notes, but being an ex-abused Windows child, something like this makes me nervous.

Does anyone else have this? And/Or know what this driver is?

---

### Post by sdennie on 2008-07-26
What is the output of:

```

uname -r

```

If it's "2.6.24-**20**-generic" then you are using the kernel from the proposed repository which is essentially a beta kernel (and drivers).  If that's the case you may want to search launchpad to see if it's a known bug and, if not, file a bug so that it can be fixed before it's released.  Also, to prevent things like this in the future, you may want to go to System->Administration->Software Sources and disable the proposed repository.

---

### Post by lzydba on 2008-07-26
Thank you Vor. uname -r does result in 2.6.24-20-generic. I must have blindly checked off the proposed updates when I was trying to install something, my bad.

I signed up at launchpad and filed the bug.

---


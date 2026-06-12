---
title: "Tip for Brother MFD users installing 11.10 64 bit"
date: 2011-10-15
forum: Hardware
---

### Post by kurt18947 on 2011-10-15
First, I'm not sure if this is the correct place for this post. Mods, please feel free to move as you see fit. 

I've had excellent success installing Brother Multi-function machines -- until 11.10. The scan function wouldn't work on 64 bit installs, the print function was as expected. 32 bit installs worked as expected.  The problem is with the 64 bit install.  The fix is found here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html)   first item.
There is one other item to be aware of when using this fix.  I moved the files using Nautilus.  Make sure you copy the files that are in ```
/user/lib64/sane/
```to ```
user/lib/sane
```I hope this saves someone the frustration it has caused me.

---

### Post by mörgæs on 2011-10-15
Thanks, moved to the hardware forum.

Also marked it 'solved'. The option is in 'thread tools'.

---

### Post by kurt18947 on 2011-10-15
> **mörgæs said:**
> Thanks, moved to the hardware forum.

Also marked it 'solved'. The option is in 'thread tools'.

Thank you.  I didn't think about 'solved', I'll keep that in mind.

---


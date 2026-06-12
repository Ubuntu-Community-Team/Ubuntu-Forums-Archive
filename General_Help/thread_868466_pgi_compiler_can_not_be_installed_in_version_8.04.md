---
title: "pgi compiler can not be installed in version 8.04"
date: 2008-07-23
forum: General Help
---

### Post by xhsh on 2008-07-23
Hello, Dear all,

I want to install pgi compiler (version 6.1.3) in Ubuntu 8.04. However, every time I run the "./install", I always get the following error message:

ERROR: arch not found (PATH = $PATH)
Exiting...

So, could you tell me how to do some setup so that I can continue with the installation process? Is there anybody who has this experience, please?

Thank you very much!!

---

### Post by mightyasp on 2008-08-01
Ditto, but for PGI 7.2-3.

For kicks I tried the recommended fix for the older versions:

replace "arch" with "uname -m" 

...but that didn't seem to get me anywhere.

Would LOVE some help with this one...I'm a little in the dark here.

Thanks!!

---


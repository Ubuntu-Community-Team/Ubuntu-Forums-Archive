---
title: "I need to compile a program with kernel 2.4..."
date: 2008-10-07
forum: General Help
---

### Post by SolidAndShade on 2008-10-07
I need to compile a program under Linux kernel 2.4 so that it'll run on a server that uses 2.4. Is there an easy way to install a 2.4 kernel and get a 2.4 environment in Hardy? My searches haven't turned up anything useful on this. Thanks for any help.

---

### Post by ajmorris on 2008-10-07
> **SolidAndShade said:**
> I need to compile a program under Linux kernel 2.4 so that it'll run on a server that uses 2.4. Is there an easy way to install a 2.4 kernel and get a 2.4 environment in Hardy? My searches haven't turned up anything useful on this. Thanks for any help.
 
hi there,
Generally package versions that old, are not kept on the repositories, and replaced with newer versions. With the kernel, running something that old, on a new system (hardy for example) will yield weird results, and things may not function correctly. However, if you *need* a 2.4 kernel, you can download one from kernel.org, and compile it manually, if you have no experience or interest in learning how to configure a kernel for manual compilation, you can try copying the .config file from your current ubuntu kernel config. But, again, copying the config file from a new kernel, to a 2.4 kernel, will end up in not everything functioning, especially as a lot of changes have been made to the kernel since 2.4.
 
This being said, why is your server using a 2.4 kernel?
 
AJ

---

